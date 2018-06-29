---
title: 'Recreating arbitration mailboxes: Exchange 2013 Help'
TOCTitle: Recreating arbitration mailboxes
ms:assetid: bb6b8524-aaee-4be8-a04e-e61cd2ab3465
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Mt829264(v=EXCHG.150)
ms:contentKeyID: 74518158
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Recreating arbitration mailboxes

 

_**Последнее изменение раздела:**2018-01-17_

**Сводка.** О почтовых ящиках арбитража в Exchange 2013 и о том, как создавать их повторно.

В Exchange 2013 доступны пять системных почтовых ящиков, называемых *почтовыми ящиками арбитража*. Почтовые ящики арбитража используются для хранения различных типов системных данных и управления рабочим процессом утверждения сообщений. Диаграммы ниже описывают все типы почтовых ящиков арбитража и их предназначение.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя почтового ящика арбитража</th>
<th>Отображаемое имя</th>
<th>Имеющиеся возможности</th>
<th>Функция</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042</p></td>
<td><p>Федеративный почтовый ящик Microsoft Exchange</p></td>
<td><p>{}</p></td>
<td><p>В этом почтовом ящике хранятся данные, которые используются для обслуживания федерации между различными организациями Exchange. В их число входят службы управления правами, зонды для мониторинга гибридных потоков обработки почты, отклики, уведомления, серверные архивы, управление записями сообщений, а также сведения о доступности в гибридной среде.</p></td>
</tr>
<tr class="even">
<td><p>SystemMailbox{1f05a927-9350-4efe-a823-5529c2d64109}</p></td>
<td><p>Помощник по утверждению Microsoft Exchange</p></td>
<td><p>{}</p></td>
<td><p>Этот почтовый ящик подготовлен к использованию инфраструктурой утверждения Exchange для контроля получателей и работы с автоматическими групповыми запросами на утверждение.</p></td>
</tr>
<tr class="odd">
<td><p>Migration.8f3e7716-2011-43e4-96b1-aba62d229136</p></td>
<td><p>Миграция Microsoft Exchange</p></td>
<td><p>{OrganizationCapabilityManagement}</p></td>
<td><p>Здесь хранятся данные службы миграции Exchange, которые используются при перемещении почтовых ящиков в пакетах.</p></td>
</tr>
<tr class="even">
<td><p>SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}</p></td>
<td><p>Microsoft Exchange</p></td>
<td><p>{OrganizationCapabilityUMDataStorage}</p></td>
<td><p>Системный почтовый ящик обнаружения.</p>
<p>Подготовлен для использования компонентом обнаружения электронных данных, с помощью которого ответственный за обеспечение соответствия требованиям ищет сообщения, задавая условия выбора. Этот почтовый ящик также используется единой системой обмена сообщениями для хранения имеющихся файлов консоли этой системы, а также других данных.</p></td>
</tr>
<tr class="odd">
<td><p>SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}</p></td>
<td><p>Microsoft Exchange</p></td>
<td><p>{OrganizationCapabilityUMGrammarReady, OrganizationCapabilityPstProvider, OrganizationCapabilityMessageTracking, OrganizationCapabilityMailRouting, OrganizationCapabilityClientExtensions, OrganizationCapabilityGMGen, OrganizationCapabilityOABGen, OrganizationCapabilityUMGrammar}</p></td>
<td><p>Это так называемый почтовый ящик организации. Он используется для создания автономных адресных книг. Чтобы сбалансировать нагрузку при формировании автономной адресной книги в организации (в том числе для отдаленных друг от друга сайтов), вы можете создать дополнительные почтовые ящики организации.</p></td>
</tr>
</tbody>
</table>


Если вам нужно повторно создать один из нескольких таких почтовых ящиков арбитража, обратитесь к инструкциям ниже.

## Что необходимо знать перед началом работы

  - Предполагаемое время выполнения: 10 минут на процедуру.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Раздел "Разрешения подготовки получателей" в статье [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Повторное создание почтового ящика арбитража с помощью командной консоли Exchange

Воспользуйтесь приведенными ниже инструкциями, чтобы повторно создать почтовый ящик арбитража определенного типа.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Все действия, описанные в приведенных ниже разделах, нужно выполнять в каталоге, в который вы извлекли данные установочного носителя Exchange.</td>
</tr>
</tbody>
</table>


## Повторное создание федеративного почтового ящика Microsoft Exchange

Чтобы повторно создать почтовый ящик арбитража FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042, выполните приведенные ниже действия.

1.  При отсутствии какого-либо почтового ящика арбитража запустите следующую команду:
    
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms

2.  В командной консоли Exchange запустите следующую команду:
    
        Enable-Mailbox -Arbitration -Identity "FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042"

## Повторное создание почтового ящика помощника по утверждению Microsoft Exchange

Чтобы повторно создать почтовый ящик арбитража SystemMailbox{1f05a927-9350-4efe-a823-5529c2d64109}, выполните приведенные ниже действия.

1.  При отсутствии какого-либо почтового ящика арбитража запустите следующую команду:
    
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms

2.  В командной консоли Exchange запустите следующую команду:
    
        Get-User | Where-Object {$_.Name -like "SystemMailbox{1f05a927-7709-4e35-9dbe-d0f608fb781a}"} | Enable-Mailbox -Arbitration

## Как повторно создать почтовый ящик миграции в Microsoft Exchange

Чтобы повторно создать почтовый ящик арбитража Migration.8f3e7716-2011-43e4-96b1-aba62d229136, выполните приведенные ниже действия.

1.  При отсутствии какого-либо почтового ящика арбитража запустите следующую команду:
    
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms

2.  В командной консоли Exchange запустите следующую команду:
    
        Enable-Mailbox -Arbitration -Identity "Migration.8f3e7716-2011-43e4-96b1-aba62d229136"

3.  В командной консоли Exchange задайте параметр "Имеющиеся возможности" (msExchCapabilityIdentifiers), запустив следующую команду:
    
        Set-Mailbox "Migration.8f3e7716-2011-43e4-96b1-aba62d229136" -Arbitration -Management:$True -Force

## Как повторно создать системный почтовый ящик обнаружения в Microsoft Exchange

Чтобы повторно создать почтовый ящик арбитража SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}, выполните указанные ниже действия.

1.  Выполните следующую команду:
    
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms

## Как повторно создать почтовый ящик организации для автономных адресных книг в Microsoft Exchange

Чтобы повторно создать почтовый ящик арбитража SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}, выполните указанные ниже действия.

1.  При отсутствии какого-либо почтового ящика арбитража запустите следующую команду:
    
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms

2.  В командной консоли Exchange запустите следующую команду:
    
        Enable-Mailbox -Arbitration -Identity "SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}"

3.  В командной консоли Exchange задайте параметр "Имеющиеся возможности" (msExchCapabilityIdentifiers), запустив следующую команду:
    
        Get-Mailbox "SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}" -Arbitration | Set-Mailbox -Arbitration -UMGrammar:$True -OABGen:$True -GMGen:$True -ClientExtensions:$True -MessageTracking:$True -PstProvider:$True -MaxSendSize 1GB -Force

Если вы выполнили команду `$OABMBX = Get-Mailbox "SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}" -Arbitration (Get-ADUser $OABMBX.SamAccountName -Properties *).msExchCapabilityIdentifiers`, то после завершения увидите отсутствие 46, 47 и 51. Чтобы снова добавить все возможности, выполните следующую команду:

    Set-ADUser $OABMBX.SamAccountName -Add @{"msExchCapabilityIdentifiers"="40","42","43","44","47","51","52","46"}

## Как проверить, все ли работает?

Чтобы убедиться в том, что вы повторно создали почтовый ящик арбитража, используйте командлет **Get-Mailbox** с параметром *Arbitration* для извлечения списка системных почтовых ящиков.

    Get-Mailbox -Arbitration | Format-Table Name, DisplayName

Просмотрите результаты выполнения команды, чтобы убедиться в том, что необходимый системный почтовый ящик был создан. Для этого вы можете использовать имя или отображаемое имя из таблицы выше.

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>

