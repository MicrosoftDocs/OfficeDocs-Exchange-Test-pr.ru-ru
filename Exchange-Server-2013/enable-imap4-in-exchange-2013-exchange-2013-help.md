---
title: 'Включение протокола IMAP4 в Exchange 2016: Exchange 2013 Help'
TOCTitle: Включение протокола IMAP4 в Exchange 2016
ms:assetid: c1ae10dd-14da-4400-b38d-2aeafde8abe6
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124489(v=EXCHG.150)
ms:contentKeyID: 50489094
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Включение протокола IMAP4 в Exchange 2016

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-06-02_

В этой статье рассказывается, как включить возможность подключения к клиентам по протоколу IMAP4 в Exchange 2016 с помощью консоли управления (MMC) или Командная консоль Exchange.

При установке Exchange Server 2016 возможность подключения к клиентам по протоколу IMAP4 не включена. Чтобы включить ее, вам потребуется запустить две службы IMAP: Microsoft Exchange IMAP4 и внутреннюю службу Microsoft Exchange IMAP4. Если вы включите поддержку протокола IMAP4, Exchange 2016 будет принимать незащищенные данные от клиентов по протоколу IMAP4 через порт 143, а данные, защищенные SSL, — через порт 993.

Вы можете управлять службой IMAP4 и внутренней службой IMAP4 на одном и том же компьютере Exchange 2016 с ролью сервера почтовых ящиков. В Exchange 2016 службы клиентского доступа включены в состав роли сервера почтовых ящиков, поэтому вам не нужно управлять этими службами отдельно друг от друга.

Дополнительные сведения о настройке протоколов POP3 и IMAP4 см. в статье [POP3 и IMAP4 в Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 2 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статьеРаздел "Разрешения POP3 и IMAP4" в статье [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Включение поддержки протокола IMAP4 с помощью консоли управления (MMC)

На компьютере с ролью сервера почтовых ящиков:

1.  В оснастке **Службы** в дереве консоли щелкните **Службы (локальные)**.

2.  В области результатов щелкните правой кнопкой мыши **Microsoft Exchange IMAP4** и выберите пункт **Свойства**.

3.  В области результатов щелкните правой кнопкой мыши **Microsoft Exchange IMAP4 Backend** и выберите пункт **Свойства**.

4.  На вкладке **Общие** в разделе **Тип запуска** выберите **Авто**, а затем нажмите кнопку **Применить**.

5.  В разделе **Состояние службы** нажмите кнопку **Запустить**, а затем нажмите кнопку **ОК**.

## Включение поддержки протокола IMAP4 с помощью Командная консоль Exchange

На компьютере с ролью сервера почтовых ящиков:

1.  Задайте автоматический запуск службы Microsoft Exchange IMAP4.
    
        Set-service msExchangeIMAP4 -startuptype automatic

2.  Запустите службу Microsoft Exchange IMAP4.
    
        Start-service msExchangeIMAP4

3.  Задайте автоматический запуск службы Microsoft Exchange IMAP4 Backend.
    
        Set-service msExchangeIMAP4BE -startuptype automatic

4.  Запустите службу Microsoft Exchange IMAP4 Backend.
    
        Start-service msExchangeIMAP4BE

## Как проверить, что все получилось?

На сервере почтовых ящиков Exchange 2016 откройте диспетчер задач Windows. Если поддержка протокола IMAP4 включена, то на вкладке **Службы** для служб **MSExchangeIMAP4** и **MSExchangeIMAP4BE** будет отображаться состояние **Работает**.

