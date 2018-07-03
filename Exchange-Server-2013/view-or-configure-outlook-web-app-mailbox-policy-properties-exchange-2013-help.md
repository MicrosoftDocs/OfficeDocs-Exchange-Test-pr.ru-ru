﻿---
title: 'Просмотр и настройка свойств политики почтовых ящиков Outlook Web App: Exchange 2013 Help'
TOCTitle: Просмотр и настройка свойств политики почтовых ящиков Outlook Web App
ms:assetid: be012ffe-8fdb-4fb7-aebd-78b3a55593fa
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd351097(v=EXCHG.150)
ms:contentKeyID: 50489014
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Просмотр и настройка свойств политики почтовых ящиков Outlook Web App

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2016-04-13_

Создав политику почтовых ящиков Outlook Web App, можно настроить множество параметров, чтобы управлять возможностями, доступными пользователям в Outlook Web App. Например, можно включить или отключить правила для папки входящих сообщений, либо создать список типов файлов, допустимых во вложениях.

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 3 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Политики почтовых ящиков Outlook Web App" в разделе [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

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

## Просмотр или настройка политик почтовых ящиков Outlook Web App с помощью Центра администрирования Exchange (EAC)

1.  В Центре администрирования Exchange выберите пункты **Разрешения** \> **Политики Outlook Web App**.

2.  В области результатов щелкните для выбора политики почтовых ящиков, которую необходимо просмотреть или настроить.

3.  Нажмите кнопку **Изменить**.

4.  
    
    На вкладке **Общие** можно просмотреть и изменить имя политики.

5.  
    
    На вкладке **Функции** включайте или отключайте функции с помощью флажков. По умолчанию отображаются наиболее часто используемые компоненты. Чтобы открыть весь список компонентов, которые можно включить или выключить, выберите команду **Дополнительные параметры**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Параметры компонентов для политик почтовых ящиков Outlook Web App имеют приоритет над параметрами виртуальных каталогов Outlook Web App. Параметры сегментации для отдельных пользователей можно изменить, используя командлет <strong>Set-CASMailbox</strong> в консоли.</td>
    </tr>
    </tbody>
    </table>


6.  
    
    На вкладке **Доступ к файлам** с помощью флажков **Прямой доступ к файлам** настройте доступ к файлам и параметры просмотра для пользователей. Доступ к файлам позволяет пользователю открывать и просматривать содержимое файлов, вложенных в сообщение электронной почты.
    
    Доступ к файлам может контролироваться на основе того, вошел пользователь в систему на общедоступном или частном компьютере. Пользователи имеют возможность выбирать доступ к частному компьютеру или к общедоступному компьютеру только в случае использования проверки подлинности на основе форм. Все другие виды проверки подлинности по умолчанию относятся к доступу с частного компьютера.

7.  На вкладке **Автономный доступ** настройте доступность в автономном режиме с помощью переключателей.

8.  Нажмите кнопку **Сохранить**, чтобы обновить политику.

## Использование командной консоли для настройки политик почтовых ящиков Outlook Web App

В этом примере разрешается доступ к календарю в политике почтовых ящиков по умолчанию.

    Set-OwaMailboxPolicy -Identity Default -CalendarEnabled $true

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-OwaMailboxPolicy](https://technet.microsoft.com/ru-ru/library/dd297989\(v=exchg.150\)).

## Использование командной консоли для просмотра политик почтовых ящиков Outlook Web App

В этом примере выполняется получение свойств политики почтовых ящиков Outlook Web App с именем `Executives` в организации `Fabrikam`.

    Get-OwaMailboxPolicy -Identity Fabrikam\Executives

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-OwaMailboxPolicy](https://technet.microsoft.com/ru-ru/library/dd351095\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться, что политика почтовых ящиков Outlook Web App изменена успешно, выполните следующие действия.

1.  В Центре администрирования Exchange (EAC) выберите **Разрешения** \> **Политики Outlook Web App**, после чего выберите определенную политику почтовых ящиков Outlook Web App.

2.  Чтобы просмотреть свойства политики почтовых ящиков, нажмите кнопку **Изменить**.

3.  Нажмите кнопку **Отмена** или **Сохранить**, чтобы закрыть страницу свойств.
