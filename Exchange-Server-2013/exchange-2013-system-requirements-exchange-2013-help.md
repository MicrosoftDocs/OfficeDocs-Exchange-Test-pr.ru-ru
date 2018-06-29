﻿---
title: 'Требования к системе для установки Exchange 2013: Exchange 2013 Help'
TOCTitle: Требования к системе для установки Exchange 2013
ms:assetid: 1e80857c-b870-4a6d-a0f4-ff7b3a7be037
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa996719(v=EXCHG.150)
ms:contentKeyID: 50487593
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Требования к системе для установки Exchange 2013

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2016-12-09_

Узнайте о требованиях для установки Exchange 2013, в том числе требованиях к оборудованию, сети и операционной системе.

Перед установкой сервера Microsoft Exchange Server 2013 рекомендуется ознакомиться с данным разделом, чтобы убедиться в соответствии сети, оборудования, программного обеспечения, клиентов и других элементов требованиям Exchange 2013. При этом следует ознакомиться со сценариями сосуществования, поддерживаемыми для Exchange 2013 и более ранних версий Exchange.

## Поддерживаемые сценарии сосуществования

В следующей таблице перечислены сценарии, поддерживающие совместную работу Exchange 2013 и более ранних версий Exchange.

### Совместная работа Exchange 2013 и более ранних версий Exchange Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Версия Exchange</th>
<th>Сосуществование организации Exchange</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange Server 2003 и более ранние версии</p></td>
<td><p>Не поддерживается</p></td>
</tr>
<tr class="even">
<td><p>Exchange 2007</p></td>
<td><p>Поддерживается в следующих минимальных версиях Exchange:</p>
<ul>
<li><p>1 Накопительный пакет обновления 10 для Exchange 2007 с пакетом обновления 3 (SP3) на всех серверах Exchange 2007 в организации, включая пограничные транспортные серверы.</p></li>
<li><p>Exchange 2013 с накопительным пакетом обновления 2 (CU2) или более поздней версии на все серверы Exchange 2013 в организации.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Exchange 2010</p></td>
<td><p>Поддерживается в следующих минимальных версиях Exchange:</p>
<ul>
<li><p>2 Exchange 2010 с пакетом обновления 3 (SP3) на все серверы Exchange 2010 в организации, включая пограничные транспортные серверы.</p></li>
<li><p>Exchange 2013 с накопительным пакетом обновления 2 (CU2) или более поздней версии на все серверы Exchange 2013 в организации.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Смешанная организация Exchange 2010 и Exchange 2007</p></td>
<td><p>Поддерживается в следующих минимальных версиях Exchange:</p>
<ul>
<li><p>1 Накопительный пакет обновления 10 для Exchange 2007 с пакетом обновления 3 (SP3) на все серверы Exchange 2007 в организации, включая пограничные транспортные серверы.</p></li>
<li><p>2 Exchange 2010 с пакетом обновления 3 (SP3) на все серверы Exchange 2010 в организации, включая пограничные транспортные серверы.</p></li>
<li><p>Exchange 2013 с накопительным пакетом обновления 2 (CU2) или более поздней версии на все серверы Exchange 2013 в организации.</p></li>
</ul></td>
</tr>
</tbody>
</table>


1 Если вы хотите создать подписку EdgeSync между транспортным сервером-концентратором Exchange 2007 и пограничным транспортным сервером Exchange 2013 с пакетом обновления 1 (SP1), необходимо установить накопительный пакет обновления 13 для Exchange 2007 с пакетом обновления 3 (SP3) или более поздней версии на транспортном сервере-концентраторе Exchange 2007.

2 Если вы хотите создать подписку EdgeSync между транспортным сервером-концентратором Exchange 2010 и пограничным транспортным сервером Exchange 2013 с пакетом обновления 1 (SP1), необходимо установить накопительный пакет обновления 5 для Exchange 2010 с пакетом обновления 3 (SP3) или более поздней версии на транспортном сервере-концентраторе Exchange 2010.

## Поддерживаемые сценарии гибридных развертываний

Exchange 2013 поддерживает гибридные развертывания с клиентами Office 365, которые были обновлены до последней версии Office 365. Дополнительные сведения о гибридных развертываниях см. в разделе [Предварительные условия для гибридного развертывания](https://technet.microsoft.com/ru-ru/library/hh534377\(v=exchg.150\)).

## Сеть и серверы каталогов

В приведенной ниже таблице описаны требования, предъявляемые к сети и серверам каталогов в организации Exchange 2013.

**Требования к сети и серверам каталогов для Exchange 2013**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Компонент</th>
<th>Требования</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Хозяин схемы</p></td>
<td><p>По умолчанию хозяин схемы работает на первом контроллере домена Active Directory, установленном в лесу. Хозяин схемы должен выполняться на одном из указанных ниже серверов.</p>
<ul>
<li><p>Windows Server 2012 R2 Standard или Datacenter1</p></li>
<li><p>Windows Server 2012 Standard или Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard или Enterprise</p></li>
<li><p>Окончательная первоначальная версия (RTM) Windows Server 2008 R2 Datacenter или более поздней версии</p></li>
<li><p>Windows Server 2008 Standard или Enterprise (32- или 64-разрядная версия)</p></li>
<li><p>Окончательная первоначальная версия (RTM) Windows Server 2008 Datacenter или более поздней версии</p></li>
<li><p>Windows Server 2003 Standard Edition с пакетом обновления 2 (SP2) или более поздняя версия (32- или 64-разрядная)</p></li>
<li><p>Windows Server 2003 Enterprise Edition с пакетом обновления 2 (SP2) или более поздняя версия (32- или 64-разрядная)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Сервер глобального каталога</p></td>
<td><p>Для каждого сайта Active Directory, где вы планируете установить Exchange 2013, должен быть хотя бы один сервер глобального каталога, работающий под управлением одной из указанных ниже систем.</p>
<ul>
<li><p>Windows Server 2012 R2 Standard или Datacenter1</p></li>
<li><p>Windows Server 2012 Standard или Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard или Enterprise</p></li>
<li><p>Окончательная первоначальная версия (RTM) Windows Server 2008 R2 Datacenter или более поздней версии</p></li>
<li><p>Windows Server 2008 Standard или Enterprise (32- или 64-разрядная версия)</p></li>
<li><p>Окончательная первоначальная версия (RTM) Windows Server 2008 Datacenter или более поздней версии</p></li>
<li><p>Windows Server 2003 Standard Edition с пакетом обновления 2 (SP2) или более поздняя версия (32- или 64-разрядная)</p></li>
<li><p>Windows Server 2003 Enterprise Edition с пакетом обновления 2 (SP2) или более поздняя версия (32- или 64-разрядная)</p></li>
</ul>
<p>Дополнительные сведения о серверах глобального каталога см. в статье <a href="http://go.microsoft.com/fwlink/p/?linkid=178996">Что такое глобальный каталог</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Контроллер домена</p></td>
<td><p>Для каждого сайта Active Directory, где вы планируете установить Exchange 2013, должен быть хотя бы один контроллер домена, доступный для записи и работающий под управлением одной из указанных ниже систем.</p>
<ul>
<li><p>Windows Server 2012 R2 Standard или Datacenter1</p></li>
<li><p>Windows Server 2012 Standard или Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard или Enterprise с пакетом обновления 1 (SP1) или более поздняя версия</p></li>
<li><p>Окончательная первоначальная версия (RTM) Windows Server 2008 R2 Datacenter или более поздней версии</p></li>
<li><p>Windows Server 2008 Standard или Enterprise с пакетом обновления 1 (SP1) или более поздняя версия (32- или 64-разрядная)</p></li>
<li><p>Окончательная первоначальная версия (RTM) Windows Server 2008 Datacenter или более поздней версии</p></li>
<li><p>Windows Server 2003 Standard Edition с пакетом обновления 2 (SP2) или более поздняя версия (32- или 64-разрядная)</p></li>
<li><p>Windows Server 2003 Enterprise Edition с пакетом обновления 2 (SP2) или более поздняя версия (32- или 64-разрядная)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Лес Active Directory</p></td>
<td><p>Сервер Active Directory должен находиться в режиме функциональности леса Windows Server 2003 или более поздней версии2.</p></td>
</tr>
<tr class="odd">
<td><p>Поддержка пространства имен DNS</p></td>
<td><p>Exchange 2013 поддерживает следующие пространства имен для службы доменных имен (DNS).</p>
<ul>
<li><p>Смежные</p></li>
<li><p>Несмежные</p></li>
<li><p>Одноуровневые домены</p></li>
<li><p>Несвязанные</p></li>
</ul>
<p>Дополнительные сведения о пространствах имен DNS, которые поддерживаются в Exchange, см. в статье 2269838 базы знаний Майкрософт <a href="http://go.microsoft.com/fwlink/?linkid=3052%26kbid=2269838">Совместимость Microsoft Exchange с одноуровневыми, несвязанными и несмежными пространствами имен</a>.</p></td>
</tr>
<tr class="even">
<td><p>Поддержка IPv6</p></td>
<td><p>В Exchange 2013 IPv6 поддерживается, только если установлен и включен IPv4. Если служба Exchange 2013 развернута в этой конфигурации и сеть поддерживает IPv4 и IPv6, все серверы Exchange могут обмениваться данными с устройствами, серверами и клиентами, использующими IPv6-адреса. Дополнительные сведения см. в статье <a href="ipv6-support-in-exchange-2013-exchange-2013-help.md">Поддержка протокола IPv6 в Exchange 2013</a>.</p></td>
</tr>
</tbody>
</table>


1 Windows Server 2012 R2 поддерживается только в Exchange 2013 с пакетом обновления 1 (SP1) и более поздних версий.

2 Режим функциональности леса Windows Server 2012 R2 поддерживается только в Exchange 2013 с пакетом обновления 1 (SP1) и более поздних версий.

## Архитектура сервера каталогов

Использование 64-разрядных контроллеров доменов Active Directory повышает производительность службы каталогов для сервера Exchange 2013.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В средах с несколькими доменами на контроллерах домена Windows Server 2008, на которых установлен японский язык Active Directory, серверы могут не получать некоторые атрибуты, которые хранятся на объекте во время входящей репликации. Дополнительные сведения см. в статье 949189 базы знаний Майкрософт <a href="http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=949189">Контроллер домена Windows Server 2008, настроенный в языковом стандарте японского языка, может не применять обновления атрибутов в объекте во время входящей репликации</a>.</td>
</tr>
</tbody>
</table>


## Установка Exchange Server 2013 на серверы каталогов

По соображениям безопасности и производительности рекомендуется устанавливать Exchange 2013 только на рядовые серверы, а не на серверы каталогов Active Directory. Тем не менее программу DCPromo нельзя запускать на компьютере под управлением Exchange 2013. После установки сервера Exchange 2013 изменить его роль с рядового сервера на сервер каталогов или наоборот нельзя.

## Оборудование

Рекомендуемые требования к оборудованию для серверов Exchange 2013 зависят от ряда факторов, включая установленные роли сервера и ожидаемые нагрузки на серверы.

Подробные сведения о выборе правильного размера и настройке развертывания см. в разделе [Рекомендации по выбору размера развертывания Exchange 2013 и его настройке](exchange-2013-sizing-and-configuration-recommendations-exchange-2013-help.md).

Сведения о развертывании Exchange в виртуализированной среде см. в разделе [Виртуализация Exchange 2013](exchange-2013-virtualization-exchange-2013-help.md).

**Требования к оборудованию для Exchange 2013**


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Компонент</th>
<th>Требования</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Процессор</p></td>
<td><ul>
<li><p>Компьютер на базе процессора Intel с архитектурой x64, поддерживающий технологию Intel 64 (прежнее название — Intel EM64T)</p></li>
<li><p>Процессор AMD, поддерживающий платформу AMD64</p></li>
<li><p>Процессоры Intel Itanium IA64 не поддерживаются</p></li>
</ul></td>
<td><p>Список поддерживаемых операционных систем см. далее в разделе &quot;Операционная система&quot;.</p></td>
</tr>
<tr class="even">
<td><p>Память</p></td>
<td><p>Зависит от установленных ролей Exchange:</p>
<ul>
<li><p><strong>Почтовый ящик</strong> — минимум 8 ГБ</p></li>
<li><p><strong>Клиентский доступ</strong> — минимум 4 ГБ</p></li>
<li><p><strong>Сочетание почтовых ящиков и клиентского доступа</strong> — минимум 8 ГБ</p></li>
<li><p><strong>Пограничный транспорт</strong> — минимум 4 ГБ</p></li>
</ul></td>
<td><p>Нет.</p></td>
</tr>
<tr class="odd">
<td><p>Размер файла подкачки</p></td>
<td><p>Минимальный и максимальный размер файла подкачки должны быть равны объему физической памяти плюс 10 МБ, при этом максимальный предел равен 32 778 МБ, если вы используете более 32 ГБ ОЗУ.</p></td>
<td><p>Подробные рекомендации по работе с файлом подкачки см. в разделе &quot;Файл подкачки&quot; статьи <a href="exchange-2013-sizing-and-configuration-recommendations-exchange-2013-help.md">Рекомендации по выбору размера развертывания Exchange 2013 и его настройке</a>.</p></td>
</tr>
<tr class="even">
<td><p>Дисковое пространство</p></td>
<td><ul>
<li><p>Не менее 30 ГБ свободного места на диске, на который устанавливается Exchange</p></li>
<li><p>Дополнительные 500 МБ свободного места на диске для каждого языкового пакета единой системы обмена сообщениями, который планируется установить</p></li>
<li><p>200 МБ свободного места на системном диске</p></li>
<li><p>Жесткий диск, на котором сохраняется база данных очереди сообщений, с не менее 500 МБ свободного пространства.</p></li>
</ul></td>
<td><p>Подробные рекомендации по выбору хранилищ см. в статье <a href="exchange-2013-storage-configuration-options-exchange-2013-help.md">Параметры конфигурации хранилища Exchange 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Дисковод</p></td>
<td><p>Устройство чтения DVD-дисков, доступное локально или через сеть</p></td>
<td><p>Нет.</p></td>
</tr>
<tr class="even">
<td><p>Разрешение экрана</p></td>
<td><p>1024 x 768 пикселей или выше</p></td>
<td><p>Нет.</p></td>
</tr>
<tr class="odd">
<td><p>Формат файлов</p></td>
<td><p>Следующие разделы диска должны быть отформатированы как NTFS:</p>
<ul>
<li><p>системный раздел;</p></li>
<li><p>разделы, на которых хранятся двоичные файлы Exchange или файлы, созданные при ведении журнала диагностики Exchange.</p></li>
</ul>
<p>Разделы диска, содержащие следующие типы файлов, могут быть отформатированы как ReFS:</p>
<ul>
<li><p>Разделы, содержащие файлы журнала транзакций</p></li>
<li><p>разделы, содержащие файлы баз данных;</p></li>
<li><p>разделы, содержащие файлы индексирования содержимого.</p></li>
</ul></td>
<td><p>Нет.</p></td>
</tr>
</tbody>
</table>


## Операционная система

В следующей таблице перечислены поддерживаемые операционные системы для Exchange 2013.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Установка Exchange 2013 на компьютере, работающем в режиме Windows Server Core, не поддерживается. На компьютере должна выполняться полная установка Windows Server. Чтобы установить Exchange 2013 на компьютере, работающем в режиме Windows Server Core, сначала необходимо преобразовать сервер в полную установку Windows Server, выполнив одно из следующих действий.
<ul>
<li><p><strong>Windows Server 2008 R2</strong>. Переустановить Windows Server и выбрать параметр <strong>Полная установка</strong>.</p></li>
<li><p><strong>Windows Server 2012 R2</strong> или <strong>Windows Server 2012</strong>. Преобразовать сервер, работающий в режиме Windows Server Core, в полную установку, выполнив указанную ниже команду.</p>
<pre><code>Install-WindowsFeature Server-Gui-Mgmt-Infra, Server-Gui-Shell -Restart</code></pre></li>
</ul></td>
</tr>
</tbody>
</table>


**Поддерживаемые операционные системы для Exchange 2013**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Компонент</th>
<th>Требования</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Роли серверов почтовых ящиков, серверов клиентского доступа и пограничных транспортных серверов</p></td>
<td><p>Один из следующих пунктов.</p>
<ul>
<li><p>Windows Server 2012 R2 Standard или Datacenter1</p></li>
<li><p>Windows Server 2012 Standard или Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard с пакетом обновления 1 (SP1)</p></li>
<li><p>Windows Server 2008 R2 Enterprise с пакетом обновления 1 (SP1)</p></li>
<li><p>Windows Server 2008 R2 Datacenter RTM или более поздней версии</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Средства управления</p></td>
<td><p>Один из следующих пунктов.</p>
<ul>
<li><p>Windows Server 2012 R2 Standard или Datacenter1</p></li>
<li><p>Windows Server 2012 Standard или Datacenter</p></li>
<li><p>Windows Server 2008 R2 Standard с пакетом обновления 1</p></li>
<li><p>Windows Server 2008 R2 Enterprise с пакетом обновления 1</p></li>
<li><p>Windows Server 2008 R2 Datacenter RTM или более поздней версии</p></li>
<li><p>64-разрядный выпуск Windows 8.12</p></li>
<li><p>64-разрядный выпуск Windows 8;</p></li>
<li><p>64-разрядный выпуск Windows 7 с пакетом обновления 1 (SP1)</p></li>
</ul></td>
</tr>
</tbody>
</table>


1 Windows Server 2012 R2 поддерживается только для Exchange 2013 с пакетом обновления 1 (SP1) или более поздних версий.

2 Windows 8.1 поддерживается только для Exchange 2013 с пакетом обновления 1 (SP1) или более поздних версий.

**Поддерживаемые версии Windows Management Framework для Exchange 2013**

Exchange 2013 поддерживает только версию Windows Management Framework, встроенную в выпуск Windows, где вы устанавливаете Exchange. Не устанавливайте на серверах с Exchange те версии Windows Management Framework, которые доступны как отдельные файлы для скачивания.

## Платформа .NET Framework

Мы настоятельно рекомендуем использовать последнюю версию .NET Framework, поддерживаемую версией Exchange, которую вы собираетесь установить.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Версия Exchange</th>
<th>.NET Framework 4.7.1</th>
<th>.NET Framework 4.6.2</th>
<th>.NET Framework 4.6.1</th>
<th>.NET Framework 4.5.2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange 2013 CU19</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange 2013 CU16 - CU18</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Поддерживаемые клиенты

Exchange 2013 поддерживает следующие версии Outlook и Entourage для Mac:

  - Outlook 2016

  - Outlook 2013

  - Outlook 2010

  - Outlook 2007

  - Entourage 2008 для Mac, Web Services Edition

  - Outlook для Mac в Office 365

  - Outlook для Mac 2011

Список выпусков Outlook, поддерживаемых Exchange, см. в статье [Обновления Outlook](https://go.microsoft.com/fwlink/p/?linkid=513459).

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Настоятельно рекомендуется установить последние доступные обновления и пакеты обновлений, чтобы подключение к Exchange было максимально эффективным.</td>
</tr>
</tbody>
</table>


Клиенты Outlook версии ранее Outlook 2007 не поддерживаются. Почтовые клиенты в операционных системах Mac, которым требуется DAV, например Entourage 2008 для Mac RTM и Entourage 2004, не поддерживаются.

Outlook Web App поддерживает несколько браузеров в различных операционных системах и устройствах. Подробные сведения см. в статье [Новые возможности Outlook Web App в Exchange 2013](what-s-new-for-outlook-web-app-in-exchange-2013-exchange-2013-help.md).

