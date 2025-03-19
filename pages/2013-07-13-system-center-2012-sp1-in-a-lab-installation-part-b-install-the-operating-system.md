---
layout: page
title: System Center 2012 SP1 in a LAB - Installation (Part B - Install the Operating System)
date: 2013-07-13 11:37
author: AdinErmie
comments: true
categories: []
---
Now that we have created the VMs for our lab, we can install the Operating System (OS). Start by connecting to one of the VMs, either by double clicking on the VM in Hyper-V Manager, right click the VM and choose Connect, or click on Connect from the Action pane/menu.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/connect-to-vm.png"><img class="alignnone size-full wp-image-93" alt="Connect To VM" src="http://adinermie.files.wordpress.com/2013/07/connect-to-vm.png" width="362" height="333" /></a></p>
When you have the VM connection up, and an ISO mounted, power the VM on.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/vm-off.png"><img class="alignnone size-large wp-image-162" alt="VM Off" src="http://adinermie.files.wordpress.com/2013/07/vm-off.png?w=584" width="584" height="457" /></a></p>
On the Windows Setup screen, select the Language, Time/Currency Format, and Keyboard Method appropriate, and click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/os-install-01.png"><img class="alignnone size-large wp-image-114" alt="OS Install 01" src="http://adinermie.files.wordpress.com/2013/07/os-install-01.png?w=584" width="584" height="438" /></a></p>
All you have to do now is click Install Now.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/os-install-02.png"><img class="alignnone size-large wp-image-115" alt="OS Install 02" src="http://adinermie.files.wordpress.com/2013/07/os-install-02.png?w=584" width="584" height="438" /></a></p>
Next you have to choose the Operating System and version you want to install. In our lab example, I will choose Windows Server 2012 Standard (Server with a GUI). Make your selection and then click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/os-install-03.png"><img class="alignnone size-large wp-image-116" alt="OS Install 03" src="http://adinermie.files.wordpress.com/2013/07/os-install-03.png?w=584" width="584" height="438" /></a></p>
You will have to accept the license terms, and then click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/os-install-04.png"><img class="alignnone size-large wp-image-117" alt="OS Install 04" src="http://adinermie.files.wordpress.com/2013/07/os-install-04.png?w=584" width="584" height="438" /></a></p>
For the Installation Type, since we don’t already have an OS installed, we will choose the ‘Custom: Install Windows only (advanced)’ option.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/os-install-05.png"><img class="alignnone size-large wp-image-118" alt="OS Install 05" src="http://adinermie.files.wordpress.com/2013/07/os-install-05.png?w=584" width="584" height="438" /></a></p>
Now select the hard drive that you want to install the OS to. Since we only created one hard drive when setting up the VM, we only have one to choose from. Select it, and click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/os-install-06.png"><img class="alignnone size-large wp-image-119" alt="OS Install 06" src="http://adinermie.files.wordpress.com/2013/07/os-install-06.png?w=584" width="584" height="438" /></a></p>
Now all you have to do is wait for the installation to finish.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/os-install-07.png"><img class="alignnone size-large wp-image-120" alt="OS Install 07" src="http://adinermie.files.wordpress.com/2013/07/os-install-07.png?w=584" width="584" height="438" /></a></p>
Once the installation is complete, you will be prompted to enter a password for the local administrator account. This is different from a domain-based local administrator account. Enter a password and click Finish.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/os-install-08.png"><img class="alignnone size-large wp-image-121" alt="OS Install 08" src="http://adinermie.files.wordpress.com/2013/07/os-install-08.png?w=584" width="584" height="438" /></a></p>
After some final quick configuration, you will then be presented with the login screen.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/os-install-09.png"><img class="alignnone size-large wp-image-122" alt="OS Install 09" src="http://adinermie.files.wordpress.com/2013/07/os-install-09.png?w=584" width="584" height="438" /></a></p>
Now repeat these steps for the other VMs in the lab.

NOTE: After you install an OS, you will need to rename the computer within the OS. To do this in Server 2012, launch Server Manager, and click on Local Server.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/local-server.png"><img class="alignnone size-full wp-image-102" alt="Local Server" src="http://adinermie.files.wordpress.com/2013/07/local-server.png" width="578" height="227" /></a></p>
Then click on the computer name. This will launch the System Properties dialog. From this dialog, click the Change button.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/system-properties-01.png"><img class="alignnone size-large wp-image-156" alt="System Properties 01" src="http://adinermie.files.wordpress.com/2013/07/system-properties-01.png?w=584" width="584" height="438" /></a></p>
From this dialog, enter the name you want to call the computer. In my lab, I called the Active Directory computer “AD”.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/system-properties-02.png"><img class="alignnone size-large wp-image-157" alt="System Properties 02" src="http://adinermie.files.wordpress.com/2013/07/system-properties-02.png?w=584" width="584" height="438" /></a></p>
Press OK after entering the name. You will encounter the following prompt. Click OK. Then click Close on the System Properties dialog.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/system-properties-03.png"><img class="alignnone size-large wp-image-158" alt="System Properties 03" src="http://adinermie.files.wordpress.com/2013/07/system-properties-03.png?w=584" width="584" height="438" /></a></p>
You can choose to either Restart Now or Restart Later, but the name change will not take effect until you do so.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/system-properties-04.png"><img class="alignnone size-large wp-image-159" alt="System Properties 04" src="http://adinermie.files.wordpress.com/2013/07/system-properties-04.png?w=584" width="584" height="438" /></a></p>
