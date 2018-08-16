---
title: 'Удаление глобального списка адресов: Exchange 2013 Help'
TOCTitle: Удаление глобального списка адресов
ms:assetid: 65d75b69-641b-4a37-a63c-47cf018f5f22
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb232077(v=EXCHG.150)
ms:contentKeyID: 50488335
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Удаление глобального списка адресов

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2014-12-16_

Глобальный список адресов — это каталог, содержащий записи для всех групп, пользователей и контактов в организации Exchange.

Дополнительные сведения о задачах управления, связанных со списками адресов, см. в разделе [Процедуры списка адресов](address-list-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Списки адресов" в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - По умолчанию Exchange Online роль "Список адресов" не назначена ни одной из групп ролей. Чтобы использовать командлеты, для которых требуется эта роль, ее необходимо добавить в группу ролей. Дополнительные сведения см. в разделе "Добавление роли в группу ролей" статьи [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

  - Невозможно удалить глобальный список адресов по умолчанию.

  - Невозможно использовать Центр администрирования Exchange (EAC) для выполнения этой процедуры. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной консоли Exchange для удаления глобального списка адресов

В этом примере показано, как удалить глобальный список адресов компании Fourth Coffee из контроллера домена ad-server.fourthcoffee.com.

    Remove-GlobalAddressList -Identity "Fourth Coffee" -DomainController ad-server.fourthcoffee.com

Чтобы подтвердить удаление глобального списка адресов, введите **Y** и нажмите клавишу ВВОД.

Подробные сведения о синтаксисе и параметрах см. в разделе [Remove-GlobalAddressList](https://technet.microsoft.com/ru-ru/library/bb124368\(v=exchg.150\)).

