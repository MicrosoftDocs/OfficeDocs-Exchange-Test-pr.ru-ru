---
title: 'Настройка параметров календаря для службы POP3: Exchange 2013 Help'
TOCTitle: Настройка параметров календаря для службы POP3
ms:assetid: ac3d60a0-8697-4c06-9e93-f8d2c4b157b6
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124133(v=EXCHG.150)
ms:contentKeyID: 50556427
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка параметров календаря для службы POP3

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-11-27_

Командную консоль можно использовать для настройки параметров доступа для пользователей, которые подключаются к своим почтовым ящикам с помощью POP3. Указанные параметры определяют, каким образом пользователи POP3 могут получить доступ к календарю и обмениваться данными календаря (например, отправлять и отвечать на приглашения на собрания) с другими пользователями.

Дополнительные сведения относительно POP3 см. в разделе [POP3 и IMAP4 в Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Параметры POP3" в разделе [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Настройка параметров календаря для службы POP3 с помощью командной консоли

В этом примере показано, как включить для пользователей POP3 использование стандартного способа обмена данными календаря — iCalendar.

    Set-PopSettings -Identity CAS01 -CalendarItemRetrievalOption iCalendar

В этом примере пользователи POP3 могут получать доступ к данным календаря с внутреннего сервера.

    Set-PopSettings -Identity CAS01 -CalendarItemRetrievalOption IntranetUrl 

В этом примере пользователи POP3 могут получать доступ к внутренним данным календаря из Интернета или с внешнего сервера.

    Set-PopSettings -CalendarItemRetrievalOption InternetUrl

В этом примере пользователи POP3 могут получать доступ к данным календаря по прямому URL-адресу Outlook Web App. Если используется `Custom`, необходимо указать URL-адрес Outlook Web App с помощью параметра *OWAServerUrl*.

    Set-PopSettings -CalendarItemRetrievalOption Custom -OwaServerUrl "https://OwaServer01"

После указания параметров календаря для службы POP3 необходимо перезапустить службу POP3. Дополнительные сведения о перезапуске службы POP3 см. в разделе [Запуск и остановка служб POP3](start-and-stop-the-pop3-services-exchange-2013-help.md).

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-POPSettings](https://technet.microsoft.com/ru-ru/library/aa997154\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы проверить, успешно ли установлены параметры календаря, выполните одно из следующих действий.

Выполните в командной консоли следующую команду.

    Get-PopSettings | format-list

Убедитесь, что параметры календаря указаны правильно.

## Дополнительные сведения

После настройки параметров календаря для POP3 можно выполнить следующие действия:

[Настройка параметров формата получения сообщений для протоколов POP3 и IMAP4](configure-pop3-and-imap4-message-retrieval-format-options-exchange-2013-help.md)

[Задайте ограничения времени ожидания подключения для протокола POP3](set-connection-time-out-limits-for-pop3-exchange-2013-help.md)

