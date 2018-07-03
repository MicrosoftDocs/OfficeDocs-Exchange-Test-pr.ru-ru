﻿---
title: 'Добавление auto attendant добавочный номер: Exchange 2013 Help'
TOCTitle: Добавление auto attendant добавочный номер
ms:assetid: f2bd62ba-1e01-4cb7-862c-c750752e20e0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb232200(v=EXCHG.150)
ms:contentKeyID: 50489462
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Добавление auto attendant добавочный номер

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2012-11-05_

Можно настроить добавочный номер или нескольких добавочных номеров для автосекретаря единой системы обмена сообщениями (UM). При добавлении добавочный номер для автосекретаря единой системы обмена СООБЩЕНИЯМИ, этот номер можно использовать для вызова в автосекретарь с абонентов. Кроме того необходимо добавить добавочные номера, поскольку существует более одного добавочный номер, вызывающие объекты можно использовать для доступа к автосекретарю. По умолчанию не добавочные номера будут настроены для создания автосекретаря.

Можно создать автосекретарь без настройки добавочный номер для автосекретаря. Также можно связать несколько номеров телефона или расширение с одного автосекретаря. Можно либо добавить добавочные номера при создании автосекретаря единой системы обмена СООБЩЕНИЯМИ или добавить их после настройки автосекретаря. Количество цифр в добавочный номер, которые настроены для автосекретаря единой системы обмена СООБЩЕНИЯМИ должно соответствовать количество цифр для добавочным номером, настроенный в абонентской группе единой системы обмена СООБЩЕНИЯМИ связанный с автосекретаря единой системы обмена СООБЩЕНИЯМИ.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Также можно добавить адрес Session Initiation Protocol (SIP) вместо добавления добавочный номер. SIP-адрес, используемый некоторые обмена филиала частных IP-адресов (УАТС) и Office Communications Server 2007 R2 или Microsoft Lync Server.</td>
</tr>
</tbody>
</table>


Дополнительные задачи управления, связанные с автосекретарями единой системы обмена сообщениями, см. в разделе [Процедуры автосекретаря единой системы обмена сообщениями](um-auto-attendant-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Автосекретари единой системы обмена сообщениями» в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что автосекретарь единой системы обмена сообщениями создан. Дополнительные сведения см. в разделе [Создание автосекретаря единой системы обмена сообщениями](create-a-um-auto-attendant-exchange-2013-help.md).

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

## Использование центра администрирования Exchange для добавления расширения или телефонных номеров для автосекретаря единой системы обмена СООБЩЕНИЯМИ

1.  В центре администрирования Exchange последовательно выберите пункты **Единой системы обмена сообщениями** \> **абонентские группы единой системы обмена СООБЩЕНИЯМИ**. В представлении списка выберите абонентскую группу единой системы обмена СООБЩЕНИЯМИ, необходимо изменить и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

2.  На странице **Единой системы обмена СООБЩЕНИЯМИ абонентская группа** в группе **Единой системы обмена СООБЩЕНИЯМИ автосекретари** выберите автосекретаря единой системы обмена СООБЩЕНИЯМИ, необходимо добавить номера расширение или по телефону.

3.  На панели инструментов нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

4.  На странице **Единой системы обмена СООБЩЕНИЯМИ автосекретаря** \> **Общие**, в списке **номера доступа**, в текстовом поле введите расширение или на телефонный номер, который требуется использовать и нажмите кнопку **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления").

5.  Нажмите кнопку **Сохранить** для добавления номера.

## Использование командной консоли Exchange для настройки добавочный номер для автосекретаря единой системы обмена СООБЩЕНИЯМИ

В этом примере показана настройка автосекретаря единой системы обмена СООБЩЕНИЯМИ с именем `MyUMAutoAttendant` с несколькими добавочные номера.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -PilotIdentifierList "12345, 72000, 75000"
