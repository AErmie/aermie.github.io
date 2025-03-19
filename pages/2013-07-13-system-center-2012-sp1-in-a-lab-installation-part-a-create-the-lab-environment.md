---
layout: page
title: System Center 2012 SP1 in a LAB – Installation (Part A – Create The Lab Environment)
date: 2013-07-13 11:35
author: AdinErmie
comments: true
categories: []
---
<h1><span style="color:#000000;font-weight:bold;font-style:inherit;line-height:1.625;">Introduction:</span></h1>
I use Hyper-V in my LAB and that's what all these virtual machines will be running on. In my lab, I have Windows Server 2012 Datacenter installed as the server OS on the host machine. All other virtual machines will be running Windows Server 2012 Standard edition, with the graphical user interface (GUI).

My hardware consists of the following:
<ul>
	<li>Intel Xeon E5-2620</li>
	<li>Asus P90X79 WS</li>
	<li>64 GB G.Skill Ripjaws Z Series</li>
	<li>2 x 256 GB + 1 x 512 GB Samsung 840 Pro Series SSD</li>
</ul>
<h2>High Level Plan</h2>
Here is a high level of what we are going to complete in this initial part of the series.
<ol>
	<li>Create the Lab Environment</li>
	<li>Install the Operating System</li>
	<li>Install Active Directory Domain Services</li>
	<li>Install SQL Server</li>
</ol>
So now let’s start with the first part, creating the lab environment.

NOTE: For product specific details, see my page on <a title="VM&nbsp;Sizing" href="http://adinermie.com/lab-environment/vm-sizing/">VM Sizing</a>, and <a title="SQL Server&nbsp;Features" href="http://adinermie.com/lab-environment/sql-server-features/">SQL Server Features</a>.
<h1>Create the Lab Environment:</h1>
<h2>Hyper-V Configuration</h2>
As mentioned, my environment uses Hyper-V. So, we’re going to start by configuring Hyper-V for our needs, and creating the Virtual Machines (VMs) required for our lab.

The first thing we need to do is setup a Virtual Switch for the VMs to connect through.

Launch Server Manager, click on Tools, and select Hyper-V Manager.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/server-manager-add-role.png"><img class="alignnone size-large wp-image-125" alt="Server Manager - Add Role" src="http://adinermie.files.wordpress.com/2013/07/server-manager-add-role.png?w=584" width="584" height="438" /></a></p>
When Hyper-V loads, it will have nothing in it. Even if we were to create a VM, it wouldn’t have a network connection to use.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/hyper-v-manager.png"><img class="alignnone size-large wp-image-100" alt="Hyper-V Manager" src="http://adinermie.files.wordpress.com/2013/07/hyper-v-manager.png?w=584" width="584" height="442" /></a></p>
So we’ll start with creating a Virtual Switch. As you can from my screenshot, I have 2 LAN ports on my host. One of them has a connection to my home network and the Internet.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/network-connections.png"><img class="alignnone size-large wp-image-103" alt="Network Connections" src="http://adinermie.files.wordpress.com/2013/07/network-connections.png?w=584" width="584" height="117" /></a></p>
In the Hyper-V Manager, click the Virtual Switch Manager from the Actions pane.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/virtual-switch-manager.png"><img class="alignnone size-large wp-image-161" alt="Virtual Switch Manager" src="http://adinermie.files.wordpress.com/2013/07/virtual-switch-manager.png?w=584" width="584" height="550" /></a></p>
Now, click on the Create Virtual Switch button.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/new-virtual-switch.png"><img class="alignnone size-large wp-image-105" alt="New Virtual Switch" src="http://adinermie.files.wordpress.com/2013/07/new-virtual-switch.png?w=584" width="584" height="550" /></a></p>
From here, you now need to configure the virtual switch that your VMs will use. Give it a name to clearly identify it (in my case I called it ‘External Network’), and choose the connection type. For more information about virtual networks, see the following TechNet article:&nbsp;<a href="http://technet.microsoft.com/en-us/library/cc816585(v=ws.10).aspx">http://technet.microsoft.com/en-us/library/cc816585(v=ws.10).aspx</a>.

Here is an excerpt from the article:
<ul>
	<li><b>External virtual networks.</b>&nbsp;Use this type when you want to provide virtual machines with access to a physical network to communicate with externally located servers and clients. This type of virtual network also allows virtual machines on the same virtualization server to communicate with each other. This type of network may also be available for use by the management operating system, depending on how you configure the networking. (The management operating system runs the Hyper-V role.) For more information, see “A closer look at external virtual networks” later in this topic.</li>
	<li><b>Internal virtual networks.</b>&nbsp;Use this type when you want to allow communication between virtual machines on the same virtualization server and between virtual machines and the management operating system. This type of virtual network is commonly used to build a test environment in which you need to connect to the virtual machines from the management operating system. An internal virtual network is not bound to a physical network adapter. As a result, an internal virtual network is isolated from all external network traffic.</li>
	<li><b>Private virtual networks.</b>&nbsp;Use this type when you want to allow communication only between virtual machines on the same virtualization server. A private virtual network is not bound to a physical network adapter. A private virtual network is isolated from all external network traffic on the virtualization server, as well any network traffic between the management operating system and the external network. This type of network is useful when you need to create an isolated networking environment, such as an isolated test domain.</li>
</ul>
For our demonstration, we are going to use an External Network so that the VMs can communicate with the Host system. Make all the appropriate selections and so forth, and then press OK. You may encounter the following warning message. This is because we are remotely connecting to the Host machine using the same network connection that we are about to setup as a Virtual Switch (hence selecting the ‘Allow management operating system to share this network adapter’ checkbox). Press ‘Yes’ to the dialog.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/apply-networking-changes.png"><img class="alignnone size-full wp-image-85" alt="Apply Networking Changes" src="http://adinermie.files.wordpress.com/2013/07/apply-networking-changes.png" width="366" height="252" /></a></p>
Now that we have the virtual switch setup, we can start creating VMs for our lab.

Here is a video of this.
[youtube http://www.youtube.com/watch?v=FA3RNocGgyU&amp;w=640&amp;h=480]
<h2>Create the Virtual Machines</h2>
Let’s now create the VM’s we will need for the lab, specifically one for Active Directory, and another for any System Center product you plan on installing.

In Hyper-V Manager, from the Actions pane, click on New and choose Virtual Machine.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/new-virtual-machine.png"><img class="alignnone size-large wp-image-104" alt="New Virtual Machine" src="http://adinermie.files.wordpress.com/2013/07/new-virtual-machine.png?w=584" width="584" height="375" /></a></p>
On the New Virtual Machine wizard beginning screen, click read the information presented and then click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/new-vm-01.png"><img class="alignnone size-large wp-image-106" alt="New VM 01" src="http://adinermie.files.wordpress.com/2013/07/new-vm-01.png?w=584" width="584" height="439" /></a></p>
Enter a name for the VM. Note that this is NOT the name the VM will have within the Operating System (unless you name it the same), but rather, used as an identifier in Hyper-V Manager. After you have entered a name, click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/new-vm-02.png"><img class="alignnone size-large wp-image-107" alt="New VM 02" src="http://adinermie.files.wordpress.com/2013/07/new-vm-02.png?w=584" width="584" height="439" /></a></p>
Now assign the amount of memory you want your VM to have, and then press Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/new-vm-03.png"><img class="alignnone size-large wp-image-108" alt="New VM 03" src="http://adinermie.files.wordpress.com/2013/07/new-vm-03.png?w=584" width="584" height="439" /></a></p>
This is the screen where you connect your VM to the network that we created, then press Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/new-vm-04.png"><img class="alignnone size-large wp-image-109" alt="New VM 04" src="http://adinermie.files.wordpress.com/2013/07/new-vm-04.png?w=584" width="584" height="439" /></a></p>
This is the screen where you configure how large a hard drive the VM will have. Make the appropriate&nbsp;customization&nbsp;and click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/new-vm-05.png"><img class="alignnone size-large wp-image-110" alt="New VM 05" src="http://adinermie.files.wordpress.com/2013/07/new-vm-05.png?w=584" width="584" height="439" /></a></p>
For the Installation Options, choose if you will install an OS later, or if you want to use an ISO, then click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/new-vm-06.png"><img class="alignnone size-large wp-image-111" alt="New VM 06" src="http://adinermie.files.wordpress.com/2013/07/new-vm-06.png?w=584" width="584" height="439" /></a></p>
&nbsp;On the Summary screen, review your selections and entries, and click Finish.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/new-vm-07.png"><img class="alignnone size-large wp-image-112" alt="New VM 07" src="http://adinermie.files.wordpress.com/2013/07/new-vm-07.png?w=584" width="584" height="439" /></a></p>
Once the VM is created, it will appear in the Hyper-V Manager.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/new-vm-08.png"><img class="alignnone size-large wp-image-113" alt="New VM 08" src="http://adinermie.files.wordpress.com/2013/07/new-vm-08.png?w=584" width="584" height="442" /></a></p>
If you want to configure further settings, like the number of CPUs and mounting an OS ISO, right click on the VM and choose Settings or click on Settings from the Actions pane.
<p align="center">&nbsp;<a href="http://adinermie.files.wordpress.com/2013/07/vm-settings.png"><img class="alignnone size-full wp-image-164" alt="VM Settings" src="http://adinermie.files.wordpress.com/2013/07/vm-settings.png" width="486" height="337" /></a></p>
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/vm-settings-02.png"><img class="alignnone size-full wp-image-163" alt="VM Settings 02" src="http://adinermie.files.wordpress.com/2013/07/vm-settings-02.png" width="183" height="270" /></a></p>
Repeat these steps for each VM you need to create, in our case one for Active Directory and another for whichever System Center product you plan on installing.

Here is a video detailing this.

[youtube http://www.youtube.com/watch?v=Fl9_4AZv1jw&amp;w=640&amp;h=480]

See my page on <a title="VM&nbsp;Sizing" href="http://adinermie.com/lab-environment/vm-sizing/">VM Sizing</a> for product specific details.
