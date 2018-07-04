---
title: 'Изменение расписания создания автономной адресной книги: Exchange 2013 Help'
TOCTitle: Изменение расписания создания автономной адресной книги
ms:assetid: d2b4d527-311e-442d-9f1f-54fac8371b80
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124719(v=EXCHG.150)
ms:contentKeyID: 50489136
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.Mailbox.OfflineAddressBookGeneralPage
ms.translationtype: MT
---

# Изменение расписания создания автономной адресной книги

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-12-05_

Автономная адресная книга — это загруженная копия адресной книги, которая позволяет пользователям Outlook получать доступ к содержащимся в ней сведениям вне подключения к серверу. Можно настроить частоту создания автономной адресной книги с помощью параметров *OABGeneratorWorkCycle* и *OABGeneratorWorkCycleCheckpoint* командлета Set-MailboxServer.

Дополнительные задачи управления, связанные с автономными адресными книгами (OAB), см. в разделе [Процедуры автономной адресной книги](offline-address-book-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Автономные адресные книги» в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Невозможно использовать Центр администрирования Exchange для выполнения этой процедуры. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной консоли для настройки свойств автономной адресной книги

В этом примере автономная адресная книга создается каждые шесть часов каждый день на сервере почтовых ящиков MBXServer01.

    Set-MailboxServer -Identity MBXServer01 -OABGeneratorWorkCycle 01.00:00:00 -OABGeneratorWorkCycleCheckpoint 06:00:00 

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-OfflineAddressBook](https://technet.microsoft.com/ru-ru/library/aa996330\(v=exchg.150\)).

