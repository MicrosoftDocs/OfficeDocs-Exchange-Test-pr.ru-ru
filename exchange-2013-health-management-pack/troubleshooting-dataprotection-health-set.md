---
title: Устранение неполадок в наборе для контроля работоспособности DataProtection
TOCTitle: Устранение неполадок в наборе для контроля работоспособности DataProtection
ms:assetid: cde3cc34-2076-4e30-8d3c-265b66d00ae8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.scom.dataprotection(v=EXCHG.150)
ms:contentKeyID: 53275669
ms.date: 11/14/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Устранение неполадок в наборе для контроля работоспособности DataProtection

 

_**Применимо к:** Exchange Server 2013, Project Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Набор для контроля работоспособности DataProtection служит для мониторинга избыточности баз данных в группе обеспечения доступности баз данных (DAG).

Если появляется предупреждение о нарушении работоспособности DataProtection, это говорит о наличии проблемы, которая может повлиять на компоненты репликации или кластерные компоненты, что может заблокировать доступ к базам данных Exchange.

## Пояснение

Служба работоспособности DataProtection отслеживается с помощью следующих зондов и мониторов.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Зонд</th>
<th>Настройки работоспособности</th>
<th>Зависимости</th>
<th>Связанные мониторы</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ClusterEndpointProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>ClusterEndpointMonitor</p></td>
</tr>
<tr class="even">
<td><p>ClusterGroupProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>ClusterGroupMonitor</p></td>
</tr>
<tr class="odd">
<td><p>ClusterNetworkProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>ClusterNetworkMonitor</p></td>
</tr>
<tr class="even">
<td><p>ClusterServiceCrashProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>ClusterServiceCrashMonitor</p></td>
</tr>
<tr class="odd">
<td><p>ServerOneCopyProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Director</p></td>
<td><p>ServerOneCopyMonitor</p></td>
</tr>
<tr class="even">
<td><p>ServerOneCopyInternalMonitorProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>ServerOneCopyInternalMonitorMonitor</p></td>
</tr>
<tr class="odd">
<td><p>ServiceHealthMSExchangeReplEndpointProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>ServiceHealthMSExchangeReplEndpointMonitor</p></td>
</tr>
<tr class="even">
<td><p>ServiceHealthMSExchangeReplCrashProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>ServiceHealthMSExchangeReplCrashMonitor</p></td>
</tr>
<tr class="odd">
<td><p>ServerSiteFailureProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>ServerSiteFailureMonitor</p></td>
</tr>
<tr class="even">
<td><p>StorageApparentControllerIssuesProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>StorageApparentControllerIssuesMonitor</p></td>
</tr>
<tr class="odd">
<td><p>DatabaseHealthTooManyMountedDatabaseProbe</p></td>
<td><p>DataProtection</p></td>
<td><p>Active Directory</p></td>
<td><p>DatabaseHealthTooManyMountedDatabaseMonitor</p></td>
</tr>
</tbody>
</table>


Дополнительные сведения о зондах и мониторах см. в разделе [Работоспособность и производительность сервера](https://technet.microsoft.com/ru-ru/library/jj150551\(v=exchg.150\)).

## Действия пользователя

Служба может восстановить работу после отображения оповещения. Поэтому если вы получите оповещение о неработоспособном состоянии настроек работоспособности, сначала убедитесь в наличии данной проблемы. Если проблема не устранена, выполните соответствующие действия по восстановлению, указанные в приведенных ниже разделах.

## Проверка наличия проблемы

1.  Определите имена настроек работоспособности и сервера, указанные в оповещении.

2.  В сообщении приводятся подробные сведения о точной причине возникновения оповещения. В большинстве случаев в сообщении приводится достаточно сведений по устранению неполадок для определения основной причины проблемы. Если в сообщении приводятся непонятные сведения:
    
    1.  Откройте Командная консоль Exchange, а затем выполните следующую команду, чтобы извлечь подробные сведения о настройках работоспособности, с которыми связано оповещение.
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Например, чтобы извлечь подробные сведения о настройках работоспособности Autodiscover.Protocol относительно сервера server1.contoso.com, выполните следующую команду.
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "Autodiscover.Protocol"}
        
        Просмотрите выходные данные команды, чтобы определить монитор, сообщивший об ошибке. Параметр **AlertValue** монитора, вызвавшего оповещение, будет иметь значение `Unhealthy`.
    
    2.  Определите зонд, на котором основан монитор. Обратите внимание, что у большинства зондов один и тот же префикс. Используя предыдущий пример, выполните поиск "**ClusterNetwork\***".
        
            Get-MonitoringItemIdentity -Identity DataProtection -Server server1.contoso.com | ?{$_.Name -like "ClusterNet ItemType  
            work*"}
        
        Возвращенные результаты должны иметь примерно следующий вид.
        
        
        <table>
        <colgroup>
        <col style="width: 25%" />
        <col style="width: 25%" />
        <col style="width: 25%" />
        <col style="width: 25%" />
        </colgroup>
        <tbody>
        <tr class="odd">
        <td><p><code>ItemType</code></p></td>
        <td><p><code>HealthSetName</code></p></td>
        <td><p><code>Name</code></p></td>
        <td><p><code>TargetResource</code></p></td>
        </tr>
        <tr class="even">
        <td><p><code>Probe</code></p></td>
        <td><p><code>DataProtection</code></p></td>
        <td><p><code>ClusterNetworkProbe</code></p></td>
        <td><p><code>MSExchangeRepl</code></p></td>
        </tr>
        </tbody>
        </table>
    
    3.  Еще раз запустите зонд для средства мониторинга, которое находится в неисправном состоянии. Обратитесь к таблице в разделе Пояснение, чтобы найти связанный зонд. Для этого выполните следующую команду.
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Например, предположим, что не работает монитор **AutodiscoverSelfTestMonitor**. С этим монитором связан зонд **AutodiscoverSelfTestProbe**. Чтобы запустить этот зонд на сервере server1.contoso.com, выполните следующую команду.
        
            Invoke-MonitoringProbe Autodiscover.Protocol\AutodiscoverSelfTestProbe -Server server1.contoso.com | Format-List
    
    4.  В выходных данных команды просмотрите значение параметра **Результат** зонда. Если этот параметр имеет значение **Succeeded**, ошибка была временной и в настоящее время устранена. В противном случае обратитесь к действиям по восстановлению, приведенным в следующих разделах.

## Действия по устранению неполадок

Если вы получите оповещение, связанное с настройками работоспособности, сообщение электронной почты содержит приведенные ниже сведения.

  - Имя сервера, отправившего оповещение.

  - Время и дата возникновения оповещения.

  - Используемый механизм проверки подлинности и сведения об учетных данных.

  - Полная трассировка исключения, связанного с последней ошибкой, включая диагностические данные и конкретные сведения о заголовке HTTP.
    
    Сведения в полной трассировке исключения можно использовать для устранения проблемы. Исключение, созданное зондом, содержит причину сбоя зонда.

Для большинства проблем, возникающих в средах высокой доступности, можно запустить командлет **Test-ReplicationHealth**, чтобы устранить неполадки в кластерах, сети, ActiveManager и службах. Для других наборов для контроля работоспособности и компонентов существуют другие командлеты с префиксом "Test-\*".

Например:

    Test-ReplicationHealth <ServerName>

Возвращенные результаты должны иметь примерно следующий вид.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><code>Server</code></p></td>
<td><p><code>Check</code></p></td>
<td><p><code>Result</code></p></td>
</tr>
<tr class="even">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>ClusterService</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="odd">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>ReplayService</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="even">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>ActiveManager</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="odd">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>TasksRpcListener</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="even">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>TcpListener</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="odd">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>ServerLocatorService</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="even">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>DagMembersUp</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="odd">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>ClusterNetwork</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="even">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>QuorumGroup</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="odd">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>FileShareQuorum</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="even">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>DatabaseRedundancyCheck</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="odd">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>DatabaseAvailabilityCheck</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="even">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>DBCopySuspended</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="odd">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>DBCopyFailed</code></p></td>
<td><p>Тест пройден</p></td>
</tr>
<tr class="even">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>DBInitializing</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="odd">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>DBDisconnected</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="even">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>DBLogCopyKeepingUp</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
<tr class="odd">
<td><p><em>&lt;ServerName&gt;</em></p></td>
<td><p><code>DBLogReplayKeepingUp</code></p></td>
<td><p><code>Passed</code></p></td>
</tr>
</tbody>
</table>


Если для всех компонентов отображается значение **Тест пройден** в столбце **Результат**, попробуйте перезапустить связанный зонд, как это показано в шаге 2c в разделе Проверка наличия проблемы.

Если проблема не устранена, перезапустите сервер. После перезапуска сервера повторно запустите связанный зонд, как показано в шаге 2c раздела Проверка наличия проблемы.

Если зонд все еще не работает, вам понадобится помощь для устранения данной проблемы. Для решения этой проблемы обратитесь к специалисту службы технической поддержки Майкрософт. Сделать это можно в [Центре решений Exchange Server](http://go.microsoft.com/fwlink/p/?linkid=180809). В области навигации выберите элемент **Варианты поддержки и ресурсы** и выберите один из вариантов в разделе **Получите техническую поддержку**, чтобы обратиться к соответствующему специалисту. Так прямое обращение в службу технической поддержки Майкрософт в вашей организации может регламентироваться, сначала ознакомьтесь с инструкциями организации.

## Дополнительные сведения

[Новые возможности в Exchange 2013](https://technet.microsoft.com/ru-ru/library/jj150540\(v=exchg.150\))

[Командлеты Exchange 2013](https://technet.microsoft.com/ru-ru/library/bb124413\(v=exchg.150\))

