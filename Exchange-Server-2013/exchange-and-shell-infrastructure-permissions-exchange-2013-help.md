---
title: 'Разрешения инфраструктуры Exchange и командной консоли: Exchange 2013 Help'
TOCTitle: Разрешения инфраструктуры Exchange и командной консоли
ms:assetid: 3646a4e8-36b2-41fb-89a4-79b0963fcb11
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638114(v=EXCHG.150)
ms:contentKeyID: 50487811
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разрешения инфраструктуры Exchange и командной консоли

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Необходимые разрешения на выполнение задач для настройки различных компонентов Microsoft Exchange Server 2013 определяются в зависимости от выполняемой процедуры или запускаемого командлета. Дополнительные сведения о соответствующих возможностях см. в следующих подразделах.

Для поиска разрешений, необходимых для выполнения процедуры или запуска командлета, выполните следующие действия.

1.  В следующей таблице найдите функцию, наиболее близко связанную с процедурой, которую необходимо выполнить, или командлетом, который необходимо запустить.

2.  После этого проверьте разрешения, необходимые для функции. Вы должны быть участником одной из этих групп ролей, равнозначной настраиваемой группы ролей или равнозначной роли управления. Вы также можете щелкнуть группу ролей, чтобы просмотреть ее роли управления. Если для функции указано несколько групп ролей, то для ее использования достаточно относиться к одной из этих групп. Дополнительные сведения о группах ролей и ролях управления см. в разделе [Общие сведения об управлении доступом на основе ролей](understanding-role-based-access-control-exchange-2013-help.md).

3.  Запустите командлет **Get-ManagementRoleAssignment**, чтобы просмотреть назначенные группы ролей или роли управления и проверить наличие необходимых разрешений для управления функцией.
    
    > [!NOTE]  
    > Для запуска командлета <strong>Get-ManagementRoleAssignment</strong> вам должна быть назначена роль управления &quot;Управление ролями&quot;. Если для запуска командлета <strong>Get-ManagementRoleAssignment</strong> отсутствуют необходимые разрешения, попросите администратора Exchange назначить группы ролей или роли управления.


Дополнительные сведения о делегировании возможности управления другим пользователям см. в разделе [Назначения роли делегата](delegate-role-assignments-exchange-2013-help.md).

> [!NOTE]  
> Для использования некоторых функций требуются разрешения локального администратора сервера, которым необходимо управлять. Для управления этими функциями необходимо быть участником локальной группы администраторов этого сервера.


## Разрешения в инфраструктуре Exchange

В следующей таблице перечислены разрешения, которые необходимы для выполнения задач по настройке основных параметров Exchange 2013.

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
<td><p>Ведение журнала аудита администратора</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры конфигурации центра администрирования Exchange</p></td>
<td><p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
<tr class="odd">
<td><p>Возможности подключения центра администрирования Exchange</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры конфигурации сервера Exchange</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Параметры справки Exchange</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Категории сообщений</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="odd">
<td><p>Ключ продукта</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Проверка работоспособности системы</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Ведение журнала аудита администратора с правом только на просмотр</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p>

> [!NOTE]  
> Группе ролей управления также можно вручную назначить роль управления &quot;Журналы аудита с правом только на просмотр&quot;. Дополнительные сведения см. в разделе <a href="view-only-audit-logs-role-exchange-2013-help.md">Роль только для просмотра журналов аудита</a>.

</td>
</tr>
<tr class="even">
<td><p>Запись в журнал аудита</p></td>
<td><p>Пользователи, являющиеся членами какой-либо группы ролей или которым назначена какая-либо роль управления, могут вносить записи в журнал аудита администратора.</p></td>
</tr>
</tbody>
</table>


## Разрешения инфраструктуры командной консоли

В следующей таблице перечислены разрешения, которые необходимы для выполнения задач по настройке функций, которые контролируют ход работы командной консоли Exchange.

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
<td><p>Параметры сервера служб домена Active Directory</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="um-management-exchange-2013-help.md">Управление единой системой обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p>Агенты расширения командлета</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Виртуальные каталоги PowerShell</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Установка PowerShell и WinRM</p></td>
<td><p>Администратор локального сервера</p></td>
</tr>
<tr class="odd">
<td><p>Удаленная командная консоль Exchange</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
</tbody>
</table>


## Разрешения сертификатов и федерации

В таблице ниже перечислены разрешения, необходимые для выполнения задач по доверию федерации, настройке OAuth, управлению сертификатами и настройке гибридного развертывания.

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
<td><p>Управление сертификатами</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Доверие федерации, OAuth</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Проверка доверия федерации, OAuth</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Настройка гибридного развертывания</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Соединители Intra-Organization</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
</tbody>
</table>

