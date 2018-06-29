---
title: 'Не удается найти службу обновления получателей_RUSMissing: Exchange 2013 Help'
TOCTitle: Не удается найти службу обновления получателей_RUSMissing
ms:assetid: 920fbf51-d5e4-4ac6-869f-7f1c5d9a3024
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.rusmissing(v=EXCHG.150)
ms:contentKeyID: 50488638
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Не удается найти службу обновления получателей\_RUSMissing

 

_**Применимо к:**Exchange Server_

_**Последнее изменение раздела:**2016-12-15_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Не удается продолжить установку Microsoft® Exchange Server 2007 или Exchange Server 2010, поскольку служба обновления получателей (RUS), которая отвечает за домен в существующей организации Exchange, не может быть найдена.

Для программы установки Microsoft Exchange требуется, чтобы на каждом домене в существующей организации Exchange присутствовал экземпляр службы обновления получателей.

Если на домене отсутствует экземпляр службы обновления получателей, новые объекты-пользователи, созданные в домене, не получат выданные им адреса электронной почты.

Чтобы устранить эту проблему, убедитесь, что для каждого домена существует экземпляр службы обновления получателей, и создайте экземпляр службы обновления получателей для доменов, на которых его нет, а затем перезапустите программу установки Microsoft Exchange.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Создание экземпляра службы обновления получателей для домена</p></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Откройте диспетчер Exchange.</p></li>
<li><p>Разверните элемент <strong>Получатели</strong>.</p></li>
<li><p>Щелкните правой кнопкой мыши узел <strong>Службы обновления получателей</strong>, затем нажмите кнопку <strong>Создать</strong> и выберите элемент <strong>Служба обновления получателей</strong>.</p></li>
<li><p>В окне &quot;Создать объект&quot; нажмите кнопку <strong>Обзор</strong>, чтобы найти имя домена.</p></li>
<li><p>Выберите имя домена и нажмите кнопку <strong>ОК</strong>.</p></li>
<li><p>В окне &quot;Создать объект&quot; нажмите кнопку <strong>Далее</strong>, а затем — <strong>Готово</strong>.</p></li>
</ol></td>
</tr>
</tbody>
</table>


Дополнительные сведения о службе обновления получателей см. в следующих статьях базы знаний Майкрософт:

  - «Как службы обновления получателей применяется политиками получателей» ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=328738](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=328738)).

  - «Как службе обновления получателей заполняет списки адресов» ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=253828](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=253828)).

  - «Как контролировать ход службы обновления получателей Exchange» ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=246127](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=246127)).

  - «Задачи, выполняемые службой обновления получателей Exchange» ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=253770](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=253770)).

