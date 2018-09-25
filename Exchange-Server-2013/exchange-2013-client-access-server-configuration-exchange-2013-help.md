---
title: 'Конфигурация сервера клиентского доступа Exchange 2013: Exchange 2013 Help'
TOCTitle: Конфигурация сервера клиентского доступа Exchange 2013
ms:assetid: 01432ae4-2a00-44a4-a4dd-4eb8d7e6cfae
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh529912(v=EXCHG.150)
ms:contentKeyID: 50487347
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Конфигурация сервера клиентского доступа Exchange 2013

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2017-07-25_

После установки сервера клиентского доступа Exchange 2013 можно выполнить различные задачи настройки. Хотя сервер клиентского доступа Exchange 2013 не обрабатывает клиентские протоколы, к нему необходимо применить некоторые настройки, в том числе виртуальные параметры каталога и сертификата.

## Настройка сертификатов сервера

В Exchange 2013 можно использовать мастер сертификатов для запроса цифрового сертификата в центре сертификации. После запроса цифрового сертификата его необходимо установить на сервере клиентского доступа.

На серверах почтовых ящиков организации не требуется устанавливать цифровые сертификаты. По умолчанию на серверах почтовых ящиков установлен самозаверяющий сертификат, который не требуется заменять. Серверы клиентского доступа организации неявно доверяют самозаверяющему сертификату на серверах почтовых ящиков. Подробнее см. в разделе [Пользовательский интерфейс управления сертификатами Exchange 2013](exchange-2013-certificate-management-ui-exchange-2013-help.md).

## Настройка виртуальных каталогов

Можно настроить несколько параметров виртуальных каталогов автономной адресной книги, веб-служб Exchange, Exchange ActiveSync, Outlook Web App и Центра администрирования Exchange. Дополнительные сведения об управлении виртуальными каталогами см. в разделе [Управление виртуальным каталогом](virtual-directory-management-exchange-2013-help.md). Можно настроить виртуальные каталоги, используя следующие команды.

  - Exchange 2013 предоставляет два набора параметров HTTP-подключения для конфигурации мобильного Outlook, чтобы администраторы могли настроить как внутреннюю, так и внешнюю конечную точку.
    
    Чтобы настроить мобильный Outlook с одним URL-адресом для подключения, укажите имя хоста и требуется ли протокол SSL и authpackage, используя следующую команду в командной консоли Exchange.
    ```powershell
        Get-OutlookAnywhere | Set-OutlookAnywhere -InternalHostname "internalServer.contoso.com" -InternalClientAuthenticationMethod Ntlm -InternalClientsRequireSsl $true -IISAuthenticationMethods Negotiate,NTLM,Basic
    ```
    Можно также указать внешне достижимую конечную точку, используя следующую команду в командной консоли Exchange.
    ```powershell
        Get-OutlookAnywhere | Set-OutlookAnywhere -InternalHostname "internalServer.contoso.com" -InternalClientAuthenticationMethod Ntlm -InternalClientsRequireSsl $true -ExternalHostname "externalServer.company.com" -ExternalClientAuthenticationMethod Basic -ExternalClientsRequireSsl $true -IISAuthenticationMethods Negotiate,NTLM,Basic
    ```
    > [!TIP]  
    > Хотя Exchange 2013 поддерживает Negotiate для проверки подлинности HTTP мобильного Outlook, это должно использоваться только если на всех серверах в среде запущен Exchange 2013.


  - Чтобы настроить Exchange ActiveSync, выполните следующую команду.
    ```powershell
        Set-ActiveSyncVirtualDirectory -Identity "<CAS2013>\Microsoft-Server-ActiveSync (Default Web Site)" -ExternalUrl "https://mail.contoso.com/Microsoft-Server-ActiveSync"
	```
  - Чтобы настроить виртуальный каталог веб-служб Exchange, выполните следующую команду.
    ```powershell
        Set-WebServicesVirtualDirectory -Identity "<CAS2013>\EWS (Default Web Site)" -ExternalUrl https://mail.contoso.com/EWS/Exchange.asmx
	```
  - Чтобы настроить автономную адресную книгу, выполните следующую команду.
    ```powershell
        Set-OABVirtualDirectory -Identity "<CAS2013>\OAB (Default Web Site)" -ExternalUrl "https://mail.contoso.com/OAB"
	```
  - Чтобы настроить точку подключения службы, выполните следующую команду.
    ```powershell
        Set-ClientAccessServer -Identity <CAS2013> -AutoDiscoverServiceInternalURI https://autodiscover.contoso.com/AutoDiscover/AutoDiscover.xml
	```
## Обновление с клиентского доступа Exchange 2007 и 2010

Используйте этот раздел при настройке внешнего доступа к протоколам на сервере клиентского доступа Exchange 2013. Выполните команды с командной консоли Exchange при настройке виртуальных каталогов как в разделе выше, а также указанные ниже команды.

Чтобы настроить виртуальные каталоги для Exchange 2013, потребуется выполнить следующие команды.

1.  Для настройки внешнего URL-адреса для Outlook Web App выполните следующую команду в командной консоли Exchange.
    ```powershell
        Set-OwaVirtualDirectory "<CAS2013>\OWA (Default Web Site)" -ExternalUrl https://mail.contoso.com/OWA
    ```
    После настройки виртуального каталога Outlook Web App в командной строке выполните следующие команды.
    
	```powershell
	Net stop IISAdmin /y
	```
	```powershell
	Net start W3SVC
	```

2.  Чтобы настроить внешний доступ к Центру администрирования Exchange, выполните следующую команду в командной консоли Exchange.
    ```powershell
        Set-EcpVirtualDirectory "<CAS2013>\ECP (Default Web Site)" -ExternalUrl https://mail.contoso.com/ECP -InternalURL https://mail.contoso.com/ECP 
	```
3.  Чтобы настроить службу доступности, выполните следующую команду в командной консоли Exchange.
    ```powershell
        Set-WebServicesVirtualDirectory -Identity "<CAS2013>\EWS (Default Web Site)" -ExternalURL https://mail.contoso.com/EWS/Exchange.asmx
	```
Чтобы проверить, правильно ли настроен внешний URL-адрес для Exchange ActiveSync или Outlook Web App, можно воспользоваться Remote Connectivity Analyzer — бесплатным веб-средством, предоставляемым корпорацией Майкрософт. Remote Connectivity Analyzer вы найдете [здесь](http://go.microsoft.com/fwlink/?linkid=154308).

Проверить, правильно ли настроена проверка подлинности для Exchange ActiveSync или Outlook Web App, можно также с помощью ExRCA.

Чтобы проверить, правильно ли настроен прямой доступ к файлам для Outlook Web App, войдите в Outlook Web App с общедоступного компьютера в качестве пользователя и попытайтесь открыть и сохранить файл, вложенный в сообщение электронной почты.

## Настройка протоколов на серверах клиентского доступа Exchange 2007

Чтобы настроить виртуальные каталоги для Exchange 2007, потребуется выполнить следующие команды.

  - Чтобы настроить внешний URL-адрес на виртуальном каталоге Exchange ActiveSync, выполните следующую команду в командной консоли Exchange.
    ```powershell
        Set-ActiveSyncVirtualDirectory -Identity "<CAS2007>\Microsoft-Server-ActiveSync (Default Web Site)" -ExternalUrl https://mail.contoso.com/Microsoft-Server-ActiveSync
	```
  - Чтобы настроить внешний URL-адрес в виртуальном каталоге Outlook Web App, выполните приведенную ниже команду в командной консоли Exchange.
    ```powershell
        Set-OwaVirtualDirectory -Identity "<CAS2007>\owa (Default Web Site)" -ExternalUrl https://legacy.contoso.com/owa
	```
