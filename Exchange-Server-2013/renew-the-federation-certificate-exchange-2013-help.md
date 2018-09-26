---
title: 'Обновление сертификатов федерации: Exchange 2013 Help'
TOCTitle: Обновление сертификатов федерации
ms:assetid: 0f390713-3058-44d0-9c07-3c982616e790
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Mt779252(v=EXCHG.150)
ms:contentKeyID: 74429173
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Обновление сертификатов федерации

 

_**Последнее изменение раздела:** 2017-02-28_

В этой статье описано, как обновить самозаверяющий сертификат, используемый в доверии федерации:

  - Если срок действия сертификата федерации не истек, выполните действия, описанные в разделе Обновление рабочего сертификата федерации.

  - Если срок действия сертификата федерации истек, выполните действия, описанные в разделе Замена сертификата федерации с истекшим сроком действия.

Дополнительные сведения о довериях федерации и федерации см. в статье [Федерация](federation-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения: 10 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Федерация и сертификаты" в разделе [Разрешения инфраструктуры Exchange и командной консоли](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - В этой статье используется командная консоль Exchange. Сведения о том, как открыть командную консоль Exchange в локальной организации Exchange, см. в статье [Открытие командной консоли Exchange](https://technet.microsoft.com/ru-ru/library/dd638134\(v=exchg.150\)).

  - Чтобы узнать, истек ли срок действия сертификата федерации, выполните следующую команду в командной консоли Exchange:
    ```powershell
        Get-ExchangeCertificate -Thumbprint (Get-FederationTrust).OrgCertificate.Thumbprint | Format-Table -Auto Thumbprint,NotAfter
	```
  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!WARNING]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Обновление рабочего сертификата федерации

Если срок действия сертификата федерации не истек, вы можете обновить его.

## Шаг 1. Создание сертификата федерации

Выполните следующую команду в командной консоли Exchange, чтобы создать сертификат федерации:

```powershell
    $SKI = [System.Guid]::NewGuid().ToString("N"); New-ExchangeCertificate -DomainName 'Federation' -FriendlyName "Exchange Delegation Federation" -Services Federation -SubjectKeyIdentifier $SKI -PrivateKeyExportable $true
```

Дополнительные сведения о синтаксисе и параметрах см. в разделе [New-ExchangeCertificate](https://technet.microsoft.com/ru-ru/library/aa998327\(v=exchg.150\)).

В результате вы получите значение отпечатка нового сертификата. Скопируйте его из окна командной консоли Exchange. Оно понадобится вам позже.

1.  Щелкните правой кнопкой мыши в окне командной консоли Exchange и выберите **Пометить** в появившемся диалоговом окне.

2.  Выберите значение отпечатка и нажмите клавишу ВВОД.

В этой статье мы будет использовать следующее значение отпечатка сертификата федерации: `6A99CED2E4F2B5BE96C5D17D662D217EF58B8F73`. Ваше значение отпечатка сертификата будет отличаться.

## Шаг 2. Настройка нового сертификата как сертификата федерации

Чтобы настроить новый сертификат как сертификат федерации с помощью командной консоли Exchange, используйте следующий синтаксис:
```powershell
    Set-FederationTrust -Identity "Microsoft Federation Gateway" -Thumbprint <Thumbprint> -RefreshMetaData
```
В этом примере используется значение отпечатка сертификата `6A99CED2E4F2B5BE96C5D17D662D217EF58B8F73` из шага 1.

```powershell
    Set-FederationTrust -Identity "Microsoft Federation Gateway" -Thumbprint 6A99CED2E4F2B5BE96C5D17D662D217EF58B8F73 -RefreshMetaData
```

Дополнительные сведения о синтаксисе и параметрах см. в статье [Set-FederationTrust](https://technet.microsoft.com/ru-ru/library/dd298034\(v=exchg.150\)).

**Примечание.** Команда возвращает предупреждение о том, что необходимо обновить TXT-запись о принадлежности домена в DNS. Как это сделать, описано ниже.

## Шаг 3. Обновление TXT-записи о принадлежности домена во внешней DNS

Вы можете спокойно выполнить это действие сейчас, так как TXT-запись проверяется только во время активации (шаг 5). Но чтобы обновленная TXT-запись распространилась по серверам, потребуется некоторое время (в зависимости от срока жизни DNS-записи). Подождите, прежде чем переходить к следующему шагу.

1.  Найдите нужные значения для необходимых TXT-записей, выполнив следующую команду в командной консоли Exchange:
    
    ```powershell
	Get-FederatedDomainProof -DomainName <Domain> | Format-List Thumbprint,Proof
	```
    
    Например, если федеративным является домен contoso.com, выполните следующую команду:
    
    ```powershell
	Get-FederatedDomainProof -DomainName contoso.com | Format-List Thumbprint,Proof
	```
    
    Команда возвращает такие сведения:
    
    `Thumbprint : <new certificate thumbprint>` (например, `6A99CED2E4F2B5BE96C5D17D662D217EF58B8F73`)
    
    `Proof      : <new hash text>` (например, `znMfbkgSbOQSsWFdsW+gm3to0nZSdE3zbcPPHGVAqdgsLFGsCPuLHiyVbKoPmgyZKX90NH2g1PbCZH0YTQF6oA==`)
    
    `Thumbprint : <old certificate thumbprint>` (например, `CC9BC204BB4DC60D06FC1F10F3C373DC785DA2A5`)
    
    `Proof      : <old hash text>` (например, `m4gZX7OLr9iOWYJMVjEklQpoSkPb5hSbcFjD7Q3/vsqmdJ2Z+HcSt7j5pzBKFmEW2s27JYr3xsK2POzAI/8Ffw==`)
    
    Обратите внимание, команда возвращает сведения о двух записях: для нового сертификата и текущего сертификата, который вы заменяете. Определить, какие сведения относятся к какому сертификату, можно по значению отпечатка и текстовому значению хэша, настроенному в текущей TXT-записи о принадлежности домена во внешней (общедоступной) DNS.

2.  Обновите TXT-запись о принадлежности домена во внешней DNS. Инструкции зависят от поставщика услуг DNS, но вы можете изменить текущую TXT-запись, чтобы заменить текущее текстовое значение хэша на новое. Дополнительные сведения см. в разделе, посвященном Exchange Online, в статье [Внешние записи DNS для Office 365](https://go.microsoft.com/fwlink/p/?linkid=265522).

## Шаг 4. Проверка распространения нового сертификата федерации по всем серверам Exchange

Exchange автоматически распространяет новый сертификат федерации по всем серверам.

Чтобы проверить распространение нового сертификата федерации с помощью командной консоли Exchange, выполните следующую команду:
```powershell
    $Servers = Get-ExchangeServer; $Servers | foreach {Get-ExchangeCertificate -Server $_ | Where {$_.Services -match 'Federation'}} | Format-List Identity,Thumbprint,Services,Subject
```
**Примечание.** В Exchange 2010 командлет **Test-FederationCertificate** возвращает имена серверов. В Exchange 2013 или более поздней версии командлет не возвращает имена серверов.

## Шаг 5. Активация нового сертификата федерации

Чтобы активировать новый сертификат федерации с помощью командной консоли Exchange, выполните следующую команду:

```powershell
Set-FederationTrust -Identity "Microsoft Federation Gateway" -PublishFederationCertificate
```

Дополнительные сведения о синтаксисе и параметрах см. в статье [Set-FederationTrust](https://technet.microsoft.com/ru-ru/library/dd298034\(v=exchg.150\)).

**Примечание.** Команда возвращает предупреждение о том, что необходимо обновить TXT-запись о принадлежности домена DNS (что вы уже сделали на шаге 3).

## Как проверить, что все получилось?

Чтобы убедиться, что вы обновили сертификат федерации, выполните следующие действия:

  - В Командная консоль Exchange выполните указанную ниже команду, чтобы убедиться, что используется новый сертификат.
    
    ```powershell
        Get-FederationTrust | Format-List *priv*
    ```
    
      - Свойство **OrgPrivCertificate** должно содержать отпечаток нового сертификата федерации.
    
      - Свойство **OrgPrevPrivCertificate** должно содержать отпечаток старого (замененного) сертификата федерации.

  - В Командная консоль Exchange замените *\<user's email address\>* на адрес электронной почты пользователя в организации и выполните следующую команду, чтобы убедиться, что доверие федерации работает:
    
    ```powershell
	Test-FederationTrust -UserIdentity <user's email address>
	```

## Замена сертификата федерации с истекшим сроком действия

Если срок действия сертификата федерации уже истек, вам нужно удалить все федеративные домены из доверия федерации, а затем удалить и заново создать доверие федерации.

1.  Если у вас несколько федеративных доменов, основной общий домен необходимо удалить в последнюю очередь. Чтобы определить основной общий домен и все федеративные домены с помощью командной консоли Exchange, выполните следующую команду:
    
    ```powershell
	Get-FederatedOrganizationIdentifier | Format-List AccountNamespace,Domains
	```
    
    Значение свойства **AccountNamespace** содержит основной общий домен в формате `FYDIBOHF25SPDLT<primary shared domain>`. Например, в значении `FYDIBOHF25SPDLT.contoso.com` contoso.com — основной общий домен.

2.  Удалите все федеративные домены, кроме общего основного домена, выполнив следующую команду в командной консоли Exchange:
    
    ```powershell
	Remove-FederatedDomain -DomainName <domain> -Force
	```

3.  После этого удалите общий основной домен, выполнив следующую команду в командной консоли Exchange:
    
    ```powershell
	Remove-FederatedDomain -DomainName <domain> -Force
	```

4.  Удалите доверие федерации, выполнив следующую команду в командной консоли Exchange:
    
    ```powershell
	Remove-FederationTrust "Microsoft Federation Gateway"
	```

5.  Создайте доверие федерации заново. Инструкции см. в статье [Создание доверия федерации](https://technet.microsoft.com/ru-ru/library/dd335198\(v=exchg.150\)).

