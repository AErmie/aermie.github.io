---
layout: page
title: Book Review: SAMS System Center 2012 Operations Manager
date: 2014-05-19 11:46
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2014/05/System-Center-2012-Operations-Manager-Unleashed-Cover.jpg"><img class="alignleft size-full wp-image-10071" src="/wp-content/uploads/2014/05/System-Center-2012-Operations-Manager-Unleashed-Cover.jpg" alt="System Center 2012 Operations Manager Unleashed Cover" width="260" height="339" /></a>Hello Everyone,

Something that you may not know about me, but I am an avid reader. Late last year I was able to complete my reading of the <a href="http://www.amazon.com/System-Center-Operations-Manager-Unleashed/dp/0672335913/ref=sr_1_6?s=books&amp;ie=UTF8&amp;qid=1400379155&amp;sr=1-6&amp;keywords=system+center+2012+r2" target="_blank">SAMS System Center 2012 Operations Manager Unleashed (2nd Edition)</a> book. That's right, I read the entire book cover-to-cover.

If you are like me, when reading a 1536 page book, you're bound to come across either some interesting points, tips, etc. However, unless you make some sort of note about it, you're more than likely to forget about it by the time you get to the end. Therefore, I have gotten into the habit of purchasing the eBook (along with a physical printed copy) and making highlights as I go. I then sync  these highlights to my Evernote account, so that I can easily access, and search them in the future.

Well, I've decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<div>
<h3 style="color: #000000;">Chapter 01: Operations Management Basics</h3>
<div style="color: #000000;">
<ul>
	<li>NONE</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 02: What's New In System Center 2012 Operations Manager</h3>
<div style="color: #000000;">
<ul>
	<li>Should you need to move the RMS emulator role, Microsoft provides the Get-SCOMRMSEmulator, Set-SCOMRMSEmulator, and Remove-SCOMRMSEmulator PowerShell cmdlets to identify, move, and delete the RMSE</li>
	<li>Windows agents do not use resource pools for failover</li>
	<li>As APM is configured using templates, it does not require authoring management packs or code modifications</li>
	<li>SP 1 adds support for WFC, ASP.NET MVC, .NET Windows Services, Azure SDK, and IIS 8.</li>
	<li>One change is the Actions pane is renamed to the Tasks pane</li>
	<li>The OpsMgr 2012 Web console is completely redesigned and based on Silverlight</li>
	<li>Having a resource pool requires at least two management servers</li>
	<li>Previous versions of Operations Manager used connectors to connect to other systems. In System Center 2012 Operations Manager, this functionality is replaced by Orchestrator integration packs.</li>
	<li>Agentless exception monitoring provides data on application crashes</li>
	<li>ACS is a secure and efficient way to gather Security event logs from systems and consolidate them for analysis and reporting</li>
	<li>The ACS agent is included in the OpsMgr agent deployment</li>
	<li>Components in OpsMgr 2007 are now called product features</li>
	<li>The OpsMgr agent is now a feature, rather than a component</li>
	<li>A gateway server enables monitoring of computers that lie outside the Kerberos trust boundaries (Kerberos realm) of the management group</li>
	<li>Gateway servers use certificates to communicate with those agents that cannot otherwise communicate with a management server</li>
	<li>The data transmitted between the agent and a management server (or gateway server) is both encrypted and compressed.</li>
	<li>Compression ratio ranging from approximately 4:1 to 6:1</li>
	<li>Management packs use XML</li>
	<li>Management packs are the brains of Operations Manager; they provide the logic and reports used for monitoring</li>
	<li>A Run As profile is a profile that associates a credential with a workflow so it can run using those credentials</li>
	<li>When a workflow requires credentials that cannot be provided by the default action account, it can be written to use a Run As profile</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 03: Looking Inside OpsMgr</h3>
<div style="color: #000000;">
<ul>
	<li>The operational and data warehouse databases should run on clustered SQL Server instances for high availability of the OpsMgr management group</li>
	<li>Failover of the RMSE role to any surviving additional management server is performed simply but manually in OpsMgr 2012 using a PowerShell cmdlet.</li>
	<li>Microsoft recommends a minimum of two management servers be deployed in all management groups monitoring mission-critical highly available infrastructures</li>
	<li>In the case of Windows computers, the agent can be staged in computer images, and the agent can discover its configuration from Active Directory.</li>
	<li>The process of multi-homing an agent occurs automatically by discovering the computer and pushing agents from two management groups—the first discovery installs the agent; the second discovery multi-homes the agent</li>
	<li>You can install the reporting server feature on the same SQL Server hosting the data warehouse database in a small environment</li>
	<li>In large and high-availability environments, SSRS typically runs on a dedicated server</li>
	<li>The OpsMgr reporting server itself cannot be made highly available</li>
	<li>All management servers are members of the All Management Servers Resource Pool unless they are expressly removed using a PowerShell cmdlet</li>
	<li>Microsoft recommends all management servers have no more than 5ms latency between them</li>
	<li>Place all management servers in the same datacenter</li>
	<li>In heavy use and high-availability scenarios, you can load balance one or more dedicated Web console servers.</li>
	<li>The gateway server resides in an external environment and uses certificates (rather than AD-based Kerberos) to secure communication back to the other features in the management group</li>
	<li>Gateway servers compress agent to management server traffic by as much as 50%</li>
	<li>Microsoft requires the version of SQL Server for the audit database match the SQL Server version of the operational database</li>
	<li>You can cluster the SQL instance hosting the ACS database for high availability,</li>
	<li>You will generally have only one ACS collector per management group.</li>
	<li>The Agentless Exception Monitoring (AEM) client feature is activated by a group policy object (GPO) applied to computers</li>
	<li>AEM centralizes the crash and bug information collected by Dr. Watson and Windows Error Reporting (WER) in your organization</li>
	<li>You will want to create a network device monitoring pool with specific management servers or gateway servers as members</li>
	<li>You should only include those management servers or gateway servers in network device monitoring pools that are not already heavily loaded with agent management traffic</li>
	<li>APM is activated by importing the APM Web IIS 7 (or IIS 8 if running Windows Server 2008 with System Center SP 1) management pack and running the Add Monitoring Wizard in the Authoring space.</li>
	<li>The health service usually runs under the local system account on all computers.</li>
	<li>The OpsMgr agent to management or gateway server connection is encrypted by a public-private key pair created on each instance of the health service (agent, management server, and gateway server), after being authenticated by Kerberos or certificate</li>
	<li>The public key is automatically regenerated during health service startup, when the key expires, and when there is a failure to decrypt a message.</li>
	<li>TCP port 5723 in OpsMgr is associated with the health service</li>
	<li>Consoles, web consoles, and report servers connect to the System Center Data Access Service.</li>
	<li>The DAS typically runs under a domain service account on management servers.</li>
	<li>The configuration service is responsible for providing the monitoring configuration to each agent’s health service</li>
	<li>The service acts as an intermediary for delivering sensitive information in an encrypted format from the OpsMgr database to the target health service on a managed computer</li>
	<li>The configuration service almost always runs under a domain service account on management servers</li>
	<li>The audit forwarding service is automatically installed (but not configured) on every OpsMgr management server, gateway server, and agent.</li>
	<li>The database is created during setup of the ACS service on the selected management server.</li>
	<li>The APM service is automatically installed (but not configured) on every OpsMgr management server, gateway server, and agent.</li>
	<li>Communication between management servers and the three OpsMgr databases (operational, data warehouse, and audit) is always via standard SQL client/server protocols, specifically OLE DB (Object Linking and Embedding Database)</li>
	<li>Between agents, as well as management and gateway servers, the primary Transmission Control Protocol (TCP) port is 5723, which is the only outbound firewall exception needed to manage a computer in a minimal configuration once the agent is installed</li>
	<li>An exception is the Web console when using the optional APM feature—this scenario requires the Web console to access the operational and data warehouse databases directly.</li>
	<li>Additional outbound ports are used when enabling ACS and AEM features.</li>
	<li>The primary OpsMgr agent-management server connection, TCP port 5723, is protected with a unique digital key and is essentially a secure sockets layer (SSL) connection, an encrypted tunnel</li>
	<li>Stopping the health service (the System Center Management Service) and deleting the Health Service State folder is a safe and standard procedure to troubleshoot many OpsMgr server and agent issues</li>
	<li>View what workflows are loaded on a management server is to run the Workflow Analyzer tool from the OpsMgr resource kit</li>
	<li>All scripts have a default timeout value as a safety feature to avoid allowing idle or dormant monitoring threads to stack up and overload the system</li>
	<li>The console is generally installed on every OpsMgr management server</li>
	<li>Only unhealthy monitors appear when you first open an object’s health model</li>
	<li>There are also two new web portals associated with the APM feature</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 04: Planning An Operations Manager Deployment</h3>
<div style="color: #000000;">
<ul>
	<li>Start by creating a single high-level design and planning document</li>
	<li>Developing a comprehensive plan and receiving backing from the appropriate sponsors within your organization.</li>
	<li>Proper technical deployments require a disciplined approach to implement the solution</li>
	<li>Understand from a monitoring perspective the current environment and history, how the organization reached where they are today</li>
	<li>An organization’s history of monitoring will show where previous pitfalls existed so they can be avoided in the future.</li>
	<li>Important to be aware of any services on which OpsMgr may have dependencies. These include but are not limited to local area network (LAN)/wide area network (WAN) connections and speeds, routers, switches, firewalls, Domain Name Server (DNS), Active Directory (AD), instant messaging, and Exchange</li>
	<li>Determining which servers Operations Manager will be monitoring (including domain/[s] workgroup they are in), applications on these servers that need to be monitored, and how long to retain alert, event, and performance information.</li>
	<li>Important that you identify what is and is not in scope for the project</li>
	<li>First phase deployment for OpsMgr 2007 often did not include monitoring for non-Windows operating systems or devices, Audit Collection Services (ACS), or Agentless Exception Monitoring (AEM)</li>
	<li>A typical first phase deployment of System Center 2012 Operations Manager will include design of the OpsMgr environment, deployment of OpsMgr, and tuning OpsMgr</li>
	<li>In most cases, a single management group is the simplest configuration to implement, support, and maintain</li>
	<li>Using a separate management group may be required should your auditors or company mandate state that the ACS functionality be administered by a separate group of individuals.</li>
	<li>Management groups cannot have a leading or trailing space in their name.</li>
	<li>The management group name is case sensitive.</li>
	<li>Do not choose an existing management group name used for Operations Manager or Service Manager</li>
	<li>An average client will use 3Kbps of network traffic between itself and the management server</li>
	<li>Operations Manager can support approximately 30 agent-managed computers on a 128KB network connection (agent-managed systems use less bandwidth than agentless-managed systems</li>
	<li>Install management servers in the same physical location as the database servers and on the same subnet if possible. OpsMgr requires high bandwidth and low latency between the management server and the database server.</li>
	<li>Minimum network connectivity Data sent from the management servers to the databases is not compressed.
<ul>
	<li>The amount of data sent by the agent depends on the management packs installed on each agent, the type of activity generated, how those management packs are tuned, and conditions in your environment. The good news is that data between agents and the management server/gateway server is compressed. Satya’s tests determined about 200Kbps is sent for 200 agents in an environment with the AD, Windows Base OS, DNS, and OpsMgr management packs.</li>
</ul>
</li>
	<li>Audit Collection Systems (forwarder to collector): Security events are sent in near real time rather than being batched together</li>
	<li>Security events sent from the agent to the collector are typically less than 100 bytes, and the event in the database is under .05 KB</li>
	<li>It is best to keep things simple by keeping the number of Operations Manager servers as low as possible while still meeting your business requirements.</li>
	<li>Infrastructure is nearly always hosted in a single site. OpsMgr without the ACS feature consists of two databases, a number of management servers and gateways, plus an optional dedicated web console and reporting server.</li>
	<li>For a distributed OpsMgr implementation, consider the location of the majority of the systems you will be managing. This generally is where you deploy the bulk of your OpsMgr environment, and should be the first thing to consider during planning</li>
	<li>Management servers provide the communication path between OpsMgr agents and gateway servers and the Operations database and OpsMgr data warehouse.</li>
	<li>Plan for a minimum of two management servers per management group. Each management server can handle up to 3,000 agent-managed computers. OpsMgr 2012 has a limit of 10 agentless monitored systems per management server</li>
	<li>If a management group will monitor more than 3,000 computers, install multiple management servers in the management group</li>
	<li>Add management servers to provide monitoring for up to 500 UNIX and Linux servers monitored by OpsMgr and to provide redundancy for these functions.</li>
	<li>Add management servers to provide monitoring for network devices</li>
	<li>Although each management server does not store any major amounts of data, it does rely on the processor, memory, and network throughput of the system to perform effectively</li>
	<li>Management servers should be separate from the Operations database</li>
	<li>If the MS and operational database are on the same server, the authors recommend monitoring no more than 200 agents with that server because it can degrade the performance of your OpsMgr solution</li>
	<li>There are high processing requirements on both the operational database and data warehouse, and they perform better with their own server</li>
	<li>1,000+ agents: 4 Disk RAID 10, 16GB of memory, 8 Cores. This will vary based on your specific environment (number of agents, network devices, monitored URLs, UNIX/Linux systems, and so on</li>
	<li>Use a highly available virtualization solution that migrates the management server(s) upon loss of a host system.</li>
	<li>Resource pool functionality does not replace AD integration—OpsMgr Windows agents are NOT assigned to report to a pool, but to a specific management server.</li>
	<li>A gateway server gathers communications from agents and forwards them to a management server on the other side of the firewall using port 5723</li>
	<li>The specified management server handle only gateway server communication; because of load issues, it is best that agents do not report directly to the same management server as a gateway server</li>
	<li>While the management server sends the command to deploy the agents to the gateway server, the gateway server does the actual agent deployment.</li>
	<li>A latency of less than 100ms is desired</li>
	<li>Data sent from the gateway server is consolidated, resulting in an estimated 20%-30% reduction of total data sent to the database</li>
	<li>Note that this reduction in data that is sent applies when there are approximately 50 or more agents reporting to the gateway. With smaller numbers of agents, there will be very little benefit in terms of bandwidth savings from implementing a gateway server</li>
	<li>Microsoft recommend assigning a dedicated management server with no traditional agents reporting to it (even in a failover scenario), for the sole purpose of collecting data from your gateway server(s).</li>
	<li>This means you typically will want to host no more than three or four gateways per management server during normal operation, and control failover such that no more than six report to a single management server at any time</li>
	<li>As a rule of thumb, trim the SQL Server instance to use only what memory is available on the server, leaving 1GB per CPU socket for operating system (OS) operations. This approach provides SQL with as much memory as possible without starving the OS.</li>
	<li>You must use either the Standard or Enterprise editions with OpsMgr</li>
	<li>Enterprise Edition is strongly recommended in high-volume ACS environments as it reduces the chance of lost security events</li>
	<li>The best practice for database servers in OpsMgr is to place the two databases on different servers to avoid resource contention.</li>
	<li>SQL collation: SQL_Latin1_General_CP1_CI_AS.Install the operational database and data warehouse on different systems. OpsMgr writes data in almost real time to these databases, making their loads similar
<ul>
	<li>SQL Server Full Text Search: Required.</li>
	<li>.NET Framework: .NET Framework 3.5 SP 1 and .NET Framework 4</li>
</ul>
</li>
	<li>Configure the database server with one disk for OS, one disk for SQL, one disk for tempdb, and one disk for transaction logs.</li>
	<li>Resize tempdb and the transaction log to be 20% of the total size of the operational database and data warehouse</li>
	<li>SSRS is often installed on the OpsMgr data warehouse server but can be installed on a separate web server</li>
	<li>The hardware requirements for ACS database servers vary depending upon the number of events per second that are being inserted into the database.</li>
	<li>Microsoft does not support using a different version of SQL Server for different Operations Manager features, so use the same SQL version for ACS as the other OpsMgr database components</li>
	<li>The ACS collector feature is installed on an existing management server, so the hardware requirements for the collector mirror those of the management server.</li>
	<li>After the service is enabled, the ACS collector feature captures all security events (which are also saved to the local Windows security event log).</li>
	<li>System Center 2012 Operations Manager includes functionality that captures, aggregates, and reports on application crashes (Dr. Watson errors).</li>
	<li>From a planning perspective, if there is a requirement for AEM, there must be a plan for a server that stores the crash information, and you must deploy a group policy to redirect the application crash information to the AEM server</li>
	<li>From a planning viewpoint, the server you will use must be identified and have sufficient space to store crash information. (Crash information can range from very small up to 8GB.)</li>
	<li>By collecting this information, identifying patterns, and working to resolve them, an organization can take a large step forward to becoming more proactive in situations affecting its end users, which will affect productivity</li>
	<li>You should install this console on all management servers, including the server with the RMS emulator role.</li>
	<li>From a performance perspective, it is best to run the Operations consoles from administrator workstations rather than from servers installed with OpsMgr features</li>
	<li>PowerShell 3.0 is required for administration of UNIX/Linux systems</li>
	<li>Web Console Servers: This server feature runs IIS and uses Silverlight to provide a web-based version of the Operations console.</li>
	<li>Most non-administrator and non-authoring users of Operations Manager should be able to use the OpsMgr Web console for a majority of day-to-day operations.</li>
	<li>Web browsers: Internet Explorer 7, Internet Explorer 8, Internet Explorer 9. Operations Manager 2012 SP 1 removes support for Internet Explorer 7 but adds Internet Explorer 10 and Silverlight 5.0.</li>
	<li>It is not required that you install Silverlight on the server where you are installing the OpsMgr Web console, but it is often recommended</li>
	<li>Web Console High Availability/Redundancy: You can configure redundancy for this feature by installing multiple Web console servers and leveraging NLB or other load-balancing solutions</li>
	<li>Each device managed by the Operations Manager requires an ML, whether you are monitoring it directly or indirectly</li>
	<li>System Center 2012 Standard: $1,323</li>
	<li>System Center 2012 Datacenter: $3,607</li>
	<li>NET monitoring is now integrated into Operations Manager so this does not affect licensing.</li>
	<li>When monitoring network devices with Operations Manager anything OSI layer 3 and below does not require an SML</li>
	<li>The planning phase identifies what needs testing as part of the POC—base testing on your business requirements</li>
	<li>Your focus during POC testing should directly relate to the business requirements identified for your OpsMgr solution.</li>
	<li>Although you are deploying your production environment design, you will limit either the number of servers to which you are deploying OpsMgr agent or the number of management packs used</li>
</ul>
<div></div>
<div></div>
</div>
<h3 style="color: #000000;">Chapter 05: Installing System Center 2012 Operations Manager</h3>
<div style="color: #000000;">
<ul>
	<li>OpsMgr 2012 does not change the AD schema. After installation, some management packs such as the AD management pack will create containers in the domain configuration. An unusual but important requirement is you cannot install OpsMgr in an AD domain with a “flat” Domain Name System (DNS) domain space</li>
	<li>The OM_MSAA and the OM_DWWA OpsMgr service accounts must be local administrators on management servers</li>
	<li>An additional consideration is the security status of the user performing your OpsMgr installation. The user account of this user requires SA (SysAdmin) rights on the SQL servers where the OpsMgr databases will be installed</li>
	<li>All server roles except for the gateway server, including all SQL database servers, require .NET 3.5 Service Pack 1.</li>
	<li>All server roles (other than gateway servers that are not involved in monitoring network devices or UNIX/Linux computers), including the operational and data warehouse SQL database servers, require .NET Framework 4</li>
	<li>If installing the Web console component, it is important the web server role (Internet Information Services) be enabled before installing .NET Framework 4.</li>
	<li>About the Enable SNMP Feature: It is not recommend installing this feature on management servers or gateways, unless they are physical servers that depend on SNMP-based agents for server hardware monitoring. OpsMgr 2012 does not leverage or interact with the Windows SNMP feature or service in any way. The Windows SNMP trap service is not used by OpsMgr and must not be enabled on OpsMgr servers monitoring network devices.</li>
	<li>All console instances require Microsoft Report Viewer 2010 Redistributable Package</li>
	<li>The list in this section is a recommended order of installation</li>
	<li>Here is the list of features to install:The OpsMgr setup wizard creates and installs the database during setup of the first management server. Note that you must enable Full Text Search in SQL Server
<ul>
	<li>1. First management server</li>
	<li>2. Additional management server(s)</li>
	<li>3. Reporting server</li>
	<li>4. Web console(s)</li>
	<li>5. Gateway server(s)</li>
	<li>6. ACS</li>
	<li>7. Agents</li>
	<li>8. ACS forwarders</li>
	<li>9. Operating system management packs</li>
</ul>
</li>
	<li>One SQL Server system each for the operations, data warehouse, and ACS databases, plus a SQL Server Reporting Services server</li>
	<li>SQL needs inbound firewall rules that permit ports TCP 1433 and UDP 1434. SQL Server Reporting Services requires ports TCP 80 and TCP 443.</li>
	<li>In the enterprise environment, consider four processor cores and 16GB memory as a recommended minimum machine configuration for the RMS emulator role.</li>
	<li>After you create a management group, you cannot change its name without reinstalling the management group</li>
	<li>Notice there is no option to use an existing database; you cannot install OpsMgr 2012 using a pre-created database.</li>
	<li>Unlike the operational database installation step, there is an option to use an existing data warehouse database.</li>
	<li>The management server action account, which must be a member of the local Administrators group on the management server</li>
	<li>This credential reads and updates information in the operational database and is assigned the sdk_user role in this database</li>
	<li>The System Center Configuration service and System Center Data Access service account. Like the management server action account (OM_MSAA), this account must be a member of the local Administrators group on the management server</li>
	<li>The Data Reader account is used to deploy reports</li>
	<li>The Data Reader account is also used as the SSRS IIS Application Pool account that connects to a management server.</li>
	<li>The Data Writer account reads data from the operational database and writes data from a management server to the data warehouse database</li>
	<li>The MSAA and SDK accounts (which should not be Domain Admins in normal practice) should be made members of the local Administrators group on management servers.</li>
	<li>You cannot install any other applications using SSRS on the instance of SQL Server used by OpsMgr reporting</li>
	<li>OpsMgr needs its own dedicated SSRS instance, one that is fully functional in a default SSRS configuration, before you install OpsMgr reporting.</li>
	<li>Each OpsMgr management group has only one reporting server</li>
	<li>Before installing OpsMgr reporting, ensure the user account you plan to use during installation has SQL SA (SysAdmin) permissions on all databases. The Data Warehouse Write account (OM_DWWA in this book) is granted necessary SQL Server logon rights during setup. Service accounts only require local administrative rights on the SQL servers; it is the user account performing the installation that requires elevated SQL permission. (Members of the local Administrators group have SQL logon rights by default.)</li>
	<li>At the Specify a Management server page, enter the name of a management server to be used by the reporting features only, shown in Figure 5.27. The specified server will handle data associated with specific management servers or management groups. Normally, this is either the name of the first OpsMgr 2012 management server you installed, or if you are using a load-balanced management server pool, specify the virtual server name of the pool</li>
	<li>After the reporting server is deployed, it can take up to 30 minutes for reports to appear in the Reporting space of the Operations console</li>
	<li>A key prerequisite for the Web console is having an existing local installation of IIS—you can ensure this by installing the web server role and related features on Windows Server. You must also install the following role services with IIS in addition to the IIS management console:The authors recommend the web server role (Internet Information Services) be enabled before installing .NET Framework 4
<ul>
	<li>Static Content</li>
	<li>Default Document</li>
	<li>Directory Browsing</li>
	<li>HTTP Errors</li>
	<li>HTTP Logging</li>
	<li>Request Monitor</li>
	<li>Request Filtering</li>
	<li>Static Content Compression</li>
	<li>Web Server (IIS) Support</li>
	<li>IIS 6 Metabase Compatibility</li>
	<li>ASP.NET</li>
	<li>Windows Authentication</li>
</ul>
</li>
	<li>If you want to enable an SSL connection to the Web console during installation (recommended), install a web server certificate to the default website before running the Web console setup.</li>
	<li>If you install a stand-alone Web console on a server, you will not be able to add the management server feature to this server</li>
	<li>Installing the Web console requires ISAPI and CGI Restrictions in IIS enabled for ASP.NET 4.</li>
	<li>At the Specify a Management server page, enter the name of a management server to be used by the Web console only, as previously shown in Figure 5.27. The management server you specify will handle data associated with specific management servers or management groups. Normally, this is the name of the first installed management server, or if using a load-balanced management server pool, the virtual server name of the pool</li>
	<li>You may see this warning (circled in Figure 5.35): Web console does not have sufficient access to the database. Setup can continue, but note that some components may not fully install. If this appears and you will be using the application performance monitoring (APM) features of OpsMgr, execute the following SQL statement against the operations and data warehouse databases in SQL Server Management Studio as demonstrated in Figure 5.36.
<ul>
	<li>EXEC [apm].GrantRWPermissionsToComputer '&lt;domainComputerName&gt;$'</li>
</ul>
</li>
	<li>Configure permissions inheritance for the Web console:The Web console requires the latest release of Silverlight and a custom Silverlight update. The first time you access the Web console with your browser, you are prompted to install or update Silverlight if needed. It may be necessary to add the website of the Web console to your browser’s trusted sites list.
<ul>
	<li>In Windows Explorer, navigate to the MonitoringView folder in the installation folder for the Web console (by default, %ProgramFiles%System Center 2012Operations ManagerWebConsoleMonitoringView), right-click the TempImages folder, and click Properties.</li>
	<li>On the Security tab, click Advanced.</li>
	<li>On the Permissions tab, select Change Permissions.</li>
	<li>Select the Include inheritable permissions from this object’s parent check box.</li>
	<li>In Permission entries, click Administrators, and then click Remove. Repeat for the SYSTEM entry, and then click OK.</li>
	<li>Click OK to close Advanced Security Settings for TempImages, and then click OK to close TempImages Properties.</li>
</ul>
</li>
	<li>If you are deploying a gateway across security boundaries, you must first deploy a public key infrastructure (PKI) using a public, an enterprise, or a stand-alone certificate authority (CA)</li>
	<li>Preparatory work for deploying a gateway may include installing .NET Framework 4 or 4.5 and obtaining an Operations Manager client certificate with a private key</li>
	<li>The management group must also be prepared for the gateway server by running the gateway approval tool</li>
	<li>Always add a gateway to the management group by running the gateway approval tool on the management server before installing the gateway software on the target computer</li>
	<li>Run the gateway approval tool on a management server. First copy Microsoft.EnterpriseManagement.GatewayApprovalTool.exe and Microsoft.EnterpriseManagement.GatewayApprovalTool.exe.config from the SupportTools folder on the OpsMgr installation media to the OpsMgr program files server folder, generally %ProgramFiles%System Center 2012Operations ManagerServer</li>
	<li>Run the tool with command line switches to assign the new gateway to an existing management server or gateway</li>
	<li>At the Gateway Action Account page, select to use Local System if the gateway will not be pushing agents to other computers. If the gateway will push install agents, enter credential information for an administrative account in the domain of the gateway server</li>
	<li>You must enable the Server Proxy setting on the new gateway server.</li>
	<li>You are using certificates for authentication, import the Operations Manager client certificate on the gateway server.</li>
	<li>Preparation for deploying ACS includes deciding whether you will install ACS reporting integrated with the reporting space in the Operations console, or on a separate, non-integrated, SSRS instance</li>
	<li>Installing ACS on a secondary management server, which creates the new ACS database</li>
	<li>Deploying ACS reporting to an SSRS instance</li>
	<li>If you will use ACS to collect security events from computers in untrusted domains or workgroups, provision the ACS collector with the same certificate used to enable management server to gateway communication</li>
	<li>Click on the DBAudit datasource and confirm Windows integrated security is selected for the connection credential type</li>
	<li>If deploying ACS reporting in the non-integrated model that is not integrated with OpsMgr reporting but is installed on a dedicated standoff instance of SSRS, you must manually upload the report banner files to avoid a red “X” (missing graphic) at the top of your ACS reports. Open SQL Server Reporting Services in your web browser and navigate to the Home folder. (You should see the AuditReports data source folder at the same level.) Click the Upload File button and locate the files banner_landscape.jpg and banner_portrait.jpg in the %ProgramFiles%System Center 2012Operations ManagerReportingReports folder on the SSRS computer.</li>
	<li>Import the Operations Manager client certificate on the agent:Enable audit collection first for all management servers and gateways, then for all agents
<ul>
	<li>Copy the MOMCertImport.exe file from the SupportTools folder on the OpsMgr installation media to the Operations Manager program files client folder.</li>
	<li>Open an elevated command prompt on the agent computer, and change directory to the OpsMgr program files server folder, such as %ProgramFiles%System Center 2012Operations ManagerAgent.</li>
	<li>Run the tool with command line switches to import the certificate as previously seen in Figure 5.46 when installing a gateway server</li>
</ul>
</li>
	<li>For any fresh deployment, deploy the latest update rollup to all management group components.</li>
	<li>The new System Center 2012 Operations Manager network device monitoring feature requires the Windows Operating System management packs to be installed</li>
	<li>To complete the core management group deployment, import these management packs:
<ul>
	<li>Windows Server Operating System Reports</li>
	<li>Windows Server Operating System Library</li>
	<li>Windows Server 2008 Operating System (Discovery)</li>
	<li>Windows Server 2008 Operating System (Monitoring)</li>
</ul>
</li>
	<li>If you are using clustered OpsMgr SQL servers, consider also importing these management packs:
<ul>
	<li>Windows Cluster Management Library</li>
	<li>Windows Cluster Management Monitoring</li>
	<li>Windows Server 2008 Cluster Management Library</li>
	<li>Windows Server 2008 Cluster Management Monitoring</li>
	<li>Windows Server 2008 Cluster Shared Volume Monitoring</li>
</ul>
</li>
	<li>Removing OpsMgr: If you need to remove Operations Manager from your environment, the recommended process is the reverse order from which you installed the components. All OpsMgr installed components are manually uninstalled in a conventional manner using Control Panel -&gt; Programs and Features. Follow this recommended outline to remove OpsMgr from your environment:
<ul>
	<li>1. Disable the ACS forwarder component on all management servers, gateways, and agents using the Operations console.</li>
	<li>2. Delete any computers monitored by agentless monitoring in the Operations console.</li>
	<li>3. Manually uninstall all manually installed agents.</li>
	<li>4. Remotely uninstall all automatically installed agents using the Uninstall task in the Operations console.</li>
	<li>5. Uninstall the gateway server component from gateways and delete the gateway computer objects in the Operations console.</li>
	<li>6. Uninstall all Web consoles and dedicated Operations console instances.</li>
	<li>7. Uninstall the Reporting Server component.</li>
	<li>8. Disable the ACS Collector role on any management servers running that role.</li>
	<li>9. Uninstall each management server, uninstalling the root management server emulator last.</li>
	<li>10. Optionally back up, and then delete the operational, data warehouse, and ACS databases from the SQL server(s) that hosted them.</li>
</ul>
</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 06: Upgrading To System Center 2012 Operations Manager</h3>
<div style="color: #000000;">
<ul>
	<li>Upgrading to System Center 2012 Operations Manager is supported from OpsMgr 2007 R2 Cumulative Update 4 (CU) or later.</li>
	<li>Specifically, by deploying network load balancing (NLB) and establishing a DNS name for the NLB address of the management server pool, you can configure Operations consoles, Web consoles, and the reporting server with the DNS name for the pool</li>
	<li>If your management servers, gateways, or database servers are running Windows Server 2008 R2 with SP 1, you can upgrade these computers to Operations Manager 2012</li>
	<li>Database servers running versions SQL Server 2008 SP 1 (or later service packs) or R2 can be upgraded</li>
	<li>Upgrading an ACS collector from OpsMgr 2007 R2 to OpsMgr 2012 does not perform SQL version checking; therefore, any existing ACS database will continue to be used by OpsMgr after the upgrade</li>
	<li>Microsoft’s process flow diagram for upgrading Operations Manager is located at <a href="http://technet.microsoft.com/en-us/systemcenter/hh204732.aspx" target="_blank">http://technet.microsoft.com/en-us/systemcenter/hh204732.aspx</a>.Manually installed agents are your first priority. The authors recommend you then upgrade gateways that report to secondary management servers, conforming to an “outside -&gt; inward” upgrade approach. This method is your best track to maintaining uninterrupted monitoring during migration</li>
	<li>If you have PowerShell (PS) scripts running in your management packs that utilize the OpsMgr 2007 snap-in PS module, verify the snap-in is still available on the upgraded servers. Run the cmdlet Get-PSSnapin -registered. If the output lists PSVersion: 1.0, Microsoft Operations Manager Shell Snapin, the module is registered. If the module is no longer registered, follow the instructions at <a href="http://derekhar.blogspot.de/2007/07/operation-manager-command-shell-on-any.html" target="_blank">http://derekhar.blogspot.de/2007/07/operation-manager-command-shell-on-any.html</a> to register the OpsMgr 2007 modules manually.</li>
	<li>the data warehouse upgrade can fail with only 2GB memory installed.</li>
	<li>Reject any agents in the Device Management -&gt; Pending Management node of the Administration space of the Operations console.</li>
	<li>Stop all System Center Operations Manager services and disable any installed connectors</li>
	<li>Verify the operational database has at least 50% free space before upgrading the management group. The upgrade might fail if there is not enough space. Also ensure that the transaction logs are 50% of the total size of the operational database:</li>
	<li>If you upgrade manually installed agents that also run the AVIcode 5.7 agent (or earlier versions of the AVIcode agent), you must include the option NOAPM=1 in the command</li>
	<li>You cannot select the current Operations Manager 2007 Web console website as that site is deleted during the upgrade.</li>
	<li>Run a SQL query on the operational database to clean up the Localizedtext table and the Publishmessage table. You can copy this query from Microsoft’s website at <a href="http://technet.microsoft.com/en-us/library/8c2dbaf4-2966-45e3-a72d-5de90ff4f495#BKMK_VerifyUpgrade" target="_blank">http://technet.microsoft.com/en-us/library/8c2dbaf4-2966-45e3-a72d-5de90ff4f495#BKMK_VerifyUpgrade</a>.</li>
	<li>Follow the procedure at http://technet.microsoft.com/library/ms187510.aspx to create a full SQL database backup if you do not have a backup process in place.</li>
	<li>Run a SQL query on the operational database to clean up the Localizedtext table and the Publishmessage table. You can copy this query from Microsoft’s website at <a href="http://technet.microsoft.com/en-us/library/8c2dbaf4-2966-45e3-a72d-5de90ff4f495#BKMK_VerifyUpgrade" target="_blank">http://technet.microsoft.com/en-us/library/8c2dbaf4-2966-45e3-a72d-5de90ff4f495#BKMK_VerifyUpgrade</a>.</li>
	<li>After upgrading your management group from the secondary management server, manually edit the rsreportserver.config configuration file for the reporting server. If you attempt to upgrade reporting without making this change, the Upgrade Wizard will report a cri</li>
	<li>tical prerequisite issue, because Operations Manager cannot connect to the reporting server. (If you upgraded your management group from the RMS, you do not have to update the configuration file manually for the reporting server.)</li>
	<li>deploy management packs in a phased and deliberate approach. In particular, deploy several sealed management packs at a time and watch the effects on the management group in terms of alerting. As you discover alerts that need overrides applied, author overrides and save them in unsealed override management packs. Once monitoring is stable and effective, add another small batch of management packs until all critical business applications have end-to-end monitoring in place.</li>
	<li>Custom distributed applications (DAs) in the OpsMgr 2007 R2 management group will likely need to be authored again using the Operations console once all required objects for the DA are discovered by OpsMgr 2012.</li>
	<li>importance of having backups of the operational and data warehouse databases, as well as the complete computer and system state backup of the RMS.</li>
	<li>A new feature in OpsMgr 2012 is enabling high availability for the Data Access Service (DAS). This allows consoles, Web consoles, and report servers not to depend on a particular management server for access to the database. While you can implement this feature using Windows network load balancing, the authors suggest a hardware or virtual appliance load balancer. In this example management group, the four OpsMgr 2012 management servers will be load-balanced and addressed by a single private DNS alias such as scom.odyssey.com.</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 07: Configuring And Using System Center 2012 Operations Manager</h3>
<div style="color: #000000;">
<ul>
	<li>It is not a good practice to run the Operations console on a management server itself; you want to dedicate all MS resources for the critical OpsMgr services it hosts.</li>
	<li>Microsoft suggests that you not plan for more than 50 simultaneous Operations console sessions in a single management group. The authors recommend you close any console sessions not in active use.</li>
	<li>To avoid cluttering your Monitoring pane, the authors recommend you avoid creating additional global views unless all users of the Operations console will use them.</li>
	<li>For information on how to remove clutter from the Monitoring pane, see the suggestions at <a href="http://blogs.catapultsystems.com/cfuller/archive/2011/05/11/quicktricks-decluttering-the-monitoring-pane-view.aspx" target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2011/05/11/quicktricks-decluttering-the-monitoring-pane-view.aspx</a>.</li>
	<li>Tip: Changing the Report URL for the Web Page View</li>
	<li>The reporting URL uses a value of “%2f” to represent the “/” character, the “%20” to represent a space “ ”, and the “%3a” to represent the “:” character. The Web Page view will not accept these characters, so to get the view to display the web page you must substitute the references to “%2f” to have “/” in their place, “%20” to have “ ” in their place, and “%3a” to have “:” in their place</li>
	<li>the Operations Manager 2007 R2 Resource Kit (<a href="http://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=26139" target="_blank">http://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=26139</a>) includes a Scheduled Maintenance Mode utility enabling you to schedule and manage maintenance mode</li>
	<li>Many organizations use Tim McFadden’s GUI-based remote maintenance scheduler, available for download at <a href="http://www.scom2k7.com/scom-remote-maintenance-mode-scheduler-20/" target="_blank">http://www.scom2k7.com/scom-remote-maintenance-mode-scheduler-20/</a>.Microsoft does not recommend or support placing a management server into maintenance mode</li>
	<li>The web version of the Health Explorer displays all health states unfiltered, as in OpsMgr 2007.</li>
	<li>Resetting the health forces the monitor back to a health state.</li>
	<li>Recalculating health forces the monitor to reassess what it believes is the current health state.</li>
	<li>Recalculating health does not work for over 95% of all monitors in Operations Manager 2012</li>
	<li>This view is extremely helpful when attempting to identify objects and whether they are discovered. Marnix Wolf gives a nice example of how this view is useful at <a href="http://thoughtsonopsmgr.blogspot.com/2010/04/where-are-my-counters-for-windows.html," target="_blank">http://thoughtsonopsmgr.blogspot.com/2010/04/where-are-my-counters-for-windows.html,</a></li>
	<li>The most effective use of the Monitoring space is a combination of configuration decisions involving these features:Let’s begin with personalizing the properties of the Active Alerts global view. This view does not include two very useful fields for reviewing active alerts—the Last Modified field and the Repeat Count field. These fields are helpful when identifying recurring alerts and when alerts last reported a modification
<ul>
	<li>Personalizing the global views and other default views</li>
	<li>Creating new global views and views in child view folders</li>
	<li>Creating new child view folders or hierarchies of view folders</li>
	<li>Creating new tasks, specific for your environment, that automate actions related to the object(s) selected in console views</li>
</ul>
</li>
	<li>the ReSearch This management pack</li>
	<li>Other community-created management packs perform actions such as calling Green Machine to reset health state, executing Windows administration tasks, forwarding alerts via email, running tools from the PsTools Suite (available at <a href="http://technet.microsoft.com/en-us/sysinternals/bb896649.aspx" target="_blank">http://technet.microsoft.com/en-us/sysinternals/bb896649.aspx</a>), and more. To download these and other examples, go to <a href="http://tinyurl.com/SCCMPs" target="_blank">http://tinyurl.com/SCCMPs</a>.</li>
	<li>When creating new management packs it is important you have thought through a plan for creating them and establish a strict naming standard for your management packs</li>
	<li>When creating a distributed application in System Center 2012 Operations Manager, first create the service that defines the distributed application monitoring object at a high level.</li>
	<li>use the Distributed Application Designer to define the individual components that are part of the distributed application you want to monitor.</li>
	<li>As a best practice, your groups should automatically populate with objects of the type you are interested in, rather than depend on manual population of the group using the explicit group membership step</li>
	<li>System Center Central provides examples of how to create dynamic groups in OpsMgr, see <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/89416/Default.aspx" target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/89416/Default.aspx</a>.</li>
	<li>Tip: How to Manage System Center Operations Manager using Groups: For additional information on groups and using them in OpsMgr, see the whitepaper at <a href="http://go.veeam.com/manage-scom-using-groups-wp.html" target="_blank">http://go.veeam.com/manage-scom-using-groups-wp.html</a>.</li>
	<li>Tip: Attributes Versus Properties: There is no difference between an attribute and a property—they are the same thing. Attributes are discovered properties of a class or type, which is made up of discovered instances or objects.</li>
	<li>Tip: Automatically Grouping Servers in OpsMgr Based on Tier: For additional information on how to gather a custom attribute such as the tier of a server (as an example, a development system may be a Tier 5 and a production critical system would then be a Tier 1 server), see the blog post at <a href="http://blogs.catapultsystems.com/cfuller/archive/2009/01/16/automatically-grouping-servers-in-opsmgr-and-configmgr.aspx" target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2009/01/16/automatically-grouping-servers-in-opsmgr-and-configmgr.aspx</a>.</li>
	<li>Tip: Avoid Creating Unnecessary Attributes: The Operations console does not let you delete attributes after they are created, so do not create attributes unless you know you will use them. (To remove an attribute, you must export the management pack, delete the attribute in the XML file, and reimport the management pack.)</li>
	<li>For additional reading on using Service Level Tracking functionality in Operations Manager, seeTip: Finding Objects and Groups for a Report Before Running the Report: How do you know what to use as the “object” or “group” for a report? When you open a report, you must change parameters to specify the start date and the targeted groups or objects. Before you even run the report, review the text at the bottom (the report details section). It specifies which objects provide what information.
<ul>
	<li>Developing SLTs with and without maintenance: <a href="http://blogs.catapultsystems.com/cfuller/archive/2011/09/07/opsmgr-dashboard-integration-developing-slt%E2%80%99s-which-show-availability-with-and-without-maintenance-windows.aspx" target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2011/09/07/opsmgr-dashboard-integration-developing-slt%E2%80%99s-which-show-availability-with-and-without-maintenance-windows.aspx</a></li>
	<li>Targeting in SLT explained: <a href="http://thoughtsonopsmgr.blogspot.com/2010/01/opsmgr-r2-and-service-level-tracking.html" target="_blank">http://thoughtsonopsmgr.blogspot.com/2010/01/opsmgr-r2-and-service-level-tracking.html</a></li>
</ul>
</li>
	<li>New reports include the Performance by System and Performance by Utilization reports, providing answers to some commonly asked questions such as How do you create a simple free disk space report</li>
	<li>Tip: System Center Reporting Tips: For additional tips on using reporting in Operations Manager, see Cameron Fuller’s Windows IT Pro article on 10 OpsMgr 2007 Reporting Tips, available at <a href="http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/10-system-center-operations-manager-reporting-tips-140603" target="_blank">http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/10-system-center-operations-manager-reporting-tips-140603</a>.</li>
	<li>Tip: Configuring Agent Proxying: Because this configuration change is extremely common and often must be performed on a large number of systems, there are a number of ways to configure agent proxying without changing systems one at a time in the Operations console. Here are several to consider:Enabling proxy allows a server to submit discovery data on instances that are higher in the hierarchy than the server itself is. This theoretically increases your attack surface, as it is possible a malicious source that gains control over a machine could inject false discovery data providing invalid information to your management group. While the authors have not heard of such a case occurring, it is important to be aware of the implications of this setting in OpsMgr.
<ul>
	<li>J.C. Hornbeck’s article on enabling agent proxy for a class in System Center Operations Manager 2007 is available at <a href="http://blogs.technet.com/b/operationsmgr/archive/2009/09/29/enabling-agent-proxy-for-a-class-in-system-center-operations-manager-2007.aspx" target="_blank">http://blogs.technet.com/b/operationsmgr/archive/2009/09/29/enabling-agent-proxy-for-a-class-in-system-center-operations-manager-2007.aspx</a>.</li>
	<li>Kevin Holman’s article on how to set agent proxy enabled for all agents is at <a href="http://blogs.technet.com/b/kevinholman/archive/2010/11/09/how-to-set-agent-proxy-enabled-for-all-agents.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2010/11/09/how-to-set-agent-proxy-enabled-for-all-agents.aspx</a>.</li>
	<li>Clive Eastwood’s ProxyCFG tool is available at <a href="http://blogs.technet.com/cliveeastwood/archive/2007/08/30/operations-manager-2007-agent-proxy-command-line-tool-proxycfg.aspx" target="_blank">http://blogs.technet.com/cliveeastwood/archive/2007/08/30/operations-manager-2007-agent-proxy-command-line-tool-proxycfg.aspx</a>.</li>
</ul>
</li>
	<li>During installation, nearly 90 management packs are imported into OpsMgr 2012, providing a minimal amount of monitoring (the number imported varies based on the service pack level you are installing).</li>
	<li>Tip: Management Pack Naming Standards: Developing and using a management pack naming standard can save countless hours and problems when trying to find custom rules, monitors, or determining the appropriate place to store an override. From the authors’ perspective, you should to have a standard, document it, and store it somewhere easy to locate (such as in SharePoint with a web page view pointing to the document library). Pete Zerger from System Center Central has a good discussion on how to choose appropriate naming conventions, available at <a href="http://www.systemcentercentral.com/tabid/145/indexId/73805/Default.aspx" target="_blank">http://www.systemcentercentral.com/tabid/145/indexId/73805/Default.aspx</a>.</li>
	<li>The Operations console management pack download and import options only provide downloads for Microsoft management packs, not any by third parties available in the System Center Marketplace.</li>
	<li>Tip: Providing Multiple SMTP Servers in OpsMgr Channels: OpsMgr supports up to three SMTP servers per channel to provide additional failover in situations where communication does not occur successfully to the primary SMTP server. The authors recommend using all these channels to provide failover even if the servers are highly available Exchange servers (such as an Exchange cluster). For details and why it is relevant in Exchange back pressure situations, see <a href="http://blogs.catapultsystems.com/cfuller/archive/2012/01/09/exchange-back-pressure-amp-opsmgr-notification-channels.aspx" target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2012/01/09/exchange-back-pressure-amp-opsmgr-notification-channels.aspx</a>.</li>
	<li>Command channel notification is like the Swiss army knife of notifications, as you can do pretty much anything with it as it is running a script. As an example, you can use the command channel to create a ticket as discussed at <a href="http://scug.be/blogs/dieter/archive/2011/05/11/scom-setup-command-notification-channel-subscriber.aspx" target="_blank">http://scug.be/blogs/dieter/archive/2011/05/11/scom-setup-command-notification-channel-subscriber.aspx</a>.</li>
	<li>create a unique email channel on a per-subscription basis and specify a different return address for each channel (for example, the SQL alerts return address could be SQLAlerts@odyssey.com). Add your OpsMgr administrators to each subscription and create Outlook rules to classify the alerts based upon the return address so your SQL alerts would route to a specific folder. This provides a quick way to identify what alerts were sent, to whom, and the subscription they came from.</li>
	<li>The message format available in notifications is customizable on a per-channel basis depending upon your requirements. Kevin Holman has gathered a list of the parameters you can use at <a href="http://blogs.technet.com/b/kevinholman/archive/2007/12/12/adding-custom-information-to-alert-descriptions-and-notifications.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2007/12/12/adding-custom-information-to-alert-descriptions-and-notifications.aspx</a>.</li>
	<li>While you can create subscribers for individual email addresses, the recommended approach is to use mail-enabled security groups to avoid the maintenance involved for individual subscriptions. Using mail-enabled security groups simplifies maintenance by using Active Directory to maintain the list of who receives subscriptions.</li>
	<li>When defining subscriptions, understand you cannot exclude a specific alert from notification</li>
	<li>Profiles: Run As profiles allow monitors, rules, and tasks to run as an account with sufficient privileges. As an example, a SQL Server instance may need a different account to provide sufficient access to the databases than the default agent action account.</li>
	<li>You can create up to 254 custom resolution states; you will want to expand on the two built-in states (Closed and New). The authors suggest at least adding the new resolution states of Acknowledged and Assigned to help manage alerts</li>
	<li>Tip: New Alert Resolution states in OpsMgr 2012 service pack: With the release of Service Pack 1 for Operations Manager 2012, several resolution states have been added, which include: Acknowledged (249), Assigned to Engineering (248), Awaiting Evidence (247), Resolved (254), and Scheduled (250).</li>
	<li>Tip: Performance Signature data Grooming: While the user interface says two days is the default performance signature retention period, the actual retention period is two business cycles and these are groomed once per week.</li>
	<li>The authors recommend enabling at least the CEIP and operational data reporting options; these do not affect the operation of the management group or its users, and they provide anonymous data to Microsoft that helps improve the quality of the OpsMgr product.</li>
	<li>the default settings of OpsMgr will fire an alert on a down agent after approximately three minutes, which is the server missed heartbeat setting multiplied by the agent heartbeat interval.</li>
	<li>one of the first views the authors will commonly create is an All Alerts view that displays all alerts regardless of their state. This view provides a quick way to see what alerts are in the database including those in a closed state.</li>
	<li>Jalasoft Xian Wings: Xian Wings provides a mobile platform for Operations Manager that supports the iPhone, iPad, Windows Phone 7, Windows Mobile, Android, and Blackberry devices, displaying information from OpsMgr that includes alerts and performance data and allows you to interact using existing OpsMgr tasks from a mobile device</li>
	<li>Source files for currently installed management packs are located on each management server at %ProgramFiles%System Center 2012Operations ManagerServerHealth Service StateManagement Packs</li>
	<li>It is a best practice to import only the management packs required to meet your monitoring and management goals</li>
	<li>The Web Application Monitoring template provides a quick way to add large numbers of URLs for monitoring in OpsMgr, with agents or resource pools serving as watcher nodes.</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 08: Installing And Configuring Agents</h3>
<div style="color: #000000;">
<ul>
	<li>The OpsMgr admin specifies if the management server action account or another account with administrator-level privileges will be used. The specified account is used for discovery with Active Directory and to push the agent to the system that will be monitored.</li>
	<li>If the option to verify discovered computers was selected (the advanced computer discovery option in step 2), each client is contacted through ports 135, 137, 139, 445, and 5723.</li>
	<li>The action account uses either Local System or the specified domain account to create tasks to deploy the agents</li>
	<li>To discover machines residing in non-trusted domains and workgroups, provide the computer name in the format &lt;domain&gt;&lt;ComputerName&gt; or &lt;workgroup&gt;&lt;ComputerName&gt;.</li>
	<li>Pete Zerger provides a two-part blog post with an example of how to identify those computers in Active Directory that do not have the Operations Manager agent (see part 1 at <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94221/Default.aspx).">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94221/Default.aspx).</a> After identifying these computers, you can automate agent installation with PowerShell (discussed in part 2, at <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94248/Default.aspx).">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94248/Default.aspx).</a> You can schedule these scripts to run on a recurring basis using the Windows task scheduler</li>
	<li>Using these performance counters, you can determine the overhead added by OpsMgr. During testing by the authors, the OpsMgr processor impact to servers typically was less than 2%;</li>
	<li>Microsoft has also added the Agent processor utilization monitor, which alerts if the agent utilization exceeds a threshold of 25% over a set of six consecutive samples.</li>
	<li>Table 8.1. OpsMgr 2012 agent and agentless monitored resource requirements during deployment</li>
	<li>Table 8.2. OpsMgr 2012 agent and agentless monitored resource requirements after deployment</li>
	<li>OpsMgr 2012 supports up to 10 agentless managed systems reporting to a single management server, and 60 in a management group</li>
	<li>With the release of System Center 2012 Service Pack (SP) 1, a Service Manager server can now have an agent installed that reports to Operations Manager in a multi-homed configuration.</li>
	<li>Active Directory Integration (provides agent configuration information, but does not actually install the agent)</li>
	<li>Although you can use OpsMgr to monitor client operating systems, most organizations typically only monitor servers (this is often a licensing-based decision)</li>
	<li>This pack provides the ability to monitor the availability, configuration, and performance of Windows client operating systems</li>
	<li>Tip: Extending Desktop Monitoring: At the Microsoft Management Summit (MMS) 2012, Infront Consulting Group demonstrated its Business Critical Desktop Monitoring management pack; this augments existing Operations Manager client monitoring by providingAdditional information on this pack and others available from Infront Consulting Group is available at <a href="http://www.infrontconsulting.com/software.php" target="_blank">http://www.infrontconsulting.com/software.php</a>.
<ul>
	<li>Monitoring for desktop and application health.</li>
	<li>Identification for currently logged on users and systems pending reboot.</li>
	<li>Associating users with their desktop for easier identification.</li>
	<li>Tasks for remediation include the ability to reboot a workstation, enable remote desktop, set current user as registered owner, and explore the remote C: drive.</li>
</ul>
</li>
	<li>Tip: The “Universal Linux” Monitoring Packs: Support for the new UNIX operating systems added with SP 1 is implemented using the “Universal Linux” monitoring packs. Here are the MP files required to add monitoring for these operating systems:The Operations Manager management server must be able to resolve the name of the OpsMgr agent and vice versa. To validate name resolution is working correctly, ping the fully qualified name of the agent from the management server, and the management server from the agent.
<ul>
	<li>Microsoft.Linux.Universal.Library.mp</li>
	<li>Microsoft.Linux.Universal.Monitoring.mp</li>
	<li>Microsoft.Linux.UniversalD.1.mpb (to support Debian and Ubuntu Linux agents)</li>
	<li>Microsoft.Linux.UniversalR.1.mpb (to support CentOS Linux agents)</li>
</ul>
</li>
	<li>An account must exist with access to the system to install the agent. On Windows, the account requires local administrator rights. On UNIX/Linux systems, the account either needs to have privileged access or the rights to use sudo or su elevation.</li>
	<li>Tip: UNIX/Linux system not Monitored: When a UNIX system shows as not monitored, this is usually because a Run As account is not assigned. As there is no local system account on UNIX, you must create a UNIX/Linux account and assign it to the UNIX/Linux Action Account RunAs profile.</li>
	<li>This means traffic must be able to route between the two servers, and the port the agent communicates with needs to be open for communication and reachable by the agent. To validate communication is working correctly, telnet from the agent to the server or from the server to the agent on the appropriate communication port. (This is port 5723 from the agent to the management server for Windows, 1270 from the management server to the agent for UNIX/Linux.)</li>
	<li>UNIX/Linux Management Pack Requirements: UNIX/Linux agents cannot have the Operations Manager agent installed until the appropriate UNIX/Linux OS management pack is imported. While the core UNIX/Linux libraries are imported when you install System Center 2012 Operations Manager, you must add the complete management packs for each OS version before attempting to monitor UNIX/Linux agents. These management packs are available on the installation media in the ManagementPacks folder or you can download them from the System Center Marketplace.</li>
	<li>The list of currently available management packs for UNIX/Linux includes individual downloads for the different versions of AIX, HP, Linux, and Solaris. Separate management packs are also available for ACS functionality on these operating systems.</li>
	<li>Agents deployed using the Discovery Wizard do not pull their information from Active Directory, even if Active Directory Integration is in place.</li>
	<li>Agents deployed through the Discovery Wizard are defined to report to a specific management server. Should the management server fail, they fail over to another management server.</li>
	<li>The best practice recommendation by the authors is to use the Discovery Wizard to discover and deploy agents in all but the largest of OpsMgr environments.</li>
	<li>Tip: Avoid using the servers only Option in the Discovery Wizard: It is a best practice to not use the Servers Only option during a discovery as the filter requires contacting each machine for verification. This process slows down the discovery and can lead to discovery failures from timeouts. The Servers Only option is most useful when doing an extremely filtered LDAP query for specific machines versus a large-scale discovery.</li>
	<li>Check the option Verify discovered computers can be contacted. This often increases the success rates of the deployment because only systems that can be communicated with over the network are listed for selection.</li>
	<li>The discovery can return approximately 4,000 computers if the verify option is selected, and approximately 10,000 computers if not selected.</li>
	<li>Note: Discovery Wizard Stuck on “Discovery is in Progress”Tip: Trust Requirements to Deploy Agents: Agent authentication in OpsMgr requires Kerberos or certificate-based authorization to provide mutual authentication. Use certificate-based authorization for gateway configurations where agents are in untrusted domains or workgroups. Within a forest, transitive two-way trusts are automatically created that support Kerberos.
<ul>
	<li>There are three common causes of having the Discovery Wizard become non-responsive according to an article by System Center MVP Marnix Wolf:</li>
	<li>SQL Broker Service is not running; see <a href="http://support.microsoft.com/kb/941409" target="_blank">http://support.microsoft.com/kb/941409</a> for further information.</li>
	<li>SPNs are not set correctly.</li>
	<li>Health Service Store on the MS is corrupted.</li>
	<li>Marnix’s blog article on this topic is available at <a href="http://thoughtsonopsmgr.blogspot.com/2010/08/discovery-wizard-is-running-for-ever.html" target="_blank">http://thoughtsonopsmgr.blogspot.com/2010/08/discovery-wizard-is-running-for-ever.html</a>. Additional discussions on troubleshooting discovery in perations Manager are available at <a href="http://go.microsoft.com/" target="_blank">http://go.microsoft.com/</a>.</li>
</ul>
</li>
	<li>Prerequisites for UNIX/Linux AgentsUsing the wizard is the easiest way for deploying OpsMgr agents to UNIX/Linux systems as well as Windows systems. Before running the wizard, import the appropriate UNIX/Linux management packs, create a resource pool to monitor the agents, create configuration certificates, define the Run As accounts, and identify the IP address(es) of the systems
<ul>
	<li>For UNIX/Linux agents to be discovered correctly, here are several required steps before running the Discovery Wizard:
<ul>
	<li>Import management packs required for UNIX/Linux monitoring, discussed in the “UNIX/Linux Management Pack Requirements” section.</li>
	<li>Create a resource pool for monitoring UNIX/Linux servers, performed at Administration -&gt; Resource Pools. Create a new resource pool and add the appropriate management servers to that resource pool.</li>
	<li>Configure the cross platform certificates (export/import) for each management server in the pool. Information on this process is available at <a href="http://technet.microsoft.com/en-us/library/hh287152.aspx.">http://technet.microsoft.com/en-us/library/hh287152.aspx.</a> Details on certificates, troubleshooting agent deployment, and other topics related to UNIX/Linux servers are discussed in Chapter 20, “Interoperability and Cross Platform.”</li>
	<li>Create and Configure Run As accounts for UNIX/Linux systems; see <a href="http://technet.microsoft.com/en-us/library/hh212926.aspx">http://technet.microsoft.com/en-us/library/hh212926.aspx</a> for additional information.</li>
</ul>
</li>
</ul>
</li>
	<li>Tip: Privileged and Unprivileged Accounts in OpsMgr 2012: A commonly asked question is What are the actual differences between a UNIX/Linux privileged and unprivileged account in OpsMgr 2012?</li>
	<li>A privileged account needs to have root-level access to the system including access to security logs and Read, Write, and Execute permissions within the directories where the OpsMgr agent was installed.</li>
	<li>An unprivileged account is a normal user account without root access or special permissions, but you can use the account for monitoring system processes and performance data.</li>
	<li>Tip: Additional Cross Platform Discovery Wizard Information: There are some excellent additional resources available online for UNIX/Linux agent information. Here are some of the authors’ favorites:Tip: Upgrading Manually Installed Agents: Once an agent is installed manually, any update rollups must be manually applied. Cameron Fuller provides a method to update manually installed agents through the Operations console, available at <a href="http://blogs.catapultsystems.com/cfuller/archive/2012/04/27/how-to-upgrade-clients-to-cu5-which-were-manually-installed-in-opsmgr-scom-sysctr.aspx.">http://blogs.catapultsystems.com/cfuller/archive/2012/04/27/how-to-upgrade-clients-to-cu5-which-were-manually-installed-in-opsmgr-scom-sysctr.aspx.</a> This builds upon Kevin Holman’s article at <a href="http://blogs.technet.com/b/kevinholman/archive/2010/02/20/how-to-get-your-agents-back-to-remotely-manageable-in-opsmgr-2007-r2.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2010/02/20/how-to-get-your-agents-back-to-remotely-manageable-in-opsmgr-2007-r2.aspx</a>.
<ul>
	<li>The wiki for UNIX/Linux agent deployment at <a href="http://social.technet.microsoft.com/wiki/contents/articles/4966.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/4966.aspx</a></li>
	<li>Kevin Holman’s blog article on deploying UNIX/Linux agents using OpsMgr 2012 at <a href="http://blogs.technet.com/b/kevinholman/archive/2012/03/18/deploying-unix-linux-agents-using-opsmgr-2012.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2012/03/18/deploying-unix-linux-agents-using-opsmgr-2012.aspx</a>.</li>
</ul>
</li>
	<li>The recommended way to install the agent is running the Setup.exe program on the root of the installation media and choosing the Local Agent option. This runs the MOMAgent.msi file for the appropriate platform and turns on logging during the installation</li>
	<li>Tip: When to Use Active Directory Integration: Jonathan Almquist provides an insightful blog article discussing when one should use Active Directory Integration in OpsMgr, available at <a href="http://blogs.technet.com/b/jonathanalmquist/archive/2010/06/14/ad-integration-considerations.aspx.">http://blogs.technet.com/b/jonathanalmquist/archive/2010/06/14/ad-integration-considerations.aspx.</a> His main point about AD Integration is that while it provides a way to facilitate including the OpsMgr agent in a server image, AD Integration is not very forgiving of mistakes made. In most cases, you can avoid AD Integration by using the command shell to assign primary and failover configuration, unless the goal is to include the OpsMgr agent in a server image.</li>
	<li>Tip: How Active Directory Integration Works: Steve Rachui put together an excellent blog article explaining how AD Integration works in OpsMgr 2007. AD Integration has not changed significantly since OpsMgr 2007, so this article still applies to OpsMgr 2012 and is available at <a href="http://blogs.msdn.com/b/steverac/archive/2008/03/20/opsmgr-ad-integration-how-it-works.aspx" target="_blank">http://blogs.msdn.com/b/steverac/archive/2008/03/20/opsmgr-ad-integration-how-it-works.aspx</a>.</li>
	<li>Microsoft documentation provides a comprehensive list of ports that are required for Operations Manager 2012, available at <a href="http://technet.microsoft.com/en-us/library/hh205990.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh205990.aspx</a>. However, the most commonly asked question focuses specifically around what ports are required to install OpsMgr agents and those that are necessary to support OpsMgr communication from the agents. Here are the ports required to install OpsMgr agents:Note: Agent Push and Firewalls
<ul>
	<li>Windows agent push installation, repair, or upgrade requires TCP 135, 139, 445, 5723, UDP 137, 138.</li>
</ul>
</li>
	<li>The OpsMgr agent is pushed using RCP/DCOM from the management server or gateway server to the system to which the agent will be installed. For agent push installation to succeed, the Windows Firewall on the server and agent must be configured to have exceptions allowing the appropriate management or gateway server(s) to communicate with the system. If the Windows Firewall is disabled on the system, the firewall exceptions are not required. The default “Domain Profile” Windows Firewall will allow agent push without modification.</li>
	<li>UNIX/Linux agent push installation requires communication from the pool of management servers monitoring UNIX/Linux systems: TCP 22 (SSH), 1270 (inbound).</li>
	<li>The required ports to maintain communication areTo change an agentless system to agent-managed, you must first delete the agentless managed system and then deploy the agent to the system
<ul>
	<li>OpsMgr agent communications to management servers on TCP 5723.</li>
	<li>If ACS is active on the agent, the ACS forwarder port is required to the ACS collector; this is TCP 51909.</li>
	<li>IF AEM is active on a system, the AEM information port is required to the AEM server; this is TCP 51906.</li>
	<li>UNIX/Linux agent communication from the pool of management servers monitoring UNIX/Linux systems; port TCP 22 (SSH), 1270 (inbound).</li>
</ul>
</li>
	<li>Here are recommended actions to check and verify the health of a Windows OpsMgr agent:
<ul>
	<li>1. First, verify agent health in the Operations console at Administration -&gt; Agent Managed. If the agent is grey, this indicates it is not communicating with OpsMgr. If the agent is not monitored, it has not reached a monitored state or it is in maintenance mode.</li>
	<li>2. Verify agent health in the Monitoring pane under Operations Manager -&gt; Agent Details -&gt; Agent Health State view. This view provides health state information from both the agent and the Health Service Watcher.</li>
	<li>3. Check the Computer view in the Monitoring pane to verify that the agent and operating system are monitored. Here are some reasons the OS may not be monitored:
<ul>
	<li>The system has not been identified with an OS that can be monitored with an installed management pack.</li>
	<li>The system is agentless monitored.</li>
	<li>The system is experiencing issues deploying the OS-specific management pack.</li>
</ul>
</li>
	<li>4. Review the Agent Details -&gt; Active Alerts view to review alerts that may be affecting the agent’s health.</li>
	<li>5. Access the Operations Manager log remotely or locally to identify critical or warning errors occurring on the system.</li>
</ul>
</li>
	<li>Here are recommended steps for checking and verifying the health of a UNIX/Linux OpsMgr agent:Steps to perform this action include using a SQL query to update the agent’s values for IsManuallyInstalled to 0. Making this change causes this agent to be seen in OpsMgr as a remotely manageable agent. Once an agent is listed as remotely manageable, it can be repaired for you to apply the current update rollup and then flush the health cache on the agent
<ul>
	<li>1. Verify agent health in the Administration -&gt; UNIX/Linux Computers node. If the agent is grey, this indicates it is not communicating with OpsMgr. If the agent is not monitored, it has not reached a monitored state or is in maintenance mode.</li>
	<li>2. Check the UNIX/Linux Computer view in the Monitoring pane to verify the agent and the operating system are monitored. Here are some reasons the OS may not be monitored:
<ul>
	<li>The system has not been identified with an OS that can be monitored with an installed management pack.</li>
	<li>The UNIX/Linux Default Action Account has not been defined for UNIX/Linux systems.</li>
	<li>The system is experiencing issues deploying the OS-specific management pack.</li>
</ul>
</li>
</ul>
</li>
	<li>The exception to the default event log size rule may be applications that are extremely intensive on the application or system logs such as Microsoft Exchange (historically, this had a recommended 40MB application event log according to the Exchange Best Practices Analyzer information available at <a href="http://technet.microsoft.com/en-us/library/aa997362" target="_blank">http://technet.microsoft.com/en-us/library/aa997362</a>), or custom-built applications.</li>
	<li>If there is a requirement to increase the log file sizes, you can do this directly through the event viewer application or by creating a group policy. For maximum recommended event log sizes per platform, see <a href="http://support.microsoft.com/kb/957662" target="_blank">http://support.microsoft.com/kb/957662</a>.</li>
	<li>There have been discussions in the OpsMgr newsgroups about problems when the agent heartbeat frequency is set to less than the default of 60 seconds. Additionally, if this value is increased it delays any heartbeat alerts that may occur.</li>
	<li>Agent failover is often a misunderstood topic in Operations Manager. To dispel a myth here first—agent failover is built into OpsMgr even without using AD Integration. If a management server fails in OpsMgr, the agent is moved to another management server. The challenge is that within the user interface there is no way to specify a management server. To define how agents fail over you must either use AD Integration or PowerShell scripts.</li>
	<li>An Operations Manager agent stores data that must be sent to the management server in a queue file. The queues prevent loss of data when a management server is not available (such as when rebooted to apply patches and other maintenance).</li>
	<li>These queues default to 15MB in size (15,360KB). For most systems, this should be sufficient to hold the OpsMgr data for several hours</li>
	<li>You can change the size of this queue on a per-agent basis in the registry at HKLMSYSTEMCurrentControlSetServicesHealthServiceParametersManagement Groups&lt;Management Group Name&gt;MaximumQueueSizeKb.</li>
	<li>Those systems monitored by Operations Manager that have their name changed must have the agent removed and reinstalled. If the renamed system does not have its agent uninstalled and reinstalled, the original system name still appears in the console, but no longer reports information back correctly to OpsMgr.</li>
	<li>agentless managed systems are systems monitored by a proxy agent that performs the actual monitoring rather than deploying an agent to the system you are monitoring, while Agentless Exception Monitoring captures aggregates and reports on application crashes (Dr. Watson errors) within your management group.</li>
	<li>Troubleshooting the Installation of the System Center Operations Manager Agent: <a href="http://support.microsoft.com/kb/2566152" target="_blank">http://support.microsoft.com/kb/2566152</a></li>
	<li>Console based Agent Deployment Troubleshooting table: <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexId/60047/Default.aspx" target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexId/60047/Default.aspx</a></li>
	<li>Troubleshooting UNIX/Linux AgentsAgents and pools: Windows agents do not report to pools in Operations Manager 2012—they still report to Operations Manager servers. Cross platform agents do report to pools in Operations Manager 2012.
<ul>
	<li>Here are recommended articles to review when troubleshooting deployment of UNIX/Linux agents in OpsMgr:
<ul>
	<li>Troubleshooting UNIX/Linux Agent Discovery in System Center 2012 - Operations Manager: <a href="http://social.technet.microsoft.com/wiki/contents/articles/4966.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/4966.aspx</a></li>
	<li>Installing sudo on Solaris: <a href="http://sysinfo.bascomp.org/solaris/installing-sudo-on-solaris/" target="_blank">http://sysinfo.bascomp.org/solaris/installing-sudo-on-solaris/</a></li>
	<li>Enable ssh root login in Solaris 10: <a href="https://blogs.oracle.com/sunrise/entry/enable_ssh_root_login_in" target="_blank">https://blogs.oracle.com/sunrise/entry/enable_ssh_root_login_in</a></li>
</ul>
</li>
</ul>
</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 09: Complex Configurations</h3>
<div style="color: #000000;">
<ul>
	<li>When designing for OpsMgr, you should consider two areas: the functional area that identifies and describes the requirements, and the technical design that maps those requirements to a certain technical solution.</li>
	<li>Using NLB, you can create an NLB cluster of some or all management servers. When the Operations console connects to that NLB cluster and a connection to a node in the cluster fails, it is automatically redirected to another management server.</li>
	<li>Incorporating NLB makes the Web console more useful as you can also make it highly available</li>
	<li>A two-node failover cluster requires at a minimum the enterprise version of the Windows Server operating system and the standard edition of SQL Server.</li>
	<li>Microsoft officially supports failover clustering for the OpsMgr operational database, data warehouse database, and audit database</li>
	<li>Microsoft does not support making SQL Server Reporting Services (SSRS) highly available for OpsMgr,</li>
	<li>default, the OpsMgr databases are installed using the simple recovery model. Log shipping only functions when replay of the log can take place, which does not occur with the simple recovery model. This means you must change to a full recovery model for those databases, resulting in larger transaction log files, which requires more disk space for each SQL database and SQL Server system.</li>
	<li>OpsMgr has specific requirements for SQL collation settings</li>
	<li>The operational and data warehouse (OperationsManager and OperationsManagerDW) databases are installed using the simple recovery model. A simple recovery model results in an empty transaction log since transactions are truncated from the log once they are written to the database.</li>
	<li>Tip: Online Resources for Log Shipping: For a detailed guide about configuring log shipping for OpsMgr, see <a href="http://social.technet.microsoft.com/wiki/contents/articles/11372.configure-sql-server-log-shipping-guide-for-the-system-center-operations-manager-2007-r22012-operational-database.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/11372.configure-sql-server-log-shipping-guide-for-the-system-center-operations-manager-2007-r22012-operational-database.aspx</a>.</li>
	<li>The console requires the System Center Data Access Service (DAS).</li>
	<li>You can use Network Load Balancing to make the System Center Data Access Service highly available.</li>
	<li>Here are the high-level steps to set up NLB for the DAS:Tip: Resources for Network Load Balancing the data Access Service: Microsoft TechNet is an excellent resource for information about network load balancing the DAS. You can begin with <a href="http://technet.microsoft.com/en-us/library/hh316108.aspx,">http://technet.microsoft.com/en-us/library/hh316108.aspx,</a> which contains references to other TechNet articles about NLB. These are must-reads for anyone interested in using network load balancing for the System Center Data Access Service.
<ul>
	<li>1. Configure static IP addresses for all nodes participating in the NLB cluster.</li>
	<li>2. Enable NLB for each management server participating in the NLB cluster.</li>
	<li>3. Create the NLB cluster with its Virtual IP (VIP) address.</li>
	<li>4. Add one or more additional hosts—running the System Center Data Access Service (this could be any OpsMgr management server)—to the NLB cluster.</li>
	<li>5. Create a host record in DNS referring to the VIP address.</li>
</ul>
</li>
	<li>The procedure required to network load balance the Web console is similar to that used for the System Center Data Access Service. Here are the high-level steps:Neil Harrison of Microsoft has written a series of blog postings about ACS high availability; see <a href="http://blogs.technet.com/b/neharris/archive/2011/03/22/acs-forwarders-and-high-availability-part-1.aspx" target="_blank">http://blogs.technet.com/b/neharris/archive/2011/03/22/acs-forwarders-and-high-availability-part-1.aspx</a>.
<ul>
	<li>1. Configure static IP addresses for all nodes participating in the NLB cluster.</li>
	<li>2. Enable NLB for each management server participating in the NLB cluster.</li>
	<li>3. Create the NLB cluster with its VIP address.</li>
	<li>4. Add one or more additional hosts—running the OpsMgr Web console—to the NLB cluster.</li>
	<li>5. Create a host record in DNS referring to the VIP address.</li>
</ul>
</li>
	<li>ACSConfig.xml is updated every 5 minutes by the AdtServer service.</li>
	<li>A mechanism is in place (such as a scheduled task) that copies ACSConfig.xml every 5 minutes from the active to the passive collector</li>
	<li>Anders Bengtsson of Microsoft has an excellent post on how to eliminate both SPOFs at <a href="http://contoso.se/blog/?p=831" target="_blank">http://contoso.se/blog/?p=831</a>.</li>
	<li>For information about configuring gateway server failover between management servers, see <a href="http://technet.microsoft.com/en-us/library/hh456445.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh456445.aspx</a>. Anders Bengtsson provides a blog posting at <a href="http://contoso.se/blog/?p=831" target="_blank">http://contoso.se/blog/?p=831</a> that also shows how to configure the agent for automatic failover</li>
	<li>While OpsMgr 2012 lets you create your own resource pools, here are some considerations:If running an OpsMgr environment with more than two management servers and you want to divide the different monitoring workloads, you could create dedicated resource pools for monitoring things such as network devices or UNIX/Linux systems
<ul>
	<li>Creating dedicated resource pools for UNIX/Linux, URL, and network monitoring allows you to scale out easily when having resource issues without affecting the other monitoring workflows.</li>
	<li>Only create a new resource pool when there is a requirement for it and an additional pool makes sense.</li>
	<li>Populate your new/custom resource pools wisely. For example, installing two additional management servers and placing them into three custom resource pools is counterproductive; those management servers would have to run the workloads of all three resource pools combined. A good rule of thumb is having at least one dedicated management server allocated to each resource pool you create.</li>
</ul>
</li>
	<li>Similar to any other OpsMgr agent, it compresses traffic sent to its management server</li>
	<li>Helpful Resources for Multi-Homing Agents Using Scripting APIS</li>
	<li>During agent deployment, its control panel applet is installed/registered with AgentConfigManager.dll. This DLL file contains useful .NET functions that you can reference and call using PowerShell, VBScript, and so on.</li>
	<li>Here are some resources about how to use these .NET functions:The authors want to thank Kevin Holman for his posting about the agent control panel applet. The same posting also contains references about the .NET functions contained by the DLL file and using them; see <a href="http://blogs.technet.com/b/kevinholman/archive/2011/11/10/opsmgr-2012-new-feature-the-agent-control-panel-applet.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2011/11/10/opsmgr-2012-new-feature-the-agent-control-panel-applet.aspx</a>.
<ul>
	<li>Copying and registering the script library: <a href="http://msdn.microsoft.com/en-us/library/hh329076.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/hh329076.aspx</a></li>
	<li>Adding and removing a management group: <a href="http://msdn.microsoft.com/en-us/library/hh329017.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/hh329017.aspx</a></li>
	<li>Displaying management group information: <a href="http://msdn.microsoft.com/en-us/library/hh352628.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/hh352628.aspx</a></li>
</ul>
</li>
	<li>You cannot connect management groups of different builds. This also means an OpsMgr 2007 management group cannot be connected with an OpsMgr 2012 management group.</li>
	<li>Microsoft provides documentation about OpsMgr connected management groups at <a href="http://technet.microsoft.com/en-us/library/hh230698.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh230698.aspx</a>. The authors strongly advise reading this article before connecting OpsMgr management groups.</li>
	<li>Here are the high-level steps that describe an approach to use when designing and building a distributed OpsMgr environment:While often people think a minimum network speed of 64Kbps between a single agent and a management server is required, this actually is not true; this is the minimum connection Microsoft supports for an agent. Average traffic on a single agent is 500 bytes per second (~4Kb/s).
<ul>
	<li>Start with design. Begin with placement of your management group, including required SQL servers. Provision enough room for growth on the database servers and for additional management servers. When a LAN segment has only four IP addresses available, it is best to use another LAN segment. When running a virtualized OpsMgr management group, ensure the hosts are not overcommitted and the storage area network (SAN) is not configured for best capacity instead of best IOPS, as that will seriously hamper I/O performance.</li>
	<li>Place the servers hosting the OpsMgr databases and SSRS with your management servers in the same LAN segment. This way traffic will flow quickly without routers between them, benefitting the overall performance and stability of your OpsMgr environment. This guarantees the highest bandwidth and lowest latency.</li>
	<li>Ensure the location where your management group resides is connected by high-speed WAN links to the other geographical locations. You will want to have the best WAN connections available for your monitoring environment. Often you will end up placing the OpsMgr management group in the corporate data center.</li>
	<li>For each geographical location, inventory what needs to be monitored. In addition to the total amount of servers or network devices, it is important to know the applications and services you will be monitoring. The more there is to monitor, such as business critical applications, websites, and .NET applications, the more network traffic is sent over the WAN connection to the management group.</li>
</ul>
</li>
	<li>Refrain from installing management servers outside the LAN segment where the management group resides even when wide WAN links are in place. This will eventually hamper the overall functionality, availability, and stability of the entire management group.</li>
	<li>This was true with OpsMgr 2007, but is even more so in Operations Manager 2012, as the resource pools require very low latency because of heartbeat detection between management servers in any given resource pool. The management servers need to be close to or on the same segment as the databases. There are no exceptions to this design principle; when a particular geographical location is large enough for its own management server, you may want to consider providing a dedicated management group at that location.</li>
	<li>Keep your Operations consoles under tight scrutiny. Too many concurrent console connections can affect the overall performance of the management group. In addition, when these consoles require updates or extensions, you know exactly which consoles to update rather than having people complain that console functionality is broken. You will want to keep the installation bits required for the console installation at a location with limited access.</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 10: Security and Compliance</h3>
<div style="color: #000000;">
<ul>
	<li>Securing Operations Manager includes utilizing role-based security, Run As profiles, Run As accounts, and understanding the various OpsMgr service accounts.</li>
	<li>The Operations console includes access to more than 150 available operations, which fall under the following categories:Role-based access control utilizes Microsoft’s Windows Authorization Manager (AzMan) framework
<ul>
	<li>Monitoring: These operations include opening views, resolving alerts, executing tasks, and overriding monitors. These views help you analyze monitoring needs.</li>
	<li>Authoring: Authoring includes creating and modifying objects to customize or supplement the default monitoring settings provided by management packs.</li>
	<li>Reporting: Reporting operations consist of using and designing reports and managing report security.</li>
	<li>Administration: Administrative operations include configuring security, importing, exporting, and removing management packs, changing global settings, discovering computers and devices, configuring notification, and installing agents.</li>
</ul>
</li>
	<li>The OpsMgr store contains user roles and their scoping. The store for OpsMgr 2007’s implementation of AzMan was an XML file named MomAuth.xml; in OpsMgr 2012, the store is maintained across multiple AzMan tables in the operational database.</li>
	<li>It is a Windows Communication Foundation (WCF)-based web service that all data access in Operations Manager passes through, and represents a single point of control for security authentication and authorization checks</li>
	<li>The Data Access Service accesses the database over ADO.Net (with a default port of 1433) using the security context under which the service runs</li>
	<li>Out of the box, Operations Manager provides the user roles and profiles listed in Table 10.1. Information on specific operations associated with each is available at <a href="http://technet.microsoft.com/en-us/library/hh872885" target="_blank">http://technet.microsoft.com/en-us/library/hh872885</a>.</li>
	<li>You can add Active Directory (AD) security groups or individual accounts to any of the predefined user roles or to a role that you create</li>
	<li>Should you create a user role based on the Author or Advanced Author profiles, be sure these users have access to an installation of the Operations console to perform the tasks allowed by those profiles.</li>
	<li>The Administrators role differs from other user roles as you can only add Active Directory security groups to this role, not individual users. In addition, when you add a group to the Operations Manager Administrators user role, you must restart the management server to which you are connected for the change to take effect.</li>
	<li>Similar to Windows file system security, when a user account is a member of multiple roles, access is the combination of what is granted to all those roles.</li>
	<li>Creating a Report Operator Role: The Report Operator role grants the users belonging to that role the ability to run audit reports; however, the Operations console does not include the capability of creating this role, nor does the new PowerShell Set-SCOMUserRole cmdlet support creating the Report Operator role.</li>
	<li>The good news is you can still load the OpsMgr 2007 PowerShell snap-in to use the workarounds previously developed for this. This line of code tells PowerShell to load the Microsoft.EnterpriseManagement.OperationsManager.Client snap-in, so the old commands will be recognized:System Center Operations Manager 2007 Unleashed (Sams, 2008) discussed using a script provided by Eugene Bykov of Microsoft to create a Report Operator role in OpsMgr 2007, modified by Neal Browne to be parameter-driven. As discussed at <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94404/Default.aspx" target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94404/Default.aspx</a>, by incorporating the OpsMgr 2007 PowerShell snap-in and changing the script to be a function, you can continue to use the 2007 code rather than delving into .NET methods to create a script that would accomplish the same thing in OpsMgr 2012.
<ul>
	<li>Add-PSSnapin Microsoft.EnterpriseManagement.OperationsManager.Client</li>
</ul>
</li>
	<li>Management pack components such as rules, monitors, tasks, and discoveries require credentials to run on the targeted computer. These components run using the credentials of the MSAA by default.</li>
	<li>A Run As profile allows a management pack author to associate an identity other than the default action account with a particular module, letting it run using the credentials of that entity. The account used must have the Allow Logon Locally right.</li>
	<li>OpsMgr 2012 automatically creates a number of Run As profiles during setup. Unless otherwise specified, the default action account is used by a Run As profile if another account is not assigned to that profile</li>
	<li>Rather than assigning additional rights to an action account, using Run As accounts and Run As profiles provides the ability to run a task, rule, or monitor using an account with the necessary rights.</li>
	<li>When OpsMgr tries to use that account, it will generate an alert if the account is not configured properly. As a best practice, verify the account exists and its credentials are adequate before using it as a Run As account. The authors also recommend using an account with a non-expiring password.</li>
	<li>Required Accounts: System Center 2012 Operations Manager uses a number of service and action accounts. Here are some things to keep in mind regarding these accounts:Table 10.4. Service accounts required for OpsMgr 2012 installation
<ul>
	<li>If you use domain accounts and your domain group policy object (GPO) allows passwords to expire, you must either change the passwords on the service accounts according to your password expiration policy, override the settings for these accounts so the passwords will not expire, or use low maintenance system accounts. Password information entered for accounts is stored, encrypted, in the operational database.</li>
	<li>You may want to consider using built-in accounts where that is practical, as the operating system maintains these accounts and they are not affected by password expiration policies. In addition, the passwords to these accounts are not exposed.</li>
</ul>
</li>
	<li>The action account is granted write access to the operational and data warehouse databases. The MSAA needs at least the following privileges:Tip: Best Practices for the Management Server Action Account: Microsoft recommends using the same MSAA on all management servers, which should be a domain account rather than Local System, except when used in a lab or very small environment.</li>
	<li>
<ul>
	<li>Member of the local Users group</li>
	<li>Read access to the Windows event logs</li>
	<li>Member of the Performance Monitor Users group</li>
	<li>Granted the Allow Logon Locally right</li>
</ul>
</li>
	<li>Using a Low-Privileged Account on the Agent: For older operating systems such as Windows XP, the agent action account must have administrative rights to the system. For other operating systems, you usually can use a low-privileged account for the action account. This is the preferred approach, as you can use Run As profiles for anything requiring a higher level of access. When using a low-privileged account, the account must have the following minimum privileges:These are the lowest privileges OpsMgr supports for the action account. Other Run As accounts can have lower privileges.</li>
	<li>
<ul>
	<li>Member of the local Users group</li>
	<li>Member of the Performance Monitor Users group</li>
	<li>Granted the Allow Logon Locally right</li>
</ul>
</li>
	<li>When you specify a domain account for the action account, you may need to add privileges to the account for various management packs to function properly. Table 10.5 lists these privileges.</li>
	<li>Table 10.5. Permissions required for the action account</li>
	<li>The actual privileges necessary for the action account and the Run As accounts vary, depending on the management packs running on the computer and how those are configured.</li>
	<li>Each management pack has its own profile; rights and privileges for each profile are added together, giving the effective rights.</li>
	<li>You cannot enable Agentless Exception Monitoring (AEM) on a management server with a low-privileged action account.</li>
	<li>For systems running Windows XP, the action account must be a member of the local Administrators security group or run as Local System. The Local System account has high privilege levels on the local system as it is a member of the Administrators security group</li>
	<li>Newer operating systems have additional built-in accounts. The built-in Network Service account has fewer access privileges than Local System, but the Network Service account is able to interact throughout the network with the credentials of the computer account.</li>
	<li>the requirement to communicate with the management server prevents use of the Local Service account, as it has no rights to communicate outside the local computer. The Network Service account has that right.</li>
	<li>Real World: Using Local System for the Default Action Account</li>
	<li>Microsoft recommends using Local System as the default action account:Both the System Center Configuration Service and System Center Data Access Service use the System Center Configuration Service and System Center Data Access Service account to update information in the operational database
<ul>
	<li>It provides the necessary rights to monitor a local machine.</li>
	<li>It is secure and low maintenance.</li>
	<li>Many management packs require using Local System.</li>
</ul>
</li>
	<li>You can run this as Local System or specify a domain user account that has local Administrator privileges; a local user account is not supported</li>
	<li>If you install the operational database on a server other than the first management server and select Local System for this account, the computer account for the management server is assigned to the sdk_user role in the operational database</li>
	<li>The account used by the Computer and Device Management Wizard for computer discovery is either the MSAA or an account with administrative privileges on the targeted computer(s).</li>
	<li>As this account installs the agent on targeted computers, it must have local Administrator rights on all systems to which the agents are deployed.</li>
	<li>The Data Warehouse Write account is used to insert and update information in the data warehouse database. This account writes data from the management servers to the data warehouse and reads data from the operational database. The credentials used for this account are assigned to the OpsMgrWriter role in the data warehouse database, and the dwsynch_users role in the operational database.</li>
	<li>The Data Reader account runs and manages reports. The credentials used for this account are assigned to the OpsMgrReader role in the data warehouse database, and are added to the Operations Manager Report Security Administrators role. The Data Reader account becomes the identity for the Report Server application pool in IIS</li>
	<li>The System Center Management service account must run using the credentials of Local System. This account registers SPNs (Service Principal Names); using credentials other than Local System results in duplicate SPNs. Microsoft does not support running the System Center Management service account under any credentials other than Local System</li>
	<li>Gateway Action Account: If you install a gateway server, you must provide credentials for an action account. This actually is an MSAA for the gateway server. Gateway servers in remote domains (and workgroups) will need their own unique action account, which functions as a Run As account for that domain, and allows you to monitor other servers in that external domain such as a DMZ (demilitarized zone).</li>
	<li>The gateway action account can run with the credentials of Local System or a domain/local account. It is a best practice to use a low-privilege account. Using a domain account enables the gateway servers to have the permissions required to install agents and perform necessary actions.</li>
	<li>The authors recommend using SQL authentication for ACS rather than Windows security.</li>
	<li>An agent and management server use Windows (Kerberos v5) or certificate authentication to mutually authenticate before the management server will accept data from the agent.</li>
	<li>After mutual authentication occurs, the data channel between the agent and management server is encrypted.</li>
	<li>OpsMgr does not support unencrypted communications.</li>
	<li>As an alternative to installing certificates on each agent in a remote domain, you could use a gateway server as the communication mechanism between two domains</li>
	<li>When monitoring an untrusted domain, only two certificates need to be installed and updated (on the gateway server and a management server).</li>
	<li>The advantage of using a gateway is only one certificate is needed in the second domain (Continent) and one port (5723) opened through the firewall,</li>
	<li>The information is decrypted by the gateway, re-encrypted by the certificate, and then encrypted using the dynamically generated key pair, which is a function of the health service.</li>
	<li>When an agent is deployed, it automatically generates a public/private key pair, sending the public key to the management server. Any time the management server will send user credential information to the agent, it uses that public key for an additional layer of protection</li>
	<li>Although agents in a workgroup environment can use a gateway server, you must install certificates for communication between the agents and the gateway server to provide a secure channel. These certificates are in addition to the certificate installed on the gateway itself to communicate with the management server.</li>
	<li>If you have installed SSL on your reporting server, you must configure the Operations console to use SSL</li>
	<li>If you use the Add or Deny options, you must restart the System Center Management service for the changes to take effect.</li>
	<li>This service communicates with the monitored computer through a WSMan layer that is on both the management server and the monitored system. Installation of the WSMan layer is a prerequisite. Communication between the WSMan layers occurs over TCP port 1270, originating from the management server or gateway server.</li>
	<li>You can use SSH to install the WSMan layer or perform diagnostics.</li>
	<li>The UNIX/Linux Run As Account Wizard is used to create two types of Run As accounts:Tip: Using sudo Eliminates the Need for Root in UNIX/Linux Deployments: Using elevation lets an unprivileged account assume the identity of a privileged account on a UNIX/Linux system. The UNIX su (superuser) and sudo programs use the credentials the management server supplies to perform the elevation process. For privileged agent maintenance operations that use SSH (such as discovery, deployment, upgrades, uninstalls, and agent recovery), support for su, sudo elevation, and support for SSH key authentication (with or without passphrase) is provided. For privileged WS-Management operations (such as viewing secure log files), support for sudo elevation (without password) is added.
<ul>
	<li>Agent maintenance account: This account establishes SSH connections to the monitored computers. This account, which must be a privileged account, performs actions such as upgrading, uninstalling, or restarting the UNIX/Linux agent.</li>
	<li>Monitoring account: Use this for ongoing monitoring. You will want to create Run As accounts both for unprivileged and privileged monitoring.</li>
	<li>UNIX/Linux Privileged Account: This profile will be associated with a privileged Run As account (root or similar), or an unprivileged account that has been configured with elevation via sudo. This is what a workflow will execute, as that requires elevated rights.</li>
	<li>UNIX/Linux Agent Maintenance Account: Use a monitoring Run As account to this profile that has privileged credentials or credentials that are elevated.</li>
	<li>UNIX/Linux Action Account: This is used by your basic monitoring workflows. Add a monitoring Run As account with unprivileged credentials to this profile.</li>
</ul>
</li>
	<li>However, you must enable sudo for the user and turn off the prompt for password. This is not a security issue if intended use of Run As credentials is observed. If the UNIX administrators enter the sudo-enabled Run As account credentials, the no prompt requirement is of less consequence. For information on configuring sudo, see <a href="http://social.technet.microsoft.com/wiki/contents/articles/7375.configuring-sudo-elevation-for-unix-and-linux-monitoring-with-system-center-2012-operations-manager.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/7375.configuring-sudo-elevation-for-unix-and-linux-monitoring-with-system-center-2012-operations-manager.aspx</a>.</li>
	<li>Cross platform security requirements are also discussed at <a href="http://technet.microsoft.com/en-us/library/hh212926.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh212926.aspx</a> and <a href="http://technet.microsoft.com/en-us/library/hh212886.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh212886.aspx</a>. Scott Weisler has an excellent discussion of cross platform security and discovery recommendations at <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/indexId/94460/Default.aspx" target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/indexId/94460/Default.aspx</a> and <a href="http://opsmgrunleashed.wordpress.com/2012/07/07/cross-platform-discovery-settings/" target="_blank">http://opsmgrunleashed.wordpress.com/2012/07/07/cross-platform-discovery-settings/</a>.</li>
	<li>Table 10.6. Ports across a firewall</li>
	<li>The authors recommend using the Group Policy Management Console (GPMC) to create and deploy an OpsMgr firewall exceptions GPO in the domain(s) where OpsMgr will manage computers</li>
	<li>By deploying and using the ACS features of Operations Manager, the organization achieves a crucial capability—being able to prove it is secure in some valuable measurements of security. ACS provides evidence of how well your environment complies with specific security policies. A question that often arises, particularly from administrators that already have security solutions deployed, involves where ACS fits in a layered security approach. Table 10.7 shows how ACS compares to a conventional intrusion detection system (IDS).</li>
	<li>Consider ACS for augmenting your existing, conventional intrusion detection systems. IDS and ACS serve different purposes, and in some scenarios, ACS provides more meaningful or actionable data than an IDS</li>
	<li>ACS provides invaluable intelligence in auditing targeted resources, such as changes to privileged groups, and knowing of unauthorized attempts to connect to hidden file shares.</li>
	<li>You must manage the expectations of ACS report consumers such as auditors or network security staff, and match those to architecture decisions, audit policies, and reports during the planning process</li>
	<li>To get audit data into the ACS database, auditing must be enabled at the Windows operating system level on each ACS forwarder. This means that you first cause the security audit events to exist, and then deploy ACS to transport security audit events to the ACS collector and write them to the ACS audit database. By default Windows does not perform security auditing; you must explicitly turn this on for ACS to collect the data. You enable auditing through security policies</li>
	<li>Table 10.8. Windows Server audit policies</li>
	<li>The authors do not recommend creating custom GPOs with security policies unless absolutely necessary; it is best to work within the default (single) domain security policy to have consistency across the enterprise</li>
	<li>There are nine categories of auditing available in the Local Policy -&gt; Audit Policy section of all types of security policies (domain and local) as they appear in the GPMC</li>
	<li>In addition to deploying the appropriate audit settings through domain group policy or local security policy, you should enforce minimum security log sizes for domain controllers and other computers</li>
	<li>A recommended initial setting for domain controllers is 160MB, with 16MB for non-domain controllers</li>
	<li>Here are five questions for you to answer when making ACS architecture decisions:
<ul>
	<li>Will you host any of your databases on clustered SQL servers?</li>
	<li>Will you implement a security partition between your OpsMgr environment and the audit database?</li>
	<li>Will you integrate the ACS reporting feature with the OpsMgr reporting feature by sharing the same SQL Service Reporting Server, or will you install ACS reporting to a dedicated SSRS instance?</li>
	<li>How many ACS collector/database pairs will you deploy in your management group(s)?</li>
	<li>Will you use SQL Standard or Enterprise edition for your ACS database server(s)?</li>
</ul>
</li>
	<li>Here are some reasons to consider clustering the ACS database server:Consider installing ACS reports on a dedicated SSRS instance if the consumers of ACS data, such as a security team, would be better served with not having access to “too much data,” that being all the reports already installed in the OpsMgr management group.
<ul>
	<li>Cost of downtime and possible emergency system restore costs.</li>
	<li>Loss of ability to collect or analyze security events while replacing or performing extended maintenance on a failed SQL Server hosting the audit database.</li>
	<li>Liability or service level agreement (SLA) failure for possible loss of safeguarded audit data.</li>
</ul>
</li>
	<li>good metric to get a handle on is the number of events per hour that you expect to be written to the audit database.</li>
	<li>A moderately busy domain controller generates over 500,000 security events in a day (about 21,000 events per hour).</li>
	<li>Assuming high-performance server and storage resources are provided, a single ACS collector can support a maximum of about 150 domain controllers or 3,000 member servers simultaneously.</li>
	<li>The Enterprise edition of SQL Server is recommended because of the stress of daily ACS database maintenance.</li>
	<li>The ACS collector communicates with the ACS database server using an ODBC data source of the System DSN type.</li>
	<li>ACS installation itself does not create or require any security groups. The group you create will contain the user accounts of the individuals authorized to browse to the ACS reporting SSRS website and run on-demand ACS reports</li>
	<li>If you deploy ACS reporting on the same SSRS instance as OpsMgr reporting, the same role-based security applies to all reports. This means that ACS reporting users must be assigned to the Operations Manager Report Operator Role to access the ACS reports.</li>
	<li>USE OperationsManagerAC UPDATE dtConfig SET Value = &lt;number of days to retain data + 1&gt; WHERE Id = 11</li>
	<li>Restart the Operations Manager Audit Collection Service on the ACS collector for this to take effect.</li>
	<li>Tip: About the Audit and Audit5 Report Templates: You may notice two cryptically named report templates in the Audit Reports folder: Audit and Audit5. These templates are used when you create a custom report. The Audit template has room for up to 22 security audit event strings, while Audit5 has room for only five strings. Shorter events index faster, and since most security audit events have five or fewer description strings anyway, select the Audit5 template for new reports unless you know the security event will contain more than five strings.</li>
	<li>The primary tool for administering ACS is a command-line tool, AdtAdmin.exe. The program folder for ACS is %SystemRoot%System32SecurityAdtServer on the ACS collector</li>
	<li>Create Windows Management Instrumentation (WMI) queries that limit the events stored in the ACS database. (-GetQuery, -SetQuery)</li>
	<li>AdtAdmin -SetQuery -query:"SELECT = FROM * FROM AdtsEvent WHERE NOT (HeaderUser='SYSTEM' OR HeaderUser='LOCAL SERVICE' or HeaderUser='NETWORK SERVICE')" creates a WMI query that will discard security events when the user account is the local computer account of the ACS forwarder. This is useful in a setting where you are interested in tracking only the activity of actual user accounts, and not machine accounts.</li>
	<li>it may be necessary to modify the security on a registry key as shown in Figure 10.27. The registry key is HKLMSystemCurrentControlSetservicesAdtServerParameters. The Network Service account needs to have the Set Value, Allow permission granted to the Parameters key.</li>
	<li>Tip: Redirect Adtadmin -Stats to a CSV File and Open in Excel: The -stats switch for the AdtAdmin.exe tool dumps all statistics about ACS database records. Redirect the output of the AdtAdmin -stats command to a text file (append "&gt; &lt;filename&gt;.CSV" to the AdtAdmin.exe command line), and open it in Microsoft Excel as a comma-separated value (CSV) file. Viewed as a spreadsheet, each forwarder is listed in a row, with 17 columns of detailed data for each ACS forwarder. A value to watch is the Average time to collector(in ms) column, which is a measure of latency between when events occur on forwarders and when the collector writes them to the database. This value should be 2,000 milliseconds or less under normal conditions.</li>
	<li>The capacity of a given ACS collector is finite, and the administrator of the ACS collector (the OpsMgr administrator) should keep an eye on collector performance. Three registry keys at HKLMSystemCurrentControlSetservicesAdtServerParameters can be tuned to help performance (see the keys in the upper portion of Figure 10.27). These keys work in conjunction with one another:A default collector queue, allowing 262,144 events of 512 bytes each, means about 134MB of memory is available for the queue.
<ul>
	<li>BackoffThreshold: Default is 75%. New forwarder clients not connected above this threshold.</li>
	<li>MaximumQueueLength: Default is 262,144 events. (This registry value must be created manually.)</li>
	<li>DisconnectThreshold: Default is 90%. Active forwarders are disconnected until below this threshold.</li>
</ul>
</li>
	<li>OpsMgr performance charts and reports are based on 5-minute samples</li>
	<li>Tip: Detailed Logging on ACS Forwarders: If you are experiencing a performance issue with a particular forwarder, you might find it useful to enable detailed logging on the forwarder temporarily. To do so, create a new DWORD value named TraceFlags with a decimal value of 524420 in the registry of the forwarder at HKLMSystemCurrentControlSetservicesAdtAgentParameters. After you create the registry key, restart the System Center Audit Forwarding Service (AdtAgent.exe) on the forwarder. A detailed log will be created at %SystemRoot%TempAdtAgent.log.</li>
	<li>Preferred solutions are to reduce the volume of events, add resources to the collector feature, or increase performance of the SQL Server.</li>
	<li>for best system performance, minimize the number of auditing entries for a given folder or file by using Windows groups to contain all the users and groups to be audited—then specify just that group on the Auditing tab.</li>
	<li>Additional information on Operations Manager security is in the Operations Guide for System Center 2012 - Operations Manager at <a href="http://technet.microsoft.com/library/hh212887.aspx" target="_blank">http://technet.microsoft.com/library/hh212887.aspx</a></li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 11: Dashboards, Trending, and Forecasting</h3>
<div style="color: #000000;">
<ul>
	<li>two additional dashboard types are prebuilt for this version of OpsMgr: the Summary and Service Level dashboards</li>
	<li>alerts from monitors should not be closed as the health state is still impacted (for more information, see <a href="http://blogs.catapultsystems.com/cfuller/archive/2011/04/15/opsmgr-never-close-an-alert-for-a-monitor-%E2%80%93-the-exception-to-the-%E2%80%9Crule-of-the-monitor%E2%80%9D.aspx," target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2011/04/15/opsmgr-never-close-an-alert-for-a-monitor-%E2%80%93-the-exception-to-the-%E2%80%9Crule-of-the-monitor%E2%80%9D.aspx,</a></li>
	<li>Operations Manager 2012 widgets are designed to be integrated with SharePoint 2010</li>
	<li>Using SharePoint provides a framework where you can combine OpsMgr widgets with other technologies to create a dashboard that spans System Center and other Microsoft products.</li>
	<li>Microsoft provides excellent documentation on the details of this process, available at <a href="http://technet.microsoft.com/en-us/library/hh212924.aspx#bkmk_howtodeploytheoperationsmanagerwebpart" target="_blank">http://technet.microsoft.com/en-us/library/hh212924.aspx#bkmk_howtodeploytheoperationsmanagerwebpart</a>. Tim McFadden also provides an excellent step-by-step on this topic, available at <a href="http://www.scom2k7.com/how-to-view-scom-2012-dashboards-in-sharepoint-2010/" target="_blank">http://www.scom2k7.com/how-to-view-scom-2012-dashboards-in-sharepoint-2010/</a>.</li>
	<li>For further details on Web Application Availability Monitoring synthetic transactions on these dashboards, see Marnix Wolf’s article at <a href="http://thoughtsonopsmgr.blogspot.com/2012/06/how-to-use-web-application-availability.html" target="_blank">http://thoughtsonopsmgr.blogspot.com/2012/06/how-to-use-web-application-availability.html</a>, and the OpsMgr product team’s article at <a href="http://blogs.technet.com/b/momteam/archive/2012/05/31/using-the-web-application-availability-monitoring-to-monitor-web-applications-health.aspx" target="_blank">http://blogs.technet.com/b/momteam/archive/2012/05/31/using-the-web-application-availability-monitoring-to-monitor-web-applications-health.aspx</a>.</li>
	<li>the Operations Manager team recently released a series of dashboards for OpsMgr 2012 to display Windows Server 2008 information, available at <a href="http://blogs.technet.com/b/momteam/archive/2012/06/12/free-windows-server-2008-dashboards-for-opsmgr-2012-and-tool-to-help-create-your-own-customized-dashboards.aspx" target="_blank">http://blogs.technet.com/b/momteam/archive/2012/06/12/free-windows-server-2008-dashboards-for-opsmgr-2012-and-tool-to-help-create-your-own-customized-dashboards.aspx</a>. This download provides two prebuilt dashboards for Windows Server 2008 (the Windows Server Summary Dashboard and Windows Server Task Pane Dashboard), and includes a tool called GMTTool. The GMTTool incorporates three items you cannot do from the Operations console:<a href="http://blogs.catapultsystems.com/cfuller/archive/2010/08/04/quicktricks-creating-really-easy-multiple-server-performance-reports-amp-how-to-create-a-report-for-multiple-objects-when-you-don%E2%80%99t-know-what-objects-to-choose.aspx" target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2010/08/04/quicktricks-creating-really-easy-multiple-server-performance-reports-amp-how-to-create-a-report-for-multiple-objects-when-you-don%E2%80%99t-know-what-objects-to-choose.aspx</a>.
<ul>
	<li>Removes management group GUIDs from dashboards so that dashboard management packs can be shared</li>
	<li>Gives the ability to add dashboard views to any folder in the monitoring pane</li>
	<li>Provides the ability to launch a custom dashboard from the Task pane</li>
	<li>Kevin Holman’s blog: Kevin Holman gathered a series of useful Operations Manager 2007 queries that are available at <a href="http://blogs.technet.com/b/kevinholman/archive/2007/10/18/useful-operations-manager-2007-sql-queries.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2007/10/18/useful-operations-manager-2007-sql-queries.aspx</a>.</li>
	<li>System Center Central: System Center Central has a downloadable set of SQL queries to use for OpsMgr dashboards and gadgets at <a href="http://www.systemcentercentral.com/Downloads/DownloadsDetails/tabid/144/IndexID/86822/Default.aspx" target="_blank">http://www.systemcentercentral.com/Downloads/DownloadsDetails/tabid/144/IndexID/86822/Default.aspx</a>.</li>
</ul>
</li>
	<li>This management pack is available free from System Center Central in the management pack catalog (<a href="http://tinyurl.com/SCC-HealthCheck" target="_blank">http://tinyurl.com/SCC-HealthCheck</a>).</li>
	<li>This management pack is available at no cost from Veeam and is available at <a href="http://www.veeam.com/extended-generic-report-library.html" target="_blank">http://www.veeam.com/extended-generic-report-library.html</a>.Community MP: Daniel Savage of Microsoft wrote a sample management pack that provides forecasting in OpsMgr 2007, available at <a href="http://blogs.technet.com/b/momteam/archive/2010/04/29/reporting-scenarios-more-samples.aspx" target="_blank">http://blogs.technet.com/b/momteam/archive/2010/04/29/reporting-scenarios-more-samples.aspx</a>.</li>
	<li>OpsLogix has written a management that provides the ability to project trends and forecast capacity for OpsMgr.</li>
	<li>Information on this management pack is available at <a href="http://www.opslogix.com/products/capacity-management-pack" target="_blank">http://www.opslogix.com/products/capacity-management-pack</a>.</li>
	<li>Top 10 Reporting Tricks: Windows IT Pro article by Cameron Fuller, available at <a href="http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/10-system-center-operations-manager-reporting-tips-140603" target="_blank">http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/10-system-center-operations-manager-reporting-tips-140603</a></li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 12: Backup and Recovery</h3>
<div style="color: #000000;">
<ul>
	<li>For further details on Web Application Availability Monitoring synthetic transactions on these dashboards, see Marnix Wolf’s article at <a href="http://thoughtsonopsmgr.blogspot.com/2012/06/how-to-use-web-application-availability.html," target="_blank">http://thoughtsonopsmgr.blogspot.com/2012/06/how-to-use-web-application-availability.html,</a> and the OpsMgr product team’s article at <a href="http://blogs.technet.com/b/momteam/archive/2012/05/31/using-the-web-application-availability-monitoring-to-monitor-web-applications-health.aspx" target="_blank">http://blogs.technet.com/b/momteam/archive/2012/05/31/using-the-web-application-availability-monitoring-to-monitor-web-applications-health.aspx</a>.</li>
	<li>the Operations Manager team recently released a series of dashboards for OpsMgr 2012 to display Windows Server 2008 information, available at <a href="http://blogs.technet.com/b/momteam/archive/2012/06/12/free-windows-server-2008-dashboards-for-opsmgr-2012-and-tool-to-help-create-your-own-customized-dashboards.aspx." target="_blank">http://blogs.technet.com/b/momteam/archive/2012/06/12/free-windows-server-2008-dashboards-for-opsmgr-2012-and-tool-to-help-create-your-own-customized-dashboards.aspx.</a> This download provides two prebuilt dashboards for Windows Server 2008 (the Windows Server Summary Dashboard and Windows Server Task Pane Dashboard), and includes a tool called GMTTool. The GMTTool incorporates three items you cannot do from the Operations console:</li>
	<li>
<ul>
	<li>Removes management group GUIDs from dashboards so that dashboard management packs can be shared</li>
	<li>Gives the ability to add dashboard views to any folder in the monitoring pane</li>
	<li>Provides the ability to launch a custom dashboard from the Task pane</li>
</ul>
</li>
	<li>Kevin Holman’s blog: Kevin Holman gathered a series of useful Operations Manager 2007 queries that are available at <a href="http://blogs.technet.com/b/kevinholman/archive/2007/10/18/useful-operations-manager-2007-sql-queries.aspx." target="_blank">http://blogs.technet.com/b/kevinholman/archive/2007/10/18/useful-operations-manager-2007-sql-queries.aspx.</a></li>
	<li>
<ul>
	<li>System Center Central: System Center Central has a downloadable set of SQL queries to use for OpsMgr dashboards and gadgets at <a href="http://www.systemcentercentral.com/Downloads/DownloadsDetails/tabid/144/IndexID/86822/Default.aspx." target="_blank">http://www.systemcentercentral.com/Downloads/DownloadsDetails/tabid/144/IndexID/86822/Default.aspx.</a></li>
</ul>
</li>
	<li><a href="http://blogs.catapultsystems.com/cfuller/archive/2010/08/04/quicktricks-creating-really-easy-multiple-server-performance-reports-amp-how-to-create-a-report-for-multiple-objects-when-you-don%E2%80%99t-know-what-objects-to-choose.aspx." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2010/08/04/quicktricks-creating-really-easy-multiple-server-performance-reports-amp-how-to-create-a-report-for-multiple-objects-when-you-don%E2%80%99t-know-what-objects-to-choose.aspx.</a></li>
	<li>This management pack is available free from System Center Central in the management pack catalog (<a href="http://tinyurl.com/SCC-HealthCheck" target="_blank">http://tinyurl.com/SCC-HealthCheck</a>).</li>
	<li>This management pack is available at no cost from Veeam and is available at <a href="http://www.veeam.com/extended-generic-report-library.html." target="_blank">http://www.veeam.com/extended-generic-report-library.html.</a></li>
	<li>Community MP: Daniel Savage of Microsoft wrote a sample management pack that provides forecasting in OpsMgr 2007, available at <a href="http://blogs.technet.com/b/momteam/archive/2010/04/29/reporting-scenarios-more-samples.aspx." target="_blank">http://blogs.technet.com/b/momteam/archive/2010/04/29/reporting-scenarios-more-samples.aspx.</a></li>
	<li>OpsLogix has written a management that provides the ability to project trends and forecast capacity for OpsMgr.</li>
	<li>Information on this management pack is available at <a href="http://www.opslogix.com/products/capacity-management-pack." target="_blank">http://www.opslogix.com/products/capacity-management-pack.</a></li>
	<li>Top 10 Reporting Tricks: Windows IT Pro article by Cameron Fuller, available at <a href="http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/10-system-center-operations-manager-reporting-tips-140603" target="_blank">http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/10-system-center-operations-manager-reporting-tips-140603</a></li>
	<li>Operations Manager does not include a backup process out of the box.</li>
	<li>There are also critical files you will want to secure through backup. This includes customized management packs, reports, the encryption keys utilized by SSRS, and the Internet Information Services (IIS) metabase</li>
	<li>Operations Manager-specific user databases include the operational database, data warehouse database, and audit database used by ACS. Installing the SQL Server Reporting Component (required for the OpsMgr reporting feature) creates two additional databases: the ReportServer and ReportServerTempDB databases.</li>
	<li>The operational database (named OperationsManager by default): This database is installed in every management group, and is the most important user database to back up</li>
	<li>The data warehouse database (OperationsManagerDW by default): This database stores aggregated data used for reporting, used by SSRS for trend analysis and performance tracking. Based on the amount of data you are collecting and the degree of aggregation, this database may be large and thus require special handling</li>
	<li>The SSRS ReportServer database: This database is used by SSRS</li>
	<li>The ReportServerTempDB database: The only reason to back up this database is to avoid having to recreate it if there is a hardware failure</li>
	<li>The audit database (named OperationsManagerAC by default): This database is associated with the Audit Collector service, which runs on the ACS collector</li>
	<li>If you installed the operational, data warehouse, reporting, or audit databases on separate database servers or instances, each will have a Master database that should be backed up.</li>
	<li>If you have installed the operational, data warehouse, reporting, or audit databases on separate database servers or instances, each will have an Msdb database that should be backed up.</li>
	<li>The authors recommend separate backups of non-sealed/customized management packs, as this provides the granularity to import them directly into Operations Manager if necessary and to save a self-contained copy of any management pack customizations.</li>
	<li>You could back up the server including the metabase, or redeploy the Web console server as part of your disaster recovery plan.</li>
	<li>Custom files include the encryption key file for the reporting server.</li>
	<li>Table 12.1. OpsMgr databases with recommended backup schedule</li>
	<li>Table 12.2. Significant files with recommended backup schedule</li>
	<li>Updates to the grooming settings are applied immediately. Once the data is groomed, it is not recoverable unless it was previously backed up.</li>
	<li>Note: Active Alerts</li>
	<li>Active alerts are never groomed. You must close an alert before it will be groomed.</li>
	<li>The Operations console does not include a graphical interface for modifying data retention settings for the data warehouse</li>
	<li>Table 12.3. Data warehouse datasets, types, and retention periods</li>
	<li>Performance, Alert, Event, and AEM data is groomed every 240 minutes (4 hours); State data is groomed every hour.</li>
	<li>Each time the stored procedure runs, it will groom a maximum of 100,000 rows</li>
	<li>You can use the standarddatasetgroom stored procedure in the data warehouse database to manually trigger grooming</li>
	<li>performance counters to keep in the data warehouse. The setting applies to hourly performance aggregations, which can take up a considerable amount of space.</li>
	<li>Both parameters are set to 91 days by default. Select an existing unsealed management pack or create a new management pack to store your overrides in, and click OK.</li>
	<li>You cannot configure daily performance aggregations, which default at 182. However, daily aggregations use considerably less disk space than hourly aggregations.</li>
	<li>With OpsMgr, Microsoft designed the databases to be self-maintaining to a degree</li>
	<li>SQL Server Enterprise Edition continues inserting processed security events but only at 30% to 40% of the regular insertion rate.</li>
	<li>The ACS collector is configured to queue 262,144 events by default</li>
	<li>Microsoft built reindexing into Operations Manager for the more significant tables in the operational database; the Optimize Index rule in the System Center Internal Library management pack executes the P_OptimizeIndexes stored procedure daily at 2:30 AM, which cannot be modified. This means you must ensure no other SQL maintenance jobs are running at 2:30 AM.</li>
	<li>The operational database needs 50% free space at all times for growth and for re-index operations to be successful. An alert is generated when free space falls below 40%.</li>
	<li>Autogrow is turned off for the operational database. It should not be turned on.</li>
	<li>Autogrow is turned on for the data warehouse database. The authors recommend changing this from the default (percent) to a defined number, such as 500MB for the database file and 100MB for the transaction log.</li>
	<li>OpsMgr does support log shipping for redundancy on the operational and data warehouse databases. If you want to implement log shipping, set the database to full recovery mode. The authors do not recommend this for the audit database, as it already has high processing requirements. If you are looking for fault tolerance, clustering is a less resource-intensive approach.</li>
	<li>you can use SQL Server’s backup feature to back up the databases to (local or remote) file or local tape, and then back up the resulting files during your normal backup process</li>
	<li>Always perform a complete backup rather than an incremental or differential backup of the operational database; by default, Operations Manager supports a simple recovery from a full backup only, not a forward recovery using the transaction log</li>
	<li>Additional information on recovery models is available at <a href="http://msdn.microsoft.com/en-us/library/ms189275.aspx." target="_blank">http://msdn.microsoft.com/en-us/library/ms189275.aspx.</a></li>
	<li>The operational, data warehouse, and audit databases should be backed up daily</li>
	<li>For general processing efficiency, the authors recommend performing backups during a period when you do not expect a high volume of updates on the database you are backing up.</li>
	<li>After restoring the database, restart the System Center Data Access Service and launch the Operations console. Open the Administration node to verify it has the correct rule groups and configuration. You can also launch the Monitoring node to confirm the agents are sending heartbeats. This validates OpsMgr is operational.</li>
	<li>In addition, you really should restore both the operational and data warehouse databases at the same time, from a backup taken at the same time. This is because many items are synchronized to both databases; therefore restoring only one of the databases creates a situation where the two will be out of sync, which can create issues with availability reports.</li>
	<li>Browse to HKLMSoftwareMicrosoftSystemCenter2010CommonDatabase, and update the string called DatabaseServerName to reflect the name of the new database server.</li>
	<li>Browse to HKLMSoftwareMicrosoftMicrosoft Operations Manager3.0Setup, and update the DatabaseServerName string to the name of the new database server.</li>
	<li>Edit %ProgramFiles%System Center 2012Operations ManagerServerConfigService.config. In the &lt;Category&gt; tab for Cmdb, change the value for ServerName to the name and instance of the new SQL Server.</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 13: Administering Management Packs</h3>
<div style="color: #000000;">
<ul>
	<li>Update the operational database with the new database server name and the location of the APM tables</li>
	<li>Enable the Broker service. On the new database instance, open a Query window and execute this command:
<ul>
	<li>SELECT is_broker_enabled FROM Sys.databases WHERE name='OperationsManager'</li>
</ul>
</li>
	<li>If the result is a value of 0, run these commands:Browse to HKLMSoftwareMicrosoftMicrosoft Operations Manager3.0Setup, and update the DataWarehouseDBServerName string to the name of the new database server. Use the ComputerNameinstance format if using a named instance of SQL Server.
<ul>
	<li>Enable CLR to allow assembly execution. On the new database instance, open a Query window and execute these commands:</li>
	<li>sp_configure 'show advanced options', 1</li>
	<li>reconfigure</li>
	<li>sp_configure 'clr enabled', 1</li>
	<li>reconfigure</li>
</ul>
</li>
	<li>On the system hosting the Audit Collection service, edit the registry key HKLMSoftwareODBCODBC.INIOpsMgrAC.</li>
	<li>If you have issues with the SSRS database or have to move it, the best practice is to simply reinstall SSRS.</li>
	<li>The authors suggest creating separate management packs to store overrides for each of the various sealed management packs loaded into OpsMgr.</li>
	<li>For purposes of regularly scheduled jobs, the authors recommend you back up your unsealed management packs in a batch mode, using PowerShell cmdlets to export the management packs.</li>
	<li>export management packs using the Export-SCOMManagementPack cmdlet.To keep things simple administratively, the authors recommend you package your reports in management packs.
<ul>
	<li>$all_mps = Get-SCOMM...</li>
	<li>$all_mps = Get-SCOMManagementPack where-object {_.Sealed -eq $false}</li>
	<li>foreach($mp in $all_mps)</li>
	<li>{</li>
	<li>Export-SCOMManagementPack -ManagementPack $mp -path "C:Backups"</li>
	<li>}</li>
</ul>
</li>
	<li>Microsoft does not support including ACS custom reports in management packs, as by default an OpsMgr administrator does not have access to ACS reporting. Customized ACS reports should be extracted using Report Builder and stored in a separate folder</li>
	<li>You can use the RSKeyMgmt.exe utility to extract a copy of the encryption key from the ReportServer database. The utility writes the key to a file you specify and scrambles the key using a password you provide. This file should be backed up as part of your backup and recovery procedures. You should also document the password used for the file.</li>
	<li>Backing Up the IIS Metabase</li>
	<li>The IIS configuration on Windows 2008 R2 and Windows 2012 servers is split between the web.config files and the applicationHost.config</li>
	<li>appcmd add backup &lt;backupname&gt;</li>
	<li>You need to develop a detailed plan for the various contingencies, and practice the various scenarios in a development environment until you (and others on your staff in case you are hit by the proverbial truck) are comfortable with the process.</li>
	<li>After the installation completes, immediately stop the three OpsMgr services on the management server to prevent the management server from sending data to the operational and data warehouse databases, as you will be overlaying these databases as part of your recovery process.</li>
	<li>you will need the SSRS encryption key and other files discussed throughout this chapter for a successful recovery</li>
	<li>you can recover a failed management server by running setup.exe with the /recover switch in a command prompt window. For syntax examples, see <a href="http://technet.microsoft.com/en-us/library/hh531578.aspx">http://technet.microsoft.com/en-us/library/hh531578.aspx</a> and <a href="http://technet.microsoft.com/en-us/library/hh531577.aspx." target="_blank">http://technet.microsoft.com/en-us/library/hh531577.aspx.</a></li>
	<li>One of the strengths of Operations Manager is its management packs are often produced by the same engineers who wrote the particular application or service</li>
	<li>OpsMgr ships with more than 200 monitor types; these are predefined workflows that monitor for specific types of instrumentation.</li>
	<li>Overrides can be applied at several levels:
<ul>
	<li>Type: A type refers to the type of object being monitored. Examples of types would be all SQL Server databases, all Exchange mail servers, all DNS servers, and so on.</li>
	<li>Group: A group is a subset of a type. For example, rather than monitoring all Exchange mail servers, you may want to apply the override to only the back-end mail servers in a particular domain, or the DNS servers in a branch office.</li>
	<li>Object: An object would be a particular instance of a type (class). You may decide to apply an override to a particular database—perhaps the operational database, or a specific DNS server.</li>
</ul>
</li>
	<li>The authors suggest you create a separate MP for each workload (Exchange, SQL Server, DNS, and so on), to simplify managing overrides.</li>
	<li>Use a naming convention that follows the management pack holding the original settings.</li>
	<li>Alternatively, you could create separate management packs for overrides only and prepend “Overrides - ” to the management pack name, such as “Overrides - Exchange 2010,” as Pete Zerger discusses at <a href="http://www.systemcentercentral.com/tabid/145/indexId/73805/Default.aspx." target="_blank">http://www.systemcentercentral.com/tabid/145/indexId/73805/Default.aspx.</a></li>
	<li>You can also find management pack guides at <a href="http://technet.microsoft.com/en-us/library/dd347500.aspx." target="_blank">http://technet.microsoft.com/en-us/library/dd347500.aspx.</a></li>
	<li>The Microsoft System Center Marketplace at <a href="http://systemcenter.pinpoint.microsoft.com/" target="_blank">http://systemcenter.pinpoint.microsoft.com</a> includes management guides as well.</li>
</ul>
</div>
<div style="color: #000000;"></div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 14: Monitoring with System Center 2012 Operations Manager</h3>
<div style="color: #000000;">
<ul>
	<li>Additional information on how bundles work is at <a href="http://blogs.technet.com/b/servicemanager/archive/2009/09/04/introducing-management-pack-bundles.aspx." target="_blank">http://blogs.technet.com/b/servicemanager/archive/2009/09/04/introducing-management-pack-bundles.aspx.</a></li>
	<li>To extract files from an MP bundle, see Daniel Grandini’s post at <a href="http://nocentdocent.wordpress.com/2012/02/28/opsmgr-2012-how-to-dump-management-pack-bundles/" target="_blank">http://nocentdocent.wordpress.com/2012/02/28/opsmgr-2012-how-to-dump-management-pack-bundles/</a> and Stefan Stranger’s discussion at <a href="http://blogs.technet.com/b/stefan_stranger/archive/2012/03/06/opsmgr-2012-how-to-dump-management-pack-bundles-small-improvement.aspx." target="_blank">http://blogs.technet.com/b/stefan_stranger/archive/2012/03/06/opsmgr-2012-how-to-dump-management-pack-bundles-small-improvement.aspx.</a></li>
	<li>you should assess management packs before importing and deploying them across your production environment.</li>
	<li>Testing may also reveal possible adjustments you will want to implement as overrides.</li>
	<li>When planning management pack deployments, you will want to decide which ones to deploy, and in what order.</li>
	<li>The order in which you implement management packs really depends on the priorities of your organization and your goals for monitoring.</li>
	<li>Real World: Implementing Management Packs</li>
	<li>It is best to deploy a single management pack at a time.</li>
	<li>As part of your approach, you should refer to the management pack guide for each management pack. Management pack guides discuss particulars for installing, configuring, and tuning management packs</li>
	<li>testing and tuning in a non-production environment is always advisable prior to unleashing something new into production</li>
	<li>A suggested approach for tuning a management pack is to work on a server-by-server or application-by-application basis, tuning from the highest severity alerts and dependencies to the lowest</li>
	<li>Consider dependencies. If your example is to monitor DNS, AD, and Exchange, you would first implement and tune the DNS management pack because Active Directory and Exchange are dependent on DNS.</li>
	<li>When a management pack is first installed, it typically uncovers a multitude of previously unknown issues in your environment. Monitor the alerts to determine potential areas of concern.</li>
	<li>If a new management pack generates many alerts, you may want to disable monitors or rules in that management pack. You can turn them on gradually, making the new management pack easier to tune and troubleshoot.</li>
	<li>Evaluate and tune each management pack until you are comfortable with its functionality and behavior. This may include resolving any outstanding alerts that are not actual problem indicators or adjusting underlying rules and alerts for issues not significant in your environment.</li>
	<li>Introduce management packs one-by-one into your management group, to isolate changes more easily in performance and behavior</li>
	<li>Identify rules and monitors that are generating the most activity and focus on understanding what is occurring</li>
	<li>After identifying the system generating the messages, you need to determine what is generating those events and how to resolve unnecessary alerts—which can include disabling rules or monitors, using overrides, or utilizing consolidation rules.</li>
	<li>Tip: Determine How Much Data You Are Collecting</li>
	<li>A quick way to find out how many event and performance records are in the operational database is by running these two SQL queries:The agent queue size is 15,360KB by default. Restart the System Center Management service on the agent-managed system for the changes to take effect.
<ul>
	<li>SELECT count(*) as COUNT from eventview</li>
	<li>SELECT count(*) as COUNT from performancecounterview</li>
</ul>
</li>
	<li>Before OpsMgr can automatically recover agents, you must add a Run As account to the Automatic Agent Management Account Run As profile. This Run As account must have administrator-level access on the target computers. OpsMgr uses the management server action account if you do not add a Run As account.</li>
	<li>These have been updated for OpsMgr 2012 by Daniele Muscetta and can be downloaded from <a href="http://blogs.msdn.com/b/dmuscett/archive/2012/02/19/boris-s-tools-updated.aspx." target="_blank">http://blogs.msdn.com/b/dmuscett/archive/2012/02/19/boris-s-tools-updated.aspx.</a></li>
	<li>About Targeting Rules and Monitors</li>
	<li>Brian Wren provides information about targeting at <a href="http://blogs.technet.com/ati/archive/2007/05/14/targeting-rules-and-monitors.aspx." target="_blank">http://blogs.technet.com/ati/archive/2007/05/14/targeting-rules-and-monitors.aspx.</a></li>
	<li>Groups are classes, just like any other object, although they are seldom targeted. If you apply a rule or monitor directly to a group, it executes against the group object itself and does not enumerate members of the group.</li>
	<li>The easiest way to validate you are using a target that actually has instances to use is with the Discovered Inventory view in the Operations console</li>
	<li>Steve Rachui, a Microsoft PFE, also discusses this topic in an article available at <a href="http://technet.microsoft.com/en-us/magazine/2008.11.targeting.aspx?pr=blog." target="_blank">http://technet.microsoft.com/en-us/magazine/2008.11.targeting.aspx?pr=blog.</a></li>
	<li>See <a href="http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/Operations-Manager-Key-Performance-Indicators-128969" target="_blank">http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/Operations-Manager-Key-Performance-Indicators-128969</a> for a discussion on KPIs and OpsMgr.</li>
	<li>To collect SNMP traps on the management server, you must first install the Windows SNMP trap provider (Control Panel -&gt; Programs and Features).</li>
	<li>you can configure OpsMgr to monitor for a particular line or string appearing in a log file of your designation.</li>
	<li>This is useful when you want to monitor the service as an individual item and potentially add it to a distributed application (DA).</li>
	<li>This is because this version of OpsMgr only monitors services that are not shared</li>
	<li>Kevin Holman discusses STTs and how they are created and tuned correctly at <a href="http://blogs.technet.com/b/kevinholman/archive/2008/03/19/self-tuning-thresholds-love-and-hate.aspx." target="_blank">http://blogs.technet.com/b/kevinholman/archive/2008/03/19/self-tuning-thresholds-love-and-hate.aspx.</a></li>
	<li>Russ Slaten has an excellent article on manual reset monitors, available at <a href="http://blogs.msdn.com/b/rslaten/archive/2010/06/25/the-challenges-with-manual-reset-monitors.aspx." target="_blank">http://blogs.msdn.com/b/rslaten/archive/2010/06/25/the-challenges-with-manual-reset-monitors.aspx.</a></li>
	<li>To understand on-demand detection, read Boris Yanushpolsky’s article on the topic at <a href="http://blogs.msdn.com/b/boris_yanushpolsky/archive/2008/06/03/on-demand-detection.aspx." target="_blank">http://blogs.msdn.com/b/boris_yanushpolsky/archive/2008/06/03/on-demand-detection.aspx.</a></li>
	<li>Additional reading on unit monitors is available from Steve Rachui, available at <a href="http://blogs.msdn.com/b/steverac/archive/2009/08/30/understanding-monitors-in-opsmgr-2007-part-i-unit-monitors.aspx." target="_blank">http://blogs.msdn.com/b/steverac/archive/2009/08/30/understanding-monitors-in-opsmgr-2007-part-i-unit-monitors.aspx.</a></li>
	<li>Steve Rachui provides details on dependency rollup monitors at <a href="http://blogs.msdn.com/b/steverac/archive/2009/10/05/understanding-monitors-in-opsmgr-2007-part-iii-dependency-monitors.aspx." target="_blank">http://blogs.msdn.com/b/steverac/archive/2009/10/05/understanding-monitors-in-opsmgr-2007-part-iii-dependency-monitors.aspx.</a></li>
	<li>Steve Rachui writes about aggregate rollup monitors at <a href="http://blogs.msdn.com/b/steverac/archive/2009/09/06/understanding-monitors-in-opsmgr-2007-part-ii-aggregate-monitors.aspx." target="_blank">http://blogs.msdn.com/b/steverac/archive/2009/09/06/understanding-monitors-in-opsmgr-2007-part-ii-aggregate-monitors.aspx.</a></li>
	<li>More information on this situation and OpsMgr is available at <a href="http://blogs.catapultsystems.com/cfuller/archive/2012/01/09/exchange-back-pressure-amp-opsmgr-notification-channels.aspx," target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2012/01/09/exchange-back-pressure-amp-opsmgr-notification-channels.aspx,</a></li>
	<li>These steps are well documented in the white paper “Notification Setup Guide for Operations Manager 2007” developed by Anders Bengtsson and Pete Zerger. You can download this white paper from <a href="http://contoso.se/blog/?p=132." target="_blank">http://contoso.se/blog/?p=132.</a></li>
	<li>Tip: Using Groups with Subscriptions</li>
	<li>The Unleashed authors developed a series of blog posts discussing how to use custom groups to simplify the Operations console for server owners. Here is a post providing information about how to use custom groups in subscriptions: <a href="http://opsmgrunleashed.wordpress.com/2009/08/28/how-to-use-customized-groups-to-simplify-the-opsmgr-console-for-server-owners-%E2%80%93-using-custom-groups-with-subscriptions-one-off-notifications/" target="_blank">http://opsmgrunleashed.wordpress.com/2009/08/28/how-to-use-customized-groups-to-simplify-the-opsmgr-console-for-server-owners-%E2%80%93-using-custom-groups-with-subscriptions-one-off-notifications/.</a> Cameron Fuller expands upon this topic with a webinar and whitepaper provided by Veeam, available at <a href="http://go.veeam.com/rs/veeam/images/whitepaper_How_To_Manage_SCOM.pdf." target="_blank">http://go.veeam.com/rs/veeam/images/whitepaper_How_To_Manage_SCOM.pdf.</a></li>
	<li>The Operations Manager Unleashed team provides information on the steps required to enable Instant Messaging in OpsMgr 2012 at <a href="http://opsmgrunleashed.wordpress.com/2012/02/24/enabling-instant-messaging-notifications-in-system-center-2012-operations-manager/" target="_blank">http://opsmgrunleashed.wordpress.com/2012/02/24/enabling-instant-messaging-notifications-in-system-center-2012-operations-manager/.</a></li>
	<li>The SMS notification channel requires a modem supporting SMS Protocol Data Unit (PDU) mode.</li>
	<li>Marnix Wolf discusses the steps to get SMS functional in OpsMgr at <a href="http://thoughtsonopsmgr.blogspot.com/2010/06/sending-out-sms-messages-with-scom.html." target="_blank">http://thoughtsonopsmgr.blogspot.com/2010/06/sending-out-sms-messages-with-scom.html.</a> System Center Central also has a series of articles at <a href="http://www.systemcentercentral.com/tabid/143/IndexId/60339/Default.aspx." target="_blank">http://www.systemcentercentral.com/tabid/143/IndexId/60339/Default.aspx.</a></li>
	<li>Table 14.2. Subscription properties and common usage</li>
	<li>Tip: Cannot Exclude from a Subscription</li>
	<li>The OpsMgr user interface does not include functionality to define a subscription that excludes specific alerts. Here are some options to work around this restriction:
<ul>
	<li>Create a subscription targeted to the specific pieces (rules/monitors); see <a href="http://blogs.technet.com/b/kevinholman/archive/2008/10/12/creating-granular-alert-notifications-rule-by-rule-monitor-by-monitor.aspx." target="_blank">http://blogs.technet.com/b/kevinholman/archive/2008/10/12/creating-granular-alert-notifications-rule-by-rule-monitor-by-monitor.aspx.</a> The problem is that with large management packs you cannot edit the subscriptions once there are a large number of rules/monitors.</li>
</ul>
</li>
	<li>Tip: Blog Posting on SubscriptionsDue to how editing of company knowledge is built into Operations Manager, it can only be performed on a 32-bit operating system
<ul>
	<li>Kevin Holman provides an excellent blog posting on subscriptions in OpsMgr 2012 at <a href="http://blogs.technet.com/b/kevinholman/archive/2012/04/28/opsmgr-2012-configure-notifications.aspx." target="_blank">http://blogs.technet.com/b/kevinholman/archive/2012/04/28/opsmgr-2012-configure-notifications.aspx.</a></li>
</ul>
</li>
	<li>You must install the Operations Manager console on the system where you will be editing company knowledge.</li>
	<li>After you install the console, there are two additional prerequisites:</li>
	<li>Microsoft Word (Word 2003 with the .NET Programmability feature, or Microsoft Office Word 2007 or Office Word 2010 Professional edition)</li>
	<li>Visio Studio 2005 Tools for Office (<a href="http://www.microsoft.com/en-us/download/confirmation.aspx?id=24263" target="_blank">http://www.microsoft.com/en-us/download/confirmation.aspx?id=24263</a>)</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 15: Monitoring .NET Applications</h3>
<div style="color: #000000;">
<ul>
	<li>System Center 2012 Service Manager Unleashed (Sams, 2013).</li>
	<li>Real World: Best Practices for Overrides</li>
	<li>Microsoft provides recommendations and best practices when creating overrides. This guide is available at <a href="http://support.microsoft.com/kb/943239." target="_blank">http://support.microsoft.com/kb/943239.</a></li>
	<li>Other best practices for overrides include
<ul>
	<li>Develop and document your standards for overrides and where they are stored. Pete Zerger writes about this at <a href="http://www.systemcentercentral.com/tabid/145/indexId/73805/Default.aspx." target="_blank">http://www.systemcentercentral.com/tabid/145/indexId/73805/Default.aspx.</a></li>
</ul>
</li>
	<li>The best practice recommendation is to create separate override management packs for each management pack.</li>
	<li>Document each override and custom management pack created based on the rule and explain why it was created</li>
	<li>Configure overrides for groups or classes instead of specific instances whenever possible.</li>
	<li>Tip: Why You Should Create Custom Alert Resolutions States</li>
	<li>Custom resolution states are often used to categorize alerts that are being worked on by different groups within an organization. As an example, there is often a requirement to create a resolution state for OpsMgr Admins, Database Admins, Web Admins, and such. You can use these resolution states in subscriptions, or to create views targeted to a resolution state.</li>
	<li>For additional information, see <a href="http://blogs.catapultsystems.com/cfuller/archive/2011/04/15/opsmgr-never-close-an-alert-for-a-monitor-%E2%80%93-the-exception-to-the-%E2%80%9Crule-of-the-monitor%E2%80%9D.aspx." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2011/04/15/opsmgr-never-close-an-alert-for-a-monitor-%E2%80%93-the-exception-to-the-%E2%80%9Crule-of-the-monitor%E2%80%9D.aspx.</a></li>
	<li>The option in Configuration Manager 2012 does not put the agent into maintenance mode in Operations Manager 2012 but will pause the OpsMgr agent so alerts are not generated during the software deployment.</li>
	<li>One of the side effects of using maintenance mode is that all monitors are reset to a healthy state.</li>
	<li>The System Center Operations Manager 2007 R2 Admin Resource Kit includes the following resource kit tools (utilities and their descriptions are a subset of the text provided by Microsoft at <a href="http://blogs.technet.com/b/momteam/archive/2011/06/03/system-center-operations-manager-2007-r2-admin-reskit-released.aspx):" target="_blank">http://blogs.technet.com/b/momteam/archive/2011/06/03/system-center-operations-manager-2007-r2-admin-reskit-released.aspx):</a></li>
	<li>The System Center Operations Manager 2007 Tools and Utilities include the following resource kit tools (utilities and their descriptions are a subset of the text provided by Microsoft at <a href="http://technet.microsoft.com/en-us/systemcenter/bb625978.aspx" target="_blank">http://technet.microsoft.com/en-us/systemcenter/bb625978.aspx</a>):</li>
	<li>System Center Operations Manager 2012 (OpsMgr) introduces the .NET application monitoring capability to enhance monitoring by collecting application performance information, including performance violations and failure details from ASP.NET and MVC applications, Windows Communication Foundation (WCF), and Web Services hosted on Internet Information Services (IIS) 7 and 7.5 (and IIS 8 in Service Pack 1).</li>
	<li>Application performance monitoring is a discipline within systems management that focuses on monitoring and managing the performance and service availability of software applications.</li>
	<li>does not require code changes and recompilations. It monitors application runtime behavior by watching all requests coming in and out and collecting statistical information as well as detailed reports of the failures and performance issues.</li>
	<li>APM in OpsMgr 2012 supports monitoring applications running on the Microsoft .NET Framework 2.0 and later, hosted inside IIS 7 and IIS 7.5. This translates into ASP.NET, Web Services, WCF hosted inside IIS, and MVC applications. System Center 2012 Service Pack (SP) 1 adds support for discovery and monitoring of MVC applications, IIS 8, and Windows services built using Microsoft .NET 4.5.</li>
	<li>APM agent components include a Windows service and application monitoring core. System Center Management APM is a Windows service and is installed as disabled by default</li>
	<li>The application monitoring core is a set of DLLs automatically loaded inside your .NET application when you enable it for monitoring.</li>
	<li>This is implemented by automatic injection of monitoring JavaScript code into your application’s response; the script then runs in the browser, collects all details, and then sends the data back to the APM agent. To be able to collect that client-side data, APM installs an additional IIS web application, CSMCollector, on each IIS website where your applications are hosted.</li>
	<li>You are required to install the OpsMgr Web console, as the OpsMgr Web console feature contains the Application Diagnostic and Application Advisor consoles; these are must-have features of APM.</li>
	<li>The only additional action required is installing the following management packs:
<ul>
	<li>Windows Server Internet Information Services 7.0 management pack</li>
	<li>Operations Manager Web APM IIS 7 management pack</li>
</ul>
</li>
	<li>If monitoring IIS 8 applications, install the IIS 8 applicable management packs.</li>
	<li>The name should reflect your line of business (LOB) application name or a subset of that. The authors recommend defining a name based on the application components you plan to place into that logical application.</li>
	<li>This could be front-end components of one application, or middle-tier application components, and naming the application group accordingly.</li>
	<li>Create a new management pack for each application to keep application settings separate</li>
	<li>You can also tag this configuration by selecting the Environment drop-down in Figure 15.5 and assigning it to Production, Staging, Test, Development, or giving it a custom tag. This is useful when you have multiple environments hosting the same application that should be managed separately and potentially have different application monitoring settings.</li>
	<li>By default, exception alerts include only security and connectivity failures and not application failures. To change these and other settings requires additional configuration.</li>
	<li>Thresholds defined for business logic components such as web services or WCF should be less than those for the front-end application components, as front-end components call business logic and run slower since they contain their own logic in addition to those calls.</li>
	<li>You must recycle IIS services on the monitoring servers to start .NET performance monitoring</li>
	<li>Additional Reading on APM Rules, Monitors, and Workflows</li>
	<li>Here is some recommended additional reading on APM rules, monitors, and workflows:
<ul>
	<li>System Center .NET application alerts versus events: <a href="http://blogs.technet.com/b/shawngibbs/archive/2012/04/13/system-center-net-application-alerts-vs-events.aspx" target="_blank">http://blogs.technet.com/b/shawngibbs/archive/2012/04/13/system-center-net-application-alerts-vs-events.aspx</a></li>
	<li>Custom APM rules for granular alerting: <a href="http://blogs.technet.com/b/momteam/archive/2012/01/23/custom-apm-rules-for-granular-alerting.aspx" target="_blank">http://blogs.technet.com/b/momteam/archive/2012/01/23/custom-apm-rules-for-granular-alerting.aspx</a></li>
	<li>Working with alerts: <a href="http://blogs.technet.com/b/momteam/archive/2011/08/23/application-monitoring-working-with-alerts.aspx" target="_blank">http://blogs.technet.com/b/momteam/archive/2011/08/23/application-monitoring-working-with-alerts.aspx</a></li>
</ul>
</li>
	<li>The most critical settings for application monitoring are performance thresholds and namespaces, as they control when to report a problem and what data to include per each incident.</li>
	<li>The Application Diagnostics console is designed to provide reporting capabilities for devops, developers, and debug engineers to investigate the root cause of the failures or performance problems. It is a web console and requires Internet Explorer.</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 16: Network Monitoring</h3>
<div style="color: #000000;">
<ul>
	<li>All firewalls between the management servers in the resource pool and the network devices need to allow SNMP (UDP) and ICMP bi-directionally, and ports 161 and 162 must be open bi-directionally</li>
	<li>These limitations suggest monitoring no more than 1,000 network devices in a single resource pool, and up to 2,000 network devices per management group.</li>
	<li>Each management server (or gateway server) is limited to a single network device discovery rule.</li>
	<li>OpsMgr also implements the AES protocol for encryption</li>
	<li>OpsMgr agents are not installed on the device in network monitoring. Instead, SNMP is used, where Get requests are sent to the device and responses are returned to the management server or gateway server in the resource pool.</li>
	<li>Since OpsMgr only reads the MIB on the device for monitoring purposes, all network monitoring workflows targeted at the device require only one Run As account</li>
	<li>Network monitoring in OpsMgr requires one of two types of Run As accounts:The community string Run As account type is always used for SNMP v1 and v2c devices, in which the only required input in the configuration is the plain text community string
<ul>
	<li>Community String</li>
	<li>SNMPv3 Account</li>
</ul>
</li>
	<li>Network device discovery is performed by manually created discovery rules</li>
	<li>each management server or gateway server can run only one discovery rule, you should plan how to make this work best for your environment.</li>
	<li>There are two types of network discovery methods: explicit and recursive</li>
	<li>An explicit discovery rule attempts to discover only those devices that you explicitly specify in the wizard by IP address or fully qualified domain name (FQDN).</li>
	<li>A recursive discovery rule attempts to discover those devices you explicitly specify in the wizard by IP address. It also attempts to discover other network devices connected to the devices specified in the discovery rule. IP addresses of these neighboring devices are gathered through the seed device’s Address Routing Protocol (ARP) table, its IP address table, or topology MIB.</li>
	<li>Sometimes it is best to consult with your network team and add only the devices necessary to create the network topology connecting the systems you are monitoring with OpsMgr.</li>
	<li>Microsoft recommends using recursive discovery only in smaller environments and that explicit discovery is used in large environments.</li>
	<li>Note: Guidance on Filtering</li>
	<li>Filtering can be an area of confusion. The best place to get guidance is in the Discovery Wizard, which includes a link for information on device filters.</li>
	<li>Three stages occur when a management server processes a discovery rule: probing, processing, and post-processing</li>
	<li>If ICMP and SNMP are used as the access mode, OpsMgr first pings the device using ICMP. If the device does not respond to the Echo request, probing ends without proceeding to the SNMP Get request and the device is not discovered.</li>
	<li>By default, the probing stage uses SNMP v2c first. If the device does not respond within the configured retry attempts, the management server attempts again using SNMP v1.</li>
	<li>Once probing determines the device is reachable, OpsMgr attempts to match the sysObjectId returned in the GetResponse message from the probing stage to a device defined in an oid2type_*.config file hosted on the management server. If OpsMgr finds a match, the device receives advanced monitoring features. Otherwise, only availability monitoring will run on the device.</li>
	<li>At a minimum, the following information is necessary to create a network device discovery rule:
<ul>
	<li>The IP address or FQDN of each device you want to include in an explicit discovery, or as seed devices in your recursive discovery.</li>
	<li>The version of SNMP each device uses (SNMP v1, v2, or v3). Remember SNMP v3 devices must always be explicitly added to your discovery rule, whether it is explicit or recursive.</li>
	<li>The SNMP community string of each SNMP v1 or v2 device you want to discover.</li>
	<li>The user name for each SNMP v3 device you want to discover. Optionally, if you require authentication and privacy, the authentication protocol, authentication key, privacy protocol, and privacy key are also needed. Check your device configuration to know which setting to select in the Discovery Wizard.</li>
	<li>The name of the network monitoring resource pool that will monitor the devices discovered.</li>
</ul>
</li>
	<li>Before creating a network device discover rule, ensure your firewalls are configured properly as discussed previously in the “Firewall Requirements” section.</li>
	<li>Note that the server performing the discovery will not be the server that monitors those devices</li>
	<li>By default, the discovery rule will run every Saturday at 2:00 am</li>
	<li>Read more about SNMP v3 Run As accounts at <a href="http://technet.microsoft.com/en-us/library/hh212920.aspx." target="_blank">http://technet.microsoft.com/en-us/library/hh212920.aspx.</a></li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 17: Using Synthetic Transactions</h3>
<div style="color: #000000;">
<ul>
	<li>If the device is the starting point for recursive discovery (seed device), you must remove the device from the discovery rule or delete the discovery rule.</li>
	<li>Port and interface monitoring is only available for those devices implementing the interface MIB (RFC 2863) and MIB-II (RFC 1213) standards</li>
	<li>OpsMgr 2012 does not currently support discovering network devices from a server using IPv6.</li>
	<li>OpsMgr 2012 incorporates a change to the base class for network devices that is incompatible with any custom OpsMgr 2007 R2 network monitoring management packs.</li>
	<li>Power Consumption: This template is added as part of the Power Management Pack. This template is used to define a collection of PDUs and computers running Windows Server 2008 R2 or 2012 that receive power from the PDU. For more information on this template, see <a href="http://technet.microsoft.com/en-us/library/ee808918.aspx." target="_blank">http://technet.microsoft.com/en-us/library/ee808918.aspx.</a></li>
	<li>Watcher nodes allow you to specify the computer(s) that will launch the simulation. The only prerequisite is that the computer you want to run the simulation from has an installed OpsMgr agent</li>
	<li>Tip: Using the Web Recorder</li>
	<li>When using the web recorder, the authors recommend performing the recording from an administrator’s workstation rather than a management server</li>
	<li>UAC challenges, 3rd party browser extensions, IE enhanced security: Kevin Holman discusses these topics at <a href="http://blogs.technet.com/b/kevinholman/archive/2009/06/19/web-application-recorder-r2-the-recorder-bar-missing-in-ie.aspx." target="_blank">http://blogs.technet.com/b/kevinholman/archive/2009/06/19/web-application-recorder-r2-the-recorder-bar-missing-in-ie.aspx.</a></li>
	<li>Recorder bar missing: Kevin Holman discusses this topic at <a href="http://blogs.technet.com/b/kevinholman/archive/2008/11/15/recording-a-web-application-browser-session-driving-you-crazy.aspx." target="_blank">http://blogs.technet.com/b/kevinholman/archive/2008/11/15/recording-a-web-application-browser-session-driving-you-crazy.aspx.</a></li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 18: Distributed Applications</h3>
<div style="color: #000000;">
<ul>
	<li>GSM delivers the external view for web monitoring by providing an outside-in perspective on your synthetic web transactions. GSM allows you to use an Azure-based service to monitor your websites from geo-distributed locations around the world. For more information on GSM, see the Operations Manager team blog entry at <a href="http://blogs.technet.com/b/momteam/archive/2012/06/19/global-service-monitor-for-system-center-2012-observing-application-availability-from-an-outside-in-perspective.aspx." target="_blank">http://blogs.technet.com/b/momteam/archive/2012/06/19/global-service-monitor-for-system-center-2012-observing-application-availability-from-an-outside-in-perspective.aspx.</a></li>
	<li>Tip: When to Use Web Application Availability Versus Web Application Transaction—it’s about Scalability</li>
	<li>The greatest benefit of web application availability monitoring versus web application transaction monitoring is scalability. Scalability is gained from using resource pools to provide automatic workflow load balancing, and by achieving high availability without alert duplication.</li>
	<li>If you are using a large number of URLs, the authors highly recommend using web application availability monitoring as a replacement for web application transaction monitoring. Web application availability is also the recommended replacement for the Bulk URL Editor in OpsMgr 2007 R2.</li>
	<li>More information on write actions and other components of the OpsMgr workflow is available at the AuthorMPs site at <a href="http://blogs.technet.com/b/authormps/" target="_blank">http://blogs.technet.com/b/authormps/</a> and Brian Wren’s TechNet blog site at <a href="http://blogs.technet.com/b/mpauthor/" target="_blank">http://blogs.technet.com/b/mpauthor/.</a></li>
	<li>The OpsMgr community provides additional examples of how to query SQL and use the results in OpsMgr, including how to perform checks for a SQL full or differential backup and how to monitor the default management pack:The default interval to run the OLE DB data source query is every two minutes.
<ul>
	<li><a href="http://blogs.technet.com/b/stefan_stranger/archive/2009/02/02/opsmgr-sql-full-or-differential-backup-check.aspx" target="_blank">http://blogs.technet.com/b/stefan_stranger/archive/2009/02/02/opsmgr-sql-full-or-differential-backup-check.aspx</a></li>
	<li><a href="http://blogs.technet.com/b/jonathanalmquist/archive/2008/11/12/monitor-default-management-pack.aspx" target="_blank">http://blogs.technet.com/b/jonathanalmquist/archive/2008/11/12/monitor-default-management-pack.aspx</a></li>
</ul>
</li>
	<li>The OLEDB module defined within the System Library management pack supports an additional level of monitoring. This module allows you to configure custom queries to run against the monitored database, meaning not only can you verify that the database is online, but you can also verify that the database is responding to queries</li>
	<li>Kevin Holman provides an example of monitoring a non-Microsoft database at <a href="http://blogs.technet.com/b/kevinholman/archive/2012/03/19/opsmgr-how-to-monitor-non-microsoft-sql-databases-in-scom-an-example-using-postgre-sql.aspx," target="_blank">http://blogs.technet.com/b/kevinholman/archive/2012/03/19/opsmgr-how-to-monitor-non-microsoft-sql-databases-in-scom-an-example-using-postgre-sql.aspx,</a></li>
	<li>Maarten Damen provides an example of how to monitor an Oracle database with an OleDB watcher at <a href="http://www.maartendamen.com/2010/09/monitor-an-oracle-database-with-a-scom-oledb-watcher/" target="_blank">http://www.maartendamen.com/2010/09/monitor-an-oracle-database-with-a-scom-oledb-watcher/.</a></li>
	<li>you can monitor any database that supports OLE DB as long as the OLE DB driver is installed where required</li>
	<li>Real World: Monitoring Oracle with the OpsLogix Management Pack</li>
	<li>The Oracle Intelligent management pack by OpsLogix provides a template allowing users to create rules and monitors specifically aimed at Oracle environments</li>
	<li>Additional information on OpsLogix and their management packs is available at the website at <a href="http://www.opslogix.com/products." target="_blank">http://www.opslogix.com/products.</a></li>
	<li>The OpsMgr DA represents your best bet to define what you really need to monitor for delivering your business-critical services</li>
	<li>By identifying those classes of objects that are involved in delivering the application (and their relationships) and collecting sets of targeted views that focus on the service delivery of the application, knowledge is encapsulated, preserved, and made portable.</li>
	<li>Tip: Install an Agent on Your Domain Controllers First</li>
	<li>If you import the Active Directory management packs before installing OpsMgr agents on your domain controllers, the DCs appear as Not Monitored in the Computers global view in the Operations console. This occurs because the Active Directory Topology Root DA discovers the DCs in the management group’s domain and makes them objects in the management group. However, without OpsMgr agents, the DCs, now identified as objects, show up as unmonitored. To prevent this from occurring, install an OpsMgr agent on your DCs before importing the Active Directory management packs.</li>
	<li>Objects discovered by the Information Worker management pack are listed at <a href="http://technet.microsoft.com/en-us/library/dd351478.aspx.)" target="_blank">http://technet.microsoft.com/en-us/library/dd351478.aspx.)</a></li>
	<li>Importing the Microsoft Information Worker management pack adds two DA templates to the Distributed Application Designer</li>
	<li>If your organization depends on information workers accessing a web-based application for a critical business function, consider using the Internet Explorer Service template to author a DA modeling that web access.</li>
	<li>The authors recommend monitoring an external web server through different outbound Internet service providers (ISPs). You should also consider monitoring an internal web server from watcher nodes at each branch office or outlying building</li>
	<li>By default, the web query runs every 2 minutes.</li>
	<li>You can find an example of using Visio integration with the Visio Add-in for Operations Manager (official name) at <a href="http://blogs.catapultsystems.com/cfuller/archive/2011/08/16/opsmgr-dashboard-integration-creating-a-visio-integrated-diagram-from-a-distributed-application.aspx." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2011/08/16/opsmgr-dashboard-integration-creating-a-visio-integrated-diagram-from-a-distributed-application.aspx.</a></li>
	<li>While this is an older management pack, it provides excellent templates that can be used to demonstrate functionality useful to include within a distributed application.</li>
	<li>The default interval to run the OLE DB data source query is every 2 minutes</li>
	<li>Cameron Fuller’s blog posting at <a href="http://blogs.catapultsystems.com/cfuller/archive/2010/09/13/using-distributed-applications-to-generate-actionable-alerting.aspx." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2010/09/13/using-distributed-applications-to-generate-actionable-alerting.aspx.</a></li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 19: Client Monitoring</h3>
<div style="color: #000000;">
<ul>
	<li>Real World: Using the SDK Versus a DA</li>
	<li>If your organization is critically dependent on a complex custom application, sometimes known as a Line of Business (LOB) application, consider creating a health model programmatically using the SDK as a long-term solution.</li>
	<li>when using the .NET Application Performance Monitoring management pack template, OpsMgr identifies .NET components in App Controller, Configuration Manager, Orchestrator, and Virtual Machine Manager that OpsMgr 2012 can monitor using application performance monitoring (APM) components.</li>
	<li>The only constraint with the Blank template is you can only add objects to components matching the type (or class) for which the component was created.</li>
	<li>Real World: Dynamic Distributed Applications</li>
	<li>For distributed applications to be even more useful, they should be designed so they can dynamically adjust to changes in their membership</li>
	<li>Implement this functionality in Operations Manager 2012 using a group with dynamic membership based upon a registry key on the system and embed this group into the design for the DA. This enables the DA to adapt as group membership changes. For further discussion on this topic, see <a href="http://blogs.catapultsystems.com/cfuller/archive/2011/11/28/opsmgr-dashboard-integration-server-health-creating-a-health-state-for-a-group-of-servers-in-a-dashboard.aspx." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2011/11/28/opsmgr-dashboard-integration-server-health-creating-a-health-state-for-a-group-of-servers-in-a-dashboard.aspx.</a></li>
	<li>OpsLogix has a free ping management pack that provides ping level monitoring for network devices (such as those not supported by the out-of-the-box network monitoring functionality in OpsMgr 2012</li>
	<li>more information about MDOP DEM, see <a href="http://www.microsoft.com/en-us/windows/enterprise/products-and-technologies/mdop/default.aspx." target="_blank">http://www.microsoft.com/en-us/windows/enterprise/products-and-technologies/mdop/default.aspx.</a></li>
	<li>Implementing AEM involves just two steps: activating the AEM feature on an OpsMgr management server, and deploying a group policy object (GPO) with AD.</li>
	<li>When you deploy AEM polices via a GPO, it configures registry keys on the client computer with values that change the behavior of Watson or WER.</li>
	<li>The WER collection component is an HTTPS listener end point, by default on port 51906.</li>
	<li>You will want to initiate the AEM feature of OpsMgr to detect application hangs and OS crashes on computers with or without OpsMgr agents</li>
	<li>The selected management server must have at least 2GB free disk space and cannot have an existing file share named “AEM,” as this is created during AEM activation.</li>
	<li>Tip: Install GPMC on the AEM Management Server</li>
	<li>If your OpsMgr administrator account is also a domain administrator, save time by installing the Group Policy Management Console (GPMC) on the management server that will have AEM enabled. You will need to import, link, and edit domain group policy.</li>
	<li>Enabling AEM on a management server by running the Configure Client Monitoring wizard also saves a group policy template with the .ADM file extension. The file name will be the FQDN of the management server;</li>
	<li>Because there is only one AEM server per management group and since you want to include all computers in the domain, you will usually link the GPO at the root of the domain.</li>
	<li>As the OpsMgr administrator, you may want to verify AEM is working and familiarize yourself with the console and reporting options available to view crash and hang information</li>
	<li>Working with the AeDebug Registry Key</li>
	<li>Installing other applications with debugging features such as Microsoft Visual Studio can modify the default debugger setting, resulting in a loss of AEM reporting functionality from that computer. To restore Watson as the default debugger and thereby enable AEM, you can run this .REG script on the Windows XP or 2003 computer (this does not apply to Windows Vista, Windows Server 2008, and later systems, which use WER and not drstsn32.exe):</li>
	<li>Tip: File and Share Security on the AEM Server</li>
	<li>The file shares created when enabling AEM on a management server have share permissions of EveryoneFull Control. Security is enforced at both the file and folder level. AEM setup creates two local computer security groups on the AEM server: AEMAgent and AEMUsers:
<ul>
	<li>The AEMAgent group membership consists of the local Administrators group with Full Control file and folder permissions.</li>
	<li>The AEMUsers group membership consists of all Authenticated Users—effectively all computer and user accounts in the domain—with special file and folder permissions.</li>
</ul>
</li>
	<li>These permissions allow error reports to be uploaded by client computers and processed by the management server. You should not need to modify these permissions.</li>
	<li>The server processes collect reports on a timed basis—it can take up to two minutes from the moment the client transmits the error report until you see the error reflected in the console</li>
	<li>Incorporating Surveys</li>
	<li>Consider employing a web-based survey technique to help solve particular errors in custom applications. You can stage a short automatic interview with the end user to gather targeted information. Here are some sample questions that might be helpful for a survey:
<ul>
	<li>What other applications (besides the one that crashed) were you running at the time of the crash?</li>
	<li>What steps can the IT department take to reproduce the crash that occurred?</li>
	<li>Will the application crash consistently if you follow the preceding steps? (Yes, Sometimes, or Never)</li>
	<li>Are you running any macros, COM add-ins, or templates?</li>
	<li>Does the crash occur for other people who log in to this computer? (Yes, No, or Unknown)</li>
</ul>
</li>
</ul>
&nbsp;

</div>
<h3 style="color: #000000;">Chapter 20: Interoperability and Cross Platform</h3>
<div style="color: #000000;">
<ul>
	<li>Tip: Community Resources on OpsMgr Reporting</li>
	<li>For ideas on how to make OpsMgr reports more useful in customer environments, consult these community resources:The transmission uses outbound TCP port 51907
<ul>
	<li><a href="http://contoso.se/blog/?p=537" target="_blank">http://contoso.se/blog/?p=537</a></li>
	<li><a href="http://blogs.technet.com/b/jimmyharper/archive/2009/02/21/aem-views-and-tables.aspx" target="_blank">http://blogs.technet.com/b/jimmyharper/archive/2009/02/21/aem-views-and-tables.aspx</a></li>
</ul>
</li>
	<li>you can have your clients send their CEIP data to the AEM server as a central collection point for the organization</li>
	<li>You must install the OpsMgr reporting feature for ODR to function</li>
	<li>The authors recommend Operations Manager administrators enable some or all of the Microsoft forwarding features, particularly those that apply to OpsMgr itself.</li>
	<li>There is also a specific Microsoft System Center Operations Manager 2012 Privacy Statement at <a href="http://technet.microsoft.com/library/hh321008.aspx." target="_blank">http://technet.microsoft.com/library/hh321008.aspx.</a> The specific OpsMgr privacy statement includes sections that address the privacy issues of each component described in this chapter, including CEIP, ODR, and WER.</li>
	<li>A single-server OpsMgr management group can easily handle 50 client computers; however, somewhere on the road toward and above 500 computers, a single management server will begin to slow down.</li>
	<li>deploying an agent to any computer incurs acquisition costs for the agent license, an incremental cost of resources consumed in the Operations Manager management group, and an ongoing cost to support the agent in terms of licensing, maintaining, and upgrading.</li>
	<li>The authors recommend selecting at least one client computer at each branch or remote office for Business Critical Monitoring. You generally want to know if these computers go offline—you monitor them like servers for high availability.</li>
	<li>This is a random, proportional sampling of client computers within each client population</li>
	<li>You can easily deploy multiple, smart sets of watcher nodes to measure the end-to-end service delivery of distributed enterprise applications.</li>
	<li>Very large environments should consider a dedicated management group for AEM. The guidelines at <a href="http://technet.microsoft.com/en-us/library/bb735402.aspx" target="_blank">http://technet.microsoft.com/en-us/library/bb735402.aspx</a> apply to AEM for OpsMgr 2007 and OpsMgr 2012.</li>
	<li>the Business Critical management pack allows for individual alerting.</li>
	<li>Note: About the Information Worker Management Pack</li>
	<li>There is a legacy information worker management pack available in the online catalog. This management pack includes monitoring of Office 2003 and Office 2007 applications. Microsoft has deprecated the Microsoft Information Worker management pack, and no further management packs for Office applications will be delivered.</li>
	<li>reports built on aggregated data require at least 24 hours of collection. Many of these reports are designed to trend data over large time-frames, such as three to six months, so there may not be much useful data for several weeks after installing the Client Monitoring management packs.</li>
	<li>You can only bring client computers into Business Critical Monitoring after discovery takes place and the clients have an agent installed on them</li>
	<li>some monitors that are data-processing intensive are turned off, even for Business Critical Monitoring. It is up to you to identify any Advanced Monitoring features you need and enable them on a case-by-case basis.</li>
	<li>An example of Advanced Monitoring is the Network Adapter state and performance views</li>
	<li>You cannot select client computers to be watcher nodes for your distributed applications unless you have deployed an OpsMgr agent to them.</li>
	<li>The authors recommend all client computers selected as distributed application watcher nodes also are subject to Business Critical Monitoring</li>
	<li>enables you not only to monitor UNIX and Linux platforms using OpsMgr, but application workloads on non-Windows operating systems, such as Java enterprise applications, sometimes known as JEE.</li>
	<li>Cross platform security has been enhanced as well with the introduction of sudo functionality, which eliminates the need for root credentials.</li>
	<li>For those platforms not supported by the OpsMgr 2012 release, Microsoft has published the Cross Platform Providers on CodePlex (<a href="http://scx.codeplex.com" target="_blank">http://scx.codeplex.com</a>) as open source (MS-PL license).</li>
	<li>Microsoft support for UNIX and Linux versions is aligned to the vendors’ support rather than an N-1 strategy. New versions of operating systems are supported within 180 days of release. Old versions are supported as long as the vendor provides support for that version.</li>
	<li>Import the following MP files to enable monitoring of the new Linux operating systems:
<ul>
	<li>Microsoft.Linux.Universal.Library.mp</li>
	<li>Microsoft.Linux.Universal.Monitoring.mp</li>
	<li>Microsoft.Linux.UniversalD.1.mpb (to support Debian and Ubuntu Linux agents)</li>
	<li>Microsoft.Linux.UniversalR.1.mpb (to support CentOS Linux agents)</li>
</ul>
</li>
	<li>For additional information, see <a href="http://technet.microsoft.com/en-us/library/jj656654.aspx." target="_blank">http://technet.microsoft.com/en-us/library/jj656654.aspx.</a></li>
	<li>Detailed cross platform OS monitoring capabilities in OpsMgr 2012 include
<ul>
	<li>CPU monitoring</li>
	<li>Disk monitoring</li>
	<li>Logical disk (file system)</li>
	<li>Physical disk</li>
	<li>Log file monitoring</li>
	<li>Memory/swap monitoring</li>
	<li>Network adapter monitoring</li>
	<li>Process monitoring</li>
</ul>
</li>
	<li>In addition to the cross platform monitoring features carried forward from OpsMgr 2007 R2, there are several new features in OpsMgr 2012, including
<ul>
	<li>File system nodes monitoring</li>
	<li>“Three state” file system free space monitors</li>
	<li>All new reports</li>
	<li>All new MP knowledge</li>
	<li>Java Enterprise Edition (JEE) application performance monitoring</li>
</ul>
</li>
	<li>The cross platform agent, which leverages OpenPegasus and supports the Distributed Management Task Force (DMTF) and Common Information Model (CIM), operates much differently.</li>
	<li>In this architecture, the agent is a listening agent that is called by a management server to collect performance and availability data. This means the cross platform agent is a lightweight; there is less code and less processing on UNIX/Linux systems than the Windows equivalent.</li>
	<li>Cross platform operating systems are discovered via SSHD (the standard secure shell daemon), and monitoring data is collected by management servers using the WSMan protocol, implemented via Windows Remote Management (WinRM) on the management server</li>
	<li>For detailed instructions in configuring certificates across the resource pool for high availability UNIX/Linux monitoring, see <a href="http://technet.microsoft.com/en-us/library/hh287152.aspx." target="_blank">http://technet.microsoft.com/en-us/library/hh287152.aspx.</a></li>
	<li>It is important to note sudo must be enabled with no password required in order for privilege elevation to function as designed</li>
	<li>Kerberos authentication is not possible when deploying agents to UNIX- or Linux-based computers, so certificates are used between the management server and these systems</li>
	<li>Certificates are not automatically deleted when you uninstall an agent; you must manually delete the certificates that are listed in the /etc/opt/microsoft/scx/ssl folder. To regenerate the certificates at install, you must remove this folder before agent installation.</li>
	<li>If you have a firewall on your UNIX- or Linux-based computer, you must open port 1270 (inbound). This port number is not configurable. If you are deploying agents in a low security environment and use the Discovery Wizard to deploy and sign the certificates, you must open the SSH port. The SSH port number is configurable. By default, SSH uses inbound TCP port 22.</li>
	<li>Each of the systems you want to discover with OpsMgr must be able to resolve their Internet Protocol (IP) address to their host name</li>
	<li>Discovering and deploying the cross platform agent requires a username and password for those systems to which you are deploying the agent</li>
	<li>The root account typically does not have access rights to log in via Secure Shell (SSH), which is the approach OpsMgr uses to deploy the agent. The cross platform agent installation executes the scripts using the sudo command (The “Notes on UNIX Commands” section includes details on this command) as part of the installation process.</li>
	<li>Before OpsMgr can discover any UNIX/Linux systems, WinRM must be configured to allow basic authentication.</li>
	<li>There are three accounts you must define as part of the cross platform functionality:
<ul>
	<li>Linux Unprivileged Monitoring Account: A monitoring Run As account for unprivileged monitoring</li>
	<li>Linux Privileged Monitoring Account: A monitoring Run As account for privileged monitoring</li>
	<li>Linux Agent Maintenance Account: An agent maintenance Run As account for upgrading, uninstalling, and other agent maintenance operations</li>
</ul>
</li>
	<li>the Distribution Security page, define whether these credentials will be stored in a less- or more-secure configuration, as shown in Figure 20.7:
<ul>
	<li>More secure: With the more-secure approach, you select the computers that will receive the credentials.</li>
	<li>Less secure: With the less-secure option, the credentials are sent automatically to all managed computers.</li>
</ul>
</li>
	<li>The more-secure approach is strongly recommended, targeting the Cross Platform Resource Group for distribution.</li>
	<li>You can also download the latest version of the cross platform MPs from the Microsoft website at <a href="http://www.microsoft.com/en-us/download/details.aspx?id=29696." target="_blank">http://www.microsoft.com/en-us/download/details.aspx?id=29696.</a></li>
	<li>You now have prepared to discover the UNIX/Linux systems. You have worked through name resolution, gathered account information from the UNIX/Linux systems, updated WinRM, configured accounts and profiles, and imported the UNIX/Linux management packs.</li>
	<li>Another option is to reissue the certificate and restart the cross platform agent, discussed at <a href="http://technet.microsoft.com/en-us/library/dd891009.aspx." target="_blank">http://technet.microsoft.com/en-us/library/dd891009.aspx.</a></li>
	<li>Tip: Using a Dedicated Management Pack</li>
	<li>The authors suggest using a dedicated management pack for the output of the UNIX and Linux monitoring templates.</li>
	<li>If you require deeper monitoring, Microsoft offers a Java Management Extension (JMX) application called BeanSpy (known during the OpsMgr 2012 beta period as the JMX Extender) that you load on the Java application server.</li>
	<li>Information collected from the application server instances includesThe application developer must choose to create custom MBeans and populate them with relevant statistics as the application runs.
<ul>
	<li>Applications deployed in the application server</li>
	<li>Number of garbage collections per second</li>
	<li>Time spent in garbage collection</li>
	<li>JVM memory usage and capacity</li>
	<li>Number of class loaded in the JVM</li>
	<li>Number of active threads</li>
</ul>
</li>
	<li>Before deep JEE application monitoring can begin, you must install and configure BeanSpy on the target Java application server</li>
	<li>OpsMgr requires that you specify the FQDN, instead of the host name or localhost, in the CN field of the Java application server certificate.</li>
	<li>Security Roles Required by BeanSpy</li>
	<li>You can find the security roles required for accessing and invoking methods in BeanSpy in the web.xml file (see Figure 20.48) located in the &lt;Tomcat_Install_Directory&gt;webappsBeanSpyWEB-INF directory on any Java server where BeanSpy is installed. The security roles are defined in this file between the &lt;security-role&gt;&lt;/security-role&gt; tags. The roles for BeanSpy are the JEE monitoring and JEE invoke roles. You must define a user account with membership in these roles in the Java server installation and provide it to OpsMgr in Run As accounts associated with the appropriate Run As profiles.</li>
	<li>Real World: Avoid Mixed Case User Names</li>
	<li>While most JEE platforms (including Tomcat 7.x, used in this chapter’s examples) support mixed case user names, OpsMgr does not seem to handle them well. A user name of OpsMgrJEE resulted in authentication failures. Switching the username to opsmgrjee (in both the tomcat-users.xml and Tomcat JEE Run As account) resolved the issue.</li>
	<li>the JEE management packs for OpsMgr 2012 are not available in the catalog; you must download them from <a href="http://www.microsoft.com/en-us/download/details.aspx?id=29270." target="_blank">http://www.microsoft.com/en-us/download/details.aspx?id=29270.</a></li>
	<li>Here are the management packs you should import to support all platforms:
<ul>
	<li>Microsoft.JEE.Library.mpb</li>
	<li>Microsoft.JEE.Templates.Library.mpb</li>
	<li>Microsoft.JEE.Templates.Library.xml</li>
</ul>
</li>
	<li>If your Java applications run as Windows services, discovery will fail and manual discovery is necessary. Manual discovery requires running a PowerShell script to add the Java application servers to OpsMgr manually.</li>
	<li>For more information on the manual discovery process, see Christopher Crammond’s article at <a href="http://blogs.technet.com/b/random_happy_dev_thoughts/archive/2012/05/21/manually-discovering-jee-application-servers-with-scom-2012.aspx.">http://blogs.technet.com/b/random_happy_dev_thoughts/archive/2012/05/21/manually-discovering-jee-application-servers-with-scom-2012.aspx.</a></li>
	<li>You can use telnet to verify ssh connectivity to the UNIX/Linux system on port 22</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 21: System Center 2012 Integration</h3>
<div style="color: #000000;">
<ul>
	<li>For the System Center Operations Manager Configuration Item (CI) Connector to work as expected, you must first import a set of management packs into Service Manager</li>
	<li>Before configuring the OpsMgr CI connector, you must first import the appropriate OpsMgr library management packs (MPs). The steps for importing management packs for OpsMgr CI connectors into Service Manager are discussed at <a href="http://technet.microsoft.com/en-us/library/hh519707.aspx.">http://technet.microsoft.com/en-us/library/hh519707.aspx.</a></li>
	<li><b>Note: Security for the Connector Role</b> To ensure full functionality of the connector, the account supplied should be a member of the Operations Manager Operators user role.</li>
	<li>See the “Accounts Required During Setup” section in the Planning Guide for System Center 2012 - Service Manager at <a href="http://technet.microsoft.com/en-us/library/hh495542.aspx,">http://technet.microsoft.com/en-us/library/hh495542.aspx,</a> also available for download at <a href="http://www.microsoft.com/en-us/download/details.aspx?id=27850.">http://www.microsoft.com/en-us/download/details.aspx?id=27850.</a></li>
	<li><b>Tip: Recommendations on Alert Closure </b>In testing, the authors discovered that if you select the Close alerts in Operations Manager when incidents are resolved or closed option on the Create a Schedule page in the OpsMgr Alert Connector Wizard, analysts could close alerts in OpsMgr that should remain open because the root cause of the alert has not been resolved.</li>
	<li>This generally does no real harm with rule-based alerts, as rules will simply raise another alert if necessary. However, when you close an alert for a monitor, the result is a monitor that remains in an error state without an associated open alert. This becomes a blind spot, as the monitor will never raise another alert until it has transitioned back to a healthy state and then back to an error state again. To avoid this risk, you could opt to only check the box labeled Resolve incidents automatically when the alerts in Operations Manager are closed,</li>
	<li><b>Real World: Use of Alert Resolution State for Sending to a Connector</b> A strategy the authors have found effective is to use alert resolution state as the sole criteria. Using custom resolution states enables granular control over which alerts are forwarded to Service Manager with relative ease.</li>
	<li>Since you are configuring OpsMgr integration with VMM, it is assumed you have deployed an OpsMgr agent to the VMM 2012 Server, all Hyper-V hosts, and VM guests.</li>
	<li>You need to install the System Center consoles to facilitate SDK access:</li>
	<li><b>Integrated Maintenance Mode (Hyper-V Host and Host Cluster Patching) </b>When you patch a Hyper-V host cluster (described at <a href="http://technet.microsoft.com/en-us/library/gg675088.aspx),">http://technet.microsoft.com/en-us/library/gg675088.aspx),</a> VMM contacts OpsMgr 2012 using an internal connector created when you configure VMM/OpsMgr integration and places the Hyper-V host in maintenance mode in Operations Manager while it is out of service and being updated. When patching is complete and the host is returned to service, VMM contacts OpsMgr to end maintenance mode for the Hyper-V host.</li>
	<li>This is required for the forecasting reports in the OpsMgr VMM 2012 management pack to be functional, and requires SSAS Analysis Management Objects (AMO) be installed on the Operations Manager reporting server</li>
	<li>Enter the SSAS server, SSAS instance, and SSAS port: The instance name must be the same as the SQL Server Reporting Services (SSRS) instance, which is MSSQLSERVER by default.</li>
	<li>Several hours after configuring SSAS integration in VMM 2012, the forecasting reports in the VMM 2012 Management Pack for OpsMgr 2012 should be functional.</li>
	<li>The Disable Operations Manager alerts while software updates run option triggers the ConfigMgr client to pause the OpsMgr agent during maintenance mode.</li>
	<li>The authors do not recommend using this option; it is better to use scheduled maintenance mode scripts with OpsMgr instead</li>
	<li>The authors suggest that in most cases, using the reporting capabilities of ConfigMgr to identify failed updates would suffice, making OpsMgr alerts on the condition unimportant.</li>
	<li>Number of community resources are available to help you get started, including these tutorials, available at <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/92651/Default.aspx:">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/92651/Default.aspx:</a></li>
	<li>Install the System Center Operations Manager console on each computer where a runbook server or runbook designer is installed that will interact with System Center Operations Manager.</li>
	<li>The third-party connectors available in OpsMgr 2007 R2 (at substantial additional cost in their original incarnation) have been replaced by integration packs in Orchestrator 2012 designed to support forwarding alerts to a number of third-party monitoring systems.</li>
	<li>OpsMgr with the VMM 2012 Management Pack is the best tool for monitoring not only resource performance and utilization in your Microsoft private cloud environment, but capacity as well</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 22: Authoring Management Packs and Reports</h3>
<div style="color: #000000;">
<ul>
	<li>
<div>Before writing a management pack, you should understand the concept of the health model</div></li>
	<li>To make full usage of the health model in OpsMgr, you should be aware of the different types of monitors</li>
	<li>Aggregate monitors are only used to roll up health; they do not monitor components by themselves</li>
	<li>Once you understand authoring concepts, the next step is gathering information about the application or device you want to monitor. This step is the most crucial in the entire process</li>
	<li>This means you should start by gathering monitoring requirements and designing a model before beginning to write the actual management pack.</li>
	<li>you need to identify the monitoring requirements of an application or service. This means being able to identify requirements and map them to the OpsMgr health model.</li>
	<li>pinpoint the exact components crucial to the application</li>
	<li>You cannot monitor a component for problems if it is not creating or logging events that you can check.</li>
	<li>For each component in your Visio diagrams, ask whether the component is significant and whether it requires monitoring. If so, what can be checked to monitor the component—services, processes, performance, or events?</li>
	<li>Here are examples of questions you could ask:Information must be usable to be valuable, or the result is a repository of all events ocurring in your environment.
<ul>
	<li>How does the application run?</li>
	<li>What does the end user expect to occur with the application?</li>
	<li>What services are running for the component?</li>
	<li>Are processes involved?</li>
	<li>Do you know of performance counters that could be of interest?</li>
	<li>How does the application perform logging? Does it log errors, or only informational events?</li>
	<li>Does the application currently log events in the Windows event logs?</li>
	<li>How can you tell the application is failing or know when it is about to fail?</li>
	<li>Have you experienced any significant outages for the application recently? Could these be detected, or avoided?</li>
	<li>How do you think the application can be monitored effectively?</li>
</ul>
</li>
	<li>Verify the components in your Visio diagram are discoverable. This can be difficult for inexperienced authors. You must be able to discover the class and its relationship</li>
	<li>Before writing the management packs used in the examples, you must first install Visio 2010 Premium Service Pack (SP) 1 and/or Visual Studio 2010; then install the extensions.</li>
	<li>The System Center 2012 Visio MP Designer is available at <a href="http://www.microsoft.com/en-us/download/details.aspx?id=30170.">http://www.microsoft.com/en-us/download/details.aspx?id=30170.</a></li>
	<li>Download the System Center 2012 Visual Studio Authoring Extensions from <a href="http://www.microsoft.com/en-us/download/details.aspx?id=30169.">http://www.microsoft.com/en-us/download/details.aspx?id=30169.</a></li>
	<li>Caution: Connector Mode Default</li>
	<li>The connector mode, listed in Table 22.1, is set to true by default, which means the tool will generate a connector management pack. Change this to false, since you want to generate a monitoring management pack.</li>
	<li>For a full pattern overview, see the TechNet wiki at <a href="http://social.technet.microsoft.com/wiki/contents/articles/6939.pattern-reference-for-visio-management-pack-designer.aspx.">http://social.technet.microsoft.com/wiki/contents/articles/6939.pattern-reference-for-visio-management-pack-designer.aspx.</a></li>
	<li>the Authoring guide at <a href="http://technet.microsoft.com/en-us/library/hh457564.aspx)">http://technet.microsoft.com/en-us/library/hh457564.aspx)</a></li>
	<li>best practice is including a description with a meaningful name so the operator understands what he is looking at.</li>
	<li>Visio Studio can automatically seal your management pack after you create a key file.</li>
	<li>It is a best practice to seal those management packs containing classes, as a management pack must be sealed to reuse its classes in other management packs.</li>
	<li>Before sealing the management pack, you must create a key file. Jonathan Almquist documents the process for creating a key file at <a href="http://blogs.technet.com/b/jonathanalmquist/archive/2008/08/19/seal-a-management-pack.aspx.">http://blogs.technet.com/b/jonathanalmquist/archive/2008/08/19/seal-a-management-pack.aspx.</a></li>
	<li>Creating a key file requires sn.exe, part of the .NET Framework SDK downloadable at <a href="http://www.microsoft.com/en-us/download/details.aspx?id=19988.">http://www.microsoft.com/en-us/download/details.aspx?id=19988.</a> After obtaining sn.exe, run this command to create the key file Unleashedkey.snk, which you can use to seal MPs:
<ul>
	<li>sn.exe -k D:MPkeyUnleashedkey.snk</li>
</ul>
</li>
	<li>The project creates unsealed and sealed versions of your management pack in the location of your project</li>
	<li>Registry discoveries have the lowest performance impact; the authors recommend checking the registry first for application-specific parameters to identify your application when writing a discovery rule</li>
	<li>The authors recommend being as precise as possible when targeting a discovery.</li>
	<li>For a complete overview on the settings and configuration references for the Visio MP Designer, see the TechNet Wiki page at <a href="http://social.technet.microsoft.com/wiki/contents/articles/6938.monitoring-and-modeling-shape-reference-for-visio-management-pack-designer.aspx.">http://social.technet.microsoft.com/wiki/contents/articles/6938.monitoring-and-modeling-shape-reference-for-visio-management-pack-designer.aspx.</a></li>
	<li>Find a complete list of alert description variables in Kevin Holman’s blog at <a href="http://blogs.technet.com/b/kevinholman/archive/2007/12/12/adding-custom-information-to-alert-descriptions-and-notifications.aspx.">http://blogs.technet.com/b/kevinholman/archive/2007/12/12/adding-custom-information-to-alert-descriptions-and-notifications.aspx.</a></li>
	<li>Be sure you understand how property bags work, as they are a powerful tool to change regular scripts into OpsMgr-compatible scripts. You only need several lines of code to make the script OpsMgr-aware</li>
	<li>For further reading on property bags and scripting in OpsMgr, refer toRules are primarily used for data collection or alerting only
<ul>
	<li><a href="http://blogs.technet.com/b/momteam/archive/2009/02/13/mp-authoring-resources.aspx">http://blogs.technet.com/b/momteam/archive/2009/02/13/mp-authoring-resources.aspx</a></li>
	<li><a href="http://blogs.technet.com/b/authormps/archive/2011/02/24/property-bags-and-multi-instance-monitoring.aspx">http://blogs.technet.com/b/authormps/archive/2011/02/24/property-bags-and-multi-instance-monitoring.aspx</a></li>
	<li><a href="http://www.systemcentercentral.com/Downloads/DownloadsDetails/tabid/144/IndexID/7803/Default.aspx">http://www.systemcentercentral.com/Downloads/DownloadsDetails/tabid/144/IndexID/7803/Default.aspx</a></li>
</ul>
</li>
	<li>To seal a Visio created management pack, refer to <a href="http://technet.microsoft.com/en-us/library/hh457550.">http://technet.microsoft.com/en-us/library/hh457550.</a></li>
	<li>To test the Windows event monitors, use the EventCreate tool, which is part of Windows.</li>
	<li>Building reports with Report Builder by Stefan Koell: <a href="http://www.code4ward.net/main/Blog/tabid/70/EntryId/81/How-to-use-Report-Builder-to-create-custom-reports-in-SCOM-2007.aspx">http://www.code4ward.net/main/Blog/tabid/70/EntryId/81/How-to-use-Report-Builder-to-create-custom-reports-in-SCOM-2007.aspx</a>A big issue with custom reporting in OpsMgr is using the correct class and performance rules and targeting the reports. To target your reports correctly you must identify the target class and the performance collection rule.
<ul>
	<li>Building reports in SQL Server Business Intelligence Development Studio by Oskar Landman: <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/60805/Default.aspx">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/60805/Default.aspx</a></li>
	<li>Building Linked reports in OpsMgr 2007 R2 by Pete Zerger: <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/64107/Default.aspx">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/64107/Default.aspx</a></li>
	<li>Reporting links for creating custom reports by Stefan Stranger: <a href="http://blogs.technet.com/b/stefan_stranger/archive/2011/01/27/opsmgr-custom-reporting-links.aspx">http://blogs.technet.com/b/stefan_stranger/archive/2011/01/27/opsmgr-custom-reporting-links.aspx</a></li>
</ul>
</li>
	<li>The easiest way to determine the correct target is to open the performance view and look at the different performance rules</li>
	<li>Tip: Targeting in Reports</li>
	<li>The most difficult part about reporting is defining the correct target and performance rule. Use the Monitoring pane to verify you have the correct information. Navigate to the performance view containing the rule you want to report on, select the properties of the rule to determine the target class, and note the performance rule name. With the target class and rule identified, you can create any report.</li>
	<li>Another more advanced option is writing reports based on groups. Be sure you are targeting properly. If the performance counters are targeted at the logical disk and you want to create a group, only add logical disks in this group and target your report on this group for free disk space.</li>
	<li>The advantage to groups is they can be populated dynamically, so you only have to create a single report. If a new instance is added, the dynamic population rule automatically adds the instance to the group. The only downside is you generate the report based on the overall performance of the group and have to run a child report to get the information per instance.</li>
	<li>This information is also is described in the article at <a href="http://www.bictt.com/blogs/bictt.php/2010/11/28/scom-reports-on-performance-counters-for-large-groups-of-servers.">http://www.bictt.com/blogs/bictt.php/2010/11/28/scom-reports-on-performance-counters-for-large-groups-of-servers.</a></li>
</ul>
</div>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 23: PowerShell and Operations Manager</h3>
<div style="color: #000000;">
<ul>
	<li>Use a self-signed certificate, using the .NET Framework 2.0 software development kit (SDK) to create the certificate</li>
	<li>Here are two great resources that discuss using Microsoft’s certificate creation tool, makecert.exe, to generate certificates to create self-signed PowerShell scripts:
<ul>
	<li>Don Jones’ TechNet Magazine article “Sign Here, Please,” available at <a href="http://technet.microsoft.com/en-us/magazine/2008.04.powershell.aspx">http://technet.microsoft.com/en-us/magazine/2008.04.powershell.aspx</a></li>
	<li>Scott Hanselman’s blog post “Signing PowerShell Scripts” at <a href="http://www.hanselman.com/blog/SigningPowerShellScripts.aspx">http://www.hanselman.com/blog/SigningPowerShellScripts.aspx</a></li>
</ul>
</li>
	<li>If you have an existing PKI infrastructure that can be utilized to generate a certificate, there is a great two-part series on signing PowerShell scripts with an enterprise PKI from the Microsoft Scripting Guys, <a href="http://blogs.technet.com/b/heyscriptingguy/archive/2010/06/16/hey-scripting-guy-how-can-i-sign-windows-powershell-scripts-with-an-enterprise-windows-pki-part-1-of-2.aspx">http://blogs.technet.com/b/heyscriptingguy/archive/2010/06/16/hey-scripting-guy-how-can-i-sign-windows-powershell-scripts-with-an-enterprise-windows-pki-part-1-of-2.aspx</a> and <a href="http://blogs.technet.com/b/heyscriptingguy/archive/2010/06/17/hey-scripting-guy-how-can-i-sign-windows-powershell-scripts-with-an-enterprise-windows-pki-part-2-of-2.aspx.">http://blogs.technet.com/b/heyscriptingguy/archive/2010/06/17/hey-scripting-guy-how-can-i-sign-windows-powershell-scripts-with-an-enterprise-windows-pki-part-2-of-2.aspx.</a></li>
	<li>Tip: More Information on the Pipeline</li>
	<li>A discussion about the PowerShell pipeline is beyond the scope of this chapter. For more information about the pipeline, PowerShell MVP Don Jones provides several resources:
<ul>
	<li>The article at <a href="http://technet.microsoft.com/en-us/magazine/2007.07.powershell.aspx">http://technet.microsoft.com/en-us/magazine/2007.07.powershell.aspx</a> is a nice discussion of the pipeline and about what it can do for you.</li>
	<li>Don created a pipeline input workbook that is a good step-by-step walkthrough of how the pipeline works, available on the morelunches.com website. See <a href="http://morelunches.com/files/powershell3/PipelineInput.pdf">http://morelunches.com/files/powershell3/PipelineInput.pdf</a> for information.</li>
</ul>
</li>
	<li>Two common uses of variables are to store information that will be later utilized within a script and to store information that is a result of running a script.</li>
	<li>You can also read more about variables in the tutorial at <a href="http://www.powershellpro.com/powershell-tutorial-introduction/variables-arrays-hashes/">http://www.powershellpro.com/powershell-tutorial-introduction/variables-arrays-hashes/.</a></li>
	<li>Tip: $True and $False</li>
	<li>To get the full story on Boolean values and operators see Jeffrey Snover’s blog post at <a href="http://blogs.msdn.com/b/powershell/archive/2006/12/24/boolean-values-and-operators.aspx.">http://blogs.msdn.com/b/powershell/archive/2006/12/24/boolean-values-and-operators.aspx.</a></li>
	<li>An example of computer discovery and push install of the agent through PowerShell is demonstrated in greater depth in the posting on automating agent discovery and deployment with PowerShell at <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94248/Default.aspx.">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94248/Default.aspx.</a></li>
	<li>The performance difference is due to that when the criteria parameter is used, the value passed is provided directly to the SQL Server database, and only the relevant data is returned. This means the data is filtered before it is returned to the PowerShell session, reducing the number of objects that must be passed back to the Windows PowerShell console.</li>
	<li>Tip: Collection of OpsMgr 2007 Single Line Examples in OpsMgr 2012</li>
	<li>For examples of OpsMgr2007 PowerShell examples migrated to OpsMgr 2012, see the collection of updated single line PowerShell scripts (one-liners) at <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/89870/Default.aspx.">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/89870/Default.aspx.</a></li>
	<li>Three resource pools are created by default: AD Assignment Resource Pool, All Management Servers Resource Pool, and Notifications Resource Pool. The memberships of these three groups are set to automatic, meaning any management server added to the environment takes part in these resource pools.</li>
	<li>Backing Up Unsealed Management Packs Nightly</li>
	<li>Part of a comprehensive backup strategy for OpsMgr would include backing up unsealed management packs on a nightly basis to the file system</li>
	<li>This is to ensure changes made to the OpsMgr environment, such as overrides, custom rules, and monitors, are captured and backed up. Chapter 12 includes a nice script that does just this job using the OpsMgr cmdlet Export-SCOMManagementPack.</li>
	<li>With a bit of effort, you can update agent failover settings in bulk as described in the article on updating agent failover settings from a spreadsheet with PowerShell at <a href="http://www.systemcentercentral.com/tabid/143/indexid/95393/default.aspx.">http://www.systemcentercentral.com/tabid/143/indexid/95393/default.aspx.</a></li>
	<li>Fortunately, with the OpsMgr Shell, you can easily balance the agent load across multiple management servers. The sample script referenced in this section evenly distributes agents across two or more management servers. Running this script as part of a schedule task can ensure the agent load is balanced as your environment grows and evolves.</li>
	<li>While it is relatively easy to balance agents across two management servers with PowerShell, the script logic becomes significantly more complex when you need to support 2–N management servers. Fortunately, that did not bother Andreas Zuckerhut, who routinely writes PowerShell-based automation solutions for OpsMgr that rate at the high end of the complexity scale. You can find a copy of this community-developed solution in the OpsMgr by Example series at <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/96292/Default.aspx.">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/96292/Default.aspx.</a></li>
	<li>The following is a list of considerations and preparatory tasks to ensure your Orchestrator runbook server can successfully run OpsMgr Shell scripts:
<ul>
	<li>Enable script execution for the 32-bit PowerShell instance on the Orchestrator runbook server. While your runbook server is running 64-bit Windows Server 2008 R2 or 2012 (with System Center 2012 SP 1), Orchestrator is still a 32-bit application, and as such, always launches a 32-bit PowerShell instance.</li>
</ul>
</li>
	<li>For details on how to set PowerShell script execution policy, see the “PowerShell Execution Policy” section.
<ul>
	<li>Install the OpsMgr Operations console on your runbook servers. Without the OpsMgr Shell present on the runbook server, OpsMgr PowerShell scripts will fail every time.</li>
	<li>Configure a connection to your OpsMgr management group(s) in the Global Configuration area of the Orchestrator Runbook Designer, available on the Tools -&gt; Options menu. To ensure all scripts have adequate permissions contained within runbooks, you will need to provide an account with OpsMgr administrator privileges. For details on how to configure OpsMgr connectivity from Orchestrator, refer to Chapter 21.</li>
</ul>
</li>
	<li>You will find detailed examples of Orchestrator runbooks interacting with OpsMgr via PowerShell in System Center 2012 Orchestrator Unleashed (<a href="http://www.amazon.com/System-Center-2012-Orchestrator-Unleashed/dp/0672336103" target="_blank">http://www.amazon.com/System-Center-2012-Orchestrator-Unleashed/dp/0672336103</a>, Sams, 2013).</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Chapter 24: Operations Manager for the Service Provider</h3>
<div style="color: #000000;">
<ul>
	<li>The maximum number of supported agents per management group is somewhere between 6,000 and 15,000, depending on factors such as the number of management packs and connected consoles.</li>
	<li>Remembering no single management server should exceed 3,000 downstream agents even when one management server has failed.</li>
	<li>The limitation comes from the quantity of manageable records in a data warehouse database, which is about 15,000</li>
	<li>Specifically, the total number of managed objects in all connected management groups cannot exceed 15,000 using a shared data warehouse database.</li>
	<li>Self-renewal features and require little administrative work for up to 20 years, the maximum recommended lifetime of a root certificate.</li>
	<li>The OpsMgr authentication certificate generally has a lifetime of two years.</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Appendix A: OpsMgr by Example: Configuring and Tuning Management Packs</h3>
<div style="color: #000000;">
<ul>
	<li>For new “by example” information and updates to existing articles, be sure to check <a href="http://opsmgrunleashed.wordpress.com/" target="_blank">http://opsmgrunleashed.wordpress.com/</a> and the OpsMgr by Example series at <a href="http://www.systemcentercentral.com/tabid/150/tag/Blog+ByExample/Default.aspx." target="_blank">http://www.systemcentercentral.com/tabid/150/tag/Blog+ByExample/Default.aspx.</a></li>
	<li>For additional information, see Cameron Fuller’s blog article at <a href="http://blogs.catapultsystems.com/cfuller/archive/2012/08/16/the-top-5-benefits-of-combining-operations-manager-and-sharepoint-%5Bscom-sysctr-sharepoint%5D.aspx)." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2012/08/16/the-top-5-benefits-of-combining-operations-manager-and-sharepoint-[scom-sysctr-sharepoint].aspx).</a></li>
	<li>Tip: Upgrading an Operating System: How to Prevent Discovery Problems
<ul>
	<li>As a best practice, before you upgrade the operating system on a monitored computer, uninstall the Operations Manager agent. After the upgrade, reinstall the Operations Manager agent. This is because a parent class that is not version-specific hosts the objects the management pack discovers, such as logical disks. When you upgrade the OS, the order in which discovery occurs can result in duplicate objects being discovered.</li>
</ul>
</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Appendix B: Performance Counters</h3>
<div style="color: #000000;">
<ul>
	<li>NONE</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Appendix C: Registry Settings</h3>
<div style="color: #000000;">
<ul>
	<li>NONE</li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Appendix D: Reference URLs</h3>
<div>
<ul>
	<li style="color: #000000;">You will also want to read Satya Vel’s article on network bandwidth utilization at <a href="http://blogs.technet.com/momteam/archive/2007/10/22/network-bandwidth-utilization-for-the-various-opsmgr-2007-roles.aspx." target="_blank">http://blogs.technet.com/momteam/archive/2007/10/22/network-bandwidth-utilization-for-the-various-opsmgr-2007-roles.aspx.</a></li>
	<li style="color: #000000;">Pete Zerger’s discussion of the OpsMgr 2007 R2 Authoring console at <a href="http://www.systemcentercentral.com/Details/tabid/147/IndexID/24878/Default.aspx." target="_blank">http://www.systemcentercentral.com/Details/tabid/147/IndexID/24878/Default.aspx.</a> (You must be logged into System Center Central to download the article.)</li>
	<li style="color: #000000;">An in-depth article on IOPS for the operational and data warehouse databases is at <a href="http://blogs.technet.com/b/momteam/archive/2008/06/24/performance-iops-for-the-db-and-dw-in-opsmgr-2007.aspx." target="_blank">http://blogs.technet.com/b/momteam/archive/2008/06/24/performance-iops-for-the-db-and-dw-in-opsmgr-2007.aspx.</a></li>
	<li style="color: #000000;">Kevin Holman discusses recommended SQL maintenance for the OpsMgr databases at <a href="http://blogs.technet.com/b/kevinholman/archive/2008/04/12/what-sql-maintenance-should-i-perform-on-my-opsmgr-databases.aspx." target="_blank">http://blogs.technet.com/b/kevinholman/archive/2008/04/12/what-sql-maintenance-should-i-perform-on-my-opsmgr-databases.aspx.</a></li>
	<li style="color: #000000;"><a href="http://learning.microsoft.com/Manager/Catalog.aspx?nav=trainingtype%3aClassroom+Training&amp;qry=system+center+2012" target="_blank">http://learning.microsoft.com/Manager/Catalog.aspx?nav=trainingtype%3aClassroom+Training&amp;qry=system+center+2012</a> will get you a listing of Microsoft-developed training for System Center 2012.</li>
	<li style="color: #000000;">Training videos are available at <a href="http://technet.microsoft.com/en-us/opsmgr/bb498237.aspx." target="_blank">http://technet.microsoft.com/en-us/opsmgr/bb498237.aspx.</a> This page is updated as new material becomes available.</li>
	<li style="color: #000000;">To clean up clutter from the Monitoring pane of the Operations console, see Cameron Fuller’s article at <a href="http://blogs.catapultsystems.com/cfuller/archive/2011/05/11/quicktricks-decluttering-the-monitoring-pane-view.aspx." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2011/05/11/quicktricks-decluttering-the-monitoring-pane-view.aspx.</a></li>
	<li style="color: #000000;">To identify computers without an installed agent, see <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94221/Default.aspx," target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94221/Default.aspx,</a> and then read about automating agent installation with PowerShell at <a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94248/Default.aspx." target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94248/Default.aspx.</a></li>
	<li style="color: #000000;">Jonathan Almquist discusses when one should use Active Directory Integration in OpsMgr at <a href="http://blogs.technet.com/b/jonathanalmquist/archive/2010/06/14/ad-integration-considerations.aspx." target="_blank">http://blogs.technet.com/b/jonathanalmquist/archive/2010/06/14/ad-integration-considerations.aspx.</a></li>
	<li style="color: #000000;">How does Active Directory Integration work? See Steve Rachui’s article at <a href="http://blogs.msdn.com/b/steverac/archive/2008/03/20/opsmgr-ad-integration-how-it-works.aspx." target="_blank">http://blogs.msdn.com/b/steverac/archive/2008/03/20/opsmgr-ad-integration-how-it-works.aspx.</a></li>
	<li style="color: #000000;">You should never close an alert on a monitor, unless it didn’t auto close on its own. Read about this at <a href="http://blogs.catapultsystems.com/cfuller/archive/2011/04/15/opsmgr-never-close-an-alert-for-a-monitor-%E2%80%93-the-exception-to-the-%E2%80%9Crule-of-the-monitor%E2%80%9D.aspx." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2011/04/15/opsmgr-never-close-an-alert-for-a-monitor-%E2%80%93-the-exception-to-the-%E2%80%9Crule-of-the-monitor%E2%80%9D.aspx.</a></li>
	<li style="color: #000000;">Cameron Fuller discusses benefits of using SharePoint with Operations Manager at <a href="http://blogs.catapultsystems.com/cfuller/archive/2012/08/16/the-top-5-benefits-of-combining-operations-manager-and-share-point-%5Bscom-sysctr-sharepoint%5D.aspx." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2012/08/16/the-top-5-benefits-of-combining-operations-manager-and-share-point-[scom-sysctr-sharepoint].aspx.</a></li>
	<li style="color: #000000;">For details on using web application availability monitoring to configure monitoring of web applications, see Marnix Wolf’s article at <a href="http://thoughtsonopsmgr.blogspot.com/2012/06/how-to-use-web-application-availability.html," target="_blank">http://thoughtsonopsmgr.blogspot.com/2012/06/how-to-use-web-application-availability.html,</a> and the OpsMgr product team’s article at <a href="http://blogs.technet.com/b/momteam/archive/2012/05/31/using-the-web-application-availability-monitoring-to-monitor-web-applications-health.aspx." target="_blank">http://blogs.technet.com/b/momteam/archive/2012/05/31/using-the-web-application-availability-monitoring-to-monitor-web-applications-health.aspx.</a></li>
	<li style="color: #000000;">The OpsMgr engineering team provides some Windows Server 2008 dashboards and a tool to help create your own customized dashboards at <a href="http://blogs.technet.com/b/momteam/archive/2012/06/12/free-windows-server-2008-dashboards-for-opsmgr-2012-and-tool-to-help-create-your-own-customized-dashboards.aspx." target="_blank">http://blogs.technet.com/b/momteam/archive/2012/06/12/free-windows-server-2008-dashboards-for-opsmgr-2012-and-tool-to-help-create-your-own-customized-dashboards.aspx.</a></li>
	<li style="color: #000000;">For some useful SQL queries to use with OpsMgr, see <a href="http://blogs.technet.com/b/kevinholman/archive/2007/10/18/useful-operations-manager-2007-sql-queries.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2007/10/18/useful-operations-manager-2007-sql-queries.aspx</a></li>
	<li style="color: #000000;">Generating reports with data can be challenging. Read some tips at <a href="http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/10-system-center-operations-manager-reporting-tips-140603." target="_blank">http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/10-system-center-operations-manager-reporting-tips-140603.</a></li>
	<li style="color: #000000;">For ideas on how to make AEM reports more useful, consult these resources:Read how to optimize SQL Server 2012 for private cloud at <a href="http://www.microsoft.com/sqlserver/en/us/solutions-technologies/hybrid-it/private-cloud.aspx." target="_blank">http://www.microsoft.com/sqlserver/en/us/solutions-technologies/hybrid-it/private-cloud.aspx.</a></li>
	<li><a href="http://contoso.se/blog/?p=537" target="_blank">http://contoso.se/blog/?p=537</a></li>
	<li><a href="http://blogs.technet.com/b/jimmyharper/archive/2009/02/21/aem-views-and-tables.aspx" target="_blank">http://blogs.technet.com/b/jimmyharper/archive/2009/02/21/aem-views-and-tables.aspx</a></li>
	<li><span style="color: #000000;"> </span></li>
	<li><span style="color: #000000;">Michael Pearson has an excellent article discussing SQL Server Reporting Services (SSRS) Recovery Planning, available online from the SQL Server Central community at </span><a href="http://www.sqlservercentral.com/columnists/mpearson/recoveryplanningforsqlreportingservices.aspx." target="_blank">http://www.sqlservercentral.com/columnists/mpearson/recoveryplanningforsqlreportingservices.aspx.</a><span style="color: #000000;"> You must register with SQLServerCentral to view the full article.</span></li>
	<li><span style="color: #000000;">For information on the types of SQL maintenance to perform on your OpsMgr databases, check Kevin Holman’s posting at </span><a href="http://blogs.technet.com/kevinholman/archive/2008/04/12/what-sql-maintenance-should-i-perform-on-my-opsmgr-databases.aspx." target="_blank">http://blogs.technet.com/kevinholman/archive/2008/04/12/what-sql-maintenance-should-i-perform-on-my-opsmgr-databases.aspx.</a></li>
	<li><span style="color: #000000;">Here’s some information on setting up SQL Server clusters:For information on debugging the infamous alert “Script or Executable Failed to Run,” see </span><a href="http://blogs.catapultsystems.com/cfuller/archive/2012/11/28/blastfromthepast-debugging-the-script-or-executable-failed-to-run-alert.aspx." target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2012/11/28/blastfromthepast-debugging-the-script-or-executable-failed-to-run-alert.aspx.</a></li>
	<li><a href="http://msdn.microsoft.com/en-us/library/ms179530.aspx." target="_blank">http://msdn.microsoft.com/en-us/library/ms179530.aspx.</a></li>
	<li><a href="http://blogs.technet.com/pfe-ireland/archive/2008/05/16/how-to-create-a-windows-server-2008-cluster-within-hyper-v-using-simulated-iscsi-storage.aspx" target="_blank">http://blogs.technet.com/pfe-ireland/archive/2008/05/16/how-to-create-a-windows-server-2008-cluster-within-hyper-v-using-simulated-iscsi-storage.aspx</a><span style="color: #000000;"> discusses creating a virtual cluster on Windows 2008/Hyper-V.</span></li>
	<li><span style="color: #000000;">Kevin Holman provides an example of monitoring a non-Microsoft database at </span><a href="http://blogs.technet.com/b/kevinholman/archive/2012/03/19/opsmgr-how-to-monitor-non-microsoft-sql-databases-in-scom-an-example-using-postgre-sql.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2012/03/19/opsmgr-how-to-monitor-non-microsoft-sql-databases-in-scom-an-example-using-postgre-sql.aspx</a></li>
	<li><span style="color: #000000;">Maarten Damen provides an example of how to monitor an Oracle database with an OLE DB watcher at </span><a href="http://www.maartendamen.com/2010/09/monitor-an-oracle-database-with-a-scom-oledb-watcher" target="_blank">http://www.maartendamen.com/2010/09/monitor-an-oracle-database-with-a-scom-oledb-watcher</a></li>
	<li><span style="color: #000000;">Learn about OpsMgr key performance indicators, read Cameron Fuller’s article at </span><a href="http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/Operations-Manager-Key-Performance-Indicators-128969." target="_blank">http://www.windowsitpro.com/article/microsoft-system-center-operations-manager-2007/Operations-Manager-Key-Performance-Indicators-128969.</a></li>
	<li><span style="color: #000000;">Kevin Holman discusses self-tuning thresholds (STTs) and how they are created and tuned correctly at </span><a href="http://blogs.technet.com/b/kevinholman/archive/2008/03/19/self-tuning-thresholds-love-and-hate.aspx." target="_blank">http://blogs.technet.com/b/kevinholman/archive/2008/03/19/self-tuning-thresholds-love-and-hate.aspx.</a></li>
	<li><span style="color: #000000;">The Alert Forward management pack is available from </span><a href="http://www.systemcentercentral.com/tabid/145/indexId/11518/Default.aspx." target="_blank">http://www.systemcentercentral.com/tabid/145/indexId/11518/Default.aspx.</a></li>
	<li><span style="color: #000000;">Read about how to use custom groups to simplify the Operations console at </span><a href="http://opsmgrunleashed.wordpress.com/2009/08/28/how-to-use-customized-groups-to-simplify-the-opsmgr-console-for-server-owners-%E2%80%93-using-custom-groups-with-subscriptions-one-off-notifications/" target="_blank">http://opsmgrunleashed.wordpress.com/2009/08/28/how-to-use-customized-groups-to-simplify-the-opsmgr-console-for-server-owners-%E2%80%93-using-custom-groups-with-subscriptions-one-off-notifications/.</a></li>
	<li><span style="color: #000000;">Learn about global service monitoring, newly available with SP 1, see </span><a href="http://blogs.technet.com/b/momteam/archive/2012/06/19/global-service-monitor-for-system-center-2012-observing-application-availability-from-an-outside-in-perspective.aspx." target="_blank">http://blogs.technet.com/b/momteam/archive/2012/06/19/global-service-monitor-for-system-center-2012-observing-application-availability-from-an-outside-in-perspective.aspx.</a></li>
	<li><span style="color: #000000;">Building reports with Report Builder by Stefan Koell: </span><a href="http://www.code4ward.net/main/Blog/tabid/70/EntryId/81/How-to-use-Report-Builder-to-create-custom-reports-in-SCOM-2007.aspx." target="_blank">http://www.code4ward.net/main/Blog/tabid/70/EntryId/81/How-to-use-Report-Builder-to-create-custom-reports-in-SCOM-2007.aspx.</a></li>
	<li><span style="color: #000000;">Building reports in SQL Server Business Intelligence Development Studio by Oskar Landman: </span><a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/60805/Default.aspx." target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/60805/Default.aspx.</a></li>
	<li><span style="color: #000000;">Building linked reports in OpsMgr 2007 R2 by Pete Zerger: </span><a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/64107/Default.aspx." target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/64107/Default.aspx.</a></li>
	<li><span style="color: #000000;">Reporting links for creating custom reports by Stefan Stranger: </span><a href="http://blogs.technet.com/b/stefan_stranger/archive/2011/01/27/opsmgr-custom-reporting-links.aspx." target="_blank">http://blogs.technet.com/b/stefan_stranger/archive/2011/01/27/opsmgr-custom-reporting-links.aspx.</a></li>
	<li><span style="color: #000000;">Here are some examples of how to query SQL and use the results in OpsMgr, including how to perform checks for a SQL full or differential backup and how to monitor the default management pack:Read about how network monitoring works at </span><a href="http://blogs.technet.com/b/momteam/archive/sell/09/20/what-gets-monitored-with-system-center-operations-manager-2012-network-monitoring.aspx" target="_blank">http://blogs.technet.com/b/momteam/archive/sell/09/20/what-gets-monitored-with-system-center-operations-manager-2012-network-monitoring.aspx</a></li>
	<li><a href="http://blogs.technet.com/b/stefan_stranger/archive/2009/02/02/opsmgr-sql-full-or-differential-backup-check.aspx" target="_blank">http://blogs.technet.com/b/stefan_stranger/archive/2009/02/02/opsmgr-sql-full-or-differential-backup-check.aspx</a></li>
	<li><span style="color: #000000;">Kevin Holman discusses collecting and monitoring information from WMI as performance data at </span><a href="http://blogs.technet.com/b/kevinholman/archive/2008/07/02/collecting-and-monitoring-information-from-wmi-as-performance-data.aspx." target="_blank">http://blogs.technet.com/b/kevinholman/archive/2008/07/02/collecting-and-monitoring-information-from-wmi-as-performance-data.aspx.</a></li>
	<li><span style="color: #000000;">Microsoft has published a whitepaper on performance tuning guidelines for Windows Server 2008 R2 at </span><a href="http://msdn.microsoft.com/en-us/windows/hardware/gg463392." target="_blank">http://msdn.microsoft.com/en-us/windows/hardware/gg463392.</a><span style="color: #000000;"> Guidelines for Windows Server 2012 are at </span><a href="http://msdn.microsoft.com/en-us/library/windows/hardware/jj248719.aspx." target="_blank">http://msdn.microsoft.com/en-us/library/windows/hardware/jj248719.aspx.</a></li>
	<li><span style="color: #000000;">Microsoft talks about mapping your requirements to an OpsMgr design at </span><a href="http://technet.microsoft.com/en-us/library/bb735402.aspx." target="_blank">http://technet.microsoft.com/en-us/library/bb735402.aspx.</a></li>
	<li><span style="color: #000000;">Collecting security events: </span><a href="http://technet.microsoft.com/en-us/library/hh212908.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh212908.aspx</a></li>
	<li><a href="http://technet.microsoft.com/en-us/library/hh212908.aspx#bkmk_acsonunixandlinus." target="_blank">http://technet.microsoft.com/en-us/library/hh212908.aspx#bkmk_acsonunixandlinus.</a></li>
	<li><span style="color: #000000;">ACS on UNIX and Linux is discussed at </span><a href="http://technet.microsoft.com/en-us/library/hh212908.aspx#bkmk_acsonunixandlinus." target="_blank">http://technet.microsoft.com/en-us/library/hh212908.aspx#bkmk_acsonunixandlinus.</a></li>
	<li><span style="color: #000000;">If you have a requirement to monitor VMware, check out Veeam’s monitoring for System Center at </span><a href="http://www.veeam.com/vmware-microsoft-esx-monitoring.html." target="_blank">http://www.veeam.com/vmware-microsoft-esx-monitoring.html.</a></li>
	<li><span style="color: #000000;">The Operations Manager Rule and Monitor Targeting Poster is available at </span><a href="http://download.microsoft.com/download/f/a/7/fa73e146-ab8a-4002-9311-bfe69a570d28/BestPractices_Rule_Monitor_REV_110607.pdf." target="_blank">http://download.microsoft.com/download/f/a/7/fa73e146-ab8a-4002-9311-bfe69a570d28/BestPractices_Rule_Monitor_REV_110607.pdf.</a></li>
	<li><span style="color: #000000;">How do multiple server resource pools actually work? See </span><a href="http://social.technet.microsoft.com/wiki/contents/articles/13920.how-do-multiple-servers-in-a-resource-pool-actually-work.aspx." target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/13920.how-do-multiple-servers-in-a-resource-pool-actually-work.aspx.</a></li>
	<li><span style="color: #000000;">Download OpsMgr component add-ons at </span><a href="http://www.microsoft.com/en-us/download/details.aspx?id=29270." target="_blank">http://www.microsoft.com/en-us/download/details.aspx?id=29270.</a></li>
	<li><span style="color: #000000;">Run As accounts for network monitoring are discussed at </span><a href="http://technet.microsoft.com/en-us/library/hh212920.aspx." target="_blank">http://technet.microsoft.com/en-us/library/hh212920.aspx.</a></li>
	<li><span style="color: #000000;">Read about using the Power Consumption monitoring template at </span><a href="http://technet.microsoft.com/en-us/library/ee808918.aspx." target="_blank">http://technet.microsoft.com/en-us/library/ee808918.aspx.</a></li>
	<li><span style="color: #000000;">Veeam provides an extended generic report library (GRL) for analyzing the health and performance of infrastructure objects. Learn more at </span><a href="http://www.veeam.com/extended-generic-report-library.html." target="_blank">http://www.veeam.com/extended-generic-report-library.html.</a></li>
	<li><a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94404/Default.aspx" target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/IndexID/94404/Default.aspx</a><span style="color: #000000;"> is an article about using PowerShell to create a Report Operator role.</span></li>
	<li><span style="color: #000000;">For information about configuring agent failover in PowerShell or a script to bulk-set this configuration for a group of servers, see </span><a href="http://www.teknoglot.se/code/powershell/opsmgr-2012-agent-failover-simple-script-with-wildcards-opsmgr-powershell/" target="_blank">http://www.teknoglot.se/code/powershell/opsmgr-2012-agent-failover-simple-script-with-wildcards-opsmgr-powershell/.</a></li>
	<li><span style="color: #000000;">You can update agent failover settings in bulk as described in the article on updating agent failover settings from a spreadsheet with PowerShell at </span><a href="http://www.systemcentercentral.com/tabid/143/indexid/95393/default.aspx." target="_blank">http://www.systemcentercentral.com/tabid/143/indexid/95393/default.aspx.</a></li>
	<li><span style="color: #000000;">Self-training guide is available at </span><a href="http://blogs.technet.com/b/musings_of_a_technical_tam/archive/2012/06/04/windows-powershell-self-training-guide.aspx." target="_blank">http://blogs.technet.com/b/musings_of_a_technical_tam/archive/2012/06/04/windows-powershell-self-training-guide.aspx.</a></li>
	<li><span style="color: #000000;">Cross platform security requirements are discussed at </span><a href="http://technet.microsoft.com/en-us/library/hh212926.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh212926.aspx</a><span style="color: #000000;"> and </span><a href="http://technet.microsoft.com/en-us/library/hh212886.aspx." target="_blank">http://technet.microsoft.com/en-us/library/hh212886.aspx.</a><span style="color: #000000;"> You will also want to read Scott Weisler’s discussion at </span><a href="http://www.systemcentercentral.com/BlogDetails/tabid/143/indexId/94460/Default.aspx," target="_blank">http://www.systemcentercentral.com/BlogDetails/tabid/143/indexId/94460/Default.aspx,</a><span style="color: #000000;"> also posted at </span><a href="http://opsmgrunleashed.wordpress.com/2012/07/07/cross-platform-discovery-settings/" target="_blank">http://opsmgrunleashed.wordpress.com/2012/07/07/cross-platform-discovery-settings/.</a><span style="color: #000000;">Virtual labs for System Center components are located at </span><a href="http://technet.microsoft.com/en-us/bb539977.aspx." target="_blank">http://technet.microsoft.com/en-us/bb539977.aspx.</a></li>
	<li><span style="color: #000000;">For information on managing resource pools for UNIX and Linux systems, see </span><a href="http://technet.microsoft.com/en-us/library/hh287152.aspx." target="_blank">http://technet.microsoft.com/en-us/library/hh287152.aspx.</a></li>
	<li><span style="color: #000000;">The monitoring pack and guides for UNIX and Linux systems can be downloaded from </span><a href="http://www.microsoft.com/en-us/download/details.aspx?id=29696." target="_blank">http://www.microsoft.com/en-us/download/details.aspx?id=29696.</a><span style="color: #000000;"> These are not available in the System Center catalog.</span></li>
</ul>
</div>
<div style="color: #000000;"></div>
<h3 style="color: #000000;">Appendix E: Available Online</h3>
<div style="color: #000000;">
<ul>
	<li>NONE</li>
</ul>
—————————————————————

Don’t forget to check out the following:

<span id="control_gen_2" class="commentary"><strong>CANITPro:</strong> Did you know there is a site dedicated to Canadian IT professionals? You can win a 3D movie prize package by upgrading your IT skills with Microsoft. Check out CANITPRO At The Movies, either in English: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600830" target="_blank">CANITPro At The Movies</a></span><span id="control_gen_3" class="commentary"> or French: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600850" target="_blank">CANITPro At The Movies</a></span>

<strong>Azure:</strong> Sign up for a FREE trial and get $200 to spend on <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597585" target="_blank">Microsoft Azure</a> cloud computing services. Full access, no strings.

<span id="control_gen_5" class="commentary"><strong>MSDN:</strong> Ever wanted to work with the latest Microsoft technologies, without having to spend thousands of dollars? Now you can, with the <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597617" target="_blank">MSDN subscription</a>. </span>

</div>
