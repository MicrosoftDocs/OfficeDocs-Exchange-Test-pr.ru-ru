---
title: 'Рекомендации по телефонии в Exchange 2013: Exchange 2013 Help'
TOCTitle: Рекомендации по телефонии в Exchange 2013
ms:assetid: e9f760f2-5901-4ed2-95a5-724555cc700e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee364753(v=EXCHG.150)
ms:contentKeyID: 50556499
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Рекомендации по телефонии в Exchange 2013

 

_**Применимо к:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2017-07-25_

Единая система обмена сообщениями требует, чтобы Microsoft Exchange был интегрирован с телефонной системой организации. Для успешного развертывания среды необходимо тщательно проанализировать имеющуюся инфраструктуру телефонии и правильно спланировать развертывание единой системы обмена сообщениями.

Планирование может оказаться затруднительным для администраторов Exchange, имеющих мало опыта работы с телефонной сетью. Сведения, которые помогут справиться с этими затруднениями, см. ниже, в подразделе Resources to Help with Your UM Deployment.

Чтобы получить сведения о шлюзах VoIP, поддерживаемых единой системой обмена сообщениями, узнать, поддерживается ли конкретная УАТС той или иной моделью шлюза VoIP или определенным изготовителем и поддерживается ли УАТС на основе протокола IP с использованием прямого подключения SIP, а также найти поддерживаемые единой системой обмена сообщениями Exchange Online пограничные контроллеры сеансов SBC, выберите одну из приведенных ниже ссылок.

  - Supported VoIP gateways

  - Supported PBXs when using an AudioCodes VoIP gateway

  - Supported PBXs when using a dialogic VoIP gateway
    
      - PBXs supported when using a DMG1000 series Media Gateway
    
      - PBXs supported when using a DMG 2000 series Media Gateway
    
      - PBXs supported when using a DMG3000 series Media Gateway

  - Supported IP PBXs

  - Supported IP PBXs when using SIP media gateways

  - Exchange Unified Messaging, Office Communications Server 2007 R2, and Microsoft Lync Server

## Ресурсы, помогающие в развертывании единой системы обмена сообщениями

Создание рекомендаций по развертыванию телефонных сетей является сложной задачей . Телефонные сети могут очень сильно отличаться друг от друга, потому что они могут включать шлюзы VoIP, УАТС и УАТС на основе протокола IP с различными параметрами, микропрограммами и требованиями. Однако доступны некоторые ресурсы, помогающие успешно развернуть единую систему обмена сообщениями.

  - **Специалисты по единой системе обмена сообщениями**   Специалисты по единой системе обмена сообщениями — это системные интеграторы, прошедшие техническое обучение по единой системе обмена сообщениями Exchange под руководством инженерной группы Exchange. Чтобы обеспечить беспроблемный переход на единую систему обмена сообщениями с устаревших систем голосовой почты, корпорация Майкрософт рекомендует всем клиентам воспользоваться помощью специалистов по единой системе обмена сообщениями. Контактные сведения см. на страницах [Специалисты по единой системе обмена сообщениями Microsoft Exchange Server 2013](https://go.microsoft.com/fwlink/p/?linkid=262708) и [Microsoft Pinpoint для единой системы обмена сообщениями](https://go.microsoft.com/fwlink/p/?linkid=261951).

  - **Заметки по конфигурации для поддерживаемых шлюзов VoIP, IP-УАТС и УАТС**   Эти примечания содержат параметры настройки и другую информацию, которая пригодится при настройке шлюзов VoIP, IP-УАТС и УАТС для взаимодействия с серверами единой системы обмена сообщениями, находящимися в вашей сети. Подробнее см. в статье [Заметки по конфигурации для поддерживаемых шлюзов VoIP, IP-УАТС и УАТС](configuration-notes-for-supported-voip-gateways-ip-pbxs-and-pbxs-exchange-2013-help.md).

  - **Заметки по конфигурации для поддерживаемых пограничных контроллеров сеансов**. Эти заметки содержат параметры настройки и другую информацию, которая пригодится при настройке пограничных контроллеров сеансов (SBC) для обмена данными с серверами единой системы обмена сообщениями при гибридных развертываниях и развертываниях этой системы в Exchange Online. Подробнее см. в статье [Сведения о конфигурации для поддерживаемых пограничных контроллеров сеансов](configuration-notes-for-supported-session-border-controllers-exchange-2013-help.md).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Поддержка Exchange Online единой системы обмена СООБЩЕНИЯМИ для сторонних производителей УАТС с помощью прямого подключения от клиентов, используемых SBC приведет к сбросу в 2018 июля. Прочитайте блог группы разработчиков Exchange <a href="https://blogs.technet.microsoft.com/exchange/2017/07/18/discontinuation-of-support-for-session-border-controllers-in-exchange-online-unified-messaging/">прекращении поддержки для пограничных контроллеров сеансов в Exchange Online единой системы обмена сообщениями</a> для получения дополнительных сведений.</td>
    </tr>
    </tbody>
    </table>


Перед обращением к специалисту по единой системе обмена сообщениями убедитесь, что вы можете ответить на ключевые вопросы, которые он задаст. Знание ответов на приведенные ниже вопросы поможет сделать взаимодействие со специалистом по единой системе обмена сообщениями более продуктивным.

  - Каково количество пользователей телефонии и голосовой почты в организации?

  - Для какого количества пользователей предполагается развернуть единую систему обмена сообщениями?

  - Какие УАТС предполагается использовать для интеграции с единой системой обмена сообщениями?

  - Сколько УАТС имеется в организации? Укажите их поставщиков, типы (коммутируемая или основанная на IP), модели и версии микропрограмм.

  - Подключены ли УАТС к сети? Централизованы ли они или расположены в разных местах?

  - Какие системы голосовой почты в настоящее время используются в организации? Укажите их поставщиков, типы, модели и версии микропрограмм.

  - Как системы голосовой почты интегрированы с УАТС (аналоговая связь, T1/E1, PRI, Digital Set Emulation, VoIP, иная технология)?

  - Используется ли передача голоса по сети?

  - Какие типы факсимильных систем используются в организации? Поддерживают ли они маршрутизацию входящих факсов для Exchange?

  - Используются ли в организации автосекретари?

  - Необходимо ли обеспечить поддержку пользователей только телефонии, т. е. пользователей, которым не нужен доступ к электронной почте?

## Поддерживаемые шлюзы VoIP

Для интеграции единой системы обмена сообщениями с УАТС необходимо использовать один или несколько шлюзов VoIP для преобразования протоколов с коммутацией каналов, используемых УАТС с временным уплотнением, в протоколы с коммутацией пакетов на основе протокола IP, используемые единой системой обмена сообщениями. Тестирование на совместимость с единой системой обмена сообщениями прошли несколько моделей медиашлюзов VoIP различных поставщиков.

Тестирование на взаимодействие с единой системы обмена сообщениями со шлюзами VoIP, IP-УАТС и пограничными контроллерами сеансов объединено с программой открытого взаимодействия объединенных коммуникаций Майкрософт (Unified Communications Open Interoperability Program). Дополнительные сведения см. в статье [Microsoft Unified Communications Open Interoperability Program](http://go.microsoft.com/fwlink/p/?linkid=140722).

Квалификационная [программа открытого взаимодействия объединенных коммуникаций Майкрософт](http://go.microsoft.com/fwlink/p/?linkid=140722) для простых и усовершенствованных шлюзов VoIP и IP-УАТС обеспечивает клиентам простую установку и техническую поддержку при использовании одобренных телефонных шлюзов VoIP и IP-УАТС с программным обеспечением объединенных коммуникаций Майкрософт. Одобрение получают только продукты, соответствующие жестким и обширным требованиям тестирования, а также спецификациям и планам тестирования.

Сведения о настройке поддерживаемых шлюзов VoIP, IP-УАТС, УАТС и пограничных контроллеров сеансов см. в одном из следующих ресурсов.

  - [Заметки по конфигурации для поддерживаемых шлюзов VoIP, IP-УАТС и УАТС](configuration-notes-for-supported-voip-gateways-ip-pbxs-and-pbxs-exchange-2013-help.md)

  - [Сведения о конфигурации для поддерживаемых пограничных контроллеров сеансов](configuration-notes-for-supported-session-border-controllers-exchange-2013-help.md)

Взаимодействие проверено для следующих поставщиков шлюзов VoIP.

  - AudioCodes

  - Dialogic

  - В следующей таблице указаны эти компании, модели шлюзов VoIP и протоколы, поддерживаемые каждой моделью.

### Шлюзы VoIP, поддерживаемые единой системой обмена сообщениями

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Поставщик</th>
<th>Модель</th>
<th>Поддерживаемые протоколы</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AudioCodes</p></td>
<td><p>MediaPack 114/8 FXO</p></td>
<td><ul>
<li><p>Аналоговый с внутриполосной сигнализацией DTMF</p></li>
<li><p>Аналоговый с SMDI</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000</p></td>
<td><ul>
<li><p>Аналоговый с внутриполосной сигнализацией DTMF</p></li>
<li><p>Аналоговый с SMDI</p></li>
<li><p>BRI Q.SIG</p></li>
<li><p>T1/E1 Q.SIG</p></li>
<li><p>IP-в-IP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><ul>
<li><p>T1/E1 CAS</p></li>
<li><p>T1/E1 Q.SIG</p></li>
<li><p>IP-в-IP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Dialogic</p></td>
<td><p>DMG1000PBXDNIW</p></td>
<td><p>Digital Set Emulation</p></td>
</tr>
<tr class="odd">
<td><p>Dialogic</p></td>
<td><p>DMG1000LSW</p></td>
<td><ul>
<li><p>Аналоговый с внутриполосной сигнализацией DTMF</p></li>
<li><p>Аналоговый с SMDI</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Dialogic</p></td>
<td><p>DMG2000</p></td>
<td><ul>
<li><p>T1 CAS</p></li>
<li><p>T1/E1 Q.SIG</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Dialogic</p></td>
<td><p>DMG3000</p></td>
<td><ul>
<li><p>BRI Q.SIG</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>NET</p></td>
<td><p>VX1200</p></td>
<td><ul>
<li><p>T1 Q.SIG</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Sonus</p></td>
<td><p>SBC 1000/2000 2.2.1 или более поздней версии</p></td>
<td><ul>
<li><p>Передача сигналов с использованием TDM (ISDN): AT&amp;T 4ESS/5ESS, Nortel DMS- 100, Euro ISDN (ETSI 300-102), QSIG, NTT InsNet (Япония), ANSI National ISDN-2 (NI-2)</p></li>
<li><p>Передача сигналов с использованием TDM (CAS): T1 CAS (E&amp;M, коммутация по шлейфу); E1 CAS (R2)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Quintum</p></td>
<td><p>Tenor DX Series</p></td>
<td><ul>
<li><p>T1 Q.SIG</p></li>
</ul></td>
</tr>
</tbody>
</table>


## УАТС, поддерживаемые при использовании шлюза VoIP компании AudioCodes

В следующей таблице указаны УАТС, которые поддерживаются с использованием шлюзов VoIP компании AudioCodes, включая MediaPack-114 FXO, MediaPack-118 FXO и Mediant 2000.

### УАТС, поддерживаемые при использовании шлюза VoIP компании AudioCodes

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Изготовитель УАТС</th>
<th>Модель или тип УАТС</th>
<th>Модель AudioCodes; «x» заменяется при необходимости на 4 или 8, «y» — на 1, 2, 4, 8 или 16</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Alcatel</p></td>
<td><p>OmniPCX 4400</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Aastra</p></td>
<td><p>M1000, M2000</p></td>
<td><ul>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>Definity G3</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Avaya</p></td>
<td><p>Magix/Merlin</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>S8300</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Avaya</p></td>
<td><p>S8700</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>IP Office</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Cisco</p></td>
<td><p>CallManager 4.x</p></td>
<td><ul>
<li><p>Mediant1000/IP-to-IP</p></li>
<li><p>Mediant2000/IP-to-IP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>NEC</p></td>
<td><p>Electra Elite</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>NEC</p></td>
<td><p>NEAX2400</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant2000/ySpans/SIP/RS232</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>NeXspan</p></td>
<td><p>S</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Nortel</p></td>
<td><p>Communication Server-1000M, 1000S, 1000E</p></td>
<td><ul>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Nortel</p></td>
<td><p>Meridian 11c, 51c, 61c, 81c</p></td>
<td><ul>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Panasonic</p></td>
<td><p>KX-TES824, KX-TEA308</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Panasonic</p></td>
<td><p>KX-TDA30, KX-TDA100, KX-TDA200, KX-TDA600</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Shortel</p></td>
<td><p>IP Telephony System</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiCom 150E</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiPath 3550</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiPath 4000</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Tadiran Telecom</p></td>
<td><p>Coral Flexicom, Coral IPX</p></td>
<td><ul>
<li><p>MediaPack 11x/FXO/AC/SIP-0</p></li>
<li><p>Mediant1000/ySpans/SIP</p></li>
<li><p>Mediant2000/ySpans/SIP</p></li>
</ul></td>
</tr>
</tbody>
</table>


## УАТС, поддерживаемые при использовании шлюза VoIP компании Dialogic

Каждый шлюз VoIP компании Dialogic поддерживает различные УАТС. В следующих таблицах приведены сведения об изготовителях и моделях УАТС и шлюзах VoIP компании Dialogic, которые можно с ними использовать. Каждый шлюз VoIP использует различные методы сигнализации, степени плотности размещения портов и протоколы.

## УАТС, поддерживаемые при использовании медиашлюза серии DMG1000

В следующей таблице указаны УАТС, которые поддерживаются шлюзом Dialogic Media Gateway (DMG1000) с низкой плотностью портов. Однако при использовании аналогового шлюза DMG1000 необходима дополнительная система передачи сигналов (протоколы RS232 SMDI, MD110, MCI или внутриполосная система DTMF).

### УАТС, поддерживаемые при использовании шлюза VoIP Dialogic DMG1000 с низкой плотностью

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Изготовитель УАТС</th>
<th>Модель или тип УАТС</th>
<th>Модель шлюза DMG и дополнительная система передачи сигналов</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aastra</p></td>
<td><p>Aastra MD110 (ранее Ericsson MD110)</p></td>
<td><p>DMG1008LSW</p>
<p>Аналоговое подключение с использованием протокола MD110 RS232</p></td>
</tr>
<tr class="even">
<td><p>Alcatel</p></td>
<td><p>Omni PCX 4400</p></td>
<td><p>DMG1008LSW</p></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>Definity G3 S8100, S8300, S8700 и S8710 (программное обеспечение Communications Mgr V2.0 или более поздней версии)</p></td>
<td><p>DMG1008DNIW</p></td>
</tr>
<tr class="even">
<td><p>Intercom</p></td>
<td><p></p></td>
<td><p>DMG1008LSW</p>
<p>Аналоговое подключение с использованием последовательного протокола SMDI</p></td>
</tr>
<tr class="odd">
<td><p>Mitel</p></td>
<td><p>SX-200D, SX-200 Light, SX-2000 Light, SX-2000 S, SX-2000 VS, SX-200 ICP</p></td>
<td><p>DMG1008MTLDNIW</p></td>
</tr>
<tr class="even">
<td><p>NEC</p></td>
<td><p>2000, 2400, 2400 IPX</p></td>
<td><p>DMG1008DNIW</p></td>
</tr>
<tr class="odd">
<td><p>Nortel</p></td>
<td><p>Meridian 1 - Option 11, 21, 21A, 51, 61, 71 и 81</p>
<p>Meridian SL1 - Generic X11, выпуск 15 или более поздний</p>
<p>Nortel Communication Server - 1000M, 1000S, 1000E с V3.0 или более поздней версии</p></td>
<td><p>DMG1008DNIW</p></td>
</tr>
<tr class="even">
<td><p>Nortel</p></td>
<td><p>SL 100</p></td>
<td><p>DMG1008LSW</p>
<p>Аналоговое подключение с использованием последовательного протокола SMDI</p></td>
</tr>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiCom 300E CS</p></td>
<td><p>DMG1008DNIW</p></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiCom 300E (европейский)</p></td>
<td><p>DMG1008LSW</p>
<p>Аналоговое подключение с использованием внутриполосной системы передачи сигналов DTMF</p></td>
</tr>
<tr class="odd">
<td><p>Siemens/ROLM</p></td>
<td><p>8000 (программное обеспечение выпуска 80003 или более поздней версии)<br />
9000 (все версии)</p>
<p>9751 (все версии программного обеспечения 9005)</p>
<p>9751 (выпуск программного обеспечения 9006.4 или более поздней версии)</p></td>
<td><p>DMG1008RLMDNIW</p></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiPath 4000</p></td>
<td><p>DMG1008LSW</p></td>
</tr>
<tr class="odd">
<td><p>Toshiba</p></td>
<td><p>CTX (программное обеспечение версии AR1ME021.00)</p></td>
<td><p>DMG1008LSW</p></td>
</tr>
<tr class="even">
<td><p>Другие</p></td>
<td><p>Различные модели</p></td>
<td><p>DMG1008LSW</p>
<p>Аналоговое подключение с использованием либо внутриполосной системы передачи сигналов DTMF, либо SMDI</p></td>
</tr>
</tbody>
</table>


## УАТС, поддерживаемые при использовании медиашлюза серии DMG 2000

В следующей таблице указаны УАТС, которые поддерживаются шлюзом T1/E1 Dialogic Media Gateway (DMG2000). Шлюз DMG2000, выпускаемый с однократной (DMG2030DTIQ), двукратной (DMG2060DTIQ) и четырехкратной (DMG2120DTIQ) плотностью, поддерживает следующие протоколы:

  - T1 CAS

  - T1 Q.SIG

  - E1 Q.SIG

  - T1 NI-2

  - T1 5ESS

  - T1 DMS100

Если используется технология передачи сигналов CAS (Channel Associated Signaling), необходима дополнительная система передачи сигналов (протоколы RS232 SMDI, MD110, MCI или внутриполосная система DTMF). Если используется система передачи сигналов Q.SIG, УАТС должна поддерживать дополнительные службы, связанные со сведениями о вызывающей и вызываемой сторонах, и возможности передачи вызовов, необходимые для единой системы обмена сообщениями.

### УАТС, поддерживаемые медиашлюзом DMG2000

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Изготовитель УАТС</th>
<th>Модель или тип УАТС</th>
<th>Необходимая версия программного обеспечения</th>
<th>Протокол и дополнительная система передачи сигналов</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Alcatel</p></td>
<td><p>Omni PCX 4400</p></td>
<td><p>3.2.712.5</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Avaya</p></td>
<td><p>Definity G3</p></td>
<td><p>3 или последующие версии</p></td>
<td><p>T1 CAS</p></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>S8500</p></td>
<td><p>Manager SW V2.0 или более поздней версии</p></td>
<td><p>T1 CAS</p>
<p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Ericsson</p></td>
<td><p>MD110</p></td>
<td><p>Выпуск MX1 TSW R2A (BC13)</p></td>
<td><p>E1 Q.SIG</p></td>
</tr>
<tr class="odd">
<td><p>Intercom</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>CAS (с последовательным протоколом SMDI)</p></td>
</tr>
<tr class="even">
<td><p>NEC</p></td>
<td><p>2400 IMX</p></td>
<td><p>Выпуск 5200 декабрь 1992 1b или последующие версии</p></td>
<td><p>CAS (с последовательным протоколом MCI)</p></td>
</tr>
<tr class="odd">
<td><p>NEC</p></td>
<td><p>2400 IPX</p></td>
<td><p>R17, выпуск 03.46.001</p></td>
<td><p>T1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Nortel</p></td>
<td><p>Meridian 1 — вариант 11c</p></td>
<td><p>Выпуск 15 или последующие версии, необходимы варианты 19 и 46</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="odd">
<td><p>Nortel</p></td>
<td><p>Communication Server 1000</p></td>
<td><p>Версия 2121, выпуск 4</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiCom 300E CS</p></td>
<td><p>Выпуск 9006.4 или более поздний (примечание: только программное обеспечение для Северной Америки)</p></td>
<td><p>T1 CAS</p></td>
</tr>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiPath 4000</p></td>
<td><p>V2 SMR 9 SMPO</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="even">
<td><p>Mitel</p></td>
<td><p>SX-2000 S, SX-2000 VS</p></td>
<td><p>LW 34</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
<tr class="odd">
<td><p>Mitel</p></td>
<td><p>3300</p></td>
<td><p>Версия 5.1.4.8</p></td>
<td><p>T1 Q.SIG</p>
<p>E1 Q.SIG</p></td>
</tr>
</tbody>
</table>


## УАТС, поддерживаемые при использовании медиашлюза серии DMG4008BRI

Медиашлюз серии DMG4000 поставляется с несколькими вариантами интерфейса TDM. DMG4008BRI поддерживает плотность 4 порта/8 каналов и следующие протоколы:

  - ISDN BRI Q.SIG

  - ETSI-DSS1 (Euro ISDN)

  - NET 3 (Бельгия)

  - VN3 (Франция)

  - 1TR6 (Германия)

  - INS-64 (Япония)

  - 5ESS Custom (Северная Америка - AT\&T)

  - National ISDN (NI1 — Северная Америка)

В следующей таблице указаны АТС, которые поддерживаются при использовании медиашлюза Dialogic 4000 (DMG4008).

### АТС, поддерживаемые при использовании медиашлюза DMG4008BRI

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Изготовитель УАТС</th>
<th>Модель или тип УАТС</th>
<th>Необходимая версия программного обеспечения</th>
<th>Протокол и дополнительная система передачи сигналов</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Siemens</p></td>
<td><p>HiCom 300</p></td>
<td><p>SA300-V3.05</p></td>
<td><p>BRI-Q.SIG (ECMAV2)</p></td>
</tr>
<tr class="even">
<td><p>Siemens</p></td>
<td><p>HiPath 4000</p></td>
<td><p>S.0 B4400</p></td>
<td><p>BRI-Q.SIG (ECMAV2)</p></td>
</tr>
</tbody>
</table>


## Поддерживаемые УАТС на основе протокола IP

IP-УАТС также поддерживаются единой системой обмена сообщениями. В следующей таблице указаны IP-УАТС, которые поддерживаются с помощью прямого подключения по протоколу SIP к единой системе обмена сообщениями.

### IP-УАТС, которые поддерживаются с помощью прямого подключения по протоколу SIP

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Изготовитель УАТС</th>
<th>Модель или тип УАТС</th>
<th>Необходимая версия программного обеспечения</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aastra</p></td>
<td><p>MX-ONE</p></td>
<td><p>4.0</p></td>
</tr>
<tr class="even">
<td><p>Avaya</p></td>
<td><p>Aura</p></td>
<td><p>5.2.1 с пакетом обновления 5 (SP5)</p></td>
</tr>
<tr class="odd">
<td><p>Avaya</p></td>
<td><p>Communication Server 2100</p></td>
<td><p>CS2100 SE13</p></td>
</tr>
<tr class="even">
<td><p>Cisco</p></td>
<td><p>Диспетчер звонков, Unified Communications Manager</p></td>
<td><p>5.1, 6.x, 7.0 and8.0</p></td>
</tr>
</tbody>
</table>


## IP-УАТС, поддерживаемые при использовании медиашлюзов SIP

IP-УАТС, использующие медиашлюзы SIP, также поддерживаются единой системой обмена сообщениями. В следующей таблице показаны IP-УАТС, которые поддерживаются с помощью функций IP-в-IP медиашлюзов SIP для подключения к единой системе обмена сообщениями.

### IP-УАТС, поддерживаемые при использовании медиашлюзов SIP

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Изготовитель УАТС</th>
<th>Модель или тип УАТС</th>
<th>Модель шлюза SIP</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cisco</p></td>
<td><p>Диспетчер звонков 4.x</p></td>
<td><p>AudioCodes Mediant 1000/2000 (с туннелем IP-в-IP)</p></td>
</tr>
</tbody>
</table>


## Единая система обмена сообщениями Exchange, Office Communications Server 2007 R2 и Microsoft Lync Server

При локальных и гибридных развертываниях единую систему обмена сообщениями Exchange, Майкрософт Office Communications Server 2007 R2 и Майкрософт Lync Server 2010 или Lync Server 2013 можно развернуть совместно для обеспечения обмена голосовыми и мгновенными сообщениями, улучшенного режима присутствия пользователя, проведения аудио- и видеоконференций, а также для предоставления встроенного решения электронной почты и обмена сообщениями для пользователей в организации. Дополнительные сведения см. в следующих разделах:

  - [Развертывание единой системы обмена сообщениями в Exchange 2013 и обзор Lync Server](deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md)

  - [Microsoft Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=202010)

Дополнительные сведения о программе открытого взаимодействия объединенных коммуникаций Майкрософт для телефонной инфраструктуры предприятия, включая поиск одобренных шлюзов SIP ТСОП и IP-УАТС, а также описание процесса присоединения поставщиков телефонной инфраструктуры к программе и участия в ней см. на странице [Microsoft Unified Communications Open Interoperability Program](https://go.microsoft.com/fwlink/p/?linkid=132071).

