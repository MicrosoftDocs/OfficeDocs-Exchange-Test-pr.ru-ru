---
title: 'Изменение записи роли: Exchange 2013 Help'
TOCTitle: Изменение записи роли
ms:assetid: 5aa4f39c-16a4-4815-ac4f-2cdcfa2b3ee1
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd298005(v=EXCHG.150)
ms:contentKeyID: 50488284
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Изменение записи роли

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-03_

Каждая запись роли управления в роли управления представляет собой отдельный командлет. При добавлении записи роли в роль управления можно регулировать параметры, доступные в этом командлете, путем добавления параметров в эту запись роли или их удаления. Дополнительные сведения о записях ролей управления в Microsoft Exchange Server 2013 см. в разделе [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md).

Изменение записей роли во встроенных ролях управления невозможно.

> [!NOTE]  
> В этом разделе не содержатся сведения по изменению записей роли управления с незаданной областью в роли управления с незаданной областью. Дополнительные сведения об изменении записей роли управления с незаданной областью см. в разделе <a href="create-a-role-exchange-2013-help.md">Создание роли</a>.


> [!CAUTION]  
> Для добавления параметров в запись роли или их удаления необходимо использовать параметры <em>AddParameter</em> или <em>RemoveParameter</em>. Если опустить параметр <em>AddParameter</em> или <em>RemoveParameter</em> при выполнении командлета <strong>Set-ManagementRoleEntry</strong>, в запись роли будут включены только параметры, указанные с помощью параметра <em>Parameters</em>. Все остальные параметры будут удалены из записи роли.


Необходимы сведения о других задачах управления, связанных с ролями? см. в разделе [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Роли управления" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - При необходимости добавить параметры к записи роли добавляемые параметры должны существовать в записи роли родительской роли. Эти параметры также должны существовать в указанном командлете.

  - Чтобы удалить параметры из записи роли, удаляемые параметры не должны существовать в записи роли любой из дочерних ролей. Необходимо удалить эти параметры из записей роли дочерних ролей. Чтобы удалить параметры из записей роли всех дочерних ролей, используйте процедуру "Использование командной консоли Exchange для удаления одного или нескольких параметров из записи роли", описанную ниже в этом разделе.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Использование командной консоли Exchange для добавления одного или нескольких параметров для записи роли

Чтобы добавить параметры к записи роли, необходимо указать эти параметры с помощью параметра *Parameters*. Затем требуется указать параметр *AddParameter*, чтобы указать на необходимость процедуры добавления.

Чтобы добавить параметры к записи роли, используйте следующий синтаксис.

    Set-ManagementRoleEntry <role name>\<cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...> -AddParameter

В этом примере добавляются параметры *EmailAddresses* и *Type* в командлет **Set-Mailbox** в роли администраторов получателя.

    Set-ManagementRoleEntry "Recipient Administrators\Set-Mailbox" -Parameters EmailAddresses, Type -AddParameter

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd351162\(v=exchg.150\)).

## Использование командной консоли Exchange для удаления одного или нескольких параметров из записи роли

Чтобы удалить параметры из записи роли, необходимо указать эти параметры с помощью параметра *Parameters*. Затем требуется указать параметр *RemoveParameter*, чтобы указать на необходимость процедуры удаления.

Чтобы удалить параметры из записи роли, используйте следующий синтаксис.

    Set-ManagementRoleEntry <role name>\<cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...> -RemoveParameter

В этом примере удаляются параметры *Port*, *ProtocolLoggingLevel* и *SmartHostAuthMechanism* из командлета **Set-SendConnector** в роли администраторов сервера 1 уровня.

    Set-ManagementRoleEntry "Tier 1 Server Administrators\Set-SendConnector" -Parameters Port, ProtocolLoggingLevel, SmartHostAuthMechanism -RemoveParameter

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd351162\(v=exchg.150\)).

## Использование командной консоли Exchange для удаления всех параметров из записи роли

Чтобы удалить все параметры из записи роли, необходимо указать значение `$Null` для параметра *Parameters*. Параметр *RemoveParameters* является необязательным.

Удаление всех параметров из записи роли наиболее полезно при необходимости сделать доступными в командлете только определенные параметры и исключить все остальные параметры. Чтобы запретить для роли доступ к командлету, полностью удалите из роли связанную запись роли вместо удаления только параметров. Дополнительные сведения о способе удаления записи роли из роли см. в разделе [Удаление записи роли из роли](remove-a-role-entry-from-a-role-exchange-2013-help.md).

> [!CAUTION]  
> Операции удаления отменить невозможно. Если из записи роли ошибочно удалены все параметры, их можно повторно добавить вручную.


Чтобы удалить все параметры из записи роли, используйте следующий синтаксис.

    Set-ManagementRoleEntry <role name>\<cmdlet> -Parameters $Null 

В этом примере удаляются все параметры из командлета **Set-CASMailbox** в роли администраторов получателя.

    Set-ManagementRoleEntry "Recipient Administrators\Set-CASMailbox" -Parameters $Null 

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd351162\(v=exchg.150\)).

## Использование командной консоли Exchange для применения определенного набора параметров

Чтобы включить в запись роли только определенный набор параметров, укажите только параметр *Parameters*. Не добавляйте параметры *AddParameter* или *RemoveParameter*. При указании только параметра *Parameters* в запись роли включаются только параметры, указанные в команде. Все другие параметры удаляются.

Чтобы указать определенный набор параметров, используйте следующий синтаксис.

    Set-ManagementRoleEntry <role name>\<cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...>

В этом примере добавляются параметры *Identity*, *DisplayName*, *MissedCallNotificationEnabled* и *PersonalAuthAttendantEnabled* в командлет **Set-UMMailbox** в роли получателей электронной почты в Сиэтле.

    Set-ManagementRoleEntry "Seattle Mail Recipients\Set-UMMailbox" -Parameters Identity, DisplayName, MissedCallNotificationEnabled, PersonalAutoAttendantEnabled

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-ManagementRoleEntry](https://technet.microsoft.com/ru-ru/library/dd351162\(v=exchg.150\)).

