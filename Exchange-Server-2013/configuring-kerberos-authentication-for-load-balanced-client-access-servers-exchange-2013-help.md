---
title: 'Настройка проверки подлинности Kerberos для серверов клиентского доступа с балансировкой нагрузки: Exchange 2013 Help'
TOCTitle: Настройка проверки подлинности Kerberos для серверов клиентского доступа с балансировкой нагрузки
ms:assetid: 8f4faeea-a825-438d-97dc-1c398ce7aba5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff808312(v=EXCHG.150)
ms:contentKeyID: 62835912
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Настройка проверки подлинности Kerberos для серверов клиентского доступа с балансировкой нагрузки

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

**Сводка.** В этой статье описывается, как использовать проверку подлинности с серверами клиентского доступа с балансировкой нагрузки в Exchange 2013.

Чтобы использовать проверку подлинности с серверами клиентского доступа с балансировкой нагрузки, необходимы выполнить процедуру настройки, представленную в этой статье.

## Создание учетных данных альтернативной учетной записи службы в доменных службах Active Directory

Все серверы клиентского доступа, которые используют одни и те же пространства имен и URL-адреса, должны использовать одинаковые учетные данные службы. В целом достаточно одной учетной записи на лес для каждой версии Exchange. *альтернативные учетные данные службы* или *учетные данные ASA*.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Exchange 2010 и Exchange 2013 не могут использовать одинаковые учетные данные ASA. Необходимо создать новые учетные данные ASA для Exchange 2013.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Общие пространства имен поддерживают записи CNAME, но корпорация Майкрософт рекомендует использовать записи A. Так клиент будет правильно отправлять запрос билета Kerberos (по общему имени, а не полному доменному имени сервера).</td>
</tr>
</tbody>
</table>


При настройке учетных данных ASA помните о следующем.

  - **Тип учетной записи.** Мы рекомендуем создать учетную запись компьютера, а не пользователя. Ученая запись компьютера не поддерживает интерактивный вход и может использовать более простые политики безопасности, чем учетная запись пользователя. При создании учетной записи компьютера срок действия пароля не истекает, но мы все равно рекомендуем периодически обновлять пароль. Локальная групповая политика может определять максимальный срок хранения учетных записей компьютера и использовать скрипты для периодического удаления учетных записей компьютера, не соответствующих текущим политикам. Локальная политика безопасности также определяет, когда следует изменить пароль. Хотя мы рекомендуем использовать учетную запись компьютера, вы можете создать учетную запись пользователя.

  - **Имя учетной записи.** Не существует определенных требований к именованию учетной записи. Можно использовать любое имя, соответствующее схеме именования.

  - **Группа учетной записи.** Учетной записи, используемой для учетных данных ASA, не требуются специальные привилегии безопасности. Если вы применяете учетную запись компьютера, то она должна входить только в группу безопасности компьютеров домена. Если вы применяете учетную запись пользователя, то она должна входить только в группу безопасности пользователей домена.

  - **Пароль учетной записи.** Используется пароль, указанный при создании этой учетной записи. Поэтому следует указать сложный пароль и, соответствующий требованиям к паролю в организации.

Создание учетных данных ASA как учетной записи компьютера

1.  Запустите Windows PowerShell или командную консоль Exchange на компьютере, присоединенном к домену.
    
    Импортируйте модуль Active Directory с помощью командлета **Import-Module**.
    
        Import-Module ActiveDirectory

2.  Выполните командлет **New-ADComputer**, чтобы создать учетную запись компьютера Active Directory, используя следующий синтаксис:
    
        New-ADComputer [-Name] <string> [-AccountPassword <SecureString>] [-AllowReversiblePasswordEncryption <System.Nullable[boolean]>] [-Description <string>] [-Enabled <System.Nullable[bool]>]
    
    **Пример:** 
    
        New-ADComputer -Name EXCH2013ASA -AccountPassword (Read-Host 'Enter password' -AsSecureString) -Description 'Alternate Service Account credentials for Exchange' -Enabled:$True -SamAccountName EXCH2013ASA
    
    Где *EXCH2013ASA* — имя учетной записи, строка *Учетные данные общей альтернативной учетной записи для Exchange* — любое описание по вашему выбору, а значение параметра *SamAccountName* (в этом случае — *EXCH2013ASA*) должно быть уникальным в вашем каталоге.

3.  С помощью командлета **Set-ADComputer** можно включить поддержку шифра AES 256, используемого в Kerberos, используя следующий синтаксис:
    
        Set-ADComputer [-Name] <string> [-add @{<attributename>="<value>"]
    
    **Пример:** 
    
        Set-ADComputer EXCH2013ASA -add @{"msDS-SupportedEncryptionTypes"="28"}
    
    Где *EXCH2013ASA* — имя учетной записи, а изменяемый атрибут — *msDS-SupportedEncryptionTypes* с десятичным значением 28, что позволяет использовать следующие шифры: RC4-HMAC, AES128-CTS-HMAC-SHA1-96, AES256-CTS-HMAC-SHA1-96.

Дополнительные сведения об этих командлетах можно [Import-Module](https://technet.microsoft.com/library/hh849725.aspx) и [New-ADComputer](https://technet.microsoft.com/library/ee617245.aspx).

## Сценарии с несколькими лесами

Если у вас есть между лесами или леса ресурсов развертывания и у вас есть пользователи, находящиеся за пределами Active Directory лес, содержащий Exchange, необходимо настроить отношения доверия леса между лесами. Кроме того для каждого леса в развертывании, необходимо настроить правила маршрутизации, которая позволяет отношения доверия между всех суффиксов имен в пределах леса и между лесами. Дополнительные сведения об управлении отношения доверия между лесами можно [доверия леса управление](https://technet.microsoft.com/library/cc772440.aspx).

## Определение имен участников-служб для связи с учетными данными ASA

После создания учетных данных ASA необходимо связать с ними имена участников служб Exchange (SPN). Список имен участников служб Exchange зависит от текущей конфигурации, но должен содержать следующие имена.

  - **http/**. Это имя SPN необходимо использовать для мобильного Outlook, MAPI через HTTP, веб-служб Exchange, службы автообнаружения и загрузок автономных адресных книг.

Формат имен участников-служб должен соответствовать формату имени службы в подсистеме балансировки сетевой нагрузки, а не на отдельных серверах. Чтобы лучше определить используемые значения SPN, рассмотрите следующие сценарии:

  - Single Active Directory site

  - Multiple Active Directory sites

В каждом из этих сценариев считается, что полные доменные имена с балансировкой нагрузки были развернуты для внутренних URL-адресов, внешних URL-адресов и внутренних URI-кодов автообнаружения, используемых рядовыми серверами клиентского доступа. Дополнительные сведения см. в статье Общие сведения о прокси-серверах и перенаправлении.

## Одиночный сайт Active Directory

Если вы используете один сайт Active Directory, ваша среда может походить на изображенную на следующем рисунке:

![Массив CAS с одним сайтом AD и проверкой подлинности Kerberos](images/Ff808312.97a1a926-f4ac-4498-bc6b-32e7fb1b70f1(EXCHG.150).jpg "Массив CAS с одним сайтом AD и проверкой подлинности Kerberos")

В зависимости от полных доменных имен, используемых внутренними клиентами Outlook на предыдущем рисунке, вам необходимо связать следующие SPN с учетными данными ASA:

  - http/mail.corp.tailspintoys.com

  - http/autodiscover.corp.tailspintoys.com

## Несколько сайтов Active Directory

Если вы используете несколько сайт Active Directory, ваша среда может походить на изображенную на следующем рисунке:

![Массив CAS с несколькими сайтами AD и проверкой подлинности Kerberos](images/Ff808312.95b52bd8-7074-4055-8bd2-e6bf1f112b42(EXCHG.150).jpg "Массив CAS с несколькими сайтами AD и проверкой подлинности Kerberos")

В зависимости от полных доменных имен, используемых внутренними клиентами Outlook на предыдущем рисунке, вам необходимо связать следующие SPN, применяемые серверами клиентского доступа на сайте ADSite 1:

  - http/mail.corp.tailspintoys.com

  - http/autodiscover.corp.tailspintoys.com

Вам также потребуется связать следующие SPN с учетными данными ASA, используемыми серверами клиентского доступа на сайте ADSite 2:

  - http/mailsdc.corp.tailspintoys.com

  - http/autodiscoversdc.corp.tailspintoys.com

## Настройте и проверьте конфигурацию учетных данных ASA на каждом сервере клиентского доступа.

После создания учетной записи необходимо убедиться, что она была реплицирована на все контроллеры домена AD DS. В частности, учетная запись должна присутствовать на каждом сервере клиентского доступа, который будет использовать учетные данные ASA. Затем настройте учетную запись как учетные данные ASA на каждом сервере клиентского доступа в вашем развертывании.

Это можно сделать с помощью командной консоли Exchange, как описано в следующих процедурах:

  - Развертывание учетных данных ASA на первом сервере клиентского доступа Exchange 2013

  - Развертывание учетных данных ASA на остальных серверах клиентского доступа Exchange 2013

Единственный поддерживаемый метод развертывания учетных данных ASA — использовать сценарий RollAlternateServiceAcountPassword.ps1. Дополнительные сведения см. в статье [Использование сценария RollAlternateserviceAccountCredential.ps1 в консоли](using-the-rollalternateserviceaccountcredential-ps1-script-in-the-shell-exchange-2013-help.md). После выполнения этого сценария рекомендуем убедиться, что все целевые серверы правильно обновлены.

## Развертывание учетных данных ASA на первом сервере клиентского доступа Exchange 2013

1.  Откройте консоль управления Exchange на сервере Exchange 2013.

2.  Измените каталоги на *\<каталог установки Exchange 2013\>*\\V15\\Scripts.

3.  Выполните следующую команду, чтобы развернуть учетные данные ASA на первом сервере клиентского доступа Exchange 2013:
    
        .\RollAlternateServiceAccountPassword.ps1 -ToSpecificServer cas-1.corp.tailspintoys.com -GenerateNewPasswordFor tailspin\EXCH2013ASA$

4.  На вопрос, изменять ли пароль для учетной записи альтернативной службы, выберите **Да**.

Ниже представлен пример выходных данных после запуска сценария RollAlternateServiceAccountPassword.ps1.

    ========== Starting at 01/12/2015 10:17:47 ==========
    Creating a new session for implicit remoting of "Get-ExchangeServer" command...
    Destination servers that will be updated:
    
    Name                                                        PSComputerName
    ----                                                        --------------
    cas-1                                                   cas-1.corp.tailspintoys.com
    
    
    Credentials that will be pushed to every server in the specified scope (recent first):
    
    UserName                                                                                                        
    Password
    --------                                                                                                        
    --------
    tailspin\EXCH2013ASA$                                                                             
    System.Security.SecureString
    
    
    Prior to pushing new credentials, all existing credentials that are invalid or no longer work will be removed from  the destination servers.
    Pushing credentials to server cas-1
    Setting a new password on Alternate Serice Account in Active Directory
    
    Password change
    Do you want to change password for tailspin\EXCH2013ASA$ in Active Directory at this time?
    [Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
    Preparing to update Active Directory with a new password for tailspin\EXCH2013ASA$ ...
    Resetting a password in the Active Directory for tailspin\EXCH2013ASA$ ...
    New password was successfully set to Active Directory.
    Retrieving the current Alternate Service Account configuration from servers in scope
    Alternate Service Account properties:
    
    StructuralObjectClass QualifiedUserName Last Pwd Update       SPNs
    --------------------- ----------------- ---------------       ----
    computer              tailspin\EXCH2013ASA$   1/12/2015 10:19:53 AM
    
    Per-server Alternate Service Account configuration as of the time of script completion:
    
    
       Array: {mail.corp.tailspintoys.com}
    
    Identity  AlternateServiceAccountConfiguration
    --------  ------------------------------------
    cas-1 Latest: 1/12/2015 10:19:22 AM, tailspin\EXCH2013ASA$
              ...
    
    ========== Finished at 01/12/2015 10:20:00 ==========
    
            THE SCRIPT HAS SUCCEEDED

## Развертывание учетных данных ASA на другом сервере клиентского доступа Exchange 2013

1.  Откройте консоль управления Exchange на сервере Exchange 2013.

2.  Измените каталоги на *\<каталог установки Exchange 2013\>*\\V15\\Scripts.

3.  Выполните следующую команду, чтобы развернуть учетные данные ASA на другом сервере клиентского доступа Exchange 2013:
    
        .\RollAlternateServiceAccountPassword.ps1 -ToSpecificServer cas-2.corp.tailspintoys.com -CopyFrom cas-1.corp.tailspintoys.com

4.  Повторите шаг 3 для каждого сервера клиентского доступа, на котором нужно развернуть учетные данные ASA.

Ниже представлен пример выходных данных после запуска сценария RollAlternateServiceAccountPassword.ps1.

    ========== Starting at 01/12/2015 10:34:35 ==========
    Destination servers that will be updated:
    
    Name                                                        PSComputerName
    ----                                                        --------------
    cas-2                                                   cas-2.corp.tailspintoys.com
    
    
    Credentials that will be pushed to every server in the specified scope (recent first):
    
    UserName                                                                                                        
    Password
    --------                                                                                                        
    --------
    tailspin\EXCH2013ASA$                                                                             
    System.Security.SecureString
    
    Prior to pushing new credentials, all existing credentials will be removed from the destination servers.
    Pushing credentials to server cas-2
    Retrieving the current Alternate Service Account configuration from servers in scope
    Alternate Service Account properties:
    
    StructuralObjectClass QualifiedUserName Last Pwd Update       SPNs
    --------------------- ----------------- ---------------       ----
    computer              tailspin\EXCH2013ASA$   1/12/2015 10:19:53 AM
    
    Per-server Alternate Service Account configuration as of the time of script completion:
    
    
       Array: cas-2.corp.tailspintoys.com
    
    Identity  AlternateServiceAccountConfiguration
    --------  ------------------------------------
    cas-2 Latest: 1/12/2015 10:37:59 AM, tailspin\EXCH2013ASA$
              ...
    
    
    ========== Finished at 01/12/2015 10:38:13 ==========
    
            THE SCRIPT HAS SUCCEEDED

## Проверка развертывания учетных данных ASA

  - Откройте консоль управления Exchange на сервере Exchange 2013.

  - Выполните следующую команду, чтобы проверить параметры на сервере клиентского доступа:
    
        Get-ClientAccessServer CAS-3 -IncludeAlternateServiceAccountCredentialStatus | Format-List Name, AlternateServiceAccountConfiguration

  - Повторите шаг 2 на каждом сервере клиентского доступа, где нужно проверить развертывание учетных данных ASA.

Ниже приводится пример выходных данных после запуска команды Get-ClientAccessServer, если учетные данные ASA еще не были заданы.

    Name                                 : CAS-1
    AlternateServiceAccountConfiguration : Latest: 1/12/2015 10:19:22 AM, tailspin\EXCH2013ASA$
                                           Previous: <Not set>
                                               ...

Ниже приводится пример выходных данных после запуска команды Get-ClientAccessServer, если учетные данные ASA уже были заданы. Возвращаются учетные данные ASA, а также дата и время их установки.

    Name                                 : CAS-3
    AlternateServiceAccountConfiguration : Latest: 1/12/2015 10:19:22 AM, tailspin\EXCH2013ASA$
                                           Previous: 7/15/2014 12:58:35 PM, tailspin\oldSharedServiceAccountName$
                                               ...

## Связывание имен участников-служб (SPN) с учетными данными ASA

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Не связывайте имена субъектов-служб с учетными данными ASA, пока эти учетные данные не будут развернуты по крайней мере на одном сервере Exchange Server, как упоминалось ранее в разделе Развертывание учетных данных ASA на первом сервере клиентского доступа Exchange 2013. В противном случае будут возникать ошибки проверки подлинности Kerberos.</td>
</tr>
</tbody>
</table>


Перед привязкой имен участников-служб с учетными данными ASA убедитесь, что целевые имена уже не связаны с другими учетными записями в лесу. Эти имена участников-служб необходимо сопоставить только с учетными данными ASA в лесу. Чтобы убедиться, что имена участников-служб не назначены другим учетным записям в лесу, выполните команду **setspn** в командной строке.

Проверка связи имени участника-службы с учетной записи в лесу с помощью команды setspn

1.  Нажмите кнопку **Пуск**. В поле **Поиск** введите **командная строка**, а затем в списке результатов выберите **Командная строка**.

2.  Введите следующую команду:
    
        setspn -F -Q <SPN>
    
    Где \<SPN\> — это имя участника-службы, которое требуется связать с учетными данными ASA. Например:
    
        setspn -F -Q http/mail.corp.tailspintoys.com
    
    Команда должна не возвратить никаких данных. Если она возвратит данные, значит, это имя участника службы уже сопоставлено с другой учетной записью. Повторите это действие один раз для каждого имени участника-службы, которое требуется связать с учетными данными ASA.

Сопоставление имени участника-службы с учетными данными ASA с помощью команды setspn

1.  Нажмите кнопку **Пуск**. В поле **Поиск** введите **командная строка**, а затем в списке результатов выберите **Командная строка**.

2.  Введите следующую команду:
    
        setspn -S <SPN> <Account>$
    
    Где \<SPN\> — это имя участника-службы, которое требуется связать с учетными данными ASA, а \<Account\> — это учетная запись, связанная с учетными данными ASA. Например:
    
        setspn -S http/mail.corp.tailspintoys.com tailspin\EXCH2013ASA$
    
    Выполните эту команду один раз для каждого имени участника-службы, которое требуется связать с учетными данными ASA.

Проверка связи имен участников-служб с учетными данными ASA с помощью команды setspn

1.  Нажмите кнопку **Пуск**. В поле **Поиск** введите **командная строка**, а затем в списке результатов выберите **Командная строка**.

2.  Введите следующую команду:
    
        setspn -L <Account>$
    
    Где \<Account\> — это учетная запись, связанная с учетными данными ASA. Например:
    
        setspn -L tailspin\EXCH2013ASA$
    
    Эту команду необходимо выполнить только один раз.

## Включение проверки подлинности Kerberos для клиентов Outlook

1.  Откройте консоль управления Exchange на сервере Exchange 2013.

2.  Чтобы включить проверку подлинности Kerberos для мобильных клиентов Outlook, выполните следующую команду на своем сервере клиентского доступа:
    
        Get-OutlookAnywhere -server CAS-1 | Set-OutlookAnywhere -InternalClientAuthenticationMethod  Negotiate

3.  Чтобы включить проверку подлинности Kerberos для клиентов протокола MAPI через HTTP, выполните следующие команды на сервере клиентского доступа Exchange 2013:
    
        Get-MapiVirtualDirectory -Server CAS-1 | Set-MapiVirtualDirectory -IISAuthenticationMethods Ntlm, Negotiate

4.  Повторите шаги 2 и 3 для каждого сервера клиентского доступа Exchange 2013, на котором нужно включить проверку подлинности Kerberos.

## Проверка работы проверки подлинности Kerberos для клиентов Exchange

После успешной настройки Kerberos и учетных данных ASA убедитесь, что клиенты могут пройти проверку подлинности, как описано далее.

## Проверка работы службы узла службы Microsoft Exchange

Служба узла службы Microsoft Exchange (MSExchangeServiceHost) на серверах клиентского доступа управляет учетными данными ASA. Если эта служба не запущена, проверка подлинности Kerberos недоступна. По умолчанию служба настроена на автоматический запуск при включении компьютера.

Проверка работы службы узла службы Microsoft Exchange

1.  Нажмите кнопку **Пуск**, введите **services.msc** и выберите **services.msc** из списка.

2.  В окне **Службы** найдите службу **узла службы Microsoft Exchange**.

3.  Состояние службы должно быть указано как **Работает**. Если состояние отличается от **Работает**, щелкните службу правой кнопкой мыши и выберите команду **Пуск**.

## Проверка работы проверки подлинности Kerberos на сервере клиентского доступа

После настройки учетных данных ASA на каждом сервере клиентского доступа выполните командлет **set-ClientAccessServer**. После этого вы сможете проверить подключение Kerberos с помощью журналов.

Проверка правильной работы Kerberos с помощью файла журнала HttpProxy

1.  В текстовом редакторе перейдите к папке, где хранится журнал HttpProxy. По умолчанию этот файл находится в следующей папке:
    
    %ExchangeInstallPath%\\Logging\\HttpProxy\\RpcHttp

2.  Откройте последний файл журнала и найдите слово **Negotiate**. Строка в файле журнала должна выглядеть примерно следующим образом:
    
        2014-02-19T13:30:49.219Z,e19d08f4-e04c-42da-a6be-b7484b396db0,15,0,775,22,,RpcHttp,mail.corp.tailspintoys.com,/rpc/rpcproxy.dll,,Negotiate,True,tailspin\Wendy,tailspintoys.com,MailboxGuid~ad44b1e0-e44f-4a16-9396-3a437f594f88,MSRPC,192.168.1.77,EXCH1,200,200,,RPC_OUT_DATA,Proxy,exch2.tailspintoys.com,15.00.0775.000,IntraForest,MailboxGuidWithDomain,,,,76,462,1,,1,1,,0,,0,,0,0,16272.3359,0,0,3,0,23,0,25,0,16280,1,16274,16230,16233,16234,16282,?ad44b1e0-e44f-4a16-9396-3a437f594f88@tailspintoys.com:6001,,BeginRequest=2014-02-19T13:30:32.946Z;BeginGetRequestStream=2014-02-19T13:30:32.946Z;OnRequestStreamReady=2014-02-19T13:30:32.946Z;BeginGetResponse=2014-02-19T13:30:32.946Z;OnResponseReady=2014-02-19T13:30:32.977Z;EndGetResponse=2014-02-19T13:30:32.977Z;,PossibleException=IOException;
    
    Если значение параметра **AuthenticationType** равно **Negotiate**, сервер успешно создает подключения с проверкой подлинности Kerberos.

## Обслуживание учетных данных ASA

Если вам требуется периодически обновлять пароль учетных данных ASA, используйте процедуру настройки учетных данных ASA, описанную в этой статье. Также для регулярного обновления пароля можно настроить запланированную задачу. Отслеживайте выполнение этой запланированной задачи для проверки своевременного переключения паролей и предотвращения возможных простоев проверки подлинности.

## Отключение проверки подлинности Kerberos

Чтобы отключить проверку подлинности Kerberos на сервере клиентского доступа, отмените связь имен участников-служб с учетными данными ASA или удалите их. Если имена участников служб удалены, то клиенты не будут выполнять проверку подлинности Kerberos, а клиенты, настроенные на использование проверки подлинности с согласованием, будут выполнять проверку подлинности NTLM. Клиенты, настроенные на использование только проверки подлинности Kerberos, не смогут устанавливать подключения. После удаления имен участников служб необходимо также удалить учетную запись.

Удаление учетных данных ASA

1.  Откройте консоль управления Exchange на сервере Exchange 2013 и выполните следующую команду:
    
        Set-ClientAccessServer CAS-1 -RemoveAlternateServiceAccountCredentials

2.  Хотя и не сразу, но вам потребуется перезапустить все клиентские компьютеры, чтобы удалить кэш билетов Kerberos с компьютера.

