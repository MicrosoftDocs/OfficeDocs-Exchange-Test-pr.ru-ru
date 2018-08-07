---
title: 'Вошедший пользователь не является членом локальной группы "Администраторы"'
TOCTitle: The logged-on user is not a member of the local Administrators group_NotLocalAdmin
ms:assetid: d06f0894-b139-49ba-afe3-f58d3bd28e32
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.notlocaladmin(v=EXCHG.150)
ms:contentKeyID: 50489256
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# The logged-on user is not a member of the local Administrators group\_NotLocalAdmin

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2012-06-05_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Exchange Server 2007 setup cannot continue because the logged-on user is not a member of the local computer's administrators group.

Exchange 2007 setup requires that the logged-on user who installs Microsoft Exchange has full access to the local computer.

To resolve this issue, log on to the computer by using an account that has local administrator access and then rerun Microsoft Exchange setup.

