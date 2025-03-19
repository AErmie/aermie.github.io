---
layout: page
title: Book Review: Managing Kubernetes: Operating Kubernetes Clusters in the Real World
date: 2020-05-11 11:43
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/05/ManagingKubernetes-Cover.jpg"><img class="alignleft wp-image-33302 size-medium" src="/wp-content/uploads/2020/05/ManagingKubernetes-Cover-229x300.jpg" alt="" width="229" height="300" /></a>Recently, I finished reading <a href="https://www.amazon.ca/Managing-Kubernetes-Operating-Clusters-World-ebook/dp/B07KFQL927/ref=sr_1_1?keywords=managing+kubernetes&amp;qid=1588708233&amp;sr=8-1" target="_blank" rel="noopener noreferrer">Managing Kubernetes: Operating Kubernetes Clusters in the Real World</a> by Brendan Burns and Craig Tracey.

I've recently been ramping up on Kubernetes, so, I had some knowledge already, including some hands-on. But one thing that I found missing most of the time, is the "day-2" and operations of Kubernetes. Most articles/books/etc. talk about setting up a cluster, deploying an application, etc. But not what you do <strong><em>after</em></strong> that.

I particularly found<span style="color: #000000;"> the whole book helpful but in particular Chapter 2 ("<strong>An Overview of Kubernetes</strong>"), Chapter 10 ("<strong>Networking</strong>"), Chapter 11 ("<strong>Monitoring Kubernetes</strong>"), and Chapter 12 ("<strong>Disaster Recovery</strong>"). </span>

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 1: Introduction</h2>
<ul>
 	<li>A Kubernetes cluster or really any significant piece of software is not something that you simply turn up, start running, and walk away from.</li>
 	<li>The first step in detecting when things break and in understanding why they are broken is to have the right metrics in place.</li>
 	<li>In addition to these container-generated metrics, the Kubernetes codebase itself has been instrumented with a significant number of application metrics.</li>
 	<li>Fortunately, Kubernetes was built in a decoupled, modular manner, with minimal state in the system. This means that, generally, at any given time, it is safe to restart any component in the system that may be overloaded or misbehaving.</li>
 	<li>Successfully managing a cluster requires that you develop and exercise a disaster response and recovery procedure.</li>
 	<li>It's important to remember that simply developing this plan is insufficient. You need to practice it regularly, or you will not be ready (and the plan itself may be flawed) in the presence of a real problem.</li>
 	<li>Part of managing a Kubernetes cluster is knowing how and when to add these tools, platforms, and projects into the cluster. It requires an exploration and understanding of not only what a particular project is attempting to accomplish but also of the other solutions that exist in the ecosystem.</li>
 	<li>Sometimes the job of managing a Kubernetes cluster involves developing new code and new extensions that enhance your cluster in ways that were previously impossible.</li>
</ul>
<h2>Chapter 2: An Overview of Kubernetes</h2>
<ul>
 	<li>The container image contains the application runtime, which consists of binaries, libraries, and other data needed to run the container.</li>
 	<li>When a container image is run, it is also executed using namespaces in the operating system. These namespaces contain the process and provide isolation for it and its peers from other things running on the machine.</li>
 	<li>Additionally, control groups (cgroups) allow the isolation of resource usage, like memory or CPU.</li>
 	<li>Containers as implemented in Linux and Windows do not currently provide strong security isolation for different processes.</li>
 	<li>Only hypervisor-level security is strong enough to isolate truly hostile workloads.</li>
 	<li>Every registry requires some form of authorization to push an image, but some registries are public, meaning that once an image is pushed, anyone in the world can pull and start running the image.</li>
 	<li>Before you even begin to set up your Kubernetes cluster, it's a good idea to figure out where you are going to store the images that you run in it.</li>
 	<li>Kuberentes' job is to take a group of machines that provide resources, like CPU, memory, and disk, and transform them into a container-oriented API that developers can use to deploy their containers.</li>
 	<li>The Kubernetes community provides a strong deprecation policy that ensures that developers and operators donâ€™t have to change what they are doing with each revision of the system.</li>
 	<li>All of the containers in a Pod are guaranteed to land on the same machine in the cluster.</li>
 	<li>Pods also share the process and interprocess communication namespaces so that different containers can use tools, like shared memory and signaling, to coordinate between the different processes in the Pod.</li>
 	<li>Consider that the Pod is also the unit of scaling and replication, which means that, if you group your frontend and your database in the same container, you will replicate your database at the same rate that you replicate your frontends. It is unlikely that you want to do things this way.</li>
 	<li>If you are deploying a container orchestrator just to run individual containers, you are probably overcomplicating your life.</li>
 	<li>NOTE: ReplicaSet is a newer object. At its v1 release, Kubernetes had an API object called a ReplicationController. Due to the deprecation policy, ReplicationControllers continue to exist in the Kubernetes API, but their usage is strongly discouraged in favor of ReplicaSets.</li>
 	<li>A Service represents a TCP or UDP load-balanced service.</li>
 	<li>The load balancing that is performed can either be round robin or deterministic, based on source and destination IP address tuples.</li>
 	<li>This DNS address provides a semantic name (e.g., frontend), which is the same as the name of the Kubernetes Service object</li>
 	<li>This programming of the network fabric is dynamic, so as Pods come and go due to failures or scaling of a ReplicaSet, the load balancer is constantly reprogrammed to match the current state of the cluster.</li>
 	<li>At present, there are more than 10 different types of Volumes you can create, including NFS, iSCSI, gitRepo, cloud storage-based Volumes, and more.</li>
 	<li>New Volume types are developed outside of the Kubernetes code and use the Container Storage Interface (CSI), an interface for storage that is independent of Kubernetes.</li>
 	<li>Different containers can mount these Volumes at different locations or can ignore the Volume entirely.</li>
 	<li>When you add a Volume to your Pod, you can choose to mount it to an arbitrary location in each running container.</li>
 	<li>A ConfigMap represents a collection of configuration files.</li>
 	<li>When you add a ConfigMap-based Volume to your Pod, the files in the ConfigMap show up in the specified directory in your running container.</li>
 	<li>It is often desirable to have a Pod definition that requests a generic type of storage (e.g., 10 gigabytes of network storage) without specifying a provider.</li>
 	<li>Instead of binding a Volume directly into a Pod, a PersistentVolume is created as a separate object. This object is then claimed to a specific Pod by a PersistentVolumeClaim and finally mounted into the Pod via this claim.</li>
 	<li>You can think of a Namespace as something like a folder for your Kubernetes API objects.</li>
 	<li>Namespaces can also provide a scope for role-based access control (RBAC) rules.</li>
 	<li>Like a folder, when you delete a Namespace, all of the objects within it are also destroyed, so be careful!</li>
 	<li>Most installations of Kubernetes also include a Namespace named kube-system, where cluster administration containers are created.</li>
 	<li>Most common Kubernetes API objects are namespaced objects. But some objects that apply to an entire cluster (e.g., Namespace objects themselves, or cluster-level RBAC), are not namespaced.</li>
 	<li>Every object in the Kubernetes API can have an arbitrary set of labels associated with it. Labels are string key-value pairs that help identify the object.</li>
 	<li>Labels and label selectors are the fundamental manner in which Kubernetes loosely couples its objects together.</li>
 	<li>Every Kubernetes API object can also have arbitrary annotations. These might include something like the icon to display next to the object or a modifier that changes the way that the object is interpreted by the system.</li>
 	<li>Often, experimental or vendor-specific features in Kubernetes are initially implemented using annotations, since they are not part of the formal API specification.</li>
 	<li>A Deployment can hold pointers to multiple ReplicaSets, (e.g., v1 and v2), and it can control the slow and safe migration from one ReplicaSet to another.</li>
 	<li>In most modern clusters, users exclusively use Deployment objects and don't manage ReplicaSets directly.</li>
 	<li>When you create an Ingress object, it receives a virtual IP address just like a Service, but instead of the one-to-one relationship between a Service IP address and a set of Pods, an Ingress can use the content of an HTTP request to route requests to different Services.</li>
 	<li>With Ingress, the routing can be based on either host or path or both</li>
 	<li>You need to also run an Ingress Controller in the cluster to take appropriate action when the Ingress object is created.</li>
 	<li>StatefulSets create multiple instances of the same container image running in a Kubernetes cluster, but the manner in which containers are created and destroyed is more deterministic, as are the names of each container.</li>
 	<li>When replicas are removed from a StatefulSet, they are removed at the highest index. If a StatefulSet is scaled down from five to four replicas, it is guaranteed that the fifth replica is the one that will be removed.</li>
 	<li>A Job represents a set of tasks that needs to be run. Like ReplicaSets and StatefulSets, Jobs operate by creating Pods to execute work by running container images. However, unlike ReplicaSets and StatefulSets, the Pods created by a Job only run until they complete and exit.</li>
 	<li>A ScheduledJob contains the definition of the Job object that you want to create, as well as the schedule on which that Job should be created.</li>
 	<li>A DaemonSet provides a template for a Pod that should be run on every machine. When a DaemonSet is created, Kubernetes ensures that this Pod is running on each node in the cluster</li>
</ul>
<h2>Chapter 3: Kubernetes Architecture</h2>
<ul>
 	<li>Instead of a single monolithic controller, Kubernetes is composed of a large number of controllers, each performing its own independent reconciliation loop.</li>
 	<li>When grouping things together into a set, there are two possible approaches explicit/static or implicit/dynamic grouping.</li>
 	<li>In Kubernetes, this implicit grouping is achieved via labels and label queries or label selectors.</li>
 	<li>NOTE: Every Kubernetes object has both labels and annotations. Initially they might seem redundant, but their uses are different. Labels can be queried and should provide information that serves to identify the object in some way. Annotations cannot be queried and should be used for general metadata about the object metadata that doesn't represent its identity (e.g., the icon to display next to the object when it is rendered graphically).</li>
 	<li>The second structural design within Kubernetes is that all interaction between components is driven through a centralized API surface area. An important corollary of this design is that the API that the components use is the exact same API used by every other cluster user.</li>
 	<li>There is an odd number of these nodes, since they need to keep quorum in a shared state using a Raft/Paxos algorithm for quorum.</li>
 	<li>The etcd system is at the heart of any Kubernetes cluster. It implements the key-value stores where all of the objects in a Kubernetes cluster are persisted.</li>
 	<li>The kubelet is the bridge that joins the available CPU, disk, and memory for a node into the large Kubernetes cluster.</li>
 	<li>The kube-proxy is responsible for implementing the Kubernetes Service load-balancer networking model.</li>
 	<li>Every Service in Kubernetes gets a virtual IP address, and the kube-proxy is the daemon responsible for defining and implementing the local load balancer that routes traffic from Pods on the machine to Pods, anywhere in the cluster, that implement the Service.</li>
 	<li>The KubeDNS Service is itself expressed as a Kubernetes Service, so the same routing provided by the kube-proxy routes DNS traffic to the KubeDNS containers. The one important difference is that the KubeDNS service is given a static virtual IP address. This means that the API server can program the DNS server into all of the containers that it creates, implementing the naming and service discovery for Kubernetes services.</li>
</ul>
<h2>Chapter 4: The Kubernetes API Server</h2>
<ul>
 	<li>Because all of the API server's persistent state is stored in a database that is external to the API server, the server itself is stateless and can be replicated to handle request load and for fault tolerance. Typically, in a highly available cluster, the API server is replicated three times.</li>
 	<li>it is critical that some form of log rolling be added to the API server so that it doesn't consume all available disk space.</li>
 	<li>Proxy is a specialized action that establishes a proxy network connection through the API server to network ports. There are only two resources (Pods and Services) that currently support proxy.</li>
 	<li>If you or a user are having trouble accessing parts of the Kubernetes API via a client library, the first stop should be the OpenAPI specification to understand how the API objects are modeled.</li>
 	<li>Alpha APIs are therefore disabled in production Kubernetes clusters.</li>
 	<li>Beta APIs are generally enabled in production Kubernetes clusters but should be used carefully.</li>
 	<li>After an API is marked as scheduled for removal, Kubernetes retains the API for at least three releases or one year, whichever comes first.</li>
 	<li>The API server has three different representations of the API at all times: the external representation, which is the representation that comes in via an API request; the internal representation, which is the in-memory representation of the object used within the API server for processing; and the storage representation, which is recorded into the storage layer to persist the API objects.</li>
 	<li>Generally speaking, JSON is better for human-readable and debuggable traffic on the network between client and server, but it is significantly more verbose and expensive to parse.</li>
 	<li>You may need to ensure that both the command-line tools and API server are roughly the same version or support the same authentication methods.</li>
 	<li>Authentication and RBAC determine whether the request is allowed to occur</li>
 	<li>Admission control determines whether the request is well formed and potentially applies modifications to the request before it is processed.</li>
 	<li>Admission controllers are called serially, each receiving the output of the previous one.</li>
 	<li>In general, validation is implemented as custom code that is defined per resource type.</li>
 	<li>NOTE: The API server actually supports two different streaming protocols. It supports the SPDY protocol, as well as HTTP2/WebSocket. SPDY is being replaced by HTTP2/WebSocket and thus we focus our attention on the WebSocket protocol.</li>
 	<li>The /proxy endpoint is used to port-forward network traffic between the client and containers and services running inside the cluster, without those endpoints being externally exposed.</li>
 	<li>There is little reason to use YAML for encoding for communicating with the server, but it can be convenient in a few circumstances (e.g., manually sending files to the server via curl).</li>
 	<li>Using Protocol Buffers can result in more efficient and higher throughput requests to the API servers.</li>
 	<li>The main issue with Protocol Buffers is that, because of their binary nature, they are significantly harder to visualize/debug in their wire format. Additionally, not all client libraries currently support Protocol Buffers requests or responses.</li>
 	<li>Because the API server is implemented as a RESTful server, all of the responses from the server are aligned with HTTP response codes.</li>
 	<li>The deletion of a custom resource is a little more complicated. This is because the deletion of a custom resource implies the deletion of all data associated with resources of that type. This is so that, if a CRD is deleted and then at some later date readded, the old data does not somehow get resurrected.</li>
 	<li>There are two log streams that the API server exports' the standard or basic logs, as well as the more targeted audit logs that try to capture why and how requests were made and the changed API server state. In addition, more verbose logging can be turned on for debugging specific problems.</li>
 	<li>The audit log is intended to enable a server</li>
 	<li>Administrator to forensically recover the state of the server and the series of client interactions that resulted in the current state of the data in the Kubernetes API.</li>
 	<li>Kubernetes uses the github.com/golang/glog leveled logging package for its logging. Using the --v flag on the API server you can adjust the level of logging verbosity.</li>
 	<li>In general, the Kubernetes project has set log verbosity level 2 (--v=2) as a sane default for logging relevant, but not too spammy messages.</li>
</ul>
<h2>Chapter 5: Scheduler</h2>
<ul>
 	<li>The Kubernetes scheduler is constantly scanning the API server (via a watch request) for Pods that don't have a nodeName; these are Pods that are eligible for scheduling.</li>
 	<li>In general, however, direct scheduling should be avoided, since it tends to make your application more brittle and your cluster less efficient. In the general use case, you should trust the scheduler to make the right decision, just as you trust the operating system to find a core to execute your program when you launch it on a single machine.</li>
 	<li>The first is predicates. Simply stated, a predicate indicates whether a Pod fits onto a particular node. Predicates are hard constraints, which, if violated, lead to a Pod not operating correctly (or at all) on that node.</li>
 	<li>A predicate is a node-selector label query specified by the user. In this case, the user has requested that a Pod only run on certain machines as indicated by the node labels.</li>
 	<li>The role of a priority function is to score the relative value of scheduling a Pod onto a particular node. In contrast to predicates, the priority function does not indicate whether or not the Pod being scheduled onto the node is viable it is assumed that the Pod can successfully execute on the node but instead, the predicate function attempts to judge the relative value of scheduling the Pod onto that particular node.</li>
 	<li>The basic operation of the scheduler is as follows:
<ul>
 	<li>First, the scheduler gets the list of all currently known and healthy nodes.</li>
 	<li>Then, for each predicate, the scheduler evaluates the predicate against the node and the Pod being scheduled. If the node is viable (the Pod could run on it), the node is added to the list of possible nodes for scheduling.</li>
 	<li>Next, all of the priority functions are run against the combination of Pod and node. The results are pushed into a priority queue ordered by score, with the best-scoring nodes at the top of the queue.</li>
 	<li>Then, all nodes that have the same score are popped off of the priority queue and placed into a final list. They are considered to be entirely identical, and one of them is chosen in a round-robin fashion and is then returned as the node where the Pod should be scheduled. Round robin is used instead of random choice to ensure an even distribution of Pods among identical nodes.</li>
</ul>
</li>
 	<li>A Kubernetes-descheduler project, which, if run in a Kubernetes cluster, scans it for Pods that are determined to be significantly suboptimal. If such Pods are found, the descheduler evicts the Pod from its current node.</li>
 	<li>Consequently, the Pod is rescheduled by the Kubernetes scheduler, as if it had just been created.</li>
 	<li>You should always run Pods (even singletons) via a ReplicaSet or Deployment.</li>
 	<li>Label selectors can also be used to identify a subset of the nodes in a Kubernetes cluster that should be used for scheduling a particular Pod.</li>
 	<li>Kubernetes has a default predicate that requires every node to match the nodeSelector label query, if it is present.</li>
 	<li>Node selectors are predicates' they specify a requirement, not a preference.</li>
 	<li>Pod affinity allows you to express a requirement or preference for scheduling alongside, or away from, other Pods with particular labels.</li>
 	<li>When a taint is applied to a node, the node is considered tainted and will be excluded by default from scheduling. Any tainted node will fail a predicate check at the time of scheduling.</li>
 	<li>It is important to note that, although a toleration for a taint enables a Pod to run on a tainted machine, it does not require that the Pod runs on the tainted machine. Indeed, all of the priorities run just as before and, thus, all of the machines in the cluster are available to execute on. Forcing a Pod onto a particular machine is a use case for nodeSelectors or affinity as described earlier.</li>
</ul>
<h2>Chapter 6: Installing Kubernetes</h2>
<ul>
 	<li>A production-grade deployment of Kubernetes ensures that data is secured, both during transport and at rest, that the Kubernetes components are well matched with their dependencies, that integrations with the environment are well defined, and that the configuration of all the cluster components work well together.</li>
 	<li>When it comes to installing a container runtime, you should ensure that it adheres to the Container Runtime Interface (CRI). This open standard defines the interface that the kubelet uses to speak to the runtime available on the host.</li>
 	<li>NOTE: When choosing a container runtime, be sure to reference the Kubernetes release notes. Each release will clearly indicate which container runtimes have been tested. This way you know which runtimes and versions are known to be both compatible and performant.</li>
 	<li>The kubelet is the single Kubernetes process that is managed by the host service manager. In almost all cases, this is likely to be systemd.</li>
 	<li>NOTE: Even if you are not installing the kubelet with the community-provided packages, examining the provided unit files is often be helpful for understanding common best practices for running the kubelet daemon.</li>
 	<li>NOTE: The kubeadm configuration is also accessible by standard kubectl ConfigMap interrogation and is, by convention, named the cluster-info ConfigMap in the kube-public namespace.</li>
 	<li>NOTE: Although not recommended, it is possible to sidestep the preflight checks with the --skip-preflight-checks command-line option. This should only be exercised by advanced administrators.</li>
 	<li>NOTE: At the time of this writing, kubeadm init, by itself, does not natively secure the kubeadm-managed etcd server with TLS. This basic command is only intended to configure a single control plane node and, is typically, for development purposes only.</li>
 	<li>Users that need kubeadm for production installs should provide a list of TLS-secured etcd endpoints with the --config option</li>
 	<li>In a production-grade deployment, an administrator deploys a multinode and highly available etcd cluster that sits adjacent to the Kubernetes deployment.</li>
 	<li>Although Kubernetes components are easily replaceable, etcd is not. And, as a result, etcd has a component life cycle (install, upgrade, maintenance, etc.) that is quite different. For this reason, a production Kubernetes cluster should segregate these responsibilities.</li>
 	<li>NOTE: Because kubeadm so easily creates this kubeconfig with cluster administrator credentials, many users tend to use these generated credentials for much more than their intended use. These credentials should be used only for bootstrapping a cluster. Any production deployment should always configure additional identity mechanisms</li>
 	<li>During the plan phase, kubeadm analyzes the running cluster and determines the possible upgrade paths.</li>
 	<li>You should upgrade system components consistent with the manner in which they were installed (typically with the OS package manager).</li>
 	<li>In terms of node order, ensure that you upgrade the control plane nodes first and then perform the upgrades on each worker node.</li>
 	<li>Control plane nodes should be unregistered as upstreams for any front-facing load balancers, upgraded, and then, after the entire control plane has been successfully upgraded, all control plane nodes should be re-registered as upstreams with the load balancer. This may introduce a short-lived period of time when the API is unavailable, but it ensures that all clients have a consistent experience.</li>
</ul>
<h2>Chapter 7: Authentication and User Management</h2>
<ul>
 	<li>The first two phases of servicing an API request (authentication and access control) focus on what we know about a user.</li>
 	<li>How you manage your users should remain consistent across your organization, regardless of the systems consuming it.</li>
 	<li>Just as with many well-designed REST-based APIs, there are multiple strategies that Kubernetes can employ for authenticating users. We can think about each of these strategies as belonging to one of three major groups:
<ul>
 	<li>Basic Authentication</li>
 	<li>X.509 client certificates</li>
 	<li>Bearer tokens</li>
</ul>
</li>
 	<li>Since base64 is merely a hash and provides no level of encryption for the transmitted credentials, it is imperative that Basic Authentication be used in conjunction with HTTPS.</li>
 	<li>Since the API server does not currently monitor this file for changes, whenever a user is added, removed, or updated, the API server needs to be restarted in order for these changes to take effect.</li>
 	<li>When installing Kubernetes in a production-quality manner, we want to be sure that not only are user-initiated requests transmitted securely, but also that service-to-service communication is encrypted.</li>
 	<li>If certificates are chosen as an authentication option, administrators should, minimally, be sure that this process is automated in some fashion and that this automation includes a process for rotating certificates over time.</li>
 	<li>These tokens are authenticated with a Hash-based Message Authentication Code (HMAC) and are not encrypted. So, again, be sure that all communication including JWT is encrypted, preferably with TLS.</li>
 	<li>With OIDC, the end user authenticates against our mutually trusted identity provider and then use the tokens she has received to subsequently prove her identity to the API server.</li>
 	<li>NOTE: If there was an error in authenticating the user for some reason, the service may also respond with an error string field as a sibling to authenticated.</li>
 	<li>Dex provides a standards-compliant OIDC frontend to a variety of common backends. There is support for LDAP, Active Directory, SQL, SAML, and even SaaS providers, such as GitHub, GitLab, and LinkedIn.</li>
 	<li>Note that when multiple authentication plug-ins are active at the same time, the first plug-in to successfully authenticate a user will shortcircuit the authentication process.</li>
 	<li>Remember that, if you do embed credentials into this configuration file, they may be used by anyone who has access to this file. Treat this file as if it were a highly sensitive password, because it effectively is.</li>
 	<li>You can think of ServiceAccounts as namespaced user accounts for all Pod resources.</li>
 	<li>Every Pod that is launched has an associated ServiceAccount.</li>
 	<li>If none is specified in the Pod manifest, a default ServiceAccount is used. This default ServiceAccount is available on a namespace-wide basis and is automatically created when a namespace is.</li>
</ul>
<h2>Chapter 8: Authorization</h2>
<ul>
 	<li>Those who have encountered REST before will be familiar with the four most basic verbs: Create, Read, Update, and Delete (CRUD). These four actions map directly to the HTTP verbs POST, GET, PUT, and DELETE, respectively, and in turn, make up the vast majority of HTTP requests normally found on the internet.</li>
 	<li>At the time of this writing, there are six authorization modules that may be configured.</li>
 	<li>Put succinctly, Kubernetes maps the attributes of the UserInfo object to the resources and verbs that the user should have access to.</li>
 	<li>With RBAC, we can only grant actions, and this module otherwise denies by default.</li>
 	<li>If we want to grant a permission that has cross-namespace capabilities, we use the ClusterRole resource.</li>
 	<li>ClusterRoles are typically employed for two primary use cases - to easily grant cluster administrators a wide degree of freedom or to grant very specific permissions to a Kubernetes controller.</li>
 	<li>Also understand that some rights grant implicit - and perhaps unintentional - rights to other resources. In particular, you should know that granting create rights to a Pod effectively grants read access to more sensitive and related resources, like Secrets. Because Secrets may be mounted or exposed via environment variables to a Pod, the Pod create rights allows a Pod owner to read those Secrets unencrypted.</li>
 	<li>Policies alone are useless unless they are applied to a user or a group.</li>
 	<li>Remember that ServiceAccounts supply the Kubernetes API credentials for all running Pod processes. Every Pod has an associated ServiceAccount, regardless of whether we specify which serviceAccountName to use in the Pod manifest. Left unattended, this could pose a significant security concern.</li>
 	<li>This concern can be largely mitigated with RBAC policies. Since RBAC policies are default deny, we recommended that any Pod that requires API capabilities have its own (or possibly shared) ServiceAccount with an associated fine-grained RBAC policy.</li>
</ul>
<h2>Chapter 9: Admission Control</h2>
<ul>
 	<li>Admission control is the third phase of API request onboarding. By the time we have reached this phase of an API request life cycle, we have already determined that the request has come from a real, authenticated user and that the user is authorized to perform this request.</li>
 	<li>NOTE: Prior to Kubernetes 1.10, the order in which admission controllers were specified mattered. With the introduction of the --enable-admission-plugins command-line parameter, this is no longer the case. For versions 1.9 and earlier, you should use the order-dependent --admission-control parameter.</li>
 	<li>The admission controllers available out of the box from Kubernetes have two primary goals: ensuring that sane defaults are utilized in the absence of user-specified values, and ensuring that users do not have more capabilities than they need.</li>
 	<li>When PodSecurityPolicies are enabled, users are unable to onboard new Pods unless there are authorized policies in place.</li>
 	<li>In production multiuser environments, administrators should use most of the policies offered by PodSecurityPolicies, since these significantly improve overall cluster security.</li>
 	<li>NOTE: Since PodSecurityPolicys are implemented as an admission controller (which enforces policy during the API request flow) Pods that have been scheduled prior to PodSecurityPolicy being enabled may no longer conform. Keep this in mind, since restarts of those Pods may render them unable to be scheduled. Ideally, the PodSecurityPolicy admission controller is enabled at installation time.</li>
 	<li>Generally speaking, it is good practice to enforce quotas on your cluster. Quotas ensure that no one user is able to utilize more than she has been allocated and is a critical component in driving overall cluster utilization.</li>
 	<li>Note, too, that when a quota is defined for a namespace, all Pod definitions (even if originating from another resource, such as Deployments or ReplicaSets) are required to specify resource requests and limits.</li>
 	<li>It is also possible to place quotas on the number of distinct Kubernetes resources (e.g., Pods, Deployments, Jobs, and more) within a Namespace.</li>
 	<li>Complementary to ResourceQuota, the LimitRange admission controller is necessary if you have defined any LimitRange policies against a Namespace.</li>
 	<li>A LimitRange, put simply, allows you to place default resource limits for Pods that are declared as a member of a particular Namespace.</li>
 	<li>When quotas are enabled, a user who has not defined resource limits on her Pod has her request rejected.</li>
 	<li>With the LimitRange admission controller, a Pod with no resource limits defined is, instead, given defaults (as defined by the administrator) and the Pod is accepted.</li>
 	<li>There are two types of dynamic admission control: validating and mutating.</li>
 	<li>With validating admission control, our business logic simply accepts or rejects a user's request, based upon our requirements.</li>
 	<li>In the mutating admission controller case, we are again evaluating requests against the API server, but in this case we are selectively altering the declaration to meet our objectives.</li>
 	<li>NOTE: Note that Dynamic Admission Control, although extraordinarily powerful, is still somewhat early in its maturity cycle. These features were alpha as of 1.8 and beta in 1.9.</li>
 	<li>As API requests may contain sensitive information, all traffic should be encrypted.</li>
 	<li>WARNING: Exercise care when modifying resources at runtime, since there may be existing logic that depends on well-defined and/or previously defined values. A general rule of thumb is to only set previously unset fields. Always avoid altering any namespaced values (e.g., resource annotations).</li>
 	<li>With mutating webhooks, we have an extremely powerful tool for standardizing our user's declarations. Use this power with caution.</li>
</ul>
<h2>Chapter 10: Networking</h2>
<ul>
 	<li>Although there are multiple aspects to networking within Kubernetes, the role of CNI is simply to facilitate Pod-to-Pod connectivity.</li>
 	<li>In addition to connecting a container to a network, CNI has capabilities for IP Address Management (IPAM). IPAM ensures that CNI always has a clear picture of which addresses are in use, as well as those that are available for configuration of new interfaces.</li>
 	<li>Not every plug-in provides support for NetworkPolicy. Be sure to evaluate the features that are offered by the plug-in before you deploy your cluster.</li>
 	<li>NOTE: The CNI is not the only mechanism for enforcing mutual TLS between Pods. With a sidecar pattern called service mesh, cluster administrators can require that workloads only communicate by a TLS-enabled local proxy. Service mesh not only provides end-to-end encryption but may also enable higher-level features, such as circuit breaking, blue/green deployments, and distributed tracing. It may also be enabled transparently for the end user.</li>
 	<li>With the Service resource, we assign a virtual IP for network services exposed by a collection of Pods. The backing Pods are discovered and connected using a Pod selector.</li>
 	<li>In the most common scenario, kube-proxy is simply manipulating iptables rules on every node.</li>
 	<li>NOTE: iptables is the implementation most commonly found in the wild. With Kubernetes 1.9, a new IP Virtual Server (IPVS) implementation has been added. This is not only more performant but also affords a variety of load-balancing algorithms that may be utilized.</li>
 	<li>The CoreDNS controller uses CoreDNS as its implementation, and kube-dns leverages dnsmasq.</li>
 	<li>NOTE: Headless Services are ClusterIP Services with clusterIP=None. These are used when you would like to define a Service but do not require that it be managed by kube-proxy. Since you will still have access to the endpoints for the Service, you can leverage this if you would like to implement your own Service discovery mechanisms.</li>
 	<li>In addition to DNS, a lesser-used feature but one to be aware of nonetheless is Service discovery using automatically injected environment variables.</li>
 	<li>Because the process environment is populated at Pod startup time, any Service discovery using this method requires that the necessary Service resources are defined before the Pod is. This method does not account for any updates to a Service after the Pod has been started.</li>
 	<li>Kubernetes provides the NetworkPolicy resource for users to define layer 3 and layer 4 rules as they pertain to their own workloads. The NetworkPolicy resource offers both ingress and egress rules that can be applied to namespaces, Pods, and even regular CIDR blocks.</li>
 	<li>NOTE: Note that NetworkPolicy can only be defined in environments where the CNI plug-in supports this functionality. The Kubernetes API server will gladly accept your NetworkPolicy declaration, but since there is no controller to reconcile the declared state, no policies will be enacted.</li>
 	<li>NOTE: It is important to note that, by default, there are no network restrictions for Pods. It is only through NetworkPolicy that we can begin to lock down Pod interconnectivity.</li>
 	<li>A service mesh is simply a collection of â€œsmartâ€ proxies that can help users with a variety of east-west or Pod-to-Pod networking needs. These proxies may operate as sidecar containers in the application Pods or may operate as DaemonSets, where they are node-local infrastructure components that may be utilized by any of the Pods on a given node. Simply configure your Pods to proxy their traffic to these service mesh proxies (typically with environment variables), and your Pods are now a part of the mesh.</li>
 	<li>NOTE: Whether you deploy as a sidecar or as a DaemonSet is typically determined by the service mesh technology that you choose and/or the availability of resources on your cluster. Since these proxies run as Pods, they do consume cluster resources and, as such, you need to make decisions about whether these resources should be shared or associated with a Pod.</li>
</ul>
<h2>Chapter 11: Monitoring Kubernetes</h2>
<ul>
 	<li>In many cases, the cluster itself appears to be operating correctly, but it is actual failing. This points to the importance of not just monitoring the cluster pieces but also monitoring the cluster functionality that users require.</li>
 	<li>Whitebox monitoring looks at signals that applications produce and uses these signals to find problems.</li>
 	<li>Blackbox or probe monitoring uses the public interfaces (e.g., Kubernetes) to take actions with known expected outcomes (e.g., "Create a ReplicaSet of size three leads to three pods") and fires alerts if the expected outcome does not occur.</li>
 	<li>Although live site incidents are an inevitable part of running a Service, customer-reported incidents should be nonexistent in a well-monitored system.</li>
 	<li>The ability to observe, visualize, and query your monitoring data is a critical tool in determining what problems are happening and in identifying problems before they become incidents.</li>
 	<li>Logging records events (e.g., a Pod being created or an API call failing), and monitoring records statistics (e.g., the latency of a particular request, the CPU used by a process, or the number of requests to a particular endpoint). Logged records, by their nature, are discrete, whereas monitoring data is a sampling of some continuous value.</li>
 	<li>It is worth noting that neither logging nor monitoring alone are sufficient to understand your cluster. Monitoring data can give you a good sense of the overall health of your cluster and can help you identify anomalous events that may be occuring. Logging, on the other hand, is critical for diving in and understanding what is actually happening, possibly across many machines, to cause such anomalous behavior.</li>
 	<li>Every server in Kubernetes exposes monitoring data via an HTTP(S) endpoint that serves the monitored data using the Prometheus protocol.</li>
 	<li>Most installations of Kubernetes set the verbosity at two, which is also the default. This produces a good balance between verbosity and spam.</li>
 	<li>NOTE: Setting the verbosity of your logs to a higher level increases visibilty, but it comes at a price both financially and in terms of performance. Because the absolute number of logs is higher, it increases storage and retention costs and can make your querying slower. When increasing the logging level, generally only do it for a short period of time and be sure that you bring the logging back to a standard level as soon as possible.</li>
 	<li>How long you retain monitoring data depends on the needs of your system and the costs you're willing to pay, in terms of storage space for the data. However, in our experience, the minimum you should have is 30-45 days' worth of data.</li>
 	<li>One important question when running InfluxDB is whether to run it as a container on the Kubernetes cluster itself. In general, this is not a recommended setup. You are using InfluxDB to monitor the cluster, so you want monitoring data to continue to be accessible, even if the cluster itself is having problems.</li>
 	<li>When assembling monitoring information, as with nearly all software, it is valuable to take a layered approach. The layers to monitor are machines, cluster basics, cluster add-ons, and finally, user applications. In this way, beginning with the basics, each layer in the monitoring stack builds on top of the layer below it.</li>
 	<li>The value of blackbox monitoring is that it gives you a very clear signal about the health of your system. The downside is that it gives you very little visibility into why your system has failed.</li>
 	<li>All of the pieces of the Kubernetes infrastructure expose metrics using the Prometheus API, and there is also a Kubernetes Service discovery that you can use to automatically discover and monitor the Kubernetes components in your cluster.</li>
 	<li>If you choose to monitor the cluster from within the cluster, it is essential to also have a "watchdog alert" that fires if a prober hasn't been run to completion in the previous N minutes.</li>
 	<li>Constructing a high-quality alerting and monitoring stack should be one of the very first priorities after a cluster is successfully set up.</li>
</ul>
<h2>Chapter 12: Disaster Recovery</h2>
<ul>
 	<li>Naturally, designing a foolproof system is an impossibility, but we should always build with the worst-case scenarios in mind.</li>
 	<li>We recommend that your etcd backing store is deployed in a three- or five-node cluster configuration.</li>
 	<li>NOTE: Understand that a failure of the Kubernetes control plane typically does not affect the data plane. In other words, if your API server, controller manager, or scheduler fails, your Pods will often continue to operate as they are. In most scenarios, you simply are not able to effect change on the cluster until the control plane is brought back online.</li>
 	<li>Particularly important in high-churn clusters, kubectl cordon renders a node unschedulable. This can help stem the tide of new Pods affecting our ability to perform a recovery action on a worker node.</li>
 	<li>The kubectl drain command allows us to remove and reschedule all running Pods from a target node. This is useful in scenarios where we intend to remove a node from the cluster.</li>
 	<li>You need to be sure that etcd has been quiesced, typically by stopping the etcd process on the etcd member where you intend to perform the backup. Further, to ensure that all in-flight data has been saved, you need to be sure to first freeze the underlying filesystem.</li>
 	<li>The most common approach, albeit resulting in slightly longer recovery times, is to utilize the native etcd command-line tools when backing up by either method, be cognizant of the fact that you are backing up the entire etcd keyspace. It is a complete copy of the state of etcd at the time of backup.</li>
 	<li>Just as with any type of database backup, if the consuming application (in our case, Kubernetes itself) is not quiesced during backup, there may be transient state that has not been consistently applied to the backing store.</li>
 	<li>If you have enabled any Kubernetes Aggregate API servers or have used an etcd-backed Calico implementation (both of which use their own etcd instances), these would not be backed up if you have only targeted the cluster's primary etcd endpoints.</li>
 	<li>What makes Ark different from the methods we have already described is that it is Kubernetes aware. Instead of blindly backing up etcd data, Ark performs backups by way of the Kubernetes API itself. This ensures that the data is always consistent, and it allows for more selective backup strategies.</li>
 	<li>With partial restoration, Ark allows you to prioritize which resources are restored.</li>
 	<li>Be sure to regularly exercise your ability to completely restore your production systems with fully automated solutions.</li>
</ul>
<h2>Chapter 13: Extending Kubernetes</h2>
<ul>
 	<li>The four types of extensibility are:
<ul>
 	<li>Cluster daemons for automation</li>
 	<li>Cluster assistants for extended functionality</li>
 	<li>Extending the life cycle of the API server</li>
 	<li>Adding more APIs</li>
</ul>
</li>
 	<li>Cluster daemons have two defining characteristics. The agent needs to run on the Kubernetes cluster itself, and the agent needs to add functionality to the cluster that is automatically provided to all users of the cluster without any action on their part.</li>
 	<li>Typically, these cluster daemons run in a dedicated Namespace so that they are not accessible to users of the cluster</li>
 	<li>Thus, any application that is run within a Kubernetes cluster with a Prometheus cluster agent automatically has metrics collected without any configuration or enablement by the developer.</li>
 	<li>When you run Prometheus within a Kubernetes cluster and configure it to do Kubernetes-based Service discovery, it operates as a cluster daemon and automatically scans all Pods in the cluster for metrics that it should ingest.</li>
 	<li>The less developers have to learn but can instead inherit automatically from their environment, the more likely their applications are to be reliable and secure.</li>
 	<li>You cannot just install a cluster daemon on a whim or because of a user's request. You must be fully committed to operational management and support of that cluster daemon for the lifetime of the cluster.</li>
 	<li>The automatic nature of cluster add-ons is a double-edged sword. Users will quickly come to rely on them, and thus the operational importance of cluster daemon add-ons can be significant.</li>
 	<li>Rather than providing automatic experiences, cluster assistants provide enriched, yet easily accessible, functionality to users of the cluster, but it is functionality that the user must be aware of and must provide appropriate information to enable.</li>
 	<li>Placing code in the API server call path should be done carefully and with monitoring, thought, and planning to ensure that there are not any unanticipated consequences.</li>
 	<li>Most API extensions use custom resource definitions.</li>
 	<li>You need to combine the Kubernetes CustomResourceDefinition with a controller application that watches these custom definitions and then takes action based on resources that the user creates, updates, or destroys.</li>
 	<li>Because a custom resource is a more complicated extension, generally speaking, the Kubernetes configuration consists of multiple objects packaged into a single YAML file.</li>
 	<li>WARNING: When a CustomResourceDefinition is deleted, all of the corresponding resources are also deleted from the cluster's data store. They cannot be recovered. So, when deleting a custom resource, be careful and make sure to communicate with all end users of that resource before you delete the CustomResourceDefinition.</li>
 	<li>There is significant additional complexity for custom resource definitions' they use the same storage associated with all of the built-in Kubernetes API objects. As a result, it is possible to impact your API server and cluster operation by storing objects too large and/or numerous in the API server using custom resources.</li>
 	<li>In general, API objects in Kubernetes are intended to be simple configuration objects. They're not intended to represent large data files.</li>
</ul>
<h2>Chapter 14: Conclusions</h2>
<ul>
 	<li>None</li>
</ul>
