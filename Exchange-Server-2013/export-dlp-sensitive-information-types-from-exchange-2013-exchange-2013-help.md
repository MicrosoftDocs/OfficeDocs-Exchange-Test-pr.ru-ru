---
title: 'Экспорт типов конфиденциальных сведений DLP из Exchange 2013: Exchange 2013 Help'
TOCTitle: Экспорт типов конфиденциальных сведений DLP из Exchange
ms:assetid: 8f02fbc2-dd1c-4276-be1a-517a43fe39b2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn479225(v=EXCHG.150)
ms:contentKeyID: 59636079
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Экспорт типов конфиденциальных сведений DLP из Exchange 2013

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2016-05-04_

Можно просмотреть или изменить сведения в рамках политики защиты от потери данных без использования командлетов Командная консоль Exchange или Центр администрирования Exchange (EAC), экспорт политик, сохранения в виде XML-файла и изменения, XML-файл. Как правило будет затем импортировать XML-файл обратно в Exchange. Таким образом политик можно редактировать вне зависимости от Exchange. Тем не менее они должны соответствовать требованиям определенный формат, также называется схемы XML для нормальной работы.

Дополнительные задачи управления, связанные с политиками DLP, приведены в разделе [Управление политиками защиты от потери данных](manage-dlp-policies-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 15 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Предотвращение потери данных (DLP)" в разделе [Политика обмена сообщениями и разрешения для соответствия требованиям](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

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


## Что необходимо сделать?

EAC не поддерживает экспорт политик или шаблонов DLP во внешний файл. Используйте Командная консоль Exchange для выполнения этой задачи.

## Использование Командная консоль Exchange для экспорта типов конфиденциальной информации DLP

В этом примере показан экспорт всех типов конфиденциальных сведений, подпадающих под действие политики защиты от потери данных, и их атрибутов в XML-файл по адресу C:\\My Documents\\exportedInformationTypes.xml. Рекомендуем создать резервную копию коллекции этих типов сведений. Один из способов — экспортировать и затем скопировать и переименовать XML-файл.

1.  Откройте Командная консоль Exchange.

2.  Введите **Get-ClassificationRuleCollection**, чтобы типы конфиденциальных данных организации на экране. Если вы не создавали собственные типы конфиденциальных сведений, вы увидите только встроенную коллекцию таких сведений по умолчанию, помеченную как "Пакет правил Майкрософт".

3.  Сохраните типы конфиденциальных сведений в переменной, введя команду **$ruleCollections = Get-ClassificationRuleCollection**.

4.  Теперь создайте форматированный XML-файл со всеми данными, введя команду **Set-Content -path "C:\\My Documents\\exportedRules.xml" -Encoding Byte -Value $ruleCollections.SerializedClassificationRuleCollection**.

После этого вы сможете изменить XML-файл, чтобы скорректировать политики. Сведения о настройке встроенных типов конфиденциальных данных см. в статье [Настройка встроенных типов конфиденциальных сведений DLP](customize-the-built-in-dlp-sensitive-information-types-exchange-2013-help.md). Сведения об импорте политик в Exchange см. в статье [Импорт настраиваемого шаблона политики защиты от потери данных из файла](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md).

## Дополнительные сведения

[Что позволяют искать типы конфиденциальной информации в Exchange](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md)

[Настройка встроенных типов конфиденциальных сведений DLP](customize-the-built-in-dlp-sensitive-information-types-exchange-2013-help.md)

[Импорт настраиваемого шаблона политики защиты от потери данных из файла](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md)

