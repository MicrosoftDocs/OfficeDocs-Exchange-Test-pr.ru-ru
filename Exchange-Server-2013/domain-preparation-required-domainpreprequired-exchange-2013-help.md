---
title: 'Необходимая подготовка домена_DomainPrepRequired: Exchange 2013 Help'
TOCTitle: Необходимая подготовка домена_DomainPrepRequired
ms:assetid: f6feae6f-7404-4b1f-887f-ed63c26a6bcd
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.domainpreprequired(v=EXCHG.150)
ms:contentKeyID: 50489545
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Необходимая подготовка домена\_DomainPrepRequired

 

_**Применимо к:**Exchange Server_

_**Последнее изменение раздела:**2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft Exchange Server 2007 из-за сбоя установки роли сервера.

Для установки Microsoft Exchange перед установкой определенных ролей Exchange Server 2007 необходимо выполнить подготовку локального домена.

Подготовка домена для установки сервера Exchange Server 2007 состоит из следующих задач:

  - установка разрешений на контейнер домена для серверов Exchange Server, администраторов организации Exchange, пользователей, прошедших проверку подлинности, и администраторов почтовых ящиков Exchange;

  - создание контейнера системных объектов Microsoft Exchange (если такой контейнер не существует) и установка разрешений на этот контейнер для серверов Exchange Server, администраторов организации Exchange и пользователей, прошедших проверку подлинности;

  - создание в текущем домене новой глобальной группы домена с названием «Серверы домена Exchange»;

  - добавление группы «Серверы домена Exchange» в универсальную группу безопасности «Серверы Exchange» в корневом домене.

Чтобы устранить данную проблему, выполните команду **setup /PrepareDomain** для подготовки локального домена и запустите установку роли сервера повторно.

Дополнительные сведения о выполнении процесса PrepareD см. в статье "Инструкции по подготовке службы Active Directory и доменов" ([https://go.microsoft.com/fwlink/?LinkId=78453](https://go.microsoft.com/fwlink/?linkid=78453)).

