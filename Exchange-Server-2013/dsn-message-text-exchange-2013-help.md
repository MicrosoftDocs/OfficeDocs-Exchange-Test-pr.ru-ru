---
title: 'Текст сообщения DSN: Exchange 2013 Help'
TOCTitle: Текст сообщения DSN
ms:assetid: eae4a050-5ecb-4c87-b377-74edb93a5995
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb125135(v=EXCHG.150)
ms:contentKeyID: 50489419
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Текст сообщения DSN

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Вы можете включить текст в пользовательское уведомление о состоянии доставки (DSN) в Microsoft Exchange Server 2013, и вы можете форматировать этот текст в HTML.

В сообщение можно добавлять любую информацию, которую должен прочитать получатель DSN-сообщения. Например, можно вставить подробное описание DSN, контактную информацию службы поддержки и ссылку на веб-сайт подразделения поддержки. Каждое DSN-сообщение может содержать не более 512 символов.

Поскольку DSN-сообщения могут отображаться в виде HTML, в текст DSN можно вставить теги форматирования HTML. Например, если требуется сделать шрифт некоторого текста в DSN-сообщении полужирным, заключите этот текст в теги HTML \<B\> и \</B\>. В следующей таблице приведены некоторые примеры допустимых тегов HTML, которые можно использовать в тексте сообщений уведомления о доставке.

### Допустимые теги HTML, которые можно применять в сообщениях уведомлений о доставке

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Тег HTML</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;B&gt;</p></td>
<td><p>Начало полужирного шрифта</p></td>
</tr>
<tr class="even">
<td><p>&lt;/B&gt;</p></td>
<td><p>Конец полужирного шрифта</p></td>
</tr>
<tr class="odd">
<td><p>&lt;A HREF=&quot;url&quot;&gt;</p></td>
<td><p>Начало гиперссылки</p></td>
</tr>
<tr class="even">
<td><p>&lt;/A&gt;</p></td>
<td><p>Конец гиперссылки</p></td>
</tr>
<tr class="odd">
<td><p>&lt;BR&gt;</p></td>
<td><p>Разрыв гиперссылки</p></td>
</tr>
<tr class="even">
<td><p>&lt;EM&gt;</p></td>
<td><p>Начало курсива</p></td>
</tr>
<tr class="odd">
<td><p>&lt;/EM&gt;</p></td>
<td><p>Конец курсивного текста</p></td>
</tr>
<tr class="even">
<td><p>&lt;P&gt;</p></td>
<td><p>Начало абзаца</p></td>
</tr>
<tr class="odd">
<td><p>&lt;/P&gt;</p></td>
<td><p>Конец абзаца</p></td>
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
<td>По умолчанию Exchange отправляет DSN-сообщения в виде HTML, но можно указать, каким отправителям должен отправлять DSN-сообщения в виде HTML: внутренним, внешним отправителям или и тем, и другим. Чтобы задать эти настройки, измените параметр <em>InternalDsnSendHtml</em> и параметр <em>ExternalDsnSendHtml</em> с помощью команды <strong>Set-TransportService</strong>.<br />
Если для параметра <em>InternalDsnSendHtml</em> установлено значение <code>$false</code>, Exchange подавляет теги HTML в DSN-сообщениях, отправляемых внутренним отправителям. Если для параметра <em>ExternalDsnSendHtml</em> установлено значение <code>$false</code>, Exchange подавляет теги HTML в DSN-сообщениях, отправляемых внешним отправителям.</td>
</tr>
</tbody>
</table>


Следующие символы, используемые Exchange в тексте DSN-сообщений, имеют специальное значение:

  - знак «больше» (\>);

  - знак «меньше» (\<);

  - амперсанд (&);

  - кавычки ("")

Эти символы используются для указания начала и конца тегов HTML и начала и конца текста, предназначенного для отправителей. Чтобы эти символы были видны в уведомлениях о доставке, необходимо использовать escape-коды, приведенные в следующей таблице.

Например, чтобы в DSN-сообщении отображался текст `"Please contact the Help Desk at <1234>."`, необходимо ввести `"Please contact the Help Desk at &lt;1234&gt;." `.

### Escape-коды для символов в уведомлениях о доставке

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Управляющий код</th>
<th>Символ</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&amp;lt;</p></td>
<td><p>&lt;</p></td>
</tr>
<tr class="even">
<td><p>&amp;gt;</p></td>
<td><p>&gt;</p></td>
</tr>
<tr class="odd">
<td><p>&amp;quot;</p></td>
<td><p>&quot;</p></td>
</tr>
<tr class="even">
<td><p>&amp;amp;</p></td>
<td><p>&amp;</p></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Чтобы ввести в текст уведомления о доставке тег HTML, содержащий двойные кавычки (&quot;), такой как <code>&lt;A HREF=&quot;url&quot;&gt;</code>, необходимо заключить весь текст уведомления в одинарные кавычки ('). Если текст уведомления о доставке и тег HTML заключить в двойные кавычки, возвращается ошибка.</td>
</tr>
</tbody>
</table>

