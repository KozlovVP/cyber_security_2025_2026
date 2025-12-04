---
## Front matter
title: "Отчёт по лабораторной работе 4-C"
subtitle: "Захват backup-сервера"
author: "Козлов В.П., Шуваев С. | НФИбд-02-22"

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

Данный сценарий посвящён атаке на внутренний резервный сервер (backup-сервер) организации с целью получения конфиденциального флага. В ходе выполнения работы демонстрируются этапы разведки внутренней сети, поиска уязвимого хоста и эксплуатации уязвимости MS17-010 (EternalBlue) для получения доступа к файловой системе. Финальной задачей является извлечение файла flag.txt, содержащего ответ на задание.

# Задание

1. Получите доступ к сети через уязвимость на корпоративном сайте или почтовом сервере, создав meterpreter-сессию.

2. Исследуйте внутреннюю сеть, добавьте маршрут и найдите активные хосты с помощью сканирования ARP.

3. Найдите backup-сервер, отсканировав открытые порты (SMB 445, FTP 21) на найденных хостах.

4. Проверьте и эксплуатируйте уязвимость MS17-010 на найденном сервере, получив на него сессию с правами SYSTEM.

5. Найдите и прочитайте флаг в файле flag.txt.

# Выполнение лабораторной работы

Обнаружил уязвимые полигоны (рис. [-@fig:002])

![Уязвимые полигоны](image/2.png){ #fig:002 width=70% }

Нашел эксплойт для WpDiscuz и выбрал подходящий модуль (рис. [-@fig:003])

![Эксплойт для WpDiscuz](image/3.png){ #fig:003 width=70% }

Настроил параметры эксплойта (рис. [-@fig:004])

![Параметры эксплойта](image/4.png){ #fig:004 width=70% }

Получил доступ к www-data (рис. [-@fig:005])

![Доступ к www-data](image/5.png){ #fig:005 width=70% }

Добавил маршрут до внутренней подсети (рис. [-@fig:006])

![Маршрут до внутренней подсети](image/6.png){ #fig:006 width=70% }

Запуск прокси-сервера (рис. [-@fig:007])

![Запуск прокси-сервера](image/7.png){ #fig:007 width=70% }

Сканирование backup-сервера (рис. [-@fig:008])

![Сканирование backup-сервера](image/8.png){ #fig:008 width=70% }

Эксплуатация уязвимости (рис. [-@fig:009])

![Эксплуатация уязвимости](image/9.png){ #fig:009 width=70% }

Нашел местоположение файла (рис. [-@fig:010])

![Местоположение файла](image/10.png){ #fig:010 width=70% }

Содержимое файла (рис. [-@fig:011])

![Содержимое файла](image/11.png){ #fig:011 width=70% }

Ответ подошел (рис. [-@fig:012])

![Ответ подошел](image/12.png){ #fig:012 width=70% }

# Выводы

Сценарий показал, как устаревшее ПО (уязвимость MS17-010) на внутреннем сервере позволяет злоумышленнику, получившему доступ к сети, быстро захватить контроль над критическим ресурсом (backup-сервером). Это подтверждает важность регулярного обновления систем и строгой сегментации сети даже внутри защищённого периметра.

# Список литературы
1.  **CVE-2019-0630** — Common Vulnerabilities and Exposures.  
    URL: `https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-0630`

2.  **CVE-2019-17427** — Уязвимость XSS в Redmine.  
    URL: `https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17427`

3.  **CVE-2019-18890** — Уязвимость Blind SQL-инъекции в Redmine.  
    URL: `https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-18890`