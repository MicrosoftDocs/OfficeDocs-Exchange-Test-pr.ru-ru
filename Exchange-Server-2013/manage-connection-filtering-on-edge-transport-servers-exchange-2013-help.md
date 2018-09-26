---
title: 'Exchange 2013: фильтрация подключений для пограничных транспортных серверов'
TOCTitle: Управление фильтрацией подключений на пограничных транспортных серверах
ms:assetid: baebc865-ec3e-48ca-ac48-7aac8b34c003
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124376(v=EXCHG.150)
ms:contentKeyID: 60829972
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Управление фильтрацией подключений на пограничных транспортных серверах

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-08_

Фильтрация подключений — это функция защиты от нежелательной почты, предоставляемая агентом фильтрации подключений. Она доступна только на пограничных транспортных серверах в Microsoft Exchange 2013. Фильтрация подключений предоставляет следующие возможности:

  - список блокировок IP-адресов;

  - поставщики черных списков IP-адресов;

  - список разрешений IP-адресов;

  - поставщики белых списков IP-адресов.

Каждый из этих компонентов можно включать и отключать независимо.

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения: 15 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Функции защиты от нежелательной почты" в разделе [Разрешения для защиты от нежелательной почты и вредоносных программ](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Использование командной консоли для включения или отключения фильтрации подключений

Чтобы полностью включить или отключить фильтрацию подключений, необходимо включить либо отключить агент фильтрации подключений. Изменения вступят в силу после перезапуска службы транспорта Microsoft Exchange. При перезапуске службы транспорта Microsoft Exchange на пограничном транспортном сервере поток обработки почты на сервере временно прерывается.

Чтобы отключить фильтрацию подключений, выполните следующую команду:

```powershell
Disable-TransportAgent "Connection Filtering Agent"
```

Чтобы включить фильтрацию подключений, выполните следующую команду:

```powershell
Enable-TransportAgent "Connection Filtering Agent"
```

Чтобы изменение вступило в силу, перезапустите службу транспорта Microsoft Exchange, выполнив следующую команду.

```powershell
Restart-Service MSExchangeTransport
```

## Как проверить, что все получилось?

Чтобы подтвердить, что фильтрация подключений успешно включена или отключена, выполните следующую команду и убедитесь, что отображается заданное вами значение.

```powershell
Get-TransportAgent "Connection Filtering Agent" | Format-List Enabled
```

## Процедуры для черного списка IP-адресов

Эти процедуры применяются к черному списку IP-адресов, настроенному вручную. Они не используются для поставщиков черного списка IP-адресов.

С помощью командлетов **IPBlockListConfig** можно просматривать и настраивать способы использования черного списка IP-адресов при фильтрации подключений. С помощью командлетов **IPBlockListEntry** можно просматривать и настраивать IP-адреса в черном списке IP-адресов.

## Использование командной консоли для просмотра конфигурации черного списка IP-адресов

Для просмотра конфигурации черного списка IP-адресов выполните следующую команду:

```powershell
    Get-IPBlockListConfig | Format-List *Enabled,*Response
```

## Использование командной консоли для включения или отключения черного списка IP-адресов

Чтобы отключить список блокировок IP-адресов, выполните следующую команду:

```powershell
Set-IPBlockListConfig -Enabled $false
```

Чтобы включить список блокировок IP-адресов, выполните следующую команду:

```powershell
Set-IPBlockListConfig -Enabled $true
```

## Как проверить, что все получилось?

Чтобы подтвердить, что список блокировок IP-адресов успешно включен или отключен, выполните следующую команду и убедитесь, что отображается заданное вами значение.

```powershell
Get-IPBlockListConfig | Format-List Enabled
```

## Использование командной консоли для настройки черного списка IP-адресов

Для настройки черного списка IP-адресов используется указанный ниже синтаксис.

```powershell
    Set-IPBlockListConfig [-ExternalMailEnabled <$true | $false>] [-InternalMailEnabled <$true | $false> -MachineEntryRejectionResponse "<Custom response text>"] [-StaticEntryRejectionResponse "<Custom response text>"]
```

В этом примере список блокировок IP-адресов настраивается со следующими параметрами:

  - список блокировок IP-адресов фильтрует входящие подключения от внутренних и внешних почтовых серверов. По умолчанию фильтруются только подключения от внешних почтовых серверов (для параметра *ExternalMailEnabled* задано значение `$true`, а для параметра *InternalMailEnabled* — значение `$false`). Подключения от внешних партнеров с проверкой подлинности и без нее считаются внешними.

  - Настраиваемый текст ответа для подключений, отфильтрованных по IP-адресам, которые были автоматически добавлены в список блокировок IP-адресов агентом анализа протокола на основе репутации отправителя — "Подключение от IP-адреса {0} было отклонено из-за репутации отправителя".

  - Настраиваемый текст ответа для подключений, отфильтрованных по IP-адресам, которые были вручную добавлены в список блокировок IP-адресов — "Подключение от IP-адреса {0} было отклонено при фильтрации подключений".

<!-- end list -->

```powershell
    Set-IPBlockListConfig -InternalMailEnabled $true -MachineEntryRejectionResponse "Connection from IP address {0} was rejected by sender reputation." -StaticEntryRejectionResponse "Connection from IP address {0} was rejected by connection filtering."
```

## Как проверить, что все получилось?

Чтобы подтвердить, что список блокировок IP-адресов успешно настроен, выполните следующую команду и убедитесь, что отображаются заданные вами значения.

```powershell
    Get-IPBlockListConfig | Format-List *MailEnabled,*Response
```

## Просмотр записей черного списка IP-адресов с помощью командной консоли

Чтобы просмотреть все записи черного списка IP-адресов, выполните следующую команду:

```powershell
Get-IPBlockListEntry
```

Обратите внимание, что каждая запись черного списка определяется целочисленным значением. Этот идентификатор назначается по возрастанию при добавлении записей в черный и список разрешений IP-адресов.

Чтобы просмотреть конкретную запись черного списка IP-адресов, используйте приведенный ниже синтаксис.

```powershell
Get-IPBlockListEntry <-Identity IdentityInteger | -IPAddress IPAddress>
```

Например, чтобы просмотреть запись, содержащую IP-адрес 192.168.1.13, выполните следующую команду:

```powershell
Get-IPBlockListEntry -IPAddress 192.168.1.13
```

> [!NOTE]  
> При использовании параметра <em>IPAddress</em> полученная запись черного списка IP-адресов может содержать отдельный IP-адрес, диапазон IP-адресов или IP-адрес CIDR. Для использования параметра <em>Identity</em> необходимо указать целое значение, назначенное записи черного списка IP-адресов.


## Добавление записей черного списка IP-адресов с помощью командной консоли

Для добавления записей черного списка IP-адресов используется указанный ниже синтаксис.

```powershell
    Add-IPBlockListEntry <-IPAddress IPAddress | -IPRange IP range or CIDR IP> [-ExpirationTime <DateTime>] [-comment "<Descriptive Comment>"]
```

Следующий пример добавляет запись черного списка IP-адресов для диапазона 192.168.1.10–192.168.1.15 и настраивает срок действия этой записи (4 июля 2014 г., 15:00).

```powershell
Add-IPBlockListEntry -IPRange 192.168.1.10-192.168.1.15 -ExpirationTime "7/4/2014 15:00"
```

## Как проверить, что все получилось?

Чтобы подтвердить, что запись успешно добавлена в список блокировок IP-адресов, выполните следующую команду и убедитесь, что отображается новая запись.

```powershell
Get-IPBlockListEntry
```

## Удаление записей черного списка IP-адресов с помощью командной консоли

Для удаления записей черного списка IP-адресов используется указанный ниже синтаксис.

```powershell
Remove-IPBlockListEntry <IdentityInteger>
```

Следующий пример удаляет запись черного списка IP-адресов, значение *Identity* которой равно 3.

```powershell
Remove-IPBlockListEntry 3
```

Следующий пример удаляет запись черного списка IP-адресов, которая содержит адрес 192.168.1.12, без использования значения *Identity*. Обратите внимание, что запись черного списка может представлять отдельный IP-адрес или диапазон IP-адресов.

```powershell
Get-IPBlockListEntry -IPAddress 192.168.1.12 | Remove-IPBlockListEntry
```

## Как проверить, что все получилось?

Чтобы подтвердить, что запись успешно удалена из черного списка IP-адресов, выполните следующую команду и убедитесь, что соответствующей записи нет.

```powershell
Get-IPBlockListEntry
```

## Процедуры поставщиков черного списка IP-адресов

Эти процедуры применяются к поставщикам черного списка IP-адресов. Они не используются для работы с самим черным списком IP-адресов.

С помощью командлетов **IPBlockListProvidersConfig** можно просматривать и настраивать способы использования поставщиков черного списка IP-адресов при фильтрации подключений. С помощью командлетов **IPBlockListProvider** можно просматривать, настраивать и тестировать поставщиков черного списка IP-адресов.

## Использование командной консоли для просмотра конфигурации всех поставщиков черного списка IP-адресов

Чтобы просмотреть, как фильтрация подключений использует всех поставщиков черного списка IP-адресов, выполните следующую команду:

```powershell
    Get-IPBlockListProvidersConfig | Format-List *Enabled,Bypassed*
```

## Использование командной консоли для включения или отключения всех поставщиков черного списка IP-адресов

Чтобы отключить всех поставщиков черного списка IP-адресов, выполните следующую команду:

```powershell
Set-IPBlockListProvidersConfig -Enabled $false
```

Чтобы включить всех поставщиков черного списка IP-адресов, выполните следующую команду:

```powershell
Set-IPBlockListProvidersConfig -Enabled $true
```

## Как проверить, что все получилось?

Чтобы подтвердить, что все поставщики черного списка IP-адресов успешно включены или отключены, выполните следующую команду и убедитесь, что отображается заданное вами значение.

```powershell
Get-IPBlockListProvidersConfig | Format-List Enabled
```

## Использование командной консоли для настройки всех поставщиков черного списка IP-адресов

Чтобы настроить способ использования всех поставщиков черного списка IP-адресов при фильтрации подключений, используйте следующий синтаксис:

```powershell
    Set-IPBlockListProvidersConfig [-BypassedRecipients <recipient1,recipient2...>] [-ExternalMailEnabled <$true | $false>] [-InternalMailEnabled <$true | $false>]
```

В следующем примере все поставщики черного списка IP-адресов настраиваются со следующими параметрами:

  - Поставщики черного списка IP-адресов фильтруют входящие подключения от внутренних и внешних почтовых серверов. По умолчанию фильтруются только подключения от внешних почтовых серверов (для параметра *ExternalMailEnabled* задано значение `$true`, а для параметра *InternalMailEnabled* — значение `$false`). Подключения от внешних партнеров с проверкой подлинности и без нее считаются внешними.

  - Сообщения, отправленные внутренним получателям chris@fabrikam.com и michelle@fabrikam.com, исключаются из фильтра по поставщикам черного списка IP-адресов. Обратите внимание, что для добавления получателей в список без влияния на существующих получателей используется синтаксис `@{Add="<recipient1>","<recipient2>"...}`.

<!-- end list -->

```powershell
    Set-IPBlockListProvidersConfig -BypassedRecipients chris@fabrikam.com,michelle@fabrikam.com -InternalMailEnabled $true
```

Дополнительные сведения см. в разделе [Set-IPBlockListProvidersConfig](https://technet.microsoft.com/ru-ru/library/aa998543\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы подтвердить, что все поставщики черного списка IP-адресов успешно настроены, выполните следующую команду и убедитесь, что отображаются заданные вами значения.

```powershell
    Get-IPBlockListProvidersConfig | Format-List *MailEnabled,Bypassed*
```

## Просмотр поставщиков черного списка IP-адресов с помощью командной консоли

Для просмотра сводного списка всех поставщиков черного списка IP-адресов выполните следующую команду:

```powershell
Get-IPBlockListProvider
```

Чтобы просмотреть сведения об определенном поставщике, используйте следующий синтаксис.

```powershell
Get-IPBlockListProvider <IPBlockListProviderIdentity>
```

Следующий пример отображает сведения о поставщике с именем "Contoso IP Block List Provider".

```powershell
    Get-IPBlockListProvider "Contoso IP Block List Provider" | Format-List Name,Enabled,Priority,LookupDomain,*Match,*Response
```

## Добавление поставщика черного списка IP-адресов с помощью командной консоли

Для добавления поставщика черного списка IP-адресов используется указанный ниже синтаксис.

```powershell
    Add-IPBlockListProvider -Name "<Descriptive Name>" -LookupDomain <FQDN> [-Priority <Integer>] [-Enabled <$true | $false>] [-AnyMatch <$true | $false>] [-BitmaskMatch <IPAddress>] [-IPAddressesMatch <IPAddressStatusCode1,IPAddressStatusCode2...>] [-RejectionResponse "<Custom Text>"]
```

Этот пример создает поставщика черного списка IP-адресов с именем "Contoso IP Block List Provider" с использованием следующих параметров:

  - **Полное доменное имя для использования поставщика**   rbl.contoso.com

  - **Используемый код битовой маски от поставщика**   127.0.0.1

<!-- end list -->

```powershell
    Add-IPBlockListProvider -Name "Contoso IP Block List Provider" -LookupDomain rbl.contoso.com -BitmaskMatch 127.0.0.1
```

> [!NOTE]  
> При добавлении нового поставщика черного списка IP-адресов он по умолчанию включен (значение <em>Enabled</em> равно <code>$true</code>), а значение приоритета увеличивается на 1 (значение <em>Priority</em> для первой записи равно 1).


Дополнительные сведения см. в разделе [Add-IPBlockListProvider](https://technet.microsoft.com/ru-ru/library/bb124358\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы подтвердить, что поставщик черного списка IP-адресов успешно добавлен, выполните следующую команду и убедитесь, что отображается добавленный поставщик.

```powershell
Get-IPBlockListProvider
```

## Использование командной консоли для включения или отключения поставщика черного списка IP-адресов

Чтобы включить или отключить определенного поставщика черного списка IP-адресов, используйте приведенный ниже синтаксис.

```powershell
Set-IPBlockListProvider <IPBlockListProviderIdentity> -Enabled <$true | $false>
```

Следующий пример отключает поставщика с именем "Contoso IP Block List Provider".

```powershell
Set-IPBlockListProvider "Contoso IP Block List Provider" -Enabled $false
```

Следующий пример включает поставщика с именем "Contoso IP Block List Provider".

```powershell
Set-IPBlockListProvider "Contoso IP Block List Provider" -Enabled $true
```

## Как проверить, что все получилось?

Чтобы подтвердить, что поставщик черного списка IP-адресов успешно включен или отключен, выполните следующую команду и убедитесь, что отображается заданное вами значение.

```powershell
Get-IPBlockListProvider <IPBlockListProviderIdentity> | Format-List Enabled
```

## Настройка поставщика черного списка IP-адресов с помощью командной консоли

Параметры конфигурации, доступные в командлете **Set-IPBlockListProvider**, совпадают с параметрами командлета **New-IPBlockListProvider**.

Для настройки существующего поставщика черного списка IP-адресов используется указанный ниже синтаксис.

```powershell
    Set-IPBlockListProvider <IPBlockListProviderIdentity> -Name "<Descriptive Name>" -LookupDomain <FQDN> [-Priority <Integer>] [-AnyMatch <$true | $false>] [-BitmaskMatch <IPAddress>] [-IPAddressesMatch <IPAddressStatusCode1,IPAddressStatusCode2...>] [-RejectionResponse "<Custom Text>"]
```

Например, чтобы добавить код состояния IP-адреса 127.0.0.1 в список существующих кодов состояния для поставщика с именем "Contoso IP Block List Provider", выполните следующую команду:

```powershell
Set-IPBlockListProvider "Contoso IP Block List Provider" -IPAddressesMatch @{Add="127.0.0.1"}
```

Дополнительные сведения см. в разделе [Set-IPBlockListProvider](https://technet.microsoft.com/ru-ru/library/bb124979\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы подтвердить, что поставщик черного списка IP-адресов успешно настроен, выполните следующую команду и убедитесь, что отображаются заданные вами значения.

```powershell
Get-IPBlockListProvider <IPBlockListProviderIdentity> | Format-List
```

## Тестирование поставщика черного списка IP-адресов с помощью командной консоли

Для тестирования поставщика черного списка IP-адресов используется указанный ниже синтаксис.

```powershell
Test-IPBlockListProvider <IPBlockListProviderIdentity> -IPAddress <IPAddressToTest>
```

Следующий пример проверяет поставщика с именем "Contoso IP Block List Provider", используя IP-адрес 192.168.1.1.

```powershell
Test-IPBlockListProvider "Contoso IP Block List Provider" -IPAddress 192.168.1.1
```

## Удаление поставщика черного списка IP-адресов с помощью командной консоли

Для удаления поставщика черного списка IP-адресов используется указанный ниже синтаксис.

```powershell
Remove-IPBlockListProvider <IPBlockListProviderIdentity>
```

Следующий пример удаляет поставщика черного списка IP-адресов с именем "Contoso IP Block List Provider".

```powershell
Remove-IPBlockListProvider "Contoso IP Block list Provider"
```

## Как проверить, что все получилось?

Чтобы подтвердить, что поставщик черного списка IP-адресов успешно удален, выполните следующую команду и убедитесь, что соответствующего поставщика нет.

```powershell
Get-IPBlockListProvider
```

## Процедуры для белого списка IP-адресов

Эти процедуры применяются к белому списку IP-адресов, настроенному вручную. Они не используются для поставщиков белого списка IP-адресов.

С помощью командлетов **IPAllowListConfig** можно просматривать и настраивать способы использования белого списка IP-адресов при фильтрации подключений. С помощью командлетов **IPAllowListEntry** можно просматривать и настраивать IP-адреса в белом списке IP-адресов.

## Использование командной консоли для просмотра конфигурации белого списка IP-адресов

Для просмотра конфигурации белого списка IP-адресов выполните следующую команду:

```powershell
    Get-IPAllowListConfig | Format-List *Enabled
```

## Использование командной консоли для включения или отключения белого списка IP-адресов

Чтобы отключить список разрешений IP-адресов, выполните следующую команду:

```powershell
Set-IPAllowListConfig -Enabled $false
```

Чтобы включить список разрешений IP-адресов, выполните следующую команду:

```powershell
Set-IPAllowListConfig -Enabled $true
```

## Как проверить, что все получилось?

Чтобы подтвердить, что список разрешений IP-адресов успешно включен или отключен, выполните следующую команду и убедитесь, что отображается заданное вами значение.

```powershell
Get-IPAllowListConfig | Format-List *Enabled
```

## Использование командной консоли для настройки белого списка IP-адресов

Для настройки белого списка IP-адресов используется указанный ниже синтаксис.

```powershell
    Set-IPAllowListConfig [-ExternalMailEnabled <$true | $false>] [-InternalMailEnabled <$true | $false>
```

Этот пример настраивает список разрешений IP-адресов для фильтрации входящих подключений от внутренних и внешних почтовых серверов. По умолчанию фильтруются только подключения от внешних почтовых серверов (для параметра *ExternalMailEnabled* задано значение `$true`, а для параметра *InternalMailEnabled* — значение `$false`). Подключения от внешних партнеров с проверкой подлинности и без нее считаются внешними.

```powershell
Set-IPAllowListConfig -InternalMailEnabled $true
```

## Как проверить, что все получилось?

Чтобы подтвердить, что список разрешений IP-адресов успешно настроен, выполните следующую команду и убедитесь, что отображаются заданные вами значения.

```powershell
    Get-IPAllowListConfig | Format-List *MailEnabled
```

## Просмотр записей белого списка IP-адресов с помощью командной консоли

Чтобы просмотреть все записи белого списка IP-адресов, выполните следующую команду:

```powershell
Get-IPAllowListEntry
```

Обратите внимание, что каждая запись белого списка определяется целочисленным значением. Этот идентификатор назначается по возрастанию при добавлении записей в черный и список разрешений IP-адресов.

Чтобы просмотреть конкретную запись белого списка IP-адресов, используйте приведенный ниже синтаксис.

```powershell
Get-IPAllowListEntry <-Identity IdentityInteger | -IPAddress IPAddress>
```

Например, чтобы просмотреть запись, содержащую IP-адрес 192.168.1.13, выполните следующую команду:

```powershell
Get-IPAllowListEntry -IPAddress 192.168.1.13
```

> [!NOTE]  
> При использовании параметра <em>IPAddress</em> полученная запись белого списка IP-адресов может содержать отдельный IP-адрес, диапазон IP-адресов или IP-адрес CIDR. Для использования параметра <em>Identity</em> необходимо указать целое значение, назначенное записи белого списка IP-адресов.


## Добавление записей белого списка IP-адресов с помощью командной консоли

Для добавления записей белого списка IP-адресов используется указанный ниже синтаксис.

```powershell
    Add-IPAllowListEntry <-IPAddress IPAddress | -IPRange IP range or CIDR IP> [-ExpirationTime <DateTime>] [-Comment "<Descriptive Comment>"]
```

Этот пример добавляет запись белого списка IP-адресов для диапазона 192.168.1.10–192.168.1.15 и настраивает срок действия этой записи (4 июля 2014 г., 15:00).

```powershell
Add-IPAllowListEntry -IPRange 192.168.1.10-192.168.1.15 -ExpirationTime "7/4/2014 15:00"
```

## Как проверить, что все получилось?

Чтобы подтвердить, что запись успешно добавлена в список разрешений IP-адресов, выполните следующую команду и убедитесь, что отображается новая запись.

```powershell
Get-IPAllowListEntry
```

## Удаление записей белого списка IP-адресов с помощью командной консоли

Для удаления записей белого списка IP-адресов используется указанный ниже синтаксис.

```powershell
Remove-IPAllowListEntry <IdentityInteger>
```

Следующий пример удаляет запись белого списка IP-адресов, значение *Identity* которой равно 3.

```powershell
Remove-IPAllowListEntry 3
```

Этот пример удаляет запись белого списка IP-адресов, которая содержит адрес 192.168.1.12, без использования значения *Identity*. Обратите внимание, что запись белого списка может представлять отдельный IP-адрес или диапазон IP-адресов.

```powershell
Get-IPAllowListEntry -IPAddress 192.168.1.12 | Remove-IPAllowListEntry
```

## Как проверить, что все получилось?

Чтобы подтвердить, что запись успешно удалена из белого списка IP-адресов, выполните следующую команду и убедитесь, что соответствующей записи нет.

```powershell
Get-IPAllowListEntry
```

## Процедуры поставщиков белого списка IP-адресов

Эти процедуры применяются к поставщикам белого списка IP-адресов. Они не используются для работы с самим белым списком IP-адресов.

С помощью командлетов **IPAllowListProvidersConfig** можно просматривать и настраивать способы использования поставщиков белого списка IP-адресов при фильтрации подключений. С помощью командлетов **IPAllowListProvider** можно просматривать, настраивать и тестировать поставщиков белого списка IP-адресов.

## Использование командной консоли для просмотра конфигурации всех поставщиков белого списка IP-адресов

Чтобы просмотреть, как фильтрация подключений использует всех поставщиков белого списка IP-адресов, выполните следующую команду:

```powershell
    Get-IPAllowListProvidersConfig | Format-List *Enabled
```

## Использование командной консоли для включения или отключения всех поставщиков белого списка IP-адресов

Чтобы отключить всех поставщиков белого списка IP-адресов, выполните следующую команду:

```powershell
Set-IPAllowListProvidersConfig -Enabled $false
```

Чтобы включить всех поставщиков белого списка IP-адресов, выполните следующую команду:

```powershell
Set-IPAllowListProvidersConfig -Enabled $true
```

## Как проверить, что все получилось?

Чтобы подтвердить, что все поставщики белого списка IP-адресов успешно включены или отключены, выполните следующую команду и убедитесь, что отображается заданное вами значение.

```powershell
Get-IPAllowListProvidersConfig | Format-List Enabled
```

## Использование командной консоли для настройки всех поставщиков белого списка IP-адресов

Чтобы настроить способ использования всех поставщиков белого списка IP-адресов при фильтрации подключений, используйте следующий синтаксис:

```powershell
    Set-IPAllowListProvidersConfig [-ExternalMailEnabled <$true | $false>] [-InternalMailEnabled <$true | $false>]
```

Этот пример настраивает всех поставщиков белого списка IP-адресов для фильтрации входящих подключений от внутренних и внешних почтовых серверов. По умолчанию фильтруются только подключения от внешних почтовых серверов (для параметра *ExternalMailEnabled* задано значение `$true`, а для параметра *InternalMailEnabled* — значение `$false`). Подключения от внешних партнеров с проверкой подлинности и без нее считаются внешними.

```powershell
Set-IPAllowListProvidersConfig -InternalMailEnabled $true
```

Дополнительные сведения см. в разделе [Set-IPBlockListProvidersConfig](https://technet.microsoft.com/ru-ru/library/aa998543\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы подтвердить, что все поставщики белого списка IP-адресов успешно настроены, выполните следующую команду и убедитесь, что отображаются заданные вами значения.

```powershell
    Get-IPAllowListProvidersConfig | Format-List *MailEnabled
```

## Просмотр поставщиков белого списка IP-адресов с помощью командной консоли

Для просмотра сводного списка всех поставщиков белого списка IP-адресов выполните следующую команду:

```powershell
Get-IPAllowListProvider
```

Чтобы просмотреть сведения об определенном поставщике, используйте следующий синтаксис.

```powershell
Get-IPAllowListProvider <IPAllowListProviderIdentity>
```

Этот пример отображает сведения о поставщике с именем "Contoso IP Allow List Provider".

```powershell
    Get-IPAllowListProvider "Contoso IP Allow List Provider" | Format-List Name,Enabled,Priority,LookupDomain,*Match
```

## Добавление поставщика белого списка IP-адресов с помощью командной консоли

Для добавления поставщика белого списка IP-адресов используется указанный ниже синтаксис.

```powershell
    Add-IPAllowListProvider -Name "<Descriptive Name>" -LookupDomain <FQDN> [-Priority <Integer>] [-Enabled <$true | $false>] [-AnyMatch <$true | $false>] [-BitmaskMatch <IPAddress>] [-IPAddressesMatch <IPAddressStatusCode1,IPAddressStatusCode2...>]
```

Этот пример создает поставщика белого списка IP-адресов с именем "Contoso IP Allow List Provider" с использованием следующих параметров:

  - **Полное доменное имя для использования поставщика**   allow.contoso.com

  - **Используемый код битовой маски от поставщика**   127.0.0.1

<!-- end list -->

```powershell
    Add-IPAllowListProvider -Name "Contoso IP Allow List Provider" -LookupDomain allow.contoso.com -BitmaskMatch 127.0.0.1
```

> [!NOTE]  
> При добавлении нового поставщика белого списка IP-адресов он по умолчанию включен (значение <em>Enabled</em> равно <code>$true</code>), а значение приоритета увеличивается на 1 (значение <em>Priority</em> для первой записи равно 1).


Дополнительные сведения см. в разделе [Add-IPBlockListProvider](https://technet.microsoft.com/ru-ru/library/bb124358\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы подтвердить, что поставщик белого списка IP-адресов успешно добавлен, выполните следующую команду и убедитесь, что отображается добавленный поставщик.

```powershell
Get-IPAllowListProvider
```

## Использование командной консоли для включения или отключения поставщика белого списка IP-адресов

Чтобы включить или отключить определенного поставщика белого списка IP-адресов, используйте приведенный ниже синтаксис.

```powershell
Set-IPAllowListProvider <IPAllowListProviderIdentity> -Enabled <$true | $false>
```

Следующий пример отключает поставщика с именем "Contoso IP Allow List Provider".

```powershell
Set-IPAllowListProvider "Contoso IP Allow List Provider" -Enabled $false
```

Следующий пример включает поставщика с именем "Contoso IP Allow List Provider".

```powershell
Set-IPAllowListProvider "Contoso IP Allow List Provider" -Enabled $true
```

## Как проверить, что все получилось?

Чтобы подтвердить, что поставщик белого списка IP-адресов успешно включен или отключен, выполните следующую команду и убедитесь, что отображается заданное вами значение.

```powershell
Get-IPAllowListProvider <IPAllowListProviderIdentity> | Format-List Enabled
```

## Настройка поставщика белого списка IP-адресов с помощью командной консоли

Параметры конфигурации, доступные в командлете **Set-IPAllowListProvider**, совпадают с параметрами командлета **New-IPAllowListProvider**.

Для настройки существующего поставщика белого списка IP-адресов используется указанный ниже синтаксис.

```powershell
    Set-IPAllowListProvider <IPAllowListProviderIdentity> -Name "<Descriptive Name>" -LookupDomain <FQDN> [-Priority <Integer>] [-AnyMatch <$true | $false>] [-BitmaskMatch <IPAddress>] [-IPAddressesMatch <IPAddressStatusCode1,IPAddressStatusCode2...>]
```

Например, чтобы добавить код состояния IP-адреса 127.0.0.1 в список существующих кодов состояния для поставщика с именем "Contoso IP Allow List Provider", выполните следующую команду:

```powershell
Set-IPAllowListProvider "Contoso IP Allow List Provider" -IPAddressesMatch @{Add="127.0.0.1"}
```

Дополнительные сведения см. в разделе [Set-IPBlockListProvider](https://technet.microsoft.com/ru-ru/library/bb124979\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы подтвердить, что поставщик белого списка IP-адресов успешно настроен, выполните следующую команду и убедитесь, что отображаются заданные вами значения.

```powershell
Get-IPAllowListProvider <IPAllowListProviderIdentity> | Format-List
```

## Тестирование поставщика белого списка IP-адресов с помощью командной консоли

Для тестирования поставщика белого списка IP-адресов используется указанный ниже синтаксис.

```powershell
Test-IPAllowListProvider <IPAllowListProviderIdentity> -IPAddress <IPAddressToTest>
```

Следующий пример проверяет поставщика с именем "Contoso IP Allow List Provider", используя IP-адрес 192.168.1.1.

```powershell
Test-IPAllowListProvider "Contoso IP Allow List Provider" -IPAddress 192.168.1.1
```

## Удаление поставщика белого списка IP-адресов с помощью командной консоли

Для удаления поставщика белого списка IP-адресов используется указанный ниже синтаксис.

```powershell
Remove-IPAllowListProvider <IPAllowListProviderIdentity>
```

Следующий пример удаляет поставщика белого списка IP-адресов с именем "Contoso IP Allow List Provider".

```powershell
Remove-IPAllowListProvider "Contoso IP Allow List Provider"
```

## Как проверить, что все получилось?

Чтобы подтвердить, что поставщик белого списка IP-адресов успешно удален, выполните следующую команду и убедитесь, что соответствующего поставщика нет.

```powershell
Get-IPAllowListProvider
```

