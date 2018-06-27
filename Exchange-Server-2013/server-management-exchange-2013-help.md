---
title: 'Управление сервером: Exchange 2013 Help'
TOCTitle: Управление сервером
ms:assetid: 30cbc4de-adb3-42e8-922f-7661095bdb8c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd876866(v=EXCHG.150)
ms:contentKeyID: 50487756
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Управление сервером

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-03-09_

Управление сервером Группа ролей управления — это одна из встроенных групп ролей, которые составляют модель разрешений для управления доступом на основе ролей (RBAC) в Microsoft Exchange Server 2013. Группы ролей назначаются одной или нескольким ролям управления, которые содержат разрешения, необходимые для выполнения определенного набора задач. Члены группы ролей получают доступ к ролям управления, назначенным группе. Дополнительные сведения о группах ролей см. в статье [Общие сведения о группах ролей управления](understanding-management-role-groups-exchange-2013-help.md).

Администраторы, которые являются участниками этой группы ролей, могут выполнять настройку серверной конфигурации транспорта, клиентского доступа и функций почтовых ящиков, таких как копии базы данных, сертификаты, транспортные запросы и соединители отправки, виртуальные каталоги, а также протоколы клиентского доступа.

Эта группа ролей соответствует роли администраторов серверов Exchange в Microsoft Exchange Server 2007. Она предоставляет доступ к возможностям управления конфигурацией физических серверов. Однако в отличие от роли администраторов серверов Exchange в Exchange 2007, которая обеспечивала доступ только к локальному серверу под управлением Exchange 2007, группа ролей управления сервером позволяет получить доступ к просмотру и настройке всех серверов Exchange Server 2010 в организации.

Если необходимо, чтобы администраторы управляли только определенными серверами в организации, можно изменить области управления, которые применяются к этой группе ролей. Также можно создать группу ролей, основанную на группе ролей управления сервером, и настроить области управления в новой группе ролей. Дополнительные сведения см. в подразделе "Настройка групп ролей" данного раздела.

Дополнительные сведения об управлении доступом на основе ролей см. в разделе [Общие сведения об управлении доступом на основе ролей](understanding-role-based-access-control-exchange-2013-help.md).

## Членство в группе ролей

Чтобы добавить участников в эту группу ролей или удалить их из нее, см. раздел [Управление участниками группы ролей](manage-role-group-members-exchange-2013-help.md).

По умолчанию только участники группы ролей управления организацией могут добавлять и удалять участников из этой группы ролей. Дополнительные сведения о том, как добавлять представителей группы ролей, см. в подразделе "Добавление или удаление представителя группы ролей" в разделе [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

Следующую команду можно использовать для просмотра списка пользователей или универсальных групп безопасности, которые являются участниками этой группы ролей.

    Get-RoleGroupMember "Server Management"

Дополнительные сведения об участниках группы ролей см. в разделе [View the members of a role group](manage-role-group-members-exchange-2013-help.md) в статье [Управление участниками группы ролей](manage-role-group-members-exchange-2013-help.md).

## Настройка группы ролей

Этой группе ролей назначены роли управления по умолчанию. Роли перечислены в разделе "Роли управления, назначенные этой группе ролей". В соответствии с требованиями организации назначения ролей можно добавлять в группы ролей или удалять из групп.

Группы ролей, предусмотренные в Exchange 2013, предназначены для решения определенных задач. Путем назначения ролей группе ролей участники группы могут выполнять задачи, связанные с ролью. Например, роль "Ведение журнала" позволяет управлять агентом ведения журнала и правилами ведения журнала. Дополнительные сведения о назначении ролей группам ролей см. в разделе [Общие сведения о назначениях ролей управления](understanding-management-role-assignments-exchange-2013-help.md).

Ролям, назначенным этой группе ролей, предоставлены области управления по умолчанию. Области управления определяют объекты Exchange, которые участники группы ролей могут просматривать и изменять. Области, связанные с назначениями между ролями и группами ролей, можно изменять. Например, это может понадобиться, чтобы позволить участникам группы ролей изменять получателей определенного подразделения или в определенном местоположении. Дополнительные сведения об областях управления см. в разделе [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md).

Дополнительные сведения о настройке этой группы ролей см. в следующих разделах.

  - [Управление группами ролей](manage-role-groups-exchange-2013-help.md)

  - [Управление участниками группы ролей](manage-role-group-members-exchange-2013-help.md)

Чтобы создать группу ролей и назначить некоторые роли, назначенные этой группе ролей, новой группе ролей, см. тему "Создание группы ролей" в разделе [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

## Роли управления, назначенные этой группе ролей

В следующей таблице перечислены все роли управления, назначенные этой группе ролей, и следующие атрибуты каждого назначения роли:

  - **Обычное назначение**. Предоставляет доступ участникам группы ролей к записям ролей управления, предоставляемым связанной ролью управления.

  - **Делегированное назначение**. Предоставляет участникам группы ролей возможность назначать определенную роль другим группам ролей, политикам назначения ролей, пользователям или универсальным группам безопасности.

  - **Область чтения получателей**. Определяет объекты получателей, которые участники группы ролей могут читать из Active Directory.

  - **Область записи получателей**. Определяет объекты получателей, которые участники группы ролей могут изменять в Active Directory.

  - **Область чтения конфигурации**. Определяет объекты сервера и конфигурации, которые участники группы ролей могут читать из Active Directory.

  - **Область записи конфигурации**. Определяет объекты сервера и организации, которые участники группы ролей могут изменять в Active Directory.

Дополнительные сведения о назначениях ролей и областях управления см. в следующих разделах:

  - [Общие сведения о назначениях ролей управления](understanding-management-role-assignments-exchange-2013-help.md)

  - [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md)

### Роли управления, назначенные этой группе ролей

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Роль управления</th>
<th>Стандартное назначение</th>
<th>Делегированное назначение</th>
<th>Область чтения получателей</th>
<th>Область записи получателей</th>
<th>Область чтения конфигурации</th>
<th>Область записи конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="database-copies-role-exchange-2013-help.md">Роль копий баз данных</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="databases-role-exchange-2013-help.md">Роль баз данных</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="exchange-connectors-role-exchange-2013-help.md">Роль соединителей Exchange</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="exchange-server-certificates-role-exchange-2013-help.md">Роль сертификатов сервера Exchange Server</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="exchange-servers-role-exchange-2013-help.md">Роль серверов Exchange</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="exchange-virtual-directories-role-exchange-2013-help.md">Роль виртуальных каталогов Exchange</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="monitoring-role-exchange-2013-help.md">Роль мониторинга</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="pop3-and-imap4-protocols-role-exchange-2013-help.md">Роль протоколов POP3 и IMAP4</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="receive-connectors-role-exchange-2013-help.md">Роль соединителей получения</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="transport-queues-role-exchange-2013-help.md">Роль очередей транспорта</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
</tbody>
</table>

