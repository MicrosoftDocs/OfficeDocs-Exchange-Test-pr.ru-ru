---
title: 'Краткий справочник по командной консоли Exchange для Exchange 2013: Exchange 2013 Help'
TOCTitle: Краткий справочник по командной консоли Exchange для Exchange 2013
ms:assetid: 3ea4a105-a93c-48ba-96ce-6170125354e1
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ619302(v=EXCHG.150)
ms:contentKeyID: 50487876
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Краткий справочник по командной консоли Exchange для Exchange 2013

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-03-09_

В этом разделе описаны наиболее часто применяемые командлеты, доступные в окончательной первоначальной версии (RTM) и более поздних версиях Microsoft Exchange Server 2013, а также приведены примеры их использования.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Скоро будет добавлено дополнительное содержимое о других аспектах использования Exchange 2013.</td>
</tr>
</tbody>
</table>


Дополнительные сведения о командной консоли Exchange в Exchange 2013 и доступных командлетах см. в следующих разделах:

  - [Использование Powershell с Exchange 2013 (командная консоль Exchange)](https://technet.microsoft.com/ru-ru/library/bb123778\(v=exchg.150\))

  - [Командлеты Exchange 2013](https://technet.microsoft.com/ru-ru/library/bb124413\(v=exchg.150\))

## О чем бы вы хотели узнать?

## Типовые действия командлетов

Следующие команды поддерживаются большинством командлетов и связаны с конкретным действием.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Создать</p></td>
<td><p>Команда New создает новый экземпляр чего-либо, например новый параметр настройки, новую базу данных или новый соединитель SMTP.</p></td>
</tr>
<tr class="even">
<td><p>Удалить</p></td>
<td><p>Команда Remove удаляет экземпляр чего-либо, например почтовый ящик или правило транспорта.</p>
<p>Все командлеты Remove поддерживают параметры <em>WhatIf</em> и <em>Confirm</em>. Дополнительные сведения об этих параметрах приведены в разделе Important Parameters.</p></td>
</tr>
<tr class="odd">
<td><p>Задействовать</p></td>
<td><p>Команда Enable включает параметр или поддержку почты для получателя.</p></td>
</tr>
<tr class="even">
<td><p>Запретить</p></td>
<td><p>Команда Disable отключает включенный параметр или поддержку почты для получателя.</p>
<p>Все задачи Disable также обеспечивают поддержку параметров <em>WhatIf</em> и <em>Confirm</em>. Дополнительные сведения об этих параметрах приведены в разделе Important Parameters.</p></td>
</tr>
<tr class="odd">
<td><p>Set</p></td>
<td><p>Команда Set изменяет конкретные параметры объекта, например псевдоним контакта или хранение удаленных элементов базы данных почтовых ящиков.</p></td>
</tr>
<tr class="even">
<td><p>Get</p></td>
<td><p>Команда Get запрашивает конкретный объект или подмножество типа объекта, таких как конкретный почтовый ящик, все пользователи почтовых ящиков или пользователей почтовых ящиков в домене.</p></td>
</tr>
</tbody>
</table>


## Важные параметры

Нижеприведенные параметры помогают управлять выполнением команд и точно показывают, какие действия выполнит команда, прежде чем она повлияет на данные.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Удостоверение</p></td>
<td><p>Параметр <em>Identity</em> определяет уникальный объект для задачи. Он обычно используется с командлетами Enable, Disable, Remove, Set и Get. Параметр <em>Identity</em> также является позиционным — это значит, что необязательно указывать имя <em>Identity</em>, указывая значение данного параметра в командной строке.</p>
<p>Допустим, <em>Get-Mailbox -Identity user1</em> запрашивает почтовый ящик пользователя <em>user1</em>. Командлет <em>Get-Mailbox user1</em> эквивалентен командлету <em>Get-Mailbox -Identity user1</em>.</p></td>
</tr>
<tr class="even">
<td><p>WhatIf</p></td>
<td><p>Параметр <em>WhatIf</em> указывает командлету на необходимость имитировать действия, которые будут выполняться над объектом. С помощью параметра <em>WhatIf</em> можно просмотреть возможные изменения без реального применения любого из этих изменений. По умолчанию установлено значение <em>$true</em>.</p></td>
</tr>
<tr class="odd">
<td><p>Confirm</p></td>
<td><p>Параметр <em>Confirm</em> используется для приостановки выполнения обработки командлетом и для ее продолжения требует подтверждения администратором дальнейших действий командлета. По умолчанию установлено значение <em>$true</em>.</p></td>
</tr>
<tr class="even">
<td><p>Проверка</p></td>
<td><p>Параметр <em>Validate</em> заставляет командлет проверить, что все требования, необходимые для выполнения операции, выполняются и что операция закончится успешно.</p></td>
</tr>
</tbody>
</table>


## Советы и рекомендации

Следующие команды связаны с различными задачами администрирования Exchange 2013.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Get-Command</p></td>
<td><p>Этот командлет возвращает все задачи, которые могут быть выполнены в Exchange 2013.</p></td>
</tr>
<tr class="even">
<td><p>Get-Command *<em>ключевое_слово</em>*</p></td>
<td><p>Этот командлет возвращает задачи, в командлете которых содержится <em>ключевое_слово</em>.</p></td>
</tr>
<tr class="odd">
<td><p>Get-<em>задача</em> | Get-Member</p></td>
<td><p>Этот командлет возвращает все свойства и методы задачи <em>задача</em>.</p></td>
</tr>
<tr class="even">
<td><p>Get-<em>задача</em> | Format-List</p></td>
<td><p>Этот командлет выводит результат запроса в виде форматированного списка. Результат любого командлета Get можно направить на вход командлета Format-List, что позволяет просмотреть весь набор имеющихся свойств объекта, возвращенных этой командой. Также можно указать конкретные свойства, которые нужно просмотреть, разделяя их запятыми, как в следующем примере: <em>Get-Mailbox *john* | Format-List alias,*quota</em></p></td>
</tr>
<tr class="odd">
<td><p>Help <em>задача</em></p></td>
<td><p>Этот командлет возвращает справочные сведения командной консоли Exchange Exchange для любой задачи в Exchange 2013, как в следующем примере: <em>Help Get-Mailbox</em></p></td>
</tr>
<tr class="even">
<td><p>Get-<em>задача</em> | Format-List &gt; <em>file.txt</em></p></td>
<td><p>Этот командлет выводит результат задачи <em>задача</em> в текстовый файл: <em>file.txt</em></p></td>
</tr>
</tbody>
</table>


## Разрешения


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Get-RoleGroupMember &quot;<em>Organization Management</em>&quot;</p></td>
<td><p>Эта команда возвращает список членов группы ролей управления <em>Organization Management</em>.</p></td>
</tr>
<tr class="even">
<td><p>Get-ManagementRoleAssignment -Role &quot;<em>Mail Recipient Creation</em>&quot; -GetEffectiveUsers</p></td>
<td><p>Эта команда извлекает список пользователей, которым предоставлены разрешения роли управления <em>Mail Recipient Creation</em>. Сюда относятся пользователи, входящие в группы ролей или универсальные группы безопасности, которым назначена эта роль. Сюда не входят пользователи, входящие в связанные группы ролей из другого леса.</p></td>
</tr>
<tr class="odd">
<td><p>Get-ManagementRoleAssignment -RoleAssignee <em>Administrator</em> | Get-ManagementRole | Get-ManagementRoleEntry</p></td>
<td><p>Эта команда извлекает список командлетов, которые может запускать пользователь <em>Administrator</em>.</p></td>
</tr>
<tr class="even">
<td><p>ForEach ($RoleEntry in Get-ManagementRoleEntry *\<em>Remove-Mailbox</em> -parameters Identity) {Get-ManagementRoleAssignment -Role $RoleEntry.Role -GetEffectiveUsers -Delegating $False | Where-Object {$_.EffectiveUserName -Ne &quot;All Group Members&quot;} | FL Role, EffectiveUserName, AssignmentChain}</p></td>
<td><p>Эта команда извлекает список пользователей, которые могут запускать командлет <em>Remove-Mailbox</em>.</p></td>
</tr>
<tr class="odd">
<td><p>Get-ManagementRoleAssignment -WritableRecipient <em>kima</em> -GetEffectiveUsers | FT RoleAssigneeName, EffectiveUserName, Role, AssignmentChain</p></td>
<td><p>Эта команда извлекает список пользователей, которые могут изменять почтовый ящик <em>kima</em>.</p></td>
</tr>
<tr class="even">
<td><p>New-ManagementScope &quot;<em>Seattle Users</em>&quot; -RecipientRestrictionFilter { <em>City</em> -Eq &quot;<em>Seattle</em>&quot; }</p>
<p>New-RoleGroup &quot;<em>Seattle Admins</em>&quot; -Roles &quot;<em>Mail Recipients</em>&quot;, &quot;<em>Mail Recipient Creation</em>&quot;, &quot;<em>Mailbox Import Export</em>&quot;, -CustomRecipientWriteScope &quot;<em>Seattle Users</em>&quot;</p></td>
<td><p>Эта команда создает новую область управления и группу ролей управления, чтобы позволить членам группы ролей управлять получателями в Сиэтле.</p>
<p>Сначала создается область управления <em>Seattle Users</em>, в которую входят только те получатели, у которых в атрибуте <em>City</em> объекта-пользователя имеется значение <em>Seattle</em>.</p>
<p>Затем создается новая группа ролей <em>Seattle Admins</em>, которой назначаются роли <em>Mail Recipients</em>, <em>Mail Recipient Creation</em> и <em>Mailbox Import Export</em>. Группа ролей привязывается к области, поэтому ее члены смогут управлять только пользователями, попадающими в область фильтрации получателей <em>Seattle Users</em>.</p></td>
</tr>
<tr class="odd">
<td><p>New-ManagementScope &quot;<em>Vancouver Servers</em>&quot; -ServerRestrictionFilter { <em>ServerSite</em> -Eq &quot;<em>Vancouver</em>&quot; }</p>
<p>$RoleGroup = Get-RoleGroup &quot;<em>Server Management</em>&quot;</p>
<p>New-RoleGroup &quot;<em>Vancouver Server Management</em>&quot; -Roles $RoleGroup.Roles -CustomConfigWriteScope &quot;<em>Vancouver Servers</em>&quot;</p></td>
<td><p>Эта команда создает новую область управления и копирует существующую группу ролей, чтобы позволить членам новой группы ролей управлять только серверами из сайта Active Directory в Ванкувере.</p>
<p>Сначала создается область управления <em>Vancouver Servers</em>, в которую входят только серверы, расположенные в сайте Active Directory <em>Vancouver</em>. Сайт Active Directory указывается в атрибуте <em>ServerSite</em> объектов-серверов.</p>
<p>Затем создается новая группа ролей <em>Vancouver Server Management</em>, представляющая собой копию группы ролей <em>Server Management</em>. Новая группа ролей привязывается к области, поэтому ее члены смогут управлять только серверами, попадающими в область фильтрации конфигурации <em>Vancouver Servers</em>.</p></td>
</tr>
<tr class="even">
<td><p>Add-RoleGroupMember &quot;<em>Organization Management</em>&quot; -Member <em>davids</em></p></td>
<td><p>Эта команда добавляет пользователя <em>davids</em> в группу ролей <em>Organization Management</em>.</p></td>
</tr>
<tr class="odd">
<td><p>Get-ManagementRoleAssignment -Role &quot;<em>Mail Recipient Creation</em>&quot; -RoleAssignee &quot;<em>Seattle Admins</em>&quot; | Remove-ManagementRoleAssignment</p></td>
<td><p>Эта команда удаляет роль <em>Mail Recipient Creation</em> из группы ролей <em>Seattle Admins</em>. Эта команда полезна, поскольку в ней не требуется знать имя назначения роли управления, связывающего роль с группой ролей.</p></td>
</tr>
</tbody>
</table>


## Удаленная командная консоль Exchange


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://<em>ExServer.contoso.com</em>/PowerShell/ -Authentication Kerberos</p>
<p>Import-PSSession $Session</p></td>
<td><p>Эти команды открывают новый удаленный сеанс консоли между локальным компьютером, включенным в домен, и удаленным сервером Exchange 2013 с полным доменным именем <em>ExServer.contoso.com</em>. Используйте эту команду при необходимости администрирования удаленного сервера Exchange 2013 в случае, если на локальном компьютере доступна только платформа Windows Management Framework, в которую входит интерфейс командной строки Windows PowerShell. Эта команда использует для подключения к удаленному серверу Exchange 2013 учетные данные текущего сеанса в системе.</p></td>
</tr>
<tr class="even">
<td><p>$UserCredential = Get-Credential</p>
<p>$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://<em>ExServer.contoso.com</em>/PowerShell/ -Authentication Kerberos -Credential $UserCredential</p>
<p>Import-PSSession $Session</p></td>
<td><p>Эти команды открывают новый удаленный сеанс консоли между локальным компьютером, включенным в домен, и удаленным сервером Exchange 2013 с полным доменным именем <em>ExServer.contoso.com</em>. Используйте эту команду при необходимости администрирования удаленного сервера Exchange 2013 в случае, если на локальном компьютере доступна только платформа Windows Management Framework, в которую входит среда Windows PowerShell. Эта команда использует для подключения к удаленному серверу Exchange 2013 явно указываемые учетные данные.</p></td>
</tr>
<tr class="odd">
<td><p>Remove-PSSession $Session</p></td>
<td><p>Эта команда закрывает удаленный сеанс консоли между локальным компьютером и удаленным сервером Exchange 2013.</p></td>
</tr>
<tr class="even">
<td><p>Import-RecipientDataProperty -Identity &quot;Tony Smith&quot; -SpokenName -FileData <em>([Byte[]]$(Get-Content -Path &quot;M:\AudioFiles\TonySmith.wma&quot; -Encoding Byte -ReadCount 0))</em></p></td>
<td><p>Эта команда служит примером синтаксиса (выделенного курсивом), необходимого для импорта файла на удаленный сервер Exchange 2013 с использованием параметра FileData в командлете. Синтаксис инкапсулирует данные, содержащиеся в файле <em>M:\AudioFiles\TonySmith.wma</em>, и передает их в потоковом режиме в свойство FileData командлета Import-RecipientDataProperty.</p>
<p>Параметр FileData принимает данные из файла на локальном компьютере при использовании данного синтаксиса в большинстве командлетов.</p></td>
</tr>
<tr class="odd">
<td><p>Export-RecipientDataProperty -Identity tony@contoso.com -SpokenName <em>| ForEach { $_.FileData | Add-Content C:\tonysmith.wma -Encoding Byte}</em></p></td>
<td><p>Эта команда служит примером синтаксиса (выделенного курсивом), необходимого для экспорта файла с удаленного сервера Exchange 2013. Синтаксис инкапсулирует данные, хранящиеся в свойстве FileData объекта, возвращаемого командлетом, и передает эти данные в потоковом режиме на локальный компьютер. Затем данные сохраняются в файле <em>C:\tonysmith.wma</em>.</p>
<p>Большинство командлетов, возвращающих объекты со свойством FileData, используют этот синтаксис для экспорта данных в файлы на локальном компьютере.</p></td>
</tr>
</tbody>
</table>

