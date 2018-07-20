---
title: 'Создание группы связанных ролей, которые зеркально встроенные группы ролей: Exchange 2013 Help'
TOCTitle: Создание группы связанных ролей, которые зеркально встроенные группы ролей
ms:assetid: 89dfcbb3-0568-4bbf-a885-746b91ba307e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd876918(v=EXCHG.150)
ms:contentKeyID: 50488582
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Создание группы связанных ролей, которые зеркально встроенные группы ролей

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-03_

При использовании связанных групп ролей управления в Microsoft Exchange Server 2013 можно связать группу ролей в лесу ресурсов Exchange 2013 с универсальной группой безопасности во внешнем лесу пользователя. Это полезно при необходимости, чтобы администраторы с учетными записями в лесу пользователя управляли серверами под управлением Exchange в лесу ресурсов. Дополнительные сведения о связанных группах ролей см. в разделе [Общие сведения о группах ролей управления](understanding-management-role-groups-exchange-2013-help.md).

По умолчанию Exchange 2013 включает в себя несколько встроенных групп ролей, предоставляющих разрешения для управления множеством функций и должностных обязанностей. Каждая группа ролей настроена на предоставление определенных разрешений для каждой функции и должностной обязанности. Однако эти группы ролей могут быть связаны с универсальными группами безопасности во внешнем лесу. Они могут содержать только пользователей и универсальные группы безопасности из леса локальных ресурсов. Однако эти встроенные группы ролей возможно реплицировать с помощью связанных групп ролей.

Можно заново создать каждую встроенную группу ролей как связанную группу ролей. Все роли и области управления, назначенные каждой группе ролей добавляются к новой связанной группе ролей. Дополнительные сведения о ролях и областях управления см. в следующих разделах:

  - [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md)

  - [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md)

Необходимы сведения о других задачах управления, связанных с группами ролей? см. в разделе [Разрешения](permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 10 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Группы ролей" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - Для настройки связанной группы ролей необходимо одностороннее доверие между лесом ресурсов Active Directory, в котором находится связанная группа ролей и внешним лесом Active Directory, в котором находятся пользователи или универсальные группы безопасности. Лес ресурсов должен иметь отношения доверия с внешним лесом.

  - Необходимо иметь следующие сведения о внешнем лесе Active Directory:
    
      - **Учетные данные**   Для доступа к внешнему лесу Active Directory необходимо иметь имя пользователя и пароль. Эти сведения используются с параметром *LinkedCredential* в командлете **New-RoleGroup**. Данные можно получить с помощью командлета **Get-Credential**. Формат имени пользователя выглядит следующим образом: *домен*\\*имя\_пользователя*.
    
      - **Контроллер домена**   Необходимо иметь полное доменное имя (FQDN) контроллера домена Active Directory во внешнем лесе Active Directory. Эти сведения используются с параметром *LinkedDomainController* в командлете **New-RoleGroup**.
    
      - **Внешняя универсальная группа безопасности**   Необходимо иметь полное имя универсальной группы безопасности во внешнем лесу Active Directory, содержащем участников, которых необходимо сопоставить со связанной группой ролей. Эти сведения используются с параметром *LinkedForeignGroup* в командлете **New-RoleGroup**.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной консоли для создания связанных групп ролей, реплицирующих встроенные группы ролей

В каждом из следующих разделов показано, как создать заново каждую группу ролей как связанную группу ролей. Следуйте инструкциям в каждом разделе для повторного создания всех встроенных групп ролей как связанных групп ролей.

## Создание связанной группы ролей управления организацией

Процесс повторного создания группы ролей Управление организацией как связанной группы отличается от процесса повторного создания других встроенных групп ролей. Это связано с тем, что группа ролей Управление организацией имеет назначения ролей делегирования между самой группой и всеми ролями управления. Для повторного создания назначений ролей делегирования требуется дополнительный шаг.

1.  Создайте универсальную группу безопасности во внешнем лесу, которая будет связана с группой ролей Управление организацией.

2.  Сохраните учетные данные внешнего леса Active Directory в переменной.
    
        $ForeignCredential = Get-Credential

3.  Сохраните все роли, назначенные группе ролей Управление организацией в переменной.
    
        $OrgMgmt  = Get-RoleGroup "Organization Management"

4.  Создайте связанную группу ролей Управление организацией и добавьте роли, назначенные встроенной группе ролей Управление организацией.
    
        New-RoleGroup "Organization Management - Linked" -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential -Roles $OrgMgmt.Roles

5.  Удалите все обычные назначения между новой связанной группой ролей Управление организацией и ролями, созданными конечным пользователем.
    
        Get-ManagementRoleAssignment -RoleAssignee "Organization Management - Linked" -Role My* | Remove-ManagementRoleAssignment

6.  Добавьте назначения ролей делегирования между новой связанной группой ролей Управление организацией и всеми ролями управления.
    
        Get-ManagementRole | New-ManagementRoleAssignment -SecurityGroup "Organization Management - Linked" -Delegating

В этом примере предполагается, что для каждого параметра используются следующие значения:

  - **LinkedForeignGroup** `Organization Management Administrators`

  - **LinkedDomainController** `DC01.users.contoso.com`

В этом примере группа ролей Управление организацией создается заново как связанная группа ролей с помощью значений, полученных в предыдущем шаге.

    $ForeignCredential = Get-Credential
    $OrgMgmt  = Get-RoleGroup "Organization Management"
    New-RoleGroup "Organization Management - Linked" -LinkedForeignGroup "Organization Management Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -Roles $OrgMgmt.Roles
    Get-ManagementRoleAssignment -RoleAssignee "Organization Management - Linked" -Role My* | Remove-ManagementRoleAssignment
    Get-ManagementRole | New-ManagementRoleAssignment -SecurityGroup "Organization Management - Linked" -Delegating

## Создание других связанных групп ролей

Чтобы заново создать встроенные группы ролей (отличные от группы ролей Управление организацией) в качестве связанных групп ролей, используйте следующую процедуру для каждой группы.

1.  Создайте универсальную группу безопасности во внешнем лесу для каждой группы ролей, которая будет связана с каждой новой группой ролей.

2.  Сохраните учетные данные внешнего леса Active Directory в переменной. Это необходимо сделать только один раз.
    
        $ForeignCredential = Get-Credential

3.  Получите список групп ролей, используя следующий командлет.
    
        Get-RoleGroup

4.  Для каждой группы ролей, отличной от группы ролей Управление организацией, выполните следующие действия.
    
        $RoleGroup = Get-RoleGroup <name of role group to re-create>
        New-RoleGroup "<role group name> - Linked" -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential -Roles $RoleGroup.Roles

5.  Повторите предыдущий шаг для каждой встроенной группы ролей, которую необходимо создать заново в качестве связанной группы ролей.

В этом примере предполагается, что для каждого параметра используются следующие значения:

  - **LinkedDomainController** `DC01.users.contoso.com`

  - **Встроенные группы ролей, которые будут повторно созданы в качестве связанных групп ролей** `Recipient Management, Server Management`

  - **Внешняя группа для связанной группы ролей управления получателями** `Recipient Management Administrators`

  - **Внешняя группа для связанной группы ролей управления сервером** `Server Management Administrators`

В этом примере Управление получателями и группы ролей управления сервером создаются заново как связанные группы ролей с помощью значений, полученных в предыдущем шаге.

    $ForeignCredential = Get-Credential
    Get-RoleGroup
    $RoleGroup = Get-RoleGroup "Recipient Management"
    New-RoleGroup "Recipient Management - Linked" -LinkedForeignGroup "Recipient Management Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -Roles $RoleGroup.Roles
    $RoleGroup = Get-RoleGroup "Server Management"
    New-RoleGroup "Server Management - Linked" -LinkedForeignGroup "Server Management Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -Roles $RoleGroup.Roles

## Другие задачи

После создания связанных групп ролей можно выполнить другие действия:

Добавить участников во внешние универсальные группы безопасности с помощью Active Directory "Пользователи и компьютеры" во внешнем лесу.

Удалить участников встроенных групп ролей. Дополнительные сведения см. в разделе [Управление участниками группы ролей](manage-role-group-members-exchange-2013-help.md).

Добавление, удаление или изменение области ролей в новых связанных группах ролей. Дополнительные сведения см. в разделе [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

Создать дополнительные связанные группы ролей. Дополнительные сведения см. в разделе [Управление группами связанных ролей](manage-linked-role-groups-exchange-2013-help.md).

