---
title: 'Включение поддержки устаревших агентов транспорта: Exchange 2013 Help'
TOCTitle: Включение поддержки устаревших агентов транспорта
ms:assetid: 00617e87-7199-406e-b4a3-94378f657f1f
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ591524(v=EXCHG.150)
ms:contentKeyID: 50487336
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Включение поддержки устаревших агентов транспорта

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

В Microsoft Exchange Server 2013 агенты транспорта, созданные с помощью Microsoft .NET Framework 4.0, поддерживаются по умолчанию. Exchange 2013 поддерживает агенты транспорта, созданные с помощью предыдущих версий Microsoft .NET Framework, но поддержка устаревших агентов транспорта не включена по умолчанию. Чтобы включить поддержку устаревших агентов транспорта, необходимо изменить соответствующий файл XML конфигурации приложения. То, какие файлы необходимо изменить, зависит от того, где установлен агент.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Сервер</th>
<th>Файлы конфигурации приложений</th>
<th>Служба Microsoft Windows</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Сервер клиентского доступа</p></td>
<td><p>%ExchangeInstallPath%Bin\MSExchangeFrontendTransport.exe.config</p></td>
<td><p>Транспорт внешнего интерфейса Microsoft Exchange (MSExchangeFrontendTransport)</p></td>
</tr>
<tr class="even">
<td><p>Сервер почтовых ящиков</p></td>
<td><ul>
<li><p>%ExchangeInstallPath%Bin\EdgeTransport.exe.config</p></li>
<li><p>%ExchangeInstallPath%Bin\MSExchangeTransport.exe.config</p></li>
</ul></td>
<td><p>Служба транспорта Microsoft Exchange (MSExchangeTransport)</p></td>
</tr>
</tbody>
</table>


Поддержка устаревших агентов транспорта контролируется ключами в файлах конфигурации приложения. По умолчанию файлы конфигурации приложения не содержат этих ключей. Их необходимо добавить вручную. В следующей таблице каждый ключ рассматривается более подробно.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Клавиша</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>useLegacyV2RuntimeActivationPolicy</em></p></td>
<td><p>Этот ключ включает или отключает поддержку устаревших агентов транспорта. Для этого ключа допустимы значения <code>true</code> или <code>false</code>. Если этот ключ не указан, значение по умолчанию — <code>false</code>.</p></td>
</tr>
<tr class="even">
<td><p><em>supportedRuntime version</em></p></td>
<td><p>Этот ключ указывает версию Microsoft .NET Framework, требуемую агентом. Допустимые значения этого ключа:</p>
<ul>
<li><p><code>v4.0</code> или <code>v4.0.30319</code></p></li>
<li><p><code>v3.5</code> или <code>v3.5.21022</code></p></li>
<li><p><code>v3.0</code> или <code>v3.0.4506</code></p></li>
<li><p><code>v2.0</code> или <code>v2.0.50727</code></p></li>
</ul>
<p>Вы можете указать несколько значений с помощью нескольких отдельных экземпляров ключа <em>supportedRuntime version</em>.</p>
<p>При включении поддержки устаревших агентов транспорта с помощью ключа <em>useLegacyV2RuntimeActivationPolicy</em> необходимо всегда указывать значение <code>v4.0</code> помимо значений, требуемых устаревшим агентом транспорта.</p></td>
</tr>
</tbody>
</table>


## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 15 минут.

  - Разрешения Exchange не применяются к процедурам, описанным в этом разделе. Эти процедуры выполняются в операционной системе сервера Exchange.

  - Изменения, сохраненные в файле конфигурации приложения, применяются после перезапуска соответствующей службы.

  - При перезапуске любой из служб, связанных с файлами конфигурации приложения, поток обработки почты на сервере временно прерывается.

  - Все специальные настройки, выполненные для каждого сервера в XML-файлах конфигурации приложения Exchange, например в файлах web.config на серверах клиентского доступа или файлах EdgeTransport.exe.config на серверах почтовых ящиков, будут перезаписаны после установки накопительного пакета обновления Exchange. Обязательно сохраните нужные данные, чтобы упростить перенастройку сервера после установки. Эти параметры необходимо перенастроить после установки накопительного пакета обновления Exchange.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Настройка поддержки устаревших агентов транспорта с помощью командной строки

Чтобы включить поддержку устаревших агентов транспорта, сделайте следующее:

1.  В окне командной строки на сервере Exchange 2013, где требуется настроить поддержу устаревших агентов транспорта, откройте в Блокноте соответствующий файл конфигурации приложения с помощью следующей команды:
    
```powershell
Notepad %ExchangeInstallPath%Bin\<AppConfigFile>
```
    
Например, чтобы открыть файл EdgeTransport.exe.config на сервере почтовых ящиков, выполните следующую команду:
    
```powershell
Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config
```

2.  Найдите ключ *\</configuration\>* в конце файла и вставьте следующие ключи перед ключом *\</configuration\>*:
    
```powershell
<startup useLegacyV2RuntimeActivationPolicy="true">
        <supportedRuntime version="v4.0" />
        <supportedRuntime version="v3.5" />
        <supportedRuntime version="v3.0" />
        <supportedRuntime version="v2.0" />
</startup>
```

3.  По завершении сохраните и закройте файл конфигурации приложения.

4.  Повторите шаги с 1 по 3, чтобы изменить остальные файлы конфигурации приложения.

5.  Перезапустите связанную службу Windows, выполнив следующую команду:
    
```powershell
net stop <service> && net start <service>
```
    
Например, если изменения были внесены в файл EdgeTransport.exe.config, перезапустите службу транспорта Microsoft Exchange, выполнив следующую команду:
    
```powershell
net stop MSExchangeTransport && net start MSExchangeTransport
```

6.  Повторите шаг 5, чтобы перезапустить службы, связанные с остальными измененными файлами конфигурации приложения.

## Как проверить, что все получилось?

Если удалось успешно установить устаревший агент транспорта, значит, все получилось. При попытке установить устаревший агент транспорта без выполнения процедур, описанных в этой статье, возникнет ошибка, например:

```powershell
Mixed mode assembly is built against version '<version>' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.
```

