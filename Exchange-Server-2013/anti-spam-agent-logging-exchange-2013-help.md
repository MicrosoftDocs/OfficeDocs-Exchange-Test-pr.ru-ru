﻿---
title: 'Ведение журнала агента защиты от спама: Exchange 2013 Help'
TOCTitle: Ведение журнала агента защиты от спама
ms:assetid: dbd478d2-7993-4931-80db-5b2f7d4269bd
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124795(v=EXCHG.150)
ms:contentKeyID: 50489341
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ведение журнала агента защиты от спама

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

В журналах агентов регистрируются действия, которые специальные агенты защиты от нежелательной почты в службе Microsoft Exchange Server 2013 выполняют с сообщением. Вносить сведения в журнал агентов могут только следующие агенты.

  - Агент фильтрации подключений

  - Агент фильтра содержимого

  - Агент пограничных правил

  - Агент фильтра получателей

  - Агент фильтра отправителей

  - Агент идентификации отправителей

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Агент фильтрации подключений и агент пограничных правил недоступны на серверах почтовых ящиков.</td>
</tr>
</tbody>
</table>


Данные, записываемые в журнал агентов, зависят от агента, события SMTP и действия, выполненного над сообщением.

Командлет **Set-TransportService** позволяет выполнять в командной консоли Exchange все задачи по настройке журнала агентов. Для журналов агентов доступны следующие параметры.

  - Включение или отключение ведения журнала агентов. По умолчанию регистрация включена.

  - Указание расположения файлов журнала агента. Значением по умолчанию является %ExchangeInstallPath%TransportRoles\\Logs\\Hub\\AgentLog.

  - Указание максимального размера для отдельных файлов журнала агента. Значение по умолчанию — 10 мегабайт (МБ).

  - Указание максимального размера для каталога, содержащего файлы журнала агента. Размер по умолчанию — 250 МБ.

  - Указание максимального срока хранения для файлов журнала агента. Значение по умолчанию – 7 дней.

Для упрощения контроля расходования пространства на диске, используемого файлами журнала, в службе Exchange используется циклическое ведение журнала для ограничения размера журналов агентов на основе размера файлов и срока их хранения.

**Содержание**

Обзор агентов транспорта

Структура файлов журнала агента

Сведения, записываемые в журнал агента

Поиск журналов агентов

## Обзор агентов транспорта

Агенты могут воздействовать на сообщения только в определенных точках последовательности команд SMTP, используемых для транспортировки сообщений через транспортную службу на сервере почтовых ящиков или пограничном транспортном сервере. Эти точки доступа в последовательности команд SMTP называются *события SMTP*. Каждому агенту можно назначить приоритет. Однако события SMTP всегда должны происходить в определенном порядке. Следовательно, приоритет агента зависит от события SMTP. Если два агента выполняют действие над сообщением во время одного события SMTP, агент, обладающий более высоким приоритетом, выполнит действие первым.

В следующей таблице перечислены события SMTP в порядке их наступления и агенты, которые записывают данные в журнал агентов в порядке приоритета, начиная с наивысшего, для каждого события SMTP.

### События SMTP в порядке их наступления и агенты, которые записывают данные в журнал агентов в порядке приоритета для каждого события SMTP

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Событие SMTP</th>
<th>Agent</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>OnConnect</strong></p></td>
<td><p>Агент фильтрации подключений</p></td>
</tr>
<tr class="even">
<td><p><strong>OnMailCommand</strong></p></td>
<td><p>Агент фильтрации подключений</p>
<p>Агент фильтра отправителей</p></td>
</tr>
<tr class="odd">
<td><p><strong>OnRcptCommand</strong></p></td>
<td><p>Агент фильтрации подключений</p>
<p>Агент фильтра получателей</p></td>
</tr>
<tr class="even">
<td><p><strong>OnEndOfHeaders</strong></p></td>
<td><p>Агент фильтрации подключений</p>
<p>Агент идентификации отправителей</p>
<p>Агент фильтра отправителей</p></td>
</tr>
<tr class="odd">
<td><p><strong>OnEndOfData</strong></p></td>
<td><p>Агент пограничных правил</p>
<p>Агент фильтрации содержимого</p></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Агент фильтрации подключений и агент пограничных правил недоступны на серверах почтовых ящиков.</td>
</tr>
</tbody>
</table>


Дополнительные сведения об агентах, событиях SMTP и приоритете агентов см. в разделе [Агенты транспорта](transport-agents-exchange-2013-help.md).

В начало

## Структура файлов журнала агента

Журналы агентов находятся в папке %ExchangeInstallPath%TransportRoles\\Logs\\Hub\\AgentLog.

Имена файлов журнала агентов имеют следующий вид: AGENTLOG*yyyymmdd-nnnn*.log. Заполнители обозначают следующее:

  - Заполнитель *yyyymmdd* представляет собой дату в формате UTC, когда был создан файл журнала. При этом заполнитель *yyyy* обозначает год, *mm* — месяц, а *dd* — день.

  - Заменитель *nnnn* представляет собой порядковый номер, который каждый день начинается со значения 1.

Данные записываются в файл журнала до тех пор, пока размер файла не достигнет максимально допустимого значения и не откроется новый файл журнала, имеющий следующий порядковый номер. Эта процедура выполняется круглосуточно. При циклическом ведении журнала удаляются самые старые файлы журнала, когда каталог журналов агентов достигает максимально допустимого размера, или когда файл журнала достигает максимально допустимого срока хранения.

Файлы журнала агентов представляют собой текстовые файлы в формате CSV. Каждый файл журнала агентов снабжен заголовком, содержащим следующие сведения.

  - **\#Software**   Название программы, создавшей файл журнала агентов. Как правило, значением является: Microsoft Exchange Server.

  - **\#Version**   Номер версии программы, создавшей файл журнала агентов. Текущее значение — 15.0.0.0.

  - **\#Log-Type**   Тип журнала — «Agent Log».

  - **\#Date**   Дата и время создания файла журнала в формате UTC. Дата и время в формате UTC переводятся в формат по стандарту ISO 8601: *yyyy-mm-dd*T*hh:mm:ss.fff*Z, где *yyyy* — год, *mm* — месяц, *dd* — день, *hh* — час, *mm* — минута, *ss* — секунда, *fff* — доли секунды. "T" указывает на начало кода времени. "Z" значит "время зулу" (еще одно обозначение формата UTC).

  - **\#Fields**   Разделенные запятыми имена полей, используемые в файлах журнала агентов.

В начало

## Сведения, записываемые в журнал агента

В журнале агентов каждая транзакция агента хранится в отдельной строке. Сведения, хранящиеся в каждой строке, сгруппированы по полям. Поля разделяются запятыми. Как правило, имя поля достаточно полно характеризует информацию, которая в нем хранится. Однако некоторые поля могут быть пустыми. Кроме того, тип данных, хранящихся в поле, может меняться в зависимости от агента или действия, выполняемого агентом над сообщением. В следующей таблице описаны поля, используемые для классификации каждой транзакции агента.

### Поля, используемые для классификации каждой транзакции агента

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя поля</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Timestamp</strong></p></td>
<td><p>Дата и время события агента в формате UTC. Дата и время в формате UTC переводятся в формат по стандарту ISO 8601: <em>yyyy-mm-dd</em>T<em>hh:mm:ss.fff</em>Z, где <em>yyyy</em> — год, <em>mm</em> — месяц, <em>dd</em> — день, <em>hh</em> — час, <em>mm</em> — минута, <em>ss</em> — секунда, <em>fff</em> — доли секунды. &quot;T&quot; указывает на начало кода времени. &quot;Z&quot; значит &quot;время зулу&quot; (еще одно обозначение формата UTC).</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionId</strong></p></td>
<td><p>Уникальный идентификатор сеанса SMTP. Идентификатор представляется 16-значным шестнадцатеричным числом.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LocalEndpoint</strong></p></td>
<td><p>Локальный IP-адрес и номер порта, принявшего сообщение. Сеансы SMTP обычно используют порт 25.</p></td>
</tr>
<tr class="even">
<td><p><strong>RemoteEndpoint</strong></p></td>
<td><p>IP-адрес и номер порта предыдущего сервера SMTP, подключавшегося к данному серверу для доставки сообщения. При прохождении потока почты из Интернета через пограничный транспортный сервер в сети периметра значением <strong>RemoteEndpoint</strong> в журнале агента на сервере почтовых ящиков будет IP-адрес пограничного транспортного сервера. Хотя сообщение передано с помощью протокола SMTP, номер порта, использованного для отправки, будет случайным числом больше 1 024.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EnteredOrgFromIP</strong></p></td>
<td><p>IP-адрес удаленного сервера SMTP, который первым подключается к организации Exchange, чтобы доставить сообщение. На пограничном транспортном сервере значения полей <strong>RemoteEndpoint</strong> и <strong>EnteredOrgFromIP</strong> одинаковы. Агенты защиты от нежелательной почты используют IP-адрес в поле <strong>EnteredOrgFromIP</strong> для проверки сообщения.</p></td>
</tr>
<tr class="even">
<td><p><strong>MessageId</strong></p></td>
<td><p>Значение поля заголовка <code>MessageID</code>. Если это значение пусто, транспортный сервер Exchange назначает произвольное значение, но только если сообщение принято. После этого значение поля <code>MessageID</code> остается постоянным на протяжении всего времени существования сообщения.</p></td>
</tr>
<tr class="odd">
<td><p><strong>P1FromAddress</strong></p></td>
<td><p>Адрес электронной почты отправителя, указанный в <code>MAIL FROM</code> конверта сообщения. Это значение используется для передачи сообщения между серверами обмена сообщениями SMTP. Это значение сравнивается со значением <strong>P2FromAddresses</strong> для определения того, не подделан ли адрес отправителя в заголовке сообщения.</p></td>
</tr>
<tr class="even">
<td><p><strong>P2FromAddresses</strong></p></td>
<td><p>Адрес электронной почты отправителя, указанный в поле заголовка <code>From</code> или в поле <code>Sender</code> заголовка сообщения.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Recipient</strong></p></td>
<td><p>Адреса электронной почты получателей. Хотя исходное сообщение может быть предназначено нескольким получателям, в одной строке журнала агентов показывается только один получатель.</p></td>
</tr>
<tr class="even">
<td><p><strong>NumRecipients</strong></p></td>
<td><p>Общее количество получателей исходного сообщения.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Агент</strong></p></td>
<td><p>Имя агента, выполнившего данное действие. Возможные значения:</p>
<ul>
<li><p>Агент фильтра содержимого</p></li>
<li><p>Агент фильтра получателей</p></li>
<li><p>Агент фильтра отправителей</p></li>
<li><p>Агент идентификации отправителей</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Event</strong></p></td>
<td><p>Событие SMTP, при котором агент выполнил действие. Значение поля <strong>Event</strong> зависит от агента. События SMTP, доступные для каждого агента, описаны в первой таблице данного раздела. Возможны следующие значения поля <strong>Event</strong>:</p>
<ul>
<li><p>OnConnect</p></li>
<li><p>OnEndOfHeaders</p></li>
<li><p>OnEndOfData</p></li>
<li><p>OnMailCommand</p></li>
<li><p>OnRcptCommand</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Action</strong></p></td>
<td><p>Выполненное агентом действие над сообщением. Возможны следующие значения поля <strong>Action</strong>:</p>
<ul>
<li><p>AcceptMessage</p></li>
<li><p>DeleteMessage</p></li>
<li><p>DeleteRecipients</p></li>
<li><p>Disconnect</p></li>
<li><p>QuarantineMessage</p></li>
<li><p>QuarantineRecipients</p></li>
<li><p>RejectAuthentication</p></li>
<li><p>RejectCommand</p></li>
<li><p>RejectConnection</p></li>
<li><p>RejectMessage</p></li>
<li><p>RejectRecipients</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>SmtpResponse</strong></p></td>
<td><p>Ответ Enhanced SMTP согласно RFC 2034.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Reason</strong></p></td>
<td><p>Причина действия, указанная агентом.</p></td>
</tr>
<tr class="even">
<td><p><strong>ReasonData</strong></p></td>
<td><p>Описание действия, указанное агентом.</p></td>
</tr>
</tbody>
</table>


В начало

## Поиск журналов агентов

Искать журналы агентов можно с помощью командлета **Get-AgentLog** и сценария **Get-AntiSpamFilteringReport.ps1**.

Сценарий **Get-AntiSpamFilteringReport.ps1** расположен в `%ExchangeInstallPath%Scripts`. Вам необходимо запустить сценарий в командной консоли из папки "Сценарии". Чтобы изменить расположение в командной консоли на папку сценариев, выполните следующую команду:

    Cd $env:ExchangeInstallPath\Scripts

Чтобы запустить папку сценариев, введите команду в следующем формате:

    .\Get-AntiSpamFilteringReport.ps1 -report <ReportValue> [<OptionalParameters>]

Для получения сведений об использовании сценария, выполните следующую команду:

    Get-Help -Detailed .\Get-AntiSpamFilteringReport.ps1

В начало
