---
title: 'Упрощение URL-адреса Outlook Web App: Exchange 2013 Help'
TOCTitle: Упрощение URL-адреса Outlook Web App
ms:assetid: 5fb6a873-f3cf-4f82-87d1-2ff6e47a0080
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa998359(v=EXCHG.150)
ms:contentKeyID: 54652120
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Упрощение URL-адреса Outlook Web App

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-07-16_

**Сводка**. Следуя указаниям в этой статье, вы можете упростить URL-адрес, используемый в организации для доступа к OWA в Exchange 2013.

Вы можете упростить URL-адрес МайкрософтOutlook Web App, который используется для доступа к почтовому ящику Exchange Server 2013.

Чтобы упростить доступ пользователей к Outlook Web App, веб-страницу Outlook Web App, которая обычно является веб-сайтом по умолчанию в службах IIS, можно настроить на автоматическое перенаправление пользователей на протокол https. Действия, описанные в разделе "Использование диспетчера IIS для упрощения URL-адреса приложения Outlook Web App и принудительного перенаправления на протокол SSL", перенаправляют запрос адреса http://*сервер* на адрес https://*сервер*/owa. Чтобы обеспечить безопасность данных, передаваемых между клиентом и сервером, необходимо при установке веб-сайта по умолчанию настроить его для использования протокола SSL.

Если в операционной системе Windows Server 2008 настроено перенаправление для каталога верхнего уровня, параметры перенаправления распространяются на каталоги нижнего уровня. Например, если на веб-сайте по умолчанию настроено перенаправление на виртуальный каталог /owa, настроенные параметры также будут отображаться на странице перенаправления HTTP во всех виртуальных каталогах, таких как /Autodiscover, /Exchange и /Public. Поэтому параметры перенаправления во всех виртуальных каталогах, за исключением того каталога, для которого они были настроены, необходимо удалить.

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 10 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Пункт "Диспетчер IIS" в подразделе "Разрешения Outlook Web App" в статье [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..</td>
</tr>
</tbody>
</table>


## Этап 1. Использование диспетчера IIS для упрощения URL-адреса Outlook Web App и принудительного перенаправления на протокол SSL

1.  Запустите диспетчер IIS.

2.  Разверните сайте локального компьютера, затем разверните сайте **сайты** и выберите элемент **веб-сайт по умолчанию**.

3.  В нижней части панели "Домашняя страница веб-сайта по умолчанию" выберите параметр **Просмотр возможностей**.

4.  В разделе **IIS** дважды щелкните элемент **Перенаправление HTTP**.

5.  Установите флажок **Запросы на перенаправление по следующему назначению**.

6.  Введите абсолютный путь к виртуальному каталогу /owa. Например, введите **https://mail.contoso.com/owa**.

7.  В разделе **Поведение при перенаправлении** установите флажок **Запросы на перенапр. содержимого этого каталога (без подкаталогов)**.

8.  В списке **Код состояния** щелкните **Найдено (302)**.

9.  В области действий нажмите кнопку **Применить**.

10. Выберите **Веб-сайт по умолчанию**.

11. В области "Домашняя страница веб-сайта по умолчанию" дважды нажмите **Параметры SSL**.

12. В разделе **Параметры SSL** снимите флажок **Требовать SSL**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если флажок <strong>Требовать SSL</strong> не снят, пользователи не будут перенаправляться при вводе незащищенного URL-адреса. Вместо этого они будут получать ошибку отказа в доступе.</td>
    </tr>
    </tbody>
    </table>


## Этап 2. Удаление перенаправления из виртуальных каталогов

Чтобы удалить параметры перенаправления для виртуального каталога, выполните следующие шаги.

1.  Откройте окно командной строки.

2.  Перейдите в \<*каталог Windows*\>\\System32\\Inetsrv.

3.  Выполните следующие команды:
    
    1.  `appcmd set config "Default Web Site/autodiscover" /section:httpredirect /enabled:false -commit:apphost`
    
    2.  `appcmd set config "Default Web Site/ecp" /section:httpredirect /enabled:false -commit:apphost`
    
    3.  `appcmd set config "Default Web Site/ews" /section:httpredirect /enabled:false -commit:apphost`
    
    4.  `appcmd set config "Default Web Site/owa" /section:httpredirect /enabled:false -commit:apphost`
    
    5.  `appcmd set config "Default Web Site/oab" /section:httpredirect /enabled:false -commit:apphost`
    
    6.  `appcmd set config "Default Web Site/powershell" /section:httpredirect /enabled:false -commit:apphost`
    
    7.  `appcmd set config "Default Web Site/rpc" /section:httpredirect /enabled:false -commit:apphost`
    
    8.  `appcmd set config "Default Web Site/rpcwithcert" /section:httpredirect /enabled:false -commit:apphost`
    
    9.  `appcmd set config "Default Web Site/Microsoft-Server-ActiveSync" /section:httpredirect /enabled:false -commit:apphost`

4.  Чтобы завершить процедуру, выполните команду `iisreset/noforce`.

При настройке перенаправления из каталога верхнего уровня файл web.config может быть создан в папке \<*диск*\>\\Program Files\\Microsoft\\Exchange Server\\\<*версия*\>\\ClientAccess\\oab. Если это произошло и впоследствии перенаправление удаляется, приложение Outlook может зависать, когда пользователи выбирают команду **Отправка и получение**. Чтобы избежать такой ситуации после удаления перенаправления, удалите файл web.config из папки \<*диск*\>\\Program Files\\Microsoft\\Exchange Server\\\<*версия*\>\\ClientAccess\\oab.

## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно упростили URL-адрес Outlook Web App и перенаправили его на SSL-соединение, выполните указанные ниже действия.

1.  Откройте браузер и введите новый URL-адрес для Outlook Web App в формате http://\<*URL-адрес*\>.

2.  Должно произойти перенаправление на страницу входа в Outlook Web App по SSL-соединению.

