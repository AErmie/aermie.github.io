---
layout: page
title: Book Review: Microsoft System Center - Operations Manager Field Experience
date: 2015-06-22 15:09
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2015/06/Operations-Manager-Field-Experience.png"><img class="alignleft wp-image-13573 size-medium" src="/wp-content/uploads/2015/06/Operations-Manager-Field-Experience-247x300.png" alt="Operations Manager Field Experience" width="247" height="300" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2015/04/21/free-ebook-microsoft-system-center-operations-manager-field-experience.aspx" target="_blank">Microsoft System Center Operations Manager Field Experience</a> eBook.

The chapter(s) that I found most helpful were basically all of them! The entire book is filled with very useful points, tips, and insights.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: The Role of Operations Manager</h3>
<div>
<ul>
	<li>By default, every installation of Operations Manager is not registered; it’s installed as an evaluation version. This is true even if you installed it from volume licensing media. To register your installed environment, you can use the Windows PowerShell cmdlet Set-SCOMLicense</li>
	<li>Since Operations Manager was designed with built-in high availability when you have two management servers, having two or more management servers is recommended. That way, if one goes down, failover is possible. To determine which management server is down and which is still up and running, the server running the Operational Database serves as a watcher node, similar to a witness in a failover cluster, and has a majority in deciding which one is the functional management server.</li>
	<li>If the primary management server for the agent goes down, the agent tries to connect to one of the management servers defined as a failover. You can define a failover management server through the console by using AD integration or by using the Set-SCOMParentManagementServer cmdlet with the –FailoverServer parameter.</li>
	<li>Azure Operational Insights provides you with the combined knowledge of the Microsoft Support Engineers, who are responsible for adding rules to the product. These rules work like an additional management pack that is managed centrally by Microsoft</li>
	<li>By default, on Windows Server 2008 R2 and higher, power management is set to Balanced. In some cases, you may experience degraded overall performance on a Windows Server machine when running with the default power plan. This is most noticeable on the SQL server running the Operational Database, where the Balanced power setting results in slow console performance since most of the background actions in the console are SQL query-based. The issue may occur irrespective of platform and may be exhibited in both physical and virtual environments</li>
	<li>Another power management setting to consider is described in the Knowledge Base article “Degraded overall performance on Windows Server 2008 R2” at <a href="http://support.microsoft.com/kb/2207548" target="_blank">http://support.microsoft.com/kb/2207548</a>. Note that even though this article describes the problem in the context of Windows Server 2008 R2, the strategies described are also valid for later versions of Windows Server</li>
	<li>You can find some important information about the power management setting on a network adapter at <a href="http://support.microsoft.com/kb/2740020" target="_blank">http://support.microsoft.com/kb/2740020</a>. As stated in the Knowledge Base article, you might want to disable the Allow The Computer To Turn Off This Device To Save Power network adapter power management setting on servers</li>
	<li>The D drive on an Azure IaaS VM is a temporary disk, using local storage from the actual hardware that is hosting your VM. This means that everything on this drive will be lost in the case of a reboot, so don’t use it to store anything that you want to keep.</li>
	<li>Find more information about SQL Server at <a href="http://blogs.technet.com/b/dataplatforminsider/archive/2014/09/25/using-ssds-in-azure-vms-to-store-sql-server-tempdb-and-buffer-pool-extensions.aspx" target="_blank">http://blogs.technet.com/b/dataplatforminsider/archive/2014/09/25/using-ssds-in-azure-vms-to-store-sql-server-tempdb-and-buffer-pool-extensions.aspx</a></li>
	<li>The general information found in this blog post also applies to SQL Server: <a href="http://blogs.msdn.com/b/mast/archive/2014/10/14/configuring-azure-virtual-machines-for-optimal-storage-performance.aspx" target="_blank">http://blogs.msdn.com/b/mast/archive/2014/10/14/configuring-azure-virtual-machines-for-optimal-storage-performance.aspx</a>.</li>
	<li>To test the speed of your disk subsystem, use the SQLIO Disk Subsystem Benchmark Tool from Microsoft, available at <a href="http://www.microsoft.com/en-us/download/details.aspx?id=2016" target="_blank">http://www.microsoft.com/en-us/download/details.aspx?id=2016</a>3.</li>
	<li>Putting a Gateway server in a remote subnet to compress the outgoing data is no longer recommended. The agent itself does an equally good job of compressing the data in Operations Manager 2012 R2. However, the other reasons for installing a Gateway server in a remote subnet are still valid, for instance to reduce the administrative overhead and to minimize the number of certificates that are needed. More information can be found at <a href="http://technet.microsoft.com/en-us/library/hh212823.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh212823.aspx</a>.</li>
	<li>When you install Operations Manager on machines running antivirus software, you should configure the antivirus software so that the following directories are excluded:
<ul>
	<li>The Health Service State folder on every management server and every agent</li>
	<li>The data and log file directories where your databases are located</li>
	<li>Excluding the actual binary files, such as MonitoringHost.exe, is not recommended.</li>
</ul>
</li>
	<li>A detailed overview of antivirus exclusions for Operations Manager can be found at <a href="http://support.microsoft.com/kb/975931" target="_blank">http://support.microsoft.com/kb/975931</a>.</li>
	<li>The best way to configure SQL Server in your Operations Manager environment is to keep it simple. The default settings for Operations Manager should be left alone unless you have very specific reasons to change them</li>
	<li>Neither auto grow nor auto shrink are recommended for the Operational Database because it needs 50 percent of free space at all times to perform maintenance and indexing tasks. If the database doesn’t have enough free space, the scheduled maintenance tasks might fail. Operations Manager will alert you when there is less than 40 percent of free space.</li>
	<li>The SQL Server edition you are using also has an important role when you are considering auto grow. SQL Server Standard edition can cause the database tables to lock out when auto grow is configured. However, this does not occur with SQL Server Enterprise edition. This applies to both the Operational Database and the Data Warehouse Database.</li>
	<li>Auto grow is supported (though not recommended), when enabled as an insurance policy against the database’s file filling up. When using auto grow on the databases, it is better to set it to increase by a fixed amount rather than a percentage. The fixed increase amount should be no more than 500 MB or 1 GB in growth to limit the blocking that might occur during the expansion process. It is also useful to configure a maximum possible size to prevent the databases from filling up the disk they reside on.</li>
	<li>More information about auto grow and auto shrink can be found in the article at <a href="http://support.microsoft.com/kb/315512/" target="_blank">http://support.microsoft.com/kb/315512/</a>.</li>
	<li>Find more information about instant file initialization at <a href="http://blogs.msdn.com/b/sql_pfe_blog/archive/2009/12/23/how-and-why-to-enable-instant-file-initialization.aspx" target="_blank">http://blogs.msdn.com/b/sql_pfe_blog/archive/2009/12/23/how-and-why-to-enable-instant-file-initialization.aspx</a> and <a href="http://sqlblog.com/blogs/tibor_karaszi/archive/2009/03/09/do-you-have-instant-file-initialization.aspx" target="_blank">http://sqlblog.com/blogs/tibor_karaszi/archive/2009/03/09/do-you-have-instant-file-initialization.aspx</a></li>
	<li>In SQL Server, data files can be initialized instantaneously. This allows for fast running of file operations. Instant file initialization reclaims used disk space without filling that space with zeros. Instead, disk content is overwritten as new data is written to the files. Log files cannot be initialized instantaneously. Instant file initialization is available only if the SQL Server (MSSQLSERVER) service account has been granted the right to perform volume maintenance tasks (SE_MANAGE_VOLUME_NAME). Members of the Windows Administrator group have this right and can grant it to other users by adding them to the Perform Volume Maintenance Tasks security policy.</li>
	<li>As a general rule, set the combined value over all the instances to about 2 GB less than the actual memory available on the host. This will secure enough available memory for the operating system to function optimally.</li>
	<li>Another low-effort, high-reward action is splitting up the files that comprise the TempDB. There’s only one TempDB per SQL Server instance, so it’s often a performance bottleneck. Make sure that the disk subsystem that holds the TempDB files is up to the task. Increase the number of data files that make up your TempDB to maximize disk bandwidth and to reduce contention in allocation structures</li>
	<li>Generally, if the number of logical processors is less than or equal to eight, use the same number of data files as logical processors. If the number of logical processors is greater than eight, use eight data files; if contention continues, increase the number of data files by multiples of four (up to the number of logical processors) until the contention is reduced to acceptable levels or make changes to the workload/code. It is also best to spread these different files over multiple disk systems and to keep all files the same size.</li>
	<li>The log file for TempDB should remain a single file at all times.</li>
	<li>It is also recommended that you size the TempDB according to the Operations Manager environment. The default size for TempDB is 8 MB with a 1-MB log file. Every time you restart SQL, it will re-create this 8-MB file from the model database</li>
	<li>TempDB optimization is explained in detail at <a href="http://technet.microsoft.com/en-us/library/ms175527(v=sql.105).aspx" target="_blank">http://technet.microsoft.com/en-us/library/ms175527(v=sql.105).aspx</a>.</li>
	<li>For SQL servers running in Azure IaaS, please refer to <a href="http://msdn.microsoft.com/library/azure/dn248436.aspx" target="_blank">http://msdn.microsoft.com/library/azure/dn248436.aspx</a> and <a href="http://msdn.microsoft.com/en-us/library/azure/dn133149.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn133149.aspx</a>.</li>
	<li>Some SQL teams automatically assume that all databases should be set to Full recovery model. This requires backing up the transaction logs on a regular basis, but gives the added advantage of restoring up to the time of the last transaction log backup. This approach does not make as much sense for Operations Manager</li>
	<li>The default and recommended settings for SQL Server in an Operations Manager environment are Windows authentication, SQL Server uses Windows logins</li>
	<li>It is best practice to use a domain account to run your SQL Server service (MSSQLSvc). The problem with this is that if your SQL Server service is not running as either the server’s system account or a domain administrator, SQL Server cannot register its Service SPN when the service is started. If the SQL Server service does not have sufficient rights, you can use the SETSPN tool manually as a domain administrator to register the necessary SPNs.</li>
	<li>More information about SPNs in Operations Manager can be found at <a href="http://blogs.technet.com/b/kevinholman/archive/2011/08/08/opsmgr-2012-what-should-the-spn-s-look-like.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2011/08/08/opsmgr-2012-what-should-the-spn-s-look-like.aspx</a>.</li>
	<li>By default, Operations Manager does self-maintenance. Since most Operations Manager administrators are not SQL Database Administrators (DBAs), Microsoft implemented several rules in Operations Manager to automatically keep the databases optimized. These maintenance tasks are defined as system rules in the Operations Manager management pack, one of the management packs installed by default when you install Operations Manager. Since these maintenance tasks run automatically, be careful that your own maintenance tasks do not conflict with the built-in system rules (if you or the DBA decide to implement additional maintenance).</li>
	<li>For the Operations Manager Data Warehouse, an automatic maintenance job runs every 60 seconds. This job, coming from the Standard Data Warehouse Data Set maintenance rule, does many things, of which re-indexing is only one. All the necessary tables are updated and re-indexed as needed. When a table is 10 percent fragmented, the job re-organizes it. When the table is 30 percent or more fragmented, the index is re-built. Therefore, especially since the built-in maintenance runs every 60 seconds, there is no need for a DBA to run any UPDATE STATISTICS or DBCC DBREINDEX maintenance commands against this database.</li>
	<li>By default, the block size of any disk less than 16 TB is 4 K. Since SQL Server reads in 64-K increments, it is best practice to format the disk containing the SQL data and log files with 64-K block size. You can only set this allocation unit size when you format the disk.</li>
	<li>If you use the wrong collation, searches may be less effective or not work at all, sorting might produce unexpected results, and other problems can happen when inserting or retrieving data.</li>
	<li>If a SQL Server collation other than SQL_Latin1_General_CP1_CI_AS is specified when you create the database, you will have to reinstall Operations Manager and create another database to fix this problem because you cannot change the collation after installing Operations Manager.</li>
	<li>The registry key path where settings for the Data Access Layer are included is:
<ul>
	<li>HKLM\SOFTWARE\Microsoft\System Center\2010\Common\DAL</li>
	<li>The DWORD setting, called DALInitiateClearPool, is used by the Data Access Service to control whether to reconnect to the database after a period of unavailability. The default value is 0 (disabled). The recommendation is to enable this feature by setting the value to 1 (decimal).</li>
</ul>
</li>
	<li>The Persistence Manager feature is used by the Health Service to read and write data to the local database. The local or cache database is called HealthServiceStore.edb, and it is a Microsoft Jet Database Engine database. The registry key path for settings belonging to this feature is:
<ul>
	<li>HKLM\SYSTEM\CurrentControlSet\Services\HealthService\Parameters</li>
	<li>The setting responsible for how often Persistence Manager writes data from memory to the disk is called Persistence Checkpoint Depth Maximum of type DWORD and is measured in bytes. The default value for this setting is 20971520 (decimal) bytes. On management servers that handle a large number of objects not managed directly by agents, such as SNMP Devices, Groups, URL Monitors, Cross-Platform Agents, and so on, you may need to increase this value to relieve disk pressure. The recommended value is 104857600 (decimal).</li>
</ul>
</li>
	<li>Health Manager is used by the Health Service to calculate and track the health state of each monitor of each object it monitors. The registry path for settings belonging to this feature is:
<ul>
	<li>HKLM\SYSTEM\CurrentControlSet\Services\HealthService\Parameters</li>
	<li>The important setting for the Health Manager is State Queue Items of type DWORD. This sets the maximum size (in bytes) of the state data queue. If the value is too small or if there are too many workflows running (based on the number of objects being managed), there could be possible state change data loss. The default value for this setting is calculated by the Health Service on startup based on how many objects it needs to manage. For agents in a small environment, this value is set to 1024 (decimal). The value is set to 10240 (decimal) on management servers in a mid-size environment. For large environments, on management servers that manage many objects, the default is 25600 (decimal). The recommendation is to double these default values, depending on where it is needed—for an agent that manages a lot of objects or a management server.</li>
</ul>
</li>
	<li>Do not change the settings for Pool Manager unless advised by Microsoft Support after a proper analysis of the environment, behavior of the resource pools, and load on the management servers. If these settings are changed, it is important to make sure that they are changed to the same value on all management servers in the environment.</li>
	<li>To remove a server from the resource pools with automatic membership, first set the group membership to manual (automatic is the default). This can be done only from within Windows PowerShell as follows:
<ul>
	<li>Get-ScomResourcePool –DisplayName "&lt;Resource Pool Name&gt;" | Set-SCOMResourcePool–EnableAutomaticMembership 0</li>
	<li>After you run this command, you can then use either Windows PowerShell or the console to remove the management server.</li>
</ul>
</li>
	<li>Daily tasks
<ul>
	<li>Use the imported management packs (general views, Management Group Health dashboard view and reports) to verify that the Operations Manager features are healthy.</li>
	<li>Check that alerts from the previous day are not still in state of New. Check the repeat counts and date created for your alerts.</li>
	<li>Check for any unusual alert or event noise; investigate further if required (for example, failing scripts, WMI issues, grey agents, and so on).</li>
	<li>Check the status of all agents for any state other than green. Verify that all managed computers are communicating.</li>
	<li>Review nightly backup jobs and database space allocation.</li>
	<li>Verify that predefined maintenance tasks scheduled to run daily are running successfully.</li>
	<li>Check the Operations Manager event logs on each management server for unusual behavior and error events.</li>
</ul>
</li>
	<li>Weekly tasks
<ul>
	<li>Schedule weekly meetings with operational application owners to review previous most common alerts and events.</li>
	<li>Use the top-down approach to running the Most Common Alerts and Most Common Events reports. Investigate further where necessary.</li>
	<li>Run the Data Volume by Management pack and Data Volume by Workflow and Instance reports.</li>
	<li>Check available disk space on all Operations Manager database systems (data and log files).</li>
</ul>
</li>
	<li>Monthly tasks
<ul>
	<li>Check for new management pack versions of any installed management packs. Also check the management pack guides of newly released management packs to determine whether they meet the requirements of your organization and are suitable for your environment.</li>
	<li>Review the baselines (performance counters) to assess the ongoing performance of the Operations Manager environment as new agents and management packs are added.</li>
	<li>Review the disaster recovery plan for any needed changes.</li>
</ul>
</li>
	<li>Microsoft’s Brian Wren has put together a very extensive authoring guide, which can be accessed at <a href="http://social.technet.microsoft.com/wiki/contents/articles/15251.system-center-management-pack-authoring-guide.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/15251.system-center-management-pack-authoring-guide.aspx</a>.</li>
</ul>
&nbsp;

</div>
<h3>Chapter 02: Best Practices for Working with Management Packs</h3>
<div>
<ul>
	<li>The product group that creates the product also makes the management packs, so you will have the combined knowledge of the people who created the product to assist you with monitoring your applications in the most recommended way</li>
	<li>Brian Wren has done an outstanding job writing the System Center Management Pack Authoring Guide, which you can find at <a href="http://social.technet.microsoft.com/wiki/contents/articles/15251.system-center-management-pack-authoring-guide.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/15251.system-center-management-pack-authoring-guide.aspx</a></li>
	<li>There is also an MSDN Channel9 series about management packs available at <a href="http://channel9.msdn.com/Series/System-Center-2012-R2-Operations-Manager-Management-Packs" target="_blank">http://channel9.msdn.com/Series/System-Center-2012-R2-Operations-Manager-Management-Packs</a> and a Microsoft Virtual Academy series available at <a href="http://www.microsoftvirtualacademy.com/training-courses/system-center-2012-r2-operations-manager-management-pack" target="_blank">http://www.microsoftvirtualacademy.com/training-courses/system-center-2012-r2-operations-manager-management-pack</a>.</li>
	<li>For more information, see the article “MP Best Practice: Using the Seed Pattern for Easy Discovery” on the TechNet Wiki at <a href="http://social.technet.microsoft.com/wiki/contents/articles/1208.mp-best-practice-using-the-seed-pattern-for-easy-discovery.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/1208.mp-best-practice-using-the-seed-pattern-for-easy-discovery.aspx</a>.</li>
	<li>For more information, see the article “How to detect and troubleshoot frequent configuration changes in Operations Manager” on Microsoft Support at <a href="http://support.microsoft.com/kb/2603913" target="_blank">http://support.microsoft.com/kb/2603913</a>. See also Kevin Holman’s article “What is config churn?” on his blog at <a href="http://blogs.technet.com/b/kevinholman/archive/2009/10/05/what-is-config-churn.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2009/10/05/what-is-config-churn.aspx</a>.</li>
	<li>For more information, see Kevin Holman’s article “Tuning tip: Do you have monitors constantly flip flopping?” on his blog at <a href="http://blogs.technet.com/b/kevinholman/archive/2009/12/21/tuning-tip-do-you-have-monitors-constantly-flip-flopping.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2009/12/21/tuning-tip-do-you-have-monitors-constantly-flip-flopping.aspx</a>.</li>
	<li>When you seal a management pack, the file is digitally signed by the provider and the user knows that it hasn’t been modified since then.
To upgrade a sealed management pack, the same key must be used or the upgrade will fail</li>
	<li>Summary of best practices
<ul>
	<li>In summary, here is a list of the most important things to consider when working with management packs:</li>
	<li>Class properties you choose should change values as seldom as possible, close to never.</li>
	<li>Don’t use Operations Manager for software inventory (System Center Configuration Manager is built to do that), and don’t collect too many properties.</li>
	<li>Monitors should change their state as seldom as possible. They should not be too sensitive, and the related issue that is described in the alert should be resolved in a more permanent manner.</li>
	<li>The type space should be kept as small as possible. Import or create only what you need and delete what you do not use.</li>
	<li>Windows PowerShell scripts that connect to the Data Access Service should be kept to a minimum. At least try to develop them in a way that loads as few objects as possible by using selection criteria for the Operations Manager cmdlets.</li>
	<li>Don’t over-use maintenance mode. If there is no way around it, reduce database grooming settings for state change events data.</li>
	<li>Targets for workflows should be as specific as possible. Use seed classes with lightweight discovery rules for custom application monitoring.</li>
	<li>Tune existing workflows using overrides. Disable unneeded workflows, adjust thresholds, set higher run intervals, and so on.</li>
	<li>Prefer static groups instead of dynamic groups, or at least try to use lightweight criteria for your dynamic groups.</li>
	<li>Change the group calculation interval when there are many groups in the Operations Manager environment.</li>
	<li>Configure before you customize. Determine if you can use an existing workflow for what you need instead of creating a new one.</li>
	<li>Classes, groups, modules, and so on should be in a sealed management pack so that they are not unexpectedly modified and so that they can be referenced by content in other management packs.</li>
</ul>
</li>
	<li>Management Pack Viewer (MP Viewer) was first developed by Boris Yanushpolsky and later updated for Operations Manager 2012 and management pack bundle (MPB) files by Daniele Muscetta. The download link for this tool is <a href="http://blogs.msdn.com/b/dmuscett/archive/2012/02/19/boris-s-tools-updated.aspx" target="_blank">http://blogs.msdn.com/b/dmuscett/archive/2012/02/19/boris-s-tools-updated.aspx</a>.</li>
	<li>Not all available management packs are divided into Discovery, Monitoring, and Presentation parts. If everything is in one management pack file, the following explanation is still valid. However, since dividing a management pack into these three different parts is best practice for building your own management packs, you should follow the example set by the SQL Server management pack.</li>
	<li>When creating your own management packs, you shouldn’t use a broad class for all of your discoveries because it will negatively impact the performance of Operations Manager. Use a broad class only for the base discovery or the seed discovery.</li>
	<li>For best practices on how to configure overrides, please see the following Microsoft Knowledge Base article: <a href="http://support.microsoft.com/kb/943239" target="_blank">http://support.microsoft.com/kb/943239</a>.</li>
	<li>More information on relationships can be found at <a href="http://social.technet.microsoft.com/wiki/contents/articles/14256.operations-manager-management-pack-authoring-classes-and-relationships.aspx#Relationships" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/14256.operations-manager-management-pack-authoring-classes-and-relationships.aspx#Relationships</a>.</li>
	<li>Thresholds don’t appear in the overview window of MP Viewer or in the Excel or HTML file when you export the management pack. To view them, select a rule or a monitor, and then click the Knowledge, Alert Description, or Raw XML tab (for monitors) or click the Knowledge or Raw XML tab (for rules) in the bottom right pane. When you select Raw XML, you will see the actual XML code that makes up the management pack. In this raw XML code, you can also see the thresholds</li>
	<li>The MP Wiki found at <a href="http://social.technet.microsoft.com/wiki/contents/articles/16174.microsoft-management-packs.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/16174.microsoft-management-packs.aspx</a> contains all the Microsoft-provided management packs and their release dates. Check this page often to determine whether you have the latest version of the management packs installed.</li>
	<li>You cannot change the target for an override using the Operations Manager console. Instead, you must note the changes you make in the specific override, delete it, and then re-create it with the new target</li>
	<li>If groups are created with extended authoring tools (or directly in XML using your preferred XML editor), they can and should be based on Windows Computer objects hosting special applications, for instance, a Windows Computer group that contains only Windows computers based on a discovered custom special application class. For notifications, the corresponding Health Service Watcher objects could be added to the group. This is necessary because you need the Health Service Watcher objects for Operations Manager self-monitoring alerts like Heartbeat Failures or Computer Not Reachable to be included too. Also remember to add cluster objects (if you need cluster-based alerts), which are not hosted by Windows Computer.</li>
	<li>More information about building and understanding groups is covered in Kevin Holman’s blog at <a href="http://blogs.technet.com/b/kevinholman/archive/2010/07/27/authoring-groups-from-simple-to-complex.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2010/07/27/authoring-groups-from-simple-to-complex.aspx</a>.</li>
</ul>
&nbsp;
<h3>Chapter 03: Getting the Most out of Operations Manager Visualizations</h3>
<div>
<ul>
	<li>The following reports are most useful for tuning:
<ul>
	<li>Alerts</li>
	<li>Event Analysis</li>
	<li>Most Common Alerts and Most Common Events</li>
	<li>Data Volume by Management Pack</li>
	<li>Data Volume by Workflow and Instance</li>
</ul>
</li>
	<li>Some well-known third-party reports that are free to download (although you might need to register first) include the following:
<ul>
	<li>System Center Central’s SCC Health Check reports <a href="http://www.systemcentercentral.com/opsmgr-database-hygiene-scc-health-check-reports-management-pack-by-oskar-landman-pete-zerger/" target="_blank">http://www.systemcentercentral.com/opsmgr-database-hygiene-scc-health-check-reports-management-pack-by-oskar-landman-pete-zerger/</a></li>
	<li>Veeam Report Library for System Center <a href="http://www.veeam.com/report-library-system-center.html" target="_blank">http://www.veeam.com/report-library-system-center.html</a></li>
	<li>The Approved Operations Manager Health Check Dashboard (providing a single page overview of where tuning is needed) <a href="http://www.approvedconsulting.com/downloads" target="_blank">www.approvedconsulting.com/downloads</a></li>
</ul>
</li>
	<li>On Kevin Holman’s blog, you can find a further explanation about state changes and how to clean out old state changes from the Operations Manager Operational database. See <a href="http://blogs.technet.com/b/kevinholman/archive/2009/12/21/tuning-tip-do-you-have-monitors-constantly-flip-flopping.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2009/12/21/tuning-tip-do-you-have-monitors-constantly-flip-flopping.aspx</a>.</li>
	<li>The list of new widgets now available are described at <a href="http://social.technet.microsoft.com/wiki/contents/articles/24133.operations-manager-dashboard-widgets.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/24133.operations-manager-dashboard-widgets.aspx</a> and at <a href="http://blogs.technet.com/b/momteam/archive/2014/04/24/new-widgets-and-dashboard.aspx" target="_blank">http://blogs.technet.com/b/momteam/archive/2014/04/24/new-widgets-and-dashboard.aspx</a>. A video with demos can be found at Channel 9 at <a href="http://channel9.msdn.com/Events/TechEd/NorthAmerica/2014/DCIM-B329" target="_blank">http://channel9.msdn.com/Events/TechEd/NorthAmerica/2014/DCIM-B329</a>.</li>
	<li>Operations Manager includes a SharePoint web part that displays selected dashboards from the web console. The SharePoint farm must be running SharePoint 2013, SharePoint Server 2010 Standard, SharePoint Server 2010 Enterprise, or SharePoint Foundation 2010, and the procedure to configure it is described at <a href="https://technet.microsoft.com/en-us/library/hh212924.aspx" target="_blank">https://technet.microsoft.com/en-us/library/hh212924.aspx</a>.</li>
</ul>
&nbsp;
<h3>Chapter 04: Troubleshooting your Operations Manager Environment</h3>
<div>
<ul>
	<li>The most basic thing to check is that the information event 6022 is being logged periodically, which indicates that the HealthService is running at least some workflows (through MonitoringHost processes) and is not in a hung state or something similar.</li>
	<li>It is more than enough to go through the events from the past 6 to 10 hours because if there is a failure at some point, that failure will repeat itself often.</li>
	<li>Usually, you should first filter the event log just on Error and Warning events (Operations Manager never triggers a Critical level event).</li>
	<li>It is good to go through each Error or Warning event and make an analysis along these lines:
<ul>
	<li>What is the frequency of the event?</li>
	<li>What is the exact event description?</li>
	<li>For events with the same event ID, are these really the exact same event based on a careful comparison of the event description?</li>
	<li>If you see a problem event for some workflow that you know should run every 10 minutes, is the last such event fresh or is it too old, maybe indicating this was a one-time problem?</li>
	<li>Is there one or more events that seem to be spamming the event log? For example, do you see the same event 50 times in 1 second, or something similar?</li>
</ul>
</li>
	<li>There can be two (or more) events that have the same event ID and exact same event description, but with a very specific and important difference: a different error code in the description</li>
	<li>Event Tracing for Windows (ETW) is a tracing technology that Windows uses. ETW tracing is also used in most Microsoft software and in Operations Manager as well. A tutorial about the ETW framework can be found at <a href="https://technet.microsoft.com/en-us/library/jj714799.aspx" target="_blank">https://technet.microsoft.com/en-us/library/jj714799.aspx</a>.
To start the trace with all available providers (trace everything), you can follow the Knowledge Base article at <a href="http://support.microsoft.com/kb/942864" target="_blank">http://support.microsoft.com/kb/942864</a>.</li>
	<li>SQL Server Profiler Tracing is a feature of Microsoft SQL Server that allows you to trace different actions in SQL Server (see <a href="https://msdn.microsoft.com/en-us/library/ms181091(v=sql.110).aspx" target="_blank">https://msdn.microsoft.com/en-us/library/ms181091(v=sql.110).aspx</a>)</li>
	<li>One of the most important aspects of maintaining a healthy and performant Operations Manager environment is management pack tuning. Each time you import a new management pack, you need to monitor the data it collects and how it behaves in the following one to two weeks.</li>
	<li>Another reason for a big StateChangeEvent table is state change events, which are older than the data grooming setting for state changes (default 7 days). This can happen if you manually (or via some automated/scripted method) close alerts without resetting the monitors that raised them. It is against best practice to do this because the grooming stored procedure to clean-up state changes does not also delete state changes that belong to a monitor that is not in the Healthy state. Additionally, a high number of state changes might cause the stored procedure to time out and not be able to delete everything.</li>
	<li>Many different issues on either management servers or agents are caused by known problems with certain versions of the Windows operating system. Because of this, a Knowledge Base article listing recommended Windows operating system (version dependent) hotfixes and update rollups is available at <a href="http://support.microsoft.com/kb/2843219" target="_blank">http://support.microsoft.com/kb/2843219</a>.</li>
	<li>A good Knowledge Base article to help troubleshoot the different scenarios for agents that are displayed as gray is available at http://support.microsoft.com/kb/2288515. One of these scenarios also describes the presence of warning event 2115, which would most likely appear on management servers or gateway servers and may involve performance problems. Another great Knowledge Base article for troubleshooting this issue in detail is available at <a href="http://support.microsoft.com/kb/2681388" target="_blank">http://support.microsoft.com/kb/2681388</a>.</li>
</ul>
&nbsp;
<h3>Chapter 05: Using Operations Manager in Cloud Environments</h3>
<div>
<ul>
	<li>Visual Studio Web Test monitoring is the other option for Global Service Monitor. It gives you the ability to import more extensive Global Service Monitor web tests that have been created using Visual Studio. Using Visual Studio Web Test monitoring, you can record actions to take against your external-facing applications and validate against multiple criteria and multiple websites at the same time. With Visual Studio Web Test monitoring, you can import a web test that was built by a developer using Visual Studio. Transactions are supported, as are authentication actions.</li>
	<li>Global Service Monitor needs a proxy or a server that has ports opened to the Internet. If your proxy server needs authentication, you will need to follow the steps described in the Microsoft Knowledge Base article at <a href="http://support.microsoft.com/kb/2900136/en-us" target="_blank">http://support.microsoft.com/kb/2900136/en-us</a>. From a security perspective, everything that is sent over the Internet is encrypted and is also stored encrypted on the Microsoft Azure watcher nodes that are managed by Microsoft.</li>
	<li>Even in the full subscription, there is a limit of 25 web tests. This can be changed by contacting Microsoft support</li>
	<li>With Azure Operational Insights, you can see where your virtual machine infrastructure needs more resources and where it’s under-utilized. You can also use “what-if” scenarios to enhance your planning options.</li>
	<li>The communication paths that should be opened can be found at <a href="http://blogs.technet.com/b/momteam/archive/2014/05/29/advisor-error-3000-unable-to-register-to-the-advisor-service-amp-onboarding-troubleshooting-steps.aspx" target="_blank">http://blogs.technet.com/b/momteam/archive/2014/05/29/advisor-error-3000-unable-to-register-to-the-advisor-service-amp-onboarding-troubleshooting-steps.aspx</a></li>
	<li>The complete Azure cmdlet reference can be found at <a href="http://msdn.microsoft.com/en-us/library/azure/jj554330.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/jj554330.aspx</a>. Using (Get-module -Name Azure).Version, you can check if you have the latest version installed, since this module gets updated often</li>
	<li>Azure uses DHCP to assign IP addresses to the virtual machines you create. This should not be changed to a fixed address since that will make your virtual machine inaccessible.</li>
	<li>Further explanations about the different types of IP addresses can be found in the blog post at <a href="http://blogs.msdn.com/b/lalitesh_kumar/archive/2014/10/06/static-ip-reserved-ip-and-instance-level-ip-in-azure.aspx" target="_blank">http://blogs.msdn.com/b/lalitesh_kumar/archive/2014/10/06/static-ip-reserved-ip-and-instance-level-ip-in-azure.aspx</a>.</li>
	<li>More information about storage accounts can be found at <a href="http://azure.microsoft.com/en-us/documentation/articles/storage-whatis-account/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/storage-whatis-account/</a> and further storage account performance optimization is discussed at <a href="http://blogs.msdn.com/b/mast/archive/2014/10/14/configuring-azure-virtual-machines-for-optimal-storage-performance.aspx" target="_blank">http://blogs.msdn.com/b/mast/archive/2014/10/14/configuring-azure-virtual-machines-for-optimal-storage-performance.aspx</a> and at <a href="http://azure.microsoft.com/en-us/documentation/articles/storage-performance-checklist/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/storage-performance-checklist/</a>.</li>
	<li>One of the (many) tools for managing your storage account is Azure Storage Explorer, which can be found at CodePlex at <a href="http://azurestorageexplorer.codeplex.com/" target="_blank">http://azurestorageexplorer.codeplex.com/</a></li>
	<li>More information about availability sets can be found at <a href="http://azure.microsoft.com/en-us/documentation/articles/virtual-machines-manage-availability/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/virtual-machines-manage-availability/</a>.</li>
	<li>More information on cloud services can be found at <a href="http://azure.microsoft.com/en-us/documentation/articles/cloud-services-what-is/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/cloud-services-what-is/</a>.</li>
	<li>A quicker way to create the virtual machine with fewer configuration options, similar to the quick create option in the management portal, is to use the New-AzureQuickVM Windows PowerShell cmdlet. In the script center at <a href="http://azure.microsoft.com/en-us/documentation/scripts/" target="_blank">http://azure.microsoft.com/en-us/documentation/scripts/</a>, you can find more scripts that can automatically create virtual machines with multiple data disks.</li>
	<li>A more extensive explanation of how to create and upload Windows Server VHD files to Microsoft Azure is here <a href="http://azure.microsoft.com/en-us/documentation/articles/virtual-machines-create-upload-vhd-windows-server/" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/virtual-machines-create-upload-vhd-windows-server/</a>.</li>
	<li>The operating system disk has read and write caching enabled. This is the best setting for the operating system, but for the Active Directory database (NTDS.DIT) and log files, it is recommended that you attach another disk with only read caching enabled to the virtual machine and put the Active Directory files on that drive.</li>
	<li>Static internal IP addresses are explained at <a href="http://msdn.microsoft.com/en-us/library/azure/dn630228.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn630228.aspx</a>.</li>
	<li>Performance guidance for SQL Server in Azure virtual machines can be found at <a href="http://msdn.microsoft.com/en-us/library/azure/dn248436.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/azure/dn248436.aspx</a>.</li>
	<li>To get the best performance from a storage perspective, add multiple data disks and spread the load over all of them</li>
	<li>More information about PowerShell DSC can be found on Keith Mayer’s blog at <a href="http://blogs.technet.com/b/keithmayer/archive/2014/10/24/end-to-end-iaas-workload-provisioning-in-the-cloud-with-azure-automation-and-powershell-dsc-part-1.aspx" target="_blank">http://blogs.technet.com/b/keithmayer/archive/2014/10/24/end-to-end-iaas-workload-provisioning-in-the-cloud-with-azure-automation-and-powershell-dsc-part-1.aspx</a></li>
	<li>More information about PowerShell DSC can be found on Keith Mayer’s blog at <a href="http://blogs.technet.com/b/keithmayer/archive/2014/10/24/end-to-end-iaas-workload-provisioning-in-the-cloud-with-azure-automation-and-powershell-dsc-part-1.aspx" target="_blank">http://blogs.technet.com/b/keithmayer/archive/2014/10/24/end-to-end-iaas-workload-provisioning-in-the-cloud-with-azure-automation-and-powershell-dsc-part-1.aspx</a></li>
	<li>Using DSC and the SCOM module that is located at <a href="https://gallery.technet.microsoft.com/xSCOM-PowerShell-Desired-052fc73c" target="_blank">https://gallery.technet.microsoft.com/xSCOM-PowerShell-Desired-052fc73c</a></li>
	<li>An extensive explanation of the Azure Monitoring Gateway was written by Cameron Fuller, MVP. This series can be found on his blog at <a href="http://blogs.catapultsystems.com/cfuller/archive/2013/12/04/operations-manager-and-azure-better-together-introducing-the-azure-monitoring-gateway-%5bsysctr-scom-azure%5d.aspx" target="_blank">http://blogs.catapultsystems.com/cfuller/archive/2013/12/04/operations-manager-and-azure-better-together-introducing-the-azure-monitoring-gateway-%5bsysctr-scom-azure%5d.aspx</a>.</li>
</ul>
</div>
</div>
</div>
</div>
