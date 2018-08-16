---
title: 'Хозяин схемы без Windows Server 2003 с пакетом обновления 1 или более поздним'
TOCTitle: Хозяин схемы не под управлением Windows Server 2003 с пакетом обновления 1 или later_SchemaFSMONotWin2003SPn
ms:assetid: 644a85ca-7b36-4ed0-bd21-c64f2742df70
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.schemafsmonotwin2003spn(v=EXCHG.150)
ms:contentKeyID: 50488155
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Хозяин схемы не под управлением Windows Server 2003 с пакетом обновления 1 или later\_SchemaFSMONotWin2003SPn

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft Exchange Server 2007, поскольку на контроллере домена, которому назначена роль хозяина схемы службы каталогов Active Directory (FSMO, Flexible Single Master Operations), не установлена операционная система Microsoft Windows Server 2003 с пакетом обновления 1 (SP1) или более поздней версии.

Для установки Exchange 2007 требуется, чтобы контроллер домена, служащий схемой FSMO, работал под управлением Windows Server 2003 с пакетом обновления 1 или более поздней версии.

FSMO управляет всеми обновлениями и изменениями схемы службы каталогов Active Directory.

Чтобы устранить данную проблему, выполните одно или несколько из указанных ниже действий:

  - Обновите контроллер домена FSMO до Windows Server 2003 с пакетом обновления 1 (SP1) или более поздней версии, а затем повторно запустите программу установки Microsoft Exchange.

  - Если в организации Exchange имеется контроллер домена FSMO с операционной системой Microsoft Windows Server 2003 с пакетом обновления 1 (SP1) или более поздней версии, запустите программу установки Exchange 2007 с параметром /domaincontroller, указывающим на этот контроллер домена FSMO:
    
    \[*/DomainController* или */dc\<FQDN of domain controller\>*\]
    
    С помощью */DomainController* параметра укажите контроллер домена, который будет использоваться для чтения и записи данных Active Directory во время установки. Можно использовать формат NetBIOS или полное доменное имя.

Чтобы получить последний пакет обновления для Windows Server 2003, обратитесь к разделу «Технический центр Windows Server» ([https://go.microsoft.com/fwlink/?LinkId=45315](https://go.microsoft.com/fwlink/?linkid=45315)).

Дополнительные сведения о параметрах установки Exchange Server 2007 можно «Как для установки Exchange 2007 в автоматическом режиме» ([https://go.microsoft.com/fwlink/?LinkId=86476](https://go.microsoft.com/fwlink/?linkid=86476)) в документации Exchange Server 2007.

