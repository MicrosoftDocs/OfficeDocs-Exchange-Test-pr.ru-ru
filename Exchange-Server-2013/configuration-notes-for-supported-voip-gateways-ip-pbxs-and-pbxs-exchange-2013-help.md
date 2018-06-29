---
title: 'Заметки по конфигурации для поддерживаемых шлюзов VoIP, IP-УАТС и УАТС: Exchange 2013 Help'
TOCTitle: Заметки по конфигурации для поддерживаемых шлюзов VoIP, IP-УАТС и УАТС
ms:assetid: 1583674f-5a57-45fd-8125-087d1624e686
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee681657(v=EXCHG.150)
ms:contentKeyID: 50556339
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Заметки по конфигурации для поддерживаемых шлюзов VoIP, IP-УАТС и УАТС

 

_**Применимо к:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2016-12-09_

На этой странице приведены ссылки на заметки по конфигурации, созданные и проверенные Майкрософт или партнерами по шлюзам VoIP. Когда Майкрософт или ее партнеры развертывают единую систему обмена сообщениями в новой конфигурации шлюза VoIP и УАТС или IP-УАТС, они документируют предварительные требования и параметры конфигурации. Эти сведения используются для создания заметки по конфигурации.

Каждая заметка по конфигурации УАТС содержит сведения о развертывании единой системы обмена сообщениями в определенной конфигурации телефонной системы, включая сведения об изготовителях, моделях и версиях встроенного ПО шлюзов VoIP, IP-УАТС или УАТС. Кроме того, каждая заметка по конфигурации УАТС может включать в себя другие сведения, указанные ниже.

  - Авторы заметки по конфигурации.

  - Подробное описание предварительных условий, включая следующие сведения:
    
      - функции, которые необходимо включить или отключить на УАТС;
    
      - специализированное оборудование, которое необходимо установить;
    
      - является ли шлюз VoIP обязательным;
    
      - функции, которые должны поддерживаться шлюзом VoIP, если он необходим;
    
      - требования к кабелям между шлюзом IP и УАТС;
    
      - список функций единой системы обмена сообщениями, которые могут быть недоступны в конкретной конфигурации телефонной системы.

Дополнительные сведения о программе открытого взаимодействия объединенных коммуникаций Майкрософт для телефонной инфраструктуры предприятия, включая поиск одобренных шлюзов SIP PSTN и IP-УАТС, а также описание процесса присоединения поставщиков телефонной инфраструктуры к программе и правил участия в ней, см. на странице [Программа открытого взаимодействия объединенных коммуникаций Майкрософт](https://go.microsoft.com/fwlink/p/?linkid=132071).

## Заметки по конфигурации шлюза VoIP, IP-УАТС и УАТС

В сотрудничестве с партнерами по шлюзам VoIP компаниями AudioCodes и Dialogic Майкрософт расширяет список протестированных УАТС. В настоящее время выполняется тестирование различных комбинаций компонентов телефонных систем, поэтому этот раздел часто обновляется. Если необходимая заметка по конфигурации отсутствует, вернитесь к этому разделу позже.

Доступны следующие заметки по конфигурации:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ul>
<li><p>Aastra</p></li>
<li><p>Alcatel</p></li>
<li><p>Avaya</p></li>
<li><p>Cisco</p></li>
<li><p>Inter-Tel</p></li>
<li><p>Intecom</p></li>
<li><p>Mitel</p></li>
<li><p>NEC</p></li>
</ul></td>
<td><ul>
<li><p>NeXspan</p></li>
<li><p>Nortel</p></li>
<li><p>Panasonic</p></li>
<li><p>Rolm</p></li>
<li><p>ShoreTel</p></li>
<li><p>Siemens</p></li>
<li><p>Sonus</p></li>
<li><p>Tadiran</p></li>
<li><p>Toshiba</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Aastra


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aastra MD110 (ранее Ericsson MD110)</p></td>
<td><p>MX1 TSW R2A (или BC13)</p></td>
<td><p>Аналоговый, серийный протокол MD110</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008LSW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Aastra MD110 (ранее Ericsson MD110)</p></td>
<td><p>MX1 TSW R2A (или BC13)</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Aastra MX-ONE</p></td>
<td><p>4.0</p></td>
<td><p>Прямое подключение SIP</p></td>
<td><p>—</p></td>
<td><p>—</p></td>
<td><p>Aastra</p></td>
<td><p><a href="http://www.aastra.com/cps/rde/aareddownload?file_id=4384-14746-_p06_xml%26dsproject=aastra%26mtype=pdf">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Alcatel


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OmniPCX 4400</p></td>
<td><p>R4.2-d2.304-4-h-il-c6s2</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Avaya


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aura</p></td>
<td><p>Communication Manager 5.2.1 с пакетом обновления 5 (SP5)</p>
<p>Диспетчер сеансов 5.2.</p></td>
<td><p>Прямое подключение SIP</p></td>
<td><p>—</p></td>
<td><p>—</p></td>
<td><p>Avaya</p></td>
<td><p><a href="https://support.avaya.com/downloads/">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>CS 2100</p></td>
<td><p>CS 2100 SE13</p></td>
<td><p>Прямое подключение SIP</p></td>
<td><p>—</p></td>
<td><p>—</p></td>
<td><p>Avaya</p></td>
<td><p><a href="https://support.avaya.com/css/p8/documents/100149819">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Definity G3</p></td>
<td><p>R009i.05.122.4</p></td>
<td><p>Digital Set Emulation (DNI7434)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008DNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Definity G3</p></td>
<td><p>R013i.01.1.628.7</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Definity G3</p></td>
<td><p>R013i.01.1.628.7</p></td>
<td><p>T1 CAS, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Definity G3</p></td>
<td><p>R013i.01.1.628.7</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Definity G3</p></td>
<td><p>R013i.01.1.628.7</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Merlin Magix</p></td>
<td><p>Выпуск 1.5 v.6.0</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>S8300</p></td>
<td><p>G3xV11 Communication Manager 1.3</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>S8300</p></td>
<td><p>R013x.01.2.632.1</p></td>
<td><p>T1 CAS, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>S8300</p></td>
<td><p>R013x.01.2.632.1</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>S8500</p></td>
<td><p>Communication Manager 3.0 (R013x00.1.346.0)</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>S8500</p></td>
<td><p>Communication Manager 3.0 (R013x00.1.346.0)</p></td>
<td><p>T1 CAS, внутриполосная передача DTMF</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>S8500</p></td>
<td><p>Communication Manager 3.0 (R013x00.1.346.0)</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>S8700</p></td>
<td><p>R011x.02.0.110.4</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Cisco


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cisco Call Manager 4.x</p></td>
<td><p>4.x</p></td>
<td><p>IP-в-IP</p></td>
<td><p>AudioCodes</p></td>
<td><p>AudioCodes</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Cisco Call Manager 5.1</p></td>
<td><p>5.1.0.9921-12</p></td>
<td><p>Прямое подключение SIP</p></td>
<td><p>—</p></td>
<td><p>—</p></td>
<td><p>Майкрософт</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=225083">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Cisco Unified Communications Manager 6.0 и 6.1</p></td>
<td><p>6.x</p></td>
<td><p>Прямое подключение SIP</p></td>
<td><p>—</p></td>
<td><p>—</p></td>
<td><p>Майкрософт</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=225083">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Cisco Unified Communications Manager 7.0</p></td>
<td><p>7.0.2.20000-5</p></td>
<td><p>Прямое подключение SIP</p></td>
<td><p>—</p></td>
<td><p>—</p></td>
<td><p>Майкрософт</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=196361">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Cisco Unified Communications Manager 8.0</p></td>
<td><p>8.0.3.20000-5</p></td>
<td><p>Прямое подключение SIP</p></td>
<td><p>—</p></td>
<td><p>—</p></td>
<td><p>Майкрософт</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=213007">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Inter-Tel


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5000</p></td>
<td><p>Inter-Tel 5000 v2.1</p></td>
<td><p>T1 CAS, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Axxess</p></td>
<td><p>Axxess V9.0</p></td>
<td><p>T1 CAS, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Intecom


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PointSpan M6880</p></td>
<td><p>40PS3.5.K.2</p></td>
<td><p>T1 CAS, SMDI</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Mitel


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>3300</p></td>
<td><p>5.1.4.8</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>3300</p></td>
<td><p>5.1.4.8</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>SX2000</p></td>
<td><p>5.0.24</p></td>
<td><p>Digital Set Emulation (DNISS430)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008MTLDNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>3300</p></td>
<td><p>7</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
</tbody>
</table>


## NEC


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Electra Elite 192</p></td>
<td><p>SP034V4.5</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>NEAX2400IMX</p></td>
<td><p>Версия 7400</p></td>
<td><p>T1 CAS, серийный протокол MCI</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>NEAX2400IMX &amp; IPX</p></td>
<td><p>Версия 7400</p></td>
<td><p>Digital Set Emulation (DNIDtermIII)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008DNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>NEAX2400IPX</p></td>
<td><p>Версия R18.06.24.000</p></td>
<td><p>T1 CAS, серийный протокол MCI</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>NEAX2400IPX</p></td>
<td><p>Версия R18.06.24.000</p></td>
<td><p>Аналоговый, серийный протокол MCI</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>NEAX2400IPX</p></td>
<td><p>Версия 17, выпуск 03.46.001</p></td>
<td><p>T1 Q.SIG, серийный протокол MCI</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
</tbody>
</table>


## NeXspan


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>S</p></td>
<td><p>RMS1 версии R1.3 E1TA</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Nortel


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CS1000</p></td>
<td><p>3.0 &amp; 4.5</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Meridian 81C</p></td>
<td><p>4.5</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Meridian 81C</p></td>
<td><p>4.5</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Option11c</p></td>
<td><p>Выпуск 25</p></td>
<td><p>Digital Set Emulation (DNI2616)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008DNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Option11c</p></td>
<td><p>Выпуск 25</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Option11c</p></td>
<td><p>Выпуск 25</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>CS-1000M (Succession)</p></td>
<td><p>Выпуск 25.40</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Panasonic


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>KX-TDA200</p></td>
<td><p>001-001</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>KX-TDA200</p></td>
<td><p>3</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>KX-TES824</p></td>
<td><p>2.0.2</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Rolm


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>9751</p></td>
<td><p>9005</p></td>
<td><p>Digital Set Emulation (DNIRP400)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008RLMDNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
</tbody>
</table>


## ShoreTel


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IP Telephony System</p></td>
<td><p>6.1</p></td>
<td><p>Аналоговый, SMDI</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>IP Telephony System</p></td>
<td><p>7.5</p></td>
<td><p>Аналоговый, SMDI</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Siemens


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HiCom 150E</p></td>
<td><p>Выпуск 2.2</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>HiCom 300</p></td>
<td><p>SA300-V3.05</p></td>
<td><p>BRI QSIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG3000</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>HiCom 300</p></td>
<td><p>9006.4SMR3</p></td>
<td><p>Digital Set Emulation (DNIOptiset)</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008DNIW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>HiCom 300</p></td>
<td><p>9006.4SMR3</p></td>
<td><p>T1 CAS, внутриполосная передача DTMF</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>HiPath 3550</p></td>
<td><p>Выпуск 3</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>HiPath 4000</p></td>
<td><p>Версия 3.0 SMR5 SMP4</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>HiPath 4000</p></td>
<td><p>SA300-V3.05</p></td>
<td><p>BRI QSIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG3000</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>HiPath 4000</p></td>
<td><p>Версия 3.0 SMR5 SMP4</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>HiPath 4000</p></td>
<td><p>Версия 2.0 SMR9 SMP0</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008LSW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>HiPath 4000</p></td>
<td><p>Версия 2.0 SMR9 SMP0</p></td>
<td><p>T1 Q.SIG</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG2030DTIQ</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Sonus


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Модель шлюза VoIP</th>
<th>Выпуск программного обеспечения шлюза VoIP</th>
<th>Поддерживаемые протоколы</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SBC 1000/2000</p></td>
<td><p>2.2.1 или более поздняя версия</p></td>
<td><ul>
<li><p>Передача сигналов с использованием TDM (ISDN): AT&amp;T 4ESS/5ESS, Nortel DMS- 100, Euro ISDN (ETSI 300-102), QSIG, NTT InsNet (Япония), ANSI National ISDN-2 (NI-2)</p></li>
<li><p>Передача сигналов с использованием TDM (CAS): T1 CAS (E&amp;M, коммутация по шлейфу); E1 CAS (R2)</p></li>
</ul></td>
<td><p>Sonus</p></td>
<td><p><a href="http://www.sonus.net/sites/default/files/sonussbc1k2kconfigo365.pdf">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Tadiran


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Coral Flexicom</p></td>
<td><p>14.67.49</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP 11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Coral Flexicom</p></td>
<td><p>14.67.49</p></td>
<td><p>BRI QSIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant</p>
<p>1000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Coral Flexicom</p></td>
<td><p>14.67.49</p></td>
<td><p>E1 CAS, внутриполосная передачи DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Coral Flexicom</p></td>
<td><p>14.67.49</p></td>
<td><p>E1 Q.SIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Coral IPX</p></td>
<td><p>14.67.49</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>MP-11x FXO</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Coral IPX</p></td>
<td><p>14.67.49</p></td>
<td><p>BRI QSIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 1000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="odd">
<td><p>Coral IPX</p></td>
<td><p>14.67.49</p></td>
<td><p>E1 CAS, внутриполосная передачи DTMF</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant 2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>Coral IPX</p></td>
<td><p>14.67.49</p></td>
<td><p>E1 QSIG</p></td>
<td><p>AudioCodes</p></td>
<td><p>Mediant</p>
<p>1000/2000</p></td>
<td><p>AudioCodes</p></td>
<td><p><a href="https://www.audiocodes.com/solutions/microsoft-unified-messaging">Скачать</a></p></td>
</tr>
</tbody>
</table>


## Toshiba


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
<th>Модель УАТС</th>
<th>Выпуск программного обеспечения для УАТС</th>
<th>Протокол</th>
<th>Поставщик шлюза</th>
<th>Модель шлюза</th>
<th>Автор конфигурации</th>
<th>Загружаемый файл конфигурации</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CTX</p></td>
<td><p>AR1ME021.00</p></td>
<td><p>Аналоговый, SMDI</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008LSW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
<tr class="even">
<td><p>CTX</p></td>
<td><p>AR1ME021.00</p></td>
<td><p>Аналоговый, внутриполосная передача DTMF</p></td>
<td><p>Dialogic</p></td>
<td><p>DMG1008LSW</p></td>
<td><p>Dialogic</p></td>
<td><p><a href="https://www.dialogic.com/support/helpweb/mg/integration.htm">Скачать</a></p></td>
</tr>
</tbody>
</table>

