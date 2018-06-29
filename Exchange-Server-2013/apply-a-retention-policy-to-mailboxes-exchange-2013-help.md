---
title: 'Применение политики хранения к почтовым ящикам: Exchange 2013 Help'
TOCTitle: Применение политики хранения к почтовым ящикам
ms:assetid: 6ccc80db-d201-44f7-8d4b-473a89c14b2f
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd298052(v=EXCHG.150)
ms:contentKeyID: 50488194
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Применение политики хранения к почтовым ящикам

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2014-10-01_

Политики хранения позволяют группировать один или несколько тегов хранения и применять их к почтовым ящикам для включения параметров хранения сообщений. Почтовый ящик не может иметь более одной политики хранения.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.Caution(EXCHG.150).gif" title="Внимание!" alt="Внимание!" />Внимание!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Срок действия сообщений истекает на основании параметров, определенных тегами хранения, связанными с политикой. Эти параметры включают такие действия, как перемещение сообщений в архив или их окончательное удаление. Перед применением политики хранения к одному или нескольким почтовым ящикам рекомендуется проверить политику и каждый связанный с ней тег хранения.</td>
</tr>
</tbody>
</table>


Дополнительные задачи управления, связанные с управлением записями сообщений (MRM), см. в статье [Процедуры управления записями сообщений](messaging-records-management-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время выполнения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Применение политик хранения" в разделе [Политика обмена сообщениями и разрешения для соответствия требованиям](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

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

## Использование EAC для применения политики хранения к одному почтовому ящику

1.  Последовательно выберите пункты **Получатели** \> **Почтовые ящики**.

2.  В представлении списка выберите почтовый ящик, к которому вы хотите применить политику, и щелкните **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  В разделе **Почтовый ящик пользователя** щелкните **Функции почтового ящика**.

4.  В списке **Политика хранения** выберите политику, которую необходимо назначить почтовому ящику, и нажмите кнопку **Сохранить**.

## Использование EAC для применения политики хранения к нескольким почтовым ящикам

1.  Последовательно выберите пункты **Получатели** \> **Почтовые ящики**.

2.  В представлении списка воспользуйтесь клавишами SHIFT или CTRL, чтобы выбрать несколько почтовых ящиков.

3.  В области сведений щелкните **Дополнительные параметры**.

4.  В разделе **Политика хранения** щелкните **Обновить**.

5.  В разделе **Групповое назначение политики хранения** выберите необходимую политику хранения, а затем щелкните **Сохранить**.

## Использование консоли для применения политики хранения к одному почтовому ящику

В этом примере показано применение политики хранения RP-Finance к почтовому ящику пользователя Morris.

    Set-Mailbox "Morris" -RetentionPolicy "RP-Finance"

Дополнительные сведения о синтаксисе и параметрах см. в статье [Set-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123981\(v=exchg.150\)).

## Использование консоли для применения политики хранения к нескольким почтовым ящикам

В этом примере выполняется применение новой политики хранения New-Retention-Policy ко всем почтовым ящикам, для которых используется старая политика Old-Retention-Policy.

    $OldPolicy={Get-RetentionPolicy "Old-Retention-Policy"}.distinguishedName
    Get-Mailbox -Filter {RetentionPolicy -eq $OldPolicy} -Resultsize Unlimited | Set-Mailbox -RetentionPolicy "New-Retention-Policy"

В этом примере показано, как применить политику хранения RetentionPolicy-Corp для всех почтовых ящиков в организации Exchange.

    Get-Mailbox -ResultSize unlimited | Set-Mailbox -RetentionPolicy "RetentionPolicy-Corp"

В этом примере показано, как применить политику хранения RetentionPolicy-Finance для всех почтовых ящиков в финансовом подразделении.

    Get-Mailbox -OrganizationalUnit "Finance" -ResultSize Unlimited | Set-Mailbox -RetentionPolicy "RetentionPolicy-Finance"

Дополнительные сведения о синтаксисе и параметрах см. в разделах [Get-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123685\(v=exchg.150\)) и [Set-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123981\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться, что вы применили политику хранения, выполните командлет [Get-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123685\(v=exchg.150\)) для получения политики хранения почтового ящика или почтовых ящиков.

В этом примере возвращаются политики хранения для почтового ящика пользователя Morris.

    Get-Mailbox Morris | Select RetentionPolicy

Эта команда возвращает все почтовые ящики, имеющие политику хранения RP-Finance.

    Get-Mailbox -ResultSize unlimited | Where-Object {$_.RetentionPolicy -eq "RP-Finance"} | Format-Table Name,RetentionPolicy -Auto

