---
title: 'Изменение параметров политики адресной книги: Exchange 2013 Help'
TOCTitle: Изменение параметров политики адресной книги
ms:assetid: ba1ca350-71c2-4c60-a612-33bfa9320b5e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh529941(v=EXCHG.150)
ms:contentKeyID: 50488999
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Изменение параметров политики адресной книги

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2016-03-30_

После создания политики адресной книги можно просмотреть или изменить имя и назначенный глобальный список адресов (GAL), автономную адресную книгу (OAB), список помещений и списки адресов.

Дополнительные сведения об управленческих задачах, связанных с политиками адресных книг, см. в разделе [Процедуры политики адресной книги](address-book-policy-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Оценка времени выполнения: менее 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись «Политики адресных книг» в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Создание политики адресной книги для организации — это многоэтапный процесс, требующий планирования. Дополнительные сведения см. в разделе [Сценарий. Развертывание политик адресных книг](scenario-deploying-https://docs.microsoft.com/ru-ru/exchange/address-books/address-book-policies/address-book-policies)

  - Невозможно использовать Центр администрирования Exchange (EAC) для настройки политики адресной книги. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

  - Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Что необходимо сделать?

## Изменение автономной адресной книги, списка помещений и глобального списка адресов для политики адресной книги

В этом примере изменяется автономная адресная книга, список помещений и глобальный список адресов, которые будут использоваться пользователями почтовых ящиков, назначенными политике адресной книги «All Fabrikam ABP».

    Set-AddressBookPolicy -Identity "All Fabrikam ABP" -OfflineAddressBook \Fabrikam-OAB-2 -GlobalAddressList "\All Fabrikam GAL" -RoomList "\All Fabrikam Rooms"

## Замена списков адресов в политике адресной книги

Списки адресов, указанные для существующей политики адресной книги, заменяют все списки адресов в ней.

В этом примере заменяются имеющиеся списки адресов GovernmentAgencyA-Atlanta и GovernmentAgencyA-Moscow для политики адресной книги Government Agency A.

    Set-AddressBookPolicy -Identity "Government Agency A" -AddressLists "GovernmentAgencyA-Atlanta","GovernmentAgencyA-Moscow"

## Добавление списков адресов в политику адресной книги

Чтобы сохранить списки адресов, которые уже определены в политике адресной книги, необходимо указать их при добавлении новых списков к политике.

В этом примере список адресов Contoso-Chicago добавляется к политике ABP Contoso, которая уже настроена на использование списка адресов Contoso-Seattle.

    Set-AddressBookPolicy -Identity "ABP Contoso" -AddressLists "Contoso-Chicago","Contoso-Seattle"

## Удаление списков адресов из политики адресной книги

Чтобы удалить имеющиеся списки адресов, которые уже определены в политике адресной книги, необходимо указать, какие списки нужно сохранить.

К примеру, политика адресной книги ABP Fabrikam использует списки адресов Fabrikam-HR и Fabrikam-Finance. Чтобы удалить список адресов Fabrikam-HR из политики адресной книги, укажите список адресов Fabrikam-Finance, который нужно сохранить.

    Set-AddressBookPolicy -Identity "ABP Fabrikam" -AddressLists Fabrikam-Finance

## Дополнительные сведения

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-AddressBookPolicy](https://technet.microsoft.com/ru-ru/library/hh529945\(v=exchg.150\)).

