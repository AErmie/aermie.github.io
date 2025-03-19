---
layout: page
title: Book Review: Docker Deep Dive: Zero to Docker in a single book (May 2020 Edition)
date: 2020-09-10 07:51
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/09/DockerDeepDive-BookCover.jpg"><img class="alignleft wp-image-33543 size-medium" src="/wp-content/uploads/2020/09/DockerDeepDive-BookCover-242x300.jpg" alt="" width="242" height="300" /></a>Recently, I finished reading <a href="https://www.amazon.ca/Docker-Deep-Dive-Nigel-Poulton-ebook/dp/B01LXWQUFF" target="_blank" rel="noopener noreferrer">Docker Deep Dive: Zero to Docker in a single book</a> by Nigel Poulton.

I've recently been ramping up on Kubernetes, so, reading and learning about Docker is a natural fit. Prior to reading this book, I did have some experience with Docker, but not a lot of depth.

I really liked/appreciated the way this book was written, including the consistent and simple format of, first a to-long-don't-read (TLDR) section up front, then a deep dive, followed by a review of the commands. I also really appreciated how the author made comparisons for both Developers and IT Operations individuals (ie. using Virtual Machines as an illustration/example). That really helped to understand concepts that would be new for someone just starting to learn about containers.

I particularly found<span style="color: #000000;"> the whole book helpful but in particular Chapter 6 ("<strong>Images</strong>"), Chapter 8 ("<strong>Containerizing an App</strong>"), and Chapter 10 ("<strong>Docker Swarm</strong>") which helped me draw a lot of parallels to Kubernetes, and Chapter 11 ("<strong>Docker Networking</strong>").</span>

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

If my highlights peak your interest, I strongly recommend that you pick up a copy for yourself.
<h2>Chapter 1: Containers From 30,000 Feet</h2>
<ul>
 	<li>It’s vital to understand that a running container shares the kernel of the host machine it is running on. This means that a containerized Windows app will not run on a Linux-based Docker host, and vice-versa — Windows containers require a Windows host, and Linux containers require a Linux host.</li>
 	<li>At the time of writing, Kubernetes uses Docker as its default container runtime — the low-level technology that pulls images and starts and stops containers.</li>
 	<li>However, Kubernetes has a pluggable container runtime interface (CRI) that makes it easy to swap-out Docker for a different container runtime.</li>
 	<li>Containerd is the small specialized part of Docker that does the low-level tasks of starting and stopping containers.</li>
</ul>
<h2>Chapter 2: Docker</h2>
<ul>
 	<li>The software is currently built from various tools from the Moby open-source project.</li>
 	<li>It’s also interesting to know that the word “Docker” comes from a British expression meaning dock worker — somebody who loads and unloads cargo from ships.</li>
 	<li>The runtime operates at the lowest level and is responsible for starting and stopping containers (this includes building all of the OS constructs such as namespaces and cgroups).</li>
 	<li>Docker implements a tiered runtime architecture with high-level and low-level runtimes that work together.</li>
 	<li>The low-level runtime is called runc and is the reference implementation of Open Containers Initiative (OCI) runtime-spec.</li>
 	<li>The higher-level runtime is called containerd. containerd does a lot more than runc. It manages the entire lifecycle of a container, including pulling images, creating network interfaces, and managing lower-level runc instances.</li>
 	<li>A typical Docker installation has a single containerd process (docker-containerd) controlling the runc (docker-runc) instances associated with each running container.</li>
</ul>
<h2>Chapter 3: Installing Docker</h2>
<ul>
 	<li>A default installation assumes you’ll be working with Linux containers. It does this by running the Docker daemon inside of a lightweight Linux Hyper-V VM.</li>
 	<li>It’s worth noting that Docker Desktop on Mac doesn’t give you the Docker Engine running natively on the Mac OS Darwin kernel. Behind the scenes, the Docker daemon is running</li>
 	<li>inside a lightweight Linux VM that seamlessly exposes the daemon and API to your Mac environment. This means you can open a terminal on your Mac and use the regular Docker commands.</li>
 	<li>Play with Docker (PWD) provides a free-to-use fully functional Docker playground that lasts for 4 hours.</li>
</ul>
<h2>Chapter 4: The Big Picture</h2>
<ul>
 	<li>It’s useful to think of a Docker image as an object that contains an OS filesystem, an application, and all application dependencies. If you work in operations, it’s like a virtual machine template.</li>
 	<li>An image contains enough of an operating system (OS), as well as all the code and dependencies to run whatever application it’s designed for.</li>
 	<li>It’s also worth noting that each image gets its own unique ID. When referencing images, you can refer to them using either IDs or names.</li>
 	<li>The -it flags tell Docker to make the container interactive and to attach the current shell to the container’s terminal.</li>
 	<li>Press Ctrl-PQ to exit the container without terminating it. This will land your shell back at the terminal of your Docker host.</li>
 	<li>You can attach your shell to the terminal of a running container with the docker container exec command.</li>
 	<li>The format of the docker container exec command is: docker container exec &lt;options&gt; &lt;container-name or container-id&gt; &lt;command/app&gt;.</li>
 	<li>Adding -a tells Docker to list all containers, even those in the stopped state.</li>
</ul>
<h2>Chapter 5: The Docker Engine</h2>
<ul>
 	<li>At the time of writing, the major components that make up the Docker engine are; the Docker daemon, containerd, runc, and various plugins such as networking and storage.</li>
 	<li>Once a container’s parent runc process exits, the associated containerd-shim process becomes the container’s parent.</li>
 	<li>However, at the time of writing, some of the major functionality that still exists in the daemon includes; image management, image builds, the REST API, authentication, security, core networking, and orchestration.</li>
 	<li>By default, network communication occur over an unsecured HTTP socket on port 2375/tcp.</li>
 	<li>Docker lets you force the client and daemon to only accept network connections that are secured with TLS. This is recommended for production environments, even if all traffic is traversing trusted internal networks.</li>
 	<li>Port 2376 is the standard port for Docker using TLS. 2375 is the default unsecured port.</li>
</ul>
<h2>Chapter 6: Images</h2>
<ul>
 	<li>A Docker image is a unit of packaging that contains everything required for an application to run. This includes; application code, application dependencies, and OS constructs.</li>
 	<li>Images are made up of multiple layers that are stacked on top of each other and represented as a single object. Inside of the image is a cut-down operating system (OS) and all of the files and dependencies required to run an application.</li>
 	<li>Images are considered build-time constructs, whereas containers are run-time constructs.</li>
 	<li>Once you’ve started a container from an image, the two constructs become dependent on each other and you cannot delete the image until the last container using it has been stopped and destroyed.</li>
 	<li>Image also don’t contain a kernel — all containers running on a Docker host share access to the host’s kernel. For these reasons, we sometimes say images contain just enough operating system (usually just OS-related files and filesystem objects).</li>
 	<li>The local image repository on a Linux-based Docker host is usually located at /var/lib/docker/&lt;storage-driver&gt;.</li>
 	<li>On Windows-based Docker hosts this is C:\ProgramData\docker\windowsfilter.</li>
 	<li>The most common registry is Docker Hub (<a href="https://hub.docker.com" target="_blank" rel="noopener noreferrer">https://hub.docker.com</a>). Other registries exist, including 3rd party registries and secure on-premises registries. However, the Docker client is opinionated and defaults to using Docker Hub.</li>
 	<li>Docker is configured to use <a href="https://index.docker.io/v1/" target="_blank" rel="noopener noreferrer">https://index.docker.io/v1/</a> as its default registry when pushing and pulling images (this actually redirects to v2).</li>
 	<li>Image registries contain one or more image repositories. In turn, image repositories contain one or more images.</li>
 	<li>You’ll probably notice that the Microsoft images we’ve used do not exist at the top-level of the Docker Hub namespace. At the time of writing, they exist under the official mcr.microsoft.com second-level namespace. This is due to legal reasons requiring them to be hosted outside of Docker Hub.</li>
 	<li>Addressing images from official repositories is as simple as providing the repository name and tag separated by a colon (:).</li>
 	<li>If you do not specify an image tag after the repository name, Docker will assume you are referring to the image tagged as latest. If the repository doesn’t have an image tagged as latest the command will fail.</li>
 	<li>A single image can have as many tags as you want. This is because tags are arbitrary alpha-numeric values that are stored as metadata alongside the image.</li>
 	<li>Latest is an arbitrary tag and is not guaranteed to point to the newest image in a repository!</li>
 	<li>A dangling image is an image that is no longer tagged, and appears in listings as &lt;none&gt;:&lt;none&gt;.</li>
 	<li>You can delete all dangling images on a system with the docker image prune command. If you add the -a flag, Docker will also remove all unused images (those not in use by any containers).</li>
 	<li>You can also use the --format flag to format output using Go templates.</li>
 	<li>One last thing about docker search. By default, Docker will only display 25 lines of results. However, you can use the --limit flag to increase that to a maximum of 100.</li>
 	<li>A Docker image is just a bunch of loosely-connected read-only layers, with each layer comprising one or more files.</li>
 	<li>Another way to see the layers of an image is to inspect the image with the docker image inspect command.</li>
 	<li>The docker history command is another way of inspecting an image and seeing layer data. However, it shows the build history of an image and is not a strict list of layers in the final image.</li>
 	<li>All Docker images start with a base layer, and as changes are made and new content is added, new layers are added on top.</li>
 	<li>It’s important to understand that as additional layers are added, the image is always the combination of all layers stacked in the order they were added.</li>
 	<li>Docker employs a storage driver that is responsible for stacking layers and presenting them as a single unified filesystem/image.</li>
 	<li>The only driver supported by Docker on Windows is windowsfilter, which implements layering and CoW on top of NTFS.</li>
 	<li>Docker on Linux supports many storage drivers. Each is free to implement image layering, layer sharing, and copy-on-write (CoW) behaviour in its own way. However, the overall result and user experience is essentially the same.</li>
 	<li>Docker 1.10 introduced a content addressable storage model. As part of this model, all images get a cryptographic content hash.</li>
 	<li>Every time you pull an image, the docker image pull command includes the image’s digest as part of the information returned.</li>
 	<li>At the time of writing, there is no native Docker command that will retrieve the digest of an image from a remote registry such as Docker Hub. This means the only way to determine the digest of an image is to pull it by tag and then make a note of its digest.</li>
 	<li>The layers are where the data lives (files and code etc.). Each layer is fully independent, and has no concept of being part of an overall bigger image.</li>
 	<li>Images and layers are immutable, and we can easily identify any changes made to either.</li>
 	<li>Docker Hub verifies every pushed layer to make sure it wasn’t tampered with en route. To do this, it runs a hash against the layer content and checks it against the hash that</li>
 	<li>was sent.</li>
 	<li>Each layer also gets something called a distribution hash. This is a hash of the compressed version of the layer and is included with every layer pushed or pulled to a registry.</li>
 	<li>The manifest list is exactly what it sounds like: a list of architectures supported by a particular image tag. Each supported architecture then has its own * manifest detailing the layers that make it up.</li>
 	<li>When you pull an image, your Docker client makes the relevant calls to the Docker Registry API exposed by Docker Hub.</li>
 	<li>We do not have to tell Docker that we need the Linux x64 or Windows x64 versions of the image. We just run normal commands and let Docker take care of getting the right image for the platform and architecture we are running!</li>
 	<li>You can create your own builds for different platforms and architectures with docker buildx and then use docker manifest create to create your own manifest lists.</li>
 	<li>At the time of writing, buildx is an experimental feature and requires experimental=true setting in your ~/.docker/config.json file.</li>
 	<li>Deleting an image will remove the image and all of its layers from your Docker host. This means it will no longer show up in docker image ls commands and all directories on the Docker host containing the layer data will be deleted.</li>
 	<li>You can list multiple images on the same command by separating them with whitespace.</li>
 	<li>A handy shortcut for deleting all images on a Docker host is to run the docker image rm command and pass it a list of all image IDs on the system by calling docker image ls with the - q flag.</li>
</ul>
<h2>Chapter 7: Containers</h2>
<ul>
 	<li>The container engine then takes OS resources such as the process tree, the filesystem, and the network stack, and carves them into isolated constructs called containers.</li>
 	<li>At a high level, hypervisors perform hardware virtualization — they carve up physical hardware resources into virtual versions called VMs. On the other hand, containers perform OS virtualization — they carve OS resources into virtual versions called containers.</li>
 	<li>The VM model carves low-level hardware resources into VMs. Each VM is a software construct containing virtual CPUs, virtual RAM, virtual disks etc. As such, every VM needs its own OS to claim, initialize, and manage all of those virtual resources.</li>
 	<li>Remember, there’s no kernel inside of a container that needs locating, decompressing, and initializing — not to mention all of the hardware enumerating and initializing associated with a normal kernel bootstrap.</li>
 	<li>Well, one thing that’s not so great about the container model is security. Out of the box, containers are less secure and provide less workload isolation than VMs. Technologies exist to secure containers and lock them down, but at the time of writing, some of them are prohibitively complex.</li>
 	<li>When you hit Return, the Docker client packaged up the command and POSTed it to the API server running on the Docker daemon. The Docker daemon accepted the command and searched the Docker host’s local image repository to see if it already had a copy of the requested image.</li>
 	<li>Note: In a standard, out-of-the-box Linux installation, the Docker daemon implements the Docker Remote API on a local IPC/Unix socket at /var/run/docker.sock. On Windows, it listens on a named pipe at npipe: ////./pipe/docker_engine. It’s possible to configure the Docker daemon to listen on the network. The default non-TLS network port for Docker is 2375, the default TLS port is 2376.</li>
 	<li>A container cannot exist without it’s designated main process.</li>
 	<li>Press Ctrl-PQ to exit the container without terminating its main process. Doing this will place you back in the shell of your Docker host and leave the container running in the background.</li>
 	<li>Stopping a container is like stopping a virtual machine. Although it’s not currently running, its entire configuration and contents still exist on the local filesystem of the Docker host. This means it can be restarted at any time.</li>
 	<li>Containers are designed to be immutable objects and it’s not a good practice to write data to them.</li>
 	<li>It’s considered a best practice to take the two-step approach of stopping the container first and then deleting it.</li>
 	<li>Docker container stop sends a SIGTERM signal to the main application process inside the container (PID 1). As we said, this gives the process a chance to clean things up and gracefully shut itself down. If it doesn’t exit within 10 seconds, it will receive a SIGKILL. This is effectively the bullet to the head. But hey, it got 10 seconds to sort itself out first.</li>
 	<li>Restart policies are applied per-container, and can be configured imperatively on the command line as part of docker-container run commands, or declaratively in YAML files for use with higher-level tools such as Docker Swarm, Docker Compose, and Kubernetes.</li>
 	<li>An interesting feature of the --restart always policy is that if you stop a container with docker container stop and the restart the Docker daemon, the container will be restarted.</li>
 	<li>If you restart the Docker daemon, the container will be automatically restarted when the daemon comes back up. You need to be aware of this.</li>
 	<li>The on-failure policy will restart a container if it exits with a non-zero exit code. It will also restart containers when the Docker daemon restarts, even containers that were in the stopped state.</li>
 	<li>-d stands for daemon mode, and tells the container to run in the background. You can’t use the -d and -it flags in the same command.</li>
 	<li>It’s important to know that port mappings are expressed as host-port:container-port.</li>
 	<li>The entries after Cmd show the command/app that the container will run unless you override it with a different one when you launch the container with docker container run.</li>
</ul>
<h2>Chapter 8: Containerizing an App</h2>
<ul>
 	<li>The process of containerizing an app looks like this: Start with your application code and dependencies Create a Dockerfile that describes your app, its dependencies, and how to run it.</li>
 	<li>Feed the Dockerfile into the docker image build command Push the new image to a registry (optional) Run container from the image.</li>
 	<li>The directory containing the application and dependencies is referred to as the build context. It’s a common practice to keep your Dockerfile in the root directory of the build context. It’s also important that Dockerfile starts with a capital “D” and is all one word. “dockerfile” and “Docker file” are not valid.</li>
 	<li>It’s considered a best practice to list a maintainer of an image so that other potential users have a point of contact when working with it.</li>
 	<li>Before you can push an image, you need to tag it in a special way. This is because Docker needs all of the following information when pushing an image:
<ul>
 	<li>Registry</li>
 	<li>Repository Tag</li>
</ul>
</li>
 	<li>The format of the command is docker image tag &lt;current-tag&gt; &lt;new-tag&gt; and it adds an additional tag, it does not overwrite the original.</li>
 	<li>The docker image build command parses the Dockerfile one-line-at-a-time starting from the top.</li>
 	<li>Comment lines start with the # character.</li>
 	<li>All non-comment lines are Instructions and take the format INSTRUCTION argument. Instruction names are not case sensitive, but it’s normal practice to write them in UPPERCASE. This makes reading the Dockerfile easier.</li>
 	<li>Examples of instructions that create new layers are FROM, RUN, and COPY.</li>
 	<li>Examples that create metadata include EXPOSE, WORKDIR, ENV, and ENTRYPOINT.</li>
 	<li>The basic premise is this — if an instruction is adding content such as files and programs to the image, it will create a new layer. If it is adding instructions on how to build the image and run the application, it will create metadata.</li>
 	<li>The way you write your Dockerfiles has a huge impact on the size of your images.</li>
 	<li>A common example is that every RUN instruction adds a new layer. As a result, it’s usually considered a best practice to include multiple commands as part of a single RUN instruction — all glued together with double-ampersands (&amp;&amp;) and backslash (\) line-breaks.</li>
 	<li>Multi-stage builds have a single Dockerfile containing multiple FROM instructions. Each FROM instruction is a new build stage that can easily COPY artefacts from previous stages.</li>
 	<li>An important thing to note, is that COPY --from instructions are used to only copy production-related application code from the images built by the previous stages. They do not copy build artefacts that are not needed for production.</li>
 	<li>For each instruction, Docker looks to see if it already has an image layer for that instruction in its cache. If it does, this is a cache hit and it uses that layer. If it doesn’t, this is a cache miss and it builds a new layer from the instruction. Getting cache hits can hugely speed up the build process.</li>
 	<li>If it finds a layer, it skips the instruction, links to that existing layer, and continues the build with the cache in tact. If it does not find a layer, it invalidates the cache and builds the layer. This operation of invalidating the cache invalidates it for the remainder of the build. This means all subsequent Dockerfile instructions are completed in full without attempting to reference the build cache.</li>
 	<li>Try and write them in a way that places instructions that are likely to invalidate the cache towards the end of the Dockerfile.</li>
 	<li>Docker performs a checksum against each file being copied, and compares that to a checksum of the same file in the cached layer. If the checksums do not match, the cache is invalidated and a new layer is built.</li>
 	<li>The squashed image will also need to send every byte to Docker Hub on a docker image push command, whereas the non-squashed image only needs to send unique layers.</li>
 	<li>If you are building Linux images, and using the apt package manager, you should use the no-install-recommends flag with the apt-get install command.</li>
 	<li>This makes sure that apt only installs main dependencies (packages in the Depends field) and not recommended or suggested packages.</li>
</ul>
<h2>Chapter 9: Deploying Apps with Docker Compose</h2>
<ul>
 	<li>Docker Compose lets you describe an entire app in a single declarative configuration file, and deploy it with a single command.</li>
 	<li>In fact, it was so good, that Docker, Inc. acquired Orchard and re-branded Fig as Docker Compose.</li>
 	<li>The version key is mandatory, and it’s always the first line at the root of the file. This defines the version of the Compose file format (basically the API). You should normally use the latest version.</li>
 	<li>It’s important to note that the versions key does not define the version of Docker Compose or the Docker Engine.</li>
 	<li>It’s important to understand that Compose will deploy each of these as a container, and it will use the name of the keys as part of the container names.</li>
 	<li>Compose will also use the name of the directory (counter-app) as the project name.</li>
 	<li>docker-compose up is the most common way to bring up a Compose app (we’re calling a multi-container app defined in a Compose file a Compose app). It builds or pulls all required images, creates all required networks and volumes, and starts all required containers.</li>
 	<li>Notice how Compose has named the newly built image as a combination of the project name (counter-app), and the resource name as specified in the Compose file (web-fe). All resources deployed by Compose will follow this naming convention.</li>
 	<li>It’s important to note that the counter-vol volume was not deleted. This is because volumes are intended to be long-term persistent data stores.</li>
 	<li>As such, their lifecycle is entirely decoupled from the applications they serve.</li>
 	<li>It’s also worth knowing that Compose builds networks and volumes before deploying services.</li>
 	<li>docker-compose restart will restart a Compose app that has been stopped with docker-compose stop. If you have made changes to your Compose app since stopping it, these changes will not appear in the restarted app. You will need to re-deploy the app to get the changes.</li>
</ul>
<h2>Chapter 10: Docker Swarm</h2>
<ul>
 	<li>Docker Swarm is two main things:
<ul>
 	<li>An enterprise-grade secure cluster of Docker hosts</li>
 	<li>An engine for orchestrating microservices apps</li>
</ul>
</li>
 	<li>On the clustering front, Swarm groups one or more Docker nodes and lets you manage them as a cluster. Out-of-the-box, you get an encrypted distributed cluster store, encrypted networks, mutual TLS, secure cluster join tokens, and a PKI that makes managing and rotating certificates a breeze.</li>
 	<li>Docker Swarm competes directly with Kubernetes — they both orchestrate containerized applications.</li>
 	<li>Nodes are configured as managers or workers. Managers look after the control plane of the cluster, meaning things like the state of the cluster and dispatching tasks to workers. Workers accept tasks from managers and execute them.</li>
 	<li>TLS is so tightly integrated that it’s impossible to build a swarm without it.</li>
 	<li>The process of building a swarm is called initializing a swarm, and the high-level process is this: Initialize the first manager node &gt; Join additional manager nodes &gt; Join worker nodes &gt; Done.</li>
 	<li>Docker nodes that are not part of a swarm are said to be in single-engine mode. Once they’re added to a swarm they’re automatically switched into swarm mode.</li>
 	<li>Running docker swarm init on a Docker host in single-engine mode will switch that node into swarm mode, create a new swarm, and make the node the first manager of the swarm.</li>
 	<li>--listen-addr: This is the IP address that the node will accept swarm traffic on. If not explicitly set, it defaults to the same value as --advertise -addr. If --advertise-addr is a load-balancer, you must use --listen-addr to specify a local IP or interface for swarm traffic.</li>
 	<li>Whether a node joins as a worker or a manager depends entirely on which token you use when joining it. You should ensure that your join tokens are kept secure, as they’re the only thing required to join a node to a swarm!</li>
 	<li>Nodes with nothing in the MANAGER STATUS column are workers.</li>
 	<li>Technically speaking, swarm implements a form of active-passive multi-manager HA. This means that although you have multiple managers, only one of them is active at any given moment. This active manager is called the “leader”, and the leader is the only one that will ever issue live commands against the swarm. So, it’s only ever the leader that changes the config, or issues tasks to workers. If a follower manager (passive) receives commands for the swarm, it proxies them across to the leader.</li>
 	<li>Managers are either leaders or followers. This is Raft terminology, because swarm uses an implementation of the Raft consensus algorithm to maintain a consistent cluster state across multiple highly available managers.</li>
 	<li>On the topic of HA, the following two best practices apply: Deploy an odd number of managers. Don’t deploy too many managers (3 or 5 is recommended) it’s a best practice to have either 3 or 5 managers for HA. 7 might work, but it’s generally accepted that 3 or 5 is optimal. You definitely don’t want more than 7, as the time taken to achieve consensus will be longer.</li>
 	<li>Docker allows you to lock a swarm with the Autolock feature. This forces restarted managers to present the cluster unlock key before being admitted back into the cluster.</li>
 	<li>You can always check your current swarm unlock key with the docker swarm unlock - key command.</li>
 	<li>Locking your swarm and protecting the unlock key is recommended for production environments.</li>
 	<li>Services let us specify most of the familiar container options, such as name, port mappings, attaching to networks, and images. But they add important cloud-native features, including desired state and automatic reconciliation.</li>
 	<li>It’s important to understand that all service replicas use the same image and config!</li>
 	<li>The --pretty flag to limit the output to the most interesting items printed in an easy-to-read format. Leaving off the --pretty flag will give a more verbose output.</li>
 	<li>Behind the scenes, swarm runs a scheduling algorithm called “spread” that attempts to balance replicas as evenly as possible across the nodes in the swarm. At the time of writing, this amounts to running an equal number of replicas on each node without taking into consideration things like CPU load etc.</li>
 	<li>Be careful using the docker service rm command as it deletes all service replicas without asking for confirmation.</li>
 	<li>This mode of publishing a port on every node in the swarm — even nodes not running service replicas — is called ingress mode and is the default. The alternative mode is host mode which only publishes the service on swarm nodes running replicas.</li>
 	<li>Docker service update lets us make updates to running services by updating the service’s desired state.</li>
 	<li>If you run a docker inspect --pretty command against the service, you’ll see the update parallelism and update delay settings are now part of the service definition. This means future updates will automatically use these settings unless you override them as part of the docker service update command.</li>
 	<li>Swarm Service logs can be viewed with the docker service logs command. However, not all logging drivers support the command.</li>
 	<li>By default, Docker nodes configure services to use the json-file log driver.</li>
 	<li>Service logs work on the premise that your application is running as PID 1 in its container and sending logs to STDOUT and errors to STDERR. The logging driver forwards these “logs” to the locations configured via the logging driver.</li>
 	<li>Managing your swarm and applications declaratively is a great way to prevent the need to recover from a backup.</li>
 	<li>Swarm configuration and state is stored in /var/lib/docker/swarm on every manager node. The configuration includes; Raft log keys, overlay networks, Secrets, Configs, Services, and more. A swarm backup is a copy of all the files in this directory.</li>
 	<li>As you have to stop the Docker daemon on the node you are backing up, it’s a good idea to perform the backup from non-leader managers.</li>
 	<li>A swarm restore is only for situations where the swarm is corrupted or otherwise lost and you cannot recover services from copies of config files stored in a source code repo.</li>
 	<li>All swarm nodes must have their Docker daemon stopped and the contents of their /var/lib/docker/swarm directories deleted.</li>
 	<li>The following must also be true for a recovery operation to work: You can only restore to a node running the same version of Docker the backup was performed on You can only restore to a node with the same IP address as the node the backup was performed on.</li>
 	<li>The --force-new-cluster flag tells Docker to create a new cluster using the configuration stored in /var/lib/docker/swarm/ that you recovered.</li>
</ul>
<h2>Chapter 11: Docker Networking</h2>
<ul>
 	<li>Docker networking is based on an open-source pluggable architecture called the Container Network Model (CNM). libnetwork is Docker’s real-world implementation of the CNM, and it provides all of Docker’s core networking capabilities. Drivers plug in to libnetwork to provide specific network topologies.</li>
 	<li>Last but not least, libnetwork provides a native service discovery and basic container load balancing solution.</li>
 	<li>In order to meet the demands of complex highly-fluid environments, libnetwork allows multiple network drivers to be active at the same time.</li>
 	<li>Every Docker host gets a default single-host bridge network. On Linux it’s called “bridge”, and on Windows it’s called “nat” (yes, those are the same names as the drivers used to create them).</li>
 	<li>By default, this is the network that all new containers will be connected to unless you override it on the command line with the --network flag.</li>
 	<li>The default “bridge” network, on all Linux-based Docker hosts, maps to an underlying Linux bridge in the kernel called “docker0”.</li>
 	<li>Beware: The default bridge network on Linux does not support name resolution via the Docker DNS service. All other user-defined bridge networks do.</li>
 	<li>Port mappings let you map a container to a port on the Docker host. Any traffic hitting the Docker host on the configured port will be directed to the container.</li>
 	<li>Single-host bridge networks are only useful for local development and very small applications.</li>
 	<li>Overlay networks are multi-host. They allow a single network to span multiple hosts so that containers on different hosts can communicate directly. They’re ideal for container-to-container communication, including container-only applications, and they scale well.</li>
 	<li>MACVLAN uses standard Linux sub-interfaces, and you have to tag them with the ID of the VLAN they will connect to.</li>
 	<li>The Docker MACVLAN driver is built on top of the tried-and-tested Linux kernel driver with the same name. As such, it supports VLAN trunking. This means we can create multiple MACVLAN networks and connect containers on the same Docker host to them.</li>
 	<li>You can also tell Docker how verbose you want daemon logging to be. To do this, edit the daemon config file (daemon.json) so that “debug” is set to “true” and “log-level” is set to one of the following:
<ul>
 	<li>debug - The most verbose option</li>
 	<li>info - The default value and second-most verbose option</li>
 	<li>warn - Third most verbose option</li>
 	<li>error - Fourth most verbose option fatal Least verbose option</li>
</ul>
</li>
 	<li>As well as a driver and configuration for daemon logs, every Docker host has a default logging driver and configuration for containers. Some of the drivers include: json-file (default) journald (only works on Linux hosts running systemd) syslog splunk gelf</li>
 	<li>Container logs work on the premise that your application is running as PID 1 inside the container and sending logs to STDOUT, and errors to STDERR. The logging driver then forwards these “logs” to the locations configured via the logging driver.</li>
 	<li>Service discovery allows all containers and Swarm services to locate each other by name. The only requirement is that they be on the same network.</li>
 	<li>Under the hood, this leverages Docker’s embedded DNS server and the DNS resolver in each container.</li>
 	<li>The Docker DNS server holds name-to-IP mappings for all containers created with the --name or --net-alias flags.</li>
 	<li>Swarm supports two publishing modes that make services accessible outside of the cluster: Ingress mode (default) Host mode</li>
 	<li>Services published via ingress mode can be accessed from any node in the Swarm — even nodes not running a service replica.</li>
 	<li>Services published via host mode can only be accessed by hitting nodes running service replicas.</li>
 	<li>To publish a service in host mode you need to use the long format of the --publish flag and add mode=host.</li>
 	<li>Behind the scenes, ingress mode uses a layer 4 routing mesh called the Service Mesh or the Swarm Mode Service Mesh.</li>
</ul>
<h2>Chapter 12: Docker Overlay Networking</h2>
<ul>
 	<li>It allows you to create a flat, secure, layer-2 network, spanning multiple hosts.</li>
 	<li>Swarm mode is a pre-requisite for overlay networks.</li>
 	<li>Data plane encryption isn’t enabled by default because of the performance overhead. It’s highly recommended that you extensively test performance before enabling data plane encryption.</li>
 	<li>By default, Docker overlay networks encrypt cluster management traffic but not application traffic. You must explicitly enable encryption of application traffic.</li>
 	<li>New overlay networks are only extended to worker nodes when they are tasked with running a container on it. This lazy approach to extended overlay networks improves network scalability by reducing the amount of network gossip.</li>
 	<li>Standalone containers that are not part of a swarm service cannot attach to overlay networks unless they have the attachable=true property.</li>
 	<li>Docker overlay networking uses VXLAN tunnels to create virtual Layer 2 overlay networks.</li>
 	<li>The beauty of VXLAN is that it’s an encapsulation technology that existing routers and network infrastructure just see as regular IP/UDP packets and handle without issue.</li>
 	<li>To create the virtual Layer 2 overlay network, a VXLAN tunnel is created through the underlying Layer 3 IP infrastructure.</li>
 	<li>A sandbox is like a container, but instead of running an application, it runs an isolated network stack — one that’s sandboxed from the network stack of the host itself.</li>
</ul>
<h2>Chapter 13: Volumes and Persistent Data</h2>
<ul>
 	<li>To deal with non-persistent data, every Docker container gets its own non-persistent storage. This is automatically created for every container and is tightly coupled to the lifecycle of the container.</li>
 	<li>To deal with persistent data, a container needs to store it in a volume. Volumes are separate objects that have their lifecycles decoupled from containers. This means you can create and manage volumes independently, and they’re not tied to the lifecycle of any container.</li>
 	<li>It’s a best practice not to change the configuration of a container after it’s deployed. If something breaks or you need to change something, you should create a new container with the fixes/updates and deploy it in place of the old container. You shouldn’t log into a running container and make configuration changes!</li>
 	<li>Every Docker container is created by adding a thin read-write layer on top of the read-only image it’s based on.</li>
 	<li>This writable layer of local storage is managed on every Docker host by a storage driver (not to be confused with a volume driver).</li>
 	<li>Volumes are the recommended way to persist data in containers. There are three major reasons for this:
<ul>
 	<li>Volumes are independent objects that are not tied to the lifecycle of a container</li>
 	<li>Volumes can be mapped to specialized external storage systems</li>
 	<li>Volumes enable multiple containers on different Docker hosts to access and share the same data</li>
</ul>
</li>
 	<li>By default, Docker creates new volumes with the built-in local driver. As the name suggests, volumes created with the local driver are only available to containers on the same node as the volume.</li>
 	<li>All volumes created with the local driver get their own directory under /var/lib/docker/volumes on Linux, and C:\ProgramData\Docker\volumes on Windows.</li>
 	<li>Docker volume prune will delete all volumes that are not mounted into a container or service replica, so use with caution!</li>
 	<li>It’s also possible to deploy volumes via Dockerfiles using the VOLUME instruction. The format is VOLUME &lt;container-mount-point&gt;.</li>
 	<li>Defining a volume in a Dockerfile requires you to specify host directories at deploy-time.</li>
 	<li>If you specify an existing volume, Docker will use the existing volume If you specify a volume that doesn’t exist, Docker will create it for you.</li>
</ul>
<h2>Chapter 14: Deploying Apps with Docker Stacks</h2>
<ul>
 	<li>They let you define complex multi-service apps in a single declarative file. They also provide a simple way to deploy the app and manage its entire lifecycle — initial deployment &gt; health checks &gt; scaling &gt; updates &gt; rollbacks and more!</li>
 	<li>The Compose file includes the entire stack of microservices that make up the app. It also includes all of the volumes, networks, secrets, and other infrastructure the app needs.</li>
 	<li>Stack files are very similar to Compose files. The only requirement is that the version: key specify a value of “3.0” or higher.</li>
 	<li>You should perform extensive testing to understand the performance overhead that encrypting data plane traffic has on your workload. It’s not uncommon for this to be approximately 10%.</li>
 	<li>One difference between Docker Stacks and Docker Compose is that stacks do not support builds. This means all images have to be built prior to deploying the stack.</li>
 	<li>By default, all ports are mapped using ingress mode. This means they’ll be mapped and accessible from every node in the Swarm — even nodes not running a replica.</li>
 	<li>The long-form syntax is recommended, as it’s easier to read and more powerful (it supports ingress mode and host mode). However, it requires at least version 3.2 of the Compose file format.</li>
 	<li>The environment key lets you inject environment variables into services replicas at runtime.</li>
 	<li>Placement constraints are a great way of influencing scheduling decisions. Swarm currently lets you schedule against all of the following:
<ul>
 	<li>Node ID. node.id == o2p4kw2uuw2a</li>
 	<li>Node name. node.hostname == wrk-12</li>
 	<li>Role. node.role != manager</li>
 	<li>Engine labels. engine.labels.operatingsystem == ubuntu 16.04</li>
 	<li>Custom node labels. node.labels.zone == prod1</li>
</ul>
</li>
 	<li>The default value for failure_action is pause, which will stop further replicas being updated. The other option is continue.</li>
 	<li>Node labels are custom-defined labels added to swarm nodes with the docker node update command. As such, they’re only applicable within the context of the node’s role in the Swarm (you can’t leverage them on standalone containers or outside of the Swarm).</li>
 	<li>Docker prepends the name of the stack to every resource it creates.</li>
 	<li>The docker stack ps command is a good place to start when troubleshooting services that fail to start. It gives an overview of every service in the stack, including which node each replica is scheduled on, current state, desired state, and error message.</li>
 	<li>For more detailed logs of a particular service you can use the docker service logs command. You pass it either the service name/ID, or replica ID.</li>
 	<li>If your stack defines volumes at the top-level, these will not be deleted by docker stack rm either. This is because volumes are intended as long-term persistent data stores and exist independent of the lifecycle of containers, services, and stacks.</li>
</ul>
<h2>Chapter 15: Security in Docker</h2>
<ul>
 	<li><strong>Note:</strong> While namespaces isolate multiple processes on a single OS, the isolation they provide is not very strong.</li>
 	<li>The most important thing to understand is that Docker containers are an organized collection of namespaces. This means that you get all of this OS isolation for free with every container.</li>
 	<li>Every join token is comprised of 4 distinct fields separated by dashes (-): PREFIX-VERSION-SWARM ID-TOKEN
<ul>
 	<li>The prefix is always SWMTKN. This allows you to pattern-match against it and prevent people from accidentally posting it publicly.</li>
 	<li>The VERSION field indicates the version of the swarm.</li>
 	<li>The Swarm ID field is a hash of the swarm’s certificate.</li>
 	<li>The TOKEN field is the part that determines whether it can join nodes as managers or workers.</li>
</ul>
</li>
 	<li>The Subject data in the output uses the standard O, OU, and CN fields to specify the Swarm ID, the node’s role, and the node ID.
<ul>
 	<li>The Organization (O) field stores the Swarm ID.</li>
 	<li>The Organizational Unit (OU) field stores the node’s role in the swarm</li>
 	<li>The Canonical Name (CN) field stores the node’s crypto ID.</li>
</ul>
</li>
 	<li>The store is currently based on the popular etcd distributed database and is automatically configured to replicate itself to all managers in the swarm.</li>
 	<li>As good as image scanning is, it’s important to understand its limitations. For example, image scanning is focused on images and does not detect security problems with networks, nodes, or orchestrators. Also, not all image scanners are equal — some perform deep binary-level scanning to detect packages, whereas others simply look at package names and do not closely inspect the content of images.</li>
 	<li>DCT can also be used to provide important context. This includes; whether or not an image has been signed for use in a particular environment such as “prod” or “dev”, or whether an image has been superseded by a newer version and is therefore stale.</li>
 	<li>You can force a Docker host to always sign and verify image push and pull operations by exporting the DOCKER_CONTENT_TRUST environment variable with a value of 1. In the real world, you’ll want to make this a more permanent feature of Docker hosts.</li>
 	<li>Behind the scenes, secrets are encrypted at rest, encrypted in-flight, mounted in containers to in-memory filesystems, and operate under a least-privilege model where they are only made available to services that have been explicitly granted access to them.</li>
</ul>
