---
title: 'Просмотр записей роли: Exchange 2013 Help'
TOCTitle: Просмотр записей роли
ms:assetid: d9bb0d14-db59-456c-8f50-a8d7f7323df9
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd351179(v=EXCHG.150)
ms:contentKeyID: 50489173
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Просмотр записей роли

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-03_

Каждая запись роли управления представляет один командлет или сценарий. Параметры, входящие в запись роли, определяют, какие параметры командлета или сценария будут доступны пользователям.

Идентификатор записи роли состоит из имени роли управления, с которой связана эта запись, и командлета или сценария, на которые ссылается запись роли. Дополнительные сведения о записях ролей в Microsoft Exchange Server 2013 см. в разделе [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md).

Необходимы сведения о других задачах управления, связанных с записями ролей? См. раздел [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Роли управления" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - В этом разделе используется конвейеризация, командлет **Format-List**, объекты и свойства. Дополнительные сведения об этих понятиях см. в следующих разделах:
    
      - [Конвейеризация](https://technet.microsoft.com/ru-ru/library/aa998260\(v=exchg.150\))
    
      - [Работа с выходными данными команды](working-with-command-output-exchange-2013-help.md)
    
      - [Структура данных](https://technet.microsoft.com/ru-ru/library/aa996386\(v=exchg.150\))

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Просмотр списка записей ролей

Для получения списка записей ролей можно использовать командлет **Get-ManagementRoleEntry**. При использовании командлета **Get-ManagementRoleEntry** необходимо указать значение, содержащее как имя роли, в состав которой входят записи роли, которые необходимо отобразить, так и имя командлета для отображаемой записи роли. Объединив имя роли и имя командлета с использованием подстановочного знака (\*), можно отобразить список определенных записей ролей или общий список.

Подробные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd335210\(v=exchg.150\)).

## Просмотр списка всех записей ролей в определенной роли

Чтобы просмотреть список записей ролей для определенной роли, используйте следующий синтаксис.

    Get-ManagementRoleEntry <role name>\*

В этом примере отображаются все записи роли для роли `Recipient Administrators`.

    Get-ManagementRole "Recipient Administrators\*"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd335210\(v=exchg.150\)).

## Просмотр списка ролей, в которых содержится определенная запись роли

Чтобы просмотреть список всех ролей, в которых содержится определенная запись роли, используйте следующий синтаксис.

    Get-ManagementRoleEntry *\<cmdlet name>

В этом примере отображаются все роли, содержащие запись роли **Set-Mailbox**.

    Get-ManagementRoleEntry *\Set-Mailbox

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd335210\(v=exchg.150\)).

## Просмотр целевого списка ролей, содержащих похожие записи ролей

Чтобы просмотреть список целевых ролей, содержащих командлеты с похожими именами, используйте следующий синтаксис.

    Get-ManagementRoleEntry *<partial role name>*\*<partial cmdlet name>*

В этом примере возвращается список записей ролей, содержащих строку `Mailbox`, которые входят в роли, содержащие в именах строку `Tier 1`.

    Get-ManagementRoleEntry "*Tier 1*\*Mailbox*"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd335210\(v=exchg.150\)).

## Просмотр отдельной записи роли

Чтобы просмотреть сведения об отдельной записи роли, используйте следующий синтаксис.

    Get-ManagementRoleEntry <role name>\<cmdlet name> | Format-List

В этом примере отображаются сведения о записи роли **Set-Mailbox** для роли `Recipient Administrators`.

    Get-ManagementRoleEntry "Recipient Administrators\Set-Mailbox" | Format-List

Если просматриваемая запись роли содержит слишком много параметров для отображения с помощью командлета **Format-List**, см. подраздел «Просмотр параметров отдельной записи роли» ниже в этом разделе.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd335210\(v=exchg.150\)).

## Просмотр параметров отдельной записи роли

Некоторые записи ролей содержат больше параметров, чем можно просмотреть при передаче результатов из командлета **Get-ManagementRoleEntry** в командлет **Format-List**. Если необходимо просмотреть все параметры записи роли, следует напрямую обратиться к свойству **Parameters** объекта записи роли.

Чтобы просмотреть параметры, хранящиеся в свойстве **Parameters** объекта записи роли, используйте следующий синтаксис.

    (Get-ManagementRoleEntry <role name>\<cmdlet name>).Parameters

В этом примере отображаются параметры записи роли **Set-Mailbox** для роли Mail Recipients.

    (Get-ManagementRoleEntry "Mail Recipients\Set-Mailbox").Parameters

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd335210\(v=exchg.150\)).

