---
title: 'Подготовка почтовых ящиков для запросов на перемещение между лесами: Exchange 2013 Help'
TOCTitle: Подготовка почтовых ящиков для запросов на перемещение между лесами
ms:assetid: fdbed4fc-a77e-40d5-a211-863b05d74784
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee633491(v=EXCHG.150)
ms:contentKeyID: 50489575
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Подготовка почтовых ящиков для запросов на перемещение между лесами

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2017-11-22_

**Сводка:**  сведения о подготовке почтовых ящиков для перемещения между лесами в Exchange 2013.

Microsoft Exchange 2013 поддерживает перемещение почтовых ящиков и миграций с помощью командной консоли Exchange, в частности командлеты **New-MoveRequest** и **New-MigrationBatch** . Вы также можете переместить почтовый ящик с помощью центра администрирования Exchange (EAC). Обратите внимание на то, что можно переместить почтовые ящики Exchange 2010 и Exchange 2013 в лес Exchange 2013.

Чтобы переместить почтовый ящик из леса Exchange лес Exchange 2013, конечный лес Exchange 2013 должно содержать допустимого пользователя почты с указанным набором атрибутов Active Directory. Если имеется по крайней мере один сервер клиентского доступа Exchange 2013, развернутые в лесу, леса считается лес Exchange 2013.

Чтобы подготовить почтовый ящик к перемещению, необходимо создать в целевом лесе пользователей с включенной поддержкой почты, имеющих требуемые атрибуты. Существует два рекомендуемых способа создания пользователей с необходимыми атрибутами:

  - Если Microsoft Identity Lifecycle Manager (ILM) развернут для синхронизации глобальных списков адресов между лесами, для создания пользователя с включенной поддержкой почты рекомендуется использовать пакет обновления 1 (SP1) для пакета дополнительных компонентов 1 (FP1) ILM 2007. Мы создали пример кода, который можно использовать для обучения настройке ILM на синхронизацию исходного пользователя почты и целевого пользователя почты.
    
    Дополнительные сведения, включая сведения о загрузке примера кода, см. в разделе [Подготовка почтовых ящиков для перемещения между лесами с помощью примера кода](prepare-mailboxes-for-cross-forest-moves-using-sample-code-exchange-2013-help.md).

  - При создании почтового пользователя с помощью средства Active Directory, отличного от ILM/MIIS, используйте командлет **Update-Recipient** с параметром *Identity* для запуска службы Address List, чтобы сгенерировать **LegacyExchangeDN** для целевого почтового пользователя. Мы создали образец сценария Windows PowerShell, который считывает из и записывает в Active Directory и вызывает командлет **Update-Recipient**.
    
    Дополнительные сведения об использовании примера сценария см. в разделе [Подготовка почтовых ящиков к перемещению между лесами с использованием в консоли сценария Prepare-MoveRequest.ps1](prepare-mailboxes-for-cross-forest-moves-using-the-prepare-moverequest-ps1-script-in-the-shell-exchange-2013-help.md).

После создания целевого пользователя почты можно запустить командлет **New-MoveRequest** или **New-MigrationBatch** для перемещения почтового ящика в целевой лес Exchange 2013.

Дополнительные сведения об удаленных запросах на перемещение см. в следующих разделах:

  - [New-MigrationBatch](https://technet.microsoft.com/ru-ru/library/jj219166\(v=exchg.150\))

  - [New-MoveRequest](https://technet.microsoft.com/ru-ru/library/dd351123\(v=exchg.150\))

Дополнительные сведения об удаленных перемещениях почтовых ящиков и удаленных перемещениях данных прежних версий см. в разделе [Перемещение почтовых ящиков в Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md).

В оставшейся части этой статьи описываются атрибуты почтовых пользователей Active Directory, необходимые для перемещения почтового ящика. Эти атрибуты настраиваются во время использования кода или сценария для подготовки перемещения почтового ящика. Однако их можно также скопировать вручную с помощью редактора Active Directory.

## Атрибуты пользователя Active Directory, необходимые для перемещения почтового ящика

Для обеспечения поддержки удаленного перемещения почтового ящика объект пользователя почты в целевом лесе Exchange 2013 должен иметь атрибуты Active Directory, описанные в данном разделе:

  - Обязательные атрибуты

  - Необязательные атрибуты

  - Связанные атрибуты

  - Атрибуты связанного пользователя

  - Атрибуты почтового ящика ресурсов

  - Дополнительные атрибуты

## Обязательные атрибуты

В следующей таблице перечислен минимальный набор атрибутов, которые необходимо настроить в ILM для целевого пользователя почты, чтобы командлет **New-MoveRequest** работал правильно.

### Атрибуты пользователя почты

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Атрибуты Active Directory пользователя почты</th>
<th>Действие</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>displayName</strong></p></td>
<td><p>Скопируйте соответствующий атрибут исходного почтового ящика или создайте новое значение.</p></td>
</tr>
<tr class="even">
<td><p><strong>Mail</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>mailNickname</strong></p></td>
<td><p>Скопируйте соответствующий атрибут исходного почтового ящика или создайте новое значение.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchArchiveGUID and msExchArchiveName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика. Атрибуты доступны только при использовании почтового ящика Exchange 2010 в качестве исходного.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchMailboxGUID</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchRecipientDisplayType</strong></p></td>
<td><p>-2147483642 (десятичный формат), эквивалентно значению 0x80000006 (шестнадцатеричный формат).</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchRecipientTypeDetails</strong></p></td>
<td><p>128 (десятичный формат)/0x80 (шестнадцатеричный формат).</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchUserCulture</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchVersion</strong></p></td>
<td><p>44220983382016 (десятичный формат).</p></td>
</tr>
<tr class="even">
<td><p><strong>cn</strong></p></td>
<td><p>Скопируйте соответствующий атрибут исходного почтового ящика или создайте новое значение.</p></td>
</tr>
<tr class="odd">
<td><p><strong>proxyAddresses</strong></p></td>
<td><p>Скопируйте атрибут <strong>proxyAddresses</strong> исходного почтового ящика. Кроме того, скопируйте значение <strong>LegacyExchangeDN</strong> исходного почтового ящика в качестве адреса X500 в атрибут <strong>proxyAddresses</strong> целевого пользователя почты.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Значение <strong>proxyAddresses</strong> пользователя исходного почтового ящика должно содержать адрес SMTP, соответствующий заслуживающему доверия домену целевого леса. Это позволяет командлету <strong>New-MoveRequest</strong> правильно выбрать <strong>targetAddress</strong> исходного пользователя с включенной поддержкой почты (преобразуемого из пользователя исходного почтового ящика после выполнения запроса на перемещение почтового ящика) для проверки работы маршрутизации почты.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="even">
<td><p><strong>sAMAccountName</strong></p></td>
<td><p>Скопируйте соответствующий атрибут исходного почтового ящика или создайте новое значение.</p>
<p>Убедитесь в том, что данное значение является уникальным в пределах домена целевого леса, к которому относится целевой пользователь почты.</p></td>
</tr>
<tr class="odd">
<td><p><strong>targetAddress</strong></p></td>
<td><p>Задайте адрес SMTP в атрибуте <strong>proxyAddresses</strong> исходного почтового ящика.</p>
<p>Этот адрес SMTP должен относиться к заслуживающему доверия домену исходного леса.</p></td>
</tr>
<tr class="even">
<td><p><strong>userAccountControl</strong></p></td>
<td><p>Константа: 514, эквивалентно значению 0x202, ACCOUNTDISABLE | NORMAL_ACCOUNT.</p></td>
</tr>
<tr class="odd">
<td><p><strong>userPrincipalName</strong></p></td>
<td><p>Скопируйте соответствующий атрибут исходного почтового ящика или создайте новое значение. Поскольку пользователю запрещен вход, данное значение <strong>userPrincipalName</strong> не используется.</p></td>
</tr>
</tbody>
</table>


## Необязательные атрибуты

Настройка следующих атрибутов не является обязательным условием для правильной работы командлета **New-MoveRequest**, однако их синхронизация позволяет улучшить сквозное взаимодействие пользователей после перемещения почтового ящика. Поскольку глобальный список адресов в целевом лесе отображает данного целевого пользователя почты, необходимо задать следующие атрибуты для глобального списка адресов.

### Атрибуты, связанные с глобальным списком адресов

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Атрибуты Active Directory пользователя почты</th>
<th>Действие</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>c</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>co</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>countryCode</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>company</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>department</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>facsimileTelephoneNumber</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>givenName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>homePhone</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>info</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>initials</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>l</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>mobile</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchAssistantName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchHideFromAddressLists</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>otherHomePhone</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>otherTelephone</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>pager</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>physicalDeliveryOfficeName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>postalCode</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>sn</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>st</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>streetAddress</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>telephoneAssistant</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>telephoneNumber</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>title</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
</tbody>
</table>


## Связанные атрибуты

Связанный атрибут — это атрибут Active Directory, который ссылается на другие объекты Active Directory в локальном лесе. Значения связанных атрибутов нельзя напрямую скопировать из почтового ящика в исходном лесе для пользователя почты в целевом лесе. Сначала необходимо найти в исходном лесе объекты Active Directory, на которые ссылается атрибут исходного почтового ящика. После этого необходимо найти в целевом лесе соответствующие объекты Active Directory для ранее упомянутого объекта Active Directory в исходном лесе. В заключение задайте атрибут целевого пользователя почты для ссылки на объекты Active Directory в целевом лесе.

### Связанные атрибуты

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Атрибуты Active Directory пользователя почты</th>
<th>Действие</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>altRecipient</strong></p></td>
<td><p>Соответствует атрибуту <strong>altRecipient</strong> исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>deliverAndRedirect</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика. Данный атрибут является логическим значением, которое необходимо задать вместе с <strong>altRecipient</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Manager</strong> (и его обратные ссылки)</p></td>
<td><p>Соответствует атрибуту manager исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>MemberOf</strong> (обратные ссылки)</p></td>
<td><p>Это обратная ссылка атрибута члена группы.</p></td>
</tr>
<tr class="odd">
<td><p><strong>publicDelegates</strong> (и его обратные ссылки)</p></td>
<td><p>Соответствует атрибуту <strong>publicDelegates</strong> исходного почтового ящика.</p></td>
</tr>
</tbody>
</table>


## Атрибуты связанного пользователя

Если необходимо переместить почтовый ящик в лес ресурсов Exchange 2013, то почтовый ящик в лесе ресурсов считается *связанным почтовым ящиком*. В данном сценарии необходимо создать связанного пользователя почты в (целевом) лесе ресурсов. Чтобы создать связанного пользователя почты, необходимо задать атрибуты, указанные в следующей таблице.

### Атрибуты связанного пользователя почты

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Атрибуты Active Directory пользователя почты</th>
<th>Действие</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>msExchMasterAccountHistory</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchMasterAccountSid</strong></p></td>
<td><p>Если у исходного почтового ящика есть атрибут <strong>msExchMasterAccountSid</strong>, скопируйте его. В противном случае скопируйте атрибут <strong>objectSid</strong> исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchRecipientDisplayType</strong></p></td>
<td><p>Константа:-1073741818 (десятичный формат), эквивалентно беззнаковому значению 0xC0000006.</p></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Связанный почтовый ящик можно создать только при наличии доверительного отношения лесов между исходным лесом и целевым лесом.</td>
</tr>
</tbody>
</table>


Если исходный объект отключен, а атрибут **msExchMasterAccountSid** установлен сам на себя (почтовый ящик ресурсов, общий почтовый ящик), не делайте пометок для целевого пользователя.

Если исходный объект отключен, а атрибут **msExchMasterAccountSid** не задан, то данный почтовый ящик не является допустимым.

Если исходный объект включен, а атрибут **msExchMasterAccountSid** задан, то данный почтовый ящик не является допустимым.

## Атрибуты почтового ящика ресурсов

Если требуется переместить почтовый ящик ресурсов в лес Exchange 2013, необходимо задать для целевого пользователя почты атрибуты, указанные в следующей таблице.

### Атрибуты почтового ящика ресурсов

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Атрибуты Active Directory пользователя почты</th>
<th>Действие</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>msExchRecipientDisplayType</strong></p></td>
<td><p>Если исходный почтовый ящик является комнатой переговоров:</p>
<ul>
<li><p><strong>Константа</strong>   -2147481850 (десятичный формат), эквивалентно беззнаковому значению 0x80000706.</p></li>
</ul>
<p>Если исходный почтовый ящик является почтовым ящиком оборудования:</p>
<ul>
<li><p><strong>Константа</strong>   -2147481594 (десятичный формат), эквивалентно беззнаковому значению 0x80000806.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>msExchResourceCapacity</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchResourceDisplay</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchResourceMetaData</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchResourceSearchProperties</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
</tbody>
</table>


## Дополнительные атрибуты

В Exchange 2007 при перемещении почтового ящика командлет **Move-Mailbox** также копировал атрибуты, указанные в следующей таблице. Если того требует используемая организация, эти атрибуты можно также скопировать.

### Атрибуты почтового ящика ресурсов

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Атрибуты Active Directory пользователя почты</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>comment</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>deletedItemFlags</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>delivContLength</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>departmentNumber</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>description</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>division</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>employeeID</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>employeeNumber</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>employeeType</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>extensionAttribute1-15</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>homePostalAddress</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>internationalISDNNumber</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ipPhone</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>language</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>lmPwdHistory</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>localeID</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>mAPIRecipient</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>middleName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msDS-PhoneticCompanyName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msDS-PhoneticDepartment</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msDS-PhoneticDisplayName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msDS-PhoneticFirstName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msDS-PhoneticLastName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchBlockedSendersHash</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchELCExpirySuspensionEnd</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchELCExpirySuspensionStart</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchELCMailboxFlags</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchExternalOOFOptions</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchMessageHygieneFlags</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchMessageHygieneSCLDeleteThreshold</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchMessageHygieneSCLJunkThreshold</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchMessageHygieneSCLQuarantineThreshold</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchMessageHygieneSCLRejectThreshold</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchMDBRulesQuota</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchPoliciesExcluded</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchSafeRecipientsHash</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>msExchSafeSendersHash</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>msExchUMSpokenName</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>otherFacsimileTelephoneNumber</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>otherIpPhone</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>otherMobile</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>otherPager</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>preferredDeliveryMethod</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>personalPager</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>personalTitle</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>photo</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>pOPCharacterSet</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>pOPContentFormat</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>postalAddress</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>postOfficeBox</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>primaryInternationalISDNNumber</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>primaryTelexNumber</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>showInAdvancedViewOnly</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>street</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>terminalServer</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>textEncodedORAddress</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>thumbnailLogo</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>thumbnailPhoto</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>url</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>userCert</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>userCertificate</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="even">
<td><p><strong>userSMIMECertificate</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>wWWHomePage</strong></p></td>
<td><p>Непосредственно скопируйте соответствующий атрибут исходного почтового ящика.</p></td>
</tr>
</tbody>
</table>

