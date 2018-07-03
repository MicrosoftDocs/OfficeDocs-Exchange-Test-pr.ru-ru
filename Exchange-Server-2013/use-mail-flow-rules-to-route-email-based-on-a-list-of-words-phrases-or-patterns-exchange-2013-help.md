﻿---
title: 'Использование правил обработки почтового потока для маршрутизации электронной почты с учетом списка слов, фраз или шаблонов: Exchange 2013 Help'
TOCTitle: Использование правил обработки почтового потока для маршрутизации электронной почты с учетом списка слов, фраз или шаблонов
ms:assetid: 4c5bee1b-58b5-4152-baef-86fa103050ae
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn951131(v=EXCHG.150)
ms:contentKeyID: 65236542
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Использование правил обработки почтового потока для маршрутизации электронной почты с учетом списка слов, фраз или шаблонов

 

_**Применимо к:** Exchange Online, Exchange Online Protection, Exchange Server 2013_

_**Последнее изменение раздела:** 2017-10-30_

Чтобы пользователи не нарушали политики организации, касающиеся электронной почты, можно использовать правила транспорта Exchange. Так вы определите способ маршрутизации электронной почты, содержащей определенные слова или шаблоны. Короткий список слов или фраз можно создать в Центре администрирования Exchange. В случае более длинного списка можно использовать модуль Exchange для Оболочка Windows PowerShell, чтобы список считывался из текстового файла.

  - Пример 1. Использование короткого списка недопустимых слов

  - Пример 2. Использование длинного списка недопустимых слов

Если организация использует защиту от потери данных, дополнительные возможности определения и маршрутизации электронной почты, содержащей конфиденциальную информацию, см. в статье [Защита от потери данных](technical-overview-of-dlp-data-loss-prevention-in-exchange.md).

## Пример 1. Использование короткого списка недопустимых слов

Если список слов или фраз короткий, можно создать правило в Центре администрирования Exchange. Например, чтобы не допустить отправку сообщений, содержащих непристойные слова или опечатки в названии компании, определенных аббревиатурах или названиях продуктов, можно создать правило для блокировки сообщения и уведомления об этом отправителя. Обратите внимание, что в словах, фразах и шаблонах регистр не учитывается.

В этом примере показаны заблокированные сообщения с типовыми опечатками.

![Правило, блокирующее сообщения на основе текстовых шаблонов](images/Dn951131.a8489cbb-be59-4890-ae30-1431703eeb88(EXCHG.150).png "Правило, блокирующее сообщения на основе текстовых шаблонов")

## Пример 2. Использование длинного списка недопустимых слов

Если список слов, фраз или шаблонов длинный, их можно занести в текстовый файл, написав каждое слово, фразу или шаблон с новой строки. Используйте модуль Exchange для Оболочка Windows PowerShell, чтобы передать список ключевых слов в переменную, создать правило транспорта и назначить переменную с ключевыми словами для условия этого правила. Например, в приведенном ниже скрипте используется список опечаток из файла misspelled\_companyname.txt.

    $keywords=Import-Content  .\misspelled_companyname.txt
    New-TransportRule -Name "Block messages with unacceptable words" -SubjectOrBodyContainsWords $keywords -SentToScope "NotInOrganization" -RejectMessageReasonText "Do not use internal acronyms, product names, or misspellings in external communications."

## Использование фраз и шаблонов в текстовом файле

Текстовый файл может содержать регулярные выражения для шаблонов, в которых не учитывается регистр. К наиболее распространенным регулярным выражениям относятся


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Выражение</strong></p></td>
<td><p><strong>Совпадения</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>.</strong></p></td>
<td><p>Любой символ</p></td>
</tr>
<tr class="odd">
<td><p><strong>*</strong></p></td>
<td><p>Все дополнительные символы</p></td>
</tr>
<tr class="even">
<td><p><strong>\d</strong></p></td>
<td><p>Любое десятичное число</p></td>
</tr>
<tr class="odd">
<td><p>[<em>группа_символов</em>]</p></td>
<td><p>Любой символ из <em>группы_символов</em>.</p></td>
</tr>
</tbody>
</table>


Например, этот текстовый файл содержит распространенные опечатки в названии Майкрософт.

    [mn]sft
    [mn]icrosft
    [mn]icro soft
    [mn].crosoft

Сведения о том, как указывать шаблоны с использованием регулярных выражений, см. в статье [Справочник по регулярным выражениям](https://go.microsoft.com/fwlink/p/?linkid=532394).
