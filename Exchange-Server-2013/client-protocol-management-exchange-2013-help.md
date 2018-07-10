---
title: 'Управление протоколом клиента: Exchange 2013 Help'
TOCTitle: Управление протоколом клиента
ms:assetid: 89ba6d24-d1d3-46d5-a0ae-61f0d4c6df21
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ657727(v=EXCHG.150)
ms:contentKeyID: 50488579
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Управление протоколом клиента

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Управление клиентскими протоколами ActiveSync, Outlook Web App, POP3, IMAP4, службы автообнаружения, веб-служб Exchange и службы доступности выполняется в три различных областях: центре администрирования Exchange (EAC), командной консоли Exchange и диспетчере Internet Information Services (IIS). Параметры, которые меняются в каждом месте, зависят от протокола.

## Управление Outlook Web App

Большинство параметров, которые влияют на возможности Outlook Web App, с которыми пользователи могут работать, задаются для виртуального каталога Outlook Web App или настраиваются в политике почтовых ящиков Outlook Web App. С помощью политик почтовых ящиков Outlook Web App можно указать функции, доступные для отдельных пользователей. Параметры политики почтовых ящиков переопределяют параметры виртуального каталога. Дополнительные сведения об управлении Outlook Web App см. в разделе [Outlook Web App](outlook-web-app-exchange-2013-help.md).

## Управление параметрами Exchange ActiveSync

В Exchange 2010 все протоколы клиентского доступа реализованы и контролируются в одном роли сервера — роли сервера клиентского доступа. Управление протоколами проводится на одном экземпляре IIS, где существует один виртуальный объект каталога в Active Directory для каждого клиентского протокола и один набор командлетов, используемых, чтобы настроить виртуальный каталог.

В Exchange 2013 управление клиентским протоколом Exchange ActiveSync разделяется между сервером клиентского доступа и сервером почтовых ящиков. Вследствие этого изменения архитектуры можно запускать разные задачи управления виртуальным каталогом на сервере клиентского доступа и сервере почтовых ящиков. Если эти два сервера не установлены на одном физическом компьютере, параметры, которые вы используете в командлетах виртуального каталога, будут меняться в зависимости от ролей сервера, на котором они выполняются.

Для получения дополнительных сведений об изменениях в архитектуре Exchange 2013 см. в разделе [Новые возможности в Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md).

Существует два типа параметров, применимых к виртуальным каталогам Exchange ActiveSync:

  - Параметры, применимые к сеансам почтового ящика

  - Параметры, применимые к серверу и виртуальному каталогу

Параметры, которые применяются для сеанса почтового ящика, это параметры сеанса пользователя. Когда пользователь подключается к серверу клиентского доступа, подключение передается через прокси-соединение серверу почтовых ящиков, на котором находится почтовый ящик пользователя. Уникальный идентификатор виртуального каталога включен в запрос через прокси. Затем сервер почтовых ящиков извлекает из Active Directory параметры виртуального каталога и применяет их к сеансу. Настройки виртуального каталога кэшируются на сервере почтовых ящиков, чтобы повысить производительность.

Если подключение будет передано на другой сайт Active Directory, параметры виртуального каталога будут загружаться из сервера клиентского доступа на том же сайте, что и сервер почтовых ящиков, а не из сервера клиентского доступа, где произошло подключение.

В нижеприведенных таблицах указаны параметры виртуального каталога и серверы, где ими можно управлять. При попытке изменения определенного параметра на сервере, для которого он не применим, будет выведено сообщение об ошибке, указывающее, что вы попытались задать для сервера свойство только для чтения.

**Параметры виртуального каталога Exchange ActiveSync на серверах клиентского доступа**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Сервер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>BadItemReportingEnabled</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>BasicAuthEnabled</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>ClientCertAuth</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>CompressionEnabled</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>ExternalAuthenticationMethods</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>ExternalURL</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>InternalAuthenticationMethods</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>InternalURL</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>MobileClientCertificateAuthorityURL</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>MobileClientCertificateProvisioningEnabled</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>MobileClientCertTemplateName</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>RemoteDocumentsActionForUnknownServers</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>RemoteDocumentsAllowedServers</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>RemoteDocumentsBlockedServers</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>RemoteDocumentsInternalDomainSuffixList</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>SendWatsonReport</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
</tbody>
</table>


**Параметры виртуального каталога Exchange ActiveSync на серверах клиентского доступа и почтовых ящиков**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Сервер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ApplicationRoot</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>AppPoolID</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>MetabasePath</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>Имя</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>Путь</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>ProxySubVdir</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>VirtualDirectoryName</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>WebsiteName</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
</tbody>
</table>


## Управление POP3 и IMAP4

В Exchange 2013 реализация POP3 и IMAP4 также была разделена между ролями сервера клиентского доступа и сервера почтовых ящиков. Из-за новой реализации подключения POP3 и IMAP4 контролируются службой на сервере клиентского доступа, а также на сервере почтовых ящиков. Имена служб, которые выполняются на сервере клиентского доступа, аналогичны именам в Exchange 2010: служба Microsoft Exchange IMAP4 и служба Microsoft Exchange POP3. Имена двух новых служб, которые запускаются на сервере почтовых ящиков, — это фоновая служба IMAP4 Microsoft Exchange и фоновая служба Microsoft Exchange POP3.

Учтите советы ниже, управляя подключениями POP3 и IMAP4 в организации:

  - Если роль сервера клиентского доступа и роль сервера почтовых ящиков находятся на одном и том же компьютере, любые изменения параметров IMAP4 или POP3 автоматически применяются к нужной службе POP3 и IMAP4.

  - Если роль сервера клиентского доступа и роль сервера почтовых ящиков находятся на разных компьютерах, необходимо управлять параметрами на компьютере, контролирующем параметр, который требуется изменить.

Нижеприведенные таблицы указывают, какие параметры POP и IMAP относятся к каждой роли сервера.

**Параметры POP3 и IMAP4 на сервере клиентского доступа**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Сервер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AuthenticatedConnectionTimeout</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>Banner</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>ExternalConnectionSettings</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>InternalConnectionSettings</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>MaxCommandSize</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>MaxConnectionFromSingleIP</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>MaxConnections</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>MaxConnectionsPerUser</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="odd">
<td><p>PreAuthenticatedConnectionTimeout</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
<tr class="even">
<td><p>UnencryptedOrTLSBindings</p></td>
<td><p>Клиентский доступ</p></td>
</tr>
</tbody>
</table>


**Параметры POP3 и IMAP4 на сервере почтовых ящиков**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Сервер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CalendarItemRetrivalOption</p></td>
<td><p>Сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>EnableExactRFC822Size</p></td>
<td><p>Сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>MessageRetrievalSortOrder</p></td>
<td><p>Сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>OWAServerURL</p></td>
<td><p>Сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>ProxyTargetPort</p></td>
<td><p>Сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>ShowHiddenFoldersEnabled</p></td>
<td><p>Сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>SuppressReadReceipt</p></td>
<td><p>Сервер почтовых ящиков</p></td>
</tr>
</tbody>
</table>


**Параметры POP3 и IMAP4 на серверах клиентского доступа и почтовых ящиков**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Сервер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>X509CertificateName</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>EnforceCertificateErrors</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>LogFileLocation</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>LogFileRolloverSettings</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>LoginType</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>LogPerFileSizeQuota</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>ProotocolLogEnabled</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="even">
<td><p>Сервер</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
<tr class="odd">
<td><p>X509CertificateName</p></td>
<td><p>Сервер клиентского доступа, сервер почтовых ящиков</p></td>
</tr>
</tbody>
</table>

