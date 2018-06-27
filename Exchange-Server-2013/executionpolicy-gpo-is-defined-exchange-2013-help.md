---
title: 'Объект групповой политики ExecutionPolicy определен: Exchange 2013 Help'
TOCTitle: Объект групповой политики ExecutionPolicy определен
ms:assetid: 63de83e2-9a6b-4f57-85b9-df445bea18dd
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.powershellexecutionpolicycheckset(v=EXCHG.150)
ms:contentKeyID: 61203528
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Объект групповой политики ExecutionPolicy определен

 

_**Применимо к:**Exchange Server_

_**Последнее изменение раздела:**2016-12-15_

Программа установки Microsoft Exchange Server 2013 не может продолжать работу, так как она обнаружила, что объект групповой политики (GPO) **ExecutionPolicy** определяет одну или обе приведенные ниже политики.

  - **MachinePolicy**

  - **UserPolicy**

Определения политик не имеют значения. Важно только то, что они определены.

Когда вы запускаете программу установки Exchange 2013, Exchange останавливает и отключает службу инструментария управления Windows (WMI). Если какая-либо из этих политик определена, службу инструментария WMI необходимо включить для выполнения сценария Windows PowerShell. Если эти политики определены, а служба инструментария WMI остановлена, программа установки прекратит работу, а сервер перейдет в несогласованное состояние.

Чтобы продолжить работу программы установки, необходимо временно удалить все определения политики **MachinePolicy** или **UserPolicy** в объекте групповой политики (GPO) **ExecutionPolicy**.

Сведения об удалении определений политики **MachinePolicy** или **UserPolicy** в объекте групповой политики (GPO) **ExecutionPolicy** см. в [статье KB981474 базы знаний](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=981474).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Хотя эта статья базы знаний написана для Exchange 2010, она также применима к накопительным и обычным пакетам обновления Exchange 2013.</td>
</tr>
</tbody>
</table>


Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

