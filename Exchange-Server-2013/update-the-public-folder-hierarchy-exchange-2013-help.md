---
title: 'обновлять иерархию общих папок;: Exchange 2013 Help'
TOCTitle: обновлять иерархию общих папок;
ms:assetid: a7b2fb51-0207-4d7d-938d-466ae110bb90
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ945055(v=EXCHG.150)
ms:contentKeyID: 52059168
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# обновлять иерархию общих папок;

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2014-04-03_

Обновление иерархии общедоступных папок необходимо лишь в том случае, когда вы хотите вручную вызвать синхронизатор иерархии и помощник по обслуживанию почтовых ящиков. Они вызываются не меньше одного раза в сутки для каждого почтового ящика общей папки организации. Если какие-либо пользователи подключены ко вторичному почтовому ящику с помощью Microsoft Outlook или клиента веб-служб Microsoft Exchange, вызов синхронизатора иерархии выполняется каждые 15 минут.

Дополнительные сведения о задачах управления, связанных с общедоступными папками в Exchange Online, см. в разделе [Процедуры с общедоступными папками в Office 365 и Exchange Online](https://technet.microsoft.com/ru-ru/library/jj966272\(v=exchg.150\)).

Дополнительные сведения о задачах управления, связанных с общедоступными папками в Exchange Server 2013, см. в разделе [Процедуры с общедоступными папками](public-folder-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Общедоступные папки" в разделе [Разрешения на общий доступ и совместную работу](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Эта процедура недоступна в Центре администрирования Exchange. Необходимо использовать командную консоль.

  - Мы советуем при запуске этой команды с параметром *InvokeSynchronizer* использовать параметр *SuppressStatus*. Если не использовать этот параметр в команде, то выходные данные будут отображать сообщения о состоянии каждые 3 секунды в течение одной минуты. Пока не пройдет минута, вы не сможете использовать этот экземпляр командной консоли.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

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


## обновлять иерархию общих папок;

В этом примере показано обновление иерархии общедоступной папки в почтовом ящике "PF\_marketing", а также отключение возвращаемых данных команды.

    Update-PublicFolderMailbox -Identity PF_marketing -InvokeSynchronizer -SuppressStatus

В этом примере показано обновление всех почтовых ящиков с общедоступными папками и отключение возвращаемых данных команды.

    Get-Mailbox -PublicFolder | Update-PublicFolderMailbox InvokeSynchronizer -SuppressStatus

