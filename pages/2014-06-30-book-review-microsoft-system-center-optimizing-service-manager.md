---
layout: page
title: Book Review: Microsoft System Center - Optimizing Service Manager
date: 2014-06-30 18:15
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2014/06/Optimizing-Service-Manager-Cover.jpg"><img class="alignleft size-full wp-image-9991" src="/wp-content/uploads/2014/06/Optimizing-Service-Manager-Cover.jpg" alt="Optimizing Service Manager Cover" width="201" height="244" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2013/12/18/free-ebook-microsoft-system-center-optimizing-service-manager.aspx" target="_blank">MSPress Microsoft System Center - Optimizing Service Manager</a> eBook.

The chapter that I found most helpful was Chapter 6 "Optimizing The Service Manager Environment", hence the majority of my highlights are from this chapter.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h3>Chapter 01: Business Reasons To Choose Service Manager</h3>
<ul>
	<li>The integration of Service Manager with the rest of the System Center suite and with Active Directory makes it one of the most mature offerings in the ITSM market.</li>
	<li>The Active Directory connector is a one-way connector between Service Manager and Active Directory Domain Services (AD DS).</li>
	<li>Active Directory groups are leveraged for personalization of the Self-Service Portal, which allows targeted services to specific stakeholders inside and outside of the IT organization.</li>
	<li>Distributed Applications can then be imported automatically into the CMDB as a Business Service, where additional service properties can be managed, including customers, key contacts, and so on.</li>
	<li>Service Manager takes advantage of Microsoft business intelligence solutions incorporated into SQL Server</li>
</ul>
<div>
<h3>Chapter 02: Deployment Costs And Non-IT Usage</h3>
<div>
<ul>
	<li>There are two different types of System Center licenses: a Standard edition and a Datacenter edition.</li>
	<li>System Center 2012 Standard licenses allow customers to manage two OSEs on premises or two OSEs in a public cloud environment</li>
	<li>System Center 2012 Datacenter licenses cover an unlimited number of OSEs for an on-premise environment or eight OSEs in a public cloud environment.</li>
	<li>The System Center license is included in the SQL Server license (Standard Edition), but SQL Server Enterprise is recommended for the data warehouse. Many customers will also need client licenses for several System Center products that also require client integration</li>
	<li>Define a shared vision for the Service Manager project team and the groups that will be using Service Manager.</li>
	<li>An important part of the Vision Scope document is to define the project's scope in such detail that it is not questioned later</li>
	<li>The envisioning workshop should also cover knowledge transfer so that the project team is aware they must actively participate in the deployment</li>
	<li>As far as project scheduling is concerned, it's important to plan for the Service Manager implementation by creating a project plan for the entire project including all milestones and resources needed for deployment.</li>
	<li>The workshops are used to collect information concerning the current state of the people, processes, and technology in the organization.</li>
	<li>TABLE 2-3 List of envisioning workshops</li>
	<li>Once the workshops have been completed, the results should be documented in a Functional Specification document—one or more documents that contain a detailed description of the full solution, including design and configuration of the tool, workflows. and processes</li>
	<li>A series of demos and process-based walkthroughs should take place with the process owners to ensure that Service Manager has been modified as per the process requirements</li>
	<li>Run pilots during the stabilization phase and track results and issues to be addressed prior to production implementation. During this phase, provide training to everyone in the organization including the customers who will be using the portal to log requests and incidents. You should train all of your IT staff to use Service Manager to avoid a flood of complaints when they actually start using it.</li>
	<li>Deploy: During this phase, Service Manager is deployed in production. Make sure there is proper support coverage for the first week; there will be plenty of questions on how to use Service Manager. What it costs to manage Service Manager will vary, but the maintenance of the platform (the technical layer) will require about 4 hours of work per week to maintain, monitor, and apply technical updates to Service Manager.</li>
	<li>Other departments outside of IT may want to use Service Manager to handle these types of requests. To do so, they will need their own views, categories, support groups, and even requests published on the Self-Service Portal</li>
	<li>Implementing non IT usage of Service Manager is not more complicated than implementing it for IT purposes. It's just a matter of working with other departments, outside of IT, to determine the types of requests and services they are offering the business.</li>
</ul>
</div>
</div>
<div>
<h3>Chapter 03: How To Plan For Service Manager</h3>
<div>
<ul>
	<li>The most successful implementations of Service Manager begins with a vision of what the organization wants Service Manager to achieve.</li>
	<li>This vision must include the three areas that Service Manager will touch: the people who will use Service Manager to perform their roles, the underlying products that Service Manager relies on to populate the configuration management database, and the processes that Service Manager will automate.</li>
	<li>When implementing Service Manager, first establish a baseline of your current environment and situation</li>
	<li>IT Service Management (ITSM) is all about behavioral changes: Attitudes drive Behaviors which result in Culture (ABC). Culture is only an outcome, so if a service and value culture is what your customer or organization is looking for, attitudes and behaviors need to change and adapt to the Service Manager journey.</li>
	<li>One common mistake is trying to implement all the Service Manager capabilities in one step. If you try to change more than 10 to 20 percent of operational behaviors in your organization with a Service Manager implementation, you risk poor adoption by the people who will be using it.</li>
	<li>Before implementing Service Manager, understand, document, and review the current processes.</li>
	<li>The goal of Service Manager is to have the IT Infrastructure move from a highly manual and reactive state to a highly automated and proactive state</li>
	<li>Unfortunately, many organizations also try to make Service Manager act and behave like their current ITSM tool without examining the business needs and service management requirements of their organization.</li>
	<li>By linking configuration items (CIs) to work items in Service Manager, you will quickly improve your incident and change management processes and enable problem management.</li>
	<li>Service Manager therefore does not provide some of the traditional call center capabilities like decision call tree, launchpad for initial intake (before you know what service, incident, request), or quick ticket (although this can be accomplished through templates).</li>
	<li>Move away from using the term tickets and instead enable service-based intakes via the portal. This enables better routing of requests and incidents since you are leveraging services for ownership and resolution.</li>
	<li>The list covers all of the capabilities in Service Manager. Make sure there is a name assigned to each role plus an outline of the time required for these roles. Remove the role types for the capabilities you will not be deploying.</li>
	<li>TABLE 3-1 Roles that need to be engaged in a Service Manager implementation</li>
</ul>
<div>
<h3>Chapter 04: How To Prepare For A Service Manager Installation</h3>
<div>
<ul>
	<li>When implementing Microsoft System Center 2012 Service Manager, you need to ensure that the quality of data to be imported and the maturity of Service Management processes are well understood and defined</li>
	<li>Prior to importing data from Active Directory, you should review the considerations listed in Table 4-1 and ensure that you examine the quality and management of data coming from Active Directory.</li>
	<li>Prior to implementing the Operations Manager connectors, examine the health of Operations Manager and understand what management packs are deployed and which items are monitored. Table 4-2 lists some Operations Manager areas to be reviewed.</li>
	<li>One of these is the Configuration Item connector, which pulls in hardware inventory, software inventory, and software updates. To get the most out of this connector, you will need to enable asset intelligence in Configuration Manager and ensure that the processor data, software inventory, and licensing WMI classes are all enabled. The data imported from Configuration Manager will augment the existing data pulled from the Active Directory connector and link the user with the computer by leveraging the asset intelligence top console user as the primary user of the computer.</li>
	<li>The second Configuration Manager connector is the Desired Configuration Management connector, which works with the Desired Configuration Management (DCM) feature of Configuration Manager to raise incidents in Service Manager when the managed configuration drifts. Before you implement these Configuration Manager connectors, you should review the health of the environment as described in Table 4-3.</li>
	<li>If Virtual Machine Manager also pushes discovery data into Operations Manager, you also need to create an Operations Manager CI connector to import these data into Service Manager. You must make sure that Operations Manager integrates with Virtual Machine Manager first and that the Virtual Machine Manager management pack is imported into Service Manager as well.</li>
	<li>The key areas to examine and discuss before configuring incident management are listed in Table 4-4.</li>
	<li>Change management in Service Manager works best if you first create predefined change templates that analysts can select from a list.</li>
</ul>
<div>
<h3>Chapter 05: Management Packs</h3>
<div>
<ul>
	<li>Most Service Manager configuration changes are contained, transferred, configured, authored, and customized through the use of management packs, so properly structuring and naming them are of the utmost importance before beginning to create new ones.</li>
	<li>When extending classes, keep extensions separate from form modifications so the form can be removed (deleted) from Service Manager without impacting the class or data records</li>
	<li>Following a naming convention consistently can certainly be helpful in the administration and configuration of Service Manager</li>
	<li>Service offerings and request offerings (which mimic a one-to-many relationship) should be contained in management packs aligned with a service offering management pack</li>
	<li>The request offering and associated template must be in the same management pack. Although not required, containing the request offering and the service offering in the same management pack is best practice.</li>
	<li>Since notification subscriptions are dependent upon notification templates, they should be maintained together by module. For example:</li>
	<li>
<div>
<ul>
	<li>MS.Incident.Notifications Notification subscriptions and templates for incident management</li>
	<li>MS.ServiceRequest.Notifications Notification subscriptions and templates for service request management</li>
</ul>
</div></li>
	<li>IMPORTANT Notifications can be configured from both subscriptions as well as the workflowconfiguration view. In Service Manager 2012, subscriptions handle related recipients as well as periodic notifications. The only time it is recommended to configure notification type workflow within the workflowsconfiguration view is if it is a notification specific to a particular workflow that also applies a work item template that doesn’t have any overlap with any other processes or workflows.</li>
	<li>Sealing management packs requires a strong name assemblies (SNK) file that contains a unique key pair consisting of a private and public key. For more information on SNK files, see <a href="http://msdn.microsoft.com/en-us/library/wd40t7ad.aspx.">http://msdn.microsoft.com/en-us/library/wd40t7ad.aspx.</a></li>
	<li>To seal a management pack you can use either the Authoring tool that comes with Service Manager or the FastSeal.exe tool. For more information on using the Authoring tool, see the step-by-step guidance at http://technet.microsoft.com/da-dk/library/hh495605.aspx. For additional information on sealing management packs and to download the Fastseal.exe tool, see <a href="http://blogs.technet.com/b/servicemanager/archive/2009/12/25/sealing-management-packs.aspx.">http://blogs.technet.com/b/servicemanager/archive/2009/12/25/sealing-management-packs.aspx.</a></li>
	<li>IMPORTANT Service Manager determines whether a management pack already exists by examining its internal name. So if you change its internal name, it will be treated like a brand new management pack. This means if you import a management pack after changing its name, at best you’ll get an error message and at worst you’ll create duplicate configurations. That is why it is important to delete the existing management pack before importing the renamed version. This means it is sometimes impossible to rename management packs after a system has been in production, since deleting certain management packs can cause loss of production data. So it’s important to get the naming correct before any custom management pack is imported into the production system.</li>
</ul>
</div>
<h3>Chapter 06: Optimizing The Service Manager Environment</h3>
<div>
<ul>
	<li>Microsoft System Center 2012 Service Manager is a complex product that requires Windows Server, Internet Information Services (IIS), Microsoft SQL Server, SQL Server Reporting Services, SQL Server Analysis Services, and Microsoft SharePoint.</li>
	<li>The first Service Manager management server to be installed acts as the workflow server and is critical to the environment</li>
	<li>The most important resources to the management servers are RAM and CPU.</li>
	<li>Always try to avoid adding other roles to the management servers, for example SharePoint or SQL Server. This is because the management server is the primary engine supporting the Service Manager infrastructure.</li>
	<li>Never maximize the Service Manager console because it impacts performance due to a Windows Presentation Foundation (WPF) issue. Instead, minimize the console and extend the window as needed, even to fill the entire screen; just don’t use the maximize button. This is a one-time task since the Service Manager console size is stored and reused at next launch.</li>
	<li>Each view the user selects when using the console increases the console start time because every view is cached. For example, selecting the All Incidents view has a huge pull on the database, and therefore it takes a long time to load.</li>
	<li>Consider using the Global Operators group when assigning tickets to limit the number of users loaded when searching for anything assigned to Analyst. Doing this can result in a drastic performance improvement. (See <a href="http://blogs.technet.com/b/servicemanager/archive/2012/12/14/faq-why-does-it-take-so-long-to-find-users-in-the-assigned-to-and-primary-owner-fields.aspx.)">http://blogs.technet.com/b/servicemanager/archive/2012/12/14/faq-why-does-it-take-so-long-to-find-users-in-the-assigned-to-and-primary-owner-fields.aspx.)</a></li>
	<li>The database is therefore very I/O intensive and is a critical component when it comes to performance</li>
	<li>For optimal performance, place the Log database, TempDB database, and the Service Manager database on separate high performance logical unit numbers (LUNs) to optimize I/O.</li>
	<li>Configure the SQL Service to use 1 to 2 GB less than the total RAM available in the server to ensure the SQL Server does not exhaust the operating system.</li>
	<li>Configure the database for the expected size and disable autogrow. This will ensure the database isn't extended during normal working hours; instead, SQL administators can manually extend the database if needed.</li>
	<li>The TempDB performance is critical to Service Manager performance. Use Multiple TempDB files, for example one per two cores (this is not necessary for the other databases). For more information, see <a href="http://technet.microsoft.com/en-us/library/ms175527(v=SQL105).aspx.">http://technet.microsoft.com/en-us/library/ms175527(v=SQL105).aspx.</a></li>
	<li>The default retention of work items in the CMDB is 90 days for incidents and 365 days for the others (change, release, service, and problem). You can decrease these settings and still comply with the requirement to have enough work items available in the console views. Decreasing the retention keeps the CMDB to a reasonable size. Remember that work items that are closed (not resolved, completed, and so on) are removed from the CMDB, but they are still available in the Data Warehouse for reporting purposes. For more information, see <a href="http://blogs.technet.com/b/servicemanager/archive/2009/09/18/data-retention-policies-aka-grooming-in-the-servicemanager-database.aspx.">http://blogs.technet.com/b/servicemanager/archive/2009/09/18/data-retention-policies-aka-grooming-in-the-servicemanager-database.aspx.</a></li>
	<li>When the Data Warehouse management group is installed and all features are enabled, seven databases are created:</li>
	<li>
<div>
<ul>
	<li>DWDataMart</li>
	<li>DWStagingAndConfig</li>
	<li>DWRepository</li>
	<li>DWASDataBase</li>
	<li>OMDWDataMart</li>
	<li>CMDWDataMart</li>
	<li>ReportServer</li>
</ul>
</div></li>
	<li>The performance of the Data Warehouse has no impact on the console user's performance experience.</li>
	<li>Split some of the Data Warehouse databases across more SQL servers. However, keep in mind:</li>
	<li>
<div>
<ul>
	<li>The DWStagingAndConfig and DWRepository databases must be on the same SQL Server instance.</li>
</ul>
</div></li>
	<li>The DWDataMart, OMDWDataMart, and CMDWDataMart can each be placed on different SQL Server instances. (There is no reason to place these databases on different SQL Server instances because the quantity of data and access to the data stored in the OMDWDataMart and CMDWDataMart databases are not large.)</li>
	<li>Place the SQL Server Analysis Server instance on a different SQL instance than the Data Warehouse databases. This will ensure that cube processing does not affect the extract, transform, and load jobs or the execution of reports. Processing of cubes is handled differently in SQL Server Standard than in SQL Server Enterprise; Enterprise can do incremental processing instead of just full. With SQL Server Enterprise, you can move the Analysis database to another drive. This is not an option in SQL Server Standard. If possible, use the Enterprise edition for the Data Warehouse.</li>
	<li>By default, data in the Data Warehouse is retained for three years. You can modify this retention setting, but it requires some complicated changes. For more information, see <a href="http://blogs.technet.com/b/servicemanager/archive/2011/06/07/how-much-data-do-we-retain-in-the-service-manager-data-warehouse.aspx.">http://blogs.technet.com/b/servicemanager/archive/2011/06/07/how-much-data-do-we-retain-in-the-service-manager-data-warehouse.aspx.</a></li>
	<li>SQL Server Enterprise includes additional features that enhance your experience with the Service Manager Data Warehouse. For the Service Manager Database (CMDB), however, the Enterprise edition of SQL is not needed.</li>
	<li>To get the best out of Service Manager, you might need to redesign some of your processes to better align them with the tool</li>
	<li>Service Manager Self-Service Portal for System Center 2012, 2012 SP1, and 2012 R2 is supported only on SharePoint 2010. SharePoint 2010 is supported to run only on Windows Server 2008 or 2008 R2, not on Windows Server 2012. Service Manager Portal is the only Service Manager component that cannot run on Windows Server 2012.</li>
	<li>You can install Service Manager Portal on the free SharePoint Foundation 2010 edition.</li>
	<li>When the Web Content Server role is installed, make sure to verify that Application Pool Recycling is disabled. The default is nightly recycling, which results in a slow initial load for the users first accessing Portal. Also make sure you do not set recycling for high memory usage. For more information, see <a href="http://blogs.technet.com/b/servicemanager/archive/2011/05/11/faq-why-is-the-self-service-Portal-so-slow.aspx.">http://blogs.technet.com/b/servicemanager/archive/2011/05/11/faq-why-is-the-self-service-Portal-so-slow.aspx.</a></li>
	<li>When designing request offerings, aim to limit the number of custom icons used. Too many custom icons can have an impact on the time it takes to load the Portal main page.</li>
	<li>For both out-of-the-box and third-party connectors, always use a unique run-as account for each connector. Doing this will create a separate MonitoringHost.exe process on the workflow management server for each connector running on the server, making it easier to see which connector is currently running and how much memory/CPU it is consuming. It also makes it easier to isolate one connector from other connectors so that it can be terminated without affecting other connectors or workflows.</li>
	<li>Configure your connectors to avoid having them pull large amounts of data into Service Manager during the day, thereby affecting performance. All of the connectors are configured via the Administration tab in the console, except the Active Directory and Virtual Machine Manager connectors, which are configured using management packs.</li>
	<li>The first thing to consider when configuring the Active Directory connector is whether you need all directory objects in the CMDB.</li>
	<li>If you are also using the Configuration Manager connector, there really isn't a need for the Active Directory connector to import all computer objects since it would only mean that Service Manager would have to import, merge, and maintain two sources. All relevant information about computers in the environment is delivered by the Configuration Manager connector.</li>
	<li>Work items are often assigned to support groups first and then to individual user accounts, so they don’t contain membership information. Therefore, groups are often not used in Service Manager. So instead of importing all Active Directory groups, filter to import only the relevant groups as needed.</li>
	<li>It is therefore important to consider which organizational units (OUs) to import users from and also whether to import both enabled and disabled users</li>
	<li>Depending on your OU structure, it is best to create separate Active Directory connectors to avoid populating the CMDB with unnecessary data</li>
	<li>NOTE Always select the Do Not Write Null Values For Properties That Are Not Set In Active Directory option to ensure the connector does not update the same attributes despite being null. If you need to write null values from Active Directory, however, do not select this option.</li>
	<li>When designing the Active Directory connector, consider using LDAP filters to import only relevant types of objects. For more information on LDAP filters, see <a href="http://msdn.microsoft.com/en-us/library/windows/desktop/aa746475(v=vs.85).aspx.">http://msdn.microsoft.com/en-us/library/windows/desktop/aa746475(v=vs.85).aspx.</a></li>
	<li>If your design includes several Active Directory connectors that daily import large numbers of changes, consider scheduling the time each connector runs, taking into account the duration that each connector needs to complete, so no more than one Active Directory connector runs at a time.</li>
	<li>If you plan to use the Operations Manager Alert connector to have alerts automatically created as incidents in Service Manager, do not create the connector until you have tuned the Operations Manager environment to report only relevant actionable alerts</li>
	<li>Begin with only a few management packs from Operations Manager to import alerts into Service Manager. Create incident management templates with predefined values for Support Group and Incident classification per management pack to start off slowly. Export all the management packs in Operations Manager and provide this list to the IT infrastructure team and ask: Who needs this alert assigned to them? Then create incident templates using the information that IT provides to streamline the assignment of alerts to the groups that are responsible for them.</li>
	<li>Be very selective concerning which Operations Manager monitored objects need to be added to the CMDB. There is no requirement for importing all Operations Manager monitored objects into the CMDB. The more objects that are imported into the CMDB, the more objects need to be maintained by the connectors, workflows, and so on. For more information, see <a href="http://blogs.technet.com/b/servicemanager/archive/2010/02/26/managing-the-allowed-list-for-the-operations-manager-ci-connector-with-powershell.aspx.">http://blogs.technet.com/b/servicemanager/archive/2010/02/26/managing-the-allowed-list-for-the-operations-manager-ci-connector-with-powershell.aspx.</a></li>
	<li>If you are not using DCM in your environment, you should disable the DCM rule in Service Manager. For more information, see <a href="http://blogs.technet.com/b/mihai/archive/2012/11/30/configuration-manager-connector-s-dcm-rule-can-cause-massive-performance-issues-in-service-manager.aspx.">http://blogs.technet.com/b/mihai/archive/2012/11/30/configuration-manager-connector-s-dcm-rule-can-cause-massive-performance-issues-in-service-manager.aspx.</a></li>
	<li>Always consider which collections in Configuration Manager to import because selecting All Systems might import data from systems that aren’t relevant to store in the CMDB.</li>
</ul>
</div>
<h3>Chapter 07: Service Manager Configuration And Customization</h3>
<div>
<ul>
	<li>Existing out-of-the-box capabilities in Service Manager should be understood and exploited before customizing a solution</li>
	<li>One of Microsoft’s technical principles is "configure before customize,"</li>
	<li>Service Manager doesn’t provide inter-field dependency, there is no connection between the enumerated list "Support Group" and the user/group relationship "Assigned To." This must therefore be implemented manually or using a template setting because if queues have been defined against support groups, an inaccessible incident or service request may be assigned.</li>
	<li>Most modern ITSM solutions use:</li>
	<li>
<div>
<ul>
	<li>Configuration item for the exact item or items the incident is about</li>
	<li>Service for the exact service or services the incident is about</li>
	<li>Resolution codes for how the incident was resolved</li>
</ul>
</div></li>
	<li>What still remains, however, is to use a classification category to describe the incident itself rather than what it is about.</li>
	<li>Keep the number of values to a minimum. A common rule is 10 x 10, which means no more than 10 parents with 10 children each. This helps facilitate reporting along classification category values.</li>
	<li>Eliminate other as an option.</li>
	<li>Do not include the term problem in the value unless it is absolutely asked for by people outside of IT. Problem as a term has specific meaning in problem management.</li>
	<li>Classify the incident, not what it is about (that’s what configuration item and service are for).</li>
	<li>The process should seek to eliminate the need to change it more than once (a performance category should apply to both configuration item and service).</li>
	<li>Microsoft therefore recommends that Orchestrator always be implemented along with Service Manager</li>
	<li>Whenever you are dealing with dates and times in Orchestrator and manipulating data in Service Manager, the date/time data is stored as UTC. You therefore should use the UTC option in Orchestrator</li>
	<li>It's important to update Closed Date with the current UTC date and time since that is not set automatically.</li>
</ul>
—————————————————————

Don’t forget to check out the following:

<span id="control_gen_2" class="commentary"><strong>CANITPro:</strong> Did you know there is a site dedicated to Canadian IT professionals? You can win a 3D movie prize package by upgrading your IT skills with Microsoft. Check out CANITPRO At The Movies, either in English: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600830" target="_blank">CANITPro At The Movies</a></span><span id="control_gen_3" class="commentary"> or French: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600850" target="_blank">CANITPro At The Movies</a></span>

<strong>Azure:</strong> Sign up for a FREE trial and get $200 to spend on <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597585" target="_blank">Microsoft Azure</a> cloud computing services. Full access, no strings.

<span id="control_gen_5" class="commentary"><strong>MSDN:</strong> Ever wanted to work with the latest Microsoft technologies, without having to spend thousands of dollars? Now you can, with the <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597617" target="_blank">MSDN subscription</a>. </span>

</div>
</div>
</div>
</div>
</div>
</div>
