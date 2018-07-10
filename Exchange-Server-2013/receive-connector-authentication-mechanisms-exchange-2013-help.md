---
title: 'Механизмы проверки подлинности соединителя получения: Exchange 2013 Help'
TOCTitle: Механизмы проверки подлинности соединителя получения
ms:assetid: 926424e1-83e3-4c4b-b2dd-bf814d81e877
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ657472(v=EXCHG.150)
ms:contentKeyID: 50488636
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Механизмы проверки подлинности соединителя получения

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_


Вот механизмы проверки подлинности соединителя получения:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Механизм проверки подлинности</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Нет</p></td>
<td><p>Нет проверки подлинности</p></td>
</tr>
<tr class="even">
<td><p>TLS</p></td>
<td><p>Advertise STARTTLS. Требует наличия на сервере сертификата для предложения TLS.</p></td>
</tr>
<tr class="odd">
<td><p>Встроенный</p></td>
<td><p>NTLM и Kerberos (встроенная проверка подлинности Windows)</p></td>
</tr>
<tr class="even">
<td><p>BasicAuth</p></td>
<td><p>Обычная проверка подлинности Требует проверки подлинности при входе.</p></td>
</tr>
<tr class="odd">
<td><p>BasicAuthRequireTLS</p></td>
<td><p>Обычная проверка подлинности поверх TLS. Требуется сертификат сервера</p></td>
</tr>
<tr class="even">
<td><p>ExchangeServer</p></td>
<td><p>Проверка подлинности Exchange Server (программный интерфейс GSSAPI и взаимный GSSAPI).</p></td>
</tr>
<tr class="odd">
<td><p>ExternalAuthoritative</p></td>
<td><p>Подключение считается имеющим внешнюю защиту при использовании механизма безопасности, внешнего по отношению к Exchange. Подключение может быть связано с протоколом IPsec или виртуальной частной сетью VPN. Вместо этого серверы могут находиться в доверительной физически контролируемой сети. Для способа проверки подлинности <code>ExternalAuthoritative</code> требуется группа разрешений <code>ExchangeServers</code>. При этом сочетании метода проверки подлинности и группы безопасности поддерживается разрешение адресов электронной почты анонимных отправителей для сообщений, получаемых через этот соединитель.</p></td>
</tr>
</tbody>
</table>


Дополнительные сведения о механизмах проверки подлинности соединителя получения см. в разделе [New-ReceiveConnector](https://technet.microsoft.com/ru-ru/library/bb125139\(v=exchg.150\)).

