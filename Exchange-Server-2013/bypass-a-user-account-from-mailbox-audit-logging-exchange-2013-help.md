﻿---
title: 'Обход сервера-посредника пользователя для учетной записи аудита почтовых ящиков ведения журнала: Exchange 2013 Help'
TOCTitle: Обход сервера-посредника пользователя для учетной записи аудита почтовых ящиков ведения журнала
ms:assetid: 98a87071-fe31-4b67-beb8-a73799e54df2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff461934(v=EXCHG.150)
ms:contentKeyID: 50488717
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Обход сервера-посредника пользователя для учетной записи аудита почтовых ящиков ведения журнала

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2013-05-21_

При включении ведения журнала аудита для почтового ящика указанные события доступа к почтовому ящику (например, доступ к папке или сообщению либо окончательное удаление сообщения) заносятся в журнал. Тем не менее, при доступе с помощью некоторых авторизованных учетных записей, например используемых средствами сторонних производителей или для отслеживания исполнения законодательства, возможно создание большого числа записей журнала аудита почтового ящика, что может являться проблемой для организации.

Можно настроить пропуск ведения журнала аудита почтовых ящиков для учетной записи пользователя или компьютера, чтобы действия, выполняемые этим пользователем или учетной записью для всех почтовых ящиков, не заносились в журнал. Пропуск доверенных учетных записей пользователей или компьютеров, которым необходим частый доступ к почтовым ящикам, позволяет сократить уровень шума в журналах аудита почтовых ящиков.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.Caution(EXCHG.150).gif" title="Внимание!" alt="Внимание!" />Внимание!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если ведение журнала аудита почтовых ящиков используется для аудита доступа к почтовым ящикам и действий с ними, необходимо регулярно отслеживать связи пропуска аудита почтовых ящиков. Если для учетной записи добавлена связь пропуска аудита почтовых ящиков, то эта учетная запись позволяет получать доступ ко всем почтовым ящикам в организации, на доступ к которым ей предоставлены разрешения, и выполнять различные действия, например удалять сообщения, без внесения записей в журнал аудита почтовых ящиков.</td>
</tr>
</tbody>
</table>


Дополнительные задачи управления, связанные с журналом аудита почтовых ящиков, см. в разделе [Процедуры ведения журнала аудита почтовых ящиков](mailbox-audit-logging-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 1 минута.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Ведение журнала аудита почтовых ящиков" в разделе [Политика обмена сообщениями и разрешения для соответствия требованиям](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Если для учетной записи настроен пропуск ведения журнала аудита почтовых ящиков, сведения о доступе в любой почтовый ящик с помощью этой учетной записи не будут заноситься в журнал. Для учетной записи невозможно настроить пропуск ведения журнала доступа в определенный почтовый ящик.

  - Вы можете использовать Центр администрирования Exchange для включения или отключения пропуска ведения журнала аудита почтовых ящиков для учетной записи. Необходимо использовать командную консоль.

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


## Включение или отключение обхода журнала аудита для учетной записи с помощью командной консоли

Пример включения обхода журнала аудита почтовых ящиков для учетной записи см. в разделе [Examples](https://technet.microsoft.com/ru-ru/ff696758\(exchg.150\)#examples) в [Set-MailboxAuditBypassAssociation](https://technet.microsoft.com/ru-ru/library/ff696758\(v=exchg.150\)).

Пример отключения обхода журнала аудита почтовых ящиков для учетной записи см. в разделе [Examples](https://technet.microsoft.com/ru-ru/ff696758\(exchg.150\)#examples) статьи [Set-MailboxAuditBypassAssociation](https://technet.microsoft.com/ru-ru/library/ff696758\(v=exchg.150\)).

## Как проверить, что все получилось?

После исключения учетной записи пользователя из журнала аудита почтовых ящиков, можно проверить настройки, выполнив командлет [Get-MailboxAuditBypassAssociation](https://technet.microsoft.com/ru-ru/library/ff696741\(v=exchg.150\)).

Примеры проверки связей обхода аудита почтовых ящиков см. в разделе [Examples](https://technet.microsoft.com/ru-ru/ff696741\(exchg.150\)#examples) статьи [Get-MailboxAuditBypassAssociation](https://technet.microsoft.com/ru-ru/library/ff696741\(v=exchg.150\)).
