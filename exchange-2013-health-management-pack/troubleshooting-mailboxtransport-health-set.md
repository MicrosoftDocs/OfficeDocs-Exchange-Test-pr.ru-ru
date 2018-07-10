---
title: Устранение неполадок группы работоспособности MailboxTransport
TOCTitle: Устранение неполадок группы работоспособности MailboxTransport
ms:assetid: 02bfa4cf-6929-437e-bae5-079ea1b92373
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.scom.mailboxtransport(v=EXCHG.150)
ms:contentKeyID: 54652159
ms.date: 11/14/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Устранение неполадок группы работоспособности MailboxTransport

 

_**Применимо к:** Exchange Server 2013, Project Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Группа работоспособности **MailboxTransport** отслеживает общую работоспособность служб отправки и доставки транспорта почтовых ящиков на серверах почтовых ящиков. Эти службы отвечают за отправку входящей и исходящей почты в базах данных почтовых ящиков. Дополнительные сведения см. в разделе [Поток обработки почты](https://technet.microsoft.com/ru-ru/library/aa996349\(v=exchg.150\)).

Предупреждение о неисправности набора работоспособности **MailboxTransport** указывает на проблему, которая может препятствовать отправке или получению почты из баз данных почтовых ящиков.

## Объяснение

Служба **MailboxTransport** отслеживается с помощью следующих зондов и мониторов.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Зонд</th>
<th>Группа работоспособности</th>
<th>Связанные мониторы</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MailboxDeliveryAvailability</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxDeliveryAvailabilityMonitor</p></td>
</tr>
<tr class="even">
<td><p>MailboxDeliveryAvailabilityAggregationProbe</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxDeliveryAvailabilityAggregationMonitor</p></td>
</tr>
<tr class="odd">
<td><p>MailboxDeliveryInstanceAvailabilityProbe</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxDeliveryInstanceAvailabilityMonitor</p></td>
</tr>
<tr class="even">
<td><p>MailboxTransportDeliveryServiceRunning</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxTransportDeliveryServiceRunningMonitor</p></td>
</tr>
<tr class="odd">
<td><p>MailboxTransportSubmissionServiceRunning</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxTransportSubmissionServiceRunningMonitor</p></td>
</tr>
<tr class="even">
<td><p>Mapi.Submit.Probe</p></td>
<td><p>MailboxTransport</p></td>
<td><p>Mapi.Submit.Monitor</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>CrashEvent.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>CrashEvent.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>DeliveryBackpressureSustainedTimeMonitor</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>DeliveryInterceptorStoreDriverAgentPctPermFailedMonitor</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MailboxTransportUserQuarantineMonitor</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MBTSubmissionInterceptorSubmissionAgentMonitor</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MSExchangeAsstAvgEventProcessingTimeSubmissionMonitor50</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>MSExchangeAsstAvgEventProcessingTimeSubmissionMonitor70</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>PrivateWorkingSetError.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>PrivateWorkingSetError.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>PrivateWorkingSetWarning.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>PrivateWorkingSetWarning.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>ProcessProcessorTimeError.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>ProcessProcessorTimeError.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>ProcessProcessorTimeWarning.msexchangedelivery</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>ProcessProcessorTimeWarning.msexchangesubmission</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>SubmissionBackpressureSustainedTimeMonitor</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>SubmissionInterceptorSubmissionAgentPctPermFailedMonitor</p></td>
</tr>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>MailboxTransport</p></td>
<td><p>TransportDeliveryFailuresDeliveryStoreDriver560Monitor</p></td>
</tr>
</tbody>
</table>


Дополнительные сведения о зондах и мониторах см. в разделе [Работоспособность и производительность сервера](https://technet.microsoft.com/ru-ru/library/jj150551\(v=exchg.150\)).

## Действия пользователя

Служба может восстановить работу после отображения оповещения. Поэтому при получении предупреждения о неисправности группы работоспособности **MailboxTransport** убедитесь, что проблема еще существует. Если проблема не устранена, выполните соответствующие действия по восстановлению, указанные в следующем разделе.

## Проверка проблемы

1.  Определите имя группы работоспособности и имя сервера, указанные в предупреждении.

2.  В сообщении приводятся подробные сведения о точной причине возникновения оповещения. В большинстве случаев в сообщении представлено достаточно диагностической информации для определения основной причины. Если в сообщении приводятся неполные сведения, выполните следующие действия.
    
    1.  Откройте Командная консоль Exchange, а затем запустите следующую команду, чтобы получить сведения о группе работоспособности, которая выдала предупреждение.
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Например, чтобы получить подробные сведения о группе работоспособности **MailboxTransport** для mailbox1.contoso.com, запустите следующую команду:
        
            Get-ServerHealth mailbox1.contoso.com | ?{$_.HealthSetName -eq "MailboxTransport"}
    
    2.  Просмотрите выходные данные команды, чтобы определить, какой монитор сообщил об ошибке. У монитора, который отправил предупреждение, параметр **AlertValue** будет иметь значение **Неисправность**.
    
    3.  Еще раз запустите зонд для монитора, который находится в неисправном состоянии. Обратитесь к таблице в разделе [Пояснение](troubleshooting-activesync-health-set.md), чтобы найти связанный зонд. Для этого выполните следующую команду:
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Допустим, что неисправен монитор **MailboxDeliveryAvailabilityMonitor**. С этим монитором связан зонд **MailboxDeliveryAvailability**. Чтобы запустить этот зонд на сервере mailbox1.contoso.com, выполните следующую команду:
        
            Invoke-MonitoringProbe MailboxTransport\MailboxDeliveryAvailabilityMonitor -Server mailbox1.contoso.com | Format-List
    
    4.  В результатах выполнения команды просмотрите раздел "Результат" зонда. Если этот параметр имеет значение **Succeeded**, ошибка была временной и в настоящее время устранена.

