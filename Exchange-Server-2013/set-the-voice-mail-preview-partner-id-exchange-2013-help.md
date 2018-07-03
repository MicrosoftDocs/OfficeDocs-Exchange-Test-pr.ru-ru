﻿---
title: 'Задать идентификатор партнера Предварительный просмотр голосовой почты: Exchange 2013 Help'
TOCTitle: Задать идентификатор партнера Предварительный просмотр голосовой почты
ms:assetid: ab98c320-9952-47a7-b141-ddfc2c0ad419
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff630924(v=EXCHG.150)
ms:contentKeyID: 51408060
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Задать идентификатор партнера Предварительный просмотр голосовой почты

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2013-02-13_

В политике почтовых ящиков единой системы обмена сообщениями возможна установка идентификатора партнера прослушивания голосовой почты. После установки идентификатора партнера прослушивания голосовой почты в политике почтовых ящиков единой системы обмена сообщениями это значение применяется к пользователям единой системы обмена сообщениями, связанным с политикой почтовых ящиков.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Установка идентификатора партнера для просмотра голосовой почты выполняется из командной консоли.</td>
</tr>
</tbody>
</table>


Для получения дополнительных сведений о партнерской программе прослушивания голосовой почты обратитесь к разделу [Помощник просмотра голосовой почты](voice-mail-preview-advisor-exchange-2013-help.md).

Дополнительные сведения о задачах управления, связанных с просмотром голосовой почты, см. в разделе [Голосовой почты Preview процедур](voice-mail-preview-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 1 минута.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Политики почтовых ящиков единой системы обмена сообщениями» в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание политики почтовых ящиков единой системы обмена сообщениями](create-a-um-mailbox-policy-exchange-2013-help.md).

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


## Использование командной консоли для установки идентификатора партнера для прослушивания голосовой почты в политике почтовых ящиков единой системы обмена сообщениями

В этом примере в политике почтовых ящиков *MyUMMailboxPolicy* устанавливается идентификатор партнера для прослушивания голосовой почты, равный CON123-2010.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy 
    -VoiceMailPreviewPartnerAssignedID CON123-2010
