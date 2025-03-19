---
layout: page
title: Book Review: Exam Ref 70-533 Implementing Microsoft Azure Infrastructure Solutions
date: 2015-07-07 08:27
author: AdinErmie
comments: true
categories: []
---
<a href="http://adinermie.com/wp-content/uploads/2015/07/ExamRef70533AzureInfraCover.jpg"><img class=" size-full wp-image-14301 alignleft" src="http://adinermie.com/wp-content/uploads/2015/07/ExamRef70533AzureInfraCover.jpg" alt="ExamRef70533AzureInfraCover" width="201" height="244" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2015/03/09/new-book-exam-ref-70-533-implementing-microsoft-azure-infrastructure-solutions.aspx" target="_blank">Exam Ref 70-533 Implementing Microsoft Azure Infrastructure Solutions</a> eBook.

The chapter(s) that I found most helpful were basically all of them! Hence the majority of my highlights are from basically the entire book. Note that I didn't just highlight all of the "Exam Tip" content, but also additional information that I found useful in learning and understanding the topic.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: Implement Websites</h3>
<div>
<ul>
	<li>When you create an Azure website, you are creating the unique DNS name, specifying the region the website will run in, and adding resources such as a Microsoft Azure SQL Database or Microsoft Azure Storage account</li>
	<li>To determine if an Azure website name already exists, use the following Azure PowerShell command.
<em>Test-AzureName -Website "contoso-web"</em>
The result will be either true or false. If it is true, then the name specified already exists and therefore cannot be used. If it is false, then the Azure website name does not exist and therefore would be a valid unique name you can use.</li>
	<li>Exam Tip: All Azure Websites are created in the Azurewebsites.net domain. If you name your website Contoso-web, it will be reachable using the URL contoso-web.azurewebsites.net.</li>
	<li>You have the option of adding up to four additional deployment slots to your website. When you have two or more deployment slots, you can swap the contents of the deployment slots as new versions of your application are being developed</li>
	<li>Exam Tip: Adding additional deployment slots to an Azure website requires that the website be configured for Standard mode.</li>
	<li>Exam Tip: A deployment slot is actually a completely separate Azure website linked to your production slot website. For example, if you create your website using the name Contoso-web and then later add a deployment slot named Staging, then the website name for the staging slot would be called Contoso-web-staging</li>
	<li>A WebJob is an application or script that can be run as a background task in an Azure website</li>
	<li>A WebJob can be configured as an On-Demand, Continuously Running, or Scheduled task.</li>
	<li>To deploy a WebJob using the management portal, it is required that the application or script be zipped and deployed as a .zip file and that the size of the .zip file be a maximum size of 100 MBs</li>
	<li>The New-AzureWebsiteJob cmdlet supports two types of jobs: Triggered and Continuous. Triggered jobs are the same as On-Demand. The JobType parameter does not support Scheduled WebJobs.</li>
	<li>Exam Tip: If an application setting, or connection string, is defined in both an application configuration file and as a site setting in the Azure website, the site setting value takes precedence over the setting in the application configuration file.</li>
	<li>Exam Tip: The awverify CNAME record is only used when using an A record to configure a custom domain.</li>
	<li>Custom domains are not supported in the free tier of Azure Websites.</li>
	<li>Exam Tip: To configure SSL for an Azure website with a custom domain, the website must be configured for Standard mode.</li>
	<li>Exam Tip: If you choose IP-based SSL for your SSL binding and your custom domain is configured using an A record, Azure will assign a new dedicated IP address to your website. This is a different IP address than what you previously used to configure the A record. Therefore, you must update the A record with your DNS registrar using the new virtual IP address. The virtual IP address can be found in the management portal by clicking the Properties part of the Website blade.</li>
	<li>Exam Tip: An Azure website must be in Standard mode to be added as an endpoint to an Azure Traffic Manager profile.</li>
	<li>Exam Tip: As users navigate to an application configured with Azure Traffic Manager, there is not any actual traffic routed through Traffic Manager. When a user browses to a website configured with Azure Traffic Manager, such as www.contoso.com, the user’s DNS server will send a new DNS query to the DNS name for the Traffic Manager profile, such as contoso-web-tm.trafficmanager.net. The Traffic Manager DNS name servers receive this query. Based on the load balancing method in the Azure Traffic Manager profile, Traffic Manager will select an endpoint from the profile, and return a CNAME record mapping contoso-web-tm.trafficmanager.net to the DNS name for the selected endpoint, such as contoso-web-east.azurewebsites.net. The user’s DNS server will then resolve the endpoint DNS name to an IP address and return it to the user. The user’s browser then calls the selected website using the IP address. The domain and IP address are cached on the client machine, so subsequent requests to the website are sent directly to the website until the local DNS cache expires.</li>
	<li>There are two categories of Azure Website log files:
<ul>
	<li>Application diagnostic logs</li>
	<li>Site diagnostic logs</li>
</ul>
</li>
	<li>Application diagnostic logs contain information produced by the application code.</li>
	<li>When you enable application logs, you must specify the logging level, which can be one of the following:
<ul>
	<li>Error</li>
	<li>Warning</li>
	<li>Information</li>
	<li>Verbose</li>
</ul>
</li>
	<li>Site diagnostic logs contain information produced by the web server that the web application is running on</li>
	<li>Exam Tip: Application diagnostic logs can be saved to the website’s file system, Azure Table Storage, or Azure Blob Storage. The web server logging in site diagnostics can be saved to the website’s file system or Azure Blob Storage.</li>
	<li>Exam Tip: Every Azure website gets the Site Control Manager site extension installed by default. There is nothing you have to do to enable it.</li>
	<li>Using the Save-AzureWebsiteLog cmdlet to download log files will download all logs except the Failed Request logs. If you use this method for retrieving log files, you will need to use one of the other options to retrieve failed request logs separately.</li>
	<li>Exam Tip: The streaming log service is available for application diagnostic logs and web server logs only. Failed request logs and detailed error messages are not available via the log-streaming service.</li>
	<li>Azure Websites support up to two endpoints for endpoint monitoring. Each endpoint can be monitored (or tested) from up to three locations</li>
	<li>Exam Tip: Alerts can be configured with a sensitivity setting of low (1), medium (2), or high (3). A setting of low triggers an alert when all test locations detect a failure within 15 minutes. A setting of medium triggers an alert when at least half of the test locations detect a failure in 10 minutes. A setting of high triggers an alert any time a failure is detected.</li>
	<li>Tip: Endpoints configured with endpoint monitoring are considered to be available as long as the conditions defined are met when the monitoring service performs a web test against the endpoint. However, even if the result is the expected result, the endpoint can still be considered unavailable if the response takes longer than 30 seconds to return. Therefore, a web test configured to expect an HTTP 200 (OK) status code would fail if the response received was an HTTP 200 but took over 30 seconds to return.</li>
	<li>You can subscribe to an RSS feed to get updates from the Azure service dashboard at <a href="http://azure.microsoft.com/en-us/status/feed/" target="_blank">http://azure.microsoft.com/en-us/status/feed/</a>. You can also see the history of service announcements at <a href="http://azure.microsoft.com/en-us/status/#history" target="_blank">http://azure.microsoft.com/en-us/status/#history</a>.</li>
	<li>Hybrid cloud workloads - Websites
Microsoft Virtual Academy provides an online training course that augments the content in this objective very well by covering how Azure Websites can be used in hybrid cloud scenarios. You can access the course at <a href="http://www.microsoftvirtualacademy.com/training-courses/hybrid-cloud-workloads-websites" target="_blank">http://www.microsoftvirtualacademy.com/training-courses/hybrid-cloud-workloads-websites</a>.</li>
	<li>Exam Tip: The storage account used to back up Azure Websites must belong to the same Azure subscription that the Azure website belongs to.</li>
	<li>Exam Tip: Before you can access the Autoscale settings for an Azure website, the website’s mode must first be set to Standard.</li>
	<li>Exam Tip: You can scale website instances up and down, but it is not possible to start and stop the website on a schedule. For example, you cannot set the low end of your instance range to zero. It must be at least one.</li>
	<li>If the average CPU falls below the low-end of the target CPU range, Azure Autoscales your running instances down (once every two hours) until the number of running instances equals the low-end range defined in the Instance Count setting.</li>
	<li>The instance size setting is only available for websites running in a Basic and Standard-mode hosting plan. This setting is not applicable for websites running the Free or Shared plans.</li>
	<li>Exam Tip: It is not possible to autoscale the instance size for running instances of your website. If you define your instance size as Medium, all of your running instances will be Medium. In other words, you cannot have one instance of your website running a Small instance size and another instance of the same website running a Large instance.</li>
	<li>Exam Tip: It is not possible to create a new empty web hosting plan. Web hosting plans are created during website creation.</li>
	<li>Exam Tip: When moving a website to a new web hosting plan, the new plan must be in the same region and resource group as the plan it is currently in.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 02: Implement Virtual Machines</h3>
<div>
<ul>
	<li>The best way to keep track of what is, and is not supported, is through the Microsoft support article: <a href="http://support.microsoft.com/kb/2721672" target="_blank">http://support.microsoft.com/kb/2721672</a>.</li>
	<li>Some options, such as configuring the load balancer, and specifying data disk configuration, are not available at creation time through the management portal but can be set after the virtual machine is created</li>
	<li>Exam Tip: In the above example, the virtual machine configuration is created using the New-AzureVMConfig cmdlet, and passed to each of the cmdlets using the PowerShell pipeline operator. This can also be accomplished by storing the returned configuration in a variable and passing it with the VM parameter (Add-AzureEndpoint -VM $config), or by piping the returned variable itself to the cmdlet ($config | Add-AzureEndpoint). Variations may show up on the exams so it is important to be familiar with each syntax.</li>
	<li>Exam Tip: Creating a virtual machine from a disk using the Azure PowerShell cmdlets has several key differences that you should be aware of. First, New-AzureQuickVM doesn’t support creating from a disk (only images are supported). Second, the Add-AzureProvisioningConfig cmdlet isn’t used because it only sets options available for provisioning from an image. Third, the default endpoints for RDP and WinRM (Windows PowerShell remoting) on Windows and SSH on Linux aren’t created automatically for you. If you want the endpoints available at boot, you must use the Add-AzureEndpoint cmdlet to add them.</li>
	<li>One of the most important concepts for deploying virtual machines is using the domain name container correctly. The host portion of the domain (contoso-vms in Figure 2-10) is also known as the cloud service name, and is referenced that way in the management portal (https://manage.windowsazure.com) and the Azure PowerShell cmdlets</li>
	<li>You can add at most 50 virtual machines into the same domain name/cloud service. This puts an upper limit on how many virtual machines can be load-balanced, Autoscaled, or configured for availability using availability sets.</li>
	<li>To validate the availability of the name using the Azure PowerShell cmdlets, use the Test-AzureName cmdlet</li>
	<li>Test-AzureName returns true, the service name already exists and is not available for you to create. That does not necessarily mean you cannot use it. If the cloud service exists in your subscription and is in the same region as the virtual machine you want to create, you can specify it when creating a virtual machine</li>
	<li>You can identify whether the service is in your subscription from Windows PowerShell by calling the Get-AzureService cmdlet and passing the cloud service name to the ServiceName parameter. If Get-AzureService returns an error, it is not available in your subscription.</li>
	<li>Note: Cloud Service Location
New-AzureQuickVM will fail if you specify the location and also if the cloud service name specified in ServiceName already exists. New-AzureVM will produce a warning that the cloud service already exists but will continue.</li>
	<li>Resource groups are logical containers that are used to group resources such as virtual machines, storage accounts, databases, websites, and others that share a common life cycle</li>
	<li>It is important to understand the difference between StoppedDeallocated and just Stopped. In the Stopped state a virtual machine is still allocated in Azure, and the operating system is simply shut down. You will still be billed for the compute time for a virtual machine in this state. A virtual machine in the StoppedDeallocated state is no longer occupying physical hardware in the Azure region, and you will not be billed for the compute time (you are still billed for the underlying storage).</li>
	<li>Note: Connection button disabled
If the connect button is disabled in a virtual machine property page, it can mean that the virtual machine is currently stopped, or that there is no endpoint with a private port of 3389 on that virtual machine.</li>
	<li>Note: Windows PowerShell remoting authentication
Connecting to a virtual machine with Windows PowerShell remoting only allows access to resources on the virtual machine itself. To access remote resources, such as install files on a file share, requires you to enable CredSSP authentication. This is also known as multi-hop support. More information on CredSSP can be found at <a href="http://msdn.microsoft.com/en-us/library/ee309365(v=vs.85).aspx" target="_blank">http://msdn.microsoft.com/en-us/library/ee309365(v=vs.85).aspx</a>.</li>
	<li>The virtual hard disk files must be registered as operating system disks or data disks to be directly usable by an Azure virtual machine as a mountable disk.</li>
	<li>The Add-AzureVHD cmdlet is designed to efficiently upload a virtual hard disk (.vhd) to an Azure Storage account. This cmdlet uses the VHD data structures to determine what bytes are actually written in the file, and only uploads those bytes instead of the empty bytes of the entire disk as an optimization.</li>
	<li>A significant difference between creating images based on Windows or Linux, is that Linux images are required to have the Azure Agent installed prior to associating the virtual hard disk file with an image.</li>
	<li>Exam Tip: There are two Azure PowerShell cmdlets for creating a virtual machine image. The Save-AzureVMImage cmdlet creates an image from an existing virtual machine and supports both Generalized and Specialized image types. The Add-AzureVMImage cmdlet creates an image from an existing virtual hard disk file (operating system disk only) and only supports generalized images.</li>
	<li>Using the Import parameter assumes the disk is already associated and you just need to specify the existing disk name and the LUN on the virtual machine</li>
	<li>The custom script extension allows you to run a script on a virtual machine at provisioning time or after it is running</li>
	<li>Exam Tip: Just a reminder that Windows PowerShell examples like the previous example can be written in multiple ways. For instance the configuration could be piped as a separate variable.</li>
	<li>Exam Tip: To use virtual machine extensions like DSC, Puppet, and Chef on Windows, the Azure virtual machine agent must be installed on the virtual machine. By default, the agent is installed on virtual machines created after February 2014 (when the feature was added). But, it’s also possible to not install the agent by using the management portal, or by using the DisableGuestAgent parameter of the Add-AzureProvisioningConfig and New-AzureQuickVM cmdlets. If the agent is not installed at provisioning time, or if you have migrated a virtual hard disk from on-premises, you can manually install the agent on these virtual machines by downloading and installing the agent from Microsoft at <a href="http://go.microsoft.com/fwlink/?LinkID=394789&amp;clcid=0x409" target="_blank">http://go.microsoft.com/fwlink/?LinkID=394789&amp;clcid=0x409</a>.</li>
	<li>Virtual machines are always created in a cloud service (or domain name as referenced in the new management portal)</li>
	<li>Each cloud service has a unique name that is part of the cloudapp.net domain.</li>
	<li>Exam Tip: Chapter 6 covers deploying multiple cloud services on the same virtual network, which allows virtual machines even in separate cloud services to have direct connectivity. For the exam, you should know that the built-in DNS server supports name resolution automatically for virtual machines within the same cloud service. However, it does not support name resolution across cloud services even if the virtual machines are deployed in a virtual network.</li>
	<li>To add additional virtual machines to the load balanced set, you must create an endpoint on each virtual machine with the same load balanced set name</li>
	<li>You can specify up to 50 access control lists per endpoint</li>
	<li>A permit rule implicitly blocks traffic to all remote networks that do not match the rule unless the incoming IP address matches another permit rule later in the access control list. Likewise, a deny rule allows traffic for source remote networks that do not match the deny rule.</li>
	<li>The reserved IP address can only be deleted if it is not associated with an existing cloud service</li>
	<li>Exam Tip: Although this objective is focused mostly on the Azure-specific networking, you might see questions related to configuring the network in the guest operating system. In general, you should avoid applying settings such as IP addresses or DNS servers within the guest operating system because those settings should be set through Azure Virtual Networks (covered in Chapter 6). However, you will still be responsible for settings like firewall rules, and algorithm- and protocol-specifc settings, such as the keep alive settings.</li>
	<li>Availability sets are used to control availability for multiple virtual machines in the same application tier. To provide redundancy for your virtual machines, it is recommended to have at least two virtual machines in an availability set</li>
	<li>Virtual machines should be deployed into availability sets according to their workload or application tier. For instance, if you are deploying a three-tier solution that consists of web servers, a middle tier, and a database tier, each tier would have its own availability set</li>
	<li>Each availability set will also be comprised of two fault domains. Fault domains represent which virtual machines will be on separate physical hardware for redundancy</li>
	<li>Each availability set will have five non-configurable update domains available, which indicates the groups of virtual machines and the underlying physical hardware that can be rebooted at the same time for host updates</li>
	<li>It is important to understand that virtual machines must be created in the same cloud service to be joined in the same availability set.</li>
	<li>Note: Moving a VM to an availability set may cause a reboot
Adding an existing virtual machine to an availability set may cause the virtual machine to restart if it has to move to another physical server.</li>
	<li>The average CPU utilization includes all instances averaged over the period of an hour.</li>
	<li>Instances will scale up or down based on the total number of messages in the queue divided by the instances</li>
	<li>You can cache reads or writes (depending on the configuration) for up to four data disks plus the operating system disk</li>
	<li>The operating system disk setting can only be set through Windows PowerShell, but it can be set at creation time or as part of an update</li>
	<li>The default cache setting is ReadWrite. This value can be changed later using the Set-AzureOSDisk cmdlet (this does require a reboot)</li>
	<li>In Azure Storage, there are really two primary limits to be aware of. The first is the size of the disks themselves. For an Azure virtual machine, the maximum capacity of the operating system disk on drive C is 127 GB. The maximum capacity of additional data disks is 1023 GB (~1 TB). Currently, the most disks you can attach to a single virtual machine are 16 for a total storage capacity of 16 TB.</li>
	<li>Storage accounts also have a maximum storage capacity of 500 TB per Azure Storage account</li>
	<li>Azure Storage provides this redundancy by replicating each disk a minimum of three times within the same region if the storage account is configured for the Local Redundant tier</li>
	<li>The Interleave parameter enables you to specify the number of bytes written in each underlying data disk in a virtual disk. Microsoft recommends that you use 256 KB for all workloads.</li>
	<li>The NumberOfColumns parameter of New-VirtualDisk should be set to the number of data disks utilized to create the underlying storage pool</li>
	<li>Exam Tip: Mounting data disks may come up on the exam. It is important to remember that on Windows, the drive D is mapped to the local resource disk, which is only for temporary data since it is actually backed by the local physical disk on the host server. The resource disk will be mounted on the /Dev/Sdb1 device on Linux with the actual mount point varying by Linux distribution.</li>
	<li>To implement Azure Files you must currently download and install a separate Windows PowerShell module</li>
	<li>Within Azure virtual machines, BitLocker is not supported for boot volumes. This is partially because guest virtual machines don’t have the Trusted Platform Modules (TPMs),</li>
	<li>However, BitLocker is supported on a virtual machine’s data disks and there are also third-party solutions available</li>
	<li>You can configure an alert to email you when one of the monitored metrics passes a configurable threshold</li>
	<li>After web endpoint monitoring is enabled, you will have two additional metrics available, Uptime and Response Time. Each remote monitoring location will have both metrics available for monitoring and alerts.</li>
	<li>The schema documentation is located on MSDN at <a href="http://msdn.microsoft.com/en-us/library/azure/hh411551.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/hh411551.aspx</a></li>
	<li>Microsoft Virtual Academy offers free online courses delivered by industry experts, including a course relevant to this exam. We recommend the Microsoft Azure IaaS Deep Dive Jump Start. You can access the course at <a href="http://www.microsoftvirtualacademy.com/training-courses/windows-azure-iaas-deep-dive-jump-start" target="_blank">http://www.microsoftvirtualacademy.com/training-courses/windows-azure-iaas-deep-dive-jump-start</a>.</li>
</ul>
&nbsp;
<h3>Chapter 03: Implement Cloud Services</h3>
<div>
<ul>
	<li>The number of instances for a role is defined in the cloud service configuration (.cscfg) file of a cloud service</li>
	<li>Exam Tip: It is possible to publish a cloud service where one of the roles has an instance count of one. However, the cloud service must have at least two instances for every role in order to qualify for the Azure service level agreement (SLA) that guarantees connectivity of 99.95 percent.</li>
	<li>An upgrade domain is a logical unit used to group role instances in a cloud service for updating purposes. By default, a cloud service has up to five upgrade domains</li>
	<li>A fault domain is a physical unit used to avoid a single point of failure for the cloud service. When a cloud service role has more than one instance, Azure will provision the instances in multiple fault domains. In a datacenter, you can think of a fault domain as a rack of physical servers.</li>
	<li>There are two settings applicable when configuring operating system settings for a cloud service. These are:
<ul>
	<li>Operating system</li>
	<li>Version</li>
</ul>
</li>
	<li>In a dedicated cache, the cache is hosted on worker role instances specifically for the purpose of caching. In this topology, the full resources of the virtual machine are used to host the distributed cache.</li>
	<li>In a co-located cache, the cache is hosted on the web and/or worker roles comprising the cloud service. In this topology, the resources (primarily memory) of the virtual machines hosting the web and/or worker roles are also used to host the distributed cache</li>
	<li>Exam Tip: The dedicated In-Role Cache is only supported for cloud service worker roles. It is not possible to use a web role for dedicated in-role caching.</li>
	<li>Azure provides a capacity planning guide spreadsheet that you can use to determine the correct configuration for your applications. The spreadsheet and instructions on how to use it are available at <a href="http://msdn.microsoft.com/en-us/library/azure/hh914129.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/hh914129.aspx</a>.</li>
	<li>Exam Tip: A cache with high availability enabled will reduce the capacity of the cache because each item added to the cache will be added twice. It also requires a role instance count of two or more.</li>
	<li>Configuring a custom domain for a cloud service involves adding CNAME and A records to your domain registrar. The CNAME record will use the site URL for the cloud service while the A record will use the public virtual IP (VIP) address of the cloud service</li>
	<li>Exam Tip: As long as a cloud service deployment exists, the public virtual IP (VIP) will remain unchanged. However, if you delete a cloud service deployment and later re-deploy the cloud service, the public VIP will be different in the new deployment. As a result, A records registered with your domain registrar will have to be updated to reference the new IP address</li>
	<li>The subject name must match the custom domain used to access the cloud service</li>
	<li>Tip: If a cloud service is configured to use an SSL certificate, the certificate must be attached when deploying the cloud service. Alternatively, you can create an empty cloud service, upload the certificate separately to Azure, and then deploy the cloud service package. Otherwise, you will get an error when attempting to deploy the cloud service package because it will see the &lt;Certificate&gt; configuration but won’t be able to find it in the Azure environment.</li>
	<li>Microsoft provides a detailed guide for securing a cloud service with an SSL certificate, which can be found at <a href="http://support2.microsoft.com/kb/2990804" target="_blank">http://support2.microsoft.com/kb/2990804</a>.</li>
	<li>Before you can configure a reserved IP address for a cloud service, you must first reserve (or obtain) one from Azure. The only way to reserve an IP address is using the Azure PowerShell cmdlets; the management portal does not support this.</li>
	<li>Exam Tip: A role can have a maximum of five internal endpoints. A cloud service can have a maximum of 25 internal endpoints across all roles.</li>
	<li>Network traffic rules are defined in the cloud service definition (.csdef) file within the &lt;NetworkTrafficRules&gt; element. There can be only one instance of this in the cloud service definition file.</li>
	<li>More information about startup tasks and best practices for using them can be found at <a href="http://msdn.microsoft.com/en-us/library/azure/hh180155.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/hh180155.aspx</a>.</li>
	<li>Configuring &lt;ipSecurity&gt;in Web.config
Generally, you would provide this information to the developer to include it in the Web.config for the web role. The Web.config file for a web role or worker role is packaged into the cloud service package (.cspkg) and therefore is not something that should be edited after the package is created</li>
	<li>Configuring a cloud service for RDP access involves registering a management certificate with the cloud service and setting up credentials to sign in to the virtual machine.</li>
	<li>The check box labeled Deploy Even If One Or More Roles Contain A Single Instance is necessary if your instance count for any role is set to one. By selecting this box, you are acknowledging that you are intentionally deploying a cloud service that won’t be subject to the financially backed SLA of 99.95 percent. Recall from earlier, to get the SLA, all roles in the cloud service must have a minimum of two instances.</li>
	<li>Exam Tip: When a cloud service is deployed to a Virtual Network, the IP address assigned to the role instances from the subnet of the Virtual Network does not influence the public virtual IP (VIP) address of the cloud service. The public VIP for the cloud service is still assigned an IP address by Azure that is publicly reachable.</li>
	<li>A virtual IP (VIP) swap equates to swapping the environment (staging or production) that the VIP and URL are assigned to.</li>
	<li>When you update a deployment, Azure applies the update sequentially across the update domains of your cloud service so as to minimize less availability of instances during the update. This assumes you have a role instance count of two or more for each role in the cloud service.</li>
	<li>The other notable difference is the check box labeled Allow The Update If Role Sizes Change Or If The Number Of Roles Change. By checking this, you’re acknowledging that if your update involves any of these conditions, any data in local storage resources will be lost because the service will have to be redeployed.</li>
	<li>Exam Tip: Unlike other compute stacks in the Azure platform, the ability to scale up or down the virtual machine size for a role instance, such as increasing it to an A7 or decreasing it to a Small, is not possible for Cloud Services. To change the virtual machine size for a role means changing the cloud service definition file and re-deploying the service.</li>
	<li>You can create a Service Bus namespace using the Azure PowerShell cmdlet New-AzureSBNamespace. This cmdlet does not specify the type for the namespace. Instead, when it creates the namespace, it creates it as a Mixed type</li>
	<li>Exam Tip: Use a storage account to store monitoring logs that is separate from any storage accounts your cloud service may be using for normal application functions. Azure Storage accounts have scalability targets of 20,000 IOPS/second. So, depending on the level of logging and activity in your cloud service, using the same storage account for logging could exhaust this capacity and potentially have a negative impact on the normal business functions the cloud service performs for users. It may even be necessary to specify different storage accounts for each role to use for logging. Monitor the storage accounts your cloud service uses to insure you are operating within the scalability targets.</li>
	<li>It is a best practice for the cloud service to have a health check page that checks for the availability of other resources it depends on, such as database, web services, storage accounts, etc.</li>
	<li>Monitoring a Service Bus relay using the management portal is only possible after a relay has been created using the Service Bus API’s. The Service Bus relay is not something you can create and manage in Azure</li>
</ul>
&nbsp;
<h3>Chapter 04: Implement Storage</h3>
<div>
<ul>
	<li>SSL just works
Each Azure storage endpoint can be accessed via HTTP or HTTPS (SSL) by default. No additional configuration is needed to access blobs through the HTTPS endpoint.</li>
	<li>Creating blob hierarchies
The blob service in Azure Storage is based on a flat storage scheme. This means that creating a container one level below the root is the only true level of container. However, you can specify a delimiter as part of the blob name to create your own virtual hierarchy. For example, you could create a blob named /January/Reports.txt and /February/Reports.txt, and filter based on /January or /February in most tools that support Azure Storage. Most third-party storage tools allow you to create folders within a container, but they are actually being clever with the name of the blob itself.</li>
	<li>To create a container at the root of the storage account, specify the special name $root for the container name. This allows you to store blobs in the root of the storage account and reference them via URLs such as https://[account name].blob.core.windows.net/fileinroot.txt.</li>
	<li>Standard_ZRS and block blobs
You cannot change the Standard ZRS (zone replicated) to any other storage account type and vice versa. Zone replicated storage accounts only support block blobs.</li>
	<li>To access a share created in Azure files, you should store the storage account name and key using the Cmdkey.exe utility. This allows you to associate the credentials with the URI to the Azure files share.</li>
	<li>Exam Tip: To add a single file to the drive and journal file, use the Srcfile parameter instead of the Srcdir parameter</li>
	<li>Azure Content Delivery Network and SSL
SSL can be enabled on each CDN endpoint to allow transport-level secure access to the object in the CDN. SSL must be enabled per CDN endpoint.</li>
	<li>Exam Tip: You can control the expiration of blob data in the CDN by setting the Cache-Control metadata property of blobs.</li>
	<li>To remove content from the CDN altogether, there are two approaches depending on how the content has been added. If the content is stored in storage, you can set the container to private, or delete the content from the container, or delete the container itself. If the content is in a cloud service or an Azure website, you can modify the application to no longer serve the content</li>
	<li>SSL is not supported with custom domains
As of this writing, using SSL with custom domains and third-party certificates is not supported for the Azure Storage Service or Azure CDN.</li>
	<li>By default, every request to an Azure Storage account requires authentication.</li>
	<li>Note: Special care may be needed when regenerating keys
When regenerating the key for a storage account that is hosting Azure Virtual Machines, ensure that you shut the virtual machines down before regenerating the key. If you don’t shut them down, you will have to redeploy the virtual machines. If you’re using Azure Media Services, you will have to re-sync the key of any storage account being used by Azure Media Services after the key regeneration.</li>
	<li>Use a SAS to grant access to a client that should not have access to the entire contents of the storage account but that still requires secure authentication.</li>
	<li>A stored access policy allows you to define the permissions, start, and end date for access to the container.</li>
	<li>Basic databases can be recovered back to seven days, Standard databases back to 14 days, and databases in the Premium tier can be recovered up to 35 days.</li>
	<li>Point-in-time restore does not allow you to overwrite an existing database or provide the ability to selectively merge changes.</li>
	<li>The difference between the two cmdlets is the Start-AzureSqlDatabaseRecovery cmdlet only allows for recovering a deleted database (the last backed up), and the Start-AzureSqlDatabaseRestore cmdlet allows restoring a deleted database (specify the deletion date using the SourceDatabaseDeletionDate parameter), or allows performing a point-in-time restore on an active database with the PointInTime parameter.</li>
	<li>When creating a secondary database using Windows PowerShell, the remote SQL Database server must already be created.</li>
	<li>A BACPAC file is an entity that encapsulates all of the objects (tables, stored procedures, views, and so on) along with the data in the database into a file. For more information about BACPAC, see on MSDN: <a href="http://msdn.microsoft.com/en-us/library/ee210546.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/ee210546.aspx</a>.</li>
	<li>Exam Tip: Downloading vault credentials is a relatively new feature. Previously, you were required to generate a self-signed certificate using a tool like Makecert.exe and upload it to the vault, as well as deploy it on the servers that are protected. The certificate is used to identify the vault and authenticate clients.</li>
	<li>The cache disk size should be at least 10-15 percent of the space required for data storage of your backups</li>
	<li>Exam Tip: Configuring the agent with vault credentials is a relatively new process. Previous versions of the wizard prompted you to browse for a self-signed certificate, which performed the same function (vault identification and authentication).</li>
	<li>It is important to understand that Azure Backup only works with files and folders. For bare metal or VSS-related backups, you must use another tool such as DPM.</li>
	<li>The maximum amount of data that can be backed up is 1.5 TB per volume.</li>
	<li>Access control lists (ACLs) are captured as part of the backup process. During restore, you can choose whether to restore ACLs.</li>
</ul>
&nbsp;
<h3>Chapter 05: Implement An Azure Active Directory</h3>
<div>
<ul>
	<li>Each directory synchronization scenario offers unique benefits. Additionally, the time and complexity involved in implementing a scenario can vary. A decision matrix is available for you to learn what you can accomplish with each scenario, and also the requirements for each scenario at <a href="http://msdn.microsoft.com/en-us/library/azure/jj573649.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj573649.aspx</a>.</li>
	<li>Exam Tip: Directory synchronization can be invoked on-demand by using the Start-OnlineCoExistence-Sync Windows PowerShell cmdlet that is installed as part of the DirSync installation. Optionally, you can pass the FullSync switch to the command if you want to invoke a full directory synchronization. Otherwise, it will only synchronize the changes since the last synchronization occurred. The script to import the module containing the cmdlet is installed at C:\Program Files\Windows Azure Active Directory Sync\DirSync\ImportModules.ps1. You must execute this script first for the cmdlets to be available.
You can get a list of all of the configuration cmdlets installed by executing the command Get-Command -All -Module “Microsoft.Online.Coexistence.PS.Config” | Select Name.
Invoking directory synchronization on demand is useful in scenarios where you need a change in the director to be synchronized immediately, such as removing a user from the on-premises directory.</li>
	<li>Additional information, potential requirements, and troubleshooting steps for the password write-back feature are available at <a href="http://msdn.microsoft.com/en-us/library/azure/dn688249.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn688249.aspx</a>.</li>
	<li>Assuming AD FS will be used for the on-premises STS, step-by-step instructions and guidance is available at <a href="http://msdn.microsoft.com/en-us/library/azure/jj205462.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj205462.aspx</a>.</li>
	<li>Exam Tip: An administrator role in Azure Active Directory, such as a global administrator, does not automatically have permission to provision services and resources in an Azure subscription. Only service administrators and co-administrators can provision services and resources in an Azure subscription. A global administrator has administrative permissions to the directory and all functions in the Office 365 Admin portal.
To add a user as a co-administrator for an Azure subscription, go to the settings section in the management portal, click the Administrators tab, and then click Add at the bottom of the page.</li>
	<li>Verifying custom domains using a TXT record or an MX record
A TXT record is the preferred record type used to verify a custom domain in Azure. However, not all domain registrars support adding TXT records. When Azure generates the unique values for the TXT record, it also generates unique values for an MX record that can be used as an alternate method for verifying the custom domain. More information about which type of record to choose can be found at <a href="http://msdn.microsoft.com/en-US/library/azure/jj151776.aspx" target="_blank">http://msdn.microsoft.com/en-US/library/azure/jj151776.aspx</a>.</li>
	<li>Cloud App Discovery is available at https://appdiscovery.azure.com. To get started using the service, you need to sign in using the organization credentials of a global administrator in the directory. The service works by collecting data from user’s computers about which cloud applications they are accessing and using. This is accomplished through an agent that you must download and install on the users’ machines you want to collect data for</li>
	<li>Synchronization Service Manager client installation
The installation of this tool during the DirSync installation does not set up the required security groups to run it, as you would normally get in a full FIM installation. As a result, when you run the tool, you’re likely to get an error indicating your account is not a member of a required security group. The security group missing is the MIISAdmins group. Therefore, you must create this group and add your user account to the group to use the tool. For more information about this issue and detailed steps to correct it, see <a href="http://support.microsoft.com/kb/2791422" target="_blank">http://support.microsoft.com/kb/2791422</a>.</li>
	<li>Before you can install the Azure Active Directory Module for Windows PowerShell, you must first install the Microsoft Online Sign-in Assistant for IT Professionals.</li>
	<li>One of the benefits of the Azure Active Directory Basic and Premium editions is the ability to assign or remove access to applications using groups. This can save you considerable time when you’re managing application access for a large group of users. Information about how to assign application access for a group is available at <a href="http://msdn.microsoft.com/en-US/library/azure/dn621141.aspx" target="_blank">http://msdn.microsoft.com/en-US/library/azure/dn621141.aspx</a>.</li>
	<li>In the Premium edition of Azure Active Directory, you can apply customized branding to the sign-in page and Access Panel for your users to display your organization’s logo, custom messaging, and colors. These customization features are available in the Configure page of the directory under the Directory Properties section</li>
	<li>The customization options that are applicable to the Access Panel are limited to the banner logo</li>
	<li>After a billing option is chosen and the MFA provider has been created, it cannot be changed. Therefore, it’s a good idea to review the pricing details for each option at <a href="http://azure.microsoft.com/en-us/pricing/details/multi-factor-authentication/" target="_blank">http://azure.microsoft.com/en-us/pricing/details/multi-factor-authentication/</a>.</li>
	<li>After enabling Multi-Factor Authentication for a user, the user’s MFA status is updated to Enabled. It is a subtle but important distinction to note that MFA for the user is not being enforced yet. At this stage, the service has only been enabled for the user. To be enforced requires that user configuration for additional security verification be completed</li>
	<li>Application passwords with Azure Multi-Factor Authentication
For non-browser applications such as Microsoft Outlook and Lync, MFA is not supported. As a result, users who have MFA configured can’t access such applications using just their organizational account credentials. Application passwords are created during additional security verification for users indicating they use non-browser applications. By updating an application to use the generated application password instead, a user is able to bypass Multi-Factor Authentication when signing in to use the application. More information about application passwords, applications that support using them, and how they are created is available at <a href="http://msdn.microsoft.com/en-us/library/azure/dn270518.aspx#howapppassword" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn270518.aspx#howapppassword</a>.</li>
	<li>Exam Tip: When an external user of a directory signs in to access an application protected by Azure Active Directory, the user authenticates to the federated identity provider, not Azure Active Directory.</li>
	<li>Sign-on URL and application ID URI
A subtle distinction between the sign-on URL and the application ID URI is the use of a URL for one and a URI for another. Many times these two terms, URL and URI, are used interchangeably. However, they are very different in their definition.
The uniform resource locator (URL) identifies a resource on the web and can be used to access that resource using, for example, your browser.
The uniform resource identifier (URI) identifies a resource. Usually the resource is a resource on the web, but it doesn’t have to be.
A good blog discussing the relationship between URLs, URIs, and uniform resource names (URNs) is available at <a href="http://www.cloudidentity.com/blog/2013/03/02/url-urn-uri-oh-my/" target="_blank">http://www.cloudidentity.com/blog/2013/03/02/url-urn-uri-oh-my/</a>.</li>
	<li>Additional information about how OAuth 2.0 is used in Azure Active Directory and best practices for application developers is available at <a href="http://msdn.microsoft.com/en-us/library/azure/dn645545.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn645545.aspx</a>.</li>
</ul>
&nbsp;
<h3>Chapter 06: Implement Virtual Networks</h3>
<div>
<ul>
	<li>Point</li>
</ul>
</div>
</div>
</div>
</div>
</div>
