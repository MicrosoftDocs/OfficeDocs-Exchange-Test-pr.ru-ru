﻿---
title: 'Использование командной консоли Exchange для управления очередями: Exchange 2013 Help'
TOCTitle: Использование командной консоли Exchange для управления очередями
ms:assetid: 5433c1d3-ad2e-4f82-b50d-b67964b32f26
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa998047(v=EXCHG.150)
ms:contentKeyID: 51408039
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Использование командной консоли Exchange для управления очередями

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Как и в предыдущих версиях Exchange, вы можете использовать командную консоль Exchange в Microsoft Exchange Server 2013 для просмотра сведений об очередях и сообщениях в этих очередях, а также для управления ими. В Exchange 2013 очереди размещаются на серверах почтовых ящиков и пограничных транспортных серверах. В этом разделе такие серверы называются *транспортными*.

При использовании командной консоли для просмотра очередей и сообщений на транспортных серверах и управления ими важно понимать, как определить очереди или сообщения, которые вам нужны. Обычно на транспортных серверах размещается множество очередей и сообщений, которые необходимо доставить. Чтобы определить нужные элементы, используются параметры фильтрации, доступные в командлетах управления очередями и сообщениями.

Для управления элементами вы также можете воспользоваться средством просмотра очереди в панели элементов Exchange. Однако командлеты поддерживают больше свойств и параметров фильтрации, чем средство просмотра очереди. Дополнительные сведения о средстве просмотра очереди см. в разделе [Средство просмотра очереди](queue-viewer-exchange-2013-help.md).

**Содержание**

  - Queue filtering parameters
    
      - Queue identity
    
      - Queue Filter parameter
    
      - Include and Exclude parameters

  - Get-QueueDigest

  - Message filtering parameters
    
      - Message identity
    
      - Message Filter parameter
    
      - Queue parameter

  - Comparison operators to use when filtering queues or messages

  - Advanced paging parameters

## Параметры фильтрации очередей

В приведенной ниже таблице описываются параметры фильтрации, доступные в командлетах управления очередями.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Командлет</th>
<th>Параметры фильтрации</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Get-Queue</strong></p></td>
<td><p><em>Identity</em></p>
<p><em>Filter</em></p>
<p><em>Include</em></p>
<p><em>Exclude</em></p></td>
<td><p>Параметр <em>Identity</em> нельзя использовать вместе с параметром <em>Filter</em>. Параметры <em>Include</em> и <em>Exclude</em> можно использовать вместе с параметром <em>Filter</em>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Resume-Queue</strong></p>
<p><strong>Retry-Queue</strong></p>
<p><strong>Suspend-Queue</strong></p></td>
<td><p><em>Identity</em></p>
<p><em>Filter</em></p></td>
<td><p>Вы можете использовать параметр <em>Identity</em> или <em>Filter</em>, но не оба параметра в одной команде.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Get-QueueDigest</strong></p></td>
<td><p><em>Server</em></p>
<p><em>Dag</em></p>
<p><em>Site</em></p>
<p><em>Forest</em></p>
<p><em>Filter</em></p></td>
<td><p>Вы можете использовать параметр <em>Server</em>, <em>Dag</em>, <em>Site</em> или <em>Forest</em>, но их нельзя использовать вместе в одной команде. Параметр <em>Filter</em> можно использовать с любыми другими параметрами фильтрации.</p></td>
</tr>
</tbody>
</table>


Обратите внимание, что параметр *Server* доступен во всех командлетах управления очередями. В командлете **Get-QueueDigest** параметр *Server* определяет область действия — сервер или серверы, на которых нужно просмотреть сводные данные об очередях. Во всех других командлетах вы используете параметр *Server* для подключения к определенному серверу и выполнения команд управления на нем. Параметр *Server* можно использовать вместе с *Filter* или без него, но параметр *Server* нельзя применять вместе с *Identity*. В параметре *Server* указывается имя узла или полное доменное имя транспортного сервера.

В начало

## Идентификатор очереди

Параметр *Identity* в командлетах управления очередями указывает очередь. При использовании параметра *Identity* нельзя указать другие параметры фильтрации очередей, так как вы и так уже задали конкретную очередь. Параметр *Identity* использует базовый синтаксис *\<Сервер\>*\\*\<Очередь\>*.

*\<Сервер\>* — это имя узла или полное доменное имя сервера Exchange, например `mailbox01` или `mailbox01.contoso.com`. Если опустить квалификатор *\<Сервер\>*, используется локальный сервер.

В квалификаторе \<*Очередь*\> можно указать одно из следующих значений:

  - **Постоянное имя очереди**. Постоянные очереди обладают уникальными согласованными именами на всех серверах почтовых ящиков и пограничных транспортных серверах. Постоянные имена очередей:
    
      - **Отправка**. Эта очередь содержит сообщения, ожидающие обработки классификатором.
    
      - **Недоступно**. Эта очередь содержит сообщения, которые невозможно маршрутизировать. Данная очередь не существует, пока в нее не будут добавлены сообщения.
    
      - **Запрещенное сообщение**. Эта очередь содержит сообщения, которые считаются потенциально вредными для сервера Exchange. Данная очередь не существует, пока в нее не будут добавлены сообщения.

  - **Имя очереди доставки**. Имя очереди доставки — это значение свойства **NextHopDomain** очереди. Например, именем очереди может быть адресное пространство соединителя отправки, имя сайта Active Directory или имя группы обеспечения доступности базы данных. Подробнее см. в подразделе "NextHopSolutionKey" темы [Очереди](queues-exchange-2013-help.md).

  - **Номер очереди**. Очередям доставки и теневым очередям в базе данных очередей назначается уникальное целочисленное значение. Но для получения номера очереди из свойств **Identity** или **QueueIdentity** нужно выполнить командлет **Get-Queue**.

  - **Имя теневой очереди**. Теневые очереди используют следующий синтаксис: `Shadow\`*\<QueueInteger\>*

В приведенной ниже таблице описывается синтаксис, который можно использовать в параметре *Identity* в командлетах управления очередями. Во всех значениях *\<Сервер\>* означает имя узла или полное доменное имя сервера.

### Форматы идентификатора очереди

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Недопустимое значение параметра</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>&lt;Server&gt;\&lt;PersistentQueueName&gt;</code> или <code>&lt;PersistentQueueName&gt;</code></p></td>
<td><p>Постоянная очередь на заданном или локальном сервере.</p>
<p><em>&lt;PersistentQueueName&gt;</em> — это <code>Submission</code>, <code>Unreachable</code> или <code>Poison</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>&lt;Server&gt;\&lt;NextHopDomain&gt;</code> или <code>&lt;NextHopDomain&gt;</code></p></td>
<td><p>Очередь доставки на заданном или локальном сервере.</p>
<p><em>&lt;NextHopDomain&gt;</em> — конечный пункт маршрутизации или группа доставки сообщений в очереди. Подробнее см. в подразделе &quot;NextHopSolutionKey&quot; темы <a href="queues-exchange-2013-help.md">Очереди</a>.</p></td>
</tr>
<tr class="odd">
<td><p><code>&lt;Server&gt;\&lt;QueueInteger&gt;</code> или <code>&lt;QueueInteger&gt;</code></p></td>
<td><p>Очередь доставки на заданном или локальном сервере.</p>
<p><em>&lt;QueueInteger&gt;</em> — это уникальное целое значение очереди, отображаемое в свойстве <strong>Identity</strong> командлета <strong>Get-Queue</strong>.</p></td>
</tr>
<tr class="even">
<td><p><code>&lt;Server&gt;\Shadow\&lt;QueueInteger&gt;</code> или <code>Shadow\&lt;QueueInteger&gt;</code></p></td>
<td><p>Теневая очередь на заданном или локальном сервере.</p></td>
</tr>
<tr class="odd">
<td><p><code>&lt;Server&gt;\*</code> или <code>*</code></p></td>
<td><p>Все очереди на заданном или локальном сервере. Учтите, что эти значения можно использовать только в командлете <strong>Get-Queue</strong>.</p></td>
</tr>
</tbody>
</table>


В начало

## Параметр фильтрации очередей

Параметр *Filter* можно использовать во всех командлетах управления очередями для указания нужных очередей на основе их свойств. Параметр *Filter* создает выражение с операторами сравнения, ограничивающими область применения операции до очередей, соответствующих фильтру. Логический оператор `-and` можно использовать для указания нескольких условий, которым должны соответствовать результаты.

Полный список свойств очередей, которые можно использовать с параметром *Filter*, см. в разделе [Очереди](queues-exchange-2013-help.md).

Список операторов сравнения, которые можно использовать с параметром *Filter*, см. в подразделе Comparison operators to use when filtering queues or messages далее в этом разделе.

Примеры процедур, применяющих параметр *Filter* для просмотра очередей и управления ими, см. в разделе [Управление очередями](manage-queues-exchange-2013-help.md).

В начало

## Параметры Include и Exclude

Для командлета `Get-Queue` в Exchange 2013 доступны параметры *Include* и *Exclude*. Их можно использовать по отдельности, друг с другом или вместе с параметром *Filter* для сужения выборки очередей на локальном или заданном транспортном сервере. Например:

  - можно исключить из результатов пустые очереди;

  - можно исключить очереди для внешних адресов;

  - можно включить очереди с определенным значением свойства **DeliveryType**.

Параметры *Include* и *Exclude* используют следующие свойства очередей для фильтрации:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Значение</th>
<th>Описание</th>
<th>Пример кода командной консоли</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>DeliveryType</code></p></td>
<td><p>Это значение включает или исключает очереди на основе свойства <strong>DeliveryType</strong>. Можно указать несколько значений, разделенных запятыми. Допустимые значения свойства <strong>DeliveryType</strong> описываются в подразделе &quot;NextHopSolutionKey&quot; раздела <a href="queues-exchange-2013-help.md">Очереди</a>.</p></td>
<td><p>Этот пример возвращает все очереди доставки на локальном сервере, следующий узел которых — это соединитель отправки на локальном сервере, настроенный для маршрутизации на промежуточный узел:</p>
<p><code>Get-Queue -Include SmartHostConnectorDelivery</code></p></td>
</tr>
<tr class="even">
<td><p><code>Empty</code></p></td>
<td><p>Это значение позволяет включить или исключить пустые очереди. У пустых очередей свойство <strong>MessageCount</strong> имеет значение <code>0</code>.</p></td>
<td><p>Этот пример возвращает все очереди на локальном сервере, содержащие сообщения</p>
<p><code>Get-Queue -Exclude Empty</code></p></td>
</tr>
<tr class="odd">
<td><p><code>External</code></p></td>
<td><p>Это значение включает или исключает очереди, для свойства <strong>NextHopCategory</strong> которых задано значение <code>External</code>.</p>
<p>Свойство <strong>DeliveryType</strong> внешних очередей всегда имеет одно из следующих значений:</p>
<ul>
<li><p><code>DeliveryAgent</code></p></li>
<li><p><code>DnsConnectorDelivery</code></p></li>
<li><p><code>NonSmtpGatewayDelivery</code></p></li>
<li><p><code>SmartHostConnectorDelivery</code></p></li>
</ul>
<p>Подробнее см. в подразделе &quot;NextHopSolutionKey&quot; темы <a href="queues-exchange-2013-help.md">Очереди</a>.</p></td>
<td><p>Этот пример возвращает все внутренние очереди на локальном сервере.</p>
<p><code>Get-Queue -Exclude External</code></p></td>
</tr>
<tr class="even">
<td><p><code>Internal</code></p></td>
<td><p>Это значение включает или исключает очереди, для свойства <strong>NextHopCategory</strong> которых задано значение <code>Internal</code>. Подробнее см. в подразделе &quot;NextHopSolutionKey&quot; темы <a href="queues-exchange-2013-help.md">Очереди</a>.</p></td>
<td><p>Этот пример возвращает все внутренние очереди на локальном сервере.</p>
<p><code>Get-Queue -Include Internal</code></p></td>
</tr>
</tbody>
</table>


Обратите внимание, что можно продублировать функции параметров *Include* и *Exclude*, используя параметр *Filter*. Например, команда `Get-Queue -Exclude Empty` дает тот же результат, что и `Get-Queue -Filter {MessageCount -gt 0}`. Однако синтаксис параметров *Include* и *Exclude* проще и его легче запомнить.

В начало

## Get-QueueDigest

В Exchange 2013 добавлен новый командлет с именем **Get-QueueDigest**. Он позволяет просматривать сведения о некоторых или всех очередях в организации Exchange с помощью одной команды. В частности, с помощью командлета **Get-QueueDigest** вы можете просмотреть информацию об очередях в зависимости от их расположения на серверах, в группах обеспечения доступности баз данных, на сайтах Active Directory или во всем лесу Active Directory. Обратите внимание, что очереди на подписанном пограничном транспортном сервере в сети периметра не включаются в результаты. Кроме того, командлет **Get-QueueDigest** доступен на пограничном транспортном сервере, но результаты ограничены очередями на данном сервере.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>По умолчанию командлет <strong>Get-QueueDigest</strong> отображает очереди доставки, включающие не менее десяти сообщений. Давность результатов составляет от одной до двух минут. Инструкции по смене этих значений по умолчанию приведены в статье <a href="configure-get-queuedigest-exchange-2013-help.md">Настройка Get-QueueDigest</a>.</td>
</tr>
</tbody>
</table>


Параметры фильтрации и сортировки, доступные в командлете **Get-QueueDigest**, приведены в следующей таблице.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Dag</em>, <em>Server</em> или <em>Site</em></p></td>
<td><p>Эти параметры являются взаимоисключающими и задают область действия командлета. Вы должны указать только один из них или переключатель <em>Forest</em>. Обычно используется имя сервера, группы обеспечения доступности базы данных или сайта Active Directory. Но вы также можете указать любое значение, уникально определяющее сервер, группу или сайт. Можно указать несколько серверов, групп доступности или сайтов, разделенных запятыми.</p></td>
</tr>
<tr class="even">
<td><p><em>Forest</em></p></td>
<td><p>Этот переключатель является обязательным, если не используется параметр <em>Dag</em>, <em>Server</em> или <em>Site</em>. Значение для этого переключателя указать нельзя. При использовании переключателя вы получаете все очереди с серверов почтовых ящиков Exchange 2013 в лесу Active Directory. Нельзя использовать переключатель <em>Forest</em> для просмотра очередей в удаленных лесах Active Directory.</p></td>
</tr>
<tr class="odd">
<td><p><em>DetailsLevel</em></p></td>
<td><p>Этот параметр может принимать значения <code>None</code>, <code>Normal</code> и <code>Verbose</code>. По умолчанию параметр имеет значение <code>Normal</code>. При использовании значения <code>None</code> имя очереди в столбце <strong>Сведения</strong> опускается.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>Данный параметр также позволяет фильтровать очереди на основе их свойств. Вы можете использовать любое из свойств, поддерживающих фильтрацию, как описано в разделе <a href="queue-filters-exchange-2013-help.md">Фильтры очередей</a>.</p></td>
</tr>
<tr class="odd">
<td><p><em>GroupBy</em></p></td>
<td><p>Этот параметр группирует результаты. Объединить результаты можно по одному из следующих свойств:</p>
<ul>
<li><p>DeliveryType</p></li>
<li><p>LastError</p></li>
<li><p>NextHopCategory</p></li>
<li><p>NextHopDomain</p></li>
<li><p>NextHopKey</p></li>
<li><p>Состояние</p></li>
<li><p>ServerName</p></li>
</ul>
<p>По умолчанию результаты группируются по свойству <code>NextHopDomain</code>. Дополнительные сведения об этих свойствах см. в разделе <a href="queue-filters-exchange-2013-help.md">Фильтры очередей</a>.</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>Этот параметр сужает результаты до заданного значения. Очереди сортируются по убыванию в зависимости от числа сообщений в них и группируются по значению, заданному параметром <em>GroupBy</em>. Значение по умолчанию — 1000. Это значит, что по умолчанию команда отображает первую тысячу очередей, сгруппированных по свойству <strong>NextHopDomain</strong> и упорядоченных по убыванию числа сообщений в очереди.</p></td>
</tr>
<tr class="odd">
<td><p><em>Timeout</em></p></td>
<td><p>Этот параметр задает количество секунд, в течение которых ожидается выполнение операции, прежде чем она будет блокирована по времени. Значение по умолчанию равно <code>00:00:10</code> или 10 секундам.</p></td>
</tr>
</tbody>
</table>


Этот пример возвращает все непустые внешние очереди на серверах почтовых ящиков Exchange 2013 с именами Mailbox01,Mailbox02 и Mailbox03.

    Get-QueueDigest -Server Mailbox01,Mailbox02,Mailbox03 -Include External -Exclude Empty

В начало

## Параметры фильтрации сообщений

В приведенной ниже таблице описываются параметры фильтрации, доступные в командлетах управления сообщениями.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Командлет</th>
<th>Параметры фильтрации</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Get-Message</strong></p></td>
<td><p><em>Identity</em></p>
<p><em>Filter</em></p>
<p><em>Queue</em></p></td>
<td><p>Все параметры фильтрации являются взаимоисключающими и их нельзя использовать вместе в одной команде.</p></td>
</tr>
<tr class="even">
<td><p><strong>Remove-Message</strong></p>
<p><strong>Resume-Message</strong></p>
<p><strong>Suspend-Message</strong></p></td>
<td><p><em>Identity</em></p>
<p><em>Filter</em></p></td>
<td><p>Вы можете использовать параметр <em>Identity</em> или <em>Filter</em>, но не оба параметра в одной команде.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Export-Message</strong></p></td>
<td><p><em>Identity</em></p></td>
<td><p>Параметр <em>Identity</em> обязателен.</p></td>
</tr>
</tbody>
</table>


Учтите, что параметр *Server* доступен во всех командлетах управления сообщениями, кроме командлета **Export-Message**. Параметр *Server* используется для подключения к определенному серверу и выполнения команд управления сообщениями на нем. Параметр *Server* можно использовать вместе с *Filter* или без него, но параметр *Server* нельзя применять вместе с *Identity*. В параметре *Server* указывается имя узла или полное доменное имя транспортного сервера.

В начало

## Идентификатор сообщения

Параметр *Identity* в командлетах управления сообщениями задает определенное сообщение в одной или нескольких очередях. При использовании параметра *Identity* нельзя указать другие параметры фильтрации сообщений, так как вы и так уже задали конкретное сообщение. Параметр *Identity* использует базовый синтаксис *\<Сервер\>*\\*\<Очередь\>*\\*\<MessageInteger\>*.

*\<Сервер\>* — это имя узла или полное доменное имя сервера Exchange, например `mailbox01` или `mailbox01.contoso.com`. Если опустить квалификатор *\<Сервер\>*, используется локальный сервер.

В квалификаторе \<*Очередь*\> указывается идентификатор очереди, как описано в подразделе "Идентификатор очереди" ранее. Например, можно использовать постоянное имя очереди, значение свойства **NextHopDomain** или уникальный целочисленный номер очереди в базе данных очередей.

*\<MessageInteger\>* представляет уникальное целое число, назначенное сообщению после первого попадания в базу данных очередей на сервере. Если сообщение отправляется нескольким получателям, которые используют множество очередей, все копии сообщения во всех очередях из базы данных очередей обладают одинаковым целочисленным номером. Но для получения номера сообщения из свойств **Identity** или **MessageIdentity** нужно выполнить командлет **Get-Message**.

В приведенной ниже таблице описывается синтаксис, который можно использовать в параметре *Identity* в командлетах управления сообщениями. Во всех значениях *\<Сервер\>* означает имя узла или полное доменное имя сервера.

### Форматы идентификатора сообщения

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Значение параметра Identity</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>&lt;Server&gt;\&lt;Queue&gt;\&lt;MessageInteger&gt;</code> или <code>&lt;Queue&gt;\&lt;MessageInteger&gt;</code></p></td>
<td><p>Сообщение в определенной очереди на заданном или локальном сервере.</p>
<p><em>&lt;MessageInteger&gt;</em> — это уникальное целое значение сообщения, отображаемое в свойстве <strong>Identity</strong> командлета <strong>Get-Message</strong>.</p>
<p><em>&lt;Очередь&gt;</em> представляет одно из следующих значений:</p>
<ul>
<li><p><strong>Постоянное имя очереди</strong>. Допустимые значения: <code>Submission</code>, <code>Unreachable</code> и <code>Poison</code>.</p></li>
<li><p><strong>Имя очереди доставки</strong>. Значение свойства <strong>NextHopDomain</strong> очереди, которое также является именем очереди. Это может быть конечный пункт маршрутизации или группа доставки. Подробнее см. в подразделе &quot;NextHopSolutionKey&quot; темы <a href="queues-exchange-2013-help.md">Очереди</a>.</p></li>
<li><p><strong>Номер очереди</strong> — это уникальное целое значение очереди доставки или теневой очереди, отображаемое в свойстве <strong>Identity</strong> командлета <strong>Get-Message</strong> или командлета <strong>Get-Queue</strong>.</p></li>
<li><p><strong>Идентификатор теневой очереди</strong>. Для идентификаторов теневых очередей используется следующий синтаксис: <code>Shadow\&lt;QueueInteger&gt;</code>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><code>&lt;Server&gt;\*\&lt;MessageInteger&gt;</code>, <code>*\&lt;MessageInteger&gt;</code> или <code>&lt;MessageInteger&gt;</code></p></td>
<td><p>Все копии сообщения во всех очередях в базе данных очередей на заданном или локальном сервере.</p></td>
</tr>
</tbody>
</table>


В начало

## Параметр фильтрации сообщений

Параметр *Filter* можно использовать в командлетах **Get-Message**, **Remove-Message**, **Resume-Message** и **Suspend-Message**, чтобы указать нужные сообщения с помощью его свойств. Параметр *Filter* создает выражение с операторами сравнения, ограничивающими область применения операции до сообщений, соответствующих фильтру. Логический оператор `-and` можно использовать для указания нескольких условий, которым должны соответствовать результаты.

Полный список свойств сообщений, которые можно использовать с параметром *Filter*, см. в разделе [Очереди](queues-exchange-2013-help.md).

Список операторов сравнения, которые можно использовать с параметром *Filter*, см. в подразделе Comparison operators to use when filtering queues or messages далее в этом разделе.

Примеры процедур, применяющих параметр *Filter* для просмотра сообщений и управления ими, см. в разделе [Управление очередями](manage-queues-exchange-2013-help.md).

В начало

## Параметр Queue

Параметр *Queue* используется только в командлете **Get-Message**. Данный параметр используется для получения всех сообщений определенной очереди или всех сообщений из нескольких очередей, если указать подстановочный знак (\*). При использовании параметра *Queue* применяется формат идентификатора очереди *\<Сервер\>*\\*\<Очередь\>*, как описано в подразделе "Идентификатор очереди" ранее.

В начало

## Операторы сравнения, используемые при фильтрации очередей и сообщений

Когда вы создаете выражение фильтрации очередей или сообщений с помощью параметра *Filter*, следует добавить оператор сравнения для выбора нужного значения свойства. В следующей таблице приводятся операторы сравнения, которые можно использовать в выражениях фильтрации, и описывается действие каждого оператора. Для всех операторов регистр задаваемых значений не учитывается.

### Операторы сравнения

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Оператор</th>
<th>Функция</th>
<th>Пример кода командной консоли</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>-eq</code></p></td>
<td><p>Этот оператор указывает, что результаты должны быть равны значению свойства, которое приводится в выражении.</p></td>
<td><p>Чтобы отобразить список всех очередей, имеющих состояние повтора:</p>
<p><code>Get-Queue -Filter {Status -eq &quot;Retry&quot;}</code></p>
<p>Отображение списка всех сообщений, которые имеют состояние повтора:</p>
<p><code>Get-Message -Filter {Status -eq &quot;Retry&quot;}</code></p></td>
</tr>
<tr class="even">
<td><p><code>-ne</code></p></td>
<td><p>Этот оператор указывает, что результаты не должны быть равны значению свойства, которое приводится в выражении.</p></td>
<td><p>Чтобы отобразить список всех очередей, имеющих активное состояние:</p>
<p><code>Get-Queue -Filter {Status -ne &quot;Active&quot;}</code></p>
<p>Отображение списка всех очередей, имеющих активное состояние:</p>
<p><code>Get-Message -Filter {Status -ne &quot;Active&quot;}</code></p></td>
</tr>
<tr class="odd">
<td><p><code>-gt</code></p></td>
<td><p>Этот оператор используется со свойствами, значения которых выражаются в виде целого числа или даты и времени. Результаты фильтрации включают в себя те очереди или сообщения, у которых значение указанного свойства больше, чем значение, приведенное в выражении.</p></td>
<td><p>Чтобы отобразить список очередей, содержащих в текущий момент более 1000 сообщений:</p>
<p><code>Get-Queue -Filter {MessageCount -gt 1000}</code></p>
<p>Отображение списка сообщений, для которых в текущий момент число попыток больше 3:</p>
<p><code>Get-Message -Filter {RetryCount -gt 3}</code></p></td>
</tr>
<tr class="even">
<td><p><code>-ge</code></p></td>
<td><p>Этот оператор используется со свойствами, значения которых выражаются в виде целого числа или даты и времени. Результаты фильтрации включают в себя те очереди или сообщения, у которых значение указанного свойства больше или равно значению, приведенному в выражении.</p></td>
<td><p>Чтобы отобразить список очередей, содержащих в текущий момент 1000 сообщений или более:</p>
<p><code>Get-Queue -Filter {MessageCount -ge 1000}</code></p>
<p>Отображение списка сообщений, для которых в текущий момент число попыток равно 3 или более:</p>
<p><code>Get-Message -Filter {RetryCount -ge 3}</code></p></td>
</tr>
<tr class="odd">
<td><p><code>-lt</code></p></td>
<td><p>Этот оператор используется со свойствами, значения которых выражаются в виде целого числа или даты и времени. Результаты фильтрации включают в себя те очереди или сообщения, у которых значение указанного свойства меньше, чем значение, приведенное в выражении.</p></td>
<td><p>Чтобы отобразить список очередей, содержащих в текущий момент менее 1000 сообщений:</p>
<p><code>Get-Queue -Filter {MessageCount -lt 1000}</code></p>
<p>Отображение списка сообщений, для которых вероятность нежелательной почты меньше 6:</p>
<p><code>Get-Message -Filter {SCL -lt 6}</code></p></td>
</tr>
<tr class="even">
<td><p><code>-le</code></p></td>
<td><p>Этот оператор используется со свойствами, значения которых выражаются в виде целого числа или даты и времени. Результаты фильтрации включают в себя те очереди или сообщения, у которых значение указанного свойства меньше или равно значению, приведенному в выражении.</p></td>
<td><p>Чтобы отобразить список очередей, содержащих в текущий момент 1000 сообщений или менее:</p>
<p><code>Get-Queue -Filter {MessageCount -le 1000}</code></p>
<p>Отображение списка сообщений, для которых вероятность нежелательной почты равна 6 или меньше:</p>
<p><code>Get-Message -Filter {SCL -le 6}</code></p></td>
</tr>
<tr class="odd">
<td><p><code>-like</code></p></td>
<td><p>Этот оператор используется со свойствами, значения которых выражаются в виде текстовой строки. Результаты фильтрации включают в себя те очереди или сообщения, у которых значение указанного свойства содержит текстовую строку, приведенную в выражении. В выражении <strong>-like</strong> можно использовать подстановочный знак *, который применяется к полю текстовой строки, но не к полю типа перечисления.</p></td>
<td><p>Чтобы отобразить список очередей доставки, назначениями которых являются любые SMTP-домены, заканчивающиеся на Contoso.com:</p>
<p><code>Get-Queue -Filter {Identity -like &quot;*contoso.com&quot;}</code></p>
<p>Отображение списка сообщений, тема которых содержит текст &quot;payday loan&quot;:</p>
<p><code>Get-Messages -Filter {Subject -like &quot;*payday loan*&quot;}</code></p></td>
</tr>
</tbody>
</table>


С помощью оператора сравнения **-and** вы можете указать фильтр, который использует несколько выражений. Чтобы попасть в результирующий набор, сообщения или очереди должны удовлетворять всем условиям фильтрации.

Этот пример отображает список очередей, назначениями которых являются любые имена SMTP-доменов, заканчивающихся на Contoso.com, и которые содержат более 500 сообщений.

    Get-Queue -Filter {Identity -like "*contoso.com*" -and MessageCount -gt 500}

Этот пример отображает список сообщений, отправленных с любого адреса в домене contoso.com, вероятность нежелательной почты которых больше 5.

    Get-Message -Filter {FromAddress -like "*Contoso.com*" -and SCL -gt 5}

В начало

## Расширенные параметры разбивки по страницам

В зависимости от текущего потока обработки почты запросы к очередям и сообщениям могут возвращать очень большой набор объектов. Для управления извлечением и отображением результатов запросов можно использовать расширенные параметры страниц.

При использовании командной консоли для просмотра очередей и сообщений, находящихся в очередях, запрос за один раз извлекает одну страницу данных. Расширенные параметры страниц управляют размером набора результатов и могут также применяться для сортировки результатов. Все расширенные параметры страниц применяются по мере необходимости и могут комбинироваться с любым из наборов параметров, которые используются в командлетах **Get-Queue** и **Get-Message**. Если расширенные параметры разбивки по страницам не указываются, запрос возвращает результаты в порядке возрастания идентификаторов.

По умолчанию при указании порядка сортировки свойство идентификатора сообщения всегда включается и сортируется в порядке возрастания. Данное отношение порядка применяется по умолчанию. Свойство идентификатора сообщения включается, поскольку другие свойства, которые могут включаться в порядок сортировки, не являются уникальными. Посредством явного включения свойства идентификации сообщения в порядок сортировки можно указать, что результаты должны отображать идентификаторы сообщений, отсортированные в порядке убывания.

С помощью параметров *BookmarkIndex* и *BookmarkObject* можно отметить позицию в отсортированном наборе результатов. Если при извлечении следующей страницы результатов объект закладки больше не существует, отношение порядка по умолчанию гарантирует, что набор результатов будет начинаться с объекта, расположенного ближе остальных к закладке. Ближайший объект определяется указанным порядком сортировки.

В следующей таблице описываются расширенные параметры разбивки по страницам.

### Расширенные параметры разбивки по страницам

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>BookmarkIndex</em></p></td>
<td><p>Этот параметр задает позицию в наборе результатов, с которой начинаются отображаемые результаты. Значение этого параметра — индекс в общем результирующем наборе с отсчетом от единицы. Если значение меньше или равно 0, возвращается первая полная страница результатов. Если значение равно <code>Int.MaxValue</code>, возвращается последняя полная страница результатов.</p></td>
</tr>
<tr class="even">
<td><p><em>BookmarkObject</em></p></td>
<td><p>Этот параметр задает объект в наборе результатов, с которого начинаются отображаемые результаты. Если указать объект закладки, этот объект используется в качестве пункта начала поиска. В зависимости от значения параметра <em>SearchForward</em> извлекаются строки, расположенные до или после этого объекта. В одиночном запросе нельзя одновременно использовать параметры <em>BookmarkObject</em> и <em>BookmarkIndex</em>.</p></td>
</tr>
<tr class="odd">
<td><p><em>IncludeBookmark</em></p></td>
<td><p>Этот параметр указывает, должен ли включаться объект закладки в набор результатов. По умолчанию для этого параметра устанавливается значение <code>$true</code>, и объект закладки включается в набор результатов. Можно выполнить запрос для получения результатов ограниченного размера, а затем указать последний элемент в этом наборе результатов в качестве закладки для следующего запроса. В этом случае, возможно, потребуется установить для параметра <em>IncludeBookmark</em> значение <code>$false</code>, чтобы объект не включался в оба набора результатов.</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>Этот параметр указывает число результатов, выводимых на каждой странице. Если значение не указано, по умолчанию используется размер результатов, равный 1000 объектам. Exchange ограничивает результирующий набор до 250 000 элементов.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReturnPageInfo</em></p></td>
<td><p>Это скрытый параметр. Он возвращает сведения об общем числе результатов и индекс первого объекта текущей страницы. По умолчанию используется значение <code>$false</code>.</p></td>
</tr>
<tr class="even">
<td><p><em>SearchForward</em></p></td>
<td><p>Этот параметр указывает, должен ли поиск в наборе результатов выполняться вперед или назад. Этот параметр не влияет на порядок, в котором возвращается набор результатов. Он определяет направление поиска относительно индекса или объекта закладки. Если не задан ни индекс, ни объект закладки, параметр <em>SearchForward</em> указывает, будет ли поиск начинаться с первого или последнего объекта в наборе результатов.</p>
<p>По умолчанию для этого параметра используется значение <code>$true</code>. Если для параметра установлено значение <code>$true</code> и задана закладка, запросом выполняется поиск в прямом направлении от закладки. Если используется данная настройка и после закладки нет результатов, запрос возвращает последнюю полную страницу результатов.</p>
<p>Если параметр <em>SearchForward</em> установлен равным <code>$false</code> и задана закладка, запросом выполняется поиск в обратном направлении от закладки. Если используется данная настройка и за закладкой имеется неполная страница результатов, запрос возвращает первую полную страницу результатов.</p></td>
</tr>
<tr class="odd">
<td><p><em>SortOrder</em></p></td>
<td><p>Этот параметр указывает массив свойств сообщений, которые используются для управления порядком сортировки набора результатов. Свойства порядка сортировки задаются в порядке убывания старшинства. Каждое свойство отделяется запятой и дополняется знаком &quot;плюс&quot; (+) для сортировки в порядке возрастания или знаком минус (-) для сортировки в порядке убывания.</p>
<p>Если с помощью этого параметра не указан явный порядок сортировки, то записи, соответствующие условиям запроса, отображаются и сортируются по полю Identity соответствующего типа объекта. Если порядок сортировки не задан в явном виде, результаты всегда сортируются по идентификатору в порядке возрастания.</p></td>
</tr>
</tbody>
</table>


В следующем примере кода показано, как использовать в запросе расширенные параметры страниц. В данном примере команда выполняет подключение к указанному серверу и извлекает набор результатов, содержащий 500 объектов. Результаты отображаются отсортированными сначала в порядке возрастания адреса отправителя, а затем в порядке убывания размера сообщения.

`Get-Message -Server mailbox01.contoso.com -ResultSize 500 -SortOrder +FromAddress,-Size`

Если требуется просмотреть последующие страницы, можно установить закладку для последнего извлеченного объекта в наборе результатов и выполнить дополнительный запрос. Для выполнения этой процедуры нужно использовать возможности работы со сценариями в командной консоли Exchange.

В следующем примере с помощью сценария извлекается первая страница результатов, устанавливается объект закладки, исключается объект закладки из набора результатов, и затем извлекаются следующие 500 объектов на указанном сервере.

1.  Откройте командную консоль и введите следующую команду, чтобы извлечь первую страницу результатов.
    
        $Results=Get-message -Server mailbox01.contoso.com -ResultSize 500 -SortOrder +FromAddress,-Size

2.  Чтобы установить объект закладки, введите следующую команду для сохранения последнего элемента первой страницы в переменной.
    
        $temp=$results[$results.length-1]

3.  Чтобы извлечь следующие 500 объектов на указанном сервере и исключить объект закладки, введите следующую команду.
    
        Get-message -Server mailbox01.contoso.com -BookmarkObject:$temp -IncludeBookmark $False -ResultSize 500 -SortOrder +FromAddress,-Size

В начало
