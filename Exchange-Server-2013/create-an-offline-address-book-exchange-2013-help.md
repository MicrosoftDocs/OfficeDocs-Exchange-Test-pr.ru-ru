---
title: 'Создание автономной адресной книги: Exchange 2013 Help'
TOCTitle: Создание автономной адресной книги
ms:assetid: b57bb4ce-5b6e-4702-a2f8-04bf3898a861
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124339(v=EXCHG.150)
ms:contentKeyID: 50488944
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.Mailbox.NewOabWizardForm.OabIntroductionWizardPage
ms.translationtype: HT
---

# Создание автономной адресной книги

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-24_

Автономная адресная книга (OAB) в службе Exchange Server 2013 — это загруженная копия адресной книги, позволяющая пользователю Outlook получить доступ к информации во время отсоединения от сервера. Администраторы Exchange могут определять, какие адресные книги доступны пользователям, работающим автономно, и настраивать метод распространения адресных книг (через Интернет или через общедоступные папки).

Дополнительные задачи управления, связанные с автономными адресными книгами (OAB), см. в разделе [Процедуры автономной адресной книги](offline-address-book-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Автономные адресные книги» в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - По умолчанию Exchange Online роль "Список адресов" не назначена ни одной из групп ролей. Чтобы использовать командлеты, для которых требуется эта роль, ее необходимо добавить в группу ролей. Дополнительные сведения см. в разделе "Добавление роли в группу ролей" статьи [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

  - Невозможно использовать Центр администрирования Exchange (EAC) для выполнения этой процедуры. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной консоли для создания автономной адресной книги с распространением через Интернет

В этом примере создается автономная адресная книга OAB\_Contoso, использующая распространение через Интернет для клиентов Outlook 2007 или последующих версий, с помощью виртуального каталога по умолчанию.

    New-OfflineAddressBook -Name "OAB_Contoso" -AddressLists "\Default Global Address List" -VirtualDirectories $Null -GlobalWebDistributionEnabled $True

Подробные сведения о синтаксисе и параметрах см. в разделе [New-OfflineAddressBook](https://technet.microsoft.com/ru-ru/library/bb123692\(v=exchg.150\)).

