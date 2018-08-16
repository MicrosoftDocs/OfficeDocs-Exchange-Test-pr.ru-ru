---
title: 'Обнаружен один или несколько серверов соединителей Active Directory'
TOCTitle: Обнаружен один или несколько серверов соединителей Active Directory_ADCFound
ms:assetid: a874f51f-09a2-4a76-9695-d61fb1ee6c1c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.adcfound(v=EXCHG.150)
ms:contentKeyID: 50488808
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Обнаружен один или несколько серверов соединителей Active Directory\_ADCFound

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2016-12-15_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Невозможно продолжить установку Microsoft Exchange Server 2007 и Exchange Server 2010, так как в текущей среде Microsoft Exchange обнаружен один или несколько соединителей Active Directory.

Соединитель Active Directory реплицирует объекты из Exchange Server 5.5 в службу каталогов Active Directory в гибридной среде Microsoft Exchange и не поддерживается в Exchange 2007 или Exchange 2010.

Для установки Exchange 2007 или Exchange 2010 необходимо удалить все компоненты соединителей Active Directory.

Чтобы устранить эту проблему, удалите все компоненты соединителей Active Directory, а затем и повторно запустите программу установки Exchange 2007 или Exchange 2010.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Удаление компонентов соединителей Active Directory</p></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Чтобы отключить службу соединителей Active Directory на сервере, на котором она работает, щелкните правой кнопкой мыши значок <strong>Мой компьютер</strong> на рабочем столе, а затем выберите элемент <strong>Управление</strong>.</p></li>
<li><p>Разверните узел <strong>Службы и приложения</strong>, а затем выберите узел <strong>Службы</strong>.</p></li>
<li><p>В правой области щелкните правой кнопкой мыши элемент <strong>Соединитель Microsoft Active Directory</strong>, а затем выберите элемент <strong>Свойства</strong>.</p></li>
<li><p>Установите для параметра <strong>Тип запуска</strong> значение <strong>Отключено</strong>. При следующем запуске компьютера служба соединителей Active Directory не запустится.</p></li>
<li><p>Нажмите кнопку <strong>Применить</strong>, а затем — кнопку <strong>ОК</strong>.</p></li>
<li><p>Чтобы удалить службу соединителей Active Directorty, используйте мастер установки Active Directory на компакт-диске с Microsoft Exchange 2000 Server или Microsoft Exchange Server 2003. Откройте папку \ADC\I386 и дважды щелкните значок программы Setup.exe. Следуйте инструкциям, чтобы <strong>Удалить все</strong> компоненты службы соединителей Active Directory.</p>

> [!IMPORTANT]  
> Чтобы устранить проблему, необходимо выполнить шаг 6 и <strong>Удалить все</strong> компоненты соединителей Active Directory. Недостаточно просто отключить службу соединителей Active Directory.

</li>
</ol></td>
</tr>
</tbody>
</table>


Дополнительные сведения о соединителях Active Directory см. в следующих статьях базы знаний Майкрософт:

  - 325300, «веб-трансляция: введение в Active Directory Connector» ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=325300](https://go.microsoft.com/fwlink/?linkid=3052&kbid=325300)).

  - 325221, «веб-трансляция: Microsoft расширенного соединителя Active Directory» ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=325221](https://go.microsoft.com/fwlink/?linkid=3052&kbid=325221)).

  - 312632, «Как установить и настроить соединитель Active Directory в Exchange 2000 Server» ([https://go.microsoft.com/fwlink/?linkid=3052\&kbid=312632](https://go.microsoft.com/fwlink/?linkid=3052&kbid=312632)).

