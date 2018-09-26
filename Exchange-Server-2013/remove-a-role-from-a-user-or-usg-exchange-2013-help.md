---
title: 'Exchange 2013: удаление роли для пользователя или USG'
TOCTitle: Удалить роль из пользователя или универсальной группы безопасности
ms:assetid: df3510ef-e0c2-4d3c-81b0-7dc3e70c01a0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd351196(v=EXCHG.150)
ms:contentKeyID: 50489353
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Удалить роль из пользователя или универсальной группы безопасности

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-02_

Пользователю или универсальной группе безопасности можно назначить роль управления. При удалении назначения роли пользователи, имевшие эту роль, не смогут получать доступ к командлетам, которые доступны для этой роли. Дополнительные сведения о назначениях ролей управления в Microsoft Exchange Server 2013 см. в разделе [Общие сведения о назначениях ролей управления](understanding-management-role-assignments-exchange-2013-help.md).

Необходимы сведения о других задачах управления, связанных с ролями? См. раздел [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время выполнения процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Назначения ролей» в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Удаление назначения роли управления

Если известно имя назначения роли, которое необходимо удалить, используйте следующий синтаксис.

```powershell
Remove-ManagementRoleAssignment <assignment name>
```

Например, чтобы удалить назначение роли "Tier 2 Help Desk", выполните следующую команду.

```powershell
Remove-ManagementRoleAssignment "Tier 2 Help Desk Assignment"
```

Если имя назначения роли не известно, используйте следующий синтаксис.
```powershell
    Get-ManagementRoleAssignment -RoleAssignee <user or USG> -Role <role name> -Delegating <$true | $false> | Remove-ManagementRoleAssignment 
```
Например, если необходимо удалить назначение обычной роли получателей почты у пользователя davids, используйте следующую команду.
```powershell
    Get-ManagementRoleAssignment -RoleAssignee davids -Role "Mail Recipients" -Delegating $false | Remove-ManagementRoleAssignment
```
