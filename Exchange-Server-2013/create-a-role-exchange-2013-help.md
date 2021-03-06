﻿---
title: 'Создание роли: Exchange 2013 Help'
TOCTitle: Создание роли
ms:assetid: e614ad8f-5946-4135-b130-89ea626afcd4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd351214(v=EXCHG.150)
ms:contentKeyID: 50489388
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Создание роли

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-17_

Можно создать роль управления, изменить записи роли управления, при необходимости добавить область действия, а затем назначить роль уполномоченному роли. Выполнение этой процедуры понадобится нечасто. Рекомендуется проверить, нельзя ли вместо создания роли управления воспользоваться встроенной ролью управления. Список встроенных ролей управления см. в разделе [Встроенные роли управления](built-in-management-roles-exchange-2013-help.md).

Дополнительные сведения о ролях управления в Microsoft Exchange Server 2013 см. в разделе [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md).

> [!NOTE]  
> В этом разделе не рассматривается создание роли управления с незаданной областью. Сведения о создании роли управления с незаданной областью см. в разделе <a href="create-an-unscoped-role-exchange-2013-help.md">Создание роли с незаданной областью</a>.


Необходимы сведения о других задачах управления, связанных с ролями? См. раздел [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время выполнения процедуры: 10 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Роли управления» в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Как это сделать?

## Шаг 1. Создание роли управления

Новые роли управления основаны на существующих ролях. При создании роли существующая роль и ее записи роли управления копируются в новую роль. Существующая роль становится родительской для новой дочерней роли. Всегда необходимо выбирать роль, содержащую все командлеты и параметры, которые нужно использовать, а затем удалять ненужные компоненты. Дочерние роли не могут содержать записи роли управления, отсутствующие в родительской роли.

Для создания новой роли используйте следующий синтаксис.

```powershell
New-ManagementRole -Parent <existing role to copy> -Name <name of new role>
```

В этом примере роль получателей почты и соответствующие записи роли управления копируются в роль Seattle Mail Recipients.

```powershell
New-ManagementRole -Parent "Mail Recipients" -Name "Seattle Mail Recipients"
```

Подробные сведения о синтаксисе и параметрах см. в разделе [New-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd298073\(v=exchg.150\)).

## Шаг 2. Изменение записей новой роли управления

После создания роли необходимо изменить записи роли. Можно удалить всю запись роли, которая полностью удаляет доступ к связанному командлету. Либо можно удалить из записи роли параметры, чтобы удалить доступ к этим конкретным параметрам связанного командлета.

Нельзя добавить новые записи роли или параметры в записи роли, если они отсутствуют в родительской роли. Так как в первом шаге была создана роль из родительской роли, невозможно добавлять дополнительные записи роли или параметры записей, потому что они не существуют в родительской роли.

При изменении записи роли можно выполнить одно из следующих действий:

  - Удалить полностью одну запись роли.

  - Удалить полностью несколько записей роли.

  - Удалить параметры из записи роли.

Инструкции по удалению записи роли из новой роли см. в разделе [Удаление записи роли из роли](remove-a-role-entry-from-a-role-exchange-2013-help.md).

## Шаг 3. Создание при необходимости настраиваемой области действия роли управления

Области действия роли управления определяют объекты, доступные пользователю для просмотра или изменения, используя записи роли, настроенные в шаге 2. Новые роли управления наследуют области чтения и записи своих родительских ролей управления. Эти области называются *неявными областями*. Но возможны случаи, когда нужно изменить область записи новой роли в соответствии с потребностями предприятия. Создание настраиваемой области переопределяет неявную область записи для роли. Неявная область чтения для роли не меняется. Дополнительные сведения об областях действия для ролей управления см. в разделе [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md).

Можно создать настраиваемую область, создать исключительную область, использовать предопределенную область или задать область назначения для подразделения. Новая область должна содержаться в неявной области чтения роли. Чтобы использовать предопределенную область или задать подразделение, перейдите к шагу 4.

Чтобы добавить настраиваемую область в новую роль, см. раздел [Создание регулярной или монопольной области](create-a-regular-or-exclusive-scope-exchange-2013-help.md).

## Шаг 4. Назначение новой роли управления

Последним шагом при создании и настройке роли является ее назначение уполномоченному роли.

При создании назначения роли можно выбрать одно из следующих действий:

  - Создание назначения роли без области.

  - Создание назначения роли с предварительно определенной областью.

  - Создание назначения роли с подразделением без фильтра ограничений домена.

  - Создание назначения роли с настраиваемой или исключительной областью, созданной в шаге 3.
    
    > [!NOTE]  
    > Нельзя задать область, создавая назначение роли для политики назначения ролей управления.


Можно назначить новую роль группе ролей, политике назначения ролей, пользователю или универсальной группе безопасности. Дополнительные сведения приведены в следующих разделах:

  - [Управление группами ролей](manage-role-groups-exchange-2013-help.md)

  - [Управление политиками назначения ролей](manage-role-assignment-policies-exchange-2013-help.md)

  - [Добавление роли для пользователя или универсальной группы безопасности](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

