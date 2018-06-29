﻿---
title: 'Re-create the Discovery system mailbox: Exchange 2013 Help'
TOCTitle: Re-create the Discovery system mailbox
ms:assetid: 5ae8426b-5661-4ecb-99c4-cdd342107fb1
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg588318(v=EXCHG.150)
ms:contentKeyID: 50488100
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Re-create the Discovery system mailbox

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2018-01-17_

Обнаружение электронных данных на месте использует системный почтовый ящик для хранения метаданных поиска. Его отображаемое имя — **SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}**. Системные почтовые ящики не отображаются в EAC и в списках адресов Exchange, а также редко удаляются случайно.

Если же системный почтовый ящик обнаружения случайно удаляется, диспетчеры обнаружения не смогут вести обнаружение электронных данных на месте и управлять текущими запросами поиска. В этом случае для включения обнаружения следует заново создать этот почтовый ящик.

## Что необходимо знать перед началом работы

  - Предполагаемое время выполнения: 10 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Подраздел "Разрешения подготовки получателей" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Использование командной консоли для повторного создания почтового ящика найденных сообщений

1.  Удалите учетную запись пользователя SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9} из Active Directory (если она существует). По умолчанию программа установки Exchange Server 2013 создает почтовый ящик в контейнере пользователей службы каталогов Active Directory. Подробные инструкции по удалению учетных записей пользователей Active Directory см. в разделе [Удаление учетной записи](https://go.microsoft.com/fwlink/p/?linkid=215850).

2.  Использование командной консоли Exchange для включения системного почтового ящика обнаружения
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Использовать EAC для включения системного почтового ящика обнаружения нельзя.<br />
    Следующую команду необходимо выполнить из той же папке, куда были извлечены установочном носителе Exchange.</td>
    </tr>
    </tbody>
    </table>
    
    Для повторного создания системного почтового ящика обнаружения, выполните следующую команду:
    
        .\Setup /preparead /IAcceptExchangeServerLicenseTerms

## Как проверить, что это работает

Чтобы убедиться в том, что вы успешно создали системный почтовый ящик обнаружения заново, используйте командлет **Get-Mailbox** с параметрами *Arbitration* для извлечения списка системных почтовых ящиков. Просмотрите результаты выполнения команды и убедитесь, что системный почтовый ящик `SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}` был воссоздан.

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

