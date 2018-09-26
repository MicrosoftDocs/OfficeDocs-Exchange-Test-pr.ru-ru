---
title: 'Справка по Exchange 2013: добавление роли для пользователя или USG'
TOCTitle: Добавление роли для пользователя или универсальной группы безопасности
ms:assetid: ae5608de-a141-4714-8876-bce7d2a22cb5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd351056(v=EXCHG.150)
ms:contentKeyID: 50488849
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Добавление роли для пользователя или универсальной группы безопасности

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-03_

Пользователю или универсальной группе безопасности можно назначить роль управления. Назначение роли пользователю или универсальной группе безопасности позволяет предоставить пользователям права на выполнение задач, зависящих от командлетов, сценариев и соответствующих параметров, определенных в роли управления.

Если необходимо назначить роли группе ролей управления или политики назначения ролей управления, см. следующие разделы.

  - [Управление группами ролей](manage-role-groups-exchange-2013-help.md)

  - [Управление политиками назначения ролей](manage-role-assignment-policies-exchange-2013-help.md)

Если следует добавить членов в группу ролей или назначить пользователю политику назначения ролей, см. следующие разделы.

  - [Управление участниками группы ролей](manage-role-group-members-exchange-2013-help.md)

  - [Изменение политики назначения для почтового ящика](change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md)

Дополнительные сведения см. в разделе [Общие сведения об управлении доступом на основе ролей](understanding-role-based-access-control-exchange-2013-help.md).

Необходимы сведения о других задачах управления, связанных с ролями? См. раздел [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Назначения ролей» в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - Несмотря на то что роли можно назначать напрямую пользователям и универсальным группам безопасности, рекомендуемым методом предоставления разрешений администраторам и пользователям является использование групп ролей управления и политик назначения ролей управления. Модель предоставления разрешений упрощается за счет использования групп и политик назначения ролей.

  - Назначения ролей являются аддитивными. Это означает, что все роли суммируются при их оценке. Если пользователю назначены две роли и одна из них содержит командлет, а другая нет, то командлет будет доступен пользователю.
    
    По умолчанию назначения ролей не предоставляют право на назначения ролей другим пользователям. Чтобы разрешить пользователю назначать роли другим пользователям или универсальным группам безопасности, см. раздел [Назначения роли делегата](delegate-role-assignments-exchange-2013-help.md).

  - При создании назначения с областью эта область переопределяет неявную область записи роли. Тем не менее, неявная область чтения данной роли по-прежнему применяется. Новая область не может возвращать объекты, которые находятся за пределами неявной области чтения этой роли. Дополнительные сведения см. в разделе [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md).

  - Во всех процедурах, приведенных в этом разделе, используется параметр *SecurityGroup* для назначения ролей универсальным группам безопасности. Чтобы назначить роль определенному пользователю, воспользуйтесь параметром *User* вместо параметра *SecurityGroup*. В остальном синтаксис всех команд одинаков.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>. 


## Что необходимо сделать?

## Создание назначения роли без области

Можно создать назначение роли без области. При этом применяются неявные области чтения и записи роли.

Используйте следующий синтаксис для назначения роли универсальной группе безопасности без области.

```powershell
    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup <USG> -Role <role name>
```

В этом примере роль Exchange Servers назначается универсальной группе безопасности SeattleAdmins.

```powershell
    New-ManagementRoleAssignment -Name "Exchange Servers_SeattleAdmins" -SecurityGroup SeattleAdmins -Role "Exchange Servers"
```

Дополнительные сведения о синтаксисе и параметрах см. в разделе [New-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd335193\(v=exchg.150\)).

## Создание назначения роли с предварительно определенной относительной областью

Если предварительно определенная относительная область соответствует бизнес-требованиям, можно применить эту область к назначению роли, а не создавать пользовательскую область. Список предварительно определенных областей и их описания см. в разделе [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md).

Используйте следующий синтаксис для назначения роли универсальной группе безопасности с предварительно определенной областью.

```powershell
    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup < USG> -Role <role name> -RecipientRelativeWriteScope < MyDistributionGroups | Organization | Self >
```

В этом примере роль Exchange Servers назначается универсальной группе безопасности SeattleAdmins, а затем применяется предварительно определенная область Organization.

```powershell
    New-ManagementRoleAssignment -Name "Exchange Servers_SeattleAdmins" -SecurityGroup SeattleAdmins -Role "Exchange Servers" -RecipientRelativeWriteScope Organization
```

Дополнительные сведения о синтаксисе и параметрах см. в разделе [New-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd335193\(v=exchg.150\)).

## Создание назначения роли с областью, основанной на фильтре получателей

Если создана область, основанная на фильтре получателей, которую следует использовать для назначения роли, необходимо включить область в команду, используемую для назначения роли универсальной группе безопасности, с помощью параметра *CustomRecipientWriteScope*. При использовании параметра *CustomRecipientWriteScope* невозможно использовать параметр *RecipientOrganizationalUnitScope*.

Чтобы добавить область к назначению роли, ее необходимо создать. Дополнительные сведения см. в разделе [Создание регулярной или монопольной области](create-a-regular-or-exclusive-scope-exchange-2013-help.md).

Используйте следующий синтаксис для назначения роли универсальной группе безопасности с областью, основанной на фильтре получателей.

```powershell
    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup < USG> -Role <role name> -CustomRecipientWriteScope <role scope name>
```

В этом примере роль Mail Recipients назначается универсальной группе безопасности Seattle Recipient Admins, а затем применяется область Seattle Recipients.

```powershell
    New-ManagementRoleAssignment -Name "Mail Recipients_Seattle Recipient Admins" -SecurityGroup "Seattle Recipient Admins" -Role "Mail Recipients" -CustomRecipientWriteScope "Seattle Recipients"
```

Дополнительные сведения о синтаксисе и параметрах см. в разделе [New-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd335193\(v=exchg.150\)).

## Создание назначения роли с областью настройки на основе сервера, списка или фильтра серверов

Если создана область настройки, основанная на списке или фильтре серверов или баз данных, которую следует использовать для назначения роли, необходимо включить область в команду, используемую для назначения роли универсальной группе безопасности, с помощью параметра *CustomConfigWriteScope*.

Чтобы добавить область к назначению роли, ее необходимо создать. Дополнительные сведения см. в разделе [Создание регулярной или монопольной области](create-a-regular-or-exclusive-scope-exchange-2013-help.md).

Используйте следующий синтаксис для назначения роли универсальной группе безопасности с областью настройки.

```powershell
    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup <USG> -Role <role name> -CustomConfigWriteScope <role scope name>
```

В этом примере роль Exchange Servers назначается универсальной группе безопасности MailboxAdmins, а затем применяется область Mailbox Servers.

```powershell
    New-ManagementRoleAssignment -Name "Exchange Servers_MailboxAdmins" -SecurityGroup MailboxAdmins -Role "Exchange Servers" -CustomConfigWriteScope "Mailbox Servers"
```

В предыдущем примере представлен процесс назначения роли с областью настройки сервера. Синтаксис для добавления области настройки базы данных одинаков. Вместо имени области сервера указывается имя области базы данных.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [New-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd335193\(v=exchg.150\)).

## Создание назначения ролей с областью применения в подразделениях

Если необходимо назначить подразделению область записи роли, можно указать это подразделение напрямую в параметре *RecipientOrganizationalUnitScope*. При использовании параметра *RecipientOrganizationalUnitScope* невозможно использовать параметр *CustomRecipientWriteScope*.

Используйте приведенный ниже синтаксис для назначения ролей универсальной группе безопасности и ограничения области записи роли для определенного подразделения.
```powershell
    New-ManagementRoleAssignment -Name <assignment name> -SecurityGroup <USG> -Role <role name> -RecipientOrganizationalUnitScope <OU>
```

В этом примере роль Mail Recipients назначается группе ролей SalesRecipientAdmins, затем область действия этого назначения сужается до подразделения sales/users в домене contoso.com.
```powershell
    New-ManagementRoleAssignment -Name "Mail Recipients_SalesRecipientAdmins" -SecurityGroup SalesRecipientAdmins -Role "Mail Recipients" -RecipientOrganizationalUnitScope contoso.com/sales/users
```

Дополнительные сведения о синтаксисе и параметрах см. в разделе [New-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd335193\(v=exchg.150\)).

## Создание назначения ролей с монопольной областью получателей или конфигураций

Чтобы создать монопольное назначение ролей с монопольной областью получателей или конфигураций, можно использовать те же процедуры, приведенные в разделах Создание назначения роли с областью, основанной на фильтре получателей и Создание назначения роли с областью настройки на основе сервера, списка или фильтра серверов. Единственное отличие состоит в том, что при создании назначения ролей с монопольной областью, необходимо указать следующие исключительные параметры в зависимости от использования монопольной области получателей или монопольной области конфигураций.

  - **Монопольные области получателей**   Используйте параметр *ExclusiveRecipientWriteScope* вместо параметра *CustomRecipientWriteScope*.

  - **Монопольные области конфигураций**   Используйте параметр *ExclusiveConfigWriteScope* вместо параметра *CustomConfigWriteScope*.

При выполнении этой процедуры пользователи, которым была назначена роль, могут выполнять действия над объектами, включенными в монопольную область. Дополнительные сведения о монопольных областях см. в разделе [Общие сведения об исключительных областях](understanding-exclusive-scopes-exchange-2013-help.md).

Нельзя создать назначение ролей одновременно со стандартной и монопольной областью.

В этом примере роль Mail Recipients назначается универсальной группе безопасности Protected User Admins, а затем применяется область Protected Users.

```powershell
    New-ManagementRoleAssignment -Name "Mail Recipients_Protected User Admins" -SecurityGroup "Protected User Admins" -Role "Mail Recipients" -ExclusiveRecipientWriteScope "Protected Users"
```

Дополнительные сведения о синтаксисе и параметрах см. в разделе [New-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd335193\(v=exchg.150\)).

