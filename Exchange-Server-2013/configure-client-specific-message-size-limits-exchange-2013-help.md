---
title: 'Настройка ограничений размера сообщений для определенного клиента: Exchange 2013 Help'
TOCTitle: Настройка ограничений размера сообщений для определенного клиента
ms:assetid: fef9ca78-b68f-4342-ada0-881ab985ce3c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh529949(v=EXCHG.150)
ms:contentKeyID: 52061291
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка ограничений размера сообщений для определенного клиента

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2017-01-26_

В Microsoft Exchange Server 2013 есть несколько различных ограничений размера сообщения, которые применяются к сообщениям по мере прохождения в организации Exchange. Подробнее см. в разделе [Ограничения на размер сообщений](message-size-limits-exchange-2013-help.md).

Однако существуют ограничения на размер сообщений, касающиеся определенных клиентов, которые вы можете настроить для Outlook Web App и почтовых клиентов, использующих ActiveSync или веб-службы Exchange. Если вы измените ограничения на размер сообщений для всей организации Exchange, убедитесь, что для Outlook Web App, ActiveSync и веб-служб Exchange заданы соответствующие ограничения. Эти значения настраиваются в файлах web.config на серверах клиентского доступа и серверах почтовых ящиков. Эти ограничения указаны в приведенных ниже таблицах.

### ActiveSync

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Роль сервера</th>
<th>Файл конфигурации</th>
<th>Ключи и значения по умолчанию</th>
<th>Размер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Клиентский доступ</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\Sync\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;30000000 bytes&quot;</code> (отсутствует по умолчанию, см. комментарии)</p></td>
<td><p>В байтах</p></td>
</tr>
<tr class="even">
<td><p>Клиентский доступ</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\Sync\web.config</code></p></td>
<td><p><code>maxRequestLength=&quot;10240&quot;</code></p></td>
<td><p>В килобайтах</p></td>
</tr>
<tr class="odd">
<td><p>Почтовый ящик</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Sync\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;30000000 bytes&quot;</code> (отсутствует по умолчанию, см. комментарии)</p></td>
<td><p>В байтах</p></td>
</tr>
<tr class="even">
<td><p>Почтовый ящик</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Sync\web.config</code></p></td>
<td><p><code>maxRequestLength=&quot;10240&quot;</code></p></td>
<td><p>В килобайтах</p></td>
</tr>
<tr class="odd">
<td><p>Почтовый ящик</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Sync\web.config</code></p></td>
<td><p><code>&lt;add key=&quot;MaxDocumentDataSize&quot; value=&quot;10240000&quot;&gt;</code></p></td>
<td><p>В байтах</p></td>
</tr>
</tbody>
</table>


**Комментарии к ограничениям для ActiveSync**

По умолчанию в файлах `web.config` нет ключа *maxAllowedContentLength* для ActiveSync. Но на максимальный размер сообщения для ActiveSync влияет значение **maxAllowedContentLength**, которое применяется ко всем веб-сайтам на сервере. Значение по умолчанию — 30 000 000 байтов (30 МБ). Чтобы просмотреть эти значения для ActiveSync на серверах клиентского доступа и серверах почтовых ящиков в диспетчере IIS, выполните указанные ниже действия.

1.  Выполните одно из следующих действий:
    
      - На серверах клиентского доступа откройте **диспетчер IIS**, перейдите в раздел **Сайты** \> **Веб-сайт по умолчанию** и выберите пункт **Microsoft-Server-ActiveSync**.
    
      - На серверах почтовых ящиков откройте **диспетчер IIS**, перейдите в раздел **Сайты** \> **Тыловой сервер Exchange** и выберите пункт **Microsoft-Server-ActiveSync**.

2.  Убедитесь, что выбран пункт **Просмотр возможностей**, и дважды щелкните элемент **Редактор конфигураций** в разделе **Управление**.

3.  Щелкните стрелку раскрывающегося списка в поле **Раздел**, перейдите в раздел **system.webServer** \> **безопасность** и выберите пункт **requestFiltering**.

4.  В результатах разверните список **requestLimits**, после чего отобразится пункт **maxAllowedContentLength** и значение по умолчанию 30 000 000 (в байтах).

Чтобы изменить значение **maxAllowedContentLength**, введите новое значение в байтах и выберите элемент **Применить**. Необходимо изменить значение на серверах клиентского доступа и серверах почтовых ящиков. После изменения значения в диспетчере IIS новый ключ *maxAllowedContentLength* записывается в соответствующий файл `web.config` (`%ExchangeInstallPath%FrontEnd\HttpProxy\Sync\web.config` на серверах клиентского доступа и `%ExchangeInstallPath%ClientAccess\Sync\web.config` на серверах почтовых ящиков).

Чтобы изменить максимальный размер сообщения для клиентов ActiveSync, необходимо изменить значение *maxRequestLength* в файле `web.config` на серверах клиентского доступа и серверах почтовых ящиков, *MaxDocumentDataSize* в файле `web.config` на серверах почтовых ящиков и *maxAllowedContentLength* в диспетчере IIS на серверах клиентского доступа и серверах почтовых ящиков.

### веб\-службы Exchange

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Роль сервера</th>
<th>Файл конфигурации</th>
<th>Ключи и значения по умолчанию</th>
<th>Размер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Клиентский доступ</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\ews\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;67108864&quot;</code></p></td>
<td><p>В байтах</p></td>
</tr>
<tr class="even">
<td><p>Почтовый ящик</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\exchweb\ews\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;67108864&quot;</code></p></td>
<td><p>В байтах</p></td>
</tr>
<tr class="odd">
<td><p>Почтовый ящик</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\exchweb\ews\web.config</code></p></td>
<td><p>14 экземпляров <code>maxReceivedMessageSize=&quot;67108864&quot;</code></p></td>
<td><p>В байтах</p></td>
</tr>
</tbody>
</table>


**Комментарии к ограничениям для веб-служб Exchange**

  - Существует 14 отдельных экземпляров значения `maxReceivedMessageSize="67108864"`, которые соответствуют различным сочетаниям привязок (http и https) и методов проверки подлинности.

  - Чтобы изменить максимальный размер сообщения для клиентов веб-служб Exchange, необходимо изменить значение *maxAllowedContentLength* в обоих файлах `web.config` и всех 14 экземплярах `maxReceivedMessageSize="67108864"` в файле `web.config` на серверах почтовых ящиков.

  - В файле `web.config` на серверах почтовых ящиков также есть два экземпляра значения `maxReceivedMessageSize="1048576"` для привязок **UMLegacyMessageEncoderSoap11Element**, которые не нужно изменять.

  - *maxRequestLength* — это параметр ASP.NET, который есть в обоих файлах web.config, но не используется веб-службами Exchange, поэтому вам не нужно его изменять.

### Outlook Web App

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Роль сервера</th>
<th>Файл конфигурации</th>
<th>Ключи и значения по умолчанию</th>
<th>Размер</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Клиентский доступ</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\owa\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;35000000&quot;</code></p></td>
<td><p>В байтах</p></td>
</tr>
<tr class="even">
<td><p>Клиентский доступ</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\owa\web.config</code></p></td>
<td><p><code>maxRequestLength=&quot;35000&quot;</code></p></td>
<td><p>В килобайтах</p></td>
</tr>
<tr class="odd">
<td><p>Почтовый ящик</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Owa\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;35000000&quot;</code></p></td>
<td><p>В байтах</p></td>
</tr>
<tr class="even">
<td><p>Почтовый ящик</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Owa\web.config</code></p></td>
<td><p><code>maxRequestLength=&quot;35000&quot;</code></p></td>
<td><p>В килобайтах</p></td>
</tr>
<tr class="odd">
<td><p>Почтовый ящик</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Owa\web.config</code></p></td>
<td><p>2 экземпляра <code>maxReceivedMessageSize=&quot;35000000&quot;</code></p></td>
<td><p>В байтах</p></td>
</tr>
<tr class="even">
<td><p>Почтовый ящик</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Owa\web.config</code></p></td>
<td><p>2 экземпляра <code>maxStringContentLength=&quot;35000000&quot;</code></p></td>
<td><p>В байтах</p></td>
</tr>
</tbody>
</table>


**Комментарии к ограничениям для Outlook Web App**

  - В файле `web.config` на серверах почтовых ящиков есть два отдельных экземпляра значений `maxReceivedMessageSize="35000000"` и `maxStringContentLength="35000000"`, которые соответствуют привязкам http и https.

  - Чтобы изменить максимальный размер сообщения для клиентов Outlook Web App, необходимо изменить все эти значения в обоих файлах, включая оба экземпляра *maxReceivedMessageSize* и *maxStringContentLength* в файле `web.config` на серверах почтовых ящиков.

  - В файле `web.config` на серверах почтовых ящиков также имеется экземпляр значения `maxStringContentLength="102400"` для привязки **MsOnlineShellService**, который не нужно изменять.

Для всех ограничений размера сообщений необходимо задать значения, превышающие требуемый максимальный размер. Это необходимо, чтобы учесть неизбежное повышение размера сообщения после кодировки вложений и других двоичных данных в формате Base64. При кодировании Base64 размер сообщения увеличивается приблизительно на 33 %, поэтому указываемые ограничения размера сообщения приблизительно на 33 % больше фактически используемых размеров сообщения. Например, если вы укажите максимальный размер сообщения 64 МБ, реалистичный максимальный размер сообщения будет равен приблизительно 48 МБ.

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 15 минут.

  - Разрешения Exchange не применяются к процедурам, описанным в этом разделе. Эти процедуры выполняются в операционной системе сервера Exchange.

  - Изменения, сохраненные в файле конфигурации Web.config, применяются после перезапуска служб IIS.

  - Чтобы учитывать увеличение размера на 33 % при кодировании Base64, умножьте нужный максимальный размер в мегабайтах на 4/3. Чтобы преобразовать это значение в килобайты, умножьте его на 1024. Чтобы преобразовать значение в байты, умножьте его на 1048756 (1024\*1024). Обратите внимание, что увеличение размера из-за кодирования Base64 может превышать 33 % и зависит от нескольких факторов, например размера файла вложения, типа, сжатия и почтового клиента, используемого для создания и отправки сообщения.

  - Все специальные настройки, выполненные для каждого сервера в XML-файлах конфигурации приложения Exchange, например в файлах web.config на серверах клиентского доступа или файлах EdgeTransport.exe.config на серверах почтовых ящиков, будут перезаписаны после установки накопительного пакета обновления Exchange. Обязательно сохраните нужные данные, чтобы упростить перенастройку сервера после установки. Эти параметры необходимо перенастроить после установки накопительного пакета обновления Exchange.

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


## Настройка ограничения на размер сообщений для определенного клиента с помощью "Блокнота"

1.  Откройте соответствующие файлы web.config в "Блокноте". Например, чтобы открыть файлы web.config для клиентов веб-служб Exchange, выполните указанные ниже команды.
    
        Notepad %ExchangeInstallPath%ClientAccess\exchweb\ews\web.config
        Notepad %ExchangeInstallPath%FrontEnd\HttpProxy\ews\web.config

2.  Найдите нужные ключи в соответствующих файлах web.config, как описано в таблицах, приведенных выше. Например, для клиентов веб-служб Exchange найдите ключ *maxAllowedContentLength* в обоих файлах и все 14 экземпляров значения `maxReceivedMessageSize="67108864"` в файле `web.config` на серверах почтовых ящиков.
    
        <requestLimits maxAllowedContentLength="67108864" />
        ...maxReceivedMessageSize="67108864"...
    
    Чтобы установить максимальный размер сообщения после кодирования Base64 равным 64 МБ, измените все экземпляры `67108864` на `89478486` (64\*4/3\*1048756):
    
        <requestLimits maxAllowedContentLength="89478486" />
        ...maxReceivedMessageSize="89478486"...

3.  Закончив, сохраните и закройте файлы web.config.

4.  Перезапустите службы IIS, выполнив следующую команду:
    
        IISReset /noforce

## Настройка ограничений на размер сообщений для определенного клиента в командной строке

Настроить ограничения на размер сообщений для конкретных клиентов можно не только в "Блокноте", но и в командной строке. Откройте командную строку с повышенными привилегиями на сервере Exchange Server (используйте для этого команду **Запуск от имени администратора**) и выполните соответствующие команды для настройки нужных ограничений.

**Примечания.**

  - В командах указываются значения размера по умолчанию, потому вам нужно будет их изменить.

  - Обратите внимание на то, в каких единицах задано значение — в байтах или в килобайтах.

**ActiveSync**

    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/Microsoft-Server-ActiveSync/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:30000000
    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/Microsoft-Server-ActiveSync/" -section:system.web/httpRuntime /maxRequestLength:10240
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/Microsoft-Server-ActiveSync/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:30000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/Microsoft-Server-ActiveSync/" -section:system.web/httpRuntime /maxRequestLength:10240
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/Microsoft-Server-ActiveSync/" -section:appSettings /[key='MaxDocumentDataSize'].value:10240000

**веб-службы Exchange**

    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/ews/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSAnonymousHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSAnonymousHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSBasicHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSBasicHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSNegotiateHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSNegotiateHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecurityHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecurityHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecuritySymmetricKeyHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecuritySymmetricKeyHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecurityX509CertHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecurityX509CertHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /webHttpBinding.[name='EWSStreamingNegotiateHttpsBinding'].maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /webHttpBinding.[name='EWSStreamingNegotiateHttpBinding'].maxReceivedMessageSize:67108864

**Outlook Web App**

    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/owa/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/owa/" -section:system.web/httpRuntime /maxRequestLength:35000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.web/httpRuntime /maxRequestLength:35000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.serviceModel/bindings /webHttpBinding.[name='httpsBinding'].maxReceivedMessageSize:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.serviceModel/bindings /webHttpBinding.[name='httpBinding'].maxReceivedMessageSize:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.serviceModel/bindings /webHttpBinding.[name='httpsBinding'].readerQuotas.maxStringContentLength:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.serviceModel/bindings /webHttpBinding.[name='httpBinding'].readerQuotas.maxStringContentLength:35000000

## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно настроили ограничение размера сообщения для определенного клиента, отправьте тестовое сообщение в почтовый ящик, доступ к которому получает затронутый клиент, и получите тестовое сообщение из этого ящика. Вы можете использовать несколько небольших вложений или одно большое, чтобы тестовые сообщения были приблизительно на 33 % меньше заданного вами значения. Например, если указать значение 85 МБ, реалистичный максимальный размер сообщения будет равен приблизительно 64 МБ.

