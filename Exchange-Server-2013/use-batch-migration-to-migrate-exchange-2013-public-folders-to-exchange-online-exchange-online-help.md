﻿---
title: 'Использование пакетной миграции для переноса общедоступных папок Exchange 2013 в Exchange Online: Exchange 2013 Help'
TOCTitle: Использование пакетной миграции для переноса общедоступных папок Exchange 2013 в Exchange Online
ms:assetid: 25a5234c-dd2c-487b-8541-3655fbeb030a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Mt798260(v=EXCHG.150)
ms:contentKeyID: 74432750
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Использование пакетной миграции для переноса общедоступных папок Exchange 2013 в Exchange Online

 

_**Последнее изменение раздела:**2018-03-26_

**Сводка.** В этой статье описано, как переместить современные общедоступные папки из Exchange 2013 в Office 365.

Миграция общедоступных папок Exchange 2013 в Exchange Online требуется Exchange Server 2013 CU15 или более поздней версии в локальной среде.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если в организации есть общедоступные папки Exchange 2013 и Exchange 2016 и вы хотите переместить их все в Exchange Online, откройте <a href="https://go.microsoft.com/fwlink/p/?linkid=845314">версию этой статьи для Exchange 2016</a>, где описано планирование и выполнение миграции. На серверах Exchange 2013 должен быть установлен накопительный пакет обновления 15 (CU15) или более поздний.</td>
</tr>
</tbody>
</table>


## Что нужно знать перед началом работы

  - При обновлении до Exchange Server 2013 CU15 или более поздней версии также необходимо подготовить Active Directory, иначе перенести общедоступные папки не удастся. Это позволит убедиться, что все необходимые командлеты и параметры PowerShell доступны для подготовки к миграции и ее выполнения. Дополнительные сведения см. в статье [Подготовка Active Directory и доменов](prepare-active-directory-and-domains-exchange-2013-help.md).

  - В Exchange Online вам необходимо быть членом группы ролей Organization Management. Эта группа ролей отличается от разрешений, которые назначаются при подписке на Office 365 или Exchange Online. Сведения о том, как включить группу ролей Organization Management, см. в статье [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

  - В Exchange Server 2013 вам необходимо быть членом группы ролей RBAC Organization Management или Server Management. Дополнительные сведения см. в статье [Добавление участников в группу ролей](https://go.microsoft.com/fwlink/?linkid=299212).

  - Если в организации есть общедоступные папки, размер которых превышает 25 ГБ, перед началом миграции рекомендуем удалить из них содержимое, чтобы сделать их меньше, или разделить их на несколько меньших общедоступных папок. Обратите внимание, что указанное здесь ограничение в 25 ГБ применяется только к общедоступной папке, а не ее дочерним папкам или подпапкам. Если ни один их этих вариантов невозможен, рекомендуем не перемещать общедоступные папки в Exchange Online. Дополнительные сведения см. в статье [Ограничения Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=391188).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если текущие квоты на хранение общедоступных папок в Exchange Online составляют менее 25 ГБ, вы можете увеличить их с помощью <a href="https://go.microsoft.com/fwlink/p/?linkid=844062">командлета Set-OrganizationConfig</a> и параметров DefaultPublicFolderIssueWarningQuota и DefaultPublicFolderProhibitPostQuota.</td>
    </tr>
    </tbody>
    </table>


  - В Office 365 и Exchange Online можно создать до 1000 почтовых ящиков общедоступных папок.

  - Если вы планируете перенести пользователей в Office 365, это необходимо сделать до переноса общедоступных папок. Дополнительные сведения см. в статье [Способы переноса нескольких записей электронной почты в Office 365](https://go.microsoft.com/fwlink/p/?linkid=842798).

  - Прокси-сервер MRS должен быть включен по крайней мере на одном сервере Exchange, на котором также размещаются почтовые ящики общедоступных папок. Дополнительные сведения см. в статье [Включение конечной точки прокси-сервера MRS для удаленных перемещений](enable-the-mrs-proxy-endpoint-for-remote-moves-exchange-2013-help.md).

  - Для выполнения процедур миграции, описанных в этой статье, нельзя использовать Центр администрирования Exchange (EAC). Необходимо использовать командную консоль Exchange на серверах Exchange 2013. В Exchange Online необходимо использовать Exchange Online PowerShell. Дополнительные сведения см. в статье [Подключение к Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=842801).

  - Поддерживается миграция удаленных элементов и папок из Exchange 2013 в Exchange Online. Перед началом миграции рекомендуется проверить все удаленные папки и элементы и навсегда удалить все, что вам не понадобится в Exchange Online. Обратите внимание, что после такого удаления элемент невозможно восстановить.
    
    Вы можете использовать следующие команды для вывода списка удаленных общедоступных папок в корзине Exchange (в локальной среде Exchange):
    
        Get-PublicFolder \NON_IPM_SUBTREE\DUMPSTER_ROOT -Recurse | ?{$_.FolderClass -ne "$null"} | ft name,foldersize
    
    Чтобы навсегда удалить определенную папку, используйте следующую команду (в этом примере используется папка Calendar2):
    
        Get-PublicFolder \NON_IPM_SUBTREE\DUMPSTER_ROOT -Recurse | ?{$_.FolderClass -ne "$null" -and $_.Name -eq "Calendar2"} | Remove-PublicFolder

  - Прежде чем начать, прочитайте эту статью целиком. На некоторых этапах предусмотрено время простоя, когда общедоступные папки будут заблокированы.

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


## Шаг 1. Скачивание сценариев миграции

1.  Скачайте все сценарии и вспомогательные файлы со страницы, содержащей [сценарии миграции общедоступных папок Exchange 2013 или Exchange 2016](https://go.microsoft.com/fwlink/p/?linkid=844893).

2.  Сохраните эти сценарии на локальном компьютере, с которого вы собираетесь запускать оболочку PowerShell. (Например, в папку C:\\PFScripts). Убедитесь, что все сценарии сохранены в одном и том же месте.

Описание сценариев и файлов:

  - `Sync-ModernMailPublicFolders.ps1`. Этот сценарий синхронизирует поддерживающие почту объекты общедоступных папок между локальной средой Exchange и Office 365. Этот сценарий нужно выполнить на сервере Exchange 2013.

  - `SyncModernMailPublicFolders.strings.psd1`. Этот вспомогательный файл используется сценарием Sync-ModernMailPublicFolders.ps1, их необходимо скачать в одну папку.

  - `Export-ModernPublicFolderStatistics.ps1`. Этот сценарий создает файл сопоставления имен папок с размерами папок и размерами удаленных элементов. Этот сценарий нужно выполнить на сервере Exchange 2013.

  - `Export-ModernPublicFolderStatistics.strings.psd1`. Этот вспомогательный файл используется сценарием Export-ModernPublicFolderStatistics.ps1, поэтому их необходимо скачать в одну папку.

  - `ModernPublicFolderToMailboxMapGenerator.ps1`. Этот сценарий создает файл сопоставления общедоступных папок с почтовыми ящиками, используя выходные данные сценария Export-ModernPublicFolderStatistics.ps1. Этот сценарий нужно выполнить на сервере Exchange 2013.

  - `ModernPublicFolderToMailboxMapGenerator.strings.psd1`. Этот вспомогательный файл используется сценарием ModernPublicFolderToMailboxMapGenerator.ps1, поэтому их необходимо скачать в одну папку.

  - `SetMailPublicFolderExternalAddress.ps1`. Этот сценарий обновляет метку `ExternalEmailAddress` поддерживающих почту общедоступных папок в локальной среде, чтобы после миграции отправляемые в них сообщения перенаправлялись в Exchange Online. Этот сценарий нужно выполнить на сервере Exchange 2013.

  - `SetMailPublicFolderExternalAddress.strings.psd1`. Этот вспомогательный файл используется сценарием SetMailPublicFolderExternalAddress.ps1, поэтому их необходимо скачать в одну папку.

## Этап 2. Подготовка к миграции

Перед переносом общедоступных папок выполните все необходимые действия, описанные в разделах ниже.

**Общие предварительные условия**

Для успешной миграции сделайте следующее:

  - Убедитесь, что в Active Directory нет потерянных почтовых объектов общедоступной папки, то есть объектов без соответствующих им объектов Exchange.

  - Убедитесь, что адреса электронной почты SMTP, настроенные для общедоступных папок в Active Directory, совпадают с адресами электронной почты SMTP в объектах Exchange.

  - Убедитесь, что в Active Directory нет повторяющихся объектов общедоступной папки, чтобы два (или больше) объекта Active Directory не указывали на одну общедоступную папку, поддерживающую почту.

**Необходимые действия в локальной серверной среде Exchange 2013**

В командной консоли Exchange (локальная среда) сделайте следующее:

1.  Кэши DNS в Интернете направят сообщения в поддерживающие почту общедоступные папки в Exchange Online спустя некоторое время после миграции. Чтобы перенесенные общедоступные папки, поддерживающие почту, получали сообщения в течение этого переходного периода, создайте обслуживаемый домен с известным именем. Для этого выполните приведенную ниже команду в локальной среде Exchange. В этом примере `target domain` — это ваш домен Office 365 или Exchange Online, для которого мастер гибридной конфигурации уже настроил соединитель отправки.
    
        New-AcceptedDomain -Name PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99 -DomainName <target domain> -DomainType InternalRelay
    
    **Пример**:
    
        New-AcceptedDomain -Name PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99 -DomainName "contoso.mail.onmicrosoft.com" -DomainType InternalRelay
    
    Если в локальной среде уже есть обслуживаемый домен, измените его имя на `PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99` и оставьте остальные атрибуты без изменений.
    
    Чтобы проверить, есть ли в локальной среде обслуживаемый домен:
    
        Get-AcceptedDomain | Where { $_.DomainName -eq "<target domain>" }
    
    Чтобы переименовать обслуживаемый домен на `PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99`, выполните следующую команду:
    
        Get-AcceptedDomain | Where { $_.DomainName -eq "<target domain>" } | Set-AcceptedDomain -Name PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если поддерживающие почту общедоступные папки в Exchange Online должны получать внешние письма из Интернета, необходимо отключить DBEB в Exchange Online и Exchange Online Protection (EOP). Дополнительные сведения см. в статье <a href="https://technet.microsoft.com/ru-ru/library/dn600322(v=exchg.150)">Использование пограничной блокировки на основе каталогов для отклонения сообщений, отправляемых недопустимым получателям</a>.</td>
    </tr>
    </tbody>
    </table>


2.  Если имя общедоступной папки содержит обратную **\\** или прямую **/** косую черту, папка может не перенестись в указанный почтовый ящик во время миграции. Перед миграцией переименуйте эти папки, чтобы удалить эти знаки.
    
    1.  Чтобы найти общедоступные папки с обратной косой чертой в имени, выполните следующую команду:
        
            Get-PublicFolder -Recurse -ResultSize Unlimited | Where {$_.Name -like "*\*" -or $_.Name -like "*/*"} | Format-List Name, Identity, EntryId
    
    2.  Если эта команда возвращает сведения об общедоступных папках, переименуйте их с помощью следующей команды:
        
            Set-PublicFolder -Identity "<public folder EntryId>" -Name "<new public folder name>"

3.  Выполните действия ниже, чтобы убедиться, что в организации нет данных о предыдущей успешной миграции. В противном случае следует установить значение `$false`.
    
    Прежде чем изменять значения, убедитесь, что предыдущую миграцию можно не учитывать, чтобы случайно не выполнить вторую миграцию.
    
    1.  Выполните следующую команду, чтобы проверить наличие предыдущих миграций и их состояния:
        
            Get-OrganizationConfig | Format-List PublicFoldersLockedforMigration, PublicFolderMigrationComplete, PublicFolderMailboxesLockedForNewConnections, PublicFolderMailboxesMigrationComplete
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Если любой из параметров <code>PublicFoldersLockedforMigration</code> или <code>PublicFolderMigrationComplete</code> имеет значение <code>$true</code>, это означает, что вы уже переносили общедоступные папки из прежней версии. Прежде чем переходить к шагу 3b, убедитесь, что все базы данных общедоступных папок из прежней версии списаны.</td>
        </tr>
        </tbody>
        </table>
    
    2.  Если любой из перечисленных выше параметров возвращается со значением `$true`, выполните следующую команду, чтобы присвоить ему значение `$false`:
        
            Set-OrganizationConfig -PublicFoldersLockedforMigration:$false -PublicFolderMigrationComplete:$false -PublicFolderMailboxesLockedForNewConnections:$false -PublicFolderMailboxesMigrationComplete:$false

4.  Чтобы вы могли проверить успешность миграции после ее завершения, рекомендуем выполнить приведенные ниже команды на всех соответствующих серверах Exchange 2013. Они сделают моментальные снимки текущего развертывания общедоступных папок, которые позднее можно будет сравнить с перенесенными общедоступными папками.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>В зависимости от размера организации Exchange это может занять некоторое время.</td>
    </tr>
    </tbody>
    </table>
    
      - Выполните следующую команду, чтобы сделать моментальный снимок начальной структуры исходных папок.
        
            Get-PublicFolder -Recurse -ResultSize Unlimited | Export-CliXML OnPrem_PFStructure.xml
    
      - Выполните следующую команду, чтобы сделать моментальный снимок статистики общедоступных папок, такой как число элементов, размер и владелец.
        
            Get-PublicFolderStatistics -ResultSize Unlimited | Export-CliXML OnPrem_PFStatistics.xml
    
      - Выполните команду ниже, чтобы сделать моментальный снимок разрешений общедоступных папок.
        
            Get-PublicFolder -Recurse -ResultSize Unlimited | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML OnPrem_PFPerms.xml
    
      - Выполните следующую команду, чтобы сделать моментальный снимок общедоступных папок, поддерживающих почту:
        
            Get-MailPublicFolder -ResultSize Unlimited | Export-CliXML OnPrem_MEPF.xml
    
      - Сохраните файлы, созданные предыдущими командами, в надежном месте, чтобы выполнить сравнение в конце миграции.

5.  Если вы используете Microsoft Azure Active Directory подключиться (Azure AD подключение) синхронизация папки локальной с Azure Active Directory, необходимо выполнить следующие действия (Если вы не используете Azure AD подключение, можно пропустить этот этап):
    
    1.  На локальный компьютер откройте Microsoft Azure Active Directory подключение и затем выберите **Настройка**.
    
    2.  На экране **Дополнительные задачи** выберите **Настройка параметров синхронизации** и нажмите кнопку **Далее**.
    
    3.  На экране **подключение к Azure AD** введите соответствующие данные и нажмите кнопку **Далее**. После подключения, снова нажмите кнопку **Далее** до на экране **Дополнительных компонентов** .
    
    4.  Убедитесь в том, что **Общедоступных папок почты Exchange** не выбран. Если он не установлен, можно продолжить к следующему разделу, *необходимые предварительные действия в Exchange Online*. Если он установлен, снимите этот флажок и нажмите кнопку **Далее**.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Если <strong>Общедоступных папок почты Exchange</strong> не отображается как вариант на экране <strong>Дополнительных компонентов</strong>, следует выйти из Microsoft Azure Active Directory подключение и перейти к следующему разделу, <em>необходимые предварительные действия в Exchange Online</em>.</td>
        </tr>
        </tbody>
        </table>
    
    5.  После очистки выбора **Общедоступных папок почты Exchange**, оставьте нажмите кнопку **Далее**, пока не будете на экране **все готово к настройке** и нажмите кнопку **настроить**.

**Необходимые действия в Exchange Online**

В Exchange Online PowerShell сделайте следующее:

1.  Убедитесь, что отсутствуют запросы на перенос общедоступных папок. Если они есть, очистите их, иначе выполнить ваш запрос не удастся. Это необходимо, только если вы считаете, что в конвейере уже есть запрос на миграцию (который не удалось выполнить или который вы хотите прервать).
    
    Существующий запрос на миграцию может относиться к одному из двух типов: пакетной миграции или последовательной миграции. Ниже указаны команды для обнаружения и удаления запросов обоих типов.
    
    В следующем примере показано, как найти существующие запросы на последовательную миграцию:
    
        Get-PublicFolderMigrationRequest | Get-PublicFolderMigrationRequestStatistics 
    
    В следующем примере показано, как удалить существующие запросы на последовательную миграцию общедоступных папок:
    
        Get-PublicFolderMigrationRequest | Remove-PublicFolderMigrationRequest
    
    В следующем примере показано, как найти существующие запросы на пакетную миграцию:
    
        Get-MigrationBatch | ?{$_.MigrationType.ToString() -eq "PublicFolder"}
    
    В следующем примере показано, как удалить существующие запросы на пакетную миграцию общедоступных папок:
    
        Remove-MigrationBatch <name of migration batch> -Confirm:$false

2.  Для клиента Office 365 должна быть включена функция миграции **PAW**. Вы можете проверить это, выполнив следующую команду в Exchange Online PowerShell:
    
        Get-MigrationConfig
    
    Если в разделе **Features** есть **PAW**, эта функция включена, и можно переходить к следующему шагу.
    
    Если функция PAW еще не включена для вашего клиента, это может быть связано с тем, что у вас уже есть пакеты миграции (общедоступных папок или пользователей). Эти пакеты могут быть в любом состоянии, в том числе "Завершено". Завершите обработку и удалите все пакеты миграции. Результат команды `Get-MigrationBatch` должен быть пустым. После удаления всех существующих пакетов функция PAW должна включиться автоматически. Обратите внимание, что изменение может вступить в силу в `Get-MigrationConfig` не сразу, но это нормально. Вы можете продолжить создавать пакеты миграции пользователей после этого шага.

3.  Убедитесь, что в Exchange Online нет общедоступных папок или почтовых ящиков общедоступных папок. Если вы обнаружите общедоступные папки в Exchange Online, выполнив указанные ниже действия, прежде чем удалять их, важно определить, почему они там находятся и кто в организации запустил иерархию общедоступных папок.
    
    1.  Чтобы проверить, имеются ли какие-либо почтовые ящики общедоступных папок, в оболочке Office 365 или Exchange Online PowerShell запустите следующую команду.
        
            Get-Mailbox -PublicFolder
    
    2.  Если команда не возвращает почтовые ящики общедоступных папок, перейдите к шагу 3 Создание CSV-файлов. В противном случае выполните следующую команду, чтобы проверить наличие общедоступных папок:
        
            Get-PublicFolder -Recurse
    
    3.  Если в Office 365 или Exchange Online есть общедоступные папки, выполните указанную ниже команду PowerShell, чтобы удалить их (после того как убедитесь, что они не нужны). Убедитесь, что вы сохранили всю нужную информацию, потому что при удалении общедоступных папок она будет навсегда потеряна.
        
            Get-MailPublicFolder -ResultSize Unlimited | where {$_.EntryId -ne $null}| Disable-MailPublicFolder -Confirm:$false 
            Get-PublicFolder -GetChildren \ -ResultSize Unlimited | Remove-PublicFolder -Recurse -Confirm:$false
    
    4.  После удаления общедоступных папок выполните следующие команды, чтобы удалить все почтовые ящики общедоступных папок:
        
            $hierarchyMailboxGuid = $(Get-OrganizationConfig).RootPublicFolderMailbox.HierarchyMailboxGuid
            Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -ne $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
            Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -eq $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
            Get-Mailbox -PublicFolder -SoftDeletedMailbox | Remove-Mailbox -PublicFolder -PermanentlyDelete:$true 

## Шаг 3. Создание CSV-файлов

Используйте скачанные сценарии, чтобы создать файлы CSV, которые будут использоваться в процессе миграции.

1.  В командной консоли Exchange (локальная среда) выполните сценарий `Export-ModernPublicFolderStatistics.ps1`, чтобы создать файл сопоставления имен папок с размерами папок. Для запуска этого сценария необходимы права администратора. Итоговый файл будет содержать три столбца: **FolderName**, **FolderSize** и **DeletedItemSize**. Значения столбцов **FolderSize** и **DeletedItemSize** будут указаны в байтах. Например, **\\PublicFolder01,10240, 100** означает, что общедоступная папка в корне иерархии PublicFolder01 имеет размер 10240 байт или 10,240 МБ, и в ней 100 байтов элементов для восстановления.
    
        .\Export-ModernPublicFolderStatistics.ps1 <Folder-to-size map path>
    
    **Пример**:
    
        .\Export-ModernPublicFolderStatistics.ps1 stats.csv

2.  Выполните сценарий `ModernPublicFolderToMailboxMapGenerator.ps1`, чтобы создать CSV-файл сопоставления исходных общедоступных папок с почтовыми ящиками общедоступных папок на целевом сервере Exchange Online. Этот файл используется для вычисления правильного количества почтовых ящиков общедоступных папок в Exchange Online.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Файл, созданный <code>ModernPublicFolderToMailboxMapGenerator.ps1</code> не будет содержать имя каждого общих папок в организации. Он содержит ссылки на родительских папок увеличенное деревьями папки или имена папок какие сами значительно большие. Можно представить этот файл в файл «исключение» используются убедитесь, что определенные деревьями папки и размер папки помещаются в соответствующей общей папки почтыполя. Это обычное каждые одного из ваших общедоступных папок в этом файле, не видят. Дочерние папки все папки, перечисленные в этом файле сопоставления также перемещаются в же почтового ящика общедоступных папок в родительской папки (если только явным образом упомянутые на еще одну строку в файле сопоставления, который направляет их в почтовый ящик различных общей папки).</td>
    </tr>
    </tbody>
    </table>
    
        .\ModernPublicFolderToMailboxMapGenerator.ps1 <Maximum mailbox size in bytes><Maximum mailbox recoverable item size in bytes><Folder-to-size map path><Folder-to-mailbox map path>
    
      - `Maximum mailbox size in bytes`— это максимальный объем данных, который вы хотите перенести в один почтовый ящик общедоступных папок в Exchange Online. В настоящее время максимальный размер этого поля составляет 50 ГБ, но мы рекомендуем использовать меньший размер, например 50 % от максимального, чтобы иметь место для расширения.
    
      - `Maximum mailbox recoverable items size in bytes` — это квота элементов для восстановления в почтовых ящиках Exchange Online. В настоящее время максимальный размер почтового ящика общедоступных папок в Exchange Online составляет 50 ГБ. Рекомендуем установить для параметра ` RecoverableItemsQuota` значение 15 ГБ или меньше.
    
      - `Folder-to-size map path` — это путь к CSV-файлу, созданному при запуске сценария `Export-ModernPublicFolderStatistics.ps1`.
    
      - `Folder-to-mailbox map path` — это путь к CSV-файлу сопоставления папок с почтовыми ящиками, создаваемый на этом шаге. Если вы укажете только имя файла, он будет создан в текущем каталоге PowerShell на локальном компьютере.

**Пример**:

    .\ModernPublicFolderToMailboxMapGenerator.ps1 -MailboxSize 25GB -MailboxRecoverableItemSize 1GB -ImportFile .\stats.csv -ExportFile map.csv

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Мы не поддерживает перенос общих папок в Exchange Online, если число уникальных общих папок почтовых ящиков в Exchange Online, больше 100.</td>
</tr>
</tbody>
</table>


## Шаг 4. Создание почтовых ящиков общедоступных папок в Exchange Online

В Exchange Online PowerShell создайте целевые почтовые ящики, которые будут содержать перемещенные общедоступные папки.

1.  Выполните приведенный ниже сценарий, чтобы создать целевые почтовые ящики общедоступных папок. Сценарий создаст целевой почтовый ящик для каждого почтового ящика в CSV-файле, созданном на шаге 3 *Создание CSV-файлов* при запуске сценария `ModernPublicFoldertoMailboxMapGenerator.ps1`.
    
        $mappings = Import-Csv <Folder-to-mailbox map path>
        $primaryMailboxName = ($mappings | Where-Object FolderPath -eq "\" ).TargetMailbox
        New-Mailbox -HoldForMigration:$true -PublicFolder -IsExcludedFromServingHierarchy:$false $primaryMailboxName 
        ($mappings | Where-Object TargetMailbox -ne $primaryMailboxName).TargetMailbox | Sort-Object -unique | ForEach-Object { New-Mailbox -PublicFolder -IsExcludedFromServingHierarchy:$false $_ }
    
      - `Folder-to-mailbox map path` — это путь к CSV-файлу сопоставления папок с почтовыми ящиками, созданному сценарием `ModernPublicFoldertoMailboxMapGenerator.ps1` на шаге 3 *Создание CSV-файлов*.

## Шаг 5. Запуск запроса на миграцию

Теперь несколько команд необходимо выполнить в локальной среде Exchange 2013 и в Exchange Online.

1.  С любого из серверов Exchange 2013, на котором размещаются почтовые ящики общедоступных папок, выполните сценарий ниже. Он синхронизирует поддерживающие почту общедоступные папки из локального каталога Active Directory с Exchange Online. Скачайте последнюю версию этого сценария и используйте командную консоль Exchange.
    
        .\Sync-ModernMailPublicFolders.ps1 -Credential (Get-Credential) -CsvSummaryFile:sync_summary.csv
    
      - `Credential` — это имя пользователя и пароль администратора Exchange Online.
    
      - `CsvSummaryFile` — это путь к файлу журнала операций и ошибок синхронизации. Журнал будет в формате CSV.

2.  На сервере Exchange 2013 найдите сервер конечной точки прокси-сервера MRS и запишите его. Эти сведения понадобятся вам для выполнения запроса на миграцию. Сохраните эти сведения для шага 3b ниже.

3.  В Exchange Online PowerShell выполните указанные ниже команды, чтобы передать учетные данные и информацию MRS с предыдущего шага в переменные командлета, которые будут использоваться в запросе на миграцию.
    
    1.  Передайте учетные данные администратора локальной среды Exchange 2013 в переменную `$Source_Credential`. Они необходимы для доступа к локальным серверам Exchange 2013, чтобы скопировать содержимое общедоступных папок в Exchange Online.
        
            $Source_Credential = Get-Credential <source_domain>\<PublicFolder_Administrator_Account>
    
    2.  Передайте сведения о прокси-сервере MRS из среды Exchange 2013, которые вы нашли на шаге 2 выше, в переменную:
        
            $Source_RemoteServer = "<paste the value here>"

4.  В Exchange Online PowerShell выполните следующие команды, чтобы создать конечную точку миграции и запрос на миграцию общедоступных папок:
    
        $PfEndpoint = New-MigrationEndpoint -PublicFolder -Name PublicFolderEndpoint -RemoteServer $Source_RemoteServer -Credentials $Source_Credential
         
        [byte[]]$bytes = Get-Content -Encoding Byte <folder_mapping.csv>
        
        New-MigrationBatch -Name PublicFolderMigration -CSVData $bytes -SourceEndpoint $PfEndpoint.Identity -NotificationEmails <email addresses for migration notifications>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Несколько адресов электронной почты необходимо разделить запятыми.</td>
    </tr>
    </tbody>
    </table>
    
    Где `folder_mapping.csv` — это файл карты, созданный на *Шаг 3: создание CSV-файлов*. Обязательно укажите полный путь к файлу. Если файл сопоставления была перемещена по любой причине, убедитесь, что для использования в новом месте.

5.  Начните миграцию, используя следующую команду в Exchange Online PowerShell:
    
        Start-MigrationBatch PublicFolderMigration

Пакетные миграции необходимо создавать с помощью командлета New-MigrationBatch в Exchange Online PowerShell, но просматривать ход выполнения и управлять им можно в Центре администрирования Exchange или с помощью командлета Get-MigrationBatch. Последний инициирует запрос на миграцию почтовых ящиков для каждого почтового ящика общедоступных папок, вы можете просмотреть состояние этих запросов на странице миграции почтовых ящиков.

Чтобы перейти на страницу миграции почтовых ящиков:

1.  Войдите в Exchange Online и откройте Центр администрирования Exchange.

2.  Выберите **Получатели** \> **Миграции**.

3.  Выберите новый запрос на миграцию и щелкните **Просмотр сведений** в области **Сведения**.

Прежде чем переходить к шагу 6 *Блокировка общедоступных папок на сервере Exchange 2013*, убедитесь, что все данные скопированы и отсутствуют ошибки миграции. Когда вы убедитесь, что пакет перешел в состояние **Синхронизировано**, выполните команды, указанные на шаге 2 *Подготовка к миграции* в разделе **Необходимые действия в локальной среде сервера Exchange 2013**, чтобы сделать моментальный снимок локальных общедоступных папок. После этого можете переходить к следующему шагу. Обратите внимание, что выполнение этих команд может занять некоторое время в зависимости от количества папок.

## Шаг 6. Блокировка общедоступных папок в среде Exchange 2013 для завершения миграции

До этого момента локальные общедоступные папки Exchange 2013 были доступны для пользователей. Для окончательной синхронизации требуется их блокировка. В течение этого времени общедоступные папки будут заблокированы для пользователей, и все сообщения, отправляемые в поддерживающие почту общедоступные папки, будут доставлены только после завершения миграции.

Перед выполнением команды `PublicFolderMailboxesLockedForNewConnections` , как описано ниже, убедитесь в том, что все задания находятся в состоянии **синхронизирован**. Это можно сделать с помощью команды `Get-PublicFolderMailboxMigrationRequest` . Выполните этот шаг только после проверки, что все задания находятся в состоянии **синхронизирован**.

В локальной среде выполните приведенную ниже команду, чтобы заблокировать общедоступные папки Exchange 2013 для завершения миграции.

    Set-OrganizationConfig -PublicFolderMailboxesLockedForNewConnections $true

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если не удается получить доступ к параметр <code>-PublicFolderMailboxesLockedForNewConnections</code> , это может быть вызвано Active Directory не подготовлен во время обновления текущую, как мы сначала создайте выше в <em>что нужно знать, прежде чем приступить к работе?</em> В разделе <a href="prepare-active-directory-and-domains-exchange-2013-help.md">Подготовка Active Directory и доменов</a> для получения дополнительных сведений.<br />
Обратите внимание, что <strong>сначала</strong> нужно перенести всех пользователей, которым необходим доступ к общедоступным папкам.</td>
</tr>
</tbody>
</table>


Если почтовые ящики общедоступных папок организации размещены на нескольких серверах Exchange 2013, вам придется подождать, пока завершится репликация AD. После этого вы сможете убедиться, что всем почтовым ящикам общедоступных папок присвоен флажок `PublicFolderMailboxesLockedForNewConnections` и все изменения, недавно внесенные пользователями в общедоступных папках, распространились по всей организации. Все это может занять несколько часов.

## Шаг 7. Завершение миграции общедоступных папок (требуется отключение общедоступных папок)

Перед выполнением миграции общих папок необходимо убедитесь, что перемещение нет других почтовых ящиков общедоступных папок или перемещение общедоступных папок переход в вашей локальной среды Exchange. Для этого списка любой существующей общей папки с помощью командлетов `Get-MoveRequest` и `Get-PublicFolderMoveRequest` перемещение. При наличии любого перемещений в процессе выполнения или в состоянии **завершения**, удалите их.

Рассмотрим процедуру для завершения миграции общих папок в Exchange Online PowerShell выполните следующую команду:

    Complete-MigrationBatch PublicFolderMigration

При выполнении этой команды Exchange будет выполните окончательный синхронизации между локальной организации Exchange и Exchange Online. В течение этого периода состояние пакета миграции будет изменен **синхронизированоЗавершение работы**, а затем наконец значение **завершено**. При успешном последней синхронизации общих папок в Exchange Online остаются разблокированными.

Обычно для пакета миграции для времени за несколько часов до его изменения состояния из **синхронизировано** для **завершения работы**, в какой точке начнется последней синхронизации.

## Шаг 8. Проверка и разблокировка общедоступных папок в Exchange Online

После миграции выполните указанные ниже действия, чтобы проверить и официально подтвердить, что она завершена. Эти действия позволят проверить иерархию перенесенных общедоступных папок, прежде чем окончательно переходить на общедоступные папки Exchange Online.

1.  В Exchange Online PowerShell сделайте один из перенесенных почтовых ящиков общедоступных папок основным для нескольких почтовых ящиков пользователей.
    
        Set-Mailbox -Identity <test user> -DefaultPublicFolderMailbox <public folder mailbox identity>
    
    Убедитесь, что у тестовых пользователей есть необходимые разрешения для создания общедоступных папок.

2.  Войдите в Outlook с помощью тестового пользователя описано в предыдущем шаге и выполните следующие тесты общедоступных папок. Обратите внимание на то, что может потребоваться 15-30 минут, чтобы изменения вступили в силу. После Outlook принять во внимание изменения, он может потребоваться перезапустить несколько раз.
    
    1.  Просмотр иерархии.
    
    2.  проверка разрешений;
    
    3.  Создайте несколько общедоступных папок, а затем удалите их.
    
    4.  Поместите содержимое в общедоступную папку и удалите его.
    
    За любой ошибок и определить, что вы готовы не переключитесь в общих папках вашей организации полностью Exchange Online в статье [Откат миграции общедоступных папок с Exchange 2013 до Exchange Online](roll-back-a-public-folder-migration-from-exchange-2013-to-exchange-online-exchange-2013-help.md).

3.  Выполните следующую команду в Exchange Online PowerShell для разблокировки общих папок в Exchange Online. После выполнения команды может занять около 15-30 минут, чтобы изменения вступили в силу. После Outlook становится принять во внимание изменения, может быть предложено пользователям перезапустить программу несколько раз.
    
        Set-OrganizationConfig -RemotePublicFolderMailboxes $Null -PublicFoldersEnabled Local

## Шаг 9: Завершение миграции локальной

Чтобы включить в общие папки с включенной поддержкой почты локальную по электронной почте, выполните следующие действия:

1.  В локальной среде выполните следующий сценарий, чтобы убедиться, что все сообщения, отправляемые в поддерживающие почту общедоступные папки, перенаправляются в Exchange Online. Сценарий обновит метку `ExternalEmailAddress` поддерживающих почту общедоступных папок, чтобы она указывала на Exchange Online:
    
        .\SetMailPublicFolderExternalAddress.ps1 -ExecutionSummaryFile:mepf_summary.csv

2.  Если проверка прошла успешно, в локальной среде выполните следующую команду, чтобы указать, что миграция общедоступных папок завершена:
    
        Set-OrganizationConfig -PublicFolderMailboxesMigrationComplete:$true -PublicFoldersEnabled Remote

## Как проверить, что это работает

На шаге 2 Подготовка к миграции вы сделали моментальные снимки структуры, статистики и разрешений локальных общедоступных папок. Ниже описано, как сделать такие же моментальные снимки в Exchange Online после миграции. Сравните данные в обоих файлах, чтобы проверить успешность.

1.  В Exchange Online PowerShell выполните следующую команду, чтобы сделать моментальный снимок новой структуры папок:
    
        Get-PublicFolder -Recurse -ResultSize Unlimited | Export-CliXML Cloud_PFStructure.xml

2.  В Exchange Online PowerShell выполните следующую команду, чтобы сделать моментальный снимок статистики общедоступных папок, в том числе количества, размеров и владельцев элементов:
    
        Get-PublicFolder -Recurse -ResultSize Unlimited | Get-PublicFolderStatistics | Export-CliXML Cloud_PFStatistics.xml

3.  В Exchange Online PowerShell выполните следующую команду, чтобы сделать моментальный снимок разрешений:
    
        Get-PublicFolder -Recurse -ResultSize Unlimited | Get-PublicFolderClientPermission | Select-Object Identity,User, AccessRights | Export-CliXML Cloud_PFPerms.xml

4.  В Exchange Online PowerShell выполните следующую команду, чтобы сделать моментальный снимок поддерживающих почту общедоступных папок:
    
        Get-MailPublicFolder -ResultSize Unlimited | Export-CliXML Cloud_MEPF.xml

## Известные проблемы

Ниже приведены распространенные проблемы миграции общих папок, которые могут возникнуть в вашей организации.

  - Мы не поддерживает перенос общих папок в Exchange Online, если число уникальных общих папок почтовых ящиков в Exchange Online, больше 100.

  - Разрешения для корневой общедоступной папки и папки EFORMS REGISTRY не будут перенесены в Exchange Online, и вам придется применить их в Exchange Online вручную. Для этого выполните команду ниже в Exchange Online PowerShell. Выполните команду по одному разу для каждого разрешения в локальной среде, которого нет в Exchange Online:
    
        Add-PublicFolderClientPermission "\" -User <user> -AccessRights <access rights>
        Add-PublicFolderClientPermission "\NON_IPM_SUBTREE\EFORMS REGISTRY" -User <user> -AccessRights <access rights>

  - Некоторые миграции общих папок завершится ошибкой, если некоторые почтовые ящики общедоступных папок не обслуживают иерархию общих папок. Это означает, что для параметра `IsExcludedFromServingHierarchy` на один или несколько почтовых ящиков — это значение `$true`. Чтобы избежать этого, задайте всех почтовых ящиков в Exchange Online для функционирования в иерархии.

  - Разрешения **Отправить как** и **Отправить от имени** не переносятся в Exchange Online. Используйте приведенные ниже команды в локальной среде, чтобы узнать, у кого есть эти разрешения.
    
    Чтобы узнать, у каких локальных общедоступных папок есть разрешения "Отправить как":
    
        Get-MailPublicFolder | Get-ADPermission | ?{$_.ExtendedRights -like "*Send-As*"}
    
    Чтобы узнать, у каких локальных общедоступных папок есть разрешения "Отправить от имени":
    
        Get-MailPublicFolder | ?{$_.GrantSendOnBehalfTo -ne "$null"} | ft name,GrantSendOnBehalfTo
    
    Чтобы добавить разрешение "Отправить от имени" для поддерживающей почту общедоступной папки в Exchange Online, выполните следующую команду в Exchange Online PowerShell:
    
        Add-RecipientPermission -Identity <mail-enabled public folder primary SMTP address> -Trustee <name of user to be assigned permission> -AccessRights SendAs
    
    **Пример**:
    
        Add-RecipientPermission -Identity send1 -Trustee Exo1 -AccessRights SendAs
    
    Чтобы добавить разрешение "Отправить как" для поддерживающей почту общедоступной папки в Exchange Online, выполните следующую команду в Exchange Online PowerShell:
    
        Set-MailPublicFolder -Identity <name of public folder> -GrantSendOnBehalfTo <user or comma-separated list of users>
    
    **Пример**:
    
        Set-MailPublicFolder send2 -GrantSendOnBehalfTo exo1,exo2

  - Если в папке "\\NON\_IPM\_SUBTREE\\DUMPSTER\_ROOT" более 10 000 папок, может возникнуть ошибка миграции. Проверяйте количество папок, вложенных в "\\NON\_IPM\_SUBTREE\\DUMPSTER\_ROOT" (непосредственных дочерних элементов). Чтобы посмотреть, сколько общедоступных папок находится в этом расположении, используйте следующую команду:
    
        (Get-PublicFolder -GetChildren "\NON_IPM_SUBTREE\DUMPSTER_ROOT").Count 
    
    Exchange Online не поддерживает более 10 000 вложенных папок, поэтому перенести более 10 000 папок не удастся. В настоящее время мы разрабатываем сценарий для поддержки таких конфигураций. Советуем подождать.

  - Выполнение заданий миграции не продвигается или остановилось. Это может произойти, если слишком много заданий выполняется параллельно, в результате чего возникают временные ошибки. Вы можете уменьшить количество параллельных заданий, уменьшив значения `MaxConcurrentMigrations` и `MaxConcurrentIncrementalSyncs`. Используйте следующий пример, чтобы установить эти значения:
    
        Set-MigrationEndpoint <PublicFolderEndpoint> -MaxConcurrentMigrations 30 -MaxConcurrentIncrementalSyncs 20  -SkipVerification 

  - Выполнение заданий миграции заканчивается, при этом отображается такое сообщение об ошибке: "Ошибка. Корзина папки корзины". Чтобы устранить эту ошибку, остановите обработку пакета и запустите ее снова.

  - Миграция заданий с ошибкой и создания «запроса в карантин из-за следующее сообщение об ошибке: данный ключ не представлен в словаре» сообщение об ошибке. Это происходит, когда поврежденный элемент присутствует в папке, которая не удается скопировать заданий миграции. Чтобы обойти эту проблему:
    
    1.  Остановите обработку пакета миграции.
    
    2.  Определите папку, содержащую поврежденный элемент. В отчете о миграции должны быть ссылки на папку, которая копировалась при возникновении ошибки.
    
    3.  В локальной среде переместите эту папку в основной почтовый ящик общедоступных папок. Вы можете использовать командлет `New-PublicFolderMoveRequest` для перемещения папок.
    
    4.  Дождитесь перемещение папки для выполнения. После завершения удаления запроса на перемещение. Перезапустите пакета миграции.

## Удаление почтовых ящиков общедоступных папок из локальной среды Exchange

После того как миграция закончится и вы убедитесь, что общедоступные папки в Exchange Online работают должным образом и содержат все нужные данные, можно удалять локальные почтовые ящики общедоступных папок.

Обратите внимание, что это действие нельзя обратить, так как после удаления почтовых ящиков общедоступных папок они не могут быть восстановлены. Таким образом мы настоятельно рекомендуем, в дополнение к проверке успешности миграции, также наблюдать за вашей общедоступные папки Exchange Online несколько недель, прежде чем удалять локальные почтовые ящики общедоступных папок.

