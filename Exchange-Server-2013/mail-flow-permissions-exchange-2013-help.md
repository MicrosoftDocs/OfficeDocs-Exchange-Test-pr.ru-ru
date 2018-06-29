---
title: 'Разрешения потока обработки почты: Exchange 2013 Help'
TOCTitle: Разрешения потока обработки почты
ms:assetid: f49f4fb5-af75-43cb-900f-c5f7b8cfa143
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638213(v=EXCHG.150)
ms:contentKeyID: 50489520
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разрешения потока обработки почты

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2016-12-09_

Разрешения, необходимые для выполнения задач, связанных с потоком обработки почты, отличаются в зависимости от выполняемой процедуры или командлета, который нужно запустить. Дополнительные сведения о функциях транспорта см. в разделе [Поток обработки почты](mail-flow-exchange-2013-help.md).

В этом разделе перечислены необходимые разрешения для управления функциями потока почты в Майкрософт Exchange Server 2013. Сведения о том, как разрешения Office 365 связаны с разрешениями Exchange, см. в статье [Разрешения в Office 365](https://go.microsoft.com/fwlink/p/?linkid=335814).

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

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Некоторые функции, которыми необходимо управлять, могут находиться на пограничных транспортных серверах. Для управления функциями на пограничных транспортных серверах необходимо стать участником локальной группы администраторов пограничного транспортного сервера, которым требуется управлять. На пограничном транспортном сервере не используется управление доступом на основе ролей (RBAC). Для функций, которыми можно управлять на пограничных транспортных серверах, столбец &quot;Требуемые разрешения&quot; в следующей таблице содержит запись &quot;Локальный администратор пограничного транспортного сервера&quot;.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для использования некоторых функций требуются разрешения локального администратора сервера, которым необходимо управлять. Для управления этими функциями необходимо быть участником локальной группы администраторов этого сервера.</td>
</tr>
</tbody>
</table>


## Разрешения потока обработки почты

Чтобы настроить параметры потока обработки почты в службе транспорта переднего плана на серверах клиентского доступа, в службе транспорта на серверах почтовых ящиков и на пограничных транспортных серверах, используйте компоненты, приведенные в таблице ниже. Также перечислены разрешения, необходимые для настройки каждого компонента.

Пользователи, которым назначена группа ролей управления с правами только для просмотра, могут просматривать конфигурацию компонентов, приведенных в следующей таблице. Дополнительные сведения см. в разделе [Управление организацией только с правом на просмотр](view-only-organization-management-exchange-2013-help.md).

**Серверы почтовых ящиков и серверы клиентского доступа**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Компонент</th>
<th>Необходимые разрешения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Обслуживаемые домены</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Управление сайтом Active Directory и ссылками сайта</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Функции защиты от нежелательной почты</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p></td>
</tr>
<tr class="even">
<td><p>Обновления средства защиты от нежелательной почты</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Управление сертификатами</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Соединители агента доставки</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Уведомления о доставке</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>EdgeSync</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Внешние соединители</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Транспортная служба переднего плана</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Ведение журнала</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="even">
<td><p>Доступ к почтовому ящику</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Конфигурация нежелательной почты почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="help-desk-exchange-2013-help.md">Служба поддержки</a></p></td>
</tr>
<tr class="even">
<td><p>Транспортная служба почтовых ящиков</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Подсказки</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Классификации сообщений</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="odd">
<td><p>Отслеживание сообщений</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Управляемый транспорт</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Очереди</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Соединители приема</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Удаленные домены</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Объединение списков надежных отправителей</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="odd">
<td><p>Соединители отправки</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Теневая избыточность</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Проверка потока почты</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Тестирование обработки правила транспорта</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Агенты транспорта</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="even">
<td><p>Конфигурация транспорта</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="odd">
<td><p>Журналы транспорта</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Правила транспорта</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="records-management-exchange-2013-help.md">Управление записями</a></p></td>
</tr>
<tr class="odd">
<td><p>служба передачи</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p></td>
</tr>
<tr class="even">
<td><p>Домены X.400</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
</tbody>
</table>


**Пограничные транспортные серверы**


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
<td><p>Обслуживаемые домены — пограничный транспортный сервер</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
<tr class="even">
<td><p>Переопределение адресов — пограничный транспорт</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
<tr class="odd">
<td><p>Пограничный транспортный сервер</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
<tr class="even">
<td><p>EdgeSync — пограничный транспортный сервер</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
<tr class="odd">
<td><p>Очереди — пограничный транспортный сервер</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
<tr class="even">
<td><p>Соединители приема — пограничный транспортный сервер</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
<tr class="odd">
<td><p>Соединители отправки — пограничный транспортный сервер</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
<tr class="even">
<td><p>Конфигурация транспорта — пограничный транспортный сервер</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
<tr class="odd">
<td><p>Журналы транспорта — пограничный транспортный сервер</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
<tr class="even">
<td><p>Правила транспорта — пограничный транспортный сервер</p></td>
<td><p>Локальный администратор пограничного транспортного сервера</p></td>
</tr>
</tbody>
</table>

