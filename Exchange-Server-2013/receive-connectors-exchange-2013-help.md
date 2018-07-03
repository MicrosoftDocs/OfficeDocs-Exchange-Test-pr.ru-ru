﻿---
title: 'Соединители получения: Exchange 2013 Help'
TOCTitle: Соединители получения
ms:assetid: 17751a60-39fe-433f-84d2-bfc14ff4ba51
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa996395(v=EXCHG.150)
ms:contentKeyID: 50487529
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Соединители получения

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-07_

Соединители приема управляют потоком сообщений, входящих в организацию Exchange. Они настраиваются на компьютерах с Microsoft Exchange Server 2013 и службой транспорта или в службе переднего плана на сервере клиентского доступа. Их можно создать в центре администрирования Exchange (EAC) или в командной консоли Exchange.

По умолчанию соединители приема, которые необходимы для внутренней передачи почты, автоматически создаются при установке сервера клиентского доступа или сервера почтовых ящиков.

Серверы Exchange 2013, на которых запущена служба транспорта, используют соединители приема для получения сообщений из Интернета, от почтовых клиентов и других почтовых серверов. Соединитель получения управляет входящими в организацию Exchange подключениями.

Каждый соединитель приема прослушивает входящие подключения, удовлетворяющие его параметрам. Получающий соединитель прослушивает подключения, полученные через определенный локальный IP-адрес и порт или из определенного диапазона IP-адресов. Соединители приема создаются, когда необходимо управлять серверами, получающими сообщения с определенного IP-адреса или диапазона адресов, и когда необходимо настроить специальные свойства соединителя для сообщений, получаемых определенных IP-адресов, например больший размер сообщения, большее число получателей для одного сообщения. Можно также определить область соединителя приема с помощью параметра *TlsCertificateName* командлета **Set-ReceiveConnector**, позволяющего указать используемый сертификат для соединителя.

Получающие соединители группируются на одном сервере и определяют, как этот сервер будет прослушивать подключения. При создании соединителя приема на сервере почтовых ящиков с запущенной службой транспорта он сохраняется в Active Directory как дочерний объект сервера, на котором он создается.

Если для определенных сценариев требуются дополнительные соединители приема, их можно создать с помощью центра администрирования Exchange (EAC) или командной консоли Exchange. Каждый соединитель приема должен использовать уникальную комбинацию привязки к IP-адресу, назначения номера порта и диапазоны удаленных IP-адресов, с которых будут приниматься почтовые сообщения.

Дополнительные сведения о создании соединителя получения см. в разделе [Процедуры для соединителя получения](receive-connector-procedures-exchange-2013-help.md).

**Содержание**

Соединители приема по умолчанию, созданные во время установки

Соединители приема по умолчанию, созданные на сервере почтовых ящиков с запущенной службой транспорта

Соединители приема по умолчанию, созданные на транспортном сервере переднего плана

Типы соединителей приема

Группы разрешений соединителя получения

Спецификации типов соединителей приема

Разрешения соединителя получения

Параметры проверки подлинности соединителя приема

Новые функции соединителя приема в Exchange 2013

## Соединители приема по умолчанию, созданные во время установки

Некоторые соединители приема создаются по умолчанию при установке роли почтового сервера.

## Соединители приема по умолчанию, созданные на сервере почтовых ящиков с запущенной службой транспорта

При установке сервера почтовых ящиков, на котором запущена служба транспорта, создаются два соединителя приема. В обычном режиме эксплуатации не требуются дополнительные соединители получения, и в большинстве случаев не требуется изменять конфигурацию соединителей получения по умолчанию. Эти соединители описаны ниже.

  - **Имя сервера \<по умолчанию\>**. Принимает подключения с серверов почтовых ящиков, на которых запущена служба транспорта, или с пограничных серверов.

  - **Имя клиента \<прокси-сервера\>**. Принимает подключения от серверов переднего плана. Как правило, сообщения отправляются на сервер переднего плана по протоколу SMTP.

Каждому соединителю назначается значение *TransportRole*. Это значение можно использовать для определения роли, в который запущен соединитель. Это может быть полезно при запуске нескольких ролей на одном сервере. Все упомянутые ранее соединители приема имеют значение *TransportRole* — **HubTransport**.

Чтобы просмотреть соединители приема по умолчанию и значения их параметров, используйте командлет [Get-ReceiveConnector](https://technet.microsoft.com/ru-ru/library/aa998618\(v=exchg.150\)).

## Соединители приема по умолчанию, созданные на транспортном сервере переднего плана

Во время установки на транспортном сервере переднего плана или сервере клиентского доступа создаются три соединителя приема. Соединитель приема переднего плана по умолчанию настраивается для получения SMTP-подключений из всех диапазонов IP-адресов. Кроме того, имеется соединитель приема, который может функционировать в качестве прокси сервера исходящих сообщений для сообщений, отправленных на сервер переднего плана с серверов почтовых ящиков. И, наконец, существует защищенный соединитель приема, настроенный для приема сообщений, зашифрованных с помощью протокола TLS. Эти соединители описаны ниже.

  - **Имя сервера переднего плана \<по умолчанию\>**. Принимает подключения от SMTP-отправителей через порт 25. Эта общая точка входа сообщений в организацию.

  - **Имя сервера переднего плана \<для исходящих сообщений\>**. Принимает сообщения с соединителя отправки на фоновом сервере с включенным прокси-сервером переднего плана.

  - **Имя сервера \<клиента переднего плана\>**. Принимает защищенные подключения с примененным протоколом (TLS).

При обычной установке дополнительные соединители получения не требуются.

## Типы соединителей приема

Тип определяет параметры безопасности по умолчанию для каждого соединителя приема.

Настройки безопасности для получающего соединителя определяют разрешения для сеансов, подключающихся к получающему соединителю, и поддерживаемые механизмы проверки подлинности.

При использовании EAC для настройки соединителя приема на странице создания соединителя приема предлагается выбрать тип соединителя. На основании сделанного выбора происходит установка параметров, соответствующих выбранной конфигурации. Дополнительные сведения о параметрах типов соединителей приема содержатся в конкретных процедурах. Примеры этих процедур — [Создание соединителя получения электронной почты из Интернета](create-a-receive-connector-to-receive-email-from-the-internet-exchange-2013-help.md) и [Создание безопасного соединителя получения для приема электронной почты от партнера](create-a-secure-receive-connector-to-receive-email-from-a-partner-exchange-2013-help.md).

## Группы разрешений соединителя получения

Группа разрешений — это предопределенный набор разрешений для известных участников безопасности, назначаемый соединителю получения. Участники безопасности — это пользователи, компьютеры и группы безопасности. Использование групп безопасности упрощает настройку разрешений для получающих соединителей. Свойство **PermissionGroups** определяет группы или роли, которые могут отправлять сообщения соединителю получения, и разрешения, назначенные этим группам.

В группы разрешений входят *Anonymous*, *ExchangeUsers*, *ExchangeServers*, *ExchangeLegacyServers* и *Partner*.

## Спецификации типов соединителей приема

Тип определяет группы разрешений по умолчанию, присвоенные соединителю приема, и механизмы проверки подлинности по умолчанию, доступные для проверки подлинности сеанса. В следующем списке перечислены доступные типы.

1.  **Клиент**. Обычно используется для подключения к клиентам, не использующим Microsoft Office Outlook. Он может использовать проверку подлинности TLS.

2.  **Настраиваемый**. Обычно используется в сценарии перекрестных лесов или в сценарии, когда организация получает сообщения с агента передачи сообщений SMTP.

3.  **Внутренний**. Используется для взаимодействия между серверами, на которых запущена служба транспорта, или между почтовыми серверами, на которых запущена служба транспорта и сторонние агенты передачи.

4.  **Интернет**. Используется для получения почты SMTP из Интернета.

5.  **Партнер**. Используется для настройки безопасного соединения с партнером.

Каждый тип соответствует определенному сценарию подключения. Выберите тип, параметры по умолчанию которого наиболее соответствуют желаемой конфигурации. Можно менять разрешения с помощью командлетов **Add-ADPermission** и **Remove-ADPermission**. Дополнительные сведения приведены в следующих разделах:

  - [Add-ADPermission](https://technet.microsoft.com/ru-ru/library/bb124403\(v=exchg.150\))

  - [Remove-ADPermission](https://technet.microsoft.com/ru-ru/library/aa996048\(v=exchg.150\))

## Разрешения соединителя получения

Разрешения получающего соединителя назначаются участникам безопасности при указании групп разрешений для соединителя. Когда участник безопасности устанавливает сеанс с получающим соединителем, получающий соединитель определяет, будет ли сеанс установлен и как будут обработаны принятые сообщения. Можно установить разрешения соединителя приема с помощью EAC или с помощью параметра *PermissionGroups* с командлетом **Set-ReceiveConnector** в командной консоли Exchange. Чтобы изменить для соединителя получения разрешения по умолчанию, также можно использовать командлет **Add-ADPermission**.

[Разрешения соединителя получения](receive-connector-permissions-exchange-2013-help.md) содержит таблицу с более подробным описанием типов участников безопасности и разрешений.

## Параметры проверки подлинности соединителя приема

В EAC используются параметры проверки подлинности для соединителя приема, чтобы установить механизм проверки подлинности, который поддерживается транспортным сервером Exchange 2013. В командной консоли Exchange для указания поддерживаемых механизмов проверки подлинности используется параметр *AuthMechanisms*. Для получающего соединителя можно настроить более одного механизма проверки подлинности. Дополнительные сведения см. в статье [Механизмы проверки подлинности соединителя получения](receive-connector-authentication-mechanisms-exchange-2013-help.md).

## Новые функции соединителя приема в Exchange 2013

В Exchange 2013 были добавлены следующие возможности.

  - С помощью параметра *TlsCertificateName* можно указать локальный центр сертификации (ЦС), выдавший сертификат, используемый для защиты почты. Это помогает свести к минимуму риск мошеннических сертификатов.

  - Параметр *TransportRole* обозначает роль сервера, связанную с этим соединителем. Он обычно используется для указания роли сервера при размещении нескольких ролей сервера на одном компьютере.

Дополнительные сведения об этих и других параметрах для соединителей получения см. в разделе [New-ReceiveConnector](https://technet.microsoft.com/ru-ru/library/bb125139\(v=exchg.150\)).
