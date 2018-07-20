---
title: 'Задачи управления виртуального каталога Exchange ActiveSync: Exchange 2013 Help'
TOCTitle: Задачи управления виртуального каталога Exchange ActiveSync
ms:assetid: f0b339b7-e184-4392-a133-20523183459d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb125170(v=EXCHG.150)
ms:contentKeyID: 50489438
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Задачи управления виртуального каталога Exchange ActiveSync

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-05_

Может управлять некоторые параметры приложения Exchange ActiveSync в Exchange Server 2013 через Exchange ActiveSync виртуальный каталог. Виртуальный каталог используется Internet Information Services (IIS) для разрешения доступа к веб-приложения, такие как Exchange ActiveSync. Перечислены некоторые параметры виртуального каталога, которые могут управлять для Exchange ActiveSync проверки подлинности, безопасности и отчеты.

## Параметры виртуального каталога Exchange ActiveSync

Можно изменить следующие свойства и параметры в виртуальном каталоге Exchange ActiveSync:

  - **InternalURL** InternalURL — это URL-адрес, внутренних клиентов можно использовать для доступа к виртуальному каталогу. Обычно это в https://servername/Microsoft-Server-ActiveSync формате. Например если имя NetBIOS сервера Sequoia, InternalURL будет https://sequoia/Microsoft-Server-ActiveSync.

  - **ExternalURL** ExternalURL — это URL-адрес, внешние клиенты могут использовать для доступа к виртуальному каталогу. Этот URL-адрес должен быть доступен из за пределами внутренней сети. Например ваш ExternalURL может быть https://www.contoso.com/.

  - **Параметры проверки подлинности** Два метода проверки подлинности, которые можно выбрать для виртуального каталога Exchange ActiveSync, обычная проверка подлинности и проверка подлинности сертификата клиента.

