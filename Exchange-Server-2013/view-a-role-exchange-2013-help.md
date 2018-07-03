﻿---
title: 'Просмотр роли: Exchange 2013 Help'
TOCTitle: Просмотр роли
ms:assetid: 1875b15f-22db-4ede-b310-ea894d6211c8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd335117(v=EXCHG.150)
ms:contentKeyID: 50487548
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Просмотр роли

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-03_

Списки ролей управления могут быть получены различными способами, в зависимости от информации, которую необходимо получить. Например, могут быть возвращены только роли определенного типа, содержащие только определенные командлеты и параметры, а также просмотрены сведения определенной роли управления. Дополнительные сведения о ролях управления в Microsoft Exchange Server 2013 см. в разделе [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md).

Для получения сведений о том, как отобразить список всех записей ролей управления для роли, см. раздел [Просмотр записей роли](view-role-entries-exchange-2013-help.md).

Необходимы сведения о других задачах управления, связанных с ролями? см. в разделе [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Роли управления" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - В этом разделе описывается использование конвейерной передачи и командлетов **Format-List** и **Format-Table**. Дополнительные сведения об этих понятиях см. в следующих разделах:
    
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

## Просмотр определенной роли управления

Подробные сведения об определенной роли можно просмотреть путем получения определенной роли с помощью командлета **Get-ManagementRole** и передачи выходных данных в командлет **Format-List**.

Чтобы просмотреть подробные сведения об определенной роли, используйте следующий синтаксис.

    Get-ManagementRole <role name> | Format-List

В этом примере выполняется получение подробных сведений о роли управления "Получатели почты".

    Get-ManagementRole "Mail Recipients" | Format-List

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351125\(v=exchg.150\)).

## Получение списка всех ролей управления

Чтобы просмотреть список всех ролей управления в организации, не указывайте ролей при запуске командлета **Get-ManagementRole**. По умолчанию имя и тип каждой роли включены в результаты.

В этом примере показано возвращение списка всех ролей в организации.

    Get-ManagementRole

Для возврата списка определенных свойств для всех ролей в организации можно передать результаты выполнения командлета **Format-Table** и указать свойства, которые должны находиться в списке результатов. Используйте следующий синтаксис.

    Get-ManagementRole | Format-Table <property 1>, <property 2...>

В данном примере показано возвращение списка всех ролей в организации и включение свойства **Name**, а также любого свойства со словом **Implicit** в начало имени свойства.

    Get-ManagementRole | Format-Table Name, Implicit*

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351125\(v=exchg.150\)).

## Получение списка ролей управления, содержащих определенный командлет

Может быть возвращен список ролей, содержащий командлет, который был указан с помощью параметра *Cmdlet* командлета **Get-ManagementRole**.

Для возврата списка ролей, содержащих указанный командлет, используйте следующий синтаксис.

    Get-ManagementRole -Cmdlet <cmdlet>

В этом примере показано возвращение списка ролей, содержащих командлет **New-Mailbox**.

    Get-ManagementRole -Cmdlet New-Mailbox

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351125\(v=exchg.150\)).

## Получение списка ролей управления, содержащих определенный параметр

Список ролей, содержащих один или несколько указанных параметров, может быть возвращен с помощью параметра *CmdletParameters* командлета **Get-ManagementRole**. Будут возвращены только роли, содержащие указанные параметры.

При использовании параметра *CmdletParameters* можно включить параметр *Cmdlet*. При включении параметра *Cmdlet* возвращаются только роли, содержащие указанные параметpы определенного командлета. Если параметр *Cmdlet* не включен, роли, содержащие указанные параметры, будут возвращены независимо от командлета, в котором они находятся.

Для возврата списка ролей, содержащих указанные параметры, используйте следующий синтаксис.

    Get-ManagementRole [-Cmdlet <cmdlet>] -CmdletParameters <parameter 1>, <parameter 2...>

В данном примере показано возвращение списка ролей, содержащих параметры *Database* и *Server*, независимо от командлета, в котором они находятся.

    Get-ManagementRole -CmdletParameters Database, Server

В данном примере показано возвращение списка ролей, в которых параметр *EmailAddresses* содержится только в командлете **Set-Mailbox**.

    Get-ManagementRole -Cmdlet Set-Mailbox -CmdletParameters EmailAddresses

C параметрами *Cmdlet* или *CmdletParameters* можно использовать подстановочный знак (\*) для совпадения с частично введенными именами или параметрами командлетов.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351125\(v=exchg.150\)).

## Получение списка ролей управления определенного типа роли

С помощью параметра *RoleType* командлета **Get-ManagementRole** может быть возвращен список ролей, основанный на определенном типе роли.

Для возврата списка ролей, соответствующих указанному типу ролей, используйте следующий синтаксис.

    Get-ManagementRole -RoleType <roletype>

В данном примере показано возвращение списка ролей, основанного на типе роли `UmMailboxes`.

    Get-ManagementRole -RoleType UmMailboxes

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351125\(v=exchg.150\)).

## Получение списка непосредственных дочерних ролей родительской роли

Список непосредственных дочерних ролей указанной родительской роли может быть возвращен с помощью параметра *GetChildren* командлета **Get-ManagementRole**. Будут возвращены только роли с указанной родительской ролью.

Для возврата списка непосредственных дочерних ролей указанной родительской роли используйте следующий синтаксис.

    Get-ManagementRole <parent role name> -GetChildren

В данном примере выполняется возвращение списка непосредственных дочерних ролей родительской роли "Аварийное восстановление".

    Get-ManagementRole "Disaster Recovery" -GetChildren

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351125\(v=exchg.150\)).

## Получение списка всех дочерних ролей ниже родительской роли

Список всей цепочки ролей от указанной родительской роли до последней дочерней роли может быть возвращен с помощью параметра *Recurse* командлета **Get-ManagementRole**. Параметр *Recurse* указывает командлету **Get-ManagementRole** обойти все найденные родительские и дочерние отношения, пока не будет достигнута последняя дочерняя роль. Родительская роль включается в список, который будет возвращен.

В данном примере показано возвращение списка всех дочерних ролей родительской роли.

    Get-ManagementRole <parent role name> -Recurse

В данном примере показано возвращение всех дочерних ролей родительской роли "Получатели почты".

    Get-ManagementRole "Mail Recipients" -Recurse

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351125\(v=exchg.150\)).
