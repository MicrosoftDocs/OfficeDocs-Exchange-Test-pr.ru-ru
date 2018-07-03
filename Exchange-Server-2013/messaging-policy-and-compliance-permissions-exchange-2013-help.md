﻿---
title: 'Политика обмена сообщениями и разрешения для соответствия требованиям: Exchange 2013 Help'
TOCTitle: Политика обмена сообщениями и разрешения для соответствия требованиям
ms:assetid: ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638205(v=EXCHG.150)
ms:contentKeyID: 50489442
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Политика обмена сообщениями и разрешения для соответствия требованиям

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Разрешения, необходимые для настройки политики обмена сообщениями и соответствия требованиям, отличаются в зависимости от выполняемой процедуры или используемого командлета. Дополнительные сведения о политиках обмена сообщениями и соответствии требованиям см. в разделе [Политика обмена сообщениями и соответствие требованиям](messaging-policy-and-compliance-exchange-2013-help.md).

Для поиска разрешений, необходимых для выполнения процедуры или запуска командлета, выполните следующие действия.

1.  В следующей таблице найдите функцию, наиболее близко связанную с процедурой, которую необходимо выполнить, или командлетом, который необходимо запустить.

2.  После этого проверьте разрешения, необходимые для функции. Вы должны быть участником одной из этих групп ролей, равнозначной настраиваемой группы ролей или равнозначной роли управления. Вы также можете щелкнуть группу ролей, чтобы просмотреть ее роли управления. Если для функции указано несколько групп ролей, то для ее использования достаточно относиться к одной из этих групп. Дополнительные сведения о группах ролей и ролях управления см. в разделе [Общие сведения об управлении доступом на основе ролей](understanding-role-based-access-control-exchange-2013-help.md).

3.  Запустите командлет **Get-ManagementRoleAssignment**, чтобы просмотреть назначенные группы ролей или роли управления и проверить наличие необходимых разрешений для управления функцией.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Для запуска командлета <strong>Get-ManagementRoleAssignment</strong> вам должна быть назначена роль управления &quot;Управление ролями&quot;. Если для запуска командлета <strong>Get-ManagementRoleAssignment</strong> отсутствуют необходимые разрешения, попросите администратора Exchange назначить группы ролей или роли управления.</td>
    </tr>
    </tbody>
    </table>


Дополнительные сведения о делегировании возможности управления другим пользователям см. в разделе [Назначения роли делегата](delegate-role-assignments-exchange-2013-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Некоторые функции, которыми необходимо управлять, могут находиться на пограничных транспортных серверах. Для управления функциями на пограничных транспортных серверах необходимо стать участником локальной группы администраторов пограничного транспортного сервера, которым требуется управлять. На пограничном транспортном сервере не используется управление доступом на основе ролей (RBAC). Для функций, которыми можно управлять на пограничных транспортных серверах, столбец &quot;Требуемые разрешения&quot; в следующей таблице содержит запись &quot;Локальный администратор пограничного транспортного сервера&quot;.</td>
</tr>
</tbody>
</table>


## Политика обмена сообщениями и соответствие требованиям

Для настройки политики обмена сообщениями и соответствия требованиям можно использовать компоненты, приведенные в следующей таблице. Также приведен список групп ролей, которые требуются для настройки каждого компонента.

Пользователи, которым назначена группа ролей управления с правами только для просмотра, могут просматривать конфигурацию компонентов в следующей таблице. Дополнительные сведения см. в разделе [Управление организацией только с правом на просмотр](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Компонент</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Предотвращение потери данных (DLP)</p></td>
<td><p>При использовании Office 365:</p>
<ul>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=335814">Глобальный администратор Office 365</a>, который автоматически включает Exchange <a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=335814">Администратор службы Office 365</a>, а также группа ролей администратора <a href="organization-management-exchange-2013-help.md">Управление организацией</a> в Exchange</p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=335814">Разрешения в Office 365</a></p></li>
</ul>
<p>Только при использовании Exchange Server 2013 или Exchange Online:</p>
<ul>
<li><p><a href="compliance-management-exchange-2013-help.md">Управление соответствием требованиям</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Удаление содержимого почтового ящика (с помощью командлета <a href="https://technet.microsoft.com/ru-ru/library/dd298173(v=exchg.150)">Search-Mailbox</a> с параметром <em>DeleteContent</em>)</p></td>
<td><p><a href="discovery-management-exchange-2013-help.md">Управление обнаружением</a> <strong>и</strong></p>
<p><a href="mailbox-import-export-role-exchange-2013-help.md">Роль импорта и экспорта почтового ящика</a></p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>По умолчанию роль экспорта-импорта не назначается никакой из групп ролей. Можно назначить роль управления встроенной или пользовательской группе ролей, пользователю или универсальной группе безопасности. Рекомендуется назначение роли для группы ролей. Дополнительные сведения см. в разделе <a href="add-a-role-to-a-user-or-usg-exchange-2013-help.md">Добавление роли для пользователя или универсальной группы безопасности</a>.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="odd">
<td><p>Создание почтовых ящиков обнаружения</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Ведение журнала</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="odd">
<td><p>Ведение журнала аудита почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="even">
<td><p>Классификации сообщений</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Управление записями сообщений</p></td>
<td><p><a href="compliance-management-exchange-2013-help.md">Управление соответствием требованиям</a></p>
<p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="even">
<td><p>Обнаружение электронных данных на месте</p></td>
<td><p><a href="discovery-management-exchange-2013-help.md">Управление обнаружением</a></p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>По умолчанию группа роли управления обнаружением не имеет членов. Отсутствуют пользователи, включая администраторов, с правами, необходимыми для поиска почтовых ящиков. Дополнительные сведения см. в разделе <a href="assign-ediscovery-permissions-in-exchange-exchange-2013-help.md">Назначение разрешений обнаружения электронных данных в Exchange</a>.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="odd">
<td><p>Хранение на месте</p></td>
<td><p><a href="discovery-management-exchange-2013-help.md">Управление обнаружением</a></p>
<p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для создания хранения на месте на основе запроса, пользователю необходимо назначить роли поиска почтовых ящиков и судебного удержания непосредственно или через членство в группе ролей, в которой назначены обе роли. Чтобы создать хранение на месте без использования запроса, который помещает все элементы сообщения на удержание, необходимо назначить роль судебного удержания. Для группы ролей управления обнаружением назначаются обе роли.<br />
Для группы ролей &quot;Управление организацией&quot; назначается роль судебного удержания. Члены группы ролей управления организацией могут применить хранение на месте для всех элементов в почтовом ящике, но не могут создать хранение на месте на основе запроса.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="even">
<td><p>Архивация на месте</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Архивация на месте — проверка подключения</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Управления правами на доступ к данным, настройка</p></td>
<td><p><a href="compliance-management-exchange-2013-help.md">Управление соответствием требованиям</a></p>
<p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Политики хранения — применение</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="even">
<td><p>Создание политик хранения</p></td>
<td><p>См. главу по управлению записями сообщений</p></td>
</tr>
<tr class="odd">
<td><p>Правила транспорта</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
</tbody>
</table>
