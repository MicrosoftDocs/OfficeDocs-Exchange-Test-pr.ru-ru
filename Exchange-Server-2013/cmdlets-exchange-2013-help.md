---
title: 'Командлеты: Exchange 2013 Help'
TOCTitle: Командлеты
ms:assetid: 1d741dea-1eb8-4909-850f-63d4efaa1a32
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa996589(v=EXCHG.150)
ms:contentKeyID: 50487622
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Командлеты

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-03-09_

*Командлет* — это наименьшая функциональная единица консоли управления Exchange. Командлет похож на встроенные команды других командных консолей, например на команду `dir` в `cmd.exe`. Так же как и эти команды, командлет можно вызвать напрямую из командной строки командной консоли и запустить в контексте этой консоли, а не как отдельный процесс.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Начиная с Microsoft Exchange Server 2007 способ внутреннего использования командлетов в Exchange 2013 изменился в результате использования функций Windows PowerShell для удаленного взаимодействия. Эти изменения практически не повлияли на способы использования командлетов, однако они предоставили дополнительную гибкость в управлении серверами Exchange.</td>
</tr>
</tbody>
</table>


Командлеты, как правило, предназначены для выполнения повторяющихся задач администрирования. В командной консоли предусмотрено несколько сотен командлетов для выполнения определенных задач управления Exchange. Они доступны в дополнение к системным командлетам, не связанным с Exchange и включенным в базовую версию проекта командной консоли Windows PowerShell. Дополнительные сведения об использовании консоли управления Exchange см. в разделе [Открытие командной консоли Exchange](https://technet.microsoft.com/ru-ru/library/dd638134\(v=exchg.150\)).

Все командлеты в командной консоли представлены в виде пар "глагол-существительное". Глагол и существительное в паре всегда пишутся через дефис (-) без пробелов, и существительное всегда стоит в единственном числе. Глаголом обозначается действие командлета. Существительное относится к объекту, над которым выполняется данное действие. Например, в командлете **Get-SystemMessage** глагол — **Get**, а существительное — **SystemMessage**. В состав всех командлетов командной консоли, отвечающих за определенную функцию, входит одно и то же существительное. В следующей таблице приведены примеры некоторых глаголов, используемых в командной консоли.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>По умолчанию, если глагол опущен, командная консоль подставляет глагол <strong>Get</strong>. Например, при вызове командлета <strong>Mailbox</strong> он будет восприниматься так же, как командлет <strong>Get-Mailbox</strong>.</td>
</tr>
</tbody>
</table>


### Примеры глаголов, используемых в командной консоли Exchange

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Глагол</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Disable</strong></p></td>
<td><p>Командлеты <strong>Disable</strong> изменяют состояние <code>Enabled</code> указанного объекта Exchange на <code>$False</code>. Это не позволяет объекту обрабатывать данные, даже если объект существует.</p></td>
</tr>
<tr class="even">
<td><p><strong>Enable</strong></p></td>
<td><p>Командлеты <strong>Enable</strong> изменяют состояние &quot;Включен&quot; указанного объекта Exchange на <code>$True</code>. Это позволяет объекту обрабатывать данные.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Get</strong></p></td>
<td><p>Командлеты <strong>Get</strong> получают сведения об указанном объекте Exchange.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Большинство командлетов <strong>Get</strong> при их выполнении возвращают только сводную информацию. Для того чтобы командлет <strong>Get</strong> возвращал подробную информацию при запуске команды, необходимо конвейерным образом передать эту команду в командлет <strong>Format-List</strong>. Дополнительные сведения о командлете <strong>Format-List</strong> см. в разделе <a href="working-with-command-output-exchange-2013-help.md">Работа с выходными данными команды</a>. Дополнительные сведения о конвейерной передаче см. в разделе <a href="https://technet.microsoft.com/ru-ru/library/aa998260(v=exchg.150)">Конвейеризация</a>.</td>
</tr>
</tbody>
</table>

</td>
</tr>
<tr class="even">
<td><p><strong>Install</strong></p></td>
<td><p>Командлеты <strong>Install</strong> устанавливают новый объект или функцию на сервер Exchange.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Move</strong></p></td>
<td><p>Командлеты <strong>Move</strong> перемещают указанный объект Exchange из одного контейнера или сервера в другой.</p></td>
</tr>
<tr class="even">
<td><p><strong>New</strong></p></td>
<td><p>Командлеты <strong>New</strong> создают новый объект Exchange.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Remove</strong></p></td>
<td><p>Командлеты <strong>Remove</strong> удаляют указанный объект Exchange.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set</strong></p></td>
<td><p>Командлеты <strong>Set</strong> изменяют свойства существующего объекта Exchange.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Test</strong></p></td>
<td><p>Командлеты <strong>Test</strong> проверяют определенные компоненты Exchange и предоставляют файлы журнала для просмотра.</p></td>
</tr>
<tr class="even">
<td><p><strong>Uninstall</strong></p></td>
<td><p>Командлеты <strong>Uninstall</strong> удаляют объекты или функции с сервера Exchange.</p></td>
</tr>
</tbody>
</table>


В следующем списке приведен пример полного набора командлетов. Этот командлет используется для управления функциями уведомлений о доставке (DSN) и сообщений о квоте почтового ящика в Exchange 2013:

  - **Get-SystemMessage**

  - **New-SystemMessage**

  - **Remove-SystemMessage**

  - **Set-SystemMessage**

