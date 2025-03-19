---
layout: page
title: Book Review: SAMS System Center 2012 Orchestrator
date: 2014-05-19 13:02
author: AdinErmie
comments: true
categories: []
---
<p style="color: #444444;"><a href="/wp-content/uploads/2014/05/System-Center-2012-Orchestrator-Unleashed-Cover.jpg"><img class="alignleft size-full wp-image-10111" src="/wp-content/uploads/2014/05/System-Center-2012-Orchestrator-Unleashed-Cover.jpg" alt="System Center 2012 Orchestrator Unleashed Cover" width="260" height="334" /></a>Hello Everyone,</p>
<p style="color: #444444;">Something that you may not know about me, but I am an avid reader. Late last year I was able to complete my reading of the <a href="http://www.amazon.com/gp/product/0672336103/ref=s9_qpp_gw_p14_d0_i1?pf_rd_m=ATVPDKIKX0DER&amp;pf_rd_s=center-4&amp;pf_rd_r=1W778JVAF1643EX0BWVJ&amp;pf_rd_t=101&amp;pf_rd_p=1688200482&amp;pf_rd_i=507846" target="_blank">SAMS System Center 2012 Orchestrator Unleashed</a> book. That’s right, I read the entire book cover-to-cover.</p>
<p style="color: #444444;">If you are like me, when reading a 768 page book, you’re bound to come across either some interesting points, tips, etc. However, unless you make some sort of note about it, you’re more than likely to forget about it by the time you get to the end. Therefore, I have gotten into the habit of purchasing the eBook (along with a physical printed copy) and making highlights as I go. I then sync  these highlights to my Evernote account, so that I can easily access, and search them in the future.</p>
<p style="color: #444444;">Well, I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).</p>

<h3>Chapter 01: Orchestration, Integration, and Automation</h3>
<ul>
	<li>Orchestrator does not define your processes. This is the first challenge you face after you decide to orchestrate your processes: Running Orchestrator does not instantly give you orchestrated processes.</li>
	<li>Define Your Processes</li>
	<li>You first must reach an agreement with your users on the service you will deliver</li>
</ul>
&nbsp;
<h3>Chapter 02: What’s New in System Center 2012 Orchestrator</h3>
<ul>
	<li>A Microsoft SQL Server database stores all data and configurations. This database is a critical feature and should be configured for high availability. If the SQL Server goes down, runbook servers cannot execute any runbooks. Orchestrator uses one database with a default name of Orchestrator and a correlation of SQL_Latin1_General_CP1_CI_AS.</li>
	<li>The management server exists primarily to establish communication between the design features and the SQL database. It is not a critical runtime feature and does not necessarily need to be highly available.</li>
	<li>You can deploy multiple runbook servers to allow for load balancing</li>
	<li>the Runbook Tester actually executes and commits changes when testing a runbook. It does not display “what if” data or scenarios. Keep this in mind, and use a development environment whenever a runbook might affect existing IT services.</li>
	<li>The management server is still limited to one per environment, is needed only to connect the Runbook Designer, and does not need to be highly available. The database and runbook servers are the features required for runbooks to execute. Each runbook server is limited by default to 50 runbooks per runbook server. If you are using Service Manager with the Orchestrator connector, you will want the Orchestrator web service to be highly available as well.</li>
</ul>
&nbsp;
<h3>Chapter 03: Looking Inside System Center 2012 Orchestrator</h3>
<ul>
	<li>also referred to as SCOrch</li>
	<li>Orchestrator enables information technology (IT) organizations to automate IT infrastructure tasks.</li>
	<li>Microsoft supports virtualization of all components of System Center 2012 Orchestrator</li>
	<li>System Center 2012 Orchestrator contains six primary features, some required and others optional.</li>
	<li>The authors recommend that your Orchestrator servers belong to an Active Directory domain, although this it is not a requirement. You can mix components between domains and workgroups; as an example, you can have your management server and database server in one domain, with runbook servers in workgroups or other domains.</li>
	<li>Only one management server can exist in an Orchestrator environment. Orchestrator does not provide the means to have a fault-tolerant management server because this role cannot be clustered.</li>
	<li>Runbook servers communicate directly with the database to obtain jobs to execute and to report results</li>
	<li>The management server is needed only when connecting to the Runbook Designer console or Deployment Manager console</li>
	<li>If you need to recover the management server in a disaster scenario, you can reinstall the role and point it to the Orchestrator database</li>
	<li>Additional information regarding runbook server deployments is available at <a href="http://technet.microsoft.com/en-us/library/hh420386.aspx.">http://technet.microsoft.com/en-us/library/hh420386.aspx.</a></li>
	<li>You can deploy multiple runbook servers, depending on constraints such as network requirements and number of runbooks that need to run at the same time.</li>
	<li>When a request to start a runbook comes in (manually by an operator or administrator, or through a scheduled activity or other automated mechanism), a job is created in the Orchestrator database. When a runbook server finds the job, it marks it as in progress, copies the runbook locally, and begins executing the runbook.</li>
	<li>The authors recommend that you deploy the Orchestrator database on a well-performing and fault-tolerant SQL Server.</li>
	<li>Using the Orchestrator web service, custom applications can connect to Orchestrator to start and stop runbooks.</li>
	<li>An important distinction between the Orchestration console and the Runbook Designer is that when you start a runbook from the Orchestration console, you can input parameters that a runbook needs to run, which you cannot do using the Runbook Designer. Using the Orchestration console, you can also see the status of runbooks and activities within runbooks.</li>
	<li>Two core considerations when determining placement and design are security requirements and the anticipated number of runbooks.</li>
	<li>Another security-related design challenge arises if you cannot assign a single Runbook Server service account all the permissions it requires on the target machines.</li>
	<li>Orchestrator communicates extensively with the database, you want high-speed communication between these two Orchestrator features and should size and configure the database for optimal performance</li>
	<li>if you have runbooks that do not require input from an operator to run, you could consider eliminating the Orchestration console</li>
	<li>Each subject matter expert team has an Orchestrator environment for development and simple testing of runbooks.</li>
	<li>Runbooks in the production environment should be handled by version control, including change management. Managing all changes to runbooks in production is important. Because System Center 2012 Orchestrator has no rollback or “undo” feature, maintaining earlier versions of runbooks and controlling all modifications to your runbooks is crucial.</li>
	<li>you can establish a sanitizing environment, which is a completely blank Orchestrator environment. This sanitizing environment can be a small virtual machine and does not need to meet Microsoft’s hardware requirements</li>
	<li>log purge job that is enabled by default in Orchestrator only cleans up runbook historical data</li>
	<li>Tools such as SanitizeExport can help by removing unnecessary information from runbooks</li>
	<li>On your runbook server, integration packs (OIP files) are stored in the %Program Files(x86)%Microsoft System Center 2012OrchestratorManagement ServerComponentsPacks folder (using default settings)</li>
	<li>reads the heartbeat column of the ACTIONSERVER table in the Orchestrator database. Each runbook server updates the table every 15 seconds. If a runbook server has not updated the heartbeat value for three heartbeat intervals (45 seconds), a platform event is generated.</li>
	<li>The Orchestrator Runbook Service (RunbookService.exe) provides the environment runbooks use to run. This service, which runs on every runbook server, checks the database every 2 seconds to see if there is a new job.</li>
	<li>For example, if you will use the Operations Manager integration pack, you need to install the Operations Manager console on each runbook server because the integration pack uses files from that installation.</li>
	<li>you can use the Orchestrator Integration Toolkit (previously known as the Quick Integration Kit) to create integration packs</li>
	<li>good source for community integration packs is the “System Center 2012 Orchestrator Community Releases” page on CodePlex</li>
	<li>Exporting and importing runbooks is possible between Orchestrator environments</li>
	<li>Each runbook is running within a policymodule.exe process</li>
	<li>The connections are global, meaning that they are accessible to everyone running the Runbook Designer console in the Orchestrator environment</li>
	<li>Integration packs are deployed to runbook servers and computers that have the Runbook Designer console installed</li>
	<li>Runbook Designer is used for designing, modifying, and deploying runbooks</li>
	<li>Using the Runbook Tester console, you can step through a runbook and review input and output data for each activity</li>
	<li>If you move the Orchestrator database, you will use the Data Store Configuration tool to update the location of the SQL Server hosting the database and the database name.</li>
	<li>Out of the box, Orchestrator does not include a PowerShell provider</li>
	<li>Orchestrator Remote Tools provides a way to launch runbooks remotely through either a graphical user interface or the command line</li>
</ul>
&nbsp;
<h3>Chapter 04: Architectural Design</h3>
<ul>
	<li>Which areas of the organization will be working with Orchestrator?</li>
	<li>Which security roles will be necessary?</li>
	<li>Which part of the organization will administer and maintain Orchestrator?</li>
	<li>What is the location of the services and servers with which Orchestrator will integrate</li>
	<li>Do any integration packs (IPs) meet your requirements, or do you need to develop your own?</li>
	<li>What is the process for approving a new runbook or version of a runbook before it is placed in production?</li>
	<li>What type of reports do you need to generate</li>
	<li>Where should log data be stored?</li>
	<li>Does the Orchestrator environment need to be fault tolerant and highly available?</li>
	<li>What are the biggest pain points today when looking at time-consuming manual work?</li>
	<li>What is the purpose or goal of the Orchestrator implementation?</li>
	<li>Compared to other System Center components, Orchestrator is rather simple in terms of physical design.</li>
	<li>If you create a runbook and later delete it, the runbook remains in the database but is marked as deleted</li>
	<li>Orchestrator retains 500 entries of historical data in the database by default, with a log purge executing daily at 1:00:00 a.m.</li>
	<li>The database has a maximum limit of 10,000 log entries for all runbooks.</li>
	<li>Using recommended hardware, the console can handle at least six requests per minute</li>
	<li>Disk performance is one of the most common bottlenecks for Microsoft SQL Server</li>
	<li>Disable autogrow for the Orchestrator database.</li>
	<li>Additional information regarding autogrow is available at <a href="http://support.microsoft.com/kb/315512.">http://support.microsoft.com/kb/315512.</a></li>
	<li>Configure the TempDB database to be 20%–40% of your Orchestrator database data file size.</li>
	<li>Configure the transaction log for the Orchestrator database to be 50% of the Orchestrator database data file size.</li>
	<li>Each runbook server must have a fast and stabile network connection to the Orchestrator database, with a maximum of 30ms latency, and less than 10ms latency recommended.</li>
	<li>Runbook servers must be enabled to access remote systems, where you will execute tasks, with a maximum of 100ms latency.</li>
	<li>Anders Bengtsson has a posting at <a href="http://contoso.se/blog/?p=3338">http://contoso.se/blog/?p=3338</a> that discusses building an Operations Manager dashboard that can show what is going on in Orchestrator.</li>
	<li>Depending on the integrations packs you use, you might need to install additional software on your runbook servers</li>
	<li>Microsoft Silverlight 4 is not required on the Orchestrator web service server or the server hosting the Orchestration console, although it is required for any computer running the Orchestration console.</li>
	<li>Microsoft currently does not support the Runbook Designer on Windows 8</li>
	<li>Runbook Designer requires Microsoft .NET Framework 3.5 Service Pack 1.</li>
	<li>Link colors: The smart link color should reflect the different paths the runbook can take. The authors suggest using green to indicate success, red for critical or warning, and orange when there is a logical condition</li>
	<li>You can use the Orchestrator Visio and Word Generator, available from CodePlex, as a documentation tool. Figure 4.7 shows an example of using this tool. The tool lets you export an Orchestrator runbook as a Visio diagram, and you can generate a connected Word file.</li>
	<li>When you install the management server, you must specify a service account for the Orchestrator Management Service. This account is also used for the Orchestrator Runbook Server Monitor service</li>
	<li>The service account must have local administrator privileges on the management server.</li>
	<li>By default, all activities in a runbook run under the Orchestrator Runbook Service account</li>
	<li>The documentation includes justification and rationale for the runbook, including all parameters, global settings, and variables</li>
	<li>Each runbook server monitors the other runbook servers, verifying the heartbeat time stamp in the Orchestrator database</li>
	<li>If a runbook server has not updated the Heartbeat column in the ACTIONSERVERS table for 45 seconds, the Orchestrator Runbook Server Monitor service generates an alert</li>
</ul>
&nbsp;
<h3>Chapter 05: Installing System Center 2012 Orchestrator</h3>
<ul>
	<li>Decisions to make before installing Orchestrator include determining the placement of the various Orchestrator features and database and web console locations</li>
	<li>Orchestrator features and high availability requirements of these features</li>
	<li>Orchestrator database high availability requirements</li>
	<li>A System Center 2012 Orchestrator installation has six primary features,</li>
	<li>Orchestrator management server</li>
	<li>Orchestrator runbook server</li>
	<li>Orchestrator database</li>
	<li>Orchestration console and web service (must be installed on the same machine)</li>
	<li>Orchestrator Runbook Designer</li>
	<li>SQL Server 2012 AlwaysOn functionality supported</li>
	<li>Software requirements for Orchestration console</li>
	<li>Silverlight 4</li>
	<li>Internet Explorer 8, 9, or 10</li>
	<li>NET Framework 4.0 for Orchestrator web service</li>
	<li>Administrator access on the server is required for installing the Orchestrator features</li>
	<li>After installing the Orchestrator infrastructure, you must perform some basic configuration before starting to build runbooks. This includes customizing security settings, registering integration packs (IPs), migrating Opalis policies, and establishing backups.</li>
	<li>In an upgrade scenario, post-installation tasks include migrating any existing Opalis policies to Orchestrator runbooks.</li>
	<li>Defining a backup strategy for your Orchestrator environment is an important post-installation task</li>
	<li>back up the Orchestrator database</li>
	<li>regularly export your runbooks to have an offline copy of your automations</li>
	<li>If you install multiple features at the same time, the same service account is used for each feature. If you need to use different service accounts for each feature, the feature installations must occur as separate installations so that you can specify a specific service account for each feature installation.</li>
	<li>Creating the new Orchestrator database through the installation wizard requires the person running the setup wizard to have sysadmin rights on the SQL Server to create the database.</li>
	<li>Enabling Network Discovery on the Runbook Designer computer is an additional step. Network discovery is a setting that enables the computer to see other computers and allows that computer to be visible to other computers on the network. Server enumerations (the Browse button for server selections) in the Runbook Designer depend on this functionality</li>
	<li>the option to enable remote access for the Runbook Designer. This default-enabled option enables you to install and run the designer on a computer other than the management server.</li>
	<li>A load balancer, such as Microsoft Windows Network Load Balancing (NLB), can spread the connection load to the console and web service hosted on an IIS server.</li>
	<li>You can install the Orchestrator web service using the Standalone Installations section on the Orchestrator installation wizard start page. This can be a single-instance installation, or you can install additional web services to provide high availability of the service. A load balancer, such as Microsoft Windows Network Load Balancing (NLB), can spread the connection load to the console and web service hosted on an IIS server.</li>
	<li>An additional step in this procedure is configuring the Orchestrator web service to use Secure Sockets Layer (SSL); <a href="http://technet.microsoft.com/en-us/library/hh529160.aspx">http://technet.microsoft.com/en-us/library/hh529160.aspx</a> provides information</li>
	<li>For guidance on requesting and installing a certificate, see the article at <a href="http://support.microsoft.com/kb/299875.">http://support.microsoft.com/kb/299875.</a></li>
	<li>You must connect each Runbook Designer to your management server.</li>
	<li>Integration packs, updates, and hotfixes can be centrally deployed to the installed Runbook Designer instances</li>
	<li>Legacy policies cannot be migrated.</li>
	<li>The Policy Mode property of an Opalis policy is now the Job Concurrency property in Orchestrator</li>
</ul>
&nbsp;
<h3>Chapter 06: Using System Center 2012 Orchestrator</h3>
<ul>
	<li>CodePlex is a good source for community-developed IPs</li>
	<li>Enabling the Store activity specific Published Data option can help troubleshoot runbook execution</li>
	<li>Published Data option can help</li>
	<li>published data is stored for the runbook you are</li>
	<li>If the runbook has a smart link, it invokes the next step in the runbook as soon as the previous task completes</li>
	<li>When a runbook needs input before it can execute the workflow, the runbook must start with the Initialize Data activity.</li>
	<li>Monitoring for an event can be the trigger for a runbook</li>
	<li>Runbooks can be configured to run at a specific or reoccurring time</li>
	<li>Give the links in your runbook meaningful names so that you can follow their flow. A name that corresponds with the condition that is set on the link using different colors can improve the visualization of the activity workflow.</li>
	<li>The conditions on the Exclude tab supersede the rules on the Include tab. In addition, conditions on each tab are joined by using an “or” condition. Only one of the conditions on a tab must be true for the entire tab to be true.</li>
	<li>Data-manipulation functions must be enclosed in square brackets ([ and ]).</li>
	<li>The activities must be linked before the published data is available.</li>
	<li>When the next activity in the runbook runs, it runs once for each item of data produced by the previous activity</li>
	<li>Regular expression matching in Orchestrator is performed based on the Microsoft .NET Framework</li>
	<li>Schedules use the system clock of the operating system on the runbook server to verify the runbook’s start time</li>
	<li>You can configure variables in the Global Settings folder in the Runbook Designer</li>
	<li>The value can be any value specified for the variable. You can choose to encrypt the value so that it is not a readable property in the logging of the runbook</li>
	<li>Using Encrypted Variables</li>
	<li>Variables that are encrypted can be decrypted only by certain fields in activities such as password fields. If you are using an encrypted variable in other fields, the result will be the encrypted text.</li>
	<li>Runbooks do not have to be complete to use the Runbook Tester</li>
	<li>The authors recommend testing and validating your runbook against a test environment, and placing runbooks in production only after positive validation in a test environment</li>
	<li>The console is intended for administrators or users who need to manage the operation of runbooks but are not required to modify them. You can modify runbooks only in the Runbook Designer.</li>
	<li>Following the process described in the “Framework for Creating Runbooks” section ensures that you have captured the necessary information before you begin building your runbook</li>
</ul>
&nbsp;
<h3>Chapter 07: Runbook Basics</h3>
<ul>
	<li>The more important function of this tab is defining a schedule for the runbook. When a schedule is provided, a runbook runs only as its schedule defines.</li>
	<li>the granularity of the unit of measure is limited to 1 hour</li>
	<li>enabling logging increases the size of your Orchestrator database.</li>
	<li>a runbook using a monitoring activity as its starting point cannot have concurrent jobs.</li>
	<li>Deciding When to Use Concurrent Jobs</li>
	<li>When deciding whether to use simultaneous jobs, consider whether the activities in the runbook have a chance of operational collision. For example, if you are writing to a log and need it to be in a sequential order, having multiple jobs writing to the same log might cause entries to become out of position.</li>
	<li>If the runbook calls any applications, it would be prudent to ensure that they are capable of handling multiple requests at the same time.</li>
	<li>The Returned Data tab (see Figure 7.6) specifies the schema for information returned to the Invoke Runbook activity. Adding values in this tab lets you specify the name and type of data the runbook returns.</li>
	<li>By default, the local group OrchestratorUsersGroup receives Full Control access to the runbook.</li>
	<li>Runbooks contain seven distinct permissions that can be assigned to an individual user or a group</li>
	<li>The real strength of Orchestrator is in sequencing activities to run an entire process, eventually connecting runbooks to orchestrate a series of processes.</li>
	<li>activity properties are not available from the Activity pane. You must first move the activity to the Workspace pane.</li>
	<li>The authors recommend naming the activity with enough detail to indicate the process that is occurring</li>
	<li>You might need to flatten the published data so that you are passing an output only once to the next activity.</li>
	<li>When flattening output, Orchestrator supports using line breaks or separating the items with a specified delimiter (defaulting to a comma). You can also specify that the output use comma-separated values (CSV) format.</li>
	<li>Orchestrator 2012 comes with nine sets of standard activities</li>
	<li>OpsMgr is capable of executing runbooks as a response to a monitoring condition</li>
	<li>More than one unlinked activity results in a multiple starting point error.</li>
	<li>although Orchestrator gives you a warning, it does not prevent the runbook from checking in.</li>
	<li>When the starting point activity is a monitoring activity, the activity waits for a certain condition to occur before continuing to the next activity.</li>
	<li>smart links must connect all activities</li>
	<li>Color-coding links is often useful to indicate different paths that a runbook will take</li>
	<li>Generally, you should arrange the activities in such a way that the runbook flow makes sense visually</li>
	<li>Managing runbooks involves more than knowing how to start or stop a runbook. Understanding how version control works in Orchestrator is also important</li>
	<li>Take time to understand where logs are located both in the console and outside it, how to enable and disable audit logging, and how to increase log verbosity when the standard logs simply do not provide enough information</li>
	<li>If you want a runbook to run on a schedule, such as every 5 minutes, use the Monitor Date/Time activity as the starting point</li>
	<li>Exported runbooks are saved with an extension of OIS_Export</li>
	<li>The export function works only with runbooks that are checked in</li>
	<li>Only already encrypted fields (credentials and so on) are encrypted upon export.</li>
	<li>If you do lose the password to a runbook and decide to import it without the password, you must deselect the Import Orchestrator encrypted data option on the Import dialog box.</li>
	<li>when the Import function is called, the highlighted node is where the import will take place.</li>
	<li>Orchestrator offers a rudimentary system of version control, known as file locking, which prevents more than one user from authoring a runbook at a time</li>
	<li>Because no capability to roll back committed changes exists, the authors strongly recommend that you create a process of exporting runbooks before you make changes. Runbooks should use a naming classification that provides a version number to help track changes</li>
	<li>If you make changes to a runbook and check it in, the audit history shows the activities that were modified.</li>
	<li>Avoid this level except for very short durations, when it is critical to see every operation in the runbook, even those not related specifically to activities.</li>
	<li>Audit logs grow to a size of 200MB before rolling over to a new log file. A datetime stamp is used in the filename to ensure uniqueness.</li>
	<li>Orchestrator does not provide a built-in process for managing these logs through a system of purging or archiving.</li>
	<li>The utility to enable audit logging is a command-line utility only</li>
	<li>Consider drawing, mapping, or diagramming a runbook before you start putting together the workflow. Outlining the process to automate can often take much longer than creating the runbook! Having a well-thought-out outline can save you the frustration of unlinking and relinking activities, as well as adjusting subscriptions to published data.</li>
</ul>
&nbsp;
<h3>Chapter 08: Advanced Runbook Concepts</h3>
<ul>
	<li>a simple schedule controls when a runbook runs, typically by indicating either how often to run or when to run</li>
	<li>The Monitor/Date Time activity adheres to the schedule based on the runbook server’s system clock; it does not operate under Coordinated Universal Time (UTC).</li>
	<li>If you are unsure which condition to use to exit a loop, you can use both. Multiple conditions are treated as OR statements. If both conditions are applied, the loop exits when either one of the conditions is met.</li>
	<li>Looping a runbook properly requires several additional elements:</li>
	<li>Returned data runbook properties</li>
	<li>Return Data activity</li>
	<li>Orchestrator 2012 provides 15 built-in data manipulation functions that allow in-line modification of data or operation using data</li>
	<li>regular expressions are case sensitive</li>
	<li>parameters are not available as the data part of the link filter.</li>
	<li>By default, links are set with success as the only filter. This means that if the object preceding the link returns a success, the runbook continues to the next activity.</li>
	<li>When using link filters, keep in mind that a link cannot use published data from any other activity except for the one to which it is anchored. This means that published data from any preceding activity is not available.</li>
	<li>all link filters should be identified and modified to reflect the right condition to indicate a true success</li>
	<li>Looping properties instruct an activity to retry until a certain condition is met</li>
	<li>Variables behave more like constants; they require you to set the value as a static assignment</li>
	<li>Use variables sparingly because they are global in nature</li>
	<li>Using NOW() As a Variable</li>
	<li>Keep in mind that environment variables are specific to the computer running the runbook</li>
	<li>If an encrypted variable is used inside a password field, Orchestrator automatically decrypts the value.</li>
</ul>
&nbsp;
<h3>Chapter 09: Standard Activities</h3>
<ul>
	<li>Accept Host Key Change: Select this check box to accept host key changes. The authors do not recommend using this option in a production environment. This setting instructs the runbook to accept any change in a server, even malicious changes.</li>
	<li>Message Content in the Send Email Activity</li>
	<li>The authors do not recommend including more than 1MB of information in the message field. If more than 1MB of text is added in the message body, the activity can fail during initialization</li>
	<li>Append Line: Appends a line of text to a text file. The file does not need to exist for this activity to function properly, although the folder must exist.</li>
</ul>
&nbsp;
<h3>Chapter 10: Runbook and Configuration Best Practices</h3>
<ul>
	<li>Establish naming standards for activities, runbooks, folders, variables, and global settings</li>
	<li>always rename your activities to describe their actions. Using short activity names is best; you can use the description field included in each activity to add longer descriptions.</li>
	<li>Naming conventions for runbooks should include a sequence number and short description of what the runbook does</li>
	<li>folder names, incorporating a number and a short description</li>
	<li>The name of each variable should reflect where it is used</li>
	<li>The authors suggest a standard of using orange for links with dependence, green for links that show the normal path, and red to show where the runbook goes in the event of a failure</li>
	<li>well-designed runbook includes links for all possible outcomes from all activities.</li>
	<li>Although you can configure a delay on the links between activities, this is not a recommended approach. Consider the issue: Because links are not listed as steps when the runbook is running, you won’t see a link as a step in the runbook or see the link delay as a step in the history log. Including a Wait or Sleep activity is better. These two activities let you easily see that the runbook is waiting at that action so that you do not think that your runbook has stopped running.</li>
	<li>A best practice is to validate all input data before executing the remaining activities in your runbook. You can perform data validation in a number of ways, such as with the Map Published Data activity, but you also can use link conditions or queries against services</li>
	<li>you should turn off logging in production environments to avoid unnecessary overhead in the Orchestrator database</li>
	<li>When authoring a runbook that will query external systems for input parameters, the authors recommend collecting all required data as the first phase of the runbook.</li>
	<li>When you update a variable with a new value, all activities that use the variable are immediately updated with that new value</li>
	<li>If you have large runbooks, making them modular by dividing them into smaller runbooks is often preferable.</li>
	<li>An alternative approach is to divide your runbooks into smaller, less complicated runbooks and have them triggered from multiple runbooks. This lets you build a library of core runbooks</li>
	<li>Although no hard limit governs the number of activities in a runbook, the authors recommend that you divide runbooks with more than 20 activities into smaller parts.</li>
	<li>Examples of other queries that behave like the Run Program activity include query activities such as Get Computer and Get User. As long as these activities are capable of querying AD, they show a success (green) result. However, the success means that they were able to query AD, not necessarily that they were able to retrieve data.</li>
	<li>Using default settings, each runbook runs on its primary runbook server. If the primary runbook server is offline, the runbook runs on the secondary runbook server</li>
	<li>By default, each runbook server can run a maximum of 50 runbooks at the same time</li>
	<li>The Orchestrator database is a single chokepoint when it comes to performance</li>
	<li>The faster the SQL Server can perform, the better Orchestrator performs</li>
	<li>Database files: Do not place database data files in the same physical drive as the operating system. Place transaction logs and database data files on separate physical drives, and place the TempDB database on its own physical drive. All database files should be placed on physical drives with fault tolerance. Physical drives that together host a logical drive are designed for best performance.</li>
	<li>Database size: Keep your Orchestrator database as small as possible. A small database performs faster and increases performance in general</li>
	<li>Autogrow: As Chapter 4 discussed, do not enable autogrow on the Orchestrator database. Autogrow can fragment your database, affecting performance.</li>
	<li>In addition, if you host the Orchestrator database on SQL Server Standard edition, autogrow can cause the database to lock out. SQL Server Enterprise does not lock the database during autogrow.</li>
	<li>Using autoclose causes queries to take additional time. By default, autoclose is disabled on the Orchestrator database</li>
	<li>Database collation: On the SQL Server instance used to support Orchestrator, the SQL collation setting must be configured for SQL_Latin1_General_CP1_CI_AS. No other collation is supported.</li>
	<li>Database recovery model: To provide the best recovery options, use the default Full Recovery model</li>
	<li>SQL maximum memory: Make sure the SQL Server leaves adequate memory for the operating system</li>
	<li>If the SQL Server is dedicated to Orchestrator, it should be configured to use only Windows Authentication.</li>
	<li>By default, Orchestrator purges runbook logs daily at 1 a.m., keeping the most recent 500 entries in the database</li>
	<li>You can run SQL queries against your Orchestrator database to verify best practices</li>
	<li>An activity is not physically deleted when it is deleted in the Runbook Designer; the activity remains in the OBJECTS database table, marked as deleted.</li>
	<li>develop a runbook that checks the design of all other runbooks in the Orchestrator database</li>
	<li>SELECT OBJECTS.Name AS</li>
	<li>Review your runbooks and update them according to the guidance in this chapter, such as renaming activities to more descriptive names.</li>
	<li>Coauthor and former MVP Anders Bengtsson of Microsoft has written a runbook validator package that is available for download. The package includes several runbooks that check runbook design and output to an HTML-based report file. You can download this package from <a href="http://contoso.se/blog/?p=3573.">http://contoso.se/blog/?p=3573.</a> This package includes a runbook with all the SQL queries used in this section.</li>
</ul>
&nbsp;
<h3>Chapter 11: Security and Administration</h3>
<ul>
	<li>Whereas other System Center components use Run As accounts, Orchestrator can be utilized as a “proxy” layer when running runbooks—that is, an individual with permissions to start a runbook and the input parameters the runbook uses does not require access to the actions the runbook does</li>
	<li>Microsoft’s recommended approach for authentication is using Active Directory, although Orchestrator does not require an Active Directory environment.</li>
	<li>System Center Orchestrator supports encryption; some features are encrypted out of the box, and you can enable encryption for other features as required.</li>
	<li>The only data encrypted by default in Orchestrator is specific data in the Orchestrator database, such as passwords, which are encrypted using Advanced Encryption Standard (AES) 128-bit encryption level and SQL Server cell-level encryption. The Orchestrator installer automatically generates an encryption key during database installation, using a random passphrase.</li>
	<li>Securing the database connection</li>
	<li>For information on encrypting all connections to SQL Server, see <a href="http://msdn.microsoft.com/library/ms191192.aspx.">http://msdn.microsoft.com/library/ms191192.aspx.</a></li>
	<li>You can use Secure Sockets Layer (SSL) to secure connections to the web-based Orchestration console. SSL can also be used to encrypt the connection from the web service to the database. Traffic is encrypted between an administrator’s workstation and the Orchestrator management server by enabling Remote Procedure Call (RPC) encryption</li>
	<li>For information on configuring the Orchestration console and web service to use SSL, see <a href="http://msdn.microsoft.com/en-us/library/hh529160.aspx.">http://msdn.microsoft.com/en-us/library/hh529160.aspx.</a></li>
	<li>To simplify administration, the authors strongly recommend using an Active Directory security group as the Orchestrator Users group.</li>
	<li>The account used to install Orchestrator also has full access to the Orchestrator environment. The authors recommend using a service account instead of a personal user account</li>
	<li>change the Orchestrator Users group after installation, use the PermissionsConfig tool. By default, the tool is located in %ProgramFiles(x86)%Microsoft System Center 2012OrchestratorManagement Server on your Orchestrator management server. For information regarding PermissionsConfig and examples, see <a href="http://technet.microsoft.com/en-us/library/hh463588.aspx.">http://technet.microsoft.com/en-us/library/hh463588.aspx.</a></li>
	<li>The Orchestrator Runbook Service service account is the default account used to execute runbooks.</li>
	<li>This audit trail consists of several text log files that contain information about the type of integration the runbooks are performing with external systems and activities running on the runbook server</li>
	<li>A new log file is created for every 200MB of log data.</li>
	<li>default, log messages are written only when there is an exception in the Orchestrator Management Service; the default folder for the log is %ProgramData%Microsoft System Center 2012Orchestrator</li>
	<li>Orchestrator typically uses three service accounts</li>
	<li>Orchestrator Runbook Service account.</li>
	<li>Orchestrator Management Service account.</li>
	<li>System Center 2012 Orchestrator Web Features application pool identity in IIS</li>
	<li>If all Orchestrator features are installed on the same server, the same account is used for all services</li>
	<li>During the export process, all encrypted data is decrypted from the database and written to the export file; this file is in eXtended Markup Language (XML) format and has an extension of ois_export.</li>
	<li>Sensitive data in the export file is also encrypted, based on the password provided when exporting the runbook</li>
	<li>Before exporting runbooks, verify that they are not checked out</li>
	<li>If you export a runbook that is checked out, you are exporting the current version from the database, not the checked-out version; this means that the version being exported might not be current</li>
	<li>If you do not supply a password, the encrypted data is still exported and is encrypted in the export file. However, the encryption is based on a 0-length string to ensure that sensitive data is not written to the export file in clear text</li>
	<li>Each setting includes all items of that category, so if you export counters, all counters are exported, not just the counters used by the runbooks you export</li>
	<li>If you import an export file that includes an existing variable, a dialog box appears asking whether you want to override the current variable value or create new variables. If you choose to create new global settings, you must update your runbooks; they are not updated automatically</li>
	<li>Orchestrator has two core user roles: Runbook Authors and Runbook Operators. Runbook Authors have administrative access to Orchestrator, including the Orchestrator database and configuration. Runbook Operators can access the Orchestration console and web service</li>
	<li>Push installation of the Runbook Designer console is accomplished using SMB/CIFS. TCP ports 135, 139, 445 and TPC dynamic ports must be accessible on the target computer.</li>
	<li>You also need to enable Windows Firewall rules for WMI and DCOM for any activities that use WMI communication, such as monitoring activities. Read more about using the Windows Firewall with Orchestrator at <a href="http://technet.microsoft.com/en-us/library/hh912321.aspx.">http://technet.microsoft.com/en-us/library/hh912321.aspx.</a></li>
	<li>The authors recommend creating a single Active Directory security group that enables all Orchestrator users to connect the Orchestrator management server and then using specific Active Directory security groups for each team’s permissions.</li>
	<li>All users using the Orchestrator Runbook Designer require Read permissions to the top level of the Runbooks folder</li>
	<li>Publish is the permission that gives users access to start and stop the runbook.</li>
	<li>To automate an IT process, the Orchestrator service account requires the same permissions as the engineers who would be performing that process</li>
</ul>
&nbsp;
<h3>Chapter 12: Orchestrator Integration Packs</h3>
<ul>
	<li>you can specify just the FQDN of the domain and allow DNS to automatically acquire a domain controller based on the site infrastructure (known as a serverless bind). This ensures that the connection will succeed as long as one domain controller is accessible</li>
</ul>
&nbsp;
<h3>Chapter 13: Integration with System Center Operations Manager</h3>
<ul>
	<li>Always test your PowerShell scripts by running them on your Orchestrator server using the x86 version of the PowerShell console or ISE</li>
</ul>
&nbsp;
<h3>Chapter 14: Integration with System Center Service Manager</h3>
<ul>
	<li>runbook activity. This also requires permissions to the Service Manager console and knowledge of how to enter the parameters.</li>
	<li>forward the Service Request ID to the runbook.</li>
</ul>
&nbsp;
<h3>Chapter 15: Integration with System Center Configuration Manager</h3>
<ul>
	<li>NONE</li>
</ul>
&nbsp;
<h3>Chapter 16: Integration with System Center Virtual Machine Manager</h3>
<ul>
	<li>NONE</li>
</ul>
&nbsp;
<h3>Chapter 17: Integration with System Center Data Protection Manager</h3>
<ul>
	<li>NONE</li>
</ul>
&nbsp;
<h3>Chapter 18: Integration with Windows Azure</h3>
<ul>
	<li>NONE</li>
</ul>
&nbsp;
<h3>Chapter 19: Runbook Automation in the Data Center and the Cloud</h3>
<ul>
	<li>NONE</li>
</ul>
&nbsp;
<h3>Chapter 20: The Orchestrator Integration Toolkit</h3>
<ul>
	<li>NONE</li>
</ul>
&nbsp;
<h3>Appendix A: Community Solutions and Tools</h3>
<ul>
	<li>Orchestrator Health Checker is another multipurpose utility with a range of capabilities, including the ability to verify health, audit runbooks, retrieve runbook information, and execute administrative tasks such as purging logs, clearing orphaned runbooks, updating activity passwords, and stopping and starting runbooks. The utility is available at <a href="http://scorch.codeplex.com./">http://scorch.codeplex.com.</a></li>
	<li>Orchestrator Remote Tools is a multipurpose utility providing three useful functions:</li>
	<li>The User Interface (UI) Generator console provides a way to browse available runbooks graphically and generate an eXtended Markup Language (XML) template complete with parameters.</li>
	<li>The Remote Runbook Launcher can launch the runbooks using the XML files created with the UI Generator.</li>
	<li>The Remote Runbook Launcher is also available using a command-line interface.</li>
	<li>You can find this utility at <a href="http://orchestrator.codeplex.com./">http://orchestrator.codeplex.com.</a></li>
	<li>Orchestrator Visio and Word Generator</li>
	<li>If you are need a way to document your runbook without using screenshots or re-creating the runbook layout in Visio, use the Orchestrator Visio and Word Generator utility to easily create a diagram of your runbook</li>
	<li>Parse Orchestrator Export</li>
	<li>This powerful, multifunction graphical utility is designed to provide a range of capabilities, from sanitizing Orchestrator exports to cranking up object-specific logging. Specifically, the utility provides the capability to do the following:</li>
	<li>View exports graphically</li>
	<li>Automatically modify smart links to follow best practices, such as color coding for success and failure</li>
	<li>Modify runbook job concurrency settings en masse</li>
	<li>Enable or disable generic logging</li>
	<li>Enable or disable object specific logging</li>
	<li>Run analysis against runbook exports for common configuration problems</li>
	<li>Rename any runbook, folder, object, and global configuration</li>
	<li>The ParseOrchestratorExport.exe utility is available at <a href="http://scorch.codeplex.com./">http://scorch.codeplex.com.</a></li>
	<li>Utilities Integration Pack</li>
	<li>The Utilities IP contains several activities that can be used to handle a miscellaneous set of tasks, such as retrieving datetime, looking at the subdirectories of a file system, managing registry keys and values, and handling text. The Utilities IP is available at <a href="http://scorch.codeplex.com./">http://scorch.codeplex.com.</a></li>
	<li>Zip Integration Pack</li>
	<li>The Zip IP contains two activities for zipping and unzipping files. The integration pack is available at <a href="http://scorch.codeplex.com./">http://scorch.codeplex.com.</a></li>
	<li>SCCM Client Center Integration Pack for Orchestrator 2012</li>
	<li>Administrators familiar with SCCM Client Center will be happy to hear about this integration pack. The SCCM Client Center IP provides a set of more than 15 different activities to control the Configuration Manager client, supplementing the System Center Configuration Manager IP that contains only a single activity for client management.</li>
	<li>The integration pack is available at <a href="http://sccmclictropalis.codeplex.com./">http://sccmclictropalis.codeplex.com.</a></li>
</ul>
&nbsp;
<h3>Appendix B: Reference URLs</h3>
<ul>
	<li>CodePlex offers community software for Orchestrator, including sample workflows, objects, and code, at <a href="http://orchestrator.codeplex.com/">http://orchestrator.codeplex.com/.</a></li>
	<li>Download the System Center 2012 R2 Orchestrator add-ons and extensions at <a href="http://www.microsoft.com/en-us/download/details.aspx?id=39622.">http://www.microsoft.com/en-us/download/details.aspx?id=39622.</a></li>
	<li>Orchestrator service accounts are discussed at <a href="http://technet.microsoft.com/en-us/library/hh912319.aspx.">http://technet.microsoft.com/en-us/library/hh912319.aspx.</a></li>
	<li>Microsoft’s list of integration packs is at <a href="http://technet.microsoft.com/en-us/library/hh295851.aspx.">http://technet.microsoft.com/en-us/library/hh295851.aspx.</a></li>
	<li>Read about best practices surrounding Orchestrator architecture and runbook deployment at <a href="http://blogs.technet.com/b/privatecloud/archive/2013/05/16/automation-orchestrator-architecture-and-runbook-deployment-process.aspx.">http://blogs.technet.com/b/privatecloud/archive/2013/05/16/automation-orchestrator-architecture-and-runbook-deployment-process.aspx.</a></li>
	<li>Read how to configure the Orchestrator web service to use HTTPS at <a href="http://technet.microsoft.com/en-us/library/hh529160.aspx.">http://technet.microsoft.com/en-us/library/hh529160.aspx.</a> Guidance on requesting and installing a certificate is at <a href="http://support.microsoft.com/kb/299875.">http://support.microsoft.com/kb/299875.</a></li>
	<li>Coauthor Anders Bengtsson of Microsoft has written a runbook validator package discussed in Chapter 10, “Runbook and Configuration Best Practices.” You can download this package from <a href="http://contoso.se/blog/?p=3573.">http://contoso.se/blog/?p=3573.</a></li>
	<li>Download runbook examples for each of the System Center 2012 components at <a href="http://orchestrator.codeplex.com/releases/view/86195">http://orchestrator.codeplex.com/releases/view/86195</a></li>
</ul>
—————————————————————

Don’t forget to check out the following:

<span id="control_gen_2" class="commentary"><strong>CANITPro:</strong> Did you know there is a site dedicated to Canadian IT professionals? You can win a 3D movie prize package by upgrading your IT skills with Microsoft. Check out CANITPRO At The Movies, either in English: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600830" target="_blank">CANITPro At The Movies</a></span><span id="control_gen_3" class="commentary"> or French: <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200600850" target="_blank">CANITPro At The Movies</a></span>

<strong>Azure:</strong> Sign up for a FREE trial and get $200 to spend on <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597585" target="_blank">Microsoft Azure</a> cloud computing services. Full access, no strings.

<span id="control_gen_5" class="commentary"><strong>MSDN:</strong> Ever wanted to work with the latest Microsoft technologies, without having to spend thousands of dollars? Now you can, with the <a href="http://www.microsoft.com/click/services/Redirect2.ashx?CR_CC=200597617" target="_blank">MSDN subscription</a>. </span>
