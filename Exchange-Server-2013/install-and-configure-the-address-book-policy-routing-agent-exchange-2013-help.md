﻿---
title: 'Установка и настройка агента маршрутизации политики адресной книги'
TOCTitle: Установка и настройка агента маршрутизации политики адресной книги
ms:assetid: 20e8a43d-4508-4388-a2c9-aa3073593cc2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ907308(v=EXCHG.150)
ms:contentKeyID: 51408012
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Установка и настройка агента маршрутизации политики адресной книги

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2014-01-09_

Агент маршрутизации политики адресной книги — это агент транспорта, который работает на сервере почтовых ящиков и контролирует то, как разрешаются получатели в организации. После установки и настройки агента маршрутизации политики адресной книги пользователи, связанные с различными глобальными списками адресов (GAL), становятся внешними получателями с той точки зрения, что они не могут просматривать карточки контактов внешних получателей.

Дополнительные сведения об управленческих задачах, связанных с политиками адресных книг, см. в разделе [Процедуры политики адресной книги](address-book-policy-procedures-exchange-2013-help.md).

Хотите узнать, какая версия Exchange Online описана в этом разделе? См. раздел [Включение маршрутизации политики адресных книг](https://technet.microsoft.com/ru-ru/library/jj891095\(v=exchg.150\)).

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения задачи: 15 минут.

  - После установки и настройки агента маршрутизации политики адресной книги может потребоваться до 30 минут, пока агент проведет оценку электронной почты в организации.

  - Выполнение этой процедуры с помощью консоли администрирования Exchange невозможно. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Как это сделать

## Действие 1. Установите агент маршрутизации политики адресной книги

Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Агенты транспорта" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

Установите агент маршрутизации политики адресной книги, выполнив следующую команду. Необходимо использовать именно эту команду с именно таким синтаксисом.
```powershell
    Install-TransportAgent -Name "ABP Routing Agent" -TransportAgentFactory "Microsoft.Exchange.Transport.Agent.AddressBookPolicyRoutingAgent.AddressBookPolicyRoutingAgentFactory" -AssemblyPath $env:ExchangeInstallPath\TransportRoles\agents\AddressBookPolicyRoutingAgent\Microsoft.Exchange.Transport.Agent.AddressBookPolicyRoutingAgent.dll
```
Появится предупреждение о том, что необходимо перезапустить транспортную службу, чтобы изменения вступили в силу. Но мы рекомендуем перед этим выполнить шаг 2, чтобы не пришлось перезапускать транспортную службу несколько раз.

Подробные сведения о синтаксисе и параметрах см. в разделе [Install-TransportAgent](https://technet.microsoft.com/ru-ru/library/aa997998\(v=exchg.150\)).

## Действие 2. Включите агент маршрутизации транспорта

Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Агенты транспорта" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

После установки агента маршрутизации политики адресной книги необходимо включить его, выполнив следующую команду.

```powershell
Enable-TransportAgent "ABP Routing Agent"
```

Подробные сведения о синтаксисе и параметрах см. в разделе [Enable-TransportAgent](https://technet.microsoft.com/ru-ru/library/bb124921\(v=exchg.150\)).

## Действие 3. Перезапустите транспортную службу и убедитесь в том, что агент маршрутизации политики адресной книги установлен и включен

Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Агенты транспорта" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

1.  Перезапустите транспортную службу, выполнив следующую команду.
    
    ```powershell
	Restart-Service MSExchangeTransport
	```

2.  После того как служба будет перезапущена, убедитесь в том, что агент маршрутизации политики адресной книги установлен и включен. Для этого запустите следующий командлет.
    
    ```powershell
	Get-TransportAgent
	```
    
    Если агент маршрутизации политики адресной книги имеется в списке, то он установлен правильно.

Подробные сведения о синтаксисе и параметрах см. в разделе [Get-TransportAgent](https://technet.microsoft.com/ru-ru/library/bb123536\(v=exchg.150\)).

## Действие 4. Включите агент маршрутизации политики адресной книги

Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Конфигурация транспорта" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

Последний шаг в этом процессе — включение агента маршрутизации политики адресной книги в организации Выполните следующую команду.

```powershell
Set-TransportConfig -AddressBookPolicyRoutingEnabled $true
```

Подробные сведения о синтаксисе и параметрах см. в разделе [Set-TransportConfig](https://technet.microsoft.com/ru-ru/library/bb124151\(v=exchg.150\)).

