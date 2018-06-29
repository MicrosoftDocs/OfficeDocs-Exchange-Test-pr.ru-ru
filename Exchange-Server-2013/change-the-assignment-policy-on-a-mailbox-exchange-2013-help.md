﻿---
title: 'Изменение политики назначения для почтового ящика: Exchange 2013 Help'
TOCTitle: Изменение политики назначения для почтового ящика
ms:assetid: 011690a5-233a-4c03-8842-92276f899a89
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638076(v=EXCHG.150)
ms:contentKeyID: 50487346
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Изменение политики назначения для почтового ящика

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2012-10-08_

Можно изменить политику назначения роли управления для почтового ящика. При изменении политики назначения роли управления почтового ящика изменения вступают в силу, как только пользователь обновляет соединение, например, при следующем входе в почтовый ящик или при открытии страницы параметров почтового ящика. Дополнительные сведения о политиках назначений в Microsoft Exchange Server 2013 см. в разделе [Общие сведения о политиках назначения ролей управления](understanding-management-role-assignment-policies-exchange-2013-help.md).

Необходимы сведения о других задачах управления, связанных с разрешениями? см. в разделе [Разрешения](permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Группы ролей" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

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


## Использование центра администрирования Exchange для изменения политики назначения для почтового ящика

1.  В центре администрирования Exchange Exchange перейдите к разделу **Получатели** \> **Почтовые ящики**.

2.  Выберите пользователя или почтовый ящик ресурса, для которого требуется изменить политику назначения, и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  Выберите вкладку **Функции почтового ящика**.

4.  В списке **Политика назначения ролей** выберите политику назначения ролей, которую необходимо назначить почтовому ящику, и нажмите на кнопку **Сохранить**.

## Использование командной консоли для изменения политики назначения для почтового ящика

Для изменения политики назначения для почтового ящика используйте следующую синтаксическую конструкцию.

    Set-Mailbox <mailbox alias or name> -RoleAssignmentPolicy <assignment policy>

В данном примере политика назначения устанавливается для пользователей единой системы обмена сообщениями на почтовом ящике "Виктор".

    Set-Mailbox Brian -RoleAssignmentPolicy "Unified Messaging Users"

## Использование командной консоли для изменения политики назначения для группы почтовых ящиков с определенной политикой назначения

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Нельзя использовать центр администрирования Exchange для одновременного изменения политики назначения для группы почтовых ящиков.</td>
</tr>
</tbody>
</table>


В этой процедуре используется конвейерная передача, командлет **Where** и параметр *WhatIf*. Дополнительные сведения об этих понятиях см. в следующих разделах:

  - [Конвейеризация](https://technet.microsoft.com/ru-ru/library/aa998260\(v=exchg.150\))

  - [Работа с выходными данными команды](working-with-command-output-exchange-2013-help.md)

  - [Параметры WhatIf, Confirm и ValidateOnly](whatif-confirm-and-validateonly-switches-exchange-2013-help.md)

Для изменения политики назначения для группы почтовых ящиков с определенной политикой назначения используйте следующую синтаксическую конструкцию.

    Get-Mailbox | Where { $_.RoleAssignmentPolicy -Eq "<assignment policy to find>" } | Set-Mailbox -RoleAssignmentPolicy <assignment policy to set>

В данном примере выполняется поиск всех почтовых ящиков с политикой назначения "Пользователи Редмонда — Без голосовой почты" и изменение политики назначения на "Пользователи Редмонда — Голосовая почта включена".

    Get-Mailbox | Where { $_.RoleAssignmentPolicy -Eq "Redmond Users - No Voicemail" } | Set-Mailbox -RoleAssignmentPolicy "Redmond Users - Voicemail Enabled"

В этот пример включен параметр *WhatIf*, поэтому можно видеть все изменяемые почтовые ящики без фиксации каких-либо изменений.

    Get-Mailbox | Where { $_.RoleAssignmentPolicy -Eq "Redmond Users - No Voicemail" } | Set-Mailbox -RoleAssignmentPolicy "Redmond Users - Voicemail Enabled" -WhatIf

Дополнительные сведения о синтаксисе и параметрах см. в разделах [Get-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123685\(v=exchg.150\)) или [Set-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123981\(v=exchg.150\)).

