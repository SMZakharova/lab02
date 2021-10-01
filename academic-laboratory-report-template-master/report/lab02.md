---
# Front matter
title: "Отчёт по лабораторной работе №2"
subtitle: "Дискреционное разграничение прав в Linux. Основные атрибуты"
author: "Захарова Софья Михайловна"

# Generic otions
lang: ru-RU

# Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

# Pdf output format
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Misc options
indent: true
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.


# Задание

Лабораторная работа подразумевает работу с виртуальной машиной VirtualBox, операционной системой Linux, дистрибутивом Centos и закрепление теоретических основ дискреционного разграничения доступа.


# Выполнение лабораторной работы

В установленной при выполнении предыдущей лабораторной работы операционной системе создаем учётную запись пользователя guest.И задаем для нее пароль.

![Рис.1. Создание учетной записи и пароля.](images/1.jpg){ #fig:001 width=70% }

Входим в систему от имени пользователя guest.

![Рис.2. Вход в систему.](images/2.jpg){ #fig:001 width=70% }

Определяем директорию, в которой находимся, командой pwd и заходим в домашнюю директорию. 

![Рис.3. Определение директории.](images/3.jpg){ #fig:001 width=70% }

Уточняем имя пользователя командой whoami.

![Рис.4. Уточнение имени пользователя.](images/4.jpg){ #fig:001 width=70% }

Уточняем данные пользователя командой id. Сравниваем вывод id с выводом команды groups.

![Рис.5. Сравниваем команды id и groups.](images/5.jpg){ #fig:001 width=70% }

Просматриваем файл /etc/passwd командой cat /etc/passwd. 

![Рис.6. Ввод команды.](images/6.jpg){ #fig:001 width=70% }

Находим свою учётную запись. Определяем uid пользователя. Определяем gid пользователя. Сравниваем найденные значения с полученными в предыдущих пунктах.Они овпадают.

![Рис.7. Сравнение данных с полученными ранее.](images/7.jpg){ #fig:001 width=70% }

Определяем существующие в системе директории командой ls -l /home/. Команда выполнилась, у нас оказалось достаточно прав.

![Рис.8. Вывод директой и их прав.](images/8.jpg){ #fig:001 width=70% }

Проверяем, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории/home, командой: lsattr /home. Здесь нам отказано в доступе.

![Рис.9. Вывод атибутов.](images/9.jpg){ #fig:001 width=70% }

Создаем в домашней директории поддиректорию dir1 командой mkdir dir1.

![Рис.10. Создание директории.](images/10.jpg){ #fig:001 width=70% }

Проверяем права и атрибуты для этой директории.

![Рис.11. Вывод прав и атрибутов.](images/11.jpg){ #fig:001 width=70% }

Снимаем все атрибуты с этой директории.

![Рис.12. Снятие атрибутов.](images/12.jpg){ #fig:001 width=70% }

Попытка создания файла. Отказано в достпе.

![Рис.13. Отказ в доступе на создание файла.](images/13.jpg){ #fig:001 width=70% }

Проверяем, действительно ли файл не создан. Отказано в доступе.

![Рис.14. Отказ в доступе.](images/14.jpg){ #fig:001 width=70% }

Заполняем таблицу установленных прав и разрешенных действий.

![Рис.15. Таблица 1. Установленные права и разрешенные действия.](images/15.jpg){ #fig:001 width=70% }

Заполняем таблицу минимально необходимых прав.

![Рис.16. Таблица 2. Минимально необходимые права.](images/16.jpg){ #fig:001 width=70% }


# Выводы

В результате выполнения данной лабораторной работы я получила практические навыки работы в консоли с атрибутами файлов, закрепила теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.
