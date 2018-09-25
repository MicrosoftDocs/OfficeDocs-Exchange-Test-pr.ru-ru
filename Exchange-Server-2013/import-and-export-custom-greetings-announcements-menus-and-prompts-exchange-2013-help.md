---
title: 'Импорт и экспорт настраиваемых приветствий, объявлений, меню и приглашений'
TOCTitle: Импорт и экспорт настраиваемых приветствий, объявлений, меню и приглашений
ms:assetid: e82da5d5-625f-4d8b-8d31-ac45513aacfd
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee681667(v=EXCHG.150)
ms:contentKeyID: 54652139
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Импорт и экспорт настраиваемых приветствий, объявлений, меню и приглашений

 

_**Применимо к:** Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:** 2015-04-08_

Можно импортировать и экспортировать записанные звуковые файлы для использования в абонентских группах и автосекретарях единой системы обмена сообщениями. Например, можно экспортировать и сохранить копию звукового файла при обновлении предыдущей версии Exchange. Также может понадобиться импортировать копию записанного звукового сигнала перед настройкой абонентской группы или автосекретаря.

Звуковые файлы используются в приведенных ниже целях.

  - В абонентских группах единой системы обмена сообщениями звуковые файлы используются для создания настраиваемых приветствий и информационных сообщений. Они воспроизводятся, когда пользователи голосового доступа к Outlook совершают вызовы на номер голосового доступа к Outlook.

  - В автосекретарях единой системы обмена сообщениями звуковые файлы используются для создания настраиваемых приветствий для нерабочих и рабочих часов, информационных сообщений, приглашений меню и навигационных меню. Они воспроизводятся, когда абоненты совершают вызовы автосекретарю единой системы обмена сообщениями.

Для создания настраиваемых приветствий, объявлений, меню и приглашений поддерживаются следующие форматы звуковых файлов.

  - WMA-файлы с кодировкой Windows Media Audio 9,2 - 96 Кбит/с/44 кГц/стерео, 1 проход, CBR (звукозапись Windows)

  - Windows Media Audio Voice 9 - 8 Кбит/с/8 кГц/моно и WAV-файлы, записанные с помощью аудиокодека линейного формата PCM (16 бит, 8 кГц).

Звуковые файлы, используемые в абонентских группах и автосекретарях единой системы обмена сообщениями, импортируются в системный почтовый ящик с именем {e0dc1c29-89c3-4034-b678-e6c29d823ed9} и экспортируются из этого системного почтового ящика. Звуковые файлы можно импортировать и экспортировать с помощью командлетов **Import-UMPrompt** и **Export-UMPrompt**.

Дополнительные задачи управления, связанные с абонентскими группами единой системы обмена сообщениями, см. в разделе [Процедуры плана телефонным единой системы обмена СООБЩЕНИЯМИ](um-dial-plan-procedures-exchange-2013-help.md).

Дополнительные задачи управления, связанные с автосекретарями единой системы обмена сообщениями, см. в разделе [Процедуры автосекретаря единой системы обмена сообщениями](https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/um-auto-attendant-procedures).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 3 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье записи "Абонентские группы единой системы обмена сообщениями" и "Автосекретари единой системы обмена сообщениями" в статье [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Перед выполнением этих процедур убедитесь, что автосекретарь единой системы обмена сообщениями создан. Дополнительные сведения см. в разделе [Создание автосекретаря единой системы обмена сообщениями](https://docs.microsoft.com/ru-ru/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant).

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Что нужно сделать

## Использование командной консоли для импорта настраиваемых приветствий, объявлений, меню и приглашений для абонентских групп и автосекретарей единой системы обмена сообщениями

В этом примере импортируется файл приветствия с именем welcomegreeting.wav из d:\\UMPrompts в абонентскую группу единой системы обмена сообщениями `MyUMDialPlan`.
```powershell
    [byte[]]$c = Get-content -Path "d:\UMPrompts\welcomegreeting.wav" -Encoding Byte -ReadCount 0
    Import-UMPrompt -UMDialPlan MyUMDialPlan -PromptFileName "welcomegreeting.wav" -PromptFileData $c
```
В этом примере импортируется файл приветствия с именем welcomegreeting.wav из d:\\UMPrompts в автосекретарь единой системы обмена сообщениями `MyUMAutoAttendant`.
```powershell
    [byte[]]$c = Get-content -Path "d:\UMPrompts\welcomegreeting.wav" -Encoding Byte -ReadCount 0
    Import-UMPrompt -UMAutoAttendant MyUMAutoAttendant -PromptFileName "welcomegreeting.wav" -PromptFileData $c
```
## Использование командной консоли для экспорта настраиваемых приветствий, объявлений, меню и приглашений для абонентских групп и автосекретарей единой системы обмена сообщениями

В этом примере экспортируется приветствие для абонентской группы единой системы обмена сообщениями `MyUMDialPlan`, которое сохраняется как файл welcomegreeting.wav.
```powershell
    $prompt = Export-UMPrompt -PromptFileName "customgreeting.wav�? -UMDialPlan MyUMDialPlan
    set-content -Path "d:\DialPlanPrompts\welcomegreeting.wav" -Value $prompt.AudioData -Encoding Byte
```
В этом примере экспортируется приветствие для рабочих часов для автосекретаря единой системы обмена сообщениями `MYUMAutoAttendant`, которое сохраняется как файл BusinessHoursWelcomeGreeting.wav.
```powershell
    $prompt = Export-UMPrompt -BusinessHoursWelcomeGreeting -UMAutoAttendant MyUMAutoAttendant
    set-content -Path "d:\UMPrompts\BusinessHoursWelcomeGreeting.wav" -Value $prompt.AudioData -Encoding Byte
```
