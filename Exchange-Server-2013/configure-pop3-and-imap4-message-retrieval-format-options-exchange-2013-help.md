---
title: 'Настройка параметров формата получения сообщений для протоколов POP3 и IMAP4: Exchange 2013 Help'
TOCTitle: Настройка параметров формата получения сообщений для протоколов POP3 и IMAP4
ms:assetid: 481096e0-4492-46c2-8ca8-bdf84a84531e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa997869(v=EXCHG.150)
ms:contentKeyID: 50556410
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка параметров формата получения сообщений для протоколов POP3 и IMAP4

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

Можно настроить формат извлечения сообщений для пользователей, которые подключаются к своей электронной почте по протоколам POP3 и IMAP4. Параметры извлечения сообщений можно настроить на уровне сервера с помощью центра администрирования Exchange или командной консоли, а также на уровне пользователя с использованием командной консоли.

Дополнительные сведения относительно POP3 и IMAP4 см. в разделе [POP3 и IMAP4 в Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье записи "Параметры POP3" и "Параметры IMAP4" в разделе [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Что необходимо сделать?

## Установка формата извлечения сообщений POP3 на уровне сервера

## Использование центра администрирования Exchange для установки формата извлечения сообщений POP3 на уровне сервера

1.  В центре администрирования Exchange перейдите к разделу **Серверы** \> **Серверы**.

2.  В списке серверов выберите сервер клиентского доступа и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице свойств сервера щелкните **POP3**.

4.  В разделе **MIME-формат сообщений** выберите один из следующих параметров.
    
      - Text
    
      - HTML
    
      - HTML и замещающий текст
    
      - Текст с разметкой
    
      - Текст с разметкой и текст
    
      - Наилучший формат текста
    
      - TNEF

5.  Нажмите кнопку **Сохранить**.

После установки параметров формата извлечения сообщений для протокола POP3 необходимо перезапустить службы POP3, чтобы изменения вступили в силу. Дополнительные сведения о перезапуске служб POP3 см. в разделе [Запуск и остановка служб POP3](start-and-stop-the-pop3-services-exchange-2013-help.md).

## Использование командной консоли для установки формата извлечения сообщений POP3 на уровне сервера

В этом примере устанавливается формат извлечения сообщений "Только текст" для всех пользователей POP3 на сервере CAS01.

    Set-PopSettings -Identity CAS01 -MessageRetrievalMimeFormat TextOnly

Можно выбрать следующие параметры. В качестве значения параметра *MessageRetrievalMimeFormat* можно указать число или текстовую строку.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>формат сообщений</strong></p></td>
<td><p><strong>Значение</strong></p></td>
</tr>
<tr class="even">
<td><p>Text</p></td>
<td><p><code>0</code> или <code>TextOnly</code></p></td>
</tr>
<tr class="odd">
<td><p>HTML</p></td>
<td><p><code>1</code> или <code>HtmlOnly</code></p></td>
</tr>
<tr class="even">
<td><p>HTML и замещающий текст</p></td>
<td><p><code>2</code> или <code>HtmlAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Текст с разметкой</p></td>
<td><p><code>3</code> или <code>TextEnriched</code></p></td>
</tr>
<tr class="even">
<td><p>Текст с разметкой и текст</p></td>
<td><p><code>4</code> или <code>TextEnrichedAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Наилучший формат текста</p></td>
<td><p><code>5</code> или <code>BestBodyFormat</code></p></td>
</tr>
<tr class="even">
<td><p>TNEF</p></td>
<td><p><code>6</code> или <code>Tnef</code></p></td>
</tr>
</tbody>
</table>


После установки параметров формата извлечения сообщений для протокола POP3 необходимо перезапустить службы POP3, чтобы изменения вступили в силу. Дополнительные сведения о перезапуске служб POP3 см. в разделе [Запуск и остановка служб POP3](start-and-stop-the-pop3-services-exchange-2013-help.md).

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-POPSettings](https://technet.microsoft.com/ru-ru/library/aa997154\(v=exchg.150\)).

## Как проверить, что все получилось?

Выполните следующие действия, чтобы убедиться, что параметры извлечения сообщений POP3 на сервере успешно установлены.

1.  Выполните в командной консоли следующую команду.
    
        Get-PopSettings | format-list

2.  Проверьте правильность параметра *MessageRetrievalMimeFormat*.

## Установка формата извлечения сообщений IMAP4 на уровне сервера

## Использование центра администрирования Exchange для установки формата извлечения сообщений IMAP4 на уровне сервера

1.  В центре администрирования Exchange перейдите к разделу **Серверы** \> **Серверы**.

2.  В списке серверов выберите сервер клиентского доступа и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице свойств сервера щелкните **IMAP4**.

4.  В разделе **MIME-формат сообщений** выберите один из следующих параметров.
    
      - Text
    
      - HTML
    
      - HTML и замещающий текст
    
      - Текст с разметкой
    
      - Текст с разметкой и текст
    
      - Наилучший формат текста
    
      - TNEF

5.  Нажмите кнопку **Сохранить**.

После установки параметров формата извлечения сообщений для протокола IMAP4 необходимо перезапустить службы IMAP4, чтобы изменения вступили в силу. Дополнительные сведения о перезапуске служб IMAP4 см. в разделе [Запуск и остановка служб IMAP4](start-and-stop-the-imap4-services-exchange-2013-help.md).

## Использование командной консоли для установки формата извлечения сообщений IMAP4 на уровне сервера

В этом примере устанавливается формат извлечения сообщений "Только текст" для всех пользователей IMAP4 на сервере CAS01.

    Set-ImapSettings -Identity CAS01 -MessageRetrievalMimeFormat TextOnly

Можно выбрать следующие параметры. В качестве значения параметра *MessageRetrievalMimeFormat* можно указать число или текстовую строку.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>формат сообщений</strong></p></td>
<td><p><strong>Значение</strong></p></td>
</tr>
<tr class="even">
<td><p>Text</p></td>
<td><p><code>0</code> или <code>TextOnly</code></p></td>
</tr>
<tr class="odd">
<td><p>HTML</p></td>
<td><p><code>1</code> или <code>HtmlOnly</code></p></td>
</tr>
<tr class="even">
<td><p>HTML и замещающий текст</p></td>
<td><p><code>2</code> или <code>HtmlAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Текст с разметкой</p></td>
<td><p><code>3</code> или <code>TextEnriched</code></p></td>
</tr>
<tr class="even">
<td><p>Текст с разметкой и текст</p></td>
<td><p><code>4</code> или <code>TextEnrichedAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Наилучший формат текста</p></td>
<td><p><code>5</code> или <code>BestBodyFormat</code></p></td>
</tr>
<tr class="even">
<td><p>TNEF</p></td>
<td><p><code>6</code> или <code>Tnef</code></p></td>
</tr>
</tbody>
</table>


После установки параметров формата извлечения сообщений для протокола IMAP4 необходимо перезапустить службы IMAP4, чтобы изменения вступили в силу. Дополнительные сведения о перезапуске служб IMAP4 см. в разделе [Запуск и остановка служб IMAP4](start-and-stop-the-imap4-services-exchange-2013-help.md).

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-IMAPSettings](https://technet.microsoft.com/ru-ru/library/aa998252\(v=exchg.150\)).

## Как проверить, что все получилось?

Выполните следующие действия, чтобы убедиться, что параметры извлечения сообщений IMAP4 на сервере успешно установлены.

1.  Выполните в командной консоли следующую команду.
    
        Get-ImapSettings | format-list

2.  Проверьте правильность параметра *MessageRetrievalMimeFormat*.

## Установка формата извлечения сообщений POP3 для пользователя

## Использование командной консоли для установки формата извлечения сообщений POP3 для пользователя

В этом примере устанавливается формат извлечения сообщений "Только текст" для доступа по протоколу POP3 для пользователя `USER01`.

    Set-CASMailbox -Identity USER01 -PopMessagesRetrievalMimeFormat TextOnly

Можно выбрать следующие параметры. В качестве значения параметра *PopMessagesRetrievalMimeFormat* можно указать число или текстовую строку.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>формат сообщений</strong></p></td>
<td><p><strong>Значение</strong></p></td>
</tr>
<tr class="even">
<td><p>Text</p></td>
<td><p><code>0</code> или <code>TextOnly</code></p></td>
</tr>
<tr class="odd">
<td><p>HTML</p></td>
<td><p><code>1</code> или <code>HtmlOnly</code></p></td>
</tr>
<tr class="even">
<td><p>HTML и замещающий текст</p></td>
<td><p><code>2</code> или <code>HtmlAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Текст с разметкой</p></td>
<td><p><code>3</code> или <code>TextEnriched</code></p></td>
</tr>
<tr class="even">
<td><p>Текст с разметкой и текст</p></td>
<td><p><code>4</code> или <code>TextEnrichedAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Наилучший формат текста</p></td>
<td><p><code>5</code> или <code>BestBodyFormat</code></p></td>
</tr>
<tr class="even">
<td><p>TNEF</p></td>
<td><p><code>6</code> или <code>Tnef</code></p></td>
</tr>
</tbody>
</table>


После установки параметров формата извлечения сообщений для протокола POP3 необходимо перезапустить службы POP3, чтобы изменения вступили в силу. Дополнительные сведения о перезапуске служб POP3 см. в разделе [Запуск и остановка служб POP3](start-and-stop-the-pop3-services-exchange-2013-help.md).

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-CASMailbox](https://technet.microsoft.com/ru-ru/library/bb125264\(v=exchg.150\)).

## Как проверить, что все получилось?

Выполните следующие действия, чтобы убедиться, что параметры формата извлечения сообщений POP3 для пользователя успешно установлены.

1.  Выполните в командной консоли следующую команду.
    
        Get-CAS Mailbox <identity> | format-list

2.  Проверьте правильность значения параметра *PopMessagesRetrievalMimeFormat*.

## Установка формат извлечения сообщений IMAP4 для пользователя

## Использование командной консоли для установки формата извлечения сообщений IMAP4 для пользователя

В этом примере устанавливается формат извлечения сообщений "Только текст" для доступа по протоколу IMAP4 для пользователя `USER01`.

    Set-CASMailbox -Identity USER01 -ImapMessagesRetrievalMimeFormat TextOnly

В качестве значения параметра *ImapMessagesRetrievalMimeFormat* можно указать число или текстовую строку.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>формат сообщений</strong></p></td>
<td><p><strong>Значение</strong></p></td>
</tr>
<tr class="even">
<td><p>Text</p></td>
<td><p><code>0</code> или <code>TextOnly</code></p></td>
</tr>
<tr class="odd">
<td><p>HTML</p></td>
<td><p><code>1</code> или <code>HtmlOnly</code></p></td>
</tr>
<tr class="even">
<td><p>HTML и замещающий текст</p></td>
<td><p><code>2</code> или <code>HtmlAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Текст с разметкой</p></td>
<td><p><code>3</code> или <code>TextEnriched</code></p></td>
</tr>
<tr class="even">
<td><p>Текст с разметкой и текст</p></td>
<td><p><code>4</code> или <code>TextEnrichedAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Наилучший формат текста</p></td>
<td><p><code>5</code> или <code>BestBodyFormat</code></p></td>
</tr>
<tr class="even">
<td><p>TNEF</p></td>
<td><p><code>6</code> или <code>Tnef</code></p></td>
</tr>
</tbody>
</table>


После установки параметров формата извлечения сообщений для протокола IMAP4 необходимо перезапустить службы IMAP4, чтобы изменения вступили в силу. Дополнительные сведения о перезапуске служб IMAP4 см. в разделе [Запуск и остановка служб IMAP4](start-and-stop-the-imap4-services-exchange-2013-help.md).

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-CASMailbox](https://technet.microsoft.com/ru-ru/library/bb125264\(v=exchg.150\)).

## Как проверить, что все получилось?

Выполните следующие действия, чтобы убедиться, что параметры формата извлечения сообщений IMAP4 для пользователя успешно установлены.

1.  Выполните в командной консоли следующую команду.
    
        Get-CAS Mailbox <identity> | format-list

2.  Проверьте правильность значения параметра *ImapMessagesRetrievalMimeFormat*.

## Дополнительные сведения

После назначения формата получения сообщений для пользователей IMAP4 и POP3 можно выполнить следующие действия.

[Включение или отключение доступа по протоколу POP3 для пользователя](enable-or-disable-pop3-access-for-a-user-exchange-2013-help.md)

[Включение и отключение доступа IMAP4 для пользователя](enable-or-disable-imap4-access-for-a-user-exchange-2013-help.md)

[Настройка параметров календаря для IMAP4](configure-calendar-options-for-imap4-exchange-2013-help.md)

[Настройка параметров календаря для службы POP3](configure-calendar-options-for-pop3-exchange-2013-help.md)

