---
title: 'Контрольный список: Обновление единой системы обмена сообщениями Exchange 2010 до Exchange 2013: Exchange 2013 Help'
TOCTitle: 'Контрольный список: Обновление единой системы обмена сообщениями Exchange 2010 до Exchange 2013'
ms:assetid: 799bd1b1-a918-4bd8-911e-e6ca08bd7b52
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn169228(v=EXCHG.150)
ms:contentKeyID: 54652124
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Контрольный список: Обновление единой системы обмена сообщениями Exchange 2010 до Exchange 2013

 

_**Применимо к:** Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2016-12-09_

Используйте этот контрольный список для обновления единой системы обмена сообщениями Exchange 2010 до Exchange 2013. Обращайтесь к этим сведениям во время обновления организации Exchange 2010 и развертывания единой системы обмена сообщениями до Exchange 2013. Пошаговые инструкции по обновлению до версии единой системы обмена сообщениями Exchange 2013 см. в разделе [Обновление единой системы обмена сообщениями Exchange 2010 до Exchange 2013](upgrade-exchange-2010-um-to-exchange-2013-um-exchange-2013-help.md).

Перед началом работы со списком убедитесь, что вы ознакомились с общими концепциями, изложенными в разделах:

  - [Планирование единой системы обмена сообщениями](planning-for-unified-messaging-exchange-2013-help.md)

  - [Интеграция телефонной системы с единой системой обмена сообщениями](telephone-system-integration-with-um-exchange-2013-help.md)

  - [Подключиться к телефонной сети вашей системы голосовой почты](connect-your-voice-mail-system-to-your-telephone-network-exchange-2013-help.md)

Пошаговое руководство по обновлению единой системы обмена сообщениями Exchange 2007 до версии единой системы обмена сообщениями Exchange 2013 см. в разделе [Обновление единой системы обмена СООБЩЕНИЯМИ Exchange 2007 до Exchange 2013](upgrade-exchange-2007-um-to-exchange-2013-um-exchange-2013-help.md).

## Контрольный список по обновлению единой системы обмена сообщениями Exchange 2010 до Exchange 2013


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
<td><p></p></td>
<td><p>Проверьте предварительные требования к установке.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Предварительные требования для Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
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
<td><p></p></td>
<td><p>Если необходимо, установите требуемые языковые пакеты для единой системы обмена сообщениями.</p></td>
<td><p><a href="install-a-um-language-pack-exchange-2013-help.md">Установка языкового пакета единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Переместите системный почтовый ящик Exchange 2010, используемый для пользовательских приглашений единой системы обмена сообщениями, в Exchange 2013.</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Перемещение почтовых ящиков в Exchange 2013</a></p>

> [!NOTE]  
> Если системный почтовый ящик уже был перемещен, вы по-прежнему можете вручную импортировать и экспортировать настраиваемые приглашения из Exchange 2010 с помощью <a href="import-and-export-custom-greetings-announcements-menus-and-prompts-exchange-2013-help.md">Импорт и экспорт настраиваемых приветствий, объявлений, меню и приглашений</a>.

</td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Экспорт и импорт сертификатов.</p></td>
<td><p><a href="deploying-certificates-for-um-exchange-2013-help.md">Развертывание сертификатов для единой системы обмена СООБЩЕНИЯМИ</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Настройка режима запуска единой системы обмена сообщениями на всех серверах клиентского доступа Exchange 2013.</p></td>
<td><p><a href="configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md">Настройка режима запуска на сервере клиентского доступа</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройка режима запуска единой системы обмена сообщениями на всех серверах почтовых ящиков Exchange 2013.</p></td>
<td><p><a href="configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md">Настройка режима запуска на сервере почтовых ящиков</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Создание или настройка существующих абонентских доступов единой системы обмена сообщениями.</p></td>
<td><p><a href="create-a-um-dial-plan-exchange-2013-help.md">Создание абонентской группы единой системы обмена сообщениями</a></p>
<p><a href="manage-a-um-dial-plan-exchange-2013-help.md">Управление абонентской группой единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Создание или настройка существующих шлюзов IP единой системы обмена сообщениями.</p></td>
<td><p><a href="create-a-um-ip-gateway-exchange-2013-help.md">Создание шлюза IP единой системы обмена сообщениями</a></p>
<p><a href="manage-a-um-ip-gateway-exchange-2013-help.md">Управление шлюзом IP единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Создание сервисной группы единой системы обмена сообщениями.</p></td>
<td><p><a href="create-a-um-hunt-group-exchange-2013-help.md">Создание сервисной группы единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Создание или настройка автосекретарей единой системы обмена сообщениями.</p></td>
<td><p><a href="create-a-um-auto-attendant-exchange-2013-help.md">Создание автосекретаря единой системы обмена сообщениями</a></p>
<p><a href="manage-a-um-auto-attendant-exchange-2013-help.md">Управление автосекретаря единой системы обмена СООБЩЕНИЯМИ</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Создание или настройка политики почтовых ящиков единой системы обмена сообщениями.</p></td>
<td><p><a href="create-a-um-mailbox-policy-exchange-2013-help.md">Создание политики почтовых ящиков единой системы обмена сообщениями</a></p>
<p><a href="manage-a-um-mailbox-policy-exchange-2013-help.md">Управление политикой почтовых ящиков единой системы обмена СООБЩЕНИЯМИ</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Перемещение существующих почтовых ящиков с включенной единой системой обмена сообщениями в Exchange 2013.</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Перемещение почтовых ящиков в Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Включение новых пользователей для единой системы обмена сообщениями или настройка параметров для существующего пользователя с включенной единой системой обмена сообщениями.</p></td>
<td><p><a href="enable-a-user-for-voice-mail-exchange-2013-help.md">Включение для пользователя поддержки голосовой почты</a></p>
<p><a href="manage-voice-mail-settings-for-a-user-exchange-2013-help.md">Управление параметрами голосовой почты для пользователя</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройка шлюзов VoIP, IP УАТС и УАТС с поддержкой SIP для направления всех входящих вызовов на серверы клиентского доступа Exchange 2013.</p></td>
<td><p><a href="configuration-notes-for-supported-voip-gateways-ip-pbxs-and-pbxs-exchange-2013-help.md">Заметки по конфигурации для поддерживаемых шлюзов VoIP, IP-УАТС и УАТС</a> <a href="connect-a-voip-gateway-ip-pbx-or-session-border-controller-to-um-exchange-2013-help.md">Подключение VoIP шлюз, IP-УАТС или сеанс пограничного контроллера единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Отключение автоответчика на серверах единой системы обмена сообщениями Exchange 2010.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=296335">Отключение единой системы обмена сообщениями на сервере Exchange 2010</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Удаление сервера единой системы обмена сообщениями Exchange 2010 из абонентской группы.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=296336">Удаление сервера единой системы обмена СООБЩЕНИЯМИ из абонентской группы</a></p></td>
</tr>
</tbody>
</table>

