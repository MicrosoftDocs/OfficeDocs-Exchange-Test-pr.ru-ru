---
title: 'Невозможно установить Exchange 2013 в лесу, в котором находятся серверы Exchange 2000 или Exchange 2003. параметр: Exchange 2013 Help'
TOCTitle: Невозможно установить Exchange 2013 в лесу, в котором находятся серверы Exchange 2000 или Exchange 2003. параметр
ms:assetid: a115b182-cbd2-4d31-aa0e-375240939301
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.exchange2000or2003presentinorg(v=EXCHG.150)
ms:contentKeyID: 50488753
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Невозможно установить Exchange 2013 в лесу, в котором находятся серверы Exchange 2000 или Exchange 2003. параметр

 

_**Применимо к:**Exchange Server_

_**Последнее изменение раздела:**2016-12-09_

Приложение Microsoft Exchange Server 2013 не может продолжить работу, так как в лесу Active Directory найдены один или несколько компьютеров с Exchange 2000 Server или Exchange Server 2003. Прежде чем установить Exchange 2013, необходимо удалить из леса все сервера Exchange 2000 и Exchange 2003. Почтовые ящики, общие папки и все другие объекты или компоненты Exchange необходимо обновить либо до версии Exchange Server 2007, либо до Exchange Server 2010. Обновление непосредственно с версии Exchange 2000 или Exchange 2003 до версии Exchange 2013 невозможно.

Необходимый путь установки Exchange 2013 в организации зависит от версии Exchange, которая установлена в лесу в данный момент. Дополнительные сведения см. в следующей таблице:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Если в вашей организации установлены следующие программы</th>
<th>Необходимо использовать этот путь для обновления до версии Exchange 2013</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange 2000</p></td>
<td><ol>
<li><p>Установите Exchange 2007 в вашей организации Exchange 2000.</p></li>
<li><p>Настройте совместную работу приложений Exchange 2007 и Exchange 2000.</p></li>
<li><p>Перенесите почтовые ящики, общие папки и другие компоненты Exchange 2000 в службу Exchange 2007.</p></li>
<li><p>Спишите и удалите все сервера Exchange 2000.</p></li>
<li><p>Install Exchange 2013 into your Exchange 2007 organization.</p></li>
<li><p>Configure Exchange 2013 and Exchange 2007 coexistence.</p></li>
<li><p>Перенесите почтовые ящики, общие папки и другие компоненты Exchange 2007 в службу Exchange 2013.</p></li>
<li><p>Спишите и удалите все сервера Exchange 2007.</p></li>
</ol>
<p>Дополнительные сведения см. на странице <a href="https://go.microsoft.com/fwlink/p/?linkid=103281">Обновление до Exchange 2007</a> и <a href="upgrade-from-exchange-2007-to-exchange-2013-exchange-2013-help.md">Обновление с Exchange 2007 до Exchange 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>Exchange 2003</p></td>
<td><ol>
<li><p>Установите Exchange 2010 в вашей организации Exchange 2003.</p></li>
<li><p>Настройте совместную работу приложений Exchange 2010 и Exchange 2003.</p></li>
<li><p>Перенесите почтовые ящики, общие папки и другие компоненты Exchange 2003 в службу Exchange 2010.</p></li>
<li><p>Спишите и удалите все сервера Exchange 2003.</p></li>
<li><p>Установите Exchange 2013 в вашей организации Exchange 2010.</p></li>
<li><p>Настройте совместную работу приложений Exchange 2013 и Exchange 2010.</p></li>
<li><p>Перенесите почтовые ящики, общие папки и другие компоненты Exchange 2010 в службу Exchange 2013.</p></li>
<li><p>Спишите и удалите все сервера Exchange 2010.</p></li>
</ol>
<p>Дополнительные сведения см. на странице <a href="https://go.microsoft.com/fwlink/p/?linkid=268414">Exchange 2003 – Планирование стратегии обновления и совместной работы</a> и <a href="upgrade-from-exchange-2010-to-exchange-2013-exchange-2013-help.md">Обновление с Exchange 2010 до Exchange 2013</a>.</p></td>
</tr>
</tbody>
</table>


При обновлении до версии Exchange 2010 или Exchange 2013, для завершения процесса развертывания, можно использовать помощник развертывания Exchange. Дополнительные сведения см. по следующим ссылкам:

  - [Помощник по развертыванию Exchange 2010](https://go.microsoft.com/fwlink/p/?linkid=171086)

  - [Помощник по развертыванию Exchange 2013](https://go.microsoft.com/fwlink/p/?linkid=277105)

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

