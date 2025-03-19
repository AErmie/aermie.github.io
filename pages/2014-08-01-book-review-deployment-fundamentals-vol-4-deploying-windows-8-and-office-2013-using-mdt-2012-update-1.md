---
layout: page
title: Book Review: Deployment Fundamentals, Vol. 4: Deploying Windows 8 and Office 2013 Using MDT 2012 Update 1
date: 2014-08-01 21:54
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2014/08/Deployment-Fundamentals-Vol4-Cover.jpg"><img class="alignleft size-full wp-image-9941" src="/wp-content/uploads/2014/08/Deployment-Fundamentals-Vol4-Cover.jpg" alt="Deployment Fundamentals Vol4 Cover" width="260" height="324" /></a>Recently, I finished reading the <a href="http://www.amazon.com/dp/9197939080/ref=cm_sw_su_dp" target="_blank">Deployment Fundamentals, Vol. 4: Deploying Windows 8 and Office 2013 Using MDT 2012 Update 1</a> eBook.

The chapters that I found most helpful were Chapter 8 "Creating Reference Images", and Chapter 9 "Deploying Windows 8 Using MDT 2012 Update 1", hence the majority of my highlights are from these chapters.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: Deployment School</h3>
<div>
<ul>
	<li>In Windows 8, there is a similar feature built into the operating system named Push Button Reset. The core difference is that the Push Button Reset feature does not restore legacy application settings, only the new Windows 8 applications.</li>
	<li>Sometimes the replace is used even if you would like to keep your old hardware. If the machine is using a third-party disk encryption system, it could be faster to treat the scenario as a replace to avoid decrypting the hard drive before deployment, or spending time getting refresh scenarios to work.</li>
	<li>Currently you cannot add Service Packs via offline servicing.</li>
	<li>In general, a thin image is more suitable in a dynamic environment</li>
	<li>If you do decide to use applications in the image, make sure that applications are Sysprep aware. For example, never, ever, put the antivirus software in the reference image. It’s the most common cause of Sysprep breaking. Other applications that don’t fit in an image are applications that include unique identifiers.</li>
	<li>If your activation server is running Windows Server 2012, you can use the new Active Directory-Based Activation service for your Windows 8 clients. The only requirement is that you have extended the Active Directory schema. Active Directory-Based Activation is configured by adding the Volume Activation Services role.</li>
	<li>If you need to support older clients like Windows 7, you still need to use the Key Management Service (KMS).</li>
	<li>You also can use an existing Windows 7 or Windows Server 2008 R2 KMS host to activate Windows 8 clients, but first you need to apply the http://support.microsoft.com/kb/2691586 hotfix on your KMS host</li>
	<li>Microsoft’s own drive encryption solution is named BitLocker, and it actually provides volume encryption rather than full disk encryption</li>
	<li>The Windows 8 version of BitLocker also supports hardware-based encryption.</li>
</ul>
&nbsp;

</div>
<div>
<h3>Chapter 02: Deployment Tools of the Trade</h3>
<div>
<ul>
	<li>The /LimitAccess switch configures DISM to get the files only from a local source.</li>
	<li>USMT only backs up local data and local profiles; you cannot point USMT to a share with roaming profiles.</li>
	<li>Some network card vendors, like Broadcom, create special versions of their drivers that only work in Windows PE.</li>
	<li>You can also extend WinRE and add your own tools if needed</li>
	<li>Windows Server 2012, WDS also can be used for the Network Unlock feature (BitLocker).</li>
	<li>In some cases, you need to modify TFTP Maximum Block Size settings for performance tuning reasons, especially when PXE traffic travels through routers and such</li>
	<li>Compare against industry best practices. You can compare your configurations against prebuilt baselines for both clients and servers.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 03: Windows 8</h3>
<div>
<ul>
	<li>The client version of Hyper-v does require that the hardware have support for SLAT (Second-Level Address Translation), and the reason is very simple. Without SLAT support, the parent partition (that’s the name of the OS that maintain all the child partitions or VMs) will be affected (bad performance).</li>
	<li>You need to allow the execution of scripts. (The default setting is to allow signed scripts only.)</li>
	<li>Using the New-PSSession cmdlet, you can now disconnect from a session without disrupting the commands that are running in the session. That means that you can connect to a machine, reboot it, and then reconnect using the session.</li>
	<li>ISE now automatically saves your open scripts every two minutes in a separate location. If something goes wrong, ISE recovers the scripts that were open in the last session the next time ISE starts, even if the scripts were not saved.</li>
	<li>Windows Server 2012 is provided in four different editions: Datacenter, Standard, Essentials, and Foundation.</li>
	<li>The GPO settings option you are looking for is called Enable Automatic Hosted Cache Discovery by Service Connection Point, and it is located under Computer Configuration Administrative Templates Network BranchCache.</li>
	<li>In Windows 8, you must import the PowerShell modules you need to use. In Windows Server 2012, that is unnecessary.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 04: Office 2013</h3>
<div>
<ul>
	<li>Sometimes customers ask why they should save the MSP file with some kind of strange name that might look like this: 0_Default.MSP. The reason is very simple: you want to make sure it has a name that ends up at the top of the files in the updates folder. If it starts with 0, it is very likely to be first. Now the reason you want this file to be at the top is because that’s the order Office process all the files, and you really want the customization to be the first step</li>
</ul>
&nbsp;

</div>
<h3>Chapter 05: ViaMonstra Inc and the Proof-of-Concept Environment</h3>
<div>
<ul>
	<li>NONE</li>
</ul>
&nbsp;

</div>
<h3>Chapter 06: Planning and Preparing for Windows 8 Deployment</h3>
<div>
<ul>
	<li>One of the most common issues with MAP inventory is related to the firewall not being opened for WMI.</li>
	<li>Although App-V allows you to run multiple versions of an application on the same machine, it is not a compatibility tool to address applications not working on a new OS. Virtualizing an application does not necessarily mean it will work on Windows 8.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 07: MDT 2012 Update 1</h3>
<div>
<ul>
	<li>System Center 2012 Orchestrator integration. The ability to call Orchestrator Runbooks as part of the task sequence.</li>
	<li>You cannot add an application just anywhere in the task sequence. It needs to be in the state restore phase (or after).</li>
	<li>For sharing the folders using Windows Explorer, we don’t recommend using the File Sharing Wizard in Windows Server 2012 (the Share button) since it resets some of the built-in permissions. Instead, make sure to select Advanced Sharing.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 08: Creating Reference Images</h3>
<div>
<ul>
	<li>You can also use this reference image for other deployment solutions, like System Center 2012 Virtual Machine manager (SCVMM), or the Windows Server 2012 VDI scenario. However, if you do, you need to make sure MDT deletes the Unattend.xml file in the image before turning of the machine</li>
	<li>Windows 8 (and earlier versions of Windows), the total folder path length must be fewer than 248 characters, and full path to a file must be fewer than 260 characters. In previous versions of Windows, these limits have not been a real deployment issue, but with Windows 8, the folders on the installation media are up to 168 characters which leaves only 79 characters for the MDT deployment share path. To make sure you don’t run into the following error message, “The specified path, file name, or both are too long. The fully qualified file name must be less than 260 characters, and the directory name must be less than 248 characters,” we have chosen a naming convention for the operating systems that is a bit shorter than we normally would use.</li>
	<li>If you use the Security and Privacy Settings to configure trusted zones, they will act as a preference, unlike if you use Group Policy to configure the settings. This means the users can still modify the settings, but you provide them with a good starting point.</li>
	<li>The reason for naming the file with a 0 (zero) at the beginning is that the Updates folder also handles Microsoft Office updates, and they are installed in alphabetical order. The Office 2013 setup works best if the customization file is installed before any updates.</li>
	<li>To keep the image as clean as possible, we don’t recommend installing the VMware Tools in the reference image.</li>
	<li>In VMware, if you don’t install the VMware Tools and open Device Manager in your virtual machine, you may see that the virtual machine is missing the driver for the VMware VMCI Bus. This is nothing to be alarmed about; the Sysprep process in Windows 8 (unlike Windows XP) is very good at cleaning out even undetected devices.</li>
	<li>The Task Sequence Windows Update action supports getting updates directly from Microsoft Windows Update, but you get a more stable patching if you use a local WSUS server. WSUS also allows for an easy process of approving the patches that you are deploying.</li>
	<li>The reason for adding the applications after the Tattoo action but before Windows update is simply to save time during the deployment. This way we can add all applications that will upgrade some of the built in components and therefore avoiding unnecessary “Windows Updating”.</li>
	<li>The goal when creating a reference image is of course to automate everything. But sometimes you have that special configuration, or application setup that is just too time-consuming to automate. If you need to do some manual configuration, you can add a little-known feature called LTI Suspend. If you add the LTISuspend.wsf script as a custom action in the task sequence, it will suspend the task sequence until you click the resume task sequence shortcut on the desktop. In addition to using the Suspend feature for manual configuration or installation, you can also use it simply for verifying a reference image before you allow the task sequence to continue and sysprep and capture the virtual machine.</li>
	<li>the Unattend.xml must match the exact version of the operating system you are servicing.</li>
	<li>In MDT, there are always two rule files, the CustomSettings.ini file and the Bootstrap.ini file</li>
	<li>The easiest way to find out the current time zone name on a Windows 8 machine is to run tzutil /g in a command prompt. You can also run tzutil /l to get a listing of all available time zone names</li>
</ul>
&nbsp;

</div>
<h3>Chapter 09: Deploying Windows 8 Using MDT 2012 Update 1</h3>
<div>
<ul>
	<li>You can also run the provided sample PowerShell script: CreateMDTProductionDriverFolders.ps1 to create the folder structure in the Deployment Workbench.</li>
	<li>Use the Lenovo ThinkVantage Update Retriever software to download the drivers. The trick to the Update Retriever is to specify the correct Lenovo Machine Type for the actual hardware (the first four characters of the model name).</li>
	<li>The main reason not to rely on plug and play for driver detection is its limitations. The first limitation is that it only can detect drivers for devices that are activated in the BIOS. As an example, if Bluetooth is disabled, plug and play might not detect the Bluetooth device. Another issue is multi-tier drivers. Since plug and play scanning only detects the first level of drivers, it will only copy half the drivers needed. That means it will only copy the bus driver since that was detected, but the other drivers for that device are never copied, resulting in a yellow exclamation mark on the device in Device Manager and possibly a sad user.</li>
	<li>In Windows 8 Enterprise, you can use CopyProfile to preserve a customized tile layout of groups on the Windows 8 Start screen. For more details on the CopyProfile feature, check this article: <a href="http://technet.microsoft.com/en-us/library/hh825135.aspx.">http://technet.microsoft.com/en-us/library/hh825135.aspx.</a></li>
	<li>One important setting is the Scratchspace size which is the temporary space used for log files, driver extraction and other temporary usages during deployment. The default 32 MB is simply too little for production deployment.</li>
	<li>Multicast requires that Windows Deployment Services (WDS) is running on Windows Server 2008 or later. In addition to the core MDT 2012 Update 1 setup for multicast, the network needs to be configured to support multicast.</li>
	<li>The multicast solution uses IGMPv3.</li>
	<li>Please don’t use USB hard drives for your offline media deployments; There are simply too many known issues with this. Use USB sticks instead. While you may get offline media deployment to work from a USB hard drive, we have seen too many cases where it fails because of the BIOS version/configuration or hard drive model being used. The symptom is that MDT tries to deploy the image to the external hard drive instead of using the internal drive, this because of how WinPE enumerates the drives.</li>
	<li>When creating offline media, you need to create the target folder first, and whatever you do, never, ever, create a subfolder inside the deployment share folder because that will break the offline media</li>
</ul>
&nbsp;

</div>
<h3>Chapter 10: Building a Distributed Environment</h3>
<div>
<ul>
	<li>The most common content replication solutions with MDT 2012 Update 1 are to use either the MDT linked deployment share feature or Distributed File System Replication (DFS-R)</li>
	<li>When you have multiple deployment servers sharing the same content, you need to configure the Bootstrap.ini file with information on which server to connect to based on which site the client is in. In MDT, that can be done by using the DefaultGateway property.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 11: Using Computer Refresh</h3>
<div>
<ul>
	<li>In addition to the USMT backup, you can enable an optional full WIM backup of the machine by configuring the MDT rules</li>
	<li>If you have many user domain profiles on your machines, it probably makes more sense to use the /uel switch which excludes profiles that have not been accessed within a specific number of days. For example, adding /uel:60 will configure ScanState (or LoadState) not to include profiles that haven’t been accessed for more than 60 days. The option of combining /ui and /uel is new in USMT 5.0</li>
</ul>
&nbsp;

</div>
<h3>Chapter 12: Replace a Computer</h3>
<div>
<ul>
	<li>If you add WipeDisk=YES to your rules, MDT will also do a secure wipe of the old machine.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 13: Inside the Matrix - Bending the Rules</h3>
<div>
<ul>
	<li>Even though it’s not a BitLocker requirement, we recommend configuring BitLocker to store the recovery key and TPM owner information in Active Directory. In this book, you learn how to enable this for the ViaMonstra environment. For additional detailed information about these features, see: <a href="http://tinyurl.com/ylrhssa.">http://tinyurl.com/ylrhssa.</a></li>
	<li>To enable BitLocker to store the recovery key and TPM information in Active Directory, you need to create a group policy for it in Active Directory. Since you are running Windows Server 2012, you don’t need to extend the schema, but you do need to set the appropriate permissions in Active Directory.</li>
	<li>Be careful when using the serial number to assign computer names. A serial number can contain more than 15 characters, and the Windows setup will be quite upset if you try to use a computer name with more than 15 characters.</li>
	<li>Named Pipes simply works best for connecting from WinPE to the SQL database.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 14: Supporting Our Legacy (Windows 7)</h3>
<div>
<ul>
	<li>NONE</li>
</ul>
&nbsp;

</div>
<h3>Chapter 15: Troubleshooting MDT 2012 Update 1</h3>
<div>
<ul>
	<li>The log files are on the client by default, and in different locations depending on when the deployment fails. Also, depending on what phase the task sequence is in, the log files can be in multiple locations, so make sure you read the latest one.</li>
	<li>You can enable server-side logging by adding the SLShare and/or SLShareDynamicLogging properties to the rules (CustomSettings.ini).</li>
	<li>SLShare=\MDT01Logs$</li>
	<li>SLShareDynamicLogging=\MDT01DynLogs$</li>
	<li>The SLShare property configures the task sequence to copy the log files to a folder on the server if a setup fails, or at the end of a successful setup.</li>
	<li>When you have DHCP and PXE servers on routed networks, make sure to use IP Helpers rather than setting the same DHCP scope options. Although the DHCP scope option may work, depending on your network environment, IP Helpers have proven to be more reliable.</li>
</ul>
&nbsp;

</div>
<h3>Appendix A: Using the Hydration Kit to Build the PoC Environment</h3>
<div>
<ul>
	<li>You can use a separate Windows Server 2012 virtual machine, with Routing and Remote Access enabled, as a gateway.  For more details on using a virtual router, see this article: <a href="http://tinyurl.com/usingvirtualrouter.">http://tinyurl.com/usingvirtualrouter.</a></li>
	<li>The SQL Server 2012 Express setup does install Report Viewer 2012, but WSUS, even in Windows Server 2012, still requires Report Viewer 2008.</li>
</ul>
—————————————————————

Don’t forget to check out the following:

<span id="control_gen_2" class="commentary"><strong>CANITPro:</strong> Did you know there is a site dedicated to Canadian IT professionals? You can win a 3D movie prize package by upgrading your IT skills with Microsoft. Check out CANITPRO At The Movies, either in English: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600830" target="_blank">CANITPro At The Movies</a></span><span id="control_gen_3" class="commentary"> or French: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600850" target="_blank">CANITPro At The Movies</a></span>

<strong>Azure:</strong> Sign up for a FREE trial and get $200 to spend on <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597585" target="_blank">Microsoft Azure</a> cloud computing services. Full access, no strings.

<span id="control_gen_5" class="commentary"><strong>MSDN:</strong> Ever wanted to work with the latest Microsoft technologies, without having to spend thousands of dollars? Now you can, with the <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597617" target="_blank">MSDN subscription</a>. </span>

</div>
</div>
