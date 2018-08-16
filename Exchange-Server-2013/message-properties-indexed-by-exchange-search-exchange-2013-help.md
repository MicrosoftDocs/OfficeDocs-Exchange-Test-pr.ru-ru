---
title: 'Exchange 2013: свойства сообщений, индексированные службой поиска Exchange'
TOCTitle: Свойства сообщений, индексированные службой поиска Exchange
ms:assetid: a9754dc1-44aa-4076-8b59-a5d39246d5b0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ983804(v=EXCHG.150)
ms:contentKeyID: 52061252
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Свойства сообщений, индексированные службой поиска Exchange

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-17_

Служба поиска Exchange индексирует различные свойства объектов, включая отправителя, получателей, текст сообщения и почтовые вложения.

## Свойства, индексируемые службой поиска Exchange

В следующей таблице представлен список свойств, индексируемых службой поиска Exchange.


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
<th>Свойство</th>
<th>Тип</th>
<th>Поддержка запросов</th>
<th>Поддержка поиска</th>
<th>Поддержка извлечения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Account</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Assistantname</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Attachment</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Attachmentfilenames</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Attachmentmetaproperties</p></td>
<td><p>Строка</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Attachmentcount</p></td>
<td><p>Целое число</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>СК</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Текст сообщения</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Businessaddress</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Businessmainphone</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Businessphonenumber</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Carphonenumber</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Category</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Копия</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Companyname</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Compositeitemid</p></td>
<td><p>Строка</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Conversationid</p></td>
<td><p>Целое число</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Conversationtopic</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Departmentname</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>DisplayName</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Displaynameprefix</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Documentid</p></td>
<td><p>Целое число</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>EmailAddress</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Emaildisplayname</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Emailoriginaldisplayname</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Errorcode</p></td>
<td><p>Целое число</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Fileas</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>FirstName</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Folderid</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>От</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Homeaddress</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>HomePhone</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Importance</p></td>
<td><p>Целое число</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Ispartiallyprocessed</p></td>
<td><p>Логическое</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Ispermanentfailure</p></td>
<td><p>Логическое</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Itemclass</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Kind</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Lastattempttime</p></td>
<td><p>Дата и время</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>LastName</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Mailboxguid</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Руководитель</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Meetinglocation</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Middlename</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Mobilephonenumber</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Nickname</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Officelocation</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Otheraddress</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Participants</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Primarytelephonenumber</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Received</p></td>
<td><p>Дата и время</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Receivedby</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Receivedrepresenting</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Получатели</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Sent</p></td>
<td><p>Дата и время</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Sharinginfo</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Size</p></td>
<td><p>Целое число</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Тема</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Tasktitle</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Должность</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Кому</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Umaudionotes</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Watermark</p></td>
<td><p>Целое число</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Yomicompanyname</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Yomifirstname</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Yomilastname</p></td>
<td><p>Строка</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
</tr>
</tbody>
</table>


**Примечания об индексированных свойствах**.

  - **Запрашиваемые свойства** могут использоваться в запросах AQS синтаксис клиентами поиска, такими как Outlook Web App в парах `property:value`, например `from:bsuneja@cotoso.com`. Часть запрашиваемых свойств, перечисленных в предыдущей таблице, также можно использовать в запросах поиска для обнаружения электронных данных на месте. Список этих свойств см. в разделе [Свойства сообщений и поисковые операторы для обнаружения электронных данных на месте](message-properties-and-search-operators-for-in-place-ediscovery-exchange-2013-help.md).

  - **Свойства, поддерживающие поиск,** — это свойства, которые невозможно задать в парах `property:value`. Но при поиске по ключевым словам будет возвращено определенное значение, если оно указано в свойстве, поддерживающем поиск. Например, невозможно использовать `body:Contoso` для поиска строки `contoso` только в тексте сообщения. Тем не менее, поиск этой строки возвратит все элементы, в которых этой свойство найдено в каком-либо свойстве, доступном для поиска.

  - **Свойства, поддерживающие извлечение,** например `documenteid` и `ispartiallyprocessed`, возвращаются при каждом поиске.

