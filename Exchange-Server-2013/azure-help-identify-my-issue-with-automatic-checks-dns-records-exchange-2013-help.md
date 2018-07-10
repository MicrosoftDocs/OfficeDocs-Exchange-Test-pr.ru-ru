---
title: 'Azure: помощь с определением неполадок путем автоматических проверок — записи DNS: Exchange 2013 Help'
TOCTitle: 'Azure: помощь с определением неполадок путем автоматических проверок — записи DNS'
ms:assetid: 1ef42cde-4df4-401a-b8f2-494630996ca8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn793619(v=EXCHG.150)
ms:contentKeyID: 62630009
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Azure: помощь с определением неполадок путем автоматических проверок — записи DNS

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Одна из самых распространенных проблем настройки конфигурации — неправильная настройка записей DNS. Вы можете использовать автоматические проверки, приведенные ниже, для проверки своей конфигурации и обновления среды.

Если у вас уже есть учетная запись Office 365, выберите "Войти". Учетная запись Azure ID не требуется. Учетная запись пользователя может потребоваться снова при запуске проверок. В этом случае введите учетные данные в формате имя\_пользователя@имя\_входа\_office365login.домен и ваш пароль.

## Необходимые условия

Мы проверим, установлены ли Помощник по входу в Azure Active Directory и Модуль Azure Active Directory для Windows PowerShell.

Помощник по входу в Azure Active Directory поставляется как две версии: [32-разрядная версия](https://go.microsoft.com/fwlink/?linkid=286261) и [64-разрядный выпуск](https://go.microsoft.com/fwlink/?linkid=286262).

Модуль Azure Active Directory для Windows PowerShell поставляется как две версии: [32-разрядная версия](https://go.microsoft.com/fwlink/?linkid=286258) и [64-разрядный выпуск](https://go.microsoft.com/fwlink/?linkid=286259).

## Проверка записей DNS


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Приложение</p></td>
<td><p>Проблема</p></td>
<td><p>Проверка</p></td>
</tr>
<tr class="even">
<td><p>Домены</p></td>
<td><p>Похоже, мой пользовательский домен (например, contoso.com) не настроен для использования в Office 365.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834905">Выполнять эту проверку</a></p></td>
</tr>
<tr class="odd">
<td><p>Домены</p></td>
<td><p>Похоже, мой пользовательский домен (например, contoso.com) не настроен для использования в Office 365 (использовалась запись CNAME).</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834905">Выполнять эту проверку</a></p></td>
</tr>
<tr class="even">
<td><p>Домены</p></td>
<td><p>Похоже, мой пользовательский домен (например, contoso.com) не настроен для использования в Office 365 (использовалась запись TXT).</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834905">Выполнять эту проверку</a></p></td>
</tr>
<tr class="odd">
<td><p>Обмен мгновенными сообщениями</p></td>
<td><p>У пользователей возникают проблемы с клиентом Lync.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834901">Выполнять эту проверку</a></p></td>
</tr>
<tr class="even">
<td><p>Обмен мгновенными сообщениями</p></td>
<td><p>Клиенты Lync пользователей не работают с другими организациями.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834902">Выполнять эту проверку</a></p></td>
</tr>
<tr class="odd">
<td><p>Почта</p></td>
<td><p>Не удается наладить автоматическую настройку Outlook с Office 365.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834897">Выполнять эту проверку</a></p></td>
</tr>
<tr class="even">
<td><p>Почта</p></td>
<td><p>Электронная почта не маршрутизируется в Office 365.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834898">Выполнять эту проверку</a></p></td>
</tr>
<tr class="odd">
<td><p>Почта</p></td>
<td><p>На почту организации приходит очень много нежелательных сообщений.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834903">Выполнять эту проверку</a></p></td>
</tr>
<tr class="even">
<td><p>Почта</p></td>
<td><p>Гибридная среда Exchange не работает.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834904">Выполнять эту проверку</a></p></td>
</tr>
</tbody>
</table>

