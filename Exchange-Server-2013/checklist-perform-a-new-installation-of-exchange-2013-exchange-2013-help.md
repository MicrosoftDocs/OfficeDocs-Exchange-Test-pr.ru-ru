---
title: 'Контрольный список: Выполнение новой установки Exchange 2013: Exchange 2013 Help'
TOCTitle: 'Контрольный список: Выполнение новой установки Exchange 2013'
ms:assetid: f70d9dd3-7370-472e-b05e-1ea1671272b2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff805042(v=EXCHG.150)
ms:contentKeyID: 50489547
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Контрольный список: Выполнение новой установки Exchange 2013

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Используйте этот контрольный список для развертывания Microsoft Exchange Server 2013. Перед началом работы с этим контрольным списком необходимо прочитать следующие разделы.

  - [Планирование и развертывание](planning-and-deployment-for-exchange-2013-installation-instructions.md)

  - [Контрольный список по безопасности развертывания](deployment-security-checklist-exchange-2013-help.md)

Этот контрольный список носит общий характер, поскольку содержит указания для типового сценария.

> [!NOTE]  
> Помощник по развертыванию Exchange Server предоставляет специализированное пошаговое руководство по развертыванию сервера Exchange Server. Он поможет вам развернуть новую установку Exchange Server 2013, обновить предыдущую версию к Exchange 2013 или настроить гибридное развертывание Exchange 2013 и Exchange Online. Дополнительные сведения см. в разделе <a href="exchange-server-deployment-assistant-exchange-2013-help.md">Помощник по развертыванию Exchange Server</a>.


## Контрольный список для выполнения новой установки Exchange 2013


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
<td><p>Раздел</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>1. Прочитайте заметки о выпуске.</p></td>
<td><p><a href="release-notes-for-exchange-2013-exchange-2013-help.md">Заметки о выпуске Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>2. Проверьте выполнение системных требований.</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Требования к системе для установки Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>3. Подтвердите выполнение предварительных действий.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Предварительные требования для Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>4. Настройте несвязанное пространство имен.</p>

> [!NOTE]  
> Это действие является необязательным. Оно необходимо, только если в организации используется несвязанное пространство имен.

</td>
<td><p><a href="disjoint-namespace-scenarios-exchange-2013-help.md">Сценарии несвязанных пространств имен</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>5. Установите роль сервера почтовых ящиков.</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Установка Exchange 2013 с помощью мастера установки</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>6. Установите роль сервера клиентского доступа.</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Установка Exchange 2013 с помощью мастера установки</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>7. Установите роль пограничного транспортного сервера.</p>

> [!NOTE]  
> Это действие является необязательным. Оно необходимо, только если в организации используется пограничный транспортный сервер. Дополнительные сведения см. в разделе <a href="edge-transport-servers-exchange-2013-help.md">Пограничные транспортные серверы</a>.

</td>
<td><p><a href="install-the-exchange-2013-edge-transport-role-using-the-setup-wizard-exchange-2013-help.md">Установка роли пограничного транспортного сервера Exchange 2013 с помощью мастера установки</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>8. Создайте подписку EdgeSync.</p>
<p>Это действие является необязательным. Оно необходимо, только если установлен пограничный транспортный сервер и необходимо настроить подписку EdgeSync между пограничным транспортным сервером и транспортным сервером-концентратором. Дополнительные сведения см. в разделе <a href="edge-subscriptions-exchange-2013-help.md">Пограничные подписки</a>.</p></td>
<td><p><a href="configure-internet-mail-flow-through-a-subscribed-edge-transport-server-exchange-2013-help.md">Настройка потока почты Интернета через подписанный пограничный транспортный сервер</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>9. Настройте транспорт.</p></td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 1: Create a Send connector</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>10. Добавьте дополнительные обслуживаемые домены.</p></td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 2: Add additional accepted domains</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>11. Настройте политики адресов электронной почты.</p></td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 3: Configure the default email address policy</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>12. Настройте параметры виртуальных каталогов, включая автономную адресную книгу, веб-службы Exchange, Центр администрирования Exchange (EAC), Outlook Web App и виртуальные каталоги Exchange ActiveSync.</p>

> [!NOTE]  
> Это действие необходимо, только если планируется использовать веб-службы Exchange, мобильный Outlook или автономную адресную книгу. Оно также может потребоваться, если нужно изменить какие-либо параметры по умолчанию для Центра администрирования Exchange, Outlook Web App или Exchange ActiveSync.

</td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 4: Configure external URLs</a></p>
<p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 5: Configure internal URLs</a></p></td>
</tr>
<tr class="even">
<td> </td>
<td><p>13. Добавьте цифровые сертификаты для сервера клиентского доступа.</p></td>
<td><p><a href="configure-mail-flow-and-client-access-exchange-2013-help.md">Step 6: Configure an SSL certificate</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>14. Настройте единую систему обмена сообщениями.</p>

> [!NOTE]  
> Это действие является необязательным. Оно необходимо, только если в организации требуется использовать единую систему обмена сообщениями.

</td>
<td><p><a href="deploying-voice-mail-and-um-exchange-2013-help.md">Развертывание голосовой почты и единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>15. Настройте дополнительные серверы единой системы обмена сообщениями (UM) и Lync Server.</p>

> [!NOTE]  
> Это действие является необязательным. Его необходимо выполнить, только если вы настроили единую систему обмена сообщениями в своей организации и хотите интегрировать ее с Lync Server.

</td>
<td><p><a href="deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md">Развертывание единой системы обмена сообщениями в Exchange 2013 и обзор Lync Server</a></p></td>
</tr>
<tr class="odd">
<td> </td>
<td><p>16. Задачи, выполняемые после установки.</p></td>
<td><p><a href="exchange-2013-post-installation-tasks-exchange-2013-help.md">Задачи после установки Exchange 2013</a></p></td>
</tr>
</tbody>
</table>

