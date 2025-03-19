---
layout: page
title: Book Review: Introducing Windows Azure For IT Professionals
date: 2015-06-19 19:03
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2015/06/IntroducingWindowsAzureForITProfessionals.jpg"><img class=" size-full wp-image-13671 alignleft" src="/wp-content/uploads/2015/06/IntroducingWindowsAzureForITProfessionals.jpg" alt="IntroducingWindowsAzureForITProfessionals" width="201" height="244" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2013/10/01/free-ebook-introducing-windows-azure-for-it-professionals.aspx" target="_blank">Introducing Windows Azure For IT Professionals</a> eBook.

The chapter(s) that I found most helpful were basically all of them! hence the majority of my highlights are from basically the entire book.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: Understanding Windows Azure</h3>
<div>
<ul>
	<li>Not every business is ready to take advantage of the different types of cloud computing services available. To help you learn whether your business is ready for the cloud, Microsoft has a web-based Cloud Security Readiness tool that assesses the systems, processes, and productivity of your current IT environment and generates a custom noncommercial report that provides recommendations to help you evaluate the benefits of cloud computing. To use this free tool, go to <a href="http://technet.microsoft.com/en-us/security/jj554736.aspx" target="_blank">http://technet.microsoft.com/en-us/security/jj554736.aspx</a>.</li>
	<li>Software as a Service (SaaS) In this approach, the customer utilizes standardized cloud-based services such as document management or email that are provided by the hoster. This model views the customer as the user who consumes cloud applications, typically as a pay-as-you-go service.</li>
	<li>Infrastructure as a Service (IaaS) In this approach, the customer pays the hoster to run a virtual machine in the hoster’s cloud. The customer is responsible for configuring and managing the virtual machine’s guest operating system and applications. This model views the customer as the IT owner since the customer has complete control over what they can do with their virtual machine.</li>
	<li>Platform as a Service (PaaS) In this approach, the customer develops and deploys applications for a specific application architecture. The hoster provides the application runtime, storage, and integration needed to run the customer’s application and is responsible for keeping the environment up and running, operating systems updated, and customer data safe. This model views the customer as the application owner since the customer is responsible for developing and maintaining the application. The customer is also responsible for data integrity and business logic.</li>
	<li>For a pictorial view of the architecture of the Windows Azure platform that you can print and hang on your office wall, download the Windows Azure poster from the Microsoft Download Center at <a href="http://www.microsoft.com/en-us/download/details.aspx?id=35473" target="_blank">http://www.microsoft.com/en-us/download/details.aspx?id=35473</a>.</li>
	<li>To keep up with all the latest that’s happening with the Windows Azure platform, subscribe to the Windows Azure blog on MSDN at <a href="http://blogs.msdn.com/b/windowsazure/" target="_blank">http://blogs.msdn.com/b/windowsazure/</a>. Or simply visit <a href="http://www.windowsazure.com" target="_blank">http://www.windowsazure.com</a></li>
</ul>
&nbsp;

</div>
<h3>Chapter 02: Windows Azure Compute Services</h3>
<div>
<ul>
	<li>You can copy virtual hard disks (VHDs) from your on-premises environment into Windows Azure to use as templates for creating new virtual machines. And you can copy VHDs out of Windows Azure and run them locally in your datacenter.</li>
	<li>In Windows Server 2012 every aspect of the operating system can be configured and managed using Windows PowerShell.</li>
	<li>The Windows Azure PowerShell module is not provided as part of Windows, however it can be added easily.</li>
	<li>All the available cmdlets in the Windows Azure module can be viewed using the command: Get-Command—Module Azure</li>
	<li>If the Windows PowerShell environment was not launched via the Windows Azure PowerShell program, then the first step is to actually import the Windows Azure PowerShell module which is accomplished using the following command: Import-Module "C:\Program Files (x86)\Microsoft SDKs\Windows Azure\
PowerShell\Azure\Azure.psd1"</li>
	<li>Run the command below to see every template that is really available.
Get-AzureVMImage | ft Label,ImageName,LogicalSizeInGB</li>
	<li>For more detailed information on what Windows Azure Virtual Machines is and how it works, see <a href="http://www.windowsazure.com/en-us/documentation/services/virtual-machines/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/virtual-machines/</a>.</li>
	<li>More information on Windows Azure PowerShell can be found at <a href="http://msdn.microsoft.com/library/windowsazure/jj156055" target="_blank">http://msdn.microsoft.com/library/windowsazure/jj156055</a>.</li>
	<li>“Building Your Lab, Dev, and Test Scenarios in Windows Azure Infrastucture Services (IaaS),” which is available at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B370" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B370</a></li>
	<li>“Best Practices from Real Customers: Deploying to Windows Azure Infrastructure Services (IaaS),” which is available at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B361" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B361</a></li>
	<li>“Crash Course on Automating Deployments in Windows Azure Virtual Machines. How and Which Tools?,” which is available at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B405" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B405</a></li>
	<li>Windows Azure provides two deployment environments for cloud services: staging and production. The staging environment is where you can test your deployment before you “swap” it into your production environment by switching the virtual IP addresses (VIPs) by which your cloud service is accessed.</li>
	<li>If you are using a web.config or app.config files, you should instead consider using a service configure (.cscfg) file.</li>
	<li>You can enable WAD within your application or after it has been deployed into Windows Azure.
WAD can be configured to collect the following data from a Windows Azure role instance:
<ul>
	<li>Windows Azure logs</li>
	<li>IIS logs (web role)</li>
	<li>WAD infrastructure logs</li>
	<li>IIS failed request logs</li>
	<li>Windows event logs</li>
	<li>Performance counters</li>
	<li>Crash dumps</li>
	<li>Custom error logs</li>
</ul>
</li>
	<li>WAD will store the data into a specific Windows Azure storage account, I recommend using a dedicated account so access can be segregated from any application data</li>
	<li>For Operations, we recommend the Cerebrata Azure Management Studio. If you are already using System Center Operations Manager (SCOM) to monitor your service, you will be happy to know that WAD is fully compatible and you can alert and report on data just like your Windows Azure role instance is an on-premises server.</li>
	<li>For more detailed information on what Windows Azure Cloud Services is and how it works, see <a href="http://www.windowsazure.com/en-us/documentation/services/cloud-services/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/cloud-services/</a>.</li>
	<li>For a walkthrough on how to create and deploy a cloud service using Windows Azure Cloud Services, see <a href="http://www.windowsazure.com/en-us/manage/services/cloud-services/how-to-create-and-deploy-a-cloud-service/" target="_blank">http://www.windowsazure.com/en-us/manage/services/cloud-services/how-to-create-and-deploy-a-cloud-service/</a>.</li>
	<li>For a demo of how to create and deploy a cloud service using Windows Azure, watch the TechEd 2013 presentation titled “Build Your First Cloud App: An Introduction to Windows Azure Cloud Services,” which can be found on Channel 9 at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B321" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B321</a>.</li>
	<li>To help you decide whether to host your web application using Windows Azure Web Sites, Virtual Machines, or Cloud Services, see <a href="http://www.windowsazure.com/en-us/manage/windows/fundamentals/compute/" target="_blank">http://www.windowsazure.com/en-us/manage/windows/fundamentals/compute/</a>.</li>
	<li>We might decide at some point to store more properties, and as long as dynamic schema is on, it modifies the table on the fly. It’s recommended that you turn that off (via the Configuration page) before going live.</li>
	<li>For more detailed information on what Windows Azure Mobile Services is and how it works, see <a href="http://www.windowsazure.com/en-us/develop/mobile/" target="_blank">http://www.windowsazure.com/en-us/develop/mobile/</a>.</li>
	<li>For a tutorial on how to get started using Windows Azure Mobile Services, see <a href="http://www.windowsazure.com/en-us/develop/mobile/tutorials/get-started/" target="_blank">http://www.windowsazure.com/en-us/develop/mobile/tutorials/get-started/</a>.</li>
	<li>“Build Real-World Modern Apps with Windows Azure Mobile Services on Windows Store, Windows Phone or Android,” which can be found at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B338" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B338</a>.</li>
</ul>
&nbsp;
<h3>Chapter 03: Windows Azure Network Services</h3>
<div>
<ul>
	<li>By default, all virtual machines running in the same cloud service can already communicate with each other without the need for you to create a virtual network for this purpose. By creating additional virtual networks, however, you can also enable virtual machines running in different cloud services to talk to each other.</li>
	<li>An affinity group is a logical grouping of Azure services that tells Windows Azure where to locate the services in order to optimize the performance of cloud applications</li>
	<li>For a comprehensive list of the different name resolution scenarios possible for Windows Azure and the solutions you can choose from, see <a href="http://msdn.microsoft.com/en-us/library/windowsazure/jj156088.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/windowsazure/jj156088.aspx</a>.</li>
	<li>In order to set up a site-to-site VPN with Windows Azure gateway, the on-premises VPN device must support IKE v1 or IKE v2.</li>
	<li>For more detailed information on what Windows Azure Virtual Network is and for tutorials on how to create and configure different kinds of virtual networks, see <a href="http://www.windowsazure.com/en-us/documentation/services/virtual-network/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/virtual-network/</a>.</li>
	<li>Additional documentation on Windows Azure Virtual Network can be found on MSDN at <a href="http://msdn.microsoft.com/en-us/library/windowsazure/jj156007.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/windowsazure/jj156007.aspx</a>.</li>
	<li>Traffic Manager lets you load balance incoming traffic across multiple hosted Windows Azure services regardless of whether they’re running in the same datacenter or in different ones at different geographical locations around the world</li>
	<li>Traffic Manager works by applying an intelligent policy engine to DNS queries for your domain names</li>
	<li>The process by which Traffic Manager routes traffic is explained in detail at <a href="http://msdn.microsoft.com/en-us/library/windowsazure/hh744833.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/windowsazure/hh744833.aspx</a>.</li>
	<li>For more detailed information on what Windows Azure Traffic Manager is, how it works, and how to plan and implement its use, see <a href="http://www.windowsazure.com/en-us/documentation/services/traffic-manager/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/traffic-manager/</a></li>
	<li>For a short walkthrough of configuring Traffic Manager to help make a cloud service highly available and reliable, see the post titled “Windows Azure July Updates: SQL Database, Traffic Manager, Autoscale, Virtual Machines” in Scott Guthrie’s blog at <a href="http://weblogs.asp.net/scottgu/archive/2013/07/23/windows-azure-july-updates-sql-database-traffic-manager-autoscale-virtual-machines.aspx" target="_blank">http://weblogs.asp.net/scottgu/archive/2013/07/23/windows-azure-july-updates-sql-database-traffic-manager-autoscale-virtual-machines.aspx</a>.</li>
	<li>For a demonstration of Traffic Manager, see the Microsoft TechEd 2012 presentations titled “Overview of New Networking Features in Windows Azure,” which is available for viewing and download from Channel 9 at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2012/AZR304" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2012/AZR304</a>.</li>
</ul>
&nbsp;
<h3>Chapter 04: Windows Azure Data Services</h3>
<div>
<ul>
	<li>Your data is safe with Windows Azure SQL Database because it’s stored in one primary datacenter and two replica datacenters</li>
	<li>Your business can grow because SQL Database supports dynamically scaling out by federation database to up to 150 databases</li>
	<li>It is important to understand that Windows Azure SQL Database is not feature-equivalent to Microsoft SQL Server, so not every exported SQL Server database can be imported successfully. Also, there are size limitations per database. For more information, see <a href="http://msdn.microsoft.com/en-us/library/windowsazure/ff394115.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/windowsazure/ff394115.aspx</a>.</li>
	<li>BLOBs provide a simple mechanism for storing large amounts of text or binary data such as images, audio, or visual files.</li>
	<li>For more detailed information on what Windows Azure SQL Database is and how to get started using it, see <a href="http://www.windowsazure.com/en-us/documentation/services/sql-database/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/sql-database/</a>.</li>
	<li>For information on other Windows Azure Storage services, including Tables and BLOB storage, see <a href="http://www.windowsazure.com/en-us/documentation/services/storage/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/storage/</a>.</li>
	<li>To get a deeper understanding of Windows Azure Tables, see <a href="http://blogs.msdn.com/b/windowsazurestorage/archive/2010/11/06/how-to-get-most-out-of-windows-azure-tables.aspx" target="_blank">http://blogs.msdn.com/b/windowsazurestorage/archive/2010/11/06/how-to-get-most-out-of-windows-azure-tables.aspx</a>.</li>
	<li>Getting the Most Out of Windows Azure Storage,” which is available at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B406" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B406</a></li>
	<li>Pushing Data to and from the Cloud with SQL Azure Data Sync,” which is available at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B207" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B207</a></li>
	<li>Protecting Your Data in Windows Azure SQL Database,” which is available at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B314" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B314</a></li>
	<li>For more detailed information on what HDInsight is and how to get started using it, see <a href="http://www.windowsazure.com/en-us/documentation/services/hdinsight/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/hdinsight/</a>.</li>
	<li>Predictive Analytics with Microsoft Big Data,” which can be found at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B339" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B339</a></li>
	<li>Big Data Analytics with Microsoft Excel 2013,” which can be found at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B336" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B336</a></li>
	<li>HDInsight: Introduction to Hadoop on Windows,” which can be found at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B221" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DBI-B221</a></li>
	<li>For detailed information on what Windows Azure SQL Reporting is and how to get started using it, see <a href="http://www.windowsazure.com/en-us/documentation/services/sql-reporting/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/sql-reporting/</a>.</li>
	<li>Windows Azure Backup uses certificates to create a secure connection between the server and the Windows Azure backup vault. In addition, all the data is encrypted before it is sent to Windows Azure. In order to do this, Microsoft uses a passphrase that you enter (or have generated) during the server registration process. The data is stored in Windows Azure Backup in an encrypted state</li>
	<li>For more detailed information on what Windows Azure Backup is and how to get started using it, see <a href="http://www.windowsazure.com/en-us/documentation/services/recovery-services/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/recovery-services/</a>.</li>
	<li>Also be sure to see the TechEd 2013 presentation titled “Automate Private Cloud Protection and Recovery with Microsoft System Center 2012 - Data Protection Manager,” which is available for viewing and download from Channel 9 at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B401" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B401</a></li>
	<li>For more detailed information on what Hyper-V Recovery Manager is and how to configure it, see <a href="http://www.windowsazure.com/en-us/documentation/services/recovery-services/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/recovery-services/</a>.</li>
	<li>For a blog detailing how Hyper-V Recovery Manager works in the context of “in the cloud,” see <a href="http://blogs.technet.com/b/in_the_cloud/archive/2013/08/14/what-s-new-in-2012-r2-cloud-integrated-disaster-recovery.aspx" target="_blank">http://blogs.technet.com/b/in_the_cloud/archive/2013/08/14/what-s-new-in-2012-r2-cloud-integrated-disaster-recovery.aspx</a>.</li>
	<li>When you are not expecting a very high load, you can scale-in the cache roles and decrease the number of instances. Please note that scaling operations may incur data loss.</li>
	<li>Also, the Cache service is designed to occupy the specified memory as soon as possible. It doesn’t wait for the memory to be allocated when the need arises. As a result, you may see that even if you have not put lot of data in cache, the memory consumption by Cache service appears to be increasing as soon as the service starts. As long as the memory usage is stabilizing eventually, this is should be okay.</li>
	<li>In a case where high availability is turned on, cache cluster will perform data replication for you.</li>
	<li>The percent memory specified is applicable only in the Windows Azure environment and not in a development environment. Cache Emulator is designed to consume 16 percent of available memory (and some overhead). You cannot override this behavior.</li>
	<li>While you are decreasing the number of instances, it is recommended that you reduce by not more than three instances at a time. Otherwise, your cache cluster can become unstable</li>
	<li>For more detailed information on what Windows Azure Cache is and how to get started using it, see the following Planning Guides on MSDN:
“Capacity Planning for Windows Azure Cache Service (Preview),” which can be found at <a href="http://msdn.microsoft.com/en-us/library/windowsazure/dn386139.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/windowsazure/dn386139.aspx</a>
“Cache Offerings for Windows Azure Cache Service (Preview),” which can be found at <a href="http://msdn.microsoft.com/en-us/library/windowsazure/dn386114.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/windowsazure/dn386114.aspx</a></li>
</ul>
&nbsp;
<h3>Chapter 05: Windows Azure App Services</h3>
<div>
<ul>
	<li>Guidelines for Deploying Windows Server Active Directory on Windows Azure Virtual Machines,” which can be found at <a href="http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx</a>.</li>
	<li>DirSync server polls for the object changes and uploads them to the cloud—every three hours</li>
	<li>The latest release of DirSync supports synchronization of hashes computed from password hashes; given the sensitivity of the password changes, the password synchronization happens in near real-time.</li>
	<li>The difference between Federated Authentication and Managed Authentication is that in the federated setting, the user authentication for all users happens through ADFS attached to the on-premises AD DS while the user validation for non-federated users happens at Windows Azure AD with no ADFS traversal</li>
	<li>For more detailed information on what Windows Azure Active Directory is and how to get started using it, see <a href="http://www.windowsazure.com/en-us/documentation/services/active-directory/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/active-directory/</a>.</li>
	<li>Running your Active Directory in Windows Azure Virtual Machines,” which can be found at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B300" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/MDC-B300</a></li>
	<li>Introduction to Windows Azure Active Directory,” which can be found at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B309" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B309</a></li>
	<li>For more detailed information on what Windows Azure Multi-Factor Authentication is and how to get started using it, see <a href="http://www.windowsazure.com/en-us/documentation/services/multi-factor-authentication/" target="_blank">http://www.windowsazure.com/en-us/documentation/services/multi-factor-authentication/</a>.</li>
	<li>“B2B Collaboration on Windows Azure,” which can be found at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B343" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/WAD-B343</a></li>
	<li>For more detailed information on what Windows Azure Media Services is and how to get started using it, see <a href="http://www.windowsazure.com/en-us/develop/media-services/" target="_blank">http://www.windowsazure.com/en-us/develop/media-services/</a>.</li>
</ul>
&nbsp;

</div>
</div>
<h3>Chapter 06: Getting Started With Windows Azure</h3>
<div>
<ul>
	<li>There’s no better way of finding out about the powerful capabilities of Windows Azure than by trying out the platform</li>
	<li>The best way to keep up with new features and enhancements in Windows Azure is by following the official Windows Azure Blog at <a href="http://www.windowsazure.com/en-us/community/blog/" target="_blank">www.windowsazure.com/en-us/community/blog/</a></li>
	<li>There are two great places you can go online to ask questions about Windows Azure and get answers from the community:
<ul>
	<li>The Windows Azure forums on MSDN at <a href="http://social.msdn.microsoft.com/Forums/ windowsazure/en-US/home?category=windowsazureplatform%2Cazuremarketplace%2 Cwindowsazureplatformctp" target="_blank">http://social.msdn.microsoft.com/Forums/ windowsazure/en-US/home?category=windowsazureplatform%2Cazuremarketplace%2 Cwindowsazureplatformctp</a>.</li>
	<li>Stack Overflow at <a href="http://stackoverflow.com/questions/tagged/azure" target="_blank">http://stackoverflow.com/questions/tagged/azure</a>.</li>
</ul>
</li>
</ul>
</div>
</div>
</div>
