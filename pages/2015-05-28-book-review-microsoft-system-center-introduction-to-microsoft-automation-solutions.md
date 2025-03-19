---
layout: page
title: Book Review: Microsoft System Center Introduction to Microsoft Automation Solutions
date: 2015-05-28 15:28
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2015/05/Introduction-to-Microsoft-Automation-Solutions.jpg"><img class="alignleft size-full wp-image-12511" src="/wp-content/uploads/2015/05/Introduction-to-Microsoft-Automation-Solutions.jpg" alt="Introduction to Microsoft Automation Solutions" width="199" height="244" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2014/12/10/free-ebook-microsoft-system-center-introduction-to-microsoft-automation-solutions.aspx" target="_blank">Microsoft System Center Introduction to Microsoft Automation Solutions</a> eBook.

The chapter(s) that I found most helpful were Chapter 2 “Understanding Automation: Architectures”, hence the majority of my highlights are from this chapters.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: Why Automation?</h3>
<div>
<ul>
	<li>Runbook Writing Wiki: <a href="http://social.technet.microsoft.com/wiki/contents/articles/26616.quick-tips-and-tricks-for-runbook-writing.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/26616.quick-tips-and-tricks-for-runbook-writing.aspx</a></li>
	<li>Functionally, the Microsoft automation tools overlap with the existing capability of System Center Orchestrator, and you may wonder which one you should use</li>
</ul>
&nbsp;
<h3>Chapter 02: Understanding Automation: Architectures</h3>
<div>
<ul>
	<li>The recommended architecture for a Service Management Automation deployment includes the following:
<ul>
	<li>A dedicated SQL server instance for the database role</li>
	<li>Three servers co-hosting the web service and runbook worker roles</li>
	<li>Load balancing of the web service role</li>
	<li>Virtual machine deployment for ease of scaling and management</li>
	<li>For hardware and software requirements, refer to the Service Management Automation TechNet article at http://technet.microsoft.com/en-us/library/dn469256.aspx.</li>
</ul>
</li>
	<li>The database must run on Microsoft SQL Server 2012 at minimum and can be deployed to a standalone SQL Server server, a SQL Server failover cluster, or a SQL Server AlwaysOn Availability Group</li>
	<li>It is worth noting the Service Management Automation database is a contained database, meaning it can be included in an availability group without the need to manually replicate additional objects.</li>
	<li>The web service is essential for the operation of your Service Management Automation deployment; therefore, planning how it is deployed with scalability and resiliency in mind is critically important.</li>
	<li>Consider the following when planning the deployment of the web service:
<ul>
	<li>Use a generic DNS hostname for your web service URL, such as sma.contoso.com.</li>
	<li>Provision a web server certificate for your web service role using your generic DNS hostname. Be sure to mark the certificate’s private key as exportable so you can install it on additional web service role servers. As a general best practice with certificates, be sure to keep the certificate’s private key safe.</li>
	<li>If you plan to use a third-party load balancer, use it to front your single server deployment initially so scaling out will not impact the service.</li>
</ul>
</li>
	<li>In the static job queue model, if a runbook worker becomes unavailable, any jobs destined for that server do not process until that server (or a new server with the same name) is brought online.</li>
	<li>When you sign up for Microsoft Azure, you establish an Azure account that acts as a management and billing container. Within an Azure account, you can create and manage one or more Azure subscriptions, which can be used to separate administrator access or manage multiple lifecycles (e.g., development, test, and production).</li>
	<li>A runbook that runs for more than 30 minutes will be suspended to allow other runbook jobs on the same runbook worker to process</li>
	<li>The Azure Automation service billing model is based on runbook processing time in minutes</li>
</ul>
&nbsp;
<h3>Chapter 03: Understanding Automation: Interfaces</h3>
<div>
<ul>
	<li>For more details of URI syntax for the Service Management Automation web service, refer to <a href="http://msdn.microsoft.com/en-us/library/dn720250.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/dn720250.aspx</a>.</li>
	<li>By default, the Service Management Automation web service is enabled for both Basic and Windows authentication</li>
	<li>Whichever authentication method is used, the authenticating user must then be authorized to use the web service through membership in the smaAdminGroup local group on the web service servers.</li>
	<li>The Service Management Automation Powershell module can be deployed on any system with Windows PowerShell version 4.0.</li>
</ul>
&nbsp;
<h3>Chapter 04: Implementing Automation</h3>
<div>
<ul>
	<li>Be aware that testing a runbook runs it live on a runbook worker server, so be sure to develop in a development environment before running your runbooks in production</li>
	<li>For more details of using activities in script workflows, please refer to <a href="http://technet.microsoft.com/en-us/library/jj574194.aspx" target="_blank">http://technet.microsoft.com/en-us/library/jj574194.aspx</a>.</li>
</ul>
&nbsp;
<h3>Chapter 05: Managing Runbooks</h3>
<div>
<ul>
	<li>Service Management Automation provides a built-in grooming process that relies on the SQL Server Agent to purge job history, and when this is enabled, the process will run every 15 minutes. By default, data older than 30 days is purged from the database.</li>
	<li>If you require more detailed event log data, you can enable the Analytic log, which provides extensive logging information. However, enabling this log should be reserved for troubleshooting very complex issues.</li>
	<li>It is always a best practice to replace a self-signed certificate with a certificate from an internal or external certificate authority that is trusted by your computers and services.</li>
	<li>The web service and runbook worker roles of Service Management Automation both utilize a service account. The account used can be the same for both, but it is better for service accounts to leverage a separate account per role to help identify issues later.</li>
	<li>During the installation of each role, the service account you provide is granted access to the Service Management Automation database with dbowner privileges and is granted the Logon as a Service right on the local server. Often, security policies override the Logon as a Service privilege by centrally managed configurations, so keep this in mind if your Service Management Automation system is not functioning.</li>
	<li>During the installation of the web service role, a local group called smaAdminGroup is created on the server. This group is used to grant access accounts using the web service. By default, during the installation of the web service, only the service account specified during installation is added to the local group. Best practice is to place a group from your Active Directory domain in this local group and use the domain group for managing access to your Service Management Automation web service.</li>
</ul>
&nbsp;
<h3>Chapter 06: Examples of Automation Scenarios</h3>
<div>
<ul>
	<li>Because the Integration Module is known to Azure Automation, you do not need to explicitly import the runbook using the Import-Module cmdlet</li>
</ul>
</div>
</div>
</div>
</div>
</div>
</div>
