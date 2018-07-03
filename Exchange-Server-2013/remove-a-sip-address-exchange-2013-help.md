﻿---
title: 'Удалите адрес SIP: Exchange 2013 Help'
TOCTitle: Удалите адрес SIP
ms:assetid: eaaff0b0-7d85-4845-a7b8-ac22b42bc415
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ662761(v=EXCHG.150)
ms:contentKeyID: 50556498
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Удалите адрес SIP

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2012-11-14_

Когда вы включаете для пользователя единую систему обмена сообщениями и связываете его с абонентской группой универсального кода ресурса SIP, создаются два прокси-адреса единой системы обмена сообщениями Microsoft Exchange. Один адрес содержит добавочный номер пользователя, а другой — SIP-адрес для него. Добавочный номер используется, когда пользователь выполняет вызов по номеру голосового доступа к Outlook.

Абонентские группы универсального кода ресурса SIP используются при интеграции единой системы обмена сообщениями с Microsoft Office Communications Server 2007 R2 или Microsoft Lync Server. SIP-адрес используется в Communications Server или Lync Server для маршрутизации входящих вызовов и отправки голосовой почты пользователю. По умолчанию SIP-адрес, используемый единой системой обмена сообщениями, также используется в Communications Server или Lync Server.

Вы можете удалить основного SIP-адрес, который был добавлен, когда пользователь была включена поддержка единой системы обмена СООБЩЕНИЯМИ или дополнительного SIP-адрес, который был добавлен более поздних версий, а также адрес прокси-сервера EUM для пользователя. Основной адрес SIP, добавленную, когда пользователь была включена поддержка единой системы обмена СООБЩЕНИЯМИ будут перечислены как основной адрес прокси-сервера EUM. Любые дополнительные адреса SIP, добавленную будут перечислены как дополнительный EUM прокси-адреса. При удалении SIP-адрес абонентов больше не можно оставить голосовой почты для пользователя с SIP-адрес, который был удален, даже если вход пользователя с SIP-адрес, назначенный пользователю в Communications Server или Lync Server.

При удалении основного SIP-адрес единой системы обмена СООБЩЕНИЯМИ не будут иметь возможность отправлять голосовой почты для почтового ящика пользователя и не будут обрабатываться правила ответа на звонок. После удаления основного SIP-адрес адрес прокси-сервера EUM для пользователя отображается как **значение Null,** в почтовом ящике пользователя в центре администрирования Exchange и при запуске командлета **Get-Mailbox** в командной консоли Exchange. Кроме того при запуске командлета **Get-UMMailbox** параметры *Extensions*, *PhoneNumber*и *CallAnsweringRulesExtensions* будет пустым или значение null.

Можно использовать Центр администрирования Exchange или командной консоли Exchange для удаления основного или дополнительного SIP-адрес. Страница **Адрес электронной почты** на почтовом ящике пользователя в центре администрирования Exchange для удаления основного или дополнительного SIP-адрес. Нельзя использовать страницу **Единой системы обмена СООБЩЕНИЯМИ почтовых ящиков** в центре администрирования Exchange для удаления основного или дополнительного SIP-адрес.

Просмотреть основной и дополнительный SIP-адреса для пользователя можно с помощью командлета **Get-UMMailbox** или **Get-Mailbox** в командной консоли.

Дополнительные задачи управления, связанные с пользователями, задействованными для голосовой почты, см. в разделе [Процедуры пользователя голосовой почты](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 3 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Почтовые ящики единой системы обмена сообщениями» в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этой процедуры убедитесь, что политика почтовых ящиков единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание политики почтовых ящиков единой системы обмена сообщениями](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что почтовый ящик пользователя была включена поддержка единой системы обмена СООБЩЕНИЯМИ и связанные с абонентской группы SIP URI. Подробное описание процедуры в разделе [Включение для пользователя поддержки голосовой почты](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что основной и дополнительный SIP-адреса настроены для пользователя.

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

## Использование центра администрирования Exchange для удаления основной или дополнительный адрес SIP

1.  В Центре администрирования Exchange перейдите к разделу **Получатели** \> **Почтовые ящики**.

2.  В представлении списка выберите почтовый ящик, из которого требуется удалить SIP-адрес и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Почтовый ящик пользователя** в поле **адрес электронной почты** выберите SIP-адрес, который требуется удалить из списка и нажмите кнопку **Удалить**![Значок удаления](images/Dd979797.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Значок удаления"). Основной адрес прокси-сервера EUM или SIP-адрес отображается в полужирный буквы и цифры.

4.  Нажмите кнопку **Сохранить**.

## Использование командной консоли Exchange для удаления основной или дополнительный адрес SIP

В этом примере удаляется tsmith@contoso.com адрес SIP из почтового ящика Tony Smith, пользователя с включенной поддержкой единой системы обмена СООБЩЕНИЯМИ.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Прежде чем удалять SIP-адрес, с помощью командной консоли Exchange, необходимо определить положение EUM адрес прокси-сервера, который требуется изменить. Чтобы определить положение, используйте команду <strong>$mbx.EmailAddresses</strong> . Первый адрес прокси-сервера EUM в списке будет иметь значение 0.</td>
</tr>
</tbody>
</table>


    $mbx = Get-Mailbox tony.smith
    $mbx.EmailAddresses.Item(1) -="eum:tsmith@contoso.com;phone-context=MyDialPlan.contoso.com"
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses
