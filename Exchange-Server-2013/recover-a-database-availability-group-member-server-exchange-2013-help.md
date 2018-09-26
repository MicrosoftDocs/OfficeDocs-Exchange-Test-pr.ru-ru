---
title: 'Восстановление рядового сервера группы обеспечения доступности баз данных: Exchange 2013 Help'
TOCTitle: Восстановление рядового сервера группы обеспечения доступности баз данных
ms:assetid: eccd8f61-9706-4bb7-a62a-ec7c166f8019
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638206(v=EXCHG.150)
ms:contentKeyID: 50489443
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Восстановление рядового сервера группы обеспечения доступности баз данных

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Если сервер почтовых ящиков, являющийся членом группы обеспечения доступности баз данных, потерян или произошел его сбой и теперь этот сервер не подлежит восстановлению и нуждается в замене, можно выполнить операцию восстановления сервера. В программе установки Microsoft Exchange Server 2013 имеется параметр */m:RecoverServer*, который можно использовать для выполнения операции восстановления сервера. Выполнение команды Setup с параметром */m:RecoverServer* предписывает программе установки считывать из службы каталогов Active Directory сведения о конфигурации для сервера с тем же именем, что и сервер, с которого выполняется программа установки. После извлечения сведений о конфигурации сервера из Active Directory на сервере устанавливаются исходные файлы и службы Exchange и к серверу применяются роли и параметры, хранившиеся в Active Directory.

Необходимы сведения о других задачах управления, связанных с группами обеспечения доступности баз данных? См. раздел [Управление группами доступности базы данных](managing-database-availability-groups-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения: 30 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Копии базы данных почтовых ящиков" в разделе [Разрешения высокого уровня доступности и устойчивости сайта](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Если Exchange устанавливается в папке, отличной от папки по умолчанию, необходимо использовать параметр программы установки */TargetDir*, чтобы указать расположение файлов программ Exchange. Если вы не воспользуетесь параметром */TargetDir*, программные файлы Exchange будут установлены в папке по умолчанию (%programfiles%\\Microsoft\\Exchange Server\\V15).
    
    Чтобы определить расположение для установки, выполните указанные ниже действия.
    
    1.  Откройте файл ADSIEDIT.MSC или LDP.EXE.
    
    2.  Перейдите в следующее расположение: **CN=ExServerName,CN=Servers,CN=First Administrative Group,CN=Administrative Groups,CN=ExOrg Name,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=DomainName,CN=Com**
    
    3.  Щелкните объект сервера Exchange правой кнопкой мыши и выберите пункт **Свойства**.
    
    4.  Найдите атрибут **msExchInstallPath**. Этот атрибут содержит текущий путь установки.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Восстановление сервера с помощью команды Setup /m:RecoverServer

1.  Извлеките все параметры задержки преобразования и задержки усечения для всех копий баз данных почтовых ящиков, существовавших на восстанавливаемом сервере, с помощью командлета [Get-MailboxDatabase](https://technet.microsoft.com/ru-ru/library/bb124924\(v=exchg.150\)).
    ```powershell
        Get-MailboxDatabase DB1 | Format-List *lag*
	```
2.  Удалите все копии баз данных почтовых ящиков, существовавшие на восстанавливаемом сервере, с помощью командлета [Remove-MailboxDatabaseCopy](https://technet.microsoft.com/ru-ru/library/dd335119\(v=exchg.150\)).
    
    ```powershell
	Remove-MailboxDatabaseCopy DB1\MBX1
	```

3.  Удалите конфигурацию отказавшего сервера из группы обеспечения доступности баз данных с помощью командлета [Remove-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/ru-ru/library/dd297956\(v=exchg.150\)).
    
    ```powershell
	Remove-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX1
	```
    
    > [!NOTE]  
    > Если удаляемый член DAG отключен и не может быть включен, к команде выше следует добавить параметр <em>ConfigurationOnly</em>. Если вы используете параметр <em>ConfigurationOnly</em>, необходимо также вручную исключить узел из кластера.


4.  Сбросьте учетную запись компьютера сервера в Active Directory. Подробное описание процедуры см. в статье [Сброс учетной записи компьютера](http://go.microsoft.com/fwlink/p/?linkid=167188).

5.  Откройте окно командной строки. С помощью исходного установочного носителя выполните такую команду:
    
    ```powershell
	Setup /m:RecoverServer
	```

6.  После завершения процесса восстановления программы установки добавьте восстановленный сервер в группу обеспечения доступности баз данных с помощью командлета [Add-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/ru-ru/library/dd298049\(v=exchg.150\)).
    
    ```powershell
	Add-DatabaseAvailabilityGroupServer -Identity DAG1 -MailboxServer MBX1
	```

7.  После того как сервер будет снова добавлен в группу обеспечения доступности баз данных, можно заново выполнить конфигурацию копий баз данных почтовых ящиков с помощью командлета [Add-MailboxDatabaseCopy](https://technet.microsoft.com/ru-ru/library/dd298105\(v=exchg.150\)). Если какая-либо из копий баз данных, добавленных ранее, имела время задержки преобразования или задержки усечения более 0, то можно использовать параметры *ReplayLagTime* и *TruncationLagTime* командлета [Add-MailboxDatabaseCopy](https://technet.microsoft.com/ru-ru/library/dd298105\(v=exchg.150\)) для переконфигурации этих параметров.
    ```powershell
        Add-MailboxDatabaseCopy -Identity DB1 -MailboxServer MBX1
        Add-MailboxDatabaseCopy -Identity DB2 -MailboxServer MBX1 -ReplayLagTime 3.00:00:00
        Add-MailboxDatabaseCopy -Identity DB3 -MailboxServer MBX1 -ReplayLagTime 3.00:00:00 -TruncationLagTime 3.00:00:00
	```
## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно восстановили член группы DAG, выполните следующие действия:

  - В консоли выполните следующую команду для проверки работоспособности и состояния восстановленного члена группы DAG:
    
```powershell
Test-ReplicationHealth <ServerName>
```
   
```powershell
Get-MailboxDatabaseCopyStatus -Server <ServerName>
```
   
 Все тесты работоспособности репликации должны пройти успешно, и состояние баз данных и их индексы содержания должны быть работоспособны.

