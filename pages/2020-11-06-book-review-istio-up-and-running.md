---
layout: page
title: Book Review: Istio Up and Running
date: 2020-11-06 07:54
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/11/IstioUpAndRunning-BookCover.jpg"><img class="alignleft size-medium wp-image-33656" src="/wp-content/uploads/2020/11/IstioUpAndRunning-BookCover-229x300.jpg" alt="" width="229" height="300" /></a>Recently, I finished reading <a href="https://learning.oreilly.com/library/view/istio-up-and/9781492043775/" target="_blank" rel="noopener noreferrer">Istio: Up and Running</a> by Lee Calcote and Zack Butcher.

I've recently been ramping up on Kubernetes, so, I had some previous knowledge and hands-on experience with Kubernetes when I read this book. But this topic takes it to another level. This is above and beyond the basics of Kubernetes, and is all about service meshes.

I particularly found the whole book helpful in understanding (though, to be honest, I struggled with some of the more "in the weeds" deeper chapters). The first 2 chapters, namely Chapter 1 ("<strong>Introducing the Service Mesh</strong>"), and Chapter 2 ("<strong>Cloud Native Approach to Uniform Observability</strong>"),  really helped to level-set on the purpose for a service mesh. I also liked how in Chapter 3 ("<strong>Istio at a Glance</strong>"), it explained why you would want to use a service mesh over some of the Kubernetes native functionality like ingress controllers.

I liked how this book explained the need/use case for a service mesh, and how it adds to what is already provided in Kubernetes.

Below are my highlights from reading this specific publication, to help you decide if this is the book for you, and if it will provide what you are looking for. Note that not every chapter will have highlights (depending on the content and the main focus of my work).

If my highlights peak your interest, I recommend that you pick up a copy for yourself.
<h2>Chapter 01: Introducing the Service Mesh</h2>
<ul>
 	<li>At their core, service meshes provide a developer-driven, services-first network: one primarily concerned with obviating the need for application developers to build network concerns (e.g., resiliency) into their code; and one that empowers operators with the ability to declaratively define network behavior, node identity, and traffic flow through policy.</li>
 	<li>Service meshes are built using service proxies. Service proxies of the data plane carry traffic. Traffic is transparently intercepted using iptable rules in the pod namespace.</li>
 	<li>Service meshes seem to deliver on the promise that organizations implementing microservices could finally realize the dream of using the best frameworks and language for their individual jobs without worrying about the availability of libraries and patterns for every single platform.</li>
 	<li>A service mesh is a dedicated infrastructure layer for making service-to-service communication safe, fast, and reliable, at times relying on a container orchestrator or integration with another service discovery system.</li>
 	<li>Organization staff we've spoken to are adopting service meshes primarily for the observability that they bring through instrumentation of network traffic.</li>
 	<li>Container orchestrators have allowed us to move simple networking concerns out of applications and into the infrastructure, freeing the collective infrastructure technology ecosystem to advance our focus to higher layers.</li>
 	<li>With respect to service meshes, API gateways are designed to accept traffic from outside your organization or network and distribute it internally. API gateways expose your services as managed APIs, focused on transiting north-south traffic (in and out of the service mesh).</li>
 	<li>Service meshes are designed primarily to manage east-west traffic internal to the service mesh.</li>
 	<li>Given their complementary nature, you'll often find API gateways and service meshes deployed in combination.</li>
 	<li>Most service meshes provide a certificate authority (CA) to manage keys and certificates for securing service-to-service communication.</li>
 	<li>You can use facade services to break down monoliths. You could also adopt a strangler pattern of building services around the legacy monolith to expose a more developer-friendly set of APIs.</li>
 	<li>In regard to tracing, the only change required within the service is to forward certain HTTP headers.</li>
 	<li>Service meshes are useful for retrofitting uniform and ubiquitous observability tracing into existing infrastructures with the least amount of code change.</li>
 	<li>Istio (in the Greek alphabet, ιστίο) is Greek for “sail,” and is pronounced “iss-teeh-oh.” And, of course, Istio’s accompanying command-line interface (CLI), istioctl, is pronounced “iss-teeh-oh-c-t-l,” because you use it to control Istio, not cuddle with it.</li>
 	<li>Service meshes don't require applications to be cognizant of running on the mesh.</li>
 	<li>But, if you are looking to use Istio in production, look for releases tagged as "LTS" (Long-Term Support).</li>
 	<li>Istio is not a white-box application performance monitoring (APM) solution.</li>
 	<li>Of the metrics and logs available with Istio, these provide insight into network traffic flows, including source, destination, latency, and errors; top-level service metrics, not custom application metrics exposed by individual workloads or cluster-level logging.</li>
</ul>
<h2>Chapter 02: Cloud Native Approach to Uniform Observability</h2>
<ul>
 	<li>TIP: The more services you deploy, the greater the return on investment you'll see from using a service mesh.</li>
 	<li>That said, lifting and shifting an application into a cloud doesn't quite make it cloud native.</li>
 	<li>The following are characteristics of cloud native applications:
<ul>
 	<li>They run on programmatically addressable infrastructure, and are dynamic and decoupled from physical resources by one or more layers of abstraction across compute, network, and storage resources.</li>
 	<li>They are distributed and decentralized with the focus often being on how the application behaves, not on where it's running. They account for software life cycle events to allow for (rolling) updates, smoothly upgrading services without service disruption.</li>
 	<li>They are resilient and scalable, designed to run redundantly without single points of failure and to survive continually.</li>
 	<li>They are observable through their own instrumentation and/or that provided by underlying layers. Given their dynamic nature, distributed systems are relatively more difficult to inspect and debug, and so their observability must be accounted for.</li>
</ul>
</li>
 	<li>Service meshes are the next logical step after a container orchestration deployment.</li>
 	<li>Depending upon your team' experience levels and your specific projects, your path to cloud native will use different combinations of software development process, operational practices, application architecture, packaging and runtimes, and application infrastructure.</li>
 	<li>Cloud native technology often takes the form of microservices (engaged through service endpoints), built-in containers (engaged through a scheduler), and function augmentation (engaged through event notifications).</li>
 	<li>The path to cloud native pushes for smaller and smaller units of deployment, enabled through high levels of resource isolation.</li>
 	<li>Though they're lightweight, isolated, and infinitely scalable, functions suffer in regard to portability, exhibiting possibly the highest degree of lock-in among the various types of packaging.</li>
 	<li>Istio and other open source service meshes deliver the next generation of networking designed for cloud native applications.</li>
 	<li>Istio, and service meshes in general, insert a dedicated infrastructure layer between Dev and Ops, separating common concerns of service communication by providing independent control over services.</li>
 	<li>The decoupling of Dev and Ops is key to providing autonomous independent iteration.</li>
 	<li>When speaking of a system's observability, you describe how well and in what way the system provides you with signals to monitor. Observable software is typically instrumented to capture and expose information (telemetry/measurements), allowing you to reason over complex software.</li>
 	<li>In contrast, monitoring is the action of observing and checking the behavior and outputs of a system and its components over time, evaluating system state. Your ability to monitor a system is improved by its number of observable attributes (its observability). Monitoring asserts whether a state is true or not true (e.g., a system is degraded or not).</li>
 	<li>Service meshes decouple development and delivery teams by introducing a management layer -- Layer 5 (L5) -- between the lower-layer infrastructure and higher-layer application services.</li>
 	<li>Some best practices for logging include enforcing quotas and dynamic rate of adjustment of log generation.</li>
 	<li>Head-based consistent sampling (or upfront sampling) makes the sampling decision once per trace at the trace's start. Tail-based sampling makes the sampling decision at the end of the request execution so that additional criteria can be considered in whether a trace should be saved.</li>
 	<li>Istio generates and sends multiple telemetric signals based on requests sent into the mesh.</li>
 	<li>Insight (observability) is the number one reason why people deploy a service mesh.</li>
 	<li>Ideally you should consider observability in advance, as this is one important factor of running apps at scale, just like backups, security, auditability, and the like. In this way, you can make the trade-offs consciously.</li>
</ul>
<h2>Chapter 03: Istio at a Glance</h2>
<ul>
 	<li>At a high level, service mesh architectures including Istio commonly comprise two planes: a control plane and data plane, while a third (management) plane might reside in incumbent/infrastructure systems.</li>
 	<li>For a more thorough explanation of service mesh deployment models and approaches to evolutionary architectures, see The Enterprise Path to Service Mesh Architectures.</li>
 	<li>Data planes are responsible for intracluster communication as well as inbound (ingress) and outbound (egress) cluster network traffic.</li>
 	<li>Control planes provide policy and configuration for services in the mesh, taking a set of isolated, stateless proxies and turning them into a service mesh.</li>
 	<li>Pilot is the head of the ship in an Istio mesh, so to speak. It stays synchronized with the underlying platform (e.g., Kubernetes) by tracking and representing the state and location of</li>
 	<li>running services to the data plane.</li>
 	<li>Galley is Istio's configuration aggregation and distribution component. As its role evolves, it will insulate the other Istio components from underlying platform and user-supplied configurations by ingesting and validating configurations. Galley uses the Mesh Configuration Protocol (MCP) as a mechanism to serve and distribute configuration.</li>
 	<li>Mixer bears responsibility for precondition checking, quota management, and telemetry reporting.</li>
 	<li>Citadel empowers Istio to provide strong service-to-service and end-user authentication using mutual Transport Layer Security (mTLS), with built-in identity and credential management.</li>
 	<li>NOTE: By default, Istio-enabled applications are unable to access URLs external to the cluster.</li>
 	<li>TIP: Why Use Istio Gateways and Not Kubernetes Ingresses?
<ul>
 	<li>In general, the Istio v1alpha3 APIs use gateways for richer functionality given that Kubernetes Ingress has proven insufficient for Istio applications. Compared to Kubernetes Ingress, Istio gateways can operate as a pure Layer 4 (L4) TCP proxy and support all protocols that Envoy supports.</li>
 	<li>Another consideration is the separation of trust domains between organizational teams. The Kubernetes Ingress API merges specification for L4 to Layer 7 (L7), making it difficult for different teams in organizations with separate trust domains (like SecOps, NetOps, ClusterOps, and Developers) to own ingress traffic management.</li>
</ul>
</li>
 	<li>Some cost/resources are as follows:
<ul>
 	<li>1 virtual CPU (vCPU) per peak thousand requests per second for the sidecar(s) with access logging (which is off by default in v1.1) and 0.5 without. Fluentd on the node is a big contributor to that cost because it captures and uploads logs.</li>
 	<li>Assuming a typical cache hit ratio (&gt;80%) for Mixer checks: 0.5 vCPU per peak thousand requests per second for the mixer pods.</li>
 	<li>Latency of approximately 8 ms is added to the 90th percentile latency.</li>
</ul>
</li>
 	<li>Mutual TLS (mTLS) costs are negligible on AES-NI capable hardware in terms of both CPU and latency.</li>
 	<li>Meshery is an open source, multiservice mesh-management plane that provisions different service meshes and sample applications and benchmarks the performance of service mesh deployments.</li>
</ul>
<h2>Chapter 04: Deploying Istio</h2>
<ul>
 	<li>To protect your cluster data, Dashboard deploys with a minimal role-based access control (RBAC) configuration by default.</li>
 	<li>No matter which approach you take to installing Istio, each will include installation of Kubernetes custom resource definitions (CRDs) for Istio.</li>
 	<li>When Istio CRDs are deployed, Istio's objects are registered as Kubernetes objects, providing a highly integrated experience with Kubernetes as a deployment platform.</li>
 	<li>After you apply a CRD to your Kubernetes cluster, they are stored in the etcd cluster, providing durability through replication and life cycle management.</li>
 	<li>The generally preferred method for any installation of Istio that might find its way into production is to use Helm or Ansible.</li>
 	<li>Be aware that while istioctl is still maintained and being enhanced as a CLI to manage Istio, kubectl is the preferred method of interaction with Istio's custom resources.</li>
 	<li>Use of mTLS permissive mode is recommended if you have existing services or applications in your Kubernetes cluster.</li>
 	<li>However, if you're starting with a fresh cluster, security best practices suggest switching to istio-demo-auth.yaml to enforce encryption of service traffic between sidecars.</li>
 	<li>Deleting the istio-system namespace will not uninstall Istio. It's a common mistake to think that it does, but deleting the istio-system removes Istio's control-plane components, leaving CRDs, sidecars, and other artifacts resident in your cluster.</li>
 	<li>Tiller is the server-side component of Helm that runs in your cluster. Tiller interacts directly with the Kubernetes API Server to install, upgrade, query, and remove Kubernetes resources. It also stores the objects that represent releases.</li>
 	<li>Part of the benefit of using a Helm-based method of deployment is that you can relatively easily customize your Istio configuration by adding one or more --set &lt;key&gt;=&lt;value&gt; installation options to the Helm command.</li>
 	<li>Production deployments typically take advantage of a package or configuration manager like Helm or Ansible. Istio deployments initially performed with these tools should also be upgraded to new versions of Istio using that same tool.</li>
</ul>
<h2>Chapter 05: Service Proxy</h2>
<ul>
 	<li>Forward proxies focusing on outbound traffic with the aim of improving performance and filtering requests are typically deployed as the interface between users on private networks and their internet requests.</li>
 	<li>Reverse proxies focus on inbound traffic coming from the internet to private networks. They are commonly used to secure and filter HTTP requests, providing load balancing across real (backend) servers.</li>
 	<li>Akin to reverse proxies, a service proxy is the client-side intermediary transiting requests on behalf of a service. The service proxy enables applications to send and receive messages over a channel as method calls.</li>
 	<li>Commonly, a given iptables environment will contain multiple tables: Filter, NAT, Mangle, and Raw. You can define your own tables; if you don't, the Filter table is used by default.</li>
 	<li>Envoy is HTTP/1.1- and HTTP/2-compatible with proxying capability for each protocol on both downstream and upstream.</li>
 	<li>WARNING: istioctl kube-inject is not idempotent
<ul>
 	<li>You cannot repeat the istioctl kube-inject operation on the output from a previous kube-inject. The kube-inject operation is not idempotent. For upgrade purposes, if you're using manual injection, we recommend that you keep the original noninjected YAML file so that the data-plane sidecars can be updated.</li>
</ul>
</li>
 	<li>One caveat: when using the namespaceSelector, make sure the namespace(s) you select really have the label you're using. Keep in mind that the built-in namespaces like default and kube-system don't have labels out of the box. Conversely, the namespace in the metadata section is the actual name of the namespace, not a label.</li>
 	<li>Init containers are often used to perform provisioning tasks like bundling assets, performing database migration, or cloning a Git repository into a volume. In Istio's case, init containers are used to set up network filters' iptables' to control the flow of traffic.</li>
 	<li>Istio's default security posture dictates that, by default, Pilot needs to be informed of which endpoints external to the cluster are acceptable to send traffic to.</li>
 	<li>Application of the Kubernetes network policy between the app and a sidecar is not possible. Only when an application's network traffic exits the pod will it encounter the Kubernetes network policy.</li>
</ul>
<h2>Chapter 06: Security and Identity</h2>
<ul>
 	<li>In Istio's case, the credential that services use when they communicate with one another is an X.509 certificate.</li>
 	<li>In Istio, authorization of service-to-service communication is configured with RBAC policies.</li>
 	<li>More specifically, Istio answers the question: "Can Service A perform action on Service B?" In other words, both entity and object are identities of services in the mesh.</li>
 	<li>Knowing what you're metering, metrics are useless data.</li>
 	<li>NOTE: In Kubernetes, a pod will use the "default" service account for the namespace it's deployed in if the ServiceAccount field is not set in the pod specification. This means that all services in the same namespace will share a single identity if service accounts aren't already set up for each service.</li>
 	<li>On Kubernetes, Istio encodes a service's ServiceAccount using the local cluster's name as the trust domain, and creates a path using the ServiceAccount name and namespace.</li>
 	<li>When the node agent dies and is restarted by the container orchestrator, it will attempt to retrieve fresh credentials for all workloads on the node.</li>
 	<li>NOTE: Envoy won't overwrite static configuration with configuration from the API, so you can't accidentally push a configuration to Envoy that makes it unable to communicate with the configuration server.</li>
 	<li>mTLS is TLS in which both parties, client and server, present certificates to each other. This allows the client to verify the identity of the server, like normal TLS, but it also allows the server to verify the identity of the client attempting to establish the connection.</li>
 	<li>Also, note that the default MeshPolicy must be named "default" or Istio will not recognize it correctly.</li>
 	<li>To roll out RBAC incrementally across the system, first enable RBAC in ON_WITH_INCLUSION mode. As you define policies for each service or namespace, add that service or namespace to the inclusion list. This allows you to enable RBAC service by service (or namespace by namespace).</li>
</ul>
<h2>Chapter 07: Pilot</h2>
<ul>
 	<li>Most values in MeshConfig cannot be updated dynamically, and you must restart the control plane for them to take effect.</li>
 	<li>Similarly, updates to values in ProxyConfig only take effect when you redeploy Envoy (e.g., in Kubernetes, when the pod is rescheduled).</li>
 	<li>MeshNetworks can be updated dynamically at runtime without restarting any control-plane components.</li>
 	<li>A physical listener is one where Envoy binds to the specified port. A virtual listener accepts traffic from a physical listener, but does not bind to a port (instead some physical listener must direct traffic to it).</li>
 	<li>These last two, istioctl proxy-config and istioctl proxy-status, are invaluable for understanding the state of network configuration in a deployment.</li>
 	<li>Meshery can validate the current state against the planned state of your Istio configuration, making deployment dry runs easier to manage, and validate that your configuration changes will have the desired effect.</li>
 	<li>Most often used for adjusting log levels, ControlZ allows you to independently and dynamically modify logging levels for each scope at runtime.</li>
</ul>
<h2>Chapter 08: Traffic Management</h2>
<ul>
 	<li>First, it's desirable to have your applications speak cleartext (communicate without encryption) to the sidecarred service proxy and let the service proxy handle transport security.</li>
 	<li>This allows the service proxy to gather L7 metadata about requests, which allows Istio to generate L7 metrics and manipulate traffic based on L7 policy. Without the service proxy performing TLS termination, Istio can generate metrics for and apply policy on only the L4 segment of the request, restricting policy to contents of the IP packet and TCP header (essentially, a source and destination address and port number).</li>
 	<li>It's important to note that within a VirtualService, the match conditions are checked at runtime in the order in which they appear. This means that the most specific match clauses should appear first, and less-specific clauses later. For safety, a "default" route, with no match conditions, should be provided.</li>
 	<li>There's a special, implicit Gateway in every Istio deployment called the mesh Gateway. This kind of Gateway has workloads that are represented by every service proxy in the mesh and exposes the wildcard host on every port.</li>
 	<li>A common tripping hazard using VirtualServices is when we try to update a VirtualService being used within the mesh to bind to a specific Gateway, displacing the mesh Gateway.</li>
 	<li>Istio ignores Kubernetes services because these services can implement only round-robin load balancing.</li>
 	<li>The one key limitation is that Istio will not perform routing based on the body of the request.</li>
 	<li>A true blue/green deployment requires double the resource capacity of a standard deployment (to have both a full blue and a full green deployment).</li>
 	<li>Canaries can be combined with in-place binary rollout strategies to get the rollback safety of a blue/green deployment while only requiring a constant amount of additional resources (spare capacity to schedule just a small number of additional workloads).</li>
 	<li>Of course, take care when using caller-supplied values (like cookies) to perform routing: ideally all services in your cluster should perform authentication and authorization on all requests.</li>
 	<li>Istio provides a lot of features to help build more resilient applications; most important being client-side load balancing, circuit breaking via outlier detection, automatic retry, and request timeouts. Istio also provides tools to inject faults into applications, allowing you to build programmatic, reproducible tests of your system's resiliency.</li>
 	<li>It's important to note that a DestinationRule applies only to hosts in Istio's service registry. If a ServiceEntry does not exist for a host, the DestinationRule is ignored.</li>
 	<li>Using Istio, you can write a set of reliable end-to-end tests of your application's behavior in the presence of failures of its dependencies.</li>
 	<li>One thing Istio can't control, though, is how client traffic gets to the ingress proxies. A common pattern in Kubernetes environments is to model Istio's ingress proxies as a NodePort service and then let the platform handle provisioning public IP addresses, DNS records, and so on.</li>
 	<li>By default, Istio allows routing of traffic to destinations that do not have a ServiceEntry. As a security best practice, this default setting should be inverted and services outside of the mesh should explicitly be whitelisted by creating service entries for them.</li>
</ul>
<h2>Chapter 09: Mixer and Policies in the Mesh</h2>
<ul>
 	<li>By default Istio deployments have two Mixer pods running in the control plane; one Mixer pod for telemetry and another for policy enforcement.</li>
 	<li>Performance and availability of the check API is important when you consider that the check API is consulted inline (synchronously) when the service proxy is processing each request.</li>
 	<li>Well-designed caches are key to enabling conscientiousness to security practices in distributed systems. Ideally, requests between services are authenticated and authorized at every single hop through the chain of upstream services.</li>
 	<li>Ideally, distributed systems have policy applied at every point in the service chain, not just at the edge. This is how we attain consistency of security throughout our distributed system.</li>
 	<li>Istio configuration lives in the Kubernetes API server. From Mixer's perspective, the Kubernetes API server is the configuration database. From Pilot's perspective, it's the service discovery mechanism.</li>
 	<li>NOTE: Which Policies Come from Pilot and Which Go Through Mixer?
<ul>
 	<li>Policies that affect traffic are defined in Pilot. Policies that call for enforcement of authentication and authorization on the request go through Mixer. If a policy needs to consult an external system to make a decision, it goes through Mixer.</li>
</ul>
</li>
</ul>
<h2>Chapter 10: Telemetry</h2>
<ul>
 	<li>The default interval for periodical reports is 10 seconds. It's recommended that this interval should not be in subseconds.</li>
</ul>
<h2>Chapter 11: Debugging Istio</h2>
<ul>
 	<li>Depending on your environment, Meshery will automatically connect your cluster(s), analyze your mesh and workload configuration, and highlight divergence from configuration best practices or suggest remediation to problem areas of your deployment think of WebSockets as a protocol that transforms HTTP into a bidirectional byte-streaming protocol.</li>
 	<li>Avoid UID 1337. Ensure that your pods do not run applications as a user with the user ID (UID) value of 1337. The Istio service proxy uses 1337 as its UID.</li>
 	<li>HTTP/1.1 or HTTP/2.0 is required. Applications must use either the HTTP/1.1 or HTTP/2.0 protocols for all its HTTP traffic; HTTP/1.0 is not supported.</li>
 	<li>Service ports must be named. To use Istio's traffic routing, ensure each service has port name key/value pairs following this syntax: name: &lt;protocol&gt;[-&lt;suffix&gt;].</li>
 	<li>Pods must include an explicit list of the ports on which each container listens. Use a containerPortconfiguration in the container specification for each port. Any unlisted ports bypass the Istio proxy.</li>
 	<li>Associate all pods to at least one service. Whether it exposes a port or not, all pods must belong to at least one Kubernetes service.</li>
 	<li>Pod configuration must allow NET_ADMIN capability. If your cluster enforces pod security policies, pods must allow the NET_ADMIN capability.</li>
 	<li>If you use the Istio CNI Plugin, the NET_ADMIN capability requirement does not apply, because the CNI plug-in (a privileged pod) will perform administrative functions on behalf of the istio-init container.</li>
 	<li>The helm template install (upgrade) process takes advantage of Kubernetes rolling update process and will upgrade all deployments and configmaps to the new version. Using this approach, you can roll back if needed by applying the YAML files from the old version.</li>
 	<li>Currently the Envoy Sidecar Proxy must run as istio-proxy with UID 1337 and is not a centrally configurable deployment option.</li>
</ul>
<h2>Chapter 12: Real-World Considerations for Application Deployment</h2>
<ul>
 	<li>A typical service mesh deployment will have several Pilot instances. Pilot, like the other Istio control-control-plane components, is a stateless service that can be horizontally scale as needed. In fact, this is the recommended best practice for production deployments.</li>
 	<li>There is one pain point related to scaling Pilot that's worth discussing. Because Envoy uses a gRPC stream to communicate configuration, there is no per-request load balancing across Pilot instances. Instead, each Envoy in an Istio deployment is sticky to its associated Pilot.</li>
 	<li>It is not possible to use Envoy's (or Istio's) own configuration to perform a percentage-based rollout of a new Pilot for Envoy to consume.</li>
 	<li>Mixer has two modes of operation with very different failure modes. In Policy mode, Mixer is part of the request path, and failures directly affect user traffic. This is because policy is necessarily blocking for requests. In Telemetry mode, Mixer is out of the request path and failures affect only the ability of the mesh to produce telemetry.</li>
 	<li>When you're upgrading Mixer policies, beware of the latency spike that you'll see when transitioning to a new instance. Mixer policies cache policy decisions very aggressively, and when you transition traffic to a new instance, you'll see latencies spike as checks miss cache and call policy backends for a decision.</li>
 	<li>We recommend that you treat management of changes' configuration and binary changes' identically.</li>
 	<li>By handling both in a single, consistent manner you can build a single set of practices and processes for mitigating service outages regardless of the root cause.</li>
 	<li>Every company making a serious investment in Kubernetes must deal with the realities of managing and deploying into multiple clusters.</li>
</ul>
<h2>Chapter 13: Advanced Scenarios</h2>
<ul>
 	<li>Mesh expansion is a topology that includes running traditional, nonmicroservice workloads (so, monolithic apps) on bare metal or VMs (or both) on your Istio service mesh.</li>
 	<li>Istio multicluster (single mesh) is a centralized approach for connecting multiple service meshes into a single service mesh. You do this by selecting a cluster that serves as the master cluster, with the others being remote clusters.</li>
 	<li>Istio defines locality as a geographic location using a combination of region, zone, and subzone concepts to prioritize load-balancing pools to control the geographic location where requests are sent.</li>
 	<li>The best way to think about Istio multicluster versus cross-cluster is to think centralized versus decentralized control planes, respectively.</li>
 	<li>From an operator point of view, the requirements are simpler for cross-cluster than they are for multicluster.</li>
 	<li>A cross-cluster topology can benefit you by removing the need for a VPN to connect each cluster together as you must do with multicluster (unless you're using v1.1's cluster-aware routing using Istio Gateways). It also protects you from having a single point of failure. The downside will be policies, which, for now, remain unique to each environment. If you want to apply the same policy globally, you'll need to do so individually in each cluster.</li>
 	<li>It's worth noting that Istio multicluster does not equal multicloud out of the box. Remember, the requirement is that all Kubernetes clusters must be able to route traffic to one another with no network overlap.</li>
</ul>
