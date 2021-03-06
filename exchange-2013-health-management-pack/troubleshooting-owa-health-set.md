﻿---
title: Устранение неполадок, связанных с настройками работоспособности OWA
TOCTitle: Устранение неполадок, связанных с настройками работоспособности OWA
ms:assetid: eae9dbd7-2ce6-43ce-b9a1-b114fd0c3ab4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.scom.owa(v=EXCHG.150)
ms:contentKeyID: 53275677
ms.date: 11/14/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Устранение неполадок, связанных с настройками работоспособности OWA

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Настройки работоспособности Outlook Web App (OWA) отвечают за мониторинг общей работоспособности службы Outlook Web App.

Если вы получите оповещение о неработоспособном состоянии Outlook Web App, это указывает на проблему, вследствие которой пользователи не могут получить доступ к своим почтовым ящикам с помощью Outlook Web App.

## Пояснение

За мониторинг службы Outlook Web App отвечают приведенные ниже зонды и мониторы.


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
<td><p>OwaCtpProbe</p></td>
<td><p>Outlook Web App</p></td>
<td><p>Active Directory</p>
<p>Банк данных</p></td>
<td><p>OwaCtpMonitor</p></td>
</tr>
</tbody>
</table>


Дополнительные сведения о зондах и мониторах см. в разделе [Работоспособность и производительность сервера](https://technet.microsoft.com/ru-ru/library/jj150551\(v=exchg.150\)).

## Распространенные проблемы

Этот зонд может не работать по нескольким причинам. Ниже приведено несколько распространенных причин.

  - Не отвечает пул приложений Outlook Web App, размещенный на наблюдаемом сервере клиентского доступа, или пул приложений, который размещен на сервере почтовых ящиков.

  - На сервере клиентского доступа возникли проблемы с сетью, и он не может подключиться к серверу почтовых ящиков или контроллеру домена.

  - Введены неправильные данные учетной записи наблюдения.

  - База данных пользователя не подключена, или для данного почтового ящика недоступен банк данных.

  - Банк данных не отвечает.

  - Контроллеры доменов не отвечают.

## Действия пользователя

Служба может восстановить работу после отображения оповещения. Поэтому если вы получите оповещение о неработоспособном состоянии настроек работоспособности, сначала убедитесь в наличии данной проблемы. Если проблема не устранена, выполните соответствующие действия по восстановлению, указанные в приведенных ниже разделах.

## Проверка наличия проблемы

1.  Определите имена настроек работоспособности и сервера, указанные в оповещении.

2.  В сообщении приводятся подробные сведения о точной причине возникновения оповещения. В большинстве случаев в сообщении приводится достаточно сведений по устранению неполадок для определения основной причины проблемы. Если в сообщении приводятся непонятные сведения:
    
    1.  Откройте Командная консоль Exchange, а затем выполните следующую команду, чтобы извлечь подробные сведения о настройках работоспособности, которые создали оповещение.
        
            Get-ServerHealth <server name> | ?{$_.HealthSetName -eq "<health set name>"}
        
        Чтобы извлечь подробные сведения о настройках работоспособности Outlook Web App относительно сервера server1.contoso.com, выполните следующую команду.
        
            Get-ServerHealth server1.contoso.com | ?{$_.HealthSetName -eq "OWA"}
    
    2.  Просмотрите выходные данные команды, чтобы определить монитор, сообщивший об ошибке. Параметр **AlertValue** монитора, вызвавшего оповещение, имеет значение `Unhealthy`.
    
    3.  Еще раз запустите зонд для средства мониторинга, которое находится в неисправном состоянии. Обратитесь к таблице в разделе Пояснение, чтобы найти связанный зонд. Для этого выполните следующую команду.
        
            Invoke-MonitoringProbe <health set name>\<probe name> -Server <server name> | Format-List
        
        Например, чтобы создать зонд мониторинга Exchange ActiveSync на сервере *server1.contoso.com*, выполните следующую команду.
        
            Invoke-MonitoringProbe -Identity ActiveSync.Protocol\ActiveSyncSelfTestProbe -Server server1.contoso.com
    
    4.  В выходных данных команды просмотрите значение параметра **Результат** зонда. Если этот параметр имеет значение **Succeeded**, ошибка была временной и в настоящее время устранена. В противном случае обратитесь к действиям по восстановлению, приведенным в следующих разделах.

## Действия по восстановлению монитора OwaCtpMonitor

Уведомление по электронной почте, отправляемое настройками работоспособности, содержит следующие сведения.

  - Имя сервера, отправившего оповещение.

  - Полная трассировка исключения, связанного с последней ошибкой, включая диагностические данные и конкретные сведения о заголовке HTTP.  
    
    **Примечание**. Сведения в полной трассировке исключения можно использовать для устранения проблемы. Исключение, создаваемое зондом, содержит поле "Причина сбоя" с описанием причины сбоя. Например, исключение содержит следующие сведения.
    
      - **MissingKeyword**. В ответе сервера не найдено ожидаемое ключевое слово. В этом случае исключение содержит ожидаемые ключевые слова.
    
      - **NameResolution**.   Сопоставлению DNS не удается сопоставить данное имя сервера.
    
      - **NetworkConnection**.   Зонду не удается подключиться к сети, когда он пытается подключиться к пулу приложения Outlook Web App в службе переднего плана на сервере клиентского доступа (CAFE).
    
      - **UnexpectedHttpResponseCode**. Ответ содержал непредвиденный код HTTP. Например, сервер вернул код HTTP **503**.
    
      - **RequestTimeout**. Сервер слишком долго отвечал на запрос клиента.
    
      - **ScenarioTimeout**. Зонд успешно завершил работу, но это заняло более одной минуты. Обычно это указывает на перегрузку системы.
    
      - **OwaErrorPage**. В Outlook Web App отобразилась страница ошибки. Обычно в сообщении об исключении приводится имя ошибки, которая привела к сбою.
    
      - **OwaMailboxErrorPage**. В Outlook Web App отобразилась страница с ошибкой, связанной с хранилищем почтовых ящиков. Это обычно указывает на неработоспособность хранилища почтовых ящиков или отключение почтовых ящиков.
    
    Трассировка исключения содержит важное поле **FailingComponent**. Зонд пытается определить причину сбоя, как, например, в следующем примере.
    
      - **Mailbox**. Зонду удается установить связь с Outlook Web App, но не удается подключиться к хранилищу почтовых ящиков. В этом случае возник сбой зонда, или задержка доступа к почтовому ящику привела к сбою зонда и созданию ошибки **ScenarioTimeout**. При таких сбоях следует проверить работоспособность серверов почтовых ящиков.
    
      - **Active Directory**. Зонду удается установить связь с Outlook Web App, но не удается подключиться к Active Directory. В этом случае возник сбой зонда, или, возможно, задержка вызова Active Directory привела к тайм-ауту зонда. При таких типах сбоев следует проверить работоспособность контроллеров доменов и сетевое подключение между серверами клиентского доступа и почтовых ящиков, а также контроллерами доменов.
    
      - **Owa**. Обычно это указывает на ошибку, которая произошла на уровне Outlook Web App. При таких сбоях следует проверить работоспособность Outlook Web App на серверах клиентского доступа и почтовых ящиков, а также сетевые подключения.
    
    Исключение также содержит сведения о последнем HTTP-запросе и ответе, полученным до сбоя зонда. Текст сообщения об эскалации содержит путь к журналам зонда. Эти сведения можно использовать для определения полного веб-запроса HTTP и ответов, отправленных при сбое зонда. Этот файл содержит данные только для неисправных зондов, поскольку в журнал записываются исключительно неудачные попытки. Эти сведения можно использовать для получения более подробной информации о сбое при тестировании.

  - Насколько опустилась метрика доступности (x%).

  - Полный путь к папке, которая содержит полные трассировки HTTP-запроса для зонда. По умолчанию эти сведения расположены в папке *\<ExchangeServer\>*\\Logging\\Monitoring\\OWA\\ClientAccessProbe.

  - Время и дата возникновения оповещения.

Для устранения данной проблемы выполните действия, указанные ниже.

1.  Создайте тестовую учетную запись пользователя, а затем войдите из нее на сервер клиентского доступа. Например, войдите в систему со следующего адреса: https://*\<имя\_сервера\>*/owa.
    
    Если не удается войти в систему, выполните проверку, используя другой сервер клиентского доступа, чтобы убедиться, что проблема возникает на определенном сервере клиентского доступа, а не на сервере почтовых ящиков.

2.  Проверьте сетевое подключение между серверами клиентского доступа и почтовых ящиков. С помощью служебной программы ping.exe убедитесь, что отвечает каждый сервер.

3.  Проверьте наличие оповещений, которые связаны с настройками работоспособности OWA.Protocol и могут указывать на проблему с определенным сервером почтовых ящиков. Подробнее см. в разделе [Устранение неполадок в наборе для контроля работоспособности OWA.Protocol](troubleshooting-owa-protocol-health-set.md).

4.  Запустите диспетчер IIS и подключитесь к серверу, который сообщает о проблеме, чтобы убедиться, что на сервере клиентского доступа запущен пул приложений MSExchangeOwaAppPool.

5.  В диспетчере IIS убедитесь, что запущен веб-сайт по умолчанию.

6.  Найдите неисправные зонды в базе данных почтовых ящиков и убедитесь, что она активна на сервере почтовых ящиков, а также что хранилище почтовых ящиков работоспособно. Чтобы получить сведения о GUID неисправной базы данных, откройте сведения о полной трассировке исключения. Каждый сбой должен содержать запись, похожую на следующий пример.
    
    Запуск зонда Owa с целевым адресом: https://localhost/owa/, имя\_пользователя: *HealthMailboxdf8b87828ab0427cb91e985bbdfcec62@yourdomain.com*

7.  Скопируйте GUID HealthMailbox, а затем выполните в командной консоли следующую команду.
    
        Get-Mailbox -Monitoring -Identity <username>
    
    Например, выполните следующую команду:
    
        Get-Mailbox -Monitoring -Identity HealthMailboxdf8b87828ab0427cb91e985bbdfcec62@yourdomain.com
    
    Возвращенный объект может содержать имя базы данных пользователя. Вы также можете определить расположение текущей активной базы данных.

8.  Если между сайтами настроено перенаправление, можно наблюдать за сбоями зондов и созданием ошибки MissingKeyword. Это происходит в связи с тем, что по умолчанию зонды сервера клиентского доступа запускаются в учетных записях для любого расположения, а также с тем, что зонд не пытается выполнить проверку сервера клиентского доступа на другом сайте при использовании перенаправления. Чтобы устранить эту проблему, убедитесь, что серверы на каждом сайте содержатся в MonitoringGroups. Серверы клиентского доступа в заданной группе мониторинга выполняют проверку только совместно с серверами почтовых ящиков в той же группе.
    
    Чтобы определить группы мониторинга для своих серверов, выполните следующую команду.
    
        Get-ExchangeServer | ft MonitoringGroup
    
    Чтобы изменить группу мониторинга на сервере, используйте параметр *MonitoringGroup* вместе с командлетом **Set-ExchangeServer**. Например, введите следующее:
    
        Set-ExchangeServer -Identity "ServerName" -MonitoringGroup "Primary"

9.  В диспетчере IIS щелкните **Пулы приложений**, а затем перезапустите пул приложений **MSExchangeOWAAppPool**, выполнив следующую команду из Командная консоль Exchange.
    
        %SystemRoot%\System32\inetsrv\Appcmd recycle MSExchangeOWAAppPool

10. Повторно запустите связанный зонд, как показано в шаге 2c раздела Проверка наличия проблемы.

11. Если проблема не устранена, перезапустите службы IIS с помощью служебной программы IISReset или следующей команды.
    
        Iisreset /noforce

12. Повторно запустите связанный зонд, как показано в шаге 2c раздела Проверка наличия проблемы.

13. Если проблема не устранена, перезапустите сервер.

14. После перезапуска сервера повторно запустите связанный зонд, как показано в шаге 2c раздела Проверка наличия проблемы.

15. Если зонд все еще не работает, вам понадобится помощь для устранения данной проблемы. Для решения этой проблемы обратитесь к специалисту службы технической поддержки Майкрософт. Сделать это можно в [Центре решений Exchange Server](http://go.microsoft.com/fwlink/p/?linkid=180809). В области навигации выберите элемент **Варианты поддержки и ресурсы** и выберите один из вариантов в разделе **Получите техническую поддержку**, чтобы обратиться к соответствующему специалисту. Так прямое обращение в службу технической поддержки Майкрософт в вашей организации может регламентироваться, сначала ознакомьтесь с инструкциями организации.

## Дополнительные сведения

[Новые возможности в Exchange 2013](https://technet.microsoft.com/ru-ru/library/jj150540\(v=exchg.150\))

[Командлеты Exchange 2013](https://technet.microsoft.com/ru-ru/library/bb124413\(v=exchg.150\))

