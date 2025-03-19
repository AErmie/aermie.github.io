---
layout: page
title: Book Review: Microsoft Azure Security Infrastructure
date: 2016-11-01 12:17
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2016/10/AzureSecurityInfrastructure_BookCover.jpg"><img class="alignleft size-thumbnail wp-image-26411" src="/wp-content/uploads/2016/10/AzureSecurityInfrastructure_BookCover-150x150.jpg" alt="azuresecurityinfrastructure_bookcover" width="150" height="150" /></a>Recently, I finished reading the <a href="https://blogs.msdn.microsoft.com/microsoft_press/2016/08/25/new-book-microsoft-azure-security-infrastructure/" target="_blank">Microsoft Azure Security Infrastructure</a> eBook.

The chapters that I found most helpful were<span style="color: #000000;"> Chapter 3 "Azure Network Security" and Chapter 4 "Data and Storage Security"</span>, hence the majority of my highlights are from these chapters.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 01: Cloud Security</h2>
<ul>
 	<li>I tell friends that in the 1990s, if I needed a dozen servers for a new project, it would
take four to six months to forecast, order, deliver, rack, network, configure, and deploy
those servers before the team could begin testing the production service. Today, in
Azure, I can do the same thing in 30 minutes, from my phone.</li>
 	<li>A private cloud is not the same as a traditional on-premises datacenter (although
the term is often misused in that way).</li>
 	<li>Cloud computing security significantly differs from traditional datacenter security in two
other major areas: assume breach and isolation</li>
 	<li>We assume that we are about to be breached, or have already been breached, and we have people, processes, and technology that help us find out when the breach occurred as early as possible, and then we eject the attacker with the goal being to limit expansion of the breach as much as possible.</li>
 	<li>Azure was built from a security foundation that uses the Security Development Lifecycle (SDL) principles from the ground up.</li>
 	<li>IMPORTANT Azure administrators should use Role-Based Access Control (RBAC) provided by Azure to delegate appropriate permission to users. Read more about RBAC at <a href="https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-configure/" target="_blank">azure.microsoft.com/documentation/articles/role-based-access-control-configure</a>.</li>
</ul>
<h2>Chapter 02: Identity Protection in Azure</h2>
<ul>
 	<li>For a complete list of built-in Azure roles, go to <a href="https://azure.microsoft.com/documentation/articles/role-based-access-built-in-roles" target="_blank">https://azure.microsoft.com/documentation/articles/role-based-access-built-in-roles</a>. To learn more about how to create custom roles, go to <a href="https://azure.microsoft.com/documentation/articles/role-based-access-control-custom-roles" target="_blank">https://azure.microsoft.com/documentation/articles/role-based-access-control-custom-roles</a>.</li>
 	<li>MORE INFO For more information about how to use PowerShell to assign roles to users, go to <a href="https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-manage-access-powershell" target="_blank">https://azure.microsoft.com/en-us/documentation/articles/role-based-access-control-manage-access-powershell</a>.</li>
 	<li>MORE INFO For more information about design choices that are directly related to your business requirements, go to <a href="https://azure.microsoft.com/en-us/documentation/articles/active-directory-hybrid-identity-design-considerations-overview/" target="_blank">aka.ms/azhidcg</a> to read the Azure Hybrid Identity Design Considerations Guide.</li>
 	<li>Azure AD Connect has two scheduler processes that are responsible for synchronizing
passwords and general objects and attributes. By default, the scheduler runs every 30 minutes.</li>
 	<li>IMPORTANT If your AD FS and Web Application Proxy servers are behind a firewall, read the article at <a href="https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-ports" target="_blank">https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-ports</a> to understand which ports should be open.</li>
 	<li>Azure AD Premium5 access and usage reports are based on machine learning and help you to easily monitor and protect access to your Azure Active Directory tenant resources.</li>
 	<li>IMPORTANT For more information about the different Azure AD editions, go to
<a href="https://azure.microsoft.com/documentation/articles/active-directory-editions" target="_blank">https://azure.microsoft.com/documentation/articles/active-directory-editions</a>.</li>
 	<li>The Identity Protection capability in Azure AD works by calculating a user risk level for each user. You can use it to configure risk-based policies to automatically protect the identities of your organization.</li>
 	<li>To learn how to install and configure an on-premises Multi-Factor Authentication server, go to <a href="https://azure.microsoft.com/documentation/videos/multi-factor-authentication-server" target="_blank">https://azure.microsoft.com/documentation/videos/multi-factor-authentication-server</a>.</li>
 	<li>MORE INFO For design considerations regarding Azure Multi-Factor Authentication, go to <a href="https://azure.microsoft.com/documentation/articles/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements" target="_blank">https://azure.microsoft.com/documentation/articles/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements</a>.</li>
 	<li>Before you implement Azure Multi-Factor Authentication, you must understand what options are available to obtain this capability. If your license is for Azure AD Premium, Enterprise Mobility Suite, or Enterprise Cloud Suite, you automatically get Azure Multi-Factor Authentication. If you don’t have it, you can purchase separate Azure Multi-Factor Authentication licenses and assign them to your users.</li>
 	<li>In the Usage Model list, select Per Authentication or Per Enabled User. Notice the warning that says that after you select this method, you cannot change it.</li>
</ul>
<h2>Chapter 03: Azure Network Security</h2>
<ul>
 	<li>The reason for this is that the ASM model is being phased out and there is no future in it, so it would be best to migrate your ASM assets (if you have any) to the new Azure Resource Management model.</li>
 	<li>MORE INFO For more information about the differences between the ASM and Azure
Resource Management models, read the article “Azure Resource Manager vs. classic deployment: Understand deployment models and the state of your resources” at <a href="https://azure.microsoft.com/documentation/articles/resource-manager-deployment-model" target="_blank">https://azure.microsoft.com/documentation/articles/resource-manager-deployment-model</a>.</li>
 	<li>Microsoft takes advantage of the Windows Server software defined networking stack—also known as “ Hyper-V Network Virtualization” (HNV). With HNV, Microsoft can isolate each customer’s network from other customer networks by encapsulating each customer’s network communications within a generic routing encapsulation (GRE) head
that contains a field that is specifically for the customer. This effectively isolates each customer’s network from the others, even if different customers are using the same IP address schemes on their Azure Virtual Networks.</li>
 	<li>MORE INFO For more information about Hyper-V network virtualization, read the article “Hyper-V Network Virtualization Overview” on TechNet at <a href="https://technet.microsoft.com/library/jj134230(v=ws.11).aspx" target="_blank">https://technet.microsoft.com/library/jj134230(v=ws.11).aspx</a>.</li>
 	<li>Azure Virtual Networks require you to use private IP addresses (RFC 1918) for VMs. The address ranges are:
<ul>
 	<li>Class A: 10.0.0.0/24</li>
 	<li>Class B: 172.16.0.0/12</li>
 	<li>Class C: 192.168.1.0/24</li>
</ul>
</li>
 	<li>Just like with on-premises networking, you should carefully consider which IP address scheme you want to use, especially if you think you will connect your Azure Virtual Network to your on-premises network. In that scenario, you should make sure there is no overlap between the IP addresses you use on-premises and those you want to use on an Azure Virtual Network.</li>
 	<li>For VMs that perform roles requiring a static IP address, you can assign a static IP address to the VM. Keep in mind that you do not configure the NIC within the VM to use a static IP address. In fact, you should never touch the NIC configuration settings within a VM. All IP addressing information should be configured within the Azure portal or by using PowerShell Remoting in Azure.</li>
 	<li>Keep in mind that you cannot bring your own DHCP server. The VMs are automatically configured to use only the DHCP server provided by Azure.</li>
 	<li>MORE INFO For more information on IP addressing in Azure, read the article “IP
addresses in Azure” at <a href="https://azure.microsoft.com/documentation/articles/virtual-network-ip-addresses-overview-arm" target="_blank">https://azure.microsoft.com/documentation/articles/virtual-network-ip-addresses-overview-arm</a>.</li>
 	<li>When you create an Azure Virtual Network, you get a simple DNS server in the bargain, at no extra charge. This simple DNS server service provides you with basic name resolution for all VMs on the same Azure Virtual Network. Name resolution does not extend outside of the Azure Virtual Network.</li>
 	<li>The simple Azure Virtual Network DNS is not configurable. You can’t create your own A
records, SRV records, or any other kind of record. If you need more flexibility than simple name resolution, you should bring your own DNS server.</li>
 	<li>A Network Security Group is the equivalent of a simple stateful packet filtering firewall or
router.</li>
 	<li>NSGs use a 5-tuple to evaluate traffic:
<ul>
 	<li>Source and destination IP address</li>
 	<li>Source and destination port</li>
 	<li>Protocol: transmission control protocol (TCP) or user datagram protocol (UDP)</li>
</ul>
</li>
 	<li>This means you can control access between a single VM and a group of VMs, or a single VM to another single VM, or between entire subnets. Again, keep in mind that this is simple stateful packet filtering, not full packet inspection. There is no protocol validation or network level intrusion detection system (IDS) or intrusion prevention system (IPS) capability in a Network Security Group.</li>
 	<li>When you create an Azure Virtual Network and then define subnets within it, Azure automatically creates a collection of system routes that allows machines on the various subnets you’ve created to communicate with each other. You don’t have to define the routes, and the appropriate gateway addresses are automatically assigned by the DHCP server–provided addresses.</li>
 	<li>Take advantage of User Defined Routes. In Azure, you can use User Defined Routes to control the entries in the routing table and override the default settings.</li>
 	<li>For a virtual network security device, you configure the Azure routing table to forward all outbound and inbound connections through that device. When you want to prevent VMs from initiating outbound connections to the Internet, you configure forced tunneling.</li>
 	<li>MORE INFO For more information about User Defined Routes, read the article “What are User Defined Routes and IP Forwarding?” at <a href="https://azure.microsoft.com/documentation/articles/virtual-networks-udr-overview" target="_blank">https://azure.microsoft.com/documentation/articles/virtual-networks-udr-overview</a>. For more information about forced tunneling, read “Configure forced tunneling using the Azure Resource Manager deployment model” at <a href="https://azure.microsoft.com/documentation/articles/vpn-gateway-forced-tunneling-rm" target="_blank">https://azure.microsoft.com/documentation/articles/vpn-gateway-forced-tunneling-rm</a>.</li>
 	<li>MORE INFO For more information about more secure remote access that uses RDP and
other protocols, read the article “Securing Remote Access to Azure Virtual Machines over the Internet” at <a href="https://blogs.msdn.microsoft.com/azuresecurity/2015/09/08/securing-remote-access-to-azure-virtual-machines-over-the-internet" target="_blank">https://blogs.msdn.microsoft.com/azuresecurity/2015/09/08/securing-remote-access-to-azure-virtual-machines-over-the-internet</a>.</li>
 	<li>The SSTP VPN protocol is interesting because, unlike other methods of remote access VPN client/server connections (such as IPsec, LTP/IPsec, or PPTP), the SSTP protocol tunnels communications over the Internet by using a TLS-encrypted HTTP header. What this means in practice is that SSTP can be used across firewalls and web proxies.</li>
 	<li>This means that you can block direct inbound access for the RDP and SSH protocols to VMs on your Azure Virtual Network over the Internet and still reach them by using those protocols after you establish the VPN connection. This entire process is secure because you have to authenticate the VPN connection first, and then authenticate again with the RDP or SSH protocols.</li>
 	<li>With a point-to-site VPN, you can connect a single device (at a time) to an Azure Virtual Network. To be clear, that doesn’t mean that when you use a point-to-site VPN you can only connect a single device at a time, which would block all other connections to the Azure Virtual Network. What it means is that when you use a point-to-site VPN, only that device is connected to the Azure Virtual Network. Other devices can connect to the same Azure Virtual Network by using a point-to-site VPN at the same time.</li>
 	<li>Most industry standard on-premises VPN gateways work with the Azure VPN gateway. Note that in contrast to the point-to-site VPN connections that use SSTP, the site-to-site VPN uses IPsec tunnel mode for the site-to-site VPN connection.</li>
 	<li>Using site-to-site VPN connections has a couple of downsides:
<ul>
 	<li>Connections to Azure top out at around 200 megabits per second (Mbps).</li>
 	<li>They, by definition, traverse the Internet, which could be a security issue.</li>
</ul>
</li>
 	<li>The MPLS version of ExpressRoute tops out at around 1 Gbps, whereas the Exchange Provider option provides you with up to 10 Gbps.</li>
 	<li>MORE INFO To learn more about dedicated WAN links to Azure Virtual Networks, read the article “ExpressRoute Technical Overview” at <a href="https://azure.microsoft.com/documentation/articles/expressroute-introduction" target="_blank">https://azure.microsoft.com/documentation/articles/expressroute-introduction</a>.</li>
 	<li>MORE INFO To learn more about external load balancing, read the article “Load balancing for Azure infrastructure services” at <a href="https://azure.microsoft.com/documentation/articles/virtual-machines-linux-load-balance" target="_blank">https://azure.microsoft.com/documentation/articles/virtual-machines-linux-load-balance</a>.</li>
 	<li>MORE INFO To learn more about internal load balancing, read the article “Internal Load Balancer Overview” at <a href="https://azure.microsoft.com/documentation/articles/load-balancer-internal-overview" target="_blank">https://azure.microsoft.com/documentation/articles/load-balancer-internal-overview</a>.</li>
 	<li>MORE INFO To learn more about Traffic Manager and how you can take advantage of
all its global load balancing features, read the article “What is Traffic Manager?” at
<a href="https://azure.microsoft.com/documentation/articles/traffic-manager-overview" target="_blank">https://azure.microsoft.com/documentation/articles/traffic-manager-overview</a>.</li>
 	<li>At the time this chapter was written, you can’t get the same level of visibility into network
traffic that you can get on-premises. Many of the on-premises devices work at the Link layer (OSI layer 2), which is not available on Azure Virtual Networks. The reason for this is that Azure Virtual Networks make use of software-defined networking and network virtualization, so the lowest level of traffic analysis you can get is at the Network layer (OSI layer 3).</li>
 	<li>At this time, you have the ability to get some network information for traffic that moves
through Network Security Groups. In particular, you can:
<ul>
 	<li>Use Azure audit logs to get information about connections made through a Network Security Group.</li>
 	<li>View which Network Security Group rules are applied to VMs and instance roles based on the MAC address.</li>
 	<li>View how many times each Network Security Group rule was applied to deny or allow traffic.</li>
</ul>
</li>
 	<li>MORE INFO To learn more about how you can obtain logging information from Network
Security Groups, read the article “Log Analytics for Network Security Groups (NSGs)” at
<a href="https://azure.microsoft.com/documentation/articles/virtual-network-nsg-manage-log" target="_blank">https://azure.microsoft.com/documentation/articles/virtual-network-nsg-manage-log</a>.</li>
 	<li>MORE INFO To learn more about the Azure DNS service, read the article “Azure DNS Overview” at <a href="https://azure.microsoft.com/documentation/articles/dns-overview" target="_blank">https://azure.microsoft.com/documentation/articles/dns-overview</a>.</li>
 	<li>MORE INFO To learn more about what virtual network security devices are available in the Azure Marketplace, on the Azure Marketplace home page (<a href="https://azure.microsoft.com/en-us/marketplace" target="_blank">https://azure.microsoft.com/en-us/marketplace</a>), enter security in the search box. You can find Azure security partners at <a href="https://azure.microsoft.com/marketplace/?term=security" target="_blank">https://azure.microsoft.com/marketplace/?term=security</a>.</li>
 	<li>Azure has a reverse proxy service that you can use to proxy connections to your on-premises resources. The reverse proxy service is called Azure Active Directory Application Proxy. You won’t find this service in the list of Azure Active Directory products on Azure.com, and you won’t find it in the table of contents.</li>
 	<li>The Azure Application Proxy is already built into Azure, and you configure it so that when
client systems want to request resources on your on-premises servers, they actually make the request to the reverse proxy on Azure. The Azure Application Proxy forwards those requests back to your on-premises servers.</li>
 	<li>MORE INFO To learn more about the Azure Application Proxy, read the article “Publish applications using Azure AD Application Proxy” at <a href="https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish" target="_blank">https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish</a>.</li>
 	<li>Best practices are based on two things: the positive experience others have had using a specific practice and the confirmation that the best practices work across a number of environments.</li>
 	<li>If you plan to connect your on-premises network to one or more Azure Virtual Networks, you need to ensure that there are no IP address conflicts. That is to say, you have to ensure that the IP address ranges you select and the subnets you create on your Azure Virtual Networks do not overlap with what you have on-premises.</li>
 	<li>A better solution is to define subnets for each of these roles and then put each VM that supports these roles into a subnet created for each role. That leads you to putting the domain controllers on the domain controllers’ subnet, the database servers on the database server subnet, the web front ends on the web front-ends subnet, and so on.</li>
 	<li>Although Network Security Groups are useful for basic network access control, keep in mind that they do not provide you any level of application layer inspection. All you have control over is the source and destination IP address, source and destination TCP or UDP port number, and the direction to allow access.</li>
 	<li>Another thing to be aware of is that if you want to create restrictive access rules with
Network Security Groups, you have to be aware of what you might inadvertently block.</li>
 	<li>Another scenario you might not think of is communications outside of your Azure Virtual
Network, but still within the Azure fabric itself; for example, when you encrypt Azure
Virtual Machines by using Azure Disk Encryption. To encrypt your operating system and
data disks, the VM needs to be able to reach the Azure Key Vault Service and an Azure
Application (these are prerequisites for Azure Disk Encryption). If you lock down your
NSGs too tight, you won’t be able to reach the Key Vault or the Azure Active Directory
application, and your VMs won’t start because the disks can’t be unencrypted.</li>
 	<li>MORE INFO For more information about how to create a site-to-site VPN connection between two Azure Virtual Networks, read the article “Configure a VNet-to-VNet Connection by using Azure Resource Manager and PowerShell” at <a href="https://azure.microsoft.com/documentation/articles/vpn-gateway-vnet-vnet-rm-ps" target="_blank">https://azure.microsoft.com/documentation/articles/vpn-gateway-vnet-vnet-rm-ps</a>.</li>
 	<li>Regardless of what operating system you deploy in Azure Virtual Machines, you want to make sure that a host-based firewall is enabled, just as you do on-premises.</li>
 	<li>You should use IPsec for all communications that aren’t encrypted by some other method (such as HTTPS or encrypted SMB 3.0).</li>
 	<li>MORE INFO To learn more about how to use IPsec for server and domain isolation, read the article “Server and Domain Isolation Using IPsec and Group Policy” at <a href="https://technet.microsoft.com/library/cc163159.aspx" target="_blank">https://technet.microsoft.com/library/cc163159.aspx</a>.</li>
 	<li>When you put a VM on an Azure Virtual Network, you might notice that the VM can connect to any other VM on the same Azure Virtual Network, even if the other VMs are on different subnets. This is possible because there is a collection of system routes that are enabled by default that allow this type of communication.</li>
 	<li>You should configure User Defined Routes when you deploy a virtual network security appliance</li>
 	<li>MORE INFO To learn more about User Defined Routes, read the article “What are User Defined Routes and IP Forwarding” at <a href="https://azure.microsoft.com/documentation/articles" target="_blank">https://azure.microsoft.com/documentation/articles</a>
/virtual-networks-udr-overview.</li>
 	<li>The default routes for an Azure Virtual Network allow VMs to initiate traffic to the Internet. This process can pose a security risk because it represents a form of split tunneling, and these outbound connections could increase the attack surface of a VM and be used by attackers. For this reason, you should enable forced tunneling on your VMs when you have cross-premises connectivity between your Azure Virtual Network and your on-premises network.</li>
 	<li>MORE INFO To learn more about forced tunneling and how to enable it, read the article
“Configure forced tunneling using the Azure Resource Manager deployment model” at
<a href="https://azure.microsoft.com/en-us/documentation/articles/vpn-gateway-forced-tunneling-rm" target="_blank">https://azure.microsoft.com/en-us/documentation/articles/vpn-gateway-forced-tunneling-rm</a>.</li>
 	<li>If you require a higher level of network security than you can obtain with network-level access controls, then you should investigate and deploy Azure Virtual Network security appliances.</li>
 	<li>For all high-security deployments, you should consider deploying a perimeter network to
enhance the level of network security for your Azure resources.</li>
 	<li>MORE INFO To learn more about perimeter networks and how to deploy them in Azure, read the article “Microsoft Cloud Services and Network Security” at <a href="https://azure.microsoft.com/documentation/articles/best-practices-network-security" target="_blank">https://azure.microsoft.com/documentation/articles/best-practices-network-security</a>.</li>
 	<li>If you require an exceptional level of security or performance for your cross-premises connections, you should consider using Azure ExpressRoute for your cross-premises connectivity. ExpressRoute is a dedicated WAN link between your on-premises location or an Exchange hosting provider. Because this is a telco connection, your data doesn’t travel over the Internet and therefore is not exposed to the potential risks inherent in Internet communications.</li>
 	<li>MORE INFO To learn more about how Azure ExpressRoute works and how to deploy it, read the article “ExpressRoute Technical Overview” at <a href="https://azure.microsoft.com/documentation/articles/best-practices-network-security" target="_blank">https://azure.microsoft.com/documentation/articles/best-practices-network-security</a>.</li>
 	<li>You should consider using Azure Application Gateway when you have:
<ul>
 	<li>Applications that require requests from the same user or client session to reach the same back-end VM. Examples of this are shopping cart apps and web mail servers.</li>
 	<li>Applications that want to free web server farms from SSL termination overhead by taking advantage of Application Gateway’s SSL offload feature.</li>
 	<li>Applications, such as a content delivery network, that require multiple HTTP requests on the same long-running TCP connection to be routed or load balanced to different backend servers.</li>
</ul>
</li>
 	<li>MORE INFO To learn more about how Azure Application Gateway works and how you can use it in your deployments, read the article “Application Gateway Overview” at <a href="https://azure.microsoft.com/documentation/articles/application-gateway-introduction" target="_blank">https://azure.microsoft.com/documentation/articles/application-gateway-introduction</a>.</li>
 	<li>MORE INFO To learn more about how the Azure External Load Balancer works and how you can deploy it, read the article “Get Started Creating an Internet Facing Load Balancer in Resource Manager using PowerShell” at <a href="https://azure.microsoft.com/documentation/articles/load-balancer-get-started-internet-arm-ps" target="_blank">https://azure.microsoft.com/documentation/articles/load-balancer-get-started-internet-arm-ps</a>.</li>
 	<li>Point-to-site VPN is more secure than direct RDP or SSH connections because the user has to authenticate twice before connecting to a VM. First, the user needs to authenticate (and be authorized) to establish the point-to-site VPN connection; second, the user needs to authenticate (and be authorized) to establish the RDP or SSH session.</li>
 	<li>It is highly recommended that you enable Azure Security Center for all of your Azure
deployments.</li>
 	<li>Microsoft has created the Datacenter Extension Reference Architecture Diagram and supporting collateral to help you understand what such a datacenter extension would look like. This provides a reference implementation that you can use to plan and design a secure enterprise datacenter extension to the cloud. You should review this document to get an idea of the key components of a secure solution.</li>
 	<li>MORE INFO For more information about the Datacenter Extension Reference Architecture Diagram, read “Datacenter extension reference architecture diagram – Interactive” at <a href="https://gallery.technet.microsoft.com/Datacenter-extension-687b1d84" target="_blank">https://gallery.technet.microsoft.com/Datacenter-extension-687b1d84</a>.</li>
</ul>
<h2>Chapter 04: Data and Storage Security</h2>
<ul>
 	<li>Many people think of storage security as securing the disk on which the data is stored. Any security for the data itself is inherited from the security applied to the storage system. In contrast, data security is security applied directly to the data, so no matter what the storage medium is, the data remains as secure as possible.</li>
 	<li>With Azure Disk Encryption, you can encrypt both the operating system .vhd and any data disk .vhd files that you have attached to your VMs.</li>
 	<li>Azure Disk Encryption works for both Windows and Linux VMs. For Windows VMs, Microsoft uses BitLocker as the disk encryption technology. For Linux VMs, Microsoft uses dm-crypt.</li>
 	<li>Azure Disk Encryption supports the following scenarios:
<ul>
 	<li>You can bring a VM that you’ve already encrypted on-premises into Azure and use the same keys you used to encrypt that VM.</li>
 	<li>You can create a VM from the Microsoft Azure Marketplace and encrypt that VM as you create it.</li>
 	<li>You can have unencrypted VMs that are currently running in Azure and encrypt them.</li>
 	<li>You can unencrypt VMs that you have encrypted, regardless of whether you’ve encrypted them on-premises, encrypted them from the time you created them in Azure, or encrypted them after you created them.</li>
</ul>
</li>
 	<li>To help ensure the security of your keys, you can sort the keys (in the case of BitLocker) or the secrets (in the case of dm-crypt) in Azure Key Vault. Key Vault is the Azure “vaulting” solution that provides you with a hardware security module (HSM) in which you store your disk encryption keys.</li>
 	<li>The following lists key points you might want to know about Azure Disk Encryption:
<ul>
 	<li>Currently, no charges are incurred for encrypting VMs.</li>
 	<li>Not all operating systems can be encrypted.</li>
 	<li>Not all operating systems can be decrypted.</li>
 	<li>Not all types of virtual disk storage can be encrypted.</li>
 	<li>You can use the Azure command-line interface (CLI), Azure PowerShell, or Azure
Resource Manager templates to encrypt an Azure VM.</li>
 	<li>The Azure VM and the Key Vault you use to store the VM’s keys must be in the same Azure country/region.</li>
 	<li>An Azure Active Directory application must be configured for Azure Disk Encryption usage.</li>
 	<li>A Key Vault access policy must be configured.</li>
</ul>
</li>
 	<li>MORE INFO To get detailed information, read “Azure Disk Encryption for Windows and Linux Azure Virtual Machines” at <a href="https://gallery.technet.microsoft.com/Azure-Disk-Encryption-for-a0018eb0" target="_blank">https://gallery.technet.microsoft.com/Azure-Disk-Encryption-for-a0018eb0</a> or “Encrypt an Azure Virtual Machine” at <a href="https://azure.microsoft.com/documentation/articles/security-center-disk-encryption" target="_blank">https://azure.microsoft.com/documentation/articles/security-center-disk-encryption</a>.</li>
 	<li>You should always encrypt your Azure VMs, regardless of the role that VM performs on your network.</li>
 	<li>Azure Storage Service Encryption automatically encrypts blob files ( binary large objects)
when you save them to your Azure storage account. When you save the object to Azure storage, the object is automatically encrypted for you. When you read the file from storage, the file is automatically decrypted for you. You don’t need to maintain any keys or secrets—Azure does all that for you in the background.</li>
 	<li>The level of encryption used by Azure Storage Service Encryption is similar to what is used in the rest of Azure, which is Advanced Encryption Standard (AES)–256</li>
 	<li>Customers have asked whether VMs that have been encrypted by using Azure Disk
Encryption have significant overhead, because these machines would have double encryption if you also use Azure Storage Service Encryption. This double encryption causes nominal overhead. Although multiple encryption/decryption operations still take place, the overhead isn’t comparable to what you see with double encryption of network traffic because with storage encryption, you don’t have the protocol overhead also.</li>
 	<li>The following list provides key facts you should know about Azure Storage Service Encryption:
<ul>
 	<li>Only Azure Resource Manager storage accounts are supported.</li>
 	<li>You cannot encrypt classic storage accounts that have been migrated to Azure Resource Manager accounts.</li>
 	<li>Azure Storage Service Encryption will not encrypt data that exists in a storage account prior to enabling encryption on the account. If you enable storage encryption on a storage account that already has data in it, you will need to remove the data from the account and then put it back in, because the encryption takes place when the data is actually placed into the storage account.</li>
 	<li>VMs created by using images available from the Azure Marketplace are a special
situation: the base image will remain unencrypted, but any subsequent writes will be encrypted. Because your private data appears only on the subsequent writes, your information is more secured.</li>
 	<li>Other types of Azure storage are not encrypted by using Azure Storage Service
Encryption; this excludes table, queue, and file storage options.</li>
</ul>
</li>
 	<li>MORE INFO To learn more about Azure Storage Service Encryption, read the article “Azure Storage Service Encryption for Data at Rest” at <a href="https://azure.microsoft.com/documentation/articles/storage-service-encryption" target="_blank">https://azure.microsoft.com/documentation/articles/storage-service-encryption</a>.</li>
 	<li>Azure Files use the same SMB protocol currently used on-premises. Server and client
applications that use the SMB protocol to access file shares on-premises now can also access information in Azure Files. In fact, you can configure Azure file shares so that they are accessible over the Internet through TCP port 445.</li>
 	<li>One significant difference between on-premises file shares and Azure Files is the level of access control. On-premises, you can apply robust and granular access controls to file shares and you can assign even deeper NTFS permissions to the files inside of those file shares. With Azure Files, access to objects within the share is controlled by a single storage account key that gives the same level of access to all files. There is also no Azure Active Directory support for permissions assignment to data contained within the file shares.</li>
 	<li>MORE INFO You can learn more about creating a shared access policy by reading the “Generate a shared access signature for a file or file share” section of the article “Develop with File storage,” at <a href="https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files" target="_blank">https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files</a>
/#generate-a-shared-access-signature-for-a-file-or-file-share.</li>
 	<li>When you use the SMB 3.x protocol to access Azure Files, you can also take advantage of automatic and transparent encryption of file data over the wire.</li>
 	<li>If the client fully supports SMB 3.x, it will be able to transparently work with Azure File Storage to generate per-session encryption keys. The encryption protocol is AES-128 CCM (128-bit Advanced Encryption Standard with CCM mode), which provides some of the highest levels of security available and enables you to confidently access these file shares across any type of network.</li>
 	<li>You can still take advantage of accessing Azure File Shares over the Internet through site-to-site VPN connections. Or, if you want to avoid the Internet entirely, you can access Azure File Shares by using the SMB protocol through ExpressRoute.</li>
 	<li>MORE INFO To learn more about Azure Files, read the article “Get Started with Azure
File Storage on Windows” at <a href="https://azure.microsoft.com/documentation/articles" target="_blank">https://azure.microsoft.com/documentation/articles</a>
/storage-dotnet-how-to-use-files/#develop-with-file-storage.</li>
 	<li>You might consider using StorSimple for many reasons, including the following:
<ul>
 	<li>You can use StorSimple as a primary storage solution for your on-premises workloads, such as a file server, collaboration server, database server, and for VMs.</li>
 	<li>You can configure policies that offload “cold” data from the on-premises StorSimple appliance into Azure storage.</li>
 	<li>You can create automated storage snapshots and have the data backed up to Azure storage.</li>
 	<li>You can use StorSimple to help with disaster recovery by installing StorSimple appliances to your new on-premises locations and then retrieving the data you need from Azure storage.</li>
</ul>
</li>
 	<li>MORE INFO You can learn more about StorSimple at <a href="https://www.microsoft.com/en-us/server-cloud/products/storsimple/features.aspx" target="_blank">https://www.microsoft.com/en-us/server-cloud/products/storsimple/features.aspx</a>.</li>
 	<li>From a security perspective, StorSimple addresses four different security scenarios:
<ul>
 	<li>User authentication to the Azure storage account where the data is stored</li>
 	<li>StorSimple appliance access to the data stored in Azure storage</li>
 	<li>Security of the data as it moves over the network</li>
 	<li>Security of the data at rest, as it sits on the disk when not being accessed</li>
</ul>
</li>
 	<li>It is highly recommended that you become familiar with how to change access keys in the Azure portal and in your StorSimple systems. You should also configure Azure to regenerate access keys every 90 days.</li>
 	<li>StorSimple systems can connect to as many as 64 different storage accounts. You can use multiple storage accounts and their associated storage access keys to compartmentalize access to data in Azure Storage by department, role, team, project, or other categorizations that might work best for you.</li>
 	<li>Data transmission between the StorSimple system and cloud storage is encrypted by using Secure Sockets Layer (SSL), supporting up to AES-256 session encryption during data transfers between the StorSimple system and Azure Storage. This encryption is separate from the storage access keys and data-at-rest encryption, although both of these measures are also in force when data is on the wire.</li>
 	<li>StorSimple encrypts data stored in the cloud with an encryption key that you provide, and
also uses AES-256 encryption that is derived from a passphrase you define or one that is generated by a key management system for you. Because StorSimple can support up to 64 storage accounts, up to 64 different encryption keys can be used in a single StorSimple system.</li>
 	<li>In general, 16 million objects are distributed across an indeterminate number of cloud storage disks for every 1 terabyte (TB) of data stored in the cloud.</li>
 	<li>User identities are stored in Azure RMS as certificate files. When a user encrypts a document, a small RMS client application creates a content key and encrypts the document with that key. The RMS client application creates a certificate that includes a policy for the document. This policy has the rights for the users or groups and the restrictions on how the document can be used.</li>
 	<li>You should remember the following four key things about Azure RMS:
<ul>
 	<li>File content is never sent to the Azure RMS service. Microsoft never has access to the actual data.</li>
 	<li>Applications enable RMS protection by allowing the configuration and enforcement of access rights.</li>
 	<li>Applications use the Azure RMS SDK to communicate with the RMS service and servers.</li>
 	<li>Azure RMS takes advantage of Azure Rights Management, Active Directory RMS, Active Directory, and Azure Key Vault.</li>
</ul>
</li>
 	<li>MORE INFO To learn more about Azure Right Management, read the article “What is Azure Rights Management?” at <a href="https://docs.microsoft.com/rights-management/understand-explore/what-is-azure-rms" target="_blank">https://docs.microsoft.com/rights-management/understand-explore/what-is-azure-rms</a>.</li>
 	<li>Azure SQL provides a rudimentary firewall that allows simple source IP address access control. This is a popular feature because you can enforce access controls on a network level so that only IP addresses that you deem safe are allowed to connect to the Azure SQL Database server or specific databases contained within the server.</li>
 	<li>There are two types of firewall access rules you can configure:
<ul>
 	<li>Those that allow IP addresses that you define access to the entire Azure SQL Database server and all the databases contained within it</li>
 	<li>Those that allow IP addresses that you define access to specific databases contained within the Azure SQL Database server</li>
</ul>
</li>
 	<li>MORE INFO To learn more about the Azure SQL Firewall and how to configure it, read the article “Configure Azure SQL Database firewall rules - overview” at <a href="https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure" target="_blank">https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure</a>.</li>
 	<li>MORE INFO To learn more about SQL Always Encrypted, read the article “Always Encrypted (Database Engine)” at <a href="https://msdn.microsoft.com/library/mt163865.aspx" target="_blank">https://msdn.microsoft.com/library/mt163865.aspx</a>.</li>
 	<li>SQL row-level security (RLS) makes it possible for you to control access to rows in a database.</li>
 	<li>Access restriction logic is located in the database tier, in contrast to SQL Always Encrypted, which takes place away from the data at the client tier. The database service applies the access control each time there is an attempt to access the data.</li>
 	<li>MORE INFO To learn more about row-level security, read the article “Row-Level Security” at <a href="https://msdn.microsoft.com/library/dn765131.aspx" target="_blank">https://msdn.microsoft.com/library/dn765131.aspx</a>.</li>
 	<li>Transparent data encryption performs real-time encryption and decryption of both data and log files. The encryption process uses a database encryption key. The database encryption key is:
<ul>
 	<li>A symmetric key secured by a certificate stored in either the master database or the server.</li>
 	<li>An asymmetric key protected by an Extensible Key Management module.</li>
</ul>
</li>
 	<li>Transparent data encryption enables software IT pros to encrypt data by using AES-encryption and 3DES-encryption algorithms without requiring the need for developers to change existing applications.</li>
 	<li>MORE INFO To learn more about SQL transparent data encryption, read the article “Transparent Data Encryption (TDE)” at <a href="https://msdn.microsoft.com/library/bb934049.aspx" target="_blank">https://msdn.microsoft.com/library/bb934049.aspx</a>.</li>
 	<li>If the amount of data that must be encrypted is small or if the application can be designed to use cell-level encryption and if performance is not a concern, cell-level encryption is recommended over transparent data encryption. Otherwise, you should use transparent data encryption for encrypting existing applications.</li>
 	<li>MORE INFO To learn more about cell-level encryption, read the article “Recommendations for using Cell Level Encryption in Azure SQL Database” at <a href="http://i1.blogs.msdn.com/b/sqlsecurity/archive/2015/05/12/recommendations-for-using-cell-level-encryption-in-azure-sql-database.aspx" target="_blank">http://i1.blogs.msdn.com/b/sqlsecurity/archive/2015/05/12/recommendations-for-using-cell-level-encryption-in-azure-sql-database.aspx</a>.</li>
 	<li>Dynamic data masking hides protected data in the result set of a query over designated database fields without changing the actual data contained within the database. You don’t need to make any changes to your application to use this feature because the masking rules are applied in the results of the query when they are sent back to the client from the server.</li>
 	<li>You should be aware that dynamic data masking is not intended to prevent users
from connecting directly to a database and then running queries that might expose sensitive data. Therefore, consider dynamic data masking as a complement to other Microsoft SQL Server security features discussed.</li>
 	<li>MORE INFO To learn more about dynamic data masking, read the article “Dynamic Data
Masking” at <a href="https://msdn.microsoft.com/library/mt130841.aspx" target="_blank">https://msdn.microsoft.com/library/mt130841.aspx</a>.</li>
</ul>
<h2>Chapter 05: Virtual Machine Protection with Antimalware</h2>
<ul>
 	<li>Microsoft Antimalware for Azure Cloud Services and Virtual Machines is built on the
same common antimalware platform as Microsoft Security Essentials, Microsoft Forefront Endpoint Protection, Microsoft System Center Endpoint Protection, Microsoft Intune, and Windows Defender for Windows 10, Windows 8.1, and Windows 8.</li>
 	<li>The customer’s Azure storage is used to store the antimalware event information. The event provider source name is Microsoft Antimalware, which is recorded by the Antimalware service. The Antimalware service also uses the Azure Diagnostics extension to collect these events from the Azure system into tables in the customer’s Azure storage account.</li>
 	<li>IMPORTANT In Windows Server 2016, Microsoft Antimalware is called Windows Defender.</li>
 	<li>MORE INFO For more information about the capabilities of AMSI, go to
<a href="https://msdn.microsoft.com/library/windows/desktop/dn889588(v=vs.85).aspx" target="_blank">https://msdn.microsoft.com/library/windows/desktop/dn889588(v=vs.85).aspx</a>.</li>
 	<li>The default configuration settings have been preoptimized for running in the Azure environment. You can customize the default antimalware configuration settings as required for your Azure application or service deployment and apply them for the Antimalware deployment scenarios. Antimalware Client and Service is not installed by default in the VM’s platform; it is available as an optional security extension.</li>
 	<li>It is important to note that VMs created in 2015 or earlier that have an old version of the Virtual Machine guest agent might need to be manually updated to a newer version of the Virtual Machine guest agent before you deploy the antimalware. The older version of the Virtual Machine guest agent has an issue that results in the %temp% folder being filled with log files, and that prevents the antimalware installation from succeeding.</li>
 	<li>By default, the antimalware files are installed in %ProgramFiles%\Microsoft Security Client. The Antimalware user interface (UI) is not available in the VM; however, you can create custom policies to turn the UI on if your organization needs that. You can also use the mpcmdrun command line in the VM itself if you need to perform a manual scan.</li>
 	<li>MORE INFO To learn how to create custom policies to turn on the UI, read the blog at <a href="https://blogs.msdn.microsoft.com/azuresecurity/2016/03/09/enabling-microsoft-antimalware-user-interface-post-deploymen" target="_blank">https://blogs.msdn.microsoft.com/azuresecurity/2016/03/09/enabling-microsoft-antimalware-user-interface-post-deploymen</a>t.</li>
 	<li>Enabling Antimalware through the Azure portal does not enable its diagnostics logs. However, if you use PowerShell for Antimalware to enable it, PowerShell has an option to enable diagnostics logs.</li>
 	<li>For more information about this behavior, go to <a href="https://blogs.msdn.microsoft.com/azuresecurity/2016/04/19/enabling-diagnostics-logging-for-azure-antimalware" target="_blank">https://blogs.msdn.microsoft.com/azuresecurity/2016/04/19/enabling-diagnostics-logging-for-azure-antimalware</a>.</li>
 	<li>MORE INFO You can use PowerShell to deploy non-Microsoft antimalware solutions also. Read more about deployment of other antimalware solutions at <a href="https://azure.microsoft.com/blog/deploying-antimalware-solutions-on-azure-virtual-machines" target="_blank">https://azure.microsoft.com/blog/deploying-antimalware-solutions-on-azure-virtual-machines</a>.</li>
 	<li>MORE INFO The easiest way to monitor your VMs for antimalware compliance is by using Azure Security Center</li>
 	<li>IMPORTANT As a best practice, you should always install an antimalware solution on a VM.</li>
</ul>
<h2>Chapter 06: Key Management in Azure with Key Vault</h2>
<ul>
 	<li>When planning to adopt data encryption, you should also plan how to manage the encryption keys because if the keys are compromised, the data is no longer secure.</li>
 	<li>One important concept to keep in mind is the difference between a secret and a key. A
secret is any sequence of bytes under 10 kilobytes (KB) and used by authorized users and apps to write and read back the secret value. Key Vault stores these secrets by encrypting them with a unique key per vault. A key refers to a cryptographic key, such as RSA 2048. The key is used by authorized users and apps to import the key or ask the service to generate one key for them. In this case, authorized users cannot read it back; they must ask the service to decrypt or sign with the key. This provides higher isolation, at the cost of higher latency because every decryption requires a remote call to the service. If your app needs frequent, low-latency access to a key (for example, Secure Sockets Layer [SSL] keys), then the key should be stored as a secret. If your app reads the key at runtime and uses it locally, and the security is more important than performance, it should be stored as a key.</li>
 	<li>MORE INFO For more information about the Key Vault REST API, go to
<a href="https://msdn.microsoft.com/library/azure/dn903609.aspx" target="_blank">https://msdn.microsoft.com/library/azure/dn903609.aspx</a>.</li>
 	<li>MORE INFO For information about Key Vault, read the Developer’s Guide at
<a href="https://azure.microsoft.com/documentation/articles/key-vault-developers-guide" target="_blank">https://azure.microsoft.com/documentation/articles/key-vault-developers-guide</a>.</li>
</ul>
<h2>Chapter 07: Azure Resource Management Security</h2>
<ul>
 	<li>Azure Security Center is an Azure service that can be used to monitor your infrastructure
as a service (IaaS) resources, such as Azure Virtual Machines and Azure Virtual Network, in addition to PaaS resources such as Azure SQL Database.</li>
 	<li>Security Center can monitor one or more subscriptions while keeping a centralized view
of all resources through the dashboard. To detect threats, Azure Security Center uses global threat intelligence from Microsoft products and services, the Microsoft Digital Crimes Unit (DCU), the Microsoft Security Response Center (MSRC), and external feeds. For detection purposes, it also applies advanced analytics, including machine learning and behavioral analysis.</li>
 	<li>IMPORTANT You can use Role-Based Access Control (RBAC) to delegate administrative tasks to other IT personnel based on the need to access information. For more information about this, read “Azure Security Center Planning and Operations Guide” at <a href="https://azure.microsoft.com/documentation/articles/security-center-planning-and-operations-guide" target="_blank">https://azure.microsoft.com/documentation/articles/security-center-planning-and-operations-guide</a>.</li>
 	<li>Security Center integrates with an ecosystem of partners, making it easy for organizations to deploy and monitor a variety of security solutions, like endpoint protection, firewalls, and more.</li>
 	<li>When you enable data collection in the subscription, all resource groups inherit the
same security policy. However, if your organization requires different polices per resource group, you can disable inheritance and configure unique policies.</li>
 	<li>The prevention policies available are as follows:
<ul>
 	<li><strong>System updates</strong> This policy verifies whether the operating system running in the VMs monitored by Security Center is fully updated.</li>
 	<li><strong>Baseline rules</strong> This policy verifies the VM settings against a set of security baseline rules to verify whether the VMs are using a recommended configuration. Security Center uses Common Configuration Enumeration4 (CCE) to assign unique identifiers for configuration rules.</li>
 	<li><strong>Endpoint Protection</strong> This policy verifies whether the VM has an endpoint protection
solution installed on it. If it does not, Endpoint Protection suggests installing one.</li>
 	<li><strong>Network Security Group</strong> This policy evaluates your network security group and makes recommendations according to the current configuration.</li>
 	<li><strong>Web Application Firewall</strong> This policy evaluates whether there are web applications
exposed to vulnerabilities and suggests the installation of a WAF solution.</li>
 	<li><strong>Next Generation Firewall</strong> This policy verifies the current networking configuration and, based on the current configuration, might suggest an installation of a next-generation firewall solution.</li>
 	<li><strong>SQL Auditing</strong> This policy evaluates your current SQL Azure PaaS solution and verifies whether auditing is enabled in the database. If it is not enabled, SQL Auditing suggests that you enable it.</li>
 	<li><strong>SQL Transparent Data Encryption</strong> This policy evaluates your current SQL Azure PaaS solution and verifies whether the database has transparent data encryption enabled.</li>
</ul>
</li>
 	<li>You can download a Microsoft Excel file with all these rules from <a href="https://gallery.technet.microsoft.com/Azure-Security-Center-a789e335" target="_blank">https://gallery.technet.microsoft.com/Azure-Security-Center-a789e335</a>.</li>
 	<li>Azure Security Center uses a multi-layer approach to detect attacks on your Azure environment. The first layer is Network Analytics, which is used to detect incoming
brute-force attacks and compromised machines (bots) that are used for malicious
activity (for example, sending spam). This layer heavily uses machine learning to
build usage profiles in order to accurately perform the detections. The second layer is
Virtual Machines Behavior Analysis, which detects suspicious behavior on the VM by
analyzing security events and processes crash dumps. The third layer includes alerts
sent from deployed partner solutions and alerts generated by the Azure resources
themselves. Lastly, Azure Security Center fuses the alerts from the different layers into
incidents, which detail the attack timeline and what the attacker actually performed.</li>
 	<li>For more information about Azure SQL Server auditing, read the article “Get started with SQL database auditing” at <a href="https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started" target="_blank">https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started</a>.</li>
 	<li>MORE INFO You can also use Power BI to visualize Security Center data related to your security status, threats, and detections. For more information, read the article “Get insights from Azure Security Center data with Power BI” at <a href="https://azure.microsoft.com/documentation/articles/security-center-powerbi" target="_blank">https://azure.microsoft.com/documentation/articles/security-center-powerbi</a>.</li>
</ul>
<h2>Chapter 08: Internet of Things Security</h2>
<ul>
 	<li>For more information about MEMS, read the article “MEMS and More: Sensor Technologies that will drive the Internet of Things” at <a href="http://www.broadcom.com/blog/wireless-technology/mems-and-more-sensor-technologies-that-will-drive-the-internet-of-things" target="_blank">www.broadcom.com/blog/wireless-technology/mems-and-more-sensor-technologies-that-will-drive-the-internet-of-things</a>.</li>
 	<li>These devices are highly specialized computers made up of hardware, operating systems, and applications like any computer. However, they often run out-of-date operating systems and application software. Worse yet, it can’t be updated. That’s because in most cases the device vendors don’t write the software; they pull in components that already exist and modify them to fit their needs. Much of this code is not actively maintained or supported by the third-party developers who are the original authors.</li>
 	<li>For more information about IoT security in Azure, read the blog post “How Microsoft Azure engineers for IoT security” at <a href="https://blogs.microsoft.com/iot/2016/03/24/how-microsoft-azure-engineers-for-iot-security" target="_blank">https://blogs.microsoft.com/iot/2016/03/24/how-microsoft-azure-engineers-for-iot-security</a>.</li>
</ul>
<h2>Chapter 09: Hybrid Environment Monitoring</h2>
<ul>
 	<li>MORE INFO You can also deploy the agent by using a command-line interface (CLI) or PowerShell. For more information about automating this process, read the article “Connect Windows computers to Log Analytics” at <a href="https://azure.microsoft.com/documentation/articles/log-analytics-windows-agents" target="_blank">https://azure.microsoft.com/documentation/articles/log-analytics-windows-agents</a>.</li>
 	<li>For more information about notable issues, read the article “OMS security notable issues” at <a href="https://blogs.technet.microsoft.com/msoms/2016/05/31/oms-security-notable-issues" target="_blank">https://blogs.technet.microsoft.com/msoms/2016/05/31/oms-security-notable-issues</a>.</li>
</ul>
<h2>Chapter 10: Operations and Management in the Cloud</h2>
<ul>
 	<li>Azure Security Center helps you set security policies for your deployments, implement
security recommendations to ensure best practices are adhered to, and monitor
the security health of your assets, in addition to the partner solutions you might be
using.</li>
</ul>
