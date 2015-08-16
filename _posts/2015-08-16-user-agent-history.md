---
layout:     post
title:      История user-agent
date:       2015-07-28
summary:    Если вам всегда было интересно почему user-agent в Chrome пишет, что он Mozilla, то добро пожаловать под кат.
categories: jekyll pixyll
permalink: /user-agent-history
---

## Первые браузеры  

Самый первый веб-браузер, Mosaic, был разработан в 1993 году в Национальном Центре Суперкомпьютерных приложений (National Center for Supercomputing Applications (NCSA)).

Его строка user-agent была довольно простой и выглядела примерно следующим образом

<pre><code class="nohighlight">Mosaic/0.9</code></pre>

Строка могла варьироваться в зависимости от операционной системы и платформы, однако, ее внешний вид оставался достаточно простым. Текст перед косой, чертой указывал на название продукта, а текст после черты — номер версии продукта.

Когда Netscape Communications начала разработку своего браузера, то дала ему кодовое имя Mozilla (сокращение от «Mosaic Killer»). Первая публичная версия называлась Netscape Navigator и использовала строку user-agent в следующем формате.

<pre><code class="nohighlight">Mozilla/Version [Language] (Platform; Encryption)</code></pre>

Как мы видим, Netscape продолжал традицию использования имени продукта и версии, однако после нее он добавлял следующую информацию:

Язык — код языка, указывающий, где предназначено использование приложения
Платформа — операционная система и/или платформы на которой приложение выполняется
Шифрование — используемый тип шифрования. Возможные значения: U (128-битное шифрование), I (40-битное шифрование), и N (не используется).

Строка user-agent в Netscape Navigator выглядела так:

<pre><code class="nohighlight">Mozilla/2.02 [fr] (WinNT; I)</code></pre>

Эта строка сообщает о том что используется Netscape Navigator версии 2.02, сборка предназначена для использования в франкоязычных странах и запущена на операционной системе WindowsNT c 40-битным шифрованием. В данном случае достаточно легко определить какой браузер используется, нужно просто взглянуть на название продукта в строке user-agent.

## Netscape Navigator 3 и Internet Explorer 3

В 1996 году был выпущен Netscape Navigator 3, он превзошел Mosaic и стал самым популярным веб-браузером. В строке user-agent произошло лишь небольшое изменение: был убран языковой маркер и добавлена дополнительная информация об операционной системе или процессоре, используемом системой.

Формат стал следующим:

<pre><code class="nohighlight">Mozilla/Version (Platform; Encryption [; OS-or-CPU description])</code></pre>

Строка user-agent для браузера Netscape  Navigator 3, запущенного под Windows выглядела следующим образом:

<pre><code class="nohighlight">Mozilla/3.0 (Win95; U)</code></pre>

Эта строка указывает что Netscape Navigator 3 работает под управлением Windows 95 с 128-битным шифрованием. Обратите внимание на то, что описание OS-or-CPU отсутствует в случае, когда браузер запущен на системе Windows.

Вскоре после выхода Netscape Navigator 3 компания Microsoft выпустила свой первый публично доступный веб-браузер — Internet Explorer 3. Netscape Navigator был доминирующим браузером в те времена, многие сервера специально делали проверку на соответствие перед тем, как отдать страницу. Эта ситуация не позволила был молодому браузеру нормально развиваться. Было принято решение создать строку user-agent, которая была бы совместима с user-agent, используемой в Netscape.

Результат стал следующим:

<pre><code class="nohighlight">Mozilla/2.0 (compatible; MSIE Version; Operating System)</code></pre>

Например, Internet Explorer 3.02 работавший на Windows 95 выдавал следующую строку user-agent

<pre><code class="nohighlight">Mozilla/2.0 (compatible; MSIE 3.02; Windows 95)</code></pre>

Поскольку большинство снифферов браузеров в то время смотрели только на первую часть строки, IE успешно определялся как Mozilla, так же как и Netscape Navigator. Этот шаг вызвал неоднозначную реакцию, поскольку нарушал Конвенцию Идентификации Браузера. Истинное же название браузера было в середине строки.

## Netscape Communicator 4 и Internet Explorer 4-8

В августе 1997 года был выпущен Netscape Communicator 4 (в этом релизе название было изменено с Navigator на Communicator). Начиная с версии 4 на компьютере с Windows 98 строка user-agent выглядела так:

<pre><code class="nohighlight">Mozilla/4.0 (Win98; I)</code></pre>

Netscape выпускала патчи и исправления для своего браузера. Соответственно, увеличивалась и версия. Как показано ниже строка user-agent выглядела имела следующий формат:

<pre><code class="nohighlight">Mozilla/4.79 (Win98; I)</code></pre>

Когда Microsoft выпустила Internet Explorer 4, строка user-agent приняла следующий формат:

<pre><code class="nohighlight">Mozilla/4.0 (compatible; MSIE Version; Operating System)</code></pre>

Например IE4, запущенный под Win98 возвращал следующую строку:

<pre><code class="nohighlight">Mozilla/4.0 (compatible; MSIE 4.0; Windows 98)</code></pre>

С этим изменением версия Mozilla и текущая версия IE были синхронизированы, что позволяло легко идентифицировать эти браузеры четвертого поколения. К сожалению, позже синхронизация была прекращена. В версии Internet Explorer 4.5 (она была выпущена только для Маков) версия Mozilla осталась обозначенной номером 4, а версия IE изменилась следующим образом:

<pre><code class="nohighlight">Mozilla/4.0 (compatible; MSIE 4.5; Mac_PowerPC)</code></pre>

Эта картина сохранялась вплоть до 7-й версии IE.

Internet Explorer 8 несколько изменил строку user-agent, добавив в нее версию движка рендеринга Trident:

<pre><code class="nohighlight">Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.1; Trident/4.0)</code></pre>

Добавление движка было важным, потому что версия MSIE изменялась на 7.0, в случае если IE8 работал в режиме совместимости, версия Trident оставалась такой же. Так как строка IE7 не включала в себя версию Trident, вы легко можете отличить IE7 от IE8 работающего в режиме совместимости.

## Gecko

Движок рендеринга Gecko это сердце браузера Firefox. Когда Gecko был впервые разработан, он входил в состав браузера Mozilla, который должен был носить имя Netscape 6. Его спецификация была написана под Netscape 6 и в ней указывалось как строка user-agent должна была выглядеть в следующих версиях. В новой версии формат строки разительно отличался от сравнительно простой строки user-agent, использовавшейся до версии 4.4.

Формат был следующим:

<pre><code class="nohighlight">Mozilla/MozillaVersion (Platform; Encryption; OS-or-CPU; Language; PrereleaseVersion)Gecko/GeckoVersion ApplicationProduct/ApplicationProductVersion</code></pre>

Эта удивительно сложная строка включат в себя многое. Чтобы лучше понять формат строки, предлагаем вам рассмотреть строки user-agent взятые из различных браузеров на основе Gecko.

Netscape 6.21 на Windows XP:

<pre><code class="nohighlight">Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:0.9.4) Gecko/20011128 Netscape6/6.2.1</code></pre>

SeaMonkey 1.1a на Linux:

<pre><code class="nohighlight">Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1b2) Gecko/20060823 SeaMonkey/1.1a</code></pre>

Firefox 2.0.0.11 на Windows XP:

<pre><code class="nohighlight">Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.11) Gecko/20071127 Firefox/2.0.0.11</code></pre>

Camino 1.5.1 на Mac OS X:

<pre><code class="nohighlight">Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en; rv:1.8.1.6) Gecko/20070809 Camino/1.5.1</code></pre>

Все эти строки говорят о том, что браузер построен на основе Gecko (хоть они и отличаются версиями). Зачастую название самого браузера не настолько важно, как понимание того, что он построен на основе Gecko.

Mozilla не изменялась с версии 5.0, с того момента, как был выпущен первый браузер на основе Gecko и изменения, скорее всего, произойдут еще не скоро.


## WebKit

В 2003 году компания Apple анонсировала свой собственный веб-браузер под названием Safari. Движок рендеринга WebKit, используемый в Safari, был начат как форк движка KHTML, используемого в Linux браузере Konqueror. Пару лет спустя, WebKit стал самостоятельным проектом с открытым исходным кодом, основной целью которого стало развитие движка.

Разработчики нового браузера и движка столкнулись с проблемой, аналогичной проблеме разработчиков Internet Explorer 3.0: как убедиться в том, что браузер не будет заблокирован популярными сайтами? Ответ был прост, необходимо было поместить в user-agent информацию о том, что браузер совместим с другим популярным браузером. Это привело к появлению строки в следующем формате:

<pre><code class="nohighlight">Mozilla/5.0 (Platform; Encryption; OS-or-CPU; Language) AppleWebKit/AppleWebKitVersion (KHTML, like Gecko) Safari/SafariVersion</code></pre>

Пример

<pre><code class="nohighlight">Mozilla/5.0 (Macintosh; U; PPC Mac OS X; en) AppleWebKit/124 (KHTML, like Gecko) Safari/125.1</code></pre>

Как вы видите, в строке указана не только версия Apple WebKit, но и версия Safari. Все браузеры на основе WebKit  идентифицируют себя как Mozilla 5.0, так же как и все Gecko браузеры.

Версия Safari это обычно номер сборки, который не обязательно соответствует номеру релиза.

<pre><code class="nohighlight">Mozilla/5.0 (Macintosh; U; PPC Mac OS X; en) AppleWebKit/522.15.5 (KHTML, like Gecko) Version/3.0.3 Safari/522.15.5</code></pre>

Наиболее интересной и спорной частью строки является  “(KHTML, like Gecko)”  в версии Safari pre-1.0. Apple встретила большое сопротивление со стороны разработчиков, которые увидели в этом попытку обмануть клиенты и сервера выдавая Safari за Gecko (как будто Mozilla/5.0 было недостаточно). Ответ Apple был похож на слова Microsoft, когда IE попал под удар: Safari совместим с Mozilla и веб-сайты не должны блокировать пользователей Safari только потому, что они используют неподдерживаемый браузер.

Стоит обратить внимание, что данная особенность имеется только в Safari, но не в WebKit, так что другие браузеры на данном движке могут представляться иначе.


## Konqueror

Konqueror — браузер, поставляемый в комплекте с Linux оболочкой KDE, основан на движке KHTML. Хотя браузер доступен только на Linux платформе, он имеет достаточно большое число активных пользователей.

Для наибольшей совместимости konqueror использует строку, основанную на формате IE, следующего формата:

<pre><code class="nohighlight">Mozilla/5.0 (compatible; Konqueror/Version; OS-or-CPU)</code></pre>

Тем не менее Konqueror 3.2 внес в user-agent изменения аналогичные WebKit, обозначающие его как KHTML:

<pre><code class="nohighlight">Mozilla/5.0 (compatible; Konqueror/Version; OS-or-CPU) KHTML/KHTMLVersion (like Gecko)</code></pre>

Пример

<pre><code class="nohighlight">Mozilla/5.0 (compatible; Konqueror/3.5; SunOS) KHTML/3.5.0 (like Gecko)</code></pre>

Номера версий Konqueror и KHTML, как правило, совпадают. Разница может быть подобной:

Konqueror 3.5 с движком KHTML 3.5.1


## Chrome

Google Chrome использует WebKit в качестве движка рендеринга страниц, но использует различные JavaScript движки. Первый бета-релиз Chrome версии 0.2 содержит всю информацию от WebKit, а так же содержит дополнительный раздел Chrome версии.

<pre><code class="nohighlight">Mozilla/5.0 (Platform; Encryption; OS-or-CPU; Language) AppleWebKit/AppleWebKitVersion (KHTML, like Gecko) Chrome/ChromeVersion Safari/SafariVersion</code></pre>

пример строки user-agent для версии Chrome 0.2

<pre><code class="nohighlight">Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/525.13 (KHTML, like Gecko) Chrome/0.2.149.29 Safari/525.13</code></pre>

Есть вероятность что версии WebKit и Safari всегда будут одинаковыми.

## Opera

Один из самых противоречивых браузеров. Однако, строка user-agent, из всех современных браузеров, выглядит здесь самой логичной. До 8-й версии формат строки был следующим:

<pre><code class="nohighlight">Opera/Version (OS-or-CPU; Encryption) [Language]</code></pre>

Если вы использовали Opera 7.54 на Windows XP, то user-agent был следующим:

<pre><code class="nohighlight">Opera/7.54 (Windows NT 5.1; U) [en]</code></pre>

С выходом 8-й версии информация о языковом регионе была перенесена внутрь круглых скобок, для большего соответствия другим браузерам:

<pre><code class="nohighlight">Opera/Version (OS-or-CPU; Encryption; Language)</code></pre>

Opera 8 на Windows XP выдавала следующую строку

<pre><code class="nohighlight">Opera/8.0 (Windows NT 5.1; U; en)</code></pre>

По умолчанию, Opera возвращает user-agent в этом формате. В настоящее время он является единственным из четырех основных браузеров использующих название продукта и версию для полной идентификации. Однако, как и другие браузеры Opera столкнулась с проблемой user-agent. Хоть технически это и правильно, но в интернете достаточно много снифферов браузеров, которые ориентируются прежде всего на имя продукта Mozilla. Существует так же изрядное количество кода, написанного специально для IE или Gecko. Вместо того, чтобы запутывать снифферы путем изменения своей строки user-agent Opera полностью идентифицирует себя как другой браузер. 

В Opera 9 есть два способа изменения User-Agent. Один из способов заключается в представлении браузера как Firefox или IE. При использовании этой опции user-agent начинает выглядеть в соответствии со строкой Firefox или IE с добавлением примечания Opera и номера версии в конце

<pre><code class="nohighlight">Mozilla/5.0 (Windows NT 5.1; U; en; rv:1.8.1) Gecko/20061208 Firefox/2.0.0 Opera 9.50</code></pre>


<pre><code class="nohighlight">Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; en) Opera 9.50</code></pre>

В первом случае браузер представляется как Firefox2, во втором как Internet Explorer 6.

Другой вариант — маскировка браузера как Firefox или IE. Но в этом случае в строке user-agent не появляется ни о браузере Opera, ни о его версии. В данном случае нет никакой возможности определить при помощи user-agent, что используется именно Opera.  Еще больше положение усложняет тенденция Opera к изменению user-agent без уведомления пользователя.

## Вывод

История user-agent рассказывает о том, что браузеры пытаются убедить снифферы определить их теми браузерами, которыми они не являются. Internet Explorer хочет быть идентифицирован как Netscape 4, WebKit и Konqueror представляются как Firefox, Chrome маскируется под Safari. Все это делает определение браузера через user-agent проблематичным (кроме случая с Opera), хотя каждый браузер предоставляет вам возможность отличить его от остальных. Главное запомните, что если браузеры и пытаются обмануть, делают они это для того, чтобы доказать свою совместимость с другими браузерами.

<p><i>Данный материал является переводом статьи: <br>Nicholas C. Zakas <a href="http://www.nczonline.net/blog/2010/01/12/history-of-the-user-agent-string/">History of the user-agent string</a></i></p>