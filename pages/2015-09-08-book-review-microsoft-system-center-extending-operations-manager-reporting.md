---
layout: page
title: Book Review: Microsoft System Center – Extending Operations Manager Reporting
date: 2015-09-08 10:33
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2015/09/Extending-Operations-Manager-Reporting-Cover-1.jpg"><img class="alignleft wp-image-18991 size-full" src="/wp-content/uploads/2015/09/Extending-Operations-Manager-Reporting-Cover-1.jpg" alt="Extending Operations Manager Reporting Cover" width="201" height="244" /></a>Recently, I finished reading the <a href="http://blogs.msdn.com/b/microsoft_press/archive/2014/12/02/free-ebook-microsoft-system-center-extending-operations-manager-reporting.aspx" target="_blank">Microsoft System Center Extending Operations Manager Reporting</a> eBook.

The chapter(s) that I found most helpful were Chapter 2 "Operations Manager Reporting Basics", and Chapter 9 "Troubleshooting Reporting In Operations Manager".

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: Operations Manager And The Cloud</h3>
<div>
<ul>
	<li>None</li>
</ul>
&nbsp;
<h3>Chapter 02: Operations Manager Reporting Basics</h3>
<div>
<ul>
	<li>For a complete list of reports installed with Operations Manager 2012 R2, see <a href="http://technet.microsoft.com/en-us/library/hh212929.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh212929.aspx</a>.</li>
	<li>If you are unfamiliar with the requirements gathering process and not sure what to ask, the following list of questions provides a good starting point for better understanding what your customer is expecting.
<ul>
	<li>What is the purpose of the report? If you have a better understanding of what the customer is trying to achieve with the report, it will give you a better idea of what data you need to retrieve from the databases.</li>
	<li>What data is required in the report? This question goes hand in hand with the previous one. When you have a good understanding of how the report will be used, you and the customer can discuss what data is available and what should be included in the report.</li>
	<li>Does the report need to cover a specific time span? You should identify whether the customer needs to be able to adjust the date range or if they require a rolling time frame, such as the past 24 hours.</li>
	<li>Does the report require drill-down capabilities? Sometimes a customer wants to drill down to more specific data about a particular object. For example, a customer may want to drill down in a report about exchange servers showing mail flow problems to determine what specific server is having problems.</li>
	<li>How often does the customer want or need the report? This question helps identify the scheduling of the report. Keep in mind that if the customer wants to use a custom date range, it must be manually selected, so the report may not be automatically delivered.</li>
	<li>How should the report be delivered? Operations Manager commonly delivers reports via email or file shares. Always validate email addresses and file share permissions to ensure the customer can receive the report on time.</li>
	<li>What method will be used to make revisions? Should the customer come directly to you, use the in-house change control process, or stop by your desk and request the change? Whatever you decide, be sure to follow up with an email confirming the requests to prevent misunderstanding.</li>
	<li>What languages does the report need to support? Translating reports into other languages is referred to as localizing. This topic is covered further in Chapter 7, “Building management packs for reporting” later in this book.</li>
	<li>Does the report require specific colors or types of charts? Be sure to ask whether the customer wants to see raw data or if they want the data presented as something more visually appealing, such as graphs or charts.</li>
	<li>What are the conditions of satisfaction for the report? This is how the overall report project will be measured. Satisfactory conditions might include that the report runs without error; that the delivery method is acceptable; and that the data is valid and in line with what the customer requires. With this question, you are trying to determine what constitutes completion of the report.</li>
</ul>
</li>
	<li>If the customer wants the report generated automatically, you cannot customize parameters. If the customer wants both customization and automatic delivery, consider creating at least two separate reports: one configured with customer-selected parameters and the other with some agreed-upon parameters.</li>
	<li>For guidance with the installation and configuration of the Operations Manager Reporting Server, go to <a href="http://technet.microsoft.com/en-us/library/hh298611.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh298611.aspx</a>.</li>
	<li>Tip: In some cases, you may want to add additional reports or report libraries to your Operations Manager environment. If you choose to do this, it is very important to remember that these changes will be reflected in the Reporting workspace of the operations console and anyone with Reporting Operator rights will have access to these reports. It is recommended to bundle your custom reports into a management pack file to keep things neatly together and portable.</li>
	<li>If you decide to create your own reports in Operations Manager, it is recommended that you first create a custom folder to store all of your custom reports. You should never edit the default or built-in reports that are supplied within a management pack or any reports provided to you by a vendor. Instead, you should make a copy of the report and store the copy in your custom folder.</li>
	<li>Some examples of the types of reports that customers often want to have regularly scheduled include:
<ul>
	<li>Expiring certificates (monthly)</li>
	<li>Servers with low disk space (daily)</li>
	<li>Servers rebooted overnight (daily)</li>
	<li>SQL Server database space (daily)</li>
</ul>
</li>
	<li>Tip: If Email delivery is missing from the delivery method options; make sure the SMTP settings are properly configured in the Email Settings of your SQL Server Reporting Services Configuration Manager.</li>
	<li>If you need to create additional or custom parameters for your reports, see <a href="http://technet.microsoft.com/en-us/library/gg697751.aspx" target="_blank">http://technet.microsoft.com/en-us/library/gg697751.aspx</a> for helpful guidance.</li>
	<li>Tip: One question that is often asked is what a Null Delivery Provider is and why one would use it. The Null Delivery Provider is a feature of SSRS that allows you to schedule a report to run at a specific time and cache the contents in the ReportServerTempDB. When the customer runs a report, it runs against the cached data which allows the report to generate much more quickly. For example, imagine that you have a report that takes 4 or 5 minutes to run because of the complexity of the query behind it. If you don’t want your customers to have to wait that long for the report to run, you can use the Null Delivery Provider to make the report run faster.</li>
</ul>
&nbsp;
<h3>Chapter 03: Working With Reports</h3>
<div>
<ul>
	<li>It is critical to know when the built-in reports from Operations Manager can be used and when to consider creating custom reports that provide exactly what customers want.</li>
	<li>It is imperative to remember that custom reporting can be time consuming, so it is important to make sure that everyone understands both the cost and the value of the customizations needed</li>
	<li>When considering custom reporting, be sure to weigh the level of effort needed to create the custom report against the urgency of the requirement.</li>
	<li>Note: It is not advised to modify a built-in report from any management pack. The recommended practice is to copy the report file, which is an XML file with the report definition language extension (.rdl), from its original folder within SQL Server Reporting Services to another folder before making any changes. Any modifications to the built-in reports can be lost if the management pack is upgraded.</li>
</ul>
&nbsp;
<h3>Chapter 04: Overview Of Report Authoring Tools</h3>
<div>
<ul>
	<li>The report creation procedures in Operations Manager 2012 have not changed from Operations Manager 2007; therefore, you should refer to the Operations Manager 2007 Report Authoring Guide for guidance, located at <a href="http://technet.microsoft.com/en-us/library/hh528528.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh528528.aspx</a>.</li>
	<li>Refer to the following URL for more information about using Report Builder: <a href="http://technet.microsoft.com/en-us/library/ms159253%28v=sql.105%29.aspx" target="_blank">http://technet.microsoft.com/en-us/library/ms159253%28v=sql.105%29.aspx</a>.</li>
	<li>For installation guidance on configuring your SharePoint environment for using Power View, refer to <a href="http://msdn.microsoft.com/en-us/library/hh231687.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/hh231687.aspx</a>.</li>
</ul>
&nbsp;
<h3>Chapter 05: Authoring Reports In Report Builder</h3>
<div>
<ul>
	<li>Before you create a report in Report Builder, you need to create a data source for pulling the report data. As a best practice, create a specific data source for this instead of using the default DataWarehouseMain data source installed by Operations Manager. Doing so enables you to control the permissions to the custom reports outside of the Operations Manager security model. This means you can allow other users to publish and run reports without adding these users to Operations Manager</li>
	<li>Tip: As a best practice, always target views in your query and not the data tables directly. Dataset data, such as Performance, State, Event, and Alert, are stored in partition tables. The views are automatically updated to retrieve data from the active partitions.</li>
</ul>
&nbsp;
<h3>Chapter 06: Authoring Reports In SQL Server Data Tools</h3>
<div>
<ul>
	<li>Tip: If you use a shared data source, it must be deployed to SSRS, as in the example in Chapter 5. If the shared data source is not deployed, the reports will fail when they are added to SSRS. One way to avoid this problem is to name the data source Data Warehouse Main in the report so that it references the default data source deployed with Operations Manager Reporting. It is a good idea to use a custom name and deploy the data source manually to avoid corrupting or deleting the default data source when custom reports are removed or modified.</li>
	<li>Report Builder, each report is edited as a standalone object while in SSDT a report project can contain multiple reports. When you add data sources or datasets to the Report Data pane in SSDT, they are added from the project and not from an external source. So if a dataset is added to the project as a shared dataset, it is available for any report inside the project.</li>
</ul>
&nbsp;
<h3>Chapter 07: Building Management Packs For Reporting</h3>
<div>
<ul>
	<li>Storing your reports and their dependencies within a management pack is a good practice because it makes your reports flexible and easy to import into other environments</li>
	<li>The Management Pack Authoring Guide on TechNet is a good resource to refresh your knowledge (see <a href="http://technet.microsoft.com/en-us/library/ee957010.aspx" target="_blank">http://technet.microsoft.com/en-us/library/ee957010.aspx</a>).</li>
	<li>Reporting depends on three major sections of the management pack schema:
<ul>
	<li>Presentation</li>
	<li>Reporting</li>
	<li>Language Packs</li>
</ul>
</li>
	<li>There are other elements in the Reporting section that are not discussed in this book. To get more information on these sections and many others, see <a href="http://msdn.microsoft.com/en-us/library/ee533489.aspx" target="_blank">http://msdn.microsoft.com/en-us/library/ee533489.aspx</a>.</li>
	<li>In the v1.1 schema, you paste the install script directly into the Install element. This can be problematic because SQL scripts sometimes include angle brackets (&lt; &gt;), which causes issues with the XML. To deal with this in the v1.1 schema, you can put the SQL query within a CDATA Section &lt;![CDATA[ script goes here ]]&gt;.</li>
	<li>The v2.0 schema addresses this issue by referencing a resource instead. However, referencing an outside file (i.e., a SQL query file) greatly changes the management pack and requires that you create a management pack bundle (.mpb) file</li>
	<li>For localization of the report to work, you need to add a new dataset, along with two additional report parameters and some custom code to the .rdl file.</li>
	<li>Details for using the Operations Manager 2007 R2 Authoring Console are documented on Microsoft TechNet at <a href="http://technet.microsoft.com/en-us/library/ee957010.aspx" target="_blank">http://technet.microsoft.com/en-us/library/ee957010.aspx</a>.</li>
	<li>Note: When inserting data with angle brackets (&lt; &gt;) into XML elements, surround it with the CDATA tag to ensure the data is imported correctly:
Click here to view code image
&lt;![CDATA[ Your data goes here ]]&gt;</li>
	<li>A list of common controls can be found on TechNet at <a href="http://technet.microsoft.com/en-us/library/dd362610.aspx#sectionSection1" target="_blank">http://technet.microsoft.com/en-us/library/dd362610.aspx#sectionSection1</a>. This list refers to Operations Manager 2007 R2, but the controls have not changed.</li>
	<li>Report dependencies define what must be present in the Operations Manager management group for the management pack to import successfully. Configuring report dependencies is not required to store your report in a management pack, but it is a good practice to follow</li>
	<li>After the empty management pack has been created, you can configure the management pack properties, such as the name, whether or not it will be sealed, and deployment options. An article describing this process can be found on TechNet at <a href="http://social.technet.microsoft.com/wiki/contents/articles/5236.visual-studio-authoring-extensions-for-system-center-2012-operations-manager.aspx#Setting_Management_Pack_Properties" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/5236.visual-studio-authoring-extensions-for-system-center-2012-operations-manager.aspx#Setting_Management_Pack_Properties</a>.</li>
	<li>The scripts to create a management pack bundle can be found on TechNet at <a href="http://social.technet.microsoft.com/wiki/contents/articles/15693.operations-manager-management-pack-authoring-management-pack-formats.aspx#Viewing_the_contents_of_a_management_pack_bundle" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/15693.operations-manager-management-pack-authoring-management-pack-formats.aspx#Viewing_the_contents_of_a_management_pack_bundle</a>.</li>
</ul>
&nbsp;
<h3>Chapter 08: Authoring Dashboards In PowerView</h3>
<div>
<ul>
	<li>To expand your reporting even further, you need to consider Business Intelligence (or, BI), specifically Power View.</li>
	<li>For a list of all the current dashboard widgets, see <a href="http://social.technet.microsoft.com/wiki/contents/articles/24133.operations-manager-dashboard-widgets.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/24133.operations-manager-dashboard-widgets.aspx</a>.</li>
	<li>It is strongly recommended that you use views instead of tables because the views abstract the tables in the database</li>
	<li>Remember that when you leverage these columns in a dashboard, the title of the item will match the data source item title exactly. For example, the AlertName column will display as AlertName without a space between the two words. If you want the column title to include a space in the dashboard, you must edit it in the Data Source view.</li>
	<li>You must install Silverlight or the Power View sheet will not load</li>
	<li>You can search many great resources online for help with configuring SharePoint, SQL Server, and Power View to visualize your data. SQL Server 2012 labs are available at <a href="http://www.microsoft.com/en-us/server-cloud/support/learning-center/virtual-labs.aspx" target="_blank">http://www.microsoft.com/en-us/server-cloud/support/learning-center/virtual-labs.aspx</a>, including one titled “Exploring Power View in SQL Server 2012 (SQL 2013).”</li>
</ul>
&nbsp;
<h3>Chapter 09: Troubleshooting Reporting In Operations Manager</h3>
<div>
<ul>
	<li>The Operations Manager SSRS instance cannot be shared with any other products, even other System Center products.</li>
	<li>If you are experiencing problems with a report in a management pack, a good place to begin troubleshooting is in the OperationsManager event log of the management server. As Operations Manager attempts to deploy the report, it logs events in the OperationsManager log.</li>
	<li>Although there could be multiple issues in your report, only the first error will be found during the deployment since the deployment fails immediately upon encountering a problem. This process may need to be repeated multiple times to successfully deploy the report.</li>
	<li>Sometimes, even though a report is successfully deployed and verified with an event 31568 in the OperationsManager log, the report is not visible in the Reporting workspace. This is another common issue with custom management packs for reports. This issue is not necessarily an error, but often happens when the Operations Manager 2007 R2 Authoring Console is used to build a management pack for reporting. In the Report Properties window shown in Figure 9-3, the Visible option is set to False. This is the default value for new reports created in the System Center Operations Manager 2007 R2 Authoring Console. Change this setting to True, reimport the management pack, and the report will be visible.</li>
	<li>Installation issues can still happen, and if an error does occur during installation, SSRS can become corrupt and unusable since Operations Manager changes the permissions to SSRS. This is why Operations Manager reporting cannot share the same SSRS instance as other products, including other System Center products. To minimize issues with SSRS, follow the installation steps on TechNet at <a href="http://technet.microsoft.com/en-us/library/hh298611.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh298611.aspx</a>.</li>
	<li>Before you make any changes to the SSRS account, you should follow the guidance found at <a href="http://msdn.microsoft.com/en-us/library/ms160340(v=sql.110).aspx" target="_blank">http://msdn.microsoft.com/en-us/library/ms160340(v=sql.110).aspx</a>.</li>
	<li>If you need to change the password of the SSRS account, make sure you follow the proper procedures for modifying the Data Reader account, found at <a href="http://technet.microsoft.com/en-us/library/hh457003.aspx" target="_blank">http://technet.microsoft.com/en-us/library/hh457003.aspx</a>.</li>
	<li>If the new reports do not populate the console or the report server within an acceptable amount of time, the Data Warehouse Synchronization Server entry may be deleted.
Another quick way to check for this problem is to run the following Windows PowerShell commands on one of your Operations Manager management servers.
<em>Import-Module OperationsManagerGet-SCOMRule -DisplayName "Data Warehouse component deployment rule" | ft –AutoSize</em>
The above commands parse the Operations Manager rules for the Data Warehouse component deployment rule. The Windows PowerShell command should return results similar to those shown in Figure 9-7. If the command does not return any data, refer to the following Microsoft Knowledge Base article for support guidance at <a href="http://support.microsoft.com/kb/2771934" target="_blank">http://support.microsoft.com/kb/2771934</a>.</li>
	<li>The Data Reader account plays a critical role in Operations Manager reporting functionalities. The Data Reader account is the account SSRS uses to run queries against the Operations Manager data warehouse database. It is a recommended practice to make this account a domain account. The Data Reader account requires logon rights to both the SQL Server nd rights to the Operations Manager management server(s).</li>
	<li>For account-specific permissions, refer to the following TechNet blog posts: Kevin Holman’s post “OpsMgr security account rights mapping - what accounts need what privileges?” at <a href="http://blogs.technet.com/b/kevinholman/archive/2008/04/15/opsmgr-security-account-rights-mapping-what-accounts-need-what-privileges.aspx" target="_blank">http://blogs.technet.com/b/kevinholman/archive/2008/04/15/opsmgr-security-account-rights-mapping-what-accounts-need-what-privileges.aspx</a> and Sergio Carrilho’s post “SCOM 2012 SP1 Security Accounts Matrix” at <a href="http://blogs.technet.com/b/scarrilho/archive/2013/05/02/scom-2012-sp1-security-accounts-matrix.aspx" target="_blank">http://blogs.technet.com/b/scarrilho/archive/2013/05/02/scom-2012-sp1-security-accounts-matrix.aspx</a>.</li>
</ul>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
