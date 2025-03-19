---
layout: page
title: Book Review: Building A Virtualized Network Solution
date: 2015-04-15 20:53
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2015/04/Building-A-Virtualized-Network-Solution-Cover.jpg"><img class="alignleft size-full wp-image-9901" src="/wp-content/uploads/2015/04/Building-A-Virtualized-Network-Solution-Cover.jpg" alt="Building A Virtualized Network Solution Cover" width="201" height="244" /></a>Recently, I finished reading the <a title="Building A Virtualized Network Solution" href="http://blogs.technet.com/b/scvmm/archive/2014/02/19/free-ebook-microsoft-system-center-building-a-virtualized-network-solution.aspx" target="_blank">Building A Virtualized Network Solution</a> eBook.

The chapters that I found most helpful were Chapter 2 "Logical Networks", Chapter 3 "Port Profiles", and Chapter 4 "Logical Networks" , hence the majority of my highlights are from these chapters.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h2>Chapter 01: Key Concepts</h2>
<ul>
	<li>Logical networks These represent an abstraction of the underlying physical network infrastructure</li>
	<li>Uplink port profiles These are applied to physical network adapters as part of logical switch deployment</li>
	<li>Network adapter port profiles These are templates that define offload settings, bandwidth policies, and security settings for virtual network adapters.</li>
	<li>Port classification This is a user friendly label that can be linked to a network adapter port profile</li>
	<li>IP address pools These allow VMM to automatically allocate static IP addresses to Windows-based virtual machines</li>
	<li>MAC Address Pools If virtual machines connected to the logical network will obtain IP addresses from a static IP address pool, you must also configure the virtual machine to use a static MAC address.</li>
	<li>ou can either specify the MAC address manually or have VMM automatically assign a MAC address from a MAC address pool.</li>
	<li>Logical switches These bring together uplink port profiles, native port profiles, port classifications, and switch extensions that are relevant to a particular physical or logical network.</li>
	<li>Virtual machine networks These provide the network interface through which a virtual machine will connect to a particular logical network.</li>
	<li>Logical networks can be used to describe networks with different purposes, to create traffic isolation, and even to support traffic with different types of service-level agreements</li>
	<li>To make the logical network available on a given host, you need to associate the logical network with a physical network adapter on that host.</li>
	<li>The IP address assigned to the virtual machine will not be changed during migration</li>
	<li>In most cases, a single uplink port profile will be required for each physical network</li>
	<li>Multiple network sites are supported by a single uplink profile</li>
	<li>Network adapter port profiles allow you to define settings such as virtual machine queue (VMQ), IPsec task offloading, and single root I/O virtualization (SR-IOV) in one place and apply these settings to any virtual network adapter in your environment</li>
	<li>Port classifications are linked to network adapter port profiles. They hide the details, settings, and configuration of a network adapter port profile from the end user</li>
	<li>A logical switch is essentially a template that contains an administrator-defined set of parameters you can use to create Hyper-V virtual switches on any of the host computers that connect to the network.</li>
	<li>Generally, a new logical switch is required for every physical network in your environment</li>
	<li>You should create a separate logical switch for Hyper-V hosts that will support production workloads</li>
	<li>You will need at least one VM network for each logical network.</li>
	<li>The relationship between a VM network and its (host) logical network is established when the VM network is initially created and cannot be changed afterward.</li>
	<li>Multiple VM networks can be connected to the same logical network with each one isolated from and totally unaware of the existence of any others</li>
	<li>Once the switch has been deployed, the physical network adapter can no longer be configured through the UI or PowerShell; any further changes to the logical networks, VLAN, and IP subnets for the network adapter must be configured in the uplink port profile.</li>
</ul>
&nbsp;
<h2>Chapter 02: Logical Networks</h2>
<ul>
	<li>Logical networks can be used to describe networks with different purposes, create traffic isolation, and even support traffic with different types of service-level agreements</li>
	<li>VM networks provide the network interface through which a VM connects to a particular logical network.</li>
	<li>Will need to define at least one VM network for each logical network that will be accessed by virtual machines.</li>
	<li>At least one logical network must be associated with a given host computer for it to support deployed virtual machines and services</li>
	<li>VMM verifies that physical network adapters on all new host computers are associated with one or more logical networks</li>
	<li>Rather than rely on any default behaviors. Therefore, turning off this setting is recommended (as in Figure 2-1). The same is true of the option to automatically create virtual switches</li>
	<li>VMM will not allow you to delete any default logical networks that have existing associations with network adapters in your host computers</li>
	<li>The next step in the design process is to identify the different groups of users, applications, and network services that will use each of the physical networks and determine whether there is a need to separate them to enforce security, ensure privacy (isolation), simplify management and administration, or simply to ensure that network traffic from certain groups is provided with the required Quality of Service (QoS).</li>
	<li>If development, test, and production network traffic all share the same physical network, you will invariably want to differentiate these workloads.</li>
	<li>NOTE If corporate policy mandates that an application or workload can be hosted only on a particular group of host computers, you would start by defining a separate logical network and then using Host Groups and Network Sites to ensure that it is only associated with the selected host computers.</li>
	<li>The VMM documentation suggests that you also consider creating separate logical networks for the front end (web servers) and the back end components (application and database servers) of multi-tier applications. The primary benefit of such an approach is that it allows you to use network sites to define the set of VLANs and IP subnets that will be used by virtual machines in each tier and, further, to apply a different set of security settings and capabilities to each network through the use of port profiles.</li>
	<li>A good starting point for the design is a single logical network for the shared compute workloads and a separate logical network for each customer that uses dedicated resources.</li>
	<li>Note that if Contoso were to use multiple IP-based storage technologies (such as iSCSI and SMB) on the physical network, each of these technologies would likely be allocated its own logical network.</li>
	<li>Computers that connect to and use the same network should be able to communicate with each other through routers that connect different networks together, enabling inter-network communication.
Often using dedicated VLANs and PVLANs to isolate different customers from one another.</li>
	<li>VMs in this release connect to a VM network, which acts as an interface to a particular part of a logical network</li>
	<li>Multiple VM networks may be linked to each logical network</li>
	<li>There is a practical limit of approximately 2,000 tenants and 4,000 VM networks per VMM server.</li>
	<li>Isolation is necessary only in cases where a logical network will be used by multiple customers (tenants). Logical networks created for corporate (internal) workloads, cloud infrastructure services, and logical networks that are dedicated to a specific customer are all single tenant, meaning that traffic isolation is optional.</li>
	<li>Only one VM network per logical network can be configured for No Isolation</li>
	<li>Instead of creating a separate logical network for each customer that will be isolated from others using VLAN technology, you can instead create a single logical network for all of these customers</li>
	<li>Specify that sites within this logical network are not connected.</li>
	<li>Each VLAN must be allocated to a network site. Multiple VLANs can exist with the same site, as shown in Figure 2-12, but each one will be totally isolated from any of the others.</li>
	<li>You can have only as many VM networks as you have subnet VLANs.</li>
	<li>Once all of the available network sites have been allocated, no further VM networks may be linked to this logical network until additional VLANs are added or some of the existing VM networks are deleted.</li>
	<li>Only 4,095 VLANs are permitted per physical network.</li>
	<li>You should associate each primary VLAN and secondary PVLAN with a network site within the logical network</li>
	<li>The virtual router does not exist on any one host. It essentially spans all hosts that contain VMs that are part of a particular VM network.</li>
	<li>When using Network Virtualization, the logical network design is relatively simple: create a single logical network for all of your customers that will be isolated from each other using Network Virtualization and configure the properties of the network with the Allow New VM Networks Created On This Network To Use Network Virtualization option</li>
	<li>Associated with every single network site linked to the logical network</li>
	<li>VMM installs a DHCP Virtual Switch extension on each host that it manages. If a tenant’s VM uses DHCP to request an IP address, the extension will respond by offering an IP address from the IP pool that has been defined for the VM network.</li>
</ul>
&nbsp;
<h2>Chapter 03: Port Profiles</h2>
<ul>
	<li>Port profiles (and logical switches) act as containers, essentially templates, for the properties and capabilities to be applied to network adapters. These tools allow you to consistently apply the same settings and capabilities to network adapters across multiple hosts.</li>
	<li>Uplink port profiles are applied to physical network adapters as part of logical switch deployment and define the set of logical networks that should be associated with those network adapters</li>
	<li>Network adapter port profiles, in contrast, are applied to virtual network adapters and define specific capabilities such as bandwidth limitations, priority, security settings, and so on.</li>
	<li>An uplink port profile defines the load-balancing algorithm and the teaming mode that should be used by any of the physical network adapters on which it is applied, together with the set of logical networks that should be associated with those adapters</li>
	<li>You can find more detailed information on the different load balancing and traffic distribution options and teaming modes that can be defined in an uplink port profile at <a href="http://technet.microsoft.com/library/hh831648.aspx" target="_blank">http://technet.microsoft.com/library/hh831648.aspx</a></li>
	<li>You need at least one uplink port profile for each physical network that exists within your environment.</li>
	<li>You should assume at least one uplink port profile will be required for each physical network that is routed (not bridged) to other internal or external networks.</li>
	<li>You would normally find multiple logical networks associated with a single physical network</li>
	<li>Multiple physical sites with their own set of VLANs and IP addresses, as in the Contoso example, will need a separate uplink port profile defined for each physical location.</li>
	<li>If you wish to allow virtual machines and services on one logical network to communicate with those connected to another, you will need to use a router or gateway device.</li>
	<li>Network adapter port profiles define the processor offload settings, security settings, and bandwidth limitations to be enforced on network adapters within a guest VM or virtual network interface cards</li>
	<li>Multiple network adapter port profiles are required whenever your environment contains physical and virtual computers with differing QoS requirements, essentially the need to provide certain guarantees for outgoing network bandwidth and security policy, or when specialist network adapters (e.g., SR-IOV) that require additional configuration with VMM have been deployed.</li>
	<li>Identify and build network adapter port profiles for workloads that need a guaranteed QoS, essentially where you need to control and manage outgoing network bandwidth</li>
	<li>Add additional network adapter port profiles to support VM networks that have different security requirements.</li>
	<li>Add network adapter port profiles for any physical network adapters that support either IPSec Task Offloading, SR-IOV, or Virtual Machine Queue (VMQ) processor offload capabilities.</li>
	<li>NOTE A given logical switch will be in either Relative Weights or Absolute Bandwidth Values mode with respect to bandwidth control. The default is Relative Weights. If some workloads will use relative weights and others will use fixed bandwidth limits, you need to create separate network adapter port profiles for each type of workload and ensure that the network adapter port profiles contained within a given logical switch match and align with the bandwidth control mode that has been defined for that switch.</li>
</ul>
&nbsp;
<h2>Chapter 04: Logical Switches</h2>
<ul>
	<li>Logical switches bring together all of the different uplink port profiles, native port profiles, port classifications and switch extensions that are relevant to a particular physical or logical network.</li>
	<li>When you use a logical switch to create a Hyper-V switch on a host computer, you select the most appropriate combination of port profiles, classifications, and switch extensions from those defined in the logical switch. You can find more information on Hyper-V virtual switches at <a href="http://technet.microsoft.com/en-us/library/hh831823.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh831823.aspx</a>.</li>
	<li>As a general principle, a new logical switch will be required for every physical network that exists in your environment</li>
	<li>A logical switch is a VMM concept or model to define a deployable template of network-related settings to a managed host. A virtual switch, on the other hand, is an operating system component utilized by Hyper-V to process network traffic.</li>
	<li>When a logical switch is applied to a network adapter on a Hyper-V host, VMM uses the information contained in the logical switch and the selected uplink port profile to create a Hyper-V virtual switch on the host and associate the network adapter with the required logical networks, VLAN, and IP subnets</li>
	<li>When you allow VMM to create and configure the virtual switch on your hosts, you may notice that if you then revisit the Hyper-V console on the configured host, the options for modifying any additional settings on the virtual switch are now disabled</li>
	<li>A virtual switch can work in only one mode at a time (absolute or relative) and by default a logical switch will function in relative</li>
	<li>You need at least one logical switch to take advantage of the capabilities offered by VMM</li>
	<li>Due to SR-IOV bypassing most of the networking stack, SR-IOV NICs cannot be teamed on the host operating system, and also you should not enable any policies, such as QoS.</li>
	<li>Finally, a maximum of eight SR-IOV–enabled connections can be assigned from your VM vNIC connections. You can find more details on SR-IOV at <a href="http://blogs.technet.com/b/jhoward/archive/2012/03/12/everything-you-wanted-to-know-about-sr-iov-in-hyper-v-part-1.aspx" target="_blank">http://blogs.technet.com/b/jhoward/archive/2012/03/12/everything-you-wanted-to-know-about-sr-iov-in-hyper-v-part-1.aspx</a>.</li>
	<li>Once integrated with VMM, network extensions are added to your logical switch, which allows you to leverage the flexibility of potentially deploying multiple logical switches to your hosts. When you associate a logical switch with a host, VMM will automatically discover if the logical switch has defined the use of an extension, will check whether the extension is deployed to the host, and then resolve the host when this is not the case.</li>
	<li>The virtual switch design, including its ability to support multiple simulations extensions is covered in detail on MSDN at <a href="http://msdn.microsoft.com/en-us/library/windows/hardware/hh582268(v=vs.85).aspx" target="_blank">http://msdn.microsoft.com/en-us/library/windows/hardware/hh582268(v=vs.85).aspx</a>.</li>
	<li>Behind the scenes, every time a VM is moved between hosts, and that VM is connected to a virtualized network, VMM updates the extensions on all relevant hosts with details of this environmental change. If VMM is not running, and a VM is moved by an external influence, that VM will effectively drop off the network. Of course, as soon as VMM recovers, it will scan for environment changes and update all the extensions as quickly as possible. Therefore, if VMM is unavailable, and you are using Virtual Networks, then you should aim to ensure that no external influence moves any VM connected to the virtual network. This will ensure everything remains healthy until VMM is restored.</li>
</ul>
&nbsp;
<h2>Chapter 05: Deployment</h2>
<ul>
	<li>When you add a host to the VMM management server, by default VMM automatically creates logical networks for those host physical network adapters that do not have logical networks defined on them. You might therefore want to consider clearing this option</li>
	<li>When a logical switch is applied to a network adapter in a Hyper-V host, VMM uses the information contained in the logical switch and the (selected) uplink port profile to create a Hyper-V virtual switch on the host and associate the network adapter with the required logical networks, VLAN, and IP subnets.</li>
	<li>When configuring virtual switches, delegated administrators can select only uplink port profiles that contain network sites that are in the administrative scope of their delegated privileges</li>
	<li>These network adapters require special attention as they are used by the host operating system (or parent partition) to access the network. The VMM Agent also uses these adapters to communicate with the VMM server, and to make this work, you need to define a logical network and a VM network for host management</li>
	<li>A logical switch deployed on physical network adapter used for management needs to be configured to add the appropriate VLAN ID to every packet that is sent from and to the host management logical network.</li>
	<li>To support untagged management traffic in VMM, define a logical network and set the VLAN ID for Network Site(s) within that network to. VMM interprets this setting as meaning “no VLAN” and as a result, the logical switch will be configured to leave outbound network traffic unchanged</li>
	<li>As the VLAN configuration happens at the end of the virtual switch configuration, it is important that VMM has uninterrupted access to the Hyper-V host. This means that VMM requires connectivity through another management interface until it can complete the VLAN configuration of the new management virtual network adapter.</li>
	<li>Once the physical network adapter has been associated with a standard switch you cannot subsequently upgrade it to a logical switch. You must first disconnect and remove the standard switch and any associated virtual network interface cards (vNIC) from the network adapter before you begin to deploy the logical switch.</li>
	<li>By default, the Host Refresh job (HostUpdateInterval) runs every 30 minutes, but to make sure the hardware changes are immediately represented in VMM, you can start a manual refresh job</li>
	<li>VMM does not support the deployment of logical switches to Windows Server 2012 Hyper-V hosts that have already have been configured with a NIC team.</li>
	<li>The only way to provision a logical switch to a Hyper-V host is to take over raw physical NICs that are not currently assigned to NIC teams or virtual switches</li>
</ul>
&nbsp;
<h2>Chapter 06: Operations</h2>
<ul>
	<li>You can find more details on SR-IOV at <a href="http://blogs.technet.com/b/privatecloud/archive/2012/05/14/increased-network-performance-using-sr-iov-in-windows-server-2012.aspx" target="_blank">http://blogs.technet.com/b/privatecloud/archive/2012/05/14/increased-network-performance-using-sr-iov-in-windows-server-2012.aspx</a>.</li>
	<li>It may be preferable to configure the majority of your uplink port profiles for teaming, and, in cases where a single physical network adapter has been dedicated to a specific function or operation, create a team of one. Then if something should happen, you can simply add a new physical network adapter to the host, join this adapter to the team, and remove the old one.</li>
	<li>There is no easy migration path from a standard switch to a logical switch since after the physical network adapter has been associated with a standard switch, you cannot subsequently upgrade it to a logical switch. You must first disconnect and remove the standard switch and any associated virtual network interface cards (vNICs) from the network adapter and remove or break any pre-existing network adapter teams (as described below) before you begin to deploy the logical switch.</li>
	<li>MORE INFO You can find an overview of NIC teaming at <a href="http://technet.microsoft.com/en-us/library/hh831648.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh831648.aspx</a>.</li>
	<li>You can create a team on a Windows Server computer manually from within Server Manager or by using Windows PowerShell. Having done so, however, you will be unable to deploy a logical switch to any of the network adapters that participate in that team. The fundamental issue is that VMM has no direct insight into how the network team was originally created or its current configuration</li>
</ul>
—————————————————————

Don’t forget to check out the following:

<span id="control_gen_2" class="commentary"><strong>CANITPro:</strong> Did you know there is a site dedicated to Canadian IT professionals? You can win a 3D movie prize package by upgrading your IT skills with Microsoft. Check out CANITPRO At The Movies, either in English: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600830" target="_blank">CANITPro At The Movies</a></span><span id="control_gen_3" class="commentary"> or French: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600850" target="_blank">CANITPro At The Movies</a></span>

<strong>Azure:</strong> Sign up for a FREE trial and get $200 to spend on <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597585" target="_blank">Microsoft Azure</a> cloud computing services. Full access, no strings.

<span id="control_gen_5" class="commentary"><strong>MSDN:</strong> Ever wanted to work with the latest Microsoft technologies, without having to spend thousands of dollars? Now you can, with the <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597617" target="_blank">MSDN subscription</a>. </span>
