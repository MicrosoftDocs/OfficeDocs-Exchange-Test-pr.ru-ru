---
title: 'Что позволяют искать типы конфиденциальной информации в Exchange: Exchange 2013 Help'
TOCTitle: Что позволяют искать типы конфиденциальной информации
ms:assetid: 98b81f9c-87bb-4905-8e53-04621c3ae74d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ150541(v=EXCHG.150)
ms:contentKeyID: 50487251
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Что позволяют искать типы конфиденциальной информации в Exchange

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2018-05-03_

Функция защиты от потери данных в Exchange поддерживает 80 типов конфиденциальной информации, которые вы можете использовать в своих политиках защиты от потери данных. В этой статье перечислены все эти типы. Кроме того, в статье рассказывается, что именно ищет политика защиты от потери данных, чтобы обнаружить данные каждого типа. Тип конфиденциальной информации определяется шаблоном, который можно идентифицировать с помощью регулярного выражения или функции. Для идентификации типов конфиденциальной информации можно также использовать подкрепляющие свидетельства, например ключевые слова и контрольные суммы. В процессе оценки также используются показатели вероятности и близости.

## Код банка ABA


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>9 цифр в виде форматированного или неформатированного шаблона.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>С форматированием</p>
<ul>
<li><p>четыре цифры, начиная с 0, 1, 2, 3, 6, 7 или 8;</p></li>
<li><p>дефис;</p></li>
<li><p>Четыре цифры</p></li>
<li><p>дефис;</p></li>
<li><p>Одна цифра</p></li>
</ul>
<p>Без форматирования</p>
<ul>
<li><p>9 последовательных цифр, начиная с 0, 1, 2, 3, 6, 7 или 8.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_aba_routing</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_ABA_Routing</code>.</p></li>
</ul>
<pre><code>&lt;!-- ABA Routing Number --&gt;
&lt;Entity id=&quot;cb353f78-2b72-4c3c-8827-92ebe4f69fdf&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_aba_routing&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_ABA_Routing&quot; /&gt;
      &lt;/Pattern&gt;
 &lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-1"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_ABA_Routing</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>aba</p>
<p>aba#</p>
<p>aba routing #</p>
<p>aba routing number</p>
<p>aba#</p>
<p>abarouting#</p>
<p>aba number</p>
<p>abaroutingnumber</p>
<p>american bank association routing #</p>
<p>american bank association routing number</p>
<p>americanbankassociationrouting#</p>
<p>americanbankassociationroutingnumber</p>
<p>bank routing number</p>
<p>bankrouting#</p>
<p>bankroutingnumber</p>
<p>routing transit number</p>
<p>RTN</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер внутреннего удостоверения личности для Аргентины (DNI)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Восемь цифр, разделенных точками.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Восемь цифр:</p>
<ul>
<li><p>Две цифры</p></li>
<li><p>точка;</p></li>
<li><p>Три цифры</p></li>
<li><p>точка;</p></li>
<li><p>Три цифры</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_argentina_national_id</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_argentina_national_id</code>.</p></li>
</ul>
<pre><code>&lt;!-- Argentina National Identity (DNI) Number --&gt;
&lt;Entity id=&quot;eefbb00e-8282-433c-8620-8f1da3bffdb2&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
   &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
      &lt;IdMatch idRef=&quot;Regex_argentina_national_id&quot;/&gt;
      &lt;Match idRef=&quot;Keyword_argentina_national_id&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-3"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_argentina_national_id</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Argentina National Identity number</p>
<p>Identity</p>
<p>Identification National Identity Card</p>
<p>DNI</p>
<p>NIC National Registry of Persons</p>
<p>Documento Nacional de Identidad</p>
<p>Registro Nacional de las Personas</p>
<p>Identidad</p>
<p>Identificación</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер банковского счета для Австралии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>6–10 цифр с номером филиала банка в штате или без него.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Номер счета состоит из 6–10 цифр.</p>
<p>Номер филиала государственного банка Австралии</p>
<ul>
<li><p>Три цифры</p></li>
<li><p>дефис;</p></li>
<li><p>Три цифры</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_australia_bank_account_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_australia_bank_account_number</code>;</p></li>
<li><p>регулярное выражение <code>Regex_australia_bank_account_number_bsb</code> находит содержимое, которое соответствует шаблону.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_australia_bank_account_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_australia_bank_account_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Australia Bank Account Number --&gt;
&lt;Entity id=&quot;74a54de9-2a30-4aa0-a8aa-3d9327fc07c7&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_australia_bank_account_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_australia_bank_account_number&quot; /&gt;
        &lt;Match idRef=&quot;Regex_australia_bank_account_number_bsb&quot; /&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_australia_bank_account_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_australia_bank_account_number&quot; /&gt;
  &lt;/Pattern&gt;
 &lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-5"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_australia_bank_account_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>swift bank code</p>
<p>correspondent bank</p>
<p>base currency</p>
<p>usa account</p>
<p>holder address</p>
<p>bank address</p>
<p>information account</p>
<p>fund transfers</p>
<p>bank charges</p>
<p>bank details</p>
<p>banking information</p>
<p>full names</p>
<p>iaea</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер водительского удостоверения для Австралии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Девять букв и цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Девять букв и цифр:</p>
<ul>
<li><p>две цифры или буквы (без учета регистра);</p></li>
<li><p>Две цифры</p></li>
<li><p>пять цифр или букв (без учета регистра).</p></li>
<li><p>ИЛИ</p></li>
<li><p>1–2 дополнительные буквы (без учета регистра);</p></li>
<li><p>4–9 цифр.</p></li>
<li><p>ИЛИ</p></li>
<li><p>девять цифр или букв (без учета регистра).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_australia_drivers_license_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_australia_drivers_license_number</code>;</p></li>
<li><p>ни одно ключевое слово из <code>Keyword_australia_drivers_license_number_exclusions</code> не находится.</p></li>
</ul>
<pre><code>&lt;!-- Australia Drivers License Number --&gt;
&lt;Entity id=&quot;1cbbc8f5-9216-4392-9eb5-5ac2298d1356&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
   &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_australia_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_australia_drivers_license_number&quot; /&gt;
        &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
          &lt;Match idRef=&quot;Keyword_australia_drivers_license_number_exclusions&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-7"> </h3>
<div>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_australia_drivers_license_number</p></th>
<th><p>Keyword_australia_drivers_license_number_exclusions</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>international driving permits</p>
<p>australian automobile association</p>
<p>sydney nsw</p>
<p>international driving permit</p>
<p>DriverLicence</p>
<p>DriverLicences</p>
<p>Driver Lic</p>
<p>Driver Licence</p>
<p>Driver Licences</p>
<p>DriversLic</p>
<p>DriversLicence</p>
<p>DriversLicences</p>
<p>Drivers Lic</p>
<p>Drivers Lics</p>
<p>Drivers Licence</p>
<p>Drivers Licences</p>
<p>Driver' Lic</p>
<p>Driver' Lics</p>
<p>Driver' Licence</p>
<p>Driver' Licences</p>
<p>Driver' Lic</p>
<p>Driver' Lics</p>
<p>Driver' Licence</p>
<p>Driver' Licences</p>
<p>Driver'sLic</p>
<p>Driver'sLics</p>
<p>Driver'sLicence</p>
<p>Driver'sLicences</p>
<p>Driver's Lic</p>
<p>Driver's Lics</p>
<p>Driver's Licence</p>
<p>Driver's Licences</p>
<p>DriverLic#</p>
<p>DriverLics#</p>
<p>DriverLicence#</p>
<p>DriverLicences#</p>
<p>Driver Lic#</p>
<p>Driver Lics#</p>
<p>Driver Licence#</p>
<p>Driver Licences#</p>
<p>DriversLic#</p>
<p>DriversLics#</p>
<p>DriversLicence#</p>
<p>DriversLicences#</p>
<p>Drivers Lic#</p>
<p>Drivers Lics#</p>
<p>Drivers Licence#</p>
<p>Drivers Licences#</p>
<p>Driver' Lic#</p>
<p>Driver' Lics#</p>
<p>Driver' Licence#</p>
<p>Driver' Licences#</p>
<p>Driver' Lic#</p>
<p>Driver' Lics#</p>
<p>Driver' Licence#</p>
<p>Driver' Licences#</p>
<p>Driver'sLic#</p>
<p>Driver'sLics#</p>
<p>Driver'sLicence#</p>
<p>Driver'sLicences#</p>
<p>Driver's Lic#</p>
<p>Driver's Lics#</p>
<p>Driver's Licence#</p>
<p>Driver's Licences#</p></td>
<td><p>aaa</p>
<p>DriverLicense</p>
<p>DriverLicenses</p>
<p>Driver License</p>
<p>Driver Licenses</p>
<p>DriversLicense</p>
<p>DriversLicenses</p>
<p>Drivers License</p>
<p>Drivers Licenses</p>
<p>Driver' License</p>
<p>Driver' Licenses</p>
<p>Driver' License</p>
<p>Driver' Licenses</p>
<p>Driver'sLicense</p>
<p>Driver'sLicenses</p>
<p>Driver's License</p>
<p>Driver's Licenses</p>
<p>DriverLicense#</p>
<p>DriverLicenses#</p>
<p>Driver License#</p>
<p>Driver Licenses#</p>
<p>DriversLicense#</p>
<p>DriversLicenses#</p>
<p>Drivers License#</p>
<p>Drivers Licenses#</p>
<p>Driver' License#</p>
<p>Driver' Licenses#</p>
<p>Driver' License#</p>
<p>Driver' Licenses#</p>
<p>Driver'sLicense#</p>
<p>Driver'sLicenses#</p>
<p>Driver's License#</p>
<p>Driver's Licenses#</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер карты медицинского страхования для Австралии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10–11 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10–11 цифр.</p>
<ul>
<li><p>Первая цифра находится в диапазоне 2–6.</p></li>
<li><p>Девятая цифра — проверочная.</p></li>
<li><p>Десятая цифра — цифра серии.</p></li>
<li><p>Одиннадцатая цифра (необязательно) — индивидуальный номер.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 95 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_australian_medical_account_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_Australia_Medical_Account_Number</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_australian_medical_account_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>  &lt;!-- Australia Medical Account Number --&gt;
&lt;Entity id=&quot;104a99a0-3d3b-4542-a40d-ab0b9e1efe63&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;95&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_australian_medical_account_number&quot;/&gt;
     &lt;Any minMatches=&quot;1&quot;&gt;
     &lt;Match idRef=&quot;Keyword_Australia_Medical_Account_Number&quot;/&gt;
     &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_australian_medical_account_number&quot;/&gt;
     &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
  &lt;Match idRef=&quot;Keyword_Australia_Medical_Account_Number&quot;/&gt;
     &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-9"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_Australia_Medical_Account_Number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>bank account details</p>
<p>medicare payments</p>
<p>mortgage account</p>
<p>bank payments</p>
<p>information branch</p>
<p>credit card loan</p>
<p>department of human services</p>
<p>local service</p>
<p>medicare</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер паспорта гражданина Австралии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Буква, за которой следуют семь цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Буква (без учета регистра), за которой следуют семь цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_australia_passport_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_passport</code> или <code>Keyword_australia_passport_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Australia Passport Number --&gt;
&lt;Entity id=&quot;29869db6-602d-4853-ab93-3484f905df50&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_australia_passport_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_passport&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_australia_passport_number&quot; /&gt;
        &lt;/Any&gt;
   &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-11"> </h3>
<div>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_passport</p></th>
<th><p>Keyword_australia_passport_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Passport Number</p>
<p>Passport No</p>
<p>Passport#</p>
<p>Passport#</p>
<p>PassportID</p>
<p>Passportno</p>
<p>passportnumber</p>
<p>パスポート</p>
<p>パスポート番号</p>
<p>パスポートのNum</p>
<p>パスポート＃</p>
<p>Numéro de passeport</p>
<p>Passeport n °</p>
<p>Passeport Non</p>
<p>Passeport#</p>
<p>Passeport#</p>
<p>PasseportNon</p>
<p>Passeportn °</p></td>
<td><p>passport</p>
<p>passport details</p>
<p>immigration and citizenship</p>
<p>commonwealth of australia</p>
<p>department of immigration</p>
<p>residential address</p>
<p>department of immigration and citizenship</p>
<p>visa</p>
<p>national identity card</p>
<p>passport number</p>
<p>travel document</p>
<p>issuing authority</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер налогоплательщика для Австралии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>8–9 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>8–9 цифр, которые обычно разделены пробелами указанным ниже образом.</p>
<ul>
<li><p>Три цифры</p></li>
<li><p>Необязательный пробел</p></li>
<li><p>Три цифры</p></li>
<li><p>Необязательный пробел</p></li>
<li><p>2–3 цифры, причем последняя цифра — контрольная</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 95 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_australian_tax_file_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_Australia_Tax_File_Number</code>;</p></li>
<li><p>ни одно ключевое слово из <code>Keyword_number_exclusions</code> не найдено;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_australian_tax_file_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>ни одно ключевое слово из <code>Keyword_Australia_Tax_File_Number</code> или <code>Keyword_number_exclusions</code> не найдено;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>    &lt;!-- Australia Tax File Number --&gt;
&lt;Entity id=&quot;e29bc95f-ff70-4a37-aa01-04d17360a4c5&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;95&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_australian_tax_file_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_Australia_Tax_File_Number&quot; /&gt;
        &lt;/Any&gt;
        &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
          &lt;Match idRef=&quot;Keyword_number_exclusions&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_australian_tax_file_number&quot; /&gt;
        &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
          &lt;Match idRef=&quot;Keyword_Australia_Tax_File_Number&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_number_exclusions&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-13"> </h3>
<div>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_Australia_Tax_File_Number</p></th>
<th><p>Keyword_number_exclusions</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>australian business number</p>
<p>marginal tax rate</p>
<p>medicare levy</p>
<p>portfolio number</p>
<p>service veterans</p>
<p>withholding tax</p>
<p>individual tax return</p>
<p>tax file number</p></td>
<td><p>00000000</p>
<p>11111111</p>
<p>22222222</p>
<p>33333333</p>
<p>44444444</p>
<p>55555555</p>
<p>66666666</p>
<p>77777777</p>
<p>88888888</p>
<p>99999999</p>
<p>000000000</p>
<p>111111111</p>
<p>222222222</p>
<p>333333333</p>
<p>444444444</p>
<p>555555555</p>
<p>666666666</p>
<p>777777777</p>
<p>888888888</p>
<p>999999999</p>
<p>0000000000</p>
<p>1111111111</p>
<p>2222222222</p>
<p>3333333333</p>
<p>4444444444</p>
<p>5555555555</p>
<p>6666666666</p>
<p>7777777777</p>
<p>8888888888</p>
<p>9999999999</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер национального документа для Бельгии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>11 цифр, а также разделители.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>11 цифр, а также разделители:</p>
<ul>
<li><p>шесть цифр и две точки в формате ГГ.ММ.ДД для даты рождения;</p></li>
<li><p>дефис;</p></li>
<li><p>три последовательные цифры (нечетные для мужчин, четные для женщин);</p></li>
<li><p>точка;</p></li>
<li><p>две проверочные цифры.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_belgium_national_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_belgium_national_number</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Belgium National Number --&gt;
  &lt;Entity id=&quot;fb969c9e-0fd1-4b18-8091-a2123c5e6a54&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
   &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_belgium_national_number&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_belgium_national_number&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-15"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_belgium_national_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Identity</p>
<p>Registration</p>
<p>Identification</p>
<p>ID</p>
<p>Identiteitskaart</p>
<p>Registratie nummer</p>
<p>Identificatie nummer</p>
<p>Identiteit</p>
<p>Registratie</p>
<p>Identificatie</p>
<p>Carte d’identité</p>
<p>numéro d'immatriculation</p>
<p>numéro d'identification</p>
<p>identité</p>
<p>inscription</p>
<p>Identifikation</p>
<p>Identifizierung</p>
<p>Identifikationsnummer</p>
<p>Personalausweis</p>
<p>Registrierung</p>
<p>Registrationsnummer</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер юридического лица для Бразилии (CNPJ)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>14 цифр, которые включают регистрационный номер, номер филиала и проверочные цифры, а также разделители.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>14 цифр, а также разделители:</p>
<ul>
<li><p>Две цифры</p></li>
<li><p>точка;</p></li>
<li><p>Три цифры</p></li>
<li><p>точка;</p></li>
<li><p>три цифры (эти первые восемь цифр — регистрационный номер);</p></li>
<li><p>косая черта;</p></li>
<li><p>номер отделения из четырех цифр;</p></li>
<li><p>дефис;</p></li>
<li><p>две проверочные цифры.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_brazil_cnpj</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_brazil_cnpj</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_brazil_cnpj</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Brazil Legal Entity Number (CNPJ) --&gt;
&lt;Entity id=&quot;9b58b5cd-5e90-4df6-b34f-1ebcc88ceae4&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
   &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_brazil_cnpj&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_brazil_cnpj&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_brazil_cnpj&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-17"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_brazil_cnpj</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNPJ</p>
<p>CNPJ/MF</p>
<p>CNPJ-MF</p>
<p>National Registry of Legal Entities</p>
<p>Taxpayers Registry</p>
<p>Legal entity</p>
<p>Legal entities</p>
<p>Registration Status</p>
<p>Business</p>
<p>Company</p>
<p>CNPJ</p>
<p>Cadastro Nacional da Pessoa Jurídica</p>
<p>Cadastro Geral de Contribuintes</p>
<p>CGC</p>
<p>Pessoa jurídica</p>
<p>Pessoas jurídicas</p>
<p>Situação cadastral</p>
<p>Inscrição</p>
<p>Empresa</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер CPF для Бразилии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>11 цифр, которые включают проверочную цифру и могут быть форматированными или неформатированными.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>С форматированием</p>
<ul>
<li><p>Три цифры</p></li>
<li><p>точка;</p></li>
<li><p>Три цифры</p></li>
<li><p>точка;</p></li>
<li><p>Три цифры</p></li>
<li><p>дефис;</p></li>
<li><p>две проверочные цифры.</p></li>
</ul>
<p>Без форматирования</p>
<ul>
<li><p>11 цифр, где две последние цифры — проверочные.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_brazil_cpf</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_brazil_cpf</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_brazil_cpf</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Brazil CPF Number --&gt;
&lt;Entity id=&quot;78e09124-f2c3-4656-b32a-c1a132cd2711&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_brazil_cpf&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_brazil_cpf&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_brazil_cpf&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-19"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_brazil_cpf</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPF</p>
<p>Identification</p>
<p>Registration</p>
<p>Revenue</p>
<p>Cadastro de Pessoas Físicas</p>
<p>Imposto</p>
<p>Identificação</p>
<p>Inscrição</p>
<p>Receita</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер внутреннего удостоверения личности для Бразилии (RG)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Registro Geral (старый формат):</p>
<dl>
<dt><span></span></dt>
<dd><p>девять цифр.</p>
</dd>
</dl>
<p>Registro de Identidade (RIC) (новый формат):</p>
<dl>
<dt><span></span></dt>
<dd><p>11 разрядов</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Registro Geral (старый формат):</p>
<ul>
<li><p>Две цифры</p></li>
<li><p>точка;</p></li>
<li><p>Три цифры</p></li>
<li><p>точка;</p></li>
<li><p>Три цифры</p></li>
<li><p>дефис;</p></li>
<li><p>одна цифра — проверочная.</p></li>
</ul>
<p>Registro de Identidade (RIC) (новый формат):</p>
<ul>
<li><p>10 цифр;</p></li>
<li><p>дефис;</p></li>
<li><p>одна цифра — проверочная.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_brazil_rg</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_brazil_rg</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_brazil_rg</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Brazil National ID Card (RG) --&gt;
&lt;Entity id=&quot;486de900-db70-41b3-a886-abdf25af119c&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_brazil_rg&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_brazil_rg&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_brazil_rg&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-21"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_brazil_rg</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cédula de identidade</p>
<p>identity card</p>
<p>national id</p>
<p>número de rregistro</p>
<p>registro de Iidentidade</p>
<p>registro geral</p>
<p>RG (ключевое слово с учетом регистра)</p>
<p>RIC (ключевое слово с учетом регистра)</p>
<p></p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер банковского счета для Канады


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Семь или двенадцать цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Номер банковского счета для Канады — семь или двенадцать цифр.</p>
<p>Транзитный номер банковского счета в Канаде имеет указанный ниже формат.</p>
<ul>
<li><p>Пять цифр</p></li>
<li><p>дефис;</p></li>
<li><p>Три цифры</p>
<p>ИЛИ</p></li>
<li><p>ноль &quot;0&quot;;</p>
<p>восемь цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_canada_bank_account_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_canada_bank_account_number</code>;</p></li>
<li><p>регулярное выражение <code>Regex_canada_bank_account_transit_number</code> находит содержимое, которое соответствует шаблону.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_canada_bank_account_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_canada_bank_account_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Canada Bank Account Number --&gt;
&lt;Entity id=&quot;552e814c-cb50-4d94-bbaa-bb1d1ffb34de&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_canada_bank_account_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_bank_account_number&quot; /&gt;
        &lt;Match idRef=&quot;Regex_canada_bank_account_transit_number&quot; /&gt;
   &lt;/Pattern&gt;
   &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_canada_bank_account_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_bank_account_number&quot; /&gt;
   &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-23"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_canada_bank_account_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>canada savings bonds</p>
<p>canada revenue agency</p>
<p>canadian financial institution</p>
<p>direct deposit form</p>
<p>canadian citizen</p>
<p>legal representative</p>
<p>notary public</p>
<p>commissioner for oaths</p>
<p>child care benefit</p>
<p>universal child care</p>
<p>canada child tax benefit</p>
<p>income tax benefit</p>
<p>harmonized sales tax</p>
<p>social insurance number</p>
<p>income tax refund</p>
<p>child tax benefit</p>
<p>territorial payments</p>
<p>institution number</p>
<p>deposit request</p>
<p>banking information</p>
<p>direct deposit</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер водительского удостоверения для Канады


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Зависит от провинции.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Различные шаблоны, соответствующие провинциям Альберта, Британская Колумбия, Манитоба, Нью-Брансуик, Ньюфаундленд и Лабрадор, Новая Шотландия, Онтарио, Остров Принца Эдуарда, Квебек и Саскачеван.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_[province_name]_drivers_license_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_[province_name]_drivers_license_name</code>;</p></li>
<li><p>находится ключевое слово из <code>Keyword_canada_drivers_license</code>.</p></li>
</ul>
<pre><code>&lt;!-- Canada Driver&#39;s License Number --&gt;
    &lt;Entity id=&quot;37186abb-8e48-4800-ad3c-e3d1610b3db0&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_alberta_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_alberta_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_british_columbia_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_british_columbia_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_manitoba_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_manitoba_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_new_brunswick_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_new_brunswick_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_newfoundland_labrador_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_newfoundland_labrador_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_nova_scotia_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_nova_scotia_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_ontario_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_ontario_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_prince_edward_island_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_prince_edward_island_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_quebec_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_quebec_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_saskatchewan_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_saskatchewan_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_canada_drivers_license&quot; /&gt;
      &lt;/Pattern&gt;
    &lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-25"> </h3>
<div>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_[province_name]_drivers_license_name</p></th>
<th><p>Keyword_canada_drivers_license</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Аббревиатура провинции, например AB.</p>
<p>Название провинции, например Альберта.</p></td>
<td><p>DL</p>
<p>DLS</p>
<p>CDL</p>
<p>CDLS</p>
<p>DriverLic</p>
<p>DriverLics</p>
<p>DriverLicense</p>
<p>DriverLicenses</p>
<p>DriverLicence</p>
<p>DriverLicences</p>
<p>Driver Lic</p>
<p>Driver Lics</p>
<p>Driver License</p>
<p>Driver Licenses</p>
<p>Driver Licence</p>
<p>Driver Licences</p>
<p>DriversLic</p>
<p>DriversLics</p>
<p>DriversLicence</p>
<p>DriversLicences</p>
<p>DriversLicense</p>
<p>DriversLicenses</p>
<p>Drivers Lic</p>
<p>Drivers Lics</p>
<p>Drivers License</p>
<p>Drivers Licenses</p>
<p>Drivers Licence</p>
<p>Drivers Licences</p>
<p>Driver' Lic</p>
<p>Driver' Lics</p>
<p>Driver' License</p>
<p>Driver' Licenses</p>
<p>Driver' Licence</p>
<p>Driver' Licences</p>
<p>Driver' Lic</p>
<p>Driver' Lics</p>
<p>Driver' License</p>
<p>Driver' Licenses</p>
<p>Driver' Licence</p>
<p>Driver' Licences</p>
<p>Driver'sLic</p>
<p>Driver'sLics</p>
<p>Driver'sLicense</p>
<p>Driver'sLicenses</p>
<p>Driver'sLicence</p>
<p>Driver'sLicences</p>
<p>Driver's Lic</p>
<p>Driver's Lics</p>
<p>Driver's License</p>
<p>Driver's Licenses</p>
<p>Driver's Licence</p>
<p>Driver's Licences</p>
<p>Permis de Conduire</p>
<p>id</p>
<p>ids</p>
<p>idcard number</p>
<p>idcard numbers</p>
<p>idcard#</p>
<p>idcard #s</p>
<p>idcard card</p>
<p>idcard cards</p>
<p>idcard</p>
<p>identification number</p>
<p>identification numbers</p>
<p>identification #</p>
<p>identification #s</p>
<p>identification card</p>
<p>identification cards</p>
<p>identification</p>
<p>DL#</p>
<p>DLS#</p>
<p>CDL#</p>
<p>CDLS#</p>
<p>DriverLic#</p>
<p>DriverLics#</p>
<p>DriverLicense#</p>
<p>DriverLicenses#</p>
<p>DriverLicence#</p>
<p>DriverLicences#</p>
<p>Driver Lic#</p>
<p>Driver Lics#</p>
<p>Driver License#</p>
<p>Driver Licenses#</p>
<p>Driver License#</p>
<p>Driver Licences#</p>
<p>DriversLic#</p>
<p>DriversLics#</p>
<p>DriversLicense#</p>
<p>DriversLicenses#</p>
<p>DriversLicence#</p>
<p>DriversLicences#</p>
<p>Drivers Lic#</p>
<p>Drivers Lics#</p>
<p>Drivers License#</p>
<p>Drivers Licenses#</p>
<p>Drivers Licence#</p>
<p>Drivers Licences#</p>
<p>Driver' Lic#</p>
<p>Driver' Lics#</p>
<p>Driver' License#</p>
<p>Driver' Licenses#</p>
<p>Driver' Licence#</p>
<p>Driver' Licences#</p>
<p>Driver' Lic#</p>
<p>Driver' Lics#</p>
<p>Driver' License#</p>
<p>Driver' Licenses#</p>
<p>Driver' Licence#</p>
<p>Driver' Licences#</p>
<p>Driver'sLic#</p>
<p>Driver'sLics#</p>
<p>Driver'sLicense#</p>
<p>Driver'sLicenses#</p>
<p>Driver'sLicence#</p>
<p>Driver'sLicences#</p>
<p>Driver's Lic#</p>
<p>Driver's Lics#</p>
<p>Driver's License#</p>
<p>Driver's Licenses#</p>
<p>Driver's Licence#</p>
<p>Driver's Licences#</p>
<p>Permis de Conduire#</p>
<p>id#</p>
<p>ids#</p>
<p>idcard card#</p>
<p>idcard cards#</p>
<p>idcard#</p>
<p>identification card#</p>
<p>identification cards#</p>
<p>identification #</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер службы здравоохранения для Канады


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10 цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_canada_health_service_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_canada_health_service_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Canada Health Service Number --&gt;
&lt;Entity id=&quot;59c0bf39-7fab-482c-af25-00faa4384c94&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_canada_health_service_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_canada_health_service_number&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-27"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_canada_health_service_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>personal health number</p>
<p>patient information</p>
<p>health services</p>
<p>speciality services</p>
<p>automobile accident</p>
<p>patient hospital</p>
<p>psychiatrist</p>
<p>workers compensation</p>
<p>disability</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер паспорта гражданина Канады


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Две прописные буквы, за которыми следуют шесть цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Две прописные буквы, за которыми следуют шесть цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_canada_passport_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_canada_passport_number</code> или <code>Keyword_passport</code>.</p></li>
</ul>
<pre><code> &lt;!-- Canada Passport Number --&gt;
&lt;Entity id=&quot;14d0db8b-498a-43ed-9fca-f6097ae687eb&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_canada_passport_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_canada_passport_number&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_passport&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-29"> </h3>
<div>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_canada_passport_number</p></th>
<th><p>Keyword_passport</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>canadian citizenship</p>
<p>canadian passport</p>
<p>passport application</p>
<p>passport photos</p>
<p>certified translator</p>
<p>canadian citizens</p>
<p>processing times</p>
<p>renewal application</p></td>
<td><p>Passport Number</p>
<p>Passport No</p>
<p>Passport#</p>
<p>Passport#</p>
<p>PassportID</p>
<p>Passportno</p>
<p>passportnumber</p>
<p>パスポート</p>
<p>パスポート番号</p>
<p>パスポートのNum</p>
<p>パスポート＃</p>
<p>Numéro de passeport</p>
<p>Passeport n °</p>
<p>Passeport Non</p>
<p>Passeport#</p>
<p>Passeport#</p>
<p>PasseportNon</p>
<p>Passeportn °</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Персональный идентификационный номер службы здравоохранения для Канады (PHIN)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Девять цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Девять цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_canada_phin</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находятся по меньшей мере два ключевых слова из <code>Keyword_canada_phin</code> или <code>Keyword_canada_provinces</code>.</p></li>
</ul>
<pre><code>&lt;!-- Canada PHIN --&gt;
&lt;Entity id=&quot;722e12ac-c89a-4ec8-a1b7-fea3469f89db&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_canada_phin&quot; /&gt;
        &lt;Any minMatches=&quot;2&quot;&gt;
          &lt;Match idRef=&quot;Keyword_canada_phin&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_canada_provinces&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-31"> </h3>
<div>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_canada_phin</p></th>
<th><p>Keyword_canada_provinces</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>social insurance number</p>
<p>health information act</p>
<p>income tax information</p>
<p>manitoba health</p>
<p>health registration</p>
<p>prescription purchases</p>
<p>benefit eligibility</p>
<p>personal health</p>
<p>power of attorney</p>
<p>registration number</p>
<p>personal health number</p>
<p>practitioner referral</p>
<p>wellness professional</p>
<p>patient referral</p>
<p>health and wellness</p></td>
<td><p>Nunavut</p>
<p>Quebec</p>
<p>Northwest Territories</p>
<p>Ontario</p>
<p>British Columbia</p>
<p>Alberta</p>
<p>Saskatchewan</p>
<p>Manitoba</p>
<p>Yukon</p>
<p>Newfoundland and Labrador</p>
<p>New Brunswick</p>
<p>Nova Scotia</p>
<p>Prince Edward Island</p>
<p>Канада</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер карты социального страхования для Канады


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Девять цифр с необязательными дефисами или пробелами.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>С форматированием</p>
<ul>
<li><p>Три цифры</p></li>
<li><p>дефис или пробел;</p></li>
<li><p>Три цифры</p></li>
<li><p>Дефис или пробел</p></li>
<li><p>Три цифры</p></li>
</ul>
<p>Без форматирования</p>
<ul>
<li><p>Девять цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_canadian_sin</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Выполняются по меньшей мере два из таких условий:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_sin</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_sin_collaborative</code>;</p></li>
<li><p>функция <code>Func_eu_date</code> находит дату в правильном формате.</p></li>
</ul></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_unformatted_canadian_sin</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_sin</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Canada Social Insurance Number --&gt;
&lt;Entity id=&quot;a2f29c85-ecb8-4514-a610-364790c0773e&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_canadian_sin&quot; /&gt;
        &lt;Any minMatches=&quot;2&quot;&gt;
          &lt;Match idRef=&quot;Keyword_sin&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_sin_collaborative&quot; /&gt;
          &lt;Match idRef=&quot;Func_eu_date&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_unformatted_canadian_sin&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_sin&quot; /&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-33"> </h3>
<div>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_sin</p></th>
<th><p>Keyword_sin_collaborative</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>sin</p>
<p>social insurance</p>
<p>numero d'assurance sociale</p>
<p>sins</p>
<p>ssn</p>
<p>ssns</p>
<p>social security</p>
<p>numero d'assurance social</p>
<p>national identification number</p>
<p>national id</p>
<p>sin#</p>
<p>soc ins</p>
<p>social ins</p></td>
<td><p>driver's license</p>
<p>drivers license</p>
<p>driver's licence</p>
<p>drivers licence</p>
<p>DOB</p>
<p>Birthdate</p>
<p>Birthday</p>
<p>Date of Birth</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер удостоверения личности для Чили


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>7–8 цифр, разделители, проверочная цифра или буква.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>7–8 цифр, а также разделители:</p>
<ul>
<li><p>1 или 2 цифры;</p></li>
<li><p>точка;</p></li>
<li><p>Три цифры</p></li>
<li><p>точка;</p></li>
<li><p>три цифры;</p></li>
<li><p>Тире</p></li>
<li><p>одна цифра или буква (без учета регистра) — проверочная.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_chile_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_chile_id_card</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_chile_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Chile Identity Card Number --&gt;
&lt;Entity id=&quot;4e979794-49a0-407e-a0b9-2c536937b925&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_chile_id_card&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_chile_id_card&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_chile_id_card&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-35"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_chile_id_card</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>National Identification Number</p>
<p>Identity card</p>
<p>ID</p>
<p>Identification</p>
<p>Rol Único Nacional</p>
<p>RUN</p>
<p>Rol Único Tributario</p>
<p>RUT</p>
<p>Cédula de Identidad</p>
<p>Número De Identificación Nacional</p>
<p>Tarjeta de identificación</p>
<p>Identificación</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер удостоверения личности жителя Китая (КНР)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>18 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>18 цифр:</p>
<ul>
<li><p>шесть цифр — код адреса;</p></li>
<li><p>восемь цифр в виде ГГГГММДД — дата рождения;</p></li>
<li><p>три цифры — серия карты;</p></li>
<li><p>одна цифра — проверочная.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_china_resident_id</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_china_resident_id</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_china_resident_id</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- China Resident Identity Card (PRC) Number --&gt;
&lt;Entity id=&quot;c92daa86-2d16-4871-901f-816b3f554fc1&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_china_resident_id&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_china_resident_id&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_china_resident_id&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-37"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_china_resident_id</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Resident Identity Card</p>
<p>PRC</p>
<p>National Identification Card</p>
<p>身份证</p>
<p>居民 身份证</p>
<p>居民身份证</p>
<p>鉴定</p>
<p>身分證</p>
<p>居民 身份證</p>
<p>鑑定</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер кредитной карты


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>16 цифр, которые могут иметь формат или неформатированные (dddddddddddddddd) и должно пройти проверку Luhn.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Очень сложный и надежный шаблон, который определяет карты всех основных мировых стандартов, включая Visa, MasterCard, Discover Card, JCB, American Express, подарочные карты и карты Diners Club.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да (рассчитывается по алгоритму Луна).</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_credit_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>Верно одно из условий ниже:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_cc_verification</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_cc_name</code>;</p></li>
<li><p>функция <code>Func_expiration_date</code> находит дату в правильном формате.</p></li>
</ul></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 65 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_credit_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Credit Card Number --&gt;
&lt;Entity id=&quot;50842eb7-edc8-4019-85dd-5a5c1f2bb085&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_credit_card&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_cc_verification&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_cc_name&quot; /&gt;
          &lt;Match idRef=&quot;Func_expiration_date&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;65&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_credit_card&quot; /&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-39"> </h3>
<div>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_cc_verification</p></th>
<th><p>Keyword_cc_name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>card verification</p>
<p>card identification number</p>
<p>cvn</p>
<p>cid</p>
<p>cvc2</p>
<p>cvv2</p>
<p>pin block</p>
<p>security code</p>
<p>security number</p>
<p>security no</p>
<p>issue number</p>
<p>issue no</p>
<p>cryptogramme</p>
<p>numéro de sécurité</p>
<p>numero de securite</p>
<p>kreditkartenprüfnummer</p>
<p>kreditkartenprufnummer</p>
<p>prüfziffer</p>
<p>prufziffer</p>
<p>sicherheits Kode</p>
<p>sicherheitscode</p>
<p>sicherheitsnummer</p>
<p>verfalldatum</p>
<p>codice di verifica</p>
<p>cod. sicurezza</p>
<p>cod sicurezza</p>
<p>n autorizzazione</p>
<p>código</p>
<p>codigo</p>
<p>cod. seg</p>
<p>cod seg</p>
<p>código de segurança</p>
<p>codigo de seguranca</p>
<p>codigo de segurança</p>
<p>código de seguranca</p>
<p>cód. segurança</p>
<p>cod. seguranca cod. segurança</p>
<p>cód. seguranca</p>
<p>cód segurança</p>
<p>cod seguranca cod segurança</p>
<p>cód seguranca</p>
<p>número de verificação</p>
<p>numero de verificacao</p>
<p>ablauf</p>
<p>gültig bis</p>
<p>gültigkeitsdatum</p>
<p>gultig bis</p>
<p>gultigkeitsdatum</p>
<p>scadenza</p>
<p>data scad</p>
<p>fecha de expiracion</p>
<p>fecha de venc</p>
<p>vencimiento</p>
<p>válido hasta</p>
<p>valido hasta</p>
<p>vto</p>
<p>data de expiração</p>
<p>data de expiracao</p>
<p>data em que expira</p>
<p>validade</p>
<p>valor</p>
<p>vencimento</p>
<p>Venc</p></td>
<td><p>amex</p>
<p>american express</p>
<p>americanexpress</p>
<p>Visa</p>
<p>mastercard</p>
<p>master card</p>
<p>mc</p>
<p>mastercards</p>
<p>master cards</p>
<p>diner's Club</p>
<p>diners club</p>
<p>dinersclub</p>
<p>discover card</p>
<p>discovercard</p>
<p>discover cards</p>
<p>JCB</p>
<p>japanese card bureau</p>
<p>carte blanche</p>
<p>carteblanche</p>
<p>credit card</p>
<p>cc#</p>
<p>cc#:</p>
<p>expiration date</p>
<p>exp date</p>
<p>expiry date</p>
<p>date d’expiration</p>
<p>date d'exp</p>
<p>date expiration</p>
<p>bank card</p>
<p>bankcard</p>
<p>card number</p>
<p>card num</p>
<p>cardnumber</p>
<p>cardnumbers</p>
<p>card numbers</p>
<p>creditcard</p>
<p>credit cards</p>
<p>creditcards</p>
<p>ccn</p>
<p>card holder</p>
<p>cardholder</p>
<p>card holders</p>
<p>cardholders</p>
<p>check card</p>
<p>checkcard</p>
<p>check cards</p>
<p>checkcards</p>
<p>debit card</p>
<p>debitcard</p>
<p>debit cards</p>
<p>debitcards</p>
<p>atm card</p>
<p>atmcard</p>
<p>atm cards</p>
<p>atmcards</p>
<p>enroute</p>
<p>en route</p>
<p>card type</p>
<p>carte bancaire</p>
<p>carte de crédit</p>
<p>carte de credit</p>
<p>numéro de carte</p>
<p>numero de carte</p>
<p>nº de la carte</p>
<p>nº de carte</p>
<p>kreditkarte</p>
<p>karte</p>
<p>karteninhaber</p>
<p>karteninhabers</p>
<p>kreditkarteninhaber</p>
<p>kreditkarteninstitut</p>
<p>kreditkartentyp</p>
<p>eigentümername</p>
<p>kartennr</p>
<p>kartennummer</p>
<p>kreditkartennummer</p>
<p>kreditkarten-nummer</p>
<p>carta di credito</p>
<p>carta credito</p>
<p>n. carta</p>
<p>n carta</p>
<p>nr. carta</p>
<p>nr carta</p>
<p>numero carta</p>
<p>numero della carta</p>
<p>numero di carta</p>
<p>tarjeta credito</p>
<p>tarjeta de credito</p>
<p>tarjeta crédito</p>
<p>tarjeta de crédito</p>
<p>tarjeta de atm</p>
<p>tarjeta atm</p>
<p>tarjeta debito</p>
<p>tarjeta de debito</p>
<p>tarjeta débito</p>
<p>tarjeta de débito</p>
<p>nº de tarjeta</p>
<p>no. de tarjeta</p>
<p>no de tarjeta</p>
<p>numero de tarjeta</p>
<p>número de tarjeta</p>
<p>tarjeta no</p>
<p>tarjetahabiente</p>
<p>cartão de crédito</p>
<p>cartão de credito</p>
<p>cartao de crédito</p>
<p>cartao de credito</p>
<p>cartão de débito</p>
<p>cartao de débito</p>
<p>cartão de debito</p>
<p>cartao de debito</p>
<p>débito automático</p>
<p>debito automatico</p>
<p>número do cartão</p>
<p>numero do cartão</p>
<p>número do cartao</p>
<p>numero do cartao</p>
<p>número de cartão</p>
<p>numero de cartão</p>
<p>número de cartao</p>
<p>numero de cartao</p>
<p>nº do cartão</p>
<p>nº do cartao</p>
<p>nº. do cartão</p>
<p>no do cartão</p>
<p>no do cartao</p>
<p>no. do cartão</p>
<p>no. do cartao</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер удостоверения личности для Хорватии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Девять цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Девять последовательных цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_croatia_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_croatia_id_card</code>.</p></li>
</ul>
<pre><code>&lt;!--Croatia Identity Card Number--&gt;
&lt;Entity id=&quot;ff12f884-c20a-4189-b185-34c8e7258d47&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_croatia_id_card&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_croatia_id_card&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-41"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_croatia_id_card</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Croatian identity card</p>
<p>Osobna iskaznica</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Индивидуальный идентификационный номер (OIB) для Хорватии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10 цифр:</p>
<ul>
<li><p>шесть цифр в виде ДДММГГ — дата рождения;</p></li>
<li><p>четыре цифры, где последняя цифра — проверочная.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_croatia_oib_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_croatia_oib_number</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_croatia_oib_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Croatia Personal Identification (OIB) Number --&gt;
&lt;Entity id=&quot;31983b6d-db95-4eb2-a630-b44bd091968d&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_croatia_oib_number&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_croatia_oib_number&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_croatia_oib_number&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-43"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_croatia_oib_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Personal Identification Number</p>
<p>Osobni identifikacijski broj</p>
<p>OIB</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер внутреннего удостоверения личности для Чехии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10 цифр с косой чертой.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10 цифр:</p>
<ul>
<li><p>шесть цифр — дата рождения;</p></li>
<li><p>косая черта;</p></li>
<li><p>четыре цифры, где последняя цифра — проверочная.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_czech_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_czech_id_card</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Czech National Identity Card Number --&gt;
&lt;Entity id=&quot;60c0725a-4eb6-455b-9dda-05d8a7396497&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_czech_id_card&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_czech_id_card&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-45"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_czech_id_card</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Czech national identity card</p>
<p>Občanský průka</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Индивидуальный идентификационный номер для Дании


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10 цифр, содержащих дефис.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10 цифр:</p>
<ul>
<li><p>шесть цифр в формате ДДММГГ — дата рождения;</p></li>
<li><p>дефис;</p></li>
<li><p>четыре цифры, где последняя цифра — проверочная.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_denmark_id</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_denmark_id</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Denmark Personal Identification Number --&gt;
&lt;Entity id=&quot;6c4f2fef-56e1-4c00-8093-88d7a01cf460&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_denmark_id&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_denmark_id&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-47"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_denmark_id</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Personal Identification Number</p>
<p>CPR</p>
<p>Det Centrale Personregister</p>
<p>Personnummer</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер Управления по борьбе с наркотиками США (DEA)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Две буквы, за которыми следуют семь цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Шаблон должен включать в себя все указанные ниже элементы.</p>
<ul>
<li><p>Одна буква (без учета регистра) из следующего набора: abcdefghjklmnprstux, представляющая собой код регистрирующегося лица</p></li>
<li><p>Одна буква (без учета регистра), представляющая собой первую букву фамилии регистрирующегося лица</p></li>
<li><p>Семь цифр, последняя из которых — контрольная</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_dea_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- DEA Number --&gt;
&lt;Entity id=&quot;9a5445ad-406e-43eb-8bd7-cac17ab6d0e4&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_dea_number&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><p>Нет</p></td>
</tr>
</tbody>
</table>


## Номер банковской карты для ЕС


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>16 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Очень сложный и надежный шаблон.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_eu_debit_card</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Верно по меньшей мере одно из условий ниже:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_eu_debit_card</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_card_terms_dict</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_card_security_terms_dict</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_card_expiration_terms_dict</code>;</p></li>
<li><p>функция <code>Func_expiration_date</code> находит дату в правильном формате.</p></li>
</ul></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>    &lt;!-- EU Debit Card Number --&gt;
    &lt;Entity id=&quot;0e9b3178-9678-47dd-a509-37222ca96b42&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
      &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_eu_debit_card&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_eu_debit_card&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_card_terms_dict&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_card_security_terms_dict&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_card_expiration_terms_dict&quot; /&gt;
          &lt;Match idRef=&quot;Func_expiration_date&quot; /&gt;
        &lt;/Any&gt;
      &lt;/Pattern&gt;
    &lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-50"> </h3>
<div>
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
<th><p>Keyword_eu_debit_card</p></th>
<th> </th>
<th><p>Keyword_card_terms_dict</p></th>
<th><p>Keyword_card_security_terms_dict</p></th>
<th><p>Keyword_card_expiration_terms_dict</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>account number</p>
<p>card number</p>
<p>card no.</p>
<p>security number</p>
<p>cc#</p></td>
<td> </td>
<td><p>acct nbr</p>
<p>acct num</p>
<p>acct no</p>
<p>american express</p>
<p>americanexpress</p>
<p>americano espresso</p>
<p>amex</p>
<p>atm card</p>
<p>atm cards</p>
<p>atm kaart</p>
<p>atmcard</p>
<p>atmcards</p>
<p>atmkaart</p>
<p>atmkaarten</p>
<p>bancontact</p>
<p>bank card</p>
<p>bankkaart</p>
<p>card holder</p>
<p>card holders</p>
<p>card num</p>
<p>card number</p>
<p>card numbers</p>
<p>card type</p>
<p>cardano numerico</p>
<p>cardholder</p>
<p>cardholders</p>
<p>cardnumber</p>
<p>cardnumbers</p>
<p>carta bianca</p>
<p>carta credito</p>
<p>carta di credito</p>
<p>cartao de credito</p>
<p>cartao de crédito</p>
<p>cartao de debito</p>
<p>cartao de débito</p>
<p>carte bancaire</p>
<p>carte blanche</p>
<p>carte bleue</p>
<p>carte de credit</p>
<p>carte de crédit</p>
<p>carte di credito</p>
<p>carteblanche</p>
<p>cartão de credito</p>
<p>cartão de crédito</p>
<p>cartão de debito</p>
<p>cartão de débito</p>
<p>cb</p>
<p>ccn</p>
<p>check card</p>
<p>check cards</p>
<p>checkcard</p>
<p>checkcards</p>
<p>chequekaart</p>
<p>cirrus</p>
<p>cirrus-edc-maestro</p>
<p>controlekaart</p>
<p>controlekaarten</p>
<p>credit card</p>
<p>credit cards</p>
<p>creditcard</p>
<p>creditcards</p>
<p>debetkaart</p>
<p>debetkaarten</p>
<p>debit card</p>
<p>debit cards</p>
<p>debitcard</p>
<p>debitcards</p>
<p>debito automatico</p>
<p>diners club</p>
<p>dinersclub</p>
<p>discover</p>
<p>discover card</p>
<p>discover cards</p>
<p>discovercard</p>
<p>discovercards</p>
<p>débito automático</p>
<p>edc</p>
<p>eigentümername</p>
<p>european debit card</p>
<p>hoofdkaart</p>
<p>hoofdkaarten</p>
<p>in viaggio</p>
<p>japanese card bureau</p>
<p>japanse kaartdienst</p>
<p>jcb</p>
<p>kaart</p>
<p>kaart num</p>
<p>kaartaantal</p>
<p>kaartaantallen</p>
<p>kaarthouder</p>
<p>kaarthouders</p>
<p>karte</p>
<p>karteninhaber</p>
<p>karteninhabers</p>
<p>kartennr</p>
<p>kartennummer</p>
<p>kreditkarte</p>
<p>kreditkarten-nummer</p>
<p>kreditkarteninhaber</p>
<p>kreditkarteninstitut</p>
<p>kreditkartennummer</p>
<p>kreditkartentyp</p>
<p>maestro</p>
<p>master card</p>
<p>master cards</p>
<p>mastercard</p>
<p>mastercards</p>
<p>mc</p>
<p>mister cash</p>
<p>n carta</p>
<p>n. carta</p>
<p>no de tarjeta</p>
<p>no do cartao</p>
<p>no do cartão</p>
<p>no. de tarjeta</p>
<p>no. do cartao</p>
<p>no. do cartão</p>
<p>nr carta</p>
<p>nr. carta</p>
<p>numeri di scheda</p>
<p>numero carta</p>
<p>numero de cartao</p>
<p>numero de carte</p>
<p>numero de cartão</p>
<p>numero de tarjeta</p>
<p>numero della carta</p>
<p>numero di carta</p>
<p>numero di scheda</p>
<p>numero do cartao</p>
<p>numero do cartão</p>
<p>numéro de carte</p>
<p>nº carta</p>
<p>nº de carte</p>
<p>nº de la carte</p>
<p>nº de tarjeta</p>
<p>nº do cartao</p>
<p>nº do cartão</p>
<p>nº. do cartão</p>
<p>número de cartao</p>
<p>número de cartão</p>
<p>número de tarjeta</p>
<p>número do cartao</p>
<p>scheda dell'assegno</p>
<p>scheda dell'atmosfera</p>
<p>scheda dell'atmosfera</p>
<p>scheda della banca</p>
<p>scheda di controllo</p>
<p>scheda di debito</p>
<p>scheda matrice</p>
<p>schede dell'atmosfera</p>
<p>schede di controllo</p>
<p>schede di debito</p>
<p>schede matrici</p>
<p>scoprono la scheda</p>
<p>scoprono le schede</p>
<p>solo</p>
<p>supporti di scheda</p>
<p>supporto di scheda</p>
<p>switch</p>
<p>tarjeta atm</p>
<p>tarjeta credito</p>
<p>tarjeta de atm</p>
<p>tarjeta de credito</p>
<p>tarjeta de debito</p>
<p>tarjeta debito</p>
<p>tarjeta no</p>
<p>tarjetahabiente</p>
<p>tipo della scheda</p>
<p>ufficio giapponese della</p>
<p>scheda</p>
<p>v pay</p>
<p>v-pay</p>
<p>visa</p>
<p>visa plus</p>
<p>visa electron</p>
<p>visto</p>
<p>visum</p>
<p>vpay</p></td>
<td><p>card identification number</p>
<p>card verification</p>
<p>cardi la verifica</p>
<p>cid</p>
<p>cod seg</p>
<p>cod seguranca</p>
<p>cod segurança</p>
<p>cod sicurezza</p>
<p>cod. seg</p>
<p>cod. seguranca</p>
<p>cod. segurança</p>
<p>cod. sicurezza</p>
<p>codice di sicurezza</p>
<p>codice di verifica</p>
<p>codigo</p>
<p>codigo de seguranca</p>
<p>codigo de segurança</p>
<p>crittogramma</p>
<p>cryptogram</p>
<p>cryptogramme</p>
<p>cv2</p>
<p>cvc</p>
<p>cvc2</p>
<p>cvn</p>
<p>cvv</p>
<p>cvv2</p>
<p>cód seguranca</p>
<p>cód segurança</p>
<p>cód. seguranca</p>
<p>cód. segurança</p>
<p>código</p>
<p>código de seguranca</p>
<p>código de segurança</p>
<p>de kaart controle</p>
<p>geeft nr uit</p>
<p>issue no</p>
<p>issue number</p>
<p>kaartidentificatienummer</p>
<p>kreditkartenprufnummer</p>
<p>kreditkartenprüfnummer</p>
<p>kwestieaantal</p>
<p>no. dell'edizione</p>
<p>no. di sicurezza</p>
<p>numero de securite</p>
<p>numero de verificacao</p>
<p>numero dell'edizione</p>
<p>numero di identificazione della</p>
<p>scheda</p>
<p>numero di sicurezza</p>
<p>numero van veiligheid</p>
<p>numéro de sécurité</p>
<p>nº autorizzazione</p>
<p>número de verificação</p>
<p>perno il blocco</p>
<p>pin block</p>
<p>prufziffer</p>
<p>prüfziffer</p>
<p>security code</p>
<p>security no</p>
<p>security number</p>
<p>sicherheits kode</p>
<p>sicherheitscode</p>
<p>sicherheitsnummer</p>
<p>speldblok</p>
<p>veiligheid nr</p>
<p>veiligheidsaantal</p>
<p>veiligheidscode</p>
<p>veiligheidsnummer</p>
<p>verfalldatum</p></td>
<td><p>ablauf</p>
<p>data de expiracao</p>
<p>data de expiração</p>
<p>data del exp</p>
<p>data di exp</p>
<p>data di scadenza</p>
<p>data em que expira</p>
<p>data scad</p>
<p>data scadenza</p>
<p>date de validité</p>
<p>datum afloop</p>
<p>datum van exp</p>
<p>de afloop</p>
<p>espira</p>
<p>espira</p>
<p>exp date</p>
<p>exp datum</p>
<p>expiration</p>
<p>expire</p>
<p>expires</p>
<p>expiry</p>
<p>fecha de expiracion</p>
<p>fecha de venc</p>
<p>gultig bis</p>
<p>gultigkeitsdatum</p>
<p>gültig bis</p>
<p>gültigkeitsdatum</p>
<p>la scadenza</p>
<p>scadenza</p>
<p>valable</p>
<p>validade</p>
<p>valido hasta</p>
<p>valor</p>
<p>venc</p>
<p>vencimento</p>
<p>vencimiento</p>
<p>verloopt</p>
<p>vervaldag</p>
<p>vervaldatum</p>
<p>vto</p>
<p>válido hasta</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Национальный идентификатор, Финляндия


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Шесть цифр, а также символ, обозначающий век, три цифры и контрольная цифра.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Шаблон должен включать в себя все указанные ниже элементы.</p>
<ul>
<li><p>Шесть цифр в формате ДДММГГ, представляющие собой дату рождения</p></li>
<li><p>Маркер века (символы &quot;-&quot; и &quot;+&quot; или буква &quot;a&quot;)</p></li>
<li><p>Трехзначный личный идентификационный номер</p></li>
<li><p>Цифра или буква (без учета регистра) — проверочная.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_finnish_national_id</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_finnish_national_id</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Finnish National ID--&gt;
&lt;Entity id=&quot;338FD995-4CB5-4F87-AD35-79BD1DD926C1&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
          &lt;IdMatch idRef=&quot;Func_finnish_national_id&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_finnish_national_id&quot; /&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-52"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_finnish_national_id</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Sosiaaliturvatunnus</p>
<p>SOTU Henkilötunnus HETU</p>
<p>Personbeteckning</p>
<p>Personnummer</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер паспорта для Финляндии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Сочетание из девяти букв и цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Сочетание из девяти букв и цифр:</p>
<ul>
<li><p>две буквы (без учета регистра);</p></li>
<li><p>семь цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_finland_passport_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_finland_passport_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Finland Passport Number --&gt;
&lt;Entity id=&quot;d1685ac3-1d3a-40f8-8198-32ef5669c7a5&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_finland_passport_number&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_finland_passport_number&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-54"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_finland_passport_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Passport</p>
<p>Passi</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер водительского удостоверения для Франции


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>12 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>12 цифр с проверкой подлинности, чтобы избежать путаницы с похожими шаблонами, например французскими номерами телефонов.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_french_drivers_license</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Верно по меньшей мере одно из условий ниже:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_french_drivers_license</code>;</p></li>
<li><p>функция <code>Func_eu_date</code> находит дату в правильном формате.</p></li>
</ul></li>
</ul>
<pre><code>&lt;!-- France Driver&#39;s License Number --&gt;
&lt;Entity id=&quot;18e55a36-a01b-4b0f-943d-dc10282a1824&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_french_drivers_license&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_french_drivers_license&quot; /&gt;
          &lt;Match idRef=&quot;Func_eu_date&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-56"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_french_drivers_license</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>drivers licence</p>
<p>drivers license</p>
<p>driving licence</p>
<p>driving license</p>
<p>permis de conduire</p>
<p>licence number</p>
<p>license number</p>
<p>licence numbers</p>
<p>license numbers</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер внутреннего удостоверения личности для Франции (CNI)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>12 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>12 цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 65 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_france_cni</code> находит содержимое, которое соответствует шаблону.</p></li>
</ul>
<pre><code>&lt;!-- France CNI --&gt;
&lt;Entity id=&quot;f741ac74-1bc0-4665-b69b-f0c7f927c0c4&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;65&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;65&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_france_cni&quot; /&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><p>Нет</p></td>
</tr>
</tbody>
</table>


## Номер паспорта гражданина Франции


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Девять цифр и букв.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Девять цифр и букв</p>
<ul>
<li><p>Две цифры</p></li>
<li><p>Две буквы (без учета регистра)</p></li>
<li><p>Пять цифр</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_fr_passport</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_passport</code>.</p></li>
</ul>
<pre><code>&lt;!-- France Passport Number --&gt;
&lt;Entity id=&quot;3008b884-8c8c-4cd8-a289-99f34fc7ff5d&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_fr_passport&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_passport&quot; /&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-59"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_passport</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Passport Number</p>
<p>Passport No</p>
<p>Passport#</p>
<p>Passport#</p>
<p>PassportID</p>
<p>Passportno</p>
<p>passportnumber</p>
<p>パスポート</p>
<p>パスポート番号</p>
<p>パスポートのNum</p>
<p>パスポート＃</p>
<p>Numéro de passeport</p>
<p>Passeport n °</p>
<p>Passeport Non</p>
<p>Passeport#</p>
<p>Passeport#</p>
<p>PasseportNon</p>
<p>Passeportn °</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Страховой номер для Франции (INSEE)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>15 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Должен соответствовать одному из двух шаблонов:</p>
<ul>
<li><p>13 цифр, за которыми идет пробел, а потом еще две цифры;</p></li>
<li><p>15 последовательных цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 95 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_french_insee</code> или <code>Func_fr_insee</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_fr_insee</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_french_insee</code> или <code>Func_fr_insee</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>ни одно ключевое слово из <code>Keyword_fr_insee</code> не находится;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- France INSEE --&gt;
&lt;Entity id=&quot;71f62b97-efe0-4aa1-aa49-e14de253619d&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;95&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_french_insee&quot; /&gt;
        &lt;Match idRef=&quot;Func_fr_insee&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_fr_insee&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_french_insee&quot; /&gt;
        &lt;Match idRef=&quot;Func_fr_insee&quot; /&gt;
        &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
          &lt;Match idRef=&quot;Keyword_fr_insee&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-61"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_fr_insee</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>insee</p>
<p>securité sociale</p>
<p>securite sociale</p>
<p>national id</p>
<p>national identification</p>
<p>numéro d'identité</p>
<p>no d'identité</p>
<p>no. d'identité</p>
<p>numero d'identite</p>
<p>no d'identite</p>
<p>no. d'identite</p>
<p>social security number</p>
<p>social security code</p>
<p>social insurance number</p>
<p>le numéro d'identification nationale</p>
<p>d'identité nationale</p>
<p>numéro de sécurité sociale</p>
<p>le code de la sécurité sociale</p>
<p>numéro d'assurance sociale</p>
<p>numéro de sécu</p>
<p>code sécu</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер водительского удостоверения для Германии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Сочетание 11 цифр и букв.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>11 цифр и букв (без учета регистра)</p>
<ul>
<li><p>Одна цифра или буква</p></li>
<li><p>Две цифры</p></li>
<li><p>Шесть цифр или букв</p></li>
<li><p>Одна цифра</p></li>
<li><p>Одна цифра или буква</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_german_drivers_license</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>Верно по меньшей мере одно из условий ниже:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_german_drivers_license_number</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_german_drivers_license_collaborative</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_german_drivers_license</code>;</p></li>
</ul></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- German Driver&#39;s License Number --&gt;
&lt;Entity id=&quot;91da9335-1edb-45b7-a95f-5fe41a16c63c&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_german_drivers_license&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_german_drivers_license_number&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_drivers_license_collaborative&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_drivers_license&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-63"> </h3>
<div>
<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_german_drivers_license_number</p></th>
<th> </th>
<th><p>Keyword_german_drivers_license_collaborative</p></th>
<th><p>Keyword_german_drivers_license</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Führerschein</p>
<p>Fuhrerschein</p>
<p>Fuehrerschein</p>
<p>Führerscheinnummer</p>
<p>Fuhrerscheinnummer</p>
<p>Fuehrerscheinnummer</p>
<p>Führerschein-</p>
<p>Fuhrerschein-</p>
<p>Fuehrerschein-</p>
<p>FührerscheinnummerNr</p>
<p>FuhrerscheinnummerNr</p>
<p>FuehrerscheinnummerNr</p>
<p>FührerscheinnummerKlasse</p>
<p>FuhrerscheinnummerKlasse</p>
<p>FuehrerscheinnummerKlasse</p>
<p>Führerschein- Nr</p>
<p>Fuhrerschein- Nr</p>
<p>Fuehrerschein- Nr</p>
<p>Führerschein- Klasse</p>
<p>Fuhrerschein- Klasse</p>
<p>Fuehrerschein- Klasse</p>
<p>FührerscheinnummerNr</p>
<p>FuhrerscheinnummerNr</p>
<p>FuehrerscheinnummerNr</p>
<p>FührerscheinnummerKlasse</p>
<p>FuhrerscheinnummerKlasse</p>
<p>FuehrerscheinnummerKlasse</p>
<p>Führerschein- Nr</p>
<p>Fuhrerschein- Nr</p>
<p>Fuehrerschein- Nr</p>
<p>Führerschein- Klasse</p>
<p>Fuhrerschein- Klasse</p>
<p>Fuehrerschein- Klasse</p>
<p>DL</p>
<p>DLS</p>
<p>Driv Lic</p>
<p>Driv Licen</p>
<p>Driv License</p>
<p>Driv Licenses</p>
<p>Driv Licence</p>
<p>Driv Licences</p>
<p>Driv Lic</p>
<p>Driver Licen</p>
<p>Driver License</p>
<p>Driver Licenses</p>
<p>Driver Licence</p>
<p>Driver Licences</p>
<p>Drivers Lic</p>
<p>Drivers Licen</p>
<p>Drivers License</p>
<p>Drivers Licenses</p>
<p>Drivers Licence</p>
<p>Drivers Licences</p>
<p>Driver's Lic</p>
<p>Driver's Licen</p>
<p>Driver's License</p>
<p>Driver's Licenses</p>
<p>Driver's Licence</p>
<p>Driver's Licences</p>
<p>Driving Lic</p>
<p>Driving Licen</p>
<p>Driving License</p>
<p>Driving Licenses</p>
<p>Driving Licence</p>
<p>Driving Licences</p></td>
<td> </td>
<td><p>Nr-Führerschein</p>
<p>Nr-Fuhrerschein</p>
<p>Nr-Fuehrerschein</p>
<p>No-Führerschein</p>
<p>No-Fuhrerschein</p>
<p>No-Fuehrerschein</p>
<p>N-Führerschein</p>
<p>N-Fuhrerschein</p>
<p>N-Fuehrerschein</p>
<p>Nr-Führerschein</p>
<p>Nr-Fuhrerschein</p>
<p>Nr-Fuehrerschein</p>
<p>No-Führerschein</p>
<p>No-Fuhrerschein</p>
<p>No-Fuehrerschein</p>
<p>N-Führerschein</p>
<p>N-Fuhrerschein</p>
<p>N-Fuehrerschein</p></td>
<td><p>ausstellungsdatum</p>
<p>ausstellungsort</p>
<p>ausstellende behöde</p>
<p>ausstellende behorde</p>
<p>ausstellende behoerde</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер удостоверения личности для Германии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>С 1 ноября 2010 г.:</p>
<dl>
<dt><span></span></dt>
<dd><p>девять букв и цифр.</p>
</dd>
</dl>
<p>С 1 апреля 1987 г. до 31 октября 2010 г.:</p>
<dl>
<dt><span></span></dt>
<dd><p>10 цифр.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>С 1 ноября 2010 г.:</p>
<ul>
<li><p>Одна буква (без учета регистра)</p></li>
<li><p>восемь цифр.</p></li>
</ul>
<p>С 1 апреля 1987 г. до 31 октября 2010 г.:</p>
<ul>
<li><p>10 цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 65 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_germany_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_germany_id_card</code>.</p></li>
</ul>
<pre><code>&lt;!-- Germany Identity Card Number --&gt;
&lt;Entity id=&quot;e577372f-c42e-47a0-9d85-bebed1c237d4&quot; recommendedConfidence=&quot;65&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;65&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_germany_id_card&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_germany_id_card&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-65"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_germany_id_card</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Identity Card</p>
<p>ID</p>
<p>Identification</p>
<p>Personalausweis</p>
<p>Identifizierungsnummer</p>
<p>Ausweis</p>
<p>Identifikation</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер паспорта гражданина Германии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10 цифр или букв.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Шаблон должен включать в себя все указанные ниже элементы.</p>
<ul>
<li><p>Первый символ — цифра или буква из следующего набора: C, F, G, H, J, K.</p></li>
<li><p>Три цифры</p></li>
<li><p>Пять цифр или букв из следующего набора: C, F-H, J-N, P, R, T, V-Z</p></li>
<li><p>Одна цифра</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_german_passport</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится любое ключевое слово из пяти соответствующих списков;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_german_passport_data</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится любое ключевое слово из пяти соответствующих списков;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- German Passport Number --&gt;
&lt;Entity id=&quot;2e3da144-d42b-47ed-b123-fbf78604e52c&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_german_passport&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_german_passport&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_passport_collaborative&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_passport_number&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_passport1&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_passport2&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_german_passport_data&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_german_passport&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_passport_collaborative&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_passport_number&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_passport1&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_german_passport2&quot; /&gt;
        &lt;/Any&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-67"> </h3>
<div>
<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_german_passport</p></th>
<th> </th>
<th><p>Keyword_german_passport_collaborative</p></th>
<th><p>Keyword_german_passport_number</p></th>
<th><p>Keyword_german_passport1</p></th>
<th><p>Keyword_german_passport2</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>reisepass</p>
<p>reisepasse</p>
<p>reisepassnummer</p>
<p>passport</p>
<p>passports</p></td>
<td> </td>
<td><p>geburtsdatum</p>
<p>ausstellungsdatum</p>
<p>ausstellungsort</p></td>
<td><p>No-Reisepass</p>
<p>Nr-Reisepass</p></td>
<td><p>Reisepass-Nr</p></td>
<td><p>bnationalit.t</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер внутреннего удостоверения личности для Греции


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Сочетание 7–8 букв и чисел, а также тире.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Семь букв и чисел (старый формат):</p>
<ul>
<li><p>одна буква (любая буква греческого алфавита);</p></li>
<li><p>Тире</p></li>
<li><p>Шесть цифр</p></li>
</ul>
<p>Восемь букв и чисел (новый формат):</p>
<ul>
<li><p>две буквы, которые в прописном виде есть как в греческом, так и латинском алфавите (ABEZHIKMNOPTYX);</p></li>
<li><p>Тире</p></li>
<li><p>Шесть цифр</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_greece_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_greece_id_card</code>.</p></li>
</ul>
<pre><code>&lt;!-- Greece National ID Card --&gt;
&lt;Entity id=&quot;82568215-1da1-46d3-874a-d2294d81b5ac&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_greece_id_card&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_greece_id_card&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-69"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_greece_id_card</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Greek identity Card</p>
<p>Tautotita</p>
<p>Δελτίο αστυνομικής ταυτότητας</p>
<p>Ταυτότητα</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер удостоверения личности для Гонконга (HKID)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Сочетание 8–9 букв и чисел, а также необязательные скобки вокруг последнего символа.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Сочетание 8–9 букв:</p>
<ul>
<li><p>1–2 буквы (без учета регистра);</p></li>
<li><p>Шесть цифр</p></li>
<li><p>последний символ (любая цифра или буква &quot;A&quot;) является проверочной цифрой и заключен в скобки (необязательно).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_hong_kong_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_hong_kong_id_card</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 65 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_hong_kong_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Hong Kong Identity Card (HKID) number --&gt;
&lt;Entity id=&quot;e63c28a7-ad29-4c17-a41a-3d2a0b70fd9c&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_hong_kong_id_card&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_hong_kong_id_card&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;65&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_hong_kong_id_card&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-71"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_hong_kong_id_card</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Hong Kong Identity Card</p>
<p>HKID</p>
<p>ID card</p>
<p>香港身份證</p>
<p>香港永久性居民身份證</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Идентификационный номер налогоплательщика для Индии (PAN)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10 букв или цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10 букв или цифр:</p>
<ul>
<li><p>пять букв (без учета регистра);</p></li>
<li><p>Четыре цифры</p></li>
<li><p>буква, которая является алфавитным проверочным символом.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_india_permanent_account_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_india_permanent_account_number</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- India Permanent Account Number --&gt;
&lt;Entity id=&quot;2602bfee-9bb0-47a5-a7a6-2bf3053e2804&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_india_permanent_account_number&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_india_permanent_account_number&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-73"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_india_permanent_account_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Permanent Account Number</p>
<p>PAN</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Индивидуальный идентификационный номер (Aadhaar) для Индии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>12 цифр, содержащих необязательные пробелы или тире.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>12 цифр:</p>
<ul>
<li><p>Четыре цифры</p></li>
<li><p>необязательный пробел или тире;</p></li>
<li><p>Четыре цифры</p></li>
<li><p>необязательный пробел или тире;</p></li>
<li><p>последняя цифра — проверочная.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_india_aadhaar</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_india_aadhar</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_india_aadhaar</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- India Unique Identification (Aadhaar) number --&gt;
&lt;Entity id=&quot;1ca46b29-76f5-4f46-9383-cfa15e91048f&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_india_aadhaar&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_india_aadhar&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_india_aadhaar&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-75"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_india_aadhar</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aadhar</p>
<p>Aadhaar</p>
<p>UID</p>
<p>आधार</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер удостоверения личности (KTP) для Индонезии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>16 цифр, содержащих необязательные точки.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>16 цифр:</p>
<ul>
<li><p>две цифры (код провинции);</p></li>
<li><p>точка (необязательно);</p></li>
<li><p>две цифры (код округа или города);</p></li>
<li><p>две цифры (код района);</p></li>
<li><p>точка (необязательно);</p></li>
<li><p>шесть цифр в формате ДДММГГ (дата рождения);</p></li>
<li><p>точка (необязательно);</p></li>
<li><p>Четыре цифры</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_indonesia_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_indonesia_id_card</code>.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_indonesia_id_card</code> находит содержимое, которое соответствует шаблону;</p></li>
</ul>
<pre><code>&lt;!-- Indonesia Identity Card (KTP) Number --&gt;
&lt;Entity id=&quot;da68fdb0-f383-4981-8c86-82689d3b7d55&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_indonesia_id_card&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_indonesia_id_card&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_indonesia_id_card&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-77"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_indonesia_id_card</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>KTP</p>
<p>Kartu Tanda Penduduk</p>
<p>Nomor Induk Kependudukan</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Международный номер банковского счета (IBAN)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Код страны (две буквы), а также проверочные цифры (две) и номер bban (до 30 символов)</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Шаблон должен включать в себя все указанные ниже элементы.</p>
<ul>
<li><p>Двухбуквенный код страны</p></li>
<li><p>Две проверочные цифры (после которых может следовать пробел)</p></li>
<li><p>1–7 групп из четырех букв или цифр (могут разделяться пробелами)</p></li>
<li><p>1–3 буквы или цифры</p></li>
</ul>
<p>Формат для названия каждой из стран немного отличается. Тип конфиденциальной информации IBAN применяется к следующим 60 странам:</p>
<dl>
<dt><span></span></dt>
<dd><p>ad, ae, al, at, az, ba, be, bg, bh, ch, cr, cy, cz, de, dk, do, ee, es, fi, fo, fr, gb, ge, gi, gl, gr, hr, hu, ie, il, is, it, kw, kz, lb, li, lt, lu, lv, mc, md, me, mk, mr, mt, mu, nl, no, pl, pt, ro, rs, sa, se, si, sk, sm, tn, tr, vg</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_iban</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;Entity id=&quot;e7dc4711-11b7-4cb0-b88b-2c394a771f0e&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_iban&quot; /&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><p>Нет</p></td>
</tr>
</tbody>
</table>


## IP-адрес


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>IPv4:</p>
<ul>
<li><p>Сложный шаблон, ответственный за форматированные (с точками) и неформатированные (без точек) версии IPv4-адресов.</p></li>
</ul>
<p>Протокол IPv6</p>
<ul>
<li><p>Сложный шаблон, ответственный за форматированные номера IPv6 (вместе с двоеточиями).</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>В случае с протоколом IPv6 политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_ipv6_address</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>ни одно ключевое слово из <code>Keyword_ipaddress</code> не находится.</p></li>
</ul>
<p>В случае с протоколом IPv4 политика защиты от потери данных с вероятностью в 95 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_ipv4_address</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_ipaddress</code>.</p></li>
</ul>
<p>В случае с протоколом IPv6 политика защиты от потери данных с вероятностью в 95 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_ipv6_address</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>ни одно ключевое слово из <code>Keyword_ipaddress</code> не находится.</p></li>
</ul>
<pre><code>    &lt;!-- IP Address --&gt;
    &lt;Entity id=&quot;1daa4ad5-e2dd-4ca4-a788-54722c09efb2&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
      &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_ipv6_address&quot; /&gt;
        &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
          &lt;Match idRef=&quot;Keyword_ipaddress&quot; /&gt;
        &lt;/Any&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;95&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_ipv4_address&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_ipaddress&quot; /&gt;
        &lt;/Any&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;95&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_ipv6_address&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_ipaddress&quot; /&gt;
        &lt;/Any&gt;
      &lt;/Pattern&gt;
    &lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-80"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_ipaddress</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IP (ключевое слово с учетом регистра)</p>
<p>ip address</p>
<p>ip addresses</p>
<p>internet protocol</p>
<p>IP-כתובת ה</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Индивидуальный социальный номер (PPS) для Ирландии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Старый формат (до 31.12.2012):</p>
<dl>
<dt><span></span></dt>
<dd><p>семь цифр, за которыми следуют 1–2 буквы.</p>
</dd>
</dl>
<p>Новый формат (с 01.01.2013):</p>
<dl>
<dt><span></span></dt>
<dd><p>семь цифр, за которыми следуют две буквы.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Старый формат (до 31.12.2012):</p>
<ul>
<li><p>семь цифр;</p></li>
<li><p>1–2 буквы (без учета регистра).</p></li>
</ul>
<p>Новый формат (с 01.01.2013):</p>
<ul>
<li><p>семь цифр;</p></li>
<li><p>буква (без учета регистра), которая является алфавитным проверочным символом;</p></li>
<li><p>буква &quot;A&quot; или &quot;H&quot; (без учета регистра).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_ireland_pps</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Верно одно из условий ниже:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_ireland_pps</code>;</p></li>
<li><p>функция <code>Func_eu_date</code> находит дату в правильном формате.</p></li>
</ul></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 65 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_ireland_pps</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Ireland Personal Public Service (PPS) Number --&gt;
&lt;Entity id=&quot;1cdb674d-c19a-4fcf-9f4b-7f56cc87345a&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_ireland_pps&quot;/&gt;
     &lt;Any minMatches=&quot;1&quot;&gt;
  &lt;Match idRef=&quot;Keyword_ireland_pps&quot;/&gt;
  &lt;Match idRef=&quot;Func_eu_date&quot;/&gt;
     &lt;/Any&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;65&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_ireland_pps&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-82"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_ireland_pps</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Personal Public Service Number</p>
<p>PPS Number</p>
<p>PPS Num</p>
<p>PPS No.</p>
<p>PPS #</p>
<p>PPS#</p>
<p>PPSN</p>
<p>Public Services Card</p>
<p>Uimhir Phearsanta Seirbhíse Poiblí</p>
<p>Uimh. PSP</p>
<p>PSP</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер банковского счета для Израиля


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>13 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>С форматированием</p>
<ul>
<li><p>Две цифры</p></li>
<li><p>Тире</p></li>
<li><p>Три цифры</p></li>
<li><p>Тире</p></li>
<li><p>восемь цифр.</p></li>
</ul>
<p>Без форматирования</p>
<ul>
<li><p>13 последовательных цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_israel_bank_account_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_israel_bank_account_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Israel Bank Account Number --&gt;
&lt;Entity id=&quot;7d08b2ff-a0b9-437f-957c-aeddbf9b2b25&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_israel_bank_account_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_israel_bank_account_number&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-84"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_israel_bank_account_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Bank Account Number</p>
<p>Bank Account</p>
<p>Account Number</p>
<p>מספר חשבון בנק</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Национальный идентификатор для Израиля


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Девять цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Девять последовательных цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_israeli_national_id_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_Israel_National_ID</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Israel National ID Number --&gt;
&lt;Entity id=&quot;e05881f5-1db1-418c-89aa-a3ac5c5277ee&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_israeli_national_id_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_Israel_National_ID&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-86"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_Israel_National_ID</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>מספר זהות</p>
<p>National ID Number</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер водительского удостоверения для Италии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Сочетание из 10 букв и цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Сочетание 10 букв и цифр.</p>
<ul>
<li><p>Одна буква (без учета регистра)</p></li>
<li><p>Буква &quot;A&quot; или &quot;V&quot; (без учета регистра)</p></li>
<li><p>Семь букв (без учета регистра), цифр или символов подчеркивания</p></li>
<li><p>Одна буква (без учета регистра)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_italy_drivers_license_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_italy_drivers_license_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Italy Driver&#39;s license Number --&gt;
&lt;Entity id=&quot;97d6244f-9157-41bd-8e0c-9d669a5c4d71&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_italy_drivers_license_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_italy_drivers_license_number&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-88"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_italy_drivers_license_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>numero di patente di guida</p>
<p>patente di guida</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер банковского счета для Японии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Семь или восемь цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Номер банковского счета:</p>
<ul>
<li><p>семь или восемь цифр.</p></li>
</ul>
<p>Код филиала для банковского счета.</p>
<ul>
<li><p>Четыре цифры</p></li>
<li><p>Пробел или тире (необязательно)</p></li>
<li><p>Три цифры</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_jp_bank_account</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Находится ключевое слово из <code>Keyword_jp_bank_account</code>.</p></li>
<li><p>Верно одно из условий ниже:</p>
<ul>
<li><p>функция <code>Func_jp_bank_account_branch_code</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_jp_bank_branch_code</code>.</p></li>
</ul></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_jp_bank_account</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_jp_bank_account</code>.</p></li>
</ul>
<pre><code>&lt;!-- Japan Bank Account Number --&gt;
&lt;Entity id=&quot;d354f95b-96ee-4b80-80bc-4377312b55bc&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
  &lt;Version minEngineVersion=&quot;15.01.0131.000&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
          &lt;IdMatch idRef=&quot;Func_jp_bank_account&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_jp_bank_account&quot; /&gt;
          &lt;Any minMatches=&quot;1&quot;&gt;
            &lt;Match idRef=&quot;Func_jp_bank_account_branch_code&quot; /&gt;
            &lt;Match idRef=&quot;Keyword_jp_bank_branch_code&quot; /&gt;
          &lt;/Any&gt;
      &lt;/Pattern&gt;
  &lt;/Version&gt;    
     &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_jp_bank_account&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_jp_bank_account&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-90"> </h3>
<div>
<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_jp_bank_account</p></th>
<th> </th>
<th><p>Keyword_jp_bank_branch_code</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Checking Account Number</p>
<p>Checking Account</p>
<p>Checking Account #</p>
<p>Checking Acct Number</p>
<p>Checking Acct #</p>
<p>Checking Acct No.</p>
<p>Checking Account No.</p>
<p>Bank Account Number</p>
<p>Bank Account</p>
<p>Bank Account #</p>
<p>Bank Acct Number</p>
<p>Bank Acct #</p>
<p>Bank Acct No.</p>
<p>Bank Account No.</p>
<p>Savings Account Number</p>
<p>Savings Account</p>
<p>Savings Account #</p>
<p>Savings Acct Number</p>
<p>Savings Acct #</p>
<p>Savings Acct No.</p>
<p>Savings Account No.</p>
<p>Debit Account Number</p>
<p>Debit Account</p>
<p>Debit Account #</p>
<p>Debit Acct Number</p>
<p>Debit Acct #</p>
<p>Debit Acct No.</p>
<p>Debit Account No.</p>
<p>口座番号を当座預金口座の確認</p>
<p>＃アカウントの確認、勘定番号の確認</p>
<p>＃勘定の確認</p>
<p>勘定番号の確認</p>
<p>口座番号の確認</p>
<p>銀行口座番号</p>
<p>銀行口座</p>
<p>銀行口座＃</p>
<p>銀行の勘定番号</p>
<p>銀行のacct＃</p>
<p>銀行の勘定いいえ</p>
<p>銀行口座番号</p>
<p>普通預金口座番号</p>
<p>預金口座</p>
<p>貯蓄口座＃</p>
<p>貯蓄勘定の数</p>
<p>貯蓄勘定＃</p>
<p>貯蓄勘定番号</p>
<p>普通預金口座番号</p>
<p>引き落とし口座番号</p>
<p>口座番号</p>
<p>口座番号＃</p>
<p>デビットのacct番号</p>
<p>デビット勘定＃</p>
<p>デビットACCTの番号</p>
<p>デビット口座番号</p></td>
<td> </td>
<td><p>Otemachi</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер водительского удостоверения для Японии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>12 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>12 последовательных цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_jp_drivers_license_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_jp_drivers_license_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Japan Driver&#39;s License Number --&gt;
&lt;Entity id=&quot;c6011143-d087-451c-8313-7f6d4aed2270&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_jp_drivers_license_number&quot; /&gt;
        &lt;Match idRef =&quot;Keyword_jp_drivers_license_number&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-92"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_jp_drivers_license_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>driver license</p>
<p>drivers license</p>
<p>driver's license</p>
<p>drivers licenses</p>
<p>driver's licenses</p>
<p>driver licenses</p>
<p>dl#</p>
<p>dls#</p>
<p>lic#</p>
<p>lics#</p>
<p>運転免許証</p>
<p>運転免許</p>
<p>免許証</p>
<p>免許</p>
<p>運転免許証番号</p>
<p>運転免許番号</p>
<p>免許証番号</p>
<p>免許番号</p>
<p>運転免許証ナンバー</p>
<p>運転免許ナンバー</p>
<p>免許証ナンバー</p>
<p>運転免許証No.</p>
<p>運転免許No.</p>
<p>免許証No.</p>
<p>免許No.</p>
<p>運転免許証#</p>
<p>運転免許#</p>
<p>免許証#</p>
<p>免許#</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер паспорта гражданина Японии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Две буквы, за которыми следуют семь цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Две буквы (без учета регистра), за которыми следуют семь цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_jp_passport</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_jp_passport</code>.</p></li>
</ul>
<pre><code>&lt;!-- Japan Passport Number --&gt;
&lt;Entity id=&quot;75177310-1a09-4613-bf6d-833aae3743f8&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_jp_passport&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_jp_passport&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-94"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_jp_passport</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>パスポート</p>
<p>パスポート番号</p>
<p>パスポートのNum</p>
<p>パスポート＃</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер регистрации резидента Японии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>11 разрядов</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>11 последовательных цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_jp_resident_registration_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_jp_resident_registration_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Japan Resident Registration Number --&gt;
&lt;Entity id=&quot;01c1209b-6389-4faf-a5f8-3f7e13899652&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_jp_resident_registration_number&quot; /&gt;
        &lt;Match idRef =&quot;Keyword_jp_resident_registration_number&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-96"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_jp_resident_registration_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Resident Registration Number</p>
<p>Resident Register Number</p>
<p>Residents Basic Registry Number</p>
<p>Resident Registration No.</p>
<p>Resident Register No.</p>
<p>Residents Basic Registry No.</p>
<p>Basic Resident Register No.</p>
<p>住民登録番号、登録番号をレジデント</p>
<p>住民基本登録番号、登録番号</p>
<p>住民基本レジストリ番号を常駐</p>
<p>登録番号を常駐住民基本台帳登録番号</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер карты социального страхования для Японии (SIN)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>7–12 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>7–12 цифр</p>
<ul>
<li><p>Четыре цифры</p></li>
<li><p>Дефис (необязательно)</p></li>
<li><p>Шесть цифр</p></li>
<li><p>ИЛИ</p></li>
<li><p>7–12 последовательных цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_jp_sin</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_jp_sin</code>.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_jp_sin_pre_1997</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_jp_sin</code>.</p></li>
</ul>
<pre><code>&lt;!-- Japan Social Insurance Number --&gt;
&lt;Entity id=&quot;c840e719-0896-45bb-84fd-1ed5c95e45ff&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_jp_sin&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_jp_sin&quot; /&gt;
    &lt;/Pattern&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_jp_sin_pre_1997&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_jp_sin&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-98"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_jp_sin</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Social Insurance No.</p>
<p>Social Insurance Num</p>
<p>Social Insurance Number</p>
<p>社会保険のテンキー</p>
<p>社会保険番号</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер удостоверения личности для Малайзии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>12 цифр, содержащих необязательные дефисы.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>12 цифр:</p>
<ul>
<li><p>шесть цифр в формате ГГММДД (дата рождения);</p></li>
<li><p>дефис (необязательно);</p></li>
<li><p>код места рождения из двух букв;</p></li>
<li><p>дефис (необязательно);</p></li>
<li><p>три случайные цифры;</p></li>
<li><p>код пола из одной цифры.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_malaysia_id_card_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_malaysia_id_card_number</code>.</p></li>
</ul>
<pre><code>&lt;!-- Malaysia ID Card Number --&gt;
&lt;/Entity&gt;
      &lt;Entity id=&quot;7f0e921c-9677-435b-aba2-bb8f1013c749&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
        &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
            &lt;IdMatch idRef=&quot;Regex_malaysia_id_card_number&quot; /&gt;
            &lt;Match idRef=&quot;Keyword_malaysia_id_card_number&quot; /&gt;
        &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-100"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_malaysia_id_card_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MyKad</p>
<p>Identity Card</p>
<p>ID Card</p>
<p>Identification Card</p>
<p>Digital Application Card</p>
<p>Kad Akuan Diri</p>
<p>Kad Aplikasi Digital</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер гражданской службы для Нидерландов (BSN)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>8–9 цифр, содержащих необязательные пробелы.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>8–9 цифр:</p>
<ul>
<li><p>Три цифры</p></li>
<li><p>пробел (необязательно);</p></li>
<li><p>Три цифры</p></li>
<li><p>пробел (необязательно);</p></li>
<li><p>2–3 цифры.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_netherlands_bsn</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_netherlands_bsn</code>;</p></li>
<li><p>функция <code>Func_eu_date2</code> находит дату в правильном формате.</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Netherlands Citizen&#39;s Service (BSN) Number --&gt;
&lt;Entity id=&quot;c5f54253-ef7e-44f6-a578-440ed67e946d&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
       &lt;IdMatch idRef=&quot;Func_netherlands_bsn&quot; /&gt; 
       &lt;Match idRef=&quot;Keyword_netherlands_bsn&quot; /&gt; 
       &lt;Match idRef=&quot;Func_eu_date2&quot; /&gt; 
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-102"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_netherlands_bsn</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Citizen service number</p>
<p>BSN</p>
<p>Burgerservicenummer</p>
<p>Sofinummer</p>
<p>Persoonsgebonden nummer</p>
<p>Persoonsnummer</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер министерства здравоохранения для Новой Зеландии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Три буквы, пробел (необязательно) и четыре цифры.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Три буквы (без учета регистра), пробел (необязательно), четыре цифры.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_new_zealand_ministry_of_health_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_nz_terms</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- New Zealand Health Number --&gt;
&lt;Entity id=&quot;2b71c1c8-d14e-4430-82dc-fd1ed6bf05c7&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_new_zealand_ministry_of_health_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_nz_terms&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-104"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_nz_terms</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NHI</p>
<p>Новая Зеландия</p>
<p>Health</p>
<p>treatment</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Идентификационный номер для Норвегии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>11 разрядов</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>11 цифр:</p>
<ul>
<li><p>шесть цифр в формате ДДММГГ (дата рождения);</p></li>
<li><p>индивидуальный номер из трех цифр;</p></li>
<li><p>две проверочные цифры.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_norway_id_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_norway_id_number</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_norway_id_numbe</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Norway Identification Number --&gt;
&lt;Entity id=&quot;d4c8a798-e9f2-4bd3-9652-500d24080fc3&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_norway_id_number&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_norway_id_number&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_norway_id_number&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-106"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_norway_id_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Personal identification number</p>
<p>Norwegian ID Number</p>
<p>ID Number</p>
<p>Identification</p>
<p>Personnummer</p>
<p>Fødselsnummer</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Единый многофункциональный идентификационный номер для Филиппин


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>12 цифр, разделенных дефисами.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>12 цифр:</p>
<ul>
<li><p>Четыре цифры</p></li>
<li><p>дефис;</p></li>
<li><p>семь цифр;</p></li>
<li><p>дефис;</p></li>
<li><p>Одна цифра</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_philippines_unified_id</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_philippines_id</code>.</p></li>
</ul>
<pre><code>&lt;!-- Philippines Unified Multi-Purpose ID number --&gt;
&lt;Entity id=&quot;019b39dd-8c25-4765-91a3-d9c6baf3c3b3&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_philippines_unified_id&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_philippines_id&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-108"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_philippines_id</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Unified Multi-Purpose ID</p>
<p>UMID</p>
<p>Identity Card</p>
<p>Pinag-isang Multi-Layunin ID</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер удостоверения личности для Польши


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Три буквы и шесть цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Три буквы (без учета регистра), за которыми следуют шесть цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_polish_national_id</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_polish_national_id_passport_number</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Poland Identity Card--&gt;
&lt;Entity id=&quot;25E64989-ED5D-40CA-A939-6C14183BB7BF&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
      &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
          &lt;IdMatch idRef=&quot;Func_polish_national_id&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_polish_national_id_passport_number&quot; /&gt;
      &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-110"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_polish_national_id_passport_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nazwa i nr dowodu tożsamości</p>
<p>Dowód Tożsamości</p>
<p>dow. os.</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Национальный идентификатор (PESEL), Польша


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>11 разрядов</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>11 последовательных цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_pesel_identification_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_pesel_identification_number</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Poland National ID (PESEL) --&gt;      
&lt;Entity id=&quot;E3AAF206-4297-412F-9E06-BA8487E22456&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
      &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
          &lt;IdMatch idRef=&quot;Func_pesel_identification_number&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_pesel_identification_number&quot; /&gt;
      &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-112"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_pesel_identification_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nr PESEL</p>
<p>PESEL</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер паспорта для Польши


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Две буквы и семь цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Две буквы (без учета регистра), за которыми следуют семь цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_polish_passport_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_polish_national_id_passport_number</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Poland Passport Number --&gt;
&lt;Entity id=&quot;03937FB5-D2B6-4487-B61F-0F8BFF7C3517&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
      &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
          &lt;IdMatch idRef=&quot;Func_polish_passport_number&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_polish_national_id_passport_number&quot; /&gt;
      &lt;/Pattern&gt;
&lt;/Entity&gt;
&lt;/Version&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-114"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_polish_national_id_passport_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nazwa i nr dowodu tożsamości</p>
<p>Dowód Tożsamości</p>
<p>dow. os.</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер карты гражданина Португалии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Восемь цифр</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Восемь цифр</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_portugal_citizen_card</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_portugal_citizen_card</code>.</p></li>
</ul>
<pre><code>&lt;!-- Portugal Citizen Card Number --&gt;
&lt;Entity id=&quot;91a7ece2-add4-4986-9a15-c84544d81ecd&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_portugal_citizen_card&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_portugal_citizen_card&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-116"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_portugal_citizen_card</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Citizen Card</p>
<p>National ID Card</p>
<p>CC</p>
<p>Cartão de Cidadão</p>
<p>Bilhete de Identidade</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Национальный идентификатор для Саудовской Аравии


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10 последовательных цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_saudi_arabia_national_id</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_saudi_arabia_national_id</code>.</p></li>
</ul>
<pre><code>&lt;!-- Saudi Arabia National ID --&gt;
&lt;Entity id=&quot;8c5a0ba8-404a-41a3-8871-746aa21ee6c0&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_saudi_arabia_national_id&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_saudi_arabia_national_id&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-118"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_saudi_arabia_national_id</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Identification Card</p>
<p>I card number</p>
<p>ID number</p>
<p>الوطنية الهوية بطاقة رقم</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер внутреннего удостоверения личности гражданина Сингапура (NRIC)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Девять букв и цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Девять букв и цифр:</p>
<ul>
<li><p>буква &quot;F&quot;, &quot;G&quot;, &quot;S&quot; или &quot;T&quot; (без учета регистра);</p></li>
<li><p>семь цифр;</p></li>
<li><p>алфавитный проверочный символ.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_singapore_nric</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_singapore_nric</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_singapore_nric</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Singapore National Registration Identity Card (NRIC) Number --&gt;
&lt;Entity id=&quot;cead390a-dd83-4856-9751-fb6dc98c34da&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_singapore_nric&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_singapore_nric&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_singapore_nric&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-120"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_singapore_nric</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>National Registration Identity Card</p>
<p>Identity Card Number</p>
<p>NRIC</p>
<p>IC</p>
<p>Foreign Identification Number</p>
<p>FIN</p>
<p>身份证</p>
<p>身份證</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Идентификационный номер для Южной Африки


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>13 цифр, которые могут содержать пробелы.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>13 цифр:</p>
<ul>
<li><p>шесть цифр в формате ГГММДД (дата рождения);</p></li>
<li><p>Четыре цифры</p></li>
<li><p>индикатор гражданства в виде одной цифры;</p></li>
<li><p>цифра &quot;8&quot; или &quot;9&quot;;</p></li>
<li><p>одна цифра (проверочная).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_south_africa_identification_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_south_africa_identification_number</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- South Africa Identification Number --&gt;
&lt;Entity id=&quot;e2adf7cb-8ea6-4048-a2ed-d89eb65f2780&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_south_africa_identification_number&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_south_africa_identification_number&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-122"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_south_africa_identification_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Identity card</p>
<p>ID</p>
<p>Identification</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Регистрационный номер жителя Южной Кореи


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>13 цифр, содержащих дефис.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>13 цифр:</p>
<ul>
<li><p>шесть цифр в формате ГГММДД (дата рождения);</p></li>
<li><p>дефис;</p></li>
<li><p>одна цифра (определяет век и пол);</p></li>
<li><p>код региона рождения из четырех цифр;</p></li>
<li><p>одна цифра, используемая для разграничения людей, у которых предшествующие цифры совпадают;</p></li>
<li><p>проверочная цифра.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_south_korea_resident_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_south_korea_resident_number</code>;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_south_korea_resident_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- South Korea Resident Registration Number --&gt;
&lt;Entity id=&quot;5b802e18-ba80-44c4-bc83-bf2ad36ae36a&quot; recommendedConfidence=&quot;85&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_south_korea_resident_number&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_south_korea_resident_number&quot;/&gt;
  &lt;/Pattern&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Func_south_korea_resident_number&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-124"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_south_korea_resident_number</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>National ID card</p>
<p>Citizen's Registration Number</p>
<p>Jumin deungnok beonho</p>
<p>RRN</p>
<p>주민등록번호</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Страховой номер для Испании (SSN)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>11–12 цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>11–12 цифр</p>
<ul>
<li><p>Две цифры</p></li>
<li><p>Косая черта (необязательно)</p></li>
<li><p>7–8 цифр</p></li>
<li><p>Косая черта (необязательно)</p></li>
<li><p>Две цифры</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_spanish_social_security_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Spain SSN --&gt;
&lt;Entity id=&quot;5df987c0-8eae-4bce-ace7-b316347f3070&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_spanish_social_security_number&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><p>Нет</p></td>
</tr>
</tbody>
</table>


## Национальный идентификатор для Швеции


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10 или 12 цифр и дополнительный разделитель.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10 или 12 цифр с необязательным разделителем</p>
<ul>
<li><p>2–4 цифры (необязательно)</p></li>
<li><p>Шесть цифр в формате даты ГГММДД.</p></li>
<li><p>Разделитель - или + (необязательно)</p></li>
<li><p>Четыре цифры</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_swedish_national_identifier</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Sweden National ID --&gt;
&lt;Entity id=&quot;f69aaf40-79be-4fac-8f05-fd1910d272c8&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_swedish_national_identifier&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><p>Нет</p></td>
</tr>
</tbody>
</table>


## Номер паспорта гражданина Швеции


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Восемь цифр</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Восемь последовательных цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет.</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Регулярное выражение <code>Regex_sweden_passport_number</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Верно одно из условий ниже:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_passport</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_sweden_passport</code>.</p></li>
</ul></li>
</ul>
<pre><code>&lt;!-- Sweden Passport Number --&gt;
&lt;Entity id=&quot;ba4e7456-55a9-4d89-9140-c33673553526&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_sweden_passport_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_passport&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_sweden_passport&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-128"> </h3>
<div>
<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_sweden_passport</p></th>
<th> </th>
<th><p>Keyword_passport</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>visa requirements</p>
<p>Alien Registration Card</p>
<p>Schengen visas</p>
<p>Schengen visa</p>
<p>Visa Processing</p>
<p>Visa Type</p>
<p>Single Entry</p>
<p>Multiple Entry</p>
<p>G3 Processing Fees</p></td>
<td> </td>
<td><p>Passport Number</p>
<p>Passport No</p>
<p>Passport#</p>
<p>Passport#</p>
<p>PassportID</p>
<p>Passportno</p>
<p>passportnumber</p>
<p>パスポート</p>
<p>パスポート番号</p>
<p>パスポートのNum</p>
<p>パスポート＃</p>
<p>Numéro de passeport</p>
<p>Passeport n °</p>
<p>Passeport Non</p>
<p>Passeport#</p>
<p>Passeport#</p>
<p>PasseportNon</p>
<p>Passeportn °</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Код SWIFT


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Четыре буквы, за которыми следуют от 5 до 31 буквы или цифры.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Четыре буквы, за которыми следуют от 5 до 31 буквы или цифры</p>
<ul>
<li><p>Четырехбуквенный код банка (без учета регистра)</p></li>
<li><p>Необязательный пробел</p></li>
<li><p>4–28 букв или цифр (основной номер банковского счета, BBAN)</p></li>
<li><p>Необязательный пробел</p></li>
<li><p>1–3 буквы или цифры (оставшаяся часть BBAN)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_swift</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_swift</code>.</p></li>
</ul>
<pre><code>&lt;Entity id=&quot;cb2ab58c-9cb8-4c81-baf8-a4e106791df4&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
&lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_swift&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_swift&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-130"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_swift</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>international organization for standardization 9362</p>
<p>iso 9362</p>
<p>iso9362</p>
<p>swift#</p>
<p>swiftcode</p>
<p>swiftnumber</p>
<p>swiftroutingnumber</p>
<p>swift code</p>
<p>swift number #</p>
<p>swift routing number</p>
<p>bic number</p>
<p>bic code</p>
<p>bic#</p>
<p>bic#</p>
<p>bank identifier code</p>
<p>標準化9362</p>
<p>迅速＃</p>
<p>SWIFTコード</p>
<p>SWIFT番号</p>
<p>迅速なルーティング番号</p>
<p>BIC番号</p>
<p>BICコード</p>
<p>銀行識別コードのための国際組織</p>
<p>Organisation internationale de normalisation 9362</p>
<p>rapide #</p>
<p>code SWIFT</p>
<p>le numéro de swift</p>
<p>swift numéro d'acheminement</p>
<p>le numéro BIC</p>
<p># BIC</p>
<p>code identificateur de banque</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Национальный идентификатор, Тайвань


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Одна буква (английская), за которой следуют девять цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Один символ , за которым следуют девять цифр</p>
<ul>
<li><p>Один символ (на английском языке, без учета регистра)</p></li>
<li><p>Цифра 1 или 2</p></li>
<li><p>восемь цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_taiwanese_national_id</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_taiwanese_national_id</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- Taiwanese National ID --&gt;
&lt;Entity id=&quot;4C7BFC34-8DD1-421D-8FB7-6C6182C2AF03&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
      &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
          &lt;IdMatch idRef=&quot;Func_taiwanese_national_id&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_taiwanese_national_id&quot; /&gt;
      &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-132"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_taiwanese_national_id</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>身份證字號</p>
<p>身份證</p>
<p>身份證號碼</p>
<p>身份證號</p>
<p>身分證字號</p>
<p>身分證</p>
<p>身分證號碼</p>
<p>身份證號</p>
<p>身分證統一編號</p>
<p>國民身分證統一編號</p>
<p>簽名</p>
<p>蓋章</p>
<p>簽名或蓋章</p>
<p>簽章</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер паспорта гражданина Тайваня


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Номер биометрического паспорта:</p>
<dl>
<dt><span></span></dt>
<dd><p>девять цифр.</p>
</dd>
</dl>
<p>Номер обычного паспорта:</p>
<dl>
<dt><span></span></dt>
<dd><p>девять цифр.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Номер биометрического паспорта:</p>
<ul>
<li><p>цифра &quot;3&quot;;</p></li>
<li><p>восемь цифр.</p></li>
</ul>
<p>Номер обычного паспорта:</p>
<ul>
<li><p>девять цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_taiwan_passport</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_taiwan_passport</code>.</p></li>
</ul>
<pre><code>&lt;!-- Taiwan Passport Number --&gt;
&lt;Entity id=&quot;e7251cb4-4c2c-41df-963e-924eb3dae04a&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_taiwan_passport&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_taiwan_passport&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-134"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_taiwan_passport</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ROC passport number</p>
<p>Passport number</p>
<p>Passport no</p>
<p>Passport Num</p>
<p>Passport #</p>
<p>护照</p>
<p>中華民國護照</p>
<p>Zhōnghuá Mínguó hùzhào</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер удостоверения жителя Тайваня (ARC/TARC)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10 букв и цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10 букв и цифр:</p>
<ul>
<li><p>две буквы (без учета регистра);</p></li>
<li><p>восемь цифр.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_taiwan_resident_certificate</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_taiwan_resident_certificate</code>.</p></li>
</ul>
<pre><code>&lt;!-- Taiwan Resident Certificate (ARC/TARC) --&gt;
&lt;Entity id=&quot;48269fec-05ea-46ea-b326-f5623a58c6e9&quot; recommendedConfidence=&quot;75&quot; patternsProximity=&quot;300&quot;&gt;
  &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
     &lt;IdMatch idRef=&quot;Regex_taiwan_resident_certificate&quot;/&gt;
     &lt;Match idRef=&quot;Keyword_taiwan_resident_certificate&quot;/&gt;
  &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-136"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_taiwan_resident_certificate</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Resident Certificate</p>
<p>Resident Cert</p>
<p>Resident Cert.</p>
<p>Identification card</p>
<p>Alien Resident Certificate</p>
<p>ARC</p>
<p>Taiwan Area Resident Certificate</p>
<p>TARC</p>
<p>居留證</p>
<p>外僑居留證</p>
<p>台灣地區居留證</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер водительского удостоверения для Соединенного Королевства


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Сочетание 18 букв и цифр в указанном формате.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>18 букв и цифр</p>
<ul>
<li><p>Пять букв (без учета регистра) или цифра 9 вместо буквы</p></li>
<li><p>Одна цифра</p></li>
<li><p>Пять цифр в формате даты ДДММГ, представляющие собой дату рождения</p></li>
<li><p>Две буквы (без учета регистра) или цифра 9 вместо буквы</p></li>
<li><p>Пять цифр</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_uk_drivers_license</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_uk_drivers_license</code>;</p></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- U.K. Driver&#39;s License Number --&gt;
&lt;Entity id=&quot;f93de4be-d94c-40df-a8be-461738047551&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_uk_drivers_license&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_uk_drivers_license&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-138"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_uk_drivers_license</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DVLA</p>
<p>light vans</p>
<p>quadbikes</p>
<p>motor cars</p>
<p>125cc</p>
<p>sidecar</p>
<p>tricycles</p>
<p>motorcycles</p>
<p>photocard licence</p>
<p>learner drivers</p>
<p>licence holder</p>
<p>licence holders</p>
<p>driving licences</p>
<p>driving licence</p>
<p>dual control car</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Регистрационный номер избирателя для Соединенного Королевства


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Две буквы, за которыми следуют 1–4 цифры.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Две буквы (без учета регистра), за которыми следуют 1–4 цифры.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_uk_electoral</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_uk_electoral</code>.</p></li>
</ul>
<pre><code>&lt;!-- U.K. Electoral Number --&gt;
&lt;Entity id=&quot;a3eea206-dc0c-4f06-9e22-aa1be3059963&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_uk_electoral&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_uk_electoral&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-140"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_uk_electoral</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>council nomination</p>
<p>nomination form</p>
<p>electoral register</p>
<p>electoral roll</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер национальной службы здравоохранения для Соединенного Королевства


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>10–17 цифр, разделенных пробелами.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>10-17 цифр</p>
<ul>
<li><p>3 или 10 цифр</p></li>
<li><p>Пробел</p></li>
<li><p>Три цифры</p></li>
<li><p>Пробел</p></li>
<li><p>Четыре цифры</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_uk_nhs_number</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Верно одно из условий ниже:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_uk_nhs_number</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_uk_nhs_number1</code>;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_uk_nhs_number_dob</code>.</p></li>
</ul></li>
<li><p>Контрольная сумма проходит проверку.</p></li>
</ul>
<pre><code>&lt;!-- U.K. NHS Number --&gt;
&lt;Entity id=&quot;3192014e-2a16-44e9-aa69-4b20375c9a78&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;85&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_uk_nhs_number&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_uk_nhs_number&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_uk_nhs_number1&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_uk_nhs_number_dob&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-142"> </h3>
<div>
<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_uk_nhs_number</p></th>
<th> </th>
<th><p>Keyword_uk_nhs_number1</p></th>
<th><p>Keyword_uk_nhs_number_dob</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>national health service</p>
<p>nhs</p>
<p>health services authority</p>
<p>health authority</p></td>
<td> </td>
<td><p>patient id</p>
<p>patient identification</p>
<p>patient no</p>
<p>patient number</p></td>
<td><p>GP</p>
<p>DOB</p>
<p>D.O.B</p>
<p>Date of Birth</p>
<p>Birth Date</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер карты национального страхования для Соединенного Королевства (NINO)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>7 или 9 символы, разделенных пробелами или тире</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Два возможных шаблонов:</p>
<ul>
<li><p>Две буквы (допустимый NINOs использовать только определенных символов в этом префикс, который проверяет этот шаблон; без учета регистра)</p></li>
<li><p>Шесть цифр</p></li>
<li><p>Либо 'A', 'B', 'C', или имелся &quot;(только для определенных символов в допускаются суффикс; не учитывают регистр, как префикс)</p></li>
</ul>
<p>ИЛИ</p>
<ul>
<li><p>Два букв</p></li>
<li><p>Пробел или тире</p></li>
<li><p>Две цифры</p></li>
<li><p>Пробел или тире</p></li>
<li><p>Две цифры</p></li>
<li><p>Пробел или тире</p></li>
<li><p>Две цифры</p></li>
<li><p>Пробел или тире</p></li>
<li><p>Либо '', 'B', 'C', или имелся &quot;</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_uk_nino</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_uk_nino</code>.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_uk_nino</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>ни одно ключевое слово из <code>Keyword_uk_nino</code> не находится.</p></li>
</ul>
<pre><code>&lt;!-- U.K. NINO --&gt;
&lt;Entity id=&quot;16c07343-c26f-49d2-a987-3daf717e94cc&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_uk_nino&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_uk_nino&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;    
     &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_uk_nino&quot; /&gt;
        &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
          &lt;Match idRef=&quot;Keyword_uk_nino&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-144"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_uk_nino</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>national insurance number</p>
<p>national insurance contributions</p>
<p>protection act</p>
<p>insurance</p>
<p>social security number</p>
<p>insurance application</p>
<p>medical application</p>
<p>social insurance</p>
<p>medical attention</p>
<p>social security</p>
<p>great britain</p>
<p>insurance</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер паспорта гражданина США и/или Соединенного Королевства


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Девять цифр.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Девять последовательных цифр.</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_usa_uk_passport</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_passport</code>.</p></li>
</ul>
<pre><code>&lt;Entity id=&quot;178ec42a-18b4-47cc-85c7-d62c92fd67f8&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_usa_uk_passport&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_passport&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-146"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_passport</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Passport Number</p>
<p>Passport No</p>
<p>Passport#</p>
<p>Passport#</p>
<p>PassportID</p>
<p>Passportno</p>
<p>passportnumber</p>
<p>パスポート</p>
<p>パスポート番号</p>
<p>パスポートのNum</p>
<p>パスポート＃</p>
<p>Numéro de passeport</p>
<p>Passeport n °</p>
<p>Passeport Non</p>
<p>Passeport#</p>
<p>Passeport#</p>
<p>PasseportNon</p>
<p>Passeportn °</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер банковского счета для США


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>8-17 цифр</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>8–17 последовательных цифр</p></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>регулярное выражение <code>Regex_usa_bank_account_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_usa_Bank_Account</code>.</p></li>
</ul>
<pre><code>&lt;!-- U.S. Bank Account Number --&gt;
&lt;Entity id=&quot;a2ce32a8-f935-4bb6-8e96-2a5157672e2c&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Regex_usa_bank_account_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_usa_Bank_Account&quot; /&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-148"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_usa_Bank_Account</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Checking Account Number</p>
<p>Checking Account</p>
<p>Checking Account #</p>
<p>Checking Acct Number</p>
<p>Checking Acct #</p>
<p>Checking Acct No.</p>
<p>Checking Account No.</p>
<p>Bank Account Number</p>
<p>Bank Account #</p>
<p>Bank Acct Number</p>
<p>Bank Acct #</p>
<p>Bank Acct No.</p>
<p>Bank Account No.</p>
<p>Savings Account Number</p>
<p>Savings Account.</p>
<p>Savings Account #</p>
<p>Savings Acct Number</p>
<p>Savings Acct #</p>
<p>Savings Acct No.</p>
<p>Savings Account No.</p>
<p>Debit Account Number</p>
<p>Debit Account</p>
<p>Debit Account #</p>
<p>Debit Acct Number</p>
<p>Debit Acct #</p>
<p>Debit Acct No.</p>
<p>Debit Account No.</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Номер водительского удостоверения для США


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Зависит от штата.</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>В зависимости от штата. Например, для Нью-Йорка:</p>
<ul>
<li><p>Подойдут девять цифр в формате ццц ццц ццц.</p></li>
<li><p>Не подойдут девять цифр в формате ццццццццц.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_new_york_drivers_license_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_[state_name]_drivers_license_name</code>;</p></li>
<li><p>обнаружено ключевое слово из списка <code>Keyword_us_drivers_license</code>.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 65 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>функция <code>Func_new_york_drivers_license_number</code> находит содержимое, которое соответствует шаблону;</p></li>
<li><p>находится ключевое слово из <code>Keyword_[state_name]_drivers_license_name</code>;</p></li>
<li><p>находится ключевое слово из <code>Keyword_us_drivers_license_abbreviations</code>;</p></li>
<li><p>ни одно ключевое слово из <code>Keyword_us_drivers_license</code> не находится.</p></li>
</ul>
<pre><code>    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_new_york_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_new_york_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_us_drivers_license&quot; /&gt;
    &lt;/Pattern&gt;
    &lt;Pattern confidenceLevel=&quot;65&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_new_york_drivers_license_number&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_new_york_drivers_license_name&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_us_drivers_license_abbreviations&quot; /&gt;
        &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
          &lt;Match idRef=&quot;Keyword_us_drivers_license&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-150"> </h3>
<div>
<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_us_drivers_license_abbreviations</p></th>
<th> </th>
<th><p>Keyword_us_drivers_license</p></th>
<th><p>Keyword_[state_name]_drivers_license_name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DL</p>
<p>DLS</p>
<p>CDL</p>
<p>CDLS</p>
<p>ID</p>
<p>IDs</p>
<p>DL#</p>
<p>DLS#</p>
<p>CDL#</p>
<p>CDLS#</p>
<p>ID#</p>
<p>IDs#</p>
<p>ID number</p>
<p>ID numbers</p>
<p>LIC</p>
<p>LIC#</p></td>
<td> </td>
<td><p>DriverLic</p>
<p>DriverLics</p>
<p>DriverLicense</p>
<p>DriverLicenses</p>
<p>Driver Lic</p>
<p>Driver Lics</p>
<p>Driver License</p>
<p>Driver Licenses</p>
<p>DriversLic</p>
<p>DriversLics</p>
<p>DriversLicense</p>
<p>DriversLicenses</p>
<p>Drivers Lic</p>
<p>Drivers Lics</p>
<p>Drivers License</p>
<p>Drivers Licenses</p>
<p>Driver' Lic</p>
<p>Driver' Lics</p>
<p>Driver' License</p>
<p>Driver' Licenses</p>
<p>Driver' Lic</p>
<p>Driver' Lics</p>
<p>Driver' License</p>
<p>Driver' Licenses</p>
<p>Driver'sLic</p>
<p>Driver'sLics</p>
<p>Driver'sLicense</p>
<p>Driver'sLicenses</p>
<p>Driver's Lic</p>
<p>Driver's Lics</p>
<p>Driver's License</p>
<p>Driver's Licenses</p>
<p>identification number</p>
<p>identification numbers</p>
<p>identification #</p>
<p>id card</p>
<p>id cards</p>
<p>identification card</p>
<p>identification cards</p>
<p>DriverLic#</p>
<p>DriverLics#</p>
<p>DriverLicense#</p>
<p>DriverLicenses#</p>
<p>Driver Lic#</p>
<p>Driver Lics#</p>
<p>Driver License#</p>
<p>Driver Licenses#</p>
<p>DriversLic#</p>
<p>DriversLics#</p>
<p>DriversLicense#</p>
<p>DriversLicenses#</p>
<p>Drivers Lic#</p>
<p>Drivers Lics#</p>
<p>Drivers License#</p>
<p>Drivers Licenses#</p>
<p>Driver' Lic#</p>
<p>Driver' Lics#</p>
<p>Driver' License#</p>
<p>Driver' Licenses#</p>
<p>Driver' Lic#</p>
<p>Driver' Lics#</p>
<p>Driver' License#</p>
<p>Driver' Licenses#</p>
<p>Driver'sLic#</p>
<p>Driver'sLics#</p>
<p>Driver'sLicense#</p>
<p>Driver'sLicenses#</p>
<p>Driver's Lic#</p>
<p>Driver's Lics#</p>
<p>Driver's License#</p>
<p>Driver's Licenses#</p>
<p>id card#</p>
<p>id cards#</p>
<p>identification card#</p>
<p>identification cards#</p></td>
<td><p>Аббревиатура штата (например, NY)</p>
<p>Название штата (например, New York)</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Идентификационный номер налогоплательщика для США (ITIN)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>Девять цифр, которые начинаются с &quot;9&quot; и содержат &quot;7&quot; или &quot;8&quot; в качестве четвертой цифры, отформатированных с помощью пробелов или тире (необязательно).</p></td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>С форматированием</p>
<ul>
<li><p>Цифра 9</p></li>
<li><p>Две цифры</p></li>
<li><p>Пробел или тире</p></li>
<li><p>Цифра 7 или 8</p></li>
<li><p>Одна цифра</p></li>
<li><p>Пробел или тире</p></li>
<li><p>Четыре цифры</p></li>
</ul>
<p>Без форматирования</p>
<ul>
<li><p>Цифра 9</p></li>
<li><p>Две цифры</p></li>
<li><p>Цифра 7 или 8</p></li>
<li><p>Пять цифр</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_formatted_itin</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Верно по меньшей мере одно из условий ниже:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_itin</code>;</p></li>
<li><p>функция <code>Func_us_address</code> находит адрес в правильном формате;</p></li>
<li><p>функция <code>Func_us_date</code> находит дату в правильном формате;</p></li>
<li><p>найдено ключевое слово из <code>Keyword_itin_collaborative</code>.</p></li>
</ul></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_unformatted_itin</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Верно по меньшей мере одно из условий ниже:</p>
<ul>
<li><p>найдено ключевое слово из <code>Keyword_itin_collaborative</code>;</p></li>
<li><p>функция <code>Func_us_address</code> находит адрес в правильном формате;</p></li>
<li><p>функция <code>Func_us_date</code> находит дату в правильном формате.</p></li>
</ul></li>
</ul>
<pre><code>&lt;!-- U.S. Individual Taxpayer Identification Number (ITIN) --&gt;
&lt;Entity id=&quot;e55e2a32-f92d-4985-a35d-a0b269eb687b&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
    &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_formatted_itin&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_itin&quot; /&gt;
          &lt;Match idRef=&quot;Func_us_address&quot; /&gt;
          &lt;Match idRef=&quot;Func_us_date&quot; /&gt;
          &lt;Match idRef=&quot;Keyword_itin_collaborative&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
    &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_unformatted_itin&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_itin&quot; /&gt;
        &lt;Any minMatches=&quot;1&quot;&gt;
          &lt;Match idRef=&quot;Keyword_itin_collaborative&quot; /&gt;
          &lt;Match idRef=&quot;Func_us_address&quot; /&gt;
          &lt;Match idRef=&quot;Func_us_date&quot; /&gt;
        &lt;/Any&gt;
    &lt;/Pattern&gt;
&lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-152"> </h3>
<div>
<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_itin</p></th>
<th> </th>
<th><p>Keyword_itin_collaborative</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>taxpayer</p>
<p>tax id</p>
<p>tax identification</p>
<p>itin</p>
<p>ssn</p>
<p>tin</p>
<p>social security</p>
<p>tax payer</p>
<p>itins</p>
<p>taxid</p>
<p>individual taxpayer</p></td>
<td> </td>
<td><p>License</p>
<p>DL</p>
<p>DOB</p>
<p>Birthdate</p>
<p>Birthday</p>
<p>Date of Birth</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Страховой номер для США (SSN)


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Формат</p></td>
<td><p>9 цифр в виде форматированного или неформатированного шаблона.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Есть SSN выдан до середины 2011 г., он отличается строгим форматированием, при котором определенные части номера должны входить в указанные диапазоны (при этом нет контрольной суммы).</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="even">
<td><p>Шаблон</p></td>
<td><p>Четыре функции выполняют поиск SSN с использованием четырех разных шаблонов:</p>
<ul>
<li><p><code>Func_ssn</code> находит SSN со строгим форматированием с тире или пробелами, выданные до 2011 г. (ццц-цц-цццц ИЛИ ццц цц цццц);</p></li>
<li><p><code>Func_unformatted_ssn</code> находит SSN со строгим форматированием, выданные до 2011 г. (без форматирования в виде девяти последовательных цифр — ццццццццц);</p></li>
<li><p><code>Func_randomized_formatted_ssn</code> находит SSN с тире или пробелами, выданные после 2011 г. (ццц-цц-цццц ИЛИ ццц цц цццц);</p></li>
<li><p><code>Func_randomized_unformatted_ssn</code> находит SSN без форматирования в виде девяти последовательных цифр, выданные после 2011 г. (ццццццццц).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Контрольная сумма</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Определение</p></td>
<td><p>Политика защиты от потери данных с вероятностью в 85 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_ssn</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Находится ключевое слово из <code>Keyword_ssn</code>.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 75 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, не отдаленном более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_unformatted_ssn</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Находится ключевое слово из <code>Keyword_ssn</code>.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 65 % верно обнаруживает этот тип конфиденциальной информации, если в расположении, отдаленном не более чем на 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_randomized_formatted_ssn</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Находится ключевое слово из <code>Keyword_ssn</code>.</p></li>
<li><p>Функция <code>Func_ssn</code> не находит содержимое, которое соответствует шаблону.</p></li>
</ul>
<p>Политика защиты от потери данных с вероятностью в 55 % верно обнаружила этот тип конфиденциальной информации, если в пределах ближайших 300 знаков:</p>
<ul>
<li><p>Функция <code>Func_randomized_unformatted_ssn</code> находит содержимое, которое соответствует шаблону.</p></li>
<li><p>Находится ключевое слово из <code>Keyword_ssn</code>.</p></li>
<li><p>Функция <code>Func_unformatted_ssn</code> не находит содержимое, которое соответствует шаблону.</p></li>
</ul>
<pre><code> &lt;!-- U.S. Social Security Number (SSN) --&gt;
    &lt;Entity id=&quot;a44669fe-0d48-453d-a9b1-2cc83f2cba77&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;
      &lt;Pattern confidenceLevel=&quot;85&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_ssn&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_ssn&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;75&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_unformatted_ssn&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_ssn&quot; /&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;65&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_randomized_formatted_ssn&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_ssn&quot; /&gt;
        &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
          &lt;Match idRef=&quot;Func_ssn&quot; /&gt;
        &lt;/Any&gt;
      &lt;/Pattern&gt;
      &lt;Pattern confidenceLevel=&quot;55&quot;&gt;
        &lt;IdMatch idRef=&quot;Func_randomized_unformatted_ssn&quot; /&gt;
        &lt;Match idRef=&quot;Keyword_ssn&quot; /&gt;
        &lt;Any minMatches=&quot;0&quot; maxMatches=&quot;0&quot;&gt;
          &lt;Match idRef=&quot;Func_unformatted_ssn&quot; /&gt;
        &lt;/Any&gt;
      &lt;/Pattern&gt;
    &lt;/Entity&gt;</code></pre></td>
</tr>
<tr class="odd">
<td><p>Ключевые слова</p></td>
<td><h3 id="section-154"> </h3>
<div>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Keyword_ssn</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Social Security</p>
<p>Social Security#</p>
<p>Soc Sec</p>
<p>SSN</p>
<p>SSNS</p>
<p>SSN#</p>
<p>SS#</p>
<p>SSID</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>

