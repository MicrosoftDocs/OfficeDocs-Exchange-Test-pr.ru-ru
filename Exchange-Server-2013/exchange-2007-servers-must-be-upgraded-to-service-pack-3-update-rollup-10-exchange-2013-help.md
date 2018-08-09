---
title: 'Для серверов Exchange 2007 необходимо установить SP3 и UR10'
TOCTitle: Серверы Exchange 2007 необходимо обновить до пакета обновления 3 со сведением 10
ms:assetid: b8028a00-c451-412e-86f2-1669f6eee8fc
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.e15e12coexistenceminversionrequirement(v=EXCHG.150)
ms:contentKeyID: 50488933
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Серверы Exchange 2007 необходимо обновить до пакета обновления 3 со сведением 10

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Программа установки Microsoft Exchange Server 2013 не может продолжить работу так как она обнаружила, что на один или несколько серверов Exchange Server 2007 не был установлен Exchange Server 2007 с пакетом обновления 3 (SP3) для сведения 10 (RU10). Перед тем, как продолжить установку Exchange 2013, установите на все серверы Exchange 2007 в вашей организации Exchange 2007 с пакетом обновления 3 RU10. Это требование относится и к пограничным транспортным серверам Exchange 2007. Подробнее см. в разделе [Обновление с Exchange 2007 до Exchange 2013](upgrade-from-exchange-2007-to-exchange-2013-exchange-2013-help.md).

> [!IMPORTANT]  
> После обновления до Exchange 2007 SP3 RU10 Exchange 2007 пограничных транспортных серверов, необходимо повторно создать пограничную подписку между организацией Exchange и каждого пограничного транспортного сервера, чтобы обновить их версия сервера в службе каталогов Active Directory. Дополнительные сведения о повторном создании пограничные подписки в Exchange 2007<a href="https://go.microsoft.com/fwlink/?linkid=282699">Подписка пограничного транспортного сервера в организацию Exchange</a>см.

