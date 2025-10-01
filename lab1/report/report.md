---
## Front matter
title: "Отчёт по лабораторной работе 1-C (НФИ-2)"
subtitle: "Программный комплекс обучения методам обнаружения, анализа и устранения последствий компьютерных атак «Ampire»"
author: "Козлов В.П., Гаинэ А., Шуваев С., Джахангиров И.З, Хватов М.Г. | НФИбд-02-22"

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

Отработка на практике методов обнаружения, анализа и нейтрализации многоэтапной компьютерной атаки, направленной на кражу научно-технической информации предприятия, с использованием учебного программного комплекса «Ampire».

# Задание

1. Обнаружить подбор пароля к файловому серверу и последующую загрузку вредоносного файла.

2. Выявить бэкдор на рабочей станции через анализ планировщика задач и запущенных процессов.

3. Зафиксировать кражу учётных данных (например, с помощью утилиты LaZagne) и их использование для доступа к Redmine.

4. Проанализировать XSS-атаку в Redmine, которая привела к включению REST API и созданию привилегированного пользователя.

5. Обнаружить слепую SQL-инъекцию, используемую для извлечения конфиденциальных данных из базы данных.

6. Нейтрализовать последствия атаки: удалить бэкдор, несанкционированного пользователя и внедрённый вредоносный код.

7. Устранить уязвимости: пропатчить Redmine от XSS (CVE-2019-17427) и SQL-инъекции (CVE-2019-18890), усилить политику паролей.

# Выполнение лабораторной работы

Активировали WireGuard и зашли на сайт платформы (рис. [-@fig:001])

![Установка Chocolatey](image/1.png){ #fig:001 width=70% }

На сайте ViPNet IDS NS просмотрели атакованные ip-адреса и суть атак (рис. [-@fig:002])

![Атакованные ip-адреса](image/2.png){ #fig:002 width=70% }

Добавили карточку инцидента Weak Password (рис. [-@fig:100])

![Карточка инцидента Weak Password](image/100.png){ #fig:100 width=70% }

Добавили карточку инцидента XSS (рис. [-@fig:200])

![Карточка инцидента XSS](image/200.png){ #fig:200 width=70% }

Добавили карточку инцидента SQL-injection (рис. [-@fig:300])

![Добавили карточку инцидента SQL-injection](image/300.png){ #fig:300 width=70% }

Атака XSS. Открыли на редактирование файл redcloth3.rb атакованного ip-адреса (рис. [-@fig:003])

![Файл redcloth3.rb атакованного ip-адреса](image/3.png){ #fig:003 width=70% }

Атака XSS. Удалили тег pre из разрешенных тегов, которые не будут экранированы (рис. [-@fig:004])

![Удаление тега](image/4.png){ #fig:004 width=70% }

Атака XSS. Перезапустили службу веб-сервера: sudo systemctl restart nginx.service (рис. [-@fig:005])

![Перезапуск службы веб-сервера](image/5.png){ #fig:005 width=70% }

Последствия XSS. Удалили пользователя hacker (рис. [-@fig:006])

![Удалиление пользователя hacker](image/6.png){ #fig:006 width=70% }

Атака SQL-инъекция. Открыли файл query.rb на редактирование на 10.10.2.15 (рис. [-@fig:007])

![Файл query.rb](image/7.png){ #fig:007 width=70% }

Атака SQL-инъекция. Отредактировали query.rb, заменив each на map (рис. [-@fig:008])

![Редактирование query.rb](image/8.png){ #fig:008 width=70% }

Атака SQL-инъекция. Перезапустили nginx (рис. [-@fig:009])

![Перезапуск nginx](image/9.png){ #fig:009 width=70% }

Атака Weak Password. Зашли на MS Active Directory (рис. [-@fig:010])

![MS Active Directory](image/10.png){ #fig:010 width=70% }
 
Атака Weak Password. Сбросили пароль на dev1 (рис. [-@fig:011])

![Сброс пароля](image/11.png){ #fig:011 width=70% }

Последствие Weak Password. Удалили Evil Task из планировщика задач (рис. [-@fig:012])

![Удаление Evil Task](image/12.png){ #fig:012 width=70% }

Все атаки и их последствия успешно устранены

# Выводы

Отработали на практике методы обнаружения, анализа и нейтрализации многоэтапной компьютерной атаки, направленной на кражу научно-технической информации предприятия, с использованием учебного программного комплекса «Ampire».

# Список литературы
1.  **CVE-2019-0630** — Common Vulnerabilities and Exposures.  
    URL: `https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-0630`

2.  **CVE-2019-17427** — Уязвимость XSS в Redmine.  
    URL: `https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17427`

3.  **CVE-2019-18890** — Уязвимость Blind SQL-инъекции в Redmine.  
    URL: `https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-18890`