﻿---
title: 'Создание темы для приложения Outlook Web App: Exchange 2013 Help'
TOCTitle: Создание темы для приложения Outlook Web App
ms:assetid: 7e1fa13c-3de3-45c2-b1fa-e74fc8487bda
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb201700(v=EXCHG.150)
ms:contentKeyID: 54652125
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Создание темы для приложения Outlook Web App

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

*Тема* определяет цвет фона, шрифты, цвета выделения, значки и заголовок, используемые МайкрософтOutlook Web App. Каждая тема представляет собой набор файлов мультимедиа и каскадных таблиц стилей (CSS-файлов), которые хранятся на сервере МайкрософтExchange в каталоге установки в папке \\Client Access\\OWA\\prem\\*version*\\resources\\themes. Каждая тема хранится в собственном подкаталоге папки themes.

Тема по умолчанию находится в папке \\Client Access\\OWA\\prem\\*version*\\resources\\themes\\base. Папка каждой темы содержит все необходимые файлы. Это CSS-файлы, графические файлы и XML-файл, определяющий имя темы. Дополнительные темы создаются путем копирования всех файлов одной из тем в новую папку и внесения в них необходимых изменений.

При установке Exchange Server 2013 по умолчанию устанавливается несколько тем.

  - CSS-файлы определяют цвета, градиентные заливки и шрифты.

  - Файлы изображений (PNG) содержат значки и другие графические элементы. При изменении значков не изменяйте их размер. При изменении размера графических элементов убедитесь, что измененные элементы подходят друг к другу.

Эти файлы хранятся на сервере клиентского доступа в каталоге установки в папке \\Client Access\\OWA\\prem\\*\<version\>*\\resources\\themes. Каждая тема хранится в подкаталоге папки themes. Дополнительные темы создаются путем копирования существующей темы и изменения копии.

После создания темы можно также выполнить следующие действия: [Настройка страниц ошибок, входа и выбора языка в Outlook Web App](customize-the-outlook-web-app-sign-in-language-selection-and-error-pages-exchange-2013-help.md).

> [!NOTE]  
> Облегченная версия Outlook Web App не поддерживает темы.


> [!CAUTION]  
> При наличии нескольких серверов, которые поддерживают Outlook Web App, необходимо скопировать настраиваемую тему на каждый из них. Кроме того, следует создать резервную копию настраиваемой темы. При переустановке или обновлении Exchange все файлы в папках тем перезаписываются. После окончания процедуры переустановки или обновления нужно снова скопировать тему в соответствующую папку.<br />
Перед созданием настраиваемой темы создайте резервные копии всех файлов, которые будут изменены.


## Что нужно знать перед началом работы

  - Предполагаемое время выполнения задачи: 60 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Виртуальные каталоги Outlook Web App" в разделе [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур требуются права администратора на доступ к локальному серверу.

  - Вам понадобится текстовый редактор для изменения цвета по умолчанию и графический редактор для изменения изображения. Если не удается найти совпадения для его в [Таблице цветов](https://go.microsoft.com/fwlink/p/?linkid=280679)должно соответствовать определенным цвет, можно использовать средства изменения изображения для образца цвета и определите его значение HTML RGB.

  - Каждый раз при создании или изменении темы Outlook Web App рекомендуется следовать приведенным ниже рекомендациям.
    
      - Если необходимо изменить существующую тему, создайте резервные копии исходных файлов, прежде чем приступить к их изменению.
    
      - Не удаляйте папку \\Client Access\\OWA\\prem\\*version*\\resources\\themes\\base и файлы в ней.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Как это сделать

## Действие 1. Создание новой темы Outlook Web App

Создайте папку для новой темы и скопируйте в нее файлы из существующей темы.

1.  Войдите на сервер Exchange, на котором размещается виртуальный каталог Outlook Web App, с учетной записью, которой делегировано членство в локальной группе администраторов.

2.  Откройте проводник Windows и перейдите к каталогу установки сервера Exchange.

3.  Создайте в папке \\Client Access\\OWA\\prem\\*version*\\resources\\themes новую папку и назовите ее, например, "Fourth Coffee".

4.  Скопируйте в новую папку все файлы из другой темы.

## Действие 2. Присвойте имя новой теме.

Чтобы назначить отображаемое имя для новой темы, выполните следующие действия.

1.  Откройте копию файла themeinfo.xml в папке настраиваемой темы, которую вы создали.

2.  Найдите значение `displayname` и измените его на требуемое имя темы. Пример: `displayname = "Fourth Coffee Theme"`.

3.  Сохраните и закройте файл themeinfo.xml.

## Действие 3. Измените порядок сортировки новой темы (необязательно).

При необходимости можно изменить порядок сортировки новой темы посредством изменения файла themeinfo.xml. Порядок сортировки определяет расположение темы на панели **Изменить тему** в меню «Параметры».

Чтобы изменить порядок сортировки новой темы с помощью файла themeinfo.xml, выполните следующие действия.

1.  Откройте копию файла themeinfo.xml в папке настраиваемой темы.

2.  Найдите значение `sortorder` и измените его в соответствии с требуемым расположением новой темы в списке. Темы будут отсортированы в порядке возрастания числового значения. По умолчанию на первом месте списка находится базовая тема, у которой параметр `sortorder` имеет значение 0. Пример: `sortorder="<number>"`.

3.  Сохраните и закройте файл themeinfo.xml.

## Действие 4. Измените новую тему.

После копирования всех файлов и назначения имени для темы вы можете настроить ее. В теме Outlook Web App можно настроить следующие элементы.

  - Файлы изображений, которые определяют область заголовка и значки.

  - Файлы CSS, которые определяют шрифты и цвета.

## Файлы изображений

Изображения темы хранятся в двух папках в каталоге \\themes*\\\<имя темы\>*\\images\\. В папке \\images\\0 находятся изображения, которые будут использоваться для языков с письмом слева направо (например, для русского языка), а для языков с письмом справа налево будут использоваться изображения из папки \\images\\rtl.

> [!NOTE]  
> Некоторые изображения в папках \images\rtl и \images\0 совпадают, но являются зеркально отраженными.


Для настройки темы можно использовать графический редактор, в котором можно открыть и изменить следующие изображения.

  - Headerbgmain.png
    
      - Это основное изображение заголовка. Рекомендуется, чтобы высота изображения заголовка не превышала 30 пикселей. В теме по умолчанию не используется фоновое изображение, поэтому это изображение прозрачное. Пример темы с настраиваемым фоновым изображением см. в папке темы **Blueprint**.

  - Headerbgright.png
    
      - Это мозаичное изображение за заголовком. В теме по умолчанию не используется мозаичное фоновое изображение, поэтому это изображение прозрачное. Пример темы с настраиваемым мозаичным фоновым изображением см. в папке темы **Blueprint**.

  - sprite1.mouse.png
    
      - Этот файл содержит большинство изображений, используемых в теме. Вы можете изменить цвет изображений в соответствии со своей темой, а также изменить стандартный текстовый логотип Outlook Web App.
    
      - Чтобы избежать ошибок, не изменяйте размер отдельных значков в спрайте и сохраните его в виде прозрачного PNG-файла.

  - themepreview.png
    
      - Это изображение будет использоваться для представления темы на панели **Изменить тему** в меню «Параметры» в Outlook Web App.

## Цвета и шрифты

Файлы каскадных таблиц стилей (CSS) определяют цвета и шрифты, используемые в теме. Они хранятся в нескольких папках в каталоге \\themes\\*\<имя темы\>*. В папке \\*\<имя темы\>*\\0 находятся CSS-файлы, которые будут использоваться для языков с письмом слева направо (например, для русского языка), а для языков с письмом справа налево будут использоваться CSS-файлы из папки \\*\<имя темы\>*\\rtl. Также существуют папки для конкретных языков (например, \\ja, \\ko, \\zhs и \\zht), в которых находятся CSS-файлы для соответствующих языков.

Сначала измените папку \\*\<theme name\>*\\images\\0. В каждой теме используются четыре цвета, которые можно изменить.

  - BrandColor: \#0072C6

  - NavBarHoverColor: \#4C9CD7

  - UnreadColor: \#2A8DD4

  - FocusColor: \#DFEDFA

Вы можете использовать текстовый редактор, например Блокнот, для поиска и замены всех экземпляров этих значений на цвета вашей темы в следующих двух файлах: owa2styles.mouseCSS и owa2styles2.mouseCSS. Эти изменения необходимо выполнить в каждой папке новой темы, где находятся эти CSS-файлы.

## Действие 5. Установка темы по умолчанию в приложении Outlook Web App

Настройка новой темы по умолчанию затронет только тех пользователей, которые не изменили свою тему в меню «Параметры» в Outlook Web App.

Чтобы принудительно установить тему по умолчанию для всех пользователей, необходимо также отключить возможность выбора темы.

## Использование командной консоли для установки темы по умолчанию для приложения Outlook Web App

В этом примере устанавливается тема по умолчанию для Outlook Web App, в которой используется имя сервера `fourthcoffee`, имя виртуального каталога `owa` и имя веб-сайта `default web site`, а сама тема расположена в папке `Custom`.
```powershell
    set-owavirtualdirectory -identity "fourthcoffee\owa (default web site)" -defaulttheme Custom 
```
Подробные сведения о синтаксисе и параметрах см. в разделе [Set-OwaVirtualDirectory](https://technet.microsoft.com/ru-ru/library/bb123515\(v=exchg.150\)).

## Отключение возможности выбора темы для Outlook Web App с помощью командной консоли

В этом примере отключается выбор темы для Outlook Web App, в которой используется имя сервера `fourthcoffee`, имя виртуального каталога `owa` и имя веб-сайта `default web site`.
```powershell
    set-owavirtualdirectory -identity "fourthcoffee\owa (default web site)" -themeselectionenabled $false 
```
Также можно выполнить обе команды одновременно, как показано в следующем примере:
```powershell
    set-owavirtualdirectory -identity "fourthcoffee\owa (default web site)" -defaulttheme Custom -themeselectionenabled $false
```
Подробные сведения о синтаксисе и параметрах см. в разделе [Set-OwaVirtualDirectory](https://technet.microsoft.com/ru-ru/library/bb123515\(v=exchg.150\)).

## Действие 6. Выполните команду iisreset/noforce, чтобы сохранить изменения.

При добавлении или изменении темы, а также изменении имени или порядка сортировки темы, необходимо остановить и перезапустить службы IIS, чтобы изменения вступили в силу. Для этого откройте окно командной строки на сервере, где создавалась новая тема, и выполните команду **iisresest /nforce**.

## Как проверить, что это работает?

1.  Войдите в Outlook Web App, используя виртуальный каталог на сервере, где создавалась новая тема. Если вы проверяете изменения для веб-сайта по умолчанию на сервере Exchange, где размещается виртуальный каталог Outlook Web App, откройте Internet Explorer и введите URL-адрес https://localhost/owa.

2.  Чтобы переключиться на настраиваемую тему, выберите команду меню «Параметры» \> **Изменить тему**, а затем выберите свою тему.

## Если вы видите, что последние изменения не применены, выполните команду iisreset/noforce.

1.  На панели инструментов Internet Explorer выберите команду меню «Параметры» \> **Свойства браузера**.

2.  На вкладке **Общие** в разделе **Журнал браузера** выберите команду **Удалить** и установите флажок **Временные файлы Интернета и файлы веб-сайта**. Затем выберите команду **Удалить**, чтобы удалить эти файлы.

3.  Нажмите кнопку **ОК**, чтобы закрыть окно **Свойства браузера**.

4.  Нажмите кнопку **Обновить**, чтобы увидеть изменения.

Возможно, эти действия придется повторять при каждом изменении темы, чтобы они вступили в силу. Если вы вносите несколько изменений, то можете оставить Outlook Web App открытым, повторить команду **iisreset/noforce** на сервере и удалить временные файлы из Internet Explorer, если это необходимо.

