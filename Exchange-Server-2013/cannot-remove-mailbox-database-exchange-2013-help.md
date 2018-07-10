---
title: 'Невозможно удалить базу данных почтовых ящиков: Exchange 2013 Help'
TOCTitle: Невозможно удалить базу данных почтовых ящиков
ms:assetid: 5881e4c0-c2e2-48db-84b4-7f9ce3cf46a7
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.unwillingtoremovemailboxdatabase(v=EXCHG.150)
ms:contentKeyID: 50488088
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Невозможно удалить базу данных почтовых ящиков

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2012-11-08_

Установку Microsoft Exchange Server 2013 не удается продолжить, так как она не может удалить базу данных почтовых ящиков с локального сервера без потенциальной потери данных.

Программа установки Exchange 2013 определяет, были ли удалены все базы данных почтовых ящиков с сервера, перед удалением роли сервера почтовых ящиков. Однако почтовые ящики пользователей могут остаться на сервере.

Чтобы устранить данную проблему, переместите все почтовые ящики, имеющиеся на сервере, на другой сервер Exchange Server, или, если почтовые ящики и данные в них неактуальны, отключите почтовые ящики. Запустите программу установки Exchange 2013 повторно.

  - Дополнительные сведения об определении почтового ящика в базе данных см. в разделе [Get-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123685\(v=exchg.150\)).

  - Дополнительные сведения о перемещении почтового ящика см. в разделе [Перемещение почтовых ящиков в Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md).

  - Дополнительные сведения об отключении почтового ящика см. в разделе [Disable-Mailbox](https://technet.microsoft.com/ru-ru/library/aa997210\(v=exchg.150\)).

  - Дополнительные сведения об удалении базы данных почтовых ящиков см. в разделе [Управление базами данных почтовых ящиков в Exchange 2013](manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md).

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

