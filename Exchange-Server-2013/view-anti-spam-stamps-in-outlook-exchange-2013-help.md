---
title: 'Просмотр пометок нежелательной почты в Outlook: Exchange 2013 Help'
TOCTitle: Просмотр пометок нежелательной почты в Outlook
ms:assetid: cddb5dbf-ad1e-471c-9fc8-28ddcf7ec1d0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb124595(v=EXCHG.150)
ms:contentKeyID: 50489095
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Просмотр пометок нежелательной почты в Outlook

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2012-10-03_

С помощью Microsoft Outlook можно просматривать пометки нежелательной почты, примененные сервером Microsoft Exchange к сообщению электронной почты. Марки для борьбы с нежелательной почтой позволяют диагностировать проблемы, связанные с нежелательными сообщениями, с помощью диагностических метаданных, или марок, например сведений об отправителе, результатов проверки задачи, результатов фильтрации содержимого, которые применяются к сообщениям, проходящим через агенты защиты от нежелательной почты при фильтрации входящих сообщений из Интернета.

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 15 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Доступ к почтовому ящику" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

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

## Просмотр пометок нежелательной почты с помощью Outlook 2010 или Outlook 2013

1.  В Outlook 2010 или Outlook 2013 на клиентском компьютере в окне **Почта** дважды щелкните сообщение, чтобы открыть его.

2.  В разделе **Теги** на ленте щелкните значок **Настройки**, чтобы отобразить диалоговое окно **Свойства** для сообщений.

3.  В диалоговом окне **Свойства** в разделе **Заголовки Интернета** воспользуйтесь полосой прокрутки, чтобы просмотреть пометки нежелательной почты, как показано в следующем примере.
    
        X-MS-Exchange-Organization-PCL:7
        X-MS-Exchange-Organization-SCL:6
        X-MS-Exchange-Organization-Antispam-Report: DV:3.1.3924.1409;SID:SenderIDStatus Fail;PCL:PhishingLevel SUSPICIOUS;CW:CustomList;PP:Presolved;TIME:TimeBasedFeatures

## Просмотр пометок нежелательной почты с помощью Outlook 2007

1.  В Outlook 2007 на клиентском компьютере в окне **Почта** дважды щелкните сообщение, чтобы открыть его.

2.  На вкладке **Сообщение** в группе **Параметры** выберите **Параметры сообщения**.

3.  В диалоговом окне **Параметры сообщения** в разделе **Заголовки Интернета** воспользуйтесь полосой прокрути, чтобы просмотреть метки защиты от нежелательной почты, как показано в следующем примере.
    
        X-MS-Exchange-Organization-PCL:7
        X-MS-Exchange-Organization-SCL:6
        X-MS-Exchange-Organization-Antispam-Report: DV:3.1.3924.1409;SID:SenderIDStatus Fail;PCL:PhishingLevel SUSPICIOUS;CW:CustomList;PP:Presolved;TIME:TimeBasedFeatures

