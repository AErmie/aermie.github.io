---
layout: page
title: Book Review: Kubernetes Best Practices
date: 2020-01-20 08:59
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2019/12/KubernetesBestPractices-BookCover.jpg"><img class="alignleft size-medium wp-image-33106" src="/wp-content/uploads/2019/12/KubernetesBestPractices-BookCover-229x300.jpg" alt="" width="229" height="300" /></a>Recently, I finished reading <a href="https://www.amazon.ca/Kubernetes-Best-Practices-Blueprints-Applications/dp/1492056472/ref=sr_1_1?keywords=Kubernetes+Best+Practices&amp;qid=1577208830&amp;sr=8-1" target="_blank" rel="noopener noreferrer">Kubernetes Best Practices</a> by Brendan Burns, Eddie Villalba, Dave Strebel, and Lachlan Evenson.

I've recently been up on Kubernetes, so, I had some knowledge (but not a lot) with Kubernetes when I read this book.

I particularly found<span style="color: #000000;"> Chapter 3 (“<strong>Monitoring and Logging in Kubernetes</strong>”), Chapter 4 (“<strong>Configuration, Secrets, and RBAC</strong>"), Chapter 10 (“<strong>Pod and Container Security</strong>”), and Chapter 11 ("<strong>Policy and Governance for Your Cluster</strong>")</span> of great value.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 1: Setting Up a Basic Service</h2>
<ul>
 	<li>When declaring the state of your application, people typically prefer YAML to JSON, though Kubernetes supports them both. This is because YAML is somewhat less verbose and more human editable than JSON. However, itâ€™s worth noting that YAML is indentation sensitive; often errors in Kubernetes configurations can be traced to incorrect indentation in YAML. If things arenâ€™t behaving as expected, indentation is a good thing to check.</li>
 	<li>When it comes to laying out the filesystem for your application, itâ€™s generally worthwhile to use the folder organization that comes with the filesystem to organize your components. Typically, a single directory is used to encompass an Application Service for whatever definition of Application Service is useful for your team. Within that directory, subdirectories are used for subcomponents of the application.</li>
 	<li>In general, the image build process can be vulnerable to "supply-chain attacks." In such attacks, a malicious user injects code or binaries into some dependency from a trusted source that is then built into your application. Because of the risk of such attacks, it is critical that when you build your images you base them on only well-known and trusted image providers. Alternately, you can build all your images from scratch.</li>
 	<li>Though the version of a container image in an image registry is theoretically mutable, you should treat the version tag as immutable. In particular, some combination of the semantic version and the SHA hash of the commit where the image was built is a good practice for naming images (e.g., v1.0.1-bfeda01f). If you don't specify an image version, latest is used by default. Although this can be convenient in development, it is a bad idea for production usage because latest is clearly being mutated every time a new image is built.</li>
 	<li>Though in Kubernetes, a ReplicaSet is the resource that manages replicating a containerized application, so it is not a best practice to use it directly. Instead, you use the Deployment resource. A Deployment combines the replication capabilities of ReplicaSet with versioning and the ability to perform a staged rollout. By using a Deployment you can use Kubernetes' built-in tooling to move from one version of the application to the next.</li>
 	<li>When running an application, the Request is the reservation that is guaranteed on the host machine where it runs. The Limit is the maximum resource usage that the container will be allowed.</li>
 	<li>CI/CD is extremely difficult to retrofit into an existing, imperatively deployed application.</li>
 	<li>It is also a best practice to ensure that the contents of your cluster exactly match the contents of your source control. The best pattern to ensure this is to adopt a GitOps approach and deploy to production only from a specific branch of your source control, using Continuous Integration (CI)/Continuous Delivery (CD) automation.</li>
 	<li>By default, cluster resources are available only within the cluster itself. To expose our application to the world, we need to create a Service and load balancer to provide an external IP address and to bring traffic to our containers.</li>
 	<li>A ConfigMap contains multiple key/value pairs representing configuration information or a file. This configuration information can be presented to a container in a pod via either files or environment variables.</li>
 	<li>Changing the configuration doesn't actually trigger an update to existing pods. Only when the pod is restarted is the configuration applied. Because of this, the rollout isn't health based and can be ad hoc or random.</li>
 	<li>NOTE: Secrets in Kubernetes are stored unecrypted by default. If you want to store secrets encrypted, you can integrate with a key provider to give you a key that Kubernetes will use to encrypt all of the secrets in the cluster. Note that although this secures the keys against direct attacks to the etcd database, you still need to ensure that access via the Kubernetes API server is properly secured.</li>
 	<li>A Volume is effectively a file or directory that can be mounted into a running container at a user-specified location.</li>
 	<li>In the case of secrets, the Volume is created as a tmpfs RAM-backed filesystem and then mounted into the container. This ensures that even if the machine is physically compromised (quite unlikely in the cloud, but possible in the datacenter), the secrets are much more difficult to obtain by the attacker.</li>
 	<li>When running stateful workloads in Kubernetes its important to use remote PersistentVolumes to manage the state associated with the application.</li>
 	<li>Unlike secrets, PersistentVolumes are generally remote storage mounted through some sort of network protocol, either file based, such as Network File System (NFS) or Server Message Block (SMB), or block based (iSCSI, cloud-based disks, etc.).</li>
 	<li>Generally, for applications such as databases, block-based disks are preferable because they generally offer better performance, but if performance is less of a consideration, file-based disks can sometimes offer greater flexibility.</li>
 	<li>NOTE: Managing state in general is complicated, and Kubernetes is no exception. If you are running in an environment that supports stateful services (e.g., MySQL as a service, Redis as a service), it is generally a good idea to use those stateful services. Initially, the cost premium of a stateful Software as a Service (SaaS) might seem expensive, but when you factor in all the operational requirements of state (backup, data locality, redundancy, etc.), and the fact that the presence of state in a Kubernetes cluster makes it difficult to move applications between clusters, it becomes clear that, in most cases, storage SaaS is worth the price premium.</li>
 	<li>A StatefulSet gives slightly stronger guarantees such as consistent names (no random hashes!) and a defined order for scale-up and scale-down. When you are deploying a singleton, this is somewhat less important, but when you want to deploy replicated state, these attributes are very convenient.</li>
 	<li>Although many PersistentVolume types can be mounted to only a single pod, we can use volume claims to write a template that can be replicated and yet have each pod assigned its own specific PersistentVolume.</li>
 	<li>Create a headless Service. A headless Service doesn't have a cluster IP address; instead, it programs a DNS entry for every pod in the StatefulSet.</li>
 	<li>Use the following best practices: Most services should be deployed as Deployment resources. Deployments create identical replicas for redundancy and scale. Deployments can be exposed using a Service, which is effectively a load balancer. A Service can be exposed either within a cluster (the default) or externally. If you want to expose an HTTP application, you can use an Ingress controller to add things like request routing and SSL. Eventually you will want to parameterize your application to make its configuration more reusable in different environments. Packaging tools like Helm are the best choice for this kind of parameterization.</li>
</ul>
<h2>Chapter 2: Developer Workflows</h2>
<ul>
 	<li>If you choose to have a development cluster per user, the significant downside of this approach is that it will be more expensive and less efficient, and you will have a large number of different development clusters to manage. The extra costs come from the fact that each cluster is likely to be heavily underutilized. Also, with developers creating different clusters, it becomes more difficult to track and garbage-collect resources that are no longer in use.</li>
 	<li>Their own cluster, and from isolation, it's much more difficult for different developers to step on one another's toes.</li>
 	<li>The advantage of the cluster-per-user approach is simplicity: each developer can self-service manage</li>
 	<li>On the other hand, a single development cluster will be significantly more efficient; you can likely sustain the same number of developers on a shared cluster for one-third the price (or less). Plus, it's much easier for you to install shared cluster services, for example, monitoring and logging, which makes it significantly easier to produce a developer-friendly cluster.</li>
 	<li>The downside of a shared development cluster is the process of user management and potential interference between developers. Because the process of adding new users and namespaces to the Kubernetes cluster isn't currently streamlined, you will need to activate a process to onboard new developers.</li>
 	<li>The recommendation is to have a single large cluster for all developers. Although there are challenges in interference between developers, they can be managed and ultimately the cost efficiency and ability to easily add organization-wide capabilities to the cluster outweigh the risks of interference. But you will need to invest in a process for onboarding developers, resource management, and garbage collection.</li>
 	<li>Namespaces can serve as scopes for the deployment of services so that one user's frontend service doesn't interfere with another user's frontend service. Namespaces are also scopes for RBAC, ensuring that one developer cannot accidentally delete another developer's work.</li>
 	<li>In general, using an external identity system is a best practice because it doesn't require that you maintain two different sources of identity, but in some cases this isn't possible and you need to use certificates.</li>
 	<li>A reasonable practice is to also grant reader access to the entire cluster; in this way developers can see what others are doing in case it is interfering with their work. Be careful in granting such read access, however, because it will include access to secret resources in the cluster.</li>
 	<li>If you want to limit the amount of resources consumed by a particular namespace, you can use the ResourceQuota resource to set a limit to the total number of resources that any particular namespace consumes.</li>
 	<li>An alternate approach is to temporarily create and assign a namespace with a bounded time to live (TTL). This ensures that the developer thinks of the resources in the cluster as transient and that it is easy to build automation around the deletion of entire namespaces when their TTL has expired.</li>
 	<li>If you want to get more integrated with Kubernetes, you can use custom resource definitions (CRDs) to enable users to dynamically create and allocate new namespaces using the kubectl tool. If you have the time and inclination, this is definitely a good practice because it makes namespace management declarative and also enables the use of Kubernetes RBAC.</li>
 	<li>Because of this risk and because there is an alternative, the best practice is to delete and re-create the Deployment.</li>
 	<li>Following these best practices will help to ensure that developers are up and running quickly: Think about developer experience in three phases: onboarding, developing, and testing. Make sure that the development environment you build supports all three of these phases. When building a development cluster, you can choose between one large cluster and a cluster per developer. There are pros and cons to each, but generally a single large cluster is a better approach. When you add users to a cluster, add them with their own identity and access to their own namespace. Use resource limits to restrict how much of the cluster they can use. When managing namespaces, think about how you can reap old, unused resources. Developers will have bad hygiene about deleting unused things. Use automation to clean it up for them. Think about cluster-level services like logs and monitoring that you can set up for all users. Sometimes, cluster-level dependencies like databases are also useful to set up on behalf of all users using templates like Helm charts.</li>
 	<li>When thinking about enabling developers to successfully build applications on Kubernetes, it's important to think about the key goals around onboarding, iterating, testing, and debugging applications.</li>
 	<li>Likewise, it pays to invest in some basic tooling specific to user onboarding, namespace provisioning, and cluster services like basic log aggregation.</li>
</ul>
<h2>Chapter 3: Monitoring and Logging in Kubernetes</h2>
<ul>
 	<li>Black-box monitoring can still be useful for monitoring at the infrastructure level, but it lacks insights and context into how the application is operating.</li>
 	<li>The USE method is described as, "For every resource, check utilization, saturation, and error rates."</li>
 	<li>The USE and RED methods are complementary to each other given that the USE method focuses on the infrastructure components and the RED method focuses on monitoring the end-user experience for the application.</li>
 	<li>You should consider cAdvisor as the source of truth for all container metrics.</li>
 	<li>The Custom Metrics API allows monitoring systems to collect arbitrary metrics. This allows monitoring solutions to build custom adapters that will allow for extending outside the core resource metrics.</li>
 	<li>The canonical implementation of the Resource Metrics API is the metrics server. The metrics server gathers resource metrics such as CPU and memory. It gathers these metrics from the kubelet's API and then stores them in memory. Kubernetes uses these resource metrics in the scheduler, Horizontal Pod Autoscaler (HPA), and Vertical Pod Autoscaler (VPA).</li>
 	<li>kube-state-metrics is focused on identifying conditions on Kubernetes objects deployed to your cluster.</li>
 	<li>As of this writing, there are 22 object types that kube-state-metrics tracks. These are always expanding, and you can find the documentation in the Github repository.</li>
 	<li>One important aspect when looking at implementing a tool to monitor metrics is to look at how the metrics are stored. Tools that provide a time-series database with key/value pairs will give you a higher degree of attributes for the metric.</li>
 	<li>It's a good practice to monitor your cluster from a "utility cluster" to avoid a production issue also affecting your monitoring system.</li>
 	<li>TIP: Avoid creating too many dashboards (aka "The Wall of Graphs") because this can be difficult for engineers to reason with in troubleshooting situations. You might think having more information in a dashboard means better monitoring, but the majority of the time it causes more confusion for a user looking at the dashboard. Focus your dashboard design on outcomes and time to resolution.</li>
 	<li>From an end-user experience, having somewhere between 30 and 45 days worth of historical logs is a good fit. This allows for investigation of problems that manifest over a longer period of time, but also reduces the amount of resources needed to store logs.</li>
 	<li>You can think of Kubernetes audit logs as security monitoring because they give you insight into who did what within the system.</li>
 	<li>The first and recommended way is to send all application logs to STDOUT because this gives you a uniform way of application logging, and a monitoring daemon set can gather the logs directly from the Docker daemon.</li>
 	<li>The other way is to use a sidecar pattern and run a log forwarding container next to the application container in a Kubernetes pod. You might need to use this pattern if your application logs to the filesystem.</li>
 	<li>The tool should have the capability to run as a Kubernetes DaemonSet and also have a solution to run as a sidecar for applications that don't send logs to STDOUT.</li>
 	<li>When looking for a tool to centralize logs, hosted solutions can provide a lot of value because they offload a lot of the operational cost. Hosting your own logging solution seems great on day N, but as the environment grows, it can be very time consuming to maintain the solution.</li>
 	<li>You really want to focus alerting on events that affect your Service-Level Objectives (SLOs).</li>
 	<li>An alert to an on-call engineer should be an issue that needs immediate human attention and is affecting the UX of the application.</li>
 	<li>It's generally recommended to set a threshold of at least five minutes to help eliminate false positives.</li>
 	<li>When building notifications for alerts you want to ensure that you provide relevant information in the notification, for example, providing a link to a "playbook" that gives troubleshooting or other helpful information on resolving the issue.</li>
 	<li>You should also include information on the datacenter, region, app owner, and affected system in notifications. Providing all this information will allow engineers to quickly formalize a theory around the issue.</li>
 	<li>NOTE: For further insight on how to approach alerting on and managing systems, read "<a href="https://docs.google.com/document/d/199PqyG3UsyXlwieHaqbGiWVa8eMWi8zzAn0YfcApr8Q/edit?usp=drivesdk" target="_blank" rel="noopener noreferrer">My Philosophy on Alerting</a>" by Rob Ewaschuk, which is based on Rob's observations as a site reliability engineer (SRE) at Google.</li>
 	<li>The following are the best practices that you should adopt regarding monitoring, logging, and alerting.
<ul>
 	<li>Monitoring
<ul>
 	<li>Monitor nodes and all Kubernetes components for utilization, saturation, and error rates, and monitor applications for rate, errors, and duration.</li>
 	<li>Use black-box monitoring to monitor for symptoms and not predictive health of a system.</li>
 	<li>Use white-box monitoring to inspect the system and its internals with instrumentation.</li>
 	<li>Implement time-series-based metrics to gain high-precision metrics that also allow you to gain insight within the behavior of your application.</li>
 	<li>Utilize monitoring systems like Prometheus that provide key labeling for high dimensionality; this will give a better signal to symptoms of an impacting issue.</li>
 	<li>Use average metrics to visualize subtotals and metrics based on factual data. Utilize sum metrics to visualize the distribution across a specific metric.</li>
</ul>
</li>
 	<li>Logging
<ul>
 	<li>You should use logging in combination with metrics monitoring to get the full picture of how your environment is operating.</li>
 	<li>Be cautious of storing logs for more than 30 to 45 days and, if needed, "use cheaper resources for long-term archiving.</li>
 	<li>Limit usage of log forwarders in a sidecar pattern, as they will utilize a lot more resources. Opt for using a DaemonSet for the log forwarder and sending logs to STDOUT.</li>
</ul>
</li>
 	<li>Alerting
<ul>
 	<li>Be cautious of alert fatigue because it can lead to bad behaviors in people and processes.</li>
 	<li>Always look at incrementally improving upon alerting and accept that it will not always be perfect.</li>
 	<li>Alert for symptoms that affect your SLO and customers and not for transient issues that don't need immediate human attention.</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2>Chapter 4: Configuration, Secrets, and RBAC</h2>
<ul>
 	<li>ConfigMap API is meant more for string data that is not really sensitive data. If your application requires more sensitive data, the Secrets API is more appropriate.</li>
 	<li>The Secret data is represented as base64-encoded information, and it is critical to understand that this is not encrypted. As soon as the secret is injected into the pod, the pod itself can see the secret data in plain text.</li>
 	<li>Secret data is meant to be small amounts of data, limited by default in Kubernetes to 1 MB in size, for the base64-encoded data, so ensure that the actual data is approximately 750 KB because of the overhead of the encoding.</li>
 	<li>Secrets are also mounted into tmpfs only on the nodes that have a pod that requires the secret and are deleted when the pod that needs it is gone.</li>
 	<li>It is important to know that by default, secrets are stored in the etcd datastore of Kubernetes in plain text, and it is important that the system administrators or cloud service provider take efforts to ensure that the security of the etcd environment, including mTLS between the etcd nodes and enabling encryption at rest for the etcd data.</li>
 	<li>To support dynamic changes to your application without having to redeploy new versions of the pods, mount your ConfigMaps/Secrets as a volume and configure your application with a file watcher to detect the changed file data and reconfigure itself as needed.</li>
 	<li>Avoid mounting ConfigMaps/Secrets using the volumeMounts.subPath property. This will prevent the data from being dynamically updated in the volume if you update a ConfigMap/Secret with new data.</li>
 	<li>As soon as the ConfigMap/Secret is created, add it as a volume in your pod's specification. Then mount that volume into the container's filesystem.</li>
 	<li>ConfigMap/Secrets must exist in the namespace for the pods that will consume them prior to the pod being deployed. The optional flag can be used to prevent the pods from not starting if the ConfigMap/Secret is not present.</li>
 	<li>There is an alpha API called PodPresets that will allow ConfigMaps and secrets to be applied to all pods based on an annotation, without needing to write a custom admission controller.</li>
 	<li>Use an admission controller to ensure specific configuration data or to prevent deployments that do not have specific configuration values set.</li>
 	<li>If you're using Helm to release applications into your environment, you can use a life cycle hook to ensure the ConfigMap/Secret template is deployed before the Deployment is applied.</li>
 	<li>Some applications require their configuration to be applied as a single file such as a JSON or YAML file. ConfigMap/Secrets allows an entire block of raw data by using the | symbol</li>
 	<li>If the application uses system environment variables to determine its configuration, you can use the injection of the ConfigMap data to create an environment variable mapping into the pod.</li>
 	<li>If you're using the configMapKeyRef or secretKeyRef method, be aware that if the actual key does not exist, this will prevent the pod from starting.</li>
 	<li>If you're loading all of the key/value pairs from the ConfigMap/Secret into the pod using envFrom, any keys that are considered invalid environment values will be skipped; however, the pod will be allowed to start. The event for the pod will have an event with reason InvalidVariableNames and the appropriate message about which key was skipped.</li>
 	<li>If there is a need to pass command-line arguments to your containers, environment variable data can be sourced using $(ENV_KEY) interpolation syntax</li>
 	<li>Update in the pod and will require a pod restart either through deleting the pods and letting the ReplicaSet controller create a new pod, or triggering a Deployment update, which will follow the proper application update strategy as declared in the Deployment specification.</li>
 	<li>When consuming ConfigMap/Secret data as environment variables, it is very important to understand that updates to the data in the ConfigMap/Secret will not that even if you're using environment variables or volumes, the code will take the new configuration data.</li>
 	<li>It is easier to assume that all changes to a ConfigMap/Secret require an update to the entire deployment; this ensures if you're using Helm to release your application code into Kubernetes, you can take advantage of an annotation in the Deployment template to check the sha256 checksum of the ConfigMap/Secret. This triggers Helm to update the Deployment using the helm upgrade command when the data within a ConfigMap/Secret is changed</li>
 	<li>Assign an imagePullSecrets to a serviceaccount that the pod will use to automatically mount the secret without having to declare it in the pod.spec.</li>
 	<li>Use CI/CD capabilities to get secrets from a secure vault or encrypted store with a Hardware Security Module (HSM) during the release pipeline. This allows for separation of duties. Security management teams can create and encrypt the secrets, and developers just need to reference the names of the secret expected. This is also the preferred DevOps process to ensure a more dynamic application delivery process.</li>
 	<li>The RBAC process in Kubernetes has three main components that need to be defined: the subject, the rule, and the role binding.</li>
 	<li>NOTE: Service accounts in Kubernetes are different than user accounts in that they are namespace bound, internally stored in Kubernetes; they are meant to represent processes, not people, and are managed by native Kubernetes controllers.</li>
 	<li>Kubernetes has two types of roles, role and clusterRole, the difference being that role is specific to a namespace, and clusterRole is a cluster-wide role across all</li>
 	<li>namespaces.</li>
 	<li>Bindings also have two modes: roleBinding, which is specific to a namespace, and clusterRoleBinding, which is across the entire cluster.</li>
 	<li>Applications that are developed to run in Kubernetes rarely ever need an RBAC role and role binding associated to it. Only if the application code actually interacts directly with the Kubernetes API directly does the application require RBAC configuration.</li>
 	<li>Best practices:
<ul>
 	<li>To a service, or if it needs to list all of the pods in a specific namespace, the best practice is to create a new service account that is then specified in the pod specification. Then, create a role that has the least amount of privileges needed to accomplish its goal.</li>
 	<li>If the application does need to directly access the Kubernetes API to perhaps change configuration depending on endpoints being added</li>
 	<li>Use an OpenID Connect service that enables identity management and, if needed, two-factor authentication. This will allow for a higher level of identity authentication. Map user groups to roles that have the least amount of privileges needed to accomplish the job.</li>
 	<li>You should use Just in Time (JIT) access systems to allow site reliability engineers (SREs), operators, and those who might need to have escalated privileges for a short period of time to accomplish a very specific task.</li>
 	<li>Specific service accounts should be used for CI/CD tools that deploy into your Kubernetes clusters. This ensures for auditability within the cluster and an understanding of who might have deployed or deleted any objects in a cluster.</li>
 	<li>If you're using Helm to deploy applications, the default service account is Tiller, deployed to kube-system. It is better to deploy Tiller into each namespace with a service account specifically for Tiller that is scoped for that namespace. In the CI/CD tool that calls the Helm install/upgrade command, as a prestep, initialize the Helm client with the service account and the specific namespace for the deployment. The service account name can be the same for each namespace, but the namespace should be specific.</li>
 	<li>Limit any applications that require watch and list on the Secrets API. This basically allows the application or the person who deployed the pod to view the secrets in that namespace. If an application needs to access the Secrets API for specific secrets, limit using get on any specific secrets that the application needs to read outside of those that it is directly assigned.</li>
</ul>
</li>
</ul>
<h2>Chapter 5: Continuous Integration, Testing, and Deployment</h2>
<ul>
 	<li>The goal of CI/CD is to have a fully automated process, from a developer checking in code to rolling out the new code to production. You want to avoid manually rolling out updates to your apps deployed to Kubernetes because it can be very error-prone.</li>
 	<li>Git has become the industry standard as a source-control management platform, and every Git repository will contain a master branch. A master branch contains your production code.</li>
 	<li>We find that including both application code and configuration code, such as a Kubernetes manifest or Helm charts, helps promote good DevOps principles of communication and collaboration.</li>
 	<li>Having both application developers and operation engineers collaborate in a single repository builds confidence in a team to deliver an application to production.</li>
 	<li>As you begin automating the delivery of infrastructure and applications to production, you need to think about running automated tests against all of the pieces of the codebase.</li>
 	<li>Testing the codebase and its delivery to production is a team effort and needs to be implemented end to end.</li>
 	<li>The following strategies will help you build the smallest image possible for your application:
<ul>
 	<li>Multistage builds
<ul>
 	<li>These allow you to remove the dependencies not needed for your applications to run.</li>
</ul>
</li>
 	<li>Distroless base images
<ul>
 	<li>These remove all the unneeded binaries and shells from the image. This really reduces the size of the image and increases the security. The trade-off with distroless images is you don't have a shell, so you can't attach a debugger to the image. You might think this is great, but it can be a pain to debug an application. Distroless images contain no package manager, shell, or other typical OS packages, so you might not have access to the debugging tools you are accustomed to with a typical OS.</li>
</ul>
</li>
 	<li>Optimized base images
<ul>
 	<li>These are images that focus on removing the cruft out of the OS layer and provide a slimmed-down image.</li>
</ul>
</li>
</ul>
</li>
 	<li>This might be a good option for you because its optimized images give you capabilities you expect for development while also optimizing for image size and lower security exposure.</li>
 	<li>Optimizing your images is extremely important and often overlooked by users. You might have reasons due to company standards for OSes that are approved for use in the enterprise, but push back on these so that you can maximize the value of containers.</li>
 	<li>It's important to have an image tagging strategy so that you can easily identify the versioned images you have deployed to your environments.</li>
 	<li>One of the most important things we can't preach enough about is not to use "latest" as an image tag. Using that as an image tag is not a version and will lead to not having the ability to identify what code change belongs to the rolled-out image. Every image that is built in the CI pipeline should have a unique tag for the built image.</li>
 	<li>The following strategies allow you to easily identify the code changes and the build with which they are associated:
<ul>
 	<li>BuildID
<ul>
 	<li>When a CI build kicks off, it has a buildID associated with it. Using this part of the tag allows you to reference which build assembled the image.</li>
</ul>
</li>
 	<li>Build System-BuildID
<ul>
 	<li>This one is the same as BuildID but adds the Build System for users who have multiple build systems.</li>
</ul>
</li>
 	<li>Git Hash
<ul>
 	<li>On new code commits, a Git hash is generated, and using the hash for the tag allows you to easily reference which commit generated the image.</li>
</ul>
</li>
 	<li>githash-buildID
<ul>
 	<li>This allows you to reference both the code commit and the buildID that generated the image. The only caution here is that the tag can be kind of long.</li>
</ul>
</li>
</ul>
</li>
 	<li>One thing to keep in mind is that you need to have a solid CI pipeline set up before focusing on CD. If you don't have a robust set of tests to catch issues early in the pipeline, you'll end up rolling bad code to all your environments.</li>
 	<li>Rolling updates are built into Kubernetes and allow you to trigger an update to the currently running application without downtime.</li>
 	<li>A Deployment object also lets you configure the maximum amount of replicas to be updated and the maximum unavailable pods during the rollout.</li>
 	<li>You need to be cautious with rolling updates because using this strategy can cause dropped connections. To deal with this issue, you can utilize readiness probes and preStop life cycle hooks.</li>
 	<li>The readiness probe ensures that the new version deployed is ready to accept traffic, whereas the preStop hook can ensure that connections are drained on the current deployed application.</li>
 	<li>Another concern with rolling updates is that you now have two versions of the application running at the same time during the rollover. Your database schema needs to support both versions of the application. You can also use a feature flag strategy in which your schema indicates the new columns created by the new app version. After the rolling update has completed, the old columns can be removed.</li>
 	<li>NOTE: Canary releases also suffer from having multiple versions of the application running at the same time. Your database schema needs to support both versions of the application. When using these strategies, you'll need to really focus on how to handle dependent services and having multiple versions running. This includes having strong API contracts and ensuring that your data services support the multiple versions you have deployed at the same time.</li>
 	<li>You need to ensure that you have an in-depth observability strategy in place, in which you have the ability to identify the effects of testing in production.</li>
 	<li>You also need a high degree of automation in place to be able to automatically recover from failures that you inject into your systems.</li>
 	<li>Consider some of the following best practices to iteratively improve on the pipeline:
<ul>
 	<li>With CI, focus on automation and providing quick builds. Optimizing the build speed will provide developers quick feedback if their changes have broken the build.</li>
 	<li>Focus on providing reliable tests in your pipeline. This will give developers rapid feedback on issues with their code. The faster the feedback loop to developers, the more productive they'll become in their workflow.</li>
 	<li>When deciding on CI/CD tools, ensure that the tools allow you to define the pipeline as code. This will allow you to version-control the pipeline with your application code.</li>
 	<li>Ensure that you optimize your images so that you can reduce the size of the image and also reduce the attack surface when running the image in production. Multistage Docker builds allow you to remove packages not needed for the application to run.</li>
 	<li>Avoid using "latest" as an image tag, and utilize a tag that can be referenced back to the buildID or Git commit.</li>
 	<li>If you are new to CD, utilize Kubernetes rolling upgrades to start out. They are easy to use and will get you comfortable with deployment. As you become more comfortable and confident with CD, look at utilizing blue/green and canary deployment strategies.</li>
 	<li>With CD, ensure that you test how client connections and database schema upgrades are handled in your application.</li>
 	<li>Testing in production will help you build reliability into your application, and ensure that you have good monitoring in place. With testing in production, also start at a small scale and limit the blast radius of the experiment.</li>
</ul>
</li>
</ul>
<h2>Chapter 6: Versioning, Releases, and Rollouts</h2>
<ul>
 	<li>The patch signifies an incremental release that includes a bug fix or very minor change that has no API changes. The minor version signifies updates that might have new API changes but is backward compatible with the previous version.</li>
 	<li>The major version is a breaking change increment to the code. In most cases, the API is no longer compatible between major versions of the same code.</li>
 	<li>It is important to understand that label selectors are immutable after they are created, which means if you add a new selector and the pod's labels have a corresponding match, a new ReplicaSet is made, not an upgrade to an existing ReplicaSet. This becomes very important to understand when dealing with rollouts</li>
 	<li>The Deployment controller is able to determine changes to the specification and will take action to update the Deployment based on a strategy that is defined by the specification. Kubernetes deployments support two strategies, rollingUpdate and recreate, the former being the default.</li>
 	<li>The best practices noted below can help to define consistent parameters that can assist DevOps teams in delivering smooth software deployments:
<ul>
 	<li>Use semantic versioning for the application in its entirety that differs from the version of the containers and the version of the pods deployment that make up the entire application. This allows for independent life cycles of the containers that make up the application and the application as a whole. This can become quite confusing at first, but if a principled hierarchical approach is taken to when one changes the other, you can easily track it.</li>
 	<li>Use a release and release version/number label in your deployment metadata to track releases from CI/CD pipelines. The release name and release number should coordinate with the actual release in the CI/CD tool records. This allows for traceability through the CI/CD process into the cluster and allows for easier rollback identification.</li>
 	<li>If Helm is being used to package services for deployment into Kubernetes, take special care to bundle together those services that need to be rolled back or upgraded together into the same Helm chart.</li>
 	<li>Agree on a release nomenclature that makes sense for the operational tempo of the organization. Simple stable, canary, and alpha states are quite adequate for most situations.</li>
</ul>
</li>
</ul>
<h2>Chapter 7: Worldwide Application Distribution and Staging</h2>
<ul>
 	<li>Any time that you do see a failure in production that wasn't caught by testing, it is a strong indicator that you need to extend and expand your testing.</li>
 	<li>This time-to-smoke period is a measure of generally how long it takes between a rollout completing and your monitoring seeing some sign of a problem.</li>
 	<li>The time-to-smoke is the probability distribution that indicates how long you should wait in order to have a strong probability that your release is operating correctly. Generally speaking, a decent rule of thumb is doubling the average time it takes for a problem to manifest.</li>
 	<li>At this point, it might be tempting to accelerate your rollout, but it is critically important to roll out only to a single region that represents any significant change in either input or load to your release.</li>
 	<li>In the heat and panic of a crisis, your brain is significantly stressed and it is much more difficult to remember even the simplest processes.</li>
 	<li>It is critical that you are capable of responding quickly, calmly, and correctly when a problem happens with a rollout.</li>
 	<li>In the heat of the moment, even the most obvious and easy steps can be the ones that are forgotten and accidentally skipped.</li>
 	<li>To ensure that everything necessary is done, and done in the correct order, it pays to have a clear checklist of tasks organized in the order in which they are to be executed as well as the expected output for each step. Write down every step, no matter how obvious it</li>
 	<li>You might need to make architectural changes to make this possible. You might need to add automation so that humans aren't cutting and pasting commands.</li>
 	<li>You too need to set up a regular cadence of practice to ensure that everyone on a team stays well versed in the proper responses and (perhaps more important) that your responses stay up to date as your system changes.</li>
 	<li>Worldwide Rollout Best Practices
<ul>
 	<li>Distribute each image around the world. A successful rollout depends on the release bits (binaries, images, etc.) being nearby to where they will be used. This also ensures reliability of the rollout in the presence of networking slowdowns or irregularities. Geographic distribution should be a part of your automated release pipeline for guaranteed consistency.</li>
 	<li>Shift as much of your testing as possible to the left by having as much extensive integration and replay testing of your application as possible. You want to start a rollout only with a release that you strongly believe to be correct.</li>
 	<li>Begin a release in a canary region, which is a preproduction environment in which other teams or large customers can validate their use of your service before you begin a larger-scale rollout.</li>
 	<li>Identify different characteristics of the regions where you are rolling out. Each difference can be one that causes a failure and a full or partial outage. Try to roll out to low-risk regions first.</li>
 	<li>Document and practice your response to any problem or process (e.g., a rollback) that you might encounter. Trying to remember what to do in the heat of the moment is a recipe for forgetting something and making a bad problem worse."</li>
</ul>
</li>
</ul>
<h2>Chapter 8: Resource Management</h2>
<ul>
 	<li>The difference is that you use a nodeSelector when you want to request a GPU-enabled node, whereas a taint reserves a node for only GPU workloads.</li>
 	<li>Taints are used on nodes to repel pods from being scheduled on them.</li>
 	<li>Taints work in conjunction with tolerations, which allow you to override tainted nodes. The combination of the two gives you fine-grained control over anti-affinity rules.</li>
 	<li>In general, you will use taints and tolerations for the following use cases:
<ul>
 	<li>Specialized node hardware</li>
 	<li>Dedicated node resources</li>
 	<li>Avoiding degraded nodes</li>
</ul>
</li>
 	<li>Managing pod resources consists of managing CPU and memory to optimize the overall utilization of your Kubernetes cluster.</li>
 	<li>With CPU limits, the container is throttled from using more than its specified limit. With memory limits, the pod is restarted if it reaches its limit. The pod might be restarted on the same host or a different host within the cluster.</li>
 	<li>A PodDisruptionBudget allows you to set a policy on the minimum available and maximum unavailable pods during voluntary eviction events</li>
 	<li>It's essential that when designing your Kubernetes cluster you think about the sizing of the cluster resources so that you can handle a number of failed nodes.</li>
 	<li>NOTE: When specifying a pod disruption budget as a percentage, it might not correlate to a specific number of pods.</li>
 	<li>In this case, Kubernetes rounds up to the closest integer</li>
 	<li>If you have multiple teams that will be using a single cluster, it is typically best to allocate a namespace to each team. If the cluster is dedicated to only one team, it might make sense to allocate a namespace for each service deployed to the cluster. There's no single solution to this; your team organization and responsibilities will drive the design.</li>
 	<li>TIP: When dealing with multiple namespaces and clusters, it can be a pain to set different namespaces and cluster context. We've found that using kubens and kubectx can help make it easy to switch between these different namespaces and contexts.</li>
 	<li>When multiple teams or applications share a single cluster, it's important to set up ResourceQuotas on your namespaces. ResourceQuotas allow you to divvy up the cluster in logical units so that no single namespace can consume more than its share of resources in the cluster.</li>
 	<li>There are things that you need to take into consideration with cluster autoscaling, and we have found that most users are better off starting with just manually scaling their nodes proactively when resources are needed.</li>
 	<li>The downside of the Cluster Autoscaler is that a new node is added only before a pod goes pending, so your workload may end up waiting for a new node to come online when it is scheduled.</li>
 	<li>You'll want to use a PodDisruptionBudget to ensure that you don't negatively affect your application when it performs its drain operation to remove the node from the cluster.</li>
 	<li>Setting the minimum and maximum is critical because you don't want the HPA to scale the replicas to an infinite amount due to an application bug or issue.</li>
 	<li>NOTE: To learn more about the internal details of the autoscaling algorithm, check out the design proposal. As of Kubernetes v1.15, the VPA is not recommended for production deployments.</li>
 	<li>Resource Management Best Practices
<ul>
 	<li>Utilize pod anti-affinity to spread workloads across multiple availability zones to ensure high availability for your application.</li>
 	<li>If you're using specialized hardware, such as GPU-enabled nodes, ensure that only workloads that need GPUs are scheduled to those nodes by utilizing taints.</li>
 	<li>Use NodeCondition taints to proactively avoid failing or degraded nodes.</li>
 	<li>Apply nodeSelectors to your pod specifications to schedule pods to specialized hardware that you have deployed in the cluster.</li>
 	<li>Before going to production, experiment with different node sizes to find a good mix of cost and performance for node types.</li>
 	<li>If you're deploying a mix of workloads with different performance characteristics, utilize node pools to have mixed node types in a single cluster.</li>
 	<li>Ensure that you set memory and CPU limits for all pods deployed to your cluster.</li>
 	<li>Utilize ResourceQuotas to ensure that multiple teams or applications are alotted their fair share of resources in the cluster.</li>
 	<li>Implement LimitRange to set default limits and requests for pod specifications that don't set limits or requests.</li>
 	<li>Start with manual cluster scaling until you understand your workload profiles on Kubernetes. You can use autoscaling, but it comes with additional considerations around node spin-up time and cluster scale down.</li>
 	<li>Use the HPA for workloads that are variable and that have unexpected spikes in their usage.</li>
</ul>
</li>
</ul>
<h2>Chapter 9: Networking, Network Security, and Service Mesh</h2>
<ul>
 	<li>Kubenet is the most basic network plug-in that comes out of the box in Kubernetes. It is the simplest of the plug-ins and provides a Linux bridge, cbr0, thatâ€™s a virtual Ethernet pair for the pods connected to it.</li>
 	<li>Kubenet Best Practices
<ul>
 	<li>Kubenet allows for a simplistic network stack and does not consume precious IP addresses on already crowded networks. This is especially true of cloud networks that are extended to on-premises datacenters.</li>
 	<li>Ensure that the pod CIDR range is large enough to handle the potential size of the cluster and the pods in each cluster. The default pods per node set in kubelet is 110, but you can adjust this.</li>
 	<li>Understand and plan accordingly for the route rules to properly allow traffic to find pods in the proper nodes. In cloud providers, this is usually automated, but on-premises or edge cases will require automation and solid network management.</li>
</ul>
</li>
 	<li>CNI Best Practices
<ul>
 	<li>Evaluate the feature set needed to accomplish the overall networking goals of the infrastructure. Some CNI plug-ins provide native high availability, multicloud connectivity, Kubernetes network policy support, and various other features.</li>
 	<li>If you are running clusters via public cloud providers, verify that any CNI plug-ins that are not native to the cloud provider's Software-Defined Network (SDN) are actually supported.</li>
 	<li>Verify that any network security tools, network observability, and management tools are compatible with the CNI plug-in of choice, and if not, research which tools can replace the existing ones.</li>
 	<li>Whatever tool you use, it should at least provide insight into the network stack and the Four Golden signals, made popular by the amazing Google SRE team and Rob Ewashuck: Latency, Traffic, Errors, and Saturation.</li>
 	<li>If you're using CNIs that do not provide an overlay network separate from the SDN network space, ensure that you have proper network address space to handle node IPs, pod IPs, internal load balancers, and overhead for cluster upgrade and scale out processes.</li>
</ul>
</li>
 	<li>Services and Ingress Controllers Best Practices
<ul>
 	<li>Limit the number of services that need to be accessed from outside the cluster. Ideally, most services will be ClusterIP, and only external-facing services will be exposed externally to the cluster.</li>
 	<li>If the services that need to be exposed are primarily HTTP/HTTPS-based services, it is best to use an Ingress API and Ingress controller to route traffic to backing services with TLS termination. Depending on the type of Ingress controller used, features such as rate limiting, header rewrites, OAuth authentication, observability, and other services can be made available without having to build them into the applications themselves.</li>
 	<li>Choose an Ingress controller that has the needed functionality for secure ingress of your web-based workloads. Standardize on one and use it across the enterprise because many of the specific configuration annotations vary between implementations and prevent the deployment code from being portable across enterprise Kubernetes implementations.</li>
 	<li>Evaluate cloud service provider-specific Ingress controller options to move the infrastructure management and load of the ingress out of the cluster, but still allow for Kubernetes API configuration.</li>
 	<li>When serving mostly APIs externally, evaluate API-specific Ingress controllers, such as Kong or Ambassador, that have more fine-tuning for API-based workloads. Although NGINX, Traefik, and others might offer some API tuning, it will not be as fine-grained as specific API proxy systems.</li>
 	<li>When deploying Ingress controllers as pod-based workloads in Kubernetes, ensure that the deployments are designed for high availability and aggregate performance throughput. Use metrics observability to properly scale the ingress, but include enough cushion to prevent client disruptions while the workload scales.</li>
</ul>
</li>
 	<li>Network policies have a simple YAML structure that can look complicated, but if you think of it as a simple East-West traffic firewall, it might help you to understand it a little better.</li>
 	<li>You can create multiple NetworkPolicy definitions that can target the same pods, and the effect is additive in nature.</li>
 	<li>If a pod falls into the scope of a policy because of a selector match, all traffic, unless explicitly defined in an ingress or egress rule, is blocked. This little, nuanced detail means that if a pod does not fall into any policy because of a selector match, all ingress and egress is allowed to the pod.</li>
 	<li>If you leave the ingress field empty, it is like a deny-all inbound. Similarly, if you leave the egress empty, it is deny-all outbound.</li>
 	<li>Ingress is assumed, and defining it explicitly is not needed.</li>
 	<li>Network Policy Best Practices
<ul>
 	<li>Start off slow and focus on traffic ingress to pods. Complicating matters with ingress and egress rules can make network tracing a nightmare. As soon as traffic is flowing as expected, you can begin to look at egress rules to further control flow to sensitive workloads. The specification also favors ingress because it defaults many options even if nothing is entered into the ingress rules list.</li>
 	<li>Ensure that the network plug-in used either has some of its own interface to the NetworkPolicy API or supports other well-known plug-ins.</li>
 	<li>If the network team is used to having a "default-deny" policy in place, create a network policy such as the following for each namespace in the cluster that will contain workloads to be protected. This ensures that even if another network policy is deleted, no pods are accidentally "exposed"
<ul>
 	<li>If there are pods that need to be accessed from the internet, use a label to explicitly apply a network policy that allows ingress. Be aware of the entire flow in case the actual IP that a packet is coming from is not the internet, but the internal IP of a load balancer, firewall, or other network device.</li>
</ul>
</li>
 	<li>Try to align application workloads to single namespaces for ease of creating rules because the rules themselves are namespace specific. If cross-namespace communication is needed, try to be as explicit as possible and perhaps use specific labels to identify the flow pattern.</li>
 	<li>Have a test bed namespace that has fewer restrictive policies, if any at all, to allow time to investigate the correct traffic patterns needed.</li>
</ul>
</li>
 	<li>The majority of service meshes available today inject a proxy that is part of the data plane into each pod that is a member of the mesh. This allows for policies and security to be synchronized across the mesh by the control-plane components.</li>
 	<li>Service Mesh Best Practices
<ul>
 	<li>These best practices are, as of this writing, based on common necessities that service meshes try to solve today:</li>
 	<li>Rate the importance of the key features service meshes offer and determine which current offerings provide the most important features with the least amount of overhead. Overhead here is both human technical debt and infrastructure resource debt.</li>
 	<li>Is the need for a cross-system mesh such as multicloud or hybrid scenarios a key requirement? Not all service meshes offer this capability, and if they do, it is a complicated process that often introduces fragility into the environment.</li>
 	<li>Many of the service mesh offerings are open source community-based projects, and if the team that will be managing the environment is new to service meshes, commercially supported offerings might be a better option. There are companies that are beginning to offer commercially supported and managed service meshes based on Istio, which can be helpful because it is almost universally agreed upon that Istio is a complicated system to manage.</li>
</ul>
</li>
</ul>
<h2>Chapter 10: Pod and Container Security</h2>
<ul>
 	<li>PodSecurityPolicy is surprisingly difficult to implement effectively and will more often than not get turned off or evaded in other ways. We do, however, strongly suggest taking the time to fully understand PodSecurityPolicy because it's one of the single most effective means to reduce your attack surface area by limiting what can run on your cluster and with what level of privilege.</li>
 	<li>It's worth mentioning that enabling PodSecurityPolicy is not widely available among public cloud providers and cluster operations tools.</li>
 	<li>WARNING: Proceed with caution when enabling PodSecurityPolicy because it's potentially workload blocking if adequate preparation isn't done at the outset.</li>
 	<li>WARNING: If you are enabling PodSecurityPolicy on an existing cluster with running workloads, you must create all necessary policies, service accounts, roles, and role bindings before enabling the admission controller.</li>
 	<li>WARNING: It's extremely important to remember that having no PodSecurityPolicies defined will result in an implicit deny. This means that without a policy match for the workload, the pod will not be created.</li>
 	<li>PodSecurityPolicy is complex and can be error-prone. Refer to the following best practices before implementing PodSecurityPolicy on your clusters:
<ul>
 	<li>It all comes down to RBAC. Whether you like it or not, PodSecurityPolicy is determined by RBAC. It's this relationship that actually exposes all of the shortcomings in your current RBAC policy design. We cannot stress just how important it is to automate your RBAC and PodSecurityPolicy creation and maintenance. Specifically locking down access to service accounts is the key to using policy.</li>
 	<li>Understand the policy scope. Determining how your policies will be laid out on your cluster is very important. Your policies can be cluster-wide, namespaced, or workload-specific in scope. There will always be workloads on your cluster that are part of the Kubernetes cluster operations that will need more permissive security privileges, so make sure that you have appropriate RBAC in place to stop unwanted workloads using your permissive policies.</li>
 	<li>Do you want to enable PodSecurityPolicy on an existing cluster? Use this handy <a href="https://github.com/sysdiglabs/kube-psp-advisor" target="_blank" rel="noopener noreferrer">open-source tool</a> to generate policies based on your current resources. This is a great start. From there, you can hone your policies.</li>
</ul>
</li>
 	<li>With careful planning and a pragmatic approach, PodSecurityPolicy can be successfully implemented on any cluster.</li>
 	<li>Container runtimes are still largely considered an insecure workload isolation boundary.</li>
 	<li>How this is implemented under the hood is that the RuntimeClass designates a RuntimeHandler which is passed to the Container Runtime Interface (CRI) to implement.</li>
 	<li>The following best practices will help you to avoid common workload isolation and RuntimeClass pitfalls:
<ul>
 	<li>Implementing different workload isolation environments via RuntimeClass will complicate your operational environment. This means that workloads might not be portable across different container runtimes given the nature of the isolation they provide. Understanding the matrix of supported features across different runtimes can be complicated to understand and will lead to poor user experience. We recommend having separate clusters, each with a single runtime to avoid confusion, if possible.</li>
 	<li>Workload isolation doesn't mean secure multitenancy. Even though you might have implemented a secure container runtime, this doesn't mean that the Kubernetes cluster and APIs have been secured in the same fashion. You must consider the total surface area of Kubernetes end to end. Just because you have an isolated workload doesn't mean that it cannot be modified by a bad actor via the Kubernetes API.</li>
 	<li>Tooling across different runtimes is inconsistent. You might have users who rely on container runtime tooling for debugging and introspection. Having different runtimes means that you might no longer be able to run docker ps to list running containers. This leads to confusion and complications when troubleshooting.</li>
</ul>
</li>
</ul>
<h2>Chapter 11: Policy and Governance for Your Cluster</h2>
<ul>
 	<li>Rather than implementing policy at runtime, when we talk about policy in the context of governance, what we mean is defining policy that controls the fields and values in the Kubernetes resource specifications themselves.</li>
 	<li>Using CRDs allows for an integrated Kubernetes experience that decouples policy authoring from implementation.</li>
 	<li>Policy templates are referred to as constraint templates, which can be shared and reused across clusters.</li>
 	<li>The best way to think about constraints is as restrictions that you apply to specific fields and values of Kubernetes resource specifications. This is really just a long way of saying policy.</li>
 	<li>This means that when constraints are defined, you are effectively stating that you DO NOT want to allow this. The implications of this approach mean that resources are implicitly allowed without a constraint that issues a deny. This is important because instead of allowing the Kubernetes resources specification fields and values you want, you are denying only the ones you do not want.</li>
 	<li>Constraint templates consist of typed parameters and the target rego that is parameterized for reuse.</li>
 	<li>Constraint templates are a Custom Resource Definition (CRD) that provide a means of templating policy so that it can be shared or reused. In addition, parameters for the policy can be validated.</li>
 	<li>When multiple policies validate the same field, if one violates then the whole request is rejected</li>
 	<li>Gatekeeper uses a config resource to manage which data is cached in OPA in order to perform evaluations</li>
 	<li>The audit results are stored in the status field of the constraint, making them easy to find by simply using kubectl.</li>
 	<li>The Gatekeeper repository ships with fantastic demonstration content that walks you through a detailed example of building policies to meet compliance for a bank. We would strongly recommend walking through the demonstration for a hands-on approach to how Gatekeeper operates. You can find the demonstration in this Git repository.</li>
 	<li>You should consider the following best practices when implementing policy and governance on your clusters:
<ul>
 	<li>If you want to enforce a specific field in a pod, you need to make a determination of which Kubernetes resource specification you want to inspect and enforce.</li>
 	<li>Constraints can be applied to Kubernetes resources on the following criteria: kinds, namespaces, and label selectors. We would strongly recommend scoping the constraint to the resources to which you want it to be applied as tightly as possible. This ensures consistent policy behavior as the resources on the cluster grow, and means that resources that don't need to be evaluated aren't being passed to OPA, which can result in other inefficiencies.</li>
 	<li>Synchronizing and enforcing on potentially sensitive data such as Kubernetes secrets is not recommended. Given that OPA will hold this in its cache (if it is configured to replicate that data) and resources will be passed to Gatekeeper, it leaves surface area for a potential attack vector.</li>
 	<li>If you have many constraints defined, a deny of constraint means that the entire request is denied. There is no way to make this function as a logical OR.</li>
</ul>
</li>
</ul>
<h2>Chapter 12: Managing Multiple Clusters</h2>
<ul>
 	<li>Following are concerns to think about when deciding to use multicluster versus a single-cluster architecture:
<ul>
 	<li>Blast radius</li>
 	<li>Compliance</li>
 	<li>Security</li>
 	<li>Hard multitenancy</li>
 	<li>Regional-based workloads</li>
 	<li>Specialized workloads</li>
</ul>
</li>
 	<li>Dan Woods wrote a great <a href="https://medium.com/@daniel.p.woods/on-infrastructure-at-scale-a-cascading-failure-of-distributed-systems-7cff2a3cd2df" target="_blank" rel="noopener noreferrer">article</a> about an actual cascading failure in a production Kubernetes environment. It is a great example of why you will want to consider multicluster architectures for larger environments.</li>
 	<li>Compliant workloads might have specific requirements with respect to security hardening, nonshared components, or dedicated workload requirements.</li>
 	<li>If you decide that a larger Kubernetes cluster fits your requirements, then ensure that you have a very good operational process for making security changes and understand the blast radius of making a change to RBAC, network policy, and pod security policies.</li>
 	<li>Some of the common challenges we find users running into are:
<ul>
 	<li>Data replication</li>
 	<li>Service discovery</li>
 	<li>Network routing</li>
 	<li>Operational management</li>
 	<li>Continuous deployment</li>
</ul>
</li>
 	<li>Each Kubernetes cluster deploys its own service discovery registry, and registries are not synchronized across multiple clusters.</li>
 	<li>Ingress into the cluster is implemented as a 1:1 mapping of ingress to the cluster because it doesn't support multicluster topologies with the Ingress resource. You'll also need to consider the egress traffic between clusters and how to route that traffic.</li>
 	<li>One of the most important aspects to managing multiclusters is ensuring that you have good automation practices in place because this will help to reduce the operational burden.</li>
 	<li>Use a tool that allows you to source control your cluster deployment for repeatability.</li>
 	<li>Two tools that you will want to install right away when dealing with multiple clusters are kubectx and kubens, which allow you to easily change between multiple contexts and namespaces.</li>
 	<li>Consider the following best practices when managing multiple Kubernetes clusters:
<ul>
 	<li>Limit the blast radius of your clusters to ensure cascading failures don't have a bigger impact on your applications.</li>
 	<li>If you have regulatory concerns such as PCI, HIPPA, or HiTrust, think about utilizing multiclusters to ease the complexity of mixing these workloads with general workloads.</li>
 	<li>If hard multitenancy is a business requirement, workloads should be deployed to a dedicated cluster.</li>
 	<li>If multiple regions are needed for your applications, utilize a Global Load Balancer to manage traffic between clusters.</li>
 	<li>You can break out specialized workloads such as HPC into their own individual clusters to ensure that the specialized needs for the workloads are met.</li>
 	<li>If you're deploying workloads that will be spread across multiple regional datacenters, first ensure that there is a data replication strategy for the workload. Multiple clusters across regions can be easy, but replicating data across regions can be complicated, so ensure that there is a sound strategy to handle asynchronous and synchronous workloads.</li>
 	<li>Utilize Kubernetes operators like the prometheus-operator or Elasticsearch operator to handle automated operational tasks.</li>
 	<li>When designing your multicluster strategy, also consider how you will do service discovery and networking between clusters.</li>
 	<li>Be sure that your CD strategy can handle multiple rollouts between regions or multiple clusters.</li>
 	<li>Investigate utilizing a GitOps approach to managing multiple cluster operational components to ensure consistency between all clusters in your fleet. The GitOps approach doesn't always work for everyone's environment, but you should at least investigate it to ease the operational burden of multicluster environments.</li>
</ul>
</li>
</ul>
<h2>Chapter 13: Integrating External Services and Kubernetes</h2>
<ul>
 	<li>When you create a Kubernetes Service without a selector, there are no Pods that match the service; thus, there is no load balancing performed. Instead, you can program this selector-less service to have the specific IP address of the external resource that you want to add to the Kubernetes cluster. That way, when a Kubernetes pod performs a lookup for your-database, the built-in Kubernetes DNS server will translate that to a service IP address of your external service.</li>
 	<li>When you export a Service via an internal load balancer, you receive a stable, routeable IP address that is visible on the virtual network outside of the cluster. You then can either use that IP address directly or set up internal DNS resolution to provide discovery for your exported service.</li>
 	<li>When integrating an external machine into the cluster for networking, you need to ensure that the pod network routing and DNS-based service discovery both work correctly.</li>
 	<li>Connecting Cluster and External Services Best Practices
<ul>
 	<li>Establish network connectivity between the cluster and on-premises. Networking can be varied between different sites, clouds, and cluster configurations, but first ensure that pods can talk to on-premises machines and vice versa.</li>
 	<li>To access services outside of the cluster, you can use selector-less services and directly program in the IP address of the machine (e.g., the database) with which you want to communicate. If you don't have fixed IP addressess, you can instead use CNAME services to redirect to a DNS name. If you have neither a DNS name nor fixed services, you might need to write a dynamic operator that periodically synchronizes the external service IP addresses with the Kubernetes Service endpoints.</li>
 	<li>To export services from Kubernetes, use internal load balancers or NodePort services. Internal load balancers are typically easier to use in public cloud environments where they can be bound to the Kubernetes Service itself. When such load balancers are unavailable, NodePort services can expose the service on all of the machines in the cluster.</li>
 	<li>You can achieve connections between Kubernetes clusters through a combination of these two approaches, exposing a service externally that is then consumed as a selector-less service in the other Kubernetes cluster.</li>
</ul>
</li>
</ul>
<h2>Chapter 14: Running Machine Learning in Kubernetes</h2>
<ul>
 	<li>Many cloud providers offer multi-GPU virtual machine (VM) types, so we recommend scaling VMs vertically to four to eight GPUs before looking into distributed training.</li>
 	<li>Distributed training is still in its infancy and is difficult to optimize. Running a training job that requires eight GPUs will almost always be faster to train on a single eight-GPU machine compared to two machines each with four GPUs.</li>
 	<li>The only time that you should resort to using distributed training is when the model doesn't fit on the biggest machine available.</li>
 	<li>It's also worth mentioning that you cannot request fractions of GPUs (for example, 0.1), which means that even if the specific GPU supports running multiple threads concurrently, you will not be able to utilize that capacity.</li>
 	<li>To achieve optimal performance for your machine learning workloads, consider the following best practices:
<ul>
 	<li>Smart scheduling and autoscaling. Given that most stages of the machine learning workflow are batch by nature, we recommend that you utilize a Cluster Autoscaler.</li>
 	<li>We recommend batching jobs to run at specific times using either taints and tolerations or via a time-specific Cluster Autoscaler. That way, the cluster can scale to the needs of the machine learning workloads when needed, and not a moment sooner.</li>
 	<li>The truth is that model training is a delicate balance. Allowing things to move faster in one area often leads to bottlenecks in others. It's an endeavor of constant observation and tuning. As a general rule of thumb, we recommend that you try to make the GPU become the bottleneck because it is the most costly resource. Keep your GPUs saturated. Be prepared to always be on the lookout for bottlenecks, and set up your monitoring to track the GPU, CPU, network, and storage utilization.</li>
 	<li>Given the high performance requirements of machine learning workloads, we recommend using a separate node pool that's tainted to accept only machine learning workloads. This will help protect the rest of the cluster from any impact from the machine learning workloads running on the machine learning node pool. Furthermore, you should consider multiple GPU-enabled node pools, each with different performance characteristics to suit the workload types. We also recommend enabling node autoscaling on the machine learning node pool(s). Use mixed mode clusters only after you have a solid understanding of the performance impact that your machine learning workloads have on your cluster.</li>
 	<li>In our experience, it's almost always the model itself and not the infrastructure supporting it that is the source of the bottleneck.</li>
</ul>
</li>
</ul>
<h2>Chapter 15: Building Higher-Level Application Patterns on Top of Kubernetes</h2>
<ul>
 	<li>You could implement a linter for Kubernetes that ensures developers submit pods and other resources that follow best practices for using Kubernetes.</li>
 	<li>CRDs are a way to dynamically add new resources to an existing Kubernetes cluster.</li>
 	<li>When building such platforms, you'll benefit from keeping the following best practices in mind:
<ul>
 	<li>Use admission controllers to limit and modify API calls to the cluster. An admission controller can validate (and reject invalid) Kubernetes resources. A mutating admission controller can automatically modify API resources to add new sidecars or other changes that users might not even need to know about.</li>
 	<li>Use kubectl plug-ins to extend the Kubernetes user experience by adding new tools to the familiar existing command-line tool. In rare occasions, a purpose-built tool might be more appropriate.</li>
 	<li>When building platforms on top of Kubernetes, think carefully about the users of the platform and how their needs will evolve. Making things simple and easy to use is clearly a good goal, but if this also leads to users that are trapped and unable to be successful without rewriting everything outside of your platform, it will ultimately be a frustrating (and unsuccessful) experience.</li>
</ul>
</li>
</ul>
<h2>Chapter 16: Managing State and Stateful Applications</h2>
<ul>
 	<li>The reality is that volume mounting is the easy component in the grand scheme of stateful applications.</li>
 	<li>Volume Best Practices
<ul>
 	<li>Try to limit the use of volumes to pods requiring multiple containers that need to share data, for example adapter or ambassador type patterns. Use the emptyDir for those types of sharing patterns.</li>
 	<li>Use hostDir when access to the data is required by node-based agents or services.</li>
 	<li>Try to identify any services that write their critical application logs and events to local disk, and if possible change those to stdout or stderr and let a true Kubernetes-aware log aggregation system stream the logs instead of leveraging the volume map.</li>
</ul>
</li>
 	<li>Kubernetes manages storage for pods using two distinct APIs, the PersistentVolume and PersistentVolumeClaim.</li>
 	<li>It is best to think of a PersistentVolume as a disk that will back any volumes that are mounted to a pod. A PersistentVolume will have a claim policy that will define the scope of life of the volume independent of the life cycle of the pod that uses the volume.</li>
 	<li>Only when a PersistentVolumeClaim matches the PersistentVolume will it actually be assigned to a pod.</li>
 	<li>PersistentVolumeClaims are a way to give Kubernetes a resource requirement definition for storage that a pod will use. Pods will reference the claim, and then if a persistentVolume that matches the claim request exists, it will allocate that volume to that specific pod.</li>
 	<li>The Container Storage Interface (CSI) and FlexVolume enable storage vendors to create custom storage plug-ins without the need to wait for direct code additions to the Kubernetes code base like most volume plug-ins today.</li>
 	<li>These best practices around storage in Kubernetes in general will help to design an effective approach to providing the required storage implementations to the application design:
<ul>
 	<li>If possible, enable the DefaultStorageClass admission plug-in and define a default storage class. Many times, Helm charts for applications that require PersistentVolumes default to a default storage class for the chart, which allows the application to be installed without too much modification.</li>
 	<li>When designing the architecture of the cluster, either on-premises or in a cloud provider, take into consideration zone and connectivity between the compute and data layers using the proper labels for both nodes and PersistentVolumes, and using affinity to keep the data and workload as close as possible. The last thing you want is a pod on a node in zone A trying to mount a volume that is attached to a node in zone B.</li>
 	<li>Consider very carefully which workloads require state to be maintained on disk. Can that be handled by an outside service like a database system or, if running in a cloud provider, by a hosted service that is API consistent with currently used APIs, say a mongoDB or mySQL as a service?</li>
 	<li>Determine how much effort would be involved in modifying the application code to be more stateless.</li>
 	<li>While Kubernetes will track and mount the volumes as workloads are scheduled, it does not yet handle redundancy and backup of the data that is stored in those volumes. The CSI specification has added an API for vendors to plug in native snapshot technologies if the storage backend can support it.</li>
 	<li>Verify the proper life cycle of the data that volumes will hold. By default the reclaim policy is set to for dynamically provisioned persistentVolumes which will delete the volume from the backing storage provider when the pod is deleted. Sensitive data or data that can be used for forensic analysis should be set to reclaim.</li>
</ul>
</li>
 	<li>Kubernetes has no sense of what type of application it is deploying. It does not know that your database system requires leader election processes, that it can or cannot handle data replication between members of the set, or, for that matter, that it is a database system at all.</li>
 	<li>The headless Service is the same as a regular Service but does not do the normal load balancing</li>
 	<li>Stateful and Operator Best Practices
<ul>
 	<li>When an application requires ordinal naming and dependable scaling, it does not always mean it requires the assignment of PersistentVolumes.</li>
 	<li>If a node in the cluster becomes unresponsive, any pods that are part of a StatefulSet are not not automatically deleted; they instead will enter a Terminating or Unkown state after a grace period. The only way to clear this pod is to remove the node object from the cluster, the kubelet beginning to work again and deleting the pod directly, or an Operator force deleting the pod. The force delete should be the last option and great care should be taken that the node that had the deleted pod does not come back online, because there will now be two pods with the same name in the cluster.</li>
 	<li>Even after force deleting a pod, it might stay in an Unknown state, so a patch to the API server will delete the entry and cause the StatefulSet controller to create a new instance of the deleted pod</li>
 	<li>If you're running a complex data system with some type of leader election or data replication confirmation processes, use preStop hook to properly close any connections, force leader election, or verify data synchronization before the pod is deleted using a graceful shutdown process.</li>
 	<li>When the application that requires stateful data is a complex data management system, it might be worth a look to determine whether an Operator exists to help manage the more complicated life cycle components of the application. If the application is built in-house, it might be worth investigating whether it would be useful to package the application as an Operator to add additional manageability to the application. Look at the CoreOS Operator SDK for an example.</li>
</ul>
</li>
</ul>
<h2>Chapter 17: Admission Control and Authorization</h2>
<ul>
 	<li>The difference between validating and mutating admission controllers is that mutating can modify the request object they admit, whereas validating cannot.</li>
 	<li>Standard admission controllers are compiled into the API server and are shipped as plug-ins with each Kubernetes release; they need to be configured when the API server is started.</li>
 	<li>Dynamic controllers, on the other hand, are configurable at runtime and are developed outside the core Kubernetes codebase. The only type of dynamic admission control is admission webhooks, which receive admission requests via HTTP callbacks.</li>
 	<li>Many of the features that ship with Kubernetes depend on the enablement of specific standard admission controllers and, as such, there is a recommended set of defaults:</li>
 	<li>--enable-admission-plugins = NamespaceLifecycle, LimitRanger, ServiceAccount, DefaultStorageClass, DefaultTolerationSeconds, MutatingAdmissionWebhook, ValidatingAdmissionWebhook, Priority, ResourceQuota, PodSecurityPolicy</li>
 	<li>Admission Control Best Practices
<ul>
 	<li>Admission plug-in ordering doesn't matter. In earlier versions of Kubernetes, the ordering of the admission plug-ins was specific to the processing order; hence it mattered. In current supported Kubernetes versions, the ordering of the admission plug-ins as specified as API server flags via --enable-admission-plugins no longer matters. Ordering does, however, play a small role when it comes to admission webhooks, so it's important to understand the request flow in this case. Request admittance or rejection operates as a logical AND, meaning if any of the admission webhooks reject a request, the entire request is rejected and an error is sent back to the user. It's also important to note that mutating admission controllers are always run prior to running validating admission controllers.</li>
 	<li>Don't mutate the same fields. Configuring multiple mutating admission webhooks also presents challenges. There is no way to order the request flow through multiple mutating admission webhooks, so itâ€™s important to not have mutating admission controllers modify the same fields, because this can result in unexpected results. In the case where you have multiple mutating admission webhooks, we generally recommend configuring validating admission webhooks to confirm that the final resource manifest is what you expect post-mutation because it's guaranteed to be run following mutating webhooks.</li>
 	<li>Fail open/fail closed. You might recall seeing the failurePolicy field as part of both the mutating and validating webhook configuration resources. This field defines how the API server should proceed in the case where the admission webhooks have access issues or encounter unrecognized errors. You can set this field to either Ignore or Fail. Ignore essentially fails to open, meaning that processing of the request will continue, whereas Fail denies the entire request. This might seem obvious, but the implications in both cases require consideration. Ignoring a critical admission webhook could result in policy that the business relies on not being applied to a resource without the user knowing.</li>
 	<li>One potential solution to protect against this would be to raise an alert when the API server logs that it cannot reach a given admission webhook. Fail can be even more devastating by denying all requests if the admission webhook is experiencing issues. To protect against this you can scope the rules to ensure that only specific resource requests are set to the admission webhook. As a tenet, you should never have any rules that apply to all resources in the cluster.</li>
 	<li>If you have written your own admission webhook, it's important to remember that user/system requests can be directly affected by the time it takes for your admission webhook to make a decision and respond. All admission webhook calls are configured with a 30-second timeout, after which time the failurePolicy takes effect. Even if it takes several seconds for your admission webhook to make an admit/deny decision, it can severely affect user experience when working with the cluster. Avoid having complex logic or relying on external systems such as databases in order to process the admit/deny logic.</li>
 	<li>Scoping admission webhooks. There is an optional field that allows you to scope the namespaces in which the admission webhooks operate on via the NamespaceSelector field. This field defaults to empty, which matches everything, but can be used to match namespace labels via the use of the matchLabels field. We recommend that you always use this field because it allows for an explicit opt-in per namespace.</li>
 	<li>The kube-system namespace is a reserved namespace that's common across all Kubernetes clusters. It's where all system-level services operate. We recommend never running admission webhooks against the resources in this namespace specifically, and you can achieve this by using the NamespaceSelector field and simply not matching the kube-system namespace. You should also consider it on any system-level namespaces that are required for cluster operation.</li>
 	<li>Lock down admission webhook configurations with RBAC.</li>
 	<li>Don't send sensitive data. Admission webhooks are essentially black boxes that accept AdmissionRequests and output AdmissionResponses. How they store and manipulate the request is opaque to the user. It's important to think about what request payloads you are sending to the admission webhook.</li>
</ul>
</li>
 	<li>In Kubernetes, the authorization of each request is performed after authentication but before admission.</li>
 	<li>Unlike admission controllers, if a single authorization module admits the request, the request can proceed. Only for the case in which all modules deny the request will an error be returned to the user.</li>
 	<li>Consider the following best practices before making changes to the authorization modules configured on your cluster:
<ul>
 	<li>Given that the ABAC policies need to be placed on the filesystem of each master node and kept synchronized, we generally recommend against using ABAC in multimaster clusters. The same can be said for the webhook module because the configuration is based on a file and a corresponding flag being present. Furthermore, changes to these policies in the files require a restart of the API server to take effect, which is effectively a control-plane outage in a single master cluster or inconsistent configuration in a multimaster cluster. Given these details, we recommend using only the RBAC module for user authorization because the rules are configured and stored in Kubernetes itself.</li>
 	<li>Webhook modules, although powerful, are potentially very dangerous. Given that every request is subject to the authorization process, a failure of a webhook service would be devastating for a cluster. Therefore, we generally recommend not using external authorization modules unless you completely vet and are comfortable with your cluster failure modes if the webhook service becomes unreachable or unavailable.</li>
</ul>
</li>
</ul>
<h2>Chapter 18: Conclusion</h2>
<ul>
 	<li>Understanding how the APIs and components of Kubernetes work is critical to successfully unlocking the power of Kubernetes to make your application development, management, and deployment easier and more reliable.</li>
 	<li>Likewise, understanding how to link Kubernetes up with a wide variety of external systems and practices as varied as an on-on-premises database and a Continuous Delivery system is critical to efficiently making use of Kubernetes in the real world.</li>
</ul>
