---
title: 'Создание глобального списка адресов: Exchange 2013 Help'
TOCTitle: Создание глобального списка адресов
ms:assetid: 59e4955a-8999-4d17-be9f-23a41a23b929
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb232063(v=EXCHG.150)
ms:contentKeyID: 50488279
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Создание глобального списка адресов

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2014-12-16_

Глобальный список адресов — это каталог, содержащий записи для всех групп, пользователей и контактов в организации Майкрософт Exchange. Если в организации используются политики адресных книг, может потребоваться создать дополнительные глобальные списки адресов. Дополнительные сведения см. в разделе [Политики адресных книг](address-book-policies-exchange-2013-help.md).

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


## Что необходимо сделать?

## Использование командной консоли для создания глобального списка адресов с помощью свойств условного фильтра

В этом примере показано, как создать глобальный список адресов с именем "GAL\_Contoso" для получателей, являющихся пользователями почтовых ящиков и сотрудниками компании Contoso.

    New-GlobalAddressList -Name "GAL_Contoso" -IncludedRecipients MailboxUsers -ConditionalCompany Contoso

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если используются свойства заранее подготовленного условного фильтра, значение параметра <em>IncludedRecipients</em> не может быть пустым.</td>
</tr>
</tbody>
</table>


Подробные сведения о синтаксисе и параметрах см. в разделе [New-GlobalAddressList](https://technet.microsoft.com/ru-ru/library/bb123785\(v=exchg.150\)).

## Использование командной консоли для создания глобального списка адресов с помощью фильтра получателей

В этом примере показано, как создать глобальный список адресов с именем "GAL\_AgencyA" для получателей, для которых параметр *CustomAttribute15* имеет значение `AgencyA`.

    New-GlobalAddressList -Name "GAL_AgencyA" -RecipientFilter {CustomAttribute15 -like "AgencyA"}

Подробные сведения о синтаксисе и параметрах см. в разделе [New-GlobalAddressList](https://technet.microsoft.com/ru-ru/library/bb123785\(v=exchg.150\)).

