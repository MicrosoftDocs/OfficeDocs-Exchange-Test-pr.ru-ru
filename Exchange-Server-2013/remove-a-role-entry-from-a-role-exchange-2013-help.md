---
title: 'Удаление записи роли из роли: Exchange 2013 Help'
TOCTitle: Удаление записи роли из роли
ms:assetid: 4736367a-750f-44d3-8a20-5149bd35e9ff
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd297947(v=EXCHG.150)
ms:contentKeyID: 50487998
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Удаление записи роли из роли

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2012-10-03_

Записи ролей управления в роли управления определяют, какие командлеты и параметры доступны для этой роли управления. Удаляя записи ролей или параметры из записи роли, можно ограничивать действия пользователей, назначенных для этой роли управления. Дополнительные сведения о записях ролей управления в Microsoft Exchange Server 2013 см. в разделе [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md).

Необходимы сведения о других задачах управления, связанных с ролями? см. в разделе [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Роли управления" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

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

## Удаление отдельной записи роли из роли

При удалении записи роли из роли отменяются возможности доступа пользователей, назначенных для этой роли, к соответствующему командлету или сценарию.

Используйте следующий синтаксис для удаления всей записи роли управления из роли.

    Remove-ManagementRoleEntry <management role>\<management role entry>

В этом примере удаляется командлет **Enable-MailUser** из роли Seattle Server Administrators.

    Remove-ManagementRoleEntry "Seattle Server Administrators\Enable-MailUser"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd351187\(v=exchg.150\)).

## Удаление нескольких записей ролей из роли

При удалении нескольких записей ролей из роли отменяются возможности доступа пользователей, назначенных для этой роли, к соответствующим командлетам или сценариям.

Чтобы удалить несколько записей ролей из роли, необходимо получить список записей ролей с помощью командлета **Get-ManagementRoleEntry** cmdlet. Затем необходимо передать выходные данные в командлет **Remove-ManagementRoleEntry**. В командлете **Get-ManagementRoleEntry** можно использовать подстановочные знаки для выбора нескольких записей ролей. Рекомендуется использовать параметр *WhatIf* для проверки удаления только необходимых записей ролей. Используйте следующий синтаксис.

    Get-ManagementRoleEntry <management role>\<role entry with wildcard character> | Remove-ManagementRoleEntry -WhatIf

В следующем примере удаляются все записи ролей, которые содержат слово journal из роли Seattle Server Administrators.

    Get-ManagementRoleEntry "Seattle Server Administrators\*Journal*" | Remove-ManagementRoleEntry -WhatIf

При выполнении команды с параметром *WhatIf* командлет возвращает список всех записей ролей, которые будут удалены. Если список соответствует поставленной задаче, следует снова выполнить команду без параметра *WhatIf* для удаления записей ролей.

    Get-ManagementRoleEntry "Seattle Server Administrators\*Journal*" | Remove-ManagementRoleEntry

Дополнительные сведения о синтаксисе и параметрах см. в разделах [Get-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd335210\(v=exchg.150\)) и [Remove-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd351187\(v=exchg.150\)).

## Удаление параметров из записи роли в роли

При удалении параметров из записи роли в роли эти параметры перестают быть доступными пользователям, назначенным для этой роли.

Используйте следующий синтаксис для удаления параметров из записи роли.

    Set-ManagementRoleEntry <management role>\<role entry> -Parameters <parameter 1>,<parameter 2...> -RemoveParameter

В этом примере удаляются параметры *MaxSafeSenders*, *MaxSendSize*, *SecondaryAddress* и*UseDatabaseQuotaDefaults* из записи роли **Set-Mailbox** в роли Seattle Server Administrators.

    Set-ManagementRoleEntry "Seattle Server Administrators\Set-Mailbox" -Parameters MaxSafeSenders,MaxSendSize,SecondaryAddress,UseDatabaseQuotaDefaults -RemoveParameter

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd351162\(v=exchg.150\)).

