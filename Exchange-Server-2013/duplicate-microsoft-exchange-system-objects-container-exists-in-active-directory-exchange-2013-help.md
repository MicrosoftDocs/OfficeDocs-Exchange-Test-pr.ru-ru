﻿---
title: 'В Active Directory существует дубликат контейнера системных объектов Microsoft Exchange: Exchange 2013 Help'
TOCTitle: В Active Directory существует дубликат контейнера системных объектов Microsoft Exchange
ms:assetid: cd0f45ab-89de-4653-b50d-c1157c2329d5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.adiniterrorrule(v=EXCHG.150)
ms:contentKeyID: 50489090
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# В Active Directory существует дубликат контейнера системных объектов Microsoft Exchange

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2013-02-18_

Программа установки Microsoft Exchange Server 2013 не может продолжить работу, потому что в контексте именования домена Active Directory обнаружен дубликат контейнера системных объектов Microsoft Exchange. Когда программа установки находит дубликат контейнера системных объектов Microsoft Exchange, то перед продолжением ее работы необходимо удалить этот дубликат контейнера. Если существует дубликат контейнера системных объектов Microsoft Exchange, можно решить эту проблему, снова запустив **DomainPrep**. Необходимо обнаружить и удалить дубликат контейнера системных объектов Microsoft Exchange.

Чтобы устранить эту проблему, выполните следующие действия.

1.  Выполните вход в контроллер домена с административными учетными данными.

2.  В разделе **Администрирование** выберите **Пользователи и компьютеры Active Directory**.

3.  На панели консоли управления **Пользователи и компьютеры Active Directory** в меню панели инструментов нажмите кнопку **Просмотреть** и выберите **Дополнительные параметры**.

4.  Найдите дубликат контейнера системных объектов Microsoft Exchange.

5.  Убедитесь, что дубликат контейнера системных объектов Microsoft Exchange не содержит допустимых объектов Active Directory.

6.  Щелкните правой кнопкой мыши дубликат контейнера системных объектов Microsoft Exchange, а затем нажмите кнопку **Удалить**.

7.  Подтвердите удаление, нажав кнопку **Да** в диалоговом окне Active Directory.

> [!NOTE]  
> Если необходимо реплицировать изменения немедленно, следует начать репликацию между контроллерами домена вручную.


Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

