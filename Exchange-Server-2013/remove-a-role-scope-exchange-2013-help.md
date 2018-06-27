---
title: 'Удаление области роли: Exchange 2013 Help'
TOCTitle: Удаление области роли
ms:assetid: ad17cba0-a8d3-4f40-b3c9-c37e6e5c3f36
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd351051(v=EXCHG.150)
ms:contentKeyID: 50488837
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Удаление области роли

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2012-10-02_

Управление областями ролей служит для определения, какие объекты будут доступны пользователям, которые, в свою очередь, смогут изменять эти объекты с помощью назначенных для этих пользователей командлетов и параметров. Если область больше не используется, ее можно удалить. Дополнительные сведения об областях ролей управления в Microsoft Exchange Server 2013 см. в разделе [Общие сведения об областях ролей управления](understanding-management-role-scopes-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Области управления" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - Прежде чем удалить область, необходимо удалить эту область из всех назначений ролей управления, в которых она может использоваться. Дополнительные сведения о порядке удаления области из назначения роли см. в разделе [Изменение назначения роли](change-a-role-assignment-exchange-2013-help.md).

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


## Удаление области с помощью командной консоли

Чтобы удалить область, используйте следующий синтаксис.

    Remove-ManagementScope <scope name>

Например, чтобы удалить область Dublin Servers, используйте следующую команду.

    Remove-ManagementScope "Dublin Servers"

