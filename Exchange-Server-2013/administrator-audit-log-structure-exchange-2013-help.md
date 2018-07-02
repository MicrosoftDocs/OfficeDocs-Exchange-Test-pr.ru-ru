---
title: 'Структура журнала аудита администратора: Exchange 2013 Help'
TOCTitle: Структура журнала аудита администратора
ms:assetid: 87e259c9-c884-4d53-bd78-d13f2300d73e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff459251(v=EXCHG.150)
ms:contentKeyID: 50556405
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Структура журнала аудита администратора

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

В журналах аудита администратора содержатся записи всех командлетов и параметров, которые запускались в командной консоли Exchange и центра администрирования Exchange (EAC). Они создаются по требованию, когда выполняется отчет аудита администраторов в центре администрирования Exchange или запускается командлет **New-AdminAuditLogSearch** в командной консоли. Дополнительные сведения о журналах аудита см. в разделе [Ведение журнала аудита администратора](administrator-audit-logging-exchange-2013-help.md).

Журналы аудита хранятся в файлах XML и могут содержать записи нескольких журналов. В следующей таблице описаны все теги XML и связанные с ними атрибуты.

Необходимы сведения о задачах управления, связанных с журналами аудита администраторов? См. раздел [Управление ведением журнала аудита администраторов](manage-administrator-audit-logging-exchange-2013-help.md).

### Теги XML и атрибуты журнала аудита

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Элемент</th>
<th>Атрибут</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;</code></p>
<p></p></td>
<td><p><code>N/A</code></p></td>
<td><p>Это тег объявления документа XML. Он включается в каждый файл XML журнала аудита и содержит номер версии XML и значение типа кодировки символов.</p></td>
</tr>
<tr class="even">
<td><p><code>SearchResults</code></p></td>
<td><p><code>N/A</code></p></td>
<td><p>В этом теге содержатся все записи журнала аудита в файле XML. Тег <code>Event</code> является дочерним для этого тега.</p>
<p>В файле XML имеется только один тег <code>SearchResults</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code>Event</code></p></td>
<td><p><code> </code></p></td>
<td><p>В этом теге содержится запись журнала аудита для отдельного командлета. В этом теге содержатся атрибуты <code>Caller</code>, <code>Cmdlet</code>, <code>ObjectModified</code>, <code>RunDate</code>, <code>Succeeded</code>, <code>Error</code> и <code>OriginatingServer</code>. Теги <code>CmdletParameters</code> и <code>ModifiedProperties</code> являются дочерними по отношению к этому тегу.</p>
<p>В каждой записи журнала аудита имеется один тег <code>Event</code>.</p></td>
</tr>
<tr class="even">
<td><p><code> </code></p></td>
<td><p><code>Caller</code></p></td>
<td><p>В этом атрибуте содержится учетная запись пользователя, запустившего командлет, указанный в атрибуте <code>Cmdlet</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code> </code></p></td>
<td><p><code>Cmdlet</code></p></td>
<td><p>В этом атрибуте содержится имя командлета, запущенного пользователем, указанным в атрибуте <code>Caller</code>.</p></td>
</tr>
<tr class="even">
<td><p><code> </code></p></td>
<td><p><code>ObjectModified</code></p></td>
<td><p>В этом атрибуте содержится объект, измененный с помощью командлета, указанного в атрибуте <code>Cmdlet</code>. Тег <code>ModifiedProperties</code> показывает, какие свойства данного объекта были изменены.</p></td>
</tr>
<tr class="odd">
<td><p><code> </code></p></td>
<td><p><code>RunDate</code></p></td>
<td><p>В этом атрибуте содержатся дата и время выполнения командлета, указанного в атрибуте <code>Cmdlet</code>.</p></td>
</tr>
<tr class="even">
<td><p><code> </code></p></td>
<td><p><code>Succeeded</code></p></td>
<td><p>Этот атрибут указывает, был ли успешно выполнен командлет, указанный в атрибуте <code>Cmdlet</code>. Значение может быть равно <code>True</code> или <code>False</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code> </code></p></td>
<td><p><code>Error</code></p></td>
<td><p>В этом атрибуте содержится сообщение об ошибке, которое создается при сбое выполнения командлета, указанного в атрибуте <code>Cmdlet</code>. Если ошибка не обнаружена, то значение равно <code>None</code>.</p></td>
</tr>
<tr class="even">
<td><p><code> </code></p></td>
<td><p><code>OriginatingServer</code></p></td>
<td><p>Этот атрибут содержит сервер, на котором запускается командлет, указанный в атрибуте <code>Cmdlet</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code>CmdletParameters</code></p></td>
<td><p><code>N/A</code></p></td>
<td><p>В этом теге содержатся все параметры, заданные при запуске командлета. Тег <code>Parameter</code> является дочерним для этого тега.</p>
<p>Имеется один тег <code>CmdletParameters</code> на каждый тег <code>Event</code>.</p></td>
</tr>
<tr class="even">
<td><p><code>Parameter</code></p></td>
<td><p><code> </code></p></td>
<td><p>В этом теге содержится отдельный параметр, заданный при запуске командлета. В этом теге содержатся атрибуты <code>Name</code> и <code>Value</code>.</p>
<p>Может существовать несколько тегов <code>Parameter</code> на каждый тег <code>CmdletParameters</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code> </code></p></td>
<td><p><code>Name</code></p></td>
<td><p>В этом атрибуте содержится имя параметра, заданного в командлете при его запуске.</p></td>
</tr>
<tr class="even">
<td><p><code> </code></p></td>
<td><p><code>Value</code></p></td>
<td><p>В этом атрибуте содержится значение, заданное для параметра, который указан в атрибуте <code>Name</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code>ModifiedProperties</code></p></td>
<td><p><code>N/A</code></p></td>
<td><p>В этом теге содержатся все свойства, которые были изменены в результате выполнения командлета. Тег <code>Property</code> является дочерним для этого тега.</p>
<p>Имеется один тег <code>ModifiedProperties</code> на каждый тег <code>Event</code>.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Этот тег заполняется, только если параметр <em>LogLevel</em> командлета <strong>Set-AdminAuditLogConfig</strong> равен <code>Verbose</code>.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="even">
<td><p><code>Property</code></p></td>
<td><p><code> </code></p></td>
<td><p>В этом теге содержится отдельное свойство, заданное при запуске командлета. В этом теге содержатся атрибуты <code>Name</code>, <code>OldValue</code> и <code>NewValue</code>.</p>
<p>Может существовать несколько тегов <code>Property</code> на каждый тег <code>ModifiedProperties</code>.</p></td>
</tr>
<tr class="odd">
<td><p><code> </code></p></td>
<td><p><code>Name</code></p></td>
<td><p>В этом атрибуте содержится имя свойства, измененного в результате выполнения командлета.</p></td>
</tr>
<tr class="even">
<td><p><code> </code></p></td>
<td><p><code>OldValue</code></p></td>
<td><p>В этом атрибуте содержится значение, которое содержалось в свойстве, указанном в атрибуте <code>Name</code>, до изменения этого свойства.</p></td>
</tr>
<tr class="odd">
<td><p><code> </code></p></td>
<td><p><code>NewValue</code></p></td>
<td><p>В этом атрибуте содержится значение, на которое было изменено свойство, указанное в атрибуте <code>Name</code>.</p></td>
</tr>
</tbody>
</table>


## Пример записи в журнале аудита

Ниже приведен пример типичной записи журнала аудита. На основе данных в записи журнала можно сказать, что произошло следующее:

  - 18.10.2012 в 15:48 (UTC-7) пользователь `Administrator` запустил командлет **Set-Mailbox**.

  - При запуске командлета **Set-Mailbox** было задано два следующих параметра:
    
      - *Identity* со значением `david`
    
      - *ProhibitSendReceiveQuota* со значением `10GB`

  - Были изменены два следующих свойства объекта `david`:
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Измененные свойства сохраняются в журнале аудита, поскольку параметр <em>LogLevel</em> командлета <code>Set-AdminAuditLogConfig</code> задан как <code>Verbose</code> в этом примере.</td>
    </tr>
    </tbody>
    </table>
    
      - *ProhibitSendReceiveQuota* с новым значением `10GB`, которым было заменено старое значение `35GB`

  - Операция успешно завершена без ошибок.

<!-- end list -->

    <?xml version="1.0" encoding="utf-8"?>
    <SearchResults>
    
      <Event Caller="corp.e15a.contoso.com/Users/Administrator" Cmdlet="Set-Mailbox" ObjectModified="corp.e15a.contoso.com/Users/david" RunDate="2012-10-18T15:48:15-07:00" Succeeded="true" Error="None" OriginatingServer="WIN8MBX (15.00.0516.032)">
        <CmdletParameters>
          <Parameter Name="Identity" Value="david" />
          <Parameter Name="ProhibitSendReceiveQuota" Value="10 GB (10,737,418,240 bytes)" />
        </CmdletParameters>
        <ModifiedProperties>
          <Property Name="ProhibitSendReceiveQuota" OldValue="35 GB (37,580,963,840 bytes)" NewValue="10 GB (10,737,418,240 bytes)" />
        </ModifiedProperties>
      </Event>
    </SearchResults>

