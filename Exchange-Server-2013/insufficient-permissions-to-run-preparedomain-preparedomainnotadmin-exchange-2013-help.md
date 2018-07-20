---
title: 'Недостаточно прав для выполнения команды /PrepareDomain_PrepareDomainNotAdmin: Exchange 2013 Help'
TOCTitle: Недостаточно прав для выполнения команды /PrepareDomain_PrepareDomainNotAdmin
ms:assetid: c33a2bc0-5b07-49b8-a1c1-53baa4933d44
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.preparedomainnotadmin(v=EXCHG.150)
ms:contentKeyID: 50489107
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Недостаточно прав для выполнения команды /PrepareDomain\_PrepareDomainNotAdmin

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft Exchange Server 2007 из-за сбоя запуска процесса **/PrepareDomain**. У вошедшего в систему пользователя недостаточно разрешений для выполнения процесса **/PrepareDomain**.

Для установки сервера Exchange Server 2007 требуется, чтобы пользователь, вошедший в систему и запускающий процесс **/PrepareDomain**, был членом группы администраторов домена для подготавливаемого домена и членом группы администраторов предприятия.

Чтобы устранить эту проблему, предоставьте пользователю, вошедшему в систему, разрешения группы администраторов домена для подготавливаемого домена и включите его в группу администраторов предприятия либо войдите в систему с учетной записью, обладающей такими разрешениями, а затем повторно запустите программу установки сервера Exchange Server 2007.

Дополнительные сведения о разрешениях Active Directory, необходимых для работы с Microsoft Exchange, см. в статье "Работа с разрешениями Active Directory на сервере Exchange Server" ([https://go.microsoft.com/fwlink/?LinkId=47592](https://go.microsoft.com/fwlink/?linkid=47592)).

