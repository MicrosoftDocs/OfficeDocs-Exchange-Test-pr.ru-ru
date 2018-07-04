---
title: 'Перемещение списка адресов: Exchange 2013 Help'
TOCTitle: Перемещение списка адресов
ms:assetid: c843bbd5-6c0e-41e1-b749-7ae87c1beb25
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124534(v=EXCHG.150)
ms:contentKeyID: 50489178
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Перемещение списка адресов

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-14_

В этом разделе объясняется, как перемещать существующий список адресов в новый контейнер корневого списка адресов.

Дополнительные сведения о задачах управления, связанных со списками адресов, см. в разделе [Процедуры списка адресов](address-list-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Списки адресов» в разделе [Разрешения для электронных адресов и адресных книг](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Невозможно использовать Центр администрирования Exchange (EAC) для выполнения этой процедуры. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной консоли Exchange для перемещения списка адресов

В данном примере для перемещения списка адресов в контейнер «Building 4», расположенный в контейнере «All Users\\Sales», используется идентификатор GUID списка адресов.

    Move-AddressList -Identity c3fffd8e-026b-41b9-88c4-8c21697ac8ac -Target "\All Users\Sales\Building4"

Введите **Y**, чтобы подтвердить перемещение этого списка адресов, и нажмите клавишу ВВОД.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Move-AddressList](https://technet.microsoft.com/ru-ru/library/bb124520\(v=exchg.150\)).

