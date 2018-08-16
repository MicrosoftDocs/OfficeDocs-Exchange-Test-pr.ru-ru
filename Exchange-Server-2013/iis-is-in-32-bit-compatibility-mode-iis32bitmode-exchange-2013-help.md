---
title: 'Справка по Exchange 2013: IIS в режиме совместимости с 32-разрядной системой'
TOCTitle: IIS находится в mode_IIS32BitMode совместимость 32-разрядная версия
ms:assetid: 742dfc32-353c-46a2-830e-68aed6a68ce0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.iis32bitmode(v=EXCHG.150)
ms:contentKeyID: 50488412
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# IIS находится в mode\_IIS32BitMode совместимость 32-разрядная версия

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2012-06-05_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Установку Microsoft® Exchange Server 2007 не удается продолжить, так как служба IIS (Microsoft Internet Information Service) работает на данном 64-разрядном компьютере в 32-разрядном режиме.

Для приложения Exchange 2007 требуется, чтобы на 64-разрядном компьютере служба IIS работала в 64-разрядном режиме.

Чтобы устранить данную проблему, переключите службу IIS в 64-разрядный режим, а затем перезапустите программу установки Microsoft Exchange

Переключение служб IIS в 64-разрядный режим

1.  Откройте окно командной строки.

2.  Введите следующую команду:
    
    **cscript c:\\inetpub\\adminscripts\\adsutil.vbs SET /w3svc/AppPools/Enable32BitAppOnWin64 False**

3.  Нажмите клавишу ВВОД.

