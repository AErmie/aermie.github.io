---
layout: page
title: Book Review: Microsoft System Center Software Update Management Field Experience
date: 2015-05-07 20:09
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2015/05/Software-Update-Management-Field-Experience-Cover.jpg"><img class="alignleft size-full wp-image-9861" src="/wp-content/uploads/2015/05/Software-Update-Management-Field-Experience-Cover.jpg" alt="Software Update Management Field Experience Cover" width="201" height="244" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2015/03/03/free-ebook-microsoft-system-center-software-update-management-field-experience.aspx" target="_blank">Microsoft System Center Software Update Management Field Experience</a> eBook.

I found the entire book very helpful.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 01: Understanding software update architecture: server side</h2>
<ul>
	<li>When you do routine maintenance, such as removing expired software updates or moving updates between software update groups, the compliance status of the software update group changes to Unknown.</li>
	<li>Configuration Manager integrates some functionalities of WSUS, such as update catalog download and distribution capabilities, but it uses its own functionality to deploy and install the updates</li>
	<li>When thinking about capacity and planning for a software update point, it is important to note that when you implement this role on a system that co-exists with another Configuration Manager site system, it is possible to support up to 25,000 clients, but if you are installing software updates on a server with no other Configuration Manager site system role, it is possible to support up to 100,000 clients. In addition, there is a practical limit of 1,000 update objects per deployment package when you are working with manual software update deployments and when you are using automated deployment rules (ADR)</li>
	<li>You cannot install more than one software update point on a Configuration Manager secondary site.</li>
	<li>The software update point failover process is not as robust as the NLB for load balancing. When installed for the first time, assuming that your environment has the Software Updates feature enabled from the Configuration Manager client settings, a client randomly selects an available software update point, with which it will maintain affinity until it is no longer able to communicate with that software update point. A combination of four failed retries at 30-minute intervals and non-retry error codes is what determines that the client is no longer able to communicate with the software update point and causes the switch to another software update point.</li>
	<li>A software update point is optional on a secondary site. When a software update point is installed on a secondary site, the WSUS database is configured as a replica instead of as an autonomous WSUS instance, which is how the WSUS database is configured when installing the software update point on a primary site or central administration site.</li>
	<li>Internet-based software update points are not supported on Configuration Manager secondary sites.</li>
	<li>This method allows you to synchronize the expired, superseded, and declined updates with the Microsoft Update Catalog, which doesn’t happen when you use the manually initiated synchronization method</li>
	<li>It is also known as the delta synchronization because it synchronizes only the updates that have been changed since the last synchronization</li>
	<li>You can manipulate either a full or a delta synchronization in Configuration Manager by creating an empty flag file inside the .\inboxes\wsyncmgr.box, located in the Configuration Manager installation path. For a full synchronization, you need to name the flag file FULL.SYN. To trigger a delta synchronization, you need to name the flag file SELF.SYN. You can review the whole synchronization process by viewing the WSYNCMGR.log</li>
	<li>It is not recommended that you manipulate the synchronization every time you need to synchronize your updates catalog, but it is definitely a useful option when troubleshooting the software updates synchronization process.</li>
	<li>The deployment package is like a bucket and contains the binary files that you need to distribute to a distribution point to make them available for the Configuration Manager clients</li>
</ul>
<h2>Chapter 02: Understanding software update architecture: client side</h2>
<ul>
	<li>Troubleshooting technique frequently used by Microsoft Support is to ask the customer to stop the WUA service and rename or delete the Software Distribution folder. When the WUA service is restarted, the Software Distribution folder is re-created, and the client scanning begins again. This approach provides a fresh start with a new Windows Update data store if the Datastore.edb file is corrupted.</li>
	<li>Consider having BITS throttling settings in place when there are network constraints, such as slow network connections between the Configuration Manager clients and the Configuration Manager software update servers.</li>
	<li>If you have configured the software update deadline for 02:00 P.M. in your time zone and the Disable Deadline Randomization option is enabled, the software update deployment may begin anytime between 01:00 P.M. and 06:00 P.M. This is because a 4-hour installation randomization is applied to the deadline. This randomization prevents all software update clients from starting update installations at the same time.</li>
	<li>The Disable Deadline Randomization option is disabled by default in Configuration Manager 2012 R2, but you should enable it for virtual environments, especially VDI environments.</li>
	<li>When troubleshooting software updates from the client side, it’s often necessary to cross-reference between WMI and the Configuration Manager client logs. You can use UpdatesDeployment.log to do this since all of the software update deployments and update unique IDs are exposed in this log</li>
	<li>By default, the Configuration Manager 2012 R2 client stores deployed packages in the %WinDir%\ccmcache folder, and the default disk space for this folder is 5 gigabytes (GB). Do not encrypt this folder because Configuration Manager cannot upload content to an encrypted folder</li>
	<li>The content remains in the cache for at least 24 hours. After that time, it can be overwritten by new content if more disk space is necessary. If the Configuration Manager administrator configures a package to persist content in the client cache, the client will not automatically delete or overwrite the package in the cache. In this case, it is necessary to increase the cache size or choose the delete option from the Control Panel applet of the client to delete the content from the cache.</li>
</ul>
<h2>Chapter 03: Managing software updates</h2>
<ul>
	<li>Software update groups function as containers to which software updates can be added and organized either by product or by timeline</li>
	<li>The Windows client can assess the applicable Windows updates, so there is no mandatory requirement to separate the software updates by products</li>
	<li>A staged rollout approach provides the best solution to identify problems with software update deployments before they are deployed to the production environment.</li>
	<li>On the Deployment Settings page, make sure that Required is selected to create a mandatory software update deployment. After the deployment is created, this option cannot be changed from Required to Available.</li>
	<li>Although an expired update cannot be deployed, a superseded update can still be installed until it expires.</li>
	<li>Updates that have been expired and aren’t part of an active deployment are deleted seven days after they expire. Configuration Manager 2012 R2 cleans up the source folders automatically.</li>
	<li>A script to clean up the source folders for versions earlier than Configuration Manager 2012 R2 can be found at <a href="http://blogs.technet.com/b/configmgrteam/archive/2012/04/12/software-update-content-cleanup-in-system-center-2012-configuration-manager.aspx" target="_blank">http://blogs.technet.com/b/configmgrteam/archive/2012/04/12/software-update-content-cleanup-in-system-center-2012-configuration-manager.aspx</a>.</li>
	<li>The first step in the process for managing content related to expired updates is getting expired updates out of any deployed update groups. Configuration Manager will never delete any expired update associated with an active deployment.</li>
	<li>It is a good idea to keep maintenance windows for software updates separate from maintenance windows used for other purposes so that administrators have more control over when software updates deploy and they will not conflict during other deployments.</li>
</ul>
<h2>Chapter 04: Monitoring software updates</h2>
<ul>
	<li>Required This means the software update is applicable but is not yet installed. Alternatively, it may mean that the software update was installed but the state message has not yet been uploaded to the site server.</li>
	<li>Not required status is calculated as part of the compliant systems.</li>
	<li>Client Activity displays active and inactive systems and computers with no Configuration Manager client installed.</li>
	<li>Client Check displays clients that passed or failed the evaluation check</li>
	<li>This evaluation check is based on the following client evaluation rules, which run as part of the task scheduler every day at midnight by default. If any of the checks fail, then Client Evaluation (CCMEval.exe) automatically tries to remediate and fix the issue.
<ul>
	<li>Verify/remediate WMI service startup and status</li>
	<li>WMI repository read/write test</li>
	<li>Verify/remediate client WMI provider</li>
	<li>WMI repository integrity test</li>
	<li>WMI event sink test</li>
	<li>Microsoft policy platform WMI integrity test</li>
	<li>Verify/remediate BITS startup type</li>
	<li>Verify/remediate client prerequisites</li>
	<li>Verify/remediate client installation</li>
	<li>Verify/remediate SMS agent host service startup and status</li>
	<li>Verify/remediate Microsoft Policy Platform service startup and status</li>
	<li>Verify/remediate antimalware service startup and status</li>
	<li>Verify/remediate Windows Update service startup type</li>
	<li>Verify/remediate Configuration Manager Remote Control service startup and status</li>
	<li>Verify/remediate Configuration Manager Proxy service startup and status</li>
	<li>Verify/remediate SQL CE database is healthy</li>
</ul>
</li>
	<li>The software update summarization task updates the status of software updates in the console for all clients in the Configuration Manager hierarchy. The summarizer does not provide real-time information in the console because it runs every hour by default</li>
	<li>You can monitor software update status summarization in Statesys.log on the primary site server</li>
	<li>The Configuration Manager 2012 R2 toolkit can be used to monitor software updates and other deployments. You can download the toolkit, including the Deployment Monitoring Tool, from <a href="http://www.microsoft.com/en-us/download/details.aspx?id=36213" target="_blank">http://www.microsoft.com/en-us/download/details.aspx?id=36213</a>. This toolkit can be installed on any system running Windows 7 or higher. The Deployment Monitoring Tool is a client side tool that allows an administrator to monitor all deployments on a specific system.</li>
	<li>Determine whether it is a server or client side issue, review the client logs located in the CCM\Logs folder, such as WUAHandler.log, ScanAgent.log, UpdateDeployment.log, or WindowsUpdate.log.</li>
	<li>The Error Lookup tool in CMTrace converts the error code into a meaningful name</li>
	<li>There is a total of 469 built-in reports in the Configuration Manager console. Of these, 30 built-in reports are just for software updates</li>
	<li>You can also review the Scan 1 – Last Scan States By Collection report located under the Software Update – D scan node to determine how many clients are running into a software update scan issue</li>
	<li>Another useful report for tracking software update deployment is Management 3 – Updates In A Deployment. This report asks for the deployment name and returns all of the updates that are part of the deployment along with the number of updates installed, required, not required, unknown, failed, and pending.</li>
</ul>
<h2>Chapter 05: Software updates automation</h2>
<ul>
	<li>Windows PowerShell is a powerful tool that can and should be utilized for automating additional tasks, such as keeping the Windows Server Update Services (WSUS) database optimized, as well as creating, modifying, deleting, or updating software update groups, deployments, and packages</li>
	<li>In the Create Automatic Deployment Rule Wizard, if an existing software update group is selected, all existing updates that currently exist in the group from the previous execution of each automatic deployment rule are removed prior to adding the newly matched updates.</li>
	<li>You cannot create a software update group manually and then create an automatic deployment rule to add new updates to the manually created group.</li>
	<li>Each time an automatic deployment rule runs, the updates that previously existed in the rule at the time of the previous successful run of the rule are removed so that the deployment will never exceed this supported limit</li>
	<li>The Systems Management Server (SMS) provider’s computer account and the user that is running the wizard to download the software updates must both have Write NTFS permissions on the download location.</li>
	<li>One commonly used best practice is to always add “Superseded = No” to the search criteria to ensure there are no superseded updates included in the deployment.</li>
	<li>Keeping the WSUS database clean of expired metadata and regularly indexed will proactively avoid software update synchronization issues due to a fragmented or bloated database</li>
	<li>It is recommended that you routinely perform WSUS cleanup actions on each software update point in your hierarchy.</li>
	<li>An important procedural item to be aware of in this overall process is that if you have more than one software update point, you should run the cleanup process on the lowest tier servers first, then work your way up the hierarchy</li>
	<li>Selecting only the truly required update classifications and products for your environment is important for keeping the SUSDB database from becoming excessively large.</li>
	<li>If an SUSDB database is hosted on Windows Internal Database, the operating system version affects how the WSUS cleanup maintenance tasks are performed.</li>
	<li>New Windows PowerShell cmdlets were introduced with the updated WSUS version that is included as a role in Windows Server 2012 R2. These new cmdlets enable SUSDB cleanup without the need for extensive custom scripts. Specifically, the Invoke-WsusServerCleanup cmdlet performs all of the WSUS maintenance tasks that historically have been accomplished either manually through the WSUS administrator console or via various community scripts.</li>
	<li>Windows Server versions prior to Windows Server 2012 R2 continue to require these scripts to initiate the WSUS maintenance tasks.</li>
	<li>The Invoke-WsusServerCleanup cmdlet can be used to clean up obsolete computers, obsolete updates, unneeded content files, as well as declining, expired, and superseded updates. If WSUS is installed on an operating system version release earlier than Windows Server 2012 R2, you can use the following Windows PowerShell script to perform the WSUS metadata cleanup tasks:<em>[reflection.assembly]::LoadWithPartialName("Microsoft.UpdateServices.Administration")` | out-null$wsus = [Microsoft.UpdateServices.Administration.AdminProxy]::GetUpdateServer();$cleanupScope = new-object Microsoft.UpdateServices.Administration.CleanupScope;$cleanupScope.DeclineSupersededUpdates = $true$cleanupScope.DeclineExpiredUpdates = $true$cleanupScope.CleanupObsoleteUpdates = $true$cleanupScope.CompressUpdates = $true$cleanupScope.CleanupObsoleteComputers = $true$cleanupScope.CleanupUnneededContentFiles = $true$cleanupManager = $wsus.GetCleanupManager();$cleanupManager.PerformCleanup($cleanupScope);</em></li>
	<li>A sample script that can be used to re-index the database on any version of WSUS is available at <a href="https://gallery.technet.microsoft.com/scriptcenter/6f8cde49-5c52-4abd-9820-f1d270ddea61" target="_blank">https://gallery.technet.microsoft.com/scriptcenter/6f8cde49-5c52-4abd-9820-f1d270ddea61</a>.</li>
	<li>One popular tool for browsing and viewing WMI namespaces, classes, instances, and properties is WMI Explorer, which can be downloaded from CodePlex at http://wmie.codeplex.com.</li>
	<li>Client Center for Configuration Manager, downloadable from <a href="http://sccmclictr.codeplex.com" target="_blank">http://sccmclictr.codeplex.com</a>. This tool is also helpful for learning the various Windows PowerShell classes, namespaces, and commands to access client side software updates information, since it displays the Windows PowerShell commands being run against the client for each action, including various software update actions.</li>
	<li>A variety of blogs offer software update automation scripts and information:</li>
	<li>Steve Rachui’s blog <a href="http://blogs.msdn.com/b/steverac/archive/2014/06/12/automating-software-updates.aspx" target="_blank">http://blogs.msdn.com/b/steverac/archive/2014/06/12/automating-software-updates.aspx</a></li>
	<li>Jason Githens’s blog <a href="http://technet.microsoft.com/en-us/video/automating-deployments-of-software-updates.aspx" target="_blank">http://technet.microsoft.com/en-us/video/automating-deployments-of-software-updates.aspx</a></li>
	<li>Deepak Singh Dhami’s blog <a href="http://www.dexterposh.com/2014/06/powershell-sccm-2012-automate-patching.html" target="_blank">http://www.dexterposh.com/2014/06/powershell-sccm-2012-automate-patching.html</a></li>
	<li>David O’Brien’s blog <a href="http://www.david-obrien.net/" target="_blank">http://www.david-obrien.net/</a></li>
	<li>In addition, see the following documentation on MSDN:
<a href="http://msdn.microsoft.com/en-us/library/hh949569.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/hh949569.aspx</a>
<a href="http://msdn.microsoft.com/en-us/library/jj217901.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/jj217901.aspx</a></li>
</ul>
—————————————————————

Don’t forget to check out the following:

<span id="control_gen_2" class="commentary"><strong>CANITPro:</strong> Did you know there is a site dedicated to Canadian IT professionals? You can win a 3D movie prize package by upgrading your IT skills with Microsoft. Check out CANITPRO At The Movies, either in English: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600830" target="_blank">CANITPro At The Movies</a></span><span id="control_gen_3" class="commentary"> or French: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600850" target="_blank">CANITPro At The Movies</a></span>

<strong>Azure:</strong> Sign up for a FREE trial and get $200 to spend on <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597585" target="_blank">Microsoft Azure</a> cloud computing services. Full access, no strings.

<span id="control_gen_5" class="commentary"><strong>MSDN:</strong> Ever wanted to work with the latest Microsoft technologies, without having to spend thousands of dollars? Now you can, with the <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597617" target="_blank">MSDN subscription</a>. </span>
