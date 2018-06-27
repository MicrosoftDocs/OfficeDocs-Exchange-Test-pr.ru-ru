---
title: 'Удаление правила защиты Outlook: Exchange 2013 Help'
TOCTitle: Удаление правила защиты Outlook
ms:assetid: 569fc3be-b269-43f5-8797-73ab0691e685
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee633467(v=EXCHG.150)
ms:contentKeyID: 50488263
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Удаление правила защиты Outlook

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2016-12-09_

Правила защиты Microsoft Outlook можно защищать сообщения с помощью управления правами на доступ к данным (IRM), применив шаблон [Службы управления правами Active Directory (AD RMS)](https://technet.microsoft.com/en-us/library/hh831364.aspx) в Outlook 2010 перед отправкой. Чтобы применить правило защиты Outlook, можно отключить правило. Удаление правило защиты Outlook удаляет определение правила из Active Directory.

Дополнительные сведения об управленческих задачах, связанных с IRM, см. в разделе [Сведения о процедуры управления правами](information-rights-management-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время выполнения: 1 минута.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Защита прав" в разделе [Политика обмена сообщениями и разрешения для соответствия требованиям](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Вы можете использовать центр администрирования Exchange (EAC) для удаления правил защиты Outlook. Необходимо использовать командную консоль.

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

## Удаление правила защиты Outlook с помощью командной консоли Exchange

В этом примере удаляется правило защиты Outlook OPR-DG-Finance.

    Remove-OutlookProtectionRule -Identity "OPR-DG-Finance"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-OutlookProtectionRule](https://technet.microsoft.com/ru-ru/library/dd297961\(v=exchg.150\)).

## Удаление всех правил защиты Outlook с помощью командной консоли Exchange

В этом примере удаляются все правила защиты Outlook в организации Exchange.

    Get-OutlookProtectionRule | Remove-OutlookProtectionRule

Дополнительные сведения о синтаксисе и параметрах см. в разделах [Get-OutlookProtectionRule](https://technet.microsoft.com/ru-ru/library/dd298004\(v=exchg.150\)) и [Remove-OutlookProtectionRule](https://technet.microsoft.com/ru-ru/library/dd297961\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться в том, что вы успешно удалили правило защиты Outlook, используйте командлет [Get-OutlookProtectionRule](https://technet.microsoft.com/ru-ru/library/dd298004\(v=exchg.150\)) для получения списка правил защиты Outlook. Пример получения правил защиты Outlook см. в разделе [Examples](https://technet.microsoft.com/ru-ru/dd298004\(exchg.150\)#examples) в описании **Get-OutlookProtectionRule**.

