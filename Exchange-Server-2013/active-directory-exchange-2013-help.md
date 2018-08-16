---
title: 'Active Directory: Exchange 2013 Help'
TOCTitle: Active Directory
ms:assetid: 8e8464df-2d1d-4d68-82de-b0c158c549c3
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb123715(v=EXCHG.150)
ms:contentKeyID: 50488606
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Active Directory

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Microsoft Exchange Server 2013 использует Active Directory для хранения и совместного использования данных каталога с Windows. Лес Active Directory для Exchange 2013 аналогичен Exchange Server 2010 кроме нескольких аспектов, рассмотренных ниже.

## Драйвер Active Directory

Драйвер Active Directory — это один из базовых компонентов сервера Microsoft Exchange, позволяющий службам Exchange создавать, изменять, удалять и запрашивать данные доменных служб Active Directory. В Exchange 2013 весь доступ к Active Directory производится с помощью самого драйвера Active Directory. Ранее, в Exchange 2010, DSAccess обеспечивал просмотр каталога для таких компонентов, как SMTP, агент передачи сообщений (MTA) и хранилище Exchange.

Кроме того, драйвер Active Directory использует возможности службы топологии Exchange Microsoft Active Directory (MSExchangeADTopology), которая позволяет драйверу Active Directory использовать данные топологии DSAccess (Directory Service Access). Эти данные включают список доступных контроллеров домена и серверов глобального каталога, которые доступны для обработки запросов Exchange. Дополнительные сведения о драйвере Active Directory см. в разделе [Доменные службы Active Directory](https://go.microsoft.com/fwlink/p/?linkid=110942).

## изменения схемы Active Directory

Exchange 2013 добавляет новые атрибуты к схеме служб домена Active Directory и вносит изменения в существующие классы и атрибуты. Дополнительные сведения о изменениях Active Directory при установке Exchange 2013 см. в разделе [Изменения схемы Active Directory в Exchange 2013](exchange-2013-active-directory-schema-changes-exchange-2013-help.md).

## Дополнительные сведения

Дополнительные сведения о том, как Exchange 2013 хранит и получает сведения в Active Directory и как можно планировать доступ к ней, см. в разделе [Доступ к Active Directory](access-to-active-directory-exchange-2013-help.md).

Дополнительные сведения о лесе Active Directory см. в разделе [Руководство по разработке AD DS](https://go.microsoft.com/fwlink/p/?linkid=264957).

Дополнительные сведения о компьютерах с операционной системой Windows в домене Active Directory и развертывании Exchange 2013 в домене, который имеет несвязанное пространство имен, см. в разделе [Сценарии несвязанных пространств имен](disjoint-namespace-scenarios-exchange-2013-help.md).

