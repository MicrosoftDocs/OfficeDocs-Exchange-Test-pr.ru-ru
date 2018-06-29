﻿---
title: 'Включение протокола POP3 в Exchange 2013: Exchange 2013 Help'
TOCTitle: Включение протокола POP3
ms:assetid: e226a5f1-429d-4046-b925-da6cc151709e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124934(v=EXCHG.150)
ms:contentKeyID: 50489373
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Включение протокола POP3 в Exchange 2013

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2017-03-28_

В этой статье рассказывается, как включить возможность подключения к клиентам по протоколу POP3 в Exchange 2016 с помощью консоли управления (MMC) или Командная консоль Exchange.

При установке Exchange Server 2016 возможность подключения к клиентам по протоколу POP3 не включена. Чтобы включить ее, вам потребуется запустить две службы POP3: Microsoft Exchange POP3 и внутреннюю службу Microsoft Exchange POP3. Если вы включите поддержку протокола POP3, Exchange 2016 будет принимать незащищенные данные от клиентов по протоколу POP3 через порт 110, а данные, защищенные SSL, — через порт 995.

Вы можете управлять службой POP3 и внутренней службой POP3 на одном и том же компьютере Exchange 2016 с ролью сервера почтовых ящиков. В Exchange 2016 службы клиентского доступа включены в состав роли сервера почтовых ящиков, поэтому вам не нужно управлять этими службами отдельно друг от друга.

Дополнительные сведения о настройке протоколов POP3 и IMAP4 см. в статье [POP3 и IMAP4 в Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 2 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статьеРаздел "Разрешения POP3 и IMAP4" в статье [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

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

## Включение поддержки протокола POP3 с помощью консоли управления (MMC)

На компьютере с ролью сервера почтовых ящиков:

1.  В оснастке **Службы** в дереве консоли щелкните **Службы (локальные)**.

2.  В области результатов щелкните правой кнопкой мыши **Microsoft Exchange POP3**, а затем выберите команду **Свойства**.

3.  В области результатов щелкните правой кнопкой мыши **Фоновая служба Microsoft Exchange POP3**, а затем выберите пункт **Свойства**.

4.  На вкладке **Общие** в разделе **Тип запуска** выберите **Авто**, а затем нажмите кнопку **Применить**.

5.  В разделе **Состояние службы** нажмите кнопку **Запустить**, а затем нажмите кнопку **ОК**.

## Включение поддержки протокола POP3 с помощью Командная консоль Exchange

На компьютере с ролью сервера почтовых ящиков:

1.  Задайте автоматический запуск службы Microsoft Exchange POP3.
    
        Set-service msExchangePOP3 -startuptype automatic

2.  Запустите службу Microsoft Exchange POP3.
    
        Start-service msExchangePOP3

3.  Задайте автоматический запуск фоновой службы Microsoft Exchange POP3.
    
        Set-service msExchangePOP3BE -startuptype automatic

4.  Запустите фоновую службу Microsoft Exchange POP3.
    
        Start-service msExchangePOP3BE

## Как проверить, что все получилось?

На сервере почтовых ящиков Exchange 2016 откройте диспетчер задач Windows. Если поддержка протокола POP3 включена, то на вкладке **Службы** для служб **MSExchangePOP3** и **MSExchangePOP3BE** будет отображаться состояние **Работает**.

