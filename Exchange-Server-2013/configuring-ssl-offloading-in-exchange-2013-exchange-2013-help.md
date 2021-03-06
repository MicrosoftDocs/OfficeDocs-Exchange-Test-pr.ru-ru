﻿---
title: 'Настройка разгрузки SSL в Exchange 2013: Exchange 2013 Help'
TOCTitle: Настройка разгрузки SSL в Exchange 2013
ms:assetid: 654cc2c2-918b-48fc-9532-9c8e3012810d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn635115(v=EXCHG.150)
ms:contentKeyID: 61203527
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка разгрузки SSL в Exchange 2013

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-08-22_

Следующая информация поможет вам настроить разгрузку SSL для протоколов и связанных служб на серверах клиентского доступа Exchange 2013 с установленным пакетом обновления 1 (SP1). Если используется несколько серверов клиентского доступа, необходимые шаги требуется выполнить для каждого протокола или службы на каждом сервере клиентского доступа с установленным пакетом обновления 1 (SP1) в вашей локальной организации. Подразумевается, что каждый сервер клиентского доступа в организации должен быть настроен идентично. Если вы устанавливаете новые накопительные пакеты обновления (CU) или пакеты обновления (SP) и хотите продолжить использование разгрузки SSL, необходимо опять выполнить следующие действия после обновления или установки этих обновлений на серверы клиентского доступа Exchange 2013.

Одно из главных преимуществ разгрузки SSL — возможность более простого управления используемыми сертификатами. Вместо отдельных SSL-сертификатов для каждого сервера клиентского доступа с пакетом обновления 1 (SP1) используется один SSL-сертификат, который импортируется на все серверы клиентского доступа. Это может быть существующий или специально созданный SSL-сертификат.

> [!CAUTION]  
> При использовании диспетчера служб IIS, командной консоли Exchange или интерфейса командной строки для настройки разгрузки SSL следует помнить, что существует <strong>веб-сайт по умолчанию</strong> и <strong>фоновый сайт Exchange</strong>. Для разгрузки SSL настраивается только <strong>веб-сайт по умолчанию</strong>, а <strong>фоновый сайт Exchange</strong> не изменяется.


**Содержание**

Настройка разгрузки SSL для Outlook Web App

Настройка разгрузки SSL для центра администрирования Exchange (EAC)

Настройка разгрузки SSL для Outlook Anywhere

Настройка разгрузки SSL для автономной адресной книги (OAB)

Настройка разгрузки SSL для Exchange ActiveSync (EAS)

Настройка разгрузки SSL для веб-служб Exchange (EWS)

Настройка разгрузки SSL для службы автообнаружения

Настройка разгрузки SSL для прокси-службы репликации почтовых ящиков (MRSProxy)

Настройка разгрузки SSL для клиентов Outlook (виртуальный каталог MAPI)

Использование скрипта для включения разгрузки SSL для всех протоколов и служб

Настройка совместной работы Exchange 2007 и Exchange 2010

## Что нужно знать перед началом работы

  - Установите для вашей организации все необходимые серверы клиентского доступа и серверы почтовых ящиков.

  - Установите пакет обновления 1 (SP1) на все серверы клиентского доступа и серверы почтовых ящиков в вашей организации. Сведения о том, как скачать пакет обновления 1 (SP1), см. в разделе [Обновления для Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md).

  - Определите необходимые разрешения для Exchange 2013, ознакомившись с разделом [Разрешения на функции](feature-permissions-exchange-2013-help.md).

  - Сведения о том, какие разрешения необходимы для серверов клиентского доступа, см. в разделе "Разрешения серверов клиентского доступа" статьи [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Сведения о том, какие разрешения необходимы для Outlook Web App, см. в разделе "Разрешения Outlook Web App" статьи [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Для выполнения некоторых процедур достаточно командной консоли. Сведения о том, как открыть командную консоль в локальной организации Exchange, см. в разделе [Открытие командной консоли Exchange](https://technet.microsoft.com/ru-ru/library/dd638134\(v=exchg.150\)).

  - Чтобы использовать существующий сертификат на серверах клиентского доступа и на устройстве, на котором терминируются SSL-подключения, экспортируйте сертификат с закрытым ключом на сервер клиентского доступа и импортируйте или установите его на устройство. Дополнительные сведения см. в разделе [Export-ExchangeCertificate](https://technet.microsoft.com/ru-ru/library/aa996305\(v=exchg.150\)).

  - Для применения нового сертификата необходимо с помощью EAC или командной консоли создать, импортировать и активировать новый сертификат. Дополнительные сведения см. в разделе [Пользовательский интерфейс управления сертификатами Exchange 2013](exchange-2013-certificate-management-ui-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Настройка разгрузки SSL для Outlook Web App

Чтобы включить разгрузку SSL для Outlook Web App, необходимо удалить требование SSL в виртуальном каталоге **owa** на **веб-сайте по умолчанию**:

  - **Шаг 1.** Вы можете использовать диспетчер служб IIS или командную строку, чтобы отключить SSL в виртуальном каталоге **owa**:
    
      - В диспетчере служб IIS разверните узел **Сайты** \> **Веб-сайт по умолчанию** и выберите виртуальный каталог **owa**. В области результатов в разделе **IIS** дважды щелкните пункт **Параметры SSL**. В области результатов **Параметры SSL** снимите флажок **Требовать SSL** и нажмите кнопку **Применить** в области **действий**.
    
      - В командной строке введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd set config "Default Web Site/owa" /section:access /sslFlags:None /commit:APPHOST
		```

  - **Шаг 2.** Необходимо перезапустить соответствующий пул приложений и службы IIS с помощью одного из следующих способов:
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd Recycle AppPool MSExchangeOWAAppPool
		```
    
      - Введите следующую команду Windows PowerShell и нажмите клавишу ВВОД:
        
        ```powershell
		IIS:\>Restart-WebAppPool MSExchangeOWAAppPool
		```
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		iisreset /noforce
		```
    
      - Использование диспетчера служб IIS. В диспетчере служб IIS в области **действий** щелкните **Перезапустить**.

В начало

## Настройка разгрузки SSL для центра администрирования Exchange (EAC)

Чтобы включить разгрузку SSL для EAC, необходимо удалить требование SSL в виртуальном каталоге **ecp** на **веб-сайте по умолчанию**:

  - **Шаг 1.** Вы можете использовать диспетчер служб IIS или командную строку, чтобы отключить SSL в виртуальном каталоге **ecp**:
    
      - В диспетчере служб IIS разверните узел **Сайты** \> **Веб-сайт по умолчанию** и выберите виртуальный каталог **ecp**. В области результатов в разделе **IIS** дважды щелкните пункт **Параметры SSL**. В области результатов **Параметры SSL** снимите флажок **Требовать SSL** и нажмите кнопку **Применить** в области **действий**.
    
      - В командной строке введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd set config "Default Web Site/ecp" /section:access /sslFlags:None /commit:APPHOST
		```
        

  - **Шаг 2.** Необходимо перезапустить соответствующий пул приложений и службы IIS с помощью одного из следующих способов:
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd Recycle AppPool MSExchangeECPAppPool
		```
    
      - Введите следующую команду Windows PowerShell и нажмите клавишу ВВОД:
        
        ```powershell
		IIS:\>Restart-WebAppPool MSExchangeECPAppPool
		```
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		iisreset /noforce
		```
    
      - Использование диспетчера служб IIS. В диспетчере служб IIS в области **действий** щелкните **Перезапустить**.

В начало

## Настройка разгрузки SSL для Outlook Anywhere

По умолчанию разгрузка SSL для мобильного Outlook включена. Клиенты мобильного Outlook могут получать сообщения электронной почты из частной или общедоступной сети. По умолчанию, чтобы разрешить подключение внутренним клиентам Outlook, используется имя внутреннего узла или полное доменное имя сервера. Но если мобильный Outlook не используется во внутренней среде, необходимо удалить имя внутреннего узла. Чтобы разрешить внутренний и внешний доступ для клиентов Outlook, требуется настроить имена внутреннего и внешнего узла, задать для них способ проверки подлинности и настроить внутренние и внешние клиенты так, чтобы они требовали использование SSL. Способ проверки подлинности внешних клиентов можно настроить с помощью EAC или командной консоли Exchange, но для внутренних клиентов необходимо использовать командную консоль:

  - **Шаг 1**. Вы можете использовать Центр администрирования Exchange или командную консоль, если вы не добавили имя внешнего узла для мобильного Outlook:
    
      - В EAC откройте раздел **Серверы**, выберите имя сервера клиентского доступа, а затем нажмите кнопку **Изменить**. В окне **Exchange Server** щелкните **Outlook Anywhere** и в поле **Укажите имя внешнего узла (например, contoso.com), с помощью которого пользователи будут подключаться к вашей организации** введите имя внешнего узла. Убедитесь, что флажок **Разрешить разгрузку SSL** установлен, и нажмите кнопку **Сохранить**.
    
      - В командной консоли Exchange нажмите **Пуск** и в меню **Пуск** щелкните **Командная консоль Exchange**. В открывшемся окне введите следующую команду и нажмите клавишу ВВОД:
        ```powershell
            Set-OutlookAnywhere -Identity ClientAccessServer1\Rpc* -Externalhostname ClientAccessServer1.contoso.com -ExternalClientsRequireSsl:$True -ExternalClientAuthenticationMethod Basic
		```
  - **Шаг 2**. По умолчанию разгрузка SSL включена. Но вы можете использовать EAC или командную консоль Exchange, если разгрузка SSL была отключена и вам требуется ее включить:
    
      - В EAC откройте раздел **Серверы**, выберите имя сервера клиентского доступа, а затем нажмите кнопку **Изменить**. В окне **Exchange Sever** щелкните **Outlook Anywhere**, установите флажок **Разрешить разгрузку SSL** и нажмите кнопку **Сохранить**.
    
      - В командной консоли введите следующую команду и нажмите клавишу ВВОД:
        ```powershell
            Set-OutlookAnywhere -Identity ClientAccessServer1\Rpc* -SSLOffloading $true
		```
  - **Шаг 3.** По умолчанию параметр **Требовать SSL** не выбран для виртуального каталога **Rpc**, но если вы хотите убедиться, что SSL отключен, можно воспользоваться диспетчером IIS.
    
      - В диспетчере служб IIS разверните узел **Сайты** \> **Веб-сайт по умолчанию** и выберите виртуальный каталог **Rpc**. В области результатов в разделе **IIS** дважды щелкните пункт **Параметры SSL**. В области результатов **Параметры SSL** убедитесь, что флажок **Требовать SSL** снят, и нажмите кнопку **Применить** в области **действий**.

  - **Шаг 4.** Необходимо перезапустить соответствующий пул приложений и службы IIS с помощью одного из следующих способов:
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd Recycle AppPool MSExchangeRpcProxyFrontEndAppPool
		```
    
      - Введите следующую команду Windows PowerShell и нажмите клавишу ВВОД:
        
        ```powershell
		IIS:\>Restart-WebAppPool MSExchangeRpcProxyFrontEndAppPool
		```
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		iisreset /noforce
		```
    
      - Использование диспетчера служб IIS. В диспетчере служб IIS в области **действий** щелкните **Перезапустить**.

> [!IMPORTANT]  
> Необходимо дождаться того, что процесс узла службы применит все изменения из Active Directory в службах IIS (что происходит каждые 15 минут), даже если вы перезапустите службы IIS на сервере клиентского доступа.


В начало

## Настройка разгрузки SSL для автономной адресной книги (OAB)

Чтобы включить разгрузку SSL для автономной адресной книги (OAB), необходимо удалить требование SSL в виртуальном каталоге **OAB** на **веб-сайте по умолчанию**:

  - **Шаг 1.** Вы можете использовать диспетчер служб IIS или командную строку, чтобы отключить SSL в виртуальном каталоге **OAB**:
    
      - В диспетчере служб IIS разверните узел **Сайты** \> **Веб-сайт по умолчанию** и выберите виртуальный каталог **OAB**. В области результатов в разделе **IIS** дважды щелкните пункт **Параметры SSL**. В области результатов **Параметры SSL** снимите флажок **Требовать SSL** и нажмите кнопку **Применить** в области **действий**.
    
      - В командной строке введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd set config "Default Web Site/OAB" /section:access /sslFlags:None /commit:APPHOST
		```

  - **Шаг 2.** Необходимо перезапустить соответствующий пул приложений и службы IIS с помощью одного из следующих способов:
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd Recycle AppPool MSExchangeOABAppPool
		```
    
      - Введите следующую команду Windows PowerShell и нажмите клавишу ВВОД:
        
        ```powershell
		IIS:\>Restart-WebAppPool MSExchangeOABAppPool
		```
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		iisreset /noforce
		```
    
      - Использование диспетчера служб IIS. В диспетчере служб IIS в области **действий** щелкните **Перезапустить**.

В начало

## Настройка разгрузки SSL для Exchange ActiveSync (EAS)

Чтобы включить разгрузку SSL для Exchange ActiveSync (EAS), необходимо удалить требование SSL в виртуальном каталоге **Microsoft-Server-ActiveSync** на **веб-сайте по умолчанию**:

  - **Шаг 1.** Вы можете использовать диспетчер служб IIS или командную строку, чтобы отключить SSL в виртуальном каталоге **Microsoft-Server-ActiveSync**:
    
      - В диспетчере служб IIS разверните узел **Сайты** \> **Веб-сайт по умолчанию** и выберите виртуальный каталог **Microsoft-Server-ActiveSync**. В области результатов в разделе **IIS** дважды щелкните пункт **Параметры SSL**. В области результатов **Параметры SSL** снимите флажок **Требовать SSL** и нажмите кнопку **Применить** в области **действий**.
    
      - В командной строке введите следующую команду и нажмите клавишу ВВОД:
        ```powershell
            appcmd set config "Default Web Site/MSExchangeSyncAppPool" /section:access /sslFlags:None /commit:APPHOST
		```
  - **Шаг 2.** Необходимо перезапустить соответствующий пул приложений и службы IIS с помощью одного из следующих способов:
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd Recycle AppPool MSExchangeSyncAppPool
		```
    
      - Введите следующую команду Windows PowerShell и нажмите клавишу ВВОД:
        
        ```powershell
		IIS:\>Restart-WebAppPool MSExchangeSyncAppPool
		```
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		iisreset /noforce
		```
    
      - Использование диспетчера служб IIS. В диспетчере служб IIS в области **действий** щелкните **Перезапустить**.

В начало

## Настройка разгрузки SSL для веб-служб Exchange (EWS)

Чтобы включить разгрузку SSL для веб-служб Exchange (EWS), необходимо удалить требование SSL в виртуальном каталоге **EWS** на **веб-сайте по умолчанию**:

  - **Шаг 1.** Вы можете использовать диспетчер служб IIS или командную строку, чтобы отключить SSL в виртуальном каталоге **EWS**:
    
      - В диспетчере служб IIS разверните узел **Сайты** \> **Веб-сайт по умолчанию** и выберите виртуальный каталог **EWS**. В области результатов в разделе **IIS** дважды щелкните пункт **Параметры SSL**. В области результатов **Параметры SSL** снимите флажок **Требовать SSL** и нажмите кнопку **Применить** в области **действий**.
    
      - В командной строке введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd set config "Default Web Site/EWS" /section:access /sslFlags:None /commit:APPHOST
		```

  - **Шаг 2.** Необходимо перезапустить соответствующий пул приложений и службы IIS с помощью одного из следующих способов:
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd Recycle AppPool MSExchangeServicesAppPool
		```
    
      - Введите следующую команду Windows PowerShell и нажмите клавишу ВВОД:
        
        ```powershell
		IIS:\>Restart-WebAppPool MSExchangeServicesAppPool
		```
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		iisreset /noforce
		```
    
      - Использование диспетчера служб IIS. В диспетчере служб IIS в области **действий** щелкните **Перезапустить**.

В начало

## Настройка разгрузки SSL для службы автообнаружения

Чтобы включить разгрузку SSL для службы автообнаружения, необходимо удалить требование SSL в виртуальном каталоге **Autodiscover** на **веб-сайте по умолчанию**:

  - **Шаг 1.** Вы можете использовать диспетчер служб IIS или командную строку, чтобы отключить SSL в виртуальном каталоге **Autodiscover**:
    
      - В диспетчере служб IIS разверните узел **Сайты** \> **Веб-сайт по умолчанию** и выберите виртуальный каталог **Autodiscover**. В области результатов в разделе **IIS** дважды щелкните пункт **Параметры SSL**. В области результатов **Параметры SSL** снимите флажок **Требовать SSL** и нажмите кнопку **Применить** в области **действий**.
    
      - В командной строке введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd set config "Default Web Site/autodiscover" /section:access /sslFlags:None /commit:APPHOST
		```

  - **Шаг 2.** Необходимо перезапустить соответствующий пул приложений и службы IIS с помощью одного из следующих способов:
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd Recycle AppPool MSExchangeAutodiscoverAppPool
		```
    
      - Введите следующую команду Windows PowerShell и нажмите клавишу ВВОД:
        
        ```powershell
		IIS:\>Restart-WebAppPool MSExchangeAutodiscoverAppPool
		```
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		iisreset /noforce
		```
    
      - Использование диспетчера служб IIS. В диспетчере служб IIS в области **действий** щелкните **Перезапустить**.

В начало

## Настройка разгрузки SSL для прокси-службы репликации почтовых ящиков (MRSProxy)

Прокси-служба репликации почтовых ящиков (MRSProxy) устанавливается на каждом сервере клиентского доступа Exchange 2013. MRSProxy помогает выполнять запросы на перемещение между лесами, а также перемещать локальные почтовые ящики в Office 365. Однако по умолчанию служба MRSProxy отключена. Если вы ее включаете, то ее необходимо активировать в удаленном лесу Exchange для перемещения локальных почтовых ящиков между лесами или в локальном лесу Exchange для перемещения почтовых ящиков в Office 365. Хотя служба MRSProxy работает на основе веб-служб Exchange (EWS), она не поддерживается для настройки разгрузки SSL.

Это связано с тем, что служба MRSProxy ожидает, что трафик будет подписан или зашифрован. Любая аппаратная подсистема балансировки нагрузки или брандмауэр должны повторно шифровать трафик MRSProxy перед его отправкой на серверы клиентского доступа. В этом случае рекомендуется настроить мост SSL для реализации разгрузки.

**Обратное преобразование SSL или мост SSL.** Если вы включили обратное преобразование SSL или мост SSL в аппаратных подсистемах балансировки нагрузки, нет необходимости выполнять предыдущие действия на каждом сервере клиентского доступа. Однако активация обратного преобразования SSL в аппаратных подсистемах балансировки нагрузки означает, что шифрование и расшифровка SSL будет применяться на серверах клиентского доступа. В этом случае шифрование и расшифровка SSL будут выполняться в аппаратных подсистемах балансировки нагрузки и на серверах клиентского доступа. Выбор разгрузки SSL Exchange 2013 или обратного преобразования SSL (моста SSL) зависит от целей организации и рекомендаций безопасности, которые необходимо реализовать. На следующем рисунке показаны возможности подключения клиентов с включенным мостом SSL (обратное преобразование SSL).

![Мост SSL](images/Dn635115.a08aacc1-0ab4-46b3-bdae-b9518a3f5748(EXCHG.150).jpg "Мост SSL")

## Настройка разгрузки SSL для клиентов Outlook (виртуальный каталог MAPI)

Чтобы включить разгрузку SSL для клиентов Outlook, необходимо удалить требование SSL в виртуальном каталоге **MAPI** на **веб-сайте по умолчанию**:

  - **Шаг 1.** Вы можете использовать диспетчер служб IIS или командную строку, чтобы отключить SSL в виртуальном каталоге **MAPI**:
    
      - В диспетчере служб IIS разверните узел **Сайты** \> **Веб-сайт по умолчанию** и выберите виртуальный каталог **MAPI**. В области результатов в разделе **IIS** дважды щелкните пункт **Параметры SSL**. В области результатов **Параметры SSL** снимите флажок **Требовать SSL** и нажмите кнопку **Применить** в области **действий**.
    
      - В командной строке введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd set config "Default Web Site/MAPI" /section:access /sslFlags:None /commit:APPHOST
		```

  - **Шаг 2.** Необходимо перезапустить соответствующий пул приложений и службы IIS с помощью одного из следующих способов:
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		appcmd Recycle AppPool MSExchangeMapiFrontEndAppPool
		```
			
      - Введите следующую команду Windows PowerShell и нажмите клавишу ВВОД:
        
        ```powershell
		IIS:\>Restart-WebAppPool MSExchangeMapiFrontEndAppPool
		```
    
      - Использование командной строки. Нажмите кнопку **Пуск**, выберите пункт **Выполнить**, введите **cmd** и нажмите клавишу ВВОД. В окне командной строки введите следующую команду и нажмите клавишу ВВОД:
        
        ```powershell
		iisreset /noforce
		```
    
      - Использование диспетчера служб IIS. В диспетчере служб IIS в области **действий** щелкните **Перезапустить**.

В начало

## Использование скрипта для включения разгрузки SSL для всех протоколов и служб

Если вы работаете с крупной организацией со множеством серверов клиентского доступа Exchange 2013, возможно, вы захотите ускорить описанные ранее действия. Вы можете скопировать и вставить команды из следующих скриптов в Блокнот, внести изменения, сохранить файл с расширением .ps1 и выполнить их в командной консоли Exchange. В зависимости от ваших потребностей оба эти скрипта можно использовать для настройки разгрузки SSL для всех протоколов и служб на одном или нескольких серверах клиентского доступа.

> [!NOTE]  
> Там, где используется командлет <strong>Set-OutlookAnywhere</strong>, замените &quot;MyServer&quot; на имена ваших серверов клиентского доступа.


**Использование Set-WebConfigurationProperty**
```powershell
    Set-OutlookAnywhere -Identity MyServer\Rpc* -Externalhostname MyServer.mail.contoso.com -ExternalClientsRequireSsl $True -ExternalClientAuthenticationMethod Basic
    Set-OutlookAnywhere -Identity MyServer\Rpc* -SSLOffloading $true
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS:  -Location "Default Web Site/OWA"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/ecp"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/EWS"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/Autodiscover"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/Microsoft-Server-ActiveSync"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/OAB"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/MAPI"
```
```powershell
iisreset /noforce
```

**Использование appcmd**

> [!NOTE]  
> Там, где используется командлет <strong>Set-OutlookAnywhere</strong>, замените &quot;MyServer&quot; на имена ваших серверов клиентского доступа.

```powershell
    Set-OutlookAnywhere -Identity MyServer\Rpc* -Externalhostname MyServer.mail.contoso.com -ExternalClientsRequireSsl $True -ExternalClientAuthenticationMethod Basic
    Set-OutlookAnywhere -Identity MyServer\Rpc* -SSLOffloading $true
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/owa" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/ecp" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/EWS" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/Autodiscover" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/Microsoft-Server-ActiveSync" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/OAB" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/MAPI" /section:access /sslFlags:None /commit:APPHOST
```	
```powershell
iisreset /noforce
```

В начало

## Настройка совместной работы Exchange 2007 и Exchange 2010

В сценарии совместной работы серверов Exchange 2003 и Exchange 2010 в организации одним из первых действий после развертывания серверов клиентского доступа Exchange 2010 должно быть изменение DNS, чтобы пользователи Exchange 2003 получили доступ к своим почтовым ящикам на группе серверов клиентского доступа Exchange 2010. В таком сценарии можно включить разгрузку SSL в подсистеме балансировки нагрузки, используемой для распределения клиентского трафика по серверам клиентского доступа.

**Совместная работа с другими версиями Outlook Web App**

Если разгрузка SSL настроена на серверах клиентского доступа Exchange 2013, поддерживается совместная работа с Exchange 2007 и Exchange 2010:

  - Для совместной работы с Exchange 2007 требуется предыдущее пространство имен, а перенаправление в него будет работать только для Outlook Web App и веб-служб Exchange. Служба автообнаружения, Outlook Anywhere и Exchange ActiveSync будут переадресованы на предыдущие версии.

  - Для совместной работы с Exchange 2010 (если задан внешний URL-адрес) будет использоваться перенаправление. В противном случае будет использоваться прокси-сервер.

В начало

