---
title: 'Настройка политики активации для копии базы данных почтовых ящиков: Exchange 2013 Help'
TOCTitle: Настройка политики активации для копии базы данных почтовых ящиков
ms:assetid: 6b37ed6e-2e36-4688-b485-8fdbb8193ec8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd298046(v=EXCHG.150)
ms:contentKeyID: 50488363
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка политики активации для копии базы данных почтовых ящиков

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-11-02_

*Активация* — это процесс изменения пассивной копии базы данных почтовых ящиков на активную копию. Активация происходит автоматически системой как части базы данных или сервера на другой ресурс при сбое операции, который может быть реализован как вручную администратором как часть операции переключения базы данных или сервере. Блокировка активации базы данных позволяет предотвратить включение ее активной копии во время перехода базы данных или сервера на другой ресурс при сбое.

Необходимы сведения о других задачах управления, связанных с копиями базы данных почтовых ящиков? См. раздел [Управление копиями баз данных почтовых ящиков](managing-mailbox-database-copies-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время выполнения задачи: 1 минута

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Копии базы данных почтовых ящиков» в разделе [Разрешения высокого уровня доступности и устойчивости сайта](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..</td>
</tr>
</tbody>
</table>


## Что необходимо сделать?

## Настройка EAC использовать политики активации для копии базы данных почтовых ящиков

1.  
    
    В Центре администрирования Exchange последовательно выберите пункты **Серверы** \> **Базы данных**.

2.  Выберите базу данных, которую нужно настроить.

3.  
    
    В области сведений в разделе **Копии базы данных** найдите копию базы данных, которую необходимо настроить, и выберите пункт **Приостановить**.

4.  При необходимости добавьте комментарий и установите флажок **Эту копию можно активировать только вручную**.

5.  Щелкните **сохранить** для сохранения изменений конфигурации для копии базы данных почтовых ящиков.

## Использование командной консоли Exchange для приостановки или возобновления активации базы данных

В этом примере показано, как заблокировать активацию копии базы данных DB1 на сервере MBX2.

    Suspend-MailboxDatabaseCopy -Identity DB1\MBX2 -ActivationOnly

В этом примере показано, как возобновить активацию копии базы данных DB1 на сервере MBX2.

    Resume-MailboxDatabaseCopy -Identity DB1\MBX2

Дополнительные сведения о синтаксисе и параметрах см. в разделах [Suspend-MailboxDatabaseCopy](https://technet.microsoft.com/ru-ru/library/dd351074\(v=exchg.150\)) или [Resume-MailboxDatabaseCopy](https://technet.microsoft.com/ru-ru/library/dd335220\(v=exchg.150\)).

## Использование командной консоли для настройки политики активации для сервера

В данном примере выполняется настройка копии баз данных на сервере, как заблокированные для активации MBX2.

    Set-MailboxServer -Identity MBX2 -DatabaseCopyAutoActivationPolicy Blocked

В данном примере выполняется настройка копии баз данных на сервере-заблокирован по MBX3 как нехватки активации сайта.

    Set-MailboxServer -Identity MBX3 -DatabaseCopyAutoActivationPolicy IntrasiteOnly

В данном примере выполняется настройка копии баз данных на сервере, как открытый для активации MBX4.

    Set-MailboxServer -Identity MBX4 -DatabaseCopyAutoActivationPolicy Unrestricted

Дополнительные сведения о синтаксисе и параметрах см. в разделах [Suspend-MailboxDatabaseCopy](https://technet.microsoft.com/ru-ru/library/dd351074\(v=exchg.150\)), [Resume-MailboxDatabaseCopy](https://technet.microsoft.com/ru-ru/library/dd335220\(v=exchg.150\)) и [Set-MailboxServer](https://technet.microsoft.com/ru-ru/library/aa998651\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться, что политика активации успешно настроена, выполните одно из следующих действий.

  - В командной консоли Exchange, выполните следующую команду, чтобы проверить параметры активации копии базы данных почтовых ящиков.
    
        Get-MailboxDatabaseCopyStatus <DatabaseCopyName> | Format-List ActivationSuspended

  - В командной консоли выполните следующую команду, чтобы проверить параметры активации для члена группы обеспечения доступности баз данных.
    
        Get-MailboxServer <ServerName> | Format-List DatabaseCopyAutoActivationPolicy

