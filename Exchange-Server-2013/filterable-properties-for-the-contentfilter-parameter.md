---
title: 'Фильтруемые свойства для параметра -ContentFilter: Exchange 2013 Help'
TOCTitle: Фильтруемые свойства для параметра -ContentFilter
ms:assetid: cf504a59-1938-489c-bb48-b27b2ac3234e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff601762(v=EXCHG.150)
ms:contentKeyID: 50556485
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Фильтруемые свойства для параметра -ContentFilter

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-09-10_

В данном разделе приведен список фильтруемых свойств для параметра *ContentFilter*. Параметр *ContentFilter* используется для экспорта сообщений в файл PST, который соответствует фильтру. Параметр *ContentFilter* используется в командлете [New-MailboxExportRequest](https://technet.microsoft.com/ru-ru/library/ff607299\(v=exchg.150\)).

## Фильтруемые свойства

Многие свойства параметра *ContentFilter* допускают ввод подстановочных знаков. При использовании подстановочных знаков применяйте оператор **-like** вместо оператора **-eq**. Оператор **-like** используется для поиска соответствия шаблону в сложных типах, таких как строки, тогда как оператор **-eq** применяется для поиска точных совпадений.

В приведенной ниже таблице содержится список фильтруемых свойств для параметра *ContentFilter*. В данной таблице приведено имя свойства, его описание, допустимые значения и пример синтаксиса. Дополнительные сведения о фильтрах OPATH см. в разделе [Фильтры в командах получателей для командной консоли](https://technet.microsoft.com/ru-ru/library/bb124268\(v=exchg.150\)).


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Свойство</th>
<th>Описание</th>
<th>Значения</th>
<th>Пример синтаксиса</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>All</p></td>
<td><p>Это свойство возвращает все сообщения, у которых в любом из индексированных свойств содержится определенная строка. Например, это свойство можно использовать, когда требуется экспортировать все сообщения, для которых имя Ayla задано в качестве получателя, отправителя или упомянуто в тексте сообщения.</p></td>
<td><p>Строка</p>
<p>Подстановочный знак</p></td>
<td>```powershell-ContentFilter {All -like '*Ayla*'}```</td>
</tr>
<tr class="even">
<td><p>Attachment</p></td>
<td><p>Данное свойство возвращает сообщения, для которых заданная строка входит в состав содержимого вложения или имени файла вложения.</p></td>
<td><p>Строка</p>
<p>Подстановочный знак</p></td>
<td>```powershell-ContentFilter {Attachment -like '*.jpg'}```</td>
</tr>
<tr class="odd">
<td><p>BCC</p></td>
<td><p>Данное свойство возвращает отправленные сообщения, для которых в поле «СК» указан заданный получатель.</p></td>
<td><p>Отображаемое имя</p>
<p>Псевдоним</p>
<p>SMTP-адрес</p>
<p>LegacyDN</p>
<p>Подстановочный знак</p></td>
<td>```powershell-ContentFilter {(BCC -eq 'ayla@contoso.com') -or (BCC -eq 'tony@contoso.com')}```</td>
</tr>
<tr class="even">
<td><p>Body</p></td>
<td><p>Данное свойство возвращает сообщения, в тексте которых указана заданная строка.</p></td>
<td><p>Строка</p>
<p>Подстановочный знак</p></td>
<td>

```powershell
-ContentFilter {Body -like '*prospectus*'}
```

</td>
</tr>
<tr class="odd">
<td><p>Category</p></td>
<td><p>Данное свойство возвращает сообщения, имеющие соответствующую категорию. Категории задаются пользователями или правилами для папки «Входящие».</p></td>
<td><p>Строка</p>
<p>Подстановочный знак</p></td>
<td>

```powershell
-ContentFilter {Category -like '*Blue*'}
```

</td>
</tr>
<tr class="even">
<td><p>CC</p></td>
<td><p>Данное свойство возвращает отправленные сообщения, для которых в поле «Копия» указан заданный получатель.</p></td>
<td><p>Краткое имя</p>
<p>Псевдоним</p>
<p>SMTP-адрес</p>
<p>LegacyDN</p>
<p>Подстановочный знак</p></td>
<td>

```powershell
-ContentFilter {(CC -eq 'ayla@contoso.com') -or (CC -eq 'tony@contoso.com')}
```

</td>
</tr>
<tr class="odd">
<td><p>Expires</p></td>
<td><p>Данное свойство возвращает сообщения с заданной отметкой времени истечения срока.</p></td>
<td><p>Отметка даты и времени</p></td>
<td>

```powershell
-ContentFilter {Expires -lt '01/01/2013'}
```

</td>
</tr>
<tr class="even">
<td><p>HasAttachment</p></td>
<td><p>Данное свойство возвращает сообщения, имеющие или не имеющие вложения.</p></td>
<td><p>Логическое</p>
<p><code>$true</code> или <code>$false</code></p></td>
<td>

```powershell
-ContentFilter {HasAttachment -eq $true}
```

</td>
</tr>
<tr class="odd">
<td><p>Importance</p></td>
<td><p>Данное свойство возвращает сообщения, имеющие заданный уровень важности.</p></td>
<td><p>0 или Low</p>
<p>1 или Normal</p>
<p>2 или High</p></td>
<td>

```powershell
-ContentFilter {Importance -eq 'high'}
```

```powershell
-ContentFilter {Importance -eq 2}
```

</td>
</tr>
<tr class="even">
<td><p>IsFlagged</p></td>
<td><p>Данное свойство возвращает сообщения, помеченные пользователем или правилом для папки «Входящие».</p></td>
<td><p>Логическое</p>
<p><code>$true</code> или <code>$false</code></p></td>
<td>

```powershell
-ContentFilter {IsFlagged -eq $true}
```

</td>
</tr>
<tr class="odd">
<td><p>IsRead</p></td>
<td><p>Данное свойство возвращает сообщения, прочитанные или не прочитанные пользователем.</p></td>
<td><p>Логическое</p>
<p><code>$true</code> или <code>$false</code></p></td>
<td>

```powershell
-ContentFilter {IsRead -eq $true}
```

</td>
</tr>
<tr class="even">
<td><p>MessageKind</p></td>
<td><p>Данное свойство возвращает сообщения, имеющие заданный тип.</p></td>
<td><p>Calendar</p>
<p>Contact</p>
<p>Doc</p>
<p>Электронная почта</p>
<p>Факс</p>
<p>InstantMessage</p>
<p>Дневник</p>
<p>Note</p>
<p>Post</p>
<p>RSSFeed</p>
<p>Task</p>
<p>Голосовая почта</p></td>
<td>

```powershell
-ContentFilter {MessageKind -eq 'Calendar'}
```

```powershell
-ContentFilter {MessageKind -ne 'Email'}
```

</td>
</tr>
<tr class="odd">
<td><p>MessageLocalee</p></td>
<td><p>Данное свойство возвращает сообщения, имеющие заданный языковой стандарт.</p></td>
<td><p>CultureInfo</p></td>
<td>

```powershell
-ContentFilter {MessageLocale -ne 'en-US'}
```

```powershell
-ContentFilter {MessageLocale -eq 'tr-TR'}
```

</td>
</tr>
<tr class="even">
<td><p>Participants</p></td>
<td><p>Данное свойство возвращает сообщения, для которых в поле «Кому», «СК» или «Копия» указан заданный получатель.</p></td>
<td><p>Краткое имя</p>
<p>Псевдоним</p>
<p>SMTP-адрес</p>
<p>LegacyDN</p>
<p>Подстановочный знак</p></td>
<td>

```powershell
-ContentFilter {(Participants -eq 'ayla@contoso.com') -or (Participants -eq 'tony@contoso.com')}
```

</td>
</tr>
<tr class="odd">
<td><p>PolicyTag</p></td>
<td><p>Данное свойство возвращает сообщения, имеющие тег политики. Хранилище Exchange сохраняет теги политики как идентификаторы GUID. Поэтому такая строка может содержать явное значение GUID, в котором затем ищется значение PR_POLICY_TAG или подстановочная строка.</p>
<p>Если указанное значение не является идентификатором GUID, команда использует сведения Active Directory для разрешения имен в идентификаторы GUID.</p></td>
<td><p>Строка</p>
<p>Подстановочный знак</p></td>
<td>

```powershell
-ContentFilter {PolicyTag -ne '00000000-0000-0000-0000-000000000000'}
```

</td>
</tr>
<tr class="even">
<td><p>Received</p></td>
<td><p>Данное свойство возвращает сообщения, принятые с заданной отметкой времени получения.</p></td>
<td><p>Отметка даты и времени</p></td>
<td>

```powershell
-ContentFilter {Received -lt '01/01/2013 9:00'}
```

```powershell
-ContentFilter {(Received -lt '01/01/2013') -and (Received -gt '01/01/2012')}
```

</td>
</tr>
<tr class="odd">
<td><p>Sender</p></td>
<td><p>Данное свойство возвращает сообщения, полученные от заданного отправителя.</p></td>
<td><p>Краткое имя</p>
<p>Псевдоним</p>
<p>SMTP-адрес</p>
<p>LegacyDN</p>
<p>Подстановочный знак</p></td>
<td>

```powershell
ContentFilter {Sender -eq 'tony'}
```

</td>
</tr>
<tr class="even">
<td><p>Sent</p></td>
<td><p>Данное свойство возвращает сообщения, отправленные с заданной отметкой времени отправки.</p></td>
<td><p>Отметка даты и времени</p></td>
<td>

```powershell
-ContentFilter {Sent -lt '01/01/2013 9:00'}
```

```powershell
-ContentFilter {(Sent -lt '01/01/2013') -and (Sent -gt '01/01/2012')}
```

</td>
</tr>
<tr class="odd">
<td><p>Size</p></td>
<td><p>Данное свойство возвращает сообщения, имеющие заданный размер.</p></td>
<td><p>Б (байт)</p>
<p>КБ (килобайт)</p>
<p>МБ (мегабайт)</p></td>
<td>

```powershell
-ContentFilter {Size -gt '10KB'}
```

</td>
</tr>
<tr class="even">
<td><p>Subject</p></td>
<td><p>Данное свойство возвращает сообщения, в теме которых указана заданная строка.</p></td>
<td><p>Строка</p>
<p>Подстановочный знак</p></td>
<td>

```powershell
-ContentFilter {Subject -like '*meeting*'}
```

</td>
</tr>
<tr class="odd">
<td><p>To</p></td>
<td><p>Данное свойство возвращает отправленные сообщения, для которых в поле «Кому» указан заданный получатель.</p></td>
<td><p>Краткое имя</p>
<p>Псевдоним</p>
<p>SMTP-адрес</p>
<p>LegacyDN</p>
<p>Подстановочный знак</p></td>
<td>

```powershell
-ContentFilter {To -eq 'aylakol'}
```

</td>
</tr>
</tbody>
</table>

