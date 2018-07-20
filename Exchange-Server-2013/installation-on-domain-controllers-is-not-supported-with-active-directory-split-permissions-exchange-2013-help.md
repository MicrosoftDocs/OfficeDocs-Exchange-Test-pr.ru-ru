---
title: 'Установка на контроллерах домена не поддерживается с разделением разрешений Active Directory: Exchange 2013 Help'
TOCTitle: Установка на контроллерах домена не поддерживается с разделением разрешений Active Directory
ms:assetid: 977e3758-5e09-40a2-80c1-fe344b1d8a2a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.installondcinadsplitpermissionmode(v=EXCHG.150)
ms:contentKeyID: 50488711
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Установка на контроллерах домена не поддерживается с разделением разрешений Active Directory

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2012-11-12_

Программа установки Microsoft Exchange Server 2013 определила, что вы запустили программу установки на контроллере домена Active Directory и выполняется одно из следующих условий:

  - В организации Exchange уже настроена служба каталогов Active Directory с разделением разрешений.

  - Вы выбрали разделение разрешений Active Directory в программе установки Exchange 2013.

Установка Exchange 2013 на контроллерах домена не поддерживается, если для организации Exchange настроено разделение разрешений Active Directory.

Если вы хотите установить Exchange 2013 на контроллере домена, необходимо настроить в организации Exchange разделение разрешений с помощью управления доступом на основе ролей или общие разрешения.

> [!IMPORTANT]  
> Мы не рекомендуем устанавливать Exchange 2013 на контроллерах домена Active Directory. Дополнительные сведения см. в разделе <a href="installing-exchange-on-a-domain-controller-is-not-recommended-exchange-2013-help.md">Не рекомендуется устанавливать Exchange на контроллере домена</a>.


Если вы хотите по-прежнему использовать разделение разрешений Active Directory, вам следует установить Exchange 2013 на сервере-участнике.

Дополнительные сведения о разделении разрешений и общих разрешениях в Exchange 2013 приведены в следующих разделах:

[Общие сведения о разделенных разрешениях](understanding-split-permissions-exchange-2013-help.md)

[Настройка разделенных разрешений в Exchange 2013](configure-exchange-2013-for-split-permissions-exchange-2013-help.md)

[Настройка общих разрешений в Exchange 2013](configure-exchange-2013-for-shared-permissions-exchange-2013-help.md)

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

