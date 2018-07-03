---
title: 'Настройка переопределений управляемой доступности: Exchange 2013 Help'
TOCTitle: Настройка переопределений управляемой доступности
ms:assetid: c8f315b3-1d5e-4ad9-8bea-9c3a4a13ebfc
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn482055(v=EXCHG.150)
ms:contentKeyID: 59890406
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка переопределений управляемой доступности

 

_**Применимо к:** Exchange Online, Exchange Server 2013 SP1_

_**Последнее изменение раздела:** 2015-11-30_

Функция управляемой доступности осуществляет непрерывное наблюдение для обнаружения возможных проблем с компонентами Exchange или зависимыми компонентами. Она также выполняет операции восстановления, чтобы работа пользователей не была затронута из-за проблемы с этими компонентами. Однако возможны сценарии, в которых стандартные настройки могут не подходить вашей среде. Зонды, мониторы и ответчики управляемой доступности можно настроить, создав переопределение.

Существует два типа переопределений: локальные и глобальные. Как следует из их названия, локальные переопределения доступны только на сервере, на котором они созданы, а глобальные переопределения используются на нескольких серверах. Оба типа переопределения можно создать либо на определенный период времени, либо для заданной версии Exchange.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При создании переопределения оно вступит в силу не сразу. Служба управления работоспособностью Microsoft Exchange проверяет наличие изменений конфигурации каждые 10 минут и загружает все обнаруженные изменения. Если вы не хотите ждать, вы можете перезапустить службу.</td>
</tr>
</tbody>
</table>


Сведения о дополнительных задачах управления, связанных с управляемой доступностью, см. в разделе [Управление настройками работоспособности и работоспособностью сервера](manage-health-sets-and-server-health-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этой процедуры можно использовать только командную консоль.Сведения о том, как открыть командную консоль Exchange в локальной организации Exchange, см. в статье [Открытие командной консоли Exchange](https://technet.microsoft.com/ru-ru/library/dd638134\(v=exchg.150\)).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Что необходимо сделать?

## Использование Командная консоль Exchange для создания локальных переопределений

Чтобы создать локальное переопределение на определенный срок, используйте следующий синтаксис.

    Add-ServerMonitoringOverride -Server <ServerName> -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <Probe | Monitor | Responder | Maintenance> -PropertyName <PropertyName> -PropertyValue <Value> -Duration <dd.hh:mm:ss>

Чтобы создать локальное переопределение для определенной версии Exchange, используйте следующий синтаксис.

    Add-ServerMonitoringOverride -Server <ServerName> -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <Probe | Monitor | Responder | Maintenance> -PropertyName <PropertyName> -PropertyValue <Value> -Version <15.01.xxxx.xxx>

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При создании переопределения значения в параметре <em>Identity</em> вводятся с учетом регистра.</td>
</tr>
</tbody>
</table>


В этом примере добавляется локальное переопределение, которое отключает ответчик `ActiveDirectoryConnectivityConfigDCServerReboot` на сервере EXCH03 на 20 дней.

    Add-ServerMonitoringOverride -Server EXCH03 -Identity "AD\ActiveDirectoryConnectivityConfigDCServerReboot" -ItemType Responder -PropertyName Enabled -PropertyValue 0 -Duration 20.00:00:00

## Как проверить, что все получилось?

Чтобы проверить, создано ли локальное переопределение, просмотрите список локальных переопределений с помощью командлета **Get-ServerMonitoringOverride**:

    Get-ServerMonitoringOverride  -Server <ServerIdentity> | Format-List

Переопределение должно появиться в списке.

## Использование Командная консоль Exchange для удаления локальных переопределений

Чтобы удалить локальное переопределение, используйте следующий синтаксис.

    Remove-ServerMonitoringOverride -Server <ServerName> -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <ExistingItemTypeValue> -PropertyName <PropertytoRemove>

В этом примере удаляется имеющееся локальное переопределение ответчика `ActiveDirectoryConnectivityConfigDCServerReboot` в группе работоспособности Exchange с сервера EXCH01.

    Remove-ServerMonitoringOverride -Server EXCH01 -Identity Exchange\ActiveDirectoryConnectivityConfigDCServerReboot -ItemType Responder -PropertyName Enabled

## Как проверить, что все получилось?

Чтобы проверить, удалено ли локальное переопределение, просмотрите список локальных переопределений с помощью командлета **Get-ServerMonitoringOverride**:

    Get-ServerMonitoringOverride  -Server <ServerIdentity> | Format-List

Переопределения не должно быть в списке.

## Использование Командная консоль Exchange для создания глобальных переопределений

Чтобы создать глобальное переопределение на определенный срок, используйте следующий синтаксис.

    Add-GlobalMonitoringOverride -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <Probe | Monitor | Responder | Maintenance> -PropertyName <PropertytoOverride> -PropertyValue <NewPropertyValue> -Duration <dd.hh:mm:ss>

Чтобы создать глобальное переопределение для определенной версии Exchange, используйте следующий синтаксис.

    Add-GlobalMonitoringOverride -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <Probe | Monitor | Responder | Maintenance> -PropertyName <PropertytoOverride> -PropertyValue <NewPropertyValue> -ApplyVersion <15.01.xxxx.xxx>

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При создании переопределения значения в параметре <em>Identity</em> вводятся с учетом регистра.</td>
</tr>
</tbody>
</table>


В этом примере добавляется глобальное переопределение, которое отключает пробу `OnPremisesInboundProxy` на 30 дней.

    Add-GlobalMonitoringOverride -Identity "FrontendTransport\OnPremisesInboundProxy" -ItemType Probe -PropertyName Enabled -PropertyValue 0 -Duration 30.00:00:00

В этом примере добавляется глобальное переопределение, которое отключает ответчик `StorageLogicalDriveSpaceEscalate` для всех серверов с Exchange версии 15.01.0225.042.

    Add-GlobalMonitoringOverride -Identity "MailboxSpace\StorageLogicalDriveSpaceEscalate" -PropertyName Enabled -PropertyValue 0 -ItemType Responder -ApplyVersion "15.01.0225.042"

## Как проверить, что все получилось?

Чтобы проверить, было ли глобальное переопределение успешно создано, выполните командлет **Get-GlobalMonitoringOverride** для просмотра списка глобальных переопределений:

    Get-GlobalMonitoringOverride

Переопределение должно появиться в списке.

## Использование Командная консоль Exchange для удаления глобальных переопределений

Чтобы удалить глобальное переопределение, используйте следующий синтаксис.

    Remove-GlobalMonitoringOverride -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <ExistingItemTypeValue> -PropertyName <OverriddenProperty>

В этом примере удаляется имеющееся глобальное переопределение свойства `ExtensionAttributes` пробы `OnPremisesInboundProxy` в группе работоспособности `FrontEndTransport`.

    Remove-GlobalMonitoringOverride -Identity FrontEndTransport\OnPremisesInboundProxy -ItemType Probe -PropertyName ExtensionAttributes

## Как проверить, что все получилось?

Чтобы проверить, было ли глобальное переопределение успешно удалено, выполните командлет **Get-GlobalMonitoringOverride** для просмотра списка глобальных переопределений:

    Get-GlobalMonitoringOverride

Переопределения не должно быть в списке.

