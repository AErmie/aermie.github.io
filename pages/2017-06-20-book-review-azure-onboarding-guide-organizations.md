---
layout: page
title: Book Review: Azure Onboarding Guide for IT Organizations
date: 2017-06-20 13:19
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2017/06/AzureOnboardingGuideITOgs_BookCover.png"><img class="alignleft wp-image-30094 size-medium" src="/wp-content/uploads/2017/06/AzureOnboardingGuideITOgs_BookCover-300x145.png" alt="" width="300" height="145" /></a>Recently, I finished reading the <a href="https://www.google.ca/url?sa=t&amp;rct=j&amp;q=&amp;esrc=s&amp;source=web&amp;cd=1&amp;cad=rja&amp;uact=8&amp;ved=0ahUKEwitreLL0czUAhUL6oMKHRIkDzIQFghGMAA&amp;url=https%3A%2F%2Fazure.microsoft.com%2Fmediahandler%2Ffiles%2Fresourcefiles%2Fd8e7430c-8f62-4bbb-9ca2-f2bc877b48bd%2FAzure%2520Onboarding%2520Guide%2520for%2520IT%2520Organizations.pdf&amp;usg=AFQjCNFusGss0vNts3BTpWDrdRNjxTLecg&amp;sig2=bIXljrEAHxdrqE_UiGLw1w" target="_blank" rel="noopener">Azure Onboarding Guide for IT Organizations</a> eBook.

The chapters that I found most helpful were Chapter 3 “Azure Network Security” and Chapter 4 “Data and Storage Security”, hence the majority of my highlights are from these chapters.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 01: Introduction</h2>
<ul>
 	<li>None</li>
</ul>
<h2>Chapter 02: Moving to the Cloud</h2>
<ul>
 	<li>The six drivers for making the move to the cloud fall under two main categories: business drivers, including business growth, efficiency, and experience, and technology drivers, including agility, cost, and assurance.</li>
 	<li>Going to the cloud for assurance frees IT to be more strategic and passes these responsibilities to a provider that is typically better at handling them than your business is.</li>
 	<li>The external nature of cloud services may require an organization to rethink its IT service management and disaster recovery practices, as well as how given cloud services integrate with its existing in-house technology infrastructure. The pay-as-you-go cost model common with cloud services may entail changes to financial management practices and total cost of ownership calculations. Procurement processes may need to be adjusted to increase agility and effectively address the unique risks associated with cloud service, and new vendor management roles may need to be established and resourced to ensure ongoing compliance with contract terms.</li>
 	<li>Enterprises will achieve the best outcomes when their IT organizations serve as enablers, simplifying and accelerating business units’ adoption of cloud services.</li>
 	<li>this means that staff must have time to explore new technologies and that organizations may need to increase their investment in IT staff training.</li>
 	<li>Microsoft Azure Stack is a product that enables organizations to deliver Azure services from their own datacenter. It helps you build and deploy your applications the same way regardless of whether it runs on Azure or Azure Stack.</li>
 	<li>IaaS is one of the most common cloud deployment patterns to date. It eliminates the need for capital expense budgets and reduces the time between purchasing and deployment to almost nothing. In addition, it is most similar to how IT operates today.</li>
 	<li>Key questions that need to be answered are: Which applications could be moved? How could they be moved? How to prioritize? How does it affect the business?</li>
 	<li>It is important to create a well-attributed catalog of applications managed by IT.</li>
 	<li>attributes such as business criticality, amount of integrations points, performance requirements, etc.</li>
 	<li>You can think about those characteristics top-down or bottom-up. Top-down describes where each application should go to; bottom-up describes where it can go.</li>
 	<li>The top assessment first evaluates the security and compliance aspects. Then it assesses the complexity, interfaces, authentication, data structure, latency requirements, and other aspects of the application architecture. Next are operational requirements, service levels, maintenance windows, monitoring, and others.</li>
 	<li>The seasonality, required scalability, and elasticity of the application need to be considered and finally business continuity and resilience requirements that the application might have.</li>
 	<li>Analyzing the applications from a bottom-up perspective is aimed at providing a view into the eligibility, at a technical level of an application to migrate. Evaluated requirements are typically maximum memory, number of cores, operating system and data disk space, network interface cards, network and IP settings, load balancing, clustering, versions of operating systems, databases, middleware products, and web servers, among others.</li>
 	<li>Many enterprise organizations take a three-step approach to cloud adoption. The first priority is to take advantage of SaaS productive workloads such as Office 365. The second priority is to base new modern cloud applications on PaaS (Azure SQL databases, Azure Web Apps, Logic Apps, Mobile Apps, etc.).</li>
 	<li>The third priority is moving existing applications to IaaS virtual machines by using one of the two approaches:
<ul>
 	<li>Lift and Shift: Existing virtual machines are shifted to the cloud.</li>
 	<li>Build in the cloud: applications are prebuilt in Azure, and traditional methods are used to back up and restore data.</li>
</ul>
</li>
 	<li>Even though migration to Azure is the goal, retaining core network services in traditional on-premises datacenters will be necessary for the near future and results in a Hybrid Cloud.</li>
 	<li>For sequencing the migration of your workloads, you should begin with less-complex projects and gradually increase the complexity after the less-complex projects have been migrated.</li>
</ul>
<h2>Chapter 03: Managing Security, Compliance, and Data Privacy</h2>
<ul>
 	<li>IT leaders are still concerned that migrating to the cloud will leave them more vulnerable to hackers than their current in-house solutions.</li>
 	<li>They also worry about losing control of where their data is stored, who is accessing it, and how it gets used.</li>
 	<li>Companies are very concerned about losing control of their data.</li>
 	<li>They also want the ability to independently verify how their data is being stored, accessed, and secured.</li>
 	<li>Companies need to know that their compliance standards will be met, and that compliance will evolve as regulations change over time.</li>
 	<li>One key operational best practice that Microsoft uses to harden its cloud services is known as the “assume breach” strategy. A dedicated “red team” of software security experts simulates real-world attacks at the network, platform, and application layers, testing Azure’s ability to detect, protect against, and recover from breaches.</li>
 	<li>Microsoft conducts regular penetration testing to improve Azure security controls and processes.</li>
 	<li>Microsoft has established a policy for customers to carry out authorized penetration testing on their own—and only their own—applications hosted in Azure.</li>
 	<li>Azure’s DDoS defense system is designed to withstand attacks generated from outside and inside the platform.</li>
 	<li>Each virtual network is isolated from other virtual networks.</li>
 	<li>Azure Disk Encryption leverages the industry-standard BitLocker feature of Windows and the DM-Crypt feature of Linux to provide volume encryption for the OS and the data disks.</li>
 	<li>SQL Database TDE is based on SQL Server’s TDE technology, which encrypts the storage of an entire database by using an industry-standard AES-256 symmetric key called the database encryption key. SQL Database protects this database encryption key with a service-managed certificate.</li>
 	<li>Azure uses industry-standard transport protocols such as TLS between devices and Microsoft datacenters, and within datacenters themselves.</li>
 	<li>When customers delete data or leave Azure, Microsoft follows strict standards for overwriting storage resources before reuse.</li>
 	<li>Customers can request reports from Microsoft that provide information about user access to their environments.</li>
 	<li>When granted, access is controlled and logged. Strong authentication, including the use of multifactor authentication, helps limit access to authorized personnel only. Access is revoked as soon as it is no longer needed.</li>
 	<li>We will not disclose Azure customer data to law enforcement except as a customer directs or where required by law. When governments make a lawful demand for Azure customer data from Microsoft, we strive to be principled, limited in what we disclose, and committed to transparency. In its commitment to transparency, Microsoft regularly publishes a Law Enforcement Requests Report that discloses the scope and number of requests we receive.</li>
 	<li>Security Center helps you prevent, detect, and respond to threats with increased visibility into and control over the security of your Azure resources.</li>
 	<li>Azure Government is designed to meet the higher level security and compliance needs for sensitive, dedicated, US Public Sector workloads</li>
 	<li>Data exchange between the two Azure regions in Germany (Germany Central and Germany Northeast) is handled by a dedicated network line leased from a German provider, just to make sure that no data is accidently routed outside of Germany.</li>
 	<li>Moving workloads to the cloud shifts many security responsibilities and costs to Microsoft, freeing your security resources to focus on the critically important areas of data, identity, strategy, and governance.</li>
 	<li>Discontinue your use of software before it reaches end of support status.</li>
</ul>
<h2>Chapter 04: Azure Enterprise Administration</h2>
<ul>
 	<li>Departments can be leveraged if an additional level to structure the Accounts and Subscriptions is needed. Cost center and Start/End date can be added as an attribute to the Department.</li>
 	<li>Azure RBAC has three basic roles that apply to all resource types:
<ul>
 	<li>Owner has full access to all resources including the right to delegate access to others.</li>
 	<li>Contributor can create and manage all types of Azure resources but can’t grant access to others.</li>
 	<li>Reader can view existing Azure resources.</li>
</ul>
</li>
 	<li>A standard naming convention for Azure resource object types can be used to manage billing across projects teams, business units, or other desired view.</li>
 	<li>Every Azure subscription has a trust relationship with an Azure Active Directory instance.</li>
 	<li>Multiple subscriptions can trust the same directory, but a subscription trusts only one directory.</li>
 	<li>As a best practice, you should sign up for Azure as an organization and use a work or school account to manage resources in Azure. Work or school accounts are preferred because they can be centrally managed by the organization that issued them, they have more features than Microsoft accounts, and they are directly authenticated by Azure Active Directory.</li>
 	<li>It is also important to minimize migration of resources between subscriptions because of subscription reorganizations.</li>
 	<li>There are currently more than 20 Built-in roles available that can be assigned to users and groups to allow a granular assignment of permissions within an Azure subscription.</li>
 	<li>For creating additional custom RBAC roles please refer to <a href="https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-custom-roles" target="_blank" rel="noopener">https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-custom-roles</a>.</li>
 	<li>When the virtual networks are attached to the same ExpressRoute circuit, they are essentially a single routing domain.</li>
 	<li>A typical subscription model will be based on a mixed model of Shared subscriptions and Project subscriptions (or business department subscriptions) driven by particular project requirements.</li>
 	<li>What you are trying to accomplish with a naming convention is to put together a meaningful name about the particular subscription and how it is represented within the company. Many organizations will have more than one subscription, which is why it is important to have a naming convention and use it consistently when creating subscriptions.</li>
</ul>
<h2>Chapter 05: Integrating Azure into the Corporate Network</h2>
<ul>
 	<li>By default, when virtual machines are created and connected to Azure Virtual Network, they are allowed to route to any subnet within the virtual network, and outbound access to the Internet is provided by Azure’s Internet connection.</li>
 	<li>Challenges with this approach include the rapid consumption of gateway connections, which limits the size of the virtual network routing capability.</li>
 	<li>The best type of connection is depending on the detailed requirements. Nevertheless, we can say that enterprise customers tend do use ExpressRoute to fulfill their security and bandwidth requirements.</li>
 	<li>Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users.</li>
 	<li>Network Security Groups are similar to firewall rules in that they provide the ability to control the inbound and outbound traffic to a subnet, a virtual machine, or virtual network adapter.</li>
 	<li>A Network Security Group rule that is applied to a subnet is more like a firewall rule that is applied at the switch and affects inbound and outbound traffic on every port in the switch. Any virtual machine connected to the switch port would be affected by the Network Security Group rule applied to the subnet.</li>
 	<li>Using network security is strongly recommended for all kind of organizations.</li>
 	<li>When using forced tunneling, any outbound packet that is attempting to go to an Internet address will be routed to the default gateway and not to the Azure Internet interface.</li>
 	<li>A virtual network that is connected over a S2S VPN connection requires forced tunneling to be defined and configured on a per virtual network basis. A virtual network that is connected over an ExpressRoute connection requires forced tunneling to be defined at the ExpressRoute circuit, and this affects all virtual networks that are connected to that circuit.</li>
 	<li>When a network firewall virtual appliance is introduced (see previous section), user-defined routing must be configured to control the traffic routing through the appliance. Without user- defined routing, no traffic will flow through the appliance.</li>
 	<li>You should closely examine the set of systems at your edge network to ensure that they are current, provide high availability, and have sufficient capacity to meet peak loads.</li>
 	<li>For a high SLA and the best performance, use ExpressRoute, a dedicated WAN connection between your network and Azure.</li>
</ul>
<h2>Chapter 06: Extending Active Directory to Azure</h2>
<ul>
 	<li>When you create a new Azure AD tenant, the contents of the directory will be managed independently from the on-premises Active Directory forest.</li>
 	<li>With password hash synchronization, the Azure AD Connect service will synchronize one-way SHA256 hashes of Active Directory password hashes into Azure AD.</li>
 	<li>When a federation trust is in place, Azure AD defers to the on-premises identity provider to collect the user’s credentials and perform the authentication.</li>
 	<li>Enterprise customers tend to use AD FS to have better control of the authentication of users.</li>
 	<li>One decision that needs to be made is whether the accounts will be migrated into a single forest at some point. This is an important thing to consider, because it will determine whether you can use the objectGUID of the user accounts as the source anchor (which is used to match the Active Directory accounts to the Azure AD accounts).</li>
 	<li>If the users will be migrated to a single forest at some point, you’ll need to use a different source anchor, such as the user’s email address or UPN. The reason is that the objectGUID can’t be migrated with the user.</li>
 	<li>Even though there are multiple user accounts in the organization, there should be only a single account for the user in Azure AD. To enable this, the synchronization service needs to be able to match user accounts across the forests to a single person. For this to happen, the accounts in each forest need to have an attribute that contains the same, unique value for a user.</li>
 	<li>When enabling a federated identity relationship between Azure AD and an on-premises identity provider, an entire domain name in Azure AD is converted from a standard domain to a federated domain. This impacts all of the users that have UPNs under the domain name. You cannot have a mix of federated and nonfederated users in a domain name. Any subdomains under a domain namespace will have the same configuration as the parent domain.</li>
 	<li>If possible, we recommend that customers have trusts between their multiple Active Directory forests, so that only a single AD FS farm is needed for Azure AD.</li>
 	<li>It is best practice that all Azure administrator accounts should be configured for MFA.</li>
 	<li>It is generally recommended to consider the Azure datacenter as a separate Active Directory site, because it will have its own IP address space and routing considerations.</li>
 	<li>The standard recommendation is to place two domain controllers within an availability set in each Azure region where virtual machines reside. It is important to note that a resource domain or forest is not recommended given the additional overhead, and these do not represent an effective security boundary.</li>
 	<li>There should be an Active Directory site created for each Azure region, and all of the virtual networks in that region should be associated with that site.</li>
 	<li>As a recommended practice, make all of the domain controllers in Azure Global Catalog servers.</li>
 	<li>The domain controllers in Azure should run the DNS Server service, if possible.</li>
 	<li>DNS Servers need to be registered in the Azure virtual networks.</li>
 	<li>The Azure name resolution services do not support the complex name resolution needs of Active Directory, so do not attempt to use Azure DNS servers on domain controllers.</li>
 	<li>Azure AD Domain Services provides managed cloud-based domain services such as domain join, group policy, LDAP, and Kerberos/NTLM authentication in Azure IaaS that are fully compatible with Windows Server AD.</li>
 	<li>This managed domain is a standalone domain and is not an extension of an organization’s on-premises domain or forest infrastructure.</li>
 	<li>Application Proxy works by installing a slim Windows service called a Connector inside your network. The Connector maintains an outbound connection from within your network to the proxy service. When users access a published application, the proxy uses this connection to provide access to the application.</li>
 	<li>Make sure that you place the Active Directory database and SYSVOL on a data disk. If you use the operating system disk or a temporary disk, the database may get corrupted or purged during an outage.</li>
 	<li>Even if all of a customer’s users are signing in to Azure AD with AD FS, it is recommended to enable password synchronization. Doing so provides a good fallback method for user authentication if AD FS goes offline.</li>
 	<li>Use Web Application Proxy servers in the AD FS deployment for Azure AD. As a general rule, we recommend starting with an equal number of Web Application Proxy servers and AD FS servers.</li>
</ul>
<h2>Chapter 07: Operating Azure IaaS Services</h2>
<ul>
 	<li>Each customer has a dedicated Azure blob that houses the long-term data.</li>
 	<li>Aggregated metrics for some of the solutions such as Capacity Management are stored in a SQL Database hosted by Microsoft Azure. This data is stored for 390 days.</li>
 	<li>OMS Log Analytics currently meet the following security standards:
<ul>
 	<li>Windows Common Engineering Criteria</li>
 	<li>Microsoft Trustworthy Computing Certification</li>
 	<li>ISO/IEC 27001 compliant</li>
 	<li>Service Organization Controls (SOC) 1 Type 1 and SOC 2 Type 1 compliant</li>
</ul>
</li>
 	<li>Azure Backup provides application-consistent virtual machine backups for Microsoft workloads by using VSS to ensure that data is written correctly to storage.</li>
 	<li>A best practice is to use Geo-Redundant-Storage, especially for any production workloads.</li>
 	<li>Azure Backup implements an optimized blob copy that ensures constant, predictable IO and backup times.</li>
 	<li>For enterprises looking to encrypt their VM data in Azure, the solution is to use BitLocker on Windows or dmcrypt on Linux machines. Both of these are volume-level encryption solutions.</li>
 	<li>Complex restore scenarios such as VMs under load balancer, VMs with multiple reserved IPs, and VMs with multiple NICs require usage of PowerShell commands as described here: <a href="https://docs.microsoft.com/en-us/azure/backup/backup-azure-vms-automation#restore-an-azure-vm" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/backup/backup-azure-vms-automation#restore-an-azure-vm</a></li>
 	<li>The Azure Backup agent is establishing connectivity to the Recovery Services Vault by using https over the Internet with or without a proxy server. Furthermore, it is possible to use ExpressRoute Public peering to establish the connection over a private WAN link. The Backup agent provides network throttling.</li>
 	<li>Throttling applies to backup and restore activities.</li>
 	<li>Azure Backup requires a passphrase for encrypting data to be backed up. The agent performs encryption prior to transmission to Azure, and decryption after performing a restore operation back to the local system.</li>
 	<li>Azure Backup uses compression to reduce transmission time and storage requirements. Once the compression and encryption is applied, the data in the backup vault is usually 30 to 40 percent smaller. Azure Backup also uses block-level incremental backup methods so that only modified blocks are backed up in subsequent backups of the same set of files and folders.</li>
 	<li>Azure Backup Server inherits the functionality of Data Protection Manager (DPM) for workload backup. The main differences between DPM and MABS are:
<ul>
 	<li>DPM offers tape protection, which is not available in MABS.</li>
 	<li>DPM can protect one datacenter’s DPM installation with a secondary DPM server in another datacenter (and vice versa), which MABS doesn’t offer.</li>
 	<li>Many DPM servers can be managed in a single, central console in Operations Manager.</li>
 	<li>DPM can act as a conduit for Azure Site Recovery services with Hyper-V replica, whereas MABS only does backup.</li>
 	<li>MABS requires an Azure Backup Subscription.</li>
</ul>
</li>
 	<li>If an application or service has an API, then a runbook can work with it. If you have a PowerShell module for the application, then you can load that module into Azure Automation and include those cmdlets in your runbook.</li>
 	<li>Cloud service attributes for Azure IaaS cannot be achieved through technology alone; mature IT service management is still required.</li>
 	<li>As the IT department adopts a service provider’s approach, it should define available services in a service catalog based on business functionality.</li>
 	<li>A mature approach to systems administration is required for achieving a service provider’s approach and for driving predictability. The vast majority of systems administration tasks should be automated.</li>
 	<li>We suggest that if the total number of disks stored in a single storage account from VMs is more than 20, spread the VMs into different backup schedules to get required IOPS during transfer phase of the backup.</li>
</ul>
<h2>Chapter 08: Migrating Existing Services to Azure</h2>
<ul>
 	<li>Instead of having to do a lengthy migration with long downtime windows, or having to rebuild servers from scratch, Azure allows you to perform a migration where you can use your ASR replica and perform a failover.</li>
 	<li>It is required to map source and target networks, choose the appropriate storage category for the migrated workload, and assign the compute power that is required for the migrated workload.</li>
 	<li>This approach seems to be the most prevalent based on what we have seen. It takes the form of changing the IP address of every VM that is involved in the migration. A drawback of this approach requires the incoming network to “learn” that the application that was at IPx is now at IPy. Even if IPx and IPy are logical names, DNS entries typically have to be changed or flushed throughout the network, and cached entries in network tables have to be updated or flushed, therefore a downtime could be seen depending on how the DNS infrastructure has been set up.</li>
 	<li>From a migration perspective, using fixed IP addresses appears to be the easiest method to implement, but it has a number of potential challenges that in practice make it the least popular approach. For the migration of virtual machines to Azure it is required to use subnet failover.</li>
 	<li>In a migration scenario the subnets would move with the associated protected VMs. The main drawback to this approach is that you have to move the whole subnet, which may be OK but it may affect the migration granularity considerations.</li>
 	<li>When a test is started, Site Recovery will spin up the failover VMs in an isolated network so they can be running at the same time as production. Users can then connect to the recovered servers and verify everything is working. When the test is complete, Site Recovery will tear down the VMs so there is no manual cleanup required.</li>
</ul>
<h2>Chapter 09: Offering Management for Cloud-Based Services</h2>
<ul>
 	<li>A resource group is a container that holds related resources for an application. The resource group could include all of the resources for an application, or only those resources that are logically grouped together. The service designer decides how to allocate resources to resource groups based on what makes the most sense for the organization.</li>
 	<li>There is no need to define your entire infrastructure in a single template. Often, it makes sense to divide the deployment requirements into a set of targeted, purpose-specific templates that are linked together.</li>
 	<li>With the release of Microsoft Azure Stack, it is now possible to use the same deployment and development tools to build and deploy applications and infrastructure that reside either in the Azure Cloud or within the enterprise on-premises datacenter.</li>
 	<li>The Azure Usage API allows subscribers to programmatically pull in usage data to gain insights into their consumption. The granularity (hourly usage information) and resource metadata information available through the API provides the necessary dataset to support flexible Showback or Chargeback models.</li>
 	<li>Price prediction requires detailed knowledge about the Azure elements that a service consists of (defined at design time) along with estimated pricing information for each.</li>
 	<li>The Azure Resource RateCard API delivers a list of available Azure resources and pricing information.</li>
 	<li>Enterprise Agreement customers can use another API that allows usage access price sheet and other billing information in format of CSV and JSON from API.</li>
 	<li>PaaS Services are fully managed by Microsoft, but Azure IaaS virtual machines have the requirement to be maintained by the customer.</li>
</ul>
