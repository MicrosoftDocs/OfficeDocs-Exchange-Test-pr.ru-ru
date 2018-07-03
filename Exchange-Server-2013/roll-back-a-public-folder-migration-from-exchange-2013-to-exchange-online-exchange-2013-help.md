---
title: 'Откат миграции общедоступных папок с Exchange 2013 до Exchange Online: Exchange 2013 Help'
TOCTitle: Откат миграции общедоступных папок с Exchange 2013 до Exchange Online
ms:assetid: bcd54aa0-aa45-4c68-b504-1475842d4b96
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Mt798259(v=EXCHG.150)
ms:contentKeyID: 74432749
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Откат миграции общедоступных папок с Exchange 2013 до Exchange Online

 

_**Последнее изменение раздела:** 2017-03-20_

**Сводка.** Следуйте приведенным ниже инструкциям, чтобы вернуть инфраструктуру общедоступных папок в локальной организации Exchange 2013 в то состояние, в котором она была перед миграцией.

Если у вас возникли проблемы с миграцией общедоступных папок в Exchange Online либо существуют другие причины для повторной активации общедоступных папок Exchange 2013, выполните описанные ниже действия.

## Откат миграции

Обратите внимание, что при откате миграции будет потеряно все содержимое, добавленное после миграции в общедоступные папки в Exchange Online с помощью клиентов или по электронной почте (для общедоступных папок, поддерживающих почту). Чтобы его сохранить, можно экспортировать содержимое общедоступной папки после миграции в PST-файл, который импортируется в локальные общедоступные папки после завершения отката.

1.  В своей локальной среде Exchange выполните указанную ниже команду, чтобы разблокировать общедоступные папки Exchange 2013. Обратите внимание, что разблокирование может занять несколько часов.
    
        Set-OrganizationConfig -PublicFolderMailboxesLockedForNewConnections:$false -PublicFolderMailboxesMigrationComplete:$false -PublicFoldersEnabled Local 

2.  В локальной среде Exchange верните для всех общедоступных папок, поддерживающих почту, значение `ExternalEmailAddress`, которое было изменено с помощью сценария SetMailPublicFolderExternalAddress.ps1 (см. *Шаг 8. Проверка и разблокировка общедоступных папок в Exchange Online* статьи [Использование пакетной миграции для переноса общедоступных папок Exchange 2013 в Exchange Online](use-batch-migration-to-migrate-exchange-2013-public-folders-to-exchange-online-exchange-online-help.md)). Чтобы получить исходные свойства для всех общедоступных папок, поддерживающих почту, можно использовать файл сводки, созданный сценарием, для определения внесенных изменений, или файл OnPrem\_MEPF.xml, сгенерированный ранее при пакетной миграции.

3.  В Exchange Online PowerShell выполните указанные ниже команды, чтобы удалить все общедоступные папки и почтовые ящики Exchange Online.
    
        Get-MailPublicFolder -ResultSize Unlimited | where {$_.EntryId -ne $null}| Disable-MailPublicFolder -Confirm:$false 
        Get-PublicFolder -GetChildren \ -ResultSize Unlimited | Remove-PublicFolder -Recurse -Confirm:$false
        $hierarchyMailboxGuid = $(Get-OrganizationConfig).RootPublicFolderMailbox.HierarchyMailboxGuid
        Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -ne $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
        Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -eq $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
        Get-Mailbox -PublicFolder -SoftDeletedMailbox | Remove-Mailbox -PublicFolder -PermanentlyDelete:$true

4.  Выполните следующую команду в среде Exchange Online, чтобы перенаправить трафик общедоступной папки обратно в локальную папку (Exchange 2013):
    
        Set-OrganizationConfig -PublicFoldersEnabled Remote

5.  Инструкции по перенастройке доступа к локальным общедоступным папкам для предоставления доступа пользователям Exchange Online см. в статье [Настройка общедоступных папок Exchange 2013 для гибридного развертывания](configure-exchange-2013-public-folders-for-a-hybrid-deployment-exchange-2013-help.md).

