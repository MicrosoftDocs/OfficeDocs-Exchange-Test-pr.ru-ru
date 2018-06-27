---
title: 'Просмотр назначения ролей: Exchange 2013 Help'
TOCTitle: Просмотр назначения ролей
ms:assetid: 0be4def9-af6d-476a-9c97-7155ae11b587
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd335086(v=EXCHG.150)
ms:contentKeyID: 50487462
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Просмотр назначения ролей

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2012-10-03_

При назначении роли управления задается роль управления для уполномоченного роли. Дополнительные сведения о назначениях ролей управления в Microsoft Exchange Server 2013 см. в разделе [Общие сведения о назначениях ролей управления](understanding-management-role-assignments-exchange-2013-help.md).

Необходимы сведения о других задачах управления, связанных с ролями? см. в разделе [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Назначения ролей" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - В этом разделе описывается использование конвейерной передачи и командлета **Format-List**. Дополнительные сведения об этих понятиях см. в следующих разделах:
    
      - [Конвейеризация](https://technet.microsoft.com/ru-ru/library/aa998260\(v=exchg.150\))
    
      - [Работа с выходными данными команды](working-with-command-output-exchange-2013-help.md)

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Что необходимо сделать?

## Просмотр списка всех назначений ролей

Можно просмотреть список всех назначений ролей, настроенных в организации, выполнив командлет **Get-ManagementRoleAssignment**. При необходимости получить список назначений ролей, соответствующих указанному частичному строковому значению, используются подстановочные знаки (\*). В этом примере возвращается список всех назначений ролей, начинающихся со строки "Tier 1".

    Get-ManagementRoleAssignment "Tier 1*"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр сведений о назначении определенных ролей

Подробные сведения о назначении ролей можно просмотреть путем конвейерной передачи результатов командлета **Get-ManagementRoleAssignment** в командлет **Format-List**. Используйте следующий синтаксис.

    Get-ManagementRoleAssignment <assignment name> | Format-List

В этом примере возвращаются подробные сведения о назначении роли службы поддержки.

    Get-ManagementRoleAssignment "Help Desk Assignment" | Format-List

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр списка назначений ролей, назначенных определенному уполномоченному роли

Для просмотра списка назначений ролей, связанных с группой ролей управления, ролью, политикой назначения роли или с пользователем или универсальной группой безопасности (USG), используется следующий синтаксис.

    Get-ManagementRoleAssignment -RoleAssignee <role assignee name>

В этом примере возвращаются все назначения ролей, связанные с группой ролей управления сервером.

    Get-ManagementRoleAssignment -RoleAssignee "Server Management"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр назначений ролей, связанных с определенной ролью

Каждая роль может иметь несколько назначений ролей. Используйте командлет **Get-ManagementRoleAssigment** для просмотра списка назначений ролей, связанных с определенной ролью.

Для просмотра списка назначений ролей, связанных с определенной ролью, используется следующий синтаксис.

    Get-ManagementRoleAssignment -Role <role name>

В этом примере возвращаются все назначения ролей, связанные с ролью получателей почты.

    Get-ManagementRoleAssignment -Role "Mail Recipients"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр списка назначений ролей, использующих определенную предварительно заданную область

Для просмотра списка назначений ролей, использующих определенную предварительно заданную область, используется следующий синтаксис.

    Get-ManagementRoleAssignment -RecipientWriteScope < MyGAL | MyDistributionGroups | Organization | Self | CustomRecipientScope | ExecutiveRecipientScope >

В этом примере возвращаются все назначения ролей, использующие предопределенную область "Организация".

    Get-ManagementRoleAssignment -RecipientWriteScope Organization

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр списка назначений ролей, ограниченных определенным подразделением организации

Для просмотра списка назначений ролей, ограниченных определенным подразделением организации, используется следующий синтаксис.

    Get-ManagementRoleAssignment -RecipientOrganizationalUnitScope <OU>

В этом примере возвращаются все назначения ролей, ограниченные подразделением North America\\Engineering\\Users в домене contoso.com.

    Get-ManagementRoleAssignment -RecipientOrganizationalUnitScope "contoso.com/North America/Engineering/Users"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр списка назначений, использующих определенную настраиваемую область

Для просмотра списка назначений ролей, использующих определенную настраиваемую область, необходимо сначала определить, является ли данная область областью получателя, областью конфигурации, исключительной областью получателя или исключительной областью конфигурации. В каждом типе области используется другой параметр командлета **Get-ManagementRoleAssignment**. В следующем списке приведены все области и связанные с ними параметры.

  - **Области получателя** *CustomRecipientWriteScope*

  - **Области конфигурации** *CustomConfigWriteScope*

  - **Исключительные области получателя** *ExclusiveRecipientWriteScope*

  - **Исключительные области получателя** *ExclusiveConfigWriteScope*

Синтаксис для всех параметров одинаковый. Укажите имя области с помощью параметра, который соответствует типу этой области.

В этом примере возвращаются все назначения ролей, использующие область получателей Ванкувера.

    Get-ManagementRoleAssignment -CustomRecipientWriteScope "Vancouver Recipients"

В этом примере возвращаются все назначения ролей, использующие исключительную область конфигурации "Сайт Active Directory в Сиэтле".

    Get-ManagementRoleAssignment -ExclusiveConfigWriteScope "Seattle AD Site"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр списка исключительных или стандартных областей

Для просмотра списка исключительных или стандартных назначений ролей используется следующий синтаксис.

    Get-ManagementRoleAssignment -Exclusive < $True | $False >

Например, для просмотра списка исключительных областей выполните следующую команду:

    Get-ManagementRoleAssignment -Exclusive $True

В этом примере возвращается список стандартных областей без каких-либо исключительных областей.

    Get-ManagementRoleAssignment -Exclusive $False

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр пользователей, которые могут изменять определенного получателя или сервер

Для просмотра списка назначений ролей, которые могут изменять определенного получателя или сервер, используются параметры *WritableRecipient* и *WritableServer*. Укажите имя получателя с помощью параметра *WritableRecipient* и имя сервера с помощью параметра *WritableServer*.

В этом примере возвращается список назначений ролей, которые могут изменить получателя Владимир.

    Get-ManagementRoleAssignment -WritableRecipient "Brian"

Параметры *WritableRecipient* и *WritableServer* можно использовать с другими параметрами, такими как *RoleAssignee* и *GetEffectiveUsers* для уточнения запроса и расширения групп ролей или универсальных групп безопасности. В этом примере возвращаются все пользователи, которые могут изменять сервер EX02, и которым назначена группа ролей управления сервером.

    Get-ManagementRoleAssignment -WritableServer EX02 -RoleAssignee "Server Management" -GetEffectiveUsers

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр пользователей, которые получают разрешения посредством назначений через группу ролей или универсальную группу безопасности

Для просмотра списка пользователей, получающих разрешения посредством назначения ролей, используется следующий синтаксис.

    Get-ManagementRoleAssignment <assignment name> -GetEffectiveUsers

В этом примере возвращается список пользователей, которым назначена роль службы поддержки.

    Get-ManagementRoleAssignment "Help Desk Assignment" -GetEffectiveUsers

Параметр *GetEffectiveUsers* можно использовать с несколькими другими параметрами командлета **Get-ManagementRoleAssignment** для расширения групп ролей и универсальных групп безопасности, которым назначены эти роли. Пример использования параметра *GetEffectiveUsers* совместно с другими параметрами см. в подразделе "Просмотр пользователей, которые могут изменять определенного получателя или сервер" данного раздела.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Просмотр списка включенных или отключенных назначений ролей

Для просмотра списка включенных или отключенных назначений ролей используется следующий синтаксис.

    Get-ManagementRoleAssignment -Enabled < $True | $False >

В этом примере возвращается список отключенных назначений ролей.

    Get-ManagementRoleAssignment -Enabled $False

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

