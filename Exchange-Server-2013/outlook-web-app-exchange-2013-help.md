---
title: 'Outlook Web App: Exchange 2013 Help'
TOCTitle: Outlook Web App
ms:assetid: 3814b665-01e8-4881-9a44-163f14789ee4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ657718(v=EXCHG.150)
ms:contentKeyID: 50487832
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Outlook Web App

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2016-12-09_

Ознакомьтесь с веб-приложением Web App, которое в версиях Microsoft Exchange, предшествующих Exchange 2010, называлось Outlook Web Access. В этой статье представлены краткий обзор и ссылки на полезные сведения.

По умолчанию при установке МайкрософтExchange 2013 вы включаете Outlook Web App. МайкрософтOutlook Web App предоставляет пользователям доступ к их почтовым ящикам Exchange практически в любом браузере.

Роль сервера клиентского доступа предоставляет службы прокси-сервера и перенаправления для Outlook Web App.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В версиях Microsoft Exchange до Exchange 2010Outlook Web App называлось Outlook Web Access.</td>
</tr>
</tbody>
</table>


Сведения о новых возможностях см. в разделе [Новые возможности в Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md). Дополнительные сведения о роли сервера клиентского доступа Exchange 2013 см. в разделе [Сервер клиентского доступа](client-access-server-exchange-2013-help.md).

## Обзор Outlook Web App

Полностью поддерживаемые браузеры предоставляют пользователям доступ к таким возможностям, как представление беседы, правила папки "Входящие", область чтения и помощник по планированию. Также можно использовать не полностью поддерживаемые браузеры, но пользователи увидят упрощенную версию Outlook Web App с меньшим числом возможностей. Сведения о новых возможностях в Outlook Web App см. в разделе [Новые возможности Outlook Web App в Exchange 2013](what-s-new-for-outlook-web-app-in-exchange-2013-exchange-2013-help.md).

## Управление Outlook Web App

В Exchange 2013 наиболее часто используемые задачи управления Outlook Web App можно выполнять в центре администрирования Exchange (EAC). Все эти задачи, а также множество других задач могут быть выполнены с помощью командной консоли Exchange. Для некоторых задач, таких как настройка протокола SSL (Secure Sockets Layer) или задание простых URL-адресов для пользователей, может потребоваться применение диспетчера IIS (Internet Information Services).

## Доступ к Outlook Web App

Вы и ваши пользователи могут входить в Outlook Web App с помощью URL-адреса, который выглядит следующим образом: **https://\<имя\_домена\>/OWA** или **https://mail.\<имя\_домена\>/OWA**

Если, например, домен организации — contoso.com, используйте URL-адрес https://contoso.com/OWA или https://mail.contoso.com/OWA. Подробнее о доступе к Outlook Web App см. [здесь](https://support.microsoft.com/en-us/kb/2897680). Сведения об изменении URL-адреса входа или принудительном перенаправлении на протокол SSL см. в разделе [Упрощение URL-адреса Outlook Web App](simplify-the-outlook-web-app-url-exchange-2013-help.md).

Если вы используете Exchange Online или Office 365 для почты, вы и ваши пользователи могут получить доступ к Outlook Web App на странице **outlook.office365.com/owa**. Кроме того, можно изучить [эту статью](http://go.microsoft.com/fwlink/p/?linkid=402333). Подробнее см. в статьях [Вход в Outlook Web App](http://go.microsoft.com/fwlink/p/?linkid=511341) и [Вход в Office 365](http://go.microsoft.com/fwlink/p/?linkid=522691).

