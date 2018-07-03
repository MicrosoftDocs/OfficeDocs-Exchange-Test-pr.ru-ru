﻿---
title: 'Предоставление пользователям сообщение ожидание индикатор (ожидающего сообщения): Exchange 2013 Help'
TOCTitle: Предоставление пользователям сообщение ожидание индикатор (ожидающего сообщения)
ms:assetid: 3d0ca657-00b6-4108-a850-b092fede1f75
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd335216(v=EXCHG.150)
ms:contentKeyID: 50556366
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Предоставление пользователям сообщение ожидание индикатор (ожидающего сообщения)

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2013-02-21_

Для пользователей, связанных с политикой почтовых ящиков единой системы обмена сообщениями, можно включить или отключить индикатор ожидающих сообщений. Средство индикации ожидающего сообщения — это функция, поддерживаемая большинством устаревших систем голосовой почты. В самом распространенном случае на телефоне подписчика голосовой почты начинает светиться индикатор, что означает наличие нового сообщения голосовой почты. Индикатор ожидающих сообщений может также обеспечить отправку текстового сообщения на мобильный телефон пользователя с включенной поддержкой единой системы обмена сообщениями. По умолчанию параметр включен.

Если индикатор ожидающих сообщений отключен в IP-шлюзе единой системы обмена сообщениями, данная функция будет недоступна для пользователей с включенной поддержкой единой системы обмена сообщениями, связанных с политикой почтовых ящиков этой системы.

Дополнительные сведения об управленческих задачах, связанных с политиками почтовых ящиков единой системы обмена сообщениями, см. в разделе [Процедуры политики почтовых ящиков единой системы обмена СООБЩЕНИЯМИ](um-mailbox-policy-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Политики почтовых ящиков единой системы обмена сообщениями» в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что политика почтовых ящиков единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание политики почтовых ящиков единой системы обмена сообщениями](create-a-um-mailbox-policy-exchange-2013-help.md).

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

## Использование Центра администрирования Exchange для включения индикатора ожидающих сообщений

1.  В Центре администрирования Exchange последовательно выберите пункты **Единая система обмена сообщениями** \> **Абонентские группы единой системы обмена сообщениями**. Выберите из списка абонентскую группу единой системы обмена сообщениями, которую необходимо изменить, и нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

2.  В разделе **Политики почтовых ящиков единой системы обмена сообщениями** выберите политику почтовых ящиков единой системы обмена сообщениями, которую требуется изменить, а затем нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Политика почтовых ящиков единой системы обмена сообщениями** установите флажок рядом с пунктом **Разрешить индикатор ожидающих сообщений**.

4.  Нажмите кнопку **Сохранить**.

## Использование командной консоли для включения индикатора ожидающих сообщений

В этом примере выполняется включение индикатора ожидающих сообщений для пользователей, связанных с политикой почтовых ящиков единой системы обмена сообщениями `MyUMMailboxPolicy`.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowMessageWaitingIndicator $true
