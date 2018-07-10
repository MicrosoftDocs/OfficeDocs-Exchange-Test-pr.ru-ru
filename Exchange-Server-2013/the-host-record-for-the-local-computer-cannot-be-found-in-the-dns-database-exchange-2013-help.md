---
title: 'Невозможно найти запись узла для локального компьютера в базе данных DNS: Exchange 2013 Help'
TOCTitle: Невозможно найти запись узла для локального компьютера в базе данных DNS
ms:assetid: 2f18cb65-29fe-4b72-8d68-52fd503d5673
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.hostrecordmissing(v=EXCHG.150)
ms:contentKeyID: 50487743
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Невозможно найти запись узла для локального компьютера в базе данных DNS

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Установку Microsoft Exchange Server 2013 невозможно продолжить, так как нельзя найти запись узла (A) для этого компьютера в базе данных службы доменных имен (DNS).

Для установки Exchange 2013 необходимо, чтобы на местном компьютере допустимая запись узла (A) была внесена в доверенную базу данных DNS.

Exchange зависит от записей узла (A) DNS для IP-адреса его следующего внутреннего или внешнего конечного сервера.

Чтобы устранить эту проблему, выполните следующие действия:

  - Убедитесь, что локальная настройка TCP/IP указывает на правильный сервер DNS. Дополнительные сведения см. на странице [Настройка параметров TCP/IP](https://go.microsoft.com/fwlink/p/?linkid=108281).

  - С помощью команды nslookup.exe убедитесь в существовании записи узла (А) на DNS-сервере. Дополнительные сведения см. в разделе [Проверка существования записей ресурсов "А" в службе DNS](https://go.microsoft.com/fwlink/?linkid=63001).

Чтобы узнать о разрешении DNS-имен, устранении неполадок и записях узла (A) см. указанные ниже статьи.

  - [Устранение неполадок DNS](https://go.microsoft.com/fwlink/p/?linkid=294828)

  - [Управление записями ресурсов](https://go.microsoft.com/fwlink/p/?linkid=294829)

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

