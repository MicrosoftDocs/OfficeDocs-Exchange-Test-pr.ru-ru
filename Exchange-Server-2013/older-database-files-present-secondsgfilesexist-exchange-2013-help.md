---
title: 'Older database files present_SecondSGFilesExist: Exchange 2013 Help'
TOCTitle: Older database files present_SecondSGFilesExist
ms:assetid: fe2908e7-df8b-4f35-946a-cfbf8521e93a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.secondsgfilesexist(v=EXCHG.150)
ms:contentKeyID: 50489532
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Older database files present\_SecondSGFilesExist

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2012-06-05_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Exchange Server 2007 setup cannot continue because it detected existing Microsoft Exchange database files in the target installation path.

Exchange 2007 setup requires that the target installation path be empty of Microsoft Exchange database files.

To resolve this issue, remove all existing files from target installation paths and then rerun setup.

**To delete existing Exchange Server database files from the target installation path**

1.  In My Computer or Windows Explorer, locate the target install path.
    
    > [!NOTE]  
    > By default, the database files are located in:<br />
    &lt;systemDrive&gt;:\Program Files\Microsoft\Exchange Server\Mailbox\First Storage Group.


2.  Right-click the files to be removed, and then select **Delete**.

3.  At the **Confirm File Delete** dialog, click **Yes**.

4.  Repeat steps 2 and 3 for all files in the target install paths.

