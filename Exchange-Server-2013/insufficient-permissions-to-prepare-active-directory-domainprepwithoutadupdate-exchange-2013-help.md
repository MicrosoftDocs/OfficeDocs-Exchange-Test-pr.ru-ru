---
title: 'Недостаточно прав для подготовки Active Directory_DomainPrepWithoutADUpdate: Exchange 2013 Help'
TOCTitle: Недостаточно прав для подготовки Active Directory_DomainPrepWithoutADUpdate
ms:assetid: 4283c4b9-983f-460e-a5de-42b2772eae0d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.domainprepwithoutadupdate(v=EXCHG.150)
ms:contentKeyID: 50487902
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Недостаточно прав для подготовки Active Directory\_DomainPrepWithoutADUpdate

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft Exchange Server 2007, так как не удается подготовить домен.

Перед подготовкой доменов в Active Directory необходимо изменить службу каталогов Active Directory для Exchange Server 2007.

Учетной записи, которая используется для выполнения команды **setup /PrepareAD**, не предоставлены соответствующие разрешения, не несмотря на то что она принадлежит группе администраторов предприятия. Возможно, она больше не действительна.

Чтобы устранить эту проблему, убедитесь, что учетная запись, в которую вы вошли, действительна и принадлежит группе администраторов предприятия, или войдите в учетную запись, которой предоставлены соответствующие разрешения, и повторно выполните команду **setup /PrepareAD**.

Дополнительные сведения о выполнении процесса PrepareAD см. в статье "Инструкции по подготовке службы Active Directory и доменов" ([https://go.microsoft.com/fwlink/?LinkId=78453](https://go.microsoft.com/fwlink/?linkid=78453)).

Дополнительные сведения о разрешениях Active Directory, необходимых для работы с Microsoft Exchange, см. в статье "Работа с разрешениями Active Directory на сервере Exchange Server" ([https://go.microsoft.com/fwlink/?LinkId=47592](https://go.microsoft.com/fwlink/?linkid=47592)).

