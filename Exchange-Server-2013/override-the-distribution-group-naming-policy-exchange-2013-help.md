---
title: 'Переопределение политики именования групп рассылки: Exchange 2013 Help'
TOCTitle: Переопределение политики именования групп рассылки
ms:assetid: 9eb23fc9-3f59-4d09-9077-85c89a051ee0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ218685(v=EXCHG.150)
ms:contentKeyID: 50487254
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Переопределение политики именования групп рассылки

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-13_

Политика именования групп для групп рассылки применяется только к группам, созданным пользователями. Когда вы или другие администраторы используете центр администрирования Exchange (EAC) для создания групп рассылки, политика именования групп пропускается и не используется для имени группы.

Однако если вы используете командную консоль Exchange, чтобы создать или переименовать группу рассылки, политика именования групп применяется к группам, созданным администраторами, если не использовать параметр *IgnoreNamingPolicy* для переопределения политики именования групп.

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 2 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Группы рассылки" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

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


## Что необходимо сделать?

## Использование командной консоли для переопределения политики именования групп при создании группы

Для переопределения политики именования групп выполните следующую команду.

    New-DistributionGroup -Name <Group Name> -IgnoreNamingPolicy

Например, если политика именования групп вашей организации — **DG\_\<Имя группы\>\_Users**, используйте следующую команду для создания группы **Все администраторы**.

    New-DistributionGroup -Name "All Administrators" -IgnoreNamingPolicy

Когда Microsoft Exchange создает эту группу, он использует имя **Все администраторы** для параметров *Name* и *DisplayName*.

## Использование командной консоли для переопределения политики именования групп при переименовании группы

Для переопределения политики именования групп при переименовании группы в консоли выполните следующую команду.

    Set-DistributionGroup -Identity <Old Group Name> -Name <New Group Name> -DisplayName <New Group Name> -IgnoreNamingPolicy

Предположим, вы создавали политику именования групп поздно вечером, а утром поняли, что допустили ошибку в тексте префикса. На следующее утро вы видите, что уже была создана новая группа с неправильным префиксом. Можно исправить политику именования групп в EAC, но для этого необходимо использовать командную консоль, чтобы переименовать группу с неправильным именем. Выполните следующую команду.

    Set-DistributionGroup -Identity "Goverment_Contracts_NWRegion" -Name "Government_ContractEstimates_NWRegion" -DisplayName "Government_ContractEstimates_NWRegion" -IgnoreNamingPolicy

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Обязательно укажите параметр <em>DisplayName</em> при переименовании группы. Иначе старое имя будет отображаться в общей адресной книге в полях &quot;Кому&quot;, &quot;Копия&quot; и &quot;От&quot; в сообщениях электронной почты.</td>
</tr>
</tbody>
</table>


## Как проверить, что все получилось?

Чтобы убедиться в том, что группа рассылки успешно создана или переименована, а политика именования групп пропущена, выполните указанные ниже команды.

    Get-DistributionGroup <Name> | FL DisplayName

    Get-OrganizationConfig | FL DistributionGroupNamingPolicy

Если формат отображаемого имени группы отличается от того, который задает политика именования групп вашей организации, все сработало.

