---
title: 'Обновление глобального списка адресов: Exchange 2013 Help'
TOCTitle: Обновление глобального списка адресов
ms:assetid: 236e8530-62dd-4c43-8a5d-8465623252e6
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb266966(v=EXCHG.150)
ms:contentKeyID: 50487613
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Обновление глобального списка адресов

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2014-12-16_

Для обновления глобального списка адресов можно использовать командную консоль. Глобальный список адресов — это каталог, содержащий записи для всех групп, пользователей и контактов в рамках реализации Майкрософт Exchange в организации.

Дополнительные сведения о задачах управления, связанных со списками адресов, см. в разделе [Процедуры списка адресов](address-list-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Списки адресов" в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - По умолчанию Exchange Online роль "Список адресов" не назначена ни одной из групп ролей. Чтобы использовать командлеты, для которых требуется эта роль, ее необходимо добавить в группу ролей. Дополнительные сведения см. в разделе "Добавление роли в группу ролей" статьи [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

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


## Использование командной консоли для обновления глобального списка адресов

В этом примере выполняется обновление глобального списка адресов для компании "Fourth Coffee".

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Выполнение этой команды приводит только к запуску обновления. Обновление глобального списка адресов может занять несколько часов.</td>
</tr>
</tbody>
</table>


    Update-GlobalAddressList -Identity "Fourth Coffee"

Подробные сведения о синтаксисе и параметрах см. в разделе [Update-GlobalAddressList](https://technet.microsoft.com/ru-ru/library/aa998806\(v=exchg.150\)).

