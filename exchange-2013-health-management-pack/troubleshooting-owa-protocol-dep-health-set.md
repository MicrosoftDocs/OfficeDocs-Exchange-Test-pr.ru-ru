---
title: Устранение неполадок в наборе для контроля работоспособности OWA.Protocol.Dep
TOCTitle: Устранение неполадок в наборе для контроля работоспособности OWA.Protocol.Dep
ms:assetid: f39c63d5-f161-4eee-9415-05f3355e7cc7
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.scom.owa.protocol.dep(v=EXCHG.150)
ms:contentKeyID: 54652197
ms.date: 01/08/2016
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Устранение неполадок в наборе для контроля работоспособности OWA.Protocol.Dep

 

_**Применимо к:**Exchange Server 2013, Project Server 2013_

_**Последнее изменение раздела:**2015-11-10_

Набор для контроля работоспособности **OWA.Protocol.DEP** отслеживает общую работоспособность служб обмена мгновенными сообщениями в Outlook Web App, интегрированных в Lync 2013 и Exchange 2013. Дополнительные сведения о включении обмена мгновенными сообщениями в Outlook Web App см. в статье [Интеграция Microsoft Lync Server 2013 и Microsoft Outlook Web App 2013](http://go.microsoft.com/fwlink/p/?linkid=280418).

Если вы получите оповещение о неисправности набора для контроля работоспособности **OWA.Protocol.DEP**, это указывает на проблему, которая может препятствовать должному обмену мгновенными сообщениями в Outlook Web App.

## Объяснение

Служба **OWA.Protocol.DEP** отслеживается с помощью следующих зондов и мониторов.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Зонд</th>
<th>Набор для контроля работоспособности</th>
<th>Связанные мониторы</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>OWA.Protocol.DEP</p></td>
<td><p>OwaIMInitializationFailedMonitor</p></td>
</tr>
<tr class="even">
<td><p>Нет (уведомление или проверка)</p></td>
<td><p>OWA.Protocol.DEP</p></td>
<td><p>WacDiscoveryFailureEventMonitor</p></td>
</tr>
</tbody>
</table>


Дополнительные сведения о зондах и мониторах см. в статье [Работоспособность и производительность сервера](https://technet.microsoft.com/ru-ru/library/jj150551\(v=exchg.150\)).

## Действия пользователя

Служба может восстановить работу после отображения оповещения. Поэтому при получении оповещения о неисправности набора для контроля работоспособности **OWA.Protocol.DEP** сначала убедитесь, что проблема осталась. Если проблема не устранена, выполните соответствующие действия по восстановлению, указанные в приведенных ниже разделах.

## Действия по восстановлению при ошибке: "InstantMessageOCSProvider.InitializeEndpointManager. Нет параметра реестра для поставщика службы обмена мгновенными сообщениями".

Эта ошибка означает, что требуемый раздел реестра отсутствует на сервере почтовых ящиков. Этот раздел реестра должен настраиваться при установке Microsoft Unified Communications Managed API (UCMA) 4.0 на сервере. Отсутствует следующий раздел реестра:

    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\MSExchange OWA\InstantMessaging

Этот раздел должен включать строку **ImplementationDLLPath**, которая указывает на DLL-файл `Microsoft.Rtc.Internal.Ucweb`. Расположение по умолчанию: `C:\Program Files\Microsoft UCMA 4.0\Runtime\SSP\Microsoft.Rtc.Internal.Ucweb.dll`.

Чтобы устранить эту проблему, переустановите UCMA 4.0 или создайте раздел реестра вручную. UCMA 4.0 можно скачать по этому адресу: [Среда выполнения Unified Communications Managed API 4.0](http://go.microsoft.com/fwlink/p/?linkid=260990).

## Действия по восстановлению при ошибке: "InstantMessageOCSProvider.InitializeEndpointManager. Не найден поставщик службы обмена мгновенными сообщениями".

Эта ошибка указывает на то, что на сервере почтовых ящиков отсутствует DLL-файл `Microsoft.Rtc.Internal.Ucweb`. Этот файл должен устанавливаться при установке UCMA 4.0 на сервере. Расположение по умолчанию: `C:\Program Files\Microsoft UCMA 4.0\Runtime\SSP`.

Чтобы устранить эту проблему, переустановите UCMA 4.0. Дополнительные сведения см. на странице [Среда выполнения Unified Communications Managed API 4.0](http://go.microsoft.com/fwlink/p/?linkid=260990).

## Действия по восстановлению при ошибке: "Имя сервера обмена мгновенными сообщениями имеет значение Null или пустое в файле web.config".

Эта ошибка указывает, что сервер Lync 2013 не определен в файле конфигурации приложения Outlook Web App (web.config) на сервере почтовых ящиков. Этот файл `web.config` расположен по адресу `%ExchangeInstallPath%ClientAccess\Owa` и должен содержать раздел с именем **IMServerName**, в котором указано полное доменное имя (FQDN) сервера Lync 2013. Чтобы устранить эту проблему, выполните следующие действия:

1.  В окне командной строки откройте файл web.config Outlook Web App в Блокноте, выполнив такую команду:
    
        Notepad %ExchangeInstallPath%ClientAccess\Owa\web.config

2.  Найдите раздел с именем **IMServerName**. Если он найден, проверьте полное доменное имя (FQDN) сервера Lync 2013. Если он не найден, добавьте его, выполнив указанные ниже действия.
    
    1.  Найдите тег с именем **\<appSettings\>**.
    
    2.  На узле **\<appSettings\>** добавьте следующую строку:
        
            <add key="IMServerName" value="Lync Server FQDN" />
        
        Например:
        
            <add key="IMServerName" value="lync01.contoso.com" />
    
    3.  Чтобы применить изменения в Outlook Web App, выполните следующую команду:
        
            %windir%\system32\inetsrv\appcmd.exe recycle apppool /apppool.name:"MSExchangeOWAAppPool"

## Действия по восстановлению при ошибке: "Отпечаток сертификата на обмен мгновенными сообщениями имеет значение Null или пустой в файле web.config".

Эта ошибка указывает, что сертификат, используемый для интеграции Lync 2013 и Outlook Web App, не определен в файле конфигурации приложения Outlook Web App (web.config) на сервере почтовых ящиков. Этот файл `web.config` расположен по адресу `%ExchangeInstallPath%ClientAccess\Owa` и должен содержать раздел с именем **IMCertificateThumbprint**, в котором указывается отпечаток сертификата (хэш).

Значение отпечатка сертификата можно получить с помощью командлета **Get-ExchangeCertificate** или выполнив команду **Серверы** \> **Сертификаты** в Центре администрирования Exchange.

Чтобы устранить эту проблему, выполните указанные ниже действия.

1.  В окне командной строки откройте файл web.config Outlook Web App в Блокноте, выполнив такую команду:
    
        Notepad %ExchangeInstallPath%ClientAccess\Owa\web.config

2.  Найдите раздел с именем **IMCertificateThumbprint**. Если он найден, проверьте правильность значения отпечатка. Если он не найден, добавьте его, выполнив указанные ниже действия.
    
    1.  Найдите тег с именем **\<appSection\>**.
    
    2.  На узле **\<appSection\>** добавьте следующую строку:
        
            <add key="IMCertificateThumbprint" value="thumbprint"/>
        
        Например:
        
            <add key="IMCertificateThumbprint" value="35CB4C441D55506C88E59B7946B567A4F45B3B5C" />
    
    3.  Чтобы применить изменения в Outlook Web App, выполните следующую команду.
        
            %windir%\system32\inetsrv\appcmd.exe recycle apppool /apppool.name:"MSExchangeOWAAppPool"

## Действия по восстановлению при ошибке: "Сертификат на обмен мгновенными сообщениями с отпечатком \<значение\> не найден".

Это сообщение об ошибке указывает, что сертификат, используемый для интеграции Lync 2013 и Outlook Web App, не найден на сервере почтовых ящиков. Этот сертификат должен быть установлен на сервере почтовых ящиков и сервере Lync 2013, причем ему должны доверять оба сервера. Дополнительные сведения о требованиях к сертификатам см. в разделе "Включение обмена мгновенными сообщениями в Outlook Web App" статьи [Интеграция Microsoft Lync Server 2013 и Microsoft Outlook Web App 2013](http://go.microsoft.com/fwlink/p/?linkid=280418).

Значение отпечатка в сообщении об ошибке можно сопоставить с сертификатом с помощью командлета **Get-ExchangeCertificate**, а также выбрав элемент **Серверы** \> **Сертификаты** в Центре администрирования Exchange.

## Действия по восстановлению при ошибке: "Срок действия сертификата на обмен мгновенными сообщениями истек".

Эта ошибка указывает на окончание срока действия сертификата, используемого для интеграции Lync 2013 и Outlook Web App. Чтобы устранить эту ошибку, необходимо обновить сертификат.

Значение отпечатка в сообщении об ошибке можно сопоставить с сертификатом с помощью командлета **Get-ExchangeCertificate**, а также выбрав элемент **Серверы** \> **Сертификаты** в Центре администрирования Exchange.

## Действия по восстановлению при ошибке: "Сертификат на обмен мгновенными сообщениями еще не вступил в силу".

Эта ошибка указывает на наличие недопустимых дат в сертификате, используемом для интеграции Lync 2013 и Outlook Web App. Чтобы устранить эту ошибку, необходимо настроить новый сертификат, а также добавить новое значение отпечатка в раздел **IMCertificateThumbprint** по адресу `%ExchangeInstallPath%ClientAccess\Owa\web.config`. Дополнительные сведения о требованиях к сертификатам см. в разделе "Включение обмена мгновенными сообщениями в Outlook Web App" статьи [Интеграция Microsoft Lync Server 2013 и Microsoft Outlook Web App 2013](http://go.microsoft.com/fwlink/p/?linkid=280418).

## Действия по восстановлению при ошибке: "У сертификата на обмен мгновенными сообщениями нет закрытого ключа".

Эта ошибка указывает на отсутствие закрытого ключа у сертификата, используемого для интеграции Lync 2013 и Outlook Web App. Чтобы устранить эту ошибку, необходимо настроить новый сертификат с закрытым ключом, а также добавить новое значение отпечатка в раздел **IMCertificateThumbprint** по адресу `%ExchangeInstallPath%ClientAccess\Owa\web.config`. Дополнительные сведения о требованиях к сертификатам см. в разделе "Включение обмена мгновенными сообщениями в Outlook Web App" статьи [Интеграция Microsoft Lync Server 2013 и Microsoft Outlook Web App 2013](http://go.microsoft.com/fwlink/p/?linkid=280418).

