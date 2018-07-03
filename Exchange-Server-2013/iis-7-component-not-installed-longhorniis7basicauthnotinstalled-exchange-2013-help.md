﻿---
title: 'Компонент IIS 7 не установлен_LonghornIIS7BasicAuthNotInstalled: Exchange 2013 Help'
TOCTitle: Компонент IIS 7 не установлен_LonghornIIS7BasicAuthNotInstalled
ms:assetid: 2eb3290c-9ce2-4c01-ad47-a26ef60bddb5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.longhorniis7basicauthnotinstalled(v=EXCHG.150)
ms:contentKeyID: 50487740
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Компонент IIS 7 не установлен\_LonghornIIS7BasicAuthNotInstalled

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2015-03-09_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

С помощью программы установки Microsoft Exchange Server 2010 или Microsoft Exchange Server 2007 невозможно установить роль сервера клиентского доступа (CAS) или роль сервера почтовых ящиков на компьютере под управлением Microsoft Windows Server 2008 или Windows Server 2008 R2, так как не установлены необходимые компоненты IIS 7.

Программы установки Exchange 2010 и Exchange 2007 требуют, чтобы на компьютере под управлением Windows Server 2008 или Windows Server 2008 R2, на который устанавливается роль сервера клиентского доступа, уже были установлены указанные ниже компоненты IIS 7.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Компоненты IIS 7 для установки роли сервера клиентского доступа</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Сжатие динамического содержимого</p></td>
</tr>
<tr class="even">
<td><p>Сжатие статического содержимого</p></td>
</tr>
<tr class="odd">
<td><p>Обычная проверка подлинности</p></td>
</tr>
<tr class="even">
<td><p>Проверка подлинности Windows</p></td>
</tr>
<tr class="odd">
<td><p>Дайджест-проверка подлинности IIS 7</p></td>
</tr>
<tr class="even">
<td><p>ASP.NET</p></td>
</tr>
<tr class="odd">
<td><p>Сопоставление сертификатов клиентов</p></td>
</tr>
<tr class="even">
<td><p>Просмотр каталогов</p></td>
</tr>
<tr class="odd">
<td><p>Ошибки HTTP</p></td>
</tr>
<tr class="even">
<td><p>Ведение журнала HTTP</p></td>
</tr>
<tr class="odd">
<td><p>Перенаправление HTTP</p></td>
</tr>
<tr class="even">
<td><p>Трассировка</p></td>
</tr>
<tr class="odd">
<td><p>Фильтры ISAPI</p></td>
</tr>
<tr class="even">
<td><p>Монитор запросов</p></td>
</tr>
<tr class="odd">
<td><p>Статическое содержимое</p></td>
</tr>
</tbody>
</table>


Программы установки Exchange 2010 и Exchange 2007 требуют, чтобы на компьютере под управлением Windows Server 2008 или Windows Server 2008 R2, на который устанавливается роль сервера почтовых ящиков, уже были установлены указанные ниже компоненты IIS 7.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Компоненты IIS 7 для установки роли сервера почтовых ящиков</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Обычная проверка подлинности</p></td>
</tr>
<tr class="even">
<td><p>Проверка подлинности Windows</p></td>
</tr>
</tbody>
</table>


Чтобы устранить эту проблему, выполните соответствующие действия по установке необходимых компонентов IIS 7 на целевом компьютере и затем снова запустите программу установки Microsoft Exchange.

Установка компонентов IIS 7 для роли сервера клиентского доступа с помощью диспетчера сервера Windows Server 2008

1.  Нажмите кнопку **Пуск** и выберите пункт **Администрирование**, а затем — **Диспетчер сервера**.

2.  В области навигации разверните элемент **Роли**, щелкните правой кнопкой мыши элемент **Веб-сервер (IIS)** и выберите элемент **Добавить службы ролей**.

3.  На панели **Выбор служб ролей** прокрутите список вниз и выберите пункт **IIS**.

4.  В области **Безопасность** установите следующие флажки:
    
      - **Обычная проверка подлинности**
    
      - **Дайджест-проверка подлинности**
    
      - **Проверка подлинности Windows**

5.  В области **Производительность** установите следующие флажки:
    
      - **Статическое сжатие**
    
      - **Динамическое сжатие**

6.  На панели **Выбор служб ролей** нажмите кнопку **Далее**, а затем — кнопку **Установить** на панели **Подтвердите выбранные элементы**.

7.  Выберите элемент **Закрыть**, чтобы завершить работу мастера добавления ролей.

Установка компонентов IIS 7 для роли сервера почтовых ящиков с помощью диспетчера сервера Windows Server 2008

1.  Нажмите кнопку **Пуск** и выберите пункт **Администрирование**, а затем — **Диспетчер сервера**.

2.  В области навигации разверните элемент **Роли**, щелкните правой кнопкой мыши элемент **Веб-сервер (IIS)** и выберите элемент **Добавить службы ролей**.

3.  На панели **Выбор служб ролей** прокрутите список вниз и выберите пункт **IIS**.

4.  В области **Безопасность** установите следующие флажки:
    
      - **Обычная проверка подлинности**
    
      - **Проверка подлинности Windows**

5.  На панели **Выбор служб ролей** нажмите кнопку **Далее**, а затем — кнопку **Установить** на панели **Подтвердите выбранные элементы**.

6.  Выберите элемент **Закрыть**, чтобы завершить работу мастера добавления ролей.
