---
title: 'Настройка отправки отчетов о сообщениях с удаленного домена: Exchange 2013 Help'
TOCTitle: Настройка отправки отчетов о сообщениях с удаленного домена
ms:assetid: 73dc686a-e7a3-44c7-b82f-f52ff9273199
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ649325(v=EXCHG.150)
ms:contentKeyID: 50488410
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Настройка отправки отчетов о сообщениях с удаленного домена

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-08_

Можно воспользоваться командной консолью Exchange, чтобы настроить способ отправки и получения сообщений электронной почты через удаленные домены. В следующем примере демонстрируется, как с помощью консоли управления Exchange настроить способ, которым Exchange обрабатывает отчеты о доставке и недоставке.

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 10 минут

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Удаленные домены" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

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


## Использование командной консоли для настройки отчетов о сообщениях

Командлет **Set-RemoteDomain** используется для настройки свойств удаленного домена.

В этом примере отключаются отчеты о доставке, отправляемые в удаленный домен Contoso. Этот параметр по умолчанию включен.

    Set-RemoteDomain Contoso -DeliveryReportEnabled $false

В этом примере отключаются отчеты о недоставке, отправляемые в удаленный домен. Этот параметр по умолчанию включен.

    Set-RemoteDomain Contoso -NDREnabled $false

