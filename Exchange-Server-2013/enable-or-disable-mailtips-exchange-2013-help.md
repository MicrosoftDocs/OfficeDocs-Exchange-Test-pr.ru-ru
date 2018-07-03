---
title: 'Включение или отключение подсказок: Exchange 2013 Help'
TOCTitle: Включение или отключение подсказок
ms:assetid: 11ad3848-f303-4ad5-a21d-9b0883db4bda
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ649321(v=EXCHG.150)
ms:contentKeyID: 50487515
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Включение или отключение подсказок

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-08_

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


## Использование командной консоли Exchange для включения или отключения подсказок

Командлет **Set-OrganizationConfig** используется для включения или отключения подсказок в организации. При установке новой организации Exchange подсказки включаются по умолчанию. В этом примере показано, как включить подсказки в организации.

    Set-OrganizationConfig -MailTipsAllTipsEnabled $true

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-OrganizationConfig](https://technet.microsoft.com/ru-ru/library/aa997443\(v=exchg.150\)).

