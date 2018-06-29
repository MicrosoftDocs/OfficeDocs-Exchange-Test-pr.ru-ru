﻿---
title: 'Настройка большой аудитории для организации: Exchange 2013 Help'
TOCTitle: Настройка большой аудитории для организации
ms:assetid: 8a37911c-4339-4921-b5d3-0a5a774d4517
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ659068(v=EXCHG.150)
ms:contentKeyID: 50488548
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Настройка большой аудитории для организации

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2015-04-08_

Командную консоль Exchange можно использовать для настройки различных параметров, определяющих способы использования подсказок в организации.

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Подсказки" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Для выполнения этой процедуры можно использовать только командную консоль.

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


## Использование командной консоли Exchange для настройки размера большой аудитории организации

Для настройки размера большой аудитории организации используется командлет **Set-OrganizationConfig**. Если сообщения отправителей адресованы нескольким получателям, количество которых превышает определенное значение, для них будет отображена подсказка большой аудитории. Размер большой аудитории по умолчанию имеет значение 25. В этом примере показано, как для размера большой аудитории в организации установить значение 50.

    Set-OrganizationConfig -MailTipsLargeAudienceThreshold 50

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-OrganizationConfig](https://technet.microsoft.com/ru-ru/library/aa997443\(v=exchg.150\)).

