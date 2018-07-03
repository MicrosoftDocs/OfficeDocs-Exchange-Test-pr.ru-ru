﻿---
title: 'Управление настройками работоспособности и работоспособностью сервера: Exchange 2013 Help'
TOCTitle: Управление настройками работоспособности и работоспособностью сервера
ms:assetid: a4f84312-6cfa-4f17-9707-676aadab1143
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn482054(v=EXCHG.150)
ms:contentKeyID: 59890405
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Управление настройками работоспособности и работоспособностью сервера

 

_**Применимо к:** Exchange Online, Exchange Server 2013 SP1_

_**Последнее изменение раздела:** 2013-12-02_

Вы можете использовать встроенные командлеты отчетов о работоспособности для выполнения различных задач, связанных с управляемой доступностью, например:

  - просмотр работоспособности сервера или группы серверов;

  - просмотр списка настроек работоспособности;

  - просмотр списка зондов, мониторов и ответчиков, связанных с определенными настройками работоспособности;

  - просмотр списка мониторов и их текущего состояния.

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 2 минуты

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

## Просмотр работоспособности сервера

С помощью командной консоли вы можете получить сводную информацию о работоспособности сервера Exchange 2013.

## Использование командной консоли для просмотра работоспособности сервера

Выполните одну из следующих команд для просмотра настроек работоспособности и сведений об исправности на сервере Exchange 2013.

    Get-HealthReport -Identity <ServerName>

    Get-ServerHealth -Identity <ServerName> | Format-Table Server,CurrentHealthSetState,Name,HealthSetName,AlertValue,HealthGroupName -Auto

Выполните одну из следующих команд для просмотра настроек работоспособности на сервере или в группе доступности базы данных Exchange 2013.

    Get-ExchangeServer | Get-HealthReport -RollupGroup

    Get-ExchangeServer | Get-HealthReport -RollupGroup -HealthSetName <HealthSet>

    (Get-DatabaseAvailabiltyGroup <DAGName>).Servers | Get-HealthReport -RollupGroup

## Просмотр списка настроек работоспособности

Настройки работоспособности — это группа мониторов, зондов и ответчиков для компонента, которые определяют, исправен ли компонент или нет. С помощью командной консоли вы можете просматривать список настроек работоспособности на сервере Exchange 2013.

## Использование командной консоли для просмотра списка настроек работоспособности

Выполните следующую команду для просмотра настроек работоспособности на сервере Exchange 2013.

    Get-HealthReport -Server <ServerName>

## Просмотр зондов, мониторов и ответчиков для настроек работоспособности

Настройки работоспособности — это группа мониторов, зондов и ответчиков для компонента, которые определяют, исправен ли компонент или нет. С помощью командной консоли вы можете просматривать список зондов, мониторов и ответчиков, связанных с настройками работоспособности, заданными на сервере Exchange 2013.

## Использование командной консоли для просмотра зондов, мониторов и ответчиков для настроек работоспособности

Выполните следующую команду для просмотра зондов, мониторов и ответчиков, связанных с настройками работоспособности на сервере Exchange 2013.

    Get-MonitoringItemIdentity -Server <ServerName> -Identity <HealthSetName> | Format-Table Identity,ItemType,Name -Auto

## Просмотр списка мониторов и их текущего состояния

Состояние мониторов определяется на основе состояния «худших» мониторов в настройках работоспособности. Вы можете просмотреть сведения о настройках работоспособности, чтобы узнать, какие мониторы исправны, а какие нет.

## Использование командной консоли для просмотра списка мониторов и их текущего состояния

Выполните следующую команду для просмотра списка мониторов и их текущего состояния на сервере Exchange 2013.

    Get-ServerHealth -HealthSet <HealthSetName> -Server <ServerName> | Format-Table Name, AlertValue -Auto
