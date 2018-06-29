﻿---
title: 'Выключение доступа к Центру администрирования Exchange: Exchange 2013 Help'
TOCTitle: Выключение доступа к Центру администрирования Exchange
ms:assetid: 49f4fa77-1722-4703-81c9-8724ae0334fb
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ218639(v=EXCHG.150)
ms:contentKeyID: 50487988
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Выключение доступа к Центру администрирования Exchange

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2013-05-20_

В целях обеспечения безопасности некоторым организациям может потребоваться ограничить доступ к Центру администрирования Exchange для пользователей из Интернета. В этой процедуре описывается, как отключить доступ к Центру администрирования Exchange. Эта процедура не запрещает пользователям доступ к параметрам в Outlook Web App.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>С помощью этой процедуры можно полностью отключить доступ администратора Центра администрирования Exchange на сервере клиентского доступа. Если необходимо дать внутренним пользователям права администратора Центра администрирования Exchange, необходимо установить отдельный сервер клиентского доступа и настроить его так, чтобы он обрабатывал только внутренние запросы. Для этого выполните следующую команду.<br />
<code>Set-ECPVirtualDirectory -Identity &quot;InternalCAS\ecp (default web site)&quot; -AdminEnabled $True</code></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.Caution(EXCHG.150).gif" title="Внимание!" alt="Внимание!" />Внимание!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Эта процедура применима только к локальным развертываниям Exchange Server 2013.</td>
</tr>
</tbody>
</table>


## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Подключение к Центру администрирования Exchange" в разделе [Разрешения инфраструктуры Exchange и командной консоли](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Выполнение этой процедуры с помощью консоли администрирования Exchange невозможно. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Выключение доступа к Центру администрирования Exchange из Интернета с помощью командной консоли

В этом примере показано, как выключить доступ к Центру администрирования Exchange на сервере CAS01.

    Set-ECPVirtualDirectory -Identity "CAS01\ecp (default web site)" -AdminEnabled $false

Подробные сведения о синтаксисе и параметрах см. в разделе [Set-EcpVirtualDirectory](https://technet.microsoft.com/ru-ru/library/dd297991\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно выключили доступ к Центру администрирования Exchange, выполните следующие действия.

1.  В веб-браузере введите внутренний или внешний URL-адрес, используемый в вашей организации для доступа к Outlook Web App, но замените идентификатор **/owa** на **/ecp**. Например, если внешний URL-адрес для доступа к Outlook Web App имеет вид https://primary.tailspintoys.com/owa, введите https://primary/tailspintoys.com/ecp.

2.  Если доступ отключен, вы получите ошибку **404 — веб-сайт не найден**.

