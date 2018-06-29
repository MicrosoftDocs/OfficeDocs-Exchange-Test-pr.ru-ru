﻿---
title: 'Требуются глобальные обновления: Exchange 2013 Help'
TOCTitle: Требуются глобальные обновления
ms:assetid: 0530f3c6-6fa6-456b-a33a-f3d2f7eaa2ef
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.globalupdaterequired(v=EXCHG.150)
ms:contentKeyID: 50487375
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Требуются глобальные обновления

 

_**Применимо к:**Exchange Server_

_**Последнее изменение раздела:**2014-12-02_

Программа установки Microsoft Exchange Server 2013 не может продолжить работу, так как вошедший пользователь не имеет соответствующих разрешений, необходимых для выполнения глобальных обновлений службы каталогов Active Directory.

Программа установки требует, чтобы пользователь, вошедший в систему при установке Exchange 2013, обладал разрешением на создание объектов в Active Directory и их изменение. При первом запуске установки в организации Exchange 2013 используемая учетная запись должна являться членом группы администраторов схемы и администраторов предприятия. Эти разрешения необходимы, так как служба Active Directory должна быть подготовлена для Exchange 2013 при первом запуске программы установки. После подготовки Active Directory учетная запись, которая используется для установки дополнительных серверов Exchange 2013, должна быть членом группы ролей управления организацией.

Для устранения этой неполадки следует предоставить вошедшему в систему пользователю соответствующие разрешения или войти в систему с использованием учетной записи, имеющей такие разрешения, и повторно запустить программу установки Exchange 2013.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Межлесная установка Exchange 2013 не поддерживается. Для установки Exchange 2013 используйте учетную запись, которая является членом леса Active Directory.</td>
</tr>
</tbody>
</table>


Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

