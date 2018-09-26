---
title: 'Включение и настройка приоритет очереди: Exchange 2013 Help'
TOCTitle: Включение и настройка приоритет очереди
ms:assetid: 1975d85d-2f1d-4852-8d19-e74ba4ba3853
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ891104(v=EXCHG.150)
ms:contentKeyID: 51408008
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Включение и настройка приоритет очереди

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2014-12-16_

*Приоритетная организация очереди* является функцией Microsoft Exchange Server 2013, которая включает приоритет сообщения, настроенный отправителем в Microsoft Outlook или Outlook Web Access с целью оказания влияния на обработку сообщения транспортной службой на сервере почтовых ящиков. При включении организации очередей с учетом приоритетов сначала по назначению передаются сообщения с высокой важностью, затем сообщения с обычной важностью, а затем сообщения с низкой важностью. Подробнее см. в разделе [Организация очередей с учетом приоритетов](priority-queuing-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 15 минут.

  - Разрешения Exchange не применяются к процедурам, описанным в этом разделе. Эти процедуры выполняются в операционной системе сервера Exchange.

  - Изменения, которые вы сохраняете в файле конфигурации приложения EdgeTransport.exe.config, вступят в действие после перезапуска транспортной службы Microsoft Exchange.

  - При перезапуске транспортной службы Microsoft Exchange поток обработки почты на сервере временно прерывается.

  - Все специальные настройки, выполненные для каждого сервера в XML-файлах конфигурации приложения Exchange, например в файлах web.config на серверах клиентского доступа или файлах EdgeTransport.exe.config на серверах почтовых ящиков, будут перезаписаны после установки накопительного пакета обновления Exchange. Обязательно сохраните нужные данные, чтобы упростить перенастройку сервера после установки. Эти параметры необходимо перенастроить после установки накопительного пакета обновления Exchange.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной строки для включения и настройки приоритетной организации очереди в файле EdgeTransport.exe.config

1.  В командной строке откройте файл конфигурации приложения EdgeTransport.exe.config в Блокноте, выполнив следующую команду:
    
    ```powershell
        Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config
    ```

2.  Найдите следующие ключи в разделе `<appSettings>`.
    
    ```powershell
        <add key="PriorityQueuingEnabled" value="false" />
        <add key="MaxPerDomainHighPriorityConnections" value="3" />
        <add key="MaxPerDomainNormalPriorityConnections" value="15" />
        <add key="MaxPerDomainLowPriorityConnections" value="2" />
        <add key="HighPriorityMessageExpirationTimeout" value="8:00:00" />
        <add key="NormalPriorityMessageExpirationTimeout" value="2.00:00:00" />
        <add key="LowPriorityMessageExpirationTimeout" value="2.00:00:00" />
        <add key="HighPriorityDelayNotificationTimeout" value="00:30:00" />
        <add key="NormalPriorityDelayNotificationTimeout" value="4:00:00" />
        <add key="LowPriorityDelayNotificationTimeout" value="8:00:00" />
        <add key="MaxHighPriorityMessageSize" value="250KB" />
    ```

Чтобы включить приоритетную организацию очереди в службе транспорта на сервере почтовых ящиков, используйте следующее значение.

```powershell
<add key="PriorityQueuingEnabled" value="true" />
```

Настройте остающиеся значения приоритетной организации очереди или оставьте их по умолчанию.

3.  Закончив, сохраните и закройте файл EdgeTransport.exe.config.

4.  Перезапустите службу транспорта Microsoft Exchange, выполнив следующую команду:
    
    ```powershell
        net stop MSExchangeTransport && net start MSExchangeTransport
    ```

## Как проверить, что все получилось?

Чтобы убедиться в успешном включении и настройке приоритетной организации очереди, выполните следующие действия.

1.  Убедитесь, что ключ **PriorityQueueinEnabled** в файле EdgeTransport.exe.config имеет значение `"true"`.

2.  В Outlook создайте тестовое сообщение высокой важности, которое превышает значение, указанное ключом **MaxHighPriorityMessageSize**, и убедитесь, что сообщение приходит как сообщение обычной важности.

3.  Постарайтесь убедиться, что сообщения более высокой важности приходят до отправки сообщений более низкой важности тому же самому получателю. Вы можете попробовать использовать несколько почтовых ящиков для отправки нескольких аналогичных тестовых сообщений с разными значениями приоритетов одному и тому же получателю одновременно.

