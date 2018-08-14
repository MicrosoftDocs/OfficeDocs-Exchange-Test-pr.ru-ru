---
title: 'Интеграция единой системы обмена сообщениями для Exchange 2013 с Lync Server'
TOCTitle: 'Контрольный список: Интеграция единой системы обмена сообщениями Exchange 2013 с сервером Lync'
ms:assetid: 3b82e86f-9f30-4445-96ad-744082abeaeb
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638120(v=EXCHG.150)
ms:contentKeyID: 52061222
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Контрольный список: Интеграция единой системы обмена сообщениями Exchange 2013 с сервером Lync

 

_**Применимо к:** Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2016-12-09_

Используйте этот контрольный список для установки и развертывания единой системы обмена сообщениями и Майкрософт Lync Server 2013. В этом разделе "Lync Server" также относится к Lync Server 2010. Однако Microsoft Office Communications Server 2007 R2 может быть также развернут вместе с единой системой обмена сообщениями.


Перед началом работы со списком убедитесь, что вы ознакомились с общими концепциями, изложенными в разделах:

  - [Развертывание единой системы обмена сообщениями в Exchange 2013 и обзор Lync Server](deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md)

  - [Сосуществование с Office Communications Server 2007 R2 и Lync Server](coexistence-with-office-communications-server-2007-r2-and-lync-server-exchange-2013-help.md)

Дополнительные сведения о выполнении задач, которые должны быть завершены для Microsoft Lync Server, см. в статье [Microsoft Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=265752).

## Контрольный список для развертывания сервера Microsoft Lync Server и единой системы обмена сообщениями


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Готово?</th>
<th>Tasks</th>
<th>Раздел</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Просмотрите перед установкой Exchange Server 2013 требования к системе.</p></td>
<td><p><a href="exchange-2013-system-requirements-exchange-2013-help.md">Требования к системе для установки Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Проверьте предварительные требования к установке.</p></td>
<td><p><a href="exchange-2013-prerequisites-exchange-2013-help.md">Предварительные требования для Exchange 2013</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Просмотрите предварительные условия для интеграции серверов Microsoft Lync Server 2013 и Microsoft Exchange Server 2013.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=282082">Предварительные условия для интеграции Microsoft Lync Server 2013 и Microsoft Exchange Server 2013</a></p>

> [!TIP]  
> Для Exchange 2013 и Lync Server 2010 и 2013 требуется установка пакета Unified Communications Managed API (UCMA) 4.0 Runtime (он устанавливается в процессе основной установки). Чтобы скачать и просмотреть сведения о UCMA 4.0, см. статью <a href="https://go.microsoft.com/fwlink/p/?linkid=258269">Unified Communications Managed API 4.0 Runtime</a>

</td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Установите требуемые серверы клиентского доступа и почтовых ящиков.</p></td>
<td><p><a href="install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md">Установка Exchange 2013 с помощью мастера установки</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Проверьте установку и просмотрите журналы установки сервера.</p></td>
<td><p><a href="verify-an-exchange-2013-installation-exchange-2013-help.md">Проверка установки Exchange 2013</a></p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Если необходимо, установите требуемые языковые пакеты для единой системы обмена сообщениями.</p></td>
<td><p><a href="install-a-um-language-pack-exchange-2013-help.md">Установка языкового пакета единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="odd">
<td><p><strong> </strong></p></td>
<td><p>Создать некоторое количество абонентских групп с универсальными кодами ресурса (URI) SIP, необходимое для организации.</p></td>
<td><p><a href="create-a-um-dial-plan-exchange-2013-help.md">Создание абонентской группы единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройте параметры безопасности абонентской группы.</p></td>
<td><p><a href="configure-the-voip-security-setting-exchange-2013-help.md">Настройка параметра безопасности VoIP</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Настройте количество одновременных вызовов на серверах почтовых ящиков.</p></td>
<td><p><a href="configure-the-number-of-incoming-calls-on-a-mailbox-server-exchange-2013-help.md">Настройте количество входящих вызовов на сервере почтовых ящиков</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройте номера голосовых доступов Outlook и другие параметры.</p></td>
<td><p><a href="manage-a-um-dial-plan-exchange-2013-help.md">Управление абонентской группой единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Добавьте к каждой абонентской группе с универсальным кодом ресурса (URI) протокола SIP все серверы клиентского доступа и почтовых ящиков.</p></td>
<td><p><a href="add-mailbox-and-client-access-servers-to-a-sip-uri-dial-plan-exchange-2013-help.md">Добавьте серверы клиентского доступа и почтовых ящиков для абонентской группы SIP URI</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройте исходящие номера для единой системы обмена сообщениями. Разрешите все вызовы для абонентских групп с универсальным кодом ресурса (URI) протокола SIP и политики почтовых ящиков единой системы обмена сообщениями, которые связаны с этими группами.</p></td>
<td><p><a href="authorize-calls-for-users-in-a-dial-plan-exchange-2013-help.md">Авторизации вызовов для пользователей в абонентской группы</a></p>
<p><a href="authorize-calls-for-a-group-of-users-exchange-2013-help.md">Авторизовать звонки для группы пользователей</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Создайте требуемое число автосекретарей.</p></td>
<td><p><a href="create-a-um-auto-attendant-exchange-2013-help.md">Создание автосекретаря единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Настройте по отдельности каждого из автосекретарей единой системы обмена сообщениями.</p></td>
<td><p><a href="set-up-a-um-auto-attendant-exchange-2013-help.md">Настройка автосекретаря единой системы обмена сообщениями</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Создайте, импортируйте и включите новый сертификат Exchange для единой системы обмена сообщениями, или включите взаимно доверенный сторонний сертификат.</p></td>
<td><p><a href="add-mailbox-and-client-access-servers-to-a-sip-uri-dial-plan-exchange-2013-help.md">Добавьте серверы клиентского доступа и почтовых ящиков для абонентской группы SIP URI</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Установите режим запуска единой системы обмена сообщениями для каждого сервера клиентского доступа и почтовых ящиков (двойной режим или режим TLS).</p></td>
<td><p><a href="configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md">Настройка режима запуска на сервере почтовых ящиков</a></p>
<p><a href="configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md">Настройка режима запуска на сервере клиентского доступа</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Перезагрузите службу единой системы обмена сообщениями Microsoft Exchange и службу маршрутизатора вызовов единой системы обмена сообщениями на всех серверах Exchange, чтобы загрузить требуемые сертификаты.</p></td>
<td><p><a href="stop-the-microsoft-exchange-unified-messaging-service-exchange-2013-help.md">Остановка службы единой системы обмена сообщениями Microsoft Exchange</a></p>
<p><a href="start-the-microsoft-exchange-unified-messaging-service-exchange-2013-help.md">Запуск службы единой системы обмена сообщениями Microsoft Exchange</a></p>
<p><a href="stop-the-microsoft-exchange-unified-messaging-call-router-service-exchange-2013-help.md">Остановка службы единой системы обмена сообщениями маршрутизатора вызовов Microsoft Exchange</a></p>
<p><a href="start-the-microsoft-exchange-unified-messaging-call-router-service-exchange-2013-help.md">Запуск службы единой системы обмена сообщениями маршрутизатора вызовов Microsoft Exchange</a></p></td>
</tr>
<tr class="even">
<td><p><strong> </strong></p></td>
<td><p>Создайте политику почтовых ящиков единой системы обмена сообщениями или настройте политику почтовых ящиков по умолчанию.</p></td>
<td><p><a href="create-a-um-mailbox-policy-exchange-2013-help.md">Создание политики почтовых ящиков единой системы обмена сообщениями</a></p>
<p><a href="manage-a-um-mailbox-policy-exchange-2013-help.md">Управление политикой почтовых ящиков единой системы обмена СООБЩЕНИЯМИ</a></p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Разрешите пользователям с SIP-адресом подключение к единой системе обмена сообщениями и свяжите их с абонентской группой с универсальным кодом ресурса (URI) по протоколу SIP.</p></td>
<td><p><a href="enable-a-user-for-voice-mail-exchange-2013-help.md">Включение для пользователя поддержки голосовой почты</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Просмотрите документацию по планированию Lync Server 2013.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=282081">Планирование</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Установите и разверните Lync Server 2013.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=282051">Развертывание Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Импортируйте взаимно доверенную внутреннюю PKI или сторонний сертификат, импортированный на серверы единой системы обмена сообщениями Exchange.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281863">Настройка сертификатов для серверов</a></p>
<p><a href="https://go.microsoft.com/fwlink/p/?linkid=281865">Настройка сертификатов на сервере, на котором работает единая система обмена сообщениями Microsoft Exchange Server</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Если необходимо, запустите на серверах службы Lync, чтобы загрузить сертификаты.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=282084">Запуск служб на серверах</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Откройте командную консоль Exchange и запустите сценарий exchucutil.ps1, расположенный в папке %Program Files%\Microsoft\Exchange Server\V15\Scripts.</p>
<p></p></td>
<td><p><a href="configure-um-to-work-with-lync-server-exchange-2013-help.md">Настройка единой системы обмена сообщениями для работы с Lync Server</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Просмотрите требования к корпоративной голосовой связи.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281876">Необходимое программное обеспечение для корпоративной голосовой связи</a></p>
<p><a href="https://go.microsoft.com/fwlink/p/?linkid=281875">Необходимые условия для обеспечения безопасности и настройки корпоративной голосовой связи</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Разверните и настройте медиашлюзы или серверы-посредники, затем определите одноранговые узлы.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281872">Развертывание серверов-посредников и определение одноранговых узлов</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Настройте магистраль между сервером-посредником и одним или несколькими одноранговыми узлами, чтобы обеспечить возможность подключения к телефонной сети общего пользования (ТСОП).</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281868">Настройка магистралей</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Создайте и настройте абонентскую группу Lync, затем создайте, определите и свяжите правила нормализации.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281867">Настройка абонентских групп</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Настройте политики голосовой связи и определите использование телефонов и маршруты исходящих вызовов.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281869">Настройка политик голосовой связи, режимов работы с ТСОП и маршрутов голосовых вызовов</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Запустите средство интеграции с Exchange (ocsumutil.exe), которое создает контактные объекты для голосового доступа к Outlook и автосекретарям.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281866">Настройка Lync Server 2013 для работы с единой системой обмена сообщениями на Microsoft Exchange Server</a></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Определите, разверните и настройте любые необходимые расширенные функции корпоративной голосовой связи.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281871">Развертывание расширенных функций корпоративной голосовой связи</a></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Включите для пользователей доступ к корпоративной голосовой связи. Введите универсальный код ресурса (URI) линии, назначьте политику голосовой связи и абонентскую группу Lync.</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=281873">Включение корпоративной голосовой связи для пользователей</a></p></td>
</tr>
</tbody>
</table>

