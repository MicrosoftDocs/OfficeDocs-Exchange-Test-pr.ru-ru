---
title: 'Предварительные требования для Exchange 2013: Exchange 2013 Help'
TOCTitle: Предварительные требования для Exchange 2013
ms:assetid: e21cf744-7813-48b3-9293-5cecd89a6c25
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb691354(v=EXCHG.150)
ms:contentKeyID: 50489257
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Предварительные требования для Exchange 2013

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2017-03-20_

В этом разделе приведены инструкции по установке необходимых компонентов операционной системы Windows Server 2012 R2, Windows Server 2012 и Windows Server 2008 R2 с пакетом обновления 1 (SP1) для ролей сервера почтовых ящиков, клиентского доступа и пограничного транспортного сервера Exchange 2013. Тут также описаны компоненты, необходимые для установки средств управления Exchange 2013 на компьютерах под управлением Windows 8, Windows 8.1 и Windows 7.

  - Что нужно знать перед началом работы

  - Подготовка Active Directory

  - Необходимые условия для установки Windows Server 2012 R2 и Windows Server 2012
    
      - Роли серверов почтовых ящиков или клиентского доступа
    
      - Роль пограничного транспортного сервера

  - Необходимые компоненты для Windows Server 2008 R2 с пакетом обновления 1 (SP1)
    
      - Роли серверов почтовых ящиков или клиентского доступа
    
      - Роль пограничного транспортного сервера

  - Необходимые условия для установки Windows 7 (только для средств администрирования) (только для средств администрирования)

  - Необходимые условия для установки Windows 8 и Windows 8.1 (только для средств администрирования) (только для средств администрирования)

## Что нужно знать перед началом работы

  - Сведения в этом разделе применимы к пакету обновления 1 и более поздним версиям Exchange 2013.

  - Роль пограничного транспортного сервера доступна в Exchange 2013 с пакетом обновления 1 (SP1) и более поздних версий.

  - Убедитесь, что используется режим работы леса не ниже Windows Server 2003, а хозяин схемы работает под управлением Windows Server 2003 с пакетом обновления 2 (SP2) или более поздней версии. Дополнительные сведения о режиме работы Windows см. в статье [Управление доменами и лесами](https://go.microsoft.com/fwlink/p/?linkid=137037).

  - Для всех серверов, на которых запущены роли сервера или средства управления Exchange 2013, следует использовать полный вариант установки Windows Server 2012 R2, Windows Server 2008 и Windows Server 2012 R2 с пакетом обновления 1 (SP1).

  - Сначала нужно присоединить компьютер к соответствующему внутреннему лесу и домену Active Directory.

  - Некоторые компоненты требуют перезагрузки сервера для завершения установки.

  - Установите на компьютере последние обновления Windows. Дополнительные сведения см. в разделе [Контрольный список по безопасности развертывания](deployment-security-checklist-exchange-2013-help.md).
    
    > [!NOTE]  
    > Если при установке роли сервера почтовых ящиков необходимо сделать сервер членом группы обеспечения доступности баз данных, потребуется Windows Server 2012 R2 Standard или Datacenter Edition, Windows Server 2012 Standard или Datacenter Edition или Windows Server 2008 R2 с пакетом обновления 1 (SP1) версии Enterprise Edition. Выпуск Windows Server 2008 R2 SP 1 Standard Edition не поддерживает компоненты, требуемые для групп обеспечения доступности баз данных.<br />
    Нельзя обновить Windows, если на сервере установлен Exchange.<br />
    Для обновления до Microsoft Unified Communications Managed API (UCMA) 4.0 сначала необходимо удалить все предыдущие версии UCMA, которые устанавливаются с помощью компонента <strong>Установка/удаление программ</strong>.


> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Подготовка Active Directory

На компьютере, который планируется использовать для подготовки Active Directory для Exchange 2013, должны быть выполнены определенные условия.

Установите следующее программное обеспечение в указанном порядке на компьютер, который будет использоваться для подготовки Active Directory.

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)

2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234) (входит в Windows Server 2012 R2)

После установки программного обеспечения, перечисленного выше, необходимо выполнить следующие действия, чтобы установить пакет средств удаленного администрирования. После установки пакета средств удаленного администрирования компьютер может использоваться для подготовки Active Directory. Дополнительные сведения о подготовке Active Directory см. в статье [Подготовка Active Directory и доменов](prepare-active-directory-and-domains-exchange-2013-help.md).

1.  Откройте среду Windows PowerShell.

2.  Установите пакет средств удаленного администрирования.
    
      - На компьютере под управлением Windows Server 2012 R2 или Windows Server 2012 выполните следующую команду.
        
            Install-WindowsFeature RSAT-ADDS
    
      - На компьютере под управлением Windows Server 2008 R2 с пакетом обновления 1 (SP1) выполните следующую команду.
        
            Add-WindowsFeature RSAT-ADDS

## Необходимые условия для установки Windows Server 2012 R2 и Windows Server 2012

Компоненты, необходимые для установки Exchange 2013 на компьютере с Windows Server 2012 R2 или Windows Server 2012, зависят от ролей Exchange, которые вы хотите установить. Изучите ниже раздел, соответствующий той роли, которую вы хотите установить.

## Роли серверов почтовых ящиков или клиентского доступа

Следуйте инструкциям в этом разделе, чтобы установить необходимые компоненты на компьютеры с Windows Server 2012 R2 или Windows Server 2012, на которых вы собираетесь выполнить одно из следующих действий:

  - Установить на компьютере только роль сервера почтовых ящиков.

  - Установите на компьютере только роль сервера клиентского доступа.

  - Установите на компьютере роли сервера почтовых ящиков и сервера клиентского доступа.

Выполните следующие действия, чтобы установить необходимые роли и компоненты Windows:

1.  Откройте среду Windows PowerShell.

2.  Запустите следующую команду для установки необходимых компонентов Windows.
    
        Install-WindowsFeature AS-HTTP-Activation, Desktop-Experience, NET-Framework-45-Features, RPC-over-HTTP-proxy, RSAT-Clustering, RSAT-Clustering-CmdInterface, RSAT-Clustering-Mgmt, RSAT-Clustering-PowerShell, Web-Mgmt-Console, WAS-Process-Model, Web-Asp-Net45, Web-Basic-Auth, Web-Client-Auth, Web-Digest-Auth, Web-Dir-Browsing, Web-Dyn-Compression, Web-Http-Errors, Web-Http-Logging, Web-Http-Redirect, Web-Http-Tracing, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Lgcy-Mgmt-Console, Web-Metabase, Web-Mgmt-Console, Web-Mgmt-Service, Web-Net-Ext45, Web-Request-Monitor, Web-Server, Web-Stat-Compression, Web-Static-Content, Web-Windows-Auth, Web-WMI, Windows-Identity-Foundation, RSAT-ADDS

После установки ролей и компонентов операционной системы установите следующее программное обеспечение в порядке перечисления:

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)
    
    > [!IMPORTANT]  
    > Для Exchange 2013 с накопительным пакетом обновления 16 (CU16) и более поздней версии <strong>требуется</strong> .NET Framework 4.6.2. Чтобы избежать появления ошибки, обновите .NET Framework на серверах до версии 4.6.2, прежде чем устанавливать Exchange 2013 с накопительным пакетом обновления 16 (CU16). Если на ваших серверах Exchange Server используется платформа .NET Framework 4.5.2, сначала установите накопительный пакет обновления 15 (CU15) для Exchange 2013, а только затем — .NET Framework 4.6.2.


2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234) (входит в Windows Server 2012 R2)

3.  [Microsoft Unified Communications Managed API 4.0, ядро среды выполнения, 64-разрядная версия](https://go.microsoft.com/fwlink/p/?linkid=258269)

## Роль пограничного транспортного сервера

Следуйте инструкциям в этом разделе, чтобы установить необходимые компоненты на компьютеры с Windows Server 2012 R2 или Windows Server 2012, на которых вы собираетесь установить роль пограничного транспортного сервера.

Выполните следующие действия, чтобы установить необходимые роли и компоненты Windows:

1.  Откройте среду Windows PowerShell.

2.  Запустите следующую команду для установки необходимых компонентов Windows.
    
        Install-WindowsFeature ADLDS

Установите версию Microsoft .NET Framework, соответствующую устанавливаемой версии Exchange 2013.

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)
    
    > [!IMPORTANT]  
    > Для Exchange 2013 с накопительным пакетом обновления 16 (CU16) и более поздней версии <strong>требуется</strong> .NET Framework 4.6.2. Чтобы избежать появления ошибки, обновите .NET Framework на серверах до версии 4.6.2, прежде чем устанавливать Exchange 2013 с накопительным пакетом обновления 16 (CU16). Если на ваших серверах Exchange Server используется платформа .NET Framework 4.5.2, сначала установите накопительный пакет обновления 15 (CU15) для Exchange 2013, а только затем — .NET Framework 4.6.2.


2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234) (входит в Windows Server 2012 R2)

## Необходимые компоненты для Windows Server 2008 R2 с пакетом обновления 1 (SP1)

Компоненты, необходимые для установки Exchange 2013 на компьютере с Windows Server 2008 R2 с пакетом управления 1 (SP1), зависят от ролей Exchange, которые вы хотите установить. Изучите ниже раздел, соответствующий той роли, которую вы хотите установить.

## Роли серверов почтовых ящиков или клиентского доступа

Следуйте инструкциям в этом разделе, чтобы установить необходимые компоненты на компьютеры с Windows Server 2008 R2 SP1, на которых вы собираетесь выполнить одно из следующих действий:

  - Установить на компьютере только роль сервера почтовых ящиков.

  - Установите на компьютере только роль сервера клиентского доступа.

  - Установите на компьютере роли сервера почтовых ящиков и сервера клиентского доступа.

Выполните следующие действия, чтобы установить необходимые роли и компоненты Windows:

1.  Откройте среду Windows PowerShell.

2.  Запустите следующую команду, чтобы загрузить модуль диспетчера сервера.
    
        Import-Module ServerManager

3.  Запустите следующую команду для установки необходимых компонентов Windows.
    
        Add-WindowsFeature Desktop-Experience, NET-Framework, NET-HTTP-Activation, RPC-over-HTTP-proxy, RSAT-Clustering, RSAT-Web-Server, WAS-Process-Model, Web-Asp-Net, Web-Basic-Auth, Web-Client-Auth, Web-Digest-Auth, Web-Dir-Browsing, Web-Dyn-Compression, Web-Http-Errors, Web-Http-Logging, Web-Http-Redirect, Web-Http-Tracing, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Lgcy-Mgmt-Console, Web-Metabase, Web-Mgmt-Console, Web-Mgmt-Service, Web-Net-Ext, Web-Request-Monitor, Web-Server, Web-Stat-Compression, Web-Static-Content, Web-Windows-Auth, Web-WMI, RSAT-ADDS

После установки ролей и компонентов операционной системы установите следующее программное обеспечение в порядке перечисления:

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)
    
    > [!IMPORTANT]  
    > Для Exchange 2013 с накопительным пакетом обновления 16 (CU16) и более поздней версии <strong>требуется</strong> .NET Framework 4.6.2. Чтобы избежать появления ошибки, обновите .NET Framework на серверах до версии 4.6.2, прежде чем устанавливать Exchange 2013 с накопительным пакетом обновления 16 (CU16). Если на ваших серверах Exchange Server используется платформа .NET Framework 4.5.2, сначала установите накопительный пакет обновления 15 (CU15) для Exchange 2013, а только затем — .NET Framework 4.6.2.


2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234)

3.  [Microsoft Unified Communications Managed API 4.0, ядро среды выполнения, 64-разрядная версия](https://go.microsoft.com/fwlink/p/?linkid=258269)

4.  [Статья базы знаний KB974405 (Windows Identity Foundation)](http://go.microsoft.com/fwlink/?linkid=3052&kbid=974405)

5.  [Статья базы знаний KB2619234 (включение куки-файла связи или GUID, используемого в RPC через HTTP, для уровня RPC в Windows 7 и Windows Server 2008 R2)](http://go.microsoft.com/fwlink/?linkid=3052&kbid=2619234)

6.  [Статья базы знаний KB2533623 (Уязвимость при загрузке библиотек может позволить злоумышленнику выполнить удаленный код)](http://go.microsoft.com/fwlink/?linkid=3052&kbid=2533623)
    
    > [!NOTE]  
    > Это исправление могло быть уже установлено, если вы настроили в Центре обновления Windows установку обновлений безопасности на своем компьютере.


## Роль пограничного транспортного сервера

Следуйте инструкциям в этом разделе, чтобы установить необходимые компоненты на компьютеры с Windows Server 2008 R2 с пакетом обновления 1 (SP1), на которых вы собираетесь установить роль пограничного транспортного сервера.

Выполните следующие действия, чтобы установить необходимые роли и компоненты Windows:

1.  Откройте среду Windows PowerShell.

2.  Запустите следующую команду, чтобы загрузить модуль диспетчера сервера.
    
        Import-Module ServerManager

3.  Запустите следующую команду для установки необходимых компонентов Windows.
    
        Add-WindowsFeature NET-Framework, ADLDS

После установки ролей и компонентов операционной системы установите следующее программное обеспечение в порядке перечисления:

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)
    
    > [!IMPORTANT]  
    > Для Exchange 2013 с накопительным пакетом обновления 16 (CU16) и более поздней версии <strong>требуется</strong> .NET Framework 4.6.2. Чтобы избежать появления ошибки, обновите .NET Framework на серверах до версии 4.6.2, прежде чем устанавливать Exchange 2013 с накопительным пакетом обновления 16 (CU16). Если на ваших серверах Exchange Server используется платформа .NET Framework 4.5.2, сначала установите накопительный пакет обновления 15 (CU15) для Exchange 2013, а только затем — .NET Framework 4.6.2.


2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234)

3.  [Microsoft Unified Communications Managed API 4.0, ядро среды выполнения, 64-разрядная версия](https://go.microsoft.com/fwlink/p/?linkid=258269)

## Необходимые условия для установки Windows 7 (только для средств администрирования)

Следуйте инструкциям в этом разделе, чтобы установить необходимые компоненты на компьютеры под управлением Windows 7 64-битной версии, присоединенные к домену, на которых будут установлены средства управления Exchange.

1.  Откройте **Панель управления** и выберите **Программы**.

2.  Щелкните элемент **Включение или отключение компонентов Windows**.

3.  Перейдите в раздел **Службы IIS** \> **Средства управления веб-сайтом** \> **Совместимость управления IIS 6**.

4.  Установите флажок **Консоль управления IIS 6** и нажмите кнопку **ОК**.

После установки ролей и компонентов операционной системы установите следующее программное обеспечение в порядке перечисления:

1.  [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)

2.  [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?linkid=390234)

3.  [Статья базы знаний KB974405 (Windows Identity Foundation)](http://go.microsoft.com/fwlink/?linkid=3052&kbid=974405)

## Необходимые условия для установки Windows 8 и Windows 8.1 (только для средств администрирования)

[.NET Framework 4.6.2](https://go.microsoft.com/fwlink/p/?linkid=808659)

