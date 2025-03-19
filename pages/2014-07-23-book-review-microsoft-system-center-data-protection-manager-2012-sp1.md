---
layout: page
title: Book Review: Microsoft System Center Data Protection Manager 2012 SP1
date: 2014-07-23 21:03
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2014/07/Data-Protection-Manager-2012-SP1-Cover.png"><img class="alignleft size-full wp-image-10041" src="/wp-content/uploads/2014/07/Data-Protection-Manager-2012-SP1-Cover.png" alt="Data Protection Manager 2012 SP1 Cover" width="302" height="376" /></a>Recently, I finished reading the <a href="http://www.packtpub.com/microsoft-system-center-data-protection-manager-2012-with-service-pack-1/book" target="_blank">PACKT Microsoft System Center Data Protection Manager 2012 SP1</a>  eBook.

The chapters that I found most helpful were Chapter 6 “DPM-Aware Windows Workload Protection”, and Chapter 11 “Disaster Recovery”, hence the majority of my highlights are from these chapters.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<div>
<h3><b>Chapter 01: What Is Data Protection Manager? </b></h3>
<div>
<ul>
	<li>Don't make your GPT disk larger than 17 TB even if Microsoft supports it. This is a recommendation from the DPM development group.</li>
	<li>The Virtual Disk Service (VDK) supports up to 32 member spanned volumes, which means that you shouldn't se more than 32 disks in the DPM disk pool.</li>
	<li>DPM doesn't do deduplication for the DPM disk pool</li>
	<li>When you are protecting a production server or a Windows client, the communication is initialized in different ways:
<ul>
	<li>In a production server scenario, the DPM server initializes the communication</li>
	<li>In a Windows client scenario, the DPM agent initializes the communication</li>
</ul>
</li>
	<li>You can also perform an optimization on protection group level by using Enable on-the-wire compression. When you are using this function, the DPM agent will compress the data it backs up before sending it to the DPM server. This will not impact the performance of your production environment severely, but it will take some CPU and RAM.</li>
	<li>To enable the EUR feature you must perform an update of the schema in your Active Directory. Keep in mind that those changes are not reversible. If you need to undo the changes made you will need to restore the Active Directory.</li>
	<li>With the Self-Service Recovery Tool (SSRT), DBAs can perform the restore process without contacting any restore administrator. The DPM admin will need to specify the group or user within the Active Directory that will be able to perform a restore and will need to define where the restored databases should be placed. The DBAs will not be able to restore any databases to their original location; just alternative locations or network folders.</li>
	<li>To verify the VSS state, just open a command prompt and type <b>vssadmin list writers</b>. The output will be a list of all the VSS writers present in the operating system and their state. If the state is 1 (stable) or 5 (waiting for completion), everything is normal.</li>
	<li>The logfiles reside in the C:%ProgramFiles%Microsoft Data Protection ManagerDPMTemp catalog. The logfiles will log all the processes that are used within the communication between DPM server and DPM agents.</li>
	<li>The logfile that you can initially look into is the DPMRACurr logfile on both the DPM agent and DPM server side. This logfile logs all the processes for the remote agent and, if the DPMRA service has encountered an error, it will be stated in the logfiles as WARNING, Failed or Error.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 02: Backup Strategies</b></h3>
<div>
<ul>
	<li>The Recovery Point Objective (RPO) defines the maximum amount of data that could be lost if you restore from your most recent backup.</li>
	<li>The RTO defines how much downtime a company or organization could manage or tolerate. There isn't an average value for the RTO; in most cases it is defined in different ways for different Windows workloads such as Exchange, SharePoint, files, and so on. The main idea is to plan the company server environment so the RTO value can easily be met. For example, if you have a RTO of zero, you must apply a clustered server environment as a minimum requirements for those Windows workloads that represents the services.</li>
	<li>The RLO defines the level of SharePoint to restore in your SharePoint farm, farms, or file server data. Depending on the RPO and RTO for the SharePoint workload, the RLO may vary. You could have a RLO that states that company data must be restored at farm level for one kind of scenario and another RLO for individual items such as sites, lists or documents.</li>
	<li>All data that is in any way critical to your company should be backed up. The initial step starts with classifying your company data. The classification is the first building block that will become your restore plan or SLA. The more accurate the classification task, the more effective the restore scenarios will be in real-world situations.</li>
	<li>You do not want multiple backups running on the same server if the server can't deliver enough performance or resources. If your servers hosting the services that can't deliver enough resource, separate the Windows workloads by using different backup schedules.</li>
	<li>One thing that is very important is the name standard of your protection groups. It should reflect the company classification of the RTO, RPO, and RLO. If you have a protection group with an RTO of 4 hours, RPO of 1 hour, and a synchronization frequency of 15 minutes, the name for that protection group should be "RTO 4 hours / RPO 1 hour / Sync 15 min". This means that the members of that group must be up and running within 4 hours, a recovery point should be created every hour, and between those points, the block-level changes are synchronized every 15 minutes.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 03: DPM Server Management Tasks</b></h3>
<div>
<ul>
	<li>DPM must allocate two different spaces on the storage pool—the replicas and recovery points—for each data source, and must allocate space on the protected file servers or workstations for the change journal</li>
	<li>Microsoft has included a bunch of SQL views in the DPM database by default. They have included them so that the DPM administrators can create some custom reports. These Custom Report Views for DPM can be found at <a href="http://technet.microsoft.com/en-us/library/hh757766.aspx." target="_blank">http://technet.microsoft.com/en-us/library/hh757766.aspx.</a></li>
	<li>Bocada has developed Prism to improve DPM report capability. They partnered with Microsoft to create two default DPM-specific reports in addition to the DPM default reports.</li>
	<li>There are a lot of dependencies based on the hostname of the DPM server, therefore you cannot rename a DPM server or move it to another domain, because of the following reasons:
<ul>
	<li>DPM internally stores the machine name in its DPM database, which is referred to in code at various places.</li>
	<li>The DPM scheduled jobs are stored as XML strings, which contain references to the original DPM machine name. Thus, changing the actual machine name of DPM can lead to undefined behavior.</li>
</ul>
</li>
	<li>The network-bandwidth-usage throttling is configured on the agent level, so you should think about setting the throttling in the function where the maximum amount of data is to be transferred.</li>
	<li>Crunch for DPM is optimized to interoperate with the unique storage workloads produced by DPM 2010 and 2012, when protecting Hyper-V, Exchange, SQL, SharePoint, and shared/networked storage (NAS and CIFS) servers.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 04: Monitoring and Managing Performance of DPM</b></h3>
<div>
<ul>
	<li>Things to know about RBA are that this feature is enabled through the central console and works from SCOM only. For example, if an administrator logs directly onto the DPM server and uses the DPM  admin console they will be able to see everything in DPM. Another item to know about RBA is that it has task-based security. For example, a user could be locked out from being able to recover data but could still view the data.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 05: Workload Protection</b></h3>
<div>
<ul>
	<li>Many people tend to get the idea that BMR can be used in a V2P migration scenario, but, this is not supported</li>
	<li>The BRM feature only supports operating systems from 2008 onward. This means that you can't use BMR in a Microsoft-supported way to manage your Windows Server 2003 operating system</li>
	<li>The data in the Active Directory Recycle Bin is protected as a part of system state on domain controllers by DPM.</li>
	<li>A prerequisite consideration regarding generic data source protection is that the application is running on a Windows operating system and that it is a Microsoft application.</li>
	<li>there is a third-party solution that can be used with DPM to protect these non-Microsoft workloads. This third-party solution is called EVault for DPM (EDPM). EDPM can protect Linux, VMware, IBM i,  IBM AIX, HP-UX, Sun Solaris, Novell Netware, and Oracle databases.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 06: DPM-Aware Windows Workload Protection</b></h3>
<div>
<ul>
	<li>Note that the DPM 2012 SP1 can protect SQL 2012 AlwaysOn. For DPM 2012 deployments pre-release SP1, to protect SQL 2012 ensure that the SQL 2012 instance you are protecting does not have the  always On feature enabled, and also ensure that the SQL NT AUTHORITYSYSTEM account has SysAdmin rights on the SQL 2012 instance.</li>
	<li>Note that when you check the box next to the SQL instance, DPM adds (Auto) next to the SQL instance name. This means that the automatic SQL database protection is turned on. The next time a database is added to the instance it will be automatically protected</li>
	<li>When you go to add a database to a protection group, DPM runs a query to see if the database is a part of an Availability Group. When a failover happens DPM automatically detects this and continues  the protection of the database(s).</li>
	<li>It is common practice in SharePoint deployments to run the SQL instances on SQL Aliases. DPM is SQL Alias aware. So, if you are running your SQL Servers on SQL Aliases, then this is not a problem for DPM. It does, however, require an extra step in configuration</li>
	<li>Note that protecting search indexes will utilize large amounts of storage. Only protect this if it is absolutely necessary. Keep in mind that search indexes are data that can be rebuilt after recovering everything else</li>
	<li>DPM 2012 supports protecting RBS. When DPM 2012 protects an RBS-enabled content database, DPM will back up everything including BLOB data. When an RBS-enabled database is restored, the BLOB data will be restored as well. Even if you restore an RBS-enabled database to a non-RBS-enabled database, the BLOB objects will be restored into the content database.</li>
	<li>A common misunderstanding is that the explicit mailbox is restored from the DPM server to the Exchange server; this is not the case. DPM will restore the entire mailbox database to an Exchange recovery database (RDB) if you are using Exchange 2010</li>
	<li>After the restore operation has finished, you must use the Exchange Management Shell (EMS) for Exchange 2010 or the Exchange Troubleshooting Assistant (ExTRA) for Exchange 2007.</li>
	<li>Using the –include switch within the XML configuration to include all the other physical disks</li>
	<li>You still need to protect Exchange as an Exchange workload to be able to restore using the latest restore technique</li>
	<li>To protect Exchange 2013 with DPM SP1, in addition to copying the ese.dll and eseutil.exe files to the DPM bin folder, you also need to install the Visual C++ redistributable for Visual Studio 2012</li>
	<li>Update 1 (vcredist) on your Exchange server.</li>
	<li>The best combination for protecting a Hyper-V environment is to combine the hostlevel backup and the guest-level backup. The host-level backup is more to be seen as a BMR, while the guest-level backup will protect the SQL or Exchange workload running within the VM. A basic setup for a great Hyper-V protection is to create a recovery point every week for the VM and back up the workload present within the VM more frequently.  Regarding the DPM disk pool, the best way is to use a pass-through disk for the DPM disk pool, if you are running the DPM server as a VM on Hyper-V. Also note that using VHDs in a disk pool for DPM is not supported.</li>
	<li>When it comes to DPM protecting Hyper-V Replica, DPM can protect Hyper-V servers using the new function Hyper-V Replica by protecting the primary node. It's not supported to protect the actual replica.</li>
	<li>Now the DPM agent can be attached to multiple DPM servers and can simply be added to a protection group on any of the DPM servers the DPM agent is aware of. This feature only works with DPM 2012 SP1 and Hyper-V on Windows Server 2012.</li>
	<li>Your DPM 2012 needs to be a fresh install. The scale-out protection for Hyper-V on DPM servers that were upgraded to DPM 2012 is not supported.</li>
	<li>DPM supports protection for Windows Server 2012 volumes that have deduplication enabled. In order to protect deduplicated volumes, you must turn on the deduplication role on DPM server by running the following PowerShell command:
PS:/&gt;importsystemmodules
PS:/&gt;add-windowsfeature FS-Data-Deduplication
Once you have enabled the deduplication role on the DPM server, you are ready to protect any deduplicated volumes. It is really important to note that DPM doesn't perform any deduplication on its own storage pool.</li>
	<li>By default, Windows automatically creates a backup of the DHCP database every 60 minutes. Windows places the database in this location: %SystemRoot%System32dhcpbackup. The DHCP database is named dhcp.mdb and this is basically what you want DPM to back up. Protecting the dhcp.mdb file will contain everything you need to restore DHCP.</li>
	<li>Another file you could consider backing up with DPM, but which is not required, is the J50.log . This is a transaction logfile also located at %SystemRoot%System32DHCP, which is used to recover incomplete transactions in case of a server malfunction. You may want to also protect the system state of your servers in your DHCP cluster, but again this is not required.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 07: DPM Non-Aware Windows Workload Protection</b></h3>
<div>
<ul>
	<li>Protecting DFS with DPM is fairly straightforward. It is recommended to protect the actual file shares directly on each of the servers in the DFS root.</li>
	<li>When you have a standalone DFS deployment you should protect the system state on the servers in the DFS root, and when you have a domain-based DFS deployment we recommend you protect your Active Directory of the domain controller that hosts the DFS root. If you are using DFS replication it is also recommended to protect the shadow copy components on servers that host the replication data, in addition to the previously mentioned items.</li>
	<li>A good thing to know is that if you protect the system state of a server, then IIS configuration will be included in this backup. This does not include the website or web application files, so you will still need to protect these in addition to a system state backup.</li>
	<li>Note the files named Meeting.Active should not be backed up. These files are in use and locked while a meeting takes place.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 08: Managing Tapes in DPM</b></h3>
<div>
<ul>
	<li>Best practice is to define your most frequently occurring recovery goal first, for example week and then go on with the month for the second recovery goal and so on. You can also let the DPM server create two copies if recovery goals clash, which is good for archiving purposes.</li>
	<li>Microsoft has created a sophisticated hardware compliant list (HCL) that covers all the supported standalone tape drives and media libraries that Microsoft themselves has verified as fully functional with DPM. You can read the HCL at the following URL: <a href="http://technet.microsoft.com/en-us/library/hh916523." target="_blank">http://technet.microsoft.com/en-us/library/hh916523.</a> In those cases where the hardware is not listed on the HCL URL, you can use the tape testing tool. More information could be found at the following URL: <a href="http://technet.microsoft.com/en-us/library/jj733580.aspx" target="_blank">http://technet.microsoft.com/en-us/library/jj733580.aspx</a></li>
	<li>There is one supported VTL solution for Microsoft, the Firestreamer software from Cristalink.</li>
	<li>You should always be careful while upgrading the DPM servers that operates in a TLS solution, since this could be considered a cluster. When upgrading the DPM servers with major upgrades like service packs and so on, you must disable the TLS feature and re-enable it after the upgrade is complete.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 09: Client Protection in DPM</b></h3>
<div>
<ul>
	<li>Administrators can put a maximum of GB/TB per user and block certain folders from being protected.</li>
	<li>DPM handles connection drops like this. If a connection goes down while DPM is synchronizing, then it will continue synchronization from the point where it dropped off. If the connection is dropped during a consistency check then DPM will retry the consistency check five minutes after the connection has dropped. If the connection is back within five minutes then it will continue the consistency check with no issues, otherwise DPM will mark the replica as inconsistent and alert will be created in DPM. The consistency will have to be manually kicked off again at this point once the connection is restored.</li>
	<li>Note that bandwidth throttling will not work over a DirectAccess connection due to a limitation in DirectAccess.</li>
	<li>For more information about Riverbed's DPM <a href="http://www.riverbed.com/assets/media/documents/briefs/PerformanceBrief-Riverbed-MS-DPM.pdf." target="_blank">http://www.riverbed.com/assets/media/documents/briefs/PerformanceBrief-Riverbed-MS-DPM.pdf.</a></li>
	<li>Note that theDPMADSchemaExtension tool makes the following changes to your Active Directory schema to support the following tasks for end-user recovery:
<ul>
	<li>Extends the schema</li>
	<li>Creates a container (MS-ShareMapConfiguration)</li>
	<li>Grants the DPM server permissions to change the contents of the container</li>
	<li>Adds mappings between source shares and shares on the replicas</li>
</ul>
</li>
	<li>To learn more about deploying software through SCCM refer to Chapter 3, DPM Server Management Tasks, or visit <a href="http://technet.microsoft.com/en-us/library/gg699393.aspx." target="_blank">http://technet.microsoft.com/en-us/library/gg699393.aspx.</a></li>
	<li>DPM 2007, DPM 2010, and DPM 2012 are not able to protect client's system state or image-level backups.</li>
	<li>There is a well-known problem with DPM client protection. Non-administrator users on client computers cannot recover data on their own. In DPM 2012 this is still an issue. This link describes the process to fix this issue on the client computer: <a href="http://blogs.technet.com/b/dpm/archive/2011/05/10/how-to-configurethe-dpm-client-to-allow-non-admin-users-to-perform-end-user-recoveryof-dpm-protected-data.aspx" target="_blank">http://blogs.technet.com/b/dpm/archive/2011/05/10/how-to-configurethe-dpm-client-to-allow-non-admin-users-to-perform-end-user-recoveryof-dpm-protected-data.aspx</a></li>
</ul>
</div>
<div></div>
<h3><b>Chapter 10: Workgroups and Untrusted Domains</b></h3>
<div>
<ul>
	<li>A guide on setting up a Certificate Authority on Windows Server 2008 R2 can be found at <a href="http://www.buchatech.com/2010/07/setup-configure-acertificate-authority-on-windows-server-2008/" target="_blank">http://www.buchatech.com/2010/07/setup-configure-acertificate-authority-on-windows-server-2008/.</a></li>
	<li>Install the certificate on the DPM server. This should be imported into the local computer's Personal store on the DPM server.</li>
	<li>The user account you use when configuring the protected agent has to be unique. This means that the user account with the same name cannot be used on another protected server. DPM does not like this and you will run into errors.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 11: Disaster Recovery</b></h3>
<div>
<ul>
	<li>DPM requires Active Directory to recover data. If the Active Directory is lost, the first step is to recover it from a tape</li>
	<li>If the DPM server is lost and no chaining is used, the agents need to be reconfigured to recover data.</li>
	<li>DPM uses a Microsoft SQL database to keep a track of the backups and where they are stored on disk and tape. This means that we always need to have a valid backup of the SQL database to ensure fast recovery.</li>
	<li>Bare Metal Recovery is only supported from Windows Server 2008 to Windows Server 2012. There is no support for Windows 2003.</li>
	<li>As additional protection, schedule a backup with the dpmbackup.exe tool that is provided by Microsoft. It backs up the DPM database, and creates shadow copies that can be used for backing up replicas. If you want to create a backup of the local DPM database, use the following command: Dpmbackup.exe –db. The previous command creates a backup of the DPM database and places the backup file at %DPMInstallLocation%VolumesShadowCopyDatabase Backupsdpmdb.bak. This file will be overwritten every time the job runs. If there is no chained DPM servers or backup to tape, it's recommended to schedule the DPM database, back up daily with Windows Task Scheduler, and after completion, copy the database to another server.</li>
	<li>The backup job generates a regular SQL backup file that can be restored from the SQL management tools. The Dpmsync.exe tool can also be used to restore the database, as follows: Dpmsync.exe -restoredb -dbloc C:dpmdb.bak -instancename dpm01 msdpm2012eval. This will restore the database from the backup file into the local DPM database. After restoring the database, no matter what method is used, DPM needs to synchronize the database with the replicas. Dpmsync.exe –Sync. The Dpmsync.exe tool will synchronize the agents and disk replication against the state of the database from the restored database.</li>
	<li>Protection groups are limited to 64 recovery points for file-based workloads, so if we want to make a recovery point multiple times a day, we limit how long we can keep data in the short-term-based storage pools</li>
	<li>It's also important to exclude the dpmra.exe/csc.exe process from the antivirus and exclude the %DPMInstallationFolder%DPMXSD and TEMPMTA directories on the DPM server.</li>
	<li>Adding a second network dedicated to backup will ensure that there is always full bandwidth available for users and applications, and if there is a need for larger recoveries, they won't slow down the network.</li>
	<li>To let DPM utilize the backup network, we need to define the network through the PowerShell prompt, using the following command: Add-BackupNetworkAddress -DpmServername DPM01 -Address 192.168.1.0/24 -SequenceNumber 1</li>
	<li>This is also a process that the backup admin should undertake at least on a yearly basis, to verify that the steps are well documented and valid.</li>
</ul>
</div>
<div></div>
<h3><b>Chapter 12: DPM PowerShell, Automation, and Private Cloud</b></h3>
<div>
<ul>
	<li>The best method for automating DPM is to utilize System Center Orchestrator (SCORCH).</li>
	<li>By default the WinRM service is running but the WinRM listener is not configured. Before we can configure the connection to DPM in SCORCH, we need to configure the WinRM listener.</li>
	<li>You can learn more about each of the System Center 2012 Data Protection Manager Activities at <a href="http://technet.microsoft.com/en-us/library/hh420346.aspx." target="_blank">http://technet.microsoft.com/en-us/library/hh420346.aspx.</a></li>
</ul>
—————————————————————

Don’t forget to check out the following:

<span id="control_gen_2" class="commentary"><strong>CANITPro:</strong> Did you know there is a site dedicated to Canadian IT professionals? You can win a 3D movie prize package by upgrading your IT skills with Microsoft. Check out CANITPRO At The Movies, either in English: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600830" target="_blank">CANITPro At The Movies</a></span><span id="control_gen_3" class="commentary"> or French: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600850" target="_blank">CANITPro At The Movies</a></span>

<strong>Azure:</strong> Sign up for a FREE trial and get $200 to spend on <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597585" target="_blank">Microsoft Azure</a> cloud computing services. Full access, no strings.

<span id="control_gen_5" class="commentary"><strong>MSDN:</strong> Ever wanted to work with the latest Microsoft technologies, without having to spend thousands of dollars? Now you can, with the <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597617" target="_blank">MSDN subscription</a>. </span>

</div>
</div>
