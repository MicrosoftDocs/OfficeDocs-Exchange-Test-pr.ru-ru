﻿---
title: 'Установку первого сервера Exchange Server в организации невозможно делегировать: Exchange 2013 Help'
TOCTitle: Установку первого сервера Exchange Server в организации невозможно делегировать
ms:assetid: 286b82ee-bddf-493c-b6ea-21aced6dbbad
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.delegatedunifiedmessagingfirstinstall(v=EXCHG.150)
ms:contentKeyID: 50487679
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Установку первого сервера Exchange Server в организации невозможно делегировать

 

_**Применимо к:**Exchange Server_

_**Последнее изменение раздела:**2014-11-05_

Не удается продолжить установку Microsoft Exchange Server 2013, так как пользователь, вошедший в систему, не имеет разрешений на установку первого сервера Exchange 2013 в организации.

Хотя программа установки Exchange 2013 позволяет использовать делегирование для установки последующих ролей сервера, необходимо, чтобы вошедший в систему пользователь был членом группы безопасности Windows "Администраторы предприятия" при установке первого сервера Exchange 2013 в организации. Это связано с тем, что во время установки программа установки Exchange 2013 создает и настраивает объекты в контейнере организации Exchange в службе каталогов Active Directory.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если схема Active Directory для Exchange 2013 не подготовлена, вошедший в систему пользователь также должен входить в группу безопасности Windows &quot;Администраторы схемы&quot;. В свою очередь, другой пользователь, являющийся членом группы администраторов схемы, может подготовить схему Active Directory перед установкой Exchange 2013.</td>
</tr>
</tbody>
</table>


Чтобы устранить эту проблему, добавьте вошедшего в систему пользователя в группу безопасности "Администраторы предприятия". Или войдите, используя учетную запись, которая входит в группу безопасности "Администраторы предприятия". Запустите программу установки Exchange 2013 повторно.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

