---
layout: page
title: Book Review: Secrets Of PowerShell Remoting
date: 2015-04-30 17:02
author: AdinErmie
comments: true
categories: []
---
<a href="http://adinermie.com/wp-content/uploads/2015/07/Secrets-of-PowerShell-Remoting-Cover.png"><img class="alignleft wp-image-15851 size-medium" src="http://adinermie.com/wp-content/uploads/2015/07/Secrets-of-PowerShell-Remoting-Cover-219x300.png" alt="Secrets of PowerShell Remoting Cover" width="219" height="300" /></a>Recently, I finished reading the <a href="https://www.penflip.com/powershellorg/secrets-of-powershell-remoting" target="_blank" rel="noopener">Secrets of PowerShell Remoting</a> eBook.

The chapters that I found most helpful were Chapter 1 “Remoting Basics”, and Chapter 2 "Accessing Remote Computers", hence the majority of my highlights are from this chapter.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 01: Remoting Basics</h2>
<ul>
 	<li>Existing client versions of Windows, such as Windows Vista, do not permit firewall exceptions on any network identified as “Public”. Networks must either be “Home” or “Work/Domain” in order to permit exceptions. In PowerShell 3.0, you can run Enable-PSRemoting with the -SkipNetworkProfileCheck switch to avoid this problem.</li>
 	<li>You can check permissions programmatically with this (whoami /all select-string S-1-16-12288) -ne $null from the PowerShell console. In an elevated shell it True is returned, otherwise False is.</li>
 	<li>Note that Invoke-Command will, by default, communicate with only 32 computers at once. If you specify more, the extras will queue up, and Invoke-Command will begin processing them as it finishes the first 32. The -ThrottleLimit parameter can raise this limit; the only cost is to your computer, which must have sufficient resources to maintain a unique PowerShell session for each computer you’re contacting simultaneously. If you expect to receive large amounts of data from the remote computers, available network bandwidth can be another limiting factor.</li>
 	<li>When you run Enter-PSSession or Invoke-Command and use their -ComputerName parameter, Remoting creates a connection (or session), does whatever you’ve asked it to, and then closes the connection (in the case of an interactive session created with Enter-PSSession, PowerShell knows you’re done when you run Exit-PSSession). There’s some overhead involved in that set-up and tear-down, and so PowerShell also offers the option of creating a persistent connection - called a PSSession. You run New-PSSession to create a new, persistent session. Then, rather than using -ComputerName with Enter-PSSession or Invoke-Command, you use their -Session parameter and pass an existing, open PSSession object. That lets the commands re-use the persistent connection you’d previously created.</li>
 	<li>Once you use New-PSSession and create your own persistent sessions, it is your responsibility to do housekeeping and close and dispose the session when you are done with them. Until you do that, persistent sessions remain active, consume resources and may prevent others from connecting. By default, only 10 simultaneous connections to a remote machine are permitted</li>
 	<li>The practical upshot of this is that Enter-PSSession is really meant for _interactive use by a human being, _not batch use by a script. If you wanted to send a command to a remote computer, from within a script, Invoke-Command is the right way to do it</li>
</ul>
&nbsp;
<h2>Chapter 02: Accessing Remote Computers</h2>
<ul>
 	<li>I don’t recommend using MakeCert.exe, since such a certificate can’t be implicitly trusted by the machines attempting to connect. I realize that every blog in the universe tells you to use MakeCert.exe to make a local self-signed certificate. Yes, it’s easy - but it’s wrong. Using it requires you to shut off most of WinRM’s security - so why bother with SSL if you plan to shut off most of its security features?</li>
 	<li>The “Common Name” is exactly what people will type to access the computer on which this SSL certificate will be installed. That might be “dca,” in our case, or “dc01.ad20082.loc” if a fully qualified name is needed, and so on.</li>
 	<li>The exception isn’t created automatically, so if you have any firewall enabled on your computer, you’ll need to manually create the exception for port 5986.</li>
 	<li>Use the -Concatenate parameter of Set-Item to add your new value to any existing ones, rather than overwriting them</li>
 	<li>There’s a quirk in Windows that tends to strip the Administrator account token for administrator accounts coming in from other domains, meaning they end up running under standard user privileges - which often isn’t sufficient. In the target domain, you need to change that behavior. To do so, run this on the target computer (type this all in one line and then hit Enter): New-ItemProperty -Name LocalAccountTokenFilterPolicy -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System -PropertyType Dword -Value 1 That should fix the problem. Note that this does disable User Account Control (UAC) on the machine where you ran it, so make sure that’s okay with you before doing so.</li>
 	<li>The following configuration changes are needed to enable the second hop: Note: This only works on Windows Vista, Windows Server 2008, and later versions of Windows. It won’t work on Windows XP or Windows Server 2003 or earlier versions. CredSSP must be enabled on your originating computer and the intermediate server you connect to. In PowerShell, on your originating computer, run: Set-Item WSMAN:\localhost\client\auth\credssp -value $true On your intermediate server(s), you make a similar change to the above, but in a different section of the configuration: Set-Item WSMAN:\localhost\service\auth\credssp -value $true Your domain policy must permit delegation of fresh credentials. In a Group Policy object (GPO), this is found in Computer Configuration &gt; Policies &gt; Administrative Templates &gt; System &gt; Credential Delegation &gt; Allow Delegation of Fresh Credentials. You must provide the names of the machines to which credentials may be delegated, or specify a wildcard like “*.ad2008r2.loc” to allow an entire domain. Be sure to allow time for the updated GPO to apply, or run Gpupdate on the originating computer (or reboot it).</li>
 	<li>When running a Remoting command, you must specify the “-Authentication CredSSP” parameter. You must also use the -Credential parameter and supply a valid DOMAIN(you’ll be prompted for the password) - even if it’s the same username that you used to open PowerShell in the first place.</li>
 	<li>Seem tedious and time-consuming to make all of those changes? There’s a faster way. On the originating computer, run this: Enable-WSManCredSSP -Role Client -Delegate name Where “name” is the name of the computers that you plan to remote to next. This can be a wildcard, like *, or a partial wildcard, like *.AD2008R2.loc. Then, on the intermediate computer (the one to which you will delegate your credentials), run this: Enable-WSManCredSSP -Role Server Between them, these two commands will accomplish almost all of the configuration points we listed earlier. The only exception is that they will modify your local policy to permit fresh credential delegation, rather than modifying domain policy via a GPO. You can choose to modify the domain policy yourself, using the GPMC, to make that particular setting more universal.</li>
</ul>
&nbsp;
<h2>Chapter 03: Working With Endpoints (aka Session Configurations)</h2>
<ul>
 	<li>None</li>
</ul>
&nbsp;
<h2>Chapter 04: Diagnostics and Troubleshooting</h2>
<ul>
 	<li>PowerShell v3 and its accompanying implementation of Remoting have much clearer and more prescriptive error messages than prior versions did. However, even v2 included an undocumented and little-appreciated module named PSDiagnostics, which is designed specifically to facilitate Remoting troubleshooting. Essentially, the module lets you turn on detailed trace log information before you attempt to initiate a Remoting connection. You can then utilize that detailed log information to get a better idea of where Remoting is failing.</li>
 	<li>We’re also going to be making use of the Microsoft-Windows-WinRM/analytic log, which does not normally contain human-readable information. In order to utilize the log’s contents, we’ll use an internal Microsoft utility (which we’ve been given permission to distribute; you’ll find it on the Downloads page at http://ConcentratedTech.com) to translate the log’s contents into something we can read.</li>
</ul>
&nbsp;
<h2>Chapter 05: Session Management</h2>
<ul>
 	<li>If you have a session open and close your copy of PowerShell, that session is automatically removed for you - so you’re not leaving anything hanging around that needs to be cleaned up.</li>
</ul>
&nbsp;
<h2>Chapter 06: PowerShell, Remoting, and Security</h2>
<ul>
 	<li>As of Windows Server 2012, PowerShell Remoting is enabled by default and is mandatory for server management. Even when running a graphical management console locally on a server, the console still “goes out” and “back in” via Remoting to accomplish its tasks. Without Remoting, server administration is impossible. Organizations are therefore well-advised to start immediately finding a way to include Remoting in their permitted protocols. Otherwise, critical services will not be able to be managed, even through Remote Desktop or directly on the server console.</li>
</ul>
&nbsp;
<h2>Chapter 07: Configuring Remoting via GPO</h2>
<ul>
 	<li>None<span id="control_gen_5" class="commentary"></span></li>
</ul>
