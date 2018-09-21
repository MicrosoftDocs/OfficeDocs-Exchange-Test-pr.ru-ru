---
title: 'Настройка параметров маршрутизации почты Exchange в Active Directory'
TOCTitle: Настройка параметров маршрутизации почты Exchange в Active Directory
ms:assetid: d01f8545-c201-4a96-be39-ed4c7008afcf
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ674705(v=EXCHG.150)
ms:contentKeyID: 50489254
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка параметров маршрутизации почты Exchange в Active Directory

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-08_

По умолчанию Microsoft Exchange Server 2013 ссылается на объекты IP-связи сайтов в Active Directory, чтобы определить путь маршрутизации с наименьшей стоимостью. Если вы определили, что стоимость IP-связи сайтов Active Directory и шаблоны потока трафика не оптимальны для маршрутизации почты в Exchange, можно настроить параметры в Active Directory, используемые только Exchange, чтобы оптимизировать поток почты.

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 15 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Сайт Active Directory и управление ссылками на сайт» в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Использование командной консоли для настройки специальной стоимости Exchange для IP-связи сайтов Active Directory

Определите имя IP-связи сайтов Active Directory, для которой вы хотите задать стоимость. Чем ниже значение стоимости, тем предпочтительнее маршрут. Чтобы получить дополнительные сведения о рассчитанном пути маршрутизации с наименьшей стоимостью между двумя сайтами Active Directory, можно просмотреть журналы таблицы маршрутизации и данные в разделе **ADTopologyPath ID**.

Установить специальную стоимость Exchange для связи сайтов Active Directory можно, выполнив следующую команду:

``` 
 Set-AdSiteLink <ADSiteLinkIdentity> -ExchangeCost <Integer | $null>
```

В этом примере показано, как для IP-связи сайтов, названной IPSiteLinkAB, установить значение специальной стоимости Exchange равное 10.

```powershell
Set-AdSiteLink IPSiteLinkAB -ExchangeCost 10
```

В этом примере показано, как удалить значение стоимости Exchange для IP-связи сайтов, названной IPSiteLinkAB.

```powershell
Set-AdSiteLink IPSiteLinkAB -ExchangeCost $null
```

## Как проверить, что все получилось?

Чтобы убедиться, что у вас получилось установить стоимость Exchange для связи сайтов Active Directory, выполните следующие действия.

1.  Выполните следующую команду:
    
    ```powershell
Get-AdSiteLink | Format-List Name,ExchangeCost
```

2.  Убедитесь, что стоимость Exchange настроена для связи сайтов Active Directory.

## Настройка сайта Active Directory в качестве концентратора с помощью командной консоли

Если на пути маршрутизации с наименьшей стоимостью есть концентратор, сообщение должно быть маршрутизировано через концентратор. Чтобы убедиться в том, что выбранный сайт находится на наименьшем по стоимости пути маршрутизации между двумя сайтами Active Directory, можно изучить содержимое журналов таблиц маршрутизации и просмотреть данные в разделе **ADTopologyPath ID**. Если дело не в этом, необходимо назначить специальную стоимость Exchange для IP-связи сайтов, чтобы путь маршрутизации с наименьшей стоимостью проходил через выбранные сайты.

Чтобы настроить сайт Active Directory в качестве концентратора, выполните команду:

```powershell
Set-AdSite <ADSiteIdentity> -HubSiteEnabled $true
```

В этом примере показано, как настроить сайт Active Directory (в примере Site A) в качестве концентратора.

```powershell
Set-AdSite "Site A" -HubSiteEnabled $true
```

В этом примере показано, как удалить атрибут концентратора с сайта Active Directory (в примере Site B).

```powershell
Set-AdSite "Site B" -HubSiteEnabled $false
```

## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно настроили сайт Active Directory в качестве концентратора, выполните следующие действия.

1.  Выполните следующую команду:
    
    ```powershell
Get-AdSite | Format-List Name,HubSiteEnabled
```

2.  Убедитесь, что значение параметра *HubSiteEnabled* для сайта Active Directory равно `True`.

