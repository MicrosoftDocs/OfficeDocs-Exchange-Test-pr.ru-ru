---
title: 'Создание правила защиты Outlook: Exchange 2013 Help'
TOCTitle: Создание правила защиты Outlook
ms:assetid: da64750d-faaf-44de-ad8c-888eba7fbdbf
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638196(v=EXCHG.150)
ms:contentKeyID: 50489187
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Создание правила защиты Outlook

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2016-12-09_

Правила защиты Microsoft Outlook позволяют защитить сообщения с помощью управления правами на доступ к данным, применяя шаблон служб управления правами Active Directory (AD RMS) Active Directory перед отправкой сообщений в Outlook 2010.

Дополнительные сведения об управленческих задачах, связанных с IRM, см. в разделе [Сведения о процедуры управления правами](information-rights-management-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время выполнения: 1 минута.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Защита прав» в разделе [Политика обмена сообщениями и разрешения для соответствия требованиям](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Необходим сервер, на котором запущена [Служба управления правами Active Directory](https://technet.microsoft.com/ru-ru/library/hh831364.aspx), развернутый в том же лесу Active Directory, что и сервер, на котором запущена служба Microsoft Exchange Server 2013.

  - Если настроить правила защиты Outlook для защиты сообщений с помощью управления правами на доступ к данным, рекомендуется включить расшифровку транспорта, чтобы позволить агентам транспорта, включая агент правил транспорта, осуществлять расшифровку сообщения и доступ к нему. При использовании ведения журнала также рекомендуется включить расшифровку отчета по журналу, чтобы позволить агенту ведения журнала сохранить незашифрованную копию сообщения в отчете по журналу. Дополнительные сведения см. в разделе [Расшифровка отчета журнала](journal-report-decryption-exchange-2013-help.md).

  - Вы можете использовать центр администрирования Exchange (EAC) для создания правил защиты Outlook. Необходимо использовать командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Использование командной консоли для создания правила защиты Outlook

В этом примере создается правило защиты Outlook Project Contoso. Это правило защищает сообщения, отправленные в группу рассылки ContosoPMs с помощью шаблона служб управления правами Active Directory «Критические для предприятия».

    New-OutlookProtectionRule -Name "Project Contoso" -SentTo "DL-ContosoPMs@contoso.com" -ApplyRightsProtectionTemplate "Business Critical"

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При использовании предиката <code>SentTo</code> для правила защиты Outlook и указании группы рассылки, защита с помощью службы управления правами на доступ к данным применяется только для сообщений, отправленным группе рассылки в полях &quot;Кому&quot;, &quot;Копия&quot; или &quot;Скрытая копия&quot;. Защита с помощью управления правами на доступ к данным не применяется к сообщениям, адресованным отдельным членам группы рассылки.</td>
</tr>
</tbody>
</table>


Кроме того, можно использовать предикаты `FromDepartment` и `SentToScope` для применения защиты с помощью управления правами на доступ к данным к сообщениям, отправляемым пользователями из заданного отдела или в заданную область (`InOrganization` для внутренних сообщений, `All` для всех получателей).

Дополнительные сведения о синтаксисе и параметрах см. в разделе [New-OutlookProtectionRule](https://technet.microsoft.com/ru-ru/library/dd298182\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться, что новое правило защиты Outlook создано успешно, выполните следующие действия.

  - Выполните командлет [Get-OutlookProtectionRule](https://technet.microsoft.com/ru-ru/library/dd298004\(v=exchg.150\)), чтобы убедиться, что правило создано, и чтобы просмотреть его свойства. Пример получения правила защиты Outlook см. в подразделе [Examples](https://technet.microsoft.com/ru-ru/dd298004\(exchg.150\)#examples) статьи **Get-OutlookProtectionRule**.

  - С помощью приложения Outlook 2010 создайте тестовое сообщение, отвечающее условиям правила, и убедитесь, что правило инициировано для клиента.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Для того, чтобы правило защиты Outlook стало доступным в приложении Outlook, может потребоваться некоторое время.</td>
    </tr>
    </tbody>
    </table>

