---
title: 'Создание списка адресов с помощью фильтров получателей: Exchange 2013 Help'
TOCTitle: Создание списка адресов с помощью фильтров получателей
ms:assetid: 8eabea64-97c6-40af-b61c-9b6a125cbdf1
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb123718(v=EXCHG.150)
ms:contentKeyID: 50488594
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Создание списка адресов с помощью фильтров получателей

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2014-12-16_

В этом разделе описывается создание списка адресов с помощью фильтров получателей. Дополнительные сведения о списках адресов см. в разделе [Списки адресов](address-lists-exchange-2013-help.md).

Дополнительные сведения о задачах управления, связанных со списками адресов, см. в разделе [Процедуры списка адресов](address-list-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Списки адресов" в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - По умолчанию Exchange Online роль "Список адресов" не назначена ни одной из групп ролей. Чтобы использовать командлеты, для которых требуется эта роль, ее необходимо добавить в группу ролей. Дополнительные сведения см. в разделе "Добавление роли в группу ролей" статьи [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

  - Чтобы использовать параметр *RecipientFilter* для создания настраиваемого фильтра, необходимо задать строку для фильтра. В командной консоли Exchange используется синтаксис фильтрации OPATH. OPATH — это язык запросов, разработанный для опроса источников данных объектов.

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


## Использование командной консоли Exchange для создания списка адресов с помощью фильтров получателей

В этом примере создается список адресов для всех пользователей с почтовыми ящиками Exchange, находящихся в Вашингтоне или Орегоне.

    New-AddressList -Name "Pacific Northwest Mailboxes" -RecipientFilter {((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'Washington') -or (StateOrProvince -eq 'Oregon')))}

В этом примере создается список адресов для всех пользователей с почтовыми ящиками Exchange, для которых параметр *CustomAttribute15* имеет значение `AgencyB`.

    New-AddressList -Name "AgencyB" -RecipientFilter {(RecipientType -eq 'UserMailbox') -and (CustomAttribute15 -like *AgencyB*)}

Подробные сведения о синтаксисе и параметрах см. в разделе [New-AddressList](https://technet.microsoft.com/ru-ru/library/aa996912\(v=exchg.150\)).

