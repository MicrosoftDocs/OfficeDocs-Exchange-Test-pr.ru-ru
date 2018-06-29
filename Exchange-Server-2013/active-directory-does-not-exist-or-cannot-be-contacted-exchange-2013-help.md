---
title: 'Службы каталогов Active Directory не существует или с ней невозможно связаться: Exchange 2013 Help'
TOCTitle: Службы каталогов Active Directory не существует или с ней невозможно связаться
ms:assetid: 56adb6fe-ecb8-4a7f-b440-89aa401c28b7
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.cannotaccessad(v=EXCHG.150)
ms:contentKeyID: 50488265
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Службы каталогов Active Directory не существует или с ней невозможно связаться

 

_**Применимо к:**Exchange Server_

_**Последнее изменение раздела:**2016-12-09_

Установку Microsoft Exchange Server 2013 не удается продолжить, так как она не может связаться с допустимым сайтом службы каталогов Active Directory. Программа установки требует, чтобы сервер, где устанавливается Exchange, был способен определить контекст именования конфигурации в Active Directory.

Чтобы устранить эту проблему, убедитесь, что учетная запись пользователя, используемая для установки Exchange, является пользователем Active Directory, и затем повторно запустите программу установки. Если это не позволит устранить проблему, для ее дальнейшей диагностики следуйте инструкциям по использованию средств поддержки dcdiag.exe и repadmin.exe, указанным в последующих разделах.

Дополнительные сведения об устранении неполадок, связанных со службой каталогов Active Directory, а также о конфигурации службы каталогов для Exchange см. в следующих статьях:

  - [Подготовка Active Directory и доменов](prepare-active-directory-and-domains-exchange-2013-help.md)

  - [Устранение неполадок доменных служб Active Directory](https://go.microsoft.com/fwlink/p/?linkid=272144)

  - [Настройка устранения неполадок на компьютере](https://go.microsoft.com/fwlink/p/?linkid=272141)

  - [Устранение неполадок репликации Active Directory](https://go.microsoft.com/fwlink/p/?linkid=272142)

  - [Мониторинг и устранение неполадок репликации Active Directory с помощью Repadmin](https://go.microsoft.com/fwlink/p/?linkid=272143)

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Нашли то, что искали? Пожалуйста, уделите немного времени для [отправки отзыва](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) касательно сведений, которые требовалось получить.

