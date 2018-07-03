---
title: 'На локальном компьютере уже запущен сервер Exchange Server_ExchangeAlreadyInstalled: Exchange 2013 Help'
TOCTitle: На локальном компьютере уже запущен сервер Exchange Server_ExchangeAlreadyInstalled
ms:assetid: 3f168b5d-9910-418f-86fb-e99d852dcb5e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.exchangealreadyinstalled(v=EXCHG.150)
ms:contentKeyID: 50487944
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# На локальном компьютере уже запущен сервер Exchange Server\_ExchangeAlreadyInstalled

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2012-06-05_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Продолжение установки Microsoft® Exchange Server 2007 невозможно, поскольку на локальном компьютере уже установлены компоненты Microsoft Exchange.

Для установки Exchange 2007 требуется, чтобы на локальном компьютере не было установлено никаких компонентов Microsoft Exchange.

Для решения этой проблемы удалите все компоненты Microsoft Exchange 2000 Server или Microsoft Exchange Server 2003 и затем повторно запустите программу установки Microsoft Exchange.

Чтобы удалить компоненты Microsoft Exchange

1.  Нажмите кнопку **Пуск**, выделите пункт **Настройка** и выберите **Панель управления**.

2.  Дважды щелкните **Установка и удаление программ**.

3.  В списке **Установленные программы** щелкните **Microsoft Exchange** и нажмите кнопку **Изменить/удалить**.

4.  В окне мастера установки Microsoft Exchange нажмите кнопку **Далее**.

5.  В списке действий на странице "Выбор компонентов" щелкните стрелку вниз рядом с каждым установленным компонентом и затем нажмите кнопку **Удалить**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Установленные компоненты помечены галочками в списке &quot;Действие&quot;. При нажатии кнопки <strong>Удалить</strong> каждая галочка заменяется словом <strong>Удаление</strong>.</td>
    </tr>
    </tbody>
    </table>


6.  Дважды нажмите кнопку **Далее**.

7.  Нажмите кнопку **Готово**.

