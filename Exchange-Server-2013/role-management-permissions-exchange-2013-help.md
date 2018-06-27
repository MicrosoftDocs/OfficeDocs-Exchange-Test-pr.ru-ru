---
title: 'Разрешения управления ролями: Exchange 2013 Help'
TOCTitle: Разрешения управления ролями
ms:assetid: cb9591c4-fbb3-4199-8007-6bbfdfd5a2e9
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638186(v=EXCHG.150)
ms:contentKeyID: 50489080
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разрешения управления ролями

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2015-03-09_

Разрешения, необходимые для выполнения задач по настройке ролей управления, зависят от выполняемой процедуры или запускаемого командлета. Дополнительные сведения о ролях управления см. в разделе [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md).

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

## Разрешения управления ролями

Компоненты, указанные в следующей таблице, можно использовать для управления группами ролей управления, ролями, политиками назначения, назначениями, областями, определяющими разрешения, которые можно назначить администраторам и пользователям. Пользователи, которым назначена группа ролей управления с правами только для просмотра, могут просматривать конфигурацию функций в приведенной ниже таблице. Дополнительные сведения см. в разделе Управление организацией с правами только на просмотр[Управление организацией только с правом на просмотр](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Функция</th>
<th>Необходимы разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Роли управления</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Роли управления с незаданной областью</p></td>
<td><p>Роль управления <a href="unscoped-role-management-role-exchange-2013-help.md">Роль управления с незаданной областью</a></p></td>
</tr>
<tr class="odd">
<td><p>Группы ролей</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Политики назначения</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Назначения ролей</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Области управления</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Записи ролей управления</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Устаревшие разрешения</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Разделенные разрешения Active Directory</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Чтобы выполнить команду <code>setup.exe</code> с параметрами <em>PrepareAD</em> и <em>ActiveDirectorySplitPermissions</em>, используемая учетная запись должна входить в группы безопасности «Администраторы схемы» и «Администраторы предприятия».</td>
</tr>
</tbody>
</table>

</td>
</tr>
</tbody>
</table>

