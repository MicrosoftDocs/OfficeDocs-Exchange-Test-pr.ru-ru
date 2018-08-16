---
title: 'Не удается определить имя сайта Active Directory'
TOCTitle: Не удается определить имя сайта Active Directory_InvalidADSite
ms:assetid: ef96e077-08a0-4108-9f7d-0d61758abcd4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.invalidadsite(v=EXCHG.150)
ms:contentKeyID: 50489460
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Не удается определить имя сайта Active Directory\_InvalidADSite

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Невозможно продолжить установку Microsoft® Exchange Server 2007, так как этот сервер не принадлежит к допустимому сайту службы каталогов Active Directory®.

Сервер, который используется для установки Exchange 2007, должен принадлежать к допустимому сайту Active Directory.

Чтобы устранить эту проблему, убедитесь, что локальный сервер принадлежит к допустимому сайту Active Directory и запустите установку сервера Exchange Server 2007 снова.

Вы можете использовать параметр **/DsGetSite** программы командной строки Nltest.exe, чтобы проверить членство на сайте. Дополнительные сведения см. в статье "Nltest.exe: Обзор NLTest в разделе "Инструменты и параметры" *Технического справочника по Windows Server 2003* ([https://go.microsoft.com/fwlink/?LinkId=27734](https://go.microsoft.com/fwlink/?linkid=27734)).

Дополнительные сведения об устранении неполадок с Active Directory см. в разделе "Устранение неполадок с Active Directory" в справочнике *Windows Server 2003: Операции* (<https://go.microsoft.com/fwlink/?linkid=68099>).

