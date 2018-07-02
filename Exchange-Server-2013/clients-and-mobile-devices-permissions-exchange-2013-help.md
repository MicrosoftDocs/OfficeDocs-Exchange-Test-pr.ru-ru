---
title: 'Разрешения клиентов и мобильных устройств: Exchange 2013 Help'
TOCTitle: Разрешения клиентов и мобильных устройств
ms:assetid: 57eca42a-5a7f-4c65-89f0-7a84f2dbea19
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638131(v=EXCHG.150)
ms:contentKeyID: 50488084
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разрешения клиентов и мобильных устройств

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-11-10_

Необходимые разрешения на выполнение задач для клиентов и мобильных устройств различаются в зависимости от выполняемой процедуры или запускаемого командлета. Дополнительные сведения о клиентах и мобильных устройствах см. в разделе [Клиенты и мобильные устройства](clients-and-mobile-exchange-2013-help.md).

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
<td>Для использования некоторых функций требуются разрешения локального администратора сервера, которым необходимо управлять. Для управления этими функциями необходимо быть участником локальной группы администраторов этого сервера.</td>
</tr>
</tbody>
</table>


## Разрешения сервера клиентского доступа

Можно настроить любые из следующих функций роли сервера клиентского доступа.

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
<td><p>Параметры массива сервера клиентского доступа</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры сервера клиентского доступа</p></td>
<td><p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Параметры почтового канала службы клиентского доступа</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры пользователя клиентского доступа</p></td>
<td><p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Параметры виртуального каталога клиентского доступа</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры клиентского доступа RPC</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
<tr class="odd">
<td><p>Параметры прокси-сервера push-уведомлений</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры перенаправления для проверки подлинности OAuth</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
</tbody>
</table>


## Разрешения Exchange ActiveSync

Можно настроить любые из следующих параметров для Exchange ActiveSync.

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
<td><p>Параметры автоблокировки Exchange ActiveSync</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры политики почтовых ящиков Exchange ActiveSync</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Параметры сервера Exchange ActiveSync</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры Exchange ActiveSync</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Параметры пользователя Exchange ActiveSync</p></td>
<td><p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры виртуального каталога Exchange ActiveSync</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Параметры политики почтовых ящиков мобильного устройства</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры пользователя мобильного устройства</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
</tbody>
</table>


## Разрешения автообнаружения

Можно настроить следующие параметры для службы автообнаружения.

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
<td><p>Параметры конфигурации службы автообнаружения</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p>
<p><a href="delegated-setup-exchange-2013-help.md">Делегированная установка</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры виртуального каталога автообнаружения</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
</tbody>
</table>


## Разрешения службы доступности

Можно настроить следующие параметры для службы доступности.

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
<td><p>Параметры адресного пространства службы доступности</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры конфигурации службы доступности</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
</tbody>
</table>


## Разрешения регулирования клиентов

Можно настроить следующие параметры для регулирования клиентов.

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
<td><p>Параметры регулирования клиентов</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
</tbody>
</table>


## Разрешения веб-служб Exchange

Можно настроить следующие параметры для виртуальных каталогов веб-служб.

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
<td><p>Параметры виртуального каталога веб-служб Exchange</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Проверка веб-служб Exchange</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="odd">
<td><p>Проверка веб-служб Outlook</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
</tbody>
</table>


## Разрешения мобильного Outlook

Можно настроить и управлять следующими параметрами Outlook Мобильный.

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
<td><p>Конфигурация Outlook Мобильный (включение, отключение, изменение, просмотр)</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p>
<p><a href="delegated-setup-exchange-2013-help.md">Делегированная установка</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p></td>
</tr>
<tr class="even">
<td><p>Компонент &quot;RPC через HTTP-прокси&quot;</p></td>
<td><p>Администратор локального сервера</p></td>
</tr>
<tr class="odd">
<td><p>Проверка подключения Outlook Мобильный</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
</tbody>
</table>


## Разрешения Outlook Web App

Можно использовать следующие функции для просмотра параметров Outlook Web App, управления безопасностью и доступом пользователей к Outlook Web App и проверки подключения Outlook Web App.

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
<td><p>Графический редактор</p></td>
<td><p>Администратор локального сервера</p></td>
</tr>
<tr class="even">
<td><p>Диспетчер IIS</p></td>
<td><p>Администратор локального сервера</p></td>
</tr>
<tr class="odd">
<td><p>ISA Server 2006</p></td>
<td><p>Администратор предприятия ISA Server</p></td>
</tr>
<tr class="even">
<td><p>Политики почтовых ящиков Outlook Web App</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Виртуальные каталоги Outlook Web App</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p></td>
</tr>
<tr class="even">
<td><p>Редактор реестра</p></td>
<td><p>Администратор локального сервера</p></td>
</tr>
<tr class="odd">
<td><p>Конфигурация S/MIME</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Текстовый редактор</p></td>
<td><p>Администратор локального сервера</p></td>
</tr>
<tr class="odd">
<td><p>Просмотр политик почтовых ящиков Outlook Web App</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p>
<p><a href="delegated-setup-exchange-2013-help.md">Делегированная установка</a></p>
<p><a href="hygiene-management-exchange-2013-help.md">Управление санацией</a></p></td>
</tr>
</tbody>
</table>


## Разрешения POP3 и IMAP4

Можно настроить следующие параметры для протоколов POP3 и IMAP4.

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
<td><p>Параметры IMAP4</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры POP3</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
<tr class="odd">
<td><p>Проверка параметров IMAP4</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
<tr class="even">
<td><p>Проверка параметров POP3</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p>
<p><a href="server-management-exchange-2013-help.md">Управление сервером</a></p>
<p><a href="view-only-organization-management-exchange-2013-help.md">Управление организацией только с правом на просмотр</a></p></td>
</tr>
</tbody>
</table>


## Разрешения виртуальных каталогов Windows PowerShell

Можно настроить следующие параметры для Windows PowerShell.

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
<td><p>Тест Windows PowerShell</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры Windows PowerShell</p></td>
<td><p><a href="organization-management-exchange-2013-help.md">Управление организацией</a></p></td>
</tr>
</tbody>
</table>


## Разрешения обмена текстовыми сообщениями

Можно настроить следующие параметры для обмена текстовыми сообщениями.

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
<td><p>Параметры уведомлений обмена текстовыми сообщениями</p></td>
<td><p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="even">
<td><p>Параметры обмена текстовыми сообщениями</p></td>
<td><p><a href="recipient-management-exchange-2013-help.md">Управление получателями</a></p></td>
</tr>
<tr class="odd">
<td><p>Параметры пользователя обмена текстовыми сообщениями</p></td>
<td><p><a href="mytextmessaging-role-exchange-2013-help.md">Роль MyTextMessaging</a></p>
<p>Пользователи могут настраивать параметры текстовых сообщений в своих почтовых ящиках. Администраторы не могут настраивать параметры текстовых сообщений в почтовом ящике другого пользователя.</p></td>
</tr>
</tbody>
</table>

