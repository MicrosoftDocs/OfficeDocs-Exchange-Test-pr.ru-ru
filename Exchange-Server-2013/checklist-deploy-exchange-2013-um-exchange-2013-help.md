---
title: 'Справка по Exchange 2013: развертывание UM Exchange 2013'
TOCTitle: 'Контрольный список: Развертывание единой системы обмена сообщениями Exchange 2013'
ms:assetid: 41b666a2-0d0d-471f-90a3-07c3c562af85
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ673520(v=EXCHG.150)
ms:contentKeyID: 52061223
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Контрольный список: Развертывание единой системы обмена сообщениями Exchange 2013

 

_**Применимо к:** Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2015-03-09_

Этот контрольный список используется для установки и развертывания единой системы обмена сообщениями в организации.

Перед началом работы со списком убедитесь, что вы ознакомились с общими концепциями, изложенными в разделах:

  - [Единая система обмена сообщениями](unified-messaging-exchange-2013-help.md)

  - [Новые функции голосовой почты](new-voice-mail-features-exchange-2013-help.md)

  - [Планирование единой системы обмена сообщениями](planning-for-unified-messaging-exchange-2013-help.md)

Пошаговое руководство по развертыванию единой системы обмена сообщениями и Microsoft Lync Server см. в разделе [Контрольный список: Интеграция единой системы обмена сообщениями Exchange 2013 с сервером Lync](checklist-integrate-exchange-2013-um-with-lync-server-exchange-2013-help.md).

## Контрольный список для развертывания единой системы обмена сообщениями


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Готово?</th>
<th>Tasks</th>
<th>Раздел</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Разверните и настройте компоненты телефонии.</p></td>
<td><p><a href="connect-um-to-your-telephone-system-exchange-2013-help.md">Подключение к телефонной системе единой системы обмена СООБЩЕНИЯМИ</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Перед установкой Exchange 2013 изучите требования к системе.</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Требования к системе для установки Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Проверьте предварительные требования к установке.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Предварительные требования для Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Установите требуемые серверы клиентского доступа и почтовых ящиков.</p>

> [!WARNING]  
> Необходимо выполнить развертывание как минимум одного сервера почтовых ящиков Exchange 2013 в организации, прежде чем настраивать шлюзы VoIP или IP-УАТС на отправку трафика UM SIP и RTP на серверы клиентского доступа Exchange 2013.

</td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Установка Exchange 2013 с помощью мастера установки</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Проверьте установку и просмотрите журналы установки сервера.</p></td>
<td><p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Проверка установки Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Если необходимо, установите требуемые языковые пакеты для единой системы обмена сообщениями.</p></td>
<td><p><a href="install-a-um-language-pack-exchange-2013-help.md">Установка языкового пакета единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="odd">
<td><p><strong> </strong></p></td>
<td><p>Создайте необходимое количество абонентских групп для организации.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan">Создание абонентской группы единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройте параметры безопасности абонентской группы.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/connect-voice-mail-system/configure-voip-security-setting">Настройка параметра безопасности VoIP</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Настройте режим запуска единой системы обмена сообщениями на каждом сервере клиентского доступа и почтовых ящиков.</p></td>
<td><p><a href="configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md">Настройка режима запуска на сервере почтовых ящиков</a></p>
<p><a href="configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md">Настройка режима запуска на сервере клиентского доступа</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройте количество одновременных вызовов на серверах почтовых ящиков.</p></td>
<td><p><a href="configure-the-number-of-incoming-calls-on-a-mailbox-server-exchange-2013-help.md">Настройте количество входящих вызовов на сервере почтовых ящиков</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Настройте номера голосовых доступов Outlook и другие параметры.</p></td>
<td><p><a href="manage-a-um-dial-plan-exchange-2013-help.md">Управление абонентской группой единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройте исходящие номера для единой системы обмена сообщениями.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/authorize-calls-using-dialing-rules">Авторизация вызовов с помощью правил набора номера</a></p>
<p><a href="https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/authorize-calls-for-users-in-a-dial-plan">Авторизации вызовов для пользователей в абонентской группы</a></p>
<p><a href="authorize-calls-for-a-group-of-users-exchange-2013-help.md">Авторизовать звонки для группы пользователей</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Создайте требуемое число автосекретарей.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant">Создание автосекретаря единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройте по отдельности каждого из автосекретарей единой системы обмена сообщениями.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/set-up-um-auto-attendant">Настройка автосекретаря единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="odd">
<td><p><strong> </strong></p></td>
<td><p>Создайте, импортируйте и включите новый сертификат Exchange для единой системы обмена сообщениями, или включите взаимно доверенный сторонний сертификат. Кроме того, импортируйте сертификат в шлюзы VoIP, IP УАТС и SBC.</p></td>
<td><p><a href="add-mailbox-and-client-access-servers-to-a-sip-uri-dial-plan-exchange-2013-help.md">Добавьте серверы клиентского доступа и почтовых ящиков для абонентской группы SIP URI</a></p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Перезагрузите службу единой системы обмена сообщениями Microsoft Exchange и службу маршрутизатора вызовов единой системы обмена сообщениями на всех серверах Exchange, чтобы загрузить требуемые сертификаты.</p></td>
<td><p><a href="stop-the-microsoft-exchange-unified-messaging-service-exchange-2013-help.md">Остановка службы единой системы обмена сообщениями Microsoft Exchange</a></p>
<p><a href="start-the-microsoft-exchange-unified-messaging-service-exchange-2013-help.md">Запуск службы единой системы обмена сообщениями Microsoft Exchange</a></p>
<p><a href="stop-the-microsoft-exchange-unified-messaging-call-router-service-exchange-2013-help.md">Остановка службы единой системы обмена сообщениями маршрутизатора вызовов Microsoft Exchange</a></p>
<p><a href="start-the-microsoft-exchange-unified-messaging-call-router-service-exchange-2013-help.md">Запуск службы единой системы обмена сообщениями маршрутизатора вызовов Microsoft Exchange</a></p></td>
</tr>
<tr class="odd">
<td><p><strong> </strong></p></td>
<td><p>Создайте политику почтовых ящиков единой системы обмена сообщениями или настройте политику почтовых ящиков по умолчанию.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy">Создание политики почтовых ящиков единой системы обмена сообщениями</a></p>
<p><a href="https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/set-up-voice-mail/manage-um-mailbox-policy">Управление политикой почтовых ящиков единой системы обмена СООБЩЕНИЯМИ</a></p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>При необходимости включите пользователей в единую систему обмена сообщениями с добавочным номером или номером E.164.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail">Включение для пользователя поддержки голосовой почты</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Включите поддержку входящих факсов (дополнительная возможность).</p></td>
<td><p><a href="enable-voice-mail-users-to-receive-faxes-exchange-2013-help.md">Обеспечение возможности получать факсы для пользователей голосовой почты</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройте защищенную голосовую почту (дополнительная возможность).</p></td>
<td><p><a href="protect-voice-mail-exchange-2013-help.md">Защита голосовой почты</a></p></td>
</tr>
</tbody>
</table>


В начало

