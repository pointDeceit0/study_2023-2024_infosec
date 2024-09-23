# 1 Цель Работы

Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей.

# 2 Теоретическое Введение

В операционной системе Linux есть много отличных функций безопасности, но одна из самых важных - это система прав доступа к файлам. Изначально каждый файл имел три параметра доступа. Вот они:
• Чтение - разрешает получать содержимое файла, но на запись нет. Для каталога позволяет получить список файлов и каталогов, расположенных в нем
• Запись - разрешает записывать новые данные в файл или изменять существующие, а также позволяет создавать и изменять файлы и каталоги
• Выполнение - невозможно выполнить программу, если у нее нет флага выполнения. Этот атрибут устанавливается для всех программ и скриптов, именно с помощью него система может понять, что этот файл нужно запускать как программу 
Каждый файл имеет три категории пользователей, для которых можно устанавливать различные сочетания прав доступа:
• Владелец - набор прав для владельца файла, пользователя, который его создал или сейчас установлен его владельцем. Обычно владелец имеет все права, чтение, запись и выполнение 
• Группа - любая группа пользователей, существующая в системе и привязанная к файлу. Но это может быть только одна группа и обычно это группа владельца, хотя для файла можно назначить и другую группу

Остальные - все пользователи, кроме владельца и пользователей, входящих в группу файла 
Команды, которые могут понадобиться при работе с правами доступа: 
• “ls -l” - для просмотра прав доступа к файлам и каталогам 
• “chmod категория действие флаг файл или каталог” - для изменения прав доступа к файлам и каталогам (категорию действие и флаг можно заменить на набор из трех цифр от 0 до 7) 
Значения флагов прав: 
• — - нет никаких прав
• –x - разрешено только выполнение файла, как программы, но не изменение и не чтение 
• -w- - разрешена только запись и изменение файла 
• -wx - разрешено изменение и выполнение, но в случае с каталогом, невозможно посмотреть его содержимое 
• r– - права только на чтение
• r-x - только чтение и выполнение, без права на запись 
• rw- - права на чтение и запись, но без выполнения 
• rwx - все права

# 3 Выполнение

![[Pasted image 20240916192554.png]]
![[Pasted image 20240916192953.png]]
![[Pasted image 20240916193012.png]]

![[Pasted image 20240916193107.png]]


 d
(000)
(000) - - - - - - - -
d –x
(010)
(000) - - - - + - - -
d -w-
(020)
(000) - - - - - - - -
d -wx
(030)
(000) + + - - + - + -
d r–
(040)
(000) - - - - - + - -
d r-x
(050)
(000) - - - - + + - -
d rw-
(060)
(000) - - - - - + - -
d rwx
(070)
(000) + + - - + + + -
——————————-—————-————-————————–———————————————————————-—————-
d
(000)
(010) - - - - - - - -
d –x
(010)
(010) - - - - + - - -
d -w-
(020)
(010) - - - - - - - -
d -wx
(030)
(010) + + - - + - + -
d r–
(040)
(010) - - - - - + - -
d r-x
(050)
(010) - - - - + + - -
d rw-
(060)
(010) - - - - - + - -
d rwx
(070)
(010) + + - - + + + -
——————————-—————-————-————————–———————————————————————-—————-
d
(000)
(020) - - - - - - - -
d –x
(010)
(020) - - + - + - - -
d -w-
(020)
(020) - - - - - - - -
d -wx
(030)
(020) + + + - + - + -
d r–
(040)
(020) - - - - - + - -
d r-x
(050)
(020) - - + - + + - -
d rw-
(060)
(020) - - - - - + - -
d rwx
(070)
(020) + + + - + + + -
——————————-—————-————-————————–———————————————————————-—————-
d
(000)
(030) - - - - - - - -
d –x
(010)
(030) - - + - + - - -
d -w-
(020)
(030) - - - - - - - -
d -wx
(030)
(030) + + - + + - + -
d r–
(040)
(030) - - - - - + - -
d r-x
(050)
(030) - - + - + + - -
d rw-
(060)
(030) - - - - - + - -
d rwx
(070)
(030) + + + - + + + -
d
(000)
(040) - - - - - - - -
d –x
(010)
(040) - - - + + - - -
d -w-
(020)
(040) - - - - - - - -
d -wx
(030)
(040) + + - + + - + -
d r–
(040)
(040) - - - - - + - -
d r-x
(050)
(040) - - - + + + - -
d rw-
(060)
(040) - - - - - + - -
d rwx
(070)
(040) + + - + + + + -
——————————-—————-————-————————–———————————————————————-—————-
d
(000)
(050) - - - - - - - -
d –x
(010)
(050) - - - + + - - -
d -w-
(020)
(050) - - - - - - - -
d -wx
(030)
(050) + + - + + - + -
d r–
(040)
(050) - - - - - + - -
d r-x
(050)
(050) - - - + + + - -
d rw-
(060)
(050) - - - - - + - -
d rwx
(070)
(050) + + - + + + + -
——————————-—————-————-————————–———————————————————————-—————-
d
(000)
(060) - - - - - - - -
d –x
(010)
(060) - - + + + - - -
d -w-
(020)
(060) - - - - - - - -
d -wx
(030)
(060) + + + + + - + -
d r–
(040)
(060) - - - - - + - -
d r-x
(050)
(060) - - + + + + - -
d rw-
(060)
(060) - - - - - + - -
d rwx
(070)
(060) + + + + + + + -
——————————-—————-————-————————–———————————————————————-—————-
d
(000)
(070) - - - - - - - -
d –x
(010)
(070) - - + + + - - -
d -w-
(020)
(070) - - - - - - - -
d -wx
(030)
(070) + + + + + - + -
d r–
(040)
(070) - - - - - + - -
d r-x
(050)
(070) - - + + + + - -
d rw-
(060)
(070) - - - - - + - -
d rwx
(070)
(070) + + + + + + + -
Сравнивая полученную таблицу с таблицей из прошлой лабораторной работы,
приходим к выводу, что изменился только последний столбец, позволяющий
изменять атрибуты у файла: теперь это сделать невозможно, т.к. у владельца
файла и директории нет на это прав (во всех случаях в первой позиции стоят
0). При определенном наборе прав остальные действия выполняются или не
выполняются аналогично предыдущей таблице, но теперь как для владельца, так
и для группы.

Создание файла d -wx (030) (000)
Удаление файла d -wx (030) (000)
Чтение файла d –x (010) (040)
Запись в файл d –x (010) (020)
Переименование файла d -wx (030) (000)
Создание поддиректории d -wx (030) (000) Удаление поддиректории d -wx (030) (000)

# 4 Выводы
В ходе выполнения данной лабораторной работы я получила практические навыки работы в консоли с атрибутами файлов для групп пользователей.