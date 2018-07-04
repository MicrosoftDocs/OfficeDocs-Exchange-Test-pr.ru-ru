---
title: 'Установка Exchange 2013 в автоматическом режиме: Exchange 2013 Help'
TOCTitle: Установка Exchange 2013 в автоматическом режиме
ms:assetid: 386465e9-41da-4e26-9816-b3b69be1f8bf
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa997281(v=EXCHG.150)
ms:contentKeyID: 50487835
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Установка Exchange 2013 в автоматическом режиме

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2014-06-19_

Автоматическая установка Microsoft Exchange Server 2013 выполняется из командной строки. Дополнительные сведения о планировании и развертывании Exchange 2013 см. в разделе [Планирование и развертывание](planning-and-deployment-for-exchange-2013-installation-instructions.md).

Рекомендуется установить роль пограничного транспортного сервера в сети периметра за пределами внутреннего леса Active Directory организации. Хотя роль пограничного транспортного сервера можно установить на компьютер, подключенный к домену, это позволит лишь включить в домене управление возможностями и параметрами Windows. Сама роль пограничного транспортного сервера не использует Active Directory. Вместо этого она использует функцию служб Active Directory облегченного доступа к каталогам (AD LDS) Windows для хранения информации о конфигурации и получателях. Дополнительные сведения о роли пограничного транспортного сервера см. в разделе [Пограничные транспортные серверы](edge-transport-servers-exchange-2013-help.md).

> [!TIP]  
> Вы слышали о помощнике по развертыванию Exchange Server? Это бесплатный инструмент в Интернете, который поможет вам быстро развернуть Exchange 2013 в вашей организации, задав вам несколько вопросов и создав контрольный список пользовательского развертывания именно для вас. Дополнительные сведения см. в разделе <a href="exchange-server-deployment-assistant-exchange-2013-help.md">Помощник по развертыванию Exchange Server</a>.


> [!NOTE]  
> После установки на компьютере под управлением Exchange 2013 каких-либо ролей сервера добавить другие роли сервера на тот же компьютер с помощью мастера установки Exchange 2013 невозможно. Если на компьютер нужно добавить дополнительные роли сервера, необходимо использовать компонент панели управления &quot;Установка и удаление программ&quot; или запустить программу Setup.exe в командной строке.<br />
Роль пограничного транспортного сервера нельзя установить на компьютере с установленными ролями сервера почтовых ящиков или клиентского доступа.


Сведения о задачах, которые необходимо выполнить после установки, см. в разделе [Задачи после установки Exchange 2013](exchange-2013-post-installation-tasks-exchange-2013-help.md).

## Что нужно знать перед началом работы

Приведенные ниже сведения относятся ко всем ролям сервера Exchange 2013.

  - Прочтите заметки о выпуске перед установкой Exchange 2013. Подробнее см. в разделе [Заметки о выпуске Exchange 2013](release-notes-for-exchange-2013-exchange-2013-help.md).

  - Компьютер, на который установлен Exchange 2013, должен иметь поддерживаемую операционную систему (например, Windows Server 2008 R2 с пакетом обновления 1 (SP1), Windows Server 2012 R2 или Windows Server 2012) и достаточно места на диске, а также соответствовать другим требованиям. Сведения о системных требованиях см. в разделе [Требования к системе для установки Exchange 2013](exchange-2013-system-requirements-exchange-2013-help.md).

  - Чтобы запустить установку Exchange 2013, необходимо установить Microsoft .NET Framework 4.5, Windows Management Framework и другое необходимое программное обеспечение. Общие сведения о предварительных условиях для всех ролей сервера см. в разделе [Предварительные требования для Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!CAUTION]  
> После установки Exchange на сервере будет невозможно изменить его имя. Переименование сервера после установки роли сервера Exchange не поддерживается.


Приведенные ниже сведения относятся к ролям сервера почтовых ящиков и сервера клиентского доступа Exchange 2013.

  - Предполагаемое время для завершения: 60 минут.

  - Для каждой организации требуется как минимум один сервер клиентского доступа и один сервер почтовых ящиков в лесу Active Directory. Кроме того, каждый из узлов Active Directory, который содержит сервер почтовых ящиков, должен также содержать как минимум один сервер клиентского доступа. При разделении серверных ролей рекомендуем сначала установить роль сервера почтовых ящиков.

  - Компьютер, на который устанавливается Exchange 2013, должен быть членом домена Active Directory.

  - Если схема Active Directory не была предварительно подготовлена, убедитесь, что для используемой учетной записи делегировано членство в группе администраторов схемы. Если устанавливаемый сервер Exchange 2013 является первым в организации, то используемая учетная запись должна входить в группу администраторов предприятия. Если в организации устанавливается не первый сервер Exchange 2013 и схема уже подготовлена, используемая учетная запись должна входить в группу ролей управления организацией Exchange 2013.
    
    Администраторы, состоящие в группе ролей делегированной установки, могут развертывать серверы Exchange 2013, подготовленные участником группы ролей управления организацией.

Приведенные ниже сведения относятся к роли пограничного транспортного сервера Exchange 2013.

  - Предполагаемое время для завершения: 40 минут.

  - Роль пограничного транспортного сервера доступна при использовании Exchange 2013 с пакетом обновления 1 (SP1) или более поздних версий.

  - На компьютере необходимо настроить основной DNS-суффикс. Например, если полное доменное имя вашего компьютера — edge.contoso.com, DNS-суффикс для этого компьютера — contoso.com. Дополнительные сведения см. в разделе [Основной суффикс DNS отсутствует](primary-dns-suffix-is-missing-exchange-2013-help.md).

  - Транспортные серверы-концентраторы Exchange 2007 и Exchange 2010 необходимо обновить перед созданием подписки EdgeSync между ними и пограничным транспортным сервером Exchange 2013. Если не установить это обновление, подписка EdgeSync будет работать неправильно. Дополнительные сведения см. в подразделе "Поддерживаемые сценарии сосуществования" раздела [Требования к системе для установки Exchange 2013](exchange-2013-system-requirements-exchange-2013-help.md).

  - Убедитесь, что используемая вами учетная запись входит в локальную группу администраторов на компьютере, на который устанавливается роль пограничного транспортного сервера.

## Установка сервера Exchange 2013 в автоматическом режиме с помощью Setup.exe

> [!NOTE]  
> Сведения о скачивании последней версии Exchange 2013 см. в разделе <a href="updates-for-exchange-2013-exchange-2013-help.md">Обновления для Exchange 2013</a>.


1.  Выполните вход на компьютере, на который необходимо установить Exchange 2013.

2.  Перейдите в расположение установочных файлов Exchange 2013 в сети.

3.  В командной строке выполните команду, применимую для вашей организации.
    
    > [!IMPORTANT]  
    > Если управление доступом на уровне пользователей (UAC) включено, необходимо выполнить <code>Setup.exe</code> из командной строки с повышенными полномочиями.
    
        Setup.exe [/Mode:<setup mode>] [/IAcceptExchangeServerLicenseTerms]
        [/Roles:<server roles to install>] [/InstallWindowsComponents] 
        [/OrganizationName:<name for the new Exchange organization>] 
        [/TargetDir:<target directory>] [/SourceDir:<source directory>]
        [/UpdatesDir:<directory from which to install updates>] 
        [/DomainController:<FQDN of domain controller>] [/DisableAMFiltering]
        [/AnswerFile:<filename>] [/DoNotStartTransport] 
        [/EnableErrorReporting] [/CustomerFeedbackEnabled:<True | False>] 
        [/AddUmLanguagePack:<UM language pack name>] 
        [/RemoveUmLanguagePack:<UM language pack name>] 
        [/NewProvisionedServer:<server>] [/RemoveProvisionedServer:<server>] 
        [/MdbName:<mailbox database name>] [/DbFilePath:<Edb file path>] 
        [/LogFolderPath:<log folder path>] [/ActiveDirectorySplitPermissions:<True | False>]
        [/TenantOrganizationConfig:<path>]

4.  Программа установки копирует файлы установки локально на компьютер, на который устанавливается сервер Exchange 2013.

5.  Программа установки проверяет выполнение предварительных условий, в том числе относящихся к устанавливаемым ролям сервера. Если выполнены не все предварительные условия, установка будет прекращена с возвратом ошибки, в которой объясняется причина сбоя. Если выполнены все условия, установка Exchange 2013 будет выполнена.

6.  Перезагрузите компьютер после завершения Exchange 2013.

7.  Завершите развертывание, выполнив задачи из раздела [Задачи после установки Exchange 2013](exchange-2013-post-installation-tasks-exchange-2013-help.md).

## Примеры

Ниже приведены примеры использования команды Setup.exe:

  - **Setup.exe /mode:Install /role:ClientAccess,Mailbox /OrganizationName:MyOrg /IAcceptExchangeServerLicenseTerms**
    
    Эта команда создает организацию Exchange 2013 в Active Directory с именем MyOrg, а также устанавливает роль сервера клиентского доступа, роль сервера почтовых ящиков и средства управления, а также принимает условия лицензирования Exchange 2013.

  - **Setup.exe /mode:Install /role:ClientAccess,Mailbox /TargetDir:"C:\\Exchange Server" /IAcceptExchangeServerLicenseTerms**
    
    Эта команда устанавливает роль сервера клиентского доступа, сервера почтовых ящиков и средства управления в каталог "C:\\Exchange Server". Эта команда предполагает, что организация Exchange 2013 уже подготовлена.

  - **Setup.exe /mode:Install /r:CA,MB /IAcceptExchangeServerLicenseTerms**
    
    Эта команда устанавливает роль сервера клиентского доступа, сервера почтовых ящиков и средства управления в каталог установки по умолчанию.

  - **Setup.exe /mode:Install /r:EdgeTransport /IAcceptExchangeServerLicenseTerms**
    
    Эта команда устанавливает роль пограничного транспортного сервера и средства управления в расположение установки по умолчанию.

  - **Setup.exe /mode:Install /r:ET /IAcceptExchangeServerLicenseTerms**
    
    Эта команда устанавливает роль пограничного транспортного сервера и средства управления в расположение установки по умолчанию.

  - **Setup.exe /mode:Uninstall /IAcceptExchangeServerLicenseTerms**
    
    Эта команда полностью удаляет с компьютера сервер Exchange 2013 и удаляет конфигурацию этого сервера Exchange из Active Directory.

  - **Setup.exe /PrepareAD /on:"My Org" /IAcceptExchangeServerLicenseTerms**
    
    Эта команда создает организацию Exchange с именем My Org и подготавливает Active Directory к установке сервера Exchange 2013.

  - **C:\\ExchangeServer\\bin\\Setup.exe /m:Install /r:ClientAccess /SourceDir:d:\\amd64 /IAcceptExchangeServerLicenseTerms**
    
    Эта команда добавляет на существующий сервер Exchange 2013 роль сервера клиентского доступа, используя в качестве исходного каталога D:\\amd64.

  - **Setup.exe /role:ClientAccess,Mailbox /UpdatesDir:"C:\\ExchangeServer\\New Patches" /IAcceptExchangeServerLicenseTerms**
    
    Эта команда обновляет файл ExchangeServer.msi с помощью исправлений, находящихся в указанном каталоге, а затем устанавливает роль сервера клиентского доступа, сервера почтовых ящиков и средства управления. Если в этом каталоге есть языковой пакет, он также устанавливается.

  - **Setup.exe /mode:Install /role:ClientAccess,Mailbox /DomainController:DC01 /IAcceptExchangeServerLicenseTerms**
    
    Эта команда использует контроллер домена DC01 для запроса и внесения изменений в Active Directory при установке роли сервера клиентского доступа, сервера почтовых ящиков и средств управления.

  - **Setup.exe /mode:Install /role:ClientAccess /AnswerFile:c:\\ExchangeConfig.txt /IAcceptExchangeServerLicenseTerms**
    
    Эта команда устанавливает роль сервера клиентского доступа, используя параметры, указанные в файле ExchangeConfig.txt.

  - **Setup.exe /rprs:Exchange03 /IAcceptExchangeServerLicenseTerms**
    
    Эта команда удаляет объект Exchange03 из Active Directory.

  - **Setup.exe /AddUmLanguagePack:ko-KR /IAcceptExchangeServerLicenseTerms**
    
    Эта команда устанавливает языковой пакет единой системы обмена сообщениями для корейского языка из каталога %ExchangeSourceDir%\\ServerRoles\\UnifiedMessaging.

## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно установили Exchange 2013, выполните действия из раздела [Проверка установки Exchange 2013](verify-an-exchange-2013-installation-exchange-2013-help.md).

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

