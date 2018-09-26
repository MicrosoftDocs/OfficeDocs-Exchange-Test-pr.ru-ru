---
title: 'Управление группами связанных ролей: Exchange 2013 Help'
TOCTitle: Управление группами связанных ролей
ms:assetid: e2a07395-90c2-4d62-b15d-ac3ff28fe786
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ657502(v=EXCHG.150)
ms:contentKeyID: 50489260
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Управление группами связанных ролей

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-09_

Чтобы разрешить участникам универсальной группы безопасности (USG) в лесу внешнего Active Directory для управления организацией Exchange Server 2013 Microsoft в лесу Active Directory ресурсов можно использовать группы ролей управления связанных. Связывая универсальной группы безопасности в внешнего леса со связанной группой ролей, при члены, универсальной группы безопасности предоставляются разрешения, предоставленные роли управления, назначенные связанная группа ролей. Дополнительные сведения о группах связанных ролей можно [Общие сведения о группах ролей управления](understanding-management-role-groups-exchange-2013-help.md).

Создание и Настройка групп связанных ролей, необходимо использовать командлеты **New-RoleGroup** и **Set-RoleGroup** . Подробный синтаксис и сведений о параметрах содержатся в следующих разделах:

  - [New-RoleGroup](https://technet.microsoft.com/ru-ru/library/dd638181\(v=exchg.150\))

  - [Set-RoleGroup](https://technet.microsoft.com/ru-ru/library/dd638182\(v=exchg.150\))

Дополнительные сведения о задачах управления, связанных с группами ролей, см. в разделе [Разрешения](permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: от 5 до 10 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Группы ролей» в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Нельзя использовать Центр администрирования Exchange (EAC) для создания или настройки групп связанных ролей. Необходимо использовать консоль управления Exchange.

  - Как минимум для настройки связанной группой ролей требуется установлено, что одностороннее отношение доверия между Active Directory леса ресурсов, в которой будет находиться связанная группа ролей и внешнего Active Directory леса, где находятся пользователи или универсальным группам безопасности. Внешний лес необходимо доверием леса ресурсов.

  - Необходимо иметь следующие сведения о внешнем лесе Active Directory:
    
      - **Учетные данные**   Необходимо иметь имя пользователя и пароль, который можно получить доступ к лесу внешнего Active Directory. Эта информация используется совместно с параметром *LinkedCredential* в командлетах **New-RoleGroup** и **Set-RoleGroup** .
    
      - **Контроллер домена**   Необходимо иметь полное доменное имя (FQDN) контроллера домена Active Directory в лесу внешнего Active Directory. Эта информация используется совместно с параметром *LinkedDomainController* в командлетах **New-RoleGroup** и **Set-RoleGroup** .
    
      - **Внешней универсальной группы безопасности**   Необходимо иметь полное имя универсальной группы безопасности в лесу внешнего Active Directory, который содержит элементы, которые необходимо связать с связанная группа ролей. Эта информация используется совместно с параметром *LinkedForeignGroup* в командлете **New-RoleGroup** и **Set-RoleGroup** .

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Создание связанной группой ролей

## Использование командной консоли для создания связанной группы ролей без области

Чтобы создать связанную группу ролей и назначить роли управления для этой группы, выполните следующие действия:

1.  Сохраните учетные данные внешнего леса Active Directory в переменной.
    
    ```powershell
	$ForeignCredential = Get-Credential
	```

2.  Создайте связанную группу ролей, используя следующую синтаксическую конструкцию.
    ```powershell
        New-RoleGroup <role group name> -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential -Roles <role1, role2, role3...>
	```
3.  Добавьте или удалите участников внешней универсальной группы безопасности с помощью средства «Пользователи и компьютеры Active Directory» на компьютере во внешнем лесу Active Directory.

В данном примере выполняется следующее:

  - Извлекаются учетные данные внешнего леса Active Directory с именем users.contoso.com. Эти данные используются для подключения к контроллеру домена DC01.users.contoso.com во внешнем лесу.

  - Создание связанной группой ролей вызывает группу ролей соответствия требованиям в ресурсов леса, где установлен Exchange 2013.

  - Новая группа ролей связывается с универсальной группой безопасности «Администраторы по соответствию требованиям» во внешнем лесу users.contoso.com Active Directory.

  - Связанной группе ролей назначаются роли управления правилами транспорта и ведением журнала.

<!-- end list -->

```powershell
$ForeignCredential = Get-Credential
```
```powershell
    New-RoleGroup "Compliance Role Group" -LinkedForeignGroup "Compliance Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -Roles "Transport Rules", "Journaling"
```
## Использование командной консоли для создания связанной группы ролей с настраиваемой областью управления

Можно создавать связанные группы ролей с настраиваемыми областями управления получателями, настраиваемыми областями управления конфигурацией или обоих видов. Чтобы создать связанную группу ролей и назначить для этой группы роли управления с настраиваемыми областями, выполните следующие действия:

1.  Сохраните учетные данные внешнего леса Active Directory в переменной.
    
    ```powershell
	$ForeignCredential = Get-Credential
	```

2.  Создайте связанную группу ролей, используя следующую синтаксическую конструкцию.
    ```powershell
        New-RoleGroup <role group name> -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -CustomConfigWriteScope <name of configuration scope> -CustomRecipientWriteScope <name of recipient scope> -LinkedCredential $ForeignCredential -Roles <role1, role2, role3...>
	```
3.  Добавьте или удалите участников внешней универсальной группы безопасности с помощью средства «Пользователи и компьютеры Active Directory» на компьютере во внешнем лесу Active Directory.

В данном примере выполняется следующее:

  - Извлекаются учетные данные внешнего леса Active Directory с именем users.contoso.com. Эти данные используются для подключения к контроллеру домена DC01.users.contoso.com во внешнем лесу.

  - Создание связанной группой ролей вызывает группу ролей Сиэтл соответствия требованиям в ресурсов леса, где установлен Exchange 2013.

  - Новая группа ролей связывается с универсальной группой безопасности «Администраторы по соответствию требованиям Сиэтла» во внешнем лесу users.contoso.com Active Directory.

  - Новой связанной группе ролей с настраиваемой областью получателей «Получатели Сиэтла» назначаются роли управления правилами транспорта и ведением журнала.

<!-- end list -->

```powershell
    $ForeignCredential = Get-Credential
    New-RoleGroup "Seattle Compliance Role Group" -LinkedForeignGroup "Seattle Compliance Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -CustomRecipientWriteScope "Seattle Recipients" -Roles "Transport Rules", "Journaling"
```

Дополнительные сведения об областях управления см. в разделе [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md).

## Использование командной консоли для создания связанной группы ролей с областью подразделения

Можно создавать связанные группы ролей, использующие область получателя подразделения. Чтобы создать связанную группу ролей и назначить для этой группы роли управления с областью подразделения, выполните следующие действия:

1.  Сохраните учетные данные внешнего леса Active Directory в переменной.
    
    ```powershell
	$ForeignCredential = Get-Credential
	```

2.  Создайте связанную группу ролей, используя следующую синтаксическую конструкцию.
    ```powershell
        New-RoleGroup <role group name> -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential -RecipientOrganizationalUnitScope <OU name> -Roles <role1, role2, role3...>
	```
3.  Добавьте или удалите участников внешней универсальной группы безопасности с помощью средства «Пользователи и компьютеры Active Directory» на компьютере во внешнем лесу Active Directory.

В данном примере выполняется следующее:

  - Извлекаются учетные данные внешнего леса Active Directory с именем users.contoso.com. Эти данные используются для подключения к контроллеру домена DC01.users.contoso.com во внешнем лесу.

  - Создание связанной группой ролей называется группа ролей соответствия руководители ресурсов леса, где установлен Exchange 2013.

  - Новая группа ролей связывается с универсальной группой безопасности «Администраторы по соответствию требованиям руководителей» во внешнем лесу users.contoso.com Active Directory.

  - Назначаются роли управления правилами транспорта и ведением журнала для новой связанной группы ролей с областью получателей подразделения «Руководители».

<!-- end list -->

```powershell
$ForeignCredential = Get-Credential
```
```powershell
    New-RoleGroup "Executives Compliance Role Group" -LinkedForeignGroup "Executives Compliance Administrators" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential -RecipientOrganizationalUnitScope "Executives OU" -Roles "Transport Rules", "Journaling"
```
Дополнительные сведения об областях управления см. в разделе [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md).

## Изменение внешней универсальной группы безопасности в связанной группой ролей

## Использование командной консоли для изменения внешней универсальной группы безопасности для связанной группы ролей

Чтобы изменить внешнюю универсальную группу безопасности, сопоставленную со связанной группой ролей, выполните следующие действия.

1.  Сохраните учетные данные внешнего леса Active Directory в переменной.
    
    ```powershell
	$ForeignCredential = Get-Credential
	```

2.  Изменение внешней универсальной группы безопасности на существующий связанная группа ролей, используя следующий синтаксис.
    ```powershell
        Set-RoleGroup <role group name> -LinkedForeignGroup <name of foreign USG> -LinkedDomainController <FQDN of foreign Active Directory domain controller> -LinkedCredential $ForeignCredential 
	```
В данном примере выполняется следующее:

  - Извлекаются учетные данные внешнего леса Active Directory с именем users.contoso.com. Эти данные используются для подключения к контроллеру домена DC01.users.contoso.com во внешнем лесу.

  - Изменяется внешняя универсальная группа безопасности для группы ролей Compliance Role Group на Regulatory Compliance Officers.

<!-- end list -->

```powershell
$ForeignCredential = Get-Credential
```
```powershell
    Set-RoleGroup "Compliance Role Group" -LinkedForeignGroup "Regulatory Compliance Officers" -LinkedDomainController DC01.users.contoso.com -LinkedCredential $ForeignCredential
```
