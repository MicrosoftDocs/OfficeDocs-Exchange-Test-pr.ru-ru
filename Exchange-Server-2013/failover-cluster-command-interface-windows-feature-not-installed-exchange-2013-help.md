---
title: 'Компонент Windows "Командный интерфейс отказоустойчивого кластера" не установлен: Exchange 2013 Help'
TOCTitle: Компонент Windows "Командный интерфейс отказоустойчивого кластера" не установлен
ms:assetid: 0d839514-5ab7-497d-8945-41392b4c3980
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.rsatclusteringcmdinterfaceinstalled(v=EXCHG.150)
ms:contentKeyID: 51408001
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Компонент Windows \"Командный интерфейс отказоустойчивого кластера\" не установлен

 

_**Применимо к:**Exchange Server_

_**Последнее изменение раздела:**2014-12-03_

Невозможно продолжить установку Microsoft Exchange Server 2013, поскольку на локальном компьютере отсутствует требуемый компонент Windows. Вам необходимо установить этот компонент Windows до продолжения установки Exchange 2013.

Программа установки Exchange 2013 требует установить на компьютере компонент Windows **Командный интерфейс отказоустойчивого кластера**, прежде чем продолжить установку.

Выполните следующие действия, чтобы установить компонент Windows на этом компьютере. Если для завершения установки компонента требуется перезагрузка, вам необходимо закрыть программу установки Exchange 2013, перезагрузить компьютер и запустить программу установки повторно.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Перед продолжением установки Exchange 2013 может потребоваться установить дополнительные компоненты или обновления Windows. Полный список обязательных компонентов и обновлений Windows см. в разделе <a href="exchange-2013-prerequisites-exchange-2013-help.md">Предварительные требования для Exchange 2013</a>.</td>
</tr>
</tbody>
</table>


1.  Откройте Windows PowerShell на локальном компьютере.

2.  Запустите следующую команду для установки необходимого компонента Windows.
    
        Install-WindowsFeature RSAT-Clustering-CmdInterface

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

