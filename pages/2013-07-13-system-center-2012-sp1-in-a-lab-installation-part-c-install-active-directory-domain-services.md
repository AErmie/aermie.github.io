---
layout: page
title: System Center 2012 SP1 in a LAB - Installation (Part C - Install Active Directory Domain Services)
date: 2013-07-13 11:44
author: AdinErmie
comments: true
categories: []
---
<h1>Install Active Directory Domain Services</h1>
Now that we have the VMs created, and the OS installed on both, we need to first install/setup Active Directory (AD).

When you log into a new installation of Server 2012, Server Manager will auto launch. From Server Manager, click on Manage, and choose ‘Add Roles and Features’.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/server-manager-add-role.png"><img class="alignnone size-large wp-image-125" src="http://adinermie.files.wordpress.com/2013/07/server-manager-add-role.png?w=584" alt="Server Manager - Add Role" width="584" height="438" /></a></p>
On the Add Roles and Features Wizard, read the information on the Before You Begin dialog, and then click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-01.png"><img class="alignnone size-large wp-image-77" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-01.png?w=584" alt="Add Roles and Features 01" width="584" height="413" /></a></p>
On the Installation Type screen, select ‘Role-based on feature-based installation’ and then click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-02.png"><img class="alignnone size-large wp-image-78" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-02.png?w=584" alt="Add Roles and Features 02" width="584" height="413" /></a></p>
On the ‘Server Selection’ screen, since we are installed Active Directory on this local system, ensure that it is selected, and click Next. Side note: Windows Server 2012 has a new feature that allows you to remotely install Roles and Features on other systems.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-03.png"><img class="alignnone size-large wp-image-79" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-03.png?w=584" alt="Add Roles and Features 03" width="584" height="413" /></a></p>
On the Server Roles screen, select ‘Active Directory Domain Services’.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-04.png"><img class="alignnone size-large wp-image-80" src="http://adinermie.files.wordpress.com/2013/07/add-roles-and-features-04.png?w=584" alt="Add Roles and Features 04" width="584" height="413" /></a></p>
When you select ‘Active Directory Domain Services’, immediately you will be presented with the following dialog. Click Add Features.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/add-roles-wizard.png"><img class="alignnone size-full wp-image-76" src="http://adinermie.files.wordpress.com/2013/07/add-roles-wizard.png" alt="Add Roles - Wizard" width="430" height="448" /></a></p>
On the Features screen, accept what has already been selected by default, and click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/06-add-roles-features.png"><img class="alignnone size-large wp-image-66" src="http://adinermie.files.wordpress.com/2013/07/06-add-roles-features.png?w=584" alt="06 Add Roles - Features" width="584" height="413" /></a></p>
On the AD DS screen, read the information presented, and click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/07-add-roles-ad-ds.png"><img class="alignnone size-large wp-image-67" src="http://adinermie.files.wordpress.com/2013/07/07-add-roles-ad-ds.png?w=584" alt="07 Add Roles - AD DS" width="584" height="413" /></a></p>
On the Confirmation screen, check the ‘Restart the destination server automatically if required’ checkbox, and then click Install. Note: You are not required to check the ‘restart’ checkbox, however, you’re going to have to restart the system anyways after the installation, so you might as well let the system do it for you.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/08-add-roles-confirmation.png"><img class="alignnone size-large wp-image-68" src="http://adinermie.files.wordpress.com/2013/07/08-add-roles-confirmation.png?w=584" alt="08 Add Roles - Confirmation" width="584" height="413" /></a></p>
Note: When you check off the ‘Restart the destination server automatically if required’ checkbox, you will immediately be prompted with the following dialog. Click Yes.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/09-add-roles-restart.png"><img class="alignnone size-full wp-image-69" src="http://adinermie.files.wordpress.com/2013/07/09-add-roles-restart.png" alt="09 Add Roles - Restart" width="462" height="172" /></a></p>
On the Results screen, click Close.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/10-add-roles-results.png"><img class="alignnone size-large wp-image-70" src="http://adinermie.files.wordpress.com/2013/07/10-add-roles-results.png?w=584" alt="10 Add Roles - Results" width="584" height="413" /></a></p>
After the system restarts, and Server Manager launches, you will have to promote the server as a domain controller. This is because Active Directory has been installed, but that process does not automatically promote the server. Click on the ‘Promote this server to a domain controller’ link.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/server-manager-post-ad-install.png"><img class="alignnone size-large wp-image-126" src="http://adinermie.files.wordpress.com/2013/07/server-manager-post-ad-install.png?w=584" alt="Server Manager - Post AD Install" width="584" height="415" /></a></p>
On the Deployment Configuration screen, select ‘Add a new forest’ since this is the first domain controller in our lab. Then enter a root domain name, and click Next. In my example I am using “SC.LAB” for System Center Lab (since I will be installing all other System Center products in my lab eventually).
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/config-domain-01.png"><img class="alignnone size-large wp-image-86" src="http://adinermie.files.wordpress.com/2013/07/config-domain-01.png?w=584" alt="Config Domain 01" width="584" height="427" /></a></p>
For the Domain Controller Options, select the appropriate Forest functional level, and Domain functional level. This is more applicable if you already have an existing domain and are adding a new domain controller. But since this is the first domain controller in our new domain, then we’ll use the highest level, that of Windows Server 2012. Also, don’t forget to create the Directory Service Restore Mode password. Then press Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/config-domain-02.png"><img class="alignnone size-large wp-image-87" src="http://adinermie.files.wordpress.com/2013/07/config-domain-02.png?w=584" alt="Config Domain 02" width="584" height="427" /></a></p>
On the DNS Options screen, you can ignore this warning message and click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/config-domain-03.png"><img class="alignnone size-large wp-image-88" src="http://adinermie.files.wordpress.com/2013/07/config-domain-03.png?w=584" alt="Config Domain 03" width="584" height="427" /></a></p>
On the Additional Options screen, click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/config-domain-04.png"><img class="alignnone size-large wp-image-89" src="http://adinermie.files.wordpress.com/2013/07/config-domain-04.png?w=584" alt="Config Domain 04" width="584" height="427" /></a></p>
On the Paths screen, normally you would change the location for the database, log files, and SYSVOL, but since we are just in a lab environment, we’ll leave it at the defaults and click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/config-domain-05.png"><img class="alignnone size-large wp-image-90" src="http://adinermie.files.wordpress.com/2013/07/config-domain-05.png?w=584" alt="Config Domain 05" width="584" height="427" /></a></p>
On the Review Options scree, review what you have entered/selected, and click Next.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/config-domain-06.png"><img class="alignnone size-large wp-image-91" src="http://adinermie.files.wordpress.com/2013/07/config-domain-06.png?w=584" alt="Config Domain 06" width="584" height="427" /></a></p>
The Prerequisites Check screen will check and confirm that everything passes before promoting the system as a domain controller. You will notice in my screenshot, that I have 1 warning because I didn’t set a static IP for the server yet.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/config-domain-07.png"><img class="alignnone size-large wp-image-92" src="http://adinermie.files.wordpress.com/2013/07/config-domain-07.png?w=584" alt="Config Domain 07" width="584" height="427" /></a></p>
After installation completes, the system will automatically restart. You will then be presented with the login screen. Something to note here, that because we were originally logged in with a local account, the first time you want to log on using a domain account you will have to type the domainusername; in my example SCAdministrator.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/domain-login.png"><img class="alignnone size-large wp-image-97" src="http://adinermie.files.wordpress.com/2013/07/domain-login.png?w=584" alt="Domain Login" width="584" height="438" /></a></p>
When you login, you will then see in the Server Manager, that AD DS is now listed, along with DNS.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/post-ad-install.png"><img class="alignnone size-large wp-image-123" src="http://adinermie.files.wordpress.com/2013/07/post-ad-install.png?w=584" alt="Post AD Install" width="584" height="438" /></a></p>
Now all that you need to do is assign a static IP to your domain controller.

To do this, in Server Manager, select Local Server from the panel on the left. From there, click on the Ethernet link labelled ‘IPv4 address assigned by DHCP, IPv6 enabled’.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/ad-local-server.png"><img class="alignnone size-large wp-image-71" src="http://adinermie.files.wordpress.com/2013/07/ad-local-server.png?w=584" alt="AD Local Server" width="584" height="438" /></a></p>
This will cause the Networks Connections explorer to open.

From here, right click on the Ethernet network that is displayed. This is in fact the network connection that we configured when we first created the VM.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/connection-properties-01.png"><img class="alignnone size-full wp-image-94" src="http://adinermie.files.wordpress.com/2013/07/connection-properties-01.png" alt="Connection Properties 01" width="575" height="346" /></a></p>
On the Ethernet Properties dialog, select ‘Internet Protocol Version 4 (TCP/IPv4)’ and click the Properties button.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/ethernet-properties.png"><img class="alignnone size-full wp-image-99" src="http://adinermie.files.wordpress.com/2013/07/ethernet-properties.png" alt="Ethernet Properties" width="377" height="475" /></a></p>
Within the Internet Protocol Version 4 (TCP/IPv4) Properties dialog, enter a static IP, gateway, and DNS that is applicable to your network. Once all the items have been entered, click OK. You will also have to click Close on the Ethernet Properties dialog as well.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/ipv4-properties.png"><img class="alignnone size-full wp-image-101" src="http://adinermie.files.wordpress.com/2013/07/ipv4-properties.png" alt="IPv4 Properties" width="414" height="462" /></a></p>
Congratulations, you now have a domain setup in your lab environment.

Here is a video detailing this:

[youtube http://www.youtube.com/watch?v=ODc5lYJTH1Q&amp;w=640&amp;h=480]
<h2>Add Systems to Your Domain</h2>
Now that you have your domain setup, you need to add your other VM (the one that you will use for installing each of the System Center products) to the domain before being able to install the product.

Log into the system you want to add to the domain. To do this in Server 2012, launch Server Manager, and click on Local Server.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/local-server.png"><img class="alignnone size-full wp-image-102" src="http://adinermie.files.wordpress.com/2013/07/local-server.png" alt="Local Server" width="578" height="227" /></a></p>
Then click on the computer name. This will launch the System Properties dialog. From this dialog, click the Change button.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/system-properties-01.png"><img class="alignnone size-large wp-image-156" src="http://adinermie.files.wordpress.com/2013/07/system-properties-01.png?w=584" alt="System Properties 01" width="584" height="438" /></a></p>
From this dialog, select the Domain option for ‘Member of’, and enter the domain name you want to join and press OK.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/system-properties-02.png"><img class="alignnone size-large wp-image-157" src="http://adinermie.files.wordpress.com/2013/07/system-properties-02.png?w=584" alt="System Properties 02" width="584" height="438" /></a></p>
After pressing OK, you are immediately presented with a Windows Security dialog, in which you need to enter the credentials of an account that has Domain Admin rights. Enter the credentials and click OK.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/domain-join.png"><img class="alignnone size-full wp-image-96" src="http://adinermie.files.wordpress.com/2013/07/domain-join.png" alt="Domain Join" width="439" height="311" /></a></p>
Once the system is successfully joined to the domain, you will receive the following Welcome message. Press OK.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/domain-welcome.png"><img class="alignnone size-full wp-image-98" src="http://adinermie.files.wordpress.com/2013/07/domain-welcome.png" alt="Domain Welcome" width="291" height="172" /></a></p>
After you press OK to the Welcome message, you will receive a second prompt, indicating that you need to restart the system for the changes to take effect.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/system-properties-03.png"><img class="alignnone size-large wp-image-158" src="http://adinermie.files.wordpress.com/2013/07/system-properties-03.png?w=584" alt="System Properties 03" width="584" height="438" /></a></p>
You will be back on the System Properties dialog. Press Close.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/system-properties.png"><img class="alignnone size-full wp-image-160" src="http://adinermie.files.wordpress.com/2013/07/system-properties.png" alt="System Properties" width="420" height="475" /></a></p>
When you press Close, you will receive yet another prompt about restarting the system. You can choose to Restart Now or Restart Later, but you won’t be able to install System Center without the VM being added to the domain.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/system-properties-04.png"><img class="alignnone size-large wp-image-159" src="http://adinermie.files.wordpress.com/2013/07/system-properties-04.png?w=584" alt="System Properties 04" width="584" height="438" /></a></p>
After the system restarts, you will then be presented with the login screen. Something to note here, that because we were originally logged in with a local account, the first time you want to log on using a domain account you will have to type the domainusername; in my example SCAdministrator.
<p style="text-align:center;"><a href="http://adinermie.files.wordpress.com/2013/07/domain-login.png"><img class="alignnone size-large wp-image-97" src="http://adinermie.files.wordpress.com/2013/07/domain-login.png?w=584" alt="Domain Login" width="584" height="438" /></a></p>
Now we have our Active Directory server setup and ready, and the VM we will be installing System Center on is joined to the domain.

Here's a video that shows these steps in action:

[youtube http://www.youtube.com/watch?v=RAViM8A2MWA&amp;w=640&amp;h=480]

&nbsp;
<h2>Populate Active Directory With Test Accounts</h2>
If you are like me, you usually rebuild your lab environment continually. But, if you are trying to work through a scenario for a client, or test something out, you need some test accounts in Active Directory to represent multiple users. Instead of creating individual accounts, why not script it? I found the follow <a title="How to use PowerShell to populate Active Directory with plenty enough users" href="http://www.wictorwilen.se/how-to-use-powershell-to-populate-active-directory-with-plenty-enough-users-for-sharepoint" target="_blank">article</a> that uses PowerShell and a list of randomly generated names, to populate Active Directory with 50, 200 User Accounts!

Give it a try if you need many accounts for your environment.

&nbsp;

Now we can move onto installing SQL Server.
