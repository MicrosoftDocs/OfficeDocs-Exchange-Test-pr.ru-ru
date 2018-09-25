---
title: 'Настройка Exchange 2013 для центра обнаружения электронных данных SharePoint'
TOCTitle: Настройка Exchange для центра обнаружения электронных данных SharePoint
ms:assetid: 795c1a3b-295c-4ee5-ade9-52cf3fda3f19
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ218665(v=EXCHG.150)
ms:contentKeyID: 50488476
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка Exchange для центра обнаружения электронных данных SharePoint

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Microsoft Exchange Server 2013 включает в себя компоненты для работы с Microsoft SharePoint Server 2013 и Microsoft Lync Server 2013, называемыми *партнерским приложениям*. Чтобы эти приложения могли получить доступ к ресурсам друг друга, необходимо настроить проверку подлинности между серверами.

В этом разделе описывается настройка проверки подлинности между Exchange 2013 и SharePoint 2013, которая позволяет использовать центр обнаружения электронных данных в SharePoint 2013 для поиска содержимого почтовых ящиков в Exchange Server 2013. Для полного использования этой функции необходимо выполнить дополнительные шаги в SharePoint 2013. Дополнительные сведения см. в разделе [Настройка обнаружения электронных данных в SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=257727).

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения задачи: 30 минут

  - Для процедур в этом разделе требуются особые разрешения. См. информацию о разрешениях по каждой процедуре.

  - Установка Exchange 2013 и SharePoint 2013 возможна в различных доменах или лесах. Отношения доверия Windows между лесами Exchange и SharePoint не требуются, поскольку в данном случае доверие между Exchange и SharePoint основано на протоколе OAuth 2.0.

  - Сайт SharePoint 2013 должны быть настроен с использованием протокола SSL.

  - [Управляемый API веб-служб Exchange](https://go.microsoft.com/fwlink/?linkid=257726) необходимо установить на каждом сервере SharePoint 2013. Перезапустите сервер IIS после установки.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Процедура выполнения

## Действие 1. Настройка проверки подлинности между серверами для Exchange 2013 на сервере SharePoint Server 2013

Выполните следующую команду, чтобы указать Exchange 2013 как надежный поставщик маркеров безопасности в SharePoint 2013.
```powershell
    New-SPTrustedSecurityTokenIssuer -Name Exchange -MetadataEndPoint https://<Exchange Server Name or FQDN>/autodiscover/metadata/json/1
```
## Действие 2. Настройка межсерверной проверки подлинности для SharePoint 2013 на сервере Exchange 2013

Выполните этот шаг на сервере Exchange 2013. Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Партнерские приложения – конфигурация" в разделе [Разрешения на общий доступ и совместную работу](sharing-and-collaboration-permissions-exchange-2013-help.md).

Выполните эту команду, чтобы настроить партнерское приложение SharePoint.
```powershell
    cd c:\'Program Files'\Microsoft\'Exchange Server'\V15\Scripts
    .\Configure-EnterprisePartnerApplication.ps1 -AuthMetadataUrl <path to SharePoint AuthMetadataUrl> -ApplicationType SharePoint
```
## Действие 3. Добавление авторизованных пользователей в группу ролей "Управление обнаружением"

Добавьте пользователей, которым необходимо выполнять поиск для обнаружения электронных данных в SharePoint 2013, в группу ролей управления обнаружением в Exchange 2013. Дополнительные сведения см. в разделе [Назначение разрешений обнаружения электронных данных в Exchange](https://docs.microsoft.com/ru-ru/exchange/security-and-compliance/in-place-ediscovery/assign-ediscovery-permissions).

> [!CAUTION]  
> Добавление пользователей в группу ролей управления обнаружением позволяет им использовать поиск обнаружения на месте для поиска по всем почтовым ящикам Exchange 2013 и доступа к потенциально конфиденциальной информации в почтовых ящиках пользователей. По умолчанию это разрешение не назначается пользователям, в том числе участникам группы ролей управления организацией. Обратитесь в юридический отдел или отдел кадров организации перед назначением этого разрешения каким-либо пользователям.

