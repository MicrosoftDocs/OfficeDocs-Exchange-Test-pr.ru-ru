---
title: 'Просмотр действующих разрешений: Exchange 2013 Help'
TOCTitle: Просмотр действующих разрешений
ms:assetid: ae6cb7cf-f998-44a6-a69a-02ad736c8260
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd638167(v=EXCHG.150)
ms:contentKeyID: 50488892
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Просмотр действующих разрешений

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-09_

Разрешения в Microsoft Exchange Server 2013 предоставляются с помощью ролей управления, которые назначаются группам ролей управления, политикам назначения ролей управления, универсальным группам безопасности или напрямую пользователям. Пользователи получают разрешения, если являются членами групп ролей или универсальных групп безопасности, а также если для них назначены политики назначения ролей.

Большинство разрешений предоставляется на основе членства в группе ролей или назначения политик пользователям. Хотя использование групп ролей и политик назначения упрощает предоставление разрешений большому количеству пользователей, можно и не знать, кто является членом группы ролей или кому была назначена политика назначения. В этом случае окажется полезным переключатель *GetEffectiveUsers* для командлета **Get-ManagementRoleAssignment**. С его помощью можно просмотреть, каким пользователям предоставлены разрешения, посредством назначенных для этих пользователей групп ролей, политик назначений и универсальных групп безопасности.

Переключатель *GetEffectiveUsers* используется в командлете **Get-ManagementRoleAssignment**, если указан параметр *Role*. При указании этого переключателя с определенной ролью при помощи командлета **Get-ManagementRoleAssignment** выполняется проверка всех назначенных роли объектов, то есть групп ролей, политик назначения и универсальных групп безопасности. После этого выводится список членов каждого объекта.

> [!NOTE]  
> Переключатель <em>GetEffectiveUser</em> не отображает тех пользователей, которые являются членами связанной внешней группы ролей. Если найдена связанная группа ролей, то вместо списка пользователей отображаются <strong>все члены связанной группы</strong>. Дополнительные сведения о разрешениях в нескольких лесах см. в разделе <a href="understanding-multiple-forest-permissions-exchange-2013-help.md">Общие сведения о разрешениях для нескольких лесов</a>.


Дополнительные сведения о ролях управления, группах ролей и политиках назначения см. в разделе [Общие сведения об управлении доступом на основе ролей](understanding-role-based-access-control-exchange-2013-help.md). Дополнительные сведения о назначениях ролей управления см. в разделе [Общие сведения о назначениях ролей управления](understanding-management-role-assignments-exchange-2013-help.md).

Необходимы сведения о других задачах управления, связанных с управлением разрешениями? См. раздел [Разрешения](permissions-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Записи «Группы ролей» или «Политика назначения ролей» в разделе [Разрешения управления ролями](role-management-permissions-exchange-2013-help.md).

  - Процедуры, описанные в этом разделе, можно выполнить только в командной консоли Exchange. Невозможно использовать центр администрирования Exchange для просмотра эффективных разрешений.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной консоли для получения списка всех действующих пользователей

Чтобы отобразить список всех пользователей, которым ролью управления предоставлены разрешения, используйте следующий синтаксис.

```powershell
Get-ManagementRoleAssignment -Role <role name> -GetEffectiveUsers
```

В этом примере отображается список пользователей, которые имеют разрешения, предоставленные ролью «Mail Recipients».

```powershell
Get-ManagementRoleAssignment -Role "Mail Recipients" -GetEffectiveUsers
```

Если нужно изменить свойства, которые возвращаются в списке, или экспортировать список в файл данных с разделителями-запятыми (CSV), см. подраздел Use the Shell to customize output and display it далее в этом разделе.

Подробные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Использование командой консоли для поиска определенного пользователя в определенной роли

Чтобы найти определенного пользователя, которому были предоставлены разрешения определенной роли управления, необходимо использовать командлет **Get-ManagementRoleAssignment**, который позволяет получить список всех эффективных пользователей, а затем передать выходные данные этого командлета в командлет **Where**. Командлет **Where** отфильтровывает выходные данные и возвращает только указанного пользователя. Используйте следующий синтаксис.
```powershell
    Get-ManagementRoleAssignment -Role <role name> -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "<name of user>" }
```
В этом примере выполняется поиск пользователя David Strome в роли Journaling.
```powershell
    Get-ManagementRoleAssignment -Role Journaling -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "David Strome" }
```
Сведения об изменении возвращаемых свойств в списке или экспорте списка в файл в формате CSV см. в подразделе Use the Shell to customize output and display it далее в этом разделе.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Использование командой консоли для нахождения определенного пользователя во всех ролях

Чтобы узнать о всех ролях, разрешения которых были предоставлены пользователю, следует использовать командлет **Get-ManagementRoleAssignment**, позволяющий получить всех действующих пользователей во всех ролях, а затем передать выходные данные в командлет **Where**. Командлет **Where** фильтрует выходные данные и возвращает только те назначения ролей, в соответствии с которыми этому пользователю были предоставлены разрешения.
```powershell
    Get-ManagementRoleAssignment -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "<name of user>" }
```
В этом примере выполняется поиск всех назначений ролей, в соответствии с которыми были предоставлены разрешения пользователю Kim Akers.

```powershell
Get-ManagementRoleAssignment -GetEffectiveUsers | Where {     Get-ManagementRoleAssignment -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "Kim Akers" }.EffectiveUserName -Eq "Kim Akers" }
```

Сведения об изменении списка возвращаемых свойств или экспорте списка в файл в формате CSV см. в подразделе Use the Shell to customize output and display it далее в этом разделе.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Использование командной консоли для настройки и отображения выходных данных

В выходных данных командлета **Get-ManagementRoleAssignment** по умолчанию могут не содержаться нужные сведения. Выходные данные командлета содержат различные свойства, которые можно просмотреть. Ниже перечислены некоторые свойства, которые могут оказаться полезными.

  - **EffectiveUserName**   Имя пользователя.

  - **Role**   Роль, предоставившая разрешения.

  - **RoleAssigneeName**   Группа ролей, политика назначения или универсальная группа безопасности, предоставленная роли и содержащая пользователя в свойстве `EffectiveUserName`.

  - **RoleAssigneeType**   Указывает объект назначения роли — группа ролей, политика назначения, универсальная группа безопасности или пользователь.

  - **AssignmentMethod**   Указывает, является ли назначение роли объекту прямым или косвенным.

  - **CustomRecipientWriteScope**   Настраиваемая область записи получателей (если применимо), которая была применена к назначению роли при его создании. Указанная в этом свойстве область имеет приоритет над неявной областью записи получателей, указанной в свойстве `RecipientWriteScope`.

  - **CustomConfigWriteScope**   Настраиваемая область записи конфигураций (если применимо), которая была применена к назначению роли при его создании. Указанная в этом свойстве область имеет приоритет над неявной областью записи конфигураций, указанной в свойстве `ConfigWriteScope`.

  - **RecipientReadScope**   Указывает неявную область чтения получателей, которая применена к этой роли.

  - **RecipientWriteScope**   Указывает неявную область записи получателей, которая применена к этой роли.

  - **ConfigReadScope**   Указывает неявную область чтения конфигураций, которая применена к этой роли.

  - **ConfigWriteScope**   Указывает неявную область записи конфигураций, которая применена к этой роли.

Чтобы выбрать свойства, которые следует отображать в списке, используйте команды, аналогичные тем, которые использовались в разделах Use the Shell to list all effective users, Use the Shell to find a specific user on a role и Use the Shell to find a specific user on all roles. Отличие заключается в том, что результаты этих команд передаются в командлеты **Format-Table** или **Select-Object**. Командлет **Format-Table** используется для вывода списка результатов на экран. Командлет **Select-Object** используется для вывода списка результатов в CSV-файл.

Оба командлета позволяют определить свойства, которые будут отображаться в нужном порядке. Командлет **Format-Table** предоставляет больше возможностей при выводе результатов на экран, а командлет **Select-Object** не изменяет выходные данные, что хорошо подходит для передачи списка в CSV-файл.

Дополнительные сведения о командлетах **Format-Table** и **Select-Object** см. в разделе [Работа с выходными данными команды](working-with-command-output-exchange-2013-help.md).

## Вывод на экран пользовательского списка

1.  Выберите отображаемые сведения и найдите связанную команду в одной из следующих процедур.
    
      - Use the Shell to list all effective users
    
      - Use the Shell to find a specific user a role
    
      - Use the Shell to find a specific user on all roles

2.  Выберите свойства, которые необходимо включить в список.

3.  Используйте следующий синтаксис для просмотра списка.
    ```command line
        <command to retrieve list > | Format-Table <property 1>, <property 2>, <property ...>
    ```
\+В этом примере показано, как найти Сергея Озерова для всех ролей и отобразить свойства `EffectiveUserName`, `Role`, `CustomRecipientWriteScope` и `CustomConfigWriteScope`.
```powershell
    Get-ManagementRoleAssignment -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "David Strome" } | Format-Table EffectiveUserName, Role, CustomRecipientWriteScope, CustomConfigWriteScope
```
Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

## Вывод пользовательского списка в CSV-файл

Чтобы экспортировать список в CSV-файл, необходимо передать результаты выполнения команды **Get-ManagementRoleAssignment** из соответствующей процедуры, приведенной выше, в командлет **Select-Object**. Затем выходные данные командлета **Select-Object** передаются в командлет **Export-CSV**, который сохраняет выходные данные с разделителями-запятыми в указанный файл.

1.  Выберите отображаемые сведения и найдите связанную команду в одной из следующих процедур.
    
      - Use the Shell to list all effective users
    
      - Use the Shell to find a specific user a role
    
      - Use the Shell to find a specific user on all roles

2.  Выберите свойства, которые необходимо включить в список.

3.  Используйте следующий синтаксис для экспорта списка в CSV-файл.
    ```command line
        <command to retrieve list > | Select-Object <property 1>, <property 2>, <property ...> | Export-CSV <filename>
    ```
\+В этом примере показано, как найти Сергея Озерова для всех ролей и отобразить свойства `EffectiveUserName`, `Role`, `CustomRecipientWriteScope` и `CustomConfigWriteScope`.
```powershell
    Get-ManagementRoleAssignment -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "David Strome" } | Select-Object EffectiveUserName, Role, CustomRecipientWriteScope, CustomConfigWriteScope | Export-CSV c:\output.csv
```
Теперь можно просмотреть CSV-файл в соответствующем приложении.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-ManagementRoleAssignment](https://technet.microsoft.com/ru-ru/library/dd351024\(v=exchg.150\)).

