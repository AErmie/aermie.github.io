---
layout: page
title: Book Review: Exam Ref 70-532 Developing Microsoft Azure Solutions
date: 2015-08-31 09:44
author: AdinErmie
comments: true
categories: []
---
<a href="http://adinermie.com/wp-content/uploads/2015/07/ExamRef70-532Cover.jpg"><img class="alignleft wp-image-17661 size-medium" src="http://adinermie.com/wp-content/uploads/2015/07/ExamRef70-532Cover-248x300.jpg" alt="ExamRef70-532Cover" width="248" height="300" /></a>Recently, I finished reading the <a href="http://www.amazon.com/70-532-Developing-Microsoft-Azure-Solutions/dp/0735697043/" target="_blank">Exam Ref 70-532 Developing Microsoft Azure Solutions</a> eBook.

The chapter(s) that I found most helpful were basically all of them! Hence the majority of my highlights are from basically the entire book. Note that I didn't just highlight all of the "Exam Tip" content, but also additional information that I found useful in learning and understanding the topic.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: Design and Implement Websites</h3>
<div>
<ul>
	<li>When you create an Azure website, you are automatically provisioned with a production slot that represents your live website. With each deployment slot, you can create up to four additional deployment slots (for a total of five) that you can swap with the production slot (or even with other non-production slots). When you swap, the site content and certain slot configurations are exchanged with no downtime.</li>
	<li>Caution: Slot Resources are Shared
All deployment slots for a given website share the same web hosting plan and are created within the same virtual machine (VM) instance that is hosting the production slot. Therefore, take care when performing stress tests on a non-production slot because you will in effect be stressing the production website by virtue of stressing the VM that hosts it. Because the same VM instance is used for all slots, you cannot scale a non-production deployment slot independently of the production slot—you can only adjust the scale settings for the production slot.</li>
	<li>The website for which you want to create a second deployment slot must be using the Standard web hosting plan mode (also referred to as tier). In other words, you cannot create a deployment slot with the Free, Shared, and Basic modes.</li>
	<li>When you swap deployment slots, all of the website content is swapped, but the same is not true of the configuration. The following configuration items will move to the destination slot:
<ul>
	<li>General settings (for example, .NET framework version, Web Sockets, Always On)</li>
	<li>Connection strings</li>
	<li>Handler mappings</li>
	<li>Application and site diagnostics settings</li>
	<li>Monitoring settings</li>
	<li>The following configuration items will not move to the destination slot:</li>
	<li>Publishing endpoints</li>
	<li>Custom domain names</li>
	<li>SSL certificates and bindings</li>
	<li>Scale settings</li>
</ul>
</li>
	<li>Two websites can participate in the same web hosting plan only when they are created in the same subscription, resource group, and region (with the same pricing tier requirements).</li>
	<li>Websites can be migrated between web hosting plans provided they meet two conditions. First, the website and the web hosting plan must reside in the same region. Second, the web hosting plans in question must be a part of the same resource group.</li>
	<li>A fundamental pattern embraced by the configuration model of Azure Websites is the separation of code from configuration, and particularly the notion that the deployment environment can override configuration.</li>
	<li>Note: App Settings and Connection Strings
App settings and connection strings, while editable in the portal, are strictly read-only when accessed through your web application code. Changes made to these settings at runtime are not persisted and may be lost if your application (or its VM host) restarts. If you need to alter these settings, you can do so manually via the portal or you can use the Azure Management API, Windows PowerShell, or xplat-cli to change them at the website level.</li>
	<li>Real World: PHP Handler Mapping
Azure Websites has built-in support for PHP. You need to configure a handler mapping for PHP only if you want to use a different PHP runtime than that which is included with Azure Websites.</li>
	<li>Type the path to the script processor in the text box with the placeholder text SCRIPT PROCESSOR PATH. Note that this value must be an absolute path</li>
	<li>You can also isolate a virtual directory within its own w3wp.exe worker process by making it an application. A common scenario is to expose a subdirectory of wwwroot as the root website while also exposing a peer to that subdirectory as a separate web application.</li>
	<li>Two types of DNS records effectively express this purpose:
A records, or address records, map your domain name to the IP address of your website.
CNAME records, or alias records, map a subdomain of your custom domain name to the canonical name of your website, expressed as &lt;yoursitename&gt;.azurewebsites.net.</li>
	<li>Note: Using a Custom Domain Name
Use of a custom domain name requires your website to be in a web hosting plan mode of Shared, Basic, or Standard. You cannot map a custom name to your website if it is in Free mode.</li>
	<li>Exam Tip: Server Name Indication (SNI) is an extension of the TLS standard that enables a web server to host multiple different certificates at a single web server host accessed using a single IP address that is shared among all the websites it hosts. Essentially, its function is very practical; it enables a client to indicate the host name of the server it is trying to access during the TLS handshake that sets up the secure connection, and then the web server is able to use this name to select the appropriate certificate from its certificate store to use in securing the communication with the client. This enables greater website density per web server because it allows a single web server host to provide HTTPS across different websites, where each is accessed using a different domain and using its own certificate for securing communication. Contrast this with the IP-based approach, which is limited to one certificate per IP address. To host multiple websites each with different certificates, you would typically need multiple hosts each with a different IP address. In the context of Azure, SNI frees Websites from having to dedicate an IP address (which are a limited resource) to a single website—leading to greater hosting efficiency and, ultimately, cost savings.
The primary obstacle to using SNI is browser support—legacy browsers do not support it and will display certificate warnings. However, the list of modern browsers supporting SNI is not insignificant, and it includes the most common browsers in use today: Microsoft Internet Explorer 7 (on Vista or higher), Mozilla Firefox 2.0 or later, Google Chrome 6 or later, and Safari 3.0 or later.</li>
	<li>In the context of Websites, the Event Log is particularly useful for capturing unhandled exceptions that may have escaped the application’s exception handling logic and surfaced to the web server</li>
	<li>Web server logs are textual files that create a text entry for each HTTP request to the website.</li>
	<li>Detailed error message logs These HTML files are generated by the web server and log the error messages for failed requests that result in an HTTP status code of 400 or higher</li>
	<li>Failed request tracing logs In addition to the error message (captured by detailed error message logs), the stack trace that led to a failed HTTP request is captured in these XML documents that are presented with an XSL style sheet for in-browser consumption</li>
	<li>Application diagnostic logs These text-based trace logs are created by web application code in a manner specific to the platform the application is built in.</li>
	<li>Exam Tip: Your own Failed Request Tracing Logs folder may include multiple folders that start with W3SVC. There are always two such folders because one is for your website and one is for the Site Control Manager (also known as Kudu) that runs in parallel to your website.</li>
	<li>Important: Azure Storage and Log Data Limitations
Application diagnostic logging to Table or Blob storage is supported only for .NET applications. While the portal may let you enable it for any website, log data will be collected to Azure Storage only from a .NET application.</li>
	<li>To debug a deployed website, you must ensure that it is a debug build (for example, it has the debug symbols)</li>
	<li>Important: How Debugging Affects your Website
When you attach the debugger and pause at a breakpoint, you are stopping the deployed Azure website for all requests, so it is not a good idea to rely on this technique for production debugging because users will think your website is down. Also, if you spend more than a few minutes stopped at any one breakpoint, Azure will treat your Websites worker process as having become unresponsive and try to restart it, so be prepared to move quickly when attached with the remote debugger to a website.</li>
	<li>Note: Availability of Endpoint Monitoring
Endpoint monitoring is available only to websites running in the Standard web hosting plan mode</li>
	<li>Operations defined within WebJobs can be triggered to run either when the job runs or when a new file is created in Blob storage or a message is sent to an Azure queue.</li>
	<li>Modify the class Program so that it is public. If you do not make the class public, WebJobs will not detect and run your operations.</li>
	<li>Within a datacenter, Azure will load balance traffic between all of your website instances using a round-robin approach.</li>
	<li>Exam Tip: Unlike other Azure compute services, Websites provides a high availability SLA of 99.9 percent using only a single standard instance. You do not need to provision more than one instance to benefit from this SLA.</li>
	<li>Each metric is measured as an aggregate (typically an average) across all of your website instances over a period of time</li>
	<li>Note: Non-Contiguous Thresholds
It is important to note that the scale-up threshold and the scale-down threshold do not have to be contiguous. For example, you can specify that one instance should be added every time the CPU utilization exceeds 80 percent, and only begin to remove one instance when the CPU utilization drops below 50 percent. This is another way to control the frequency of scaling operations.</li>
	<li>The existing portal allows you to define only a single pair of scale-up and scale-down rules based on the CPU percentage metric. You do not have control over the Over Past period, the step (or number of instances added/removed), or the cool-down period used each time a scaling rule is triggered—these default to 20 minutes, one instance, and 20 minutes, respectively</li>
	<li>Traffic Manager combines endpoint monitoring of your website with DNS so that client traffic is always directed toward a viable endpoint. It is important to understand that traffic does not flow through Traffic Manager to your website endpoint, but rather it is guided to your website endpoint as a result of DNS resolution</li>
	<li>Custom Domain Names and Traffic Manager
If you plan to use a custom domain name with Traffic Manager, you must configure the DNS settings for the custom domain to use a CNAME record that maps to the &lt;yourprefix&gt;. trafficmanager.net address. You cannot use an A record to map to an IP address exposed by Traffic Manager. This means that you can only use Traffic Manager for subdomains, such as www.contoso.com and not for contoso.com.</li>
	<li>Choosing a TTL Value
The default TTL used by Traffic Manager in response to DNS queries is 300 seconds (5 minutes). If you are using Traffic Manager primarily for failover, you might be tempted to set the TTL to a very low value to ensure clients who had been communicating with a now unreachable endpoint can quickly start communicating with a functioning endpoint. The minimum TTL allowed is 30 seconds, and you can use this value, but be aware you are creating additional DNS traffic as well as incurring additional Traffic Manager costs to handle the increased load of DNS queries.</li>
	<li>Avoiding Cascading Failures
When using the performance load balancing method, be aware that if all the endpoints in the closest datacenter are not available, then Traffic Manager will switch to a round-robin method, distributing traffic to endpoints located in other datacenters to avoid overwhelming the endpoints in the next closest datacenter and potentially causing a chain of failures.</li>
	<li>Cloud Patterns
For comprehensive coverage of a number of cloud design patterns, see the material supplied by Microsoft Patterns &amp; Practices at <a href="http://msdn.microsoft.com/en-us/library/dn568099.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/dn568099.aspx</a>.</li>
	<li>If your web application consumes an external service (such as the SQL Database or Storage service), your application code must be aware of how the service may throttle your requests and handle the throttling exceptions properly (perhaps by retrying the operation later)</li>
	<li>An implementation of the Circuit Breaker pattern prevents an application from attempting an operation that is likely to fail</li>
	<li>If everything is working as expected, the circuit breaker is said to be in the closed state, and any requests from the application are routed through to the operation</li>
	<li>If the number of recent failures invoking the operation exceeds a threshold over some defined period of time, the circuit breaker is tripped and changes to the open state.</li>
	<li>In the open state, a timer controls the “cool-down” period of the proxy. When this cool-down period expires, the circuit breaker switches to a half-open state, and a limited number of trial requests are allowed to flow through to the operation while the rest fail immediately, or the code queries the health of the service hosting the operation. In the half-open state, if the trial requests succeed or the service responds as healthy, then the failure is deemed repaired, and the circuit breaker changes back to the closed state</li>
	<li>Application Request Routing (ARR) is a feature of Websites that effectively enables sticky sessions between the client (such as the browser) and the first instance of the website it connects to by providing the client with a cookie that encodes identification for that website instance</li>
</ul>
&nbsp;
<h3>Chapter 02: Create and Manage Virtual Machines</h3>
<div>
<ul>
	<li>There are two approaches to identifying supported Azure workloads.
<ul>
	<li>The first is to determine whether the workload is already explicitly supported and offered through the Marketplace, which provides a large collection of free and for-pay solutions from Microsoft and third parties that deploy to VMs</li>
	<li>The second approach is to compare the requirements of the workload you want to deploy directly to the published capabilities of Azure VMs or, in some cases, to perform proof of concept deployments to measure whether the requirements can be met</li>
</ul>
</li>
	<li>Fundamentally, there are two approaches to creating a new VM. You can upload a VM that you have built on-premises, or you can instantiate one from the pre-built images available in the Marketplace</li>
	<li>SSH Key Generation
To create the SSH public key that you need to provision your Linux VM, run ssh-keygen on a Mac OSX or Linux terminal, or, if you are running Windows, use Puttygen. A good reference for the latter, if you are not familiar with it, is available at <a href="http://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-use-ssh-key/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-use-ssh-key/</a>.</li>
	<li>Manually Installing the Azure VM Agent
If your uploaded Windows or Linux VM does not have the VM Agent installed, you can download it to your VM instance and install it manually. For detailed instructions on how to install the VM Agent, visit <a href="http://msdn.microsoft.com/en-us/library/dn832621.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/dn832621.aspx</a>.</li>
	<li>If you have built a VM in Azure, you can capture the VM and create a VM image for future reuse. Note that for a generalized image, you must generalize and shut down your VM before you perform the capture operation. If you attempt to capture a running VM, you effectively take a snapshot of that VM to create a specialized image, but you risk not capturing any changes that are currently in the running VM’s memory because this state is not captured.</li>
	<li>With the Save-AzureImage cmdlet, you indicate that the VM has been generalized by providing an OSState parameter with a value of Generalized. Otherwise, you provide a value of Specialized. Note that when the cmdlet finishes, the target VM is deleted.</li>
	<li>To create instances of your VM image in a region different than the one where the storage account containing the VM image exists, copy the VM image to Storage Accounts in the target region. To accomplish this effectively, consider using the AZCopy utility. You can download this utility from <a href="http://azure.microsoft.com/en-us/documentation/articles/storage-use-azcopy/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/storage-use-azcopy/</a>.</li>
	<li>When you create a new VM in the existing portal or Preview portal, the VM Agent is installed by default</li>
	<li>Exam Tip: After the DSC runs, a Managed Object Format (MOF) file is created, which is a standard endorsed by the Distributed Management Task Force (DTMF). See <a href="http://www.dmtf.org/education/mof" target="_blank">http://www.dmtf.org/education/mof</a>.</li>
	<li>DSC Resource Kit
The Windows PowerShell team released a number of DSC resources to simplify working with Active Directory, SQL Server, and IIS. See <a href="https://gallery.technet.microsoft.com/DSC-Resource-Kit-All-c449312d" target="_blank">https://gallery.technet.microsoft.com/DSC-Resource-Kit-All-c449312d</a>.</li>
	<li>Adding Resources to the zip File
When you build your configuration zip using Publish-AzureVMDSCConfiguration, it will not automatically include the resources you specify, for example additional Windows PowerShell module dependencies or any files or folders that you intend to deploy. You must add those manually to the zip file before configuring the VM with the DSC script.</li>
	<li>Be sure to use an instance size minimum of A2 to support the puppet master extension.</li>
	<li>Exam Tip: If you supply the wrong fully qualified address to the puppet master node during this configuration process, the agent will not automatically register with the puppet master node. If this happens, to fix the address, you must manually edit the Puppet agent configuration on the machine and manually send a registration request from a remote desktop session.
See the guide, “Getting Started Guide: Deploying Puppet Enterprise in Microsoft Azure” at <a href="http://info.puppetlabs.com/pe-azure-gsg.html" target="_blank">http://info.puppetlabs.com/pe-azure-gsg.html</a> for additional details on these steps.</li>
	<li>Introduction to Puppet
If you are new to Puppet, you can start learning more about it with the documentation at <a href="https://docs.puppetlabs.com/guides/introduction.html" target="_blank">https://docs.puppetlabs.com/guides/introduction.html</a>.</li>
	<li>Chef Setup on Azure
The following references provide additional information related to learning Chef and for setting up Chef on Azure:
<a href="http://learn.getchef.com/" target="_blank">http://learn.getchef.com/</a>
<a href="https://www.getchef.com/partners/microsoft/" target="_blank">https://www.getchef.com/partners/microsoft/</a></li>
	<li>Exam Tip: From your Chef workstation, you can run Chef knife commands to generate the client.rb and validation.pem key for the final step in the previous procedure. For more information about the Azure portal settings, see <a href="https://docs.getchef.com/azure_portal.html" target="_blank">https://docs.getchef.com/azure_portal.html</a>.</li>
	<li>This DNS name resolves to the public virtual IP address of the cloud service, and after the cloud service has been created, the DNS name cannot be changed</li>
	<li>To assign a PIP to your VM, first ensure that your VM is deployed to a regional virtual network (VNET) since a PIP cannot be assigned to VMs that do not belong to a VNET</li>
	<li>If you want to ensure that the IP address remains fixed and reflected as being owned by your Azure subscription, even if the cloud service it is associated with is deleted, then you need to configure a reserved IP address.</li>
	<li>To use a reserved IP address with a VM, you must request it as a part of creating both a new cloud service and new VM. There is currently no support for assigning a reserved IP address to an existing cloud service and VM.</li>
	<li>A network access control list (ACL) allows you to restrict access to your VMs to specific ranges of IP addresses by defining a list of permit or deny rules. They perform packet filtering on the host node running your VM, controlling what external traffic is allowed to reach it via the endpoint. They are defined on a VM endpoint or load balanced set and apply only to external traffic (for example, traffic that flows through the VIP and load balancer). They are not applied to internal traffic and cannot be applied to a VNET or to a subnet within a VNET.</li>
	<li>ACL rule evaluation proceeds in priority order, where rules with the lowest order value have highest priority and are evaluated before rules with higher order values that have a lower priority. The first rule to match the traffic in the list, if there is a match, is applied and stops further rule evaluation.</li>
	<li>Exam Tip: You can use ACL to restrict access to a single host instead of the many hosts that would be described by an IP address range. To do so, when specifying the remote subnet, use the /32 subnet mask, for example 70.0.0.1/32.</li>
	<li>Load balanced endpoints (public or internal) is functionality available only to VMs in the Standard tier and not to VMs in the Basic tier.</li>
	<li>DSR changes the last two steps of this process and enables the VM to return the response directly to the client instead of sending it through the load balancer. DSR is most commonly needed to support SQL Server AlwaysOn Availability Groups.</li>
	<li>Direct Server Return can be enabled only during the creation of an endpoint, and it requires that the public and private ports have the same value.</li>
	<li>Unlike Websites which can automatically provision new instances as a part of scale out, Virtual Machines must be pre-provisioned in order for auto-scale to turn instances on or off during a scaling operation</li>
	<li>Availability sets enable you to improve the availability of VMs deployed to your cloud service by identifying to Azure a group of VMs that should never be brought down simultaneously during updates and that should be physically separated (that is, connected to a separate power source and network switch) so that the failure of a host does not cause all of the VMs in that group to fail.</li>
	<li>VMs located in separate update domains will never experience an update (or a restart of the host machine) at the same time</li>
	<li>Azure provides a fixed set of five update domains in which it places your VMs in a round-robin process. When you add VMs to an availability set, Azure places the first five VMs in separate update domains, then continues to distribute additional VMs across update domains in a round-robin fashion, assigning the sixth VM to the first update domain, the seventh VM to the second update domain, and so on until all VMs have been assigned to one of the five update domains.</li>
	<li>Whereas update domains apply to the roll out of host machine updates, fault domains consider isolation in terms of power and network. When two VMs are placed in separate fault domains, they will never be located such that they share the power source or network switch, which basically means that they will not be on the same host machine or even on the same server rack as one another. When you add VMs to an availability set, they are distributed between two fault domains in round-robin fashion</li>
	<li>For multi-tier applications (such as those having separate front-end, middle, and back-end tiers), it is a best practice to place all the VMs belonging to a single tier in a single availability set and to have separate availability sets for each application tier</li>
	<li>The primary requirement of an availability set is that all member VMs must belong to the same cloud service.</li>
	<li>Auto-scale automatically adjusts the number of VM instances running within an availability set based on load or according to a schedule. It does this by turning on additional VM instances in the availability set during a scale-up event, and stopping (de-allocating) them during a scale-down event. For this to happen, these machines must have already been provisioned, but they can be in the stopped (de-allocated) state as they wait for auto-scale to turn them on</li>
	<li>Using auto-scale is predicated upon a few requirements. To begin, all VMs involved must be in the Standard tier (the Basic tier does not provide auto-scale support). All the VMs you want to turn on or off with auto-scale must belong to the same availability set, and because you cannot create a single availability set that includes VMs spanning multiple cloud services, these VMs must also exist within the same cloud service. Also, all VMs in the availability set must be of the same instance size or you will be prevented from configuring auto-scale.</li>
	<li>Azure Storage can provide a higher rate of random I/Os than the local disk used for caching. For predominantly random I/O workloads, therefore, it is best to set the cache to None and let Azure Storage handle the load directly</li>
	<li>Note that geo-replication is not synchronized across blob files and, therefore, VHD disks, which means writes for a file that is spread across multiple disks, as happens when you use storage pools, could be replicated out of order. As a result, if you mount the replicated copies to a VM, the disks will almost certainly be corrupt. To avoid this problem, configure the disks to use locally redundant replication which does not add any additional availability and reduces costs (since geo-replicated storage is more expensive).</li>
	<li>It does not matter if your VMs’ data disks are located in a different storage account or even if your share uses a storage account that is within a different Azure subscription than your VMs. As long as your shares are created within the same region as your VMs, those VMs will have access.</li>
	<li>Note that currently this means you cannot mount shares across regions (even if you set up VNET-to-VNET connectivity) or access shares from your on-premises resources (if you are using a point-to-site or site-to-site VPN with a VNET).</li>
	<li>Naming Requirements
Interestingly, while Blob storage is case sensitive, share, directory, and file names are case insensitive but will preserve the case you use. For more information, see <a href="http://msdn.microsoft.com/en-us/library/azure/dn167011.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn167011.aspx</a>.</li>
	<li>Note that you cannot create a share below another share</li>
	<li>File Lock Interaction between SMB and REST
If you are curious about how file locking is managed between SMB and REST endpoints for clients interacting with the same file at the same time, the following is a good resource for more information: <a href="http://msdn.microsoft.com/en-us/library/azure/dn194265.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn194265.aspx</a>.</li>
	<li>You can mount a share to a VM so that it will remain available indefinitely to the VM, regardless of restarts.</li>
	<li>Geo-replication should not be used for Azure Storage accounts that store VHDs because the added redundancy does not provide additional protection against corrupting the data and may in fact result in data loss if you attempt to restore from a geo-replication</li>
</ul>
&nbsp;
<h3>Chapter 03: Design and Implement Cloud Services</h3>
<div>
<ul>
	<li>When the install completes, the SDK installs two emulators, the Azure Compute Emulator and the Azure Storage Emulator.</li>
	<li>Cloud Services supports two kinds of roles:
<ul>
	<li>Web roles Used for web server applications hosted in IIS, such as an ASP.NET MVC application or a Web API application</li>
	<li>Worker roles Used for running a compute workload. It can be used to launch an executable process or for background worker implementations that work in a similar manner to a Windows service.</li>
</ul>
</li>
	<li>Exam Tip: PaaS cloud services discussed in this chapter are conceptually different from IaaS cloud services discussed in Chapter 2, “Create and manage virtual machines.” With PaaS cloud services, you are entrusting Azure to manage the operating system updates, patching, and deployment lifecycle of your applications. IaaS cloud services are a mechanism for grouping assets in your VM topology.</li>
	<li>The cloud service template should be the startup project in the solution. It references the roles associated with the cloud service and holds the configuration settings for each role</li>
	<li>By default, adding multiple roles will result in multiple VMs. Each role then operates in isolation with its own configuration settings. It is possible to configure multiple roles to deploy to a single VM.</li>
	<li>Note: Role Entry Point and Web Roles
You are not required to modify the default implementation of RoleEntryPoint for a web role; however, it is common to add code that interacts with the RoleEnvironment. For example, you can write code to interact with role lifecycle events such as preventing a restart for certain configuration setting changes.</li>
	<li>Consider putting some key configuration settings in the role configuration settings instead of in the web.config application settings. This makes it possible to surface those settings to the management portal for modification.</li>
	<li>If your application has any dependencies that require installation on the destination VM or control over IIS-related settings, use a startup task to provide an unattended deployment for this configuration.</li>
	<li>More Info: Resilient Cloud Architectures
The following reference provides additional insights, some specific to Azure, regarding designing resilient architectures for the cloud: <a href="http://msdn.microsoft.com/library/azure/jj853352.aspx" target="_blank">http://msdn.microsoft.com/library/azure/jj853352.aspx</a>.</li>
	<li>More Info: Logging from Startup Tasks
Visibility into your startup task process is important if there are issues that require troubleshooting. Log activity from your startup tasks to help with this. For more information on this and other helpful tips, see <a href="http://msdn.microsoft.com/en-us/library/azure/jj129545.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj129545.aspx</a>.</li>
	<li>More Info: Examples of Startup Task Implementations
See the following reference for an example of how to create batch files that run Windows PowerShell scripts and initialize IIS settings: <a href="http://msdn.microsoft.com/en-us/library/azure/hh180155.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/hh180155.aspx</a>.</li>
	<li>Add an executionContext attribute with the value “limited” or “elevated.” If you add “limited,” the task will run without administrator privileges. If you use “elevated,” the task will run with administrator privileges and be able to modify the registry, change IIS configurations, and interact with other protected resources</li>
	<li>More Info: Startup Tasks and Role Recycling
Startup tasks must be designed to run more than once for the role VM. When roles restart, the startup tasks run again. For information on how to design startup tasks for graceful restarts, see <a href="http://msdn.microsoft.com/en-us/library/azure/jj129544.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj129544.aspx</a>.</li>
	<li>Unlike websites and VMs, whose instance size can be adjusted through the management portal, scaling the instance size of a role instance requires that you change the cloud service definition and re-deploy the package</li>
	<li>Also note that you can combine schedule-based and metric-based scaling. When you define a schedule and then select it from the Edit Scale Settings For Schedule drop-down list, you can configure scaling by CPU or by queue conditions within the timeframe represented by that schedule</li>
	<li>Each OnlyAllowTrafficTo element describes the source role endpoint and destination role endpoint for which communication should be allowed; any other combinations will be denied.</li>
	<li>More Info: NetworkTrafficRules Schema
For a complete explanation of the NetworkTrafficRules schema, see <a href="http://msdn.microsoft.com/en-us/library/azure/gg557551.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/gg557551.aspx</a></li>
	<li>More Info: NetworkConfiguration Schema
For the complete schema documentation of the NetworkConfiguration element, see <a href="http://msdn.microsoft.com/en-us/library/azure/jj156091.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj156091.aspx</a>.</li>
	<li>Important: ACL updates and deployments
Currently, you must perform a complete re-deployment if you enable ACLs on a service that already exists. An update deployment will fail with an error.</li>
	<li>To join a role to a particular subnet in a virtual network requires two major steps, both performed by adding configuration within the NetworkConfiguration element</li>
	<li>First, you must associate the cloud service with a virtual network. This is accomplished by adding a VirtualNetworkSite element and specifying the name of the virtual network as the value for the name attribute.</li>
	<li>Second, you need to add an AddressAssignments element that contains one InstanceAddress element for each role in the cloud service. The InstanceAddress element is associated with the role by the value specified for the roleName attribute (whose value must be the name of the role). Within the InstanceAddress element, specify a &lt;Subnets&gt; element that will contain a &lt;Subnet&gt; entry whose name attribute indicates the name of the subnet in the virtual network in which instances of the role shall be placed</li>
	<li>Before you can configure a reserved IP on a cloud service, you need to create a reserved IP in your Azure subscription</li>
	<li>Local storage can persist between restarts of the VM that hosts your role. The data will be lost if your role is migrated to a different VM host. If you require durability, you should use Azure Blob storage</li>
	<li>It is important to be aware of disk space management. If you reach your maximum size of local storage, when you attempt to write again, you will get an out of disk space error message. Note that on the Local Storage configuration tab, you can configure a disk space that is higher than that allotted to your chosen role VM size. No error will be generated until the disk actually fills past the capacity allotted. Always have a method for deleting old files and clearing out space so that writing can continue.</li>
	<li>A single web role is not limited to hosting only a single website. By differentiating between websites using either host headers, a single web role can be configured, by editing the cloud service definition, to host multiple websites.</li>
	<li>The key difference between the two is that an A record maps a domain to an IP address and a CNAME creates an alias that maps a domain name to another domain name.</li>
	<li>When using an A record, you have to be cautious that the IP address value you map to does not change, because if it does, your custom domain will not resolve to your cloud service</li>
	<li>It is a best practice to deploy to the staging slot first and then perform a VIP swap operation that moves your new deployment into production to ensure you don’t lose the VIP associated with production.</li>
	<li>Another way to preserve the IP address of the cloud service is to assign a reserved IP to your cloud service and then use that IP address in the A record.</li>
	<li>If you a have a cloud service with a web role, a worker role, and a cacherole, only instances from those three roles can access the cache, in particular, VMs and websites cannot access the cache provided by In-Role Cache.</li>
	<li>Note: RoleEntryPoint Code within a Web Role
If you are attempting to use the cache within a web role’s RoleEntryPoint logic (for example in WebRole.cs) as opposed to within ASP.NET code behind files, then you must programmatically configure the cache instead of relying on the web.config to provide the settings. See the following link for examples on how to do so: <a href="http://msdn.microsoft.com/en-us/library/azure/jj852128.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj852128.aspx</a>.</li>
	<li>When you deploy to Azure using a package, you deploy two files: the application package file and the service configuration file.</li>
	<li>When considering the incremental update option, the most influential setting is the upgradeDomainCount, which sets the number of upgrade domains into which your role instances are distributed. By default, this is set to 5 (such that your instances will be distributed across five upgrade domains), but you can increase that value up to 20.</li>
	<li>When deciding whether to perform an upgrade deployment (either incremental or simultaneous) or a full deployment, note that any of the following changes require a full deployment (or the VIP swap approach, discussed later); you will not be able to perform an upgrade for these changes:
<ul>
	<li>Change to the name of a role</li>
	<li>Change to the upgrade domain count</li>
	<li>Reduction in the size of local storage resources</li>
</ul>
</li>
	<li>More Info: Supported Changes for an Upgrade
For a list of all of the changes that you can make to a deployment and still perform an upgrade, see <a href="http://msdn.microsoft.com/en-us/library/azure/hh472157.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/hh472157.aspx</a>.</li>
	<li>More Info: Diagnostic Data Sources
For a more detailed description of each of the diagnostic data sources, see <a href="http://msdn.microsoft.com/en-us/library/dn205075.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/dn205075.aspx</a>.</li>
	<li>As of the Azure SDK 2.5, the only supported mechanism for configuring diagnostics is by using the XML configuration file diagnostics.wadcfgx</li>
	<li>More Info: Manually Querying Diagnostics
For tools and instructions for manually querying the diagnostics data, see <a href="http://msdn.microsoft.com/en-us/library/hh411534.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/hh411534.aspx</a>.</li>
	<li>Important: How Debugging Affects your Cloud Service
When you attach the debugger and pause at a breakpoint, you are stopping the deployed instance for all requests, so it is not a good idea to rely on this technique for production debugging or users will think your cloud service is down. Also, if you spend more than a few minutes stopped at any one breakpoint, Azure treats the process that is stopped as unavailable and does not send traffic to that instance. Furthermore, if you are stopped too long, the remote debugger service (msvsmon.exe) detaches from the process.</li>
	<li>Note: Intellitrace Requirements
IntelliTrace requires you to use Visual Studio Ultimate against a cloud service that is running an application built with .NET 4 or .NET 4.5.</li>
</ul>
&nbsp;
<h3>Chapter 04: Design and Implement A Storage Strategy</h3>
<div>
<ul>
	<li>Azure Storage enables storage and retrieval of large amounts of unstructured data. You can store content files such as documents and media in the Blob service, use the Table service for NoSQL data, use the Queue service for reliable messages, and use the File service for Server Message Block (SMB) file share scenarios</li>
	<li>Exam Tip: There are many ways to interact with and develop against Azure Storage including the management portal, using Windows PowerShell, using client libraries such as those for the .NET Framework, and using the Storage Services REST API. In fact, the REST API is what supports all other options.</li>
	<li>Each blob storage account can store up to 500 terabytes of data.</li>
	<li>Note: Container Access Permissions
You can choose between the following access permissions on the container:
Private All access to the container and its blobs require authentication.
Public Container All access to the container and its blobs are anonymous.
Public Blob You cannot list blobs in the container without authentication, but you can navigate to the blob URL, if you have it, and read it anonymously.
This setting can be changed at any time through the management portal, by using Windows PowerShell, or by configuring it programmatically.</li>
	<li>Always use the primary key for management activities</li>
	<li>Exam Tip: Any updates made to a blob are atomic. While an update is in progress, requests to the blob URL will always return the previously committed version of the blob until the update is complete.</li>
	<li>A container has only read-only system properties, while blobs have both read-only and read-write properties.</li>
	<li>More Info: Blob Metadata
Blob metadata includes both read-only and read-write properties that are valid HTTP headers and follow restrictions governing HTTP headers. The total size of the metadata is limited to 8 KB for the combination of name and value pairs. For more information on interacting with individual blob metadata, see <a href="http://msdn.microsoft.com/en-us/library/azure/hh225342.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/hh225342.aspx</a>.</li>
	<li>Exam Tip: If the metadata key doesn’t exist, an exception is thrown</li>
	<li>The Azure Blob service has two different ways of storing your data: block blobs and page blobs. Block blobs are great for streaming data sequentially, like video and other files. Page blobs are great for non-sequential reads and writes, like the VHD on a hard disk mentioned in earlier chapters.</li>
	<li>Any blocks you upload that aren’t committed to a blob will be deleted after a week. Block blobs can be up to 200 GB.</li>
	<li>Unlike block blobs, page blob writes are done in place and are immediately committed to the file. The maximum size of a page blob is 1 terabyte.</li>
	<li>To authorize access to content, you can authenticate in three different ways to your storage account and content:
<ul>
	<li>Shared Key Constructed from a set of fields related to the request. Computed with a SHA-256 algorithm and encoded in Base64.</li>
	<li>Shared Key Lite Similar to Shared Key, but compatible with previous versions of Azure Storage. This provides backwards compatibility with code that was written against versions prior to 19 September 2009. This allows for migration to newer versions with minimal changes.</li>
	<li>Shared Access Signature Grants restricted access rights to containers and blobs. You can provide a shared access signature to users you don’t trust with your storage account key. You can give them a shared access signature that will grant them specific permissions to the resource for a specified amount of time.</li>
</ul>
</li>
	<li>The copy operation is always the entire length of the blob; you can’t copy a range.</li>
	<li>Exam Tip: A storage account can have multiple Copy Blob operations processing in parallel; however, an individual blob can have only one pending copy operation.</li>
	<li>By default, blobs have a seven-day time-to-live (TTL) at the CDN edge node. After that time elapses, the blob is refreshed from the storage account to the edge node. Blobs that are shared via CDN must support anonymous access.</li>
	<li>Exam Tip: It can take 60 minutes before the CDN is ready for use on the storage account.</li>
	<li>A blob container has several options for access permissions. When set to Private, all access requires credentials. When set to Public Container, no credentials are required to access the container and its blobs. When set to Public Blob, only blobs can be accessed without credentials if the full URL is known.</li>
	<li>Azure Storage is a non-relational (NoSQL) entity storage service on Microsoft Azure. When you create a storage account, it includes the Table service alongside the Blob and Queue services. Table services can be accessed through a URL format</li>
	<li>You can group inserts and other operations into a single batch transaction. All operations in the batch must take place on the same partition. You can have up to 100 entities in a batch. The total batch payload size cannot be greater than 4 MB</li>
	<li>Wherever possible, you should try to query with the partition key and row key. Querying entities by other properties does not work well because it launches a scan of the entire table.</li>
	<li>One technique you can use to update a record is to use InsertOrReplace(). This creates the record if one does not already exist or updates an existing record</li>
	<li>Table storage does not support anonymous access, so you must supply credentials using the account key or a Shared Access Signature (SAS) (discussed in “Manage Access”) before you can perform requests using OData.</li>
	<li>Note: Query Limitations
The result is limited to 1,000 entities per request, and the query will run for a maximum of five seconds.</li>
	<li>For query performance, you should use the partition key and row key together when possible. This leads to an exact row match. The next best thing is to have an exact partition match with a row range. It is best to avoid scanning the entire table.</li>
	<li>More Info: Large Messages
There is a limit of 64 KB per message stored in a queue. It is considered best practice to keep the message small and to store any required data for processing in a durable store, such as SQL Azure, storage tables, or storage blobs. This also increases system reliability since each queued message can expire after seven days if not processed. For more information, see the reference at <a href="http://msdn.microsoft.com/en-us/library/azure/hh690942.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/hh690942.aspx</a>.</li>
	<li>Note: Invisibility Setting
By default, when you de-queue a message, it is invisible to the queue for 30 seconds. In the event message processing exceeds this timeframe, supply an alternate setting for this value when creating or updating the message. You can set the timeout to a value between one second and seven days. Visibility can also exceed the message expiry time.</li>
	<li>You can retrieve up to 32 messages from a queue using the GetMessages() method to process multiple messages in parallel</li>
	<li>Each individual queue has a target of approximately 2,000 messages per second (assuming a message is within 1 KB).</li>
	<li>More Info: Controlling Anonymous Access
To control anonymous access to containers and blobs, follow the instructions provided at <a href="http://msdn.microsoft.com/en-us/library/azure/dd179354.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dd179354.aspx</a>.</li>
	<li>Important: Secure Use of SAS
Always use a secure HTTPS connection to generate an SAS token to protect the exchange of the URI, which grants access to protected storage resources.</li>
	<li>When you extend write access to storage resources with SAS, the contents of those resources can potentially be made corrupt or even be tampered with by a malicious party, particularly if the SAS was leaked. Be sure to validate system use of all resources exposed with SAS keys.</li>
	<li>The stored access policy can be used to control all issued SAS tokens that are based on the policy. For a step-by-step tutorial for creating and testing stored access policies for blobs, queues, and tables, see <a href="http://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-2" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-2</a>.</li>
	<li>Important: Recommendation for SAS Tokens
Use stored access policies wherever possible, or limit the lifetime of SAS tokens to avoid malicious use</li>
	<li>Important: Managing Key Regeneration
It is imperative that you have a sound key management strategy. In particular, you must be certain that all applications are using the primary key at a given point in time to facilitate the regeneration process.</li>
	<li>When you configure storage metrics for a storage account, tables are generated to store the output of metrics collection</li>
	<li>Retention can be configured for each service in the storage account. By default, Storage Analytics will not delete any metrics data. When the shared 20-terabyte limit is reached, new data cannot be written until space is freed. This limit is independent of the storage limit of the account. You can specify a retention period from 0 to 365 days. Metrics data is automatically deleted when the retention period is reached for the entry.</li>
	<li>Note: Choosing a Metrics Level
Minimal metrics yield enough information to provide a picture of the overall usage and health of the storage account services. Verbose metrics provide more insight at the API level, allowing for deeper analysis of activities and issues, which is helpful for troubleshooting.</li>
	<li>Note: Deleting the Log Container
After Storage Analytics has been enabled, the log container cannot be deleted; however, the contents of the log container can be deleted.</li>
	<li>The major difference is in a measurement called database throughput units (DTUs). A DTU is a blended measure of CPU, memory, disk reads, and disk writes.</li>
	<li>Add the following metrics:
<ul>
	<li>CPU Percentage</li>
	<li>Physical Data Reads Percentage</li>
	<li>Log Writes Percentage</li>
	<li>All three of these metrics are shown relative to the DTU of your database. If you reach 80 percent of your performance metrics, it’s time to consider increasing your service tier or performance level</li>
</ul>
</li>
	<li>Azure SQL Database does a full backup every week, a differential backup each day, and an incremental log backup every five minutes</li>
	<li>When you restore a new database, the service tier stays the same, but the performance level changes to the minimum level of that tier.</li>
	<li>Standard geo-replication allows the user to fail over the database to a different region when a database is not available. It is available on the standard and premium service tiers. The main difference between active and standard geo-replication is that standard geo-replication does not allow clients to connect to the secondary server. It is offline until it’s needed to take over for the primary. The target region for the offline secondary server is pre-determined. For instance, if your primary server is in North Central US, then your secondary server will be in South Central US. The source and target servers must belong to the same subscription.</li>
	<li>Note: Uses for Creating an Offline Secondary
Another use for this feature has to do with the ability to terminate the continuous copy relationship between a primary and secondary database. You can terminate the relationship and then upgrade the primary database to a different schema to support a software upgrade. The secondary database gives you a rollback option.</li>
</ul>
&nbsp;
<h3>Chapter 05: Manage Application And Network Services</h3>
<div>
<ul>
	<li>More Info: Directory Integration
For additional information on directory integration, Azure AD Sync, and Azure AD Connect see <a href="http://msdn.microsoft.com/en-us/library/azure/jj573653.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj573653.aspx</a>.</li>
	<li>More Info: Multi-Factor Authentication
Azure AD makes it easy to enable multi-factor authentication for users in your directory. For additional information, see <a href="http://azure.microsoft.com/en-us/documentation/services/multi-factor-authentication/" target="_blank">http://azure.microsoft.com/en-us/documentation/services/multi-factor-authentication/</a>.</li>
	<li>More Info: Administrator Roles
For additional information about directory administrator roles, see <a href="http://msdn.microsoft.com/en-us/library/azure/dn468213.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn468213.aspx</a>.</li>
	<li>More Info: User Management
For additional information about managing users from the management portal, see <a href="http://msdn.microsoft.com/en-us/library/azure/hh967609.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/hh967609.aspx</a>.</li>
	<li>More Info: Authentication Scenarios
See the following reference for a review of these key authentication scenarios with related sample applications: <a href="http://msdn.microsoft.com/en-us/library/azure/dn499820.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn499820.aspx</a>.</li>
	<li>More Info: Azure AD Code Samples
Integration between applications and Azure AD involves selecting a protocol for user authentication and for specific application authorization scenarios and choosing components for your application platform to simplify working with protocols. The following reference has many authentication and authorization samples to help you apply the review in this section to code, illustrating the most common integration scenarios: <a href="http://msdn.microsoft.com/en-us/library/azure/dn646737.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn646737.aspx</a>.</li>
	<li>Exam Tip: You can substitute the tenant identifier with the tenant name for protocol endpoint URLs. See, for example, <a href="https://login.windows.net/solexpaad.onmicrosoft.com/wsfed" target="_blank">https://login.windows.net/solexpaad.onmicrosoft.com/wsfed</a>.</li>
	<li>More Info: Moving a VM to an Existing Network
You can move a VM to a previously created virtual network, but it requires some downtime. Virtual networks are typically chosen when you create a VM. To change the virtual network of an existing VM, you can remove it from the first network and then create a new VM with the same VHD as part of the new network. There is no method to move the VM itself to a different network after it is created.
When you remove an existing VM from a network, the VHD is still attached and registered as a disk in the management portal. When you create a new VM, you can select that disk under My Disks in the management portal to reuse it.</li>
	<li>Exam Tip: Using shared DNS servers with a virtual network allows resources on the network to use a DNS server that you specify. You can use one that Azure provides, but if you need more control over DNS settings, or if you have needs outside normal, you can specify your own DNS servers. DNS servers are not round-robin load balanced. The first DNS server on the list will always be used unless it is unavailable, in which case then the next one will be used.</li>
	<li>More Info: NetworkConfiguration Section
For a complete set of options for cloud services network configuration settings, see <a href="http://msdn.microsoft.com/en-us/library/azure/jj156091.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj156091.aspx</a>.</li>
	<li>Exam Tip: You cannot modify or delete a subnet after services or VMs have been deployed to it. You can modify prefixes as long as the subnets containing existing VMs or services are not affected by the change.</li>
	<li>More Info: Service Bus Resources and Samples
See these references for a collection of overviews, tutorials, and samples related to Service Bus:
<a href="http://msdn.microsoft.com/en-us/library/azure/ee732537.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/ee732537.aspx</a>
<a href="http://msdn.microsoft.com/en-us/library/azure/dn194201.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn194201.aspx</a></li>
	<li>More Info: Securing Service Bus Resources
The recommended way to secure Service Bus resources is with SAS tokens, so by default, an ACS namespace is not created. With Windows PowerShell commands, you can indicate an ACS namespace for securing the resources in the namespace. For more information on securing Service Bus resources, see <a href="http://msdn.microsoft.com/en-us/library/azure/dn170478.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn170478.aspx</a>.</li>
	<li>More Info: AMQP Protocol
Advanced Message Queuing Protocol (AMQP) is the recommended protocol to use for brokered message exchange if firewall rules are not an issue. For additional information, see <a href="http://msdn.microsoft.com/en-us/library/azure/jj841071.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj841071.aspx</a>.</li>
	<li>Exam Tip: Connectivity issues are common for on-premises environments that disable ports other than 80 and 443. For this reason, it is still often necessary for portability to use HTTP protocol for brokered messaging.</li>
	<li>Exam Tip: TCP relay supports two connection modes: relayed (the default) or hybrid. In hybrid mode, communications are initially relayed, but if possible, a direct socket connection is established between client and service, thus removing the relay from communications for the session.</li>
	<li>It is not recommended to use the root shared access policy. Instead, create an entry for a receiver and sender policy that respectively can only listen or send.</li>
	<li>Note: Sender and Receiver Keys
It is considered best practice to create separate keys for the sender and receiver, and possibly multiple keys according to different groups of senders and receivers. This allows you to more granularly control which applications have send, receive, and management rights to Service Bus relays created in the namespace.</li>
	<li>Exam Tip: You can configure WCF relay endpoints programmatically or by using application configuration in the &lt;system.servicemodel&gt; section. The latter is more appropriate for dynamically configuring the host environment for production applications.</li>
	<li>More Info: Azure Queues vs. Service Bus Queues
Azure queues (discussed in Chapter 4, “Design and implement a storage strategy”) are built on top of storage, while Service Bus queues are built on top of a broader messaging infrastructure. For more information on how the two compare, and how to choose between them, see <a href="http://msdn.microsoft.com/en-us/library/azure/hh767287.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/hh767287.aspx</a>.</li>
	<li>There are no direct commands for creating and deleting Service Bus queues; however, you can construct a custom Windows PowerShell script that includes code to produce a queue programmatically. For more information, see <a href="http://blogs.msdn.com/b/paolos/archive/2014/12/02/how-to-create-a-service-bus-queues-topics-and-subscriptions-using-a-powershell-script.aspx" target="_blank">http://blogs.msdn.com/b/paolos/archive/2014/12/02/how-to-create-a-service-bus-queues-topics-and-subscriptions-using-a-powershell-script.aspx</a>.</li>
	<li>Exam Tip: The connection string shown in the management portal for queues, topics, notification hubs, and event hubs does not use AMQP protocol by default. You must add a TransportType=Amqp string as follows to tell the client library to use this recommended protocol</li>
	<li>Exam Tip: The BrokeredMessage type can accept any serializable object or a stream to be included in the body of the message. You can also set additional custom properties on the message and provide settings relevant to partitions and sessions.</li>
	<li>Note: Duplicate Messages
Service Bus queues support at-least-once processing. This means that under certain circumstances, a message might be redelivered and processed twice. To avoid duplicate messages, you can use the MessageId of the message to verify that a message was not already processed by your system.</li>
	<li>More Info: Dead Letter Queues
Messages that cannot be processed are considered poison messages and should be removed from the queue and handled separately. This is typically done with a dead letter queue. Service Bus queues have a dead letter sub-queue available for this purpose. You write to the dead letter sub-queue when you detect a poison message and provide a separate service to process those failures. Messages written to the dead letter sub-queue do not expire. For a sample, see <a href="https://code.msdn.microsoft.com/windowsazure/Brokered-Messaging-Dead-22536dd8#content" target="_blank">https://code.msdn.microsoft.com/windowsazure/Brokered-Messaging-Dead-22536dd8#content</a>.</li>
	<li>Exam Tip: If you enable batch processing for the subscription, you can receive a batch of messages in a single call using ReceiveBatch() or ReceiveBatchAsync(). This will pull messages in the subscription up to the number you specify, or fewer if applicable. Note that you must be aware of the potential lock timeout while processing the batch.</li>
	<li>You cannot create a subscription with filter criteria through the management portal, but you can create it programmatically using the NamespaceManager object and its CreateSubscription() method.</li>
	<li>Exam Tip: Event hubs can by default handle 1-MB ingress per second, 2-MB egress per second per partition. This can be increased to 1-GB ingress per second and 2-GB egress per second through a support ticket.</li>
	<li>Exam Tip: You can create between 8 and 32 partitions, but with a support ticket you can increase that number up to 1,024.</li>
	<li>Exam Tip: By default, there are no shared access policies created for a new event hub. You will usually create at least one policy for each receiver and one for send permissions to separate key access between clients and services.</li>
	<li>Note: Partitions and Partition Keys
You can optionally supply a partition key to group event data so that the data is collected in the same partition in sequence. Otherwise, data is sent in a round-robin fashion across partitions. In addition, you can supply custom properties and a sequence number to event data prior to sending</li>
	<li>Consumer Groups
A default consumer group is created for each new event hub, but you can optionally create multiple consumer groups (receivers) to consume events in parallel.</li>
	<li>For a set of tutorials with steps for each platform supported, including the steps for setting up the mobile application, the back-end application, and the notification hub, see <a href="http://azure.microsoft.com/en-us/documentation/articles/notification-hubs-windows-store-dotnet-get-started" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/notification-hubs-windows-store-dotnet-get-started</a>.</li>
	<li>Notification Hub Guides
The following references provide additional background and programming guidance for notification hubs and mobile services:
<ul>
	<li>Notification hubs overview and tutorials: <a href="http://msdn.microsoft.com/en-us/library/azure/jj891130.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj891130.aspx</a></li>
	<li>Notification hubs documentation: <a href="http://azure.microsoft.com/en-us/documentation/services/notification-hubs/" target="_blank">http://azure.microsoft.com/en-us/documentation/services/notification-hubs/</a></li>
	<li>Mobile services documentation: <a href="http://azure.microsoft.com/en-us/documentation/services/mobile-services/" target="_blank">http://azure.microsoft.com/en-us/documentation/services/mobile-services/</a></li>
</ul>
</li>
	<li>Exam Tip: Relay services can be replaced with queues or topics to provide greater throughput, scalability, and design flexibility.</li>
	<li>When you create a new queue or topic, you must choose the maximum expected storage from 1 GB to 5 GB, and this cannot be resized. This impacts the amount of concurrent storage supported as messages flow through Service Bus.</li>
	<li>Exam Tip: You can request additional throughput units for a namespace by calling Microsoft support.</li>
	<li>Service Bus Explorer is a tool used for managing and monitoring Service Bus features such as queues, topics, relays, and notification hubs. While you can use the management portal to monitor basic communication statistics, this tool can provide additional insights. For tutorials and to access the source code, see <a href="https://code.msdn.microsoft.com/windowsazure/Service-Bus-Explorer-f2abca5a" target="_blank">https://code.msdn.microsoft.com/windowsazure/Service-Bus-Explorer-f2abca5a</a>.</li>
	<li>Exam Tip: The large Redis Cache size is 53 GB.</li>
	<li>Exam Tip: You can add any non-primitive type to the cache when it is serialized. Use any of your favorite serializers, such as JSON format, and then store the result as a string with StringSet(). When you retrieve it, use the same serializer to de-serialize the value after StringGet().</li>
	<li>Exam Tip: Azure Managed Cache Service can only be created using Windows PowerShell cmdlets. You can then manage the cache settings from the management portal.</li>
</ul>
</div>
</div>
</div>
</div>
</div>
