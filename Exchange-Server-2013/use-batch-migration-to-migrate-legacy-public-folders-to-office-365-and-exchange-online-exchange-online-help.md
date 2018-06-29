﻿---
title: 'Использование пакетной миграции для переноса устаревших общедоступных папок в Office 365 и Exchange Online: Exchange 2013 Help'
TOCTitle: Использование пакетной миграции для переноса устаревших общедоступных папок в Office 365 и Exchange Online
ms:assetid: e8ab9309-7d12-4f02-bfc4-14e61a373958
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn874017(v=EXCHG.150)
ms:contentKeyID: 63895111
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Использование пакетной миграции для переноса устаревших общедоступных папок в Office 365 и Exchange Online

 

_**Применимо к:**Exchange Online, Exchange Server, Exchange Server 2013_

_**Последнее изменение раздела:**2018-03-26_

**Сводка**. Используйте эти процедуры, чтобы переместить общедоступные папки Exchange 2007 и Exchange 2010 в Office 365.

В этой статье описано, как перенести общедоступные папки в рамках прямой или поэтапной миграции с накопительного пакета обновления 8 для Exchange Server 2010 с пакетом обновления 3 (SP3) или с накопительного пакета обновления 15 для Exchange 2007 с пакетом обновления 3 (SP3) в Office 365 или Exchange Online.

В этом разделе серверы Exchange 2010 с пакетом обновления 3 (SP3) и накопительным пакетом обновления 8 (RU8) и Exchange 2007 с пакетом обновления 3 (SP3) и накопительным пакетом обновления 15 (RU15) называются *сервером Exchange прежних версий*. Кроме того, инструкции, приведенные в этом разделе, применимы к Exchange Online и Office 365. Данные продукты в контексте этого раздела являются взаимозаменяемыми.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Метод пакетной миграции, описанный в этой статье, — это единственный поддерживаемый способ миграции общедоступных папок предыдущих версий в Office 365 и Exchange Online. Майкрософт больше не поддерживает старый метод последовательной миграции общедоступных папок.</td>
</tr>
</tbody>
</table>


Мы не рекомендуем использовать функцию экспорта в PST-файл Outlook для переноса общедоступных папок в Office 365 или Exchange Online. Ростом почтового ящика общедоступных папок Office 365 и Exchange Online управляет функция авторазбиения, которая разбивает почтовый ящик, если его размер превышает заданные квоты. Функция авторазбиения не может справиться с внезапным разрастанием почтовых ящиков общедоступных папок при использовании экспорта в PST-файл для переноса общедоступных папок. Перемещение данных из основного почтового ящика может занять до двух недель. Мы рекомендуем использовать инструкции на основе командлетов, описанные в этом документе, чтобы переносить общедоступные папки в Office 365 и Exchange Online. Однако если вы решите использовать экспорт в PST-файл, ознакомьтесь с разделом Перенос общедоступных папок в Office 365 с помощью функции экспорта в PST-файл Outlook далее в этой статье.

Миграция выполняется с помощью командлетов **\*-MigrationBatch**, а также с помощью следующих сценариев PowerShell.

  - `Export-PublicFolderStatistics.ps1`: этот сценарий создает файл сопоставления имени и размера папки. Этот сценарий запускается на сервере Exchange прежних версий.

  - `Export-PublicFolderStatistics.psd1`: этот файл поддержки используется сценарием `Export-PublicFolderStatistics.ps1`, его необходимо загрузить в то же расположение.

  - `PublicFolderToMailboxMapGenerator.ps1`: этот сценарий создает файл сопоставления общедоступной папки и почтового ящика, используя выходные данные сценария `Export-PublicFolderStatistics.ps1`. Этот сценарий запускается на сервере Exchange прежних версий.

  - `PublicFolderToMailboxMapGenerator.strings.psd1`: этот файл поддержки используется сценарием `PublicFolderToMailboxMapGenerator.ps1`, и его необходимо загрузить в то же расположение.

  - `Create-PublicFolderMailboxesForMigration.ps1`. Этот сценарий создает почтовые ящики целевой общедоступной папки для переноса. Кроме того, этот сценарий подсчитывает необходимое количество почтовых ящиков для обработки прогнозируемой пользовательской нагрузки, основываясь на указаниях по количеству входов пользователей на почтовый ящик общедоступных папок с учетом рекомендаций в [Ограничения общедоступных папок](limits-for-public-folders-exchange-2013-help.md).

  - `Create-PublicFolderMailboxesForMigration.strings.psd1`. Этот файл поддержки используется сценарием Create-PublicFolderMailboxesForMigration.ps1 и должен быть скачан в то же расположение.

  - `Sync-MailPublicFolders.ps1`: этот сценарий синхронизирует объекты общедоступных папок, поддерживающих почту, между развертыванием Exchange и Office 365 в локальной среде. Этот сценарий запускается на сервере Exchange прежних версий.

  - `SyncMailPublicFolders.strings.psd1`: это файл поддержки, используемый сценарием `Sync-MailPublicFolders.ps1`. Его необходимо скопировать в то же расположение, что и предыдущие сценарии.

Шаг 1. Скачивание сценариев переноса содержит сведения о том, куда их скачивать. Убедитесь, что все сценарии скачиваются в одно и то же расположение.

Дополнительные сведения о задачах управления, связанных с общедоступными папками, см. в статье [Процедуры с общедоступными папками](public-folder-procedures-exchange-2013-help.md).

## Версии Exchange, для которых поддерживается миграция общедоступных папок в Office 365 и Exchange Online

Exchange поддерживает перемещение ваших общедоступных папок в Office 365 и Exchange Online из таких прежних версий Exchange Server:

  - Exchange 2010 с пакетом обновления 3 (SP3) и накопительным пакетом обновления 8 (RU8) или более поздних версий;

  - Exchange 2007 с пакетом обновления 3 (SP3) и накопительным пакетом обновления 15 (RU15) или более поздних версий.

Если вам нужно переместить общедоступные папки в Exchange Online, но на локальных серверах нет минимальных поддерживаемых версий Exchange 2010 или Exchange 2007, мы настоятельно рекомендуем обновить локальные серверы и использовать пакетную миграцию, так как это единственный поддерживаемый метод миграции общедоступных папок.

Перенести общедоступные папки непосредственно из Exchange 2003 невозможно. Если в вашей организации используется Exchange 2003, переместите все базы данных и реплики общедоступных папок в Exchange 2010 с пакетом обновления 3 (SP3) и накопительным пакетом обновления 8 (RU8) или более поздних версий либо в Exchange 2007 с пакетом обновления 3 (SP3) и накопительным пакетом обновления 10 (RU10) или более поздних версий. Реплики общедоступных папок не могут оставаться в Exchange 2003. Кроме того, почта, отправленная в общедоступную папку Exchange 2013, не может передаваться через сервер Exchange 2003.

## Что нужно знать перед началом работы

  - Сервер Exchange 2010 должен работать под управлением Exchange 2010 с пакетом обновления 3 (SP3) и накопительным пакетом обновления 8 (RU8) или более поздних версий.

  - Сервер Exchange 2007 должен работать под управлением Exchange 2007 с пакетом обновления 3 (SP3) и накопительным пакетом обновления 15 (RU15) или более поздних версий.

  - В Office 365 и Exchange Online вам необходимо быть членом группы ролей "Управление организацией". Эта группа ролей отличается от разрешений, которые назначаются при подписке на Office 365 или Exchange Online. Сведения о том, как включить группу ролей "Управление организацией", см. в статье [Управление группами ролей](manage-role-groups-exchange-2013-help.md).

  - В Exchange 2010 вам необходимо быть членом группы ролей RBAC "Управление организацией" или "Управление сервером". Дополнительные сведения см. в статье [Добавление участников в группу роли](https://go.microsoft.com/fwlink/?linkid=299212).

  - В Exchange 2007 вам необходима роль администратора организации Exchange или администратора сервера Exchange Server. Кроме того, вам необходима роль администратора общедоступных папок, а также вы должны входить в локальную группу администраторов целевого сервера. Дополнительные сведения см. в статье [Инструкции по добавлению пользователя или группы в роль администратора](https://go.microsoft.com/fwlink/p/?linkid=81779).

  - При работе с сервером Exchange 2007 необходимо выполнить обновление до [Windows PowerShell 2.0 и WinRM 2.0 для 64-разрядного выпуска Windows Server 2008](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=968930).

  - Если какая-либо из общедоступных папок в организации имеет размер больше 2 ГБ, то перед выполнением миграции рекомендуется либо удалить из нее содержимое, либо разбить его на несколько общедоступных папок. Если ни один их этих вариантов неприемлем, рекомендуется не перемещать общедоступные папки в Office 365 и Exchange Online.

  - В Office 365 и Exchange Online можно создать до 1000 почтовых ящиков общедоступных папок.

  - Перед переносом общедоступных папок рекомендуем сначала переместить все почтовые ящики пользователей в Office 365 и Exchange Online. Дополнительные сведения см. в статье [Способы переноса нескольких записей электронной почты в Office 365](https://go.microsoft.com/fwlink/p/?linkid=524030).

  - На сервере Exchange Server прежних версий должен быть включен мобильный Outlook. Дополнительные сведения о том, как включить мобильный Outlook на серверах Exchange 2010, см. в статье [Включение мобильного Outlook](https://go.microsoft.com/fwlink/p/?linkid=187249). Дополнительные сведения о том, как включить мобильный Outlook на серверах Exchange 2007, см. в статье [Инструкции по включению мобильного Outlook](https://go.microsoft.com/fwlink/p/?linkid=167210).

  - Эту процедуру невозможно выполнить с помощью Центра администрирования Exchange или консоли управления Exchange. На серверах Exchange прежних версий необходимо использовать командную консоль Exchange. В Exchange Online необходимо использовать Exchange Online PowerShell. Дополнительные сведения см. в статье [Подключение к Exchange Online с помощью удаленной оболочки PowerShell](https://technet.microsoft.com/ru-ru/library/jj984289\(v=exchg.150\)).

  - Перед началом мы советуем вам полностью прочитать этот раздел, поскольку при выполнении некоторых действий требуется простой.

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


## Как это сделать

## Шаг 1. Загрузка сценариев переноса

1.  Скачайте все сценарии и сопутствующие файлы со страницы [Public Folders Migration Scripts](https://go.microsoft.com/fwlink/?linkid=299838).

2.  Сохраните эти сценарии на локальном компьютере, с которого вы собираетесь запускать оболочку PowerShell. (Например, в папку C:\\PFScripts). Убедитесь, что все сценарии сохранены в одном и том же месте.

3.  Скачайте указанные ниже файлы на странице [Общедоступные папки с включенной поддержкой почты: скрипт для синхронизации каталогов](https://go.microsoft.com/fwlink/p/?linkid=532376).
    
    1.  `Sync-MailPublicFolders.ps1`
    
    2.  `SyncMailPublicFolders.strings.psd1`

4.  Сохраните эти сценарии в расположение, упоминавшееся на шаге 2, например в C:\\PFScripts.

## Этап 2. Подготовка к миграции

Перед началом миграции выполните указанные ниже предварительные действия.

**Общие предварительные условия**

  - Убедитесь, что в Active Directory нет потерянных почтовых объектов общедоступной папки, то есть объектов без соответствующих им объектов Exchange.

  - Убедитесь, что электронный адрес SMTP, настроенный для общедоступных папок в Active Directory, совпадает с электронными адресами SMTP в объектах Exchange.

  - Убедитесь, что в Active Directory нет повторяющихся объектов общедоступной папки, чтобы два (или больше) объекта Active Directory не указывали на одну общедоступную папку, поддерживающую почту.

**Предварительные действия на сервере Exchange прежней версии**

1.  Убедитесь, что на сервере Exchange прежних версий маршрутизация в общедоступные папки, поддерживающие почту, которые будут существовать в Office 365 или Exchange Online, продолжает работать до тех пор, пока все кэши DNS в Интернете не будут обновлены так, чтобы указывать на DNS Office 365 или Exchange Online, в которой располагается организация. Для этого запустите следующую команду, чтобы настроить обслуживаемый домен с хорошо известным именем, который будет правильно выполнять маршрутизацию сообщений электронной почты в домен Office 365 или Exchange Online.
    
        New-AcceptedDomain -Name "PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99" -DomainName contoso.onmicrosoft.com -DomainType InternalRelay 

2.  Если имя общедоступной папки содержит обратную косую черту (**\\**), то после миграции общедоступные папки будут созданы внутри родительской общедоступной папки. Мы советуем вам перед миграцией переименовать общедоступные папки с обратной косой чертой в имени.
    
    1.  Чтобы найти общедоступные папки с обратной косой чертой в имени, на сервере Exchange 2010 выполните следующую команду:
        
            Get-PublicFolderStatistics -ResultSize Unlimited | Where {($_.Name -like "*\*") -or ($_.Name -like "*/*") } | Format-List Name, Identity
    
    2.  Чтобы найти общедоступные папки с обратной косой чертой в имени, на сервере Exchange 2007 выполните следующую команду:
        
            Get-PublicFolderDatabase | ForEach {Get-PublicFolderStatistics -Server $_.Server | Where {$_.Name -like "*\*"}}
    
    3.  Если эта команда возвращает сведения об общедоступных папках, переименуйте их с помощью такой команды:
        
            Set-PublicFolder -Identity <public folder identity> -Name <new public folder name>

3.  Убедитесь в отсутствии записи о предыдущей успешной миграции. В противном случае следует установить значение `$false`. Если значение равно `$true`, то запрос на миграцию не удастся выполнить.
    
    1.  В следующем примере проверяется состояние миграции общедоступных папок.
        
            Get-OrganizationConfig | Format-List PublicFoldersLockedforMigration, PublicFolderMigrationComplete
    
    2.  Если для свойства *PublicFoldersLockedforMigration* или *PublicFolderMigrationComplete* установлено состояние `$true`, выполните следующую команду, чтобы установить значение `$false`.
        
            Set-OrganizationConfig -PublicFoldersLockedforMigration:$false -PublicFolderMigrationComplete:$false
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ983803.warning(EXCHG.150).gif" title="Предупреждение" alt="Предупреждение" />Предупреждение.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>После сброса этих свойств необходимо дождаться обнаружения новых параметров системой Exchange. На это может потребоваться до двух часов.</td>
    </tr>
    </tbody>
    </table>


4.  Для проверки в конце миграции рекомендуем сначала выполнить указанные ниже команды командной консоли Exchange на сервере Exchange прежних версий, чтобы сделать моментальные снимки текущего развертывания общедоступных папок.
    
    1.  Выполните следующую команду, чтобы сделать моментальный снимок начальной структуры исходных папок.
        
            Get-PublicFolder -Recurse | Export-CliXML C:\PFMigration\Legacy_PFStructure.xml
    
    2.  Выполните следующую команду, чтобы сделать моментальный снимок статистики общедоступных папок, такой как число элементов, размер и владелец.
        
            Get-PublicFolderStatistics -ResultSize Unlimited | Export-CliXML C:\PFMigration\Legacy_PFStatistics.xml
    
    3.  Выполните следующую команду, чтобы сделать моментальный снимок разрешений.
        
            Get-PublicFolder -Recurse | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML C:\PFMigration\Legacy_PFPerms.xml
    
    Сохраните информацию, полученную в результате выполнения этих команд, для сравнения в конце процесса миграции.

5.  Если вы используете Microsoft Azure Active Directory подключиться (Azure AD подключение) для синхронизации с Azure Active Directory локально размещенные каталоги, необходимо выполните следующие действия (Если вы не используете Azure AD подключение, можно пропустить этот этап):
    
    1.  На локальный компьютер откройте Microsoft Azure Active Directory подключение и затем выберите **Настройка**.
    
    2.  На экране **Дополнительные задачи** выберите **Настройка параметров синхронизации** и нажмите кнопку **Далее**.
    
    3.  На экране **подключение к Azure AD** введите соответствующие данные и нажмите кнопку **Далее**. После подключения, снова нажмите кнопку **Далее** до на экране **Дополнительных компонентов** .
    
    4.  Убедитесь в том, что **Общедоступных папок почты Exchange** не выбран. Если он не установлен, можно продолжить к следующему разделу, *необходимые предварительные действия в Office 365 и Exchange Online*. Если он установлен, снимите этот флажок и нажмите кнопку **Далее**.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Если <strong>Общедоступных папок почты Exchange</strong> не отображается как вариант на экране <strong>Дополнительных компонентов</strong>, следует выйти из Microsoft Azure Active Directory подключение и перейти к следующему разделу, <em>необходимые предварительные действия в Office 365 и Exchange Online</em>.</td>
        </tr>
        </tbody>
        </table>
    
    5.  После очистки выбора **Общедоступных папок почты Exchange**, оставьте нажмите кнопку **Далее**, пока не будете на экране **все готово к настройке** и нажмите кнопку **настроить**.

Подробные сведения о синтаксисе и параметрах см. в таких разделах:

  - [New-AcceptedDomain](https://technet.microsoft.com/ru-ru/library/aa995975\(v=exchg.150\))

  - [Get-PublicFolder](https://technet.microsoft.com/ru-ru/library/aa997615\(v=exchg.150\))

  - [Get-PublicFolderDatabase](https://technet.microsoft.com/ru-ru/library/jj733416\(v=exchg.150\))

  - [Set-PublicFolder](https://technet.microsoft.com/ru-ru/library/aa998596\(v=exchg.150\))

  - [Get-PublicFolderStatistics](https://technet.microsoft.com/ru-ru/library/aa998663\(v=exchg.150\))

  - [Get-PublicFolderClientPermission](https://technet.microsoft.com/ru-ru/library/bb124365\(v=exchg.150\))

  - [Get-OrganizationConfig](https://go.microsoft.com/fwlink/p/?linkid=183212)

  - [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?linkid=183213)

**Предварительные действия в Office 365 и Exchange Online**

1.  Убедитесь в отсутствии существующих запросов на миграцию общедоступных папок. Если они есть, очистите их. В противном случае запрос на миграцию завершится ошибкой. Это действие требуется не всегда. Его необходимо выполнить, только если вы подозреваете, что конвейер может содержать существующий запрос на миграцию.
    
    Существующий запрос на миграцию может относиться к одному из двух типов: пакетной миграции или последовательной миграции. Ниже указаны команды для обнаружения и удаления запросов обоих типов.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Перед удалением запроса на миграцию важно понять, почему он существовал. Выполните следующие команды, чтобы определить, когда сделан предыдущий запрос, и обнаружить любые возможные проблемы. Чтобы определить, почему сделано это изменение, может потребоваться консультация с другими администраторами в организации.</td>
    </tr>
    </tbody>
    </table>
    
    В примере ниже показано обнаружение существующих запросов на последовательную миграцию.
    
        Get-PublicFolderMigrationRequest | Get-PublicFolderMigrationRequestStatistics -IncludeReport | Format-List
    
    В примере ниже показано удаление существующих запросов на последовательную миграцию общедоступных папок.
    
        Get-PublicFolderMigrationRequest | Remove-PublicFolderMigrationRequest
    
    В примере ниже показано обнаружение существующих запросов на пакетную миграцию.
    
        $batch = Get-MigrationBatch | ?{$_.MigrationType.ToString() -eq "PublicFolder"}
    
    В примере ниже показано удаление существующих запросов на пакетную миграцию общедоступных папок.
    
        $batch | Remove-MigrationBatch -Confirm:$false

2.  Убедитесь, что в Office 365 нет никаких общедоступных папок или почтовых ящиков общедоступных папок.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если вы видите общих папок в Office 365 и Exchange Online, важно определить, почему они существуют и пользователей, которые в вашей организации работы иерархии общедоступных папок перед удалением общих папок и почтовых ящиков общедоступных папок.</td>
    </tr>
    </tbody>
    </table>
    
    1.  Чтобы проверить, имеются ли какие-либо почтовые ящики общедоступных папок, в оболочке Office 365 или Exchange Online PowerShell запустите следующую команду.
        
            Get-Mailbox -PublicFolder 
    
    2.  Если команда не вернула никаких почтовых ящиков общедоступных папок, перейдите на Step 3: Generate the CSV files. Если команда вернула какие-либо почтовые ящики общедоступных папок, запустите следующую команду, чтобы проверить, имеются ли какие-либо общедоступные папки.
        
            Get-PublicFolder
    
    3.  Если в Office 365 или Exchange Online имеются какие-либо общедоступные папки, выполните следующую команду оболочки PowerShell, чтобы удалить их. Убедитесь, что вы сохранили все данные из общедоступных папок в Office 365. При удалении общедоступных папок все данные в них удаляются без возможности восстановления.
        
            Get-MailPublicFolder | where {$_.EntryId -ne $null}| Disable-MailPublicFolder -Confirm:$false 
            
            
            Get-PublicFolder -GetChildren \ | Remove-PublicFolder -Recurse -Confirm:$false
    
    4.  После удаления общедоступных папок выполните следующие команды, чтобы удалить все почтовые ящики общедоступных папок.
        
            $hierarchyMailboxGuid = $(Get-OrganizationConfig).RootPublicFolderMailbox.HierarchyMailboxGuid
            
            Get-Mailbox -PublicFolder:$true | Where-Object {$_.ExchangeGuid -ne $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false
            
            Get-Mailbox -PublicFolder:$true | Where-Object {$_.ExchangeGuid -eq $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false

Подробные сведения о синтаксисе и параметрах см. в следующих статьях.

  - [Get-MigrationBatch](https://technet.microsoft.com/ru-ru/library/jj219164\(v=exchg.150\))

  - [Get-PublicFolderMigrationRequest](https://technet.microsoft.com/ru-ru/library/jj218718\(v=exchg.150\))

  - [Remove-PublicFolderMigrationRequest](https://technet.microsoft.com/ru-ru/library/jj218625\(v=exchg.150\))

  - [Get-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123685\(v=exchg.150\))

  - [Get-PublicFolder](https://technet.microsoft.com/ru-ru/library/aa997615\(v=exchg.150\))

  - [Get-MailPublicFolder](https://technet.microsoft.com/ru-ru/library/bb124772\(v=exchg.150\))

  - [Disable-MailPublicFolder](https://technet.microsoft.com/ru-ru/library/bb123781\(v=exchg.150\))

  - [Remove-PublicFolder](https://technet.microsoft.com/ru-ru/library/bb124894\(v=exchg.150\))

  - [Remove-Mailbox](https://technet.microsoft.com/ru-ru/library/aa995948\(v=exchg.150\))

## Действие 3. Создание CSV-файлов

1.  На сервере Exchange прежних версий запустите сценарий `Export-PublicFolderStatistics.ps1`, чтобы создать файл сопоставления имени и размера папки. Этот сценарий всегда должен запускать локальный администратор. Файл будет иметь два столбца: **FolderName** и **FolderSize**. Значения для столбца **FolderSize** будут отображены в байтах (например, **\\PublicFolder01,10000**).
    
        .\Export-PublicFolderStatistics.ps1  <Folder to size map path> <FQDN of source server>
    
      - *FQDN of source server* указывает полное доменное имя сервера почтовых ящиков, на котором размещена иерархия общедоступных папок.
    
      - *Folder to size map path* указывает имя файла и путь к этому файлу в сетевой общедоступной папке, в которой необходимо сохранить CSV-файл. Далее в этом разделе вам понадобится использовать Exchange Online PowerShell для доступа к этому файлу. Если указать только имя файла, он будет создан в текущем каталоге оболочки PowerShell на локальном компьютере.
    
      - При необходимости, прежде чем продолжить, удалите системные папки, поддерживающие почту, из выходных данных сценария.

2.  Запустите сценарий `PublicFolderToMailboxMapGenerator.ps1`, чтобы создать файл сопоставления общедоступных папок и почтовых ящиков. Этот файл используется для вычисления правильного количества почтовых ящиков общедоступных папок в Exchange Online.
    
        .\PublicFolderToMailboxMapGenerator.ps1 <Maximum mailbox size in bytes> <Folder to size map path> <Folder to mailbox map path>
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Файл сопоставления общедоступных папок для почтового ящика не должно превышать 1000 строк. Если этот файл превышает 1 000 строк, структуре общей папки необходимо упростить. Продолжить с помощью файла размером более 1 000 строк не рекомендуется и может стать причиной ошибки переноса.</td>
    </tr>
    </tbody>
    </table>
    
      - Прежде чем запустить сценарий используйте следующий командлет для проверки текущего ограничения общедоступных папок в Exchange Online клиентов. Запишите текущие значения квот для общих папок. `Get-OrganizationConfig | fl *quota*`
        
        В Exchange Online значением по умолчанию является 1,7 ГБ для **DefaultPublicFolderIssueWarningQuota** и 2 ГБ для **DefaultPublicFolderProhibitPostQuota**.
    
      - *Maximum mailbox size in bytes* указывает максимальный размер, который требуется установить для новых почтовых ящиков общедоступных папок. В Exchange Online максимальный размер почтовых ящиков общедоступных папок — 100 ГБ. Мы рекомендуем использовать параметр 15 ГБ, чтобы каждый почтовый ящик общедоступных папок имеет место на случай увеличения. Exchange Online имеет квоту «запретить запись» общедоступные папки по умолчанию 2 ГБ. При наличии отдельных общих папок, размер которых превышает 2 ГБ для устранения этой проблемы можно использовать любой из следующих параметров:
        
          - Прежде чем начать пакета миграции, увеличьте квоту «запретить отправку» общей папки по умолчанию, выполнив следующий командлет:
            
            `Set-OrganizationConfig -DefaultPublicFolderProhibitPostQuota <size value> -DefaultPublicFolderIssueWarningQuota <size value>`
        
          - Прежде чем начать пакета миграции, удалите общей папки, не более контента для уменьшения размера контента до 2 ГБ.
        
          - Прежде чем начать пакета миграции, разбейте общедоступную папку на несколько общедоступных папок, которые являются каждого 2 ГБ или меньше.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Если Общедоступная папка превышает 30 ГБ, и если оно не будет невозможно удалить содержимое или разбить на несколько общедоступных папок, мы рекомендуем не перемещение общих папок в Exchange Online.</td>
        </tr>
        </tbody>
        </table>
    
      - *Folder to size map path* указывает путь к CSV-файлу, который вы создали при выполнении сценария `Export-PublicFolderStatistics.ps1` .
    
      - *Folder to mailbox map path* — это имя файла и путь к папке для почтового ящика CSV-файла, создаваемого на этом этапе. При указании имени файла, файл создается в текущем каталоге PowerShell на локальном компьютере.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>После выполнения сценариев и создаются CSV-файлов, любые новые общих папок или обновления для существующих общедоступных папок не будут собраны.</td>
</tr>
</tbody>
</table>


## Этап 4. Создание почтовых ящиков общедоступных папок в Exchange Online

1.  Выполните следующую команду, чтобы создать целевые почтовые ящики общедоступной папки. Сценарий создаст целевой почтовый ящик для каждого ящика в файле .csv, созданного на шаге 3, запустив сценарий PublicFoldertoMailboxMapGenerator.ps1.
    
        .\Create-PublicFolderMailboxesForMigration.ps1 -FolderMappingCsv Mapping.csv -EstimatedNumberOfConcurrentUsers:<estimate>
    
    *Mapping.csv* — файл, созданный сценарием PublicFoldertoMailboxMapGenerator.ps1 на шаге 3. Предполагаемое количество одновременных подключений пользователей, просматривающих иерархию общедоступной папки, обычно меньше, чем общее количество пользователей в организации.

## Шаг 5. Запуск запроса на перенос

1.  На сервере Exchange устаревшей версии выполните следующую команду, чтобы синхронизировать общедоступные папки, поддерживающие почту, между локальным каталогом Active Directory и Exchange Online.
    
        Sync-MailPublicFolders.ps1 -Credential (Get-Credential) -CsvSummaryFile:sync_summary.csv
    
    `Credential` — ваше имя пользователя и пароль для Office 365. `CsvSummaryFile` — путь к файлу журнала в формате CSV, в котором нужно регистрировать ошибки и операции синхронизации.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Рекомендуем сначала имитировать действия сценария до их фактического выполнения, запустив сценарий с параметром <code>-WhatIf</code>.</td>
    </tr>
    </tbody>
    </table>


2.  На сервере Exchange прежних версий получите следующие сведения, необходимые для запуска запроса на миграцию.
    
    1.  Найдите `LegacyExchangeDN` учетной записи пользователя, являющегося участником роли администратора общедоступных папок. Это будет тот же пользователь, чьи учетные данные потребовались на шаге 3 этой процедуры.
        
            Get-Mailbox <PublicFolder_Administrator_Account> | Select-Object LegacyExchangeDN
    
    2.  Найдите `LegacyExchangeDN` любого сервера почтовых ящиков, на котором есть база данных общедоступных папок.
        
            Get-ExchangeServer <public folder server> | Select-Object -Expand ExchangeLegacyDN
    
    3.  Найдите полное доменное имя для имени узла мобильного Outlook. Если имеется несколько экземпляров мобильного Outlook, рекомендуется выбрать либо экземпляр, находящийся ближе всего к конечной точке миграции, либо экземпляр, находящийся ближе всего к репликам общедоступных папок в организации Exchange прежних версий. С помощью следующей команды можно найти все экземпляры мобильного Outlook.
        
            Get-OutlookAnywhere | Format-Table Identity,ExternalHostName

3.  В оболочке Office 365 PowerShell выполните следующие команды, чтобы передать сведения, возвращенные на предыдущем шаге, в переменные, которые будут использованы в запросе на миграцию.
    
    1.  Передайте учетные данные пользователя, имеющего разрешения администратора на сервере Exchange прежних версий, в переменную `$Source_Credential`. Запрос на миграцию, запущенный в Exchange Online, будет использовать эти учетные данные для получения доступа к серверам Exchange прежних версий для копирования содержимого.
        
            $Source_Credential = Get-Credential <source_domain\PublicFolder_Administrator_Account>
    
    2.  Используйте `ExchangeLegacyDN` пользователя миграции на сервере Exchange более ранней версии, найденном на шаге 2a, и передайте его в переменную `$Source_RemoteMailboxLegacyDN`.
        
            $Source_RemoteMailboxLegacyDN = "<paste the value here>"
    
    3.  Используйте имя `ExchangeLegacyDN` сервера общедоступных папок, найденное на этапе 2b, и передайте его в переменную `$Source_RemotePublicFolderServerLegacyDN`.
        
            $Source_RemotePublicFolderServerLegacyDN = "<paste the value here>"
    
    4.  Используйте имя внешнего узла мобильного Outlook, найденное ранее на этапе 2c, и передайте его в переменную `$Source_OutlookAnywhereExternalHostName`.
        
            $Source_OutlookAnywhereExternalHostName = "<paste the value here>"

4.  Наконец, в оболочке Exchange Online PowerShell выполните следующие команды, чтобы создать запрос на миграцию.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Метод проверки подлинности в указанном ниже примере для командной консоли Exchange должен соответствовать настройкам мобильного Outlook, иначе команда даст сбой.</td>
    </tr>
    </tbody>
    </table>
    
        $PfEndpoint = New-MigrationEndpoint -PublicFolder -Name PublicFolderEndpoint -RPCProxyServer $Source_OutlookAnywhereExternalHostName -Credentials $Source_Credential -SourceMailboxLegacyDN $Source_RemoteMailboxLegacyDN -PublicFolderDatabaseServerLegacyDN $Source_RemotePublicFolderServerLegacyDN -Authentication Basic
        
        [byte[]]$bytes = Get-Content -Encoding Byte <folder_mapping.csv>
        
        New-MigrationBatch -Name PublicFolderMigration -CSVData $bytes -SourceEndpoint $PfEndpoint.Identity -NotificationEmails <email addresses for migration notifications>
    
    Здесь файл \<*folder\_mapping.csv*\> — это файл, создание которого описано в разделе Действие 3. Создание CSV-файлов.

5.  Запустите миграцию, выполнив следующую команду.
    
        Start-MigrationBatch PublicFolderMigration

Пакетную миграцию необходимо запускать с помощью командлета **New-MigrationBatch** в Командная консоль Exchange, но просматривать ход миграции и управлять им можно в Центре администрирования Exchange. Так как командлет **New-MigrationBatch** инициирует запрос на миграцию почтовых ящиков для каждого почтового ящика общедоступных папок, вы можете просмотреть состояние этих запросов на странице миграции почтовых ящиков. Чтобы перейти на страницу миграции почтовых ящиков и создать отчеты о миграции, которые вы сможете отправить себе по электронной почте, сделайте следующее:

1.  Войдите в Exchange Online и откройте Центр администрирования Exchange.

2.  Последовательно выберите пункты **Почтовый ящик** \> **Перенос**.

3.  Выберите только что созданный запрос на перенос и щелкните **Просмотр сведений** в области **Сведения**.

Подробные сведения о синтаксисе и параметрах см. в следующих разделах:

  - [Get-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123685\(v=exchg.150\))

  - [Get-ExchangeServer](https://technet.microsoft.com/ru-ru/library/bb123873\(v=exchg.150\))

  - [Get-OutlookAnywhere](https://technet.microsoft.com/ru-ru/library/bb124263\(v=exchg.150\))

  - [New-PublicFolderMigrationRequest](https://technet.microsoft.com/ru-ru/library/jj218636\(v=exchg.150\))

  - [Get-PublicFolderDatabase](https://technet.microsoft.com/ru-ru/library/jj733416\(v=exchg.150\))

  - [Get-PublicFolderMigrationRequest](https://technet.microsoft.com/ru-ru/library/jj218718\(v=exchg.150\))

  - [Get-PublicFolderMigrationRequestStatistics](https://technet.microsoft.com/ru-ru/library/jj218697\(v=exchg.150\))

## Действие 6. Блокировка общедоступных папок на сервере Exchange предыдущей версии для окончательной миграции (требуется простой в работе)

До этого этапа в процессе миграции у пользователей был доступ к общедоступным папкам. На следующих этапах общедоступные папки прежних версий блокируются для последней синхронизации. В это время у пользователей не будет доступа к общедоступным папкам. Кроме того, все сообщения, отправленные в общедоступные папки, поддерживающие почту, будут поставлены в очередь и доставлены только после завершения миграции общедоступных папок.

Перед выполнением команды `PublicFoldersLockedForMigration` , как описано ниже, убедитесь в том, что все задания находятся в состоянии **синхронизирован**. Это можно сделать с помощью команды `Get-PublicFolderMailboxMigrationRequest` . Выполните этот шаг только после проверки, что все задания находятся в состоянии **синхронизирован**.

На сервере Exchange прежних версий выполните следующую команду для блокировки старых общедоступных папок для завершения процесса.

    Set-OrganizationConfig -PublicFoldersLockedForMigration:$true

Дополнительные сведения о синтаксисе и параметрах см. в статье [Set-OrganizationConfig](https://technet.microsoft.com/ru-ru/library/aa997443\(v=exchg.150\)).

Если в организации используется несколько баз данных общедоступных папок, потребуется дождаться завершения репликации общедоступных папок, чтобы убедиться, что все базы данных общедоступных папок получили флаг `PublicFoldersLockedForMigration` и все ожидающие обработки изменения, сделанные пользователем в папках, сошлись во всей организации. Это может занять несколько часов.

## Шаг 7. Завершение переноса общедоступных папок (требуется простой в работе)

Чтобы завершить миграцию общедоступных папок, выполните следующую команду.

    Complete-MigrationBatch PublicFolderMigration

После завершения миграции Exchange будет выполнять окончательный синхронизации между прежних версий Exchange server и Exchange Online. При успешном последней синхронизации общих папок в Exchange Online остаются разблокированными и состояние пакета миграции будет изменено на **завершено**. Обычно для пакета миграции для времени за несколько часов до его изменения состояния из **синхронизировано** для **завершения работы**, в какой точке начнется последней синхронизации.

Если между локальными серверами Exchange и Office 365 настроено гибридное развертывание, после завершения миграции необходимо выполнить в Exchange Online PowerShell следующую команду:

    Set-OrganizationConfig -RemotePublicFolderMailboxes $Null -PublicFoldersEnabled Local

## Этап 8. Проверка результатов миграции и разблокировка общедоступных папок

После завершения миграции общедоступных папок необходимо выполнить указанную ниже проверку и убедиться, что миграция прошла успешно. Это позволит вам проверить иерархию перенесенных общедоступных папок, прежде чем начать использовать их в Office 365 или Exchange Online.

1.  В Office 365 или Exchange Online PowerShell настройте несколько тестовых почтовых ящиков так, чтобы они использовали любой перенесенный почтовый ящик общедоступных папок в качестве почтового ящика общедоступных папок по умолчанию.
    
        Set-Mailbox -Identity <Test User> -DefaultPublicFolderMailbox <Public Folder Mailbox Identity>

2.  Войдите в Outlook 2007 или более поздней версии с помощью тестового пользователя, определенного во время предыдущего действия, и выполните такие тесты общедоступной папки:
    
      - Просмотр иерархии.
    
      - проверка разрешений;
    
      - Создание и удаление общедоступных папок.
    
      - Опубликуйте содержимое в общедоступной папке и удалите его.

3.  При выполнении в любой проблемы, видеть откат миграции данного раздела. Если содержимое общих папок и иерархии является приемлемым и функции, как ожидалось, перейдите к следующему шагу.

4.  На сервере Exchange прежних версий выполните приведенную ниже команду, чтобы указать завершение миграции общедоступных папок:
    
        Set-OrganizationConfig -PublicFolderMigrationComplete:$true

5.  Проверив завершение миграции, выполните следующую команду в Exchange Online PowerShell и убедитесь, что для параметра *PublicFoldersEnabled* в **Set-OrganizationConfig** установлено значение `Local`:
    
        Set-OrganizationConfig -PublicFoldersEnabled Local

Подробные сведения о синтаксисе и параметрах см. в таких разделах:

[Set-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123981\(v=exchg.150\))

[Get-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123685\(v=exchg.150\))

[Set-OrganizationConfig](https://technet.microsoft.com/ru-ru/library/aa997443\(v=exchg.150\))

## Как проверить, что это работает

В Step 2: Prepare for the migration указывалось, что перед началом миграции необходимо сделать моментальные снимки структуры, статистики и разрешений общедоступных папок. С помощью приведенных ниже действий можно проверить успешность миграции общедоступных папок, сделав такие же моментальные снимки после завершения миграции. Затем можно сравнить данные в обоих файлах, чтобы проверить успешность.

1.  В Exchange Online PowerShell выполните следующую команду, чтобы сделать моментальный снимок новой структуры папок.
    
        Get-PublicFolder -Recurse | Export-CliXML C:\PFMigration\Cloud_PFStructure.xml

2.  В Exchange Online PowerShell выполните следующую команду, чтобы сделать моментальный снимок статистики общедоступных папок, таких как число элементов, размер и владелец.
    
        Get-PublicFolderStatistics -ResultSize Unlimited | Export-CliXML C:\PFMigration\Cloud_PFStatistics.xml

3.  В Exchange Online PowerShell выполните следующую команду, чтобы сделать моментальный снимок разрешений.
    
        Get-PublicFolder -Recurse | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML  C:\PFMigration\Cloud_PFPerms.xml

## Удаление баз данных общедоступных папок с серверов Exchange прежних версий

После окончания миграции и проверки надлежащей работы общедоступных папок Exchange Online необходимо удалить базы данных общедоступных папок с серверов Exchange прежних версий.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Так как все почтовые ящики перенесены в Office 365 прежде общедоступной папки, настоятельно рекомендуем обеспечить маршрутизацию трафика через Office 365 (децентрализованный поток обработки почты), а не через локальную среду (централизованный поток). Если вы выберете централизованный поток обработки почты, могут возникнуть ошибки доставки в общедоступные папки, так как в локальной организации удалены базы данных почтовых ящиков для общедоступных папок.</td>
</tr>
</tbody>
</table>


  - Дополнительные сведения об удалении баз данных общедоступных папок с серверов Exchange 2007 см. в разделе [Удаление баз данных общих папок](https://go.microsoft.com/fwlink/?linkid=123678).

  - Дополнительные сведения об удалении баз данных общедоступных папок с серверов Exchange 2010 см. в разделе [Удаление баз данных общих папок](https://go.microsoft.com/fwlink/?linkid=81409).

## Откат миграции

Если из-за ошибок при миграции необходимо повторно активировать общедоступные папки Exchange прежних версий, выполните следующие действия.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ983803.warning(EXCHG.150).gif" title="Предупреждение" alt="Предупреждение" />Предупреждение.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если выполнять откат миграции на серверы Exchange прежних версий, то будут потеряны все сообщения электронной почты, которые отправлены на общедоступные папки, поддерживающие почту, и содержимое, опубликованное в общедоступных папках после миграции. Чтобы сохранить это содержимое, необходимо экспортировать содержимое общедоступных папок в PST-файл, а затем импортировать его в общедоступные папки прежних версий после отката.</td>
</tr>
</tbody>
</table>


1.  На сервере Exchange прежних версий выполните следующую команду, чтобы разблокировать общедоступные папки на сервере Exchange прежних версий. Этот процесс может занять несколько часов.
    
        Set-OrganizationConfig -PublicFoldersLockedForMigration:$False

2.  Чтобы удалить все общедоступные папки Exchange Online, в Exchange Online PowerShell выполните следующие команды.
    
        $hierarchyMailboxGuid = $(Get-OrganizationConfig).RootPublicFolderMailbox.HierarchyMailboxGuid
        
        Get-Mailbox -PublicFolder:$true | Where-Object {$_.ExchangeGuid -ne $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
        
        Get-Mailbox -PublicFolder:$true | Where-Object {$_.ExchangeGuid -eq $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force

3.  На сервере Exchange прежних версий выполните следующую команду, чтобы для флага `PublicFolderMigrationComplete` установить значение `$false`.
    
        Set-OrganizationConfig -PublicFolderMigrationComplete:$False

## Перенос общедоступных папок в Office 365 с помощью функции экспорта в PST-файл Outlook

Мы не рекомендуем использовать функцию экспорта в PST-файл Outlook для переноса общедоступных папок в Office 365 или Exchange Online, если размер иерархии папок превышает 30 ГБ. Ростом почтового ящика общедоступных папок Office 365 управляет функция авторазбиения, которая разбивает почтовый ящик, если его размер превышает заданные квоты. Функция авторазбиения не может справиться с внезапным разрастанием почтовых ящиков общедоступных папок при использовании экспорта в PST для переноса общедоступных папок. Перемещение данных из основного почтового ящика может занять до двух недель. Кроме того, рассмотрите следующие моменты, прежде чем использовать функцию экспорта в PST-файл Outlook для переноса общедоступных папок в Office 365 или Exchange Online.

  - Разрешения общедоступных папок будут потеряны в ходе этого процесса. Запишите текущие разрешения перед переносом и вручную добавьте их после его завершения.

  - Если вы используете сложные разрешения или переносите большое число папок, мы рекомендуем использовать командлеты.

  - Любые изменения элементов или папок в исходных общедоступных папках во время экспорта в PST-файл будут потеряны. Поэтому мы рекомендуем использовать инструкции на основе командлетов, если для процесса экспорта и импорта потребуется много времени.

Если вы все равно хотите переместить общедоступные папки с помощью PST-файлов, выполните следующие действия, чтобы успешно завершить операцию.

1.  Следуйте инструкциям в разделе Step 1: Download the migration scripts, чтобы загрузить сценарии переноса. Вам нужно скачать только файл `PublicFolderToMailboxMapGenerator.ps1`.

2.  Выполните шаг 2 Действие 3. Создание CSV-файлов, чтобы создать файл сопоставления общедоступных папок и почтовых ящиков. Этот файл используется для вычисления правильного количества почтовых ящиков общедоступных папок в Exchange Online.

3.  Создайте необходимые почтовые ящики общедоступных папок на основе файла сопоставления. Дополнительные сведения см. в статье [Создание почтового ящика общедоступных папок](create-a-public-folder-mailbox-exchange-2013-help.md).

4.  Используйте командлет New-PublicFolder, чтобы создать общедоступную папку верхнего уровня в каждом почтовом ящике общедоступных папок, используя параметр *Mailbox*.

5.  Экспорт и импорт PST-файлов с помощью Outlook.

6.  Установите разрешения для общедоступных папок с помощью Центра администрирования Exchange. Дополнительные сведения см. в разделе [Step 3: Assign permissions to the public folder](set-up-public-folders-in-a-new-organization-exchange-2013-help.md) статьи [Настройка общедоступных папок в новой организации](set-up-public-folders-in-a-new-organization-exchange-2013-help.md).

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ983803.warning(EXCHG.150).gif" title="Предупреждение" alt="Предупреждение" />Предупреждение.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если вы уже начали перенос с помощью PST-файлов и основной почтовый ящик заполнился, у вас есть два варианта для восстановления переноса с использованием PST.
<ol>
<li><p>Дождитесь, пока функция авторазбиения переместит данные из основного почтового ящика. Это может занять до двух недель. Однако все общедоступные папки в заполненном почтовом ящике общедоступных папок не смогут получать новое содержимое, пока авторазбиение не завершится.</p></li>
<li><p><a href="create-a-public-folder-mailbox-exchange-2013-help.md">Создание почтового ящика общедоступных папок</a> и используйте командлет <strong>New-PublicFolder</strong> с параметром <em>Mailbox</em>, чтобы создать оставшиеся общедоступные папки в дополнительном почтовом ящике общедоступных папок. В этом примере в дополнительном почтовом ящике создается общедоступная папка PF201.</p>
<pre><code>New-PublicFolder -Name PF201 -Mailbox SecondaryPFMbx</code></pre></li>
</ol></td>
</tr>
</tbody>
</table>


## Никогда не работали с Office 365?


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/Bb123521.eac8a413-9498-4220-8544-1e37d1aaea13(EXCHG.150).png" title="Небольшой значок LinkedIn Learning" alt="Небольшой значок LinkedIn Learning" /> <strong>Никогда не работали с Office 365?</strong><br />
<a href="https://support.office.com/ru-ru/article/office-365-admin-and-it-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5">Office 365 admins and IT pros</a> будут заинтересованы бесплатными видеокурсами, предоставленными платформой LinkedIn Learning.</p></td>
</tr>
</tbody>
</table>

