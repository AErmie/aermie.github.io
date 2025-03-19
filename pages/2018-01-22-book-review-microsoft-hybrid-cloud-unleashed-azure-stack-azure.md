---
layout: page
title: Book Review: Microsoft Hybrid Cloud Unleashed With Azure Stack and Azure
date: 2018-01-22 10:08
author: AdinErmie
comments: true
categories: []
---
&nbsp;

<a href="/wp-content/uploads/2018/01/MicrosoftHybridCloudWithAzureStackAndAzure_BookCover.jpg"><img class="alignleft wp-image-30746 size-medium" src="/wp-content/uploads/2018/01/MicrosoftHybridCloudWithAzureStackAndAzure_BookCover-229x300.jpg" alt="" width="229" height="300" /></a>Recently, I finished reading the <a href="https://www.amazon.com/Microsoft-Hybrid-Cloud-Unleashed-Azure/dp/0672338505" target="_blank" rel="noopener">Microsoft Hybrid Cloud Unleashed With Azure Stack and Azure</a> ebook.

The chapters that I found most helpful were the entire book. Although I am already familiar with Azure, this book helped explain a lot about Azure Stack and where it fits into the hybrid cloud model.

I particularly found the last chapter (Chapter 11 "Customizing Azure Stack") of interest, because it went into detail on how to create the GUI workflow (similar to how we experience it in public Azure). <span style="color: #000000;"> </span>

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 01: Introducing Cloud Computing</h2>
<ul>
 	<li>Defined in the simplest of terms, cloud is a metaphor for hosted technology resources and applications. Hosted technology offers technology as a service to which businesses and consumers subscribe.</li>
 	<li>In more traditional computer implementations, technology is paid for by purchasing infrastructure and software licenses, and employing technology professionals to keep the lights on regardless of consumption. Cloud technology is a consuming technology, similar to how customers use (consume) power from electric or gas utilities.</li>
 	<li>As early as 2012, a Vanson Bourne study found cloud to have a measurable impact on business, including improved time to market, increased company growth, increased process efficiency, reduced operational costs, reduced IT spending, and reduced IT maintenance costs.</li>
 	<li>One of the strengths of the cloud model is it enables adding resources to the cloud pool of resources as needed, without incurring downtime.</li>
 	<li>Using cloud enables companies, regardless of size, to access massive cloud environments and resources. This levels the field of technology available to an organization for that competitive advantage it can get from digitally transforming its business.</li>
 	<li>Organizations can move their teams away from mundane remedial IT work, refocusing them on more strategic initiatives that impact the business’s bottom line.</li>
 	<li>Multi-cloud disadvantages include management overhead with multiple environments and keeping up with development from multiple vendors.</li>
 	<li>Another interesting observation by the IDC is that IaaS and PaaS will outpace the dominant SaaS growth with a CAGR of 27.0% and 30.6%, respectively, in 2016.</li>
 	<li>Adopting cloud is similar to adopting any technology solution: Without the proper approach, the technology will fail.</li>
 	<li>The reality is that cloud is a great enabler and cost saver for the business when done properly, but many companies get it wrong. Following are the top seven reasons cloud projects fail:
<ul>
 	<li>Lack of proper planning on cloud projects</li>
 	<li>Hasty adoption of cloud without vetting that the cloud solution accurately meets
the needs of the business</li>
 	<li>Lack of process such as ITIL (Information Technology Infrastructure Library) and
application lifecycle management (ALM)</li>
 	<li>No understanding of business or end users’ needs</li>
 	<li>Believing traditional IT or one’s existing data center infrastructure is a cloud solution</li>
 	<li>Bias towards one cloud provider or set of cloud solutions</li>
 	<li>Insufficient skill sets or talents needed to adopt and run cloud</li>
</ul>
</li>
 	<li>The key to successful cloud project is process. Utilizing proper process has you take a step back and cover all bases of a project, helping avoid these pitfalls. Here’s how:
<ul>
 	<li>Using the process framework with ITIL, first map out what IT offers to the business,
with part of that step including talking to business owners to gather their needs.</li>
 	<li>Designing the solution and proving it before going into production confirms you are
using the right technology for the solution.</li>
 	<li>Using ITIL includes evaluating that you have the right people in place with the
proper skill sets.</li>
</ul>
</li>
 	<li>Being listed as a leader in the magic quadrant demonstrates that a company is established in that market.</li>
 	<li>Microsoft Azure is the only major cloud platform ranked by Gartner as an industry leader for both IaaS and PaaS. Azure’s powerful combination of managed and unmanaged services lets you build, deploy, and manage applications in a way that makes the most sense for you.</li>
 	<li>Microsoft’s Azure Stack hybrid cloud platform lets customers use Azure as an extension to their on-premise data centers, expanding Azure’s cloud in their data centers as another region. Microsoft’s intent with Azure Stack is to meet its customers in the middle, letting them run their applications wherever they want to run them, instead of pushing those customers to use public cloud.</li>
 	<li>According to the Right Scale report, hybrid cloud is growing at a faster rate than private cloud adoption.</li>
 	<li>As Microsoft’s hybrid cloud platform and an extension of Azure, Azure Stack delivers a consistent cloud computing model between the on-premise data center and public cloud data centers, enabling IT professionals and developers to provision and scale services in the cloud with the same experience whether the deployment is on-premise or public cloud.</li>
 	<li>A recurring question that comes up in Azure Stack discussions is: While Azure Stack makes sense for service providers, how does it apply to the enterprise? Following are several reasons why and how Azure Stack applies to the enterprise:
<ul>
 	<li>For security reasons, some workloads cannot be run in public cloud.</li>
 	<li>For political reasons, some workloads cannot be run in public cloud.</li>
 	<li>The business is not ready to adopt a full-on public cloud solution.</li>
 	<li>The business has already heavily invested in on-premise data centers and would like to receive the benefits of a cloud model on existing infrastructure.</li>
 	<li>The business wants to adopt a multi cloud or hybrid cloud strategy.</li>
 	<li>The business wants to offer a self-service cloud solution to reduce shadow IT while
maintaining centralized control.</li>
 	<li>The business would like to develop solutions or deploy new applications in a test
scenario and move to production using the same platform. In addition, the business
would like to leverage public cloud for dev teams and move production workloads
on-premise for production, or vice versa.</li>
</ul>
</li>
 	<li>Microsoft’s goal with hybrid cloud and Azure Stack is for you, as the customer, to run your workloads where you want to run them. Microsoft provides you with a cloud platform that can be used at enterprise-scale (on-premise Azure Stack) data centers or hyper-scale (public cloud Azure) implementations. Azure Stack translates to your cloud, on your terms.</li>
 	<li>Using Azure Stack, IT professionals and developers can provision and scale services in the cloud with the same experience regardless of being deployed on-premise or to public cloud.</li>
 	<li>Go into cloud with a strategy. Start with a high value tactical problem and solve it with cloud.</li>
 	<li>Address cloud security concerns up-front.</li>
 	<li>Solidify your network infrastructure and ensure the best possible speeds. The adoption of cloud makes the network and internet connections business critical.</li>
 	<li>Automate everything you can in your cloud solution. Cloud is about removing traditional obstacles, resulting in lower overhead (costs), and enabling self-service.</li>
</ul>
<h2>Chapter 02: Applying ITIL and DevOps to Hybrid Cloud</h2>
<ul>
 	<li>Hybrid cloud is anticipated to become the most common use of cloud by 2019, with corporations moving from a no-cloud policy to a cloud-first policy and then eventually adopting a cloud-only policy.</li>
 	<li>With the advent of cloud, IT is becoming a service provider. Process does not go away when IT becomes a service provider; it becomes even more critical.</li>
 	<li>As IT departments continue to move to cloud, it becomes absolutely critical to shift from
managing IT as separate bundles of technology and capabilities to managing it as business services (also known as applications) that are offered to the organization. Not making this transition in regards to management when utilizing cloud can give rise to serious operational risk.</li>
 	<li>IT departments not aligned to the business’s goals carry a high risk of business units in their organization moving to what is known as shadow IT.</li>
 	<li>As shadow IT will bring cloud into your environment, it is a best practice for you to proactively bring cloud into your service strategy.</li>
 	<li>Think of CAPEX as buying a car and OPEX as renting or leasing that car. OPEX has a lower cost of entry and a short-term commitment as you only pay for what you use. CAPEX has a larger cost for point of entry and a long-term commitment because once you have purchased equipment you own it.</li>
 	<li>One huge benefit of leveraging cloud is that you can expand capacity extremely quickly to
meet growing demands or even last-minute demands.</li>
 	<li>Availability sets could span across Azure and Microsoft Azure Stack in a hybrid cloud
scenario.</li>
 	<li>The other and better option with hybrid cloud is that you can burst into public cloud when your on-premise resources top out.</li>
 	<li>Azure Stack has built-in resiliency as well through Microsoft technologies at the fabric layer. The technologies powering the resiliency are Hyper-V clustering, Windows storage clustering, load balancing, automated patching, self-healing, and more.</li>
 	<li>The end user and business do not care if the service is cloud-based or based on traditional IT platforms; they simply want to consume the service and know that it works.</li>
 	<li>It is also important that you have a simple, efficient, and fast change management process so as not to diminish the speed that using cloud brings to the business.</li>
 	<li>Azure Stack can be deployed without the need to have Azure Active Directory in a completely disconnected model utilizing ADFS.</li>
 	<li>Businesses and end users are now accustomed to technology moving faster, including receiving new features and fixes more quickly; the days of annual software updates are long gone.</li>
 	<li>DevOps is a combination of development and operations tasks and teams tearing down the development and operations silos. It requires a cultural change inside of an organization that fosters team building, interdepartmental collaboration, and an open, communication-oriented environment.</li>
 	<li>Businesses adopting DevOps become more competitive because they are able to decrease their time to market with products, with lower release failure rates, faster turnaround on fixes, and overall greater product quality.</li>
 	<li>Application Insights can be used to monitor applications running on Azure and Azure Stack</li>
 	<li>Microsoft provides a DevOps self-assessment tool to help you gauge your DevOps readiness. The tool looks at seven key DevOps practice areas and produces an assessment of where you should focus your DevOps efforts. Using this tool is a great way to get started with DevOps. Find the DevOps self-assessment tool at <a href="https://devopsassessment.azurewebsites.net" target="_blank" rel="noopener">https://devopsassessment.azurewebsites.net</a>.</li>
 	<li>An IT department should align to a business’s needs, not require the business to align
to IT’s needs. DevOps and Cloud empower this refocus, interlocking strategies and tools
to transform IT from not delivering at a pace the business needs to becoming a business
enabler.</li>
 	<li>Proactive monitoring can help identify patterns and issues before they bubble up, and helps in identifying the root causes of issues. Cloud platforms often come with the ability to identify patterns, helping you get down to the root cause, and can even monitor down to the code level through application performance monitoring (APM) integrating directly with source control systems.</li>
 	<li>Because Azure and Azure Stack simplify the platform and tooling, they often become a key driver in an organization adoption of DevOps.</li>
 	<li>Cloud can become the catalyst for digital transformation.</li>
 	<li>Having a consistent underlying platform means that one set of DevOps-related tools can work across any of these aforementioned clouds.</li>
 	<li>Regardless of the DevOps-related tooling used, the consistent management layer across
the board is Azure Resource Manager (ARM), whether you are using Azure or Azure Stack. Microsoft continuously adds integration of DevOps-related tooling into its ecosystem, and has created an Azure DevOps Integrations website (<a href="http://aka.ms/trydevops" target="_blank" rel="noopener">http://aka.ms/trydevops</a>), which contains a wizard allowing you to describe your DevOps scenario along with the tooling you plan to use.</li>
 	<li>Hybrid cloud is here to enhance the IT pro and developer experience. With Azure and Azure Stack, Microsoft has built what can be termed as hybrid cloud evolved.</li>
 	<li>Hybrid cloud evolved also is software-defined everything, bringing fabric management into the infrastructure as code realm.</li>
 	<li>Microsoft hybrid cloud + DevOps and ITIL can give you a best of breed solution to help
bring your organization into the digital transformation age.</li>
 	<li>With ITIL and DevOps frameworks it is best to learn and understand the benefits of each and apply the parts that apply to you and your environment.</li>
</ul>
<h2>Chapter 03: Azure Stack Architecture</h2>
<ul>
 	<li>Azure Stack is consistent with Azure as it provides the same management experience
of the Azure portal, service deployment via Azure Resource Manager (ARM) templates,
PowerShell, and Azure command-line interface (CLI) and application development using
the Azure software development kit (SDK).</li>
 	<li>Azure Stack Region
An Azure Stack region is a set of scale units that share the same physical location, and
are under one physical and logical administrator.</li>
 	<li>An Azure Stack scale unit is always associated with a single region and is a unit of capacity expansion in Azure Stack. There can be one or more scale units within a region. Each scale unit can be composed of a different generation of hardware than the others (homogenous within the scale unit). A scale unit is also equivalent to a fault domain, which resembles a failover cluster within your Azure Stack region.</li>
 	<li>Every single component in Azure Stack is deployed in a resilient manner; the resiliency depends on that particular component.</li>
 	<li>Also, all servers within a single scale unit must be homogenously configured (that is, CPU, memory, NIC, and storage devices).</li>
 	<li>Retrieving hardware-related health information is handled by out-of-band management tools; as Microsoft does not allow monitoring agents to be installed, all hardware-related health information is gathered using an intelligent platform management interface (IPMI) through the BMC.</li>
 	<li>It uses a PowerShell implementation and authenticates using Just Enough Administration (JEA) principles in PowerShell.</li>
 	<li>Azure Stack Hardware Lifecycle Host (HLH) is a server connected to a BMC network, which is external to the Azure Stack environment.</li>
 	<li>This server will host the hardware monitoring software (such as Dell OpenManage), perform firmware configuration and software updates (drivers), and enable emergency management and hardware monitoring.</li>
 	<li>During initial setup it holds several roles including Active Directory Domain Services (ADDS), Windows Deployment Services (WDS), Dynamic Host Controller Protocol (DHCP), and so on. When the deployment of first physical nodes is complete, these roles are moved to those physical nodes.</li>
 	<li>All servers within a scale unit must have the same configuration, meaning you need to have the exact same hardware available inside a scale unit.</li>
 	<li>The VM sizes in Microsoft Azure vary; as Azure is a massive distributed system, not all VM SKUs available in the public cloud are available in a consumer deployment of Azure Stack—due to its limited capacity compared to Azure.</li>
 	<li>At the time of writing of this book, Azure Stack supports the A, D, and Dv2 series of VM SKUs.</li>
 	<li>Tenant VM creation sequence in Azure Stack differs from classic Hyper-V VM creation.</li>
 	<li>When you curate compute content for Azure Stack (that is, upload your own custom image to Azure Stack marketplace), you need to ensure that the dependencies included in the compute content in your Azure Stack deployment (extensions, custom content, and so on) do not restrict you from using that image in Azure.</li>
 	<li>S2D uses a cluster shared volume file system (CSVFS) with ReFS as the file system allowing cluster-wide data access, fast VHD(X) creation, expansion, and checkpoints; these enhance the performance and reliability of the storage system.</li>
 	<li>A single S2D cluster can occupy over 3PB of raw storage and allows you to add servers to scale out and drives to scale up, with the S2D pool automatically absorbing new drives when they are added for capacity expansion.</li>
 	<li>In a hyper-converged architecture, both compute and storage resources scale and are managed together in a single system. This is the default deployment option for Azure Stack.</li>
 	<li>Azure Stack SDN embraces industry standards like Virtual Extensible LAN (VXLAN) and Open vSwitch Database (OVSDB), and incorporates technologies directly from Azure such as the Software Load Balancer (SLB) and Virtual Filtering Platform (VFP) vSwitch extension that is proven to be reliable, robust, and scalable.</li>
 	<li>Resiliency is always adhered to while designing each infrastructure component in Azure
Stack. In the network layer, resiliency is achieved by using redundant network interfaces
(DATA – 10Gbps + single physical NIC with dual ports at a minimum), and on top of that
using switch-embedded-teaming for port/link resiliency and building up a dual-switch
(TOR) configuration from there.</li>
 	<li>SDN implementation in Azure Stack is possible since the three network planes—the
management, control, and data planes—are independent of the network devices
themselves, but abstracted for use by other entities such as Azure Stack. SDN allows Azure Stack to dynamically manage its data center network to provide an automated, centralized mechanism to meet the requirements of the applications and workloads.</li>
 	<li>The network resource provider offers more granular network control, metadata tags, faster configuration, and rapid and repeatable customization. It also supports multiple control interfaces such as PowerShell, .NET SDK, Node.JS SDK, REST-based API, and so on.</li>
 	<li>VNets in Azure Stack allow you to deploy your own network. They are completely isolated
from one another, allowing you to create disjointed networks for development, testing,
and production that all use the same CIDR address blocks. Using VNets, you can create
subnets with your private or public IP address spaces.</li>
 	<li>By default, Internet access in a VNet is provided through NAT and does not require a gateway.</li>
 	<li>Another important consideration in VNets is how Azure Stack performs name resolution.
Azure Stack has an internal DNS name resolution mechanism for instances deployed in
tenant VNet. Tenants can also use their own DNS servers and configure the subsequent
VNets to use with them.</li>
 	<li>VNets in Azure Stack support for VXLAN or NVGRE encapsulation formats (VXLAN is the
default), and the Virtual Network Manager module in the network controller manages CA/
PA mappings. Packet processing occurs on the Azure Stack host(s).</li>
 	<li>VIPs are in the SLB multiplexer (MUX).</li>
 	<li>Each MUX uses border gateway protocol (BGP) to advertise each VIP to routers on the physical network as a /32 route.</li>
 	<li>Gateways in Azure Stack are designed to allow cross-premise connectivity capacities such as site-to-site (S2S) VPN. Azure Stack leverages the multi-tenant gateway capabilities of Windows Server 2016 and provides high availability through an M+N model (active/passive).</li>
 	<li>If you just want to resolve Internet DNS names and to connect to other virtual machines in
the same virtual network, there is no need to specify anything in the network configuration
and resolution will just work using iDNS.</li>
 	<li>iDNS cannot create a DNS record for a name that can be resolved from outside the virtual
network.</li>
 	<li>Azure Stack leverages Azure Active Directory (AAD) or Active Directory Federation Services (ADFS) as its authentication mechanism. Multiple instances of AAD can be integrated to provide authentication for tenant services in Azure Stack. You also need to consider factors such as federated identity, self-service user management, and so on, to provide a robust end-user experience for your tenants.</li>
 	<li>As Azure Stack is delivered as an integrated system you will not be setting up any hardware on your own; instead, you will purchase a deployment ready rack-and-stack scale unit from one of the Microsoft OEM partners, ready to plug into your data center.</li>
 	<li>When you power on your Azure Stack system, one of the very first configuration tasks
would be to establish connectivity with AAD or ADFS, and so on.</li>
 	<li>Unlike Windows Server updates, Azure Stack updates are delivered as one package that contain updates for hardware, OS, and software. The updates will be delivered at a rapid cadence, letting you choose when to apply them within a given time frame depending on their business requirements. Should you not deploy an update before the given time frame, the scale unit will go out of support. This ensures that patching and updating in Azure Stack will always be reliable, single-sourced, and easy to use.</li>
 	<li>While Azure Stack does not allow you to install any monitoring agents, you can use existing connections from its own monitoring system such as Rest API, BMC, and SNMP to integrate with your existing monitoring solution and an information technology service management (ITSM) system.</li>
</ul>
<h2>Chapter 04: Installing and Configuring Azure Stack</h2>
<ul>
 	<li>The ASDK is a 180-day time-bombed version of Azure Stack, and is not suitable for production workloads. The Azure Stack Development Kit does not receive software updates from Microsoft; to test a newer version of Azure Stack (once made available), you must redeploy the server from scratch with the version you want to evaluate.</li>
 	<li>The ASDK can be installed with two types of identity providers. You can choose to use Azure Active Directory (AAD) or use the inbox Active Directory Federated Services (ADFS) environment.</li>
 	<li>Errors may occur during installation. There can be many reasons for errors. Microsoft created the installer such that it knows the last successful step it has run, meaning you only need to initiate a rerun after resolving the problem.</li>
 	<li>Azure Stack takes a different approach. Jeffrey Snover, a Technical Fellow at Microsoft, explained it this way (<a href="https://regularitguy.com/2017/01/24/azure-stack-update-with-jeffrey-snover/" target="_blank" rel="noopener">https://regularitguy.com/2017/01/24/azure-stack-update-with-jeffrey-snover/</a>):
<ul>
 	<li>Like you cannot log in to a SAN controller to install your own software and agents (backup/ monitoring), you also will not be able to install any software on your own on Azure Stack infra VMs and physical nodes. This is the concept of sealed hosts. You will have an administrative portal and CLIs available to manage your cloud environment.</li>
</ul>
</li>
 	<li>To prepare for Azure Stack in your own data center, you need to plan regarding
monitoring, identity management, and network connectivity.</li>
 	<li>Azure Stack is a black box that you can integrate into your Information Technology
service management (ITSM) environment. This means you can use an application
programming interface (API) to retrieve monitoring details regarding the health of the
Azure Stack software. Hardware is monitored by a vendor solution and made available to
you using the hardware vendor’s software.</li>
 	<li>You can choose to integrate Azure AD as the identity provider in Azure Stack, or if installing Azure Stack in a disconnected scenario, as might banks or the U.S. Department of Defense (DoD), you can use ADFS as your identity provider. After installing Azure Stack in a disconnected scenario, connect your ADFS environment from your own domain to the Azure Stack ADFS and allow the Azure Stack Graph API to retrieve users and groups from your Active Directory.</li>
 	<li>Inside the Azure Stack integrated system, routing uses Border Gateway Protocol (BGP). BGP is not a requirement for routing outside of the stack or routing management subnets into the Azure Stack environment. When ordering Azure Stack, at least two Top of Rack (ToR) switches must be connected to your border/core network, which you can connect using BGP or static routing.</li>
 	<li>A minimum of six subnets must be defined for your Azure Stack deployment. Those subnets are categorized as DATA and BMC subnets. The DATA subnets are the networks that are consumed by resources deployed and hosted in Azure Stack. The BMC subnets are networks that connect the Out of Band (OOB) and the switch management subnet.</li>
 	<li>It is the responsibility of the Azure Stack owner to determine which URL to expose to the
Internet and corporate network.</li>
 	<li>Azure Stack includes three types of administrators:
<ul>
 	<li>Tenant administrator</li>
 	<li>Delegated provider administrator</li>
 	<li><span style="font-size: 14px;">Service administrator</span></li>
</ul>
</li>
 	<li>If you use Azure (public cloud) and create your own subscription, you are the tenant administrator of your subscription. The tenant administrator controls all resources that exist in the resource groups and in his subscription.</li>
 	<li>The delegated provider administrator is an individual who, in addition to consuming resources as a tenant administrator, is allowed to create and resell offers from the service provider to her customers. The delegated provider administrator can also be used in an enterprise environment where a central IT group delegates the task of creating and assigning offers to the business.</li>
 	<li>The service administrator is an individual who is in control of the fabric infrastructure and
can manage the resource providers in the system. The user account used for installing
Azure Stack is the overall service administrator.</li>
 	<li>The authentication method is defined at installation time when the vendor starts the installation of Azure Stack. It cannot be changed later.</li>
 	<li>Security measurements are built into Azure Stack to mitigate and prevent
breaches throughout the system.</li>
 	<li>By leveraging least privilege, RBAC and Just Enough Administration (JEA), administrator endpoints are secured by allowing them to run just the commands necessary to do their job. The days of being a member of the Azure Stack’s domain admin are gone!</li>
 	<li>The Azure Stack physical hosts and management virtual machines (VMs) are sealed. That means you are not able to log in to these systems.</li>
 	<li>Antivirus is not sufficient these days; Microsoft changed its approach with Azure Stack, as it knows exactly what is running on the hardware. Azure Stack blocks all code except that which is allowed to run Azure Services in your data center. On the servers, Microsoft uses code integrity policies to lock down the server:
<ul>
 	<li>Security OS baseline: By leveraging an OS baseline configured with device guard
and enhanced kernel mode protection using hypervisor code integrity, only software
from Microsoft is able to run on the system.</li>
</ul>
</li>
 	<li>To establish a site-to-site VPN to Azure in an ASDK, you must perform an unsupported implementation of NAT on the public IP on your firewall and redirect it to your MAS-BGPNAT01 VM. In a multi-node configuration, the IP address for the Gateway pool is advertised to the network and the MAS-BGPNAT01 VM is not used.</li>
 	<li>You can syndicate gallery items from public Azure into your Azure Stack environment. This requires that Azure Stack is installed in a “connected” scenario.</li>
 	<li>For syndication to work, Azure Stack must be able to connect to Azure. You currently cannot syndicate marketplace items to a disconnected Azure Stack environment.</li>
</ul>
<h2>Chapter 05: Using Resource Providers</h2>
<ul>
 	<li>In the real world, IaC is not about implementing infrastructure with code; it is about setting up and configuring infrastructure with automation using code.</li>
 	<li>The primary function of ARM is enabling you to work with resources in a solution as a group, where deploying, updating, or deleting all the resources in an application can occur in a single, coordinated operation. ARM also provides security, auditing, and tagging features that ease the burden of managing resources in an application after its deployment.</li>
 	<li>A resource must always be part of a resource group and can only be part of one resource group. Resource groups cannot be nested in other resource groups.</li>
 	<li>From a security standpoint, it is important to understand that infrastructure resource providers can only be called within the admin subscription in Azure Stack.</li>
 	<li>Health state in Azure Stack is directly linked to alerts: If there are no alerts for a given component, that component is healthy;</li>
 	<li>There are no health state roll-ups in Azure Stack, as the rules involved in roll-ups can mask issues or present issues when none exist. Finally, the health of cloud services is separated from the health of cloud fabric (infrastructure).</li>
 	<li>Alerts are only reported against well-known objects and have consistent alert severity definitions. This ensures that only critical alerts need administrative action immediately, while warning alerts can be acted on by an administrator as needed. The monitoring system provides a clear description of the problem and remediation required, and includes links to online troubleshooting guides for step-by-step guidance.</li>
 	<li>Each of the IaaS VMs hosted within those roles has the Azure monitoring agent present. This is the same monitoring agent used in Azure to stream events to a central monitoring location to raise alerts so Microsoft engineers can act on them. That agent is being used in Azure Stack to forward Event Tracing for Windows (ETW) events to individual storage accounts that are associated with each of the RPs registered with HRP.</li>
 	<li>For low-level device information and alerts, Microsoft relies on the hardware partners shipping the Azure Stack solution to provide agentless monitoring solutions via their baseboard management controllers. Similarly, network switches need to be monitored via external monitoring solutions that leverage SNMP.</li>
 	<li>When you create an IaaS VM in Azure Stack, CRP and SRP collaborate behind the scenes where the page blob toggles to SMB-only at VM run time, providing a super-optimized Hyper-V-over-SMB I/O path.</li>
 	<li>This resource provider does not currently support all database management capabilities of Azure SQL Database, such as elastic database pools and the ability to scale database performance.</li>
 	<li>While the Azure SQL Database service in Azure is based on micro services, the SQL Adapter that is a part of the SQL RP in Azure Stack utilizes SQL running in IaaS VMs, and uses a different namespace in ARM from the Azure SQL database. The SQL RP also does not contain the same functionality as the SQL Database service available in Azure.</li>
 	<li>Azure Stack runs your apps on fully managed virtual machines, and you can select between shared VM resources or dedicated VMs.</li>
 	<li>SQL RP installation may fail if it takes more than 90 minutes. You will see an on-screen failure message and notice an error in the log file. However, the actual deployment is re-tried from the failed step.</li>
 	<li>When you add servers, assign them to a new or existing SKU to differentiate service offerings. As an example, you could offer a SQL Enterprise instance with database capacity and automatic backup while reserving high performance servers for individual departments. Have the SKU name reflect the database server’s properties, which will help the tenants place their databases appropriately. Note that all hosting servers in a particular SKU should have the same capabilities.</li>
 	<li>The MySQL RP deployment can span from 20 minutes to several hours. The length depends on the Azure Stack host system performance and download speeds of the Internet connection.</li>
 	<li>You must configure SSO to enable the advanced developer tools within app service—
Kudu—and enable use of the Azure Functions Portal experience.</li>
 	<li>You cannot enable SSO or the Azure Functions portal in ADFS-based environments at this time.</li>
</ul>
<h2>Chapter 06: Azure Stack Tenant Configuration and Capabilities</h2>
<ul>
 	<li>Similar to public Azure, tenants can request subscriptions through one of the offerings Microsoft makes available. In Azure Stack, the service administrator must create the offers. Differing from Azure—where customers only can see offers—in Azure Stack the service administrator builds the offer by creating plans, adding services, and ultimately creating an offer based off a plan with additional add-on plans. The service administrator can also choose to allow self-service sign-up to offers or assign them manually to tenants using the administrator portal.</li>
 	<li>Using a plan, you define the services that are available and the region from which they are provided.</li>
 	<li>For each service you assign to a plan you also can define a quota on that service.</li>
 	<li>When creating an offer, you must select those plans that will be part of your offer. When the offer is created, it is by default configured in a private state, which means that tenants cannot sign up to it using the portal. Alternatively, you could make the offer public, enabling tenants to sign up to that offer.</li>
 	<li>The authors recommend not setting all quotas to unlimited, as you might run out of resources if someone decides to create many resources and over-provision your Azure Stack instance.</li>
 	<li>A service administrator can have a hierarchy five levels deep of delegated providers reselling services to their customers.</li>
</ul>
<h2>Chapter 07: Managing Azure Stack with CloudOps</h2>
<ul>
 	<li>Managing Azure Stack requires using a CloudOps model in a CloudOps way; Microsoft built Azure Stack from the ground up with CloudOps in mind.</li>
 	<li>One difference between Azure Stack and Azure is that the management of Azure Stack is the responsibility of the organization that purchases and deploys it. Managing Azure Stack is very different compared to traditional management of an Information Technology (IT) infrastructure and systems within that infrastructure. The management is different because Azure Stack is not just an ordinary infrastructure or system. Azure Stack is a full-blown cloud—a full-blown extension of Azure itself.</li>
 	<li>IT operations (ITOps) and ITSM do not go away with CloudOps; CloudOps is the evolution of ITOps and ITSM. CloudOps pulls from frameworks such as the Information Technology Information Library (ITIL), Lean IT, Prince, Application Lifecycle Management (ALM), and more; funneling the best practices from these frameworks into CloudOps, which is used to achieve continuous operations in clouds.</li>
 	<li>CloudOps shifts the focus of IT to becoming centered around powering business applications that are critical on the digital front.</li>
 	<li>Rather than focusing directly on building and deploying business applications, CloudOps focuses on delivery of the cloud infrastructure and platform services to support customer self-service, leveraged by DevOps teams.</li>
 	<li>CloudOps exists to support DevOps, and DevOps is core to digital transformation.</li>
 	<li>Digital transformation is the new Industrial Revolution of business, with CloudOps and DevOps the assembly line that brings innovation. Using DevOps, businesses can bring digital services to the market. Businesses can use Azure and Azure Stack to empower digital transformation by leveraging technologies such as Internet of Things (IoT), micro services, server-less computing, containers, block chain, extreme automation, and hyper-scale.</li>
 	<li>Region management is the operation of an Azure Stack instance, resources, and offerings. An Azure Stack region can have a single node or many nodes. Regardless of the number of nodes, those nodes, hardware, and their resources can be managed together at a region level.</li>
 	<li>By default Azure Stack removes all closed alerts from the system after seven days.</li>
 	<li>The update process will be fully automated across the entire Azure Stack infrastructure, minimizing any downtime to Azure Stack deployment and running tenant production workloads.</li>
 	<li>Microsoft has developed a management pack (MP) for monitoring Azure Stack with System Center Operations Manager (SCOM).</li>
 	<li>This Azure Stack monitoring solution is agentless. The management pack utilizes the Azure Stack REST APIs to remotely discover and collect information about the specified Azure Stack deployment.</li>
 	<li>The Azure Stack management pack does not automatically discover your Azure Stack environment. Further configuration is required to add an Azure Stack deployment.</li>
 	<li>The rule checks Azure Stack environments every 180 seconds by default; you can modify the timing via an override in the management pack. The interval is initially set to 180 seconds because Azure Stack’s own internal health monitoring system detects new health state on a two-to-three-minute interval. The rule also queries the Azure Stack health resource provider API for closures, every 30 seconds by default.</li>
 	<li>The System Center Management Pack for Microsoft Azure monitors Azure Stack tenant workloads.</li>
 	<li>The Azure Stack diagnostics tools streamline the log collection mechanism from the many moving parts of the Azure Stack fabric.</li>
 	<li>By default, the log collection tool collects logs for the past four hours. The three layers of protection for Azure Stack include:
<ul>
 	<li>The fabric/infrastructure</li>
 	<li>The individual services (resource providers) powering IaaS, PaaS, DBaaS, XaaS (and so on) offerings for consumers</li>
 	<li>The tenant workloads</li>
</ul>
</li>
 	<li>Azure Stack includes a backup resource provider that works directly with the Infrastructure Backup Controller to back up data to an external file share in a tarball. You will need to protect the data on that file share with an external backup program such as System Center Data Protection Manager (DPM).</li>
 	<li>Backups are full backups; there are no incremental backups.</li>
 	<li>Infrastructure backup does not include network switch configuration or hardware management server configuration.</li>
 	<li>GridPro provides a third-party solution with EvOPS as an Azure Stack add-on. You can use EvOPS to turn the Azure Stack portal into a service catalog where your customers can submit incidents and check on incidents or service requests. Find EvOPS at <a href="https://www.gridprosoftware.com/products/evops" target="_blank" rel="noopener">https://www.gridprosoftware.com/products/evops</a>.</li>
 	<li>On the backend, EvOPS integrates with ITSM solutions such as System Center Service Manager, Cherwell, ServiceNow, and BMC Remedy. EvOPS also contains a workflow engine that can automate tasks and workflows in Azure Stack or external systems.</li>
</ul>
<h2>Chapter 08: Provisioning Resources and Scripting</h2>
<ul>
 	<li>Azure Resource Manager provides security, auditing, and tagging features to help you manage your resources after deployment.</li>
 	<li>RDP limits connections to Azure Stack to two concurrent users. While it is a quick way to connect once the Azure Stack is created, you will probably find that using VPN is easier once it is registered on your workstation.</li>
 	<li>Unlike RDP, multiple users/computers can connect at the same time, making VPN the preferred method for connecting. Through VPN you can access the administrator and user portals, or use installed tools such as PowerShell, Azure CLI, or Visual Studio.</li>
 	<li>While connecting and managing Azure Stack is similar to connecting to Microsoft Azure, it requires Azure Stack-compatible Azure PowerShell modules. Connecting and managing Azure Stack also requires a set of PowerShell modules that support the API versions used in your Azure Stack.</li>
 	<li>Using an ARM template is the modern way to deploy resources.</li>
 	<li>Deploying a VM using cmdlets, rather than ARM templates, can be quite complex. Multiple resources are required and the deployment must be performed in the correct order to ensure each resource is available when needed.</li>
 	<li>Verify that each resource was successfully deployed before continuing to the next resource. Azure Resource Manager manages this when you use ARM templates, and you can redeploy the same template on top of a failed deployment to retry deploying the failed resources. If you use a script and want to be able to redeploy using that script, you would need to delete all the resources before trying to redeploy, or add code to determine if a resource exists or needs to be deployed.</li>
 	<li>Azure CLI commands differ from PowerShell commands in that they are designed to complete a task, without being as modular as the cmdlets are. For example, deploying a virtual machine in Azure CLI requires fewer commands than when using PowerShell.</li>
 	<li>Unlike PowerShell, you can use Azure CLI to deploy a virtual machine using a single command. While this enables easy deployment, it does not provide the same freedom as the modularity of the PowerShell cmdlets.</li>
 	<li>Deploy a template by explicitly providing a value for each parameter, or use a template parameters file that contains values for some or all parameters to make this task easier.</li>
 	<li>Two modes are available when deploying an ARM template:
<ul>
 	<li>Incremental: The default mode, this leaves unchanged resources unchanged, adds any new resources, and updates any that have changed.</li>
 	<li>Complete: Use this mode to re-deploy a complete group. The mode deletes any resources that exist in the resource group but not in the template, adds new resources, applies changes as needed to update resources, and leaves any unchanged resources.</li>
 	<li>Read more about deployment modes at <a href="https://docs.microsoft.com/en-us/azure/" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/</a>
azure-resource-manager/resource-group-template-deploy#incremental-and-completedeployments.</li>
</ul>
</li>
 	<li>Use the deployment portal if you just need to do a single deployment. For scheduled or repeated deployments, the authors recommend using PowerShell or Azure CLI instead. Tools such as Azure Automation and Visual Studio Team Services can even help you automate and schedule deployments.</li>
 	<li>Optionally, PowerShell provides a cmdlet to validate the template before deploying. You can use this cmdlet to save time or in automated testing scenarios such as continuous deployment (DevOps).</li>
 	<li>Because you are executing the command with the -verbose parameter, the output indicates whether the test is successful. When executing the command without -verbose, the test is successful if there is no output or errors.</li>
 	<li>The name of the deployment is automatically generated using the name of the template plus the current date; this is useful because the name is used in logs. The default deployment mode is Incremental, but you can use the -Mode parameter to change to Complete mode.</li>
 	<li>While ARM functions include the uniqueString() function to generate a unique string, there is no function that generates a unique GUID.</li>
 	<li>While some prefer to deploy resources via commands, the authors recommend using ARM templates for most use cases due to their idempotent nature, which allows repeated deployments using the same template and enables easy administration and maintenance of both new and existing resources.</li>
</ul>
<h2>Chapter 09: Using ARM Templates in Hybrid Cloud</h2>
<ul>
 	<li>ARM). A template can include all types of resources—even when the deployment is a complete server farm, such as a SharePoint farm. You also can utilize templates to apply changes to existing resources.</li>
 	<li>Idempotence is a concept often mentioned in relation to ARM and PowerShell Desired State Configuration (DSC). It enables content such as a template or configuration to be deployed multiple times to the same resources, while only applying changes.</li>
 	<li>APIs. Some consider JSON the successor to eXtended Markup Language (XML), defining less text to describe the content, also useful when transferring content over the Internet. JSON’s modular and simple structure makes it perfect for defining resources and settings.</li>
 	<li>Another upcoming player in the IDE market is Microsoft Visual Studio Code. Being cross-platform, open source, and free, it includes a great editor with out-of-the-box features similar to a subset of the features in Microsoft Visual Studio. Its ability to incorporate available community extensions gives it infinite extensibility capabilities.</li>
 	<li>Different resource types support different API versions, with each version supporting different features. To ensure you get the features you need, research the API versions you require. This is particularly true when sharing templates between Azure Stack and public Azure, since not all APIs from Azure may be available in Azure Stack.</li>
 	<li>The Azure Stack documentation provides more information about authoring templates, including currently available API versions, at <a href="https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-develop-templates" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-develop-templates</a>. Additional details about ARM template design and authoring, such as functions and other references, are available in the Azure documentation at <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-resource-manager/</a>
resource-group-authoring-templates.</li>
 	<li>An old template might use an old version of the API schema; check whether a new schema is available. Available schemas are found in the Azure GitHub repository at <a href="https://github.com/Azure/azure-resource-manager-schemas/tree/master/schemas" target="_blank" rel="noopener">https://github.com/Azure/azure-resource-manager-schemas/tree/master/schemas</a>.</li>
 	<li>Define outputs in templates to enable using the template within other templates in a nested scenario.</li>
 	<li>Name parameters with a lowercase letter as the first letter, and afterwards using uppercase letters only at the start of each new word. This is also known as camelCase and is mentioned in the Azure documentation at <a href="https://docs.microsoft.com/en-us/azure/azureresource-manager/resource-manager-template-best-practices" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azureresource-manager/resource-manager-template-best-practices</a>. The authors recommend parameter names that are easily understandable, without shortened or abbreviated words, as they will be viewed in the portal and other GUIs. As an example, it is better to name a parameter virtualNetworkName than vNetName.</li>
 	<li>The authors recommend placing all values for the different properties in the resources into variables, making it easier to later reuse templates.</li>
 	<li>The authors recommend using names that are easy to understand, as even the template developer might need to read the template six to twelve months later and understand its purpose.</li>
 	<li>Like parameters, variables should be named using a lowercase letter as the first letter, and afterwards with uppercase letters whenever a new word starts; for example, virtualNetworkName.</li>
 	<li>Another important phase of planning a successful project is to determine what resources are needed and how they are connected, perhaps by creating a diagram using Microsoft Visio.</li>
 	<li>It is important that any resource providers used are available in the correct API version in the targeted region (any Azure Stack instances or public Azure); otherwise, deployment will fail.</li>
 	<li>For information about available resource types and their configurations, see the ARM template reference documentation at <a href="https://docs.microsoft.com/en-us/azure/templates/" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/templates/</a>.</li>
 	<li>Another great tool to modify resources is the Resource Explorer, available in Azure at https://resources.azure.com/, and in Azure Stack at https://portal.local.azurestack.external/#blade/HubsExtension/ArmExplorerBlade.</li>
 	<li>An often used function is concat, which combines multiple values into one. Functions can be pooled with other functions to combine, separate, or modify the value(s) in other ways.</li>
 	<li>Available functions are described in detail in the ARM template documentation at <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-functions" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-functions</a>.</li>
 	<li>Author your templates in a modular fashion, with standard resource configurations separate from larger templates. It is common to save templates for specific types of resources such as SQL Server, then reuse that template whenever a SQL server is needed. This practice can ease administration when deploying resources on a regular basis, and can save time in testing of each part of a template, as it is easier to test a smaller template containing one resource.</li>
 	<li>When using nested templates, consider a number of items to be sure the template works as intended:
<ul>
 	<li>Generalization: Ensure the template you author for nesting is as flexible as possible; do not hardcode resource names to fixed values—these should be inputs or incorporated in functions to generate names.</li>
 	<li>Separate deployment logs: Logs of nested template deployments are shown separately. Find the nested template deployment using the portal, with PowerShell or Azure CLI.</li>
 	<li>Place nested templates in an available location: You can retrieve templates with a URI; confirm the URI is available. A URI cannot be a local path, such as the same folder as the template; it must be available from the Azure Stack Resource Manager.</li>
 	<li>Define correct outputs: Define the outputs required by the parent template, such as the resource ID of created resources.</li>
 	<li>Be sure dependencies are set correctly: If a value is needed from a nested template, use the dependsOn property to confirm it runs before the value is used.</li>
</ul>
</li>
 	<li>Nested templates can be very useful, but you should tread carefully and plan properly before authoring. The ARM documentation provides additional information about nested templates at <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-linked-templates" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-linked-templates</a>.</li>
 	<li>When you add a new resource using a resource template, check if the API version used by the template is supported in the current version of Azure Stack. The supported API version for storage accounts, virtual networks, network interfaces, and public IPs at the time of writing this chapter is 2015-06-15, but will change with future updates.</li>
 	<li>Notice a comma (,) is used to separate multiple parts in a JSON block; as you are removing the last one, you must also remove the comma from the end of the subnet-1 definition.</li>
 	<li>IntelliSense is one of the biggest advantages of using Visual Studio or another IDE with the IntelliSense feature, compared to using a simple text editor. IntelliSense helps discover the properties and values available when the resources are defined. It is based on schemas published by Microsoft, which currently is the only way available to explore all available resources and their settings.</li>
 	<li>The authors recommend using the Azure Resource Manager Tools extension when authoring templates in VS Code. This is currently included in the default installer</li>
 	<li>VS Code also features a snippet feature that can be pre-filled with ARM Resource snippets.</li>
 	<li>Azure documentation describes how to get started authoring templates in VS Code; see <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-vs-code" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-vs-code</a>.</li>
 	<li>A huge advantage of using Azure Stack as an on-premise cloud provider is its consistency with Microsoft Azure. Azure Stack has the same API, many of the same resource providers, and is manageable using the same PowerShell modules. While this enables reusing templates between Microsoft Azure and Microsoft Azure Stack, be careful—some things, such as environment endpoints and region capabilities, are not exactly the same.</li>
 	<li>Templates that are intended to be shared between clouds should only utilize resource providers available to both.</li>
 	<li>In most cases, you can add a parameter to the template to use as a value for the differences. However, this can make the templates confusing and difficult to use. The authors recommend researching whether a way exists to get the value dynamically, such as getting the location from the resource group to which the resources are deployed, or getting the base URI for a storage account URI using the resource function.</li>
 	<li>Microsoft provides a template validator script for Azure Stack that is part of the Azure Stack tools. The script uses a JSON file that describes the capabilities of Azure Stack and validates the template. You can get the script at <a href="https://github.com/Azure/" target="_blank" rel="noopener">https://github.com/Azure/</a>
AzureStack-Tools/tree/master/TemplateValidator.</li>
 	<li>For additional information about the reference function, see <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-functions#reference" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-functions#reference</a>.
To read more about template best practices, go to <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-template-best-practices#resources" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-template-best-practices#resources</a>.</li>
 	<li>Extensions are executed by the VM agent in the VM guest OS, enabling the OS to be configured without actually having (username/password/network) access to the VM. They are added as part of the deployment or added to existing VMs using a template, command line, or portal GUI.</li>
 	<li>Configuring VMs using PowerShell DSC is an excellent way to set up the guest OS on the VM during deployment, or modify the configuration on an existing VM.</li>
 	<li>Using a custom script extension makes it simple to execute scripts inside a VM. There are two versions of this extension: one for Windows and one for Linux.</li>
 	<li>The Windows version supports executing a command line, also known as batch. Use powershell.exe to execute PowerShell commands. The Linux version executes a Bash command.</li>
 	<li>There are a number of custom script extensions for Windows examples in the Quick Start templates. For more information, see <a href="https://github.com/Azure/AzureStack-Quick-Start-Templates/tree/master/101-vm-windows-apply-extension-customscript-cmd" target="_blank" rel="noopener">https://github.com/Azure/AzureStack-Quick-Start-Templates/tree/master/101-vm-windows-apply-extension-customscript-cmd</a> and <a href="https://github.com/Azure/AzureStack-QuickStart-Templates/tree/master/101-vm-windows-apply-extension-customscript-pscmd" target="_blank" rel="noopener">https://github.com/Azure/AzureStack-QuickStart-Templates/tree/master/101-vm-windows-apply-extension-customscript-pscmd</a>.</li>
 	<li>To execute an external file, see the example at <a href="https://github.com/Azure/AzureStack-QuickStart-Templates/tree/master/101-vm-windows-apply-extensioncustomscript-sf" target="_blank" rel="noopener">https://github.com/Azure/AzureStack-QuickStart-Templates/tree/master/101-vm-windows-apply-extensioncustomscript-sf</a>.</li>
 	<li>Many discussions touch the topic of using ARM templates versus using PowerShell cmdlets. While there are use cases for both, templates are typically the best approach. Templates typically deploy faster, and scripting dependencies in a PowerShell script can be difficult.</li>
 	<li>The authors suggest copying from available examples, such as Azure Stack Quick Start, ensuring you rarely have to write anything from scratch. Save and re-use anything you author, as many deployments are similar.</li>
</ul>
<h2>Chapter 10: Automating Your Hybrid Cloud</h2>
<ul>
 	<li>Utilizing assets enables a more secure and easily maintainable way of using values, versus typing them in scripts or external files. In addition, assets can be updated at runtime to save values such as when a check was last performed.</li>
 	<li>Webhooks provide easy-to-use endpoints for triggering automation from external systems either on-premise or in the cloud. They make it easy to integrate from one system to another without custom code.</li>
 	<li>Hybrid workers must meet the minimum requirements of Windows 2012 R2 or above, PowerShell 4.0, two cores, and 4GB of memory.</li>
 	<li>PowerShell is the fastest authoring method for developing Windows automation. It includes the most comprehensive library of modules, which you can use to connect to many of the systems and products that currently exist. There is almost no limit to what you can do with PowerShell.</li>
 	<li>PowerShell Workflow: Workflows differ from scripts, supporting more advanced features such as parallel processing and the ability to resume at checkpoints if there is a failure. Workflows do not support the exact same code as scripts, as not all PowerShell cmdlets are compatible; however, they are very similar. A disadvantage of workflows is their startup time, which can range from a few seconds to several minutes in extreme cases. Workflows are great for advanced scenarios in automation, when a little startup time is not an issue.</li>
 	<li>For more information about the advantages and limitations of each runbook type, see the Azure Automation documentation at <a href="https://docs.microsoft.com/en-us/azure/automation/automation-runbook-types" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/automation/automation-runbook-types</a>.</li>
 	<li>A sandbox is created whenever you queue a runbook to execute in Azure, isolating its execution from other instances on the same machine and providing an additional degree of security and privacy that would otherwise not be available. Using a sandbox helps ensure that each app running on a machine has a minimum guaranteed level of service. The runtime limits enforced by the sandbox protect apps from being adversely affected by other resource-intensive apps that might be running on the same machine.</li>
 	<li>All PowerShell modules stored in Assets are transferred to this sandbox, making the queue time relative to how many modules are installed in the automation account. If another runbook job is executed within a certain period of time, the same sandbox is used and the queue time is shorter. It is important to understand that all runbooks executed in Azure fall within the fair share rule, which means a runbook cannot run for more than three hours, after which it is stopped. For more information about runbook execution and fair share, see <a href="https://docs.microsoft.com/en-us/azure/automation/automation-runbook-execution" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/automation/automation-runbook-execution</a>.</li>
 	<li>Assets are one of the most valuable features of Azure Automation, as they provide a way to save information centrally and re-use that information in multiple runbooks. An asset could be a server address, such as an SMTP server to send emails, that is used in multiple runbooks. When the address changes, you only need to change it in one place; all runbooks using the asset will use the new value. Another advantage of assets is that they can be encrypted, letting you save secret values such as keys or passwords.</li>
 	<li>Variables can be encrypted, making it impossible for non-administrators or external systems to read the value. An encrypted variable value can only be read from within a runbook.</li>
 	<li>Integration modules are similar to PowerShell modules; the difference being that they can contain a meta file describing one or more connection type assets for the module. Read more about integration modules at <a href="https://docs.microsoft.com/en-us/azure/automation/automation-integration-modules" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/automation/automation-integration-modules</a>.</li>
 	<li>
<div>If you are repeatedly deploying complete solutions, the authors recommend using an ARM template to add assets to a new or existing automation account.</div></li>
 	<li>
<div><span style="font-size: 14px;">Deploying automation resources using ARM templates is also known as automation packs. For examples of automation packs, see the Azure Automation GitHub repository at </span><span style="font-size: 14px;"><a href="https://github.com/azureautomation/automation-packs" target="_blank" rel="noopener">https://github.com/azureautomation/automation-packs</a>. </span></div></li>
 	<li>Common errors when executing automation include service account passwords that are expired or incorrect, or server names that have changed.</li>
 	<li>When using workflows that contain checkpoints, read the assets required by each part of the workflow, after each CheckPoint-Workflow command. This enables the operator to update server names and service accounts when the workflow suspends, and then resume the workflow, which retrieves the new values and continues execution.</li>
 	<li>Many scripters use the PowerShell ISE to author their scripts. While you can edit runbooks in a standard PowerShell ISE, accessing assets requires changes in the runbook code to make it work. The PowerShell ISE add-on enables synching assets to the local machine, which makes them available to test and debug runbooks, providing a much faster  nd efficient workflow when developing runbooks.</li>
 	<li>The Azure Automation Authoring Toolkit also provides several features for authoring, testing, and publishing runbooks and DSC configuration in Azure Automation.</li>
 	<li>Connecting to an automation account creates a workspace on the local hard drive, located in C:\AutomationWorkSpace by default. This workspace contains any resources retrieved from the account, such as runbooks or assets, and includes credentials. Although redential asset values are not retrieved from the automation account and must be typed in manually, they are saved in the workspace. Keep this in mind when using the PowerShell ISE add-on. To follow best practices, you should only use the add-on in a development or testing environment.</li>
 	<li>
<div>Using graphical runbooks over the other options is based on personal preference. Some people love the high-level overview they provide, while others think they are an unnecessary <span style="font-size: 14px;">complication of the authoring and usage of PowerShell.</span></div></li>
 	<li>While graphical runbooks support inserting single cmdlets as activities, the authors recommend you use them to combine multiple complete runbooks.</li>
 	<li>Using a graphical runbook can make it easier for non-scripters to understand the logic of complex scenarios.</li>
 	<li>To see how to create and link a schedule using an ARM template, check the template sample at <a href="https://github.com/azureautomation/automation-packs/blob/master/101-sample-automation-resource-templates/sample-deploy-schedule/" target="_blank" rel="noopener">https://github.com/azureautomation/automation-packs/blob/master/101-sample-automation-resource-templates/sample-deploy-schedule/</a>.</li>
 	<li>The hybrid worker server role is a feature of Microsoft’s OMS (Operations Management Suite) agent a.k.a. Microsoft Monitoring Agent (MMA). This means any server with the OMS agent installed and connected to an OMS workspace can be turned into a hybrid worker.</li>
 	<li>Hybrid workers have the following advantages:
<ul>
 	<li>No incoming connection required: A hybrid worker does not require incoming connections from Azure. It only requires several outgoing ports for a specific set of DNS addresses; a proxy server can be used if necessary.</li>
 	<li>No fair share limit: If you execute runbooks in Azure, the fair share limit limits each runbook to three hours maximum per runbook. Executing a longer-running runbook requires a hybrid worker.</li>
 	<li>All PowerShell modules supported: Any modules that require installed applications, such as consoles, cannot be used in Azure, but can be used on a hybrid worker.</li>
 	<li>Use executables: As a hybrid worker is a standard Windows server, any executables can be installed and executed.</li>
 	<li>Local access: You can access any servers within the environment of which the hybrid worker is a member. This enables many use cases that cannot be performed from Azure.</li>
</ul>
</li>
 	<li>There are also some disadvantages:
<ul>
 	<li>Install and maintain PowerShell modules: While any PowerShell modules included in the automation account are automatically implemented for use in Azure, this is not the case with hybrid workers. Ensure all required modules are installed; optionally, use DSC to configure the hybrid worker and modules.</li>
 	<li>Maintenance: You must maintain the server, applying Windows patches and so on.</li>
</ul>
</li>
 	<li>Webhooks are a simple way to trigger runbooks from other environments or scripts. They enable an HTTPS endpoint that requires no authentication besides the URI, which contains a token.</li>
 	<li>Following are some examples of when to use webhooks:
<ul>
 	<li>SharePoint workflows: Using out-of-the-box activities, a runbook can be triggered from a SharePoint workflow.</li>
 	<li>Custom scripts: Just about any command line, scripting, or programming language features a way to trigger a HTTPS address. You could use webhooks to trigger runbooks from *nix Bash scripts, Python, or PHP.</li>
 	<li>Services that support webhooks: Many cloud services today, including GitHub and ServiceNow, support triggering web services or webhooks and can submit data from the service to a runbook.</li>
</ul>
</li>
 	<li>Previously, much of the integration between systems/services was based on polling, where a script runbook ran every x seconds/minutes and looked for changes. Webhooks enable event-based integrations. This is more optimized, as it saves the systems from many unnecessary calls and load.</li>
 	<li>Using this capability requires that automation &amp; control be enabled on the OMS workspace. There are also several requirements for the automation account to be able to link to a workspace: The account must be located in the same subscription, location, and resource group.</li>
 	<li>PowerShell DSC does not support registering a hybrid worker by default, although you can do so using the script DSC resource. A community project by MVP Ben Gelens simplifies the process by using a custom DSC resource. The module contains a resource to wait for the hybrid worker PowerShell module and a resource for the registration itself. The PowerShell module is found in the PowerShell Gallery at <a href="https://www.powershellgallery.com/packages/HybridRunbookWorkerDsc" target="_blank" rel="noopener">https://www.powershellgallery.com/packages/HybridRunbookWorkerDsc</a>.</li>
 	<li>When using the DSC extension, the authors recommend developing and testing the configuration manually on a VM before adding the extension to the template. This enables a much faster workflow, as the testing instantly provides verbose feedback.</li>
</ul>
<h2>Chapter 11: Customizing Azure Stack</h2>
<ul>
 	<li>At the time of writing this book, Azure Stack has limited options for customizing colors, logos, and such. However, one of its customizable areas is the marketplace. While it is simple to create a standard marketplace item, customized items provide many new options for users, such as custom inputs, using a wizard, and incorporating custom pictures (icons/screenshots). Customized marketplace items take Azure Stack’s usability to a whole new level.</li>
 	<li>The technique to place conditionals into the template is to use a parameter as an input value and a special construct known as a configuration hashtable. Although current public documentation does not describe the configuration hashtable, it is fully supported in Azure and Azure Stack.</li>
 	<li>If using the template for a marketplace item, the empty template must have the same parameters as the original template; otherwise, the template cannot validate.</li>
 	<li>Microsoft recently added a completely new native function for performing conditional deployments to Azure. While no news about Azure Stack support or formal documentation is available yet, you can find an example at <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-authoring-templates#resources" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-authoring-templates#resources</a>.
This functionality will greatly simplify conditional deployments.</li>
 	<li>For a DSC configuration to be available for a deployment, you must compress the configuration itself and the DSC resources it uses into a zip file and make that available via an URI. The authors recommend using an Azure storage account for these files, as it is easy to use and supports private connections.</li>
 	<li>Use built-in controls when developing the GUI wizard for the marketplace item to provide a better user experience for selecting the VM size and public IP name. These controls require specific input parameters in the main ARM template. You then add the conditional deployments switches, requiring more parameters.</li>
 	<li>Add default value “” to any parameter that does not have a default value. This is required when using the template for a marketplace item, as the validation process checks for values on all parameters.</li>
 	<li>Referencing an empty template when a feature is disabled requires a set of empty template files. The ARM template syntax requires an empty template for each feature, as it must have the same parameters as the real linked template.</li>
 	<li>After this introduction to designing the GUI, you can start authoring the CreateUIDefinition file, which contains the layout of each step and the outputs sent to the template when deploying the marketplace item. The available controls for a CreateUIDefinition file are described at <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/managed-application-createuidefinition-elements" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-resource-manager/managed-application-createuidefinition-elements</a>.</li>
 	<li>After defining the steps, perform a test before adding outputs, as outputs can invalidate the template if incorrectly typed. After adding outputs, perform another test to check output.</li>
 	<li>Before reaching the Summary page, press F11 to open the console in the browser. Output from the wizard is sent to the console when the wizard reaches this page. The output format is JSON, resembles an ARM template parameter file, and can be used to check if the inputs of the ARM template are correct. Test by deploying the azuredeploy.json template using a parameter file with the content of the output.</li>
 	<li>The marketplace item metadata contains all values used to display that item in the marketplace. The resources are content files with images to show in the portal, and one or more string resource JSON files. The manifest file describes the overall structure and values of the item, such as title, category, and templates to deploy. The UIDefinition file describes the blade type to use.</li>
 	<li>The authors recommend adding images to the marketplace item to provide the best possible user experience. Images are shown as icons with a screenshot displayed in the marketplace browser. Multiple icons are required to support the different sizes of icons.</li>
 	<li>The images must be the exact size in pixels for the marketplace item package to be accepted by ARM.</li>
 	<li>Azure and Azure Stack accept packaged marketplace items in a file type called azpkg. The package is actually just a zip file with a certain structure and content.</li>
 	<li>The manifest and files referenced in either of the marketplace item definition files are packaged into an azpkg file before publishing to the marketplace. Use the Azure Gallery Packager tool to create the package. The Azure Stack documentation describes this process at <a href="https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-create-and-publish-marketplace-item#create-a-marketplace-item" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-create-and-publish-marketplace-item#create-a-marketplace-item</a>.</li>
 	<li>To read more about how to author the UI for the marketplace item, check the documentation at <a href="https://docs. microsoft.com/en-us/azure/azure-resource-manager/managedapplication-createuidefinition-functions" target="_blank" rel="noopener">https://docs. microsoft.com/en-us/azure/azure-resource-manager/managedapplication-createuidefinition-functions</a> and <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/managed-application-createuidefinition-elements" target="_blank" rel="noopener">https://docs.microsoft.com/en-us/azure/azure-resource-manager/managed-application-createuidefinition-elements</a>.</li>
</ul>
