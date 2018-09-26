---
title: 'Настройка параметров календаря для IMAP4: Exchange 2013 Help'
TOCTitle: Настройка параметров календаря для IMAP4
ms:assetid: 6679c8b2-3f0f-449a-a17c-a7b30001538c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa998606(v=EXCHG.150)
ms:contentKeyID: 50556443
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка параметров календаря для IMAP4

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-11-27_

С помощью командной консоли можно настроить параметры доступа к календарю для пользователей, которые подключаются к своим почтовым ящикам по протоколу IMAP4. Заданные параметры определяют, как пользователи IMAP4 могут получать доступ к календарю и обмениваться данными календаря (например, отправить приглашение на собрание или ответить на него) с другими пользователями.

Дополнительные сведения о IMAP4 см. в разделе [POP3 и IMAP4 в Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Параметры IMAP4" в разделе [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Использование командной консоли Exchange для настройки параметров календаря для службы IMAP4

показано, как включить для пользователей IMAP4 использование стандарта iCalendar для обмена данными календаря.

```powershell
Set-ImapSettings -Identity CAS01 -CalendarItemRetrievalOption iCalendar
```

В этом примере показано, как включить для пользователей IMAP4 доступ к внутренним данным календаря на внутреннем сервере.
```powershell
    Set-ImapSettings -Identity CAS01 -CalendarItemRetrievalOption IntranetUrl 
```
В этом примере показано, как включить для пользователей IMAP4 доступ к данным календаря на внешнем сервере через Интернет.

```powershell
Set-ImapSettings -CalendarItemRetrievalOption InternetUrl
```

В этом примере показано, как включить для пользователей IMAP4 доступ к данным календаря по прямому URL-адресу Outlook Web App. Если используется `Custom`, с помощью параметра *OWAServerUrl* необходимо указать URL-адрес Outlook Web App.

```powershell
Set-Imap4Settings -CalendarItemRetrievalOption Custom -OwaServerUrl "https://OwaServer01"
```

После настройки параметров календаря необходимо перезапустить службы IMAP4. Дополнительные сведения о перезапуске служб IMAP4 см. в разделе [Запуск и остановка служб IMAP4](start-and-stop-the-imap4-services-exchange-2013-help.md).

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-IMAPSettings](https://technet.microsoft.com/ru-ru/library/aa998252\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы проверить, успешно ли установлены параметры календаря, выполните одно из следующих действий.

Выполните в командной консоли следующую команду.

```powershell
Get-ImapSettings | format-list
```

Убедитесь, что параметры календаря указаны правильно.

## Дополнительные сведения

После настройки параметров календаря для службы IMAP4 можно выполнить другие действия.

[Настройка параметров формата получения сообщений для протоколов POP3 и IMAP4](configure-pop3-and-imap4-message-retrieval-format-options-exchange-2013-help.md)

[Установка для протокола IMAP4 пределов времени ожидания подключения](set-connection-time-out-limits-for-imap4-exchange-2013-help.md)

