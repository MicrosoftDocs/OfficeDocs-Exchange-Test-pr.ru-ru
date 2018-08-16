---
title: 'Формат адресации SMTP не поддерживается_SMTPAddressLiteral: Exchange 2013 Help'
TOCTitle: Формат адресации SMTP не поддерживается_SMTPAddressLiteral
ms:assetid: b8b55917-d81f-4c0a-ad65-7bb10ac58df8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.smtpaddressliteral(v=EXCHG.150)
ms:contentKeyID: 50488989
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Формат адресации SMTP не поддерживается\_SMTPAddressLiteral

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft Exchange Server 2007 и Exchange Server 2010, так как в указанной политике получателей используется неподдерживаемый формат SMTP-адреса.

Exchange 2007 и Exchange 2010 требуется, чтобы все SMTP-адреса, используемые для политик адресов электронной почты, не содержали литералы IP-адресов, например: *user@\[10.10.1.1\]*.

Чтобы устранить эту проблему, измените значение SMTP-адреса в политике получателей так, чтобы оно не содержало литерала IP-адреса. Замените квадратные скобки (\[\]) и цифры (10.10.1.1) литерала IP-адреса на формат имен DNS, например: *user@contoso.com*. После этого перезапустите программу установки Exchange.

Дополнительные сведения об управлении политиками получателей для сервера Exchange Server 2007 см. в статье "Управление политиками адресов электронной почты" ([https://go.microsoft.com/fwlink/?LinkId=86653](https://go.microsoft.com/fwlink/?linkid=86653)).

Дополнительные сведения об управлении политиками получателей для сервера Exchange Server 2010 см. в статье "Управление политиками адресов электронной почты" ([https://go.microsoft.com/fwlink/?LinkId=179519](https://go.microsoft.com/fwlink/?linkid=179519)).

