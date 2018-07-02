---
title: 'Условия правил транспорта (предикаты): Exchange 2013 Help'
TOCTitle: Условия и исключения (предикаты) правил потока обработки почты
ms:assetid: c918ea00-1e68-4b8b-8d51-6966b4432e2d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638183(v=EXCHG.150)
ms:contentKeyID: 50489068
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Условия правил транспорта (предикаты)

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2017-12-20_

Условия и исключения в правилах потока обработки почты (также называемых правилами транспорта) определяют, к каким сообщениям правило применяется, а к каким — нет. Например, если правило добавляет к сообщениям заявление об отказе, вы можете настроить это правило так, чтобы оно применялось только к сообщениям от определенных пользователей, содержащим указанные слова, или ко всем сообщениям, кроме тех, которые были отправлены участникам определенной группы. Совокупное название условий и исключений в правилах потока обработки почты — *предикаты*, так как для каждого условия существует аналогичное исключение с такими же параметрами и синтаксисом. Единственное отличие заключается в том, что условия указывают, к каким сообщениям правило применяется, а исключения — наоборот.

Большинство условий и исключений содержат только одно свойство, принимающее одно или несколько значений. Например, для условия **Отправитель** необходимо указать отправителя сообщения. У некоторых условий есть два свойства. Например, для условия **Заголовок сообщения включает любое из этих слов** необходимо указать в одном свойстве поле заголовка сообщения, а в другом — искомый текст. У некоторых условий и исключений нет свойств. Например, условие **В любом вложении есть исполняемое содержимое** просто ищет в сообщениях вложения с исполняемым содержимым.

Дополнительные сведения о правилах поток почты в Exchange Server 2013[Правила обработки почтового потока и транспорта](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)см.

Дополнительные сведения о условий и исключений в правилах поток почты в Exchange Online Protection или Exchange Online можно [Почтовые поток правила условий и исключений (предикаты) в Exchange Online](https://technet.microsoft.com/ru-ru/library/jj919235\(v=exchg.150\)) или [Почтовые поток правила условий и исключений (предикаты) в Exchange Online Protection](https://technet.microsoft.com/ru-ru/library/jj919234\(v=exchg.150\)).

## Условия и исключения для правил потока обработки почты на серверах почтовых ящиков

В таблицах в следующих разделах описываются условия и исключения, доступных в правилах поток почты на серверах почтовых ящиков. Типы свойств описаны в разделе типы свойств .

Отправители

Получатели

Тема или текст сообщения

Вложения

Все получатели

Типы конфиденциальной информации, значения в полях "Кому" и "Копия", размер и кодировки сообщений

Отправитель и получатель

Свойства сообщения

Заголовки сообщений

**Примечания.**

  - Когда вы выберете условие или исключение в Центре администрирования Exchange (EAC), значение, которое в итоге отобразится в поле **Применить это правило, если** или **Кроме случаев, когда**, скорее всего, будет короче указанного (если вы составляли его из частей). Кроме того, при создании правил на основе шаблона (отфильтрованного списка сценариев) часто можно не составлять условие из частей, а выбрать для него краткое имя. Краткие имена и полные названия условий и исключений представлены в столбцах с данными по Центру администрирования Exchange.

  - Если в Центре администрирования Exchange выбрано условие **\[Применить ко всем сообщениям\]**, указывать другие условия невозможно. В командной консоли Exchange для создания такого правила достаточно не указывать никаких параметров условий.

  - Условия и исключения содержат одни и те же параметры и свойства, поэтому в выходных данных командлета **Get-TransportRulePredicate** исключения не указываются отдельно. Кроме того, имена некоторых предикатов, возвращаемые этим командлетом, отличаются от имен соответствующих параметров, а в предикате может потребоваться указать несколько параметров.

## Отправители

Для условий и исключений, проверяющих адрес отправителя, можно указать, где правило будет искать этот адрес.

Откройте Центр администрирования Exchange и в разделе **Свойства этого правила** выберите **Соответствие адреса отправителя в сообщении**. Обратите внимание, что для отображения этого параметра может потребоваться выбрать **Дополнительные параметры**. В командной консоли Exchange для этого используется параметр *SenderAddressLocation*. Ниже представлены возможные значения.

  - **Заголовок** (Header). Проверяются только отправители в заголовках сообщений (например, полях **From**, **Sender** или **Reply-To**). Это значение по умолчанию, которое использовалось в правилах потока обработки почты до выпуска накопительного пакета обновления 1 (CU1) для Exchange 2013.

  - **Конверт**. Проверяются только отправители из конверта сообщения (значение **MAIL FROM**, используемое при передаче данных по протоколу SMTP, которое обычно хранится в поле **Return-Path**). Обратите внимание на то, что поиск в конверте сообщения доступен только для следующих условий (и соответствующих исключений):
    
      - **Отправитель** (*From*)
    
      - **Отправитель входит в группу** (*FromMemberOf*)
    
      - **Адрес отправителя содержит** (*FromAddressContainsWords*)
    
      - **Адрес отправителя соответствует** (*FromAddressMatchesPatterns*)
    
      - **Домен отправителя** (*SenderDomainIs*)

  - **Заголовок или конверт** (`HeaderOrEnvelope`). Проверяются отправители в заголовке и конверте сообщения.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Условие или исключение в Центре администрирования Exchange</th>
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Отправитель...</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Является этим пользователем</strong></p></td>
<td><p><em>From</em></p>
<p><em>ExceptIfFrom</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, отправленные указанными почтовыми ящиками, почтовыми пользователями или почтовыми контактами в организации Exchange.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Расположение отправителя</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Является внешним/внутренним</strong></p></td>
<td><p><em>FromScope</em></p>
<p><em>ExceptIfFromScope</em></p></td>
<td><p><code>UserScopeFrom</code></p></td>
<td><p>Сообщения от внутренних или внешних отправителей.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Отправитель входит в группу</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Является членом этой группы</strong></p></td>
<td><p><em>FromMemberOf</em></p>
<p><em>ExceptIfFromMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, отправленные участником заданной группы.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Адрес отправителя содержит</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Имеет адрес, который содержит любое из этих слов</strong></p></td>
<td><p><em>FromAddressContainsWords</em></p>
<p><em>ExceptIfFromAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, электронный адрес отправителя которых содержит указанные слова.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Адрес отправителя совпадает с</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Имеет адрес, который соответствует любому из этих текстовых шаблонов</strong></p></td>
<td><p><em>FromAddressMatchesPatterns</em></p>
<p><em>ExceptIfFromAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, электронный адрес отправителя которых содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Указанные свойства отправителя включают любое из этих слов</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Имеет свойства, включающие любое из этих слов</strong></p></td>
<td><p><em>SenderADAttributeContainsWords</em></p>
<p><em>ExceptIfSenderADAttributeContainsWords</em></p></td>
<td><p>Первое свойство: <code>ADAttribute</code></p>
<p>Второе свойство: <code>Words</code></p></td>
<td><p>Сообщения, в которых заданный атрибут Active Directory отправителя содержит любые из указанных слов.</p>
<p>Обратите внимание, что в атрибуте <strong>Country</strong> должен быть указан двухбуквенный код страны (например, DE для Германии).</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Указанные свойства отправителя совпадают с этими текстовыми шаблонами</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Имеет свойства, соответствующие этим текстовым шаблонам</strong></p></td>
<td><p><em>SenderADAttributeMatchesPatterns</em></p>
<p><em>ExceptIfSenderADAttributeMatchesPatterns</em></p></td>
<td><p>Первое свойство: <code>ADAttribute</code></p>
<p>Второе свойство: <code>Patterns</code></p></td>
<td><p>Сообщения, в которых заданный атрибут Active Directory отправителя содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Отправитель переопределил подсказку политики</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Переопределил подсказку политики</strong></p></td>
<td><p><em>HasSenderOverride</em></p>
<p><em>ExceptIfHasSenderOverride</em></p></td>
<td><p>Н/д</p></td>
<td><p>Сообщения, для которых отправитель переопределил политику защиты от потери данных (DLP). Дополнительные сведения о политиках защиты от потери данных см. в статье <a href="technical-overview-of-dlp-data-loss-prevention-in-exchange.md">Защита от потери данных</a>.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>IP-адрес отправителя находится в диапазоне</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Имеет IP-адрес, который находится в одном из этих диапазонов или точно совпадает</strong></p></td>
<td><p><em>SenderIPRanges</em></p>
<p><em>ExceptIfSenderIPRanges</em></p></td>
<td><p><code>IPAddressRanges</code></p></td>
<td><p>Сообщения, IP-адрес отправителя которых совпадает с указанным IP-адресом или находится в указанном диапазоне IP-адресов.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Домен отправителя...</strong></p>
<p><strong>Отправитель</strong> &gt; <strong>Принадлежит к домену</strong></p></td>
<td><p><em>SenderDomainIs</em></p>
<p><em>ExceptIfSenderDomainIs</em></p></td>
<td><p><code>DomainName</code></p></td>
<td><p>Сообщения, в которых домен электронного адреса отправителя совпадает с указанным значением.</p>
<p>Если требуется найти домены отправителя, которые <em>содержат</em> указанный домен (например, любой его поддомен), используйте условие <strong>Адрес отправителя соответствует</strong> (<em>FromAddressMatchesPatterns</em>) и укажите домен, используя синтаксис <code>'@domain\.com$'</code>.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Получатели


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Условие или исключение в Центре администрирования Exchange</th>
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Получатель</strong></p>
<p><strong>Получатель</strong> &gt; <strong>Является этим пользователем</strong></p></td>
<td><p><em>SentTo</em></p>
<p><em>ExceptIfSentTo</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, одним из получателей которых является указанный почтовый ящик, почтовый пользователь или почтовый контакт в организации Exchange. Получатели могут быть указаны в поле <strong>To</strong>, <strong>Cc</strong> или <strong>Bcc</strong> сообщения.</p>
<p><strong>Примечание.</strong> Нельзя указать группы рассылки или поддерживающие почту группы безопасности. Если необходимо предпринимать действия в отношении сообщений, отправляемых в группу, используйте условие <strong>Поле &quot;Кому&quot; содержит</strong> (<em>AnyOfToHeader</em>).</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Расположение получателя</strong></p>
<p><strong>Получатель</strong> &gt; <strong>Является внешним/внутренним</strong></p></td>
<td><p><em>SentToScope</em></p>
<p><em>ExceptIfSentToScope</em></p></td>
<td><p><code>UserScopeTo</code></p></td>
<td><p>Сообщения, отправленные внутренним получателям, внешним получателям, внешним получателям из партнерских организаций или внешним получателям из организаций, не являющихся партнерскими.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Получатель входит в группу</strong></p>
<p><strong>Получатель</strong> &gt; <strong>Является членом этой группы</strong></p></td>
<td><p><em>SentToMemberOf</em></p>
<p><em>ExceptIfSentToMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, у которых есть получатели, являющиеся членами указанной группы. Группа может быть указана в поле <strong>To</strong>, <strong>Cc</strong> или <strong>Bcc</strong> сообщения.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Адрес получателя содержит</strong></p>
<p><strong>Получатель</strong> &gt; <strong>Имеет адрес, который содержит любое из этих слов</strong></p></td>
<td><p><em>RecipientAddressContainsWords</em></p>
<p><em>ExceptIfRecipientAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, электронный адрес получателя которых содержит указанные слова.</p>
<p><strong>Примечание.</strong> Это условие не учитывает сообщения, отправленные на прокси-адреса получателя. Сопоставляются только сообщения, отправленные на основной электронный адрес получателя.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Адрес получателя соответствует</strong></p>
<p><strong>Получатель</strong> &gt; <strong>Имеет адрес, который соответствует любому из этих текстовых шаблонов</strong></p></td>
<td><p><em>RecipientAddressMatchesPatterns</em></p>
<p><em>ExceptIfRecipientAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, электронный адрес получателя которых содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p>
<p><strong>Примечание.</strong> Это условие не учитывает сообщения, отправленные на прокси-адреса получателя. Сопоставляются только сообщения, отправленные на основной электронный адрес получателя.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Указанные свойства получателя содержат любое из следующих слов</strong></p>
<p><strong>Получатель</strong> &gt; <strong>Имеет свойства, включающие любое из этих слов</strong></p></td>
<td><p><em>RecipientADAttributeContainsWords</em></p>
<p><em>ExceptIfRecipientADAttributeContainsWords</em></p></td>
<td><p>Первое свойство: <code>ADAttribute</code></p>
<p>Второе свойство: <code>Words</code></p></td>
<td><p>Сообщения, в которых заданный атрибут Active Directory получателя содержит любое из указанных слов.</p>
<p>Обратите внимание, что в атрибуте <strong>Country</strong> должен быть указан двухбуквенный код страны (например, DE для Германии).</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Указанные свойства получателя соответствуют этим текстовым шаблонам</strong></p>
<p><strong>Получатель</strong> &gt; <strong>Имеет свойства, соответствующие этим текстовым шаблонам</strong></p></td>
<td><p><em>RecipientADAttributeMatchesPatterns</em></p>
<p><em>ExceptIfRecipientADAttributeMatchesPatterns</em></p></td>
<td><p>Первое свойство: <code>ADAttribute</code></p>
<p>Второе свойство: <code>Patterns</code></p></td>
<td><p>Сообщения, в которых заданный атрибут Active Directory получателя содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Домен получателя...</strong></p>
<p><strong>Получатель</strong> &gt; <strong>Принадлежит к домену</strong></p></td>
<td><p><em>RecipientDomainIs</em></p>
<p><em>ExceptIfRecipientDomainIs</em></p></td>
<td><p><code>DomainName</code></p></td>
<td><p>Сообщения, в которых домен электронного адреса получателя совпадает с указанным значением.</p>
<p>Если требуется найти домены получателя, которые <em>содержат</em> указанный домен (например, любой его поддомен), используйте условие <strong>Адрес получателя соответствует</strong> (<em>RecipientAddressMatchesPatterns</em>) и укажите домен, используя синтаксис <code>'@domain\.com$'</code>.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Тема или текст сообщения

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Поиск слов и текстовых шаблонов в теме или других полях заголовка сообщения выполняется <em>после</em> расшифровки сообщения, к которому применялся метод кодирования для передачи сообщений MIME. Этот метод используется для передачи двоичных сообщений между SMTP-серверами с преобразованием их в текст ASCII. Вы не можете применять условия или исключения для поиска необработанных закодированных значений (обычно в формате Base64) в теме или других полях заголовка сообщения.</td>
</tr>
</tbody>
</table>



<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Условие или исключение в Центре администрирования Exchange</th>
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Тема или текст содержат</strong></p>
<p><strong>Тема или текст</strong> &gt; <strong>Тема или текст сообщения содержит любые из следующих слов</strong></p></td>
<td><p><em>SubjectOrBodyContainsWords</em></p>
<p><em>ExceptIfSubjectOrBodyContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, в которых поле <strong>Subject</strong> или текст содержит указанные слова.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Тема или основной текст соответствует</strong></p>
<p><strong>Тема или текст</strong> &gt; <strong>Тема или текст сообщения соответствует этим шаблонам текста</strong></p></td>
<td><p><em>SubjectOrBodyMatchesPatterns</em></p>
<p><em>ExceptIfSubjectOrBodyMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, в которых поле <strong>Subject</strong> или текст содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Тема содержит</strong></p>
<p><strong>Тема или текст</strong> &gt; <strong>Тема содержит любое из этих слов</strong></p></td>
<td><p><em>SubjectContainsWords</em></p>
<p><em>ExceptIfSubjectContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, в которых поле <strong>Subject</strong> содержит указанные слова.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Тема соответствует</strong></p>
<p><strong>Тема или текст</strong> &gt; <strong>Тема соответствует этим текстовым шаблонам</strong></p></td>
<td><p><em>SubjectMatchesPatterns</em></p>
<p><em>ExceptIfSubjectMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, в которых поле <strong>Subject</strong> содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Вложения

Дополнительные сведения о как правила потока почты проверки вложений сообщений можно [Использование правил транспорта для проверки вложений сообщений](use-transport-rules-to-inspect-message-attachments-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Условие или исключение в Центре администрирования Exchange</th>
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Содержимое любого вложения включает</strong></p>
<p><strong>Любое вложение</strong> &gt; <strong>Имеет содержимое, которое включает любое из этих слов</strong></p></td>
<td><p><em>AttachmentContainsWords</em></p>
<p><em>ExceptIfAttachmentContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, вложения которых содержат указанные слова.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Содержимое любого вложения совпадает с</strong></p>
<p><strong>Любое вложение</strong> &gt; <strong>Имеет содержимое, которое соответствует этим текстовым шаблонам</strong></p></td>
<td><p><em>AttachmentMatchesPatterns</em></p>
<p><em>ExceptIfAttachmentMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, вложения которых содержат текстовые шаблоны, соответствующие указанным регулярным выражениям.</p>
<p><strong>Примечание.</strong> Проверяются только первые 150 КБ каждого вложения.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Невозможно проверить содержимое каких-либо вложений</strong></p>
<p><strong>Любое вложение</strong> &gt; <strong>Имеет содержимое, которое невозможно просмотреть</strong></p></td>
<td><p><em>AttachmentIsUnsupported</em></p>
<p><em>ExceptIfAttachmentIsUnsupported</em></p></td>
<td><p>Н/д</p></td>
<td><p>Сообщения вложение не будет изначально распознаваемых Exchange, куда требуется IFilter не установлен на сервере почтовых ящиков. Для получения дополнительных сведений см <a href="register-filter-pack-ifilters-with-exchange-2013-exchange-2013-help.md">Регистрация фильтров IFilter из пакета фильтров с помощью Exchange 2013</a>.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Любое имя вложенного файла, соответствующее</strong></p>
<p><strong>Любое вложение</strong> &gt; <strong>Содержит файл, имя которого соответствует этим текстовым шаблонам</strong></p></td>
<td><p><em>AttachmentNameMatchesPatterns</em></p>
<p><em>ExceptIfAttachmentNameMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, в которых имя файла вложения содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Расширение файла любого вложения соответствует</strong></p>
<p><strong>Любое вложение</strong> &gt; <strong>Содержит файл, расширение которого включает эти слова</strong></p></td>
<td><p><em>AttachmentExtensionMatchesWords</em></p>
<p><em>ExceptIfAttachmentExtensionMatchesWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, в которых расширение файла вложения совпадает с любым из указанных свойств.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Любое вложение размером не менее</strong></p>
<p><strong>Любое вложение &gt; Имеет размер не меньше</strong></p></td>
<td><p><em>AttachmentSizeOver</em></p>
<p><em>ExceptIfAttachmentSizeOver</em></p></td>
<td><p><code>Size</code></p></td>
<td><p>Сообщения, содержащие вложения, размер которых равен заданному или превышает его.</p>
<p>В Центре администрирования Exchange указать размер можно только в килобайтах (КБ).</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Сообщение не завершило сканирование</strong></p>
<p><strong>Любое вложение</strong> &gt; <strong>Не прошло сканирование</strong></p></td>
<td><p><em>AttachmentProcessingLimitExceeded</em></p>
<p><em>ExceptIfAttachmentProcessingLimitExceeded</em></p></td>
<td><p>Н/д</p></td>
<td><p>Сообщения, для которых обработчику правил не удалось завершить сканирование вложений. С помощью этого условия можно создавать правила, которые совместно определяют и обрабатывают сообщения, содержимое которых не полностью прошло сканирование.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Любое вложение содержит исполняемое содержимое</strong></p>
<p><strong>Любое вложение</strong> &gt; <strong>Содержит исполняемое содержимое</strong></p></td>
<td><p><em>AttachmentHasExecutableContent</em></p>
<p><em>ExceptIfAttachmentHasExecutableContent</em></p></td>
<td><p>Н/д</p></td>
<td><p>Сообщения, которые содержат вложения, являющиеся исполняемыми файлами. Система просматривает свойства файла, а не только его расширение.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Любое вложение защищено паролем</strong></p>
<p><strong>Любое вложение</strong> &gt; <strong>Защищено паролем</strong></p></td>
<td><p><em>AttachmentIsPasswordProtected</em></p>
<p><em>ExceptIfAttachmentIsPasswordProtected</em></p></td>
<td><p>Н/Д</p></td>
<td><p>Сообщения с вложениями, защищенными паролем (такие файлы нельзя проверить). Обнаружение пароля работает только для документов Office и ZIP-файлов.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Все получатели

Условия и исключения в этом разделе предоставляют уникальную возможность, влияющую на *всех* получателей, если сообщение содержит как минимум одного из указанных получателей. Допустим, у вас есть правило, которое отклоняет сообщения. При использовании условия из раздела Получатели сообщение отклоняется только для указанных получателей. Например, если правило обнаружит в сообщении указанного получателя, но это у этого сообщения есть еще пять получателей, то оно будет отклонено для указанного получателя и доставлено пяти остальным.

Если добавить условие для получателей из данного радела, сообщение будет отклонено как для обнаруженного получателя, так и для пяти остальных пользователей.

И наоборот, исключение для получателей из данного раздела *предотвращает* применение правила ко *всем* (а не только к обнаруженным) получателям сообщения.

**Примечание.** Это условие не учитывает сообщения, отправленные на прокси-адреса получателя. Сопоставляются только сообщения, отправленные на основной электронный адрес получателя.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Условие или исключение в Центре администрирования Exchange</th>
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Адрес какого-либо получателя содержит</strong></p>
<p><strong>Любой получатель</strong> &gt; <strong>Имеет адрес, который содержит любое из этих слов</strong></p></td>
<td><p><em>AnyOfRecipientAddressContainsWords</em></p>
<p><em>ExceptIfAnyOfRecipientAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, в которых поле <strong>To</strong>, <strong>Cc</strong> или <strong>Bcc</strong> содержит указанные слова.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Адрес какого-либо получателя соответствует</strong></p>
<p><strong>Любой получатель</strong> &gt; <strong>Имеет адрес, который соответствует любому из этих текстовых шаблонов</strong></p></td>
<td><p><em>AnyOfRecipientAddressMatchesPatterns</em></p>
<p><em>ExceptIfAnyOfRecipientAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, в которых поле <strong>To</strong>, <strong>Cc</strong> или <strong>Bcc</strong> содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Типы конфиденциальной информации, значения в полях "Кому" и "Копия", размер и кодировки сообщений

Условия в этом разделе, основанные на значениях в полях **To** и **Cc**, действуют как условия в разделе Любой получатель (правило затрагивает *всех*, а не только обнаруженных получателей сообщения).

**Примечание.** Это условие не учитывает сообщения, отправленные на прокси-адреса получателя. Сопоставляются только сообщения, отправленные на основной электронный адрес получателя.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Условие или исключение в Центре администрирования Exchange</th>
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Сообщение содержит конфиденциальные сведения</strong></p>
<p><strong>Сообщение</strong> &gt; <strong>Содержит любой из этих типов конфиденциальной информации</strong></p></td>
<td><p><em>MessageContainsDataClassifications</em></p>
<p><em>ExceptIfMessageContainsDataClassifications</em></p></td>
<td><p><code>SensitiveInformationTypes</code></p></td>
<td><p>Сообщения, которые содержат конфиденциальную информацию, определенную в политиках защиты от потери данных (DLP).</p>
<p>Это условие необходимо для правил, использующих действие <strong>Уведомить отправителя подсказкой политики</strong> (<em>NotifySender</em>).</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Поле &quot;Кому&quot; содержит</strong></p>
<p><strong>Сообщение</strong> &gt; <strong>Содержит этого пользователя в поле &quot;Кому&quot;</strong></p></td>
<td><p><em>AnyOfToHeader</em></p>
<p><em>ExceptIfAnyOfToHeader</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, в которых поле <strong>To</strong> содержит какого-либо из указанных получателей.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Поле &quot;Кому&quot; содержит члена группы</strong></p>
<p><strong>Сообщение</strong> &gt; <strong>Содержит члена этой группы в поле &quot;Кому&quot;</strong></p></td>
<td><p><em>AnyOfToHeaderMemberOf</em></p>
<p><em>ExceptIfAnyOfToHeaderMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, в которых поле <strong>To</strong> содержит получателя, являющегося членом указанной группы.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Поле &quot;Копия&quot; содержит</strong></p>
<p><strong>Сообщение</strong> &gt; <strong>Содержит этого пользователя в поле &quot;Копия&quot;</strong></p></td>
<td><p><em>AnyOfCcHeader</em></p>
<p><em>ExceptIfAnyOfCcHeader</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, в которых поле <strong>Cc</strong> содержит какого-либо из указанных получателей.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Поле &quot;Копия&quot; содержит члена группы</strong></p>
<p><strong>Сообщение</strong> &gt; <strong>Содержит члена этой группы в поле &quot;Копия&quot;</strong></p></td>
<td><p><em>AnyOfCcHeaderMemberOf</em></p>
<p><em>ExceptIfAnyOfCcHeaderMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, в которых поле <strong>Cc</strong> содержит получателя, являющегося членом указанной группы.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Поле &quot;Кому&quot; или &quot;Копия&quot; содержит</strong></p>
<p><strong>Сообщение</strong> &gt; <strong>Содержит этого пользователя в поле &quot;Кому&quot; или &quot;Копия&quot;</strong></p></td>
<td><p><em>AnyOfToCcHeader</em></p>
<p><em>ExceptIfAnyOfToCcHeader</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, в которых поле <strong>To</strong> или <strong>Cc</strong> содержит какого-либо из указанных получателей.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Поле &quot;Кому&quot; или &quot;Копия&quot; содержит члена группы</strong></p>
<p><strong>Сообщение</strong> &gt; <strong>Содержит члена этой группы в поле &quot;Кому&quot; или &quot;Копия&quot;</strong></p></td>
<td><p><em>AnyOfToCcHeaderMemberOf</em></p>
<p><em>ExceptIfAnyOfToCcHeaderMemberOf</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, в которых поле <strong>To</strong> или <strong>Cc</strong> содержит получателя, являющегося членом указанной группы.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Размер сообщения превышает или равен</strong></p>
<p><strong>Сообщение</strong> &gt; <strong>Имеет размер не меньше</strong></p></td>
<td><p><em>MessageSizeOver</em></p>
<p><em>ExceptIfMessageSizeOver</em></p></td>
<td><p><code>Size</code></p></td>
<td><p>Сообщения, общий размер которых (сообщение и вложения) равен заданному или превышает его.</p>
<p>В Центре администрирования Exchange указать размер можно только в килобайтах (КБ).</p>
<p><strong>Примечание.</strong> Сначала выполняется проверка согласно ограничениям на размер сообщений, и только потом — согласно правилам потока обработки почты. Отправка слишком большого для почтового ящика сообщения будет отклонена прежде, чем сработает правило с соответствующим условием.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Имя набора символов включаем любое из этих слов</strong></p>
<p><strong>Сообщение</strong> &gt; <strong>Содержит в имени набора символов одно из этих слов</strong></p></td>
<td><p><em>ContentCharacterSetContainsWords</em></p>
<p><em>ExceptIfContentCharacterSetContainsWords</em></p></td>
<td><p><code>CharacterSets</code></p></td>
<td><p>Сообщения с какими-либо из указанных кодировок.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Отправитель и получатель


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Условие или исключение в Центре администрирования Exchange</th>
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Отправитель приходится получателю</strong></p>
<p><strong>Отправитель и получатель</strong> &gt; <strong>Отправитель относительно получателя</strong></p></td>
<td><p><em>SenderManagementRelationship</em></p>
<p><em>ExceptIfSenderManagementRelationship</em></p></td>
<td><p><code>ManagementRelationship</code></p></td>
<td><p>Сообщения, в которых отправитель является либо руководителем получателя, либо его подчиненным.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>сообщение пересылается между членами этих групп</strong></p>
<p><strong>Отправитель и получатель</strong> &gt; <strong>Сообщение передается между членами этих групп</strong></p></td>
<td><p><em>BetweenMemberOf1</em> и <em>BetweenMemberOf2</em></p>
<p><em>ExceptIfBetweenMemberOf1</em> и <em>ExceptIfBetweenMemberOf2</em></p></td>
<td><p><code>Addresses</code></p></td>
<td><p>Сообщения, отправляемые между участниками заданных групп.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Руководитель отправителя или получателя</strong></p>
<p><strong>Отправитель и получатель</strong> &gt; <strong>Начальником отправителя или получателя является этот пользователь</strong></p></td>
<td><p><em>ManagerForEvaluatedUser</em> и <em>ManagerAddress</em></p>
<p><em>ExceptIfManagerForEvaluatedUser</em> и <em>ExceptIfManagerAddress</em></p></td>
<td><p>Первое свойство: <code>EvaluatedUser</code></p>
<p>Второе свойство: <code>Addresses</code></p></td>
<td><p>Сообщения, отправители или получатели которых являются подчиненными указанного пользователя.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Сравнение свойства отправителя со свойством какого-либо получателя дает результат</strong></p>
<p><strong>Отправитель и получатель</strong> &gt; <strong>Свойство отправителя и получателя относятся как</strong></p></td>
<td><p><em>ADAttributeComparisonAttribute</em> и <em>ADComparisonOperator</em></p>
<p><em>ExceptIfADAttributeComparisonAttribute</em> и <em>ExceptIfADComparisonOperator</em></p></td>
<td><p>Первое свойство: <code>ADAttribute</code></p>
<p>Второе свойство: <code>Evaluation</code></p></td>
<td><p>Сообщения, в которых у отправителя и получателя совпадают или не совпадают значения указанного атрибута Active Directory.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Свойства сообщения


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Условие или исключение в Центре администрирования Exchange</th>
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Тип сообщения</strong></p>
<p><strong>Свойства сообщения</strong> &gt; <strong>Включают тип сообщения</strong></p></td>
<td><p><em>MessageTypeMatches</em></p>
<p><em>ExceptIfMessageTypeMatches</em></p></td>
<td><p><code>MessageType</code></p></td>
<td><p>Сообщения указанного типа.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если Outlook или Outlook Web App настроен для пересылки сообщения, свойство <strong>ForwardingSmtpAddress</strong> добавляется к сообщению. Тип сообщения не будет изменено на <code>AutoForward</code>.</td>
</tr>
</tbody>
</table>

</td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Сообщение классифицировано как</strong></p>
<p><strong>Свойства сообщения</strong> &gt; <strong>Включают эту классификацию</strong></p></td>
<td><p><em>HasClassification</em></p>
<p><em>ExceptIfHasClassification</em></p></td>
<td><p><code>MessageClassification</code></p></td>
<td><p>Сообщения с указанной классификацией. Это пользовательская классификация сообщений, которую можно создать в организации с помощью командлета <strong>New-MessageClassification</strong>.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Сообщению не присвоена какая-либо классификация</strong></p>
<p><strong>Свойства сообщения</strong> &gt; <strong>Не содержат классификаций</strong></p></td>
<td><p><em>HasNoClassification</em></p>
<p><em>ExceptIfHasNoClassification</em></p></td>
<td><p>Н/д</p></td>
<td><p>Сообщения, у которых нет классификации.</p></td>
<td><p>Exchange 2010 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Сообщение имеет значение вероятности нежелательной почты не менее</strong></p>
<p><strong>Свойства сообщения</strong> &gt; <strong>Включают уровень вероятности нежелательной почты больший или равный</strong></p></td>
<td><p><em>SCLOver</em></p>
<p><em>ExceptIfSCLOver</em></p></td>
<td><p><code>SCLValue</code></p></td>
<td><p>Сообщения, которым назначена вероятность нежелательной почты, равная указанному значению или превышающая его.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><strong>Важность сообщения имеет значение</strong></p>
<p><strong>Свойства сообщения</strong> &gt; <strong>Включают уровень важности</strong></p></td>
<td><p><em>WithImportance</em></p>
<p><em>ExceptIfWithImportance</em></p></td>
<td><p><code>Importance</code></p></td>
<td><p>Сообщения с указанным уровнем важности.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Заголовки сообщений

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Поиск слов и текстовых шаблонов в теме или других полях заголовка сообщения выполняется <em>после</em> расшифровки сообщения, к которому применялся метод кодирования для передачи сообщений MIME. Этот метод используется для передачи двоичных сообщений между SMTP-серверами с преобразованием их в текст ASCII. Вы не можете применять условия или исключения для поиска необработанных закодированных значений (обычно в формате Base64) в теме или других полях заголовка сообщения.</td>
</tr>
</tbody>
</table>



<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Условие или исключение в Центре администрирования Exchange</th>
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Заголовок сообщения включает</strong></p>
<p><strong>Заголовок сообщения</strong> &gt; <strong>Включает любое из этих слов</strong></p></td>
<td><p><em>HeaderContainsMessageHeader</em> и <em>HeaderContainsWords</em></p>
<p><em>ExceptIfHeaderContainsMessageHeader</em> и <em>ExceptIfHeaderContainsWords</em></p></td>
<td><p>Первое свойство: <code>MessageHeaderField</code></p>
<p>Второе свойство: <code>Words</code></p></td>
<td><p>Сообщения, которые содержат указанное поле заголовка. Значение этого поля содержит указанные слова.</p>
<p>Имя поля заголовка и значение этого поля всегда используются вместе.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><strong>Заголовок сообщения соответствует</strong></p>
<p><strong>Заголовок сообщения</strong> &gt; <strong>Соответствует этим текстовым шаблонам</strong></p></td>
<td><p><em>HeaderMatchesMessageHeader</em> и <em>HeaderMatchesPatterns</em></p>
<p><em>ExceptIfHeaderMatchesMessageHeader</em> и <em>ExceptIfHeaderMatchesPatterns</em></p></td>
<td><p>Первое свойство: <code>MessageHeaderField</code></p>
<p>Второе свойство: <code>Patterns</code></p></td>
<td><p>Сообщения, которые содержат указанное поле заголовка. Значение этого поля содержит указанные регулярные выражения.</p>
<p>Имя поля заголовка и значение этого поля всегда используются вместе.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Условия и исключения для правил потока обработки почты на пограничных транспортных серверах

В правилах потока обработки почты на пограничных транспортных серверах доступны только некоторые из условий и исключений, доступных на серверах почтовых ящиков. На пограничных транспортных серверах недоступен Центр администрирования Exchange, поэтому управлять правилами потока обработки почты на локальном пограничном транспортном сервере можно только с помощью командной консоли Exchange. В представленной ниже таблице описываются эти условия и исключения. Типы свойств описываются в разделе Типы свойств.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметры условий и исключений в командной консоли Exchange</th>
<th>Тип свойства</th>
<th>Описание</th>
<th>Доступен в</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AnyOfRecipientAddressContainsWords</em></p>
<p><em>ExceptIfAnyOfRecipientAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, в которых поля <strong>To</strong>, <strong>Cc</strong> или <strong>Bcc</strong> содержат указанные слова.</p>
<p>Если сообщение содержит указанного получателя, действие правила применяется (или не применяется) ко <em>всем</em> получателям сообщения. Например, сообщение отклоняется для всех получателей сообщения, а не только для указанного пользователя.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><em>AnyOfRecipientAddressMatchesPatterns</em></p>
<p><em>ExceptIfAnyOfRecipientAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, в которых поле <strong>To</strong>, <strong>Cc</strong> или <strong>Bcc</strong> содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p>
<p>Если сообщение содержит указанного получателя, действие правила применяется (или не применяется) ко <em>всем</em> получателям сообщения. Например, сообщение отклоняется для всех получателей сообщения, а не только для указанного пользователя.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><em>AttachmentSizeOver</em></p>
<p><em>ExceptIfAttachmentSizeOver</em></p></td>
<td><p><code>Size</code></p></td>
<td><p>Сообщения, содержащие вложения, размер которых равен заданному или превышает его.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><em>FromAddressContainsWords</em></p>
<p><em>ExceptIfFromAddressContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, электронный адрес отправителя которых содержит указанные слова.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><em>FromAddressMatchesPatterns</em></p>
<p><em>ExceptIfFromAddressMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, электронный адрес отправителя которых содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><em>FromScope</em></p>
<p><em>ExceptIfFromScope</em></p></td>
<td><p><code>UserScopeFrom</code></p></td>
<td><p>Сообщения от внутренних или внешних отправителей.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><em>HeaderContainsMessageHeader</em> и <em>HeaderContainsWords</em></p>
<p><em>ExceptIfHeaderContainsMessageHeader</em> и <em>ExceptIfHeaderContainsWords</em></p></td>
<td><p>Первое свойство: <code>MessageHeaderField</code></p>
<p>Второе свойство: <code>Words</code></p></td>
<td><p>Сообщения, которые содержат указанное поле заголовка. Значение этого поля содержит указанные слова.</p>
<p>Имя поля заголовка и значение этого поля всегда используются вместе.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><em>HeaderMatchesMessageHeader</em> и <em>HeaderMatchesPatterns</em></p>
<p><em>ExceptIfHeaderMatchesMessageHeader</em> и <em>ExceptIfHeaderMatchesPatterns</em></p></td>
<td><p>Первое свойство: <code>MessageHeaderField</code></p>
<p>Второе свойство: <code>Patterns</code></p></td>
<td><p>Сообщения, которые содержат указанное поле заголовка. Значение этого поля содержит указанные регулярные выражения.</p>
<p>Имя поля заголовка и значение этого поля всегда используются вместе.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><em>MessageSizeOver</em></p>
<p><em>ExceptIfMessageSizeOver</em></p></td>
<td><p><code>Size</code></p></td>
<td><p>Сообщения, общий размер которых (сообщение и вложения) равен заданному или превышает его.</p></td>
<td><p>Exchange 2013 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><em>SCLOver</em></p>
<p><em>ExceptIfSCLOver</em></p></td>
<td><p><code>SCLValue</code></p></td>
<td><p>Сообщения, которым назначена вероятность нежелательной почты, равная указанному значению или превышающая его.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><em>SubjectContainsWords</em></p>
<p><em>ExceptIfSubjectContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, в которых поле <strong>Subject</strong> содержит указанные слова.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><em>SubjectMatchesPatterns</em></p>
<p><em>ExceptIfSubjectMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, в которых поле <strong>Subject</strong> содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="odd">
<td><p><em>SubjectOrBodyContainsWords</em></p>
<p><em>ExceptIfSubjectOrBodyContainsWords</em></p></td>
<td><p><code>Words</code></p></td>
<td><p>Сообщения, в которых поле <strong>Subject</strong> или текст содержит указанные слова.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
<tr class="even">
<td><p><em>SubjectOrBodyMatchesPatterns</em></p>
<p><em>ExceptIfSubjectOrBodyMatchesPatterns</em></p></td>
<td><p><code>Patterns</code></p></td>
<td><p>Сообщения, в которых поле <strong>Subject</strong> или текст содержит текстовые шаблоны, соответствующие указанным регулярным выражениям.</p></td>
<td><p>Exchange 2007 или более поздней версии</p></td>
</tr>
</tbody>
</table>


К началу страницы

## Типы свойств

В представленной ниже таблице описываются типы свойств, используемые в условиях и исключениях.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если свойство — это строка, конечные пробелы не допускаются.</td>
</tr>
</tbody>
</table>



<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Тип свойства</th>
<th>Допустимые значения</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>ADAttribute</code></p></td>
<td><p>Выберите из встроенного списка атрибутов Active Directory</p></td>
<td><p>UNRESOLVED_TOKENBLOCK_VAL(PD_Transport_Rules_ADAttributes_Snippet)</p>
<p>Чтобы указать в Центре администрирования Exchange несколько слов или текстовых шаблонов для одного атрибута, разделите их запятыми. Например, значение <strong>Москва,Екатеринбург</strong> атрибута <strong>Город</strong> позволяет находить пользователей из Москвы или Екатеринбурга.</p>
<p>В командной консоли Exchange используйте синтаксис <code>&quot;AttributeName1:Value1,Value 2 with spaces,Value3...&quot;,&quot;AttributeName2:Word4,Value 5 with spaces,Value6...&quot;</code>, где <code>Value</code> — это искомое слово или текстовый шаблон.</p>
<p>Пример: <code>&quot;City:San Francisco,Palo Alto&quot;</code> или <code>&quot;City:San Francisco,Palo Alto&quot;</code>,<code>&quot;Department:Sales,Finance&quot;</code>.</p>
<p>Если указано несколько атрибутов (или несколько значений для одного атрибута), используется оператор <strong>or</strong>. Не используйте значения с пробелами в начале или в конце.</p>
<p>Обратите внимание, что атрибут <strong>Country</strong> принимает значение двухбуквенного кода страны по стандарту ISO 3166-1 (например, DE для Германии). Найти значение можно на странице <a href="https://go.microsoft.com/fwlink/p/?linkid=331680">https://go.microsoft.com/fwlink/p/?LinkId=331680</a>.</p></td>
</tr>
<tr class="even">
<td><p><code>Addresses</code></p></td>
<td><p>Получатели в Exchange</p></td>
<td><p>В зависимости от характера условия или исключения, вы можете указать любой объект в организации, поддерживающий почту (например, для условий, связанных с получателями), или только объект определенного типа (например, группы для условий, связанных с членством в группах). Кроме того, условие или исключение может принимать только одно значение или поддерживать использование нескольких значений.</p>
<p>В Командная консоль Exchange эти значения следует разделять запятыми.</p>
<p><strong>Примечание.</strong> Это условие не учитывает сообщения, отправленные на прокси-адреса получателя. Сопоставляются только сообщения, отправленные на основной электронный адрес получателя.</p></td>
</tr>
<tr class="odd">
<td><p><code>CharacterSets</code></p></td>
<td><p>Массив имен кодировок</p></td>
<td><p>Одна или несколько кодировок содержимого, присутствующих в сообщении. Пример:</p>
<ul>
<li><p><code>Arabic/iso-8859-6</code></p></li>
<li><p><code>Chinese/big5</code></p></li>
<li><p><code>Chinese/euc-cn</code></p></li>
<li><p><code>Chinese/euc-tw</code></p></li>
<li><p><code>Chinese/gb2312</code></p></li>
<li><p><code>Chinese/iso-2022-cn</code></p></li>
<li><p><code>Cyrillic/iso-8859-5</code></p></li>
<li><p><code>Cyrillic/koi8-r</code></p></li>
<li><p><code>Cyrillic/windows-1251</code></p></li>
<li><p><code>Greek/iso-8859-7</code></p></li>
<li><p><code>Hebrew/iso-8859-8</code></p></li>
<li><p><code>Japanese/euc-jp</code></p></li>
<li><p><code>Japanese/iso-022-jp</code></p></li>
<li><p><code>Japanese/shift-jis</code></p></li>
<li><p><code>Korean/euc-kr</code></p></li>
<li><p><code>Korean/johab</code></p></li>
<li><p><code>Korean/ks_c_5601-1987</code></p></li>
<li><p><code>Turkish/windows-1254</code></p></li>
<li><p><code>Turkish/iso-8859-9</code></p></li>
<li><p><code>Vietnamese/tcvn</code></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><code>DomainName</code></p></td>
<td><p>Массив доменов SMTP</p></td>
<td><p>Пример: <code>contoso.com</code> или <code>eu.contoso.com</code>.</p>
<p>В командной консоли Exchange можно указать несколько доменов, разделив их запятыми.</p></td>
</tr>
<tr class="odd">
<td><p><code>EvaluatedUser</code></p></td>
<td><p>Одно значение: <strong>Sender</strong> или <strong>Recipient</strong></p></td>
<td><p>Указывает, чьего руководителя ищет правило: отправителя или получателя.</p></td>
</tr>
<tr class="even">
<td><p><code>Evaluation</code></p></td>
<td><p>Одно значение: <strong>Равно</strong> (Equal) или <strong>Не равно</strong> (<code>NotEqual</code>)</p></td>
<td><p>При сравнении атрибутов Active Directory отправителя и получателей данный параметр указывает, должны ли их значения совпадать.</p></td>
</tr>
<tr class="odd">
<td><p><code>Importance</code></p></td>
<td><p>Одно значение: <strong>Низкий</strong> (Low), <strong>Обычный</strong> (Normal) или <strong>Высокий</strong> (High)</p></td>
<td><p>Уровень важности, который был назначен сообщения по отправителям в Outlook или Outlook Web App.</p></td>
</tr>
<tr class="even">
<td><p><code>IPAddressRanges</code></p></td>
<td><p>Массив IP-адресов или диапазонов адресов</p></td>
<td><p>IPv4-адреса вводятся с использованием следующего синтаксиса:</p>
<ul>
<li><p><strong>Один IP-адрес</strong>. Пример: <code>192.168.1.1</code>.</p></li>
<li><p><strong>Диапазон IP-адресов</strong>. Пример: <code>192.168.0.1-192.168.0.254</code>.</p></li>
<li><p><strong>Диапазон IP-адресов CIDR</strong>. Пример: <code>192.168.0.1/25</code>.</p></li>
</ul>
<p>В командной консоли Exchange можно указать несколько IP-адресов или диапазонов, разделив их запятыми.</p></td>
</tr>
<tr class="odd">
<td><p><code>ManagementRelationship</code></p></td>
<td><p>Одно значение: <strong>Руководитель</strong> (Manager) или <strong>Подчиненный</strong> (<code>DirectReport</code>)</p></td>
<td><p>Задает отношение между отправителем и любым получателем. Правило проверяет атрибут <strong>Manager</strong> в Active Directory, чтобы узнать, является ли отправитель руководителем или подчиненным получателя.</p></td>
</tr>
<tr class="even">
<td><p><code>MessageClassification</code></p></td>
<td><p>Одна классификация сообщения</p></td>
<td><p>В Центре администрирования Exchange нужно выбрать одну из созданных классификаций в списке.</p>
<p>В командной консоли Exchange для указания классификации сообщения используется командлет <strong>Get-MessageClassification</strong>. Например, с помощью приведенной ниже команды можно найти сообщения с классификацией <code>Company Internal</code> и добавить перед темой сообщения значение <code>CompanyInternal</code>.</p>
<p><code>New-TransportRule &quot;Rule Name&quot; -HasClassification @(Get-MessageClassification &quot;Company Internal&quot;).Identity -PrependSubject &quot;CompanyInternal&quot;</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MessageHeaderField</code></p></td>
<td><p>Одиночная строка</p></td>
<td><p>Задает имя поля заголовка. Имя поля заголовка всегда используется вместе со значением этого поля (соответствие текстовому шаблону или слову).</p>
<p><em>Заголовок сообщения</em> — это коллекция обязательных и необязательных полей заголовка для сообщения. Примеры полей заголовков: <strong>To</strong>, <strong>From</strong>, <strong>Received</strong> и <strong>Content-Type</strong>. Официальные поля заголовков определены в стандарте RFC 5322. Неофициальные поля заголовков начинаются с &quot;<strong>X-</strong>&quot; и называются <em>X-заголовками</em>.</p></td>
</tr>
<tr class="even">
<td><p><code>MessageType</code></p></td>
<td><p>Одно значение типа сообщения</p></td>
<td><p>Задает один из следующих типов сообщения:</p>
<ul>
<li><p><strong>автоматический ответ</strong> (<code>OOF</code>);</p></li>
<li><p><strong>автоматическое перенаправление</strong> (<code>AutoForward</code>);</p></li>
<li><p><strong>зашифрованное сообщение</strong>;</p></li>
<li><p><strong>уведомление о календаре</strong>;</p></li>
<li><p><strong>с управлением разрешениями</strong> (<code>PermissionControlled</code>);</p></li>
<li><p><strong>сообщение голосовой почты</strong>;</p></li>
<li><p><strong>подписанное сообщение</strong>;</p></li>
<li><p><strong>запрос на подтверждение</strong> (<code>ApprovalRequest</code>);</p></li>
<li><p><strong>уведомление о прочтении</strong> (<code>ReadReceipt</code>).</p></li>
</ul>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если Outlook или Outlook Web App настроен для пересылки сообщения, свойство <strong>ForwardingSmtpAddress</strong> добавляется к сообщению. Тип сообщения не будет изменено на <code>AutoForward</code>.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="odd">
<td><p><code>Patterns</code></p></td>
<td><p>Массив регулярных выражений</p></td>
<td><p>Задает одно или несколько регулярных выражений, используемых для определения текстовых шаблонов в значениях. Дополнительные сведения см. в статье <a href="https://go.microsoft.com/fwlink/p/?linkid=180327">Синтаксис регулярного выражения</a>.</p>
<p>В командной консоли Exchange можно указать несколько регулярных выражений, разделив их запятыми и заключив каждое из них в кавычки (&quot;).</p></td>
</tr>
<tr class="even">
<td><p><code>SCLValue</code></p></td>
<td><p>Одно из указанных ниже значений:</p>
<ul>
<li><p><strong>Обойти фильтр нежелательной почты</strong> (<code>-1</code>).</p></li>
<li><p>Целые числа от 0 до 9.</p></li>
</ul></td>
<td><p>Указывает вероятность нежелательной почты, назначенную сообщению. Чем больше ее значение, тем вероятнее, что сообщение окажется спамом.</p></td>
</tr>
<tr class="odd">
<td><p><code>SensitiveInformationTypes</code></p></td>
<td><p>Массив типов конфиденциальной информации</p></td>
<td><p>Задает один или несколько типов конфиденциальной информации, определенные в вашей организации. Список типов встроенных конфиденциальных данных в разделе <a href="what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md">Что позволяют искать типы конфиденциальной информации в Exchange</a>.</p>
<p>В командной консоли Exchange используйте синтаксис <code>@{&lt;SensitiveInformationType1&gt;},@{&lt;SensitiveInformationType2&gt;},...</code>. Например, чтобы найти содержимое, включающее как минимум два номера кредитных карт и как минимум один код банка ABA, используйте значение <code>@{Name=&quot;Credit Card Number&quot;; minCount=&quot;2&quot;},@{Name=&quot;ABA Routing Number&quot;; minCount=&quot;1&quot;}</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>Size</code></p></td>
<td><p>Одно значение размера</p></td>
<td><p>Задает размер вложения или всего сообщения.</p>
<p>В Центре администрирования Exchange указать размер можно только в килобайтах (КБ).</p>
<p>В командной консоли Exchange при вводе значения укажите одну из следующих единиц измерения:</p>
<ul>
<li><p><code>B</code> (байт)</p></li>
<li><p><code>KB</code> (килобайт)</p></li>
<li><p><code>MB</code> (мегабайт)</p></li>
<li><p><code>GB</code> (гигабайт)</p></li>
</ul>
<p>Например, <code>20MB</code></p>
<p>Значение без указания единицы измерения обычно обрабатывается как количество байт, но небольшие значения могут быть округлены до ближайшего значения в килобайтах.</p></td>
</tr>
<tr class="odd">
<td><p><code>UserScopeFrom</code></p></td>
<td><p>Одно значение: <strong>Внутри организации</strong> (<code>InOrganization</code>) или <strong>Вне организации</strong> (<code>NotInOrganization</code>)</p></td>
<td><p>Считается, что отправитель находится в организации, если выполняется какое-либо из следующих условий:</p>
<ul>
<li><p>Отправитель является почтовым ящиком, почтовым пользователем, группой или общедоступной папкой, поддерживающей почту, в Active Directory организации.</p></li>
<li><p>Адрес электронной почты отправителя находится в обслуживаемый домен, настроенный как уполномоченный домен или домен внутренней ретрансляции, <strong>и</strong> сообщение было, отправленных и полученных через подключение с проверкой подлинности. Дополнительные сведения об обслуживаемых доменов можно <a href="accepted-domains-exchange-2013-help.md">Обслуживаемые домены</a>.</p></li>
</ul>
<p>Считается, что отправитель находится вне организации, если выполняется какое-либо из следующих условий:</p>
<ul>
<li><p>Электронный адрес отправителя не находится на обслуживаемом домене.</p></li>
<li><p>Электронный адрес отправителя находится на обслуживаемом домене, настроенном как домен внешней ретрансляции.</p></li>
</ul>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Чтобы определить, где находятся почтовые контакты (в организации или вне ее), адрес отправителя сравнивают со списком обслуживаемых доменов организации.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="even">
<td><p><code>UserScopeTo</code></p></td>
<td><p>Одно из указанных ниже значений:</p>
<ul>
<li><p><strong>Внутри организации</strong> (<code>InOrganization</code>)</p></li>
<li><p><strong>Вне организации</strong> (<code>NotInOrganization</code>)</p></li>
<li><p><strong>Во внешней партнерской организации</strong> (<code>ExternalPartner</code>)</p></li>
<li><p><strong>Во внешней не партнерской организации</strong> (<code>ExternalNonPartner</code>)</p></li>
</ul></td>
<td><p>Считается, что получатель находится в организации, если выполняется какое-либо из следующих условий:</p>
<ul>
<li><p>Получатель является почтовым ящиком, почтовым пользователем, группой или общедоступной папкой, поддерживающей почту, в Active Directory организации.</p></li>
<li><p>Электронный адрес получателя находится на обслуживаемом домене, настроенном в качестве домена внутренней ретрансляции или уполномоченного домена, <strong>и</strong> сообщение было отправлено или получено через подключение с проверкой подлинности.</p></li>
</ul>
<p>Считается, что получатель находится вне организации, если выполняется какое-либо из следующих условий:</p>
<ul>
<li><p>Электронный адрес получателя не находится на обслуживаемом домене.</p></li>
<li><p>Электронный адрес получателя находится на обслуживаемом домене, настроенном в качестве домена внешней ретрансляции.</p></li>
</ul>
<p>Внешние партнерские организации — это внешние домены, на которых параметры безопасности домена (взаимная проверка подлинности TLS) настроены на отправку почты.</p>
<p>Внешние не партнерские организации — это все остальные внешние домены, которые не считаются партнерскими доменами.</p></td>
</tr>
<tr class="odd">
<td><p><code>Words</code></p></td>
<td><p>Массив строк</p></td>
<td><p>Задает одно или несколько искомых слов. При поиске слов не учитывается регистр. Кроме того, в начале и в конце этих слов можно добавлять пробелы и знаки препинания. Подстановочные знаки и частичные совпадения не поддерживаются.</p>
<p>Например, &quot;contoso&quot; совпадает с &quot; Contoso.&quot;. Однако если текст окружен другими символами, он не считается совпадением. Например, &quot;contoso&quot; не совпадает со следующими значениями:</p>
<ul>
<li><p>Acontoso</p></li>
<li><p>Contosoa</p></li>
<li><p>Acontosob</p></li>
</ul>
<p>Звездочка (*) считается литералом и не используется в качестве подстановочного знака.</p></td>
</tr>
</tbody>
</table>


В начало

## Дополнительные сведения

[Правила обработки почтового потока и транспорта](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)

[Действия правил транспорта](mail-flow-rule-actions-in-exchange-2013-exchange-2013-help.md)

[Процедуры правил обработки почтового потока и транспорта](mail-flow-or-transport-rule-procedures-exchange-2013-help.md)

[Почтовые поток правила условий и исключений (предикаты) в Exchange Online](https://technet.microsoft.com/ru-ru/library/jj919235\(v=exchg.150\)) для Exchange Online

[Почтовые поток правила условий и исключений (предикаты) в Exchange Online Protection](https://technet.microsoft.com/ru-ru/library/jj919234\(v=exchg.150\)) для Exchange Online Protection

