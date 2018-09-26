---
title: 'Настройка проксирования push-уведомлений в случае приложения OWA для устройств'
TOCTitle: Настройка передачи push-уведомлений в службе "Веб-приложение OWA для устройств"
ms:assetid: c0f4912d-8bd3-4a54-9097-03619c645c6a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn511017(v=EXCHG.150)
ms:contentKeyID: 59954068
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка передачи push-уведомлений в службе \"Веб-приложение OWA для устройств\"

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Включение push-уведомлений в службе Outlook Web App для устройств (веб-приложение OWA для iPhone и iPad) для локального развертывания Microsoft Exchange 2013 позволяет отправлять пользователям обновления Outlook Web App путем обозначения количества непрочитанных сообщений в их почтовых ящиках на значке веб-приложения OWA для iPhone и iPad. Если push-уведомления не включены или не настроены, пользователь Outlook Web App для устройств сможет узнать о непрочитанных сообщениях, только запустив приложение. Когда поступает новое сообщение, индикатор событий Outlook Web App для устройств обновляется на устройстве пользователя и выглядит так, как показано на рисунке ниже.

![Эмблема использования OWA для устройств](images/Dn511017.f399ba74-5395-4d24-ae7d-d16bf0ac7b35(EXCHG.150).png "Эмблема использования OWA для устройств")

## Как включить push-уведомления?

Для активации push-уведомлений необходимо подключить локальные серверы Exchange 2013 к службе push-уведомлений Office 365, чтобы отправлять их на устройства iPhone и iPad. Локальные серверы Exchange 2013 маршрутизируют свои уведомления об обновлениях через службы уведомлений Office 365, поэтому нет необходимости регистрировать учетные записи разработчиков в сторонних службах уведомлений. На схеме ниже изображен процесс получения обновлений о непрочитанных сообщениях с помощью индикаторов событий на устройствах iPhone и iPad.

![Процесс настройки принудительных уведомлений](images/Dn511017.36764ce6-7351-492f-a17e-c42b781e2781(EXCHG.150).jpg "Процесс настройки принудительных уведомлений")

Чтобы включить push-уведомления, администратор должен:

1.  зарегистрировать свою организацию в службе Office 365 для предприятий;

2.  обновить все локальные серверы Exchange Server 2013 до версии накопительного пакета обновления 3 (CU3) или более поздней;

3.  настроить локальный сервер Exchange 2013 для проверки подлинности в Office 365;

4.  включить получение push-уведомлений с локального сервера Exchange Server 2013 в службу Office 365 и убедиться в их работоспособности.

## Регистрация организации в службе Office 365 для предприятий

Office 365 — это облачная служба, которая предназначена для удовлетворения потребностей организации в надежной системе безопасности, безотказности и производительности труда пользователей. Office 365 предусматривает использование планов подписки, которые обеспечивают доступ к приложениям Office, а также другим высокопроизводительным службам в Интернете (облачные службы), например службы веб-конференций Lync и размещенной электронной почты Exchange Online для бизнеса.

Большинство планов Office 365 также содержат последние классические версии приложений Office, которые пользователи могут установить на несколько компьютеров и устройств. Все планы Office 365 подлежат оплате на условиях подписки, ежемесячно или ежегодно. Подробнее об этом, а также о регистрации службы Office 365 в своей организации см. на странице [Что такое Office 365 для бизнеса?](http://go.microsoft.com/fwlink/?linkid=335705). Дополнительные сведения о каждой службе, предлагаемой в рамках Office 365, см. в статье [Описание службы Office 365](http://go.microsoft.com/fwlink/?linkid=335704).

## Обновление до версии CU3 или более поздней

Накопительный пакет обновления 3 (CU3) для Exchange Server 2013 устраняет проблемы, обнаруженные в Exchange Server 2013 с момента выпуска его окончательной версии. Он охватывает все проблемы и исправления накопительных пакетов обновления 1 и 2, а также содержит другие исправления и обновления для накопительного пакета 2. Установка этого обновления настоятельно рекомендуется для всех локальных клиентов Exchange Server 2013 и необходима для включения push-уведомлений. О накопительных накопительный пакетах обновления, в том числе о пакете CU3, читайте в разделе [Обновления для Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md).

## Настройка локального сервера Exchange 2013 для проверки подлинности в Office 365

В Exchange Server 2013 используется единый, стандартизованный способ проверки подлинности сервера. [Exchange Server 2013](http://go.microsoft.com/fwlink/?linkid=290946) (а также [Lync Server 2013](http://go.microsoft.com/fwlink/?linkid=273796), [SharePoint 2013](http://go.microsoft.com/fwlink/?linkid=335701)) и [Office 2013](http://go.microsoft.com/fwlink/?linkid=335696) поддерживают протокол OAuth (Open Authorization) для проверки подлинности и авторизации "сервер-сервер". При использовании протокола OAuth — стандартного протокола авторизации на многих крупных веб-сайтах — учетные данные и пароли пользователей не передаются с одного компьютера на другой. При этом проверка подлинности и авторизация выполняются с использованием токенов безопасности OAuth, которые обеспечивают доступ к определенному набору ресурсов на конкретный период времени.

В проверке подлинности OAuth, как правило, участвуют три компонента: единый сервер авторизации и две области, которые должны обмениваться данными. Сервер авторизации (также называемый "сервер токенов безопасности") отправляет токены безопасности этим двум областям. Токены проверяют, установлено ли между двумя областями доверительное соединение. Например, сервер авторизации создает токены, которые подтверждают, что пользователи одной области Lync Server 2013 могут получить доступ к области Exchange 2013 и наоборот.

> [!TIP]  
> Область является контейнером безопасности.


Однако для локальной проверки подлинности "сервер-сервер" нет необходимости использовать сторонние токены. Такие серверные продукты, как Lync Server 2013 и Exchange 2013, содержат встроенные серверы токенов, которые можно использовать для проверки подлинности на других серверах Майкрософт (например, SharePoint Server), поддерживающих проверку подлинности "сервер-сервер". Например, Lync Server 2013 может сам создать и подписать токен безопасности, с помощью которого затем установит связь с Exchange 2013. В таком случае использовать сторонний сервер токенов не нужно.

Чтобы настроить проверку подлинности "сервер-сервер" для локальной реализации Exchange Server 2013 в службе Office 365, необходимо выполнить два действия.

  -  **Действие 1. Назначение сертификата встроенному издателю токенов локального сервера Exchange Server.** Во-первых, локальный администратор Exchange должен создать сертификат, если он не был создан ранее, и назначить его встроенному издателю токенов локального сервера Exchange Server с помощью сценария командной консоли Exchange. Это действие выполняется только один раз; созданный сертификат не заменяется и повторно используется для других сценариев проверки подлинности. Обязательно обновите значение *$tenantDomain* в соответствии с именем своего домена. Для этого скопируйте и вставьте указанный ниже код.
    

        > [!WARNING]  
        > Копирование кода в текстовый редактор, например Блокнот, и сохранение его с расширением PS1 упрощает запуск сценариев командной консоли.
    
        ```powershell
        # Make sure to update the following $tenantDomain with your Office 365 tenant domain.

        $tenantDomain = "Fabrikam.com"
        
        # Check whether the cert returned from Get-AuthConfig is valid and keysize must be >= 2048
        
        $c = Get-ExchangeCertificate | ?{$_.CertificateDomains -eq $env:USERDNSDOMAIN -and $_.Services -ge "SMTP" -and $_.PublicKeySize -ge 2048 -and $_.FriendlyName -match "OAuth"}
        If ($c.Count -eq 0)
        {
            Write-Host "Creating certificate for oAuth..."
            $ski = [System.Guid]::NewGuid().ToString("N")
            $friendlyName = "Exchange S2S OAuth"
            New-ExchangeCertificate -FriendlyName $friendlyName -DomainName $env:USERDNSDOMAIN -Services Federation -KeySize 2048 -PrivateKeyExportable $true -SubjectKeyIdentifier $ski
            $c = Get-ExchangeCertificate | ?{$_.friendlyname -eq $friendlyName}
        }
        ElseIf ($c.Count -gt 1)
        {
            $c = $c[0]
        }
        
        $a = $c | ?{$_.Thumbprint -eq (get-authconfig).CurrentCertificateThumbprint}
        If ($a.Count -eq 0)
        {
            Set-AuthConfig -CertificateThumbprint $c.Thumbprint
        }
        Write-Host "Configured Certificate Thumbprint is:"(get-authconfig).CurrentCertificateThumbprint
        
        # Export the certificate
        
        Write-Host "Exporting certificate..."
        if((test-path $env:SYSTEMDRIVE\OAuthConfig) -eq $false)
        {
            md $env:SYSTEMDRIVE\OAuthConfig
        }
        cd $env:SYSTEMDRIVE\OAuthConfig
        
        $oAuthCert = (dir Cert:\LocalMachine\My) | where {$_.FriendlyName -match "OAuth"}
        $certType = [System.Security.Cryptography.X509Certificates.X509ContentType]::Cert
        $certBytes = $oAuthCert.Export($certType)
        $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
        [System.IO.File]::WriteAllBytes($CertFile, $certBytes)
        
        # Set AuthServer
        $authServer = Get-AuthServer MicrosoftSts;
        if ($authServer.Length -eq 0)
        {
            Write-Host "Creating AuthServer Config..."
            New-AuthServer MicrosoftSts -AuthMetadataUrl https://accounts.accesscontrol.windows.net/metadata/json/1/?realm=$tenantDomain
        }
        elseif ($authServer.AuthMetadataUrl -ne "https://accounts.accesscontrol.windows.net/metadata/json/1/?realm=$tenantDomain")
        {
            Write-Warning "AuthServer config already exists but the AuthMetdataUrl doesn't match the appropriate value. Updating..."
            Set-AuthServer MicrosoftSts -AuthMetadataUrl https://accounts.accesscontrol.windows.net/metadata/json/1/?realm=$tenantDomain
        }
        else
        {
            Write-Host "AuthServer Config already exists."
        }
        Write-Host "Complete."
        ```

        Пример ожидаемого результата приведен ниже.

        ```powershell
        Configured Certificate Thumbprint is: 7595DBDEA83DACB5757441D44899BCDB9911253C
        Exporting certificate...
        Complete.
        ```

        > [!WARNING]  
        > Для продолжения необходимы командлеты Модуль Azure Active Directory для Windows PowerShell. Если командлеты Модуль Azure Active Directory для Windows PowerShell (предыдущее название — модуль Microsoft Online Services для Windows PowerShell) не установлены, это можно сделать, следуя указаниям из статьи <a href="http://aka.ms/aadposh">Управление службой Azure AD с помощью Windows PowerShell</a>.


  - **Действие 2. Настройка взаимодействия Office 365 с локальным сервером Exchange 2013.** Настройте службу Office 365, с которой будет обмениваться данными сервер Exchange Server 2013, как партнерское приложение. Например, если локальный сервер Exchange Server 2013 должен взаимодействовать с Office 365, необходимо настроить его как партнерское приложение. Партнерское приложение — это любое приложение, непосредственно с которым Exchange 2013 может обмениваться токенами безопасности, не используя при этом сторонний сервер токенов безопасности. Администратор локального сервера Exchange 2013 должен использовать указанный ниже сценарий командной консоли Exchange, чтобы настроить клиент Office 365 для взаимодействия с Exchange 2013 как партнерское приложение. Во время выполнения сценария будет предложено ввести имя пользователя и пароль администратора домена клиента Office 365, например administrator@fabrikam.com. Обязательно обновите значение *$CertFile* в соответствии с расположением сертификата, если он не был создан с помощью предыдущего сценария. Для этого скопируйте и вставьте указанный ниже код.

    
```powershell
# Make sure to update the following $CertFile with the path to the cert if not using the previous script.

$CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"

If (Test-Path $CertFile)
{
    $ServiceName = "00000002-0000-0ff1-ce00-000000000000";

    $objFSO = New-Object -ComObject Scripting.FileSystemObject;
    $CertFile = $objFSO.GetAbsolutePathName($CertFile);

    $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate
    $cer.Import($CertFile);
    $binCert = $cer.GetRawCertData();
    $credValue = [System.Convert]::ToBase64String($binCert);

    Write-Host "Please enter the administrator user name and password of the Office 365 tenant domain..."

    Connect-MsolService;
    Import-Module msonlineextended;

    Write-Host "Adding a key to Service Principal..."

    $p = Get-MsolServicePrincipal -ServicePrincipalName $ServiceName
    New-MsolServicePrincipalCredential -AppPrincipalId $p.AppPrincipalId -Type asymmetric -Usage Verify -Value $credValue -StartDate $cer.GetEffectiveDateString() -EndDate $cer.GetExpirationDateString()
}
Else
{
    Write-Error "Cannot find certificate."
}
``` 
    
Пример ожидаемого результата приведен ниже.
    
```powershell
    Please enter the administrator user name and password of the Office 365 tenant domain...
    Adding a key to Service Principal...
    Complete.
```

## Включение передачи push-уведомлений

После успешной настройки проверки подлинности OAuth с помощью описанных выше действий, локальный администратор должен включить передачу push-уведомлений, используя следующий сценарий. Обязательно обновите значение *$tenantDomain* в соответствии с именем своего домена. Для этого скопируйте и вставьте указанный ниже код.
```powershell
    $tenantDomain = "Fabrikam.com"
    Enable-PushNotificationProxy -Organization:$tenantDomain
```
Пример ожидаемого результата приведен ниже.
```powershell
    RunspaceId        : 4f2eb5cc-b696-482f-92bb-5b254cd19d60
    DisplayName       : On Premises Proxy app
    Enabled           : True
    Organization      : fabrikam.com
    Uri               : https://outlook.office365.com/PushNotifications
    Identity          : OnPrem-Proxy
    IsValid           : True
    ExchangeVersion   : 0.20 (15.0.0.0)
    Name              : OnPrem-Proxy
    DistinguishedName : CN=OnPrem-Proxy,CN=Push Notifications Settings,CN=First Organization,CN=Microsoft
                        Exchange,CN=Services,CN=Configuration,DC=Domain,DC=extest,DC=microsoft,DC=com
    Guid              : 8b567958-58a4-403c-a8f0-524d7f1e9279
    ObjectCategory    : fabrikam.com/Configuration/Schema/ms-Exch-Push-Notifications-App
    ObjectClass       : {top, msExchPushNotificationsApp}
    WhenChanged       : 8/27/2013 7:23:47 PM
    WhenCreated       : 8/14/2013 1:30:27 PM
    WhenChangedUTC    : 8/28/2013 2:23:47 AM
    WhenCreatedUTC    : 8/14/2013 8:30:27 PM
    OrganizationId    :
    OriginatingServer : server.fabrikam.com
    ObjectState       : Unchanged
```
## Проверка работоспособности push-уведомлений

Выполнив предыдущие действия, можно проверить работоспособность push-уведомлений с помощью одного из описанных ниже способов.

  - **Отправка тестового сообщения электронной почты в почтовый ящик пользователя.**
    
    1.  В учетной записи службы "Веб-приложение OWA для устройств" на мобильной устройстве подпишитесь на получение уведомлений.
    
    2.  Вернитесь на начальный экран устройства; служба "Веб-приложение OWA для устройств" продолжит работу в фоновом режиме.
    
    3.  Отправьте сообщение электронной почты с другого устройства, например с компьютера, в почтовый ящик учетной записи, настроенный на мобильном устройстве.
    
    4.  Через несколько минут на значке приложения должен появиться счетчик непрочитанных сообщений.

  - **Включение отслеживания.** Еще один способ проверить работоспособность push-уведомлений (или узнать, почему они не работают) — включение отслеживания на сервере почтовых ящиков в своей организации. Администратор локального сервера Exchange 2013 должен включить отслеживание передачи push-уведомлений с помощью следующего сценария. Для этого скопируйте и вставьте указанный ниже код.
    
    ```powershell
    # Send a push notification to verify connectivity.
        
        $s = Get-ExchangeServer | ?{$_.ServerRole -match "Mailbox"}
        If ($s.Count -gt 1)
        {
            $s = $s[0]
        }
        If ($s.Count -ne 0)
        {
            # Restart the monitoring service to clear the cache from when push was previously disabled.
            Restart-Service MSExchangeHM
        
            # Give the monitoring service enough time to load.
            Start-Sleep -Seconds:120
        
            Invoke-MonitoringProbe PushNotifications.Proxy\PushNotificationsEnterpriseConnectivityProbe -Server:$s.Fqdn | fl ResultType, Error, Exception
        }
        Else
        {
            Write-Error "Cannot find a Mailbox server in the current site."
        }
    ```
    
    Пример ожидаемого результата приведен ниже.
    ```powershell
        ResultType : Succeeded
        Error      :
        Exception  :
	```