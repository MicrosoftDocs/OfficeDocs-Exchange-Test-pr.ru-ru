﻿---
title: 'Удаление роли: Exchange 2013 Help'
TOCTitle: Удаление роли
ms:assetid: 2fb6f453-f37a-4636-8353-3f9927f81298
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd335178(v=EXCHG.150)
ms:contentKeyID: 50487752
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Удаление роли

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-03_

Роли управления, которые больше не требуются, можно удалять из организации. Удалять можно только созданные пользователем роли управления. Невозможно удалить встроенные роли управления. Дополнительные сведения о ролях управления в Microsoft Exchange Server 2013 см. в разделе [Общие сведения о ролях управления](understanding-management-roles-exchange-2013-help.md).

Необходимы сведения о других задачах управления, связанных с ролями? см. в разделе [Дополнительные разрешения](advanced-permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Роли управления" в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Для выполнения этих процедур необходимо использовать командную консоль Exchange.

  - Перед удалением роли управления необходимо удалить все назначения этой роли. Дополнительные сведения об удалении назначения роли см. в разделе [Удалить роль из пользователя или универсальной группы безопасности](remove-a-role-from-a-user-or-usg-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Удаление роли управления без дочерних ролей

Чтобы удалить роль без дочерних ролей, используйте следующую синтаксическую конструкцию.

```powershell
Remove-ManagementRole <role name>
```

В этом примере показано, как удалить роль администраторов сервера в Сиэтле.

```powershell
Remove-ManagementRole "Seattle Server Administrators"
```

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351170\(v=exchg.150\)).

## Удаление роли управления с дочерними ролями

Если роль, которую необходимо удалить, имеет дочерние роли, необходимо также удалить эти роли. При попытке удалить роль, имеющую дочерние роли, отображается сообщение об ошибке, если не используется параметр *Recurse*. Если при удалении роли задан параметр *Recurse*, указанная роль будет удалена со всеми ее дочерними ролями.

> [!CAUTION]  
> Если задан параметр <em>Recurse</em>, удаляются также все дочерние роли указанной роли, которую необходимо удалить. Проверьте, какие именно роли будут удалены, прежде чем запускать эту команду.


Чтобы убедиться, что будут удалены только те роли, которые необходимо удалить, используйте с командой параметр *WhatIf*, позволяющий проверить ее правильность. Используйте следующий синтаксис.

```powershell
Remove-ManagementRole <role name> -Recurse -WhatIf
```

При использовании параметра *WhatIf* команда выполняется без фиксации каких-либо изменений и при этом сообщается о тех ролях, которые были бы удалены. Дополнительные сведения о параметре *WhatIf* см. в разделе [Параметры WhatIf, Confirm и ValidateOnly](whatif-confirm-and-validateonly-switches-exchange-2013-help.md).

После подтверждения правильности выбора ролей, которые необходимо удалить, выполните ту же команду без параметра *WhatIf*. В этом примере показано, как удалить роль администраторов в Лондоне и всех ее дочерних ролей.

```powershell
Remove-ManagementRole "London Administrators" -Recurse
```

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351170\(v=exchg.150\)).

## Удаление роли управления с незаданной областью

Чтобы удалить роль управления с незаданной областью, можно использовать процедуры, которые описаны в этом разделе в подразделах Удаление роли управления без дочерних ролей и Удаление роли управления с дочерними ролями. Единственное отличие заключается в том, что при удалении роли с незаданной областью при запуске команды необходимо задать параметр *UnScopedTopLevel*. В этом примере показано, как удалить роль с незаданной областью и все ее дочерние роли.

```powershell
Remove-ManagementRole "Custom IT Scripts" -Recurse -UnScopedTopLevel
```

При удалении других ролей необходимо использовать параметр *WhatIf*, чтобы проверить правильность выбора ролей для удаления.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-ManagementRole](https://technet.microsoft.com/ru-ru/library/dd351170\(v=exchg.150\)).

