﻿---
title: 'Выполнение переключения сервера: Exchange 2013 Help'
TOCTitle: Выполнение переключения сервера
ms:assetid: ffcefd56-b0a0-4229-9011-fff4197b7c74
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd298187(v=EXCHG.150)
ms:contentKeyID: 62523832
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Выполнение переключения сервера

 

_**Применимо к:** Exchange Server 2013 SP1_

_**Последнее изменение раздела:** 2014-06-23_

Переключение сервера — это задача, которая выполняется для перемещения всех копий активных баз данных почтовых ящиков с текущего сервера почтовых ящиков на один или несколько других серверов почтовых ящиков в группе доступности базы данных. Эта задача является частью процесса подготовки к запланированному отключению текущего сервера почтовых ящиков.

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 30 секунд на базу данных

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Группы обеспечения доступности баз данных" в разделе [Разрешения высокого уровня доступности и устойчивости сайта](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..


## Переключение сервера с помощью Центра администрирования Exchange

Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Копии базы данных почтовых ящиков" в разделе [Разрешения высокого уровня доступности и устойчивости сайта](high-availability-and-site-resilience-permissions-exchange-2013-help.md).

1.  В Центре администрирования Exchange последовательно выберите пункты **Серверы** \> **серверы**.

2.  Выберите сервер почтовых ящиков, на который требуется переключиться.

3.  В области сведений выберите команду **Переключить сервер**.

4.  На странице **Переключение сервера** выполните одно из указанных ниже действий.
    
    1.  Не изменяйте параметр по умолчанию **Автоматически выбрать конечный сервер** (в этом случае система автоматически выберет наиболее подходящий сервер почтовых ящиков для каждой переключаемой базы данных) и нажмите кнопку **сохранить**.
    
    2.  Выберите пункт **Использовать указанный сервер как цель для переключения**, нажмите кнопку **Обзор**, чтобы выбрать сервер почтовых ящиков, а затем нажмите кнопку **сохранить**.

5.  После завершения переключения нажмите кнопку **закрыть**, чтобы выйти со страницы **Переключение сервера**.

## Переключение сервера с помощью командной консоли Exchange

В этом примере выполняется переключение сервера MBX1. Система автоматически выбирает наиболее подходящий сервер почтовых ящиков для каждой активной базы данных сервера MBX1.

```powershell
Move-ActiveMailboxDatabase -Server MBX1
```

В этом примере выполняется переключение сервера почтовых ящиков MBX4. После завершения выполнения команды сервер MBX5 размещает активную копию баз данных, которые были ранее активны на сервере MBX4.

```powershell
Move-ActiveMailboxDatabase -Server MBX4 -ActivateOnServer MBX5
```

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Move-ActiveMailboxDatabase](https://technet.microsoft.com/ru-ru/library/dd298068\(v=exchg.150\)).

