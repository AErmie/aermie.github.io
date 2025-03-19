---
layout: page
title: Book Review: Microsoft System Center Configuration Manager Field Experience
date: 2015-04-30 16:11
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2015/04/Configuration-Manager-Field-Experience-Cover.jpg"><img class="alignleft size-full wp-image-10011" src="/wp-content/uploads/2015/04/Configuration-Manager-Field-Experience-Cover.jpg" alt="Configuration Manager Field Experience Cover" width="200" height="244" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2013/10/03/free-ebook-2-in-this-series-microsoft-system-center-configuration-manager-field-experience.aspx" target="_blank">Microsoft System Center: Configuration Manager Field Experience</a> eBook.

The chapters that I found most helpful was Chapter 6 "Operating System Deployment Tips", hence the majority of my highlights are from this chapter.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 01: Introduction to WMI in Configuration Manager 2012</h2>
<ul>
	<li>None</li>
</ul>
&nbsp;
<h2>Chapter 02: Configuration Manager Custom Reporting</h2>
<ul>
	<li>For example, you might want information about MAC addresses. Start by finding the table or view that contains this information. To do this, run the following query to get all tables and views that contain a column name like %MacAddress%: Select * from INFORMATION_SCHEMA.COLUMNS Where COLUMN_NAME like '%MacAddress%'</li>
	<li>The configuration database contains different types of views. For example, views that start with V_GS contain current data while those that start with V_HS contain historical data.</li>
	<li>An inner join returns the matching records in both tables.</li>
	<li>So an inner join by design looks for matching records in both tables.</li>
</ul>
&nbsp;
<h2>Chapter 03: Integrating SQL Server Reporting Services with Configuration Manager 2012</h2>
<ul>
	<li>To change the URL, you must uninstall the reporting services point, change the URL, and then reinstall the reporting services point</li>
	<li>The reporting services point account must have Read rights to the site database.</li>
</ul>
&nbsp;
<h2>Chapter 04: Customizing SSRS Reports for Configuration Manager 2012</h2>
<ul>
	<li>None</li>
</ul>
&nbsp;
<h2>Chapter 05: Customizing Function-Based Built-In Reports</h2>
<ul>
	<li>None</li>
</ul>
&nbsp;
<h2>Chapter 06: Operating System Deployment Tips</h2>
<ul>
	<li>You can test missing drivers with drvload to see if you have the correct driver to add to your boot image. Below is a quick step-by-step procedure for using drvload to verify that you have the proper driver.
<ul>
	<li>1. Determine the driver that is missing and download it to media.</li>
	<li>2. Insert media and change directory to the folder holding your INF files.</li>
	<li>3. Run drvload.exe NameOfYour.inf.</li>
	<li>4. Validate that you can access the disk or obtain an IP address</li>
	<li>5. Add to a boot image in Configuration Manager.</li>
</ul>
</li>
	<li>Best practice is to build a solid driver store that is easy for you to maintain and to know what you have in your environment. Michael Niehaus (<a href="http://blogs.technet.com/b/mniehaus/default.aspx?PageIndex=1" target="_blank">http://blogs.technet.com/b/mniehaus/default.aspx?PageIndex=1</a>) and Johan Arwidmark (<a href="http://deploymentresearch.com/Research.aspx" target="_blank">http://deploymentresearch.com/Research.aspx</a>) both have very detailed blog posts on the subject with examples of sound driver stores if you would like to find out more information.</li>
	<li>It’s important to regularly check your OEM for updated drivers not only to improve device functionality but to also patch security vulnerabilities in the drivers.</li>
	<li>Always build your reference image on a virtual machine in BIOS compatibility mode.</li>
	<li>USB boot media must be formatted as FAT32</li>
	<li>The typical disk layout for UEFI deployments looks like this:
<ul>
	<li>Recovery (NTFS, 300 MB)</li>
	<li>System (FAT32, active, 300 MB)</li>
	<li>Microsoft Reserved Partition (MSR, 128 MB)</li>
	<li>Operating System (NTFS, 100%)</li>
</ul>
</li>
	<li>By integrating MDT into Configuration Manager, you gain the ability to use the additional templates, actions, and customized boot images and to call external scripts, databases, web services, and much more to enhance and streamline your operating system deployment needs.</li>
	<li>Setting OSDPreserveDriveLetter=YES will deploy the operating system to the drive from which it was captured. For instance, the install.wim is captured with the c:\ drive as the destination disk, so that would hold true with OSDPreserveDriveLetter set to true. In some cases, this setting does not produce the desired affect, but in most cases this will work fine.</li>
	<li>The task sequence disables Group Policy Object (GPO) processing during the task sequence</li>
	<li>By default only one rollover log is maintained and the rest of the log is purged.</li>
	<li>The Configuration Manager team has provided the ability to extend logging so you can have more to work with if you are troubleshooting something or simply want to verify what happened. CCMLOGLEVEL, CCMLOGMAXHISTORY, and CCMLOGMAXSIZE all are configurable in the installation properties of the ConfigMgr Client Installation step of the task sequence. By setting these variables, you will gain more robust logging:
<ul>
	<li>CCMLOGLEVEL=0 Turns on verbose logging.</li>
	<li>CCMLOGMAXHISTORY=6 Sets the number of log files to keep.</li>
	<li>CCMLOGMAXSIZE=2621440 Sets the log size to 2.5 MB.</li>
</ul>
</li>
	<li>Global conditions in Configuration Manager 2012 are rules that represent business or technical conditions that can be used to specify how an application is provided and deployed to client devices</li>
	<li>For details about how to set up chassis-type global conditions, go to <a href="http://blogs.technet.com/b/brandonlinton/archive/2013/01/30/configmgr-2012-chassis-type-global-condition.aspx" target="_blank">http://blogs.technet.com/b/brandonlinton/archive/2013/01/30/configmgr-2012-chassis-type-global-condition.aspx</a>.</li>
	<li>Configuration Manager task sequences run under the system context in session 0, so any application that requires interaction will fail or simply sit and time out</li>
	<li>MDT has a variable called SLShare that you can use in MDT Integrated task sequences to find all of the common log files and copy them up to a file share when the task sequence is complete.</li>
</ul>
—————————————————————

Don’t forget to check out the following:

<span id="control_gen_2" class="commentary"><strong>CANITPro:</strong> Did you know there is a site dedicated to Canadian IT professionals? You can win a 3D movie prize package by upgrading your IT skills with Microsoft. Check out CANITPRO At The Movies, either in English: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600830" target="_blank">CANITPro At The Movies</a></span><span id="control_gen_3" class="commentary"> or French: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600850" target="_blank">CANITPro At The Movies</a></span>

<strong>Azure:</strong> Sign up for a FREE trial and get $200 to spend on <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597585" target="_blank">Microsoft Azure</a> cloud computing services. Full access, no strings.

<span id="control_gen_5" class="commentary"><strong>MSDN:</strong> Ever wanted to work with the latest Microsoft technologies, without having to spend thousands of dollars? Now you can, with the <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597617" target="_blank">MSDN subscription</a>. </span>
