---
title: 'Включение и отключение расшифровки отчета журнала: Exchange 2013 Help'
TOCTitle: Включение и отключение расшифровки отчета журнала
ms:assetid: 1dedbe73-2c1a-4b14-8799-5091aaec7965
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638092(v=EXCHG.150)
ms:contentKeyID: 50487588
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Включение и отключение расшифровки отчета журнала

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Включение расшифровки отчета журнала позволяет агент ведения журнала присоединение расшифрованного копию защищенное сообщение журнала отчетов. Прежде чем включить расшифровка отчетов, необходимо добавить почтовый ящик федеративных доставки для группы пользователей, настроенной на сервере [Службы управления правами Active Directory (AD RMS)](https://technet.microsoft.com/en-us/library/hh831364.aspx) .

Дополнительные задачи управления, связанные с управлением правами на доступ к данным (IRM), см. в разделе [Сведения о процедуры управления правами](information-rights-management-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 1 минута

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Защита прав" в разделе [Политика обмена сообщениями и разрешения для соответствия требованиям](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Участникам группы суперпользователей предоставляется лицензия на частное использование при запросе лицензии из кластера AD RMS. Это позволит им расшифровывать все содержимое, защищенное с помощью служб управления правами и созданное этим кластером AD RMS.

  - Кластер службы управления правами Active Directory нужно установить в лесу Active Directory.

  - В группу суперпользователей AD RMS добавлен почтовый ящик федеративной доставки. Дополнительные сведения см. в разделе [Добавление федеративного почтового ящика в группу суперпользователей службы управления правами Active Directory](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md).

  - Центр администрирования Exchange (EAC) нельзя использовать для включения функций расшифровки отчета по журналу. Необходимо использовать командную консоль.

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


## Что необходимо сделать?

## Использование командной консоли Exchange для включения расшифровки отчета по журналу

В этом примере показано, как включить расшифровку отчета по журналу для организации Exchange.

    Set-IRMConfiguration -JournalReportDecryptionEnabled $true

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-IRMConfiguration](https://technet.microsoft.com/ru-ru/library/dd979792\(v=exchg.150\)).

## Использование командной консоли Exchange для отключения расшифровки отчета по журналу

В этом примере показано, как отключить расшифровку отчета по журналу для организации Exchange.

    Set-IRMConfiguration -JournalReportDecryptionEnabled $false

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-IRMConfiguration](https://technet.microsoft.com/ru-ru/library/dd979792\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться, что расшифровка отчета по журналу включена или отключена, выполните командлет **Get-IRMConfiguration** и проверьте значение свойства *JournalDecryptionEnabled*.

Пример проверки конфигурации IRM см. в разделе [Examples](https://technet.microsoft.com/ru-ru/e1821219-fe18-4642-a9c2-58eb0aadd61a\(exchg.150\)#examples) в статье **Get-IRMConfiguration**.

