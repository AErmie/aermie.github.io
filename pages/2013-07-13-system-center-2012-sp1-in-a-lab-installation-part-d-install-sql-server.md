---
layout: page
title: System Center 2012 SP1 in a LAB - Installation (Part D - Install SQL Server)
date: 2013-07-13 11:59
author: AdinErmie
comments: true
categories: []
---
For product specific SQL requirements, please see the <a title="SQL Server&nbsp;Features" href="http://adinermie.com/lab-environment/sql-server-features/">SQL Server Features</a> page.
<h1>Install SQL Server</h1>
At this point, since we will be installing SQL Server on the same server that we will be installing System Center, it is expected that you have the VM created, the OS is installed, the appropriate networking has been configured, and it is joined to your lab domain.

To avoid a specific installation error (see the end of the Install SQL Server section), you have to install the .NET Framework 3.5. So we’re going to complete this first before we start the installation of SQL.
<h2>.NET Framework Installation</h2>
To install the specific version of .NET that we require (version 3.5 in this case), start by launching the Server Manager, and selecting Manager &gt; Add Roles and Features.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/server-manager-add-role.png"><img class="alignnone size-large wp-image-125" alt="Server Manager - Add Role" src="http://adinermie.files.wordpress.com/2013/07/server-manager-add-role.png?w=584" width="584" height="438" /></a></p>
On the Add Roles and Features Wizard, read the information on the Before You Begin screen, and then click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-01.png"><img class="alignnone size-large wp-image-77" alt="Add Roles and Features 01" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-01.png?w=584" width="584" height="413" /></a></p>
<p style="text-align:left;" align="center">On the Installation Type screen, select ‘Role-based or feature-based installation’, and click Next.</p>
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-02.png"><img class="alignnone size-large wp-image-78" alt="Add Roles and Features 02" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-02.png?w=584" width="584" height="413" /></a></p>
On the Server Selection screen, since we are installing SQL on the same server as SCOM, ensure that it is selected, and then click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-03.png"><img class="alignnone size-large wp-image-79" alt="Add Roles and Features 03" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-03.png?w=584" width="584" height="413" /></a></p>
On the Server Roles screen, we are not installing a Role, but rather a Feature, so just click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-04.png"><img class="alignnone size-large wp-image-80" alt="Add Roles and Features 04" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-04.png?w=584" width="584" height="413" /></a></p>
On the Features screen, select .NET Framework 3.5 Features, and click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-05.png"><img class="alignnone size-large wp-image-81" alt="Add Roles and Features 05" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-05.png?w=584" width="584" height="413" /></a></p>
Since in Windows Server 2012 the .NET Framework 4.x is the main framework, the OS installation does not contain the source files for this installation. Therefore, you will need to click on the ‘Specify an alternate source path’ link at the bottom of the dialog.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-06.png"><img class="alignnone size-large wp-image-82" alt="Add Roles and Features 06" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-06.png?w=584" width="584" height="413" /></a></p>
You will need to provide the path to where the source files are. This is found within the installation media of Windows Server 2012. If you insert a DVD or mount an ISO, specify the path to the SxS folder (i.e. D:SourcesSxS), and then press OK.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-07.png"><img class="alignnone size-large wp-image-83" alt="Add Roles and Features 07" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-07.png?w=584" width="584" height="463" /></a></p>
Click Install, and once it has completed, click Close.

<a style="line-height:1.5em;" href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-08.png"><img class="size-large wp-image-84 aligncenter" alt="Add Roles and Features 08" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-08.png?w=584" width="584" height="413" /></a>

Here is a video that shows how to do this:

[youtube http://www.youtube.com/watch?v=gyWdHR_WusU&amp;w=640&amp;h=480]
<h2>SQL Installation</h2>
Start by either extracting or mounting the SQL Server ISO, and run the setup.exe. In this example, we are installing SQL Server 2012 SP1.

On the main installation screen, click on the Installation link on the left pane.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-01.png"><img class="alignnone size-large wp-image-129" alt="SQL Install 01" src="http://adinermie.files.wordpress.com/2013/07/sql-install-01.png?w=584" width="584" height="438" /></a></p>
From the Installation screen, click the ‘New SQL Server stand-along installation or add features to an existing installation’ link.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-02.png"><img class="alignnone size-large wp-image-130" alt="SQL Install 02" src="http://adinermie.files.wordpress.com/2013/07/sql-install-02.png?w=584" width="584" height="438" /></a></p>
This is initiate the installation. First, the Setup Support Rules will check for any issues. As long as there isn’t any ‘Failed’ issues, click OK to continue with the installation.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-03.png"><img class="alignnone size-large wp-image-131" alt="SQL Install 03" src="http://adinermie.files.wordpress.com/2013/07/sql-install-03.png?w=584" width="584" height="438" /></a></p>
Next, enter your product key or select the evaluation copy to install, and press Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-04.png"><img class="alignnone size-large wp-image-132" alt="SQL Install 04" src="http://adinermie.files.wordpress.com/2013/07/sql-install-04.png?w=584" width="584" height="438" /></a></p>
Accept the License Terms and choose if you will send usage data to Microsoft, then press Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-05.png"><img class="alignnone size-large wp-image-133" alt="SQL Install 05" src="http://adinermie.files.wordpress.com/2013/07/sql-install-05.png?w=584" width="584" height="438" /></a></p>
If you have an Internet connection, the installer will check if there are any applicable updates to the installation, and will download the updates to use during the install. Click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-06.png"><img class="alignnone size-large wp-image-134" alt="SQL Install 06" src="http://adinermie.files.wordpress.com/2013/07/sql-install-06.png?w=584" width="584" height="438" /></a></p>
The Setup will perform another Setup Support Rules check. As long as there are no Failures, you can click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-07.png"><img class="alignnone size-large wp-image-135" alt="SQL Install 07" src="http://adinermie.files.wordpress.com/2013/07/sql-install-07.png?w=584" width="584" height="438" /></a></p>
Next is the Setup Role. For our needs, we will choose ‘SQL Server Feature Installation’, then press Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-08.png"><img class="alignnone size-large wp-image-136" alt="SQL Install 08" src="http://adinermie.files.wordpress.com/2013/07/sql-install-08.png?w=584" width="584" height="438" /></a></p>
For the Feature Selection, select the applicable features to install. As a minimum, you will probably need the Database Engine Services (for the database), and the Management Tools - Basic and Complete (to be able to configure SQL). If your specific System Center product has a reporting element, then you will also need the Reporting Services - Native feature.

Check the products documentation for specific SQL Server requirements, make the applicable selections, and then press Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-09.png"><img class="alignnone size-large wp-image-137" alt="SQL Install 09" src="http://adinermie.files.wordpress.com/2013/07/sql-install-09.png?w=584" width="584" height="438" /></a></p>
The Installation Rules will run to determine if anything will block the SQL installation. If there are no Failures, click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-10.png"><img class="alignnone size-large wp-image-138" alt="SQL Install 10" src="http://adinermie.files.wordpress.com/2013/07/sql-install-10.png?w=584" width="584" height="438" /></a></p>
Next we will configure the instance. You can choose either to use a Default instance, or a Named instance. In this example, I will use a named instance, so as to not get this installation of SQL mixed up with any other I will have in my lab. Make your applicable choice, and click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-11.png"><img class="alignnone size-large wp-image-139" alt="SQL Install 11" src="http://adinermie.files.wordpress.com/2013/07/sql-install-11.png?w=584" width="584" height="438" /></a></p>
The setup will check and confirm there is enough space on the drive for the installation. If everything is reported as OK, click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-12.png"><img class="alignnone size-large wp-image-140" alt="SQL Install 12" src="http://adinermie.files.wordpress.com/2013/07/sql-install-12.png?w=584" width="584" height="438" /></a></p>
You next have to configure the server, which includes the Service Accounts and Collation.

In Production, it is best practice to have a separate account for each of the services. In our lab, we will leave everything at defaults, with the exception of changing the ‘SQL Server Agent’ startup type from ‘Manual’ to ‘Automatic’. After you have completed this, don’t click Next, but rather click on the Collation tab.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-13.png"><img class="alignnone size-large wp-image-141" alt="SQL Install 13" src="http://adinermie.files.wordpress.com/2013/07/sql-install-13.png?w=584" width="584" height="438" /></a></p>
On the Collation tab, you will need to click the Customize button to be able to change it appropriately.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-14.png"><img class="alignnone size-large wp-image-142" alt="SQL Install 14" src="http://adinermie.files.wordpress.com/2013/07/sql-install-14.png?w=584" width="584" height="438" /></a></p>
On the Customize dialog, select ‘SQL collation, used for backwards compatibility’.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-15.png"><img class="alignnone size-large wp-image-143" alt="SQL Install 15" src="http://adinermie.files.wordpress.com/2013/07/sql-install-15.png?w=584" width="584" height="410" /></a></p>
Within the list, find ‘SQL_Latin1_General_CP1_CI_AS’ and select it, then click OK.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-16.png"><img class="alignnone size-large wp-image-144" alt="SQL Install 16" src="http://adinermie.files.wordpress.com/2013/07/sql-install-16.png?w=584" width="584" height="410" /></a></p>
You will be back on the Server Configuration dialog, click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-17.png"><img class="alignnone size-large wp-image-145" alt="SQL Install 17" src="http://adinermie.files.wordpress.com/2013/07/sql-install-17.png?w=584" width="584" height="438" /></a></p>
On the Database Engine Configuration screen, leave the Authentication Mode at ‘Windows authentication mode’. What do have to change is to add SQL Server Administrators. Click the Add button.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-18.png"><img class="alignnone size-large wp-image-146" alt="SQL Install 18" src="http://adinermie.files.wordpress.com/2013/07/sql-install-18.png?w=584" width="584" height="438" /></a></p>
On the next dialog, you will need to add either the user(s) or security group(s) you want to have administrator access to SQL. At a bare minimum, add the current user account, so that you can log into SQL Server. Add the user(s)/security group(s), and click OK.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-19.png"><img class="alignnone size-full wp-image-147" alt="SQL Install 19" src="http://adinermie.files.wordpress.com/2013/07/sql-install-19.png" width="471" height="258" /></a></p>
You will be back on the Database Engine Configuration screen, and your accounts will now be present. In my example, I have an Active Directory Security Group I specifically created for SQL Administrators. Then click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-20.png"><img class="alignnone size-large wp-image-148" alt="SQL Install 20" src="http://adinermie.files.wordpress.com/2013/07/sql-install-20.png?w=584" width="584" height="438" /></a></p>
Since we checked off Reporting Services, we are now presented with its configuration. Leave the default ‘Install and configure’ option selected, and click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-21.png"><img class="alignnone size-large wp-image-149" alt="SQL Install 21" src="http://adinermie.files.wordpress.com/2013/07/sql-install-21.png?w=584" width="584" height="438" /></a></p>
You can choose to send Error Reporting information to Microsoft. Make your choice, and click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-22.png"><img class="alignnone size-large wp-image-150" alt="SQL Install 22" src="http://adinermie.files.wordpress.com/2013/07/sql-install-22.png?w=584" width="584" height="438" /></a></p>
The setup will now re-check the configuration rules, based on the selections and information that has been supplied. If it passes, click Next.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-23.png"><img class="alignnone size-large wp-image-151" alt="SQL Install 23" src="http://adinermie.files.wordpress.com/2013/07/sql-install-23.png?w=584" width="584" height="438" /></a></p>
Review the information on the Ready To Install screen, and then click Install.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-24.png"><img class="alignnone size-large wp-image-152" alt="SQL Install 24" src="http://adinermie.files.wordpress.com/2013/07/sql-install-24.png?w=584" width="584" height="438" /></a></p>
Note: during the installation, you may encounter the following error message. This is due to not having the .NET Framework 3.5 installed prior to attempting to install SQL Server. If you encounter this, cancel the SQL server installation, and install the .NET Framework 3.5 (which is an available feature within Roles and Features).
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-error-01.png"><img class="alignnone size-large wp-image-155" alt="SQL Install Error 01" src="http://adinermie.files.wordpress.com/2013/07/sql-install-error-01.png?w=584" width="584" height="173" /></a></p>
You may have to wait a while for the Installation Progress to complete.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-25.png"><img class="alignnone size-large wp-image-153" alt="SQL Install 25" src="http://adinermie.files.wordpress.com/2013/07/sql-install-25.png?w=584" width="584" height="438" /></a></p>
On the Complete screen, click Close.
<p align="center"><a href="http://adinermie.files.wordpress.com/2013/07/sql-install-26.png"><img class="alignnone size-large wp-image-154" alt="SQL Install 26" src="http://adinermie.files.wordpress.com/2013/07/sql-install-26.png?w=584" width="584" height="438" /></a></p>
Congratulations, you now have SQL Server installed and are finally ready to install System Center.

Here is a video I created that walks through these steps:

[youtube http://www.youtube.com/watch?v=jOb0bAL4yz4&w=640&h=480]
