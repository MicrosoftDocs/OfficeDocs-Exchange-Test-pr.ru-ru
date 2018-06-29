﻿---
title: 'Окончательное удаление почтового ящика: Exchange 2013 Help'
TOCTitle: Окончательное удаление почтового ящика
ms:assetid: df35765a-0bef-4561-9846-d91d69c0269c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ863440(v=EXCHG.150)
ms:contentKeyID: 50556493
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Окончательное удаление почтового ящика

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2012-11-16_

Если окончательно удалить активные почтовые ящики и отключенные почтовые ящики, все их содержимое очищается из базы данных почтовых ящиков Exchange, и потеря данных будет постоянной. Если окончательно удалить активный почтовый ящик, сопоставленная ему в Active Directory учетная запись пользователя также удаляется.

Альтернативой окончательному удалению почтового ящика является его отключение. После отключения почтового ящика по умолчанию он сохраняется в базе данных почтовых ящиков на 30 дней. Это дает вам возможность снова подключить или восстановить почтовый ящик еще до того, как данные будут удалены из базы данных.

Дополнительные сведения об отключенных почтовых ящиках и других задачах управления приведены в следующих разделах:

  - [Отключенные почтовые ящики](disconnected-mailboxes-exchange-2013-help.md)

  - [Отключение или удаление почтового ящика](disable-or-delete-a-mailbox-exchange-2013-help.md)

  - [Подключение отключенного почтового ящика](connect-a-disabled-mailbox-exchange-2013-help.md)

  - [Подключение или восстановление удаленного почтового ящика](connect-or-restore-a-deleted-mailbox-exchange-2013-help.md)

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Нельзя использовать EAC для окончательного удаления активного почтового ящика или отключенного почтового ящика.</td>
</tr>
</tbody>
</table>


## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения: 2 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Тема "Разрешения подготовки получателей" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

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

## Окончательное удаление активного почтового ящика

## Использование командной консоли Exchange для полного удаления активного почтового ящика

Выполните следующую команду, чтобы окончательно удалить активный почтовый ящик и соответствующую учетную запись пользователя в Active Directory.

    Remove-Mailbox -Identity <identity> -Permanent $true

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если не включить параметр <em>Permanent</em>, удаленный почтовый ящик остается в базе данных почтовых ящиков на 30 дней по умолчанию, прежде чем будет окончательно удален.</td>
</tr>
</tbody>
</table>


Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-Mailbox](https://technet.microsoft.com/ru-ru/library/aa995948\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться в том, что активный почтовый ящик удален, выполните следующие действия:

1.  Убедитесь, что почтовый ящик отсутствует в EAC.

2.  Убедитесь, что соответствующая пользовательская учетная запись больше не отображается в оснастке "Active Directory — пользователи и компьютеры".

3.  Выполните следующую команду, чтобы убедиться, что почтовый ящик был успешно удален из базы данных почтовых ящиков Exchange.
    
        Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" }
    
    Если почтовый ящик успешно очищен, команда не даст никаких результатов. Если почтовый ящик не был очищен, команда вернет сведения о почтовом ящике.

## Окончательное удаление отключенного почтового ящика

## Использование командной консоли для окончательного удаления отключенного почтового ящика

Существует два типа отключенных почтовых ящиков: обратимо удаленные и отключенные. Необходимо указать один из следующих типов при выполнении командлета, чтобы окончательно удалить почтовый ящик. Если заданный тип не совпадает с фактическим типом отключенного почтового ящика, происходит сбой команды.

Выполните следующую команду, чтобы определить, удален ли отключенный почтовый ящик.

    Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisplayName,MailboxGuid,Database,DisconnectReason

Значение свойства *DisconnectReason* для отключенных почтовых ящиков будет равно `Disabled` или `SoftDeleted`.

Можно выполнить следующую команду, чтобы отобразить типы всех отключенных почтовых ящиков в организации.

    Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisconnectReason -ne $null } | fl DisplayName,MailboxGuid,Database,DisconnectReason

<table>
<thead>
<tr class="header">
<th><img src="images/JJ983803.warning(EXCHG.150).gif" title="Предупреждение" alt="Предупреждение" />Предупреждение.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При использовании командлета <strong>Remove-StoreMailbox</strong> для очистки отключенного почтового ящика и всего его содержимого из базы данных почтовых ящиков происходит окончательная потеря данных.</td>
</tr>
</tbody>
</table>


В этом примере окончательно удаляется отключенный почтовый ящик с идентификатором GUID 2ab32ce3-fae1-4402-9489-c67e3ae173d3 из базы данных почтовых ящиков MBD01.

    Remove-StoreMailbox -Database MBD01 -Identity "2ab32ce3-fae1-4402-9489-c67e3ae173d3" -MailboxState Disabled

В этом примере выполняется окончательное удаление обратимо удаленного почтового ящика пользователя Dan Jump из базы данных почтовых ящиков MBD01.

    Remove-StoreMailbox -Database MBD01 -Identity "Dan Jump" -MailboxState SoftDeleted

В этом примере окончательно удаляются все обратимо удаленные почтовые ящики из базы данных почтовых ящиков MBD01.

    Get-MailboxStatistics -Database MBD01 | where {$_.DisconnectReason -eq "SoftDeleted"} | ForEach {Remove-StoreMailbox -Database $_.Database -Identity $_.MailboxGuid -MailboxState SoftDeleted}

Дополнительные сведения о синтаксисе и параметрах см. в разделах [Remove-StoreMailbox](https://technet.microsoft.com/ru-ru/library/ff829913\(v=exchg.150\)) и [Get-MailboxStatistics](https://technet.microsoft.com/ru-ru/library/bb124612\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться в том, что отключенный почтовый ящик окончательно удален и успешно очищен из базы данных почтовых ящиков Exchange, выполните следующую команду.

    Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" }

Если почтовый ящик успешно очищен, команда не даст никаких результатов. Если почтовый ящик не был очищен, команда вернет сведения о почтовом ящике.

