﻿---
title: 'Программа установки не может установить Exchange в controller_ComputerRODC домена только для чтения: Exchange 2013 Help'
TOCTitle: Программа установки не может установить Exchange в controller_ComputerRODC домена только для чтения
ms:assetid: 4934d755-65be-47e2-86b0-6ea1ab148a96
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.computerrodc(v=EXCHG.150)
ms:contentKeyID: 50487975
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Программа установки не может установить Exchange в controller\_ComputerRODC домена только для чтения

 

_**Применимо к:**Exchange Server_

_**Последнее изменение раздела:**2012-06-05_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку сервера Microsoft Exchange Server 2007, поскольку конечный компьютер является контроллером домена только для чтения.

Контроллеры домена только для чтения являются возможностью Active Directory операционной системы Windows Server 2008. Контроллер домена только для чтения является одним из вариантов установки контроллера домена, используемым при установке на удаленные сайты с низким уровнем физической безопасности.

Программе установки Exchange требуется доступ на запись для конечного компьютера.

Чтобы устранить эту проблему, выберите конечный компьютер, не являющийся контроллером домена только для чтения, и заново запустите программу установки.

