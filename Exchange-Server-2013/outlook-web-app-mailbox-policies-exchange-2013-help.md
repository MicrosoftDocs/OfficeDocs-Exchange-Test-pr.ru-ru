---
title: 'Политики почтовых ящиков Outlook Web App: Exchange 2013 Help'
TOCTitle: Политики почтовых ящиков Outlook Web App
ms:assetid: 213b8b7a-1c29-49ee-8c98-d0364ddf4f9d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd335142(v=EXCHG.150)
ms:contentKeyID: 50487661
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Политики почтовых ящиков Outlook Web App

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2012-10-05_

Политики почтовых ящиков МайкрософтOutlook Web App используются для создания политик на уровне организации для управления доступом к функциям в Outlook Web App.

**Содержание**

Политики почтовых ящиков Outlook Web App

Создание или удаление политик почтовых ящиков Outlook Web App

Настройка политик почтовых ящиков Outlook Web App

Применение политик почтовых ящиков Outlook Web App

## Политики почтовых ящиков Outlook Web App

В Exchange 2013 можно создать несколько политик почтовых ящиков Outlook Web App и применить их к отдельным почтовым ящикам. Если к почтовому ящику применяется политика почтовых ящиков Outlook Web App, параметры виртуального каталога будут изменены.

Для управления функциями Outlook Web App можно настроить виртуальные каталоги Outlook Web App. Параметры виртуальных каталогов будут использоваться для всех почтовых ящиков, к которым не была применена политика почтовых ящиков.

## Создание или удаление политик почтовых ящиков Outlook Web App

Политика почтовых ящиков по умолчанию Outlook Web App создается автоматически при установке Exchange. По умолчанию все параметры политики почтовых ящиков Outlook Web App по умолчанию включены. В соответствии с требованиями организации можно создать любое необходимое количество политик почтовых ящиков Outlook Web App.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Политика почтовых ящиков по умолчанию Outlook Web App не применяется автоматически ни к каким почтовым ящикам.</td>
</tr>
</tbody>
</table>


Дополнительные сведения о создании или удалении политик почтовых ящиков см. в разделах [Создание политики почтовых ящиков Outlook Web App](create-an-outlook-web-app-mailbox-policy-exchange-2013-help.md) и [Удаление политики почтовых ящиков Outlook Web App с сервера Exchange](remove-an-outlook-web-app-mailbox-policy-from-exchange-exchange-2013-help.md).

## Настройка политик почтовых ящиков Outlook Web App

В политике почтовых ящиков Outlook Web App по умолчанию все параметры включены по умолчанию. Дополнительные сведения о настройке политик почтовых ящиков Outlook Web App см. в разделе [Просмотр и настройка свойств политики почтовых ящиков Outlook Web App](view-or-configure-outlook-web-app-mailbox-policy-properties-exchange-2013-help.md).

## Применение политик почтовых ящиков Outlook Web App

К почтовому ящику можно применить только одну политику почтовых ящиков Outlook Web App.

Если к почтовому ящику не применяется политика почтовых ящиков Outlook Web App, будут применены параметры, определенные для виртуального каталога.

Политику почтовых ящиков Outlook Web App можно применить к почтовому ящику с помощью центра администрирования Exchange (EAC). При этом EAC позволяет изменить существующий почтовый ящик, а командная консоль и командлет [Set-CASMailbox](https://technet.microsoft.com/ru-ru/library/bb125264\(v=exchg.150\)) позволяют применить политику почтовых ящиков. Дополнительные сведения см. в разделе [Применение или удаление политики почтовых ящиков Outlook Web App в почтовом ящике](apply-or-remove-an-outlook-web-app-mailbox-policy-on-a-mailbox-exchange-2013-help.md).

