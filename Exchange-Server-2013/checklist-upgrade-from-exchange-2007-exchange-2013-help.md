---
title: 'Контрольный список: Обновление с Exchange 2007: Exchange 2013 Help'
TOCTitle: 'Контрольный список: Обновление с Exchange 2007'
ms:assetid: 53aaa370-4562-43e4-9b75-7a705400c5a5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff805032(v=EXCHG.150)
ms:contentKeyID: 51408029
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Контрольный список: Обновление с Exchange 2007

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2016-12-09_

Используйте этот контрольный список для обновления Microsoft Exchange Server 2007 до версии Exchange Server 2013. Перед началом работы с этим контрольным списком необходимо прочитать следующие разделы.

  - [Планирование и развертывание](planning-and-deployment-for-exchange-2013-installation-instructions.md)

  - [Новые возможности в Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md)

Этот контрольный список содержит стандартное руководство для типичного сценария обновления.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Помощник по развертыванию Exchange Server предоставляет специализированное пошаговое руководство по развертыванию сервера Exchange Server. Он поможет вам развернуть новую установку Exchange Server 2013, обновить предыдущую версию к Exchange 2013 или настроить гибридное развертывание Exchange 2013 и Exchange Online. Дополнительные сведения см. в разделе <a href="exchange-server-deployment-assistant-exchange-2013-help.md">Помощник по развертыванию Exchange Server</a>.</td>
</tr>
</tbody>
</table>


## Контрольный список для обновления Exchange 2007 до Exchange 2013


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Готово?</p></td>
<td><p>Задача</p></td>
<td><p>Раздел (-ы)</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>1. Прочитайте заметки о выпуске.</p></td>
<td><p><a href="release-notes-for-exchange-2013-exchange-2013-help.md">Заметки о выпуске Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>2. Проверка системных требований</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Требования к системе для установки Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>3. Подтвердите выполнение предварительных действий.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Предварительные требования для Exchange 2013</a></p>
<p><a href="deployment-security-checklist-exchange-2013-help.md">Контрольный список по безопасности развертывания</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>4. Настройте несвязанное пространство имен.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Это действие является необязательным. Оно необходимо, только если в организации используется несвязанное пространство имен.</td>
</tr>
</tbody>
</table>

</td>
<td><p><a href="configure-the-dns-suffix-search-list-for-a-disjoint-namespace-exchange-2013-help.md">Настройка списка поиска DNS-суффиксов для несвязанного пространства имен</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>5. Выберите автономную адресную книгу для всех баз данных почтовых ящиков Exchange 2007.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/?linkid=320546">Подготовка получателей для загрузки автономных адресных книг</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>6. Создайте имя узла для прежних версий Exchange.</p></td>
<td><p><a href="https://technet.microsoft.com/ru-ru/library/dn130105(v=exchg.150)">Создание устаревшего имени узла Exchange</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>7. Установите Exchange 2013.</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Установка Exchange 2013 с помощью мастера установки</a></p>
<p><a href="install-the-exchange-2013-edge-transport-role-using-the-setup-wizard-exchange-2013-help.md">Установка роли пограничного транспортного сервера Exchange 2013 с помощью мастера установки</a></p>
<p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Проверка установки Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>8. Создайте почтовый ящик Exchange 2013.</p></td>
<td><p><a href="create-user-mailboxes-exchange-2013-help.md">Создание почтовых ящиков пользователя</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>9. Настройте связанные с Exchange виртуальные каталоги.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Это действие необходимо, только если планируется использовать веб-службы Exchange, мобильный Outlook или автономную адресную книгу. Он также может потребоваться, если необходимо изменить какие-либо параметры по умолчанию для панели управления Exchange, Microsoft Office Outlook Web App или Exchange ActiveSync.<br />
</td>
</tr>
</tbody>
</table>

<p></p></td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Конфигурация сервера клиентского доступа Exchange 2013</a></p>
<p></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>10. Настройте сертификаты Exchange 2013.</p></td>
<td><p><a href="digital-certificates-and-ssl-exchange-2013-help.md">Цифровые сертификаты и протокол SSL</a></p>
<p></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>11. Настройте сертификаты Exchange 2007.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/?linkid=320553">Управление протоколом SSL на сервере клиентского доступа</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>12. Настройте пограничный транспортный сервер.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Это действие является необязательным. Оно необходимо, только если в организации используется пограничный транспортный сервер.</td>
</tr>
</tbody>
</table>

</td>
<td><p><a href="configure-internet-mail-flow-through-a-subscribed-edge-transport-server-exchange-2013-help.md">Настройка потока почты Интернета через подписанный пограничный транспортный сервер</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>13. Настройте единую систему обмена сообщениями.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Это действие является необязательным. Оно необходимо, только если в организации требуется использовать единую систему обмена сообщениями.</td>
</tr>
</tbody>
</table>

</td>
<td><p><a href="planning-for-unified-messaging-exchange-2013-help.md">Планирование единой системы обмена сообщениями</a></p>
<p><a href="deploy-exchange-2013-um-exchange-2013-help.md">Развертывание единой системы обмена сообщениями Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>14. Включите и настройте мобильный Outlook.</p></td>
<td><p><a href="outlook-anywhere-exchange-2013-help.md">Мобильный Outlook</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>15. Настройте точку подключения службы.</p></td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Конфигурация сервера клиентского доступа Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>16. Настройте URL-адреса Exchange 2007.</p></td>
<td><p><a href="https://technet.microsoft.com/ru-ru/library/dn282262(v=exchg.150)">Настройка внешних URL-адресов Exchange 2007</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>17. Настройте записи DNS.</p></td>
<td><p><a href="https://technet.microsoft.com/ru-ru/library/dn283988(v=exchg.150)">Настройка DNS-записей при установке Exchange 2007 на несколько серверов</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>18. Переместите почтовые ящики с Exchange 2007 на Exchange 2013.</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Перемещение почтовых ящиков в Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>19. Переместите данные общедоступных папок с Exchange 2013 на Exchange 2013.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Это действие является необязательным. Оно необходимо, только если в организации используются общедоступные папки.</td>
</tr>
</tbody>
</table>

</td>
<td><p><a href="public-folders-exchange-2013-help.md">Общедоступные папки</a></p>
<p><a href="https://technet.microsoft.com/ru-ru/library/jj150486(v=exchg.150)">Использование последовательной миграции для переноса общедоступных папок в Exchange 2013 из предыдущих версий</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>20. Задачи, выполняемые после установки.</p></td>
<td><p><a href="exchange-2013-post-installation-tasks-exchange-2013-help.md">Задачи после установки Exchange 2013</a></p></td>
</tr>
</tbody>
</table>

