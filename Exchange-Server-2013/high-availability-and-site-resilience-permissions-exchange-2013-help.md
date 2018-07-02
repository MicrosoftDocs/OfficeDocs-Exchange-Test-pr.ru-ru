---
title: 'Разрешения высокого уровня доступности и устойчивости сайта: Exchange 2013 Help'
TOCTitle: Разрешения высокого уровня доступности и устойчивости сайта
ms:assetid: 66085107-4d4d-41c3-a425-82314acd9eee
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638136(v=EXCHG.150)
ms:contentKeyID: 50488165
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разрешения высокого уровня доступности и устойчивости сайта

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-11-12_

Разрешения, требуемые для настройки высокого уровня доступности, отличаются в зависимости от выполняемой процедуры или используемого командлета. Дополнительные сведения о высоком уровне доступности см. в разделе [Высокая доступность и устойчивость сайтов](high-availability-and-site-resilience-exchange-2013-help.md).

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

## Разрешения группы доступности базы данных

В следующей таблице перечислены функции, которые можно использовать для добавления, удаления и настройки параметров групп доступности баз данных.

Пользователи, которым назначена группа ролей управления с правами только для просмотра, могут просматривать конфигурацию функций в приведенной ниже таблице. Дополнительные сведения см. в разделе Управление организацией с правами только на просмотр[Управление организацией только с правом на просмотр](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Функция</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Членство в группе доступности базы данных</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="database-availability-groups-role-exchange-2013-help.md">Роль групп обеспечения доступности баз данных</a></p></td>
</tr>
<tr class="even">
<td><p>Свойства группы доступности базы данных</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="database-availability-groups-role-exchange-2013-help.md">Роль групп обеспечения доступности баз данных</a></p></td>
</tr>
<tr class="odd">
<td><p>Группы доступности базы данных</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="database-availability-groups-role-exchange-2013-help.md">Роль групп обеспечения доступности баз данных</a></p></td>
</tr>
<tr class="even">
<td><p>Сети доступности базы данных</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="database-availability-groups-role-exchange-2013-help.md">Роль групп обеспечения доступности баз данных</a></p></td>
</tr>
</tbody>
</table>


## Разрешения на копирование базы данных почтовых ящиков

В таблице ниже перечислены функции, которые можно использовать для добавления, удаления, обновления и активации копий базы данных почтовых ящиков.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Функция</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Переключение базы данных</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="databases-role-exchange-2013-help.md">Роль баз данных</a></p></td>
</tr>
<tr class="even">
<td><p>Копии базы данных почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="database-copies-role-exchange-2013-help.md">Роль копий баз данных</a></p></td>
</tr>
<tr class="odd">
<td><p>Переключение сервера</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="databases-role-exchange-2013-help.md">Роль баз данных</a></p></td>
</tr>
<tr class="even">
<td><p>Обновление копии базы данных почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="database-copies-role-exchange-2013-help.md">Роль копий баз данных</a></p></td>
</tr>
</tbody>
</table>

