---
## Front matter
title: "Отчёт по лабораторной работе 1-C (НФИ-2)"
subtitle: "Программный комплекс обучения методам обнаружения, анализа и устранения последствий компьютерных атак «Ampire»"
author: "Козлов В.П., Гэинэ А., Шуваев С., Джахангиров И.З, Хватов М.Г. | НФИбд-02-22"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: Arial
romanfont: Arial
sansfont: Arial
monofont: Arial
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
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Отработать сценарий действий нарушителя
«Защита контроллера домена предприятия» на базе программного комплекса
обучения методам обнаружения, анализа и устранения последствий
компьютерных атак «Ampire».

# Задание

1. Обнаружить SQL-injection на PHP Server.

2. Устранить уязвимость в контроллере NewsController.php.

3. Устранить последствие (Web portal meterpreter). Убиваем сессию нарушителя.

4. Обнаружить сессию нарушителя на узле администратора.

5. Запустить защиту в реальном времени Windows defender, очистить регистр.

6. Устранить последствие (Admin meterpreter). Убиваем сессию нарушителя.

7. Обнаружить попытку подбора паролей на узле MS Active Directory.

8. Изменить пароль к учетной записи администратора на более
сложный.

9. Устранить последствие (AD User). Удалить нового привилегированного пользователя.

# Выполнение лабораторной работы

На сайте ViPNet IDS NS просмотрели атакованные активы и суть атак (рис. [-@fig:002])

![Атакованные ip-адреса](image/2.png){ #fig:002 width=70% }

Добавили карточку инцидента "SQL Инъекция" (рис. [-@fig:100])

![Карточка инцидента "SQL Инъекция"](image/100.png){ #fig:100 width=70% }

Добавили карточку инцидента "Отключённый антивирус" (рис. [-@fig:200])

![Карточка инцидента "Отключённый антивирус"](image/200.png){ #fig:200 width=70% }

Добавили карточку инцидента "Слабый пароль сервера AD" (рис. [-@fig:300])

![Добавили карточку инцидента "Слабый пароль сервера AD"](image/300.png){ #fig:300 width=70% }

SQL Инъекция. Открыли контроллер NewsController, добавили простейший фильтр для id (рис. [-@fig:003])

![NewsController.php](image/3.png){ #fig:003 width=70% }

SQL Инъекция. Убиваем сессию нарушителя (рис. [-@fig:004])

![Убиваем сессию](image/4.png){ #fig:004 width=70% }

Отключённый антивирус. Заходим на узел администратора, удаляем запись из регистра (рис. [-@fig:005])

![Удаление из регистра](image/5.png){ #fig:005 width=70% }

Отключённый антивирус. Включаем защиту в настоящем времени (рис. [-@fig:006])

![Включаем антиврус](image/6.png){ #fig:006 width=70% }

Отключённый антивирус. Находим PID сессии с нарушителем, убиваем её (рис. [-@fig:007])

![Сессия нарушителя устранена](image/7.png){ #fig:007 width=70% }

Слабый пароль. Заходим на MS AD, меняем пароль администратора (рис. [-@fig:008])

![Меняем пароль](image/8.png){ #fig:008 width=70% }

Слабый пароль. В Active directory users and computers, удаляем нового пользователя (рис. [-@fig:009])

![Удалили hacker'а](image/9.png){ #fig:009 width=70% }

Все атаки и их последствия успешно устранены

# Выводы

Отраболи сценарий действий нарушителя
«Защита контроллера домена предприятия» на базе «Ampire».

# Список литературы
1.  **CVE-2019-0630** — Common Vulnerabilities and Exposures.  
    URL: `https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-0630`

2.  **CVE-2019-17427** — Уязвимость XSS в Redmine.  
    URL: `https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17427`

3.  **CVE-2019-18890** — Уязвимость Blind SQL-инъекции в Redmine.  
    URL: `https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-18890`