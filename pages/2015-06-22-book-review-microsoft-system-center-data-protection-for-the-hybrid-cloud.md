---
layout: page
title: Book Review: Microsoft System Center - Data Protection For The Hybrid Cloud
date: 2015-06-22 10:43
author: AdinErmie
comments: true
categories: []
---
<p style="text-align: justify;"><a href="/wp-content/uploads/2015/06/System-Center-Data-Protection-For-The-Hybrid-Cloud-Cover.png"><img class=" size-full wp-image-13741 alignleft" src="/wp-content/uploads/2015/06/System-Center-Data-Protection-For-The-Hybrid-Cloud-Cover.png" alt="System Center Data Protection For The Hybrid Cloud Cover" width="163" height="189" /></a>Recently, I finished reading the <a href="http://blogs.technet.com/b/dpm/archive/2015/06/16/free-ebook-microsoft-system-center-data-protection-for-the-hybrid-cloud.aspx" target="_blank">Microsoft System Center - Data Protection For The Hybrid Cloud</a> eBook.</p>
<p style="text-align: justify;">The chapter(s) that I found most helpful were Chapter 3 “Protection Microsoft Workloads”, and Chapter 5 "Protection Hyper-V Virtual Machines" hence the majority of my highlights are from this chapters. But really, the entire book is full of useful information.</p>
<p style="text-align: justify;">It is also very interesting that Chapter 6 is about protecting VMware Private Clouds, but there is no information yet for it; therefore, when the book is re-released, look for an update on this page.</p>
<p style="text-align: justify;">I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).</p>
&nbsp;
<h3>Chapter 01: Data Protection Trends And Challenges</h3>
<div>
<ul>
 	<li>Digitally created data is expected to double roughly every two years and reach an astounding 40,000 exabytes by 2020.</li>
 	<li>In the data protection domain, the contribution to data growth comes from the need for traditional forms of protection. The 3-2-1 rule summarizes this perfectly—3 copies of data on at least 2 different forms of storage with at least 1 copy that is offsite.</li>
 	<li>For more information on the 3-2-1 rule, see <a href="http://www.40tech.com/2012/06/12/follow-the-3-2-1-backup-rule-to-safeguard-your-files" target="_blank">http://www.40tech.com/2012/06/12/follow-the-3-2-1-backup-rule-to-safeguard-your-files</a>/.</li>
</ul>
&nbsp;
<h3>Chapter 02: Overview of Hybrid Cloud Backup</h3>
<div>
<ul>
 	<li>For more information on data transfer pricing, see <a href="http://azure.microsoft.com/en-us/pricing/details/data-transfers/" target="_blank">http://azure.microsoft.com/en-us/pricing/details/data-transfers/</a>.</li>
 	<li>The DPM roadmap also includes support for host-level VMware VM backup, to have parity with the backup that is supported for Hyper-V VMs. Future workloads that will be supported are Oracle and IBM DB2, both running on Linux.</li>
 	<li>Security All Azure backups are encrypted at source, during transmission, and stored encrypted in Azure. The encryption key is stored at source and is the only way to restore any of the data stored in Azure, so the customer is in full control of access to the data in the service.</li>
 	<li>Future enhancements include a central management that enables customers to centrally manage all the backup infrastructure</li>
 	<li>Efficiency After the initial copy is seeded in Azure, incremental backups are taken as per the backup policy, compressed, encrypted, and sent to Azure where they are stored as incrementals. This optimizes network utilization during transfer as well as storage consumption in Azure, both of which are key factors to keep in mind when sending data to Azure.</li>
 	<li>A key value offered with Azure Backup is that restore operations do not incur egress charges. This information is updated frequently, so please visit the product page (http://azure.microsoft.com/en-us/pricing/details/backup) for updated pricing information.</li>
 	<li>For more information on how to determine if cloud backup is right for your servers, see <a href="http://www.gartner.com/reprints/microsoft?id=1-2CV21H1&amp;ct=150402&amp;st=sb" target="_blank">http://www.gartner.com/reprints/microsoft?id=1-2CV21H1&amp;ct=150402&amp;st=sb</a>.</li>
 	<li>Support for file-consistent backup of Linux guests running on Hyper-V without needing to take them offline</li>
 	<li>Inline de-duplication is done as part of the backup process where every backup set is de-duplicated as it is stored in the backup storage</li>
 	<li>Offline de-duplication is done as a post-processing step after the backup has completed.</li>
 	<li>De-duplication is an I/O- and performance-intensive operation, so the number of backups running and the size of the backup storage pool determines which approach works better</li>
 	<li>The approach used in DPM is offline de-duplication that provides excellent throughput and storage savings up to 70 percent in large-scale private cloud deployments.</li>
 	<li>A central console that leverages System Center Operations Manager to manage and monitor multiple DPM servers. This is the recommended best practice to monitor backups in an enterprise environment</li>
</ul>
&nbsp;
<h3>Chapter 03: Protecting Microsoft Workloads</h3>
<div>
<ul>
 	<li>To take advantage of built-in Windows Server de-duplication capability, it is recommended that you deploy the DPM server in a virtualized environment.</li>
 	<li>If the servers to be protected are in a different domain or behind a firewall, the agent must be installed separately on each server and attached to the DPM server.</li>
 	<li>For agent installation in different domains, follow the steps outlined in the TechNet documentation at <a href="https://technet.microsoft.com/en-us/library/bb870934.aspx" target="_blank">https://technet.microsoft.com/en-us/library/bb870934.aspx</a>.</li>
 	<li>You can select multiple types of data sources in a single protection group, but it is recommended that you segregate data sources based on their type and protection goals since a protection group is a means to logically group data sources that have the same protection intent.</li>
 	<li>Select Co-Locate Data Source On The Same Disk if the type of data is a Hyper-V VM or client computer or SQL Server databases to gain storage efficiencies.</li>
 	<li>When you select data sources, it is critical that you select the right set of members for enabling protection. For instance, when selecting clustered resources, do not pick data sources from individual nodes; instead, point to the cluster to select data sources. Similarly, when you select a SharePoint data source, it is critical to point the selection to the web front end server as opposed to the back end SQL Server instance machine.</li>
 	<li>DPM leverages Volume Shadow Copy Services (VSS) and filter bitmaps to make the backup process efficient. DPM leverages file filter technology to maintain a bitmap of changes between two synchronization events</li>
 	<li>With System Center Virtual Machine Manager (VMM) integration, DPM is able to continue protection of a VM during live migration without requiring user intervention as long as the DPM agent is installed on all the target Hyper-V hosts</li>
 	<li>Hyper-V protection includes protection of Windows as well as Linux VMs in both standalone and clustered environments</li>
 	<li>1. Install the VMM console on the DPM server and associate the VMM server with the DPM server from DPM PowerShell running in Administrator mode:
Click here to view code image
Set-DPMGlobalProperty –DPMServerName &lt;&gt; -KnownVMMServers &lt;&gt;
2. Start the DPM-VMM Helper Service from the control panel.</li>
 	<li>The block size is maintained as 16 KB to optimize the amount of data that is transferred and stored on the replica</li>
 	<li>For a VM, the restore can be to the same host, to the same cluster, or to a different cluster.</li>
 	<li>To ensure consistent backups are captured for Linux VMs, it is critical to install Linux Integration Services</li>
 	<li>While the laptop or the desktop computer is disconnected from the network, the data changes to the files and folders are tracked and stored on the local hard drive of the client computer. When the client machine is connected to the corporate network, only delta changes since the most recent backup are synchronized to DPM, thereby ensuring efficient storage of incremental data changes on the DPM replica storage.</li>
 	<li>For detailed steps to configuring an Exchange database from DPM backup, see the TechNet article at <a href="https://technet.microsoft.com/en-us/library/jj628013.aspx" target="_blank">https://technet.microsoft.com/en-us/library/jj628013.aspx</a>.</li>
 	<li>DPM doesn’t support SQL Server backup when it has database files stored on a remote SMB file share or Windows scale-out file server. DPM also doesn’t support databases whose data is stored on Windows Azure blob storage.</li>
 	<li>In SQL Server AlwaysOn deployments, DPM honors Preferred Replica, Replica Only, Any Replica, and Primary preferences set by the SQL Server administrator (see Figure 3-3). However, for Preferred Replica, DPM always backs up only from the replica node. When Availability Group is selected for protection, all databases that are added to the availability group are automatically backed up.</li>
 	<li>For a description of how to configure protection of SQL Server AlwaysOn configuration, see <a href="https://technet.microsoft.com/en-us/library/hh780998.aspx" target="_blank">https://technet.microsoft.com/en-us/library/hh780998.aspx</a>.</li>
 	<li>When you use DPM, it is critical that no other process backing or truncating transaction logs is enabled because it would interfere with DPM. After the transaction logs are backed up, they are truncated, and this could lead to a break in the transaction log chain.</li>
 	<li>In addition, to express full backup, DPM ships a transaction log to the DPM replica storage, thereby minimizing data loss up to 15 minutes. While express full backup is efficient in terms of data transfer and storage on the replica, it is expensive on the disk IOPS since storage snapshots are maintained on the production server while the backup data is being copied. Transaction log backup, alternatively, is lightweight and enables up to a 15-minute recovery point objective (RPO).</li>
 	<li>The main goal of protecting a SharePoint farm is to protect the content that is stored in the SQL Server content database, as well as the configuration of the SharePoint farm so that the SharePoint farm can be recovered in the event of a disaster, data loss, or corruption.</li>
 	<li>If SharePoint configuration files need to be backed up, it is advised to back up the SharePoint server with System State backup.</li>
 	<li>Restoring an entire site to the original site is not recommended without restoring the entire farm since it could lead to inconsistencies. The recommended practice is to recover to an alternate site or an alternate server for configuration or content database recovery.</li>
 	<li>If the entire site needs to be recovered from scratch, it is recommended that you recover the SharePoint server from bare metal and then recover the configuration and content databases using DPM.</li>
</ul>
&nbsp;
<h3>Chapter 04: Protecting Azure IaaS Workloads</h3>
<div>
<ul>
 	<li>By running DPM in an Azure infrastructure-as-a-service (IaaS) virtual machine (VM), you get the ability to back up workloads running in other Azure IaaS VMs</li>
 	<li>Ensure that you pick the Standard tier. The size of the VM should be at least A2 (2 cores, 3.5 GB of memory).</li>
 	<li>If you have multiple subscriptions, pick the subscription that also contains the VMs and workloads that need to be protected. The DPM VM should be placed in this subscription.</li>
 	<li>The DPM VM should have an independent storage account</li>
 	<li>The default replication setting for the automatically-created storage account is Geo-redundant. This setting is also recommended for your backup data because it acts as insurance against Azure disasters</li>
 	<li>The DPM VM should have proximity to the workloads that need to be protected. At the very least, the DPM VM should be placed in the same region as the VMs whose workloads need to be protected</li>
 	<li>If you have created a virtual network for your VMs and workloads, the DPM VM must be placed in the same virtual network. Between selecting a region and a virtual network, a virtual network gets preference.</li>
 	<li>When DPM is running as a VM in Azure, the only type of storage that can be used is a VHD. The VHDs that are created and attached to the VM together form the backup storage pool for DPM consumption.</li>
 	<li>Any given data source can be a part of only one Protection Group, but a Protection Group can manage multiple data sources.</li>
 	<li>The list of workloads supported by Azure is a continuously evolving one. You can find the latest and up-to-date information at <a href="http://support.microsoft.com/kb/2721672" target="_blank">http://support.microsoft.com/kb/2721672</a>. Additionally, the detailed list of workloads, versions, and capabilities supported by DPM can be found in the TechNet documentation at <a href="http://technet.microsoft.com/en-us/library/jj860400.aspx" target="_blank">http://technet.microsoft.com/en-us/library/jj860400.aspx</a>.</li>
 	<li>Here is a list of recommendations based on performance tests run with DPM in various configurations:
<ul>
 	<li>1. Use the Standard tier when creating a VM in which DPM will be installed. The IOPS per attached disk is higher for the Standard tier (500 IOPS) than for the Basic tier (300 IOPS).</li>
 	<li>2. Do not use the same storage account for the DPM disks and the disks attached to the production VMs. Azure places a limit of 20,000 IOPS per storage account. If the data to be backed up is read and written to the same storage account, you have effectively halved the IOPS available from the storage account to the workloads or DPM.</li>
 	<li>3. The minimum VM size should be A2 with 3.5 GB of RAM. DPM needs at least 2 GB of RAM to work correctly, and A2 is the smallest VM size where the RAM is greater than 2 GB.</li>
 	<li>4. Since DPM and the workloads are in the same region, there is no network egress cost incurred during backup or restore.</li>
</ul>
</li>
 	<li>Table 4-1 lists the operating limits that are suggested for DPM VMs of different sizes. The maximum number of protected servers that a given size can support is derived from scale tests that have been run, while the maximum raw backup storage is a limit imposed by Azure and can be explored in greater detail at <a href="http://msdn.microsoft.com/en-us/library/azure/dn197896.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn197896.aspx</a>.
TABLE 4-1 Limits on raw backup storage and number of protected servers for each VM</li>
 	<li>There is no easy way to increase the size of an existing virtual disk in Azure. In order to utilize the full storage capacity of a VM, ensure that each disk is created with size of 1,023 GB—the maximum possible. Azure charges you for the data consumed on the virtual disk rather than on the created size of the virtual disk.</li>
 	<li>The recommendation is to use Azure Backup as the bottomless storage pit for anything more than a few days. Thus, the data retained with DPM is always the freshest and can be used quickly for any immediate recovery scenarios. This also postpones the decision to scale up or scale out with respect to hitting the maximum raw backup storage limit.</li>
</ul>
&nbsp;
<h3>Chapter 05: Protecting Hyper-V Virtual Machines</h3>
<div>
<ul>
 	<li>Before installing DPM 2012 R2 and performing a series of required configuration tasks, you should devise a strategy for what to back up, when to back up, and where to back up</li>
 	<li>What to back up (host level vs. guest level)
It is recommended that you protect your Hyper-V environment by combining host-level backup of Hyper-V VMs with the existing backup strategy for your in-guest applications, like Microsoft SQL Server, Microsoft Exchange, and Microsoft SharePoint.</li>
 	<li>Host-level backup of VMs is equivalent to protecting a physical server using bare-metal recovery. It is recommended that you protect your application data more frequently than your VMs. For example, VMs can have a schedule that backs up data once per day or once per week, while Microsoft SQL Server databases could be backed up as frequently as every 15 minutes.</li>
 	<li>With UR3, you can now create specific time windows within which to run the scheduled backup jobs and consistency check (CC) jobs to achieve the SLAs</li>
 	<li>These time windows are configured through Windows PowerShell at the level of a protection group to strictly ensure that all backup and CC jobs run only during the set window. Jobs that are actively transferring backup data after the window has ended are allowed to continue, but all other jobs are automatically cancelled. The backup/CC windows do not affect ad hoc jobs triggered by the user.</li>
 	<li>It is recommended that you use Azure Backup as the bottomless storage for host-level VM backups for longer retention. You can still have a few days’ worth of backup on-premises to ascertain faster operational recovery jobs.</li>
 	<li>A DPM server can protect up to 800 VMs with co-location turned on and up to 300 VMs with co-location turned off.</li>
 	<li>In general, you have one replica volume and one recovery point volume per protected data source.</li>
 	<li>Co-location enables you to have multiple data sources mapping on a single replica and recovery point volume. It allows you to locate data from different protection groups on the same disk or tape storage.</li>
 	<li>For an explanation of how to leverage the DPM scale-out feature to protect VMs deployed on a big cluster, see the TechNet blog entry at <a href="http://blogs.technet.com/b/dpm/archive/2013/05/01/sc-2012-sp1-dpm-leveraging-dpm-scaleout-feature-to-protect-vms-deployed-on-a-big-cluster.aspx" target="_blank">http://blogs.technet.com/b/dpm/archive/2013/05/01/sc-2012-sp1-dpm-leveraging-dpm-scaleout-feature-to-protect-vms-deployed-on-a-big-cluster.aspx</a>.</li>
 	<li>Double-parity (and not three-way mirrored) is recommended for backup storage, leveraging Windows Server de-duplication to reduce the amount of backup storage consumed</li>
 	<li>A white paper describing all the pre-requisites as well as guidance on how to ensure you get the most de-duplication savings from your setup is available at <a href="http://technet.microsoft.com/en-us/library/dn891438.aspx" target="_blank">http://technet.microsoft.com/en-us/library/dn891438.aspx</a>.</li>
 	<li>Note that you get app-consistent backups for the VMs running Microsoft workloads while you get file-consistent snapshots for the VMs running Linux workloads due to no Volume Shadow Copy Service (VSS) support in the guest</li>
 	<li>In order to get scalable backups with DPM, you cannot use non-Microsoft file servers that implement the SMB 3.0 protocol (because the DPM agent doesn’t work with these file servers).</li>
 	<li>For a description of a few different Hyper-V over SMB configurations with increasing levels of availability, see the blog post at <a href="http://blogs.technet.com/b/josebda/archive/2013/01/26/hyper-v-over-smb-sample-configurations.aspx" target="_blank">http://blogs.technet.com/b/josebda/archive/2013/01/26/hyper-v-over-smb-sample-configurations.aspx</a>.</li>
 	<li>Learn more about Hyper-V backup at private cloud scale at <a href="http://blogs.technet.com/b/dpm/archive/2014/08/12/hyper-v-backup-at-private-cloud-scale.aspx" target="_blank">http://blogs.technet.com/b/dpm/archive/2014/08/12/hyper-v-backup-at-private-cloud-scale.aspx</a>.</li>
 	<li>Learn more about how to get uninterrupted data protection during live migration of VMs at <a href="http://blogs.technet.com/b/dpm/archive/2013/04/24/sc-2012-sp1-dpm-windows-2012-vm-mobility-uninterrupted-data-protection.aspx" target="_blank">http://blogs.technet.com/b/dpm/archive/2013/04/24/sc-2012-sp1-dpm-windows-2012-vm-mobility-uninterrupted-data-protection.aspx</a>.</li>
 	<li>Learn more about the motivations, scenarios, and the product guidance at <a href="http://blogs.technet.com/b/virtualization/archive/2014/04/24/backup-of-a-replica-vm.aspx" target="_blank">http://blogs.technet.com/b/virtualization/archive/2014/04/24/backup-of-a-replica-vm.aspx</a>.</li>
 	<li>DPM supports protecting Hyper-V VMs on the servers that use local user account (NTLM authentication) or that use certificates. For Hyper-V clusters, only certificate authentication is supported, not the NTLM certification. Even protection of a primary DPM server to a secondary DPM (in an untrusted domain) is supported through certificate authentication.</li>
 	<li>Learn how to protect computers in untrusted domains and how to set up protection with certificate authentication at <a href="http://technet.microsoft.com/en-in/library/hh757801.aspx" target="_blank">http://technet.microsoft.com/en-in/library/hh757801.aspx</a>.</li>
 	<li>DPM server itself provides the additional capability of performing item-level recovery (ILR), which allows you to recover individual files, folders, volumes, and VHDs from a host-level backup. An advantage of using ILR is that the protection agent does not need to be installed on the guest operating system of the VMs on the host.</li>
 	<li>Item-level recovery does not support recovery of an item to its original location.</li>
 	<li>Note
You can recover multiple files from a single VHD but not from across multiple VHDs at the same time.</li>
 	<li>A description of various options for item recovery is available at <a href="https://technet.microsoft.com/en-us/library/hh757981.aspx" target="_blank">https://technet.microsoft.com/en-us/library/hh757981.aspx</a>.</li>
 	<li>In a private cloud deployment, it is recommended that you deploy all VMs with a golden image (a single parent VHD). Leveraging the same parent VHD and creating differencing disks for the VMs saves disk space. It is recommended that you keep the parent VHD on a high performant storage (for example, SSD) because most read operations will come from this VHD. DPM supports restoring the VM to the original location with or without a parent disk, but there are more steps involved with the latter option.</li>
 	<li>The following list of recommendations is based on the changes that were introduced in DPM 2012 R2 UR3 to support Hyper-V backup at scale and on the results of various tests that were specifically conducted to develop this guidance:
<ul>
 	<li>Use the default provider shipped with DPM 2012 R2 UR3 and later since the host-level volume snapshot on the production servers (Windows Server 2012 R2) was eliminated. There is no additional benefit if hardware providers are used.</li>
 	<li>Deploy DPM on VMs running on Windows Server 2012 R2 Hyper-V servers.</li>
 	<li>Provision backup storage through VHDs residing on SOFS shares and run DPM virtual to get the storage savings. DPM VHD/VHDX files should be 1 TB.</li>
 	<li>Use multiple DPM servers, each protecting 250 to 300 VMs and leverage System Center Operations Manager for alerting, monitoring, and reporting. If you are especially concerned about reducing the DPM footprint, leverage the co-location feature and protect around 800 VMs, but note that there is a trade-off in terms of space savings.</li>
 	<li>Use the Backup And Consistency Check window to control the backup.</li>
 	<li>Do not overlap the backup/CC and de-duplication window since both are resource-intensive operations.</li>
</ul>
</li>
</ul>
&nbsp;
<h3>Chapter 06: VMware Private Cloud Protection</h3>
<em>This information is not yet publicly available. It wil be included when this ebook is re-issued in summer 2015</em>

<strong>Update</strong>: As of August 30, 2016 Microsoft has released the supplement to this book. which includes this new chapter. The ebook itself has not been updated as of yet, but you can find the supplement material here: <a href="https://blogs.msdn.microsoft.com/microsoft_press/2016/08/30/free-ebook-supplement-microsoft-system-center-data-protection-manager-vmware-private-cloud-protection/" target="_blank">https://blogs.msdn.microsoft.com/microsoft_press/2016/08/30/free-ebook-supplement-microsoft-system-center-data-protection-manager-vmware-private-cloud-protection/</a>

Here are my "highlights" based on the supplement information released:
<ul>
 	<li>DPM uses native vStorage APIs for Data Protection (VADP) provided by VMware and specifically designed to take host-level VM backups</li>
 	<li>In VMware backup terminology, this is referred to as agentless backup since the backup operations run from the VMware host server without the need for any agents deployed either on the host or in the VM.</li>
 	<li>With VMware, however, all the VMs in the vCenter environment are discoverable, which makes VM protection simple since there is no need to browse through each host to discover and protect the VMs.</li>
 	<li>If the entire folder is selected for protection, any new VMs that are added to the folder are automatically protected by DPM. This feature is available only with VMware VM backup; Hyper-V does not provide folder-level abstraction.</li>
 	<li>If DPM is deployed on Hyper-V 2012 R2, it can leverage Windows deduplication to optimize backup storage. <i>For more information on de-duplicating DPM storage, see </i><a href="http://technet.microsoft.com/en-us/library/dn891438.aspx" target="_blank"><i>http://technet.microsoft.com/en-us/library/dn891438.aspx</i></a>.</li>
 	<li>A credential cannot be deleted if it is currently being used by any VMware server’s authentication setting for backup. Before attempting to delete a credential, all VMware servers using that credential need to be updated to use a different credential.</li>
 	<li>The DPM server supports vMotion where it continues to protect VMs even if they migrate to other hosts within a data center without any needing any manual intervention.</li>
 	<li>During the discovery step within the DPM protection workflow, either the entire folder or some of the virtual machines in the folder can be selected for protection. Additionally, if the entire folder is selected for protection, any new virtual machines that are added to the folder are automatically protected by DPM using the backup policy associated with that folder.</li>
 	<li>DPM servers have built-in checks to avoid duplicate protection of a virtual machine or folder by multiple DPM servers.</li>
 	<li>If the backed up VMware virtual machine is running a Windows guest operating system, user can select and explore each VMDK file and select required files or folders to be recovered. In this case, DPM server will only restore the selected files or folders instead of recovering the entire virtual machine.</li>
 	<li>All VMware VM protection reports can be generated by leveraging DPM Central Reporting feature.</li>
</ul>
</div>
</div>
</div>
&nbsp;
<div>
<div>
<div>
<div>
<h3>Chapter 07: Protecting the Microsoft Cloud Platform System</h3>
<div>
<ul>
 	<li>Make sure that you maintain the following backup frequency:
VMs Once per week backup with a two-week retention period.
Databases Once every four hours backup with a five-day retention period.</li>
 	<li>The DPM Central Console is integrated with Operations Manager (and does not show up as a separate interface). It enables you (through the System Center 2012 R2 Data Protection Manager node) to monitor all management cluster and tenant DPM servers and to take actions in response to alerts.</li>
 	<li>For more information about managing multiple DPM servers with Central Console, see <a href="http://technet.microsoft.com/library/jj860391.aspx" target="_blank">http://technet.microsoft.com/library/jj860391.aspx</a>.</li>
</ul>
&nbsp;
<h3>Chapter 08: Optimizing Backup Storage</h3>
<div>
<ul>
 	<li>A simplistic formula encapsulates this notion: backup storage requirement = InitialSize + (InitialSize × DailyChurn% × RetentionPeriodInDays)</li>
 	<li>Deduplication covers the whole backup data to find common chunks, while compression takes each chunk and attempts to reduce the data.</li>
 	<li>In source deduplication, the deduplication processing is done at the primary location (source). The overhead of deduplication is incurred by the production server, and the deduplication happens before any data transfer to the backup location (target).</li>
 	<li>In target deduplication, the deduplication processing is done at the backup location (target). The overhead of deduplication is incurred by the backup infrastructure, and the deduplication happens after the data is transferred between the primary location and the backup location</li>
 	<li>Azure Backup adds value to this already optimized storage stack by compressing the data written to Azure Storage</li>
 	<li>The deduplication style that DPM uses is essentially target deduplication</li>
 	<li>Both DPM and Azure Backup use some variation of target deduplication. This means that the product workload is unaffected by the deduplication operation, and the customer need not account for the impact of a CPU-intensive operation like deduplication on the production server</li>
 	<li>DPM is designed to work with Windows Server Deduplication in a very specific configuration. More details about the setup and instructions for enabling deduplication are available in the whitepaper at <a href="https://technet.microsoft.com/en-us/library/dn891438.aspx" target="_blank">https://technet.microsoft.com/en-us/library/dn891438.aspx</a>.</li>
 	<li>In a deduplication-enabled DPM deployment, the DPM VHDs must be placed on a separate file server system volume—typically a storage volume for the shared folder</li>
 	<li>There are two main restrictions—the SOFS volume size and the file size—for which the details can be found at <a href="http://blogs.technet.com/b/filecab/archive/2014/12/04/sizing-volumes-for-data-deduplication-in-windows-server.aspx" target="_blank">http://blogs.technet.com/b/filecab/archive/2014/12/04/sizing-volumes-for-data-deduplication-in-windows-server.aspx</a>.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 09: Integration with System Center</h3>
<div>
<ul>
 	<li>For more information about the salient features of the recently released DPM Management Reporting, Discovery, and Monitoring management packs, see <a href="http://blogs.technet.com/b/dpm/archive/2015/04/16/announcing-centralized-and-customizable-backup-reports-using-data-protection-manager.aspx" target="_blank">http://blogs.technet.com/b/dpm/archive/2015/04/16/announcing-centralized-and-customizable-backup-reports-using-data-protection-manager.aspx</a>.</li>
 	<li>For more information about Central Console features and the various tasks that can be performed with the Central Console, see <a href="https://technet.microsoft.com/en-us/library/jj860391.aspx" target="_blank">https://technet.microsoft.com/en-us/library/jj860391.aspx</a>.</li>
 	<li>These alerts cannot be auto-resolved because if a data source has missed its SLA, you cannot travel back in time to create a recovery point for it. The only way to resolve an alert like this is to manually inactivate the alert</li>
 	<li>More details concerning the Client Auto Deployment management pack can be found at <a href="https://technet.microsoft.com/en-us/library/hh757976.aspx" target="_blank">https://technet.microsoft.com/en-us/library/hh757976.aspx</a>.</li>
</ul>
&nbsp;
<h3>Chapter 10: Integration with Azure Backup</h3>
<div>
<ul>
 	<li>With Azure Backup, backed up data is always encrypted on both the wire and at rest on Azure such that it is always secure before it leaves the on-premises datacenter.</li>
 	<li>For more information about Azure Backup and a list of frequently asked questions, see <a href="http://azure.microsoft.com/en-us/documentation/articles/backup-azure-backup-faq/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/backup-azure-backup-faq/</a>.</li>
 	<li>With Azure Backup, organizations can back up files and folders on their Windows-based desktops and laptop computers directly to the cloud with an entirely self-service model where the IT administrator needs to take minimal or no action on behalf of the user.</li>
 	<li>For more information on the support for backup of Azure IaaS VMs, see <a href="http://azure.microsoft.com/blog/2015/03/26/azure-backup-announcing-support-for-backup-of-azure-iaas-vms/" target="_blank">http://azure.microsoft.com/blog/2015/03/26/azure-backup-announcing-support-for-backup-of-azure-iaas-vms/</a>.</li>
 	<li>With Azure Backup, you can technically store data for up to 99 years, but in practice, most businesses need a solution that retains data for about 7 to 10 years.</li>
 	<li>For detailed information about the steps for configuring Azure Backup long-term retention policies. see <a href="http://azure.microsoft.com/en-gb/documentation/articles/backup-azure-backup-cloud-as-tape/" target="_blank">http://azure.microsoft.com/en-gb/documentation/articles/backup-azure-backup-cloud-as-tape/</a>.</li>
</ul>
&nbsp;
<h3>Chapter 11: Protecting Azure IaaS Virtual Machines</h3>
<div>
<ul>
 	<li>To learn more about using Azure Backup for the backup of Azure VMs, read the online documentation that covers these aspects in much greater detail at <a href="http://azure.microsoft.com/en-us/documentation/articles/backup-azure-vms" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/backup-azure-vms</a>.</li>
</ul>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
