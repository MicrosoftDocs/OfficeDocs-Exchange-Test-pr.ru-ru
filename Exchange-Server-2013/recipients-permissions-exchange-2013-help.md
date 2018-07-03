---
title: 'Разрешения получателей: Exchange 2013 Help'
TOCTitle: Разрешения получателей
ms:assetid: 5b690bcb-c6df-4511-90e1-08ca91f43b37
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638132(v=EXCHG.150)
ms:contentKeyID: 50488289
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разрешения получателей

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Разрешения, необходимые для выполнения задач по управлению получателями, зависят от выполняемой процедуры или запускаемого командлета.

Для поиска разрешений, необходимых для выполнения процедуры или запуска командлета, выполните следующие действия.

1.  В следующей таблице найдите функцию, наиболее близко связанную с процедурой, которую необходимо выполнить, или командлетом, который необходимо запустить.

2.  После этого проверьте разрешения, необходимые для функции. Вы должны быть участником одной из этих групп ролей, равнозначной настраиваемой группы ролей или равнозначной роли управления. Вы также можете щелкнуть группу ролей, чтобы просмотреть ее роли управления. Если для функции указано несколько групп ролей, то для ее использования достаточно относиться к одной из этих групп. Дополнительные сведения о группах ролей и ролях управления см. в разделе [Общие сведения об управлении доступом на основе ролей](understanding-role-based-access-control-exchange-2013-help.md).

3.  Запустите командлет **Get-ManagementRoleAssignment**, чтобы просмотреть назначенные группы ролей или роли управления и проверить наличие необходимых разрешений для управления функцией.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Для запуска командлета <strong>Get-ManagementRoleAssignment</strong> вам должна быть назначена роль управления &quot;Управление ролями&quot;. Если для запуска командлета <strong>Get-ManagementRoleAssignment</strong> отсутствуют необходимые разрешения, попросите администратора Exchange назначить группы ролей или роли управления.</td>
    </tr>
    </tbody>
    </table>


Дополнительные сведения о делегировании возможности управления другим пользователям см. в разделе [Назначения роли делегата](delegate-role-assignments-exchange-2013-help.md).

## Разрешения для сервера почтовых ящиков

Пользователи, которым назначена группа ролей управления с правами только для просмотра, могут просматривать конфигурацию функций в приведенной ниже таблице. Дополнительные сведения см. в разделе Управление организацией с правами только на просмотр[Управление организацией только с правом на просмотр](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Функция</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Восстановление календаря, конфигурации сервера</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Делегирование серверов почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Политики адресов электронной почты</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Служба поиска Exchange</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Служба поиска Exchange — диагностика</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p>
<p>Роль поддержки диагностики</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Роль поддержки диагностики не назначена группе ролей. Подробнее см. в разделе <a href="add-a-role-to-a-user-or-usg-exchange-2013-help.md">Добавление роли для пользователя или универсальной группы безопасности</a>.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="even">
<td><p>Групповые метрики</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Импорт и экспорт</p></td>
<td><p>Роль импорта и экспорта почтового ящика</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Роль импорта и экспорта почтового ящика не назначена группе ролей. Подробнее см. в разделе <a href="mailbox-import-export-role-exchange-2013-help.md">Роль импорта и экспорта почтового ящика</a>.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="even">
<td><p>Помощники по обслуживанию почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Перемещение почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Восстановление почтового ящика</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Запрос на исправление почтового ящика</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Запрос на восстановление почтового ящика</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Конфигурация сервера почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Управление службой индексатора поиска Exchange на сервере почтовых ящиков</p></td>
<td><p>Локальный администратор на сервере почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>Подключение MAPI</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Виртуальные каталоги автономной адресной книги</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Удаление почтового ящика хранилища</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
</tbody>
</table>


## Разрешения на общий доступ к календарю

Пользователи, которым назначена группа ролей управления с правами только для просмотра, могут просматривать конфигурацию функций в приведенной ниже таблице. Дополнительные сведения см. в разделе Управление организацией с правами только на просмотр[Управление организацией только с правом на просмотр](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Функция</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Конфигурация календаря</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="even">
<td><p>Диагностика календаря</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p>
<p><a href="compliance-management-exchange-2013-help.md">Управление соответствием требованиям</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="odd">
<td><p>Обработка календаря</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="even">
<td><p>Уведомления</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Связи организации</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Политики общего доступа</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
</tbody>
</table>


## Разрешения на изменение настроек почтового ящика ресурса

Пользователи, которым назначена группа ролей управления с правами только для просмотра, могут просматривать конфигурацию функций в приведенной ниже таблице. Дополнительные сведения см. в разделе Управление организацией с правами только на просмотр[Управление организацией только с правом на просмотр](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Функция</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Политики резервирования</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="even">
<td><p>Делегирование</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Конфигурация схемы почтового ящика ресурса</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
</tbody>
</table>


## Разрешения для базы данных почтовых ящиков

Пользователи, которым назначена группа ролей управления с правами только для просмотра, могут просматривать конфигурацию функций в приведенной ниже таблице. Дополнительные сведения см. в разделе Управление организацией с правами только на просмотр[Управление организацией только с правом на просмотр](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Функция</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Базы данных почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
</tbody>
</table>


## Разрешения на подготовку получателей

В этой таблице содержатся различные разрешения, которые требуются для управления получателями.

Пользователи, которым назначена группа ролей управления с правами только для просмотра, могут просматривать конфигурацию функций в приведенной ниже таблице. Дополнительные сведения см. в разделе Управление организацией с правами только на просмотр[Управление организацией только с правом на просмотр](view-only-organization-management-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Функция</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Список адресов, глобальный список адресов</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Защита от нежелательной почты</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Приложения для Outlook</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="even">
<td><p>Применение политик общего доступа</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Арбитраж</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Возможность подключения к архиву</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Назначение автономных адресных книг</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Автоматические ответы</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="odd">
<td><p>Конфигурация календаря</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Восстановление календаря</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Параметры объединения контактов</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
<tr class="even">
<td><p>Отключенные почтовые ящики</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="odd">
<td><p>Группы рассылки</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Динамические группы рассылки</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Адреса электронной почты</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="um-management-exchange-2013-help.md">Управление единой системой обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p>Правила для папки «Входящие»</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="odd">
<td><p>Почтовые контакты</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Советы по использованию электронной почты</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Пользователь почты</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Разрешения для папки почтового ящика</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="odd">
<td><p>Папки почтового ящика</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Подключение MAPI</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Конфигурация сообщения</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="even">
<td><p>Квоты сообщений</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Контроль</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Разрешения и делегирование</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Архивные почтовые ящики</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Свойства данных получателя</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Удаленные почтовые ящики</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Хранение и юридические удержания</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="odd">
<td><p>Отправить как</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Конфигурация проверки орфографии</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="odd">
<td><p>Единая система обмена сообщениями.</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="um-management-exchange-2013-help.md">Управление единой системой обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p>Почтовые ящики пользователей</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Фотографии пользователя</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
</tbody>
</table>


## Разрешения на перемещение и миграцию почтовых ящиков

Таблица содержит разрешения, которые требуются для переноса локальных почтовых ящиков в разных доменах или лесах, а также для миграции локальных почтовых ящиков в организации на основе облака.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Функция</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Перемещение почтовых ящиков (локально или между лесами)</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Перемещение почтовых ящиков (гибридное развертывание)</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Миграция (в облако и из облака)</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
</tbody>
</table>

