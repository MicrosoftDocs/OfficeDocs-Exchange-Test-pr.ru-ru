---
title: 'Контроллер домена переопределен в реестре_ConfigDCHostNameMismatch: Exchange 2013 Help'
TOCTitle: Контроллер домена переопределен в реестре_ConfigDCHostNameMismatch
ms:assetid: 3aef5470-d510-4b59-a4b6-36d274a984ae
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.configdchostnamemismatch(v=EXCHG.150)
ms:contentKeyID: 50487856
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Контроллер домена переопределен в реестре\_ConfigDCHostNameMismatch

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-15_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft Exchange Server 2007, так как не удается использовать указанный контроллер домена. Контроллер домена статически назначен в реестре.

Для установки Exchange 2007 требуется, чтобы указанный в команде установки контроллер домена соответствовал контроллеру домена, статически назначенному с помощью переопределения в реестре.

Чтобы устранить данную проблему, запустите программу установки повторно и укажите статически назначенный контроллер домена для параметра **/DomainController: \<***FQDN of thestatically mapped domain controller***\>** .

Для получения дополнительных сведений о DSAccess и определение служб каталогов, увидеть статья базы знаний Майкрософт 250570, «Каталог службы обнаружения и DSAccess использования сервера» ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=250570](https://go.microsoft.com/fwlink/?linkid=3052&kbid=250570)).

