---
title: 'Настройка проверки подлинности OAuth между организациями Exchange и Exchange Online: Exchange 2013 Help'
TOCTitle: Настройка проверки подлинности OAuth между организациями Exchange и Exchange Online
ms:assetid: f703e153-98e2-4268-8a6e-07a86b0a1d22
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn594521(v=EXCHG.150)
ms:contentKeyID: 61170801
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка проверки подлинности OAuth между организациями Exchange и Exchange Online

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

В гибридных развертываниях только с Exchange 2013 проверка подлинности OAuth настраивается с помощью мастера создания гибридной конфигурации. Для смешанных сред с Exchange 2013 и 2010 или Exchange 2013 и 2007 мастер создания гибридной конфигурации не настраивает новое гибридное подключение проверки подлинности OAuth между Office 365 и локальными организациями Exchange. Эти развертывания по умолчанию используют процесс доверия федерации. Однако определенные возможности Exchange 2013 полностью доступны в организации только при применении протокола проверки подлинности Exchange OAuth.

В настоящее время новый процесс проверки подлинности Exchange OAuth позволяет использовать следующие возможности Exchange:

  - управление правами на сообщения (MRM);

  - функция Exchange "Обнаружение электронных данных на месте".

  - архивация Exchange на месте.

После настройки гибридного развертывания с помощью мастера гибридной конфигурации рекомендуется настроить во всех смешанных организациях Exchange, реализующих гибридное развертывание с Exchange 2013 и Exchange Online, проверку подлинности OAuth Exchange.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если в вашей локальной организации используются только серверы Exchange 2013 с накопительным пакетом обновления 5 или более поздней версией, запустите мастер гибридного развертывания вместо выполнения действий, описанных в этом разделе.<br />
Эта возможность Exchange Server 2013 не совместима полностью со службой Office 365, предоставляемой компанией 21Vianet в Китае. Кроме того, возможны некоторые ограничения. <a href="https://go.microsoft.com/fwlink/?linkid=313640">Дополнительные сведения о службе Office 365, предоставляемой компанией 21Vianet</a>.</td>
</tr>
</tbody>
</table>


## Что нужно знать перед началом работы

  - Предполагаемое время выполнения задачи: 15 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись разрешений "Федерация и сертификаты" в разделе [Разрешения инфраструктуры Exchange и командной консоли](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Выполненная настройка гибридного развертывания с помощью мастера гибридного развертывания. Дополнительные сведения см. в разделе [Гибридные развертывания Exchange Server](https://technet.microsoft.com/ru-ru/library/jj200581\(v=exchg.150\)).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Настройка проверки подлинности OAuth между локальной организацией Exchange и Exchange Online

## Действие 1. Создание объекта сервера проверки подлинности для организации Exchange Online

Чтобы выполнить это действие, необходимо указать проверенный домен для организации Exchange Online. Это должен быть домен, используемый как основной домен SMTP для размещенных в облаке учетных записей электронной почты. Имя этого домена для следующей процедуры — *\<ваш проверенный домен\>*.

Выполните следующую команду в командной консоли Exchange (Exchange PowerShell) в своей локальной организации Exchange.

    New-AuthServer -Name "WindowsAzureACS" -AuthMetadataUrl https://accounts.accesscontrol.windows.net/<your verified domain>/metadata/json/1

## Действие 2. Включение партнерского приложения для организации Exchange Online

Выполните следующую команду в командной консоли Exchange в своей локальной организации Exchange.

    Get-PartnerApplication |  ?{$_.ApplicationIdentifier -eq "00000002-0000-0ff1-ce00-000000000000" -and $_.Realm -eq ""} | Set-PartnerApplication -Enabled $true

## Действие 3. Экспорт локального сертификата проверки подлинности

На этом этапе необходимо выполнить сценарий PowerShell, чтобы экспортировать локальный сертификат проверки подлинности, который затем будет импортирован в вашу организацию Exchange Online.

1.  Сохраните следующий текст в файл сценария PowerShell с именем **ExportAuthCert.ps1**.
    
        $thumbprint = (Get-AuthConfig).CurrentCertificateThumbprint
         
        if((test-path $env:SYSTEMDRIVE\OAuthConfig) -eq $false)
        {
            md $env:SYSTEMDRIVE\OAuthConfig
        }
        cd $env:SYSTEMDRIVE\OAuthConfig
         
        $oAuthCert = (dir Cert:\LocalMachine\My) | where {$_.Thumbprint -match $thumbprint}
        $certType = [System.Security.Cryptography.X509Certificates.X509ContentType]::Cert
        $certBytes = $oAuthCert.Export($certType)
        $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
        [System.IO.File]::WriteAllBytes($CertFile, $certBytes)

2.  В командной консоли локальной организации Exchange выполните сценарий PowerShell, созданный на предыдущем этапе. Например:
    
        .\ExportAuthCert.ps1

## Действие 4. Передача локального сертификата проверки подлинности в службы управления доступом Azure Active Directory

Затем вам нужно использовать Windows PowerShell, чтобы отправить локальный сертификат проверки подлинности, экспортированный на предыдущем этапе, в Служба контроля доступа Azure Active Directory. Для этого должны быть установлены командлеты Модуль Azure Active Directory для Windows PowerShell. Если он не установлен, перейдите на страницу <https://aka.ms/aadposh>, чтобы установить Модуль Azure Active Directory для Windows PowerShell. После установки Модуль Azure Active Directory для Windows PowerShell выполните следующие действия.

1.  Щелкните ярлык **Модуль Azure Active Directory для Windows PowerShell**, чтобы открыть рабочее пространство Windows PowerShell с установленными командлетами Azure AD. Все команды на этом этапе выполняются с помощью Windows PowerShell для консоли Azure Active Directory.

2.  Сохраните следующий текст в файл сценария PowerShell с именем **UploadAuthCert.ps1**.
    
        Connect-MsolService;
        Import-Module msonlineextended;
        
        $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
        
        $objFSO = New-Object -ComObject Scripting.FileSystemObject;
        $CertFile = $objFSO.GetAbsolutePathName($CertFile);
        
        $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate
        $cer.Import($CertFile);
        $binCert = $cer.GetRawCertData();
        $credValue = [System.Convert]::ToBase64String($binCert);
        
        $ServiceName = "00000002-0000-0ff1-ce00-000000000000";
        
        $p = Get-MsolServicePrincipal -ServicePrincipalName $ServiceName
        New-MsolServicePrincipalCredential -AppPrincipalId $p.AppPrincipalId -Type asymmetric -Usage Verify -Value $credValue

3.  Выполните сценарий PowerShell, созданный на предыдущем этапе. Например:
    
        .\UploadAuthCert.ps1

4.  После запуска сценария откроется диалоговое окно учетных данных. Введите данные учетной записи администратора клиента своей организации Microsoft Online Azure AD. После выполнения сценария оставьте сеанс Windows PowerShell для Azure AD открытым. Он понадобится для запуска сценария PowerShell на следующем этапе.

## Действие 5. Регистрация всех имен узлов для внешних конечных точек HTTP локального сервера Exchange с Azure Active Directory

На этом этапе необходимо выполнить сценарий для каждой общедоступной конечной точки локальной организации Exchange. Рекомендуется по возможности использовать подстановочные знаки. Например, предположим, что сервер Exchange доступен для внешних пользователей по адресу **https://mail.contoso.com/ews/exchange.asmx**. В таком случае нужно использовать один подстановочный знак: **\*.contoso.com**. Таким образом будут охвачены конечные точки доменов autodiscover.contoso.com и mail.contoso.com. Однако домен верхнего уровня, **contoso.com**, охвачен не будет. Если серверы клиентского доступа Exchange 2013 доступны для внешних пользователей со службы имен узлов верхнего уровня, эту службу имен узлов необходимо также зарегистрировать как **contoso.com**. Можно регистрировать неограниченное количество дополнительных служб внешних имен узлов.

Если вы не уверены во внешних конечных точках Exchange своей локальной организации Exchange, можно получить список внешних настроенных точек веб-служб, выполнив следующую команду в командной консоли Exchange PowerShell своей локальной организации Exchange:

    Get-WebServicesVirtualDirectory | FL ExternalUrl

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для успешного выполнения следующего сценария необходимо подключить Windows PowerShell для Azure Active Directory к своему клиенту Microsoft Online Azure AD, как описано в действии 4 предыдущего раздела.</td>
</tr>
</tbody>
</table>


1.  Сохраните следующий текст в файл сценария PowerShell с именем **RegisterEndpoints.ps1**. В этом примере используется подстановочный знак для регистрации всех конечных точек для домена contoso.com. Замените **contoso.com** службой имен узлов своей локальной организации Exchange.
    
        $externalAuthority="*.contoso.com"
         
        $ServiceName = "00000002-0000-0ff1-ce00-000000000000";
         
        $p = Get-MsolServicePrincipal -ServicePrincipalName $ServiceName;
         
        $spn = [string]::Format("{0}/{1}", $ServiceName, $externalAuthority);
        $p.ServicePrincipalNames.Add($spn);
         
        Set-MsolServicePrincipal -ObjectID $p.ObjectId -ServicePrincipalNames $p.ServicePrincipalNames;

2.  В Windows PowerShell для Azure Active Directory выполните сценарий PowerShell, созданный на предыдущем этапе. Например:
    
        .\RegisterEndpoints.ps1

## Действие 6. Создание соединителя IntraOrganizationConnector локальной организации со службой Office 365

Необходимо определить целевой адрес ваших почтовых ящиков, размещенных в Exchange Online. Этот целевой адрес создается автоматически в процессе создания клиента Office 365. Например, если доменом вашей организации, размещенным в клиенте Office 365, является "contoso.com", то ваш целевой адрес службы — "contoso.mail.onmicrosoft.com".

С помощью Exchange PowerShell выполните следующий командлет в своей локальной организации:

    New-IntraOrganizationConnector -name ExchangeHybridOnPremisesToOnline -DiscoveryEndpoint https://outlook.office365.com/autodiscover/autodiscover.svc -TargetAddressDomains <your service target address>

## Действие 7. Создание соединителя IntraOrganizationConnector клиента Office 365 с локальной организацией Exchange

Необходимо определить целевой адрес ваших почтовых ящиков, размещенных в локальной организации. Если основным SMTP-адресом организации является "contoso.com", то ваш целевой адрес — "contoso.com".

Кроме того, необходимо определить внешнюю точку автообнаружения для локальной организации. Если ваша компания — "contoso.com", нужно использовать одно из следующих значений:

  - https://autodiscover.\<ваш основой домен SMTP\>/autodiscover/autodiscover.svc

  - https://\<ваш основной домен SMTP\>/autodiscover/autodiscover.svc

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Командлет <a href="https://technet.microsoft.com/ru-ru/library/dn551183(v=exchg.150)">Get-IntraOrganizationConfiguration</a> можно использовать для локальных клиентов и клиентов Office 365 для определения значений конечных точек, необходимых для командлета <a href="https://technet.microsoft.com/ru-ru/library/dn551178(v=exchg.150)">New-IntraOrganizationConnector</a>.</td>
</tr>
</tbody>
</table>


С помощью Windows PowerShell выполните следующий командлет:

    $UserCredential = Get-Credential
    
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    
    Import-PSSession $Session
    
    New-IntraOrganizationConnector -name ExchangeHybridOnlineToOnPremises -DiscoveryEndpoint <your on-premises Autodiscover endpoint> -TargetAddressDomains <your on-premises SMTP domain>

## Действие 8. Настройка AvailabilityAddressSpace для любых серверов Exchange до версии Exchange 2013 с пакетом обновления 1 (SP1)

При настройке гибридного развертывания в организации с версией Exchange, предшествующей Exchange 2013, необходимо установить в существующей организации Exchange по крайней мере один сервер Exchange 2013 SP1 или более поздней версии с ролями сервера клиентского доступа и сервера почтовых ящиков. Серверы клиентского доступа и почтовых ящиков Exchange 2013 действуют как интерфейсные серверы и управляют взаимодействием между существующей локальной организацией Exchange и организацией Exchange Online. Это взаимодействие включает в себя функции транспорта сообщений и обмена ими между локальной организацией и организацией Exchange Online. Мы настоятельно рекомендуем устанавливать в локальной организации более одного сервера Exchange 2013, чтобы повысить надежность и доступность компонентов гибридного развертывания.

В смешанном развертывании с Exchange 2013 и 2010 или Exchange 2013 и 2007 рекомендуется, чтобы все интерфейсные серверы, доступные из Интернета, для вашей организации были серверами клиентского доступа под управлением Exchange 2013 SP1 или более поздней версии. Все запросы веб-служб Exchange (EWS) из Office 365 и Exchange Online должны подключаться к серверам клиентского доступа Exchange 2013 в локальном развертывании. Кроме того, все запросы EWS из локальных организаций Exchange для Exchange Online должны пересылаться через сервер клиентского доступа с Exchange 2013 SP1 или более поздней версией. Так как эти серверы клиентского доступа Exchange 2013 должны обрабатывать дополнительные входящие и исходящие запросы EWS, важно использовать достаточно серверов клиентского доступа Exchange 2013 для обработки нагрузки и обеспечения избыточности подключений. Необходимое число серверов клиентского доступа зависит от среднего объема запросов EWS и в различных организациях разное.

Перед выполнением следующего действия убедитесь в следующем:

  - Интерфейсные гибридные серверы работают под управлением Exchange 2013 SP1 или более поздней версии.

  - У вас есть уникальный внешний URL-адрес EWS для серверов Exchange 2013. Клиент Office 365 должен подключаться к этим серверам для правильной работы облачных запросов гибридных функций.

  - На серверах используются роли сервера клиентского доступа и почтовых ящиков.

  - На всех существующих серверах почтовых ящиков и клиентского доступа Exchange 2010 и 2007 установлены последние накопительные пакеты обновлений (CU) или пакеты обновлений (SP).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Существующие серверы почтовых ящиков Exchange 2010 или 2007 могут продолжать использовать серверы клиентского доступа Exchange 2010 и 2007 для интерфейсных серверов с негибридными подключениями. Только запросам компонентов гибридного развертывания от клиента Office 365 необходимо подключаться к серверам Exchange 2013.</td>
    </tr>
    </tbody>
    </table>


Необходимо настроить *AvailabilityAddressSpace* на серверах клиентского доступа с версией Exchange, предшествующей Exchange 2013, таким образом, чтобы он указывал на конечную точку веб-служб Exchange на локальных серверах клиентского доступа Exchange 2013 с пакетом обновления 1 (SP1). Используется конечная точка, описанная выше на шаге 5, либо ее можно определить, выполнив указанный ниже командлет на локальном сервере клиентского доступа Exchange 2013 с пакетом обновления 1 (SP1).

    Get-WebServicesVirtualDirectory | FL AdminDisplayVersion,ExternalUrl

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если сведения о виртуальных каталогах возвращается от нескольких серверов, используйте конечную точку, полученную для сервера клиентского доступа Exchange 2013 SP1. Для нее значение параметра <em>AdminDisplayVersion</em> будет равно &quot;15.0 (Build 847.32)&quot;.</td>
</tr>
</tbody>
</table>


Чтобы настроить *AvailabilityAddressSpace*, с помощью Exchange PowerShell выполните приведенный ниже командлет в своей локальной организации.

    Add-AvailabilityAddressSpace -AccessMethod InternalProxy -ProxyUrl <your on-premises External Web Services URL> -ForestName <your Office 365 service target address> -UseServiceAccount $True

## Как проверить, что все получилось?

Проверить правильность конфигурации OAuth можно с помощью командлета [Test-OAuthConnectivity](https://technet.microsoft.com/ru-ru/library/jj218623\(v=exchg.150\)). Этот командлет проверяет, могут ли конечные точки локальной организации Exchange и Exchange Online обмениваться запросами на проверку подлинности.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При подключении к своей организации Exchange Online с помощью сеанса удаленной среды Remote PowerShell можно использовать параметр <em>AllowClobber</em> с командлетом <strong>Import-PSSession</strong> для импорта последних команд в локальный сеанс PowerShell.</td>
</tr>
</tbody>
</table>


Чтобы убедиться, что локальная организация Exchange может успешно подключиться к Exchange Online, выполните следующую команду в Exchange PowerShell в своей локальной организации:

    Test-OAuthConnectivity -Service EWS -TargetUri https://outlook.office365.com/ews/exchange.asmx -Mailbox <On-Premises Mailbox> -Verbose | fl

Чтобы убедиться, что организация Exchange Online может успешно подключиться к локальной организации Exchange, воспользуйтесь сеансом удаленной среды [Remote PowerShell](https://technet.microsoft.com/ru-ru/library/jj984289\(v=exchg.150\)), чтобы подключиться к своей организации Exchange Online и выполнить следующую команду:

    Test-OAuthConnectivity -Service EWS -TargetUri <external hostname authority of your Exchange On-Premises deployment>/metadata/json/1 -Mailbox <Exchange Online Mailbox> -Verbose | fl

Например, Test-OAuthConnectivity -Service EWS -TargetUri https://lync.contoso.com/metadata/json/1 -Mailbox ExchangeOnlineBox1 -Verbose | fl

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Ошибку &quot;С SMTP-адресом не сопоставлен почтовый ящик&quot; можно игнорировать. Важно, чтобы параметр <em>ResultTask</em> возвращал значение <strong>Успех</strong>. Например, последний раздел тестовых выходных данных должен выглядеть так:<br />
<code>ResultType: Success</code><br />
<code>Identity: Microsoft.Exchange.Security.OAuth.ValidationResultNodeId</code><br />
<code>IsValid: True</code><br />
<code>ObjectState: New</code></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>

