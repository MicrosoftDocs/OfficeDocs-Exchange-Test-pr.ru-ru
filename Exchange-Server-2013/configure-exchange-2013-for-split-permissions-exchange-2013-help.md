---
title: 'Настройка разделенных разрешений в Exchange 2013: Exchange 2013 Help'
TOCTitle: Настройка разделенных разрешений в Exchange 2013
ms:assetid: 8c74f893-a6f3-4869-8571-3bc0f662cc87
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638155(v=EXCHG.150)
ms:contentKeyID: 50488599
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка разделенных разрешений в Exchange 2013

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-07_

Благодаря разделенным разрешениям можно включить две отдельные группы, например администраторов Active Directory и администраторов Microsoft Exchange Server 2013, для управления соответствующими службами, объектами и атрибутами. Администраторы Active Directory управляют участниками безопасности, например пользователями, которые предоставляют разрешения на доступ к лесу Active Directory. Администраторы Exchange управляют связанными с Exchange атрибутами объектов Active Directory, а также отвечают за создание и контроль объектов, относящихся к Exchange.

Microsoft Exchange Server 2013 предлагает следующие типы моделей разделенных разрешений.

  - **Разделенные разрешения RBAC**   Разрешения на создание участников безопасности в разделе домена Active Directory контролируются моделью управления доступом на основе ролей (RBAC). Только члены соответствующих групп ролей могут создавать участников безопасности.

  - **Разделенные разрешения Active Directory**   Разрешения на создание субъектов безопасности в разделе домена Active Directory полностью удаляются из настроек пользователя, службы или сервера Exchange. В модели RBAC отсутствует возможность создания участников безопасности. Эта процедура должна выполняться в службе Active Directory с помощью средств управления Active Directory.
    
    > [!NOTE]  
    > Разделенные разрешения Active Directory доступны в организациях с Microsoft Exchange Server 2010 с пакетом обновления 1 (SP1) или более поздней версией, Exchange 2013 или обеими версиями Exchange.


Выбор модели зависит от структуры и потребностей организации. Выберите процедуру, применимую к модели, которую необходимо настроить. Рекомендуется использовать модель разделения разрешений RBAC. Модель разделения разрешений RBAC обеспечивает значительно большую гибкость при сохранении почти такого же разделения администрирования, как при разделении разрешений Active Directory.

Дополнительные сведения о разрешениях на совместный и раздельный доступ см. в разделе [Общие сведения о разделенных разрешениях](understanding-split-permissions-exchange-2013-help.md).

Дополнительные сведения о группах ролей управления, ролях управления, регулярных назначениях ролей управления и назначениях делегирования ролей управления см. в следующих разделах:

  - [Общие сведения об управлении доступом на основе ролей](understanding-role-based-access-control-exchange-2013-help.md)

  - [Общие сведения о группах ролей управления](understanding-management-role-groups-exchange-2013-help.md)

  - [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md)

  - [Общие сведения о назначениях ролей управления](understanding-management-role-assignments-exchange-2013-help.md)

Необходимы сведения о других задачах управления, связанных с разрешениями? см. в разделе [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Разделение разрешений Active Directory" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать Windows PowerShell, командную консоль Windows или оба этих средства. Дополнительные сведения см. в каждой процедуре.

  - Если в организации присутствуют серверы Exchange 2010, выбранная модель разрешений будет также применена и к этим серверам.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Переключение на разделение разрешений RBAC

В организации Exchange 2013 можно настроить разделение разрешений RBAC. После завершения настройки только администраторы Active Directory смогут создавать участников безопасности Active Directory. Это означает, что администраторы Exchange не смогут использовать следующие командлеты:

  - **New-Mailbox**

  - **New-MailContact**

  - **New-MailUser**

  - **New-RemoteMailbox**

  - **Remove-Mailbox**

  - **Remove-MailContact**

  - **Remove-MailUser**

  - **Remove-RemoteMailbox**

Администраторы Exchange будут управлять только атрибутами Exchange для существующих участников безопасности Active Directory. Однако они смогут создавать объекты, связанные с Exchange, например правила транспорта и группы рассылки, а также управлять этими объектами. Дополнительные сведения см. в подразделе "Разделение разрешений RBAC" в разделе [Общие сведения о разделенных разрешениях](understanding-split-permissions-exchange-2013-help.md).

Для настройки в Exchange 2013 разделения разрешений необходимо группе ролей назначить роль создания получателей почты и роль создания и участия в группе безопасности, которая также содержит участников, являющихся администраторами Active Directory. После этого необходимо удалить назначения между этими ролями и любой группой ролей или универсальной группой безопасности (USG), содержащей администраторов Exchange.

Чтобы настроить разделение разрешений RBAC, выполните следующие действия.

1.  Если организация в данный момент настроена для разделенных разрешений Active Directory, выполните следующие действия в командной строке командной консоли Windows.
    
    1.  Отключите разделенные разрешения Active Directory, выполнив следующую команду с установочного носителя Exchange 2013.
        
        ```powershell
            setup.exe /PrepareAD /ActiveDirectorySplitPermissions:false
        ```
    
    2.  Перезапустите серверы Exchange 2013 в организации или подождите, пока маркер доступа к службе каталогов Active Directory не будет реплицирован на все серверы Exchange 2013.
        
        > [!NOTE]  
        > Если в организации есть серверы Exchange 2010, их также нужно перезагрузить.


2.  В командной консоли Exchange выполните следующие действия:
    
    1.  Создайте группу ролей для администраторов Active Directory. Кроме создания группы ролей, команда создает стандартные назначения ролей между новой группой ролей и ролью создания получателей почты, а также ролью создания и участия в группе безопасности.
        
        ```powershell
            New-RoleGroup "Active Directory Administrators" -Roles "Mail Recipient Creation", "Security Group Creation and Membership"
        ```

        > [!NOTE]  
        > Если требуется, чтобы члены этой группы ролей могли создавать назначения ролей, включите роль управления ролями. Нет необходимости добавлять эту роль сейчас. Тем не менее, если в какой-либо момент потребуется назначить роль создания получателей почты (Mail Recipient Creation) или роль создания и участия в группе безопасности (Security Group Creation and Membership) другим уполномоченным ролей, то роль управления ролями должна быть назначена этой новой группе ролей. Ниже приводится процедура настройки группы ролей администраторов Active Directory в качестве единственной группы ролей, которая может делегировать эти роли.
    
    2.  Создайте назначения ролей делегирования между новой группой ролей, с одной стороны, и ролью создания получателей почты (Mail Recipient Creation) и ролью создания и участия в группе безопасности (Security Group Creation and Membership), с другой стороны, с помощью следующих команд.
        
        ```powershell
            New-ManagementRoleAssignment -Role "Mail Recipient Creation" -SecurityGroup "Active Directory Administrators" -Delegating
            New-ManagementRoleAssignment -Role "Security Group Creation and Membership" -SecurityGroup "Active Directory Administrators" -Delegating
        ```

    3.  Добавьте участников в новую группу ролей с помощью следующей команды.
        
        ```powershell
        Add-RoleGroupMember "Active Directory Administrators" -Member <user to add>
        ``` 
    
    4.  Замените список делегатов на новую группу ролей, чтобы только участники группы ролей могли добавлять или удалять участников.
        
        ```powershell
        Set-RoleGroup "Active Directory Administrators" -ManagedBy "Active Directory Administrators"
        ```
        
        > [!IMPORTANT]  
        > Члены группы ролей Управление организацией, а также те, которым назначена роль управления ролями напрямую или через другую группу ролей либо универсальную группу безопасности, могут пропускать проверку безопасности делегатов. Чтобы запретить администратору Exchange добавлять себя в новую группу ролей, необходимо удалить назначение роли между ролью управления ролями и любым администратором Exchange, а затем назначить ее другой группе.
    
    5.  Найдите все назначения стандартных ролей и назначения ролей делегирования для роли создания получателей почты с помощью следующей команды. Данная команда отображает только свойства **Name**, **Role** и **RoleAssigneeName**.
        
        ```powershell
            Get-ManagementRoleAssignment -Role "Mail Recipient Creation" | Format-Table Name, Role, RoleAssigneeName -Auto
        ```

    6.  Удалите все назначения стандартных ролей и ролей делегирования для роли создания получателей почты, не связанные с новой группой ролей или с любыми другими группами, универсальными группами безопасности или прямыми назначениями, которые необходимо сохранить, с помощью следующей команды.
        
        ```powershell
        Remove-ManagementRoleAssignment <Mail Recipient Creation role assignment to remove>
        ```
        
        > [!NOTE]  
        > Если требуется удалить все назначения обычной роли и роли делегирования для роли создания получателей почты (Mail Recipient Creation) по отношению к уполномоченному роли, не связанному с группой ролей администраторов Active Directory, используйте следующую команду. Параметр <em>WhatIf</em> позволяет увидеть, какие назначения ролей будут удалены. Удалите параметр <em>WhatIf</em> и снова запустите команду, чтобы удалить назначения ролей.
        
        ```powershell
            Get-ManagementRoleAssignment -Role "Mail Recipient Creation" | Where { $_.RoleAssigneeName -NE "Active Directory Administrators" } | Remove-ManagementRoleAssignment -WhatIf
        ```

    7.  Найдите все назначения стандартных ролей и назначения ролей делегирования для роли создания и участия в группе безопасности (Security Group Creation and Membership) с помощью следующей команды. Данная команда отображает только свойства **Name**, **Role** и **RoleAssigneeName**.
        
        ```powershell
            Get-ManagementRoleAssignment -Role "Security Group Creation and Membership" | Format-Table Name, Role, RoleAssigneeName -Auto
        ```

    8.  Удалите все назначения стандартных ролей и ролей делегирования для роли создания и участия в группе безопасности (Security Group Creation and Membership), не связанные с новой группой ролей или с любыми другими группами, универсальными группами безопасности или прямыми назначениями, которые необходимо сохранить, с помощью следующей команды:
        
        ```powershell
            Remove-ManagementRoleAssignment <Security Group Creation and Membership role assignment to remove>
        ```

        > [!NOTE]  
        > Такую же команду из предыдущего замечания можно использовать с целью удаления всех назначений стандартных ролей и ролей делегирования для роли создания и участия в группе безопасности по отношению к любому уполномоченному роли, не связанному с группой ролей администраторов Active Directory, как показано в этом примере.
        
        ```powershell
            Get-ManagementRoleAssignment -Role "Security Group Creation and Membership" | Where { $_.RoleAssigneeName -NE "Active Directory Administrators" } | Remove-ManagementRoleAssignment -WhatIf
        ```

Подробные сведения о синтаксисе и параметрах см. в следующих разделах:

  - [New-RoleGroup](https://technet.microsoft.com/ru-ru/library/dd638181\(v=exchg.150\))

  - [New-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd335193\(v=exchg.150\))

  - [Add-RoleGroupMember](https://technet.microsoft.com/ru-ru/library/dd638207\(v=exchg.150\))

  - [Set-RoleGroup](https://technet.microsoft.com/ru-ru/library/dd638182\(v=exchg.150\))

  - [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\))

  - [Remove-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351205\(v=exchg.150\))

## Переключение на разделение разрешений Active Directory

Организацию Exchange 2013 можно настроить на разделение разрешений Active Directory. При разделении разрешений Active Directory полностью удаляются разрешения, которые позволяют администраторам и серверам Exchange создавать участников безопасности в службе Active Directory или изменять не связанные с системой Exchange атрибуты этих объектов. После завершения настройки только администраторы Active Directory смогут создавать участников безопасности Active Directory. Это означает, что администраторы Exchange не смогут использовать следующие командлеты:

  - **Add-DistributionGroupMember**

  - **New-DistributionGroup**

  - **New-Mailbox**

  - **New-MailContact**

  - **New-MailUser**

  - **New-RemoteMailbox**

  - **Remove-DistributionGroup**

  - **Remove-DistributionGroupMember**

  - **Remove-Mailbox**

  - **Remove-MailContact**

  - **Remove-MailUser**

  - **Remove-RemoteMailbox**

  - **Update-DistributionGroupMember**

Администраторы и серверы Exchange будут управлять только атрибутами Exchange для существующих участников безопасности Active Directory. Однако они смогут создавать объекты, связанные с Exchange, например правила транспорта и абонентские группы единой системы обмена сообщениями, а также управлять этими объектами.

> [!CAUTION]  
> После включения разделения разрешений Active Directory администраторы и серверы Exchange больше не смогут создавать участников безопасности в службе Active Directory, а также управлять составом групп рассылки. Эти задачи должны выполняться с помощью средств управления Active Directory с необходимыми разрешениями Active Directory. Прежде чем вносить эти изменения, необходимо понять, какое влияние они окажут на процессы администрирования и сторонние приложения, которые интегрируются в систему Exchange 2013 и модель разрешений RBAC.<br />
Дополнительные сведения см. в подразделе &quot;Разделенные разрешения Active Directory&quot; в разделе <a href="understanding-split-permissions-exchange-2013-help.md">Общие сведения о разделенных разрешениях</a>.


Чтобы переключиться с разрешений общего доступа или разделения разрешений RBAC на разделение разрешений Active Directory, выполните следующие действия:

1.  Чтобы включить разделенные разрешения Active Directory, в командной консоли Windows выполните следующую команду с установочного носителя Exchange 2013.
    
    ```powershell
        setup.exe /PrepareAD /ActiveDirectorySplitPermissions:true
    ```

2.  Если в организации имеется несколько доменов Active Directory, необходимо либо запустить `setup.exe /PrepareDomain` в каждом дочернем домене, содержащем серверы или объекты Exchange, либо запустить `setup.exe /PrepareAllDomains` с сайта, где находится сервер Active Directory из каждого домена.

3.  Перезапустите серверы Exchange 2013 в организации или подождите, пока маркер доступа к Active Directory не будет реплицирован на все серверы Exchange 2013.
    
    > [!NOTE]  
    > Если в организации есть серверы Exchange 2010, их также нужно перезагрузить.

