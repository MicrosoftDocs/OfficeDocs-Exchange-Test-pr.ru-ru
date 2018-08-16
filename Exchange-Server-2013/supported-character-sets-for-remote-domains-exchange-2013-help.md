---
title: 'Поддерживаемые наборы знаков для удаленных доменов: Exchange 2013 Help'
TOCTitle: Поддерживаемые наборы знаков для удаленных доменов
ms:assetid: 66023a62-1fd3-4019-be2b-4e7147db148a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa998600(v=EXCHG.150)
ms:contentKeyID: 52059189
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Поддерживаемые наборы знаков для удаленных доменов

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Для сообщений, отправленных в удаленные домены, можно указать следующие наборы знаков.

  - В Центре администрирования Exchange (EAC) на странице **Удаленный домен** выберите имя в раскрывающихся списках **Набор знаков MIME** и **Набор знаков не-MIME**.

  - В командной консоли используйте значение в столбце "Имя" следующей таблицы для параметра *CharacterSet* или *NonMimeCharacterSet* в командлете [Set-RemoteDomain](https://technet.microsoft.com/ru-ru/library/aa997857\(v=exchg.150\)).

### Поддерживаемые наборы символов для конфигурации удаленного домена

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>big5</p></td>
<td><p>Китайский традиционный (Big5)</p></td>
</tr>
<tr class="even">
<td><p>DIN_66003</p></td>
<td><p>Немецкий (IA5)</p></td>
</tr>
<tr class="odd">
<td><p>euc-jp</p></td>
<td><p>Японский (EUC)</p></td>
</tr>
<tr class="even">
<td><p>euc-kr</p></td>
<td><p>Корейский (EUC)</p></td>
</tr>
<tr class="odd">
<td><p>GB18030</p></td>
<td><p>Китайский упрощенный (GB18030)</p></td>
</tr>
<tr class="even">
<td><p>gb2312</p></td>
<td><p>Китайский упрощенный (GB2312)</p></td>
</tr>
<tr class="odd">
<td><p>hz-gb-2312</p></td>
<td><p>Китайский упрощенный (HZ)</p></td>
</tr>
<tr class="even">
<td><p>iso-2022-jp</p></td>
<td><p>Японский (JIS)</p></td>
</tr>
<tr class="odd">
<td><p>iso-2022-kr</p></td>
<td><p>Корейский (ISO)</p></td>
</tr>
<tr class="even">
<td><p>iso-8859-1</p></td>
<td><p>Западноевропейский (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>iso-8859-2</p></td>
<td><p>Центральноевропейский (ISO)</p></td>
</tr>
<tr class="even">
<td><p>iso-8859-3</p></td>
<td><p>Латинский 3 (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>iso-8859-4</p></td>
<td><p>Балтийский (ISO)</p></td>
</tr>
<tr class="even">
<td><p>iso-8859-5</p></td>
<td><p>Кириллица (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>iso-8859-6</p></td>
<td><p>Арабский (ISO)</p></td>
</tr>
<tr class="even">
<td><p>iso-8859-7</p></td>
<td><p>Греческий (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>iso-8859-8</p></td>
<td><p>Иврит (ISO)</p></td>
</tr>
<tr class="even">
<td><p>iso-8859-9</p></td>
<td><p>Турецкий (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>iso-8859-13</p></td>
<td><p>Эстонский (ISO)</p></td>
</tr>
<tr class="even">
<td><p>iso-8859-15</p></td>
<td><p>Латинский 9 (ISO)</p></td>
</tr>
<tr class="odd">
<td><p>koi8-r</p></td>
<td><p>Кириллица (KOI8-R)</p></td>
</tr>
<tr class="even">
<td><p>koi8-u</p></td>
<td><p>Кириллица (KOI8-U)</p></td>
</tr>
<tr class="odd">
<td><p>ks_c_5601-1987</p></td>
<td><p>Корейский (Windows)</p></td>
</tr>
<tr class="even">
<td><p>NS_4551-1</p></td>
<td><p>Норвежский (IA5)</p></td>
</tr>
<tr class="odd">
<td><p>SEN_850200_B</p></td>
<td><p>Шведский (IA5)</p></td>
</tr>
<tr class="even">
<td><p>shift_jis</p></td>
<td><p>Японский (Shift-JIS)</p></td>
</tr>
<tr class="odd">
<td><p>utf-8</p></td>
<td><p>Юникод (UTF-8)</p></td>
</tr>
<tr class="even">
<td><p>windows-1250</p></td>
<td><p>Центральноевропейский (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>windows-1251</p></td>
<td><p>Кириллица (Windows)</p></td>
</tr>
<tr class="even">
<td><p>windows-1252</p></td>
<td><p>Западноевропейский (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>windows-1253</p></td>
<td><p>Греческий (Windows)</p></td>
</tr>
<tr class="even">
<td><p>windows-1254</p></td>
<td><p>Турецкий (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>windows-1255</p></td>
<td><p>Иврит (Windows)</p></td>
</tr>
<tr class="even">
<td><p>windows-1256</p></td>
<td><p>Арабский (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>windows-1257</p></td>
<td><p>Балтийский (Windows)</p></td>
</tr>
<tr class="even">
<td><p>windows-1258</p></td>
<td><p>Вьетнамский (Windows)</p></td>
</tr>
<tr class="odd">
<td><p>windows-874</p></td>
<td><p>Тайский (Windows)</p></td>
</tr>
</tbody>
</table>

