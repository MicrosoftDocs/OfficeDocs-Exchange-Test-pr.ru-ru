---
title: 'Управление получателями: Exchange 2013 Help'
TOCTitle: Управление получателями
ms:assetid: 669d602e-68e3-41f9-a455-b942d212d130
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd298028(v=EXCHG.150)
ms:contentKeyID: 50488342
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Управление получателями

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Управление получателямиГруппа ролей управления — это одна из встроенных групп ролей, которые составляют модель разрешений для управления доступом на основе ролей (RBAC) в Microsoft Exchange Server 2013. Группы ролей назначаются одной или нескольким ролям управления, которые содержат разрешения, необходимые для выполнения определенного набора задач. Члены группы ролей получают доступ к ролям управления, назначенным группе. Дополнительные сведения о группах ролей см. в статье [Общие сведения о группах ролей управления](understanding-management-role-groups-exchange-2013-help.md).

Администраторы, являющиеся участниками группы ролей Управление получателями, имеют административный доступ для создания или изменения получателей Exchange 2013 в организации Exchange 2013.

Эта группа ролей эквивалентна роли администраторов получателей Exchange в Exchange Server 2007.

Дополнительные сведения об управлении доступом на основе ролей см. в разделе [Общие сведения об управлении доступом на основе ролей](understanding-role-based-access-control-exchange-2013-help.md).

## Членство в группе ролей

Чтобы добавить участников в эту группу ролей или удалить их из нее, см. раздел [Управление участниками группы ролей](manage-role-group-members-exchange-2013-help.md).

По умолчанию только участники группы ролей управления организацией могут добавлять и удалять участников из этой группы ролей. Дополнительные сведения о том, как добавлять представителей группы ролей, см. в подразделе "Добавление или удаление представителя группы ролей" в разделе [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

Следующую команду можно использовать для просмотра списка пользователей или универсальных групп безопасности, которые являются участниками этой группы ролей.

```powershell
Get-RoleGroupMember "Recipient Management"
```

Дополнительные сведения об участниках группы ролей см. в разделе [View the members of a role group](manage-role-group-members-exchange-2013-help.md) в статье [Управление участниками группы ролей](manage-role-group-members-exchange-2013-help.md).

## Настройка группы ролей

Этой группе ролей назначены роли управления по умолчанию. Роли перечислены в разделе "Роли управления, назначенные этой группе ролей". В соответствии с требованиями организации назначения ролей можно добавлять в группы ролей или удалять из групп.

Группы ролей, предусмотренные в Exchange 2013, предназначены для решения определенных задач. Путем назначения ролей группе ролей участники группы могут выполнять задачи, связанные с ролью. Например, роль "Ведение журнала" позволяет управлять агентом ведения журнала и правилами ведения журнала. Дополнительные сведения о назначении ролей группам ролей см. в разделе [Общие сведения о назначениях ролей управления](understanding-management-role-assignments-exchange-2013-help.md).

Ролям, назначенным этой группе ролей, предоставлены области управления по умолчанию. Области управления определяют объекты Exchange, которые участники группы ролей могут просматривать и изменять. Области, связанные с назначениями между ролями и группами ролей, можно изменять. Например, это может понадобиться, чтобы позволить участникам группы ролей изменять получателей определенного подразделения или в определенном местоположении. Дополнительные сведения об областях управления см. в разделе [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md).

Дополнительные сведения о настройке этой группы ролей см. в следующих разделах.

  - [Управление группами ролей](manage-role-groups-exchange-2013-help.md)

  - [Управление участниками группы ролей](manage-role-group-members-exchange-2013-help.md)

Чтобы создать группу ролей и назначить некоторые роли, назначенные этой группе ролей, новой группе ролей, см. тему "Создание группы ролей" в разделе [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

Если создание участников безопасности в организации, например учетных записей пользователей, контролируется определенной группой, а не администраторами Exchange, можно создать группу ролей и переместить роль создания получателей почты и роль создания и членства в группе безопасности в новую группу ролей. Это действие используется для запрета участникам группы ролей Управление получателями создавать объекты Active Directory. Они могут, тем не менее, продолжать включать поддержку почты для новых объектов Active Directory. Дополнительные сведения о разрешениях с разделением см. в разделе [Общие сведения о разделенных разрешениях](understanding-split-permissions-exchange-2013-help.md).

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
<td><p><a href="distribution-groups-role-exchange-2013-help.md">Роль групп рассылки</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="mail-recipient-creation-role-exchange-2013-help.md">Роль создания получателя электронной почты</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="mail-recipients-role-exchange-2013-help.md">Роль получателей почты</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="message-tracking-role-exchange-2013-help.md">Роль отслеживания сообщений</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="migration-role-exchange-2013-help.md">Роль переноса</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="move-mailboxes-role-exchange-2013-help.md">Роль перемещения почтовых ящиков</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><a href="recipient-policies-role-exchange-2013-help.md">Роль политик получателя</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><a href="team-mailboxes-role-exchange-2013-help.md">Роль почтовых ящиков рабочей группы</a></p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
</tbody>
</table>

