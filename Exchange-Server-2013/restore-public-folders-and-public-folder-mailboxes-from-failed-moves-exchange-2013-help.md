﻿---
title: 'Восстановление общедоступных папок и их почтовых ящиков после неудачных перемещений: Exchange 2013 Help'
TOCTitle: Восстановление общедоступных папок и их почтовых ящиков после неудачных перемещений
ms:assetid: 2ade83c9-5f9b-4945-bf32-48fa8185b515
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ983802(v=EXCHG.150)
ms:contentKeyID: 52061215
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Восстановление общедоступных папок и их почтовых ящиков после неудачных перемещений

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2013-02-13_

Если запрос на перемещение общедоступной папки или ее почтового ящика выполнен неудачно, можно восстановить эту папку или почтовый ящик при выполнении следующих условий.

  - **Неудачное перемещение общедоступной папки**   Обратимо удаленная копия общедоступной папки по-прежнему существует в исходном почтовом ящике общедоступной папки и срок ее хранения еще не истек.

  - **Неудачное перемещение почтового ящика общедоступной папки**   Обратимо удаленная копия почтового ящика общедоступной папки по-прежнему существует в исходной базе данных почтовых ящиков и срок ее хранения еще не истек.

Если срок хранения почтового ящика истек, можно восстановить отдельный почтовый ящик общедоступной папки из резервной копии. Затем данные из восстановленного почтового ящика извлекаются и копируются в целевую папку или добавляются в другой почтовый ящик. Подробнее см. в разделе [Восстановление данных с помощью базы данных восстановления](restore-data-using-a-recovery-database-exchange-2013-help.md).

Дополнительные сведения о задачах управления, связанных с общедоступными папками, см. в разделе [Процедуры с общедоступными папками](public-folder-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Запрос на восстановление почтового ящика» в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

  - Выполнение этой процедуры с помощью консоли администрирования Exchange невозможно. Необходимо использовать командную консоль.

  - Чтобы создать запрос на восстановление, необходимо задать значения параметров *DisplayName*, *LegacyDN* или *MailboxGUID* для обратимо удаленного почтового ящика общедоступной папки.

  - По умолчанию вместе с обычными папками восстанавливается и папка корзины. Чтобы не восстанавливать папку корзины, можно использовать командлет *ExcludeDumpster*.

  - Процесс восстановления почтовых ящиков общедоступных папок отличается от процесса восстановления обычных почтовых ящиков тем, что папки не будут созданы, если таких же папок нет в целевом почтовом ящике. Список недостающих папок будет отображен в предупреждающем сообщении в конце выполнения запроса на восстановление.

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

## Восстановление обратимо удаленной общедоступной папки

В этом примере показано, как восстановить общедоступную папку \\Dev\\CustomerEnagagements в целевой почтовый ящик общедоступной папки Development01.

    New-MailboxRestoreRequest -SourceStoreMailbox Development -SourceDatabase MBX_DB01 -TargetMailbox Development01 -AllowLegacyDNMismatch -IncludeFolders \Dev\CustomerEngagements

Подробные сведения о синтаксисе и параметрах см. в разделе [New-MailboxRestoreRequest](https://technet.microsoft.com/ru-ru/library/ff829875\(v=exchg.150\)).

## Восстановление обратимо удаленного почтового ящика общедоступной папки

В этом примере показано, как восстановить почтовый ящик общедоступной папки PF\_Singapore в новый почтовый ящик общедоступной папки PF\_Singapore\_Restore.

    New-MailboxRestoreRequest -SourceStoreMailbox PF_Singapore -SourceDatabase MBX_DB01 -TargetMailbox PF_Singapore_Restore -AllowLegacyDNMismatch

Подробные сведения о синтаксисе и параметрах см. в разделе [New-MailboxRestoreRequest](https://technet.microsoft.com/ru-ru/library/ff829875\(v=exchg.150\)).
