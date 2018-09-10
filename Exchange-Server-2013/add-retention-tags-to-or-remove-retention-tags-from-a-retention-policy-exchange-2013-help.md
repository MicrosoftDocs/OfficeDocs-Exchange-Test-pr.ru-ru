---
title: 'Добавление и удаление тегов хранения для политики хранения: Exchange 2013 Help'
TOCTitle: Добавление и удаление тегов хранения для политики хранения
ms:assetid: 3a5196ce-2764-453d-9bc1-5ec22d06b40d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd362328(v=EXCHG.150)
ms:contentKeyID: 50487847
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Добавление и удаление тегов хранения для политики хранения

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-02_

Можно добавить теги хранения в политику хранения при создании политики или после ее создания. Дополнительные сведения о создании политики хранения с одновременным добавлением тегов хранения см. разделе [Создание политики хранения](https://docs.microsoft.com/ru-ru/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy).

Политика хранения может содержать следующие теги хранения.

  - Один или несколько тегов политики хранения (RPT) для поддерживаемых папок по умолчанию

  - Один тег политики по умолчанию (DPT) с действием **Переместить в архив**

  - Один тег DPT с действием **Удалить и разрешить восстановление** или **Окончательно удалить**

  - Один тег DPT для голосовой почты

  - Любое количество личных тегов

Дополнительные сведения о тегах хранения см. в статье [Теги хранения и политики хранения](retention-tags-and-retention-policies-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время выполнения: 10 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Управление записями сообщений" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

  - Теги хранения не применяются к почтовому ящику до тех пор, пока они не будут связаны с политикой хранения и помощник для управляемых папок не обработает почтовый ящик. Сведения о запуске помощника по обслуживанию управляемых папок для обработки почтового ящика см. в статье [Настройка помощника для управляемых папок](configure-the-managed-folder-assistant-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Что необходимо сделать?

## Использование Центра администрирования Exchange для добавления или удаления тегов хранения

1.  Выберите пункты **Управление соответствием требованиям** и **Политики хранения**.

2.  В представлении списка выберите политику хранения, в которую нужно добавить теги хранения, и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  В окне **Политика хранения** используйте следующие параметры:
    
      - **Добавить** ![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления")   Нажмите эту кнопку, чтобы добавить тег хранения в политику.
    
      - **Удалить** ![Значок "Удалить"](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Значок \"Удалить\"") Выберите тег из списка и нажмите эту кнопку, чтобы удалить его из политики.

## Добавление или удаление тегов хранения с помощью консоли

В этом примере показано добавление тегов VPs-Default, VPs-Inbox и VPs-DeletedItems в политику хранения RetPolicy-VPs, которая еще не имеет тегов хранения, связанных с ней.

> [!CAUTION]  
> Если политика уже имеет теги хранения, связанные с ней, выполнение этой команды заменит существующие теги.


    Set-RetentionPolicy -Identity "RetPolicy-VPs" -RetentionPolicyTagLinks "VPs-Default","VPs-Inbox","VPs-DeletedItems"

В этом примере показано, как добавить тег хранения VPs-DeletedItems в политику хранения RetPolicy-VPs, с которой связаны другие теги хранения.

    $TagList = (Get-RetentionPolicy "RetPolicy-VPs").RetentionPolicyTagLinks
    $TagList.Add((Get-RetentionPolicyTag 'VPs-DeletedItems').DistinguishedName)
    Set-RetentionPolicy "RetPolicy-VPs" -RetentionPolicyTagLinks $TagList

В этом примере показано удаление тега хранения VPs-Inbox из политики хранения RetPolicy-VPs.

    $TagList = (Get-RetentionPolicy "RetPolicy-VPs").RetentionPolicyTagLinks
    $TagList.Remove((Get-RetentionPolicyTag 'VPs-Inbox').DistinguishedName)
    Set-RetentionPolicy "RetPolicy-VPs" -RetentionPolicyTagLinks $TagList

Дополнительные сведения о синтаксисе и параметрах см. в разделах [Set-RetentionPolicy](https://technet.microsoft.com/ru-ru/library/dd335196\(v=exchg.150\)) и [Get-RetentionPolicy](https://technet.microsoft.com/ru-ru/library/dd298086\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы проверить успешность добавления или удаления тега хранения из политики, используйте командлет [Get-RetentionPolicy](https://technet.microsoft.com/ru-ru/library/dd298086\(v=exchg.150\)) для проверки свойства *RetentionPolicyTagLinks*.

Этот пример использует командлет **Get-RetentionPolicy** для получения тегов хранения, добавленных в политику "Default MRM", и передает их в командлет **Format-Table** для вывода свойства имени каждого тега.

    (Get-RetentionPolicy "Default MRM Policy").RetentionPolicyTagLinks | Format-Table name

