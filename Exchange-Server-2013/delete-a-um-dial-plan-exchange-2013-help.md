﻿---
title: 'Удаление абонентской группы единой системы обмена СООБЩЕНИЯМИ: Exchange 2013 Help'
TOCTitle: Удаление абонентской группы единой системы обмена СООБЩЕНИЯМИ
ms:assetid: c9b32ef6-432c-45ca-b94c-31bbcc973128
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124546(v=EXCHG.150)
ms:contentKeyID: 50489064
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Удаление абонентской группы единой системы обмена СООБЩЕНИЯМИ

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2012-11-11_

Существующую абонентскую группу единой системы обмена сообщениями можно удалить. При удалении абонентской группы единой системы обмена сообщениями она станет недоступной для шлюза IP, политик почтовых ящиков и сервисных групп единой системы обмена сообщениями. Невозможно удалить абонентскую группу единой системы обмена сообщениями, если она связана с политиками почтовых ящиков, автосекретарями или сервисными группами единой системы обмена сообщениями.

Дополнительные задачи управления, связанные с абонентскими группами единой системы обмена сообщениями, см. в разделе [Процедуры плана телефонным единой системы обмена СООБЩЕНИЯМИ](um-dial-plan-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Абонентская группа единой системы обмена сообщениями" в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

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

## Использование Центра администрирования Exchange для удаления существующей абонентской группы

1.  В Центре администрирования Exchange последовательно выберите пункты **Единая система обмена сообщениями** \> **Абонентские группы единой системы обмена сообщениями**.

2.  Выберите в списке абонентскую группу единой системы обмена сообщениями, которую необходимо удалить, и нажмите кнопку **Удалить**![Значок удаления](images/Dd979797.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Значок удаления").

3.  На странице предупреждения нажмите кнопку **Да**.

## Использование командной консоли для удаления существующей абонентской группы

В этом примере удаляется абонентская группа единой системы обмена сообщениями `MyUMDialPlan`.

    RemoveUMDialplan -identity MyUMDialPlan
