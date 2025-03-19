---
layout: page
title: Book Review: Exam Ref 70-744 Securing Windows Server 2016
date: 2017-02-13 08:43
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2017/02/70744Cover.jpg"><img class="alignleft wp-image-27741 size-medium" src="/wp-content/uploads/2017/02/70744Cover-247x300.jpg" width="247" height="300" /></a>Recently, I finished reading the <a href="https://www.microsoftpressstore.com/store/exam-ref-70-744-securing-windows-server-2016-9781509304264" target="_blank">Exam Ref 70-744 Securing Windows Server 2016</a> eBook.

<span style="color: #000000;">The chapter(s) that I found most helpful were basically all of them! </span>Hence the majority of my highlights are from basically the entire book. Note that I didn't just highlight all of the "Exam Tip" content, but also additional information that I found useful in learning and understanding the topic.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h3>Chapter 01: Implement Server Hardening Solutions</h3>
<ul>
 	<li>To be effective, BitLocker Drive Encryption must be deployed alongside the IT security
principle of least privilege. This means that server operators should be able to access only
those resources that they need to do their jobs.</li>
 	<li>Any new server hardware you purchase nowadays uses UEFI firmware. Windows Server 2016 fully supports all UEFI features, especially Secure Boot.</li>
 	<li>Secure Boot is a UEFI feature that protects the server’s startup environment. The UEFI firmware stores a database of trusted hardware, drivers, operating systems, and option ROMs.</li>
 	<li>In short, your server starts up only if its operating system boot loader files and device drivers are digitally signed and trusted by the Secure Boot database.</li>
 	<li>Windows Server 2016 supports both the current-generation TPM v1.2 as well as the original TPM 1.0 specification. An often-confused point about TPM is its relationship to Secure Boot. Technically, TPM can provide the same type of boot-time protection that UEFI Secure Boot can. However, the two systems are separate and rely upon separate trust stores.</li>
 	<li>EXAM TIP
We must always remember why we enable controls such as Secure Boot and TPM security; namely, to prevent the injection of unauthorized boot code that can compromise our servers. Microsoft certification exams tend to put more emphasis on the “why” rather than the “how,” although we do need to understand how to configure security controls in order to conquer the 70-744 certification exam.</li>
 	<li>Specifically, the BCD is a firmware-independent database that stores Windows startup
configuration data. In Windows Server 2016, the BCD is located on the unlettered, 500 MB
System Reserved partition on your startup disk.</li>
 	<li>You may get better performance and reliability configuring your Windows Server 2016 servers to use Secure Boot for BCD verification because, at least in my experience, benign changes to the BCD can sometimes trigger BitLocker Recovery</li>
 	<li>As you probably expect, we use Group Policy to specify our server BitLocker Drive Encryption policy. The policy in question is called Require Additional Authentication At Startup, and it’s located in the same GPO path we used earlier: Computer Configuration\Policies\Administrative Templates\Windows Components\BitLocker Drive Encryption\Operating System Drives.</li>
 	<li>Although it’s certainly not recommended, you can configure Windows Server 2016 to use
BitLocker without TPM protection.</li>
 	<li>Network Unlock allows automatic access to BitLocker decryption keys, which means that you can start, restart, or remotely manage (perhaps via Wake on LAN) your Windows Server 2016 servers without the manual intervention required by the PIN protector method.</li>
 	<li>NEED MORE REVIEW? GET FAMILIAR WITH NETWORK UNLOCK
The 70-744 exam objectives require only that we understand the basics of BitLocker
Network Unlock. For a deeper, step-by-step treatment, see the TechNet article “Bit-
Locker: “How to Enable Network Unlock” at <a href="https://technet.microsoft.com/en-us/library/" target="_blank">https://technet.microsoft.com/en-us/library/</a>
jj574173(v=ws.11).aspx#BKMK_NUnlockCoreReqs.</li>
 	<li>NOTE: OTHER CAUSES OF BITLOCKER RECOVERY MODE
Forgetting a PIN or unlock password is only one of a few reasons why BitLocker may enter
Recovery mode. Changing the boot order in UEFI/BIOS setup also triggers Recovery mode. Microsoft suggests putting your server’s operating system drive first in the boot order to avoid this issue. Other reasons include creating, deleting, or resizing a primary partition, disabling the TPM chip, upgrading the UEFI firmware itself, and installing or removing certain hardware devices.</li>
 	<li>Any server on which you enable BitLocker stores its recovery password and possibly its encryption keys in Active Directory. One gotcha: this Group Policy change doesn’t affect servers that already use BitLocker.</li>
 	<li>NOTE ARCHIVING TPM TO AD DS</li>
 	<li>Conveniently, Windows Server 2016 allows us to archive TPM data to Active Directory Domain Services as well. In Group Policy Editor, navigate to Computer Configuration\Policies\Administrative Templates\System\Trusted Platform Module Services and enable the policy Turn On TPM Backup To Active Directory Domain Services.</li>
 	<li>By default, EFS generates self-signed certificates and stores them in each user or administrator’s profile folder. This is a bad idea in production because:
<ul>
 	<li>The EFS encryption keys can be stolen or damaged</li>
 	<li>There’s no trust chain with self-signed certificates</li>
</ul>
</li>
 	<li>Therefore, if you plan to implement EFS in your enterprise, you should have a “true blue”
public key infrastructure (PKI) established, preferably with Active Directory Certificate Services (AD CS) so you can fully manage EFS certificates. After all, AD CS includes Basic EFS and EFS Recovery Agent certificate templates out of the box.</li>
 	<li>NEED MORE REVIEW? DIGGING DEEPER WITH WSUS
If you’d like more planning/architectural details on WSUS, as well as a step-by-step installation and configuration tutorial, consider reading the TechNet whitepaper series “Deploy Windows Server Update Services in Your Organization” at <a href="https://technet.microsoft.com/en-us/library/hh852340%28v=ws.11%29.aspx?f=255&amp;MSPPError=-2147217396" target="_blank">https://technet.microsoft.com/en-us/library/hh852340%28v=ws.11%29.aspx?f=255&amp;MSPPError=-2147217396</a>.</li>
 	<li>The “gotcha” regarding WSUS reports is that you need to install the Microsoft Report Viewer 2012 Runtime and the system CLR types from the SQL Server 2012 SP1 Feature Pack before you can actually view these reports.</li>
 	<li>NEED MORE REVIEW?
WSUS TROUBLESHOOTING GUIDANCE FROM MICROSOFT
Given how much TechNet documentation exists for troubleshooting WSUS, I would guess that Microsoft has fielded quite a few WSUS-related support incidents over the years. Perhaps the most comprehensive guide for you to start with is the TechNet wiki library “WSUS Troubleshooting Survival Guide” at <a href="http://social.technet.microsoft.com/wiki/contents/articles/2491.wsus-troubleshooting-survival-guide.aspx" target="_blank">http://social.technet.microsoft.com/wiki/contents/articles/2491.wsus-troubleshooting-survival-guide.aspx</a>.</li>
 	<li>NOTE
WINDOWS DEFENDER VS. SYSTEM CENTER ENDPOINT PROTECTION
In consulting the Microsoft literature, you’ll find references to Windows Defender and System Center 2012 Endpoint Protection (SCEP). The presence of these two nearly identical applications causes some confusion for some Windows administrators. In a nutshell, here are the facts: while Windows Defender and SCEP share the same code base, their use cases are different. Windows Defender is technically a stand-alone application, even on servers, while SCEP is used in conjunction with centralized antimalware management via System Center Configuration Manager.</li>
 	<li>NOTE
WINDOWS DEFENDER VS. MICROSOFT SECURITY ESSENTIALS
In your Windows Server 2016 WSUS console, don’t be surprised if you see some of your
Windows Defender definition updates listed as Definition Update for Microsoft Security Essentials. Microsoft Security Essentials (MSE) is the older (Windows 7-compatible) version of today’s Windows Defender antimalware engine. Both applications use the same definition update files.</li>
 	<li>AppLocker is the successor to the old Software Restriction Policies introduced in Windows
Server 2003. AppLocker, like BitLocker or any security application, presupposes the principle of least privilege.</li>
 	<li>NOTE
LEAST PRIVILEGE AND STANDARD USER ACCOUNTS
An easier (but not easy) way to limit the introduction of installed malware on your network is to ensure that all users and admins operate their computers under standard user identities. Thus, any software installer that requires administrative elevation simply fails. Two issues with this approach are (a) some software installers allow standard users to install their product in, say, the user’s profile folder; and (b) you have to be an administrator to log onto a Windows Server computer.</li>
 	<li>NEED MORE REVIEW?
DEEP-DIVE INTO APPLOCKER DESIGN AND IMPLEMENTATION
The 70-744 exam doesn’t deal with AppLocker basics, instead opting to jump into the proverbial “deep end of the pool” with configuring AppLocker rules. To gain a more fundamental knowledge of AppLocker, consider reading the excellent TechNet white paper series “AppLocker Deployment Guide” at <a href="https://technet.microsoft.com/en-us/itpro/windows/keep-secure/applocker-policies-deployment-guide" target="_blank">https://technet.microsoft.com/en-us/itpro/windows/keep-secure/applocker-policies-deployment-guide</a>.</li>
 	<li>Control Flow Guard (CFG) is a developer-focused feature which remediates against memory corruption vulnerabilities. If application data in server RAM were to break, a vulnerability could be exposed that makes it possible for an attacker to steal sensitive data from memory.</li>
 	<li>EXAM TIP
Microsoft has a free tool called Enhanced Mitigation Experience Toolkit (EMET) that allows
administrators to tweak DEP and ASLR settings. EMET also includes built-in application
profiles that remediate against low-level vulnerabilities in certain software applications
such as Adobe Acrobat and the Internet Explorer browser.</li>
 	<li>The first thing you should understand about Device Guard is that it isn’t a single Microsoft
product. Instead, Device Guard is a collection of security-related hardware and software
features that, when implemented together, fully protects the server’s executable environment.</li>
 	<li>Device Guard is the ultimate extension of application whitelisting. If any component of a
system firmware, installed operating system, device drivers, or application does not exist on the system’s code integrity policy whitelist, then the system won’t start or the application
won’t run, period.</li>
 	<li>Device Guard is aimed only at mission-critical servers with stable workloads. Also, as of this writing Device Guard is extremely difficult to manage because every change requires a reboot and Microsoft hasn’t yet released user-friendly tooling.</li>
 	<li>Virtualization-Based Security (VBS) employs the Hyper-V hypervisor to protect the operating system kernel and other potentially vulnerable components.</li>
 	<li>VBS does have hardware requirements, particularly 64-bit processors with CPU virtualization extensions and Second-Level Address Translation (SLAT) support. Your system firmware, as I’m sure you’d expect by now, must use UEFI v2.3.1c or higher with UEFI Secure Boot enabled.</li>
 	<li>NOTE
DEVICE GUARD INTEGRATION
Device Guard is one of several technologies that rely upon the Hyper-V hypervisor to virtualize and protect critical system files and volatile memory. At first blush, Device Guard may remind you of AppLocker, at least in terms of its focus on application whitelisting. The Microsoft best practices are in flux on this subject, but as of this writing they suggest using Device Guard for your most restrictive application whitelisting, and consider AppLocker for fine-tuning code execution/application restrictions in your organization.</li>
 	<li>Note that a Windows Server 2016 or Windows 10 computer can have only one code integrity policy at a time; this means that you’ll be spending perhaps the majority of your time testing and tweaking your code integrity policies to get them right at deployment time.</li>
 	<li>Microsoft best practice suggests that you use a public or Active Directory Certificate Services (AD CS) code-signing certificate to sign your code integrity policies.</li>
 	<li>You can store your application whitelisting exceptions in catalog files and Device Guard whitelists the catalog entries the same way it does with ordinary signed code.</li>
 	<li>You use the PackageInspector.exe command-line tool, which is included by default in Win-
dows Server 2016, to create catalog files for your unsigned apps.</li>
 	<li>NOTE
DERIVED CREDENTIALS
If you check the Microsoft TechNet literature, you’ll see references to “derived credentials,”
and an explanation of how Credential Guard protects them. According to the National Institute of Standards and Technology (NIST), derived credentials refers to cryptographic identities (usernames and password hashes, most commonly) that are cached on a mobile device. For our purposes, we can consider domain derived credentials as the NTLM hashes and/or Kerberos tickets that Windows caches by default in the user-mode LSASS process.</li>
 	<li>You need to run Windows 10 Enterprise Edition if you plan to enable Credential Guard on Windows Client systems.</li>
 	<li>Credential Guard Configuration: If you choose Enabled Without Lock, then Credential Guard can be disabled remotely via Group Policy. If you choose Enabled With UEFI Lock, then Credential Guard can be disabled only via interactive logon and never remotely.</li>
 	<li>Here’s the list of stored credentials and attack types that are unaffected by Credential Guard status:
<ul>
 	<li>Local accounts and Microsoft accounts (Credential Guard pertains to on-premises Active Directory domain credentials only)</li>
 	<li>Third-party credential management software</li>
 	<li>Key loggers</li>
 	<li>Physical attacks</li>
 	<li>Malware that leverages the currently logged on user’s credentials (another argument in favor of implementing least privilege always)</li>
 	<li>Digest and CredSSP credentials</li>
</ul>
</li>
 	<li>We must remember that NTLM, especially NTLM vX, is an old, flawed protocol that doesn’t contribute to acceptable authentication security in most 21st century IT environments.</li>
 	<li>NTLM blocking is nothing more than preventing NTLM from being used for authentication in your domain, period.</li>
 	<li>According to Microsoft documentation and best practices, it typically takes a business at
least six months of testing before “pulling the trigger” on production NTLM blocking.</li>
 	<li>Microsoft publishes a free tool called Security Compliance Manager (SCM). SCM is a solutions accelerator that simplifies the analysis, creation, comparison, and deployment of Group Policy-based security templates.</li>
</ul>
&nbsp;
<h3>Chapter 02: Secure a Virtualization Infrastructure</h3>
<ul>
 	<li>We recommend that you deploy at least three physical or virtual HGS servers to provide
high availability. The reason for this is simple: you won’t be able to work with any shielded
VMs unless the HGS cluster is available.</li>
 	<li>Each HGS server becomes a domain controller in a new, separate, “safe harbor” Active Directory Domain Services (AD DS) forest. For this reason, your hosts need to be configured for workgroup networking and not be a member of any other AD domain.</li>
 	<li>You’ll also observe that PowerShell installs the Active Directory Domain Services, Failover Clustering, Web Server, and BitLocker Drive Encryption server roles or features in the bargain.</li>
 	<li>HGS makes use of Representational State Transfer (REST) application programming interfaces (APIs) to perform the attestation and key transfer operations. That’s why the IIS Web Server was installed when you set up your HGS cluster.</li>
 	<li>NOTE MANAGING THE HOST GUARDIAN SERVICE IN THE ENTERPRISE
If you think all this system-by-system PowerShell configuration is tedious, you’re certainly
not alone. The good news is that Microsoft is building HGS-aware tooling into both System
Center 2016 Virtual Machine Manager (SCVMM) as well as Azure Stack to manage HGS
clusters and shielded VMs.</li>
 	<li>The process of shielding an existing VM is called grandfathering by Microsoft.</li>
 	<li>NOTE
GENERATION 1 NEED NOT APPLY
The Host Guardian Service can work with only Generation 2 virtual machines that use the
.VHDX virtual hard disk file format. Generation 2 VMs are required to support UEFI firmware and virtual TPM, among other features.</li>
 	<li>Because Microsoft Azure supports only Generation 1 .VHD VMs, Host Guardian Service does not work in Azure. This is likely to change, given that the Azure development team ships several new features every single business day.</li>
 	<li>Because you won’t get console access to the VM once it becomes shielded, it’s crucial that you prepare the unshielded VM beforehand. This involves setting appropriate rules in Windows Firewall, configuring WSMan remote management, and (most importantly) enabling BitLocker Drive Encryption on the VM’s virtual hard drive.</li>
 	<li>A shielded virtual machine is a Generation 2 Hyper-V virtual machine running Windows Server 2012 R2, Windows Server 2016, or Linux that uses a variety of current-generation technologies, including virtualization based security (VBS) and BitLocker Drive Encryption</li>
 	<li>NOTE
DID YOU SAY WINDOWS SERVER 2012R2? AND LINUX?
Windows Server 2012 R2 supports Generation 2 VMs, so you can deploy Windows Server 2012 R2–based shielded virtual machines on Windows Server 2016 Hyper-V hosts. Although the documentation is sketchy as of this writing, Windows Server 2016 supports Linux-based Hyper-V shielded VMs as well. Linux supports TPM, UEFI, and Secure Boot, but not BitLocker Drive Encryption. To that end, Microsoft plans to employ the dm-crypt disk encryption subsystem to provide whole-disk encryption for Linux-based shielded VMs.</li>
 	<li>NOTE
THE EVER-VOLATILE NATURE OF WINDOWS
Don’t be surprised if you try the Protect-ServerVHDX command on your Windows Server 2016 server and receive an error from the PowerShell engine. This cmdlet could very well be renamed to Protect-TemplateDisk. You could see a similar shift from the Protect-ShieldingDataFile cmdlet to its supposed, eventual New-ShieldingDataFile replacement. We need to keep in mind that today’s rapid development/continuous delivery IT service model means that what’s true today with Microsoft technology can be renamed (at the least), or removed or replaced (at the worst), with minimal advance notice from the Microsoft development teams.</li>
 	<li>EXAM TIP
Microsoft is infamous for spontaneously and repeatedly changing product and technology names. On the 70-744 exam you could see references to Virtual Secure Mode (VSM), Isolated User Mode (IUM), or Virtualization-Based Security (VBS). These acronyms all mean the same thing.</li>
 	<li>The good news is that the VM’s vTPM is as portable as the rest of the VM. This means that your shielded VMs remain protected even when their data is transmitted over the network.</li>
 	<li>Each Hyper-V VM runs as a worker process named vmwp.exe on the host. Shielded VMs have “hardened” VM worker processes that prevent illicit tampering from fabric administrators; for instance, attaching a debugger to the process.</li>
 	<li>The Microsoft Datacenter and Private Cloud Security team put up a blog post called “Step by Step - Shielded VM Recovery (http://timw.info/svm) that cleverly takes advantage of the nested virtualization feature of Windows Server 2016 Hyper-V to get around the console access problem.</li>
</ul>
&nbsp;
<h3>Chapter 03: Secure a Network Infrastructure</h3>
<ul>
 	<li>As a general security best practice, you should change as many default port assignments as possible to improve your servers’ security posture. If you do this with SQL Server, however, you need to define SQL Server aliases to reflect the non-standard port assignment.</li>
 	<li>Sometimes after a server restart, you find the server’s network connection (or connections) revert from “Domain” to “Private.” You can correct this problem and force the domain profile with three lines of Windows PowerShell:
$profile = Get-NetConnectionProfile -InterfaceAlias 'Ethernet0'
$profile.NetworkCategory = 'DomainAuthenticated'
Set-NetConnectionProfile -InputObject $profile</li>
 	<li>NOTE BE CAREFUL WITH WINDOWS FIREWALL RULES IMPORT
When you import a .wfw file into Group Policy, any rule configuration you might have
performed to that point is completely overwritten. You’ve been warned!</li>
 	<li>NOTE IPSEC AND NETWORK OVERHEAD
Some administrators won’t consider implementing IPSec policies on their LANs due to the mistaken assumption that IPSec slows down network performance with all its security overhead. While it’s true that ESP adds minimal overhead to LAN traffic, you need to ask yourself if data encryption between internal hosts is truly what you need. If authenticated communication is your goal, then you can simply enable AH and experience no additional overhead at all.</li>
 	<li>NOTE IPSEC EXEMPTION
We just saw a policy called Allow Authenticated IPSec Bypass that whitelists one or more
domain computers with Windows Firewall. Don’t get confused between this policy and the
IPSec connection security rule type Authentication exemption. This latter policy is used to
exempt servers from IPSec authentication, not Windows Firewall.</li>
 	<li>EXAM TIP
We see in this section a discrepancy between “Distributed firewall” and “Data center firewall.” The fact that Microsoft seemingly changes its product names on a whim can be reflected in your 70-744 exam. Therefore, you should be prepared to see references to product names that have since been changed. That means the onus is on you to keep current with your Microsoft technology news to keep abreast of these many (often spontaneous) name shifts.</li>
 	<li>NOTE PLANNING AN SDN INFRASTRUCTURE
Planning for SDN involves purchasing hardware that is optimized not only for performance
but also for the heavy abstraction and access control involved. This subject is far outside
this book’s scope, so we want to draw your attention to the excellent Microsoft TechNet
article “Plan a Software Defined Network Infrastructure” at <a href="http://timw.info/sdn" target="_blank">http://timw.info/sdn</a>.</li>
 	<li>In Azure terminology, the Network Security Group (NSG) is a firewall that granularly allows or blocks traffic to a particular virtual machine. Windows Server 2016 Datacenter Firewall uses the older term “access control list” but for the same purpose: we apply Datacenter Firewall ACLs to individual virtual network interfaces, or to virtual networks.</li>
 	<li>Notice the new virtual switch extension called Windows Azure Virtual Filtering Platform
(VFP).</li>
 	<li>According to Microsoft’s preliminary literature on the subject, we can leverage this extension to link our Hyper-V virtual switches to on-premises SDN or directly to public Azure virtual networks.</li>
 	<li>SMB 3.1.1 uses the AES-128-GCM algorithm by default. This is a 2x improvement over AES-128-CCM used in previous SMB versions. What’s more is that the GCM algorithm is backward-compatible with Windows Server 2012 R2 SMB encryption.</li>
 	<li>NOTE BINARY OPTIONS AND WINDOWS POWERSHELL
In binary, 0 typically refers to Boolean False and 1 signifies Boolean True. Therefore, in
PowerShell we use 1 and 0 to signify $true and $false states, respectively. Don’t forget that as long as you’ve run Update-Help to download the PowerShell help, you can run the following command to get full syntax help for any supported cmdlet: Get-Help -Name Set-SmbServerConfiguration -ShowWindow</li>
 	<li>SMB has long supported cryptographic signing at the packet level. SMB signing should be enabled on your domain controller because it ensures that client devices receive genuine Group Policy configurations.</li>
 	<li>NOTE SMB SIGNING AND NETWORK PERFORMANCE
According to the Microsoft TechNet library (<a href="http://timw.info/smb" target="_blank">http://timw.info/smb</a>), using SMB packet sign-
ing can degrade file service transaction performance by up to 15 percent. This makes sense when you remember that Windows needs to calculate hash values on every single packet in an SMB stream.</li>
</ul>
&nbsp;
<h3>Chapter 04: Manage Privileged Identities</h3>
<ul>
 	<li>The Enhanced Administrative Security Environment (ESAE) is a reference architecture that is designed to protect administrative accounts and their credentials from exposure to malicious access by sequestering them in a separate Active Directory (AD) forest. ESAE is not a product, a role, or a feature. It is instead a collection of design principles that enables you to create a separate, single-domain forest that is dedicated to Active Directory management. Because the administrative forest sees limited use, you can harden it to a greater degree than your production forest(s).</li>
 	<li>NOTE LIMITING THE SCOPE OF THE ADMINISTRATIVE FOREST
While it is possible to use the administrative forest for other management functions or ap-
plications, this is likely to increase the attack surface of the forest and reduce the effective-
ness of the ESAE design. For maximum protection of the most privileged accounts in the
enterprise, do not use the administrative forest for any other purposes.</li>
 	<li>When you create a forest trust, you have the option of using forest-wide or selective authentication. Selective authentication enables you to restrict the accounts in the administrative forest to specific servers in the production forest.</li>
 	<li>NOTE CONFIGURING DNS FOR A BASTION FOREST
The bastion forest should have its own DNS server, typically running on the domain con-
troller. It should not use the DNS server that services your production forest domains. The
production DNS server is later configured to forward name requests to the bastion forest’s
DNS server.</li>
 	<li>NEED MORE REVIEW? CREATING A BASTION FOREST USING PAM
For a detailed walkthrough of the procedure for creating a bastion forest and setting up
PAM using Microsoft Identity Manager 2016, see <a href="https://docs.microsoft.com/en-us/microsoft-identity-manager/pam/configuring-mim-environment-for-pam" target="_blank">https://docs.microsoft.com/en-us/microsoft-identity-manager/pam/configuring-mim-environment-for-pam</a>.</li>
 	<li>By default, PAM servers approve client requests for access to a role automatically, but you can also configure a role to require approval before a request is granted. By adding the ApprovalEnabled parameter to a New-PAMRole command line, you override the automatic request processing.</li>
 	<li>Just-Enough-Administration (JEA, pronounced jee’-ah) is designed to limit administrative users to only the elevated privileges required to perform a given task. As with PAM, JEA provides users with privileges that time out after a specified period. Unlike PAM, JEA is a Windows PowerShell-based technique that you can implement easily on a server running Windows Server 2016. There is no need for a bastion forest or additional hardware or software.</li>
 	<li>EXAM TIP
For the purposes of the 70-744 exam, be sure that you are able to distinguish between the
principles of Just-In-Time Administration and Just-Enough-Administration. You should also be familiar with the tools used to implement each of these principles on an enterprise
network.</li>
 	<li>For some organizations, JEA represents a fundamental shift in administrative practices,
from graphical tools to character-based ones.</li>
 	<li>JEA is based on the remote user capabilities built into Windows PowerShell. Users log on
to Windows using unprivileged accounts and then use Windows PowerShell to establish a
connection to a PowerShell session configuration, also known as a PowerShell endpoint.</li>
 	<li>You can create a role capabilities file in an existing module in one of these locations or you
can create a new module. In either case, you must create a RoleCapabilities subfolder in the module folder for your session configuration scripts to find it.</li>
 	<li>NOTE MODIFYING ROLE CAPABILITY FILES
Once you have registered an endpoint, you can make changes to the associated role capability file, if necessary, without repeating the registration, because PowerShell loads the role capabilities each time a session starts. However, sessions that are already in progress when you modify the file retain their existing capabilities for the duration of the session.</li>
 	<li>To use JEA on earlier Windows versions, including Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows 8.1, Windows 8, and Windows 7 SP1,
you must download and install Windows Management Framework (WMF) 5.0. WMF 5.0 is available from the Microsoft Download Center at the following URL: <a href="https://www.microsoft.com/en-us/download/details.aspx?id=50395" target="_blank">https://www.microsoft.com/en-us/download/details.aspx?id=50395</a>.</li>
 	<li>However, on Windows Server 2008 R2 and Windows 7 SP1, you must first install Windows Management Framework 4.0 and .NET Framework 4.5, and then install WMF 5.0.</li>
 	<li>IMPORTANT RUNNING JEA ON WINDOWS SERVER 2008 R2 AND WINDOWS 7 SP1
Windows Server 2008 R2 and Windows 7 do not provide full JEA functionality, even with
WMF 5.0 installed. On these platforms, Windows PowerShell endpoints cannot create and assign virtual accounts to connected users.</li>
 	<li>Privileged Access Workstation (PAW) is a designation that Microsoft uses to define the hardware and software configurations required to create dedicated administrative workstations. Deploying PAWs properly is more than just a matter of purchasing new computers. The object of the PAW principle is to create a workstation environment that can only be used for administrative purposes, even if an administrator should try to do otherwise. This includes creating an Active Directory (AD) substructure devoted to PAW users and Group Policy settings that enforce the administrators’ roles.</li>
 	<li>Therefore, a PAW deployment also includes an implementation of security groups and Group Policy settings that prevent PAWs from being used to access insecure resources.</li>
 	<li>Other system hardening techniques you can consider include Credential Guard in Windows 10, full disk encryption, disabling Internet browsing (by configuring the browser to use a loopback address as a proxy server), and restricting the use of USB ports to non-
media devices.</li>
 	<li>NEED MORE REVIEW? DEPLOYING PAWS
Complete instructions for a PAW deployment, including details of the AD infrastructure
modifications and Group Policy settings required, as well as scripts for creating them, are
available at <a href="https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/privileged-access-workstations" target="_blank">https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/privileged-access-workstations</a>.</li>
 	<li>Credential Guard is a security feature first introduced in Windows 10 Enterprise and Windows Server 2016 that protects user credentials by storing them in a virtualized container that is separate from the operating system.</li>
 	<li>Credential Guard creates a container called the isolated LSA process that is virtualized using the same hypervisor that Hyper-V uses. An attacking program running on the system with administrative privileges cannot access credentials stored in the isolated LSA process.</li>
 	<li>Remote Credential Guard works by redirecting the connector’s Kerberos authentication requests back to the source system. Because the credentials never reach the target computer, they are not endangered.</li>
 	<li>Local Administrator Password Solution (LAPS) is a free Microsoft product that enables
workstations to automatically change the passwords on local accounts and store those passwords as attributes of the computer objects in Active Directory. Using permissions, you can control which users are allowed to read the passwords and change them.</li>
 	<li>LAPS is a client/server tool that runs as a Group Policy client-side extension on your computers.</li>
 	<li>Deploying LAPS on your network consists of three basic steps: installing the LAPS management tools, modifying your Active Directory schema, and deploying the LAPS client to your workstations.</li>
 	<li>For LAPS client computers to be able to update their passwords, they must have the Write
permission to the attributes LAPS created. To deploy these permissions, you use the Set-AdmPwdComputerSelfPermission cmdlet to apply them to the Active Directory organizational unit (OU) objects which contain your LAPS client workstations.</li>
 	<li>LAPS can always identify the Administrator account by its SID. Configuring this policy setting causes LAPS to manage another local account instead of Administrator, not in addition to it. LAPS can only protect one account on a system.</li>
</ul>
&nbsp;
<h3>Chapter 05: Implement Threat Detection Solutions</h3>
<ul>
 	<li>The advanced audit policy settings enable you to be more selective in the events and resources you choose to audit, keeping your logs more manageable in the process.</li>
 	<li>NOTE CONFIRMING OBJECT AUDITING
One of the prominent maintenance issues in Windows auditing has always been the inability to determine which objects have correct SACLs applied to them, except by viewing each object individually. Global object access auditing makes it possible for administrators to confirm that all elements are appropriately configured with SACLs by viewing the Advanced Security Settings dialog box associated with the policy setting.</li>
 	<li>The basic and advanced audit policies are not compatible with each other. If you configure advanced audit settings in a GPO, any existing basic audit settings are cleared on a computer before the advanced settings are applied. Choosing between the basic and advanced audit policy settings is essentially a matter of how granular you want your auditing to be.</li>
 	<li>You can also create a single GPO that contains both basic and advanced audit policy settings, keeping in mind that the older operating systems ignore the advanced settings and the newer ones do not apply the basic settings.</li>
 	<li>NOTE AUDIT MANAGEMENT PREREQUISITES
To set up and administer an audit policy, you must possess the Manage Auditing and Security Log user right for the computer on which you want to configure a policy or review a log. This right is granted by default to the Administrators group. However, to delegate this task to another user, such as a container administrator, that person must possess the specific right. In addition, any files or folders to be audited must be located on NTFS volumes.</li>
 	<li>NOTE COPYING SACLS WITH POWERSHELL
To replicate the SACL from one file to another using this technique, be sure to include the audit parameter in the Get-Acl command. If you do not, GetAcl does not include the SACL in its output, so it is not copied to the other file.</li>
 	<li>The Audit PNP Activity policy, found in the Detail Tracking category, generates an event in the Security log each time Plug and Play (PNP) detects the connection of an external device of any type. The policy even generates a new event each time a user connects the same device to the system.
The value of this policy is that administrators can correlate the insertion of a PNP device with other activities on the system.</li>
 	<li>NOTE LOGGING SUSPICIOUS CODE
Windows PowerShell automatically logs blocks of code that contain suspicious commands or scripts, even if you do not enable the Turn On PowerShell Script Block Logging policy. These event log entries are flagged with a Warning status, while the entries generated by the enabled policy are flagged as Information or Verbose. If you explicitly disable the policy, no code blocks are recorded to the log, including suspicious ones.</li>
 	<li>ATA gathers information from Windows logs and uses deep packet inspection techniques to evaluate trends in network traffic to and from domain controllers and the behavior of users, devices, and resources.</li>
 	<li>In most cases, one ATA Center computer can service an entire Active Directory forest. If your enterprise consists of multiple forests, you need one ATA center for each one.</li>
 	<li>The standalone ATA Gateway can service multiple domain controllers, up to a maximum of
50,000 packets per second of domain controller traffic.</li>
 	<li>The standalone gateway provides a security advantage; because it is separate from the domain controllers, potential attackers have a harder time learning that ATA is installed on the network. The main disadvantage is that the standalone ATA Gateway requires a server, and a server license, of its own.</li>
 	<li>ATA Lightweight Gateways service only the domain controllers on which they are installed,
and support up to 10,000 packets per second. ATA Lightweight Gateways continually monitor the CPU and memory utilization on the domain controllers where they are running, and throttle their resource usage to ensure that the native functions of the domain controller are not affected.</li>
 	<li>Less expensive, because a separate server is not required, ATA Lightweight Gateways are an ideal solution for branch offices and cloud-based virtual domain controllers.</li>
 	<li>NOTE PORT MIRRORING AND ATA GATEWAYS
Only standalone ATA Gateways use port mirroring to receive network traffic from domain
controllers. ATA Lightweight Gateways run on the domain controllers, so they already have
access to the required traffic.</li>
 	<li>If you are implementing ATA on physical computers, you must configure your switch to mirror the domain controller traffic to your ATA Gateway computer. If you are using virtual machines, you can usually configure port mirroring on the virtual network adapters in the virtual machines.</li>
 	<li>To install the ATA Lightweight Gateway on a domain controller, the computer must have a processor with at least two cores and also a minimum of six gigabytes of memory.</li>
 	<li>If you are using a virtual machine for your domain controller, be sure to allocate the full amount of memory required and do not use the Dynamic Memory feature in Hyper-V or any similar memory management feature. ATA does not support the use of these technologies.</li>
 	<li>It takes up to a month after the initial installation for ATA to construct a baseline for your network activity.</li>
 	<li>EXAM TIP
When preparing for the 70-744 exam, be sure that when you are studying a large, complex software product like OMS, you concentrate on the features related to threat detection that are likely to be covered in the exam.</li>
 	<li>NOTE USING OMS WITH SYSTEM CENTER OPERATIONS MANAGER
OMS can function in tandem with the System Center Operations Manager (SCOM) product, funneling all of the agent data through an on-premise SCOM server to the OMS service, or it can function independently, with the data going directly from the agents to OMS. Hybrid implementations are also possible.</li>
 	<li>NOTE USING OMS SECURITY AND AUDIT WITH SCOM COMPUTERS
When computers are members of an SCOM management group, most of the information collected by the agent goes to the SCOM server first, which then relays it to the OMS service. However, depending on the auditing options you select, the logs required by the Security and Audit solution can accumulate extremely large amounts of data, and sending that data directly to OMS can prevent an unnecessary burden on the SCOM server.</li>
 	<li>To supply OSM with the Security log data it needs, you must configure the advanced auditing policies on your servers using Group Policy.</li>
 	<li>NEED MORE REVIEW? RECOMMENDED AUDITING POLICY SETTINGS
For a detailed listing of Microsoft’s recommendations for advanced auditing policy settings, see <a href="https://technet.microsoft.com/windows-server-docs/identity/ad-ds/plan/security-best-practices/audit-policy-recommendations" target="_blank">https://technet.microsoft.com/windows-server-docs/identity/ad-ds/plan/security-best-practices/audit-policy-recommendations</a>.</li>
 	<li>For Application log data, you should configure your servers to log information on which executable files, installer scripts, and packages are used in your network.</li>
</ul>
&nbsp;
<h3>Chapter 06: Implement Workload-Specific Security</h3>
<ul>
 	<li>The Nano Server installation option and the two implementations of containers in Windows Server 2016 Windows Containers and Hyper-V Containers are intended to provide server and application environments that are more isolated and therefore more resistant to attack than standard Windows Server installations.</li>
 	<li>The two basic scenarios for Nano Server deployments are as follows:
<ul>
 	<li>Server cloud infrastructure services, such as Hyper-V, Failover Clustering, Scale-Out File Servers, DNS, and Internet Information Services (IIS)</li>
 	<li>Born-in-the-cloud applications running on virtual machines, containers, or physical servers, using development platforms that do not require a graphical interface</li>
</ul>
</li>
 	<li>By default, Nano Server runs less than half as many services and processes as a full Windows Server installation, and far fewer than Server Core, as well as maintaining fewer open ports.</li>
 	<li>The main shortcoming of the Nano Server design, at least at this point in its development, is its relatively limited utility. The server supports only a small subset of the roles and features in the full Windows Server product.</li>
 	<li>NOTE REUSING A DOMAIN COMPUTER NAME
If a computer account with the name specified in the ComputerName parameter already exists in Active Directory, you can configure a Nano Server image to reuse that account by adding the ReuseDomainNode parameter to the NewNanoServerImage command line.</li>
 	<li>NOTE USING THE NANO SERVER RECOVERY CONSOLE INTERFACE
The Nano Server Recovery Console has no support for the mouse, and even its keyboard support is limited. Number pads are not supported, nor are CapsLk and NumLk keys. To navigate the interface, you use the cursor keys or the Tab key to highlight an option and press Enter to select it. The legend at the bottom of the screen specifies additional key combinations.</li>
 	<li>NOTE CONFIGURING A DNS SERVER ADDRESS
Unusually, there is no way to specify a DNS server address in the Nano Server Recovery Console interface. To configure the DNS server address for an initial Nano Server configuration, you must use the Ipv4Dns parameter on the NewNanoServerImage command line or use DHCP to supply the address.</li>
 	<li>This interface does not provide full administrative access to Windows Firewall. It is intended only to provide you with sufficient control to gain remote access to the Nano Server. You can activate or deactivate an existing rule, but you cannot modify rules themselves or create new ones. Once you have remote access to the Nano Server, you can use standard tools, such as the Windows Firewall with Advanced Security console or the Windows PowerShell cmdlets, to exercise complete control over the firewall.</li>
 	<li>To add a computer to the Trusted Hosts list using PowerShell, you specify its name or IP address in the Set-Item cmdlet, as in the following example:
<em>set-item </em>wsman<em>:\localhost\client\trustedhosts "192.168.10.41"</em>
You can also use the Winrm.exe tool from the command prompt, as follows:
winrm<em> set </em>winrm<em>/config/client @{TrustedHosts="192.168.10.41"}</em></li>
 	<li>NEED MORE REVIEW? POWERSHELL CORE FEATURE OMISSIONS
For a list of the features not included in PowerShell Core, see <a href="https://technet.microsoft.com/en-us/windows-server-docs/compute/nano-server/powershell-on-nano-server" target="_blank">https://technet.microsoft.com/en-us/windows-server-docs/compute/nano-server/powershell-on-nano-server</a>.</li>
 	<li>You can configure a Nano Server to pull configurations from a DSC server, or receive configurations pushed from a server, but a Nano Server cannot function as a pull server for other clients. The Nano Server DSC implementation does include all of the cmdlets from the full version.</li>
 	<li>NEED MORE REVIEW? NANO SERVER DSC CAPABILITIES
For a complete list of what the Nano Server Desired State Configuration feature can and cannot do, see <a href="https://msdn.microsoft.com/en-us/powershell/dsc/nanodsc" target="_blank">https://msdn.microsoft.com/en-us/powershell/dsc/nanodsc</a>.</li>
 	<li>To deploy a DSC configuration module, the administrator must decide between implementing a pull or a push architecture. In a pull architecture, the MOF files are stored on a Pull Server, which is an SMB server or an IIS web server with an OData interface, set up with its own DSC configuration.</li>
 	<li>In a push architecture, the administrator runs the Start-DscConfiguration cmdlet on the server, specifying the location where the MOF files are stored in the -Path parameter.</li>
 	<li>Unlike virtual machines, however, which run completely separate copies of the operating system, containers actually share the operating system of the host system. There is no need to install a separate instance of the operating system for each container, nor does the container have to perform a boot sequence, load libraries, or devote memory to the operating system files. Containers start in seconds, and you can create more containers on a host system than you can virtual machines.</li>
 	<li>The working environment appears similar to that of a virtual machine, but unlike a virtual machine, which maintains separate copies of all of the operating system files, a container is actually sharing these files with the host, not copying them. It is only when a user or application in a container modifies a file that a copy is made in the container’s file system.</li>
 	<li>Windows Server Containers share everything with the host computer, including the operating system kernel and the system memory.</li>
 	<li>Hyper-V provide an additional level of isolation by using the hypervisor to create a separate copy of the operating system kernel for each container. The containers also have their own memory assigned to them and isolated storage and network I/O.</li>
 	<li>The two types of containers are interchangeable. You can create an image for a Windows Server Container and later run it in a Hyper-V container without modification.</li>
 	<li>NOTE CONTAINER PORTABILITY
While Windows-based containers are interchangeable between Windows Server Containers and Hyper-V containers, Windows containers are not interchangeable with Linux containers. You cannot run a Linux container in Windows, nor can you run a Windows container on a Linux machine. This is because the kernel APIs of the two operating systems are not compatible.</li>
 	<li>There is no automatic installer for these files. You must create a folder on your computer called C:\Program Files\Docker and use the following two Invoke-WebRequest commands in PowerShell to download them.
<em>invoke-</em>webrequest<em> -</em>uri<em> https://aka.ms/tp5/b/dockerd -</em>outfile<em> "c:\program files\docker\</em>
<em>dockerd.exe"</em>
<em>invoke-</em>webrequest<em> -</em>uri<em> https://aka.ms/tp5/b/docker -</em>outfile<em> "c:\program files\docker\</em>
<em>docker.exe"</em></li>
 	<li>NTFS quotas are limited to controlling storage on entire volumes, on a per-user basis. When you create FSRM quotas for volumes or folders, they apply to all users. NTFS quotas are also limited to creating event log entries only, while FSRM quotas can also send email notifications, execute commands, and generate reports, as well as log events.</li>
 	<li>The File Classification Infrastructure (FCI) in FSRM enables administrators to create additional properties for files, based on the specific needs of the organization.</li>
 	<li>FCI also includes classification rules, which can automatically assign values to specific properties based on the contents of a file.</li>
 	<li>NOTE LOCAL CLASSIFICATION PROPERTIES
When you create classification properties in FSRM, they are stored and applied locally on the server. If you move a classified file to a server that does not have the same properties configured, then any classification information in the file is lost. In Windows Server 2016, it is also possible to create domain-wide properties that are stored in Active Directory, making them available to all of the Windows servers in the domain.</li>
 	<li>The Classification Management tools in FSRM operate on the local server only. To create and deploy properties on multiple servers, you must use Dynamic Access Control to create resource properties in Active Directory Administrative Center, package them as resource property lists, and deploy them to your file servers using Windows PowerShell.</li>
 	<li>To use Work Folders in a production environment, you have to obtain a Secure Sockets Layer (SSL) certificate for the server and bind it to the Default Web Site created by the IIS Hostable Web Core.</li>
 	<li>When there are no changes to the files in the client’s Work Folders directory, the client attempts to sync with the server every ten minutes, seeking modifications to its folder on the server. Adding or modifying a file in the client Work Folder directory triggers an immediate sync.</li>
 	<li>EXAM TIP
When preparing for the 70-744 exam, be sure to remain conscious of the differences in scope between the local properties and rules that you create in File Server Resource Manager and the domain-based Dynamic Access Control elements that you create in Active Directory Administrative Center, such as claim types, resource properties, and central access rules. The DAC elements are global and available to all of the file servers in the domain. The FSRM rules and properties affect only the local file system. If you want to deploy FSRM rules and properties throughout your network, you must create them on each file server individually.</li>
 	<li>Resource properties are similar in function to the classification properties you can create in File Server Resource Manager. They contain metadata that you can add to files and folders. The primary difference is that resource properties are stored in Active Directory, and are therefore available to any file server in the domain. This prevents you from having to create the same classification properties in FSRM on every file server.</li>
 	<li>When you create a central access rule, the default option in the Permissions section is Use Following Permissions as Proposed Permissions. Leaving this option selected in your CARs causes the resulting CAPs to generate access requests for the targeted resources and log them in the system’s event logs. You can then examine the logs in Event Viewer to determine whether the correct resources have been targeted and the correct permissions proposed.</li>
 	<li>Windows Server 2016 includes a feature called access-denied remediation (also called access-denied assistance) that addresses this issue by enabling administrators to customize the message displayed to users when they are denied access.</li>
</ul>
