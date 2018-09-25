---
title: 'Настройка проверки подлинности OAuth в SharePoint 2013 и Lync 2013'
TOCTitle: Настройка проверки подлинности OAuth в SharePoint 2013 и Lync 2013
ms:assetid: ca3c78a3-80cc-4df2-859f-0106bbd57a07
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ649094(v=EXCHG.150)
ms:contentKeyID: 50489214
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка проверки подлинности OAuth в SharePoint 2013 и Lync 2013

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2014-03-03_

Exchange Server 2013 позволяет другим приложениям использовать OAuth, чтобы проверять подлинность для Exchange. Приложения должны быть настроены как партнер приложений в Exchange 2013.

В Exchange 2013 конфигурация OAuth с партнерскими приложениями, такими как SharePoint 2013 и Lync Server 2013, поддерживаться только посредством использования сценария `Configure-EnterpriseApplication.ps1`. Автоматизируя задачу, сценарий упрощает настройку проверки подлинности с партнерскими приложениями и уменьшает количество ошибок настройки. Он позволяет выполнять следующие задачи:

1.  Настройка партнерского приложения предприятия, которое самостоятельно выпускает маркеры OAuth для успешной проверки подлинности на сервере Exchange.

2.  Назначение ролей управления доступом на основе ролей (RBAC) партнерскому приложению для его авторизации на вызов определенных API веб-служб Exchange.

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 5 минут.

  - Партнерское приложение должно опубликовать для Exchange 2013 документ метаданных авторизации, чтобы установить непосредственное доверие этому приложение и принимать запросы проверки подлинности.

  - В приведенных в данном разделе примерах используется следующее расположение каталога `\Scripts` по умолчанию: `C:\Program Files\Microsoft\Exchange Server\V15\Scripts`.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Партнерские приложения — конфигурация» в разделе [Разрешения на общий доступ и совместную работу](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Настройка проверки подлинности OAuth с партнерским приложением

В этой процедуре используется сценарий `Configure-EntepririseApplication.ps1` для настройки проверки подлинности OAuth с партнерскими приложениями. Доступ к ресурсам зависит от разрешений, назначенных партнерскому приложению или пользователю, которого оно олицетворяет, с помощью RBAC.

После настройки проверки подлинности OAuth из Exchange партнерское приложение может использовать ресурсы Exchange 2013. Если серверу Exchange 2013 также нужно получать доступ к ресурсам, предлагаемым партнерским приложением, необходимо также настроить проверку подлинности OAuth в партнерском приложении.

В этом примере настраивается проверка подлинности OAuth для SharePoint 2013.
```powershell
    Cd C:\Program Files\Microsoft\Exchange Server\V15\Scripts
    Configure-EnterprisePartnerApplication.ps1 -AuthMetaDataUrl https://sharepoint.contoso.com/_layouts/15/metadata/json/1 -ApplicationType SharePoint
```
В этом примере настраивается проверка подлинности OAuth для Lync Server 2013.
```powershell
    Cd C:\Program Files\Microsoft\Exchange Server\V15\Scripts
    Configure-EnterprisePartnerApplication.ps1 -AuthMetaDataUrl https://lync.contoso.com/metadata/json/1 -ApplicationType Lync
```
## Как проверить, что все получилось?

Чтобы подтвердить успешную настройку партнерского приложения предприятия для проверки подлинности на сервере Exchange 2013, в командной консоли запустите командлет [Get-PartnerApplication](https://technet.microsoft.com/ru-ru/library/jj218721\(v=exchg.150\)), чтобы получить конфигурацию. Можно также запустить командлет [Test-OAuthConnectivity](https://technet.microsoft.com/ru-ru/library/jj218623\(v=exchg.150\)), чтобы проверить подключение OAuth к партнерскому приложению для пользователя.

## Дополнительные сведения

  - В гибридных развертываниях можно использовать проверку подлинности OAuth между локальной организацией Exchange 2013 и организацией Exchange Online. Дополнительные сведения см. в разделе [Использование проверки подлинности OAuth для поддержки обнаружения электронных данных в гибридном развертывании Exchange](using-oauth-authentication-to-support-ediscovery-in-an-exchange-hybrid-deployment-exchange-2013-help.md).

  - В локальных развертываниях можно настроить проверку подлинности "сервер-сервер" между Exchange 2013 и SharePoint 2013, чтобы администраторы и ответственные за обеспечение соответствия требованиям могли использовать Центр обнаружения электронных данных в SharePoint 2013 для поиска почтовых ящиков Exchange 2013. Дополнительные сведения см. в разделе [Настройка Exchange для центра обнаружения электронных данных SharePoint](configure-exchange-for-sharepoint-ediscovery-center-exchange-2013-help.md).

