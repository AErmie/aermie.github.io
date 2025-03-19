---
layout: page
title: Book Review: Microsoft System Center - Cloud Management with App Controller
date: 2015-05-28 13:12
author: AdinErmie
comments: true
categories: []
---
<div class="entry-content clearfix">

<a href="/wp-content/uploads/2015/05/Cloud-Management-with-App-Controller.jpg"><img class=" size-medium wp-image-12411 alignleft" src="/wp-content/uploads/2015/05/Cloud-Management-with-App-Controller-246x300.jpg" alt="Cloud Management with App Controller" width="246" height="300" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2013/11/26/free-ebook-microsoft-system-center-cloud-management-with-app-controller.aspx" target="_blank">Microsoft System Center: Cloud Management with App Controller</a> eBook.

The chapters that I found most helpful were Chapter 2 “Managing Private Clouds", Chapter 3 "Managing Public Clouds", and Chapter 4 "Managing Hybrid Clouds", hence the majority of my highlights are from these chapters.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: App Controller Essentials</h3>
<div>
<ul>
	<li>For installing App Controller, the Deployment Tools and Windows PE are especially essential</li>
	<li>Installing App Controller on a server requires a domain user account with local Administrator privileges. The service account to run App Controller services can be the built-in Network Service account or a domain account.</li>
	<li>The user account installing App Controller must have at least database owner (DBO) permissions on the database associated with your App Controller installation.
The authorization model that App Controller uses is inherited from that of the associated VMM server.</li>
	<li>One key distinction of accessing resources with App Controller and VMM Admin Console is that App Controller does not reveal fabric regardless of whether the account is a VMM administrator or one with a Fabric Administrator role.</li>
	<li>Cloud service providers can provide multiple instances of App Controller targeting different users with different resources for different deployment scenarios to best serve the intended users.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 02: Managing Private Clouds</h3>
<div>
<ul>
	<li>For details on the process of building private clouds with VMM, be sure to leverage the information and step-by-step walkthroughs provided at <a href="http://aka.ms/BuildYourCloud" target="_blank">http://aka.ms/BuildYourCloud</a>.</li>
	<li>For highly available App Controller installations, System Center 2012 R2 also supports the following high availability configurations:
<ul>
	<li>Database Server Install the database server as a clustered installation of SQL Server</li>
	<li>App Controller Install App Controller in a Highly Available Virtual Machine (HAVM) on a Hyper-V Host Cluster</li>
</ul>
</li>
	<li>With System Center 2012 R2, multiple App Controller servers can also be located behind a load balancer. Note that in a load-balanced configuration, each App Controller server will need to share a common encryption key. After installing the first App Controller server, you can export the encryption key by using the Export-SCACAesKey Windows PowerShell cmdlet. You will then provide this same exported encryption key when installing the other App Controller servers.</li>
	<li>During the installation of System Center 2012 R2 App Controller, the setup program will automatically install .NET Framework 4.0 and the Web Server (IIS) role. In addition, on Windows Server 2008 R2 servers, .NET Framework 3.5.1 will also be automatically installed to support the Windows PowerShell module for App Controller. On Windows Server 2012 and later, .NET Framework 3.5.1 must be manually installed to use the Windows PowerShell module for App Controller.</li>
	<li>When installing System Center 2012 R2 App Controller in a production environment, it is recommended that you use a registered SSL certificate from a trusted certificate provider</li>
	<li>Network file shares are useful in App Controller when copying virtual machine files from other locations to/from a VMM library for deployment within a private cloud.</li>
	<li>If files will be copied to/from an added file share via the App Controller portal, the machine account for each App Controller server must also be granted Full Control permissions to each added file share.</li>
	<li>VM Templates are used to specify a template configuration for a single VM being deployed to a private cloud, whereas Service Templates can include a template configuration for more complex multi-tier applications that can involve multiple virtual machines, applications, virtual networks, and load balancers as part of a single template.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 03: Managing Public Clouds</h3>
<div>
<ul>
	<li>After you have access to an active Windows Azure subscription, you’ll next need to set up a management certificate. To maintain a secure connection between App Controller and Windows Azure, a management certificate is used to authenticate the connection. In a production environment, you’ll typically want to provision this management certificate via an internal Public Key Infrastructure (PKI) so that certificates can be easily managed and renewed on a centralized basis</li>
	<li>You can find additional details on planning and deployment of AD CS in the Microsoft TechNet library at <a href="http://aka.ms/SC2012AC-ADCS" target="_blank">http://aka.ms/SC2012AC-ADCS</a>.</li>
	<li>After a management certificate has been created, the public keys associated with this certificate must be exported and uploaded to Windows Azure</li>
	<li>To export a copy of the certificate with both public and private keys, you use the IIS Manager tool again. However, this time you use the Export option from the Server Certificates page to export a password-protected .PFX file that includes both public and private keys</li>
	<li>App Controller can support connections for up to 20 Windows Azure subscriptions per user from a single management portal. This can be useful when supporting centralized public cloud management in an organization where each business unit or team has been allocated their own subscriptions for charge-back or show-back purposes.</li>
	<li>Storage accounts in Windows Azure provide a cloud-based storage location where virtual hard disks and other files can be stored</li>
	<li>After a Windows Azure storage account is created, you need to create at least one container inside the new storage account in which to store virtual hard disks and files</li>
	<li>A container in a Windows Azure storage account provides capabilities that are similar to a folder in an on-premises file system.</li>
	<li>In Windows Azure, a cloud service provides a “container” in which one or more virtual machines can run.</li>
	<li>to learn more about building virtual networks you can leverage the Build Virtual Networks in Windows Azure Step-by-Step Lab Guide that is available at <a href="http://aka.ms/VNetCloudLab" target="_blank">http://aka.ms/VNetCloudLab</a>.</li>
	<li>By tagging multiple virtual machines with the same availability set name, Windows Azure automatically locates these virtual machines in separate upgrade domains and fault domains to provide the highest possible level of application availability during planned and unplanned downtime windows</li>
	<li>Note that configuring endpoints only configures the Windows Azure virtual firewall. If the operating system running within a virtual machine also includes a firewall, such as Windows Firewall with Advanced Services, you will need to confirm that this firewall permits the allowed inbound traffic as well.</li>
	<li>Note that when stopping cloud services or performing a shutdown of virtual machines from the App Controller portal, the configuration, processor, memory, and IP address resources are kept in a reserved state. Because these reservations are maintained, Windows Azure continues to accumulate compute charges for cloud services and virtual machines in this state</li>
</ul>
&nbsp;
<h3>Chapter 04: Managing Hybrid Clouds</h3>
<div>
<ul>
	<li>To effectively use App Controller user managed resources deployed in a hybrid computing environment, it is essential to understand the VMM private cloud deployment model using service templates and the Windows Azure Infrastructure as a Service (IaaS) deployment methodology. You might find the following resources helpful in this regard:
<ul>
	<li><a href="http://aka.ms/SCVMM" target="_blank">http://aka.ms/SCVMM</a></li>
	<li><a href="http://aka.ms/AzureIaaSMethod" target="_blank">http://aka.ms/AzureIaaSMethod</a></li>
</ul>
</li>
	<li>There are three types of Windows Azure storage: blob, table, and queue storage. To consume storage, you first need to create a storage account in Windows Azure</li>
	<li>VHD files must be stored in page blob format, and each page blob has a maximum size of 1 TB.</li>
	<li>What this means is that there must be a cloud service for every deployment instance. For example, with IaaS the objects that are delivered are virtual machines.</li>
	<li>In the world of cloud computing, it’s not just about managing virtual machines anymore; instead, it’s about managing services. This concept is well explained in “A Memorandum to IT Leadership and Decision Makers” which is found at <a href="http://aka.ms/memo" target="_blank">http://aka.ms/memo</a>.</li>
	<li>An affinity group is a designation to a Microsoft data center in a specific region such as North America, Europe, or Asia. When you create a new virtual network it must be associated with an affinity group in order to ensure that all compute instances (virtual machines) associated with the virtual network are deployed in the same data center so they can be as close together as possible to optimize performance and help reduce transmission costs. Affinity groups can also be applied to storage accounts so that all the VHDs of virtual machines on the same virtual network are kept near their associated compute instances.</li>
	<li>A blog post explaining all this in more detail can be found at <a href="http://aka.ms/AzureIaaSMethod" target="_blank">http://aka.ms/AzureIaaSMethod</a>.</li>
	<li>In the Windows Azure PaaS model you can chose to deploy the application (package) to either a staging or a production environment. A staging environment is a holding place for testing purposes and does not provide a virtual IP address, which means the deployed application is not exposed to the Internet. A production environment assigns a virtual IP address and therefore exposes the application to the Internet.</li>
	<li>When you configure virtual machines as an availability set, however, Windows Azure automatically eliminates single point of failure due to hardware by placing the virtual machine instances across multiple fault domains. (Windows Azure guarantees at least two fault domains for an availability set.)</li>
	<li>For more information on fault domains and availability sets, see http://aka.ms/wafdud.</li>
	<li>Each disk is a page blob in Windows Azure Storage and can have a maximum size of 1 TB.</li>
</ul>
&nbsp;
<h3>Chapter 05: App Controller cmdlets</h3>
<div>
<ul>
	<li>Both the subscription ID and a local management certificate in PFX format are required to establish a secure connection.</li>
	<li>The local management certificate is paired up with an already uploaded x.509 certificate for the intended Windows Azure subscription so that communications between App Controller and the Windows Azure subscription can be carried out in a private and secure fashion.</li>
	<li>There are 29 cmdlets included in the AppController PowerShell module</li>
	<li>Once you have acquired an x.509 certificate for connecting with Windows Azure, right-click the certificate to install it in the local certificate store on the server. Next, use the Certificates snap-in to export the certificate to PFX format with the private key as shown in Figure 5-6. Then log on to the target Windows Azure subscription and upload the x.509 certificate to the certificate store by selecting the Settings workspace of the Windows Azure Management Portal.</li>
	<li>A library share is basically a tool for performing certain complicated tasks in a simple and straightforward manner. For instance, to move a VHD from an on-premises location to your Windows Azure cloud is often tedious work. But by using App Controller this is now as simple as performing a copy-and-paste operation with a library share. You simply place the target VHD on a network share and then expose the share as a library share in App Controller. Then, as shown in Figure 5-9, you copy the VHD from the library share and paste it into a storage container of your Windows Azure subscription.</li>
	<li>The Add-SCACAzureDisk cmdlet first requires importing the VMM module (that is, virtualmachinemanager) into a current Windows PowerShell session in order to run this cmdlet.</li>
</ul>
&nbsp;

</div>
&nbsp;

</div>
</div>
</div>
&nbsp;
