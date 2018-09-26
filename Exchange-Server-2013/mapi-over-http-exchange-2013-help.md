---
title: 'Протокол MAPI over HTTP: Exchange 2013 Help'
TOCTitle: Протокол MAPI over HTTP
ms:assetid: 4663b5db-5b30-4a5a-a302-be6fef7fe5da
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn635177(v=EXCHG.150)
ms:contentKeyID: 61203525
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Протокол MAPI over HTTP

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2017-05-10_

Интерфейс MAPI через HTTP — новый транспортный протокол, реализованный в МайкрософтExchange Server 2013 с пакетом обновления 1 (SP1). Протокол MAPI через HTTP повышает надежность и стабильность подключений Outlook и Exchange посредством перемещения транспортного уровня на стандартную модель HTTP. Это обеспечивает большую видимость ошибок транспорта и улучшенные возможности восстановления. Дополнительные функции включают поддержку явной функции приостановки и возобновления. Благодаря этому поддерживаемые клиенты могут менять сети или выходить из режима гибернации, сохраняя тот же контекст сервера.

При внедрении протокола MAPI через HTTP Outlook сможет использовать и другие протоколы для доступа к Exchange. Клиенты Outlook, не поддерживающие протокол MAPI через HTTP, все равно могут использовать мобильный Outlook (протокол RPC через HTTP) для доступа к Exchange через сервер клиентского доступа с включенной поддержкой интерфейса MAPI.

## Преимущества протокола MAPI через HTTP

Протокол MAPI через HTTP обеспечивает поддерживающим его клиентам следующие преимущества:

  - Обеспечение дальнейших нововведений в проверку подлинности благодаря использованию протокола на основе HTTP.

  - Более быстрое повторное подключение после разрыва связи вследствие необходимости восстановления только подключений TCP (не RPC). Примеры разрывов связи приведены ниже.
    
      - Гибернация устройства
    
      - Замена проводной сети на беспроводную или сеть мобильной связи

  - Предоставление контекста сеанса, не зависящего от подключения. Сервер поддерживает контекст сеанса в течение настраиваемого интервала времени, даже если пользователь меняет сети.

## Развертывание протокола MAPI через HTTP

Соблюдайте приведенные ниже требования при включении протокола MAPI over HTTP.

  - **Поддержка**. Убедитесь в поддержке версий конфигурации, которые планируется использовать.

  - **Предварительные условия**. Убедитесь, что среда обновлена и подготовлена к использованию протокола MAPI over HTTP.

  - **Конфигурация**. Настройте виртуальные каталоги и включите интерфейс MAPI в своей организации.

## Поддержка

Убедитесь, что ваши клиенты и серверы поддерживают протокол MAPI over HTTP, воспользовавшись приведенной ниже матрицей.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Продукт</th>
<th>Exchange 2013 с пакетом обновления 1 (SP1)</th>
<th>Exchange 2013 RTM</th>
<th>Exchange 2010 с пакетом обновления 3 (SP3)</th>
<th>Exchange 2007 с пакетом обновления 3 (SP3)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2013 с пакетом обновления 1 (SP1)</p></td>
<td><ul>
<li><p>Протокол MAPI через HTTP</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
<td><p>Мобильный Outlook</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Outlook 2013 RTM</p></td>
<td><p>Мобильный Outlook</p></td>
<td><p>Мобильный Outlook</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Outlook 2010 с пакетом обновления 2 (SP2) и обновлениями KB2956191 и KB2965295 (14 апреля 2015 г.)</p></td>
<td><ul>
<li><p>MAPI через HTTP<span></span></p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
<td><p>Мобильный Outlook</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Outlook 2010 с пакетом обновления 2 (SP2) или более ранней версии</p></td>
<td><p>Мобильный Outlook</p></td>
<td><p>Мобильный Outlook</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Outlook 2007</p></td>
<td><p>Мобильный Outlook</p></td>
<td><p>Мобильный Outlook</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Мобильный Outlook</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Необходимые условия

Выполните приведенные ниже действия, чтобы обеспечить поддержку протокола MAPI через HTTP клиентами и серверами.

1.  Обновите клиенты Outlook до Outlook 2013 с пакетом обновления 1 (SP1) или Outlook 2010 с пакетом обновления 2 (SP2) и обновлениями KB2956191 и KB2965295 (14 апреля 2015 г.).

2.  Обновите серверы клиентского доступа и почтовых ящиков до Exchange 2013 с пакетом обновления 1 (SP1). Дополнительные сведения об обновлении см. в разделе [Обновление Exchange 2013 с помощью последнего накопительного или обычного пакета обновления](upgrade-exchange-2013-to-the-latest-cumulative-update-or-service-pack-exchange-2013-help.md).
    
    > [!NOTE]  
    > Все серверы клиентского доступа необходимо обновить до Exchange 2013 с пакетом обновления 1 (SP1), прежде чем включить протокол MAPI over HTTP. В противном случае Outlook может не подключиться к почтовым ящикам.<br />
    Если вы не обновите все серверы почтовых ящиков в группе обеспечения доступности баз данных, это может привести к задержкам при отправке электронной почты и требованию клиента перезапустить Outlook в случае отработки отказа базы данных.


3.  На всех серверах Exchange 2013 необходимо установить Майкрософт.NET Framework 4.5.2. Дополнительные сведения см. в статье [Установка .NET Framework 4.5](https://go.microsoft.com/fwlink/p/?linkid=518380).

4.  На всех серверах клиентского доступа Exchange 2013 с пакетом обновления 1 добавьте переменную среды Windows **COMPLUS\_DisableRetStructPinning**. Вот как это сделать:
    
    1.  Откройте окно командной строки, запустите в нем `systempropertiesadvanced` и щелкните **Переменные среды**.
    
    2.  В разделе **Системные переменные** выберите **Новая** и введите следующие сведения.
        
          - **Имя переменной**   `COMPLUS_DisableRetStructPinning`
        
          - **Значение переменной**   1
    
    3.  По завершении нажмите кнопку **ОК**.

## Конфигурация

Выполните приведенные ниже действия, чтобы настроить протокол MAPI через HTTP для своей организации.

1.  **Конфигурация виртуального каталога**. По умолчанию Exchange 2013 с пакетом обновления 1 (SP1) создает виртуальный каталог для протокола MAPI через HTTP. Командлет **Set-MapiVirtualDirectory** используется для настройки виртуального каталога. Вам необходимо настроить внутренний либо внешний URL-адрес или оба этих адреса. Дополнительные сведения см. в разделе [Set-MapiVirtualDirectory](https://technet.microsoft.com/ru-ru/library/dn595082\(v=exchg.150\)).
    
    Например, чтобы настроить виртуальный каталог MAPI по умолчанию на локальном сервере Exchange путем задания для внутреннего URL-адреса значения https://contoso.com/mapi, а также установить метод проверки подлинности `Negotiate`, выполните приведенную ниже команду.
    
        Set-MapiVirtualDirectory -Identity "Contoso\mapi (Default Web Site)" -InternalUrl https://Contoso.com/mapi -IISAuthenticationMethods Negotiate

2.  **Конфигурация сертификата**. Цифровой сертификат, который используется в среде Exchange, должен включать те же значения *InternalURL* и *ExternalURL*, которые определены в виртуальном каталоге MAPI. Дополнительные сведения об управлении сертификатами Exchange 2013 см. в разделе [Цифровые сертификаты и протокол SSL](digital-certificates-and-ssl-exchange-2013-help.md). Убедитесь, что сертификат Exchange является доверенным на клиентской рабочей станции Outlook. Также убедитесь в отсутствии ошибок сертификата, особенно если вы получаете доступ к URL-адресам, настроенным в виртуальном каталоге MAPI.

3.  **Обновление правил сервера**. Убедитесь, что ваши подсистемы балансировки нагрузки, обратные прокси-серверы и брандмауэры разрешают доступ к виртуальному каталогу протокола MAPI через HTTP.

4.  **Включение протокола MAPI через HTTP в организации Exchange**
    
    Выполните приведенную ниже команду.
    
    ```powershell
	Set-OrganizationConfig -MapiHttpEnabled $true
	```

## Проверка подключений MAPI через HTTP

Сквозное подключение MAPI через HTTP можно проверить с помощью командлета **Test-OutlookConnectivity**. Чтобы использовать командлет **Test-OutlookConnectivity**, необходимо запустить службу диспетчера работоспособности Microsoft Exchange (MSExchangeHM).

В примере ниже проверяется подключение MAPI через HTTP от сервера Exchange с именем ContosoMail.

```powershell
Test-OutlookConnectivity -RunFromServerId ContosoMail -ProbeIdentity OutlookMapiHttpSelfTestProbe
```

При успешной проверке возвращаются результаты, похожие на приведенный ниже пример.
```powershell
    MonitorIdentity                                          StartTime              EndTime                Result      Error     Exception
    ---------------                                          ---------              -------                ------      -----     ---------
    OutlookMapiHttp.Protocol\OutlookMapiHttpSelfTestProbe    2/14/2014 7:15:00 AM   2/14/2014 7:15:10 AM   Succeeded
```
Дополнительные сведения см. в разделе [Test-OutlookConnectivity](https://technet.microsoft.com/ru-ru/library/dd638082\(v=exchg.150\)).

Журналы действий MAPI через HTTP находятся в указанных ниже папках.

  - %ExchangeInstallPath%Logging\\MAPI Address Book Service\\

  - %ExchangeInstallPath%Logging\\MAPI Client Access\\

  - %ExchangeInstallPath%Logging\\HttpProxy\\Mapi\\

## Управление протоколом MAPI через HTTP

Для управления конфигурацией протокола MAPI через HTTP используются приведенные ниже командлеты.

  - [Set-MapiVirtualDirectory](https://technet.microsoft.com/ru-ru/library/dn595082\(v=exchg.150\))

  - [Get-MapiVirtualDirectory](https://technet.microsoft.com/ru-ru/library/dn595080\(v=exchg.150\))

  - [New-MapiVirtualDirectory](https://technet.microsoft.com/ru-ru/library/dn595081\(v=exchg.150\))

  - [Remove-MapiVirtualDirectory](https://technet.microsoft.com/ru-ru/library/dn595083\(v=exchg.150\))

