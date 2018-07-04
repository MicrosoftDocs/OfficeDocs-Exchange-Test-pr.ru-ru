---
title: 'Включение или отключение Exchange ActiveSync для почтового ящика: Exchange 2013 Help'
TOCTitle: Включение или отключение Exchange ActiveSync для почтового ящика
ms:assetid: dcf7c05b-b1b9-4b0f-800d-fec9f2ddc9e4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124809(v=EXCHG.150)
ms:contentKeyID: 50556494
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Включение или отключение Exchange ActiveSync для почтового ящика

 

_**Применимо к:** Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:** 2012-11-13_

Можно использовать EAC или командную консоль для включения и отключения Microsoft Exchange ActiveSync для почтового ящика пользователя. Exchange ActiveSync является клиентским протоколом, который позволяет пользователям синхронизировать мобильные устройства с почтовым ящиком Exchange. Exchange ActiveSync включается по умолчанию при создании почтового ящика пользователя. Дополнительные сведения см. в разделе [Служба Exchange ActiveSync](exchange-activesync-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 2 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись «Параметры Exchange ActiveSync» в разделе [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Что необходимо сделать?

## Использование EAC для включения и отключения Exchange ActiveSync

1.  В центре администрирования Exchange перейдите к разделу **Получатели** \> **Почтовые ящики**.

2.  Выберите в списке почтовых ящиков пользователей тот ящик, для которого требуется включить или выключить Exchange ActiveSync, а затем — команду **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице свойств почтового ящика нажмите кнопку **Функции почтового ящика**.

4.  В разделе **Мобильные устройства** выполните одно из следующих действий.
    
      - Чтобы отключить Exchange ActiveSync, щелкните **Отключить Exchange ActiveSync**.
        
        Будет выведено предупреждение с запросом на подтверждение выключения Exchange ActiveSync. Нажмите кнопку **Да**.
    
      - Чтобы включить Exchange ActiveSync, щелкните **Включить Exchange ActiveSync**.

5.  Нажмите кнопку **Сохранить**, чтобы сохранить изменения.

> [!NOTE]  
> Можно включать и отключать Exchange ActiveSync для нескольких почтовых ящиков, используя функцию массового редактирования в EAC. Дополнительные сведения о том, как это сделать, можно найти в разделе &quot;Массовое редактирование пользовательских почтовых ящиков&quot; в разделе <a href="manage-user-mailboxes-exchange-2013-help.md">Управление почтовыми ящиками пользователей</a>.


## Использование командной консоли для включения и отключения Exchange ActiveSync

В этом примере Exchange ActiveSync отключается для почтового ящика Yan Li.

    Set-CASMailbox -Identity "Yan Li" -ActiveSyncEnabled $false

Этот пример включает Exchange ActiveSync для почтового ящика Elly Nkya.

    Set-CASMailbox -Identity Ellyn@contoso.com -ActiveSyncEnabled $true

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-CASMailbox](https://technet.microsoft.com/ru-ru/library/bb125264\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы проверить, успешно ли включено или выключено Exchange ActiveSync для почтового ящика пользователя, выполните одно из следующих действий.

  - В EAC откройте раздел **Получатели** \> **Почтовые ящики**, выберите почтовый ящик и нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

  - На странице свойств почтового ящика нажмите кнопку **Функции почтового ящика**.

  - В разделе **Мобильные устройства** проверьте, включено или выключено Exchange ActiveSync.

Или

  - Выполните в командной консоли следующую команду.
    
        Get-CASMailbox <identity>
    
    Если Exchange ActiveSync включено, значение свойства *ActiveSyncEnabled* равно `True`. Если Exchange ActiveSync отключено, значение равно `False`.

