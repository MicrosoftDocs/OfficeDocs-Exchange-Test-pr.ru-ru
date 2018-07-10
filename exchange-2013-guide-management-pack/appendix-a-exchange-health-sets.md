---
title: 'Appendix A: Exchange health sets'
TOCTitle: 'Appendix A: Exchange health sets'
ms:assetid: 29af464e-ae07-40f8-ac6e-28e876a91d90
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn195906(v=EXCHG.150)
ms:contentKeyID: 54652200
ms.date: 04/03/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Appendix A: Exchange health sets

 

_**Дата изменения раздела:** 2015-03-09_

The Exchange Server 2013 Management Pack relies on the Managed Availability feature in Exchange 2013. In Managed Availability, each component in Exchange 2013 monitors itself using *probes*, *monitors* and *responders*. Each Exchange 2013 component that implements Managed Availability is referred to as a *health set*. The following tables list all the health sets available in Exchange 2013.

> [!NOTE]
> Only the health sets that apply to your Exchange deployment are seen in the SCOM console. Therefore, depending on your configuration, some of these health sets may not be present in your deployment.


## Customer Touch Points Health Sets


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Health set</th>
<th>Server Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ActiveSync</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of the Exchange ActiveSync service for mobile clients.</p></td>
</tr>
<tr class="even">
<td><p>Autodiscover</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the overall health of the Autodiscover service for clients.</p></td>
</tr>
<tr class="odd">
<td><p>Compliance</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the health of compliance features.</p></td>
</tr>
<tr class="even">
<td><p>ECP</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of the Exchange Administration Center (EAC), as well as the overall health of the Outlook Web App end user setting service.</p></td>
</tr>
<tr class="odd">
<td><p>EWS</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the overall health of Exchange Web Services.</p></td>
</tr>
<tr class="even">
<td><p>IMAP</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the overall health and availability of the IMAP4 service and IMAP4 client connectivity.</p></td>
</tr>
<tr class="odd">
<td><p>Outlook</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the health of Outlook client connectivity.</p></td>
</tr>
<tr class="even">
<td><p>OWA</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the overall health of the Outlook Web App service.</p></td>
</tr>
<tr class="odd">
<td><p>POP</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the overall health and availability of the POP3 service and POP3 client connectivity.</p></td>
</tr>
<tr class="even">
<td><p>PublicFolders</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health of public folder availability and replication in your organization.</p></td>
</tr>
<tr class="odd">
<td><p>RPS</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of the Remote PowerShell service.</p></td>
</tr>
<tr class="even">
<td><p>SiteMailbox</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health and accessibility of site mailboxes in your organization.</p></td>
</tr>
<tr class="odd">
<td><p>UM</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the overall health of the Unified Messaging service in your organization.</p></td>
</tr>
</tbody>
</table>


## Service Components Health Sets


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Health set</th>
<th>Server Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ActiveSync.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the Exchange ActiveSync communications protocol on the Mailbox server.</p></td>
</tr>
<tr class="even">
<td><p>ActiveSync.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the Exchange ActiveSync infrastructure on the Client Access server.</p></td>
</tr>
<tr class="odd">
<td><p>Antimalware</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the health of the basic anti-malware protection feature.</p></td>
</tr>
<tr class="even">
<td><p>Antispam</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the health of the basic anti-spam protection feature.</p></td>
</tr>
<tr class="odd">
<td><p>Autodiscover.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the Autodiscover communications protocol on the Mailbox server.</p></td>
</tr>
<tr class="even">
<td><p>Autodiscover.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the availability of the Autodiscover proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="odd">
<td><p>Classification</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the health of the Data Loss Prevention (DLP) feature.</p></td>
</tr>
<tr class="even">
<td><p>ClientAccess.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the availability of the proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="odd">
<td><p>DataProtection</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the redundancy of databases in a database availability group (DAG).</p></td>
</tr>
<tr class="even">
<td><p>ECP.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the availability of the EAC proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="odd">
<td><p>Ediscovery.Procotol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the eDiscovery protocol on the Mailbox server.</p></td>
</tr>
<tr class="even">
<td><p>EDS</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Extracts performance counters and generates notifications when a threshold is exceeded.</p></td>
</tr>
<tr class="odd">
<td><p>EventAssistants</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the health of event-based mailbox assistants.</p></td>
</tr>
<tr class="even">
<td><p>EWS.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the Exchange Web Services communications protocol on the Mailbox server.</p></td>
</tr>
<tr class="odd">
<td><p>EWS.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the availability of the Exchange Web Services proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="even">
<td><p>FfoQuarantine</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the health of the Forefront message quarantine feature.</p></td>
</tr>
<tr class="odd">
<td><p>FfoTransport</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the Transport components in Forefront such as server and agent latency, DSNs generated, transport databases, SMTP, mailbox transport, and shadow redundancy.</p></td>
</tr>
<tr class="even">
<td><p>FfoUMC</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the overall health of the Forefront administration website.</p></td>
</tr>
<tr class="odd">
<td><p>FfoWebService</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the health of the Forefront web service.</p></td>
</tr>
<tr class="even">
<td><p>FIPS</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the health of a Transport rules component that analyzes messages.</p></td>
</tr>
<tr class="odd">
<td><p>FreeBusy</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health of the free/busy information in your organization.</p></td>
</tr>
<tr class="even">
<td><p>FrontendTransport</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of the Frontend Transport service that runs on Client Access servers.</p></td>
</tr>
<tr class="odd">
<td><p>HubTransport</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of the Hub Transport service that runs on Mailbox servers.</p></td>
</tr>
<tr class="even">
<td><p>IMAP.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the IMAP4 protocol on the Mailbox server.</p></td>
</tr>
<tr class="odd">
<td><p>IMAP.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the availability of the IMAP4 proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="even">
<td><p>MailboxMigration</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health of the Migration Service.</p></td>
</tr>
<tr class="odd">
<td><p>MailboxTransport</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health of the Transport component that delivers messages to and picks messages up from user mailboxes.</p></td>
</tr>
<tr class="even">
<td><p>MailFlow</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the health of the mail flow paths within your organization.</p></td>
</tr>
<tr class="odd">
<td><p>MessageTracing</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health and availability of message tracking and delivery reports.</p></td>
</tr>
<tr class="even">
<td><p>Monitoring</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the health of the monitoring service itself.</p></td>
</tr>
<tr class="odd">
<td><p>MRS</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health of the Mailbox Replication service.</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeCertificateDeployment</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the state of certificates in your Exchange organization.</p></td>
</tr>
<tr class="odd">
<td><p>OAB</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health of offline address book (OAB) generation and distribution.</p></td>
</tr>
<tr class="even">
<td><p>OAB.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the availability of the OAB proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="odd">
<td><p>Outlook.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the MAPI protocol on the Mailbox server.</p></td>
</tr>
<tr class="even">
<td><p>Outlook.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the availability of the Outlook Anywhere proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="odd">
<td><p>OWA.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the Outlook Web App protocol on the Mailbox server.</p></td>
</tr>
<tr class="even">
<td><p>OWA.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the availability of the Outlook Web App proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="odd">
<td><p>POP.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the POP3 protocol on the Mailbox server.</p></td>
</tr>
<tr class="even">
<td><p>POP.Proxy</p></td>
<td><p>CAS</p></td>
<td><p>Monitors the availability of the POP3 proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="odd">
<td><p>PowershellDataProvider</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of the Exchange Management Shell.</p></td>
</tr>
<tr class="even">
<td><p>PushNotifications.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the push notifications protocol on the Mailbox server.</p></td>
</tr>
<tr class="odd">
<td><p>RemoteMonitoring</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the health of the monitoring service on other servers.</p></td>
</tr>
<tr class="even">
<td><p>RPS.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the Remote PowerShell protocol on the Mailbox server.</p></td>
</tr>
<tr class="odd">
<td><p>RPS.Proxy</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the availability of the Remote PowerShell service proxy infrastructure on the Client Access server.</p></td>
</tr>
<tr class="even">
<td><p>Search</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of the Exchange Search service.</p></td>
</tr>
<tr class="odd">
<td><p>SMTP</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of SMTP on Exchange servers.</p></td>
</tr>
<tr class="even">
<td><p>Store</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health of the Exchange store on the Exchange servers.</p></td>
</tr>
<tr class="odd">
<td><p>Transport</p></td>
<td><p>CAS</p></td>
<td><p>Monitors Transport components such as server and agent latency, DSNs generated, transport databases, SMTP, mailbox transport, and shadow redundancy.</p></td>
</tr>
<tr class="even">
<td><p>UM.CallRouter</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of the Unified Messaging Call Router service.</p></td>
</tr>
<tr class="odd">
<td><p>UM.Protocol</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the Unified Messaging protocol on the Mailbox server.</p></td>
</tr>
<tr class="even">
<td><p>UserThrottling</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the overall health of throttling policies in your organization.</p></td>
</tr>
</tbody>
</table>


## Server Resources Health Sets


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Health set</th>
<th>Server Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clustering</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the health of the Windows cluster service on a Mailbox server that is a DAG member.</p></td>
</tr>
<tr class="even">
<td><p>DiskSpace</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the disk space utilization on Exchange servers.</p></td>
</tr>
<tr class="odd">
<td><p>MailboxSpace</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the overall health of mailbox databases.</p></td>
</tr>
<tr class="even">
<td><p>Memory</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the memory utilization on Exchange servers.</p></td>
</tr>
</tbody>
</table>


## Key Dependencies Health Sets


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Health set</th>
<th>Server Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AD</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Monitors the availability of Active Directory.</p></td>
</tr>
<tr class="even">
<td><p>Network</p></td>
<td><p>CAS, Mailbox</p></td>
<td><p>Checks to verify that the server is registered in DNS.</p></td>
</tr>
<tr class="odd">
<td><p>OWA.Protocol.Dep</p></td>
<td><p>Mailbox</p></td>
<td><p>Monitors the health of the OWA protocol dependency.</p></td>
</tr>
</tbody>
</table>

