---
title: 'Ограничения общедоступных папок: Exchange 2013 Help'
TOCTitle: Ограничения общедоступных папок
ms:assetid: 709b075e-9584-484b-bcaa-e781c26497b4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn594582(v=EXCHG.150)
ms:contentKeyID: 61170907
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ограничения общедоступных папок

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

В Exchange Server 2013 мы отошли от использования традиционной архитектуры баз данных для общих папок в пользу архитектуры почтовых ящиков. Этот переход позволяет общим папкам использовать такие возможности, как группа доступности базы данных и другие функции почтового ящика, разрабатываемые в течение многих лет. Тем не менее, следует учитывать новые ограничения и вопросы производительности. В этом документе мы предоставляем инструкции высокого уровня для имеющихся в вашем распоряжении параметров конфигурации, которые способны повлиять на производительность и подключение общих папок.

## Ограничения

В таблице ниже перечислены ограничения для общих папок на локальном сервере Exchange Server 2013. Если ограничения специально не указаны в качестве рекомендуемых, представленные ниже значения являются поддерживаемыми ограничениями для общих папок.

> [!IMPORTANT]  
> Сведения об ограничениях Exchange Online для Office 365 см. в статье <a href="https://go.microsoft.com/fwlink/?linkid=391188">Ограничения Exchange Online</a>.



<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Элемент</th>
<th>Ограничения</th>
<th>Примечания</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Общее число почтовых ящиков общедоступных папок</p></td>
<td><p>100</p></td>
<td><p>Хотя вы можете создать более 100 почтовых ящиков общедоступных папок, на эту возможность не распространяется поддержка. <a href="https://docs.microsoft.com/ru-ru/exchange/collaboration-exo/public-folders/create-public-folder-mailbox">Создание почтового ящика общедоступных папок</a></p></td>
</tr>
<tr class="even">
<td><p>Общее число общедоступных папок в иерархии</p></td>
<td><p>1,000,000</p></td>
<td><p>Хотя вы можете создать более 1 000 000 общедоступных папок, эта возможность не поддерживается. При развертывании 100 000 или более общих папок мы рекомендуем изучить раздел <a href="considerations-when-deploying-public-folders-exchange-2013-help.md">Рекомендации по развертыванию общедоступных папок</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Вложенные папки в родительской папке</p></td>
<td><p>10,000</p></td>
<td><p>Хотя вы можете создать более 1000 вложенных папок в родительской папке, это действие не рекомендуется.</p>
<p>Параметр <em>FolderHierarchyChildrenCountReceiveQuota</em> в командлете <a href="https://technet.microsoft.com/ru-ru/library/bb123981(v=exchg.150)">Set-Mailbox</a>.</p></td>
</tr>
<tr class="even">
<td><p>Глубина вложенности папок</p></td>
<td><p>300</p></td>
<td><p>Глубина папок — это число уровней вложенных папок, допустимое в одной ветви дерева общедоступной папки. Параметр <em>FolderHierarchyDepthRecieveQuota</em> в командлете <a href="https://technet.microsoft.com/ru-ru/library/bb123981(v=exchg.150)">Set-Mailbox</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Максимальное число сообщений на общую папку</p></td>
<td><p>1 000 000</p></td>
<td><p>Параметр <em>MailboxMessagesPerFolderCountRecieveQuota</em> в командлете <a href="https://technet.microsoft.com/ru-ru/library/bb123981(v=exchg.150)">Set-Mailbox</a>.</p></td>
</tr>
<tr class="even">
<td><p>Максимальный размер отдельной общедоступной папки</p></td>
<td><p>10 ГБ</p></td>
<td><p>В это ограничение не входят вложенные папки в одной папке.</p>
<p><a href="configure-storage-quotas-for-a-mailbox-exchange-2013-help.md">Настройка квот хранилища для почтового ящика</a></p></td>
</tr>
<tr class="odd">
<td><p>Размер почтового ящика общедоступной папки</p></td>
<td><p>100 ГБ</p></td>
<td><p><a href="configure-storage-quotas-for-a-mailbox-exchange-2013-help.md">Настройка квот хранилища для почтового ящика</a></p></td>
</tr>
<tr class="even">
<td><p>Количество входов пользователей на почтовый ящик общедоступных папок</p></td>
<td><p>2000 параллельных входов пользователей</p></td>
<td><p>Рекомендуем настроить иерархию так, чтобы на один почтовый ящик общедоступных папок приходилось не более 2000 пользователей. Например, если у вас 20 000 пользователей, у вас должно быть 10 почтовых ящиков общедоступных папок.</p></td>
</tr>
<tr class="odd">
<td><p>Хранение перемещенных элементов</p></td>
<td><p>Рекомендуемый срок составляет 14 дней</p></td>
<td><p>Используйте параметр <em>DefaultPublicFolderMovedItemRetention</em> в командлете <strong>Set-OrganizationConfig</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Ограничения времени хранения</p></td>
<td><p>Рекомендуем установить для этого параметра то же значение, что по умолчанию используется для обычных почтовых ящиков.</p></td>
<td><p>Эти параметры можно установить на следующих уровнях.</p>
<ul>
<li><p><strong>Организационный уровень:</strong> параметр <em>DefaultPublicFolderAgeLimit</em> в командлете <strong>Set-OrganizationConfig</strong>.</p></li>
<li><p><strong>Уровень почтового ящика:</strong> параметр <em>AgeLimit</em> в командлете <strong>Set-Mailbox</strong>.</p></li>
<li><p><strong>Уровень папки:</strong> параметр <em>AgeLimit</em> в командлете <strong>Set-PublicFolder</strong>.</p></li>
</ul>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Хранение удаленного элемента</p></td>
<td><p>Рекомендуем установить для этого параметра то же значение, что по умолчанию используется для обычных почтовых ящиков.</p></td>
<td><p>Эти параметры можно установить на следующих уровнях.</p>
<ul>
<li><p><strong>Организационный уровень:параметр</strong> <em>DefaultPublicFolderMovedItemRetention</em> в командлете <strong>Set-OrganizationConfig</strong>.</p></li>
<li><p><strong>Уровень почтового ящика:</strong> параметр <em>RetainDeletedItemsFor</em> в командлете <strong>Set-Mailbox</strong>.</p></li>
<li><p><strong>Уровень папки:</strong> параметр <em>RetainDeleteItemsFor</em> в командлете <strong>Set-PublicFolder</strong>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Максимальное количество общедоступных папок, которое можно перенести в Exchange 2013</p></td>
<td><p>500,000</p></td>
<td><p>Это максимальное количество папок, которое можно перенести в Exchange 2013 из прежних версий Exchange за один раз. Дополнительные сведения о переносе общедоступных папок см. в статье <a href="use-batch-migration-to-migrate-public-folders-to-exchange-2013-from-previous-versions-exchange-2013-help.md">Использование пакетной миграции для переноса общедоступных папок в Exchange 2013 из предыдущих версий</a>.</p></td>
</tr>
</tbody>
</table>

