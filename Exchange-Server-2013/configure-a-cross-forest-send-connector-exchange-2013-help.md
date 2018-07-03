﻿---
title: 'Настройка соединителя отправки между лесами: Exchange 2013 Help'
TOCTitle: Настройка соединителя отправки между лесами
ms:assetid: 7840d172-071e-4f13-9379-2fe1eee1a7cc
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ945053(v=EXCHG.150)
ms:contentKeyID: 52061234
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка соединителя отправки между лесами

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2013-02-21_

В Active Directory*лес* представляет внешнюю границу службы каталогов. Для взаимодействия между лесами вы можете создать соединители отправки. В этом примере соединители используют обычную проверку подлинности.

Сведения о дополнительных задачах, связанных с настройкой соединителей, см. в разделе [соединители;](connectors-exchange-2013-help.md).

Хотите узнать о сценариях, где используется эта процедура? См. следующие разделы:

  - [Развертывание Exchange 2013 в топологии с несколькими лесами](deploy-exchange-2013-in-a-cross-forest-topology-exchange-2013-help.md)

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 20 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Записи "Соединители отправки" и "Соединители получения" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Если вы находитесь на начальном этапе установки, см. [Развертывание новой установки Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md). После установки вы можете использовать действия в этом разделе, чтобы создать соединители для настройки топологии перекрестных лесов.

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

## Создание учетной записи пользователя для каждого леса.

Для использования обычной проверки подлинности нужно создать учетную запись пользователя в каждом лесу. Создайте учетную запись в каждом лесу и добавьте все из них в универсальную группу безопасности Exchange Server, используемую для взаимодействия. Эта учетная запись используется соединителем отправки для проверки подлинности на принимающем сервере в другом лесу. Например, создайте учетную запись пользователя с именем участника-пользователя FourthCoffee@Contoso.com в качестве учетных данных, которые будут использоваться при проверке подлинности сервером Exchange в домене Fourth Coffee при отправке почты на сервер Exchange в домене Contoso.

## Использование EAC для создания соединителя отправки для маршрутизации почты в другой лес Exchange 2013

Настройте поток почты между лесами с использованием обычной проверки подлинности.

1.  В Центре администрирования Exchange последовательно выберите пункты **поток обработки почты** \> **соединители отправки**. Щелкните **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления").

2.  В мастере **создания соединителя отправки** укажите имя соединителя отправки и выберите **Внутренний** в поле **Тип**. Нажмите кнопку **далее**.

3.  Выберите **Маршрутизация почты через промежуточные узлы**, а затем щелкните **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"). В окне **добавить промежуточный узел** введите IP-адрес целевого сервера во втором лесу, например 64.4.6.100. Нажмите кнопку **сохранить**, а затем кнопку **далее**.
    
    Для параметра **Проверка подлинности промежуточных узлов** выберите **Обычная проверка подлинности** и введите имя пользователя и пароль. Здесь можно установить флажок **Предлагать использовать обычную проверку подлинности только после запуска TLS** для безопасной передачи данных по протоколу TLS.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если вы используете обычную проверку подлинности по протоколу TLS, целевой сервер нужно настроить для применения сертификата X.509.</td>
    </tr>
    </tbody>
    </table>


4.  В разделе **Адресное пространство** нажмите кнопку **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"). В окне **добавить домен** укажите SMTP как **Тип**. В поле **Полное доменное имя** введите принимающий домен, например fourthcoffee.com. Нажмите **сохранить**, а затем **далее**.

5.  Для **Исходный сервер** нажмите кнопку **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"). В окне **Выбор сервера** выберите сервер, который будет использоваться, и нажмите кнопку **добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"). Нажмите кнопку **ОК**.

6.  Нажмите кнопку **готово**. Соединитель появится в списке соединителей отправки.

После создания соединителя отправки создайте во втором лесу соединитель отправки, отправляющий почту в первоначальный лес. В этом случае полное доменное имя, которое вы указываете, будет именем домена первого леса. Например, contoso.com.

## Использование командной консоли для установки разрешений соединителя отправки

Этот пример использует сценарий Enable-CrossForestConnector.ps1 в командной консоли для установки разрешений соединителя отправки, который будет использоваться в топологии перекрестного леса.

    .\Enable-CrossForestConnector.ps1 -Connector "Cross-Forest" -user "ANONYMOUS LOGON"

## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно создали соединитель отправки для маршрутизации почты во второй лес, отправьте сообщение от пользователя в вашей организации (можно использовать Outlook Web App) в домен, который был указан в поле **Адресное пространство**. Если он получает сообщение, то вы правильно настроили соединитель отправки.

## Дополнительные сведения

[Создание соединителя отправки для электронной почты, отправляемой в Интернет](create-a-send-connector-for-email-sent-to-the-internet-exchange-2013-help.md)

[Соединители отправки](send-connectors-exchange-2013-help.md)
