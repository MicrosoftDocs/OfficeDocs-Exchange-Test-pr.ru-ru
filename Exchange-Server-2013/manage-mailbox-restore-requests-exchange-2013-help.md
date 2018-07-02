---
title: 'Управление запросами на восстановление почтового ящика: Exchange 2013 Help'
TOCTitle: Управление запросами на восстановление почтового ящика
ms:assetid: 8e668a52-c601-4d96-a51c-ab60267e1321
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ863437(v=EXCHG.150)
ms:contentKeyID: 50556456
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Управление запросами на восстановление почтового ящика

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Запросы на восстановление почтовых ящиков используются для восстановления отключенных почтовых ящиков. Отсоединенный почтовый ящик — это почтовый ящик в базе данных почтовых ящиков Exchange, не связанный с учетной записью пользователя Active Directory. Почтовые ящики становятся отсоединенными, когда они отключаются, удаляются или перемещаются в другую базу данных. Подробнее см. в разделе [Отключенные почтовые ящики](disconnected-mailboxes-exchange-2013-help.md).

Отключенные почтовые ящики хранятся в базе данных почтовых ящиков в течение времени, указанного в параметрах хранения удаленных почтовых ящиков для базы данных почтовых ящиков. По умолчанию отключенные почтовые ящики хранятся в течение 30 дней. Во время периода хранения содержимое удаленного почтового ящика можно восстановить (скопировать) в существующий почтовый ящик. В этом разделе описывается использование командной консоли для управления запросами на восстановление почтовых ящиков.

Дополнительные задачи управления, связанные с отсоединенными почтовыми ящиками, содержатся в следующих разделах:

[Отключение или удаление почтового ящика](disable-or-delete-a-mailbox-exchange-2013-help.md)

[Подключение отключенного почтового ящика](connect-a-disabled-mailbox-exchange-2013-help.md)

[Подключение или восстановление удаленного почтового ящика](connect-or-restore-a-deleted-mailbox-exchange-2013-help.md)

[Восстановление обратимо удаленного почтового ящика](restore-a-soft-deleted-mailbox-exchange-2013-help.md)

[Окончательное удаление почтового ящика](permanently-delete-a-mailbox-exchange-2013-help.md)

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 2 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Запрос на восстановление почтового ящика" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

  - Процедуры, описанные в этом разделе, можно выполнить только в командной консоли Exchange. Нельзя использовать EAC для управления запросами на восстановление почтовых ящиков.

  - Чтобы просмотреть значение свойства *Identity* для всех запросов на восстановление почтовых ящиков, выполните следующую команду.
    
        Get-MailboxRestoreRequest | Format-Table Identity
    
    Можно использовать это значение идентификатора для указания определенного запроса на восстановление почтового ящика при выполнении процедур, приведенных в данном разделе.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..</td>
</tr>
</tbody>
</table>


## Что необходимо сделать?

## Использование командной консоли для просмотра свойств запроса на восстановление

Можно просмотреть свойства запроса на восстановление почтового ящика, которые содержит основные сведения о состоянии запроса.

Чтобы просмотреть список и значение свойства *Identity* для всех запросов на восстановление почтовых ящиков, выполните следующую команду.

    Get-MailboxRestoreRequest | Format-Table Identity

Можно использовать идентификатор для получения сведений о конкретных запросах на восстановление почтовых ящиков.

В этом примере возвращается состояние запроса на восстановление "Pilar Pinilla \\MailboxRestore" с помощью параметра *Identity*.

    Get-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore"

В этом примере возвращается вся информация для второго запроса на восстановление для целевого почтового ящика "Pilar Pinilla".

    Get-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore1" | Format-List

В этом примере возвращается состояние запросов на восстановление, восстанавливаемых из исходной базы данных MBD01.

    Get-MailboxRestoreRequest -SourceDatabase MBD01

Этот пример возвращает все запросы на восстановление, которые в настоящее время выполняются.

    Get-MailboxRestoreRequest -Status InProgress

Другие полезные состояния — `Queued`, `Completed`, `Suspended` и `Failed`.

В этом примере возвращаются все приостановленные запросы на восстановление.

    Get-MailboxRestoreRequest -Suspend $true

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-MailboxRestoreRequest](https://technet.microsoft.com/ru-ru/library/ff829907\(v=exchg.150\)).

## Выходные данные командлета Get-MailboxRestoreRequest

По умолчанию командлет **Get-MailboxRestoreRequest** возвращает имя запроса, целевой почтовый ящик, в который восстанавливаются данные, и состояние запроса. В следующей таблице содержатся сведения, возвращаемые при конвейерной передаче командлета в командлет **Format-List**.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Значение</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>SourceDatabase</code></p></td>
<td><p>Указывает базу данных, содержащую восстанавливаемый отключенный почтовый ящик.</p></td>
</tr>
<tr class="even">
<td><p><code>TargetMailbox</code></p></td>
<td><p>Указывает почтовый ящик, в который восстанавливаются данные.</p></td>
</tr>
<tr class="odd">
<td><p><code>Name</code></p></td>
<td><p>Указывает имя запроса.</p></td>
</tr>
<tr class="even">
<td><p><code>RequestQueue</code></p></td>
<td><p>Указывает базу данных, в которой служба репликации почтовых ящиков Microsoft Exchange (MRS) сохраняет дополнительные сведения о состоянии запроса.</p></td>
</tr>
<tr class="odd">
<td><p><code>Status</code></p></td>
<td><p>Указывает состояние запроса.</p></td>
</tr>
<tr class="even">
<td><p><code>Suspend</code></p></td>
<td><p>Указывает, приостановлен ли запрос. Восстановление почтового ящика может быть приостановлено при создании с помощью командлета <strong>New-MailboxRestoreRequest</strong> с параметром <em>Suspend</em>. Оно также может быть приостановлено, когда происходит сбой операции восстановления почтового ящика, или вручную администратором с помощью командлета <strong>Suspend-MailboxRestoreRequest</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><code>Identity</code></p></td>
<td><p>Указывает идентификатор запроса. Этот идентификатор представляет собой сочетание имени целевого почтового ящика и имени запроса.</p></td>
</tr>
</tbody>
</table>


## Как проверить, что все получилось?

Запустите **Get-MailboxRestoreRequest** для проверки того, что вы можете просматривать свойства запросов на восстановление почтовых ящиков. Если командлет возвращает ошибку, убедитесь, что используется правильный синтаксис и идентификатор. В некоторых случаях командлет работает успешно, но не возвращает никаких результатов. Например, если вы отправили запрос на восстановление почтового ящика и выполнили команду `Get-MailboxRestoreRequest -Status InProgress`, но никакие результаты не возвращаются, тогда ни один из запросов на восстановление не запущен.

## Использование командной консоли для просмотра статистики запросов на восстановление

Можно просмотреть статистику запросов на восстановление почтовых ящиков, которая предоставляет подробную информацию, которая может использоваться для поиска и устранения неисправностей.

В этом примере возвращается статистика по умолчанию для запроса на восстановление danp\\MailboxRestore1. Сведения, получаемые по умолчанию, включают в себя имя, почтовый ящик, состояние и процент выполнения.

    Get-MailboxRestoreRequestStatistics -Identity danp\MailboxRestore1

В этом примере возвращается статистика почтового ящика «Dan Park», а отчет экспортируется в CSV-файл.

    Get-MailboxRestoreRequestStatistics -Identity "Dan Park\MailboxRestore" | Export-CSV \\SERVER01\RestoreRequest_Reports\DanPark_Restorestats.csv

В этом примере возвращаются дополнительные сведения о запросе на восстановление для пользователя Pilar Pinilla с помощью параметра *IncludeReport*, а результаты передаются по конвейеру в командлет **Format-List**.

    Get-MailboxRestoreRequestStatistics -Identity "Pilar Pinilla\MailboxRestore" -IncludeReport | Format-List 

В этом примере возвращаются дополнительные сведения о всех запросах на восстановление с состоянием `Failed` с помощью параметра *IncludeReport*; затем эти сведения сохраняются в текстовом файле AllRestoreReports.txt в том расположении, в котором запускалась команда.

    Get-MailboxRestoreRequest -Status Failed | Get-MailboxRestoreRequestStatistics -IncludeReport | Format-List > AllRestoreReports.txt

Дополнительные сведения о синтаксисе и параметрах см. в разделах [Get-MailboxRestoreRequestStatistics](https://technet.microsoft.com/ru-ru/library/ff829912\(v=exchg.150\)) и [Get-MailboxRestoreRequest](https://technet.microsoft.com/ru-ru/library/ff829907\(v=exchg.150\)).

## Выходные данные командлета Get-MailboxRestoreRequestStatistics

По умолчанию командлет [Get-MailboxRestoreRequestStatistics](https://technet.microsoft.com/ru-ru/library/ff829912\(v=exchg.150\)) возвращает имя запроса, состояние запроса, псевдонимы целевого почтового ящика и процент выполнения. В следующей таблице содержатся сведения, возвращаемые при конвейерной передаче командлета в командлет **Format-List**.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Значение</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Name</code></p></td>
<td><p>Указывает имя запроса.</p></td>
</tr>
<tr class="even">
<td><p><code>Status</code></p></td>
<td><p>Указывает состояние запроса.</p></td>
</tr>
<tr class="odd">
<td><p><code>StatusDetail</code></p></td>
<td><p>Указывает дополнительные сведения о состоянии запроса. Например, если значение <code>Status</code> возвращает состояние <code>InProgress</code>, то значение <code>StatusDetail</code> возвратит определенные стадии состояния <code>InProgress</code>, например <code>CreatingFolderHierarchy</code> и <code>CopyingMessages</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>SyncStage</code></p></td>
<td><p>Указывает процент выполнения запроса на восстановление.</p></td>
</tr>
<tr class="odd">
<td><p><code>Suspend</code></p></td>
<td><p>Указывает, приостановлен ли запрос на восстановление. Этот параметр будет иметь значение <code>true</code> в следующих сценариях.</p>
<ul>
<li><p>Служба MRS остановила или останавливает запрос из-за ошибки.</p></li>
<li><p>Администратор приостановил запрос.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><code>SourceExchangeGuid</code></p></td>
<td><p>Указывает идентификатор GUID исходного почтового ящика, из которого восстанавливаются данные.</p></td>
</tr>
<tr class="odd">
<td><p><code>SourceRootFolder</code></p></td>
<td><p>Указывает имя корневой папки в иерархии исходного почтового ящика, из которого восстанавливаются данные. Если это значение не указано, данные восстанавливаются из папки «Корневой уровень хранилища».</p></td>
</tr>
<tr class="even">
<td><p><code>SourceDatabase</code></p></td>
<td><p>Указывает имя базы данных, в которой размещен исходный почтовый ящик.</p></td>
</tr>
<tr class="odd">
<td><p><code>MailboxRestoreFlags</code></p></td>
<td><p>Указывает, что восстанавливаемый почтовый ящик имеет состояние <code>Disabled</code> или <code>Soft-Deleted</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>TargetAlias</code></p></td>
<td><p>Указывает псевдоним целевого почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><code>TargetIsArchive</code></p></td>
<td><p>Указывает, восстанавливается ли почтовый ящик в архив.</p></td>
</tr>
<tr class="even">
<td><p><code>TargetExchangeGuid</code></p></td>
<td><p>Указывает идентификатор GUID целевого почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><code>TargetRootFolder</code></p></td>
<td><p>Указывает имя корневой папки в иерархии конечного почтового ящика, где восстанавливаются данные. Если это значение не указано, данные восстанавливаются в папку «Корневой уровень хранилища».</p></td>
</tr>
<tr class="even">
<td><p><code>TargetDatabase</code></p></td>
<td><p>Указывает имя базы данных, в которой размещен целевой почтовый ящик.</p></td>
</tr>
<tr class="odd">
<td><p><code>TargetMailboxIdentity</code></p></td>
<td><p>Указывает идентификатор целевого почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><code>IncludeFolders</code></p></td>
<td><p>Указывает список папок, которые необходимо включить в процесс восстановления. Если это значение не указано, то при создании запроса папки не были заданы, поэтому в почтовый ящик будут восстановлены все папки (если не используется параметр <em>ExcludeFolders</em> для исключения определенных папок из списка).</p></td>
</tr>
<tr class="odd">
<td><p><code>ExcludeFolders</code></p></td>
<td><p>Указывает список папок, которые необходимо исключить из процесса восстановления. Если это значение не указано, то при создании запроса папки не были заданы, поэтому в почтовый ящик будут восстановлены все папки (если не используется параметр <em>IncludeFolders</em> для включения определенных папок).</p></td>
</tr>
<tr class="even">
<td><p><code>ExcludeDumpster</code></p></td>
<td><p>Указывает, была ли исключена папка «Элементы для восстановления» при создании запроса.</p></td>
</tr>
<tr class="odd">
<td><p><code>ConflictResolutionOption</code></p></td>
<td><p>Указывает действие, которое будет выполнять служба репликации почтовых ящиков (MRS) при наличии идентичных сообщений в целевой и исходной папках.</p></td>
</tr>
<tr class="even">
<td><p><code>AssociatedMessagesCopyOption</code></p></td>
<td><p>Указывает, копируются ли сопоставленные сообщения при обработке запроса. Сопоставленные сообщения — это особые сообщения, которые содержат скрытые данные о правилах, представлениях и формах.</p></td>
</tr>
<tr class="odd">
<td><p><code>BadItemLimit</code></p></td>
<td><p>Указывает количество неправильных элементов, которое служба репликации почтовых ящиков будет пропускать при обнаружении поврежденных сообщений в запросе.</p></td>
</tr>
<tr class="even">
<td><p><code>BadItemsEncountered</code></p></td>
<td><p>Указывает количество поврежденных сообщений, обнаруженных при выполнении команды. Если значение <em>BadItemsEncountered</em> превышает значение <em>BadItemLimit</em>, запрос не будет выполнен.</p></td>
</tr>
<tr class="odd">
<td><p><code>QueuedTimeStamp</code></p></td>
<td><p>Указывает дату и время отправки запроса в службу репликации почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p><code>StartTimeStamp</code></p></td>
<td><p>Указывает дату и время, с которого началась обработка запроса на восстановление в службе репликации почтовых ящиков.</p></td>
</tr>
<tr class="odd">
<td><p><code>LastUpdateTimeStamp</code></p></td>
<td><p>Указывает дату и время последнего изменения запроса. Изменение могло быть выполнено администратором или службой репликации почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p><code>SuspendTimeStamp</code></p></td>
<td><p>Указывает дату и время приостановки запроса.</p></td>
</tr>
<tr class="odd">
<td><p><code>OverallDuration</code></p></td>
<td><p>Указывает время, которое потребовалось для выполнения запроса. Если запрос имеет состояние <code>Failed</code>, это значение указывает время, прошедшее с момента запуска запроса до момента его сбоя. Если запрос не был завершен, это значение указывает время, прошедшее с момента начала запроса до запуска командлета <strong>Get-MailboxRestoreRequestStatistics</strong>.</p></td>
</tr>
<tr class="even">
<td><p><code>TotalSuspendedDuration</code></p></td>
<td><p>Указывает время, в течение которого запрос находился в состоянии <code>Suspended</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code>TotalFailedDuration</code></p></td>
<td><p>Указывает время, в течение которого запрос находился в состоянии <code>Failed</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>TotalQueuedDuration</code></p></td>
<td><p>Указывает время, в течение которого запрос находился в состоянии <code>Queued</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code>TotalInProgressDuration</code></p></td>
<td><p>Указывает время, в течение которого запрос находился в состоянии <code>In Progress</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>TotalStalledDueToHADuration</code></p></td>
<td><p>Указывает время, в течение которого запрос был остановлен из-за высокой доступности.</p></td>
</tr>
<tr class="odd">
<td><p><code>MRSServerName</code></p></td>
<td><p>Указывает имя сервера клиентского доступа, обработавшего запрос.</p></td>
</tr>
<tr class="even">
<td><p><code>EstimatedTransferSize</code></p></td>
<td><p>Указывает общий размер восстановленного файла или размер файла, который будет восстановлен службой репликации почтовых ящиков, если запрос находится в состоянии <code>In Progress</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code>EstimatedTransferItemCount</code></p></td>
<td><p>Указывает количество восстановленных элементов или количество элементов, которые будут восстановлены службой репликации почтовых ящиков, если запрос находится в состоянии <code>In Progress</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>BytesTransferredPerMinute</code></p></td>
<td><p>Указывает среднее количество переданных в минуту байтов.</p></td>
</tr>
<tr class="odd">
<td><p><code>ItemsTransferred</code></p></td>
<td><p>Указывает количество переданных элементов.</p></td>
</tr>
<tr class="even">
<td><p><code>PercentComplete</code></p></td>
<td><p>Указывает процент выполнения запроса.</p></td>
</tr>
<tr class="odd">
<td><p><code>CompletedRequestAgeLimit</code></p></td>
<td><p>Указывается срок, в течение которого выполненный запрос на восстановление будет храниться перед удалением. Значение по умолчанию — 30 дней.</p></td>
</tr>
<tr class="even">
<td><p><code>PositionInQueue</code></p></td>
<td><p>Если обработка запроса не начата, это значение указывает положение запроса в очереди.</p></td>
</tr>
<tr class="odd">
<td><p><code>FailureCode</code></p></td>
<td><p>Если произошел сбой, это значение указывает код ошибки.</p></td>
</tr>
<tr class="even">
<td><p><code>FailureType</code></p></td>
<td><p>Если произошел сбой, это значение указывает тип ошибки.</p></td>
</tr>
<tr class="odd">
<td><p><code>FailureSide</code></p></td>
<td><p>Если произошел сбой, это значение указывает, произошел ли он в целевом или в исходном почтовом ящике.</p></td>
</tr>
<tr class="even">
<td><p><code>Message</code></p></td>
<td><p>Если произошел сбой, это значение указывает сообщение об ошибке. Это значение может также указывать примечание о приостановке.</p></td>
</tr>
<tr class="odd">
<td><p><code>FailureTimestamp</code></p></td>
<td><p>Если произошел сбой запроса, это значение указывает дату и время сбоя.</p></td>
</tr>
<tr class="even">
<td><p><code>FailureContext</code></p></td>
<td><p>Если произошел сбой запроса, это значение указывает сведения о действии, которое выполнялось в момент сбоя.</p></td>
</tr>
<tr class="odd">
<td><p><code>ValidationMessage</code></p></td>
<td><p>Если запрос был недопустим, это значение указывает причину.</p></td>
</tr>
<tr class="even">
<td><p><code>RequestQueue</code></p></td>
<td><p>Указывает базу данных, в которой служба репликации почтовых ящиков сохраняет дополнительные сведения о состоянии запроса.</p></td>
</tr>
<tr class="odd">
<td><p><code>Identity</code></p></td>
<td><p>Указывает идентификатор запроса.</p></td>
</tr>
<tr class="even">
<td><p><code>Report</code></p></td>
<td><p>При использовании параметра <em>IncludeReport</em> это значение указывает сведения, которые можно использовать для устранения неполадок, связанных с запросом.</p></td>
</tr>
</tbody>
</table>


## Как проверить, что все получилось?

Запустите **Get-MailboxRestoreRequestStatistics** для проверки того, что вы можете просматривать статистику запросов на восстановление почтовых ящиков. Если командлет возвращает ошибку, убедитесь, что используется правильный идентификатор.

## Использование командной консоли для изменения свойств запроса на восстановление

Если не удается выполнить запрос на восстановление почтового ящика, можно воспользоваться командлетом **Set-MailboxRestoreRequest** для изменения свойств запроса и восстановления после сбоя.

В этом примере кода указывается, что запрос на восстановление MailboxRestore1 для почтового ящика Debra Garcia будет пропускать 10 поврежденных элементов.

    Set-MailboxRestoreRequest -Identity "Debra Garcia\MailboxRestore1" -BadItemLimit 10

В этом примере кода указывается, что запрос на восстановление MailboxRestore1 для почтового ящика Florence Flipo будет пропускать 100 поврежденных элементов. В связи с тем, что значение параметра *BadItemLimit* больше 50, необходимо указывать значение для параметра *AcceptLargeDataLoss*.

    Set-MailboxRestoreRequest -Identity "Florence Flipo\MailboxRestore1" -BadItemLimit 100 -AcceptLargeDataLoss

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-MailboxRestoreRequest](https://technet.microsoft.com/ru-ru/library/ff829909\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться в том, что свойства запроса на восстановление успешно изменены, запустите **Get-MailboxRestoreRequestStatistics**, чтобы вывести на экран измененные свойства запроса на восстановление. При успешном создании запроса на восстановление свойство *Status* имеет значение `Queued`, `InProgress` или `Completed`. После завершения запроса на восстановление содержимое удаленного почтового ящика будет присутствовать в целевом почтовом ящике.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-MailboxRestoreRequestStatistics](https://technet.microsoft.com/ru-ru/library/ff829912\(v=exchg.150\)).

## Использование командной консоли для приостановки запроса на восстановление

Можно приостановить запрос на восстановление в любое время после создания запроса, но до того, как он перейдет в состояние `Completed`. См. далее в подразделе Использование командной консоли для возобновления запроса на восстановление информацию о синтаксисе команд для возобновления запроса на восстановление с помощью командлета [Resume-MailboxRestoreRequest](https://technet.microsoft.com/ru-ru/library/ff829908\(v=exchg.150\)).

В этом примере приостанавливается запрос MailboxRestore1 на восстановление почтового ящика пользователя Pilar Pinilla.

    Suspend-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore1"

В этом примере все выполняемые запросы на восстановление приостанавливаются путем получения всех запросов с состоянием `InProgress` и последующей конвейерной передачи выходных данных в командлет **Suspend-MailboxRestoreRequest** с примечанием о приостановке «Resume after FY13Q2 Maintenance» (Возобновить после обслуживания в FY13Q2).

    Get-MailboxRestoreRequest -Status InProgress | Suspend-MailboxRestoreRequest -SuspendComment "Resume after FY13Q2 Maintenance"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Suspend-MailboxRestoreRequest](https://technet.microsoft.com/ru-ru/library/ff829906\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться в том, что запрос на восстановление почтового ящика успешно приостановлен, выполните следующую команду.

    Get-MailboxRestoreRequest <identity> | Format-List Suspend,Status

Если значение свойства *Suspend* равняется `True`, запрос на восстановление успешно приостановлен. Кроме того, значение `Suspended` у свойства *Status* указывает, что запрос приостановлен.

## Использование командной консоли для возобновления запроса на восстановление

Командлет **Resume-MailboxRestoreRequest** используется для возобновления запроса на восстановление, который был приостановлен или завершен с ошибкой.

В этом примере возобновляется запрос на восстановление Pilar Pinilla\\MailboxRestore1.

    Resume-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore1"

В этом примере показано, как возобновить все запросы на восстановление, которые имеют состояние Failed.

    Get-MailboxRestoreRequest -Status Failed | Resume-MailboxRestoreRequest

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Resume-MailboxRestoreRequest](https://technet.microsoft.com/ru-ru/library/ff829908\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться, что запрос на восстановление возобновился, выполните следующую команду.

    Get-MailboxRestoreRequest <identity> | Format-List Suspend,Status

Если значение свойства *Suspend* равняется `False`, запрос на восстановление успешно восстановлен. Кроме того, значение `InProgress` у свойства *Status* указывает, что запрос возобновлен.

## Использование командной консоли для удаления запроса на восстановление

Командлет **Remove-MailboxRestoreRequest** используется для удаления запросов на восстановление. Если удалить запрос на восстановление после начала копирования данных почтового ящика в целевой почтовый ящик, уже скопированные данные останутся в целевом почтовом ящике.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Как было сказано выше, выполненные запросы на восстановление хранятся в течение 30 дней до автоматического удаления.</td>
</tr>
</tbody>
</table>


В этом примере удаляется запрос на восстановление Pilar Pinilla\\MailboxRestore1.

    Remove-MailboxRestoreRequest -Identity "Pilar Pinilla\MailboxRestore1"

Этот пример удаляет все запросы на восстановление, которые имеют состояние «Completed».

    Get-MailboxRestoreRequest -Status Completed | Remove-MailboxRestoreRequest

В этом примере запрос на восстановление на сервере MBXDB01 отменяется с помощью параметра *RequestGuid*. Набор параметров, в котором обязательными являются параметры *RequestGuid* и *RequestQueue*, используется только для отладки службы репликации Microsoft. Эти параметры можно использовать только при получении соответствующих указаний от службы технической поддержки корпорации Майкрософт.

    Remove-MailboxRestoreRequest -RequestQueue MBXDB01 -RequestGuid 25e0eaf2-6cc2-4353-b83e-5cb7b72d441f

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-MailboxRestoreRequest](https://technet.microsoft.com/ru-ru/library/ff829910\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться в том, что запрос на восстановление почтового ящика успешно удален, выполните следующую команду.

    Get-MailboxRestoreRequest -Identity <identity of removed restore request>

Команда возвратит ошибку, указывающую, что запрос на восстановление не существует.

Вы также можете запустить командлет **Get-MailboxRestoreRequest**. Если запрос на восстановление успешно удален, он не включается в результаты.

