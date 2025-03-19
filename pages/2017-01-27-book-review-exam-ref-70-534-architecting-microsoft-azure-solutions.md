---
layout: page
title: Book Review: Exam Ref 70-534 Architecting Microsoft Azure Solutions
date: 2017-01-27 20:46
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2017/01/ExamRef70534Cover.jpg"><img class="alignleft wp-image-26771 size-medium" src="/wp-content/uploads/2017/01/ExamRef70534Cover-244x300.jpg" width="244" height="300" /></a>Recently, I finished reading the Exam Ref 70-534 Architecting Microsoft Azure Solutions eBook.

<span style="color: #000000;">The chapter(s) that I found most helpful were basically all of them! </span>Hence the majority of my highlights are from basically the entire book. Note that I didn't just highlight all of the "Exam Tip" content, but also additional information that I found useful in learning and understanding the topic.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h3>Chapter 01: Design Microsoft Azure infrastructure and networking</h3>
<ul>
 	<li>EXAM TIP You might find both MCIO and GFS are used in documentation, online materials, and white papers to refer to the team that operates Azure datacenters. As far as the exam is concerned, the two names are interchangeable. Also, sometimes Azure datacenters are referred to as Microsoft datacenters. The exam doesn’t distinguish between the two, either.</li>
 	<li>Azure is available in 140 countries and supports 10 languages and 19 currencies. Massive
datacenters at 17 geographic regions provide scalable services to all Azure customers around the globe. For example, Azure Storage stores more than 30 trillion objects and serves on average in excess of 3 million requests per second.</li>
 	<li>Be aware that in some texts the terms “regions” and “locations” are often used interchangeably. A datacenter is also sometimes referred as a facility. Azure doesn’t have a formal concept of “zones,” although a zone roughly maps to a datacenter or a facility in some contexts. For example, Azure Storage provides Zone-Redundant Storage (ZRS), which maintains three copies of your data across two to three facilities within a single region or across two regions.</li>
 	<li>It’s perfectly fine to use a user interface (UI) localized in Japanese to manage resources around the globe. However, many Azure objects don’t allow non-English characters in their names or identifiers.</li>
 	<li>Azure adopts polices such as just-in-time administrator accesses and just-enough administrator accesses. Microsoft staff doesn’t have access to customer data by default. When Microsoft personnel need access to Azure resources for diagnosing specific customer problems, they are granted access to the related resources for no more than
a predetermined window. All activities are carefully monitored and logged.</li>
 	<li>When patch releases are required, they are analyzed and applied to the Azure environment based on the severity. Patches are also automatically applied to customer guest VMs unless the customer has chosen manual upgrades, in which case the customer is responsible for patching.</li>
 	<li>To help customers to achieve compliance goals, Microsoft has developed an extensible
compliance framework by which Azure can adapt to regulatory changes. Azure has been
independently verified by a diverse range of compliance programs, such as ISO 27001/27002, FISMA, FedRAMP, HIPPA, and EU Model Clauses.</li>
 	<li>Microsoft Azure Trust Center (http://azure.microsoft.com/en-us/support/trust-center/) is a
central point of reference for materials related to security and compliance. For an up-to-date compliance program list, go to <a href="http://azure.microsoft.com/en-us/support/trust-center/compliance" target="_blank">http://azure.microsoft.com/en-us/support/trust-center/compliance</a>.</li>
 	<li>As a matter of fact, Microsoft runs some of the most effi cient cloud-scale datacenters in
the world with Power Usage Effectiveness (PUE) measures as low as 1.125. PUE is the ratio between total facility power usage and IT equipment’s power usage. A lower PUE means less power is consumed to support day-to-day facility operations such as providing office lighting and running elevators. Because such additional power consumption is unavoidable, A PUE of 1.125 is very hard to achieve. For comparison, the industry norm is about 1.8.</li>
 	<li>Unplanned maintenances are triggered by unexpected physical infrastructure problems such as network failures, rack-level failures and other hardware failures. When such a failure is detected, Azure automatically moves your VMs to a healthy host.</li>
 	<li>At the hardware level, Fault Domains don’t share a common power source or network switch, so the probability of two Fault Domains failing at the same time is low.</li>
 	<li>Regardless of how short the window is, the VM is still restarted. Your application needs to be able to restart itself when this happens. Otherwise, although the VM is recovered, your application is still unavailable.</li>
 	<li>Different Azure services throttle service calls based on different criteria, such as the
amount of stored data, the number of transactions, and system throughputs. When you
subscribe to an Azure service, you should understand how the service throttles your calls and ensure that your application won’t exceed those limits.</li>
 	<li>If you’ve decided that a single service entity won’t satisfy your application’s
needs, you should plan ahead to build multi-entity support into your architecture so that your application can be scaled out as needed.</li>
 	<li>Azure services supports three different authentication strategies: using a secret key, using a Shared Access Signature (SAS), and using federated authentication via Azure AD.</li>
 	<li>SAS is a proven way to provide detailed level of access control over entities. With SAS, you can grant access to specific data with explicit rights during given time windows. The access is automatically revoked as soon as the window is closed.</li>
 	<li>When you provision a new VM on Azure, you never gain physical access to the hosting machine. Instead, you need to operate the machine through remote connections such as remote desktop or Secure Shell (SSH).</li>
 	<li>NOTE ABOUT AFFINITY GROUPS FOR VIRTUAL NETWORKS
Previously, when you created a virtual network, you needed to associate the network
E with an Affinity Group. This is no longer a requirement. Now, virtual networks are
associated directly with a region (location). Such virtual networks are called regional
virtual network in some texts.</li>
 	<li>You can also use CNAME or A records to associate a custom domain name with your VM.
When you use A records, however, you need to note that the VIP of your VM might change.</li>
 	<li>When you provision a VM on Azure by using the management portal, by default the device is accessible through Remote Desktop and Windows PowerShell Remoting for Windows-based VMs, and through SSH for Linux-based VMs. This is because Azure automatically defines the corresponding endpoints.</li>
 	<li>When you apply an ACL to a load-balanced endpoint, it’s applied to all VMs in the same load-balanced set. You can specify up to 50 ACL rules per VM endpoint.</li>
 	<li>Each NSG comes with a number of default rules that you can’t remove. However, as these rules have lower priorities, you can override them by additional rules.</li>
 	<li>NSGs are different from ACLs in a couple of aspects:
<ul>
 	<li>ACLs are applied to traffic t o a specific VM endpoint, whereas NSGs are applied to all traffic that is inbound and outbound on the VM.</li>
 	<li>ACLs are associated to a VM endpoint, whereas NSGs are associated to a VM, or a
subnet within a virtual network.</li>
</ul>
</li>
 	<li>NOTE INCOMPATIBILITY BETWEEN ACL AND NSG
You cannot use both ACL and NSG on the same VM instance. You must first remove all endpoint ACLs before you can associate an NSG.</li>
 	<li>Basic tier is most suitable for development, tests, and simple production workloads. It doesn’t have features such as load balancing and autoscaling. And, there are fewer VM sizes from which to choose. On the other hand, the Standard tier provides a wide range of VM sizes with features such as load balancing and autoscaling to support production workloads.</li>
 	<li>EXAM TIP A0 to A4 are called by different names in the Basic tier and the Standard tier. In the Basic tier, they are referred as Basic_A0 to Basic_A4, whereas in the Standard series, each of the sizes has its own corresponding names, which are used in scripts and API calls. You should know how these names mapped to VM sizes:
<ul>
 	<li>A0: extra small</li>
 	<li>A1: small</li>
 	<li>A2: medium</li>
 	<li>A3: large</li>
 	<li>A4: extra large</li>
</ul>
</li>
 	<li>NOTE INCREASED OS DRIVE SIZES
The maximum capacity of OS drives used to be 127 GB. Since March 2015, this limit has been increased to 1,023 GB.</li>
 	<li>You can choose a host caching preference—None, Read Only, or Read/Write—for each
data drive. The default settings usually work fine, unless you are hosting database workloads or other workloads that are sensitive to small I/O performance differences.</li>
 	<li>Before you can capture a generalized image, you need to shut down the VM. After the VM is captured as an image, the original VM is automatically deleted.</li>
 	<li>If a VM is running when an image is captured, the image is in crash-consistent state. If application consistency or cross-drive capture is needed, it’s recommended to shut down the VM before capturing the image.</li>
 	<li>When you provision a new VM, a light-weight Azure Virtual Machine Agent (VM Agent)
is installed on the VM by default.</li>
 	<li>NOTE VM AGENT OPT-OUT
When creating a VM, you can choose not to install VM agent. You can install VM Agent
to an existing VM; however, when a VM agent is installed, removing it is not a supported
scenario. You can, of course, physically remove the agent, but the exact behavior after
removal is unsupported.</li>
 	<li>Windows PowerShell Desired State Configuration (DSC) takes a different approach. Instead of describing steps of how the VM state should be built up, you simply describe what the desired final state is with DSC. Then, DSC ensures that the final state is reached.</li>
 	<li>You can use the Test-AzureResourceGroupTemplate cmdlet to validate your template at any time. You need an actual Resource Group in order to use the cmdlet.</li>
 	<li>AGILITY
Compared to VMs, containers are much more light weight because containers use process
isolation and file system virtualization to provide process-level isolations among containers. Containers running on the same VM share the same system core so that the system core is not packaged as part of the container. Because starting a new container instance is essentially the same as starting a new process, you can start containers quickly—usually in time frames less than a second. The fast-start time makes containers ideal for the cases such as dynamic scaling and fast failover.</li>
 	<li>EXAM TIP
Container technology has gained considerable momentum in the past few years. New
capabilities, new services, and new companies are emerging rapidly and the landscape is
changing continually. For example, there are many variations in capabilities of different orchestration offerings. At this point, the container should not be a focus of the test, so you
shouldn’t spend a lot of energy to chase new developments in the field. However it’s very
important to understand the benefits of containers because they will become increasingly
important in future tests.</li>
 	<li>Scaling-up refers to increasing the compute power of the hosting nodes. In an on-premises
datacenter, scaling up means to increase the capacity of the servers by increasing memory, processing power, or drive spaces.</li>
 	<li>In the cloud, scaling-up means to choose a bigger VM size. In this case, scaling-up is constrained by what VM sizes are available.</li>
 	<li>Scaling-out takes a different approach. Instead of trying to increase the compute power
of existing nodes, scaling-out brings in more hosting nodes to share the workload. There’s no theoretical limit to how much you can scale-out—you can add as many nodes as needed. This makes it possible for an application to be scaled to very high capacity that is often hard to achieve with scaling-up. Scaling-out is a preferable scaling method for cloud applications.</li>
 	<li>The ILBs are not publically accessible. Instead, you can access them only by other roles
in the same Cloud Services, or other VMs within the same virtual network. ILB provides an
ideal solution for scaling a protected middle tier without exposing the layer to the public.</li>
 	<li>The load balancer will keep probing all of the VMs (including the unhealthy ones) so that when the failed VM is recovered, it will automatically be rejoined to the balanced set. You can use this feature to temporarily take a VM off the load balancer for maintenance by forcing a false response to probe signals.</li>
 	<li>Please note that the autoscaling system doesn’t respond to every metric value changes. Instead, it makes decisions based on the average value in the past hour.</li>
 	<li>NOTE AUTOSCALING AFTER THE FIRST HOUR
Because autoscaling uses the average value of the past hour, it’s not triggered as frequently as you might have expected. This is a very common point of confusion for many
users who set up the autoscaling policy for the first time.</li>
 	<li>No specific VPN devices are needed in this case. Instead, you install a Windows VPN client through which you can connect to any VMs and Cloud Services within the virtual network.</li>
 	<li>With Point-to-Site connection, you can connect to your VMs on Azure from anywhere. It
uses Secured Socket Tunneling Protocol (SSTP), which means that you can establish the connection through fi rewalls and Network Address Translation (NAT).</li>
 	<li>If you want to use both Site-to-Site VPN and Point-to-Site VPN at the same time, you’ll need a dynamic gateway.</li>
 	<li>Because VPNs go through the public Internet, there’s no SLA to guarantee the connectivity.</li>
 	<li>Azure confi gures a pair of cross-connections between Azure and the provider’s infrastructure in an active-active confi guration to ensure availability and resilience against failures.</li>
 	<li>To use Traffic Manager, you define a Traffic Manager profile that consists of a domain
name, a list of endpoints, and a load-balancing policy. When a user tries to access a service, the following activities happen:
<ul>
 	<li>1. The user accesses the service by the domain name provided by Traffic Manager
(*.traffi cmanager.net). If a custom domain is used, another DNS resolution is performed to first resolve the custom domain name to the Traffic Manager domain name.</li>
 	<li>2. When Traffic Manager receives the DNS resolution request, it evaluates its policy and picks an endpoint address based on availability, performance, or a round-robin policy.</li>
 	<li>3. Traffic Manager returns a CNAME record that maps the Traffic Manager domain name to the selected endpoint.</li>
 	<li>4. The user’s DNS server resolves the endpoint address to its IP address and sends it to the user.</li>
 	<li>5. The user calls the endpoint directly by the IP address.</li>
</ul>
</li>
 	<li>A couple of points are worth discussing here. First, Traffi c Manager functions during the
DNS resolution phase. The actual traffic doesn’t go through Traffi c Manager. Second, because DNS records are often cached, Traffi c Manager isn’t involved in every service request. Third, the endpoints don’t need to be on Azure. They can be on other cloud platforms, or even in on-premises datacenters.</li>
 	<li>You can also nest Traffi c Manager profiles, which means a profile at a higher level uses
other Traffi c Manager endpoints as candidate endpoints. Using nested profiles, you can
implement more complex policies. For example, you can have a top-level profile that uses the failover method to establish a primary site and a secondary site, and a second-level profile that distributes user traffics based on performance. You can have up to 10 levels of nested profiles.</li>
</ul>
<div>
<h3>Chapter 02: Secure Resources</h3>
<ul>
 	<li>EXAM TIP
Quite a few components participate in an authentication and authorization workflow.
Understanding how they interact with one another is the key to a successful implementation. Swim-lane diagrams such as that shown in Figure 2-1 are a proven, effective method to explain, or to memorize, how different parties work together. As an exercise in preparing for the exam, you should try to re-create these diagrams by yourself to ensure that you clearly understand how the process works.</li>
 	<li>the Premium tier also provides advanced features, such as machine learning–based security and usage reports, alerting, and multifactor authentication. For a detailed comparison of feature sets provided by these tiers, go to <a href="http://azure.microsoft.com/en-us/pricing/details/active-directory/" target="_blank">http://azure.microsoft.com/en-us/pricing/details/active-directory/</a>.</li>
 	<li>The second difference is that Azure AD and on-premises AD DS use different protocols.
On-premises AD DS uses protocols such as Kerberos and Lightweight Directory Access
Protocol (LDAP), whereas Azure AD uses Internet-oriented protocols, such as SAML 2.0, ws-Federation, OpenID Connect, and RESTful Graph API.</li>
 	<li>Third, although their functionalities overlap in terms of authentication and authorization,
they have mutually exclusive features. For instance, only on-premises AD DS supports constructs such as forests, domains, and organization units. Conversely, only Azure AD natively provides features such as Azure Access Panel and RESTful interfaces.</li>
 	<li>MORE INFO GRAPH EXPLORER
You can use a sample graphic explorer at https://graphexplorer.cloudapp.net/ to try out graphic queries. The site generates necessary authentication headers for you.</li>
 	<li>AD FS is the Microsoft implementation of the ws-Federation Passive Requestor Profi le protocol. With it, cloud-based applications can use on-premises AD DS user credentials to authenticate by using standard protocols and SAML tokens.</li>
 	<li>During synchronization, you can choose whether hashes of user passwords are synchronized, as well. If the password hashes are synchronized, the target directory can carry out authentications without the involvement of the original directory. Otherwise, the actual authentication operations are passed back to the original directory.</li>
 	<li>NOTE ERROR: A CONSTRAINT VIOLATION HAS OCCURRED
The user who runs the configuration wizard needs to be a member of the FIMSync-Admins group, you must log off and log on again for it to take effect. Otherwise, you might
receive the error message “a constraint violation has occurred” during configuration.</li>
 	<li>NOTE AZURE TRUST CENTER
Azure Trust Center provides valuable information regarding Azure’s security, privacy,
and compliance practices. For more information, go to <a href="http://azure.microsoft.com/en-us/support/trust-center/" target="_blank">http://azure.microsoft.com/en-us/support/trust-center/</a>.</li>
 	<li>StorSimple uses AES-256 with Cipher Block Chaining (CBC), which is the strongest commercially available encryption.</li>
 	<li>SQL Server Transparent Data Encryption (TDE) provides protection for at-rest data by
performing real-time I/O encryption and decryption of the data and log files. With TDE, developers can encrypt data by using AES and 3DES encryption algorithms without application changes. TDE provides protection over physical or logical breaches when underlying file systems are compromised and data files are exposed.</li>
 	<li>For a more granular encryption, you can use SQL Server Column-Level Encryption (CLE). CLE ensures that data remains encrypted until it is used. When a data page is loaded in memory, sensitive data is decrypted only when SQL Server is processing it. However, using CLE has a couple of downsides. First, applications need to be changed to invoke encryption/decryption. Second, there could be performance impacts not only because of the extra processing time, but also the negative effects on query optimizations.</li>
 	<li>In addition, Azure Storage also supports URL-based access with Shared Access Signatures (SAS). Using SAS, you can grant direct access to storage entities (containers, Blobs, queues, tables, or table rows) with a specified set of permissions during a specified time frame.</li>
 	<li>In addition, you can use Stored Access Policy (SAP) to manage SASs in bulk. For example, you can change the access window, or deny access to a group of SASs, using an SAP.</li>
 	<li>Server. Because Azure SQL Database instances are not domain-joined, only standard SQL authentication by user ID and password is supported. For SQL Server instances running on Azure Virtual Machines, they can also authenticate by using Kerberos tokens if the virtual machines (VMs) are domain-joined.</li>
 	<li>An ACL rule defines whether access should be allowed or denied from a certain network
address range. You can define either “Allow” rules or “Deny” rules. Allow rules permit access from the given IP range, and they deny accesses from any other IPs. Conversely, Deny rules allow accesses from all IP ranges except for the one specified in the rule.</li>
 	<li>Each Azure subscription can have 100 NSG rules, and each NSG rule can contain up to 200 rules, which can be either inbound rules or outbound rules.</li>
 	<li>The difference between an ACL and an NSG is that an ACL is applied to traffic through an
endpoint, whereas an NSG is applied to all traffic to and from a VM. You cannot apply NSG and ACL to the same VM.</li>
 	<li>Each SQL Database has three database replicas running at any given time. If the primary
replica fails, SQL Database automatically fails-over to a secondary replica to ensure continuous data access. If a replica fails, a new one is automatically created to always maintain three replicas.</li>
 	<li>SQL Database provides an automatic “Point in Time Restore” feature, which automatically backs up your SQL database and retains the backups for 7 days for Basic tier, 14 days for Standard tier, and 35 days for Premium tier. This feature is active by default and it incurs no additional charges, except when you use the restore capability.</li>
 	<li>Another fault tolerance feature you get automatically is “geo-restore.” When backing
up your databases, Azure stores the most recent daily backup of your database in a different geographical location. In the event of a large-scale outage in a region, your data can be restored within 24 hours from another region.</li>
 	<li>Standard geo-replication (available to Standard and Premium-tier users) creates additional secondary replicas in a different region than the region in which your database is deployed (this region is called a paired region). These replicas are offline, but they can be brought online for an application to fail-over to them in the event of a datacenter disruption. Active geo-replication (available to Premium-tier users) provides the most rapid recovery time by keeping four geo-replicated live secondaries.</li>
 	<li>EXAM TIP
Azure Backup, StorSimple, and Azure Site Recovery provide tiered protection over your
business data. Backup works at the fi le and folder level, StoreSimple works at the volume
level, and Site Recovery works at the VM and topology level. They can work separately and they can work together. When preparing for the exam, you should keep their relationships in mind to help you identify appropriate technologies to use for different scenarios. Knowing their differences will also help you to easily eliminate some of the choices when asked specific questions.</li>
 	<li>EXAM TIP
Encryption, replication, and appropriate access control are three key technologies for data
security. All of the tools and services mentioned in this objective revolve around these
three elements. If you learn best by hands-on practice, you can try to set up Backup using
a client machine fairly easily following the example scenario in this section. To try out Site
Recovery with minimum confi guration, you can use a Hyper-V replica set as the primary
site and back it up to Azure. With this confi guration, you can walk through the major Site
Recovery workflows with minimum hardware requirements. It’s hard to set up StorSimple
yourself because special hardware is needed.</li>
 	<li>NOTE EXISTING SUBSCRIPTION ADMINISTRATORS AND CO-ADMINISTRATORS
Existing Azure subscription administrators and co-administrators are automatically assigned to the Owner role in this access control model.</li>
 	<li>NOTE SECURITY QUESTIONS
Security questions are less secure than phone or email-based password reset methods. You should avoid using security questions alone.</li>
 	<li>Not all SaaS applications support federated authentications with Azure AD. To provide a
smooth SSO experience, Azure AD Access Panel can securely save user credentials and automatically complete the sign-in process on the user’s behalf.</li>
 	<li>Azure AD helps administrators to discover what SaaS services are being used in the enterprise via the Cloud App Discovery (preview) service. By deploying agents on enterprise devices, Cloud App Discovery is capable of discovering what services are being used as well as their usage patterns. The results provide a great starting point for administrators to begin consolidating application access controls into the Azure AD Access Panel or to close down access to certain services.</li>
</ul>
<div>
<h3>Chapter 03: Design an application storage and data access strategy</h3>
<ul>
 	<li>Walmart handles over 1 million transactions per hour, which are all stored in databases.
More than 5 billion people are calling, texting, tweeting, and browsing on mobile phones worldwide. Facebook has 100 TB of data uploaded daily. Today, there is a projected 40 percent yearly growth in data generated globally, whereas corporate spending on IT is only growing at 5 percent per year. (You can fi nd this data and more Big-Data statistics at <a href="http://wikibon.org/blog/big-data-statistics/" target="_blank">http://wikibon.org/blog/big-data-statistics/</a>.)</li>
 	<li>You can set up multiple Storage accounts, but each is limited to 20,000 input/output operations per second (IOPS) and a total of 500 TB of storage.</li>
 	<li>Block blobs can store up to 200 GB of data and are optimized for streaming. This is the type by which most blobs are stored.</li>
 	<li>Page blobs can store up to 1 TB and are optimized for random read/write operations. They provide the ability to write to a range of bytes in a Blob. Virtual Drives in Azure Virtual Machines use page blobs because they are accessed randomly.</li>
 	<li>File storage is a shared storage that uses the standard Server Message Block (SMB) 2.1
protocol.</li>
 	<li>There is no limit to the number of Azure resources that can connect to the File storage and access the file share.</li>
 	<li>EXAM TIP
Know the various storage types and their uses. For example, many times you can use
Queues to decouple components of a system.</li>
 	<li>You can create databases in SQL Database up to 500 GB in size. There are a few things that are not available in SQL Database: There is no SQL Agent, SQL Profiler, Native Encryption, Service Broker, Common Language Runtime (CLR), Use command, distributed transactions, or distributed views. If you need any of these things or a larger database size for the solution, you will need to look at running SQL Server in a VM (IaaS).</li>
 	<li>EXAM TIP
Azure might update to change feature availability. The exam is updated over time, as well,
to refl ect these changes. However, because of the way Azure is steadily being updated, the newest features might not be on the exams.</li>
 	<li>SQL Database employs multiple security strategies. The first is an allow list of all of the IP
addresses that are allowed to access the database. If the server that you are on is not on the list—even if you have a valid user name and password to the database—access will be denied.</li>
 	<li>By default, SQL Database also requires that you use Secure Sockets Layer (SSL) encryption at all times.</li>
 	<li>Azure Storage does provide security for the data that is stored within it. The fi rst level of
security is that you must use an HTTPS connection to access every service in Azure Storage.</li>
 	<li>The second level of security is that to access any of the various types of data, you need to have the account name and the Access Keys. This means that without both, you cannot access the data.</li>
 	<li>Azure Storage can also use a Shared Access Signature (SAS) to limit the time and permissions that a user has to a storage account.</li>
 	<li>Azure Storage also can use a Shared Access Policy to set the access to the storage account. This is similar to SAS, but it gives you the ability to implement an online policy that can be changed to shut down access event if people have a valid key. This can be useful if you’re giving access outside your company which might later need to be removed. A Table, Queue, or Blob container can have up to five access policies.</li>
 	<li>MORE INFO AZURE SQL DATABASE SECURITY
You can learn more about Azure SQL Database security guidelines and limitations at <a href="http://msdn.microsoft.com/en-us/library/azure/ff394108.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/ff394108.aspx</a>. You can learn more about Azure Shared Access Storage at <a href="http://azure.microsoft.com/en-us/documentation/articles/storagedotnet-shared-access-signature-part-1/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/storagedotnet-shared-access-signature-part-1/</a>.</li>
 	<li>The performance levels define how many Database Throughput Units (DTUs) the level can support. DTUs are based on a blended measure of CPU, memory, reads, and writes.</li>
 	<li>Each service tier also has a maximum allowed database size: 2 GB for Basic, 250 GB for Standard, and 500 GB for the Premium tier.</li>
 	<li>EXAM TIP
Performance levels of the database are important to a company, and the ability to change
this at times is equally important. The limits of each level of SQL Database can help the
architect to determine the minimum level needed to satisfy those needs.</li>
 	<li>Mobile Services also includes the idea of a soft delete for data. Soft delete adds a _deleted
field to the data being saved; then, when the data is deleted, it still exists in the storage, but it’s marked as deleted. This can be useful for systems in which the data is taken out of general use, but the fact that it existed in the first place is still needed.</li>
 	<li>Mobile Services that are running at a Basic or Standard level also operate under an SLA
that specifies 99.9 percent availability.</li>
 	<li>MORE INFO MOBILE SERVICES
You can learn more about Azure Mobile Services at <a href="http://azure.microsoft.com/en-us/documentation/services/mobile-services/" target="_blank">http://azure.microsoft.com/en-us/documentation/services/mobile-services/</a>.</li>
 	<li>MORE INFO CROSS-PLATFORM SUPPORT
You can learn more about Azure Mobile Services in iOS apps at <a href="http://azure.microsoft.com/en-us/documentation/articles/mobile-services-android-how-to-use-client-library/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/mobile-services-android-how-to-use-client-library/</a>. For more information about Azure Mobile Services in Android apps, go to <a href="http://azure.microsoft.com/en-us/documentation/articles/mobile-services-android-how-to-use-client-library/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/mobile-services-android-how-to-use-client-library/</a>.</li>
 	<li>You will need to change the project to build for x86, x64, or ARM. The Any CPU option is not supported by the SQLite runtime.</li>
 	<li>MORE INFO OFFLINE SYNC
You can learn more about Mobile Services Offline Sync at <a href="http://azure.microsoft.com/en-us/documentation/articles/mobile-services-windows-phone-get-started-offlline-data/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/mobile-services-windows-phone-get-started-offlline-data/</a>.</li>
 	<li>MORE INFO USER AUTHENTICATION
You can learn more about Azure Mobile Services user authentication at <a href="http://azure.microsoft.com/en-us/documentation/articles/mobile-services-how-to-use-server-scripts/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/mobile-services-how-to-use-server-scripts/</a>.</li>
 	<li>MORE INFO USER AUTHENTICATION
You can learn more about Azure Mobile Services user authentication at <a href="http://azure.microsoft.com/en-us/documentation/articles/mobile-services-windows-phone-get-started-users/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/mobile-services-windows-phone-get-started-users/</a>.</li>
 	<li>A key difference between push notification directly in Mobile Services and using a notification hub is scale. Notification hubs are optimized to broadcast millions of push notifications within minutes. Mobile Services push notification is good for simple event-driven events, such as notifying a participant in a game that it is her turn.</li>
 	<li>Another use of push notifications would be to create a secure notification system. For
example, suppose that an application needs to send some sensitive data to a user. Raw data could be pushed to the user and the application on the device could use that raw data to pull sensitive data down over a secure connection. This way the sensitive data does not need to go through the PNS, because the PNS might not support secure connections. Having this type of trigger to inform the application that there is new data to retrieve is the best practice instead of adding the data directly into the payload.</li>
 	<li>MORE INFO PUSH NOTIFICATION
You can learn more about Azure Mobile Services push notification at <a href="http://azure.microsoft.com/en-us/documentation/articles/mobile-services-javascript-backend-windows-phone-get-started-push/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/mobile-services-javascript-backend-windows-phone-get-started-push/</a>.</li>
 	<li>MORE INFO ENHANCED PUSH
You can learn more about getting started with notification hubs at <a href="http://azure.microsoft.com/en-us/documentation/articles/partner-xamarin-notification-hubs-android-get-started/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/partner-xamarin-notification-hubs-android-get-started/</a>.</li>
 	<li>MORE INFO CUSTOM WEB API
You can learn more about the custom Web APIs using SQL Server at <a href="http://azure.microsoft.com/en-us/documentation/articles/web-sites-dotnet-rest-service-aspnet-api-sql-database/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/web-sites-dotnet-rest-service-aspnet-api-sql-database/</a>.</li>
 	<li>Basic and Standard-level web hosting plans can scale the website to multiple instances.
This is referred to as scaling out. Basic instances can be scaled to three instances, whereas Standard instances can be scaled to ten instances.</li>
 	<li>The metrics that you can use to scale Azure websites are CPU, Memory Percentage, Disk Queue, Length, HTTP Queue Length, Data In, and Data Out.</li>
 	<li>The Over Past setting is used to alert that the metric is over the threshold for more than a given number of minutes. The Cool Down value is the number of minutes to wait before applying any other scaling rules.</li>
 	<li>If the program or script needs to have additional files, such as data files or dynamic-link
libraries (DLLs), zip all of the files that are needed to run the program and then upload the zip file.</li>
 	<li>For continuous tasks, it is recommended that you turn on the Always On feature on the
Confi gure page for the website. This feature, available in Basic and Standard mode, prevents websites from being unloaded, even if they have been idle for some time. If your website is always loaded, your continuously running task might run more reliably.</li>
 	<li>WebJobs are deployed in the App_Data/jobs folder under the root of the website. From there, WebJob will be in a folder using the name of the WebJob, in either a continuous or triggered folder based on how the WebJob is set up.</li>
 	<li>Using BizTalk API Apps Hybrid Connections, you can make connections to on-premises resources that use static TCP ports, such as SQL Server, MySQL, Web APIs, and most web services. As of this writing, Hybrid Connections does not support services that use dynamic ports, such as SQL Express.</li>
 	<li>Administrators also do not need to make changes to incoming firewall rules, because the traffic for the Hybrid Connections requires only outbound TCP and HTTP connectivity.</li>
 	<li>EXAM TIP
You can set up a Hybrid Data Connector in BizTalk API Apps to connect a mobile service or website to a database that is on-premises.</li>
 	<li>MORE INFO HYBRID CONNECTIONS
You can learn more about the .NET on-premises/cloud hybrid application using Service Bus Relay at <a href="http://azure.microsoft.com/en-us/documentation/articles/cloud-services-dotnet-hybrid-app-using-service-bus-relay/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/cloud-services-dotnet-hybrid-app-using-service-bus-relay/</a>.</li>
 	<li>MORE INFO WEB APPS VPN
You can learn more about Web Apps Virtual Network integration at <a href="http://azure.microsoft.com/blog/2014/09/15/azure-websites-virtual-network-integration/" target="_blank">http://azure.microsoft.com/blog/2014/09/15/azure-websites-virtual-network-integration/</a>.</li>
 	<li>MORE INFO CONNECTING TO A DOMAIN
You can learn more about the how to join web and worker roles to a domain in the same Virtual Network at <a href="https://code.msdn.microsoft.com/windowsazure/How-to-join-web-and-worker-3a72db70" target="_blank">https://code.msdn.microsoft.com/windowsazure/How-to-join-web-and-worker-3a72db70</a>. To learn more about the domain joining Virtual Machines, go to <a href="https://gallery.technet.microsoft.com/scriptcenter/Domain-Joining-Windows-fefe7039" target="_blank">https://gallery.technet.microsoft.com/scriptcenter/Domain-Joining-Windows-fefe7039</a>.</li>
 	<li>AES Clear Key dynamic encryption is a basic “lite” encryption. This is done on-the-wire and is widely known as symmetric AES encryption.</li>
</ul>
<div>
<h3>Chapter 04: Design an advanced application</h3>
<ul>
 	<li>You often hear about how the cloud is scalable and available. However, this doesn’t mean that an application automatically will be available and scalable on the cloud. You need to design applications to take advantage of these offerings.</li>
 	<li>MORE INFO BIG COMPUTE AND BIG DATA
Big Compute and Big Data are often mentioned together, and the boundary between the two isn’t always clear. Indeed, many applications need to perform complex operations on large amounts of data. To distinguish the two, you need to remember that they have different focus. Big Compute is concerned with using raw computing power to perform complex computing tasks, whereas Big Data is about an entire data pipeline that includes data ingress, transform, storage, analysis, and presentation.</li>
 	<li>NOTE USING A DEPLOYMENT SCRIPT
You can deploy an HPC cluster by manually preparing and configuring the nodes. However, because deploying such clusters involves provisioning and configuring a large number of resources, it is recommended that you instead use automated scripts. There’s an HPC Pack IaaS Deployment Script, which you can download from the Microsoft Download Center at <a href="http://www.microsoft.com/en-us/download/details.aspx?id=44949" target="_blank">http://www.microsoft.com/en-us/download/details.aspx?id=44949</a>.</li>
 	<li>Premium storage drives provide up to 5,000 I/O operations per second (IOPS) with 200 megabits per second (Mbps) throughput. With the 16-core DS series VMs, you can attach up to 32 TB of data disks and achieve more than 50,000 IOPS.</li>
 	<li>NOTE DIFFERENCES BETWEEN D-SERIES AND DS-SERIES
D-series is designed for applications with high demand in compute power and temporary drive performance. D-series uses SSDs as temporary drives. DS-series is designed for I/O intensive workloads. DS-series uses SSDs for both hosting VM drives and local caches.</li>
 	<li>You have two ways to programmatically interact with Batch: a higher-level Batch Apps API,
or a lower-level Batch API. When using the Batch API, you are directly scheduling computational tasks onto a pool of resources. You need to manage task scheduling and execution yourself. On the other hand, with Batch Apps API, you can wrap an existing application and run it as parallel tasks. Batch will handle all the details for you, such as task scheduling, managing execution pipelines, and partitioning workloads.</li>
 	<li>The two most common deployment strategies are homogeneous instances and primary–secondary instances.</li>
 	<li>HOMOGENEOUS INSTANCES
In such a multi-instance deployment, all instances are identical. They often have similar processing power, and they are joined behind a load balancer, which distributes workloads evenly to them.</li>
 	<li>A practical challenge of using homogeneous instances is session state management. Because services’ requests are distributed by the load balancer, requests within a user session are likely to be routed to different instances.</li>
 	<li>NOTE STATELESS VERSUS STATE-FUL
Using stateless instances is defi nitely not the only way to design scalable applications. In many cases, state-ful instances have preferable characteristics in terms of simplicity and performance, and there are fascinating programming models such as the Actor pattern to help you to write scalable, distributed applications. Further discussion on the Actor pattern is beyond the scope of this book.</li>
 	<li>PRIMARY–SECONDARY INSTANCES
A primary–secondary deployment designates a primary instance that handles all incoming
requests, with one or more secondary instances as active backups. When the primary instance fails, a secondary instance is promoted to primary to handle requests. The original primary instance is repaired and brought back online as a new secondary.</li>
 	<li>The downside of scaling out is that the application must be designed to accommodate it, which might call for architectural changes to legacy applications.</li>
 	<li>EXAM TIP
We intentionally left out many details so that we could focus on architecture topics in this
chapter. However, sometimes the exam can be very specific. You might be asked about
Azure Service Definition Schema, which is commonly referred to as service definition file
(see <a href="https://msdn.microsoft.com/en-us/library/azure/ee758711.aspx" target="_blank">https://msdn.microsoft.com/en-us/library/azure/ee758711.aspx</a>). This is an XML file
with a .csdef extension. It defines the service model of an application, including roles,
endpoints, and configurations. Similarly, there is Azure Service Configuration Schema, or as it’s more commonly known, service configuration file. This is another XML file with a .cscfg extension that supplies configuration values for different environments (see <a href="https://msdn.microsoft.com/en-us/library/azure/ee758710.aspx" target="_blank">https://msdn.microsoft.com/en-us/library/azure/ee758710.aspx</a>). When you create a new Cloud Services project, you can observe both files in the project folder. Follow the attached links to familiarize yourself with these two schemas in case some specific schema questions are asked.</li>
 	<li>For many transactional applications, strong consistency is highly desirable because many
parties operate based on the universal truth of the data. On the other hand, for reading heavy applications, eventual consistency is often desirable for improved performance.</li>
 	<li>If your application does a large amount of writes, pessimistic concurrency usually provides
a better performance, because optimistic concurrency will lead to many failed operations in
this case. On the other hand, you can use optimistic concurrency when your application has mostly reads and fewer writes.</li>
 	<li>NOTE ADOPTING MULTITENANCY
Adapting a single-tenant application for multitenancy is a serious architectural change that should not be taken lightly. Such change often needs modifications across all application layers, so it’s a high-risk change. More important, multitenancy often has profound impacts on business processes, such as sales strategy, support workflow, and version managements. For example, because all customers are moved to new versions at the same time, a customer can’t elect to keep using a known working version to reduce the risk of breaking changes. Another example is that at business level, the company often needs to adapt from licensing or installation-based sales to subscription-based sales, which deeply affects sales prediction, cash flow management, and even sales team building.</li>
 	<li>EXAM TIP
This chapter views some of the Azure services from the perspective of real-life scenarios.
However, this is not an exhaustive list of all Azure services. Azure services are constantly
evolving, so it’s impossible to put an up-to-date service list in print. The easiest way to get
an overview of all available Azure services is to go to http://azure.microsoft.com. On the
home page, click the Features link, which displays a current list of all Azure services organized in different categories. Clicking each of the services opens a service overview page that provides several bullet points, highlighting the most important features of the service. Going through these pages is a great way to get a general understanding of Azure services.</li>
 	<li>DocumentDB is optimized for frequent writes so that you can push documents into DocumentDB quickly and update documents as frequently as needed. And, it automatically maintains all indexes for you.</li>
 	<li>In addition to full-text search, Search also affords advanced search behaviors such as autosuggestion, autocompletion, faceted searches, results highlighting, spell corrections,
and geospatial searches.</li>
 	<li>CDN improves site performance in two ways: First, it provides faster response time by serving contents from locations closest to the end user, and second, it removes a large portion of content serving workloads from the service servers.</li>
 	<li>An event hub can connect to more than one million data producers, with over 1 Gbps aggregated throughput. You can send data to Event Hubs through either HTTP or AMQP.</li>
 	<li>Stream Analytics takes in millions of events per second, and it transforms, augments, and correlates data as needed as it works through streams of data. In addition, it can detect patterns and abnormalities in streaming data. Finally, it can correlate streaming data with reference data.</li>
 	<li>EXAM TIP
The key to designing a complex system is to determine how the system should be separated into individual components. More components often bring more flexibility in system design and more agility in development process. However, the increasing number of components also means more complex communication patterns among components. When choosing which services to use in your system, you need to evaluate the services to ensure that they can indeed provide, or can be extended to provide, solutions to the specific problems you need to address. Although some exam questions might ask you to do a simple problem-to-service match, you need to keep in mind that in reality the decision process is often much more complex.</li>
</ul>
<div>
<h3>Chapter 05: Design Web Apps</h3>
<ul>
 	<li>The DOM Explorer includes a pane that shows the styles, computed data, layout, events, and changes to help you to determine the source of any issues with the website.</li>
 	<li>By default, the Site Control Manager shows currently running processes, system information, application settings, connection strings, environment variables, PATH, HTTP headers, and server variables. Site Control Manager also has the ability to launch a remote CMD or PowerShell window so that you can perform commands directly.</li>
 	<li>MORE INFO REMOTE WEBSITE DEBUGGING
You can learn more about remotely debugging Azure websites at <a href="http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/" target="_blank">http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/</a>.</li>
 	<li>To support older ASP.NET websites, App Services Web Apps also supports .NET 3.5 as well as .NET 4.5. This makes it possible for companies that have not upgraded to the newest version of .NET to still use and transfer websites to Azure.</li>
 	<li>The .cscfg file defines the number of instances and the configuration settings for the service to be uploaded. If remote desktop is turned on, the logon information is stored in the .cscfg file, as well. The .csdef file defines the name of the Web Role Service and the EndPoints for the service.</li>
 	<li>EXAM TIP
Until recently, App Service Web Apps was called Azure Websites, and that might be what
you see on the exam or in Visual Studio if you have an older Azure SDK installed.</li>
 	<li>MORE INFO WEB APPS, CLOUD SERVICES, AND VIRTUAL MACHINES
You can learn more about all three services at <a href="http://azure.microsoft.com/en-us/documentation/articles/choose-web-site-cloud-service-vm/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/choose-web-site-cloud-service-vm/</a>.</li>
 	<li>EXAM TIP
Web Apps and Websites are the same thing. The new name is what is used in the management portal and in the latest Azure SDK for Visual Studio.</li>
 	<li>Site Extensions is a feature of App Service Web Apps with which you can create and deploy custom administrator functionality.</li>
 	<li>Every web application has its own Site Control Manager that you use for administration and debugging. This is automatically created and available for all websites.</li>
 	<li>MORE INFO WRITING SITE EXTENSIONS
You can learn more about writing your own site extensions at <a href="http://blog.azure.com/2014/09/09/writing-a-site-extension-for-azure-websites/" target="_blank">http://blog.azure.com/2014/09/09/writing-a-site-extension-for-azure-websites/</a>.</li>
 	<li>MORE INFO CREATING DEPLOYMENT PACKAGES
You can learn more about web deployment packages at <a href="https://msdn.microsoft.com/en-us/library/dd465323(v=vs.110).aspx" target="_blank">https://msdn.microsoft.com/en-us/library/dd465323(v=vs.110).aspx</a>.</li>
 	<li>If an App Service Plan is changed to a different pricing tier, all of the websites and other App Services that are under that plan are moved to the new pricing tier, as well. In addition, the scaling and autoscaling for all of the services can be set together.</li>
 	<li>MORE INFO APP SERVICE PLAN
You can learn more about App Service Plan at <a href="http://azure.microsoft.com/en-us/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/</a>.</li>
 	<li>EXAM TIP
Keep in mind that App Hosting Plan in now named App Service Plan. You might see it
either way on the exam.</li>
 	<li>The benefit of using a deployment slot is that you are not uploading to the live site; instead, you’re uploading to a separate deployment slot. You can test the website in the deployment slot with it connected to either a test or production database to verify that everything is in place for the update to a new version of the website.</li>
 	<li>One feature that is available in the Preview Management Portal is that you can set the
connection strings and app settings to be sticky with the slot for which they are defi ned. This way, a test site can use a connection string that points to a test database instead of the live database. When the test site is swapped into production, it will use the connection string that is set up to be used only in production.</li>
 	<li>MORE INFO STAGING ENVIRONMENTS FOR WEB APPS
You can learn more about staging environments for Web Apps at <a href="http://azure.microsoft.com/en-us/documentation/articles/web-sites-staged-publishing/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/web-sites-staged-publishing/</a>.</li>
 	<li>MORE INFO RESOURCE GROUPS
You can learn more about resource groups at <a href="http://azure.microsoft.com/en-us/documentation/articles/azure-preview-portal-using-resource-groups/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/azure-preview-portal-using-resource-groups/</a>.</li>
 	<li>MORE INFO WEB DEPLOY
You can learn more about Web Deploy at <a href="http://www.iis.net/downloads/microsoft/web-deploy" target="_blank">http://www.iis.net/downloads/microsoft/web-deploy</a>.</li>
 	<li>You can manually scale-out Web Apps running at the Basic tier and above. Basic tier
can scale-out to three instances, Standard can scale-out to 10 instances, and Premium can scale-out to 20 instances, subject to availability.</li>
 	<li>SQL Database offers a scaling feature called Elastic Scale. You can scale databases horizontally to shard the database into multiple databases based on the data. Sharding a database means to split it and partition the different parts to multiple drives.</li>
 	<li>MORE INFO ELASTIC SCALE
You can learn more about Elastic Scale at <a href="http://azure.microsoft.com/en-us/documentation/articles/sql-database-elastic-scale-introduction/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/sql-database-elastic-scale-introduction/</a>.</li>
 	<li>A feature of the managed SQL Database system is SQL Sync. You can use this to set a time interval at which the database synchronizes its data to one of more other databases. You also can use this feature to synchronize data to an on-premises SQL Server database. SQL Sync is not a replacement for actual data replication, because it is not being run against the transactions, but it does move the data to where it needs to go.</li>
 	<li>Geo-replication sets up replica databases on other SQL Servers or in other datacenters that can be used in a disaster recovery scenario. With the Standard tier, you can configure an offline secondary. This means that the database will be replicated, but it is not readable. To create a readable backup, you need to use the Premium tier. With the Premium tier, you can create up to four readable backups.</li>
 	<li>MORE INFO GEO-REPLICATION FOR SQL DATABASE
You can learn more about geo-replication for SQL Databases at <a href="https://msdn.microsoft.com/en-us/library/azure/dn741339.aspx" target="_blank">https://msdn.microsoft.com/en-us/library/azure/dn741339.aspx</a>.</li>
 	<li>The Premium tier for Web Apps provides up to 50 backups each day, whereas the Standard tier provides a single backup per day. When planning your backup strategy, you
need to determine how often backups are needed.</li>
 	<li>MORE INFO DISASTER RECOVERY
You can learn more about disaster recovery planning and strategies at <a href="http://blogs.msdn.com/b/rockyh/archive/2013/06/15/whitepaper-disaster-recovery-and-high-availability-forwindows-azure-applications.aspx" target="_blank">http://blogs.msdn.com/b/rockyh/archive/2013/06/15/whitepaper-disaster-recovery-and-high-availability-forwindows-azure-applications.aspx</a>.</li>
 	<li>A standard RDBMS system uses Transact-SQL (T-SQL) or maybe command-line interface (CLI) functions defined to get or manipulate data. For a NoSQL system, each one could have different ways of getting to the data</li>
 	<li>Many database administrators feel that using a stored procedure is the best method because they can fine-tune those procedures to optimize access to any needed data. Many NoSQL systems do not support the concept of a stored procedure for defining the commands to be used.</li>
 	<li>The managed SQL Database can only scale up to 500 GB for a single database;</li>
</ul>
<h3>Chapter 06: Design a management, monitoring, and business continuity strategy</h3>
<ul>
 	<li>EXAM TIP
A Cloud Distribution Point is a Configuration Manager Site System Role in the Cloud. By
using it, companies do not need to worry about size, performance, reliability, security, and
access from all around the world.</li>
 	<li>EXAM TIP
The PowerShell Deployment Toolkit is the fastest and easiest way to deploy all or most
components of System Center.</li>
 	<li>There are many architectural considerations when designing a hybrid management solution with System Center. Most important is authentication and the bandwidth needed for the volume of data moving between systems.</li>
 	<li>Your options are to either use domain authentication with a VPN connection between Azure and your on-premises systems or public-key infrastructure (PKI) computer certificates with Internet Protocol Security (IPSec).</li>
 	<li>Even if you do have a VPN between your networks, you might consider setting up IPSec and certifi cates for authentication to increase the security posture of those communications.</li>
 	<li>You should consider the amount of data being backed up and how long it will take to back up changes (also known as the backup window). Based on the bandwidth you have available, you should determine that you have enough capacity to perform the daily, weekly, or monthly backups. You will want to verify that you have enough performance on your Internet connection to handle the backup &amp; restore load without detracting from other critical services.</li>
 	<li>REAL WORLD BANDWIDTH PERFORMANCE BOTTLENECKS
Systems designed without proper consideration of the bandwidth needs of all systems communications—including backup, restore and replication, as well as users, servers, and other services connecting to cloud resources—often create bandwidth bottlenecks. It is important to evaluate all communications at the busiest time of day and year to ensure that you have all data transfers covered. Not doing so will end up costing money, time, and aggravation to fix it later on.</li>
 	<li>EXAM TIP
You can use Azure Site Recovery to manage replication of a multisite organization for which systems from one site are replicated to another site. In event of a site failure, Site Recovery can orchestrate the recovery of the systems on the secondary or replica site. You also can use Azure as a replica site and confi gure it to be the failover destination.</li>
 	<li>EXAM TIP
Using Azure with System Center Data Protection Manager to store offsite data in Azure can significantly decrease cost, complexity, and restore window time for data recovery operations. Even without Data Protection Manager, With Azure, you will still realize cost savings and benefit from a shorter restore window.</li>
 	<li>Most Azure services use certificate-based authentication by default, so if you are not already comfortable with Private/Public Key authentication, you could benefit from digging into it a bit. You can find more on creating and uploading a management certificate for Azure at <a href="https://msdn.microsoft.com/library/azure/gg551722.aspx" target="_blank">https://msdn.microsoft.com/library/azure/gg551722.aspx</a>.</li>
 	<li>Each of the computer agents would need to connect to the gateway which would require two things. First, you would need to allow traffic out of the agent machine on 5723 and into the gateway machine by opening the firewall ports and endpoints. By default, outbound traffic is allowed, but inbound traffic to the gateway will need to be configured. Second, there must be authentication done between the machines, which, in this case, is done by a certificate.</li>
 	<li>System Center Operations Manager uses Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString to connect to the Azure SDK. The connection string for Windows Azure Diagnostics must be specified in the service configuration file (.cscfg)</li>
 	<li>NOTE ADDING MORE PERFORMANCE COUNTERS FOR CLOUD SERVICES
If you use verbose monitoring, you can add more performance counters at the cloud service role instance startup through a diagnostics configuration file. To be able to monitor these metrics in the management portal, you must add the performance counters before you configure verbose monitoring. For more information go to <a href="http://azure.microsoft.com/documentation/articles/cloud-services-dotnet-diagnostics/" target="_blank">http://azure.microsoft.com/documentation/articles/cloud-services-dotnet-diagnostics/</a>.</li>
 	<li>EXAM TIP
Global Service Monitor is an Azure cloud service used to monitor availability of a public
website from multiple external points.</li>
 	<li>Application Insights gives developers deep analysis on what is going on inside their application, making it possible for them to pinpoint problems introduced as a result of application changes. This is a feature that came out of the Application Performance Monitoring (APM) feature (from AviCode acquisition) in System Center Operations Manager 2012 R2.</li>
 	<li>You can have a maximum of 20 update domains per role service; the default is set to 5 per service.</li>
 	<li>Here are some questions that you need to consider when planning:
<ul>
 	<li>What is an acceptable amount of data loss? How many minutes, hours, or days of data can your business afford to lose in case of a disaster? The answer to this will determine your Recovery Point Objective.</li>
 	<li>How long you are prepared to be down before the data and services are back online
after a disaster? This is known as Recovery Time Objective.</li>
 	<li>Recovery Point Objective (RPO) RPO is the target maximum length of time that data loss can occur during a disaster—how many seconds, minutes, hours, or days, you can afford to lose data. This can be, and usually is, different for different types of data. From a planning standpoint, this is the amount of data (in time) that can be lost due to a disaster.</li>
 	<li>Recovery Time Objective (RTO) This is the amount of time that systems can be unavailable in the event of a disaster before unacceptable business loss occurs. From a planning standpoint, systems must be restored to functional levels within the RTO.</li>
</ul>
</li>
 	<li>EXAM TIP
RPO is the amount of data that can be lost (in time)—it is the amount of time between backup, replication, or synchronization. It answers the question, “What is an acceptable amount of data loss?” It is usually much smaller than RTO. RTO is how long it takes to restore services after a disaster. It answers the question, “How long will it take to get service back up?”</li>
 	<li>If your RPO is short (minutes), you need to design high availability for services. If your RTO is short, you will likely need to use multiple geographies and synchronize your data so that the systems can be brought up quickly.</li>
 	<li>EXAM TIP
An asynchronous operation is one that transpires sequentially: fi rst one action, and then another. The operations do not take place simultaneously. This type of processing means that there is a time gap between the fi rst operation and the second. An example would be writing data to primary and secondary storage. First data is written to the primary;
data destined for the secondary is queued and must wait until the write operation to the primary is complete.</li>
 	<li>EXAM TIP
Synchronous means that operations are carried out at the same time (think of this as parallel processing). With this type of processing, there is no time gap between the first process and the second process. Both operations take place simultaeously.</li>
 	<li>EXAM TIP
You should learn the Azure service SLA table. At the very least, the Azure service and the
Azure SLA for that service will be needed for the exam.</li>
 	<li>MORE INFO AZURE SLA TABLE
For more information on SLAs, go to <a href="http://go.microsoft.com/fwlink/?LinkId=309059" target="_blank">http://go.microsoft.com/fwlink/?LinkId=309059</a>.</li>
 	<li>SQL Server AlwaysOn Availability Group is a capability built in to SQL Server that only
works when SQL is configured properly and running in a cluster of VMs in Azure. To set up
this configuration, you need a three-node cluster of servers, and then configure Windows
Server Failover Cluster (WSFC) using the three VMs. You can use more, but three is the minimum: one for the primary database, one for the replica database, and one for the quorum or witness. All three VMs should be in the same storage container and in the same Availability Set</li>
 	<li>Scaling-out adds machines with the same characteristics (CPU, memory, bandwidth) to relieve some of the load from the existing machines. Scaling-up means to add additional resources (CPU, memory, bandwidth) to an existing machine.</li>
 	<li>EXAM TIP
Sharding is when you split a database and partition the different parts of the database
across multiple drives. A shard is a single horizontal partition of the database.</li>
 	<li>For a more in-depth look at scaling, read Best Practices for the Design of Large-Scale Services on Azure Cloud Services at <a href="http://go.microsoft.com/fwlink/?LinkId=309060" target="_blank">http://go.microsoft.com/fwlink/?LinkId=309060</a>.</li>
 	<li>Because the replication is configured for the VM (instead of the host), a single Hyper-V host can replicate different VMs to different replica hosts. Communication is via HTTP. You can turn on encryption, if desired.</li>
 	<li>MORE INFO DISASTER RECOVERY USING ACTIVE GEO-REPLICATION
For additional information on disaster recovery using Active Geo-Replication, read Designing Cloud Solutions for Disaster Recovery Using Active Geo-Replication at <a href="https://msdn.microsoft.com/en-us/library/azure/dn741328.aspx" target="_blank">https://msdn.microsoft.com/en-us/library/azure/dn741328.aspx</a>.</li>
 	<li>MORE INFO HIGH AVAILABILITY AND DISASTER-RECOVERY FOR SQL SERVER
For additional information on high availability and disaster-recovery approaches for SQL Server in Azure VMs, read High Availability and Disaster Recovery for SQL Server in Azure Virtual Machines at <a href="https://msdn.microsoft.com/en-us/library/azure/jj870962.aspx" target="_blank">https://msdn.microsoft.com/en-us/library/azure/jj870962.aspx</a>.</li>
 	<li>There is no bandwidth cost to move data into (ingress) Azure. You pay for the instance plus the storage consumed. Your data is encrypted before it leaves your premises, and remains encrypted in Azure, and only you have the key.</li>
 	<li>One restriction is that data must be on an online local fixed disk, which must be an NTFS-formatted volume. Read-only volumes, network share volumes, and removable drives are not supported.</li>
 	<li>For VMs running in Azure, you can perform a snapshot of the Blob to capture the drives
kept in Blob storage in Azure. This works for both Windows and Linux machines. However,
to get the system state, the VM must be stopped or shut down.</li>
 	<li>EXAM TIP
When you create a recovery vault for Backup, use a different region than that of the servers and services you will be backing up. This will provide a level of protection against a
regional disaster such as the failure of an Azure datacenter or hurricane that can take out
an entire region including your on-premises datacenter.</li>
 	<li>EXAM TIP
If you choose Offline for your initial backup, you can save to a USB drive that can then be
shipped to Microsoft to import into to your storage account. You select the staging location
(USB or Network), Import Job Name, Azure Publish Settings File, Azure Subscription
ID, Azure Storage Account, and Azure Storage Container. Microsoft needs all of this to gain access to your account and storage and place the files where you want them.</li>
 	<li>NOTE BACKUP SIZE LIMITS
Backup imposes a limit of 1,700 GB of data per volume that that you can back up in one backup operation.</li>
 	<li>EXAM TIP
In the Azure PowerShell command, OB stands for Online Backup. If you get an Azure
PowerShell exam question on backup, make sure that your answer is using the Online
Backup or OB version of the command; for example:
<ul>
 	<li>Get-OBPolicy retrieves the current backup policy, which includes the schedule.</li>
 	<li>Start-OBBackup –Policy $policy –Force executes a Backup Now.</li>
</ul>
</li>
 	<li>To run Azure PowerShell modules for Online Backup, you must be running with Administrative permissions (elevated).</li>
 	<li>Data Protection Manager uses Changed Block Tracking to identify what blocks on a particular file have changed and only needs to transfer and store those blocks. However, when doing a restore, you can do point-in-time restore of an entire file. If that file is a Hyper-V VHD, Item Level Restore (ILR) allows you to restore individual files inside the VHD.</li>
 	<li>Remember, the number of recovery points can’t exceed 366, so you need to design your online recovery points (daily + weekly + monthly + yearly) to ensure that they do not exceed this limit. Data Protection Manager is a much more robust platform for backup than Azure Backup alone.</li>
 	<li>If you are running Data Protection Manager in an Azure Virtual Machine, you need to be aware that you are limited to 16 volumes on a drive. This will have a very significant effect on your ability to set many recovery points because recovery points are stored as volumes.</li>
 	<li>Another thing to consider as you design system backups that use Azure Storage is there is a 500 TB limit per storage account. Another key limitation to emphasize is that Data Protection Manager is for Microsoft workloads (with DPM 2012 R2 there is limited support for Linux if it is running in a VM).</li>
 	<li>MORE INFO ADDITIONAL INFORMATION ONLINE
For a more in-depth look at deploying Data Protection Manager backup and recovery for
business continuity go to <a href="https://technet.microsoft.com/en-us/library/dn621063.aspx" target="_blank">https://technet.microsoft.com/en-us/library/dn621063.aspx</a>.</li>
 	<li>EXAM TIP
StorSimple uses iSCSI protocol to link data storage. This means that the storage that is in
Azure is presented as locally attached iSCSI volumes.</li>
 	<li>You should use StorSimple when you want local storage that is very fast and scalable to give you seemingly limitless expansion into Azure. It is designed more for tiering data than for backup. It is great for storing file shares, when you want very fast access to files that are used regularly but want to take infrequently used data off the expensive internal storage and put it on cloud storage.</li>
 	<li>With StorSimple, it is not necessary to do a full system restore to begin using the data, so the RTO is greatly reduced. However, the data that can be backed up and restored is limited to Exchange, SharePoint, Hyper-V, or virtual hard drive data and files or file shares.</li>
 	<li>Data Protection Manager is best suited when live access to the data is not needed. It is a backup solution, not a local, real-time high-speed, high-resiliency storage solution like StorSimple. Data Protection Manager is better used for workloads with a higher RPO because some data loss is likely, depending on how the recovery points are configured. Data Protection Manager also gives you the ability to do tape archiving, whereas no such capability exists with StorSimple.</li>
 	<li>EXAM TIP
You can use either the Add-AzureAccount cmdlet or the Get-AzurePublishSettingsFile and
Import-AzurePublishSettingsFile cmdlets to authenticate Windows PowerShell to Azure.</li>
 	<li>IMPORTANT PUBLISH SETTINGS FILE AUTHENTICATION
The publishSettingsFile has certificate credentials embedded in it. After adding it to Windows PowerShell, you should delete it from your computer to prevent others from
gaining access to the file and gaining access to your Azure subscription.</li>
 	<li>EXAM TIP
Following is the Azure PowerShell command to retrieve the primary storage account:
$StorageAccountKey = Get-AzureStorageKey $StoreName | %{ $_.Primary }</li>
 	<li>EXAM TIP
You can fi nd Windows PowerShell workflows in the management portal. Go to the main
navigation, and then look in the Automation section.</li>
 	<li>The $Using: variable is required within the InlineScript to reference variables and parameters that are external to the InlineScript.</li>
 	<li>The best use-case for Desired State Configuration is if you want to ensure that newly
deployed servers configured a certain way. Another case is when you want to eliminate
configuration drift; that is, guarantee the servers maintain their desired configuration at all
times.</li>
</ul>
</div>
</div>
</div>
</div>
