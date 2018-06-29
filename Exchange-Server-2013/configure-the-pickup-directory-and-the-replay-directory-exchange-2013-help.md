﻿---
title: 'Настройка каталогов раскладки и преобразования: Exchange 2013 Help'
TOCTitle: Настройка каталогов раскладки и преобразования
ms:assetid: c9ca7358-9a08-4f57-89d0-910e4438df8a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124549(v=EXCHG.150)
ms:contentKeyID: 50489208
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка каталогов раскладки и преобразования

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-04-08_

Каталоги раскладки и преобразования используются транспортной службой на серверах почтовых ящиков и пограничных транспортных серверах для добавления файлов сообщений непосредственно на транспортный конвейер. Правильно отформатированные файлы сообщений электронной почты, скопированные в каталоги раскладки или преобразования, отправляются на доставку. Каталог раскладки используется администраторами для проверки потока сообщений или приложениями, которые создают и отправляют собственные сообщения. Каталог преобразования получает сообщения от серверов, не являющихся шлюзами SMTP, и повторно передает сообщения, экспортированные из очередей серверов Microsoft Exchange.

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 15 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Служба транспорта" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - Значение параметра *PickupDirectoryMaxMessagesPerMinute* в командлете **Set-TransportService** используется каталогами раскладки и преобразования.

  - При изменении расположения каталогов раскладки и преобразования существующие файлы сообщений не копируются из старого местоположения в новое. Новое местонахождение каталога раскладки или преобразования становится действительным почти сразу же после изменения конфигурации, но все существующие файлы сообщений остаются в старом местоположении.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Необходимые действия

## Использование командной консоли для настраивания каталога раскладки

Для настраивания каталога раскладки используется указанный ниже синтаксис.

    Set-TransportService <ServerIdentity> -PickupDirectoryPath <LocalFilePath> -PickupDirectoryMaxHeaderSize <Size> -PickupDirectoryMaxRecipientsPerMessage <Integer> -PickupDirectoryMaxMessagesPerMinute <Integer>

В этом примере в каталог раскладки на сервере почтовых ящиков с именем Exchange01 вносятся следующие изменения.

  - Для местоположения каталога раскладки указан путь D:\\Pickup Directory.

  - Максимальный размер заголовка сообщений в файле сообщения увеличен до 96 КБ.

  - Максимальное количество получателей для файла сообщения увеличено до 250.

  - Максимальная скорость обработки сообщений для каталогов раскладки и преобразования увеличивается до 200 сообщений в минуту.

<!-- end list -->

    Set-TransportService Exchange01 -PickupDirectoryPath "D:\Pickup Directory" -PickupDirectoryMaxHeaderSize 96KB -PickupDirectoryMaxRecipientsPerMessage 250 -PickupDirectoryMaxMessagesPerMinute 200

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>Установка для параметра <em>PickupDirectoryPath</em> значения <code>$null</code> отключает использование каталога раскладки.</p></li>
<li><p>Для параметров <em>PickupDirectoryPath</em> и <em>ReplayDirectoryPath</em> запрещается указывать один каталог.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Использование командной консоли для настройки каталога преобразования

Для настройки каталога преобразования используется указанный ниже синтаксис.

    Set-TransportService <ServerIdentity> -ReplayDirectoryPath "C:\Replay Directory" <LocalFilePath> -PickupDirectoryMaxMessagesPerMinute <Integer>

В этом примере в каталог преобразования на сервере почтовых ящиков с именем Exchange01 вносятся следующие изменения.

  - Для местоположения каталога преобразования указан путь D:\\Replay Directory.

  - Максимальная скорость обработки сообщений для каталогов раскладки и преобразования увеличивается до 200 сообщений в минуту.

<!-- end list -->

    Set-TransportService Exchange01 -ReplayDirectoryPath "D:\Replay Directory" -PickupDirectoryMaxMessagesPerMinute 200

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>Установка для параметра <em>ReplayDirectoryPath</em> значения <code>$null</code> отключает использование каталога преобразования.</p></li>
<li><p>Для параметров <em>PickupDirectoryPath</em> и <em>ReplayDirectoryPath</em> запрещается указывать один каталог.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Как проверить, что все получилось?

Для проверки правильности конфигурации каталогов раскладки и преобразования выполните следующие действия:

1.  Выполните следующую команду:
    
        Get-TransportService <ServerIdentity> | Format-List Pickup*,Replay*

2.  Убедитесь, что отображаются значения, которые вы настроили.

