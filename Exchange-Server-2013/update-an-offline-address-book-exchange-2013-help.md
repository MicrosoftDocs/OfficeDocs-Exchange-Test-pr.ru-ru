---
title: 'Обновление автономной адресной книги: Exchange 2013 Help'
TOCTitle: Обновление автономной адресной книги
ms:assetid: 448a207e-41b4-4cef-9fe9-a68b81e2ec4e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa997684(v=EXCHG.150)
ms:contentKeyID: 50487958
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Обновление автономной адресной книги

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2013-11-15_

После создания автономной адресной книги или изменения ее параметров внесенные изменения не будут доступны пользователям, пока не завершится процесс формирования автономной адресной книги.

Дополнительные задачи управления, связанные с автономными адресными книгами (OAB), см. в разделе [Процедуры автономной адресной книги](offline-address-book-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Автономные адресные книги" в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Невозможно использовать Центр администрирования Exchange (EAC) для выполнения этой процедуры. Необходимо использовать командную консоль.

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


## Создание автономной адресной книги с помощью командной консоли

В этом примере "Автономная адресная книга" обновляется на "Моя автономная адресная книга".

    Update-OfflineAddressBook -Identity "My OAB"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Update-OfflineAddressBook](https://technet.microsoft.com/ru-ru/library/aa995979\(v=exchg.150\)).

