---
title: 'Настройка Get-QueueDigest: Exchange 2013 Help'
TOCTitle: Настройка Get-QueueDigest
ms:assetid: f730c520-4ba5-4a15-8846-132bff500bb8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn505733(v=EXCHG.150)
ms:contentKeyID: 59636083
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка Get-QueueDigest

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2014-12-16_

Командлет **Get-QueueDigest** позволяет просматривать сведения о некоторых или всех очередях в организации Exchange с помощью одной команды.

По умолчанию командлет **Get-QueueDigest** возвращает значения одно-двухминутной давности. Эти значения контролируются с помощью следующих параметров:

  - **Ключ QueueLoggingInterval в EdgeTransport.exe.config**   Этот ключ указывает, как часто записываются в журнал данные очереди, и доступен для **Get-QueueDigest**. Значение по умолчанию: `00:01:00` (одна минута). Чтобы указать значение, введите его как промежуток времени: *чч:мм:сс*, где *чч* — часы, *мм* — минуты, а *сc* — секунды. По умолчанию данного ключа нет в файле EdgeTransport.exe.config.

  - **Параметр QueueDiagnosticsAggregationInterval в Set-TransportConfig**   Этот параметр указывает, как часто серверы почтовых ящиков получают совместный доступ к данным очереди. Значение по умолчанию: `00:01:00` (одна минута). Чтобы указать значение, введите его как промежуток времени: *чч:мм:сс*, где *чч* — часы, *мм* — минуты, а *сc* — секунды.

Сумма значений ключа **QueueLoggingInterval** и параметра *QueueDiagnosticsAggregationInterval* определяет максимальный срок результатов, возвращаемых **Get-QueueDigest**.

Кроме того, **Get-QueueDigest** возвращает результаты на основании типа и состояния очереди. Например, в результатах отображаются следующие очереди, если они содержат хотя бы одно сообщение:

  - очередь передачи, очередь недоставленных сообщений и очередь подозрительных сообщений (постоянные очереди);

  - очереди доставки в состоянии "Приостановлено" (очереди приостановлены вручную администратором).

По умолчанию очереди доставки с состоянием "Активно", "Подключение", "Готово" или "Повтор" возвращаются в результатах, только если очередь содержит не менее 10 сообщений. Этим значением управляет ключ **QueueLoggingThreshold** в файле EdgeTransport.exe.config. Можно указать меньшее или большее целое число. По умолчанию данного ключа нет в файле EdgeTransport.exe.config.

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения: 15 минут

  - Чтобы просмотреть разрешения Exchange, необходимые для запуска **Set-TransportConfig** в командной консоли Exchange, см. подраздел "Конфигурация транспорта" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Разрешения Exchange не применяются к изменению файла EdgeTransport.exe.config и перезапуску службы транспорта Microsoft Exchange. Эти процедуры выполняются в операционной системе Exchange Server.

  - Изменения, которые вы сохраняете в файле конфигурации EdgeTransport.exe.config, вступят в действие после перезапуска транспортной службы Microsoft Exchange. При перезапуске этой службы поток почты на сервере временно прерывается.

  - Все специальные настройки, выполненные для каждого сервера в XML-файлах конфигурации приложения Exchange, например в файлах web.config на серверах клиентского доступа или файлах EdgeTransport.exe.config на серверах почтовых ящиков, будут перезаписаны после установки накопительного пакета обновления Exchange. Обязательно сохраните нужные данные, чтобы упростить перенастройку сервера после установки. Эти параметры необходимо перенастроить после установки накопительного пакета обновления Exchange.

  - Изменения, сделанные с помощью **Set-TransportConfig**, влияют на все серверы почтовых ящиков в организации. Изменения, внесенные в файл EdgeTransport.exe.config, влияют только на локальный сервер почтовых ящиков.

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


## Настройка Get-QueueDigest

1.  В окне командной строки откройте файл EdgeTransport.exe.config в Блокноте, выполнив следующую команду:
    
        Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config

2.  Добавьте один или оба следующих ключа в раздел `<appSettings>`.
    
        <add key="QueueLoggingThreshold" value="<integer>" />
        <add key="QueueLoggingInterval" value="<hh:mm:ss>" />
    
    Например, чтобы задать для параметра **QueueLoggingThreshold** значение 1, а для **QueueLoggingInterval** — 30 секунд, используйте следующие значения:
    
        <add key="QueueLoggingThreshold" value="1" />
        <add key="QueueLoggingInterval" value="00:00:30" />

3.  Закончив, сохраните и закройте файл EdgeTransport.exe.config.

4.  Перезапустите службу транспорта Microsoft Exchange, выполнив следующую команду:
    
        net stop MSExchangeTransport && net start MSExchangeTransport

5.  Чтобы изменить значение параметра *QueueDiagnosticsAggregationInterval* в командной консоли Exchange, используйте следующий синтаксис:
    
        Set-TransportConfig -QueueDiagnosticsAggregationInterval <hh:mm:ss>
    
    Например, чтобы изменить значение на 30 секунд, выполните следующую команду:
    
        Set-TransportConfig -QueueDiagnosticsAggregationInterval 00:00:30

## Как проверить, что все получилось?

Чтобы убедиться в успешной настройке **Get-QueueDigest**, выполните следующие действия:

1.  Проверьте значения ключей **QueueLoggingThreshold** и **QueueLoggingInterval** в файле EdgeTransport.exe.config. Если ключи отсутствуют, используются значения по умолчанию.

2.  Проверьте значение параметра *QueueDiagnosticsAggregationInterval*, выполнив следующую команду:
    
        Get-TransportConfig | Format-List *queue*

