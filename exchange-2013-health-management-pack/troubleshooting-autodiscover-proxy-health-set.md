﻿---
title: Устранение неполадок, связанных с наборами средств для проверки работоспособности Autodiscover.Proxy
TOCTitle: Устранение неполадок, связанных с наборами средств для проверки работоспособности Autodiscover.Proxy
ms:assetid: b6a817cf-0b85-4620-adb7-cc3616c11268
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.scom.autodiscover.proxy(v=EXCHG.150)
ms:contentKeyID: 53275668
ms.date: 11/14/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Устранение неполадок, связанных с наборами средств для проверки работоспособности Autodiscover.Proxy

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Комплект средств для проверки работоспособности службы Autodiscover.Proxy отслеживает доступность прокси-инфраструктуры Autodiscover на сервере клиентского доступа (CAS). Комплекс средств для проверки работоспособности Autodiscover.Proxy тесно связан со следующими комплексами контроля работоспособности:

[Troubleshooting ClientAccess.Proxy Health Set](troubleshooting-clientaccess-proxy-health-set.md)

Если вам приходит предупреждение, в котором указано, что служба Autodiscover.Proxy неработоспособна, это указывает на проблему, которая может препятствовать обнаружению почтовых ящиков пользователей с помощью процесса автоопределения Exchange.

## Пояснение

Слежение за службой автообнаружения выполняется с помощью следующих зондов и средств мониторинга.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Зонд</th>
<th>Настройки работоспособности</th>
<th>Зависимости</th>
<th>Связанные мониторы</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AutoDiscoverProxyTestProbe</p></td>
<td><p>Autodiscover.Proxy</p></td>
<td><p>Active Directory</p></td>
<td><p>AutodiscoverProxyTestMonitor</p></td>
</tr>
</tbody>
</table>


Дополнительные сведения о зондах и мониторах см. в разделе [Работоспособность и производительность сервера](https://technet.microsoft.com/ru-ru/library/jj150551\(v=exchg.150\)).

## Распространенные проблемы

Этот зонд может не работать по любой из следующих распространенных причин:

  - Пул приложений, размещенный на отслеживаемом сервере клиентского доступа, работает неправильно.

  - Введены неправильные данные учетной записи наблюдения.

  - Контроллеры доменов не отвечают.

## Действия пользователя

Служба может восстановить работу после отображения оповещения. Поэтому если вы получите оповещение о неработоспособном состоянии настроек работоспособности, сначала убедитесь в наличии данной проблемы. Если проблема не устранена, выполните соответствующие действия по восстановлению, указанные в приведенных ниже разделах.

## Проверка наличия проблемы

1.  Определите имена настроек работоспособности и сервера, указанные в оповещении.

2.  В сообщении приводятся подробные сведения о точной причине возникновения оповещения. В большинстве случаев в сообщении приводится достаточно сведений по устранению неполадок для определения основной причины проблемы. Если в сообщении приводятся непонятные сведения:
    
    1.  Откройте Командная консоль Exchange, а затем выполните следующую команду, чтобы извлечь подробные сведения о настройках работоспособности, с которыми связано оповещение.
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Например, чтобы извлечь подробные сведения о настройках работоспособности Autodiscover.Protocol относительно сервера server1.contoso.com, выполните следующую команду.
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "Autodiscover.Protocol"}
    
    2.  Просмотрите выходные данные команды, чтобы определить монитор, сообщивший об ошибке. Параметр **AlertValue** монитора, вызвавшего оповещение, будет иметь значение `Unhealthy`.
    
    3.  Еще раз запустите зонд для средства мониторинга, которое находится в неисправном состоянии. Обратитесь к таблице в разделе Пояснение, чтобы найти связанный зонд. Для этого выполните следующую команду.
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Например, предположим, что не работает монитор **AutodiscoverSelfTestMonitor**. С этим монитором связан зонд **AutodiscoverSelfTestProbe**. Чтобы запустить этот зонд на сервере server1.contoso.com, выполните следующую команду.
        
            Invoke-MonitoringProbe Autodiscover.Protocol\AutodiscoverSelfTestProbe -Server server1.contoso.com | Format-List
    
    4.  В выходных данных команды просмотрите значение параметра **Результат** зонда. Если этот параметр имеет значение **Succeeded**, ошибка была временной и в настоящее время устранена. В противном случае обратитесь к действиям по восстановлению, приведенным в следующих разделах.

## Действия по восстановлению AutodiscoverProxyTestMonitor

Если вы получите оповещение, связанное с настройками работоспособности, сообщение электронной почты содержит приведенные ниже сведения.

  - Имя сервера клиентского доступа, отправившего оповещение.

  - Полная трассировка исключения, связанного с последней ошибкой, включая диагностические данные и конкретные сведения о заголовке HTTP.
    
    Сведения в полной трассировке исключения можно использовать для устранения проблемы.

  - Время и дата возникновения проблемы.

Для устранения данной проблемы выполните действия, указанные ниже.

1.  Просмотрите журналы протоколов на сервере клиентского доступа. Журналы протокола расположены в папке *\<каталог установки Exchange Server\>*\\Logging\\HttpProxy*\\\<protocol\>* на сервере клиентского доступа.

2.  Создайте тестовую учетную запись пользователя, а затем войдите из нее на сервер клиентского доступа. Например, войдите в систему со следующего адреса: https:// *\<имя\_сервера\>*/owa.

3.  Запустите диспетчер IIS, а затем подключитесь к серверу, от которого пришла информация о проблеме. Убедитесь в том, что служба MSExchangeAutodiscoverAppPool запущена на CAS.

4.  Выберите пункт **Пулы приложений**, а затем повторно запустите пул приложений **MSExchangeAutoDiscoverAppPool**, выполнив следующую команду из командной консоли:
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeAutoDiscoverAppPool

5.  Повторно запустите связанный зонд, как показано в шаге 2c раздела Проверка наличия проблемы.

6.  Если проблема не устранена, перезапустите службы IIS с помощью служебной программы IISReset.

7.  Повторно запустите связанный зонд, как показано в шаге 2c раздела Проверка наличия проблемы.

8.  Если проблема не устранена, перезапустите сервер.

9.  После перезапуска сервера повторно запустите связанный зонд, как показано в шаге 2c раздела Проверка наличия проблемы.

10. Если зонд все еще не работает, вам понадобится помощь для устранения данной проблемы. Для решения этой проблемы обратитесь к специалисту службы технической поддержки Майкрософт. Сделать это можно в [Центре решений Exchange Server](http://go.microsoft.com/fwlink/p/?linkid=180809). В области навигации выберите элемент **Варианты поддержки и ресурсы** и выберите один из вариантов в разделе **Получите техническую поддержку**, чтобы обратиться к соответствующему специалисту. Так прямое обращение в службу технической поддержки Майкрософт в вашей организации может регламентироваться, сначала ознакомьтесь с инструкциями организации.

## Дополнительные сведения

[Новые возможности в Exchange 2013](https://technet.microsoft.com/ru-ru/library/jj150540\(v=exchg.150\))

[Служба автообнаружения](https://technet.microsoft.com/ru-ru/library/bb124251\(v=exchg.150\))

