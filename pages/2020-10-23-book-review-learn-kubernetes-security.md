---
layout: page
title: Book Review: Learn Kubernetes Security
date: 2020-10-23 13:21
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/10/LearnKubernetesSecurity-BookCover.jpg"><img class="alignleft wp-image-33618 size-medium" src="/wp-content/uploads/2020/10/LearnKubernetesSecurity-BookCover-243x300.jpg" alt="" width="243" height="300" /></a>Recently, I finished reading <a href="https://www.amazon.ca/Learn-Kubernetes-Security-orchestrate-microservices/dp/1839216506/ref=sr_1_1_sspa?dchild=1&amp;keywords=learn+kubernetes+security&amp;qid=1603113103&amp;sr=8-1-spons&amp;psc=1&amp;spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEzVDFLVUhaT0RHNUIwJmVuY3J5cHRlZElkPUEwODM3Mjc5MTdCM1A4U0c2Mk4zRyZlbmNyeXB0ZWRBZElkPUEwMjYzMDYxMURBNDBIMVk1S0c2MyZ3aWRnZXROYW1lPXNwX2F0ZiZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=" target="_blank" rel="noopener noreferrer">Learn Kubernetes Security</a> by Kaizhe Huang and Pranjal Jumde.

I've recently been ramping up on Kubernetes, so, I have some previous knowledge and hands-on experience with Kubernetes when I read this book.

I found<span style="color: #000000;"> the whole book quite helpful and in particular Chapter 1 ("<strong>Kubernetes Architecture</strong>") and Chapter 2 ("<strong>Kubernetes Networking</strong>") provide a great overview of core Kubernetes concepts, in a clear and concise way. </span>

<span style="color: #000000;"> Chapter 6 ("<strong>Securing Cluster Components</strong>") was an amazingly detailed chapter, where it provides a breakdown of each Kubernetes component, and the best practices around security. I highlighted practically the entire chapter! Similarly, Chapter 8 ("<strong>Securing Kubernetes Pods</strong>"), has a lot of details for security from the Pod perspective. </span>

<span style="color: #000000;">I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).</span>

<span style="color: #000000;">If my highlights peak your interest, I strongly recommend that you pick up a copy for yourself.</span>
<h2>Chapter 1: Kubernetes Architecture</h2>
<ul>
 	<li>With a dedicated network namespace, processes cannot communicate with other processes without a proper network configuration, even though they're running on the same node.</li>
 	<li>There are two types of nodes: master nodes and worker nodes. The main control plane, such as kube-apiserver, runs on the master nodes. The agent running on each worker node is called kubelet, working as a minion on behalf of kube-apiserver, and runs on the worker nodes.</li>
 	<li>A master node generally has kube-apiserver, etcd storage, kube-controller-manager, cloud-controller-manager, and kube-scheduler.</li>
 	<li>The worker nodes have kubelet, kube-proxy, a Container Runtime Interface (CRI) component, a Container Storage Interface (CRI) component, and so on.
<ul>
 	<li><strong>kube-apiserver:</strong> The Kubernetes API server (kube-apiserver) is a control-plane component that validates and configures data for objects such as pods, services, and controllers.</li>
 	<li><strong>etcd:</strong> etcd is a high-availability key-value store used to store data such as configuration, state, and metadata.</li>
 	<li><strong>kube-scheduler:</strong> kube-scheduler is a default scheduler for Kubernetes. It watches for newly created pods and assigns pods to the nodes.</li>
 	<li><strong>kube-controller-manager:</strong> The Kubernetes controller manager is a combination of the core controllers that watch for state updates and make changes to the cluster accordingly.</li>
 	<li><strong>cloud-controller-manager:</strong> The cloud container manager was introduced in v1.6; it runs controllers to interact with the underlying cloud providers. This is an attempt to decouple the cloud vendor code from the Kubernetes code.</li>
 	<li><strong>kubelet:</strong> kubelet runs on every node. It registers the node with the API server. kubelet monitors pods created using Podspecs and ensures that the pods and containers are healthy.</li>
 	<li><strong>kube-proxy:</strong> kube-proxy is a networking proxy that runs on each node. It manages the networking rules on each node and forwards or filters traffic based on these rules.</li>
 	<li><strong>kube-dns:</strong> DNS is a built-in service launched at cluster startup. With v1.12, CoreDNS became the recommended DNS server, replacing kube-dns.</li>
</ul>
</li>
 	<li>kubenet only supports 50 nodes per cluster, which obviously cannot meet any requirements of large-scale deployment.</li>
 	<li>Kubernetes leverages a Container Networking Interface (CNI) as a common interface between the network providers and Kubernetes' networking components to support network communication in a cluster with a large scale.</li>
 	<li>The container storage interface provides an interface for exposing arbitrary blocks and file storage to Kubernetes.</li>
 	<li>At the lowest level of Kubernetes, container runtimes ensure containers start, work, and stop. The most popular container runtime is Docker.</li>
 	<li>A pod is a basic building block of a Kubernetes cluster. It's a group of one or more containers that are expected to co-exist on a single host. Containers within a pod can reference each other using localhost or inter-process communications (IPCs).</li>
 	<li>Kubernetes deployments help scale pods up or down based on labels and selectors. The YAML spec for a deployment consists of replicas, which is the number of instances of pods that are required, and template, which is identical to a pod specification.</li>
 	<li>A Kubernetes service is an abstraction of an application. A service enables network access for pods. Services and deployments work in conjunction to ease the management and communication between different pods of an application.</li>
 	<li>It is better to use deployments over replica sets. Deployments encapsulate replica sets and pods. Additionally, deployments provide the ability to carry out rolling updates.</li>
 	<li>Namespaces help a physical cluster to be divided into multiple virtual clusters. Multiple objects can be isolated within different namespaces. Default Kubernetes ships with three namespaces: default, kube-system, and kube-public.</li>
 	<li>Pods that need to interact with kube-apiserver use service accounts to identify themselves. By default, Kubernetes is provisioned with a list of default service accounts: kube-proxy, kube-dns, node-controller, and so on.</li>
 	<li>The pod security policy is a cluster-level resource that defines a set of conditions that must be fulfilled for a pod to run on the system.</li>
 	<li>These policies must be accessible to the requesting user or the service account of the target pod to work.</li>
 	<li>There is another thing that OpenShift projects do better than kubernetes namespaces when creating a project in OpenShift, you can modify the project template and add extra objects, such as NetworkPolicy and default quotas, to the project that are compliant with your company's policy.</li>
 	<li>Kubedex (<a href="https://kubedex.com/google-gke-vs-microsoft-aks-vs-amazon-eks/" target="_blank" rel="noopener noreferrer">https://kubedex.com/google-gke-vs-microsoft-aks-vs-amazon-eks/</a>) have carried out a great comparison of the cloud Kubernetes services.</li>
</ul>
<h2>Chapter 2: Kubernetes Networking</h2>
<ul>
 	<li>The beauty of this design is that it offers a clean, backward-compatible model where pods act like Virtual Machines (VMs) or physical hosts from the perspective of port allocation, naming, service discovery, load balancing, application configuration, and migration.</li>
 	<li>The Kubernetes service is the one that surfaces the internal application to the public.</li>
 	<li>The IP address assigned to each pod is a private IP address or a cluster IP address that is not publicly accessible.</li>
 	<li>Containers inside the same pod share at least the same IPC namespace and network namespace; as a result, K8s needs to resolve potential conflicts in port usage.</li>
 	<li>Despite the lack of activity, the Pause container plays a critical role in the pod. It serves as a placeholder to hold the network namespace for all other containers in the same pod.</li>
 	<li>The Kubernetes service is an abstraction of a grouping of sets of pods with a definition of how to access the pods.</li>
 	<li>The reason to call it a virtual IP address is that, from a node's perspective, there is neither a namespace nor a network interface bound to a service as there is with a pod.</li>
 	<li>So, what kube-proxy does to solve the two problems mentioned earlier is that it forwards all the traffic whose destination is the target service (the virtual IP) to the pods grouped by the service (the actual IP); meanwhile, kube-proxy watches the Kubernetes control plane for the addition or removal of the service and endpoint objects (pods).</li>
 	<li>By default, kube-proxy in user space mode uses a round-robin algorithm to choose which backend pod to forward the requests to.</li>
 	<li>kube-proxy in the iptables proxy mode is only responsible for maintaining and updating the iptables rules. Any traffic targeted to the service IP will be forwarded to the backend pods by netfilter, based on the iptables rules managed by kube-proxy.</li>
 	<li>The disadvantage of this mode is the error handling required. For a case where kube-proxy runs in the iptables proxy mode, if the first selected pod does not respond, the connection will fail. While in the user space mode, however, kube-proxy would detect that the connection to the first pod had failed and then automatically retry with a different backend pod.</li>
 	<li>Services are usually defined with a selector, which is a label attached to pods that need to be in the same service. A service can be defined without a selector.</li>
 	<li>A service can have four different types, as follows:
<ul>
 	<li><strong>ClusterIP:</strong> This is the default value. This service is only accessible within the cluster.</li>
 	<li><strong>NodePort:</strong> This service is accessible via a static port on every node. NodePorts expose one service per port and require manual management of IP address changes.</li>
 	<li><strong>LoadBalancer:</strong> This service is accessible via a load balancer. A node balancer per service is usually an expensive option.</li>
 	<li><strong>ExternalName:</strong> This service has an associated Canonical Name Record (CNAME) that is used to access the service.</li>
</ul>
</li>
 	<li>Ingress is a smart router that provides external HTTP/HTTPS (short for HyperText Transfer Protocol Secure) access to a service in a cluster. Services other than HTTP/HTTPS can only be exposed for the NodePort or LoadBalancer service types.</li>
 	<li>Ingress objects have five different variations, listed as follows:
<ul>
 	<li><strong>Single-service Ingress:</strong> This exposes a single service by specifying a default backend and no rules</li>
 	<li><strong>Simple fanout:</strong> A fanout configuration routes traffic from a single IP to multiple services based on the Uniform Resource Locator (URL)</li>
 	<li><strong>Name-based virtual hosting:</strong> This configuration uses multiple hostnames for a single IP to reach out to different services</li>
 	<li><strong>Transport Layer Security (TLS):</strong> A secret can be added to the ingress spec to secure the endpoints</li>
 	<li><strong>Load balancing:</strong> A load balancing ingress provides a load balancing policy, which includes the load balancing algorithm and weight scheme for all ingress objects.</li>
</ul>
</li>
 	<li>The CNI specification is only concerned with the network connectivity of containers and removing allocated resources when the container is deleted.
<ul>
 	<li>First, from a container runtime's perspective, the CNI spec defines an interface for the Container Runtime Interface (CRI) component (such as Docker) to interact with</li>
 	<li>Secondly, from a Kubernetes network model's perspective, since CNI plugins are actually another flavor of Kubernetes network plugins, they have to comply with Kubernetes network model requirements</li>
</ul>
</li>
 	<li>The network policy implementation is not required in the CNI specification, but when DevOps choose which CNI plugins to use, it is important to take security into consideration. Alexis Ducastel's article (<a href="https://itnext.io/benchmark-results-of-kubernetes-network-plugins-cni-over-10gbit-s-network-36475925a560" target="_blank" rel="noopener noreferrer">https://itnext.io/benchmark-results-of-kubernetes-network-plugins-cni-over-10gbit-s-network-36475925a560</a>) did a good comparison of the mainstream CNI plugins with the latest update in April 2019.</li>
 	<li>Here are a few things about Calico worth highlighting:
<ul>
 	<li>Calico provides a flat IP network, which means there will be no IP encapsulation appended to the IP message (no overlays). Also, this means that each IP address assigned to the pod is fully routable. The ability to run without an overlay provides exceptional throughput characteristics.</li>
 	<li>Calico has better performance and less resource consumption, according to Alexis Ducastel's experiments. Calico offers a more comprehensive network policy compared to Kubernetes' built-in network policy.</li>
 	<li>Kubernetes' network policy can only define whitelist rules, while Calico network policies can define blacklist rules (deny).</li>
</ul>
</li>
</ul>
<h2>Chapter 3: Threat Modeling</h2>
<ul>
 	<li>Threat modeling involves identifying threats, understanding the effects of each threat, and finally developing a mitigation strategy for every threat.</li>
 	<li>After a successful threat modeling session, you're able to define the following:
<ul>
 	<li><strong>Asset:</strong> A property of an ecosystem that you need to protect.</li>
 	<li><strong>Security control:</strong> A property of a system that protects the asset against identified risks. These are either safeguards or countermeasures against the risk to the asset.</li>
 	<li><strong>Threat actor:</strong> A threat actor is an entity or organization including script kiddies, nation-state attackers, and hacktivists who exploit risks.</li>
 	<li><strong>Attack surface:</strong> The part of the system that the threat actor is interacting with. It includes the entry point of the threat actor into the system.</li>
 	<li><strong>Threat:</strong> The risk to the asset.</li>
 	<li><strong>Mitigation:</strong> Mitigation defines how to reduce the likelihood and impact of a threat to an asset.</li>
</ul>
</li>
 	<li>The industry usually follows one of the following approaches to threat modeling:
<ul>
 	<li><strong>STRIDE:</strong> The STRIDE model was published by Microsoft in 1999. It is an acronym for Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Escalation of Privilege. STRIDE models threats to a system to answer the question, 'What can go wrong with the system?'</li>
 	<li><strong>PASTA:</strong> Process for Attack Simulation and Threat Analysis is a risk-centric approach to threat modeling. PASTA follows an attacker-centric approach, which is used by the business and technical teams to develop asset-centric mitigation strategies.</li>
 	<li><strong>VAST:</strong> Visual, Agile, and Simple Threat modeling aims to integrate threat modeling across application and infrastructure development with SDLC and agile software development. It provides a visualization scheme that provides actionable outputs to all stakeholders such as developers, architects, security researchers, and business executives.</li>
</ul>
</li>
 	<li>It is worth noting that only kube-apiserver communicates with etcd. Other Kubernetes components such as kube-scheduler, kube-controller-manager, and cloud-controller manager interact with kube-apiserver running in the master nodes in order to fulfill their responsibilities. On the worker nodes, both kubelet and kube-proxy communicate with kube-apiserver.</li>
 	<li>Neither data in transit nor at rest is encrypted by default in etcd.</li>
 	<li>DaemonSet basically means the microservice will run inside a pod in every node.</li>
 	<li>Note that not all communication between components is secure by default. It depends on the configuration of those components.</li>
 	<li>Also, note that kube-apiserver and etcd are the brain and heart of a Kubernetes cluster. If either of them were to get compromised, that would be game over.</li>
 	<li>Trail of Bits and Atredis Partners have done a good job on Kubernetes components' threat modeling. Their whitepaper highlights in detail the threats in each Kubernetes component. You can find the whitepaper at <a href="https://github.com/kubernetes/community/blob/master/wg-security-audit/findings/Kubernetes%20Threat%20Model.pdf" target="_blank" rel="noopener noreferrer">https://github.com/kubernetes/community/blob/master/wg-security-audit/findings/Kubernetes%20Threat%20Model.pdf</a>.</li>
</ul>
<h2>Chapter 4: Applying the Principle of Least Privilege in Kubernetes</h2>
<ul>
 	<li>Kubernetes supports both ABAC and RBAC. Though ABAC is powerful and flexible, the implementation in Kubernetes makes it difficult to manage and understand. Thus, it is recommended to enable RBAC instead of ABAC in Kubernetes.</li>
 	<li>Users in the system:master group have the cluster-admin role granted, meaning they can manage the entire Kubernetes cluster, while users in the system:kube-proxy group can only access the resources required by the kube-proxy component.</li>
 	<li>From version 1.6 onward, RBAC is enabled by default in Kubernetes. Before version 1.6, RBAC could be enabled by running the Application Programming Interface (API) server with the --authorization-mode=RBAC flag.</li>
 	<li>Pods authenticate to the kube-apiserver object using a service account. Service accounts are created using API calls. They are restricted to namespaces and have associated credentials stored as secrets. By default, pods authenticate as a default service account.</li>
 	<li>To ensure least privilege, cluster administrators should associate every Kubernetes resource with a service account with least privilege to operate.</li>
 	<li>In Kubernetes, there are no deny permissions. Thus, a role is an addition of a set of permissions.</li>
 	<li>By default, Kubernetes has three different namespaces. The three namespaces are described as follows:
<ul>
 	<li>default: A namespace for resources that are not part of any other namespace.</li>
 	<li>kube-system: A namespace for objects created by Kubernetes such as kube-apiserver, kube-scheduler, controller-manager, and coredns.</li>
 	<li>kube-public: Resources within this namespace are accessible to all. By default, nothing will be created in this namespace.</li>
</ul>
</li>
 	<li>In Kubernetes, not all objects are namespaced. Lower-level objects such as Nodes and persistentVolumes span across namespaces.</li>
 	<li>A user in Kubernetes is for humans, while a service account is for microservices in pods.</li>
 	<li>In order to implement least privilege for Kubernetes subjects, you may ask yourself the following questions before you create a Role or RoleBinding object in Kubernetes:
<ul>
 	<li><strong>Does the subject need privileges for a namespace or across namespaces?</strong> This is important because once the subject has cluster-level privileges it may be able to exercise the privileges across all namespaces.</li>
 	<li><strong>Should the privileges be granted to a user, group, or service account?</strong> When you grant a role to a group, it means all the users in the group will automatically get the privileges from the newly granted role. Be sure you understand the impact before you grant a role to a group. Also, note that some microservices do not need any privilege at all as they don't interact with kube-apiserver or any Kubernetes objects directly.</li>
 	<li><strong>What are the resources that the subjects need to access?</strong> When creating a role, if you don't specify the resource name or do set * in the resourceNames field, it means access is granted to all the resources of the resource type.</li>
</ul>
</li>
 	<li>Besides accessing kube-apiserver to operate Kubernetes objects, processes in a pod can also access resources on the worker nodes and other pods/microservices in the clusters.</li>
 	<li>Configuring the pod/container security context should be on the developers' task list (with the help of security design and review), while pod security policies the other way to limit pod/container access to system resources at the cluster level should be on DevOps's to-do list.</li>
 	<li>It is highly recommended not to run your microservice as a root user (UID = 0) in containers. The security implication is that if there is an exploit and a container escapes to the host, the attacker gains the root user privileges on the host immediately.</li>
 	<li>Note that AllowPrivilegeEscalation is always true when the container is either running as privileged or has a CAP_SYS_ADMIN capability.</li>
 	<li>It's always a good practice to set resource requests and limits for workload. The resource request impacts which node the pods will be assigned to by the scheduler, while the resource limit sets the condition under which the container will be terminated.</li>
 	<li>In general, a Kubernetes network policy defines rules of how a group of pods are allowed to communicate with each other and other network endpoints. You can define both ingress rules and egress rules for your workload.</li>
 	<li>During deployment, DevOps should consider using a PodSecurityPolicy and a network policy to enforce least privileges across the entire cluster.</li>
 	<li>Help defining RBAC privilege grants: <a href="https://github.com/liggitt/audit2rbac" target="_blank" rel="noopener noreferrer">https://github.com/liggitt/audit2rbac</a></li>
</ul>
<h2>Chapter 5: Configuring Kubernetes Security Boundaries</h2>
<ul>
 	<li>In containerized environments, chroot prevents containers from tampering with the filesystems of other containers.</li>
 	<li>Think of trust boundary as a wall and security boundary as a fence around the wall.</li>
 	<li>A Kubernetes cluster can be broadly split into three security domains:
<ul>
 	<li><strong>Kubernetes master components:</strong> Kubernetes master components define the control plane for the Kubernetes ecosystem. The master components are responsible for decisions required for the smooth operation of the cluster, such as scheduling. Master components include kube-apiserver, etcd, the kube-controller manager, DNS server, and kube-scheduler. A breach in the Kubernetes master components can compromise the entire Kubernetes cluster.</li>
 	<li><strong>Kubernetes worker components:</strong> Kubernetes worker components are deployed on every worker node and ensure that Pods and containers are running nicely. Kubernetes worker components use authorization and TLS tunneling for communicating with the master components.</li>
 	<li><strong>Kubernetes objects:</strong> Kubernetes objects are persistent entities that represent the state of the cluster: deployed applications, volumes, and namespaces. Kubernetes objects include Pods, Services, volumes, and namespaces.</li>
</ul>
</li>
 	<li>kube-apiserver is the only security boundary that protects the master components from compromise by privileged attackers. If a privileged attacker compromises kube-apiserver, it's game over.</li>
 	<li>By default, each Pod has its own network namespace and IPC namespace. Each container inside the same pod has its own PID namespace so that one container has no knowledge about other containers running inside the same Pod. Similarly, a Pod does not know other Pods exist in the same worker node.</li>
 	<li>By default, here is a list of capabilities that are assigned to containers in Kubernetes clusters:
<ul>
 	<li>CAP_SETPCAP</li>
 	<li>CAP_MKNOD</li>
 	<li>CAP_AUDIT_WRITE</li>
 	<li>CAP_CHOWN</li>
 	<li>CAP_NET_RAW</li>
 	<li>CAP_DAC_OVERRIDE</li>
 	<li>CAP_FOWNER</li>
 	<li>CAP_FSETID</li>
 	<li>CAP_KILL</li>
 	<li>CAP_SETGID</li>
 	<li>CAP_SETUID</li>
 	<li>CAP_NET_BIND_SERVICE</li>
 	<li>CAP_SYS_CHROOT</li>
 	<li>CAP_SETFCAP</li>
</ul>
</li>
 	<li>You should drop all the capabilities and only add the required ones.</li>
 	<li>In general, the fewer capabilities granted to containers, the more secure the boundaries are for other microservices.</li>
 	<li>And it is highly recommended to use PodSecurityPolicy to restrict the usage of host namespaces as well as extra capabilities so that the security boundaries of microservices are fortified.</li>
 	<li>To strengthen the trust boundaries for microservices from a network aspect, you might want to either specify the allowed ipBlock from external or allowed microservices from a specific namespace.</li>
 	<li>Kubernetes network policies: <a href="https://kubernetes.io/docs/concepts/services-networking/network-policies/" target="_blank" rel="noopener noreferrer">https://kubernetes.io/docs/concepts/services-networking/network-policies/</a></li>
</ul>
<h2>Chapter 6: Securing Cluster Components</h2>
<ul>
 	<li>kube-apiserver, by default, supports Attribute-Based Access Control (ABAC), Role-Based Access Control (RBAC), node authorization, and Webhooks for authorization. RBAC is the recommended mode of authorization.</li>
 	<li>To secure the API server, you should do the following:
<ul>
 	<li><strong>Disable anonymous authentication:</strong>
<ul>
 	<li>Use the anonymous-auth=false flag to set anonymous authentication to false. This ensures that requests rejected by all authentication modules are not treated as anonymous and are discarded.</li>
</ul>
</li>
 	<li><strong>Disable basic authentication:</strong>
<ul>
 	<li>Basic authentication is supported for convenience in kube-apiserver and should not be used. Basic authentication passwords persist indefinitely. kube-apiserver uses the --basic-auth-file argument to enable basic authentication. Ensure that this argument is not used.</li>
</ul>
</li>
 	<li><strong>Disable token authentication:</strong>
<ul>
 	<li>--token-auth-file enables token-based authentication for your cluster. Token-based authentication is not recommended. Static tokens persist forever and need a restart of the API server to update. Client certificates should be used for authentication.</li>
</ul>
</li>
 	<li><strong>Ensure connections with kubelet use HTTPS:</strong>
<ul>
 	<li>By default, --kubelet-https is set to true. Ensure that this argument is not set to false for kube-apiserver.</li>
</ul>
</li>
 	<li><strong>Disable profiling:</strong>
<ul>
 	<li>Enabling profiling using --profiling exposes unnecessary system and program details. Unless you are experiencing performance issues, disable profiling by setting --profiling=false.</li>
</ul>
</li>
 	<li><strong>Disable AlwaysAdmit:</strong>
<ul>
 	<li>--enable-admission-plugins can be used to enable admission control plugins that are not enabled by default. AlwaysAdmit accepts the request. Ensure that the plugin is not in the --enabled-admission-plugins list.</li>
</ul>
</li>
 	<li><strong>Use AlwaysPullImages:</strong>
<ul>
 	<li>The AlwaysPullImages admission control ensures that images on the nodes cannot be used without correct credentials. This prevents malicious pods from spinning up containers for images that already exist on the node.</li>
</ul>
</li>
 	<li><strong>Use SecurityContextDeny:</strong>
<ul>
 	<li>This admission controller should be used if PodSecurityPolicy is not enabled. SecurityContextDeny ensures that pods cannot modify SecurityContext to escalate privileges.</li>
</ul>
</li>
 	<li><strong>Enable auditing:</strong>
<ul>
 	<li>Auditing is enabled by default in kube-apiserver. Ensure that --audit-log-path is set to a file in a secure location. Additionally, ensure that the maxage, maxsize, and maxbackup parameters for auditing are set to meet compliance expectations.</li>
</ul>
</li>
 	<li><strong>Disable AlwaysAllow authorization:</strong>
<ul>
 	<li>Authorization mode ensures that requests from users with correct privileges are parsed by the API server. Do not use AlwaysAllow with --authorization-mode.</li>
</ul>
</li>
 	<li><strong>Enable RBAC authorization:</strong>
<ul>
 	<li>RBAC is the recommended authorization mode for the API server. ABAC is difficult to use and manage. The ease of use, and easy updates to, RBAC roles and role bindings makes RBAC suitable for environments that scale often.</li>
</ul>
</li>
 	<li><strong>Ensure requests to kubelet use valid certificates:</strong>
<ul>
 	<li>By default, kube-apiserver uses HTTPS for requests to kubelet. Enabling --kubelet-certificate-authority, --kubelet-client-key, and --kubelet-client-key ensures that the communication uses valid HTTPS certificates.</li>
</ul>
</li>
 	<li><strong>Enable service-account-lookup:</strong>
<ul>
 	<li>In addition to ensuring that the service account token is valid, kube-apiserver should also verify that the token Enable PodSecurityPolicy: --enable-admission-plugins can be used to enable PodSecurityPolicy. PodSecurityPolicy is used to define the security-sensitive criteria for a pod.</li>
</ul>
</li>
 	<li><strong>Use a service account key file:</strong>
<ul>
 	<li>Use of --service-account-key-file enables rotation of keys for service accounts. If this is not specified, kube-apiserver uses the private key from the Transport Layer Security (TLS) certificates to sign the service account tokens.</li>
</ul>
</li>
 	<li><strong>Enable authorized requests to etcd:</strong>
<ul>
 	<li>--etcd-certfile and --etcd-keyfile can be used to identify requests to etcd. This ensures that any unidentified requests can be rejected by etcd.</li>
</ul>
</li>
 	<li><strong>Do not disable the ServiceAccount admission controller:</strong>
<ul>
 	<li>This admission control automates service accounts. Enabling ServiceAccount ensures that custom ServiceAccount with restricted permissions can be used with different Kubernetes objects.</li>
</ul>
</li>
 	<li><strong>Do not use self-signed certificates for requests:</strong>
<ul>
 	<li>If HTTPS is enabled for kube-apiserver, a --tls-cert-file and a --tls-private-key-file should be provided to ensure that self-signed certificates are not used.</li>
</ul>
</li>
 	<li><strong>Secure connections to etcd:</strong>
<ul>
 	<li>Setting --etcd-cafile allows kube-apiserver to verify itself to etcd over Secure Sockets Layer (SSL) using a certificate file.</li>
</ul>
</li>
 	<li><strong>Use secure TLS connections:</strong>
<ul>
 	<li>Set --tls-cipher-suites to strong ciphers only. --tls-min-version is used to set the minimum-supported TLS version. TLS 1.2 is the recommended minimum version.</li>
</ul>
</li>
 	<li><strong>Enable advanced auditing:</strong>
<ul>
 	<li>Advanced auditing can be disabled by setting the --feature-gates to AdvancedAuditing=false. Ensure that this field is present and is set to true. Advanced auditing helps in an investigation if a breach happens.</li>
</ul>
</li>
</ul>
</li>
 	<li>To secure kubelet, you should do the following:
<ul>
 	<li><strong>Disable anonymous authentication:</strong>
<ul>
 	<li>If anonymous authentication is enabled, requests that are rejected by other authentication methods are treated as anonymous. Ensure that --anonymous-auth=false is set for each instance of kubelet.</li>
</ul>
</li>
 	<li><strong>Set the authorization mode:</strong>
<ul>
 	<li>The authorization mode for kubelet is set using config files. A config file is specified using the --config parameter. Ensure that the authorization mode does not have AlwaysAllow in the list.</li>
</ul>
</li>
 	<li><strong>Rotate kubelet certificates:</strong>
<ul>
 	<li>kubelet certificates can be rotated using a RotateCertificates configuration in the kubelet configuration file. This should be used in conjunction with RotateKubeletServerCertificate to auto-request rotation of server certificates.</li>
</ul>
</li>
 	<li><strong>Provide a Certificate Authority (CA) bundle:</strong>
<ul>
 	<li>A CA bundle is used by kubelet to verify client certificates. This can be set using the ClientCAFile parameter in the config file.</li>
</ul>
</li>
 	<li><strong>Restrict access to the Kubelet API:</strong>
<ul>
 	<li>Only the kube-apiserver component interacts with the kubelet API. If you try to communicate with the kubelet API on the node, it is forbidden. This is ensured by using RBAC for kubelet.</li>
</ul>
</li>
 	<li><strong>Disable the read-only port:</strong>
<ul>
 	<li>The read-only port is enabled for kubelet by default, and should be disabled. The read-only port is served with no authentication or authorization.</li>
</ul>
</li>
 	<li><strong>Enable the NodeRestriction admission controller:</strong>
<ul>
 	<li>The NodeRestriction admission controller only allows kubelet to modify the node and pod objects on the node it is bound to.</li>
</ul>
</li>
</ul>
</li>
 	<li>To secure etcd, you should do the following:
<ul>
 	<li><strong>Restrict node access:</strong>
<ul>
 	<li>Use Linux firewalls to ensure that only nodes that need access to etcd are allowed access.</li>
</ul>
</li>
 	<li><strong>Ensure the API server uses TLS:</strong>
<ul>
 	<li>--cert-file and --key-file ensure that requests to etcd are secure.</li>
</ul>
</li>
 	<li><strong>Use valid certificates:</strong>
<ul>
 	<li>--client-cert-auth ensures that communication from clients is made using valid certificates, and setting --auto-tls to false ensures that self-signed certificates are not used.</li>
</ul>
</li>
 	<li><strong>Encrypt data at rest:</strong>
<ul>
 	<li>--encryption-provider-config is passed to the API server to ensure that data is encrypted at rest in etcd.</li>
</ul>
</li>
</ul>
</li>
 	<li>To secure kube-scheduler, you should do the following:
<ul>
 	<li><strong>Disable profiling:</strong>
<ul>
 	<li>Profiling of kube-scheduler exposes system details. Setting --profiling to false reduces the attack surface.</li>
</ul>
</li>
 	<li><strong>Disable external connections to kube-scheduler:</strong>
<ul>
 	<li>External connections should be disabled for kube-scheduler. AllowExtTrafficLocalEndpoints is set to true, enabling external connections to kube-scheduler. Ensure that this feature is disabled using --feature-gates.</li>
</ul>
</li>
 	<li><strong>Enable AppArmor:</strong>
<ul>
 	<li>By default, AppArmor is enabled for kube-scheduler. Ensure that AppArmor is not disabled for kube-scheduler.</li>
</ul>
</li>
</ul>
</li>
 	<li>To secure kube-controller-manager, you should use --use-service-account-credentials which, when used with RBAC ensures that control loops run with minimum privileges.</li>
 	<li>kube-dns has been superseded by CoreDNS since version 1.11 because of security vulnerabilities in dnsmasq and performance issues in SkyDNS. CoreDNS is a single container that provides all the functions of kube-dns.</li>
 	<li>To secure CoreDNS, do the following:
<ul>
 	<li><strong>Ensure that the health plugin is not disabled:</strong>
<ul>
 	<li>The health plugin monitors the status of CoreDNS. It is used to confirm if CoreDNS is up and running. It is enabled by adding health to the list of plugins to be enabled in Corefile.</li>
</ul>
</li>
 	<li><strong>Enable istio for CoreDNS:</strong>
<ul>
 	<li>istio is a service mesh that is used by Kubernetes to provide service discovery, load balancing, and authentication. It is not available by default in Kubernetes and needs to be added as an external dependency.</li>
</ul>
</li>
</ul>
</li>
 	<li>kube-bench is an automated tool written in Go and published by Aqua Security that runs tests documented in the CIS benchmark.</li>
 	<li>GitHub (kube-bench): <a href="https://github.com/aquasecurity/kube-bench" target="_blank" rel="noopener noreferrer">https://github.com/aquasecurity/kube-bench</a></li>
</ul>
<h2>Chapter 7: Authentication, Authorization, and Admission Control</h2>
<ul>
 	<li>Authentication validates the identity of a user. Once the identity is validated, authorization is used to check whether the user has the privileges to perform the desired action.</li>
 	<li>Admission controllers intercept requests that create, update, or delete an object in the admission controller.</li>
 	<li>Admission controllers fall into two categories: mutating or validating.</li>
 	<li>Mutating admission controllers run first; they modify the requests they admit.</li>
 	<li>Validating admission controllers run next. These controllers cannot modify objects.</li>
 	<li>In v1.6+, anonymous access is allowed to support anonymous and unauthenticated users for the RBAC and ABAC authorization modes. It can be explicitly disabled by passing the --anonymous-auth=false flag to the API server configuration.</li>
 	<li>Using X509 Certificate Authority (CA) certificates is the most common authentication strategy in Kubernetes. It can be enabled by passing --client-ca-file=file_path to the</li>
 	<li>server static tokens, which are a popular mode of authentication in development and debugging environments but should not be used in production clusters.</li>
 	<li>Once compromised, the only way to generate a new token is to restart the API server.</li>
 	<li>Similar to static tokens, basic authentication passwords cannot be changed without restarting the API server. Basic authentication should not be used in production clusters.</li>
 	<li>Bootstrap tokens are the default authentication method used in Kubernetes. They are dynamically managed and stored as secrets in kube-system.</li>
 	<li>The default service account is associated with a pod if no service account is specified.</li>
 	<li>The service account authenticator is automatically enabled. It verifies signed bearer tokens. The signing key is specified using --service-account-key-file. If this value is unspecified, the Kube API server's private key is used.</li>
 	<li>Node authorization mode grants permissions to kubelets to access services, endpoints, nodes, pods, secrets, and persistent volumes for a node.</li>
 	<li>ABAC is difficult to configure and maintain. It is not recommended that you use ABAC in production environments.</li>
 	<li>Role and RoleBinding are restricted to namespaces. If a role needs to span across namespaces, ClusterRole and ClusterRoleBinding can be used to grant permissions to users across namespace boundaries.</li>
 	<li>A cluster can have four types of limits: Namespace, Server, User and SourceAndObject. With each limit, the user can have a maximum limit for the Queries Per Second (QPS), the burst and cache size.</li>
 	<li>It is recommended that PodSecurityPolicy is enabled by default in a cluster. However, due to the administrative overhead, SecurityContextDeny can be used until PodSecurityPolicy is configured for the cluster.</li>
 	<li>Policies for OPA are defined in a custom language called Rego.</li>
 	<li>You can use the official OPA documentation (<a href="https://www.openpolicyagent.org/docs/latest/kubernetes-tutorial/" target="_blank" rel="noopener noreferrer">https://www.openpolicyagent.org/docs/latest/kubernetes-tutorial/</a>) to install OPA on your cluster.</li>
</ul>
<h2>Chapter 8: Securing Kubernetes Pods</h2>
<ul>
 	<li>Image scanning tools only focus on finding publicly disclosed issues in applications bundled inside the image. But, following the best practices along with secure configuration while building the image ensures that the application has a minimal attack surface.</li>
 	<li>A Dockerfile contains a series of instructions, such as copy files, configure environment variables, configure open ports, and container entry points, which can be understood by the Docker daemon to construct the image file.</li>
 	<li>Each Dockerfile instruction will create a file layer in the image.</li>
 	<li>Let's take a look at the security recommendations from CIS Docker benchmarks regarding container images:
<ul>
 	<li>Create a user for a container image to run a microservice:
<ul>
 	<li>It is good practice to run a container as non-root. Although user namespace mapping is available, it is not enabled by default.</li>
</ul>
</li>
 	<li>Use trusted base images to build your own image:
<ul>
 	<li>Images downloaded from public repositories cannot be fully trusted. It is well known that images from public repositories may contain malware or crypto miners. Hence, it is recommended that you build your image from scratch or use minimal trusted images, such as Alpine. Also, perform the image scan after your image has been built.</li>
</ul>
</li>
 	<li>Do not install unnecessary packages in your image:
<ul>
 	<li>Installing unnecessary packages will increase the attack surface. It is recommended that you keep your image slim. Occasionally, you will probably need to install some tools during the process of building an image. Do remember to remove them at the end of the Dockerfile.</li>
</ul>
</li>
 	<li>Scan and rebuild an image in order to apply security patches:
<ul>
 	<li>It is highly likely that new vulnerabilities will be discovered in your base image or in the packages you install in your image. It is good practice to scan your image frequently. Once you identify any vulnerabilities, try to patch the security fixes by rebuilding the image. Image scanning is a critical mechanism for identifying vulnerabilities at the build stage.</li>
</ul>
</li>
 	<li>Enable content trust for Docker:
<ul>
 	<li>Content trust uses digital signatures to ensure data integrity between the client and the Docker registry. It ensures the provenance of the container image. However, it is not enabled by default. You can turn it on by setting the environment variable, DOCKER_CONTENT_TRUST, to 1.</li>
</ul>
</li>
 	<li>Add a HEALTHCHECK instruction to the container image:
<ul>
 	<li>A HEALTHCHECK instruction defines a command to ask Docker Engine to check the health status of the container periodically. Based on the health status check result, Docker Engine then exits the non-healthy container and initiates a new one.</li>
</ul>
</li>
 	<li>Ensure that updates are not cached in Dockerfile:
<ul>
 	<li>Depending on the base image you choose, you may need to update the package repository before installing new packages. However, if you specify RUN apt-get update (Debian) in a single line in the Dockerfile, Docker Engine will cache this file layer, so, when you build your image again, it will still use the old package repository information that is cached. This will prevent you from using the latest packages in your image. Therefore, either use update along with install in a single Dockerfile instruction or use the --no-cache flag in the Docker build command.</li>
</ul>
</li>
 	<li>Remove setuid and setgid permission from files in the image:
<ul>
 	<li>setuid and setgid permissions can be used for privilege escalation as files with such permissions are allowed to be executed with owners' privileges instead of launchers' privileges. You should carefully review the files with setuid and setgid permissions and remove those files that don't require such permissions.</li>
</ul>
</li>
 	<li>Use COPY instead of ADD in the Dockerfile:
<ul>
 	<li>The COPY instruction can only copy files from the local machine to the filesystem of the image, while the ADD instruction can not only copy files from the local machine but also retrieve files from the remote URL to the filesystem of the image. Using ADD may introduce the risk of adding malicious files from the internet to the image.</li>
</ul>
</li>
 	<li>Do not store secrets in the Dockerfile:
<ul>
 	<li>There are many tools that are able to extract image file layers. If there are any secrets stored in the image, secrets are no longer secrets. Storing secrets in the Dockerfile renders containers potentially exploitable. A common mistake is to use the ENV instruction to store secrets in environment variables.</li>
</ul>
</li>
 	<li>Install verified packages only:
<ul>
 	<li>This is similar to using the trusted base image only. Observe caution as regards the packages you are going to install within your image. Make sure they are from trusted package repositories.</li>
</ul>
</li>
</ul>
</li>
 	<li>Ideally, application developers and security engineers work together to harden the microservice at the pod and container level by configuring the security context provided by Kubernetes.</li>
 	<li>We classify the major security attributes into four categories:
<ul>
 	<li>Setting host namespaces for pods</li>
 	<li>Security context at the container level</li>
 	<li>Security context at the pod level</li>
 	<li>AppArmor profile</li>
</ul>
</li>
 	<li>The following attributes in the pod specification are used to configure the use of host namespaces:
<ul>
 	<li>hostPID: By default, this is false. Setting it to true allows the pod to have visibility on all the processes in the worker node.</li>
 	<li>hostNetwork: By default, this is false. Setting it to true allows the pod to have visibility on all the network stacks in the worker node.</li>
 	<li>hostIPC: By default, this is false. Setting it to true allows the pod to have visibility on all the IPC resources in the worker node.</li>
</ul>
</li>
 	<li>Each container can have its own security context, which defines privileges and access controls. The design of a security context at a container level provides a more fine-grained security control for Kubernetes workloads.</li>
 	<li>The following are the principal attributes of a security context for containers:
<ul>
 	<li><strong>privileged:</strong> By default, this is false. Setting it to true essentially makes the processes inside the container equivalent to the root user on the worker node.</li>
 	<li><strong>capabilities:</strong> There is a default set of capabilities granted to the container by the container runtime. The default capabilities granted are as follows: CAP_SETPCAP, CAP_MKNOD, CAP_AUDIT_WRITE, CAP_CHOWN, CAP_NET_RAW, CAP_DAC_OVERRIDE, CAP_FOWNER, CAP_FSETID, CAP_KILL, CAP_SETGID, CAP_SETUID, CAP_NET_BIND_SERVICE, CAP_SYS_CHROOT, and CAP_SETFCAP
<ul>
 	<li>You may add extra capabilities or drop some of the defaults by configuring this attribute. Capabilities such as CAP_SYS_ADMIN and CAP_NETWORK_ADMIN should be added with caution. For the default capabilities, you should also drop those that are unnecessary.</li>
</ul>
</li>
 	<li><strong>allowPrivilegeEscalation:</strong> By default, this is true. Setting it directly controls the no_new_privs flag, which will be set to the processes in the container. Basically, this attribute controls whether the process can gain more privileges than its parent process. Note that if the container runs in privileged mode, or has the CAP_SYS_ADMN capability added, this attribute will be set to true automatically. It is good practice to set it to false.</li>
 	<li><strong>readOnlyRootFilesystem:</strong> By default, this is false. Setting it to true makes the root filesystem of the container read-only, which means that the library files, configuration files, and so on are read-only and cannot be tampered with. It is a good security practice to set it to true.</li>
 	<li><strong>runAsNonRoot:</strong> By default, this is false. Setting it to true enables validation that the processes in the container cannot run as a root user (UID=0). Validation is done by kubelet. With runAsNonRoot set to true, kubelet will prevent the container from starting if run as a root user. It is a good security practice to set it to true. This attribute is also available in PodSecurityContext, which takes effect at pod level. If this attribute is set in both SecurityContext and PodSecurityContext, the value specified at the container level takes precedence.</li>
 	<li><strong>runAsUser:</strong> This is designed to specify to the UID to run the entrypoint process of the container image. The default setting is the user specified in the image's metadata (for example, the USER instruction in the Dockerfile). This attribute is also available in PodSecurityContext, which takes effect at the pod level. If this attribute is set in both SecurityContext and PodSecurityContext, the value specified at the container level takes precedence.</li>
 	<li><strong>runAsGroup:</strong> Similar to runAsUser, this is designed to specify the Group ID or GID to run the entrypoint process of the container. This attribute is also available in PodSecurityContext, which takes effect at the pod level. If this attribute is set in both SecurityContext and PodSecurityContext, the value specified at the container level takes precedence.</li>
 	<li><strong>seLinuxOptions:</strong> This is designed to specify the SELinux context to the container. By default, the container runtime will assign a random SELinux context to the container if not specified. This attribute is also available in PodSecurityContex, which takes effect at the pod level. If this attribute is set in both SecurityContext and PodSecurityContext, the value specified at the container level takes precedence.</li>
</ul>
</li>
 	<li>In general, the security best practices are as follows:
<ul>
 	<li>Do not run in privileged mode unless necessary.</li>
 	<li>Do not add extra capabilities unless necessary.</li>
 	<li>Drop unused default capabilities.</li>
 	<li>Run containers as a non-root user.</li>
 	<li>Enable a runAsNonRoot check.</li>
 	<li>Set the container root filesystem as read-only.</li>
</ul>
</li>
 	<li>Note that adding NETWORK_ADMIN is not recommended for containers running in production environments.</li>
 	<li>The following is a list of the principal security attributes at the pod level:
<ul>
 	<li><strong>fsGroup:</strong> This is a special supplemental group applied to all containers. The effectiveness of this attribute depends on the volume type. Essentially, it allows kubelet to set the ownership of the mounted volume to the pod with the supplemental GID.</li>
 	<li><strong>sysctls:</strong> sysctls is used to configure kernel parameters at runtime. In such a context, sysctls and kernel parameters are used interchangeably. These sysctls commands are namespaced kernel parameters that apply to the pod. The following sysctls commands are known to be namespaced: kernel.shm*, kernel.msg*, kernel.sem, and kernel.mqueue.*. Unsafe sysctls are disabled by default and should not be enabled in production environments.</li>
 	<li><strong>runAsUser:</strong> This is designed to specify the UID to run the entrypoint process of the container image. The default setting is the user specified in the image's metadata (for example, the USER instruction in the Dockerfile). This attribute is also available in SecurityContext, which takes effect at the container level. If this attribute is set in both SecurityContext and PodSecurityContext, the value specified at the container level takes precedence.</li>
 	<li><strong>runAsGroup:</strong> Similar to runAsUser, this is designed to specify the GID to run the entrypoint process of the container. This attribute is also available in SecurityContext, which takes effect at the container level.</li>
 	<li><strong>runAsNonRoot:</strong> Set to false by default, setting it to true enables validation that the processes in the container cannot run as a root user (UID=0). Validation is done by kubelet. By setting it to true, kubelet will prevent the container from starting if run as a root user. It is a good security practice to set it to true.</li>
 	<li><strong>seLinuxOptions:</strong> This is designed to specify the SELinux context to the container. By default, the container runtime will assign a random SELinux context to the container if not specified.</li>
</ul>
</li>
 	<li>Note that AppArmor is not a Kubernetes object, like a pod, deployment, and so on. It can't be operated through kubectl. You will have to SSH to each node and load the AppArmor profile into the kernel so that the pod may be able to use it.</li>
 	<li>Open source tools such as bane can help create AppArmor profiles for containers.</li>
 	<li>A Kubernetes PodSecurityPolicy is a cluster-level resource that controls security-sensitive aspects of the pod specification through which the access privileges of a Kubernetes pod are limited.</li>
 	<li>You can think of a PodSecurityPolicy as a policy to evaluate the security attributes defined in the pod's specification. Only those pods whose security attributes meet the requirements of PodSecurityPolicy will be admitted to the cluster.</li>
 	<li>After you have created the Pod Security Policy, there is one more step required in order to enforce it. You will have to grant the privilege of using the PodSecurityPolicy object to the users, groups, or service accounts. By doing so, the pod security policies are entitled to evaluate the workloads based on the associated service account.</li>
 	<li>Kubernetes PodSecurityPolicy Advisor (also known as kube-psp-advisor) is an open source tool from Sysdig. It scans the security attributes of running workloads in the cluster and then, on this basis, recommends pod security policies for your cluster or workloads.</li>
</ul>
<h2>Chapter 9: Image Scanning in DevOps Pipelines</h2>
<ul>
 	<li>The image scanning tool extracts the image file, then looks for all the available packages and libraries in the image and looks up their version within the vulnerability database. If there is any package whose version matches with any of the CVE's descriptions in the vulnerability database, the image scanning tool will report that there is a vulnerability in the image.</li>
 	<li>The CVSS calculator is available at <a href="https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator" target="_blank" rel="noopener noreferrer">https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator</a></li>
 	<li>Anchore Engine policies allow you to define rules to handle vulnerabilities differently based on their severity.</li>
 	<li>A rough definition of the DevOps stages that are applicable for image scanning:
<ul>
 	<li>Build: When the image is built in the CI/CD pipeline</li>
 	<li>Deployment: When the image is about to be deployed in a Kubernetes cluster</li>
 	<li>Runtime: After the image is deployed to a Kubernetes cluster and the containers are up and running</li>
</ul>
</li>
 	<li>Anchore also offers an image scan GitHub action called Anchore Container Scan. It launches the Anchore Engine scanner on the newly built image and returns the vulnerabilities, manifests, and a pass/fail policy evaluation that can be used to fail the build if desired.</li>
 	<li>Image scanning admission controller is an open source project from Sysdig. It scans images from the workload that is about to be deployed. If an image fails the image scanning policy, the workload will be rejected.</li>
 	<li>Scanning as validating admission is a good security practice for Kubernetes deployment.</li>
</ul>
<h2>Chapter 10: Real-Time Monitoring and Resource Management of a Kubernetes Cluster</h2>
<ul>
 	<li>If all the resources of the node are being utilized by the pods, kubelet on the node will clean up dead pods â€“ unused images. If the cleanup does not reduce the stress, kubelet will start evicting those pods that consume more resources.</li>
 	<li>LimitRanger works when the request to create or update the object is received by the API Server but not at runtime. If a pod has a violating limit before the limit is applied, it will keep running.</li>
 	<li>It is recommended that service account tokens should be used to access Kubernetes Dashboard</li>
 	<li>Kubernetes Dashboard provides all the functionality a cluster administrator requires in order to manage resources and objects within the cluster. Given the functionality of the dashboard, access to the dashboard should be limited to cluster administrators.</li>
 	<li>To allow a service account to use the Kubernetes dashboard, you need to add the cluster-admin role to the service account.</li>
 	<li>Ensure that the dashboard container is running with the following arguments:
<ul>
 	<li>Disable insecure port: --insecure-port enables Kubernetes Dashboard to receive requests over HTTP. Ensure that it is disabled in production environments.</li>
 	<li>Disable insecure address: --insecure-bind-address should be disabled to avoid a situation where Kubernetes Dashboard is accessible via HTTP.</li>
 	<li>Bind address to localhost: --bind-address should be set to 127.0.0.1 to prevent hosts from being connected over the internet.</li>
 	<li>Enable TLS: Use tls-cert-file and tls-key-file to access the dashboard over secure channels. Ensure token authentication mode is enabled: Authentication mode can be specified using the --authentication-mode flag. By default, it is set to token. Ensure that basic authentication is not used with the dashboard.</li>
 	<li>Disable insecure login: Insecure login is used when the dashboard is available via HTTP. This should be disabled by default.</li>
 	<li>Disable skip login: Skip login allows unauthenticated users to access the Kubernetes dashboard. --enable-skip-login enables skip login; this should not be present in production environments.</li>
 	<li>Disable settings authorizer: --disable-settings-authorizer allows unauthenticated users to access the settings page. This should be disabled in production environments.</li>
</ul>
</li>
 	<li>Metrics Server aggregates cluster usage data using the Summary API exposed by each kubelet on each node.</li>
 	<li>Metrics Server exposes the collected metrics through the Metrics API, which are used by the horizontal pod autoscalar and the vertical pod autoscalar.</li>
 	<li>In production clusters, make sure that Metrics Server does not use the --kubelet-insecure-tls flag, which allows Metrics Server to skip verification of certificates by the CA.</li>
 	<li>Prometheus uses a pull system. It sends an HTTP request called a scrape, which fetches data from the system components, including API Server, node-exporter, and kubelet. The response to the scrape and the metrics are stored in a custom database on the Prometheus server.</li>
 	<li>Let's look at some examples of Prometheus queries that will be helpful for cluster administrators:
<ul>
 	<li>Kubernetes CPU usage:
<ul>
 	<li>sum(rate(container_cpu_usage_seconds_total{container_name!=""POD"",pod_name!=""""}[5m]))</li>
</ul>
</li>
 	<li>Kubernetes CPU usage by namespace:
<ul>
 	<li>sum(rate(container_cpu_usage_seconds_total{container_name!=""POD"",namespace!=""""}[5m])) by (namespace)</li>
</ul>
</li>
 	<li>CPU requests by pod:
<ul>
 	<li>sum(kube_pod_container_resource_requests_cpu_cores) by (pod)</li>
</ul>
</li>
</ul>
</li>
 	<li>Using Alertmanager with Prometheus helps deduplicate, group, and route alerts from applications such as Prometheus and route it to integrated clients, including email, OpsGenie, and PagerDuty.</li>
</ul>
<h2>Chapter 11: Defense in Depth</h2>
<ul>
 	<li>With auditing, a Kubernetes cluster administrator is able to answer questions such as the following:
<ul>
 	<li>What happened? (A pod is created and what kind of pod it is)</li>
 	<li>Who did it? (From user/admin)</li>
 	<li>When did it happen? (The timestamp of the event)</li>
 	<li>Where did it happen? (In which namespace is the pod created?)</li>
</ul>
</li>
 	<li>An audit policy allows users to define rules about what kind of event should be recorded and how much detail of the event should be recorded.</li>
 	<li>When an event is processed by kube-apiserver, it compares the list of rules in the audit policy in order. The first matching rules also dictate the audit level of the event.</li>
 	<li>There are four audit levels, detailed as follows:
<ul>
 	<li>None: Do not log events that match the audit rule.</li>
 	<li>Metadata: When an event matches the audit rule, log the metadata (such as user, timestamp, resource, verb, and more) of the request to kube-apiserver.</li>
 	<li>Request: When an event matches the audit rule, log the metadata as well as the request body. This does not apply for the non-resource URL.</li>
 	<li>RequestResponse: When an event matches the audit rule, log the metadata, request-and-request-and-response body. This does not apply for the non-resource request.</li>
</ul>
</li>
 	<li>The request-level event is more verbose than the metadata level events, while the RequestResponse level event is more verbose than the request-level event.</li>
 	<li>It is quite necessary to understand the differences between the audit levels so that you can define audit rules properly, both for resource consumption and security.</li>
 	<li>Please do choose the audit level properly. More verbose logs provide deeper insight into the activities being carried out. However, it does cost more in storage and time to process the audit events.</li>
 	<li>One thing worth mentioning is that if you set a request or a RequestResponse audit level on Kubernetes secret objects, the secret content will be recorded in the audit events. If you set the audit level to be more verbose than metadata for Kubernetes objects containing sensitive data, you should use a sensitive data redaction mechanism to avoid secrets being logged in the audit events.</li>
 	<li>There are two types of audit backends that can be configured to use process audit events: a log backend and a webhook backend.</li>
 	<li>Specifying more than one replica in the deployment or the StatefulSet, or using a DaemonSet, will ensure the high availability of your workload.</li>
 	<li>kube-dns are spun up with more than one pod by default, so their high availability is ensured.</li>
 	<li>By default, the secret data is stored in plaintext (encoded format) in etcd. etcd can be configured to encrypt secrets at rest.</li>
 	<li>Similarly, if etcd is not configured to encrypt communication using Transport Layer Security (TLS), secret data is transferred in plaintext too.</li>
 	<li>The init container is to prepopulate our secret, and the sidecar container is to keep that secret data in sync throughout our application's life cycle.</li>
 	<li>Under the hood, kubectl-capture starts a new pod to do the capture on the host where the suspected victim pod is running, with a 120-second capture duration, so that we can see everything that is happening right now and in the next 120 seconds in that host.</li>
 	<li>Kubernetes auditing: <a href="https://kubernetes.io/docs/tasks/debug-application-cluster/audit/" target="_blank" rel="noopener noreferrer">https://kubernetes.io/docs/tasks/debug-application-cluster/audit/</a></li>
 	<li>High availability with kubeadm: <a href="https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/high-availability/" target="_blank" rel="noopener noreferrer">https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/high-availability/</a></li>
</ul>
<h2>Chapter 12: Analyzing and Detecting Crypto-Mining Attacks</h2>
<ul>
 	<li>None</li>
</ul>
<h2>Chapter 13: Learning from Kubernetes CVEs</h2>
<ul>
 	<li>Security advisories and announcements (<a href="https://kubernetes.io/docs/reference/issues-security/security/" target="_blank" rel="noopener noreferrer">https://kubernetes.io/docs/reference/issues-security/security/</a>) published by Kubernetes are the best way to keep track of new security vulnerabilities found in Kubernetes.</li>
 	<li>kube-hunter is an open source tool that is developed and maintained by Aqua that helps identify known security issues in your Kubernetes cluster.</li>
</ul>
