---
title: 'Настройка ведения журнала для протоколов POP3 и IMAP4: Exchange 2013 Help'
TOCTitle: Настройка ведения журнала для протоколов POP3 и IMAP4
ms:assetid: 451b337b-cb6b-4460-8687-be0b19c469bc
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa997690(v=EXCHG.150)
ms:contentKeyID: 50556372
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка ведения журнала для протоколов POP3 и IMAP4

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-11-27_

С помощью командной консоли можно включить, отключить или изменить настройки ведения журнала протокола для POP3 и IMAP4. По умолчанию ведение журнала протокола отключено.

Функция ведения журнала протокола позволяет просматривать подключения по протоколам POP3 и IMAP4 в среде Exchange. Эти сведения могут быть полезны при устранении неполадок, связанных с производительностью протоколов POP3 или IMAP4. Дополнительные сведения см. в разделе [Ведение журнала для протоколов POP3 и IMAP4](protocol-logging-for-pop3-and-imap4-exchange-2013-help.md). Дополнительные сведения о POP3 и IMAP4 см. в разделе [POP3 и IMAP4 в Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Записи "Параметры POP3" и "Параметры IMAP4" в разделе [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Что необходимо сделать?

## Использование командной консоли для включения ведения журнала для протоколов POP3 или IMAP4

В этом примере выполняется включение ведения журнала для протоколов IMAP4 или POP3 на сервере клиентского доступа CAS01.

    Set-ImapSettings -Server "CAS01" -ProtocolLogEnabled $true
    Set-PopSettings -Server "CAS01" -ProtocolLogEnabled $true

> [!NOTE]  
> После изменения параметров ведения журнала протокола для POP3 или IMAP4 необходимо перезапустить используемые службы: POP3 или IMAP4. Дополнительные сведения о перезапуске служб POP3 и IMAP4 см. в разделах <a href="start-and-stop-the-pop3-services-exchange-2013-help.md">Запуск и остановка служб POP3</a> и <a href="start-and-stop-the-imap4-services-exchange-2013-help.md">Запуск и остановка служб IMAP4</a>.


Дополнительные сведения о синтаксисе и параметрах см. в разделах [Set-IMAPSettings](https://technet.microsoft.com/ru-ru/library/aa998252\(v=exchg.150\)) и [Set-POPSettings](https://technet.microsoft.com/ru-ru/library/aa997154\(v=exchg.150\)).

## Использование командной консоли Exchange для отключения ведения журнала для протоколов POP3 или IMAP4

В этом примере выполняется отключение ведения журнала для протоколов IMAP4 или POP3 на сервере клиентского доступа CAS01.

    Set-ImapSettings -Server "CAS01" -protocolLogEnabled $false
    Set-PopSettings -Server "CAS01" -protocolLogEnabled $false

> [!NOTE]  
> После изменения параметров ведения журнала протокола для POP3 или IMAP4 необходимо перезапустить используемые службы: POP3 или IMAP4. Дополнительные сведения о перезапуске служб POP3 и IMAP4 см. в разделах <a href="start-and-stop-the-pop3-services-exchange-2013-help.md">Запуск и остановка служб POP3</a> и <a href="start-and-stop-the-imap4-services-exchange-2013-help.md">Запуск и остановка служб IMAP4</a>.


Дополнительные сведения о синтаксисе и параметрах см. в разделах [Set-IMAPSettings](https://technet.microsoft.com/ru-ru/library/aa998252\(v=exchg.150\)) и [Set-POPSettings](https://technet.microsoft.com/ru-ru/library/aa997154\(v=exchg.150\)).

## Использование командной консоли Exchange для изменения параметров ведения журнала для протоколов POP3 или IMAP4

Чтобы изменить параметры ведения журнала для протоколов POP3 или IMAP4, запустите командлеты **Set-ImapSettings** или **Set-PopSettings** с одним или несколькими следующими параметрами.

  - *LogFileLocation*   Этот параметр указывает расположение файлов журнала протокола POP3 или IMAP4. По умолчанию файлы журнала протокола POP3 расположены в каталоге C:\\Program Files\\Microsoft\\Exchange Server\\V15\\Logging\\Pop3. В этом примере выполняется включение ведения журнала для протокола POP3 на сервере клиентского доступа CAS01. В нем также задается каталог журнала протокола POP3: C:\\Pop3Logging.
    
    ```powershell
Set-PopSettings -Server "CAS01" -ProtocolLogEnabled $true -LogFileLocation "C:\Pop3Logging"
```

  - *LogFileRollOverSettings*   Этот параметр определяет, как часто в ходе ведения журнала протокола POP3 или IMAP4 создаются новые файлы журналов. По умолчанию новый файл журнала создается каждый день. Возможные значения:
    
    Hourly (Каждый час)
    
    Daily (Ежедневно)
    
    Weekly (Еженедельно)
    
    Monthly (Ежемесячно)
    
    Этот параметр применяется, только если параметр *LogPerFileSizeQuota* имеет нулевое значение. В этом примере параметры ведения журнала для протокола POP3 на сервере клиентского доступа CAS01 изменяются таким образом, чтобы новый файл журнала создавался каждый час.
    
    ```powershell
Set-PopSettings -Server "CAS01" -LogPerFileSizeQuota 0 -LogFileRollOverSettings Hourly
```

  - *LogPerFileSizeQuota*   Этот параметр указывает максимальный размер файла журнала протокола POP3 или IMAP4 в байтах. По умолчанию для этого параметра установлено нулевое значение. Если значение равно нулю, то новые файлы журнала протокола создаются с частотой, заданной параметром *LogFileRollOverSettings*.
    
    В этом примере параметры ведения журнала для протокола POP3 на сервере клиентского доступа CAS01 изменяются таким образом, чтобы новый файл журнала создавался при достижении предыдущим файлом размера 2 МБ.
    
    ```powershell
Set-PopSettings -Server "CAS01" -LogPerFileSizeQuota 2000000
```
    
    В этом примере параметры ведения журнала для протокола POP3 на сервере клиентского доступа CAS01 изменяются таким образом, чтобы использовался тот же файл журнала независимо от его размера и даты создания.
    
    ```powershell
Set-PopSettings -Server "CAS01" -LogPerFileSizeQuota unlimited
```

> [!NOTE]  
> После изменения параметров ведения журнала протокола для POP3 или IMAP4 необходимо перезапустить используемые службы: POP3 или IMAP4. Дополнительные сведения о перезапуске служб POP3 и IMAP4 см. в разделах <a href="start-and-stop-the-pop3-services-exchange-2013-help.md">Запуск и остановка служб POP3</a> и <a href="start-and-stop-the-imap4-services-exchange-2013-help.md">Запуск и остановка служб IMAP4</a>.


Дополнительные сведения о синтаксисе и параметрах см. в разделах [Set-IMAPSettings](https://technet.microsoft.com/ru-ru/library/aa998252\(v=exchg.150\)) и [Set-POPSettings](https://technet.microsoft.com/ru-ru/library/aa997154\(v=exchg.150\)).

## Как проверить, что все получилось?

Выполните следующую команду в командной консоли, чтобы проверить параметры ведения журнала протокола POP3. Если ведение журнала протокола POP3 включено, для параметра *ProtocolLogEnabled* устанавливается значение `True`. Если ведение журнала протокола POP3 отключено, устанавливается значение `False`. Также можно убедиться в правильности значений параметров *LogFileLocation*, *LogPerFileSizeQuota* и *LogFileRollOverSettings*.

```powershell
Get-PopSettings | format-list
```

Выполните следующую команду в командной консоли, чтобы проверить параметры ведения журнала протокола IMAP4. Если ведение журнала протокола IMAP4 включено, для параметра *ProtocolLogEnabled* устанавливается значение `True`. Если ведение журнала протокола IMAP4 отключено, устанавливается значение `False`. Также можно убедиться в правильности значений параметров *LogFileLocation*, *LogPerFileSizeQuota* и *LogFileRollOverSettings*.

```powershell
Get-ImapSettings | format-list
```

## Дополнительные сведения

После настройки параметров ведения журнала для протоколов POP3 и IMAP4 можно выполнить также следующие действия:

[Запуск и остановка служб IMAP4](start-and-stop-the-imap4-services-exchange-2013-help.md)

[Запуск и остановка служб POP3](start-and-stop-the-pop3-services-exchange-2013-help.md)

