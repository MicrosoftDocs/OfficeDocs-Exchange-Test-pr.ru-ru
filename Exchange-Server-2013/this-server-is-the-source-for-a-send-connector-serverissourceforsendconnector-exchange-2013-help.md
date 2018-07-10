---
title: 'Этот сервер — источник соединителя отправки_ServerIsSourceForSendConnector: Exchange 2013 Help'
TOCTitle: Этот сервер — источник соединителя отправки_ServerIsSourceForSendConnector
ms:assetid: 151c0014-c90c-4c52-8e74-4b3f1bc7aaf1
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.serverissourceforsendconnector(v=EXCHG.150)
ms:contentKeyID: 50487493
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Этот сервер — источник соединителя отправки\_ServerIsSourceForSendConnector

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft Exchange Server 2007, потому что не удается удалить роль транспортного сервера-концентратора. Локальный компьютер — это источник одного или нескольких соединителей отправки в организации Exchange.

Соединитель отправки — это логический шлюз, через который отправляются исходящие сообщения.

Перед удалением роли сервера с компьютера с ролью транспортного сервера-концентратора необходимо переместить или удалить все соединители отправки для организации Exchange.

Чтобы устранить эту проблему, переместите или удалите с локального компьютера все соединители отправки, а затем повторно запустите программу установки.

Дополнительные сведения об изменении и перемещении соединителей отправки см. в следующих разделах документации на сервер Exchange Server 2007:

  - "Инструкции по удалению соединителя отправки" ([https://go.microsoft.com/fwlink/?LinkId=86655](https://go.microsoft.com/fwlink/?linkid=86655)).

  - "Инструкции по изменению настройки соединителя отправки" ([https://go.microsoft.com/fwlink/?LinkId=86656](https://go.microsoft.com/fwlink/?linkid=86656)).

