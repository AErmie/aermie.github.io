---
layout: page
title: Book Review: Introduction to Windows Containers
date: 2017-10-28 11:40
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2017/10/IntroductionToWindowsContainers_BookCover.jpg"><img class="alignleft wp-image-30578 size-thumbnail" src="/wp-content/uploads/2017/10/IntroductionToWindowsContainers_BookCover-150x150.jpg" alt="" width="150" height="150" /></a>Recently, I finished reading the <a href="https://blogs.msdn.microsoft.com/microsoft_press/2017/08/30/free-ebook-introduction-to-windows-containers/" target="_blank" rel="noopener">Introduction to Windows Containers</a> ebook.

The chapters that I found most helpful were Chapter 1 “Containers 101" especially since this is something new to me. I also found Chapter 5 "Deep Dive Containerizing Your Application" useful to round out my understanding, so that I can more effectively guide customers thinking about this technology. Chapter 3 "Deep Dive Host Deployment" could have had more substance in my opinion. I wish it had more context in relating Container Hosts to how we (in IT Ops) view and understand working with Virtual Machines and Hyper-V hosts.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 01: Containers 101</h2>
<ul>
 	<li>A container is another form of virtualization, but one that is focused at the operating system (OS) layer. It is geared toward deploying and running applications without requiring a full virtual machine (VM) for each application.</li>
 	<li>In a modern datacenter, containers can achieve a greater density per host than VMs because the footprint of a container is considerably smaller than that of a VM.</li>
 	<li>VMs require individual management, which generally increases the associated overhead of running an application.</li>
 	<li>They don’t have the same management footprint, because you no longer need to manage a full OS, thus reducing potentials costs associated to the container lifecycle.</li>
 	<li>The isolation essentially gives the application its own view of the OS from the perspective of memory, CPU and file system, among other things. The application can perform any operation in this “bubble,” even delete what it thinks is the OS without affecting any other containers that are running.</li>
 	<li>Containers also don’t maintain state; you are required to maintain state outside of the container runtime.</li>
 	<li>Containers also give an enterprise a migration path toward making its applications cloud-native without a major replatform. It also facilitates an agility to migrate applications between clouds.</li>
 	<li>Containers also require applications that are intended to be containerized to have noninteractive user interface (UI) or service-based applications.</li>
 	<li>With this simple understanding, we can begin to understand why containers are best geared toward headless apps.</li>
 	<li>If you want to provide additional isolation so that applications cannot interfere with one another, containers are a good fit.</li>
 	<li>Containers make it possible for enterprises to take the first steps on their cloud journey and move from a traditional monolithic architecture to a more modern microservices architecture without major recoding of their applications initially.</li>
 	<li>With a microservices architecture, organizations can scale and update part of an application independently of the other parts.</li>
 	<li>Containers are autonomous files that contain an entire runtime environment: an application plus all its dependencies, libraries, and configuration files needed for it to run identically in any environment. By containerizing an application and its dependencies, developers can abstract differences in OS distributions and underlying infrastructure.</li>
 	<li>Windows Server Containers share a kernel with the container host and all running containers. It provides isolation for the application through process and namespace isolation technology.</li>
 	<li>Windows Server Containers with Hyper-V Isolation provide an isolated kernel experience through a utility VM on a host. This increases security of the container because the isolation mechanisms are enforced at the hardware level, instead.</li>
 	<li>Container management in Windows Container host, be it a Windows Server Container or a Windows Server Containers with Hyper-V Isolation deployment, will use Docker as the main management tool for administering the lifecycle of the containers that are running.</li>
 	<li>A custom container image starts with the base OS layer being deployed to a container host. The enterprise can then install all its application dependencies and components. Following installation, because a container by default is immutable, you need to commit these changes to start a container with the deployed application.</li>
 	<li>Committing these changes creates a new layer with a dependency link to the base OS layer. This means that if an application is invoked, it will check whether the base OS layer has been loaded already into the container host before trying to invoke the application container.</li>
 	<li>Network traffic between two containers in the same IP subnet and attached to the same container host is directly bridged. Network traffic between two containers on different IP subnets or attached to different container hosts is sent out through the external vSwitch.</li>
 	<li>Each container has its own virtual Network Interface Card (vNIC) that is isolated and connected to the vSwitch.</li>
 	<li>Containers are designed to be standalone, nondomain-joined entities.</li>
 	<li>Containers are different in that each one should generally represent one app, and the host is implicitly trusted.</li>
 	<li>If the base image is tampered with, it will be detected and repaired by the existing code integrity features.</li>
 	<li>Enterprises can use tools like Docker Security Scanner to validate an image from a private repository from known vulnerabilities and exposures.</li>
 	<li>Containers can have antivirus programs installed within the image. However, it introduces some challenges that each antivirus vendor will need to overcome to avoid affecting the performance of the container. For example, because containers share a view of the same data from a container host, it is possible to perform redundant virus scans on this data.</li>
 	<li>To install antivirus capabilities in a container, Microsoft has published guidance available to configure the solution and avoid redundant scans.</li>
 	<li>You might therefore think that by simply updating the base layer and then the framework layer, the application layer will be automatically updated because we have a dependency on the base OS image. In fact, this is not the case. Indeed, if you update the base OS image either via a patch or by downloading the latest version available from the image repository, it will break the framework layer and the application layer.</li>
 	<li>Because containers are a mix of an infrastructure technology and a development technology, you need to examine the possibility of introducing a DevOps model to update the base image and provide subsequent build tasks, which will deploy the necessary framework and application into their respective layer.</li>
</ul>
<h2>Chapter 02: Docker 101</h2>
<ul>
 	<li>Docker is becoming the standard unit of deployment and is emerging as the de facto standard implementation for containers on developer desktops, datacenters, and in the cloud.</li>
 	<li>With developers building, and then packaging their applications into containers, and providing them to IT to run on a standardized platform, containers reduce the overall effort to deploy applications and can streamline the entire development and test cycle, ultimately reducing costs.</li>
 	<li>Docker containers isolate applications from one another and from the underlying infrastructure. Docker provides the strongest default isolation to limit app issues to a single container instead of the entire machine.</li>
 	<li>Windows Server Containers help secure and modernize existing enterprise .NET and line-of-business server applications with little or no code changes.</li>
 	<li>Each container has an independent session namespace, which helps to provide isolation and security. The kernel object namespace is isolated per container.</li>
 	<li>To create more isolation, Windows Server Containers with Hyper-V Isolation each have their own copy of the Windows kernel and have memory assigned directly to them</li>
 	<li>Containers are a solution to deployment problems caused by app dependencies on libraries and the OS that make transitioning the app from one environment to the next (e.g., from QA to production) so problematic.</li>
 	<li>Scaling the instances of containers is far faster and easier than deploying additional VMs.</li>
 	<li>Breaking up the monolithic application into subsystems that can be scaled, developed, and deployed individually is the entry point into the realm of microservices.</li>
</ul>
<h2>Chapter 03: Deep Dive Host Deployment</h2>
<ul>
 	<li>If a container host is a VM and a Hyper-V nested container host, you need to allocate at least 4 GB RAM to this machine. A container host VM also requires that you allocate at least two virtual processors to it.</li>
 	<li>Because containers in Windows Server will be managed via Docker, it is recommended that you use the OneGet Windows PowerShell engine. This will turn on the container feature and install the Docker engine and client. For this to work, the host will require Internet access.</li>
 	<li>The localport 2375 is used to make a remote nonsecured connection for the Docker client to the daemon; if you require a secured connection, use localport 2376.</li>
 	<li>To verify whether the processor(s) supports nested virtualization, run this command:
<span style="color: #00ccff;">Get-WMIObject Win32_Processor |Select SecondLevelAddressTranslationExtensions</span>
If the output is True, the processor(s) supports nested virtualization, if False, the processor does not support nested virtualization.</li>
</ul>
<h2>Chapter 04: Deep Dive Working with Containers</h2>
<ul>
 	<li>When you use the docker run command, you need to consider how you want the container to run. For example, do you want it to run in the background and do its job, or do you need to interact with it? This will determine the initial runtime option you select; for example, <span style="color: #00ccff;">-detach</span> or <span style="color: #00ccff;">-d</span> for detached mode, or <span style="color: #00ccff;">-interactive</span> or <span style="color: #00ccff;">-</span>i for interactive mode.</li>
 	<li><strong>Note</strong> Be careful when you start a container in interactive mode because the process you are starting within the container needs to support this!</li>
 	<li>By default, when you deploy a container host, it will automatically deploy a default Network Address Translation (NAT) network, unless you have modified the dameon.json configuration file located at C:\ProgramData\Docker\Config\deamon.json.</li>
 	<li>Containers in NAT mode are isolated unless you present their endpoint via a port mapping so that it becomes accessible to the outside world. For example, if you run an Internet Information Services (IIS) container image, you will not be able to access the web page until you expose the port.</li>
 	<li>You must set up port mappings as you are creating a container, or you must stop the container and perform the mapping by using the <span style="color: #00ccff;">-p</span> parameter</li>
 	<li>Also, if you do not specify an external port, Docker will automatically create a dynamic mapping for use</li>
 	<li>If you specify multiple network adapter names in the form of “adapter1”,”adapter2”,”adapter3”, you can create a teamed network for Docker to use.</li>
 	<li>The escape character for Docker is the backslash (\). This, obviously can be very problematic in Windows because we use that character quite extensively when working with directories, for example. For example, normally a path to the temp directory might be C:\Temp\. But, if you’re referencing that directory Dockerfiles, you need to escape the backslash; thus, it becomes C:\\Temp\\.</li>
 	<li><strong>Note</strong> A coding best practice is for each command to be all uppercase.</li>
 	<li>There are two roles in Swarm mode: a manager node and worker nodes. Every node begins with a manager node, which is also responsible for initializing the Swarm, controlling the worker nodes, and maintaining the overall desired state of the applications running on the Swarm. There can be multiple manager and worker nodes in a Swarm.</li>
 	<li><strong>Note</strong> Before creating a Docker Swarm, consider the use of availability sets for the worker nodes if you plan on using a virtualization technology or public cloud. This is to ensure that not all worker nodes and manager nodes end up on the same host.</li>
 	<li>Swarm mode introduces a network driver called Overlay (Windows Server 2016 April 2017 CU and Windows 10 Creators Update sets up this feature) The Overlay network is based on VXLAN Technology and you can use it to span multiple container hosts. Each overlay network is assigned its own private IP subnet.</li>
 	<li>When scaling as just described, load-balancing across the services come into question with regard to how we achieve this. Whereas Docker Swarm has support for a few different options, with Windows Containers, only two are currently supported: DNS Round Robin, and external load-balancing using published ports.</li>
</ul>
<h2>Chapter 05: Deep Dive Containerizing Your Application</h2>
<ul>
 	<li>There are a significant number of factors that ultimately might stack up against an
application for initial containerization. It is also important to note that while some applications might not be good initial candidates for containerization, this simply highlights that the system needs to be modernized, which could lead to code refactoring or a new development.</li>
 	<li>Although containerizing does provide a lot of benefits, the overall mindset with which you should approach this topic is one of application modernization. Application modernization is a complex journey by which you configure your applications to be more cloud aware. This does include containerization, but it is not necessarily the end of the journey. Containerization can provide the first steps to help an enterprise separate an application into a microservices-like architecture, and then eventually to a full microservice-based system like Service fabric.</li>
 	<li>If the original source code is old and written in something like COBOL, Fortran, or other legacy languages, this will almost certainly lead to a code refactoring</li>
 	<li>Applications written in a modern development language will lend themselves to containerization easier than older languages.</li>
 	<li>If it is a mainframe application, this will not be a good candidate to containerize and will
require refactoring. A traditional N-tier or single-server application at least initially looks like a more appropriate candidate to containerize.</li>
 	<li>If an application has a server-side user interface that is required to run for the application to function, this also will not be a good candidate to migrate as a container. However, if the server-side interface application could be decoupled from the main service running the server, it becomes a more viable candidate for containerization.</li>
 	<li>Containers do not maintain state, if you reboot a container, whatever existed within the container at that time is destroyed. When selecting an application, this is an important item to consider because state does not only mean where does it store my data; it also means where does it store any transient information it requires to function.</li>
 	<li>Applications being selected for containerization need to be able to externalize the state of the application, be it data or configuration files or log files.</li>
 	<li>If we have an application that has multiple services on a single box, we need to examine the possibility of splitting these services. The developers might have written the application to communicate only across the local system and not over TCP connections between systems. If the application has been written to be on only a single system, code refactoring will be required to allow you to break apart the layers of the application.</li>
 	<li>If the application was never designed for high availability (HA), we must consider the potential impact of containerizing it. Although this is not a technical blocker, because you can simply invoke one container, it is more the operational process you need to have in place to ensure that the application is not scaled! It might be beneficial for the enterprise to understand how the application might be designed or refactored to support HA.</li>
 	<li>Containers themselves do not technically have any identity. They also are not domain joined. This again is not technically a blocker, but an enterprise needs to understand how its applications authenticate and how moving to containers will affect this.</li>
 	<li>Refactoring of the authentication and authorization methods might be required.</li>
 	<li>Because containers are not domain joined and are stateless, we need to consider how we will retrieve information about the application running and information on the health of the container itself.</li>
 	<li>Even though you probably will need to significantly debug the application in a container and provide “fixes” to get it to work, it is possible to stuff a single app with dependent services inside and container and run it. However, it is considered a dirty approach and will end up costing more time in the long run. strategy. Although refactoring the code of your
application to a full microservices platform might not be feasible, taking steps to split the application so that it represents functional components of a microservices architecture might be possible.</li>
</ul>
