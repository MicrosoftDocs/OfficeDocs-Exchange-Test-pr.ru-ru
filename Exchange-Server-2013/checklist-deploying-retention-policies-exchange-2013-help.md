---
title: 'Контрольный список: Развертывание политик хранения: Exchange 2013 Help'
TOCTitle: 'Контрольный список: Развертывание политик хранения'
ms:assetid: 59e299fd-b6a8-48f5-88ae-dc20dbe32e90
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee364743(v=EXCHG.150)
ms:contentKeyID: 50488094
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Контрольный список: Развертывание политик хранения

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Используйте этот контрольный список для развертывания политик хранения в организации Майкрософт Exchange Server 2013. Перед началом работы с этим контрольным списком необходимо прочитать следующие разделы.

  - [Управление записями сообщений](https://docs.microsoft.com/ru-ru/exchange/security-and-compliance/messaging-records-management/messaging-records-management)

  - [Теги хранения и политики хранения](retention-tags-and-retention-policies-exchange-2013-help.md)

## Контрольный список для развертывания политик хранения


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Готово?</th>
<th>Tasks (Задачи).</th>
<th>Ресурсы</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p> </p></td>
<td><p>Оценка требований к управлению записями сообщений (MRM) для различных наборов пользователей.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/security-and-compliance/messaging-records-management/messaging-records-management">Управление записями сообщений</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Определение используемых версий клиентов Microsoft Outlook.</p></td>
<td><p>Анализ файлов журнала клиентского доступа RPC, находящихся в папке <code>%ExchangeInstallPath%Logging\RPC Client Access</code>.</p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Создание тегов хранения.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy">Создание политики хранения</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Создание политик хранения.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy">Создание политики хранения</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Добавление тегов хранения в политики хранения.</p></td>
<td><p><a href="add-retention-tags-to-or-remove-retention-tags-from-a-retention-policy-exchange-2013-help.md">Добавление и удаление тегов хранения для политики хранения</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Включение удержания на хранение для почтовых ящиков.</p></td>
<td><p><a href="place-a-mailbox-on-retention-hold-exchange-2013-help.md">Включение временного сохранения для почтового ящика</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Применение политики хранения к одному почтовому ящику для проверки.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/security-and-compliance/messaging-records-management/apply-retention-policy">Применение политики хранения к почтовым ящикам</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Необязательно. Реализация блокировки клиентов Outlook прежних версий.</p></td>
<td><p><a href="configure-outlook-client-blocking-exchange-2013-help.md">Настройка блокирования клиентов Outlook для управления записями сообщений</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Начало взаимодействия пользователей и обучающих мероприятий. Учитывается крайний срок, к которому необходимо обработать политики хранения и переместить или удалить элементы.</p></td>
<td><p>Неприменимо</p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Применение политики хранения к дополнительным почтовым ящикам.</p></td>
<td><p><a href="https://docs.microsoft.com/ru-ru/exchange/security-and-compliance/messaging-records-management/apply-retention-policy">Применение политики хранения к почтовым ящикам</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Предварительное напоминание пользователям о крайнем сроке (за несколько дней).</p></td>
<td><p>Неприменимо</p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>При наступлении крайнего срока отключение удержания на хранение для почтовых ящиков.</p></td>
<td><p><a href="place-a-mailbox-on-retention-hold-exchange-2013-help.md">Включение временного сохранения для почтового ящика</a></p></td>
</tr>
</tbody>
</table>

