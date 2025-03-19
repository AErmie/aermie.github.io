---
layout: page
title: Book Review: Microsoft System Center Network Virtualization and Cloud Computing
date: 2015-06-05 08:58
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2015/06/Network-Virtualization-and-Cloud-Computing.jpg"><img class="alignleft size-full wp-image-12891" src="/wp-content/uploads/2015/06/Network-Virtualization-and-Cloud-Computing.jpg" alt="Network Virtualization and Cloud Computing" width="157" height="190" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2014/03/24/free-ebook-microsoft-system-center-network-virtualization-and-cloud-computing.aspx" target="_blank">Microsoft System Center Network Virtualization and Cloud Computing</a> eBook.

There are only 2 chapters, and they were both very useful.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: Hyper-V Network Virtualization Internals</h3>
<div>
<ul>
	<li>Network virtualization should allow a virtual network, including all of its IP addresses, routes, network appliances, and so on, to appear to be running directly on the physical network</li>
	<li>So without network virtualization, a key feature of server virtualization is much less flexible (i.e., you can move VMs only to hosts on the same physical subnet) and less automated (i.e., you might need to reconfigure the network before a VM can be migrated).</li>
	<li>For HNV, a centralized control plane is used to distribute policies to the endpoints needed to properly encapsulate and de-encapsulate the packets. This allows for a centralized policy with a global view of the virtual network while the actual encapsulation and de-encapsulation based on this policy happens at each end host</li>
	<li>There can be many VM networks on a single physical network</li>
	<li>On a single host there can be a mixture of IPv4 and IPv6 customer addresses if they are in different VM networks.</li>
	<li>Within a single VM network, IP and MAC addresses cannot overlap, just like in a physical network. On the other hand, across multiple VM networks, each VM network can contain the same IP and MAC address, even when those VM networks are on the same physical network</li>
	<li>Only VMs can be joined to a virtual network. Windows does allow the host operating system to run through the Hyper-V virtual switch and can be attached to a VM network</li>
	<li>Currently a single instance of VMM manages a particular VM network. This limits the size of the VM network to the number of VMs supported by a single instance of VMM. In the R2 release, VMM allows a maximum of 8,000 VMs and 4,000 VM networks.</li>
	<li>HNV uses a built-in router that is part of every host to form a distributed router for the virtual network. This means that every host, in particular the Hyper-V virtual switch, acts as the default gateway for all traffic that is going between virtual subnets that are part of the same VM network</li>
	<li>The role of the HNV Gateway is to provide a bridge between a particular VM network and either the physical network or other VM networks.</li>
	<li>The IP address in the VM network must be routable on the physical network</li>
	<li>A second major feature of the gateway is that a single gateway VM can be the gateway for multiple VM networks. This is enabled by the Windows networking stack becoming multi-tenant aware with the ability to compartmentalize multiple routing domains from each other.</li>
	<li>The gateway must be in its own virtual subnet.</li>
	<li>HNV uses a particular format of GRE, called Network Virtualization using Generic Routing Encapsulation (NVGRE), for the encapsulation protocol</li>
	<li>HNV NDIS LWF does not have to be bound to network adapters anymore</li>
	<li>After you attach a network adapter to the virtual switch you can enable HNV simply by assigning a virtual subnet ID to a particular virtual network adapter</li>
	<li>When the two VMs are on the same host, there is no NVGRE encapsulation</li>
	<li>NOTE You can set a VLAN on a PA to associate the PA to a VLAN. You might want to do this if for instance you want all HNV traffic to be isolated and on the same VLAN.</li>
</ul>
</div>
&nbsp;
<h3>Chapter 02: Implementing Cloud Computing with Network Virtualization</h3>
<div>
<ul>
	<li>With the new multi-tenant TCP/IP stack in Windows Server 2012 R2, a single VM can be used to route packets in a compartmentalized manner exclusively between tenants’ interfaces</li>
	<li>Routing compartments virtualize the TCP/IP stack to enable multiple routing entities with overlapping IP addresses to co-exist on the same gateway VM. Packets and network entities including interfaces, IP addresses, route tables, and ARP entries of each tenant are isolated by routing compartments. Interfaces and packets in one compartment cannot be seen in another compartment</li>
	<li>You can use Windows PowerShell to configure multi-tenancy</li>
	<li>To ensure that that all Network Virtualization using Generic Routing Encapsulation (NVGRE) packets in the Contoso routing domain are transmitted to the Contoso interface IfCi1, the following configuration step is required on the host:
<ul>
	<li>Add-VmNetworkAdapterRoutingDomainMapping -VMName GW-VM -VMNetworkAdapterName NIC1
-RoutingDomainld "{12345678-1000-2000-3000-123456780001}" -RoutingDomainName "Contoso"
-IsolationId 6001 -IsolationName "IfCil"</li>
</ul>
</li>
	<li>Compartments also enable routing between virtual and physical networks using the forwarding gateway feature in Windows Server 2012 R2.</li>
	<li>It is therefore recommended that you rate-limit traffic on each S2S tunnel. The following cmdlet is an example where bandwidth is limited to 1,024 kilobits per second (kbps) in each direction:
<ul>
	<li>Set-VpnS2SInterface -RoutingDomain Contoso -Name If2 -TxBandwidthKbps 1024
-RxBandwidthKbps 1024</li>
	<li>By default, all connections are created with a 5,120 kbps limit in each direction so that no single tunnel hogs the CPU.</li>
</ul>
</li>
	<li>Adding and removing routes based on tunnel states like this requires manual intervention and results in sub-optimal routing that can lead to connectivity loss. One way to solve this problem is via route metrics (see http://support.microsoft.com/kb/140859 for some background information on route metrics).</li>
	<li>For more information on BGP, see <a href="http://www.bgp4.as/" target="_blank">http://wwwbgp4.as</a></li>
	<li>BGP uses the concept of autonomous system (AS) and AS number (ASN) for making routing decisions. This example assumes that each site is identified by a unique ASN in the private range 64512 to 65535.</li>
	<li>Isolation of routing information is maintained by storing routes using Windows Route Table Manager v2 (RTMv2) (see <a href="http://msdn.microsoft.com/en-us/library/windows/desktop/aa373798(v=vs.85).aspx" target="_blank">http://msdn.microsoft.com/en-us/library/windows/desktop/aa373798(v=vs.85).aspx</a>). This enables the configuration of multiple virtual BGP routers, one per routing domain</li>
	<li>For a walkthrough of how you can build a test lab for implementing HNV, see the blog post “Software Defined Networking: Hybrid Clouds using Hyper-V Network Virtualization (Part 2)” at <a href="http://blogs.technet.com/b/privatecloud/archive/2013/11/21/software-defined-networking-hybrid-clouds-using-hyper-v-network-virtualization-part-2.aspx" target="_blank">http://blogs.technet.com/b/privatecloud/archive/2013/11/21/software-defined-networking-hybrid-clouds-using-hyper-v-network-virtualization-part-2.aspx</a>.</li>
	<li>For an example of how a cloud hosting provider could offer Disaster Recovery as a Service (DRaaS) using HNV, see the blog post “Software Defined Networking: Hybrid Clouds using Hyper-V Network Virtualization (Part 3)” at <a href="http://blogs.technet.com/b/privatecloud/archive/2013/11/28/software-defined-networking-hybrid-cloud-using-hyper-v-network-virtualization.aspx" target="_blank">http://blogs.technet.com/b/privatecloud/archive/2013/11/28/software-defined-networking-hybrid-cloud-using-hyper-v-network-virtualization.aspx</a>.</li>
</ul>
</div>
