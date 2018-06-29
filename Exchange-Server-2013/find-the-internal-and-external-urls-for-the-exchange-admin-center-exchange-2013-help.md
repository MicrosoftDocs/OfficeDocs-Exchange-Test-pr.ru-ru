---
title: 'Поиск внутренних и внешних URL-адресов для Центра администрирования Exchange: Exchange 2013 Help'
TOCTitle: Поиск внутренних и внешних URL-адресов для Центра администрирования Exchange
ms:assetid: 3ddb30ff-a405-4b9d-8d77-2d7a3a5ab8fa
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ680108(v=EXCHG.150)
ms:contentKeyID: 50487864
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Поиск внутренних и внешних URL-адресов для Центра администрирования Exchange

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2013-02-04_

Так как Центр администрирования Exchange в Exchange Server 2013 — это веб-консоль управления, для доступа к нему нужно ввести в веб-браузере URL-адрес виртуального каталога ECP. В этом разделе описывается, как найти этот URL-адрес.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Панель управления Exchange (ECP) — это веб-интерфейс пользователя, разработанный для Exchange Server 2010. В именах командлетов Центра администрирования Exchange, предназначенных для работы с виртуальными каталогами, по-прежнему используется слово &quot;ECP&quot;. С их помощью можно управлять виртуальными каталогами ECP Exchange 2010 и Exchange 2013.</td>
</tr>
</tbody>
</table>


Дополнительные сведения о Центре администрирования Exchange см. в разделе [Центр администрирования Exchange в Exchange 2013](exchange-admin-center-in-exchange-2013-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 5 минут.

  - Выполнение этой процедуры с помощью консоли администрирования Exchange невозможно. Необходимо использовать командную консоль.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Подключение Exchange Administration Center" в разделе [Разрешения инфраструктуры Exchange и командной консоли](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

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


## Определение внутреннего и внешнего URL-адресов для виртуального каталога ECP с помощью командной консоли

В этом примере возвращаются имя, внутренний URL-адрес и внешний URL-адрес виртуального каталога ECP в виде форматированного списка.

    Get-ECPVirtualDirectory | Format-List Name,InternalURL,ExternalURL

Чтобы запустить Центр администрирования Exchange, введите в адресной строке браузера возвращенное значение *InternalURL* или *ExternalURL*.

Подробные сведения о синтаксисе и параметрах см. в разделе [Get-EcpVirtualDirectory](https://technet.microsoft.com/ru-ru/library/dd351058\(v=exchg.150\)).

