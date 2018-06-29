---
title: 'Удаление политики почтовых ящиков Outlook Web App с сервера Exchange: Exchange 2013 Help'
TOCTitle: Удаление политики почтовых ящиков Outlook Web App с сервера Exchange
ms:assetid: edab7bac-b62c-4b82-8f21-dcac77cf0e8f
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd351239(v=EXCHG.150)
ms:contentKeyID: 50489452
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Удаление политики почтовых ящиков Outlook Web App с сервера Exchange

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2013-03-15_

Политику почтовых ящиков МайкрософтOutlook Web App можно удалить из организации Exchange, используя Центр администрирования Exchange или командную консоль.

Дополнительные сведения о задачах управления, связанных с политиками почтовых ящиков Outlook Web App, см. в разделе [Политики почтовых ящиков Outlook Web App](outlook-web-app-mailbox-policies-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 3 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Политики почтовых ящиков Outlook Web App" в разделе [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

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

## Использование Центра администрирования Exchange для удаления политики почтовых ящиков Outlook Web App

1.  В Центре администрирования Exchange выберите пункты **Разрешения** \> **Политики Outlook Web App**.

2.  В области результатов выберите политику почтовых ящиков, которую требуется удалить.

3.  Нажмите кнопку **Удалить**.

4.  В окне подтверждения нажмите кнопку **Да**, чтобы удалить политику почтовых ящиков, или кнопку **Нет**, чтобы отменить удаление.

## Использование командной консоли для удаления политики почтовых ящиков Outlook Web App

В этом примере удаляется политика почтовых ящиков Outlook Web App с именем `Policy1`.

    Remove-OwaMailboxPolicy -Name Policy1 

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-OwaMailboxPolicy](https://technet.microsoft.com/ru-ru/library/dd298103\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться, что вы успешно удалили политику почтовых ящиков Outlook Web App, выполните следующие действия.

  - В Центре администрирования Exchange выберите пункты **Разрешения** \> **Политики Outlook Web App**. Политика, которую вы удалили, не должна больше отображаться в списке.

