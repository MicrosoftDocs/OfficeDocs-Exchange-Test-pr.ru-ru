---
title: 'Обновление с Exchange 2007 до Exchange 2013: Exchange 2013 Help'
TOCTitle: Обновление с Exchange 2007 до Exchange 2013
ms:assetid: a604b96d-2a51-480f-937f-45ad753c2cad
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ898581(v=EXCHG.150)
ms:contentKeyID: 51408062
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Обновление с Exchange 2007 до Exchange 2013

 

_**Применимо к:**Exchange Online, Exchange Server, Exchange Server 2013_

_**Последнее изменение раздела:**2015-03-09_

Microsoft Exchange Server 2010 и Exchange Server 2007 имеют несколько ролей сервера: Сервер клиентского доступа, сервер почтовых ящиков, транспортный сервер-концентратор, сервер единой системы обмена сообщениями и пограничный транспортный сервер. В Exchange Server 2013 количество ролей сервера было уменьшено с пяти до трех: сервер клиентского доступа, сервер почтовых ящиков и пограничный транспортный сервер. Теперь единая система обмена сообщениями — это компонент голосовых функций в Exchange 2013. (Дополнительные сведения об изменениях см. в разделе "Архитектура Exchange 2013" статьи [Новые возможности в Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md).)

При обновлении имеющейся организации Exchange 2007 до версии Exchange 2013 в ней в течение некоторого времени совместно работают Exchange 2007 и Exchange 2013. Можно работать в этом режиме в течение неопределенного периода времени или немедленно завершить обновление до Exchange 2013 путем перемещения всех ресурсов с серверов Exchange 2007 на сервер Exchange 2013 и последующего списания серверов Exchange 2007. Сценарий сосуществования реализуется при наличии следующих условий:

  - Система Exchange 2013 развернута в существующей организации Exchange.

  - Несколько версий Microsoft Exchange предоставляют для организации службы обмена сообщениями.

Существующую организацию Exchange 2003 нельзя обновить непосредственно до Exchange 2013. Сначала необходимо обновить организацию Exchange 2003 до Exchange 2007 или Exchange 2010, а затем можно обновить организацию Exchange 2007 или Exchange 2010 до Exchange 2013. Мы рекомендуем обновлять организацию от Exchange 2003 до Exchange 2010, а затем — от Exchange 2010 до Exchange 2013.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ983803.warning(EXCHG.150).gif" title="Предупреждение" alt="Предупреждение" />Предупреждение.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Необходимо удалить все экземпляры Exchange 2003 из вашей организации, прежде чем обновлять ее до Exchange 2013.</td>
</tr>
</tbody>
</table>


Можно перенести все ваши почтовые ящики Exchange 2003 в Exchange Online. Больше об этом подходе можно узнать в статье [Способы переноса нескольких записей электронной почты в Office 365](https://go.microsoft.com/fwlink/p/?linkid=524030).

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

## Сосуществование Exchange 2013 и Exchange 2007 с Exchange 2010 в смешанном режиме

При наличии сайтов Active Directory, где установлены версии Exchange 2010 и Exchange 2007, следуйте указаниям по обновлению для Exchange 2010 и Exchange 2007, выполняя действия по обновлению, необходимые для каждой версии.

## Обзор процесса обновления

Чтобы сделать обзор процесса обновления Exchange 2007 до Exchange 2013, в следующей таблице мы собрали ресурсы, связанные с каждой ключевой задачей. Точные пошаговые указания см. в статье [Контрольный список: Обновление с Exchange 2007](checklist-upgrade-from-exchange-2007-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Задача</th>
<th>Раздел</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Сведения о ролях и компонентах Exchange 2013</p></td>
<td><p><a href="what-s-new-in-exchange-2013-exchange-2013-help.md">Новые возможности в Exchange 2013</a></p>
<p><a href="client-access-server-exchange-2013-help.md">Сервер клиентского доступа</a></p>
<p><a href="mailbox-server-exchange-2013-help.md">Сервер почтовых ящиков</a></p>
<p><a href="mail-flow-exchange-2013-help.md">Поток обработки почты</a></p>
<p><a href="unified-messaging-exchange-2013-help.md">Единая система обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p>Установка Exchange 2013</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Установка Exchange 2013 с помощью мастера установки</a></p>
<p><a href="install-the-exchange-2013-edge-transport-role-using-the-setup-wizard-exchange-2013-help.md">Установка роли пограничного транспортного сервера Exchange 2013 с помощью мастера установки</a> (необязательно)</p>
<p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Проверка установки Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Добавление цифровых сертификатов на сервере клиентского доступа</p></td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Конфигурация сервера клиентского доступа Exchange 2013</a></p>
<p><a href="digital-certificates-and-ssl-exchange-2013-help.md">Цифровые сертификаты и протокол SSL</a></p>
<p><a href="create-a-digital-certificate-request-exchange-2013-help.md">Создание запроса на цифровой сертификат</a></p></td>
</tr>
<tr class="even">
<td><p>Настройка виртуальных каталогов, связанных с Exchange</p></td>
<td><p><a href="default-settings-for-exchange-virtual-directories-exchange-2013-help.md">Параметры по умолчанию для виртуальных каталогов Exchange</a></p></td>
</tr>
<tr class="odd">
<td><p>Перемещение почтовых ящиков из Exchange 2010</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Перемещение почтовых ящиков в Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Настройка компонентов транспорта</p></td>
<td><p><a href="edge-subscriptions-exchange-2013-help.md">Пограничные подписки</a> (только если установлен пограничный транспортный сервер)</p>
<p><a href="mail-routing-exchange-2013-help.md">Маршрутизация почты</a></p>
<p><a href="shadow-redundancy-exchange-2013-help.md">Теневая избыточность</a></p>
<p><a href="delivery-reports-for-administrators-exchange-2013-help.md">Отчеты о доставке для администраторов</a></p></td>
</tr>
<tr class="odd">
<td><p>Настройка и развертывание единой системы обмена сообщениями</p></td>
<td><p><a href="planning-for-unified-messaging-exchange-2013-help.md">Планирование единой системы обмена сообщениями</a></p>
<p><a href="deploying-voice-mail-and-um-exchange-2013-help.md">Развертывание голосовой почты и единой системы обмена сообщениями</a></p></td>
</tr>
</tbody>
</table>

