---
title: 'Форматы файлов, индексируемые службой поиска Exchange: Exchange 2013 Help'
TOCTitle: Форматы файлов, индексируемые службой поиска Exchange
ms:assetid: e5110ac1-28e1-4554-acc3-85d08c997bc5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee633485(v=EXCHG.150)
ms:contentKeyID: 52061295
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Форматы файлов, индексируемые службой поиска Exchange

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2015-07-21_

В МайкрософтExchange Server 2013 и Exchange Online служба поиска Exchange включает фильтры для индексирования наиболее распространенных типов форматов файлов, которые включаются в сообщения в качестве вложений. Кроме того, можно установить фильтры для индексации дополнительных типов файлов.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В Exchange 2013 можно не устанавливать и регистрировать пакет фильтров Microsoft Office.</td>
</tr>
</tbody>
</table>


При управлении службой поиска Exchange и зависимыми функциями (например, [Обнаружение электронных данных на месте](in-place-ediscovery-exchange-2013-help.md)) или их использовании учитывайте различия между элементами, не включаемыми в поиск, и форматами файлов, которые отключены для индексирования или содержат контент, недоступный для индексирования.

  - **Элементы, не поддерживающие поиск**   Когда подсистема поиска Exchange не может индексировать отдельный тип файлов по любой причине (например, не установлен нужный фильтр), поиск этого типа файлов завершается с ошибкой. Сообщения, которые содержат такие вложения, помечаются как *частично индексированные*. Элементы, не включаемые в поиск, можно извлечь с помощью командлета [Get-FailedContentIndexDocuments](https://technet.microsoft.com/ru-ru/library/dd351154\(v=exchg.150\)). При копировании результатов поиска обнаружения электронных данных на месте в почтовый ящик обнаружения или экспорте результатов в PST-файл вы можете добавить элементы, не поддерживающие поиск. Дополнительные сведения см. в разделе [Элементы, которые не включены в поиск при обнаружении электронных данных Exchange](unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md).

  - **Форматы файлов с содержимым, недоступным для индексирования**. Определенные типы файлов, например Windows Media Video (WMV), не включают содержимое, доступное для индексации, и поэтому не индексируются. Сообщения с вложенными файлами таких типов не возвращаются в качестве элементов, не включаемых в поиск, при поиске для обнаружения электронных данных на месте.

  - **Отключенные форматы файлов**. В локальных организациях администратор может отключить индексирование указанных форматов файлов. Сообщения с вложениями, которые включают данные в отключенном формате, не возвращаются в качестве элементов, не включаемых в поиск.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Хотя вложение в сообщение может не включаться в поиск или формат файла может не индексироваться, тема и текст сообщения, а также другие метаданные могут индексироваться и возвращаться в результатах поиска.</td>
</tr>
</tbody>
</table>


Дополнительные сведения о задачах управления, связанных со службой поиска Exchange в локальных организациях, см. в разделе [Процедуры поиска в службе Exchange](exchange-search-procedures-exchange-2013-help.md).

## Фильтры по умолчанию

В следующей таблице перечислены фильтры поиска по умолчанию, установленные на сервере почтовых ящиков Exchange 2013 и в Exchange Online. Список фильтров по умолчанию можно извлечь с помощью командлета [Get-SearchDocumentFormat](https://technet.microsoft.com/ru-ru/library/jj873755\(v=exchg.150\)).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Фильтр</th>
<th>Расширение файла</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Сообщение электронной почты</p></td>
<td><p>EML</p></td>
</tr>
<tr class="even">
<td><p>Формат GIF</p></td>
<td><p>GIF</p></td>
</tr>
<tr class="odd">
<td><p>JPEG</p></td>
<td><p>.jpeg</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Excel</p></td>
<td><p>XLS, XLT, XLSX, XLSM, XLB, XLC, XLSB</p></td>
</tr>
<tr class="odd">
<td><p>Файл Excel</p></td>
<td><p>odbcexcel</p></td>
</tr>
<tr class="even">
<td><p>Microsoft InfoPath</p></td>
<td><p>INFOPATHML</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Office Binder</p></td>
<td><p>OBT, OBD</p></td>
</tr>
<tr class="even">
<td><p>Microsoft PowerPoint</p></td>
<td><p>PPTX, PPTM, PPT, PPSX, PPSM, PPS, PPAM, POTM, POT, POTX</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Publisher</p></td>
<td><p>PUB</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Word</p></td>
<td><p>DOC, DOCM, DOTX, DOTM, DOT, DOCX</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft XPS</p></td>
<td><p>XPS</p></td>
</tr>
<tr class="even">
<td><p>OneNote</p></td>
<td><p>ONE</p></td>
</tr>
<tr class="odd">
<td><p>Презентация OpenDocument</p></td>
<td><p>ODP</p></td>
</tr>
<tr class="even">
<td><p>Электронная таблица OpenDocument</p></td>
<td><p>ODS</p></td>
</tr>
<tr class="odd">
<td><p>Текстовый файл OpenDocument</p></td>
<td><p>ODT</p></td>
</tr>
<tr class="even">
<td><p>Элемент Outlook</p></td>
<td><p>MSG</p></td>
</tr>
<tr class="odd">
<td><p>Формат PDF</p></td>
<td><p>PDF</p></td>
</tr>
<tr class="even">
<td><p>Формат RTF</p></td>
<td><p>RTF</p></td>
</tr>
<tr class="odd">
<td><p>Text</p></td>
<td><p>TXT</p></td>
</tr>
<tr class="even">
<td><p>vCalendar</p></td>
<td><p>VCS</p></td>
</tr>
<tr class="odd">
<td><p>vCard</p></td>
<td><p>VCF</p></td>
</tr>
<tr class="even">
<td><p>Visio</p></td>
<td><p>VDW, VSD, VSS, VST, VSX, VTX, VSSX, VSSM, VSDM, VSTX, VSTM, VDX</p></td>
</tr>
<tr class="odd">
<td><p>Веб-архив</p></td>
<td><p>MHTML</p></td>
</tr>
<tr class="even">
<td><p>Веб-страница</p></td>
<td><p>HTML</p></td>
</tr>
<tr class="odd">
<td><p>XML-документ</p></td>
<td><p>XML</p></td>
</tr>
<tr class="even">
<td><p>ZIP-архив</p></td>
<td><p>ZIP</p></td>
</tr>
</tbody>
</table>


## Отключенные форматы файлов

В следующей таблице перечислены фильтры поиска, отключенные по умолчанию на сервере почтовых ящиков Exchange 2013 и в Exchange Online. В Exchange 2013 администраторы могут выключать и включать поддерживаемые форматы файлов для индексирования с помощью командлета [Set-SearchDocumentFormat](https://technet.microsoft.com/ru-ru/library/jj873756\(v=exchg.150\)). Этот командлет недоступен в Exchange Online.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Фильтр</th>
<th>Расширение файла</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AVI</p></td>
<td><p>AVI</p></td>
</tr>
<tr class="even">
<td><p>Точечный рисунок</p></td>
<td><p>.bmp</p></td>
</tr>
<tr class="odd">
<td><p>MP3</p></td>
<td><p>.mp3</p></td>
</tr>
<tr class="even">
<td><p>MPEG</p></td>
<td><p>.mpeg</p></td>
</tr>
<tr class="odd">
<td><p>PNG</p></td>
<td><p>.png</p></td>
</tr>
<tr class="even">
<td><p>Звукозапись Microsoft Windows</p></td>
<td><p>.wav</p></td>
</tr>
</tbody>
</table>

