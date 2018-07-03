---
title: 'Управление параметрами единой системы обмена СООБЩЕНИЯМИ на сервере почтовых ящиков: Exchange 2013 Help'
TOCTitle: Управление параметрами единой системы обмена СООБЩЕНИЯМИ на сервере почтовых ящиков
ms:assetid: 6df4853d-21d2-473f-b0ca-ebc996d8794a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa998815(v=EXCHG.150)
ms:contentKeyID: 50556389
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.UnifiedMessaging.UMServerPropertiesPropertyPage
ms.translationtype: MT
---

# Управление параметрами единой системы обмена СООБЩЕНИЯМИ на сервере почтовых ящиков

 

_**Применимо к:** Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2013-02-11_

После установки сервера почтовых ящиков, который работает под управлением службы единой системы обмена сообщениями Microsoft Exchange, можно настроить несколько параметров, включая количество одновременных вызовов, прослушивающие TCP- и TLS-порты, состояние и режим запуска данной системы.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Чтобы абонентская группа единой системы обмена сообщениями могла обрабатывать вызовы для данной системы, в эту группу не нужно предварительно добавлять сервера почтовых ящиков. Исключение составляют случаи интеграции единой системы обмена сообщениями и Microsoft Office Communications Server 2007 R2 или Microsoft Lync Server. По умолчанию все серверы почтовых ящиков в организации способны отвечать на входящие вызовы.</td>
</tr>
</tbody>
</table>


Сведения о дополнительных задачах управления, связанных с единой системой обмена сообщениями и серверами почтовых ящиков, см. в разделе [Процедуры служб единой системы обмена СООБЩЕНИЯМИ](um-services-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Сервер почтовых ящиков (служба единой системы обмена сообщениями)" в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Убедитесь, что сервер почтовых ящиков установлен либо на том же компьютере, что и сервер клиентского доступа, либо на отдельном компьютере.

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

## Использование командной консоли для настройки свойств единой системы обмена сообщениями на сервере почтовых ящиков

В этом примере показано, как удалить сервер почтовых ящиков `MyMailboxServer` из всех абонентских групп на основе протокола SIP.

    Set-UMService -Identity MyMailboxServer -DialPlans $null

В этом примере показано, как добавить сервер почтовых ящиков `MyMailboxServer` в абонентскую группу SIP этой системы с именем `MySIPDialPlanName`, а также установить максимальное число входящих голосовых вызовов.

    Set-UMService -Identity MyMailboxServer -DialPlans MySIPDialPlanName -MaxCalls 150 

В этом примере показано, как установить двойной режим запуска для сервера почтовых ящиков `MyUMServer`.

    Set-UMService -Identity MyMailboxServer -DialPlans MySIPDialPlanName -UMStartUpMode -Dual 

## Использование командной консоли для просмотра свойств сервера почтовых ящиков

В этом примере отображается список всех серверов почтовых ящиков.

    Get-UMService

В этом примере отображается форматированный список свойств для сервера почтовых ящиков `MyMailboxServer`.

    Get-UMService -Identity MyMailboxServer | Format-List

