---
title: 'Active Directory: определение проблемы с помощью автоматических проверок'
TOCTitle: Помощь в определении проблемы с помощью автоматических проверок — Active Directory
ms:assetid: af08e7a1-775a-4e56-a6fe-4ffc10460514
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn793979(v=EXCHG.150)
ms:contentKeyID: 62633050
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Помощь в определении проблемы с помощью автоматических проверок — Active Directory

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Проверки, описанные на этой странице, помогут вам определить некоторые распространенные проблемы при настройке. Вы можете воспользоваться автоматическими проверками ниже, чтобы подтвердить правильность конфигурации и обновить среду.

Если у вас уже есть учетная запись Office 365, нажмите кнопку **Вход**. Вам не понадобится учетная запись Azure ID. Учетная запись пользователя может потребоваться снова при запуске проверок. В этом случае понадобится ваша учетная запись пользователя в формате имя\_пользователя@имя\_входа\_office365login.домен и ваш пароль.

## Необходимые условия

Мы проверим, установлены ли Помощник по входу в Azure Active Directory и Модуль Azure Active Directory для Windows PowerShell.

Помощник по входу в Azure Active Directory поставляется как две версии: [32-разрядная версия](https://go.microsoft.com/fwlink/?linkid=286261) и [64-разрядный выпуск](https://go.microsoft.com/fwlink/?linkid=286262).

Модуль Azure Active Directory для Windows PowerShell поставляется как две версии: [32-разрядная версия](https://go.microsoft.com/fwlink/?linkid=286258) и [64-разрядный выпуск](https://go.microsoft.com/fwlink/?linkid=286259).

## Проверки Active Directory


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
<td><p>Версия Exchange</p></td>
<td><p>Я не знаю, установлен ли локальный сервер Exchange Server или какая его версия установлена.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834879">Выполнять эту проверку</a></p></td>
</tr>
<tr class="odd">
<td><p>Учетные данные</p></td>
<td><p>Не знаю, правильные ли у меня учетные данные для входа в Office 365</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834880">Выполнять эту проверку</a></p></td>
</tr>
<tr class="even">
<td><p>Средства сторонних производителей</p></td>
<td><p>Я не знаю, какие приложения от сторонних производителей установлены в моей среде обмена сообщениями.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834907">Выполнять эту проверку</a></p></td>
</tr>
<tr class="odd">
<td><p>Общие почтовые ящики</p></td>
<td><p>Мне хотелось бы установить, кто управляет почтовыми ящиками для других (осуществляет делегирование).</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834917">Выполнять эту проверку</a></p></td>
</tr>
</tbody>
</table>

