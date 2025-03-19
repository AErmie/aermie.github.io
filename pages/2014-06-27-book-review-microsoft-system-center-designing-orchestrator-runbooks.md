---
layout: page
title: Book Review: Microsoft System Center - Designing Orchestrator Runbooks
date: 2014-06-27 20:18
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2014/06/Designing-Orchestrator-Runbooks-Cover.png"><img class="alignleft size-full wp-image-9961" src="/wp-content/uploads/2014/06/Designing-Orchestrator-Runbooks-Cover.png" alt="Designing Orchestrator Runbooks Cover" width="198" height="244" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2013/09/18/free-ebook-system-center-designing-orchestrator-runbooks.aspx" target="_blank">MSPress Microsoft System Center - Designing Orchestrator Runbooks</a> eBook.

The chapters that I found most helpful were Chapter 4 "Modular Runbook Design And Development", and Chapter 5 "Orchestrator Runbook Best Practices And Patterns", hence the majority of my highlights are from these chapters.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h3>Chapter 01: Introducing System Center 2012</h3>
<ul>
	<li>Orchestration and automation can help reduce the cost of IT while improving consistency and quality of IT service delivery</li>
	<li>Creating what we call “modular automation” where small, focused pieces of automation are progressively built into larger and more complex solutions.</li>
	<li>System Center 2012 is comprised of a suite of components, each focused on part of the infrastructure management lifecycle such as provisioning, monitoring, backup, and disaster recovery</li>
	<li>For heterogeneous environments, VMM can manage both VMware and Citrix XenServer environments in addition to Hyper-V.</li>
	<li>VMM is a key component in establishing private cloud infrastructure as a service (IaaS).</li>
	<li>From an IT process automation perspective, VMM, with its ability to manage compute, network, storage, and virtual resources, backed by hundreds of Windows PowerShell cmdlets, will be one of the most important System Center components utilized by many automated processes.</li>
	<li>Operations Manager has expanded to support monitoring Linux systems as well as network and storage resources.</li>
	<li>Operations Manager is frequently the sources of alerts and events which are the triggers for process automation or Orchestrator runbooks.</li>
	<li>System Center Service Manager deals with the ITIL-based service management and human workflow side of process automation</li>
	<li>Service Manager implements ITIL-based service management processes, such as Incident and Change Management, by enabling a human workflow engine for topics such as help desk ticketing, approvals, and routing</li>
	<li>Backup and disaster recovery are ideal candidates for automation as they require a strict sequence of events, must be tested periodically, and must be executed as quickly and consistently as possible.</li>
	<li>When selecting processes to automate, typically the most repetitive or error prone have the largest ROI, and in many cases those are client device or user related.</li>
	<li>Such as deploying software in certain conditions, or automating the assessment and upgrade of desktop devices</li>
</ul>
<div>

&nbsp;
<h3>Chapter 02: System Center Orchestrator</h3>
<div>
<div>
<ul>
	<li>Orchestrator runbooks are conceptually similar to scripts in that they perform some set of operations in a repeatable manner.</li>
	<li>Where they differ is that Orchestrator runbooks can be created by IT pros without as deep of a background in scripting or programming initially, but can also include script components in more advanced scenarios</li>
	<li>The amount of logging data retained and automatic periodic purging of the logging data (recommended for good console performance) is configured by right-clicking the Orchestrator server at the top of the runbook folder hierarchy and selecting Log Purge.</li>
	<li>To use an integration pack it must be imported and deployed to all of your Orchestrator runbook servers and a connection established between Orchestrator and the target management system (VMM in this example) using a service account with adequate (typically administrator) permissions on the target management system.</li>
	<li>There are some limitations to the Runbook Tester such as only being able to test an individual runbook and not larger or more complex scenarios where multiple runbooks are nested or sequentially executed</li>
	<li>The Runbook Tester executes runbooks under the context of the logged-on user, not under the context of the Orchestrator service account which is used for executing runbooks in production scenarios. In many cases, a runbook may work in the tester but not in production due to differences in permissions between the service account and the runbook author in the tester.</li>
	<li>The Orchestration console is a web-based user interface for initiating and monitoring runbook execution. From this console you can see all running runbooks and their status.</li>
	<li>The OIT enables you to write your own integration packs for systems or applications that don’t have an integration pack but support some form of automation such as web services application programming interfaces (APIs).</li>
	<li>For more information about integration pack development and for other options for building custom solutions with Orchestrator, refer to the “System Center 2012 Integration Guide,” which you can find on Microsoft TechNet at http://social.technet.microsoft.com/wiki/contents/articles/13188.system-center-2012-integration-guide.aspx.</li>
</ul>
</div>
</div>
</div>
<div></div>
<div>
<div>
<h3>Chapter 03: Orchestrator Architecture And Deployment</h3>
<div>
<ul>
	<li>Although the left side of the window shows a similar interface to File Explorer, all runbooks, regardless of how you manage and group them, are stored in the Orchestrator database and not in the file system.</li>
	<li>This component is actually limited to one single management server, so within every Orchestrator environment there can only be one management server</li>
	<li>An Orchestrator 2012 database is hosted on Microsoft SQL Server 2008 or SQL Server 2012 with the basic database engine features, so there is no need for additional features.</li>
	<li>From a high availability perspective we would recommend you to use Failover Clustering and at least two nodes for SQL Server.</li>
	<li>For high availability we recommend you install the Orchestrator web service on multiple IIS servers and use a load balancer to both provide additional capacity as well as continuous web service support in case of a failure of one of your web servers.</li>
	<li>Runbook servers are not designed to run on a cluster node. To achieve high availability in that case, we recommend deploying at least two runbook servers</li>
	<li>There are actually two mechanisms in place that are combined, the “spill over” mechanism helps spread the load of runbook instances across the existing runbook servers.</li>
	<li>The second mechanism will check for the health of a runbook server using a heartbeat signal. As soon as the runbook server is unhealthy (after 3 missed heartbeats, or 45 seconds) the assignment of a runbook instance will be changed to another runbook server.</li>
	<li>By default, each runbook server is configured to run a maximum of 50 runbooks concurrently. You can change that number based on your experience, resource requirements of your runbooks, and the available resources of your runbook servers.</li>
	<li>You can change the default value of 50 to another number by using the runbook server Runbook Throttling tool.</li>
	<li>Configuring a runbook server across a wide area network (WAN) for the purpose of managing devices and/or integrating with systems is not recommended and will result in failures in your runbooks</li>
	<li>Where latency in your network is greater than 30ms, the recommended approach is to configure a dedicated Orchestrator infrastructure in each datacenter and build runbooks that pass data between the datacenters using the Orchestrator web services</li>
	<li>There is only one active management server, with backups/restores another standby management server is kept updated and in case of a datacenter loss, the backup management server can take over.</li>
</ul>
&nbsp;
<div>
<h3>Chapter 04: Modular Runbook Design And Development</h3>
<div>
<ul>
	<li>The system time of the runbook server is utilized for scheduling.</li>
	<li>Access can be granted to users to run, start, stop, view, and change runbooks at either the folder level or the runbook level.</li>
	<li>A runbook executes in the security context of the Orchestrator runbook service service account or if using an integration pack, the account used in the integration pack connection to the target management system.</li>
	<li>A monitor activity, if utilized, must be the first activity in the runbook and any runbooks beginning with a monitor activity must be started in order for the monitoring to be in effect.</li>
	<li>You need to ensure that upon runbook server reboots or other operations that all your runbooks with monitors are started</li>
	<li>You may want to execute a subsequent step on each row of data returned, which Orchestrator lets you do and is one of its most powerful features (parallel execution of multiple runbooks) or you may want to "flatten" the data, and pass all 100 rows of data to the next step as one large published data item</li>
	<li>Runbook can only have one starting point activity. Typically runbooks will utilize an Initialize Data activity or a Monitor activity as the starting point.</li>
	<li>Links include properties which allow you to establish conditional logic</li>
	<li>An activity can have multiple links on its input side and/or multiple links on its output side</li>
	<li>A key design goal of efficient runbooks is relatively small, fast-executing runbooks</li>
	<li>Data from one activity is "published" to the data bus which makes it available to any downstream activities in the runbook.</li>
	<li>The Return Data activity allows you to return data from the current runbook to a runbook that invoked the current runbook.</li>
	<li>Each activity in Orchestrator (other than starting point activities) has both an input side and an output side, as well as a set of properties. Activities can have multiple inputs and outputs. Using just these constructs as well as the general left to right execution flow they encourage, we recommend using a "three rail" design. A "three rail" design is where the center rail performs the main action, audit or notification functions are at the top, and error handling is below.</li>
	<li>The primary functionality of the runbook is contained in the middle rail, proceeding from left to right. Each left to right link contains conditional logic capturing the success conditions required to proceed. All failure conditions, as well as "catch all" conditions for unexpected scenarios, should be captured in links down to the lower, error handling rail.</li>
	<li>Use default black links for success conditions and red links for error conditions</li>
	<li>Where a subsequent step is executed multiple times in parallel, we use a different color and a label to indicate the previous step is returning multiple results which will each execute the subsequent steps in parallel</li>
	<li>The more standard and descriptive the naming (described in later chapters) and the more consistent the usage of the three-rail design, labels, and colors, the easier it will be to maintain a large library of runbooks.</li>
	<li>A key mentality of enterprise runbook design is similar to software development where for each step you need to consider expected success states, expected error states, and unexpected states.</li>
	<li>Nearly every single activity in every runbook has an error path on the output side of the activity.</li>
	<li>The error path is enabled by configuring a link from the given activity to an Invoke Runbook activity which calls a common error handling routine</li>
	<li>The second aspect of our error handling methodology is also critical to runbook portability and reuse and that is that the error path of each runbook activity links to an Invoke Runbook activity which calls a single error handling runbook</li>
	<li>Enable a single location (runbook) where error handling and logging is configured.</li>
	<li>The key concept here is that the error handling runbook functionality is configured in one place only and called by all other runbooks when needed</li>
	<li>Once the error handling runbook has been invoked, the final step of the runbook is a Return Data activity which will return the overall status of the runbook (which in this case would be an error status since the error path was taken).</li>
	<li>The Error path in all runbooks using this framework is an Invoke Runbook activity that calls a separate Error Routine control runbook which contains the desired error logging functionality (such as generate an event log message, create an Operations Manager alert, or create a Service Manager incident).</li>
	<li>Component runbooks are the lowest level and most granular, aligned to the automation layer of management architecture</li>
	<li>Control runbooks are the intermediate tier aligning with the management layer of the architecture</li>
	<li>Initiation runbooks are the top tier of the structure and align to the orchestration and service management tiers of the management architecture</li>
	<li>Component runbooks in our framework are low level, typically single purpose runbooks with no external dependencies.</li>
	<li>They take a set of input parameters, perform an action, then exit with success or failure.</li>
	<li>The difference between a component runbook and an individual activity in Orchestrator is the addition of input parameters, error handling, and multiple output paths.</li>
	<li>Component runbooks, given their low level focus, typically do not include process logic.</li>
	<li>A category (and associated runbook folder) called Computer Management might contain component runbooks for starting, rebooting, or turning off a computer. Other runbooks such as pinging a computer could also be created.</li>
	<li>The purpose of a control runbook is to encode process logic and call appropriate component runbooks to execute functionality.</li>
	<li>An example would be a runbook that first pings a computer to see if it is online, then attempts to check the server to see if a particular process is running on the server and if not, reboot the server. The three individual steps (ping, check for process, and reboot) would be defined as component runbooks.</li>
	<li>The highest level tier is called an initiation runbook. The purpose of an initiation runbook is to call one or more control runbooks which then call one or more component runbooks.</li>
	<li>Separating the method for initiating automation from the automation itself is key to a modular design</li>
	<li>The key to getting the most out of Orchestrator is a structured approach to deciding what processes to automate founded on a return on investment (ROI) methodology.</li>
	<li>The greatest ROI for IT process automation is typically found in areas with high repetition or high complexity requiring a large amount of involvement by IT staff</li>
	<li>In the requirements gathering phase, the following items should be identified and documented:
<ul>
	<li>The process to be automated (for example, . scale-out a web farm)</li>
	<li>The conditions that trigger when the automation should be performed (for example, when transactions per node exceed 1000 transactions/sec)</li>
	<li>The definition of scale out for this process (add another web server virtual machine, deploy the web application, add to load balancer)</li>
	<li>Success validation criteria (for example, requests per node drop to under 1000 transactions/sec)</li>
	<li>Expected failure conditions (for example, web virtual machine fails to deploy, load balancer fails to distribute load)</li>
	<li>How to capture unexpected failure conditions (for example, requests per node fails to drop under 1000 transactions/sec or any individual step in the automation fails)</li>
	<li>Does the process require any human approvals or can it be automated end to end</li>
	<li>What data needs to be logged or traced through the execution of the process</li>
</ul>
</li>
	<li>It is important to optimize processes before automating them</li>
	<li>The existing process should be fully mapped and documented.</li>
	<li>Full understanding and documentation of the current process is critical in both understanding what must be performed as well as identifying areas that can be eliminated or streamlined.</li>
	<li>You can find a sample service map diagram at http://aka.ms/SCrunbook/files.</li>
	<li>The next step is to take the desired process (for example, scale out a web farm based on performance monitoring) and list all of the steps in the current process.</li>
	<li>The new runbook design should contain information about the target functionality, an outline of all the steps included in the runbook, and the layers or products in the infrastructure where those steps must be performed.</li>
	<li>Once the streamlined process has been mapped, the next phase of runbook development can begin which is the documentation of functional specifications for each of the steps in the process (components), the overall process itself (control), and the conditions or triggers for the process (initiation).</li>
	<li>Each low level step of an individual task in the process should be defined as component runbooks.</li>
	<li>The overall workflow or structure of the process should be captured using a control runbook.</li>
	<li>The control runbook would call each component runbook in order and determine whether each was successful or failed and determine the final status of the process.</li>
	<li>With this logical outline in place, each oftherunbooks defined must have a set of functional specifications created sotherunbook authors can create itinOrchestrator. The functional specificationsforrunbooks should contain the following elements:
<ul>
	<li>Name</li>
	<li>Description</li>
	<li>Use cases</li>
	<li>Inputs</li>
	<li>Runbooks utilized (if this is a component runbook this would be blank, for control or initiation runbooks this should list the other runbooks it calls)</li>
	<li>Scripts or code requirements</li>
	<li>Integration packs required</li>
	<li>Variables required or utilized</li>
	<li>Connections to other systems</li>
	<li>Other dependencies</li>
</ul>
</li>
	<li>Since component runbooks represent the bulk of the functionality utilized, they must be created and tested first.</li>
	<li>The control runbook and overall flow should be tested under many different conditions and scenarios</li>
	<li>During the process of development, the runbook functional specifications should be updated with as-built design documentation, diagrams of the runbooks and process flow, and so on.</li>
	<li>The Runbook Tester is critical to the development of component run books (since the Runbook Tester can only test one run book at a time and not follow invokes to other run books).</li>
	<li>It is critical to test many different scenarios and permutations to validate the enterprise readiness of the process being automated</li>
	<li>Many other scenarios should be tested such as multiple simultaneous executions of the process, injection of failure conditions or losses of connectivity, execution of the runbooks while other processes and runbooks are running, and so on</li>
	<li>The goal is to test as many production conditions as possible and to verify not only the success paths through the runbooks but also the failure paths, different triggering conditions, error handling, and logging.</li>
	<li>The recommended folder structure for a runbook library specifies a single root folder containing three additional folders named Component Runbooks, Control Runbooks, and Initiation Runbooks</li>
	<li>Because component runbooks are not bound to any specific scenario, but instead are leveraged by multiple scenarios, it is most effective to organize them into feature-specific runbook collections. For instance, a folder named Firewall should contain all runbooks related to firewall configurations. This approach enables those feature-specific runbooks to be centrally maintained while providing functionality that can be accessed by multiple control runbooks</li>
	<li>Folders should be created within each feature-specific component runbook folder to accommodate each version. Those folders should be named using a major version number that corresponds to the supported platform, and a minor version number that expresses each change made within that platform. For example, the feature-specific Firewall folder should contain a folder named 1.0 to support Windows Server 2008 R2, and a folder named 2.0 for Windows Server 2012</li>
	<li>Additional folders should then be created within each platform-specific folder to accommodate each new version of those runbooks.</li>
	<li>Because control runbooks are bound to a specific scenario, a new folder should be dedicated to each scenario being modeled. For instance, new folders should be created with names like Hyper-V Replica, and Azure VM Provisioning</li>
	<li>A stable release management process is required to avoid breaking existing code while deploying new runbooks.</li>
	<li>To facilitate these goals the following schema will be used: major.minor.revision.build</li>
	<li>Orchestrator does not provide a good means of versioning runbooks</li>
	<li>Orchestrator supports exporting and importing runbooks as xml-notated files which can be stored in TFS for source control. Runbooks can be exported individually, on a folder-level, or the entire folder structure</li>
	<li>In addition to importing and exporting runbooks, the source code for scripts in runbooks, such as Windows PowerShell, can be maintained as source code files as well.</li>
</ul>
&nbsp;
<div>
<h3>Chapter 05: Orchestrator Runbook Best Practices And Patterns</h3>
<div>
<ul>
	<li>When designing runbooks, you should strive to increase readability of the overall flow. In many instances it is a good idea to label links between activities to further explain execution flow without having to look at the link details</li>
	<li>As a design best practice, all error paths should be colored red as shown above and all branching logic should be labeled to indicate what the branch is for.</li>
	<li>Please note that storing execution data will cause more database activity on the Orchestrator database and will increase the size of the database if there are no log-purging settings set up. To set up log purging, from the Runbook Designer, right-click the server name in the leftmost window and choose Log Purge. The Log Purge Configuration dialog box, as shown in Figure 5-9, will open and from there you can set how often you want the logs purged and how much data to retain.</li>
	<li>Be careful using the Do Not Exit rules and make sure any criteria set here does not cause an infinite loop.</li>
	<li>Sequential vs. parallel activity execution: There is a lot of confusion as to whether multiple activations of an activity happen sequentially or in parallel. The bottom line is inside of a single runbook, all activities run sequentially with one exception. The Invoke Runbook activity, when the Wait For Completion check box is cleared, as shown in Figure 5-12, and the child runbook’s job concurrency is set greater than one, allows the child runbook to run in near-parallel for multiple activations. The downside to this though is the inability to capture the result output from these executions.</li>
	<li>MORE INFO For more information on the mechanics of sequential and parallel activity execution, read the blog article at http://blogs.technet.com/b/orchestrator/archive/2012/05/11/sequential-vs-parallel-processing-of-runbook-activities.aspx.</li>
	<li>Job concurrency allows a single runbook to have multiple simultaneous executions when the value is greater than 1.</li>
	<li>The one drawback currently is that Orchestrator runs in a 32-bit process and most Windows PowerShell modules today are written for 64-bit only. To get around this, opening a remote session using Windows PowerShell remoting will allow scripts to run in a 64-bit process.</li>
	<li>All Published Data should be captured at the top of the script and not embedded further into the script to aid readability.</li>
	<li>There are three standard variables that are published from all scripts, which are the ErrorState, ErrorMessage, and Trace variables. ErrorState is an integer that represents success (0), warning (1), error (2), or critical error (3).</li>
	<li>At the beginning of the script we set these variables to their default values as well as clear the built-in Error variable.
<ul>
	<li>$ErrorState = 0</li>
	<li>$ErrorMessage = ""</li>
	<li>$Trace = ""</li>
	<li>$Error.Clear()</li>
</ul>
</li>
	<li>All inputs sent to the remote script should be validated to the extent possible</li>
	<li>Since this script will be making a remote call, establish the remote session with error checking</li>
	<li>Use the Invoke-Command cmdlet to execute the remote script, passing in any input parameters.</li>
	<li>The remote script should be wrapped in a try…catch…finally block to handle any exceptions that occur and to properly close out the Trace variable</li>
	<li>As the remote script runs, append information to the Trace variable that will help in debugging issues in the case of failure. At the beginning of the remote script, write out the input variables for easy reference</li>
	<li>If the script encounters something unexpected that does not throw an error by itself (like getting back a null value from a cmdlet), use the throw keyword to raise exceptions</li>
	<li>At the end of the remote script, if no problems have occurred, set the ErrorState variable to 0. In the case of an exception, inside the catch statement, set the ErrorState to the appropriate value, and then populate the ErrorMessage variable with the exception caught.</li>
	<li>The last step in the remote script is to package up the results into the Results variable as an array and return the Results variable to the calling script</li>
	<li>Close the remote session to free up resources.</li>
	<li>If the Process Group XML Node activity shown in Figure 5-15 processed four items in the loop, then the subsequent activity Populate OM Group (Name) would execute four times</li>
	<li>The following rules are in place to guide the design.</li>
	<li>The runbook performs a simple task without complex business logic. Business logic is the domain for control runbooks.</li>
	<li>The runbook will declare all inputs with the Initialize Data activity.</li>
	<li>If Windows PowerShell scripts are used, the scripts should follow the Windows PowerShell guidelines on making remote calls, error handling, and error / trace reporting defined in the “Using Windows PowerShell in Orchestrator” section.</li>
	<li>Therunbook should publish success / failure by publishing at a minimum,ErrorState,ErrorMessage,TraceRunbook Name, and Activity Name. More information on publishing data can be found in the “Publishing data” section:
<ul>
	<li>The runbook should have the Log Common Published Data setting active. More information can be found in the “Logging execution data” section.</li>
	<li>The runbook should have Job Concurrency set greater than 1. When it is not possible, it should be noted in documentation for future reference as to the reasons Job Concurrency must be set to 1. More information on job concurrency can be found in the “Setting job concurrency” section.</li>
	<li>The runbook will have no dependencies on Orchestrator global variables. All inputs will be defined on the Initialize Data activity.</li>
	<li>The runbook will have no dependencies on other Orchestrator runbooks.</li>
	<li>The runbook will have no dependencies on additional software being installed on the Runbook server outside of IPs.</li>
</ul>
</li>
	<li>Component runbooks are executed using the Invoke Runbook activity where the Wait For Completion property is checked</li>
	<li>Thecontrolrunbook pattern encapsulates the business logic needed and the overall workflow required to perform a complex task.Controlrunbooks are composed of:
<ul>
	<li>An Initialize Data activity</li>
	<li>Optionally, one or more component runbooks</li>
	<li>Optionally, one or more control runbooks since control runbooks can be nested</li>
	<li>Error routine runbooks in case of error</li>
	<li>Other Orchestrator activities</li>
</ul>
</li>
	<li>Rules: The following rules are in place to guide the design.
<ul>
	<li>The control runbook stitches one or more component runbooks together to perform a complex task.</li>
	<li>The runbook can have dependencies on variables. For more information on variables, refer to the “File-based runbook variables” section.</li>
	<li>The runbook should have dependencies on component runbooks.</li>
	<li>The runbook will perform error handling by utilizing a component error handling runbook.</li>
	<li>The runbook will publish an overall ErrorState of success / failure.</li>
	<li>The runbook should have no dependencies on additional software being installed on the Runbook server outside of IPs.</li>
	<li>If Windows PowerShell scripts are used, the scripts should follow the Windows PowerShell guidelines on making remote calls, error handling, and error / trace reporting defined in the “Using Windows PowerShell in Orchestrator” section.</li>
	<li>The runbook should start with an Initialize Data activity to handle any required inputs. Runbooks that start via a Monitor activity are handled as Initiation runbooks.</li>
</ul>
</li>
	<li>The second activity in each control runbook should be a validation script activity that will check if all required parameters are passed in and that the values are not null. Additionally, a range check can be used where appropriate.</li>
	<li>The sole purpose of initiation runbooks is to call control runbooks based on a trigger condition that is initiated by one of the various Orchestrator monitor activities</li>
	<li>Rules: The following rules are in place to guide the design.
<ul>
	<li>The runbook should start with one of the monitor activities followed by a call to a control runbook. The exception to this rule is when the initiation is controlled by System Center Service Manager service requests. This is detailed in the “Service requests initiation runbooks” section later in this chapter.</li>
	<li>The runbook should execute the control runbook without waiting for completion.</li>
	<li>The runbook should only provide error handling if the Monitor activity needs to report on errors.</li>
</ul>
</li>
	<li>The only time error handling should be added to an initiation runbook is when the Monitor activity is not based on date/time and itself could throw an exception. An example would be the Monitor Object activity from the System Center Service Manager IP.</li>
	<li>To properly implement service requests in Service Manager, the request needs to publish the runbook activity ID to a property on the runbook’s Initialize Data activity. This way, if an error occurs, the runbook can set the runbook automation activity to a failed status so that the default error handling will not break the success / failure logic inherent in Service Manager</li>
	<li>Orchestrator global variables present a number of challenges, especially when dealing witharunbook library concept as opposed to a one-off development implementation. These challenges include:
<ul>
	<li>Lack of visibility into runbook dependencies. There is no way to know if a variable value is changed, what runbooks are affected by that change.</li>
	<li>Runbook exports always export all global variables, used or not for the scope of the export. There are CodePlex solutions to strip the unused variables out of export files but this is not supported by Microsoft.</li>
	<li>Multivalued variables are not available. CSV values can be created but are not user-friendly to read or edit.</li>
	<li>In practice, most “global” variables truly only apply to one or a select few runbooks.</li>
</ul>
</li>
	<li>Your runbook automation library (Automation Library) should define a root path for all files in the Orchestrator global variable Runbook Root File Path</li>
	<li>Suggested location would be placing a share on the Orchestrator database server but is by no means a hard requirement.</li>
</ul>
</div>
<div></div>
<h3>Chapter 06: Modular Runbook Example</h3>
<div>
<ul>
	<li>One of the primary benefits of mapping out the optimized, end-to-end process on paper is that it serves as an input to the functional specifications of the runbooks that must be created.</li>
	<li>The control runbooks are where the process logic and state management of the process are contained.</li>
	<li>The reason for this modularity is to support multiple methods of triggering a given process</li>
</ul>
</div>
<div></div>
<h3>Chapter 07: Calling And Executing Orchestrator Runbooks</h3>
<div>
<ul>
	<li>The options for execution include using the Orchestration console, programmatically using the Orchestrator REST application programming interfaces (APIs), and executing runbooks though the System Center Service Manager service catalog.</li>
	<li>Orchestrator currently does not ship with any built-in Windows PowerShell cmdlets but you can make calls to the Orchestrator REST API in a similar fashion</li>
	<li>Making sure to select the Is Ready For Automation check box. If this is not selected, the runbook will not execute.</li>
</ul>
</div>
<div></div>
<div>
<h3>Appendix A: Windows PowerShell Source Code For Core Component Runbooks</h3>
<div>
<ul>
	<li>NONE</li>
</ul>
<div></div>
</div>
</div>
<h3>Appendix B: Steps To Set Up VMM To SM Integration</h3>
<div>
<ul>
	<li>NONE</li>
</ul>
</div>
</div>
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
