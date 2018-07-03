﻿---
title: 'Управление утверждением сообщений и устранение неполадок: Exchange 2013 Help'
TOCTitle: Управление утверждением сообщений и устранение неполадок
ms:assetid: 860df43f-a05b-4da3-83f1-68d3123a923d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd298110(v=EXCHG.150)
ms:contentKeyID: 52061266
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Управление утверждением сообщений и устранение неполадок

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

При попытке удалить почтовый ящик разрешения конфликтов может отобразиться следующее сообщение об ошибке.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Не удалось удалить почтовый ящик разрешения конфликтов &lt;<em>почтовый ящик</em>&gt;, так как он используется для рабочего процесса утверждения текущих получателей, имеющих ограничения членства или с включенной модерацией. Отключите функции утверждения для этих получателей или укажите для них другой почтовый ящик разрешения конфликтов перед удалением этого ящика.</p></td>
</tr>
</tbody>
</table>


Почтовый ящик разрешения конфликтов может использоваться для обработки рабочего процесса утверждения управляемых получателей и утверждения членства в группе рассылки. Для нахождения всех получателей, настроенных на использование почтового ящика разрешения конфликтов, воспользуйтесь PowerShell. После определения получателей вы можете настроить их на использование другого почтового ящика разрешения конфликтов или отключить для них модерацию.

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 15 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Разрешение конфликтов" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Действие 1. Для нахождения всех получателей, использующих почтовый ящик разрешения конфликтов, который вы пытаетесь удалить, воспользуйтесь командной консолью.

Выполните следующие команды:

    $AM = Get-Mailbox "<arbitration mailbox>" -Arbitration
    $AMDN = $AM.DistinguishedName
    Get-Recipient -RecipientPreviewFilter {ArbitrationMailbox -eq $AMDN}

Например, чтобы найти всех получателей, использующих почтовый ящик разрешения конфликтов с именем Arbitration Mailbox01, выполните следующие команды.

    $AM = Get-Mailbox "Arbitration Mailbox01" -Arbitration
    $AMDN = $AM.DistinguishedName
    Get-Recipient -RecipientPreviewFilter {ArbitrationMailbox -eq $AMDN}

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Почтовый ящик разрешения конфликтов указывается, используя различающееся имя. Если вам известно различающееся имя почтового ящика разрешения конфликтов, можно запустить одну команду. <code>Get-Recipient -RecipientPreviewFilter {ArbitrationMailbox -eq &lt;DN&gt;}</code>.</td>
</tr>
</tbody>
</table>


## Действие 2. Использование командной консоли для указания другого почтового ящика разрешения конфликтов или отключения модерации для получателей.

Для отключения управляемых получателей от использования удаляемого почтового ящика разрешения конфликтов можно указать другой почтовый ящик или отключить модерацию для получателей.

Если требуется указать другой почтовый ящик для получателей, выполните следующую команду.

    Set-<RecipientType> <Identity> -ArbitrationMailbox <different arbitration mailbox>

Например, чтобы изменить конфигурацию группы рассылки с именем "Все сотрудники" для использования почтового ящика разрешения конфликтов с именем Arbitration Mailbox02 с целью утверждения членства, выполните следующую команду.

    Set-DistributionGroup "All Employees" -ArbitrationMailbox "Arbitration Mailbox02"

Если требуется отключить модерацию для получателей, выполните следующую команду.

    Set-<RecipientType> <Identity> -ModerationEanbled $false

Например, чтобы отключить модерацию для почтового ящика с именем "Отдел кадров", выполните следующую команду.

    Set-Mailbox "Human Resources" -ModerationEanbled $false

## Как проверить, что все получилось?

Процедура прошла успешно, если вы можете удалить почтовый ящик разрешения конфликтов без получения сообщения об ошибке его использования.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).
