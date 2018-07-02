---
title: 'Серверы Exchange 2010 или Exchange 2007 не обнаружены: Exchange 2013 Help'
TOCTitle: Серверы Exchange 2010 или Exchange 2007 не обнаружены
ms:assetid: 789cabab-c769-4a16-a6c8-3db82cff8861
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.noe14serverwarning(v=EXCHG.150)
ms:contentKeyID: 50488472
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Серверы Exchange 2010 или Exchange 2007 не обнаружены

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2012-11-08_

Установка Microsoft Exchange Server 2013 вывела данное предупреждение, потому что в организации нет ролей сервера Exchange Server 2010 и Exchange Server 2007.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.Caution(EXCHG.150).gif" title="Внимание!" alt="Внимание!" />Внимание!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если продолжить установку Exchange Server 2013, вы не сможете добавить серверы Exchange 2010 или Exchange 2007 в организации в будущем.</td>
</tr>
</tbody>
</table>


Перед развертыванием Exchange 2013 нужно учесть следующие факторы, которые могут привести к необходимости развертывания серверов Exchange 2010 или Exchange 2007 перед Exchange 2013:

  - **Приложения сторонних производителей или разработанные предприятием**   Приложения, разработанные для более ранних версий Exchange, могут оказаться несовместимы с Exchange 2013. Может потребоваться поддержание серверов Exchange 2010 или Exchange 2007 для поддержки таких приложений.

  - **Требования по сосуществованию или перемещению**   Если планируется миграция почтовых ящиков в организации, для некоторых решений могут понадобиться серверы Exchange 2010 или Exchange 2007.

Если необходимо развернуть серверы Exchange 2010 или Exchange 2007, то необходимо сделать это перед развертыванием Exchange 2013. Необходимо подготовить Active Directory для каждой версии Exchange в следующем порядке:

1.  Exchange 2007

2.  Exchange 2010

3.  Exchange 2013

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

