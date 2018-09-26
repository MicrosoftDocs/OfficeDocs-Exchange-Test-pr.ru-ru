---
title: 'Exchange 2013: переопределение адресов для пограничных транспортных серверов'
TOCTitle: Управление переопределением адресов на пограничных транспортных серверах
ms:assetid: 323a0b55-f921-425d-b1b0-18ad0fac315c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa997185(v=EXCHG.150)
ms:contentKeyID: 61060570
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Управление переопределением адресов на пограничных транспортных серверах

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-08_

Командная консоль Exchange на пограничном транспортном сервере используется для всех задач управления, связанных с переопределением адресов и агентами переопределения адресов. Дополнительные сведения о переопределении адресов см. в разделе [Переопределение адресов на пограничных транспортных серверах](address-rewriting-on-edge-transport-servers-exchange-2013-help.md).

Вы можете создать записи переопределения адресов, которые применятся к отдельному получателю, всем получателям в определенном домене или поддомене либо всем получателям в нескольких поддоменах. Переопределение адресов может применяться только к исходящим сообщениям или входящим и исходящим сообщениям одновременно (двунаправленное переопределение адресов). Создавая записи переопределения адресов, помните о приведенном ниже.

  - Убедитесь, что в организации используются уникальные адреса электронной почты, полученные в результате.

  - В значениях адресов электронной почты поддерживаются только буквенные строки.

  - Подстановочный знак (\*) поддерживается только во внутреннем адресе (адресах, которые нужно изменить). При использовании подстановочного знака допускается следующий синтаксис: **\*.contoso.com**. Запрещено использовать значения **\*contoso.com** или **sales.\*.com**.

  - Если используется подстановочный знак, переопределение адресов необходимо настроить только для исходящих сообщений (т. е. задать для параметра *OutboundOnly* значение `$true`).

  - Когда вы настраиваете переопределение адресов только для исходящих сообщений (путем задания для параметра *OutboundOnly* значения `$true`), необходимо настроить прокси-адреса затронутых получателей. Это обеспечивает должную доставку почты, отправляемой на переопределенный адрес.

  - По умолчанию переопределение адресов двунаправленное для отдельных получателей или всех получателей в определенном домене или поддомене (по умолчанию для параметра *OutboundOnly* задается значение `$false`).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 10 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Раздел "Пограничные транспортные серверы" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - Соблюдайте осторожность при настройке переопределения адресов. Любые внесенные изменения применяются немедленно после выполнения команды. Попробуйте выполнить команду с помощью параметра *WhatIf*. Дополнительные сведения о параметре *WhatIf* см. в разделе [Параметры WhatIf, Confirm и ValidateOnly](whatif-confirm-and-validateonly-switches-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Включение и выключение переопределения адресов с помощью командной консоли

Чтобы полностью включить или отключить переопределение адресов, необходимо включить либо отключить его агенты. По умолчанию агенты переопределения адресов включены на пограничном транспортном сервере.

Чтобы отключить переопределение адресов, выполните приведенные ниже команды.
```powershell
    Disable-TransportAgent "Address Rewriting Inbound Agent"
    Disable-TransportAgent "Address Rewriting Outbound Agent"
```
Чтобы включить переопределение адресов, выполните приведенные ниже команды.
```powershell
    Enable-TransportAgent "Address Rewriting Inbound Agent"
    Enable-TransportAgent "Address Rewriting Outbound Agent"
```
## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно включили или отключили переопределение адресов, выполните приведенные ниже действия.

1.  Выполните приведенную ниже команду.
    
    ```powershell
	Get-TransportAgent
	```

2.  Убедитесь, что для свойства **Enabled** агентов переопределения адресов входящих и исходящих сообщений заданы настроенные вами значения.

## Просмотр записей переопределения адресов с помощью командной консоли

Чтобы просмотреть сводный список всех записей переопределения адресов, выполните приведенную ниже команду.

```powershell
Get-AddressRewriteEntry
```

Чтобы просмотреть сведения о записи переопределения адресов, используйте указанный ниже синтаксис.

```powershell
Get-AddressRewriteEntry <AddressRewriteEntryIdentity> | Format-List
```

В примере ниже показаны сведения о записи переопределения адресов "Rewrite Contoso.com to Northwindtraders.com".

```powershell
Get-AddressRewriteEntry "Rewrite Contoso.com to Northwindtraders.com" | Format-List
```

## Создание записей переопределения адресов с помощью командной консоли

## Переопределение адресов электронной почты отдельных получателей

Чтобы переопределить адрес электронной почты для отдельного получателя, используйте указанный ниже синтаксис.
```powershell
    New-AddressRewriteEntry -Name "<Descriptive Name>" -InternalAddress <internal email address> -ExternalAddress <external email address> [-OutboundOnly <$true | $false>]
```
В примере ниже переопределяется адрес электронной почты всех входящих и исходящих сообщений организации Exchange для получателя joe@contoso.com. Исходящие сообщения переопределяются таким образом, что они приходят с адреса support@northwindtraders.com. Входящие сообщения, отправляемые по адресу support@northwindtraders.com, переопределяются на адрес joe@contoso.com для доставки получателю (для параметра *OutboundOnly* задается значение по умолчанию `$false`).
```powershell
    New-AddressRewriteEntry -Name "joe@contoso.com to support@northwindtraders.com" -InternalAddress joe@contoso.com -ExternalAddress support@northwindtraders.com
```
## Переопределение адресов электронной почты для получателей в отдельном домене или поддомене

Чтобы переопределить адреса электронной почты для получателей в отдельном домене или поддомене, используйте указанный ниже синтаксис.
```powershell
    New-AddressRewriteEntry -Name "<Descriptive Name>" -InternalAddress <domain or subdomain> -ExternalAddress <domain> [-OutboundOnly <$true | $false>]
```
В примере ниже переопределяются адреса электронной почты всех входящих и исходящих сообщений организации Exchange для получателей в домене contoso.com. Исходящие сообщения переопределяются таким образом, что они приходят с домена fabrikam.com. Входящие сообщения, отправляемые по адресам электронной почты fabrikam.com, переопределяются на домен contoso.com для доставки получателям (для параметра *OutboundOnly* задается значение по умолчанию `$false`).
```powershell
    New-AddressRewriteEntry -Name "Contoso to Fabrikam" -InternalAddress contoso.com -ExternalAddress fabrikam.com
```
В примере ниже переопределяются адреса электронной почты всех исходящих сообщений организации Exchange, которые отправляют получатели в поддомене sales.contoso.com. Исходящие сообщения переопределяются таким образом, что они приходят с домена contoso.com. Входящие сообщения, отправляемые по адресам электронной почты contoso.com, не переопределяются.
```powershell
    New-AddressRewriteEntry -Name "sales.contoso.com to contoso.com" -InternalAddress sales.contoso.com -ExternalAddress contoso.com -OutboundOnly $true
```
## Переопределение адресов электронной почты для получателей в нескольких поддоменах

Чтобы переопределить адреса электронной почты для получателей в домене или всех поддоменах, используйте указанный ниже синтаксис.
```powershell
    New-AddressRewriteEntry -Name "<Descriptive Name>" -InternalAddress *.<domain> -ExternalAddress <domain> -OutboundOnly $true [-ExceptionList <domain1,domain2...>]
```
В примере ниже переопределяются адреса электронной почты всех исходящих сообщений организации Exchange, которые отправляют получатели в домене contoso.com и всех поддоменах. Исходящие сообщения переопределяются таким образом, что они приходят с домена contoso.com. Входящие сообщения, отправляемые получателям в домене contoso.com, невозможно переопределить, поскольку в параметре *InternalAddress* используется подстановочный знак.
```powershell
    New-AddressRewriteEntry -Name "Rewrite all contoso.com subdomains" -InternalAddress *.contoso.com -ExternalAddress contoso.com -OutboundOnly $true
```
Единственное отличие приведенного ниже примера от предыдущего примера состоит в том, что сообщения, отправляемые получателями в поддоменах legal.contoso.com и corp.contoso.com, не переопределяются.
```powershell
    New-AddressRewriteEntry -Name "Rewrite all contoso.com subdomains except legal.contoso.com and corp.contoso.com" -InternalAddress *.contoso.com -ExternalAddress contoso.com -OutboundOnly $true -ExceptionList legal.contoso.com,corp.contoso.com
```
## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно создали записи переопределения адресов, выполните приведенные ниже действия.

1.  Выполните команду `Get-AddressRewriteEntry <AddressRewriteEntryIdentity> | Format-List` и убедитесь, что отображаются настроенные вами параметры.

2.  Отправьте проверочное сообщение на внешний почтовый ящик из почтового ящика, на который влияет запись переопределения адресов. Убедитесь, что проверочное сообщение приходит с переопределенного адреса электронной почты.

3.  Ответьте на проверочное сообщение из внешнего почтового ящика. Убедитесь, что ответ доставлен в исходный почтовый ящик.

## Изменение записей переопределения адресов с помощью командной консоли

Параметры конфигурации, доступные при изменении существующей записи переопределения адресов, не отличаются от параметров конфигурации, которые применяются при создании новой записи переопределения адресов.

## Изменение записей переопределения адресов для отдельных получателей

Чтобы изменить запись переопределения адреса электронной почты для отдельного получателя, используйте указанный ниже синтаксис.
```powershell
    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -Name "<Descriptive Name>" -InternalAddress <internal email address> -ExternalAddress <external email address> -OutboundOnly <$true | $false>
```
В примере ниже изменяются следующие свойства записи переопределения адреса для отдельного получателя "joe@contoso.com to support@northwindtraders.com".

  - Внешний адрес изменяется на support@northwindtraders.net.

  - Имя записи переопределения адресов изменяется на "joe@contoso.com to support@northwindtraders.net".

  - Значение параметра *OutboundOnly* изменяется на `$true`. Обратите внимание: для этого изменения требуется настроить support@northwindtraders.net в качестве прокси-адреса в почтовом ящике Джо.

<!-- end list -->
```powershell
    Set-AddressRewriteEntry "joe@contoso.com to support@nortwindtraders.com" -Name "joe@contoso.com to support@northwindtraders.net" -ExternalAddress support@northwindtraders.net -OutboundOnly $true
```
## Изменение записей переопределения адресов для получателей в отдельных доменах или поддоменах

Чтобы изменить запись переопределения адресов электронной почты для получателей в отдельном домене или поддомене, используйте указанный ниже синтаксис.
```powershell
    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -Name "<Descriptive Name>" -InternalAddress <domain or subdomain> -ExternalAddress <domain> -OutboundOnly <$true | $false>
```
В примере ниже изменяется значение внутреннего адреса записи переопределения адресов для отдельного домена "Northwind Traders to Contoso".

```powershell
Set-AddressRewriteEntry "Northwindtraders to Contoso" -InternalAddress northwindtraders.net
```

## Изменение записей переопределения адресов для получателей в нескольких поддоменах

Чтобы изменить запись переопределения адресов электронной почты для получателей в домене и всех поддоменах, используйте указанный ниже синтаксис.
```powershell
    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -Name "<Descriptive Name>" -InternalAddress *.<domain> -ExternalAddress <domain> -ExceptionList <list of domains>
```
Чтобы заменить значения в существующем списке исключений для записи переопределения адресов в нескольких поддоменах, используйте указанный ниже синтаксис.
```powershell
    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -ExceptionList <domain1,domain2,...>
```
В примере ниже заменяется существующий список исключений для записи переопределения адресов в нескольких поддоменах "Contoso to Northwind Traders"; при этом заменяются значения marketing.contoso.com и legal.contoso.com.
```powershell
    Set-AddressRewriteEntry "Contoso to Northwind Traders" -ExceptionList sales.contoso.com,legal.contoso.com
```
Чтобы выборочно добавить или удалить значения списка исключений из записи переопределения адресов в нескольких поддоменах, не изменяя значения в существующем списке исключений, используйте указанный ниже синтаксис.
```powershell
    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -ExceptionList @{Add="<domain1>","<domain2>"...; Remove="<domain1>","<domain2>"...}
```
В примере ниже в список исключений записи переопределения адресов в нескольких поддоменах "Contoso to Northwind Traders" вносятся следующие изменения: добавляется значение finance.contoso.com и удаляется значение marketing.contoso.com.
```powershell
    Set-AddressRewriteEntry "Contoso to Northwind Traders" -ExceptionList @{Add="finanace.contoso.com"; Remove="marketing.contoso.com"}
```
## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно изменили запись переопределения адресов, выполните приведенные ниже действия.

1.  Выполните команду `Get-AddressRewriteEntry <AddressRewriteEntryIdentity> | Format-List` и убедитесь, что отображаются настроенные вами параметры.

2.  Отправьте проверочное сообщение на внешний почтовый ящик из почтового ящика, на который влияет запись переопределения адресов. Убедитесь, что проверочное сообщение приходит с переопределенного адреса электронной почты.

3.  Ответьте на проверочное сообщение из внешнего почтового ящика. Убедитесь, что ответ доставлен в исходный почтовый ящик.

## Удаление записей переопределения адресов с помощью командной консоли

Чтобы удалить отдельную запись переопределения адресов, используйте указанный ниже синтаксис.

```powershell
Remove-AddressRewriteEntry <AddressRewriteEntryIdentity>
```

В примере ниже удаляется запись переопределения адресов "Contoso.com to Northwindtraders.com".

```powershell
Remove-AddressRewriteEntry "Contoso.com to Northwindtraders.com"
```

Чтобы удалить несколько записей переопределения адресов, используйте указанный ниже синтаксис.
```powershell
    Get-AddressRewriteEntry [<search criteria>] | Remove-AddressRewriteEntry [-WhatIf]
```
В примере ниже удаляются все записи переопределения адресов.

```powershell
Get-AddressRewriteEntry | Remove-AddressRewriteEntry
```

В примере ниже имитируется удаление записей переопределения адресов, в именах которых содержится текст "to contoso.com". Переключатель *WhatIf* позволяет выполнить предварительный просмотр результата без внесения изменений.
```powershell
    Get-AddressRewriteEntry "*to contoso.com" | Remove-AddressRewriteEntry -WhatIf
```
Если вы удовлетворены результатом, снова выполните команду без переключателя *WhatIf*, чтобы удалить записи переопределения адресов.
```powershell
    Get-AddressRewriteEntry "*to contoso.com" | Remove-AddressRewriteEntry
```
## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно удалили запись переопределения адресов, выполните приведенные ниже действия.

1.  Выполните команду `Get-AddressRewriteEntry` и убедитесь, что в списке отсутствуют удаленные записи переопределения адресов.

2.  Отправьте проверочное сообщение на внешний почтовый ящик из почтового ящика, на который влияет запись переопределения адресов. Убедитесь, что удаленная запись переопределения адресов не затрагивает проверочное сообщение.

3.  Ответьте на проверочное сообщение из внешнего почтового ящика. Убедитесь, что ответ доставлен в исходный почтовый ящик, а удаленная запись переопределения адресов не затрагивает сообщение.

