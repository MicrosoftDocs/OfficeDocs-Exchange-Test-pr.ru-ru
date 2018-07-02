---
title: 'Контрольный список: Обновление с Exchange 2010: Exchange 2013 Help'
TOCTitle: 'Контрольный список: Обновление с Exchange 2010'
ms:assetid: 06c1045a-5fcf-4e24-a901-1a979302fb8d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee332309(v=EXCHG.150)
ms:contentKeyID: 51407997
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Контрольный список: Обновление с Exchange 2010

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-07_

Используйте этот контрольный список для обновления Microsoft Exchange 2010 до версии Exchange 2013. Перед началом работы с этим контрольным списком необходимо прочитать следующие разделы.

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


## Контрольный список для обновления Exchange 2010 до Exchange 2013


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
<td><p>1. Прочитайте заметки о выпуске.</p></td>
<td><p><a href="release-notes-for-exchange-2013-exchange-2013-help.md">Заметки о выпуске Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>2. Проверьте системные требования.</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Требования к системе для установки Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>3. Подтвердите выполнение предварительных действий.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Предварительные требования для Exchange 2013</a></p>
<p><a href="deployment-security-checklist-exchange-2013-help.md">Контрольный список по безопасности развертывания</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
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
<td><p>5. Выберите автономную адресную книгу для всех баз данных почтовых ящиков Exchange 2010.</p></td>
<td><p><a href="manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md">Set mailbox database properties</a> в <a href="manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md">Управление базами данных почтовых ящиков в Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>6. Установите Exchange 2013.</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Установка Exchange 2013 с помощью мастера установки</a></p>
<p><a href="install-the-exchange-2013-edge-transport-role-using-the-setup-wizard-exchange-2013-help.md">Установка роли пограничного транспортного сервера Exchange 2013 с помощью мастера установки</a></p>
<p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Проверка установки Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>7. Создайте почтовый ящик Exchange 2013.</p></td>
<td><p><a href="create-user-mailboxes-exchange-2013-help.md">Создание почтовых ящиков пользователя</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>8. Настройте связанные с Exchange виртуальные каталоги.</p>
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

</td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Конфигурация сервера клиентского доступа Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>9. Добавьте цифровые сертификаты для сервера клиентского доступа.</p></td>
<td><p><a href="digital-certificates-and-ssl-exchange-2013-help.md">Цифровые сертификаты и протокол SSL</a></p>
<p></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>10. Переместите почтовый ящик разрешения конфликтов.</p></td>
<td><p><a href="move-the-exchange-2010-system-mailbox-to-exchange-2013-exchange-2013-help.md">Перемещение системного почтового ящика Exchange 2010 в Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>11. Настройте единую систему обмена сообщениями.</p>
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
<td><p><a href="upgrade-exchange-2010-um-to-exchange-2013-um-exchange-2013-help.md">Обновление единой системы обмена сообщениями Exchange 2010 до Exchange 2013</a></p>
<p></p></td>
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
<td><p></p></td>
<td><p>13. Включите и настройте мобильный Outlook.</p></td>
<td><p><a href="outlook-anywhere-exchange-2013-help.md">Мобильный Outlook</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>14. Настройте точку подключения службы.</p></td>
<td><p><a href="exchange-2013-client-access-server-configuration-exchange-2013-help.md">Конфигурация сервера клиентского доступа Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>15. Настройте записи DNS.</p></td>
<td><p><a href="https://technet.microsoft.com/ru-ru/library/dn307232(v=exchg.150)">Настройка записей DNS для установки Exchange 2010 с несколькими серверами</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>16. Переместите почтовые ящики из Exchange 2010 в Exchange 2013.</p></td>
<td><p><a href="mailbox-moves-in-exchange-2013-exchange-2013-help.md">Перемещение почтовых ящиков в Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>17. Переместите данные общедоступных папок с Exchange 2013 на Exchange 2013.</p></td>
<td><p><a href="public-folders-exchange-2013-help.md">Общедоступные папки</a></p>
<p><a href="https://technet.microsoft.com/ru-ru/library/jj150486(v=exchg.150)">Использование последовательной миграции для переноса общедоступных папок в Exchange 2013 из предыдущих версий</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>18. Задачи, выполняемые после установки.</p></td>
<td><p><a href="exchange-2013-post-installation-tasks-exchange-2013-help.md">Задачи после установки Exchange 2013</a></p></td>
</tr>
</tbody>
</table>

