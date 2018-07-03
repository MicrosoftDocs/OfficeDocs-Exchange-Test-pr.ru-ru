---
title: 'Управление фильтрацией отправителей: Exchange 2013 Help'
TOCTitle: Управление фильтрацией отправителей
ms:assetid: a7f4b3e1-2970-45ad-911e-a9f46d880d3d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124087(v=EXCHG.150)
ms:contentKeyID: 50488793
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Управление фильтрацией отправителей

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-08_

Фильтрация отправителей обеспечивается агентом фильтра отправителей. Агент фильтра отправителей на основе данных в SMTP-заголовке **MAIL FROM:**  определяет, SMTP-заголовок определяет, какое действие нужно выполнить (и нужно ли) в отношении входящего сообщения электронной почты.

Если на сервере Exchange включена фильтрация отправителей, она выполняется для всех сообщений, поступающих через все соединители получения на этом компьютере.

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Функции защиты от нежелательной почты» в разделе [Разрешения для защиты от нежелательной почты и вредоносных программ](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - По умолчанию функции защиты от нежелательной почты в транспортной службе на сервере почтовых ящиков не включены. Как правило, функции защиты от нежелательной почты на сервере почтовых ящиков включают, только если организация Exchange не выполняет никакую предварительную фильтрацию нежелательной почты до приема входящих сообщений. Дополнительную информацию см. в статье [Включение функции защиты от нежелательной почты на сервере почтовых ящиков](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

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

## Включение или отключение фильтрации отправителей с помощью командной консоли Exchange

Чтобы отключить фильтрацию отправителей, выполните следующую команду:

    Set-SenderFilterConfig -Enabled $false

Чтобы включить фильтрацию отправителей, выполните следующую команду:

    Set-SenderFilterConfig -Enabled $true

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Когда фильтрация отправителей отключена, базовый агент фильтрации отправителей остается включенным. Чтобы отключить агент фильтрации отправителей, выполните следующую команду: <code>Disable-TransportAgent &quot;Sender Filter Agent&quot;</code>.</td>
</tr>
</tbody>
</table>


## Как проверить, что все получилось?

Чтобы убедиться в успешном включении или отключении фильтрации отправителей, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderFilterConfig | Format-List Enabled

2.  Убедитесь, что отображается значение, которое вы настроили.

## Использование командной консоли для настройки заблокированных отправителей и доменов

Чтобы заменить существующие значения, выполните следующую команду:

    Set-SenderFilterConfig -BlockedSenders <sender1,sender2...> -BlockedDomains <domain1,domain2...> -BlockedDomainsAndSubdomains <domain1,domain2...>

В данном примере представлена настройка агента фильтрации отправителей для блокировки сообщений с адресов inna@contoso.com и sergey@contoso.com, сообщений с домена fabrikam.com, а также сообщений с домена northwindtraders.com и всех его поддоменов.

    Set-SenderFilterConfig -BlockedSenders kim@contoso.com,john@contoso.com -BlockedDomains fabrikam.com -BlockedDomainsAndSubdomains northwindtraders.com

Чтобы добавить или удалить записи, не изменив существующие значения, выполните следующую команду:

    Set-SenderFilterConfig -BlockedSenders @{Add="<sender1>","<sender2>"...; Remove="<sender1>","<sender2>"...} -BlockedDomains @{Add="<domain1>","<domain2>"...; Remove="<domain1>","<domain2>"...} -BlockedDomainsAndSubdomains @{Add="<domain1>","<domain2>"...; Remove="<domain1>","<domain2>"...}

В данном примере представлена настройка агента фильтрации отправителей, при которой указываются следующие сведения.

  - Добавьте alexey@contoso.com и darya@contoso.com в список существующих заблокированных отправителей.

  - Удалите tailspintoys.com из списка существующих заблокированных доменов отправителей.

  - Добавьте blueyonderairlines.com в список существующих заблокированных доменов и поддоменов отправителей.

<!-- end list -->

    Set-SenderFilterConfig -BlockedSenders @{Add="chris@contoso.com","michelle@contoso.com"} -BlockedDomains @{Remove="tailspintoys.com"} -BlockedDomainsAndSubdomains @{Add="blueyonderairlines.com"}

## Как проверить, что все получилось?

Чтобы убедиться в успешной настройке блокировки отправителей, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderFilterConfig | Format-List BlockedSenders,BlockedDomains,BlockedDomainsAndSubdomains

2.  Убедитесь, что отображаются значения, которые вы настроили.

## Использование командной консоли для включения или отключения блокировки сообщений, отправители которых не указаны

Чтобы включить или отключить блокировку сообщений, отправители которых не указаны, выполните следующую команду:

    Set-SenderFilterConfig -BlankSenderBlockingenabled <$true | $false>

В данном примере представлена настройка агента фильтрации отправителей таким образом, чтобы блокировать сообщения, в которых отправитель не указан в SMTP-команде MAIL FROM:

    Set-SenderFilterConfig -BlankSenderBlockingEnabled $true

## Как проверить, что все получилось?

Чтобы убедиться в успешном включении или отключении блокировки сообщений, отправители которых не указаны, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderFilterConfig | Format-List BlankSenderBlockingEnabled

2.  Убедитесь, что отображается значение, которое вы настроили.

