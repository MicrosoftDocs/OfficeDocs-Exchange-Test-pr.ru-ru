---
title: 'Какие изменения происходят в Active Directory при установке Exchange 2013'
TOCTitle: Какие изменения происходят в Active Directory при установке Exchange 2013?
ms:assetid: 07386078-6103-49a2-8698-2d41db9cec95
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn750898(v=EXCHG.150)
ms:contentKeyID: 62371371
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Какие изменения происходят в Active Directory при установке Exchange 2013?

 

_**Применимо к:** Exchange Server, Exchange Server 2013_

_**Последнее изменение раздела:** 2014-05-26_

При установке Exchange 2013 в лес и домены Active Directory вносятся изменения. Это необходимо Exchange для хранения информации о серверах, почтовых ящиках и других объектах Exchange, связанных с Exchange, в вашей организации. Данные изменения применяются при запуске мастера установки Exchange 2013 или выполнении команд *PrepareSchema*, *PrepareAD* и *PrepareDomains* (использование этих команд описано в разделе [Подготовка Active Directory и доменов](prepare-active-directory-and-domains-exchange-2013-help.md)) при установке Exchange 2013 из командной строки. Если вы хотите узнать, какие изменения Exchange вносит в Active Directory, эта статья для вас. Здесь описывается, что Exchange делает на каждом этапе подготовки Active Directory.

Существует три этапа подготовки Active Directory для Exchange:

  - Расширение схемы Active Directory

  - Подготовка контейнеров, объектов и других элементов Active Directory

  - Подготовка доменов Active Directory

После завершения этих операций лес Active Directory готов к использованию Exchange 2013. Дополнительные сведения об установке Exchange 2013 см. в статье [Установка Exchange 2013 с помощью мастера установки](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md).

## Расширение схемы Active Directory

При расширении схемы Active Directory добавляются и обновляются классы, атрибуты и другие элементы. Эти изменения необходимы для того, чтобы Exchange мог создавать контейнеры и объекты для хранения информации об организации Exchange. Так как Exchange вносит множество изменений в схему Active Directory, этому посвящен отдельный раздел. Список всех изменений схемы см. в разделе [Изменения схемы Active Directory в Exchange 2013](exchange-2013-active-directory-schema-changes-exchange-2013-help.md).

Этот этап выполняется автоматически при запуске мастера установки Exchange 2013 на первом сервере Exchange 2013 в лесу Active Directory. Он также выполняется при установке Exchange 2013 из командной строки с помощью команды *PrepareSchema* (или команды *PrepareAD*) на первом сервере Exchange 2013 в лесу. Дополнительные сведения о расширении схемы см. в разделе [Extend the Active Directory schema](prepare-active-directory-and-domains-exchange-2013-help.md) статьи [Подготовка Active Directory и доменов](prepare-active-directory-and-domains-exchange-2013-help.md).

После завершения расширения схемы Exchange задает версию схемы, которая хранится в атрибуте **ms-Exch-Schema-Version-Pt**. Чтобы убедиться, что схема Active Directory успешно расширена, проверьте значение этого атрибута. Если оно соответствует версии схемы, указанной для установленного выпуска Exchange 2013, схема была успешно расширена. Список выпусков Exchange и способ проверки значения атрибутов см. в разделе [How do you know this worked?](prepare-active-directory-and-domains-exchange-2013-help.md) статьи [Подготовка Active Directory и доменов](prepare-active-directory-and-domains-exchange-2013-help.md).

## Подготовка контейнеров, объектов и других элементов Active Directory

После расширения схемы следующим шагом будет добавление всех контейнеров, объектов, атрибутов и других элементов, используемых Exchange для хранения информации в Active Directory. Большинство изменений, вносимых на этом этапе, применяются ко всему лесу Active Directory. Ряд изменений вносятся в локальный домен Active Directory, где во время установки была выполнена команда *PrepareAD*.

Следующие изменения применяются к лесу Active Directory:

  - Контейнер Microsoft Exchange создается в разделе CN=Services,CN=Configuration,DC=\<*root domain*\>, если он еще не существует.

  - Следующие объекты и контейнеры создаются в разделе CN=\<*organization name*\>,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<*root domain*\>, если они не существуют.
    
      - CN=Address Lists Container
    
      - CN=AddressBook Mailbox Policies
    
      - CN=Addressing
    
      - CN=Administrative Groups
    
      - CN=Approval Applications
    
      - CN=Auth Configuration
    
      - CN=Availability Configuration
    
      - CN=Client Access
    
      - CN=Connections
    
      - CN=ELC Folders Container
    
      - CN=ELC Mailbox Policies
    
      - CN=ExchangeAssistance
    
      - CN=Federation
    
      - CN=Federation Trusts
    
      - CN=Global Settings
    
      - CN=Hybrid Configuration
    
      - CN=Mobile Mailbox Policies
    
      - CN=Mobile Mailbox Settings
    
      - CN=Monitoring Settings
    
      - CN=OWA Mailbox Policies
    
      - CN=Provisioning Policy Container
    
      - CN=Push Notification Settings
    
      - CN=RBAC
    
      - CN=Recipient Policies
    
      - CN=Remote Accounts Policies Container
    
      - CN=Retention Policies Container
    
      - CN=Retention Policy Tag Container
    
      - CN=ServiceEndpoints
    
      - CN=System Policies
    
      - CN=Team Mailbox Provisioning Policies
    
      - CN=Transport Settings
    
      - CN=UM AutoAttendant Container
    
      - CN=UM DialPlan Container
    
      - CN=UM IPGateway Container
    
      - CN=UM Mailbox Policies
    
      - CN=Workload Management Settings

  - Следующие объекты и контейнеры создаются в разделе CN=Transport Settings,CN=\<*Organization Name*\>,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<*root domain*\>, если они не существуют.
    
      - CN=Accepted Domains
    
      - CN=ControlPoint Config
    
      - CN=DNS Customization
    
      - CN=Interceptor Rules
    
      - CN=Malware Filter
    
      - CN=Message Classifications
    
      - CN=Message Hygiene
    
      - CN=Rules
    
      - CN=MicrosoftExchange329e71ec88ae4615bbc36ab6ce41109e

  - Разрешения задаются во всем разделе конфигурации в Active Directory.

  - Импортируется файл Rights.ldf. Файл добавляет разрешения, необходимые для установки Exchange и настройки Active Directory.

  - Создается подразделение групп безопасности Майкрософт Exchange в корневом домене леса. Созданному подразделению выдаются определенные разрешения.

  - В подразделении групп безопасности Microsoft Exchange создаются следующие группы ролей управления, если они не существуют:
    
      - Управление соответствием требованиям
    
      - Делегированная установка
    
      - Управление обнаружением
    
      - Служба поддержки
    
      - Управление санацией
    
      - Управление организацией
    
      - Управление общими папками
    
      - Управление получателями
    
      - Управление записями
    
      - Управление сервером
    
      - Управление единой системой обмена сообщениями
    
      - Управление организацией только с правом на просмотр

  - Новые группы ролей управления (которые отображаются как универсальный группы безопасности (USG) в Active Directory), созданные подразделении групп безопасности МайкрософтExchange, добавляются в атрибут **otherWellKnownObjects**, сохраненный в контейнере CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<*root domain*\>.

  - Создается контакт отправителя голосового сообщения единой системы обмена сообщениями в контейнере объектов системы Microsoft Microsoft Exchange корневого домена.

  - Домен, где была выполнена команда *PrepareAD*, подготавливается для Exchange 2013. Сведения, что входит в подготовку домена Active Directory для Exchange, см. в статье Подготовка доменов Active Directory.

  - Задается свойство **msExchProductId** объекта организации Exchange. Чтобы убедиться, что схема Active Directory успешно расширена, проверьте значение этого свойства. Если оно соответствует версии схемы, указанной для установленного выпуска Exchange 2013, схема была успешно расширена. Список выпусков Exchange и способ проверки значения этого свойства см. в разделе [How do you know this worked?](prepare-active-directory-and-domains-exchange-2013-help.md) статьи [Подготовка Active Directory и доменов](prepare-active-directory-and-domains-exchange-2013-help.md).

## Подготовка доменов Active Directory

Последний шаг подготовки Active Directory для Exchange состоит в том, чтобы подготовить все домены Active Directory, где будут установлены серверы Exchange или где будут размещены пользователи с поддержкой почты. Этот этап автоматически выполняется в домене, где была выполнена команда *PrepareAD*.

Следующие изменения применяются к доменам Active Directory:

  - Контейнер системных объектов Microsoft Exchange создается в разделе корневого домена Active Directory, если он еще не существует.

  - Задаются разрешения в контейнере системных объектов Microsoft Exchange для групп безопасности "Серверы Exchange", "Управление организацией" и "Прошедшие проверку".

  - Глобальная группа серверов установки доменов группа домена Exchange создается в текущем домене и размещается в контейнере системных объектов Microsoft Exchange.

  - Группа серверов установки доменов Exchange добавляется в универсальную группу безопасности серверов Exchange в корневом домене.

  - На уровне домена назначаются разрешения для универсальных групп безопасности "Серверы Exchange" и "Управление организацией".

  - Устанавливается свойство **objectVersion** в контейнере системных объектов Microsoft Exchange в разделе DC=\<*root domain*\>. Чтобы убедиться, что схема Active Directory успешно расширена, проверьте значение этого свойства. Если оно соответствует версии схемы, указанной для установленного выпуска Exchange 2013, схема была успешно расширена. Список выпусков Exchange и способ проверки значения этого свойства см. в разделе [How do you know this worked?](prepare-active-directory-and-domains-exchange-2013-help.md) статьи [Подготовка Active Directory и доменов](prepare-active-directory-and-domains-exchange-2013-help.md).

