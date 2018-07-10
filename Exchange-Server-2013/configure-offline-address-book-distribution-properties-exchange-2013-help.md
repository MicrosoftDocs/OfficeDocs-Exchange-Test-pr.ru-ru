---
title: 'Настройка свойств распространения автономной адресной книги: Exchange 2013 Help'
TOCTitle: Настройка свойств распространения автономной адресной книги
ms:assetid: 8df985e9-75ba-47ea-9cc3-aa98a5d8acf4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb123710(v=EXCHG.150)
ms:contentKeyID: 50488601
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.ClientAccess.OabDistributionGeneralPage
ms.translationtype: HT
---

# Настройка свойств распространения автономной адресной книги

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-14_

Для каждой точки распространения автономной адресной книги сервера Exchange Server 2010 можно настроить два URL-адреса: внутренний URL-адрес, к которому можно получить доступ только из внутренней корпоративной сети, и внешний URL-адрес, к которому можно получить доступ из Интернета.

Дополнительные задачи управления, связанные с автономными адресными книгами (OAB), см. в разделе [Процедуры автономной адресной книги](offline-address-book-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Автономные адресные книги" в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Невозможно использовать Центр администрирования Exchange (EAC) для выполнения этой процедуры. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование консоли для настройки свойств распространения автономной адресной книги

В этом примере устанавливается интервал опроса в шесть часов для распространения автономной адресной книги в виртуальном каталоге автономной адресной книги с именем OAB (веб-сайт по умолчанию).

    Set-OABVirtualDirectory "OAB (Default Web Site)" -PollInterval 360

В этом примере в качестве внешней точки распространения устанавливается адрес https://contoso.com/OAB для виртуального каталога автономной адресной книги с именем OAB (веб-сайт по умолчанию).

    Set-OABVirtualDirectory "OAB (Default Web Site)" -ExternalUrl https://contoso.com/OAB

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-OabVirtualDirectory](https://technet.microsoft.com/ru-ru/library/bb124707\(v=exchg.150\)).

## Дополнительные сведения

[автономные адресные книги,](offline-address-books-exchange-2013-help.md)

