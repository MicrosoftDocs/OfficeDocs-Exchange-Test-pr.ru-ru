---
title: 'Общие сведения об областях ролей управления: Exchange 2013 Help'
TOCTitle: Общие сведения об областях ролей управления
ms:assetid: 24ed4a38-438a-4223-9f9c-5d4dea4b046b
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd335146(v=EXCHG.150)
ms:contentKeyID: 50487634
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Общие сведения об областях ролей управления

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-07_

*Области ролей управления* позволяют задавать определенную область влияния роли управления при создании назначения роли управления. При применении области уполномоченный роли, которому назначается роль, может изменять только те объекты, которые находятся в пределах данной области. В качестве уполномоченного роли может выступать группа ролей управления, роль управления, политика назначения ролей управления, пользователь или универсальная группа безопасности. Дополнительные сведения о ролях управления см. в разделе [Общие сведения об управлении доступом на основе ролей](understanding-role-based-access-control-exchange-2013-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В этом разделе рассматриваются расширенные возможности управления доступом на основе ролей (RBAC). Сведения об управлении базовыми разрешениями Exchange 2013, такими как использование Центра администрирования Exchange для добавления и удаления участников групп ролей, создания и изменения групп ролей, а также создания и изменения политик назначения ролей, см. в разделе <a href="permissions-exchange-2013-help.md">Разрешения</a>.</td>
</tr>
</tbody>
</table>


Каждая роль управления, встроенная или настраиваемая, имеет области управления. Области управления делятся на следующие.

  - **Обычные***Обычная область* не является монопольной. Она определяет область Active Directory, объекты которой могут просматривать или изменять пользователи с назначенной ролью управления. Другими словами, роль управления определяет объекты, которые могут создавать или изменять пользователи, а область роли управления определяет пространство, в котором пользователи могут создавать или изменять эти объекты. Обычные области могут быть явными или неявными и будут рассматриваться подробнее далее в этом разделе.

  - **Монопольные***Монопольная область* действует практически так же, как и обычная область. Основное различие состоит в том, что с ее помощью можно запретить доступ пользователей к объектам, находящимся в пределах монопольной области, если им не назначена роль, сопоставленная с данной монопольной областью. Все монопольные области являются явными и рассматриваются далее в этом разделе.
    
    Дополнительные сведения о монопольных областях см. в разделе [Общие сведения об исключительных областях](understanding-exclusive-scopes-exchange-2013-help.md).

Области могут наследоваться из роли управления, указанной в качестве предварительно определенной относительной области для назначения роли управления, или создаваться с помощью пользовательских фильтров и добавляться в назначение роли управления. Области, наследуемые из ролей управления, называются *неявными областями*, а предварительно определенные и настраиваемые — *явными областями*. В следующих подразделах описываются все типы областей.

  - Неявные области

  - Явные области

  - Предварительно определенные относительные области

  - Настраиваемые области
    
      - Области фильтра получателей
    
      - Области конфигурации

Каждая роль может иметь следующие типы областей.

  - **Область чтения получателей**   Неявная область чтения получателей определяет объекты получателей, которые пользователь с назначенной ролью управления может читать из Active Directory.

  - **Область записи получателей**   Неявная область записи получателей определяет объекты получателей, которые пользователь с назначенной ролью управления может изменять в Active Directory.

  - **Область чтения конфигурации**   Неявная область чтения конфигурации определяет объекты конфигурации, которые пользователь с назначенной ролью управления может читать из Active Directory.

  - **Область записи конфигурации**   Неявная область записи конфигурации определяет объекты организации, базы данных и сервера, которые пользователь с назначенной ролью управления может изменять в службе каталогов Active Directory.

К объектам получателей относятся почтовые ящики, группы рассылки, пользователи с включенной поддержкой почты и другие объекты. К объектам конфигурации относятся серверы под управлением Microsoft Exchange Server 2013 и базы данных, размещенные на серверах под управлением Exchange. Каждый тип области может быть явной или неявной областью.

## Неявные области

Неявные области — это области по умолчанию, которые применяются к типу роли управления. Поскольку неявные области сопоставлены с типом роли управления, все родительские и дочерние роли управления с одним типом роли также имеют неявные области. Неявные области применяются как к встроенным ролям управления, так и к настраиваемым. Дополнительные сведения о ролях управления и типах ролей управления см. в разделе [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md).

В следующих таблицах приведены все неявные области, которые могут определяться в ролях управления.

### Неявные области, определенные в ролях управления

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Неявные области</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Organization</code></p></td>
<td><p>Если область <code>Organization</code> присутствует в области записи получателей роли, эта роль может создавать или изменять объекты получателей в организации Exchange.</p>
<p>Если область <code>Organization</code> присутствует в области чтения получателей роли, то эти роли могут просматривать любые объекты получателей в организации Exchange.</p>
<p>Эта область используется только с областями чтения и записи получателей.</p></td>
</tr>
<tr class="even">
<td><p><code>MyGAL</code></p></td>
<td><p>Если область <code>MyGAL</code> присутствует в области записи получателей роли, эта роль может просматривать свойства любых получателей, находящихся в текущем глобальном списке адресов (GAL) пользователя.</p>
<p>Если область <code>MyGAL</code> присутствует в области чтения получателей роли, эта роль может просматривать свойства любых получателей, находящихся в текущем глобальном списке адресов.</p>
<p>Эта область используется только с областями чтения получателей.</p></td>
</tr>
<tr class="odd">
<td><p><code>Self</code></p></td>
<td><p>Если область <code>Self</code> присутствует в области записи получателей роли, эта роль может изменять свойства только текущего почтового ящика пользователя.</p>
<p>Если область <code>Self</code> присутствует в области чтения получателей роли, эта роль может просматривать свойства только текущего почтового ящика пользователя.</p>
<p>Эта область используется только с областями чтения и записи получателей.</p></td>
</tr>
<tr class="even">
<td><p><code>MyDistributionGroups</code></p></td>
<td><p>Если область <code>MyDistributionGroups</code> присутствует в области записи получателей роли, эта роль может создавать или изменять объекты списка рассылки, принадлежащего текущему пользователю.</p>
<p>Если область <code>MyDistributionGroups</code> присутствует в области чтения получателей роли, эта роль может просматривать объекты списка рассылки, принадлежащего текущему пользователю.</p>
<p>Эта область используется только с областями чтения и записи получателей.</p></td>
</tr>
<tr class="odd">
<td><p><code>OrganizationConfig</code></p></td>
<td><p>Если область <code>OrganizationConfig</code> присутствует в области записи конфигурации роли, эта роль позволяет создавать или изменять любые объекты конфигурации сервера или базы данных в организации Exchange.</p>
<p>Если область <code>OrganizationConfig</code> присутствует в области чтения конфигурации роли, эта роль позволяет просматривать любые объекты конфигурации сервера или базы данных в организации Exchange.</p>
<p>Эта область используется только с областями чтения и записи конфигурации.</p></td>
</tr>
<tr class="even">
<td><p><code>None</code></p></td>
<td><p>Если в области присутствует область <code>None</code>, эта область недоступна для роли. Например, роль, в области записи получателей которой присутствует область <code>None</code>, не может изменять объекты получателей в организации Exchange.</p></td>
</tr>
</tbody>
</table>


Если уполномоченному роли назначена роль с незаданными предварительно определенными или настраиваемыми областями, то для управления объектами получателей или организации, которые пользователь может просматривать или изменять, используются неявные области, определенные в роли.

Неявная область записи роли всегда равна или меньше неявной области чтения. Это означает, что роль не может изменять объекты, не входящие в область.

Изменить неявные области, определенные в ролях управления, невозможно. Однако неявные область записи и область конфигурации в роли управления можно переопределить. Если в назначении роли используется предварительно определенная относительная область или настраиваемая область, неявная область записи в роли переопределяется, и приоритет имеет новая область. Неявная область чтения в роли применяется постоянно и ее невозможно переопределить. Дополнительные сведения см. в разделах Предварительно определенные относительные области и Настраиваемые области.

В следующей таблице приведен список встроенных ролей управления и их неявных областей. Дополнительные сведения о каждой из встроенных ролей см. в разделе [Встроенные роли управления](built-in-management-roles-exchange-2013-help.md).

## Неявные области встроенных ролей управления


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Роль управления</th>
<th>Область чтения получателей</th>
<th>Область записи получателей</th>
<th>Область чтения конфигурации</th>
<th>Область записи конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Active Directory Permissions</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Address Lists</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>ApplicationImpersonation</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><code>ArchiveApplication</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Audit Logs</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Cmdlet Extension Agents</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Data Loss Prevention</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Database Availability Groups</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Database Copies</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Databases</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Disaster Recovery</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Distribution Groups</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Edge Subscriptions</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>E-Mail Address Policies</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Exchange Connectors</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Exchange Server Certificates</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Exchange Servers</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Exchange Virtual Directories</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Federated Sharing</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Information Rights Management</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Journaling</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Legal Hold</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><code>LegalHoldApplication</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Mail Enabled Public Folders</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Mail Recipient Creation</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Mail Recipients</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Mail Tips</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Mailbox Import Export</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Mailbox Search</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><code>MailboxSearchApplication</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Message Tracking</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Migration</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Monitoring</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Move Mailboxes</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>OfficeExtensionApplication</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>My Custom Apps</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>My Marketplace Apps</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyAddressInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyBaseOptions</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyContactInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyDiagnostics</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyDisplayName</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyDistributionGroupMembership</code></p></td>
<td><p><code>MyGAL</code></p></td>
<td><p><code>MyGAL</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyDistributionGroups</code></p></td>
<td><p><code>MyGAL</code></p></td>
<td><p><code>MyDistributionGroups</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyMobileInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyName</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyPersonalInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyProfileInformation</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyRetentionPolicies</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyTeamMailboxes</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>MyTextMessaging</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>MyVoiceMail</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Organization Client Access</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Organization Configuration</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Organization Transport Settings</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>POP3 And IMAP4 Protocols</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Public Folders</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Receive Connectors</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Recipient Policies</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Remote and Accepted Domains</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Reset Password</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Retention Management</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Role Management</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Security Group Creation and Membership</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Send Connectors</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Support Diagnostics</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>TeamMailboxLifecycleApplication</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>Self</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Transport Agents</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Transport Hygiene</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Transport Queues</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>Transport Rules</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>UM Mailboxes</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>UM Prompts</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>Unified Messaging</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>UnScoped Role Management</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>UserApplication</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="odd">
<td><p><code>User Options</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
<tr class="even">
<td><p><code>View-Only Audit Logs</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><code>View-Only Configuration</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="even">
<td><p><code>View-Only Recipients</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>None</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>None</code></p></td>
</tr>
<tr class="odd">
<td><p><code>WorkloadManagement</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>Organization</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
<td><p><code>OrganizationConfig</code></p></td>
</tr>
</tbody>
</table>


## Явные области

Явные области — это области, которые пользователь устанавливает самостоятельно для управления объектами, которые может изменять роль управления. Несмотря на то что неявные области определяются в роли управления, явные области определяются в назначении роли управления. Это позволяет применять неявные области равномерно для всех ролей управления, пока они не будут переопределены явной областью. Дополнительные сведения о назначениях ролей управления см. в разделе [Общие сведения о назначениях ролей управления](understanding-management-role-assignments-exchange-2013-help.md).

Явные области переопределяют неявные области записи и конфигурации в роли управления. Однако они не переопределяют неявную область чтения в роли управления. Неявная область чтения продолжает определять, какие объекты может просматривать роль управления.

Явные области полезны, когда неявная область записи роли управления не отвечает потребностям предприятия. В добавленную явную область можно включать любые объекты с условием, чтобы они не выходили за границу действия неявной области чтения. Для создания или изменения объектов с помощью командлетов, входящих в роль управления, командлеты должны иметь возможность считывать данные об объектах или контейнерах с объектами. Например, если неявная область чтения в роли управления имеет значение `Self`, добавить явную область записи `Organization` невозможно, так как явная область записи выходит за пределы неявной области чтения.

Дополнительные сведения см. в следующих разделах.

  - Предварительно определенные относительные области

  - Настраиваемые области

## Предварительно определенные относительные области

Сервер Exchange 2013 предоставляет несколько предварительно определенных относительных областей записи, которые можно использовать для изменения области роли управления. Предварительно определенные относительные области — это простой способ удовлетворения потребностей предприятия без необходимости создавать настраиваемые области вручную. Относительными областями они называются потому, что они соотносятся с уполномоченным роли, которому присвоено сопоставленное назначение роли. Например, предварительно определенная относительная область `Self` ограничивает область записи только текущим пользователем. Предварительно определенная относительная область `MyDistributionGroups` ограничивает область записи только группой рассылки, принадлежащей текущему пользователю. Предварительно определенные относительные области могут использоваться только для определения области объектов получателей. Предварительно определенные относительные области нельзя использовать для определения области объектов конфигурации. В следующей таблице приведены предварительно определенные относительные области, которые можно использовать.

### Предварительно определенные относительные области

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Неявные области</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>Organization</code></p></td>
<td><p>Если область <code>Organization</code> присутствует в области записи получателей роли, эта роль может создавать или изменять объекты получателей в организации Exchange.</p>
<p>Если область <code>Organization</code> присутствует в области чтения получателей роли, то эти роли могут просматривать любые объекты получателей в организации Exchange.</p>
<p>Эта область используется только с областями чтения и записи получателей.</p></td>
</tr>
<tr class="even">
<td><p><code>Self</code></p></td>
<td><p>Если область <code>Self</code> присутствует в области записи получателей роли, эта роль может изменять свойства только текущего почтового ящика пользователя.</p>
<p>Если область <code>Self</code> присутствует в области чтения получателей роли, эта роль может просматривать свойства только текущего почтового ящика пользователя.</p>
<p>Эта область используется только с областями чтения и записи получателей.</p></td>
</tr>
<tr class="odd">
<td><p><code>MyDistributionGroups</code></p></td>
<td><p>Если область <code>MyDistributionGroups</code> присутствует в области записи получателей роли, эта роль может создавать или изменять объекты списка рассылки, принадлежащего текущему пользователю.</p>
<p>Если область <code>MyDistributionGroups</code> присутствует в области чтения получателей роли, эта роль может просматривать объекты списка рассылки, принадлежащего текущему пользователю.</p>
<p>Эта область используется только с областями чтения и записи получателей.</p></td>
</tr>
</tbody>
</table>


Предварительно определенные относительные области применяются при создании нового назначения роли управления. Во время создания назначения роли с помощью командлета **New-ManagementRoleAssignment** предварительно определенную относительную область можно задать, используя параметр *RecipientRelativeWriteScope*. После создания назначения роли новая предварительно определенная роль переопределяет неявную область записи роли управления. Настраиваемую область получателей невозможно указать при создании назначения роли с предварительно определенной относительной областью. Тем не менее, при необходимости можно указать настраиваемую область конфигурации.

Дополнительные сведения о добавлении назначения роли управления с предварительно определенной относительной областью см. в разделе [Добавление роли для пользователя или универсальной группы безопасности](add-a-role-to-a-user-or-usg-exchange-2013-help.md).

## Настраиваемые области

Настраиваемые области используются, когда ни неявная область записи, ни предварительно определенные относительные области не отвечают требованиям предприятия. Настраиваемые области позволяют определить на более детальном уровне область, к которой будет применяться роль управления. Например, она может применяться к определенному подразделению, определенному типу получателей или к тому и другому. Или можно разрешить группе администраторов управлять определенным набором баз данных почтовых ящиков.

Настраиваемые области, так же как и предварительно определенные относительные области, переопределяют неявные области записи и конфигурации организации, определенные для ролей управления. При этом неявная область чтения ролей управления продолжает применяться, и полученная настраиваемая область не должна выходить за границы неявной области чтения. Можно создать настраиваемые области трех типов.

  - **Область подразделения**   Область подразделения, которая является самой простой настраиваемой областью, создается с помощью параметра *RecipientOrganizationalUnitScope* командлета **New-ManagementRoleAssignment**. Область подразделения, указанная при назначении роли, позволяет пользователю, которому назначена эта роль, изменять только объекты получателей, находящихся в этом подразделении. Дополнительные сведения о добавлении назначения роли управления с областью подразделения см. в разделе [Добавление роли для пользователя или универсальной группы безопасности](add-a-role-to-a-user-or-usg-exchange-2013-help.md).

  - **Область фильтра получателей**   В областях фильтра получателей используются фильтры для указания определенных получателей на основе их типа или других свойств, таких как отдел, менеджер, местоположение и другие. Дополнительные сведения см. в разделе Области фильтра получателей.

  - **Область конфигурации**   В областях конфигурации используются фильтры или списки для указания определенных серверов на основе списков серверов или фильтруемых свойств, заданных на серверах, таких как сайт Active Directory или роль сервера. Области конфигурации также могут использовать области баз данных для задания определенных баз данных на основе списков баз данных или фильтруемых свойств баз данных. Дополнительные сведения см. в разделе Области конфигурации.

Простые, более сложные и детальные настраиваемые области получателей и конфигурации создаются с помощью командлета **New-ManagementScope**. При создании области получателей или конфигурации возвращаются только объекты получателей, серверов или баз данных, которые соответствуют своим областям. Когда для применения этих областей к назначению роли используется командлет **New-ManagementRoleAssignment** или **Set-ManagementRoleAssignment**, уполномоченный роли может изменять только те объекты, которые соответствуют этим областям. После создания настраиваемой области изменить тип области невозможно. Область получателей всегда будет областью получателей, а область конфигурации всегда будет областью конфигурации.

По умолчанию настраиваемая область предоставляет уполномоченному роли доступ к набору объектов, которые соответствуют заданным областям. Однако они не закрывают доступ другим уполномоченным роли, которым не назначена эта же или эквивалентная область. Любая настраиваемая область может иметь доступ к тем же объектам, если списки или фильтры этих областей соответствуют этим же объектам. Однако такое поведение может быть неприемлемым для некоторых объектов, например для руководства компании. Для этих объектов можно определить монопольные области. В монопольных областях фильтры или списки применяются так же, как и в обычных областях. Однако в отличие от обычных областей, монопольные области запрещают доступ к объектам, включенным в область, всем пользователям, которые не входят в эту же или равнозначную монопольную область. Дополнительные сведения о монопольных областях см. в разделе [Общие сведения об исключительных областях](understanding-exclusive-scopes-exchange-2013-help.md).

## Области фильтра получателей

Области фильтра получателей позволяют контролировать, какими объектами получателей могут управлять уполномоченные ролей, путем оценки одного или нескольких свойств объекта получателя по значению, указанному в инструкции фильтра. К получателям, входящим в состав областей получателей, относятся почтовые ящики, пользователи с включенной поддержкой почты, группы рассылки и почтовые контакты. Уполномоченные ролей, которым назначено это назначение роли, могут управлять только теми получателями, которые соответствуют указанному фильтру. В качестве примера инструкции фильтра можно привести выражение `{ Name -Eq "David" }`, где **Name** — это оцениваемое свойство объекта получателя, а **David** — значение, которое необходимо оценить по свойству. Оператор сравнения **-Eq** указывает, что значение, хранящееся в свойстве, должно быть равно значению, указанному в фильтре, чтобы считаться значением True. Если фильтр имеет значение True, получатель включается в состав области.

Области фильтра получателей создаются при указании используемого фильтра получателей с помощью параметра *RecipientRestrictionFilter* командлета **New-ManagementScope**. По умолчанию с помощью командлета **New-ManagementScope** создаются обычные области. Чтобы создать монопольную область, используйте параметр *Exclusive* с параметром *RecipientRestrictionFilter*.

При создании фильтра ограничений получателей система Exchange по умолчанию оценивает указанный фильтр по каждому объекту получателя в организации. Чтобы ограничить ряд получателей, оцениваемых областью, можно использовать параметр *RecipientRoot* с параметром *RecipientRestrictionFilter*. Параметр *RecipientRoot* принимает значение подразделения. При использовании параметра *RecipientRoot* система Exchange оценивает по заданному фильтру только получателей в указанном подразделении.

Если область фильтра получателей добавляется в назначение роли, необходимо указать имя этой области в параметре *CustomRecipientWriteScope* в командлете **New-ManagementRoleAssignment**, чтобы создать новое назначение роли, или в командлете **Set-ManagementRoleAssignment**, чтобы обновить существующее назначение роли. Каждое назначение роли может иметь одну область получателей, включая предварительно определенные относительные области. В то же назначение роли, в которое была добавлена область получателей, можно добавить одну область конфигурации.

Дополнительные сведения о синтаксисе фильтра и полный список фильтруемых свойств получателей см. в разделе [Общие сведения о фильтрах области ролей управления](understanding-management-role-scope-filters-exchange-2013-help.md).

## Области конфигурации

В системе Exchange 2013 представлено два типа областей конфигурации.

  - **Области серверов**   Существует два типа областей серверов: области фильтра серверов и области списка серверов. Управление конфигурацией сервера, включая соединители приема, очереди транспорта, сертификаты сервера, виртуальные каталоги и т. д., может выполняться в случае, если в область сервера входит объект сервера.
    
      - **Области фильтра серверов**   Области фильтра серверов позволяют контролировать, какими объектами сервера могут управлять уполномоченные ролей, путем оценки одного или нескольких свойств объекта сервера по значению, указанному в инструкции фильтра. Область фильтра серверов создается с помощью параметра *ServerRestrictionFilter* командлета **New-ManagementScope**.
    
      - **Области списка серверов**   Области списка серверов позволяют контролировать, какими объектами сервера могут управлять уполномоченные ролей, путем создания списка серверов, к которым уполномоченный роли может иметь доступ. Область списка серверов создается с помощью параметра *ServerList* командлета **New-ManagementScope**.

  - **Области баз данных**   Существует два типа областей баз данных: области фильтра баз данных и области списка баз данных. Если объект базы данных включен в область баз данных, это позволяет управлять следующими элементами конфигурации базы данных: квотами базы данных, обслуживанием базы данных, репликацией общих папок, подключением базы данных и т. д. Кроме конфигурации базы данных для контроля создаваемых получателей баз данных можно использовать области баз данных. Если в организации имеются серверы предыдущих версий Exchange 2010 SP1, см. раздел Области баз данных и предыдущие версии Exchange.
    
      - **Области фильтра баз данных**   Области фильтра баз данных позволяют контролировать, какими объектами базы данных могут управлять уполномоченные ролей, путем оценки одного или нескольких свойств объекта базы данных по значению, указанному в инструкции фильтра. Область фильтра баз данных создается с помощью параметра *DatabaseRestrictionFilter* командлета **New-ManagementScope**.
    
      - **Области списка баз данных**   Области списка баз данных позволяют контролировать, какими объектами базы данных могут управлять уполномоченные ролей, путем создания списка баз данных, к которым уполномоченный роли может иметь доступ. Область списка баз данных создается с помощью параметра *DatabaseList* командлета **New-ManagementScope**.

Дополнительные сведения о синтаксисе фильтра и полный список фильтруемых свойств серверов и баз данных см. в разделе [Общие сведения о фильтрах области ролей управления](understanding-management-role-scope-filters-exchange-2013-help.md).

Списки серверов и баз данных можно задать путем указания всех серверов и баз данных, которые необходимо включить в их соответствующие области. Чтобы указать в областях несколько серверов или баз данных, необходимо разделить их имена запятой.

Если область конфигурации серверов или баз данных добавляется в назначение роли, необходимо указать имя этой области в параметре *CustomConfigWriteScope* в командлете **New-ManagementRoleAssignment**, чтобы создать новое назначение роли, или в командлете **Set-ManagementRoleAssignment**, чтобы обновить существующее назначение роли. Каждое назначение роли может иметь только одну область конфигурации.

Области баз данных позволяют контролировать не только, какими базами данных могут управлять уполномоченные роли, но и в каких базах данных уполномоченные роли могут создавать почтовые ящики. Эта функция отличается от функции управления получателями, которыми может управлять уполномоченный роли. Если уполномоченный роли имеет разрешения создавать почтовые ящики, включать поддержку почты для существующих пользователей или перемещать почтовые ящики, эти разрешения можно уточнить с помощью областей баз данных, чтобы контролировать, в какой базе данных создается почтовый ящик или в какую базу данных он перемещается. Чтобы контролировать, какими получателями может управлять уполномоченный роли, необходимо указать область получателей в параметре *CustomRecipientWriteScope* командлета **New-ManagementRoleAssignment** или командлета **Set-ManagementRoleAssignment**. Чтобы контролировать, в каких базах данных может создаваться почтовый ящик или в какие базы данных он может перемещаться, необходимо указать область баз данных в параметре *CustomConfigurationWriteScope* тех же командлетов.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Автоматическим распределением почтовых ящиков можно управлять с помощью областей баз данных.</td>
</tr>
</tbody>
</table>


Для функций Exchange может требоваться управление областями серверов, областями баз данных или обоими типами областей. Если для функции требуется управление обеими областями серверов и баз данных, необходимо создать два назначения роли и назначить их уполномоченному роли, который должен иметь права доступа к этой функции для управления. Одно назначение роли должно быть связано с областью серверов, а другое — с областью баз данных.

Некоторые командлеты могут использовать области конфигурации, которые не являются очевидными. В следующей таблице приведен список командлетов и областей конфигурации, с помощью которых можно управлять их использованием. При использовании командлетов, включенных в функциональную область получателей, области конфигурации позволяют контролировать базами данных, в которых можно создавать получателей. Они не определяют, какими получателями можно управлять. Столбец **Требуемые области** может содержать следующие данные.

  - **База данных**   Чтобы выполнить командлет, уполномоченному роли должно быть назначено назначение роли с областью баз данных, включающей в себя управляемую базу данных, или неявная область записи конфигурации роли должна включать в себя управляемую базу данных.

  - **Сервер**   Чтобы выполнить командлет, уполномоченному роли должно быть назначено назначение роли с областью серверов, включающей в себя управляемый сервер, или неявная область записи конфигурации роли должна включать в себя управляемый сервер.

  - **Сервер или база данных**   Чтобы выполнить командлет, уполномоченному роли должно быть назначено назначение роли, в котором либо область баз данных включает в себя управляемую базу данных, либо область серверов включает в себя сервер, на котором расположена база данных. Или, неявная область записи конфигурации роли должна содержать управляемую базу данных или сервер, на котором расположена база данных, а уполномоченный роли не должен иметь настраиваемую область записи.

  - **Сервер и база данных**   Чтобы выполнить этот командлет, уполномоченному роли необходимо назначить два назначения роли. Первое назначение роли должно включать в себя область баз данных, содержащую базу данных для управления. Второе назначение роли должно включать в себя область серверов, содержащую сервер, на котором размещена база данных. Назначения роли могут иметь заданные настраиваемые области конфигурации, или они могут наследовать неявные области записи конфигурации из роли. Чтобы наследовать неявную область записи из роли, назначение роли не должно иметь настраиваемую область записи.

### Функциональные области и применяемые области баз данных и серверов

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Функциональная область</th>
<th>Командлет</th>
<th>Требуемые области</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Базы данных</p></td>
<td><p><strong>Dismount-Database</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="even">
<td><p>Базы данных</p></td>
<td><p><strong>Mount-Database</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="odd">
<td><p>Базы данных</p></td>
<td><p><strong>Move-DatabasePath</strong></p></td>
<td><p>Сервер и база данных</p></td>
</tr>
<tr class="even">
<td><p>Базы данных</p></td>
<td><p><strong>Remove-MailboxDatabase</strong></p></td>
<td><p>Сервер или база данных</p></td>
</tr>
<tr class="odd">
<td><p>Базы данных</p></td>
<td><p><strong>Set-MailboxDatabase</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="even">
<td><p>Высокая доступность</p></td>
<td><p><strong>Add-DatabaseAvailabilityGroupServer</strong></p></td>
<td><p>Сервер</p></td>
</tr>
<tr class="odd">
<td><p>Высокая доступность</p></td>
<td><p><strong>Add-MailboxDatabaseCopy</strong></p></td>
<td><p>Сервер</p></td>
</tr>
<tr class="even">
<td><p>Высокая доступность</p></td>
<td><p><strong>Move-ActiveMailboxDatabase</strong></p></td>
<td><p>Сервер</p></td>
</tr>
<tr class="odd">
<td><p>Высокая доступность</p></td>
<td><p><strong>Remove-DatabaseAvailabilityGroupServer</strong></p></td>
<td><p>Сервер</p></td>
</tr>
<tr class="even">
<td><p>Высокая доступность</p></td>
<td><p><strong>Remove-MailboxDatabaseCopy</strong></p></td>
<td><p>Сервер или база данных</p></td>
</tr>
<tr class="odd">
<td><p>Высокая доступность</p></td>
<td><p><strong>Resume-MailboxDatabaseCopy</strong></p></td>
<td><p>Сервер или база данных</p></td>
</tr>
<tr class="even">
<td><p>Высокая доступность</p></td>
<td><p><strong>Set-MailboxDatabaseCopy</strong></p></td>
<td><p>Сервер или база данных</p></td>
</tr>
<tr class="odd">
<td><p>Высокая доступность</p></td>
<td><p><strong>Suspend-MailboxDatabaseCopy</strong></p></td>
<td><p>Сервер или база данных</p></td>
</tr>
<tr class="even">
<td><p>Высокая доступность</p></td>
<td><p><strong>Update-MailboxDatabaseCopy</strong></p></td>
<td><p>Сервер или база данных</p></td>
</tr>
<tr class="odd">
<td><p>Получатели</p></td>
<td><p><strong>Connect-Mailbox</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="even">
<td><p>Получатели</p></td>
<td><p><strong>Enable-Mailbox</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="odd">
<td><p>Получатели</p></td>
<td><p><strong>New-Mailbox</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="even">
<td><p>Получатели</p></td>
<td><p><strong>New-MoveRequest</strong></p></td>
<td><p>Database</p></td>
</tr>
<tr class="odd">
<td><p>Устранение неполадок</p></td>
<td><p><strong>Test-MapiConnectivity</strong></p></td>
<td><p>Database</p></td>
</tr>
</tbody>
</table>


## Области баз данных и предыдущие версии Exchange

Впервые области баз данных были представлены в Microsoft Exchange 2010 с пакетом обновления 1 (SP1). Их поддержка продолжается в Exchange 2013. Версии Exchange до Exchange 2010 с пакетом обновления 1 (SP1) поддерживают только области получателей и области конфигураций серверов. При создании области баз данных в Exchange 2010 с пакетом обновления 1 (SP1) или в более поздней версии появится следующее предупреждение.

    WARNING: Database management scopes will only be applied when a user connects to a server running Exchange 2010 SP1 or later. Servers running a version of Exchange prior to Exchange 2010 SP1 won't apply any roles from a role assignment linked to a database scope. Database management scopes also won't be visible to the Get-ManagementScope cmdlet when it's run from a pre-Exchange 2010 SP1 server.

При создании области баз данных они применяется только к пользователям, подключенным к серверам с Exchange 2010 с пакетом обновления 1 (SP1) или более поздней версией. Пользователи, подключенные к серверам предыдущих версий Exchange 2010, не будут иметь назначения ролей, связанные с примененным к ним областям баз данных. Это значит, что пользователи, подключающиеся к серверам предыдущих версий Exchange 2010 SP1, не получат разрешения, предоставляемые назначениями этих ролей. На серверах предыдущих версий Exchange 2010 SP1 нельзя создавать, удалять, изменять или просматривать области баз данных.

Область баз данных может содержать любую базу данных в организации Exchange. К ним относятся серверы Exchange Server 2007, Exchange 2010 и Exchange 2013. Это позволяет определять, какими базами данных, независимо от версии Exchange, могут управлять пользователи. Как и в случае с другими областями баз данных, назначения ролей, связанные с областями баз данных, которые содержат базы данных Exchange 2007 и Exchange 2010, применяются только к пользователям, подключающимся к серверу Exchange 2010 с пакетом обновления 1 (SP1) или более поздней версии.

Пользователи, подключающиеся к серверам предыдущих версий Exchange 2010 с пакетом обновления 1 (SP1), могут просматривать и изменять назначения ролей, связанные с областями баз данных. Также пользователи могут изменять область конфигурации на область серверов в существующем назначении роли, если оно в данный момент связано с областью баз данных. Однако если область конфигурации в назначении роли меняется на область сервера и пользователь в дальнейшем хочет изменить ее снова на область баз данных или если пользователь хочет изменить область конфигурации на другую область баз данных, пользователь должен внести изменения во время подключения к серверу Exchange 2010 с пакетом обновления 1 (SP1) или более поздней версией. Когда пользователи изменяют область конфигурации в назначении роли и если они подключены к предыдущей версии сервера Exchange 2010 с пакетом обновления 1 (SP1), они могут указывать только области конфигураций.

