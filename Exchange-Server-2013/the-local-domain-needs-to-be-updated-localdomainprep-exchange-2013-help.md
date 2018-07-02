---
title: 'Необходимо обновить локальный домен_LocalDomainPrep: Exchange 2013 Help'
TOCTitle: Необходимо обновить локальный домен_LocalDomainPrep
ms:assetid: f33e6785-e85a-495e-a124-ebcb2b763e75
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.localdomainprep(v=EXCHG.150)
ms:contentKeyID: 50489499
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Необходимо обновить локальный домен\_LocalDomainPrep

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft Exchange Server 2007, поскольку вошедший в систему пользователь не обладает разрешениями, необходимыми для подготовки домена.

Программе установки Exchange требуется, чтобы пользователь, вошедший в систему при выполнении команды **Setup /PrepareDomain**, был членом групп администраторов домена и администраторов организации Exchange или группы администраторов предприятия.

Чтобы устранить эту проблему, предоставьте пользователю, вошедшему в систему, разрешения администратора домена и администратора организации Exchange, включите его в группу администраторов предприятия либо войдите в систему с учетной записью, обладающей такими разрешениями, а затем повторно запустите программу установки Exchange Server 2007.

Дополнительные сведения о разрешениях Active Directory, необходимых для работы с Microsoft Exchange, см. в статье "Работа с разрешениями Active Directory на сервере Exchange Server" ([https://go.microsoft.com/fwlink/?LinkId=47592](https://go.microsoft.com/fwlink/?linkid=47592)).

