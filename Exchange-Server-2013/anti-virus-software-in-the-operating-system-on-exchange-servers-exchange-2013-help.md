---
title: 'Антивирусная программа в операционной системе на серверах Exchange: Exchange 2013 Help'
TOCTitle: Антивирусная программа в операционной системе на серверах Exchange
ms:assetid: 7cef6017-7a55-41f3-a636-1ca4fce575b1
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb332342(v=EXCHG.150)
ms:contentKeyID: 50488441
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Антивирусная программа в операционной системе на серверах Exchange

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-07-22_

В этом разделе описываются действия антивирусных программ, работающих на файловом уровне, на компьютерах под управлением Microsoft Exchange Server 2013. Рекомендации, описанные в этом разделе, позволяют улучшить безопасность и работоспособность организации Exchange.

Средства проверки на файловом уровне широко используются. Тем не менее их неправильная настройка может привести к проблемам в Exchange 2013. Существует два типа средств проверки на файловом уровне.

  - *Резидентное средство проверки на файловом уровне* — это часть антивирусной программы, выполняющей проверку на файловом уровне, которая всегда загружена в память. Она проверяет все файлы, которые используются на жестком диске и в памяти компьютера.

  - *Средство проверки на файловом уровне по запросу* — это часть антивирусной программы, выполняющей проверку на файловом уровне, которую можно настроить для проверки файлов на жестком диске вручную или по расписанию. Некоторые версии антивирусных программ начинают проверку по запросу автоматически после обновления сигнатур вирусов, чтобы обеспечить проверку всех файлов с использованием последних сигнатур.

Ниже описаны проблемы, которые могут возникать при использовании средств проверки на файловом уровне в Exchange 2013.

  - Средства проверки на файловом уровне могут проверять файлы при их использовании или через запланированный интервал. Это может привести к тому, что средства проверки заблокируют либо поместят на карантин файл журнала или базы данных Exchange, в то время как Exchange 2013 будет пытаться использовать его. Это поведение может вызвать серьезный сбой в системе Exchange 2013, а также ошибки -1018.

  - Средства проверки на файловом уровне не обеспечивают защиту от вирусов, которые распространяются по электронной почте, таких как вирус Storm Worm. Это была вредоносная программа типа "Троянский конь" с лазейкой, которая распространялась через сообщения электронной почты. Вирус-червь присоединял зараженный компьютер к бот-сети, где компьютер использовался для периодической отправки серий сообщений нежелательной почты.

## Рекомендации по использованию сканирования на уровне файлов в Exchange 2013

При развертывании средств проверки на файловом уровне на серверах Exchange 2013 убедитесь в наличии соответствующих исключений, таких как исключения для каталогов, процессов и расширений имен файлов, для резидентных проверок в памяти и на файловом уровне. В этом разделе описаны рекомендуемые исключения для каталогов, процессов и расширений имен файлов.

**Содержание**

Исключения для каталогов

Исключения для процессов

Исключения для расширений имен файлов

## Исключения для каталогов

Необходимо задать исключения для отдельных каталогов для каждого сервера Exchange, на котором запускается средство поиска вирусов на файловом уровне. В этом разделе описаны каталоги, которые следует исключить из сканирования на уровне файлов.

  - **Серверы почтовых ящиков**
    
      - **Базы данных почтовых ящиков**
        
          - Базы данных, файлы контрольных точек и файлы журналов Exchange. По умолчанию они находятся во вложенных папках папки %ExchangeInstallPath%\\Mailbox. Чтобы определить расположение базы данных почтовых ящиков, журнала транзакций и файла контрольных точек, выполните следующую команду: `Get-MailboxDatabase -Server <servername>| Format-List *path*`
        
          - Индексы содержимого баз данных. По умолчанию они находятся в той же папке, что и файл базы данных.
        
          - Файлы групповых метрик. По умолчанию они находятся в папке %ExchangeInstallPath%GroupMetrics.
        
          - Файлы общих журналов, например файлы журнала отслеживания сообщений и восстановления календаря. По умолчанию они находятся в подпапках в папках %ExchangeInstallPath%TransportRoles\\Logs и %ExchangeInstallPath%Logging. Чтобы определить используемые пути к журналам, выполните следующую команду в командной консоли Exchange: `Get-MailboxServer <servername> | Format-List *path*`
        
          - Файлы автономной адресной книги. По умолчанию они находятся в подпапках в папке %ExchangeInstallPath%ClientAccess\\OAB.
        
          - Системные файлы IIS в папке %SystemRoot%\\System32\\Inetsrv.
        
          - Временная папка базы данных почтовых ящиков: %ExchangeInstallPath%Mailbox\\MDBTEMP
    
      - **Члены групп доступности базы данных**
        
          - Все элементы, перечисленные в списке **Базы данных почтовых ящиков**, и база данных кворума кластера, которая находится в папке %Windir%\\Cluster.
        
          - Файлы следящего каталога. Эти файлы располагаются на другом сервере среды, обычно на сервере клиентского доступа, который не установлен на том же компьютере, что и сервер почтовых ящиков. По умолчанию файлы следящего каталога расположены в папке %SystemDrive%:\\DAGFileShareWitnesses\\\<DAGFQDN\>.
    
      - **служба передачи**
        
          - Файлы журналов, например файлы журнала отслеживания сообщений и журнала подключений. По умолчанию эти файлы находятся в подпапках в папке %ExchangeInstallPath%TransportRoles\\Logs. Чтобы определить используемые пути к журналам, выполните следующую команду в командной консоли Exchange: `Get-TransportService <servername> | Format-List *logpath*,*tracingpath*`
        
          - Папки каталогов сообщений о раскладке и преобразовании. По умолчанию эти папки расположены в папке %ExchangeInstallPath%TransportRoles. Чтобы определить используемые пути, выполните следующую команду в командной консоли Exchange: `Get-TransportService <servername>| Format-List *dir*path*`
        
          - Базы данных очереди, контрольные точки и файлы журналов. По умолчанию они расположены в папке %ExchangeInstallPath%TransportRoles\\Data\\Queue.
        
          - База данных репутации отправителей, контрольная точка и файлы журналов. По умолчанию они расположены в папке %ExchangeInstallPath%TransportRoles\\Data\\SenderReputation.
        
          - Временные папки, которые используются для выполнения преобразований:
            
              - По умолчанию преобразования содержимого выполняются на сервере Exchange в папке %TMP%.
            
              - По умолчанию преобразование формата RTF в MIME/HTML выполняется в папке %ExchangeInstallPath%\\Working\\OleConverter.
        
          - Компонент проверки содержимого используется агентом защиты от вредоносных программ и системой предотвращения потери данных (DLP). По умолчанию они находятся в папке %ExchangeInstallPath%FIP-FS.
    
      - **Транспортная служба почтовых ящиков**
        
          - Файлы журналов, например журналов подключения. По умолчанию эти файлы находятся в подпапках в папке %ExchangeInstallPath%TransportRoles\\Logs\\Mailbox. Чтобы определить используемые пути к журналам, выполните следующую команду в командной консоли Exchange: `Get-MailboxTransportService <servername> | Format-List *logpath*`
    
      - **Единая система обмена сообщениями**
        
          - Файлы грамматики для разных языковых стандартов, например en-EN или es-ES. По умолчанию они хранятся в подпапках папки %ExchangeInstallPath%UnifiedMessaging\\grammars.
        
          - Файлы голосовых приглашений, приветствий и информационных сообщений. По умолчанию они хранятся в подпапках папки %ExchangeInstallPath%UnifiedMessaging\\Prompts.
        
          - Файлы голосовой почты, которые временно хранятся в папке %ExchangeInstallPath%UnifiedMessaging\\voicemail.
        
          - Временные файлы, создаваемые единой системой обмена сообщениями. По умолчанию они хранятся в папке %ExchangeInstallPath%UnifiedMessaging\\temp.
    
      - **Установка**
        
          - Временные файлы установки Exchange Server. Обычно эти файлы расположены в каталоге %SystemRoot%\\Temp\\ExchangeSetup.
    
      - **Служба поиска Exchange**
        
          - Временные файлы, используемые службой поиска Exchange и пакетом фильтров Microsoft Filter Pack для преобразования файлов в изолированной среде. Эти файлы находятся в папке %SystemRoot%\\Temp\\OICE\_*\<GUID\>*\\.

<!-- end list -->

  - **Серверы клиентского доступа**
    
      - **Веб-компоненты**
        
          - Для серверов, на которых используются службы IIS 7.0, папка сжатия, используемая вместе с Майкрософт Outlook Web App. По умолчанию папка сжатия для служб IIS 7.0 имеет следующий путь: %SystemDrive%\\inetpub\\temp\\IIS Temporary Compressed Files.
        
          - Системные файлы IIS в папке %SystemRoot%\\System32\\Inetsrv.
        
          - Inetpub\\logs\\logfiles\\w3svc
        
          - Вложенные папки в каталоге %SystemRoot%\\Microsoft.NET\\Framework64\\v4.0.30319\\Temporary ASP.NET Files
    
      - **Журналы протоколов POP3 и IMAP4**
        
          - Папка POP3: %ExchangeInstallPath%Logging\\POP3
        
          - Папка IMAP4: %ExchangeInstallPath%Logging\\IMAP4
    
      - **Транспортная служба переднего плана**
        
          - Файлы журналов, например журналов подключений и журналов протоколов. По умолчанию эти файлы находятся в подпапках в папке %ExchangeInstallPath%TransportRoles\\Logs\\FrontEnd. Чтобы определить используемые пути к журналам, выполните следующую команду в командной консоли Exchange: `Get-FrontEndTransportService <servername> | Format-List *logpath*`
    
      - **Установка**
        
          - Временные файлы программы установки Exchange Server. Как правило, эти файлы находятся в папке %SystemRoot%\\Temp\\ExchangeSetup.

Рекомендации по использованию сканирования на уровне файлов в Exchange 2013

## Исключения для процессов

Многие современные средства проверки на файловом уровне поддерживают проверку процессов, что может неблагоприятно повлиять на Microsoft Exchange, если сканируются неправильные процессы. Поэтому необходимо отключить проверку на файловом уровне для указанных ниже процессов.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Процесс</th>
<th>Путь</th>
<th>Комментарии</th>
<th>Серверы</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dsamain.exe</p></td>
<td><p>%SystemRoot%\System32</p></td>
<td><p>Службы Active Directory облегченного доступа к каталогам (AD LDS) на подписанных пограничных транспортных серверах.</p></td>
<td><p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="even">
<td><p>EdgeTransport.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Рабочий процесс службы транспорта Microsoft Exchange</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="odd">
<td><p>fms.exe</p></td>
<td><p>%ExchangeInstallPath%FIP-FS\Bin</p></td>
<td><p>Компонент сканирования контента, используемый агентом вредоносных программ и DLP.</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>hostcontrollerservice.exe</p></td>
<td><p>%ExchangeInstallPath%Bin\Search\Ceres\HostController</p></td>
<td><p>Служба контроллера узла поиска Microsoft Exchange (HostControllerService)</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p></td>
</tr>
<tr class="odd">
<td><p>inetinfo.exe</p></td>
<td><p>%SystemRoot%\System32\inetsrv</p></td>
<td><p>Службы IIS (Internet Information Services).</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.AntispamUpdateSvc.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба обновления средства защиты от нежелательной почты Microsoft Exchange (MSExchangeAntispamUpdate)</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.ContentFilter.Wrapper.exe</p></td>
<td><p>%ExchangeInstallPath%TransportRoles\agents\Hygiene</p></td>
<td><p>Агент фильтра содержимого</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Diagnostics.Service.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба диагностики Microsoft Exchange (MSExchangeDiagnostics)</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Directory.TopologyService.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба топологии Active Directory Microsoft Exchange (MSExchangeADTopology)</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.EdgeCredentialSvc.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба учетных данных Microsoft Exchange (MSExchangeEdgeCredential)</p></td>
<td><p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.EdgeSyncSvc.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба Microsoft Exchange EdgeSync (MSExchangeEdgeSync)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Imap4.exe</p></td>
<td><p>ExchangeInstallPath%FrontEnd\PopImap</p></td>
<td><p>Служба IMAP4 Microsoft Exchange (MSExchangeImap4)</p></td>
<td><p>Серверы клиентского доступа</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Imap4service.exe</p></td>
<td><p>%ExchangeInstallPath%ClientAccess\PopImap</p></td>
<td><p>Внутренняя служба IMAP4 Microsoft Exchange (MSExchangeIMAP4BE)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Pop3.exe</p></td>
<td><p>%ExchangeInstallPath%FrontEnd\PopImap</p></td>
<td><p>Служба POP3 Microsoft Exchange (MSExchangePop3)</p></td>
<td><p>Серверы клиентского доступа</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Pop3service.exe</p></td>
<td><p>%ExchangeInstallPath%ClientAccess\PopImap</p></td>
<td><p>Внутренняя служба POP3 Microsoft Exchange (MSExchangePOP3BE)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.ProtectedServiceHost.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба узла Microsoft Exchange (MSExchangeServiceHost)</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.RPCClientAccess.Service.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба клиентского доступа RPC Microsoft Exchange (MSExchangeRPC)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Search.Service.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба поиска Microsoft Exchange (MSExchangeFastSearch)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Servicehost.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба узла Microsoft Exchange (MSExchangeServiceHost)</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.Store.Service.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба банка сообщений Microsoft Exchange (MSExchangeIS)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Exchange.Store.Worker.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Рабочий процесс службы банка данных Microsoft Exchange</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Exchange.UM.CallRouter.exe</p></td>
<td><p>%ExchangeInstallPath%FrontEnd\CallRouter</p></td>
<td><p>Служба маршрутизатора вызовов службы единой системы обмена сообщениями Microsoft Exchange (MSExchangeUMCR)</p></td>
<td><p>Серверы клиентского доступа</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeDagMgmt.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба управления группами обеспечения доступности баз данных Microsoft Exchange (MSExchangeDagMgmt)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeDelivery.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба доставки транспорта почтовых ящиков Microsoft Exchange (MSExchangeDelivery)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeFrontendTransport.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Интерфейсная транспортная служба Microsoft Exchange (MSExchangeFrontEndTransport)</p></td>
<td><p>Серверы клиентского доступа</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeHMHost.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба диспетчера работоспособности Microsoft Exchange (MSExchangeHM)</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeHMWorker.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Рабочий процесс службы диспетчера работоспособности Microsoft Exchange</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeMailboxAssistants.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба помощников по обслуживанию почтовых ящиков Microsoft Exchange (MSExchangeMailboxAssistants)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeMailboxReplication.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба репликации почтовых ящиков Microsoft Exchange (MSExchangeMailboxReplication)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeMigrationWorkflow.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба рабочего процесса миграции Microsoft Exchange (MSExchangeMigrationWorkflow)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeRepl.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба репликации Microsoft Exchange (MSExchangeRepl)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeSubmission.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба отправки транспорта почтовых ящиков Microsoft Exchange (MSExchangeSubmission)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeTransport.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба транспорта Microsoft Exchange (MSExchangeTransport)</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeTransportLogSearch.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба поиска в журнале транспорта Microsoft Exchange (MSExchangeTransportLogSearch)</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeThrottling.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба регулирования Microsoft Exchange (MSExchangeThrottling)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>Noderunner.exe</p></td>
<td><p>%ExchangeInstallPath%Bin\Search\Ceres\Runtime\1.0</p></td>
<td><p>Служба поиска Microsoft Exchange (MSExchangeFastSearch)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>OleConverter.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Преобразует сообщения в формате RTF в MIME/HTML для внешних получателей.</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>ParserServer.exe</p></td>
<td><p>%ExchangeInstallPath%Bin\Search\Ceres\ParserServer</p></td>
<td><p>Служба поиска Microsoft Exchange (MSExchangeFastSearch)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>Powershell.exe</p></td>
<td><p>C:\Windows\System32\WindowsPowerShell\v1.0</p></td>
<td><p>Командная консоль Exchange</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p>
<p>Пограничные транспортные серверы</p></td>
</tr>
<tr class="even">
<td><p>ScanEngineTest.exe</p></td>
<td><p>%ExchangeInstallPath%FIP-FS\Bin</p></td>
<td><p>Компонент сканирования контента, используемый агентом вредоносных программ и DLP.</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>ScanningProcess.exe</p></td>
<td><p>%ExchangeInstallPath%FIP-FS\Bin</p></td>
<td><p>Компонент сканирования контента, используемый агентом вредоносных программ и DLP.</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>TranscodingService.exe</p></td>
<td><p>%ExchangeInstallPath%ClientAccess\Owa\Bin\DocumentViewing</p></td>
<td><p>Просмотр документов WebReady в Outlook Web App.</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>UmService.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Служба единой системы обмена сообщениями Microsoft Exchange (MSExchangeUM)</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>UmWorkerProcess.exe</p></td>
<td><p>%ExchangeInstallPath%Bin</p></td>
<td><p>Рабочий процесс службы единой системы обмена сообщениями Microsoft Exchange</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>UpdateService.exe</p></td>
<td><p>%ExchangeInstallPath%FIP-FS\Bin</p></td>
<td><p>Компонент сканирования контента, используемый агентом вредоносных программ и DLP.</p></td>
<td><p>Серверы почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>W3wp.exe</p></td>
<td><p>%SystemRoot%\System32\inetsrv</p></td>
<td><p>Службы IIS (Internet Information Services).</p></td>
<td><p>Серверы почтовых ящиков</p>
<p>Серверы клиентского доступа</p></td>
</tr>
</tbody>
</table>


Рекомендации по использованию сканирования на уровне файлов в Exchange 2013

## Исключения для расширений имен файлов

Кроме определенных каталогов и процессов, из проверки необходимо исключить перечисленные ниже расширения имен файлов, свойственные Exchange, в случае сбоя исключений каталогов или перемещения файлов из расположений по умолчанию.

  - Расширения, связанные с приложениями
    
      - .config
    
      - .dia
    
      - .wsb

<!-- end list -->

  - Расширения, связанные с базами данных
    
      - .chk
    
      - .edb
    
      - .jrs
    
      - .jsl
    
      - .log
    
      - .que

<!-- end list -->

  - Расширения, связанные с автономной адресной книгой
    
      - .lzx

<!-- end list -->

  - Расширения, связанные с индексами содержимого
    
      - .ci
    
      - .dir
    
      - .wid
    
      - .000
    
      - .001
    
      - .002

<!-- end list -->

  - Расширения, связанные с единой системой обмена сообщениями
    
      - .cfg
    
      - .grxml

<!-- end list -->

  - Расширения, связанные с групповыми метриками
    
      - .dsc
    
      - .txt

Рекомендации по использованию сканирования на уровне файлов в Exchange 2013

