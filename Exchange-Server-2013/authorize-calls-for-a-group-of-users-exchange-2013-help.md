﻿---
title: 'Авторизовать звонки для группы пользователей: Exchange 2013 Help'
TOCTitle: Авторизовать звонки для группы пользователей
ms:assetid: 7fc36757-868c-4bde-b793-6ae630da155c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb232099(v=EXCHG.150)
ms:contentKeyID: 51408049
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Авторизовать звонки для группы пользователей

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2013-02-21_

В политике почтовых ящиков единой системы обмена сообщениями можно включить авторизации набора номера. Авторизации набора номера в политике почтовых ящиков можно использовать для запрета прошедшим проверку пользователям голосового доступа к Outlook, которые привязаны к политике почтовых ящиков единой системы обмена сообщениями, осуществлять звонки внутри страны или региона, международные звонки или *исходящие звонки*. Исходящий звонок осуществляется, когда единая система обмена сообщениями совершает исходящий вызов для пользователя, после того как он набрал телефонный номер голосового доступа к Outlook, настроенный для абонентской группы единой системы обмена сообщениями. Параметры политики почтовых ящиков единой системы обмена сообщениями применяются для всех пользователей системы, связанных с политикой почтовых ящиков системы.

Дополнительные сведения о задачах управления, связанных с исходящими звонками, см. в разделе [Которое позволяет пользователям выполнять вызовы процедур](allowing-users-to-make-calls-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Политики почтовых ящиков единой системы обмена сообщениями» в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что политика почтовых ящиков единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание политики почтовых ящиков единой системы обмена сообщениями](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что в абонентской группе единой системы обмена сообщениями созданы правила набора номера для вызовов внутри страны и региона, а также для международных вызовов. Дополнительные сведения см. в разделе [Создание правил набора номера для пользователей](create-dialing-rules-for-users-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..</td>
</tr>
</tbody>
</table>


## Что необходимо сделать?

## Использование Центра администрирования Exchange для включения авторизаций набора номера в политике почтовых ящиков единой системы обмена сообщениями для групп правил набора номеров внутри страны/региона

1.  В Центре администрирования Exchange последовательно выберите пункты **Единая система обмена сообщениями** \> **Абонентские группы единой системы обмена сообщениями**. Выберите из списка абонентскую группу единой системы обмена сообщениями, которую необходимо изменить, и нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

2.  На странице **Абонентская группа единой системы обмена сообщениями** в разделе **Политики почтовых ящиков единой системы обмена сообщениями** выберите политику почтовых ящиков этой системы, для которой необходимо создать авторизацию набора номера, а затем нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Политика почтовых ящиков единой системы обмена сообщениями** \> **Авторизация набора номера** щелкните **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления") в разделе **Авторизованные группы правил набора номера внутри страны или региона**.

4.  На странице **Выбор разрешенных групп правил набора номера** выберите группу правил набора номера, нажмите кнопку **OK**, а затем — кнопку **Сохранить**.

## Использование Центра администрирования Exchange для включения авторизаций набора номера в политике почтовых ящиков единой системы обмена сообщениями для групп правил набора международных номеров

1.  В Центре администрирования Exchange последовательно выберите пункты **Единая система обмена сообщениями** \> **Абонентские группы единой системы обмена сообщениями**. Выберите из списка абонентскую группу единой системы обмена сообщениями, которую необходимо изменить, и нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

2.  На странице **Абонентская группа единой системы обмена сообщениями** в разделе **Политики почтовых ящиков единой системы обмена сообщениями** выберите политику почтовых ящиков этой системы, для которой необходимо создать авторизацию набора номера, а затем нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Политика почтовых ящиков единой системы обмена сообщениями** \> **Авторизация набора номера** щелкните **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления") в разделе **Авторизованные группы правил набора международных номеров**.

4.  На странице **Выбор разрешенных групп правил набора номера** выберите группу правил набора номера, нажмите кнопку **OK**, а затем — кнопку **Сохранить**.

## Использование командной консоли для включения авторизаций набора номеров внутри страны/региона и международных номеров в политике почтовых ящиков единой системы обмена сообщениями

В этом примере показано, как включить авторизации набора номеров InCountry/RegionGroup1, InCountry/RegionGroup2, InternationalGroup1 и InternationalGroup2 для политики почтовых ящиков единой системы обмена сообщениями с именем `MyUMMailboxPolicy`.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -AllowedInCountryOrRegionGroups InCountry/RegionGroup1,InCountry/RegionGroup2 -AllowedInternationalGroups InternationalGroup1,InternationalGroup2
