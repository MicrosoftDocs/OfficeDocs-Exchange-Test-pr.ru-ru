---
title: 'Не достаточно прав для удаления всех ролей сервера'
TOCTitle: Недостаточно разрешений для удаления всех ролей сервера_CannotUninstallDelegatedServer
ms:assetid: 214ae6f3-15e7-4337-99e8-40f9547c8e0c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.cannotuninstalldelegatedserver(v=EXCHG.150)
ms:contentKeyID: 50487603
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Недостаточно разрешений для удаления всех ролей сервера\_CannotUninstallDelegatedServer

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft Exchange Server 2007, так как не удается удалить все роли сервера.

Пользователь, удаляющий роли сервера, должен быть членом группы администраторов организации Exchange или группы администраторов предприятия.

Чтобы устранить эту проблему, предоставьте пользователю, вошедшему в систему, права администратора организации Exchange, включите его в группу администраторов предприятия или войдите в учетную запись, которой предоставлены соответствующие разрешения, и повторно запустите программу установки Exchange 2007.

Дополнительные сведения о необходимых с Microsoft Exchange Active Directory разрешений можно «Работа с Active Directory разрешений в Exchange Server» ([https://go.microsoft.com/fwlink/?LinkId=47592](https://go.microsoft.com/fwlink/?linkid=47592)).

