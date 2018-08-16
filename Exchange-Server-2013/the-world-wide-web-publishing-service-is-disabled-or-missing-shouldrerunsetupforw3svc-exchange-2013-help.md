---
title: 'Служба веб-публикаций отключена или отсутствует'
TOCTitle: The World Wide Web Publishing Service is disabled or missing_ShouldReRunSetupForW3SVC
ms:assetid: f1815a6d-d16b-4271-9fab-84087465529e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/ms.exch.setupreadiness.shouldrerunsetupforw3svc(v=EXCHG.150)
ms:contentKeyID: 50489449
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# The World Wide Web Publishing Service is disabled or missing\_ShouldReRunSetupForW3SVC

 

_**Применимо к:** Exchange Server_

_**Последнее изменение раздела:** 2012-06-05_

Содержимое этой статьи не обновлялось для Microsoft Exchange Server 2013. Несмотря на отсутствие обновления, оно может быть применимо для Exchange 2013. Если вам все еще нужна помощь, ознакомьтесь с указанными ниже ресурсами сообщества.

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Microsoft® Exchange Server 2007 setup cannot continue because its attempt to install the Mailbox Server or Client Access role found that the World Wide Web Publishing Service is either disabled or not installed on this computer.

Exchange 2007 setup requires the computer that you are installing Microsoft Exchange to have the World Wide Web Publishing Service installed and set to something other than disabled.

To resolve this issue, verify that the World Wide Web Publishing service is installed and not disabled on the local computer, and then rerun Microsoft Exchange setup.

**To verify that the World Wide Web Publishing Service is installed and not disabled**

1.  Right-click **My Computer** on the desktop, and then click **Manage**.

2.  Expand the **Services and Applications** node, and then click the **Services** node.

3.  In the right pane, locate the **World Wide Web Publishing Service**.
    
    If the **World Wide Web Publishing Service** is not displayed in the list of services installed, follow the steps in the procedure below to install it.

4.  If the **World Wide Web Publishing Service** is displayed but has a status other than **Started**, continue with the steps below to start it.

5.  Right-click **World Wide Web Publishing Service**, and then click **Properties**.

6.  Verify the **Startup Type** is **Automatic** and the **Service status** is set to **Started**.

7.  Click **Apply**, and then click **OK**.

**To install the World Wide Web Publishing Service**

1.  On the **Start** menu, select **Settings**, **Control Panel**, and then click **Add or Remove Programs**

2.  Click **Add/Remove Windows Components**.

3.  In the **Components** list, select the **Application Server** check box, and then click **Details**.

4.  Select **Internet Information Services Manager**, and then click **Details**.

5.  Select **World Wide Web Service**, and then select the check box.

6.  Click **OK** two times to return to the **Components** list, and then click **Next**.

7.  Click **Finish** when the IIS service is installed.

