---
title: 'Обзор служб Exchange 2013: Exchange 2013 Help'
TOCTitle: Обзор служб Exchange 2013
ms:assetid: 2ed45d18-2ff3-4099-b841-050eb16a416b
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee423542(v=EXCHG.150)
ms:contentKeyID: 74479253
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Обзор служб Exchange 2013

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2017-10-20_

Во время установки Exchange Server 2013 набор задач, установка новых служб в Microsoft Windows запуска программы установки. Служба — в фоновом режиме, который может быть запущено во время загрузки сервера с Windows диспетчера управления службами. Службы, исполняемые файлы, предназначенные для работы с независимо друг от друга и без вмешательства администратора. Службу можно запустить с помощью графического пользовательского интерфейса режим или режим консоли.

Все предыдущие версии Exchange включали компоненты, реализуемые в виде служб. Каждая роль сервера Exchange Server включает службы, которые входят в состав роли сервера (или могут быть ей необходимы), для выполнения своих функций. Обратите внимание, что некоторые службы становятся активны только при использовании определенных функций.

В этом разделе описаны различные службы, установленные с Exchange 2013 на серверах почтовых ящиков, серверов клиентского доступа и пограничных транспортных серверах. Для служб, которые помечены как необязательно можно отключить службу, если вы определяете вашей организации не требуются возможности, предоставляемые службой.

## Exchange служб на серверах почтовых ящиков Exchange 2013

В приведенной ниже таблице описываются службы Exchange, устанавливаемые на серверах почтовых ящиков.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя службы</th>
<th>Короткое имя службы</th>
<th>Описание и зависимости</th>
<th>Тип запуска по умолчанию</th>
<th>Контекст безопасности</th>
<th>Зависимости</th>
<th>Обязательная или необязательная</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft Exchange Топология Active Directory</p></td>
<td><p>MSExchangeADTopology</p></td>
<td><p>Предоставляет сведения о топологии Active Directory для служб Exchange. Если работа этой службы будет остановлена, большинство служб Exchange не смогут запускаться.</p></td>
<td><p>Автоматическая</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба совместного доступа к портам Net.TCP</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Обновление средства защиты от нежелательной почты Microsoft Exchange</p></td>
<td><p>MSExchangeAntispamUpdate</p></td>
<td><p>Предоставляет обновления определений спама для Exchange SmartScreen.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>1 ноября 2016 г. корпорация Майкрософт перестала выпускать обновления определений спама для фильтров SmartScreen в Exchange и Outlook. Существующие определения спама для SmartScreen останутся, но их эффективность будет снижаться с течением времени. Дополнительные сведения см. в статье <a href="https://go.microsoft.com/fwlink/p/?linkid=835894">Прекращение поддержки SmartScreen в Outlook и Exchange</a>.</td>
</tr>
</tbody>
</table>

</td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Необязательная</p></td>
</tr>
<tr class="odd">
<td><p>Служба управления DAG Microsoft Exchange</p></td>
<td><p>MSExchangeDagMgmt</p></td>
<td><p>Предоставляет возможности управления структурами хранилищ и макетами баз данных для серверов почтовых ящиков в группах обеспечения доступности баз данных.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p>
<p>Служба совместного доступа к портам Net.TCP</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Служба диагностики Microsoft Exchange</p></td>
<td><p>MSExchangeDiagnostics</p></td>
<td><p>Предоставляет агент, отслеживающий работоспособность сервера Exchange Server.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Нет</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange EdgeSync</p></td>
<td><p>MSExchangeEdgeSync</p></td>
<td><p>Реплицирует данные о конфигурации и получателях, передавая их с сервера почтовых ящиков в службы Active Directory облегченного доступа к каталогам (AD LDS) на подписанных пограничных транспортных серверах по защищенному каналу LDAP, а также наоборот.</p>
<p>Если у вас нет подписанных пограничных транспортных серверов, можете отключить эту службу.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Необязательная</p></td>
</tr>
<tr class="even">
<td><p>Диспетчер работоспособности Microsoft Exchange</p></td>
<td><p>MSExchangeHM</p></td>
<td><p>Часть службы управляемой доступности, отслеживающая работоспособность ключевых компонентов на сервере Exchange Server.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Журнал событий Windows</p>
<p>Инструментарий управления Windows (WMI)</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Внутренняя служба IMAP4 Microsoft Exchange</p></td>
<td><p>MSExchangeIMAP4BE</p></td>
<td><p>Получает прокси клиентских подключений из из службы IMAP4 на серверах клиентского доступа. По умолчанию эта служба не выполняется, поэтому клиентов IMAP4 не удается подключиться к серверу Exchange только после запуска службы.</p>
<p>Если у вас нет клиентов IMAP4, можете отключить эту службу.</p></td>
<td><p>Вручную</p></td>
<td><p>Сетевая служба</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Необязательная</p></td>
</tr>
<tr class="even">
<td><p>Банк данных Microsoft Exchange</p></td>
<td><p>MSExchangeIS</p></td>
<td><p>Управляет базами данных почтовых ящиков на сервере. Если эта служба остановлена, базы данных почтовых ящиков на сервере недоступны.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p>
<p>Удаленный вызов процедур (RPC)</p>
<p>Сервер</p>
<p>Журнал событий Windows</p>
<p>Рабочая станция</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Помощники по обслуживанию почтовых ящиков Microsoft Exchange</p></td>
<td><p>MSExchangeMailboxAssistants</p></td>
<td><p>Выполняет фоновую обработку почтовых ящиков в соответствующих базах данных на сервере.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Служба репликации почтовых ящиков Microsoft Exchange</p></td>
<td><p>MSExchangeMailboxReplication</p></td>
<td><p>Обрабатывает операции перемещения и запросы на перемещение почтовых ящиков.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p>
<p>Служба совместного доступа к портам Net.TCP</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Служба доставки транспорта почтовых ящиков Microsoft Exchange</p></td>
<td><p>MSExchangeDelivery</p></td>
<td><p>Получает сообщения SMTP от службы транспорта Microsoft Exchange (на локальных или удаленных серверах почтовых ящиков) и доставляет их в локальную базу данных почтовых ящиков с помощью RPC.</p></td>
<td><p>Автоматически</p></td>
<td><p>Сетевая служба</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Служба отправки транспорта почтовых ящиков Microsoft Exchange</p></td>
<td><p>MSExchangeSubmission</p></td>
<td><p>Получает сообщения RPC из локальной базы данных почтовых ящиков и отправляет их по протоколу SMTP в службу транспорта Microsoft Exchange (на локальных или удаленных серверах почтовых ящиков).</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Внутренняя служба POP3 Microsoft Exchange</p></td>
<td><p>MSExchangePOP3BE</p></td>
<td><p>Получает прокси клиентских подключений от службы POP3 на серверах клиентского доступа. По умолчанию эта служба не выполняется, поэтому клиентов POP3 не удается подключиться к серверу Exchange только после запуска службы.</p></td>
<td><p>Вручную</p></td>
<td><p>Сетевая служба</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Необязательная</p></td>
</tr>
<tr class="even">
<td><p>Служба репликации Microsoft Exchange</p></td>
<td><p>MSExchangeRepl</p></td>
<td><p>Обеспечивает репликацию баз данных почтовых ящиков в группах обеспечения доступности баз данных.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Клиентский доступ RPC Microsoft Exchange</p></td>
<td><p>MSExchangeRPC</p></td>
<td><p>Управляет клиентскими подключениями RPC для Exchange.</p></td>
<td><p>Автоматически</p></td>
<td><p>Сетевая служба</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Служба поиска Microsoft Exchange</p></td>
<td><p>MSExchangeFastSearch</p></td>
<td><p>Обеспечивает индексацию содержимого почтовых ящиков, которая повышает скорость поиска содержимого.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Хост-контроллер поиска Microsoft Exchange</p></td>
<td><p>HostControllerService</p></td>
<td><p>Предоставляет службы развертывания и управления для приложений на локальном сервере Exchange Server.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>HTTP-служба</p></td>
<td><p>Обязательный</p></td>
</tr>
<tr class="even">
<td><p>Расширение сервера Microsoft Exchange для системы архивации данных Windows Server</p></td>
<td><p>WSBExchange</p></td>
<td><p>Позволяет службе резервного копирования Windows Server копировать и восстанавливать данные сервера Exchange Server.</p></td>
<td><p>Вручную</p></td>
<td><p>Локальная система</p></td>
<td><p>Нет</p></td>
<td><p>Необязательная</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange Service Host</p></td>
<td><p>MSExchangeServiceHost</p></td>
<td><p>Предоставляет узел службы для компонентов Exchange, у которых нет собственных служб.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Регулирование Microsoft Exchange</p></td>
<td><p>MSExchangeThrottling</p></td>
<td><p>Предоставляет возможность управления рабочими нагрузками пользователей. Такое управление ограничивает частоту пользовательских операций, оно ранее называлось регулированием пользователей.</p></td>
<td><p>Автоматически</p></td>
<td><p>Сетевая служба</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Транспорт Microsoft Exchange</p></td>
<td><p>MSExchangeTransport</p></td>
<td><p>Предоставляет SMTP-сервер и транспортный стек.</p></td>
<td><p>Автоматически</p></td>
<td><p>Сетевая служба</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p>
<p>Служба управления фильтрацией Майкрософт</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Поиск журналов транспорта Microsoft Exchange</p></td>
<td><p>MSExchangeTransportLogSearch</p></td>
<td><p>Предоставляет возможность удаленного поиска для файлов журналов транспорта (например, отслеживание сообщений).</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Необязательная</p></td>
</tr>
<tr class="odd">
<td><p>Единая система обмена сообщениями Microsoft Exchange</p></td>
<td><p>MSExchangeUM</p></td>
<td><p>Предоставляет функции единой системы обмена сообщениями: позволяет хранить голосовые и факсимильные сообщения в Exchange, а также предоставляет пользователям доступ с телефона к электронной почте, голосовой почте, календарю, контактам или автосекретарю. Если служба остановлена, единая система обмена сообщениями недоступна.</p>
<p>Если у вас нет единой системы обмена сообщениями, можете отключить эту службу.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Изоляция ключей CNG</p>
<p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Необязательная</p></td>
</tr>
</tbody>
</table>


## Exchange служб на серверах клиентского доступа Exchange 2013

В следующей таблице описываются службы Exchange, установленные на серверах клиентского доступа.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя службы</th>
<th>Короткое имя службы</th>
<th>Описание и зависимости</th>
<th>Тип запуска по умолчанию</th>
<th>Контекст безопасности</th>
<th>Зависимости</th>
<th>Обязательная или необязательная</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft Exchange Топология Active Directory</p></td>
<td><p>MSExchangeADTopology</p></td>
<td><p>Предоставляет сведения о топологии Active Directory для служб Exchange. Если работа этой службы будет остановлена, большинство служб Exchange не смогут запускаться.</p></td>
<td><p>Автоматическая</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба совместного доступа к портам Net.TCP</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Служба диагностики Microsoft Exchange</p></td>
<td><p>MSExchangeDiagnostics</p></td>
<td><p>Предоставляет агент, отслеживающий работоспособность сервера Exchange Server.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Нет</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Интерфейсная служба транспорта Microsoft Exchange</p></td>
<td><p>MSExchangeFrontEndTransport</p></td>
<td><p>Прокси-серверы SMTP подключения от внешних узлов, чтобы Microsoft Exchange транспортной службы на сервере почтовых ящиков.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Диспетчер работоспособности Microsoft Exchange</p></td>
<td><p>MSExchangeHM</p></td>
<td><p>Часть службы управляемой доступности, отслеживающая работоспособность ключевых компонентов на сервере Exchange Server.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Журнал событий Windows</p>
<p>Инструментарий управления Windows (WMI)</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange IMAP4</p></td>
<td><p>MSExchangeIMAP4</p></td>
<td><p>Прокси-серверы IMAP4 клиентские подключения к службе IMAP4 на серверах почтовых ящиков. По умолчанию эта служба не выполняется, поэтому клиентов IMAP4 не удается подключиться к серверу Exchange только после запуска службы.</p>
<p>Если у вас нет клиентов IMAP4, можете отключить эту службу.</p></td>
<td><p>Вручную</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Необязательная</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange POP3</p></td>
<td><p>MSExchangePOP3</p></td>
<td><p>Прокси-серверы POP3 клиентские подключения к службе IMAP4 на серверах почтовых ящиков. По умолчанию эта служба не выполняется, поэтому клиентов POP3 не удается подключиться к серверу Exchange только после запуска службы.</p></td>
<td><p>Вручную</p></td>
<td><p>Сетевая служба</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Необязательная</p></td>
</tr>
<tr class="odd">
<td><p>Хост-контроллер поиска Microsoft Exchange</p></td>
<td><p>HostControllerService</p></td>
<td><p>Предоставляет службы развертывания и управления для приложений на локальном сервере Exchange Server.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>HTTP-служба</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange Service Host</p></td>
<td><p>MSExchangeServiceHost</p></td>
<td><p>Предоставляет узел службы для компонентов Exchange, у которых нет собственных служб.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Маршрутизатор вызовов единой системы обмена сообщениями Microsoft Exchange</p></td>
<td><p>MSExchangeUMCR</p></td>
<td><p>Перенаправляет единой системы обмена СООБЩЕНИЯМИ клиентские подключения к службе единой системы обмена сообщениями на сервере почтовых ящиков.</p>
<p>Если у вас нет единой системы обмена сообщениями, можете отключить эту службу.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Изоляция ключей CNG</p>
<p>Служба топологии Active DirectoryMicrosoft Exchange</p></td>
<td><p>Необязательная</p></td>
</tr>
</tbody>
</table>


## службы Exchange на Exchange 2013 пограничных транспортных серверов

В приведенной ниже таблице описываются службы Exchange, устанавливаемые на пограничных транспортных серверах.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя службы</th>
<th>Короткое имя службы</th>
<th>Описание</th>
<th>Тип запуска по умолчанию</th>
<th>Контекст безопасности</th>
<th>Зависимости</th>
<th>Обязательная или необязательная</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>ADAM_MSExchange</p></td>
<td><p>Хранит сведения о конфигурации и получателях на пограничном транспортном сервере. Эта служба представляет именованный экземпляр служб Active Directory облегченного доступа к каталогам (AD LDS), автоматически создаваемый программой установки Exchange.</p></td>
<td><p>Автоматически</p></td>
<td><p>Сетевая служба</p></td>
<td><p>Система событий COM+</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Обновление средства защиты от нежелательной почты Microsoft Exchange</p></td>
<td><p>MSExchangeAntispamUpdate</p></td>
<td><p>Предоставляет обновления определений спама для Exchange SmartScreen.</p>
<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>1 ноября 2016 г. корпорация Майкрософт перестала выпускать обновления определений спама для фильтров SmartScreen в Exchange и Outlook. Существующие определения спама для SmartScreen останутся, но их эффективность будет снижаться с течением времени. Дополнительные сведения см. в статье <a href="https://go.microsoft.com/fwlink/p/?linkid=835894">Прекращение поддержки SmartScreen в Outlook и Exchange</a>.</td>
</tr>
</tbody>
</table>

</td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Необязательная</p></td>
</tr>
<tr class="odd">
<td><p>Служба учетных данных Microsoft Exchange</p></td>
<td><p>MSExchangeEdgeCredential</p></td>
<td><p>Отслеживает изменения учетных данных в службах Active Directory облегченного доступа к каталогам (AD LDS) и применяет изменения на пограничном транспортном сервере.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Служба диагностики Microsoft Exchange</p></td>
<td><p>MSExchangeDiagnostics</p></td>
<td><p>Предоставляет агент, отслеживающий работоспособность сервера Exchange Server.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Нет</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Диспетчер работоспособности Microsoft Exchange</p></td>
<td><p>MSExchangeHM</p></td>
<td><p>Часть службы управляемой доступности, отслеживающая работоспособность ключевых компонентов на сервере Exchange Server.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Журнал событий Windows</p>
<p>Инструментарий управления Windows (WMI)</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Exchange Service Host</p></td>
<td><p>MSExchangeServiceHost</p></td>
<td><p>Предоставляет узел службы для компонентов Exchange, у которых нет собственных служб.</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="odd">
<td><p>Транспорт Microsoft Exchange</p></td>
<td><p>MSExchangeTransport</p></td>
<td><p>Предоставляет SMTP-сервер и транспортный стек.</p></td>
<td><p>Автоматически</p></td>
<td><p>Сетевая служба</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Обязательная</p></td>
</tr>
<tr class="even">
<td><p>Поиск журналов транспорта Microsoft Exchange</p></td>
<td><p>MSExchangeTransportLogSearch</p></td>
<td><p>Предоставляет возможность удаленного поиска для файлов журналов транспорта (например, отслеживание сообщений).</p></td>
<td><p>Автоматически</p></td>
<td><p>Локальная система</p></td>
<td><p>Microsoft Exchange ADAM</p></td>
<td><p>Необязательная</p></td>
</tr>
</tbody>
</table>

