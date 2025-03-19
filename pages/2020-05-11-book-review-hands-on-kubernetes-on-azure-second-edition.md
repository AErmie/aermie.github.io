---
layout: page
title: Book Review: Hands-On Kubernetes on Azure, Second Edition
date: 2020-05-11 11:41
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/05/HandsOnKubernetesOnAzure2ndEdition-Cover.png"><img class="alignleft wp-image-33295 size-medium" src="/wp-content/uploads/2020/05/HandsOnKubernetesOnAzure2ndEdition-Cover-244x300.png" alt="" width="244" height="300" /></a>Recently, I finished reading <a href="https://azure.microsoft.com/en-us/resources/get-started-with-kubernetes-on-azure/" target="_blank" rel="noopener noreferrer">Hands-On Kubernetes on Azure, Second Edition</a> by Nills Franssens, Shivakumar Gopalakrishnan, and Gunther Lenz.

I've recently been ramping up on Kubernetes, so, I had some knowledge (but not a lot) with Kubernetes when I read this book.

I particularly found<span style="color: #000000;"> the whole book helpful but in particular Chapter 5 ("<strong>Handling common failures in AKS</strong>"), Chapter 7 ("<strong>Monitoring the AKS cluster and the application</strong>"), and Chapter 10 ("<strong>Securing your AKS cluster</strong>").</span>

Even though I don't have a lot of highlights to share, I really liked this book. I found it most useful because it provides progressive hands-on experience with Kubernetes. My challenge, being an IT Pro, has always been the fact that I don't have the skills to create an app, just to use it as an example/reference for something else I was doing.

This book provides several example applications (in container form, obviously) so that you have pods/services/etc. deployed to work through the concepts in the book.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 1: Introduction to Docker and Kubernetes</h2>
<ul>
 	<li>When a Pod contains multiple containers, these containers share the same filesystem, and the same network namespace. This means that when a container that is part
of a Pod writes a file, other containers in that same Pod can read that file. This also means that all containers in a Pod can communicate with each other using localhost
networking.</li>
 	<li>You should only put containers that need to be tightly integrated in the same pod.</li>
 	<li>The purpose of a ReplicaSet is to maintain a stable set of Pods running at any given time. If you perform updates to your Deployment, Kubernetes will create a new ReplicaSet that will contain the updated Pods.</li>
 	<li>A Service in Kubernetes is a network-level abstraction. This allows you to expose the multiple Pods you have in your Deployment under a single IP address and a single DNS name.</li>
 	<li>The master nodes contain the Kubernetes API and a database that contains the cluster state. The worker nodes are the VMs that run your actual workload.</li>
</ul>
<h2>Chapter 2: Kubernetes on Azure (AKS)</h2>
<ul>
 	<li>None</li>
</ul>
<h2>Chapter 3: Application deployment on AKS</h2>
<ul>
 	<li>Setting requests and limits is best practice in Kubernetes</li>
 	<li>A ConfigMap is a portable way of configuring containers without having specialized images for each configuration</li>
 	<li>A ConfigMap is used for non-secret configuration</li>
 	<li>Due to the ephemeral nature of containers, you should never connect to a container to do additional configuration or installation. This should either be part of your container image or configuration you provide via Kubernetes</li>
 	<li>Virtual machines behind a basic load balancer can make outbound connections without any specific configuration. Virtual machines behind a standard load balancer (which is the default for AKS now) need a specific configuration to make outbound connections.</li>
 	<li>You can think of Helm Charts as parameterized Kubernetes YAML file</li>
 	<li>Helm charts allow you to write YAML files with certain parameters in them, which you can dynamically set. This setting of the parameters can be done through a values file or as a command-line variable when you deploy the chart.</li>
 	<li>To make Kubernetes handle stateful workloads, it has a specific object called a StatefulSet.</li>
 	<li>A StatefulSet (https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/) is like a deployment with the additional capability of ordering, and the uniqueness of the Pods. This means that Kubernetes will ensure that the Pod and its storage are kept together. Another way that StatefulSets help is with the consistent naming of Pods in a StatefulSet. The Pods are named &lt;pod-name&gt;-#, where # starts from 0 for the first Pod, and 1 for the second Pod.</li>
 	<li>When a deployment pod is deleted, Kubernetes will launch it again anywhere it can, whereas when a StatefulSet pod is deleted, Kubernetes will relaunch it only on the node it was running on. It will relocate the pod only if the node is removed from the Kubernetes cluster.</li>
</ul>
<h2>Chapter 4: Building scalable applications</h2>
<ul>
 	<li>You can even scale it down to zero (one of the tricks used to reload the configuration when the application doesn't support the dynamic reload of configuration</li>
 	<li>To make automated changes, you can use the kubectl patch command.</li>
 	<li>There are two main ways in which to use kubectl patch, either by creating a file containing your changes (called a patch file) or by providing the changes inline</li>
 	<li>The main thing about a patch file is that it only has to contain the changes and doesn't have to be capable of deploying the whole resource.</li>
</ul>
<h2>Chapter 5: Handling common failures in AKS</h2>
<ul>
 	<li>There is a configuration in Kubernetes called pod-eviction-timeout that define how long the system will wait to reschedule Pods on a healthy host</li>
 	<li>Kubernetes uses requests to calculate how much CPU power or memory a certain Pod requires</li>
 	<li>Note: In Kubernetes, you can use either the binary prefix notation or the base 10 notation to specify memory and storage. Binary prefix notation means using KiB (kibibyte) to represent 1,024 bytes, MiB (mebibyte) to represent 1,024 KiB, and Gib (gibibyte) to represent 1,024 MiB. Base 10 notation means using kB (kilobyte) to represent 1,000 bytes, MB (megabyte) to represent 1,000 kB, and GB (gigabyte) represents 1,000 MB.</li>
 	<li>Kubernetes (versions 1.5 or newer) will not delete Pods just because a Node is unreachable. The Pods running on an unreachable Node enter the Terminating or Unknown state after a timeout. Pods may also enter these states when the user attempts the graceful deletion of a Pod on an unreachable Node</li>
</ul>
<h2>Chapter 6: Securing your application with HTTPS and Azure AD</h2>
<ul>
 	<li>A CRD is a way to extend the Kubernetes API server to create custom resources, like a certificate issuer.</li>
 	<li>Annotations are used by multiple Ingress providers to pass detailed configuration data to the Ingress provider in the back end.</li>
</ul>
<h2>Chapter 7: Monitoring the AKS cluster and the application</h2>
<ul>
 	<li>When monitoring an application running on top of a Kubernetes cluster, you'll need to examine multiple things in parallel, including containers, Pods, Services, and the nodes in the cluster</li>
 	<li>The nominated node is the node where that higher-priority Pod will start once the lower-priority Pods gracefully terminate. A readiness gate is a way to introduce external system components as the readiness for a Pod.</li>
 	<li>Note: Kubernetes maintains events for only 1 hour by default.</li>
 	<li>Note: You can either use a slash or a space in between pod and podname.
The following two commands will have the same output:
kubectl describe pod/&lt;pod-name&gt;
kubectl describe pod &lt;pod-name&gt;</li>
 	<li>The node section lets us know which physical node/VM the Pod is running on. If the Pod is repeatedly restarting or having issues running and everything else seems OK, there might be an issue with the node. Having this information is essential to perform advanced debugging.</li>
 	<li>This is how connections such as Service | Deployment | ReplicaSet | Pod are made. If you see that traffic is not being routed to a Pod from a Service, this is the first thing you should check. If the labels don't match, the resources won't attach.</li>
 	<li>If you were to have two Pods running a web server on the same node, those could both use port 80, since each Pod has its own IP address. This is a huge management advantage as you don't have to worry about port collisions. The port that needs to be configured is also fixed so that scripts can be written simply without the
logic of figuring out which port actually got allocated for the Pod.</li>
 	<li>Note: Most errors come from misconfiguration, where they can be fixed by editing the specification. Errors in the application code itself require a new image to be built and used.</li>
 	<li>The following points summarize some of the common errors and methods to fix these errors:
<ul>
 	<li>Errors can come in many shapes and forms.</li>
 	<li>Most of the errors encountered by the deployment team are configuration issues.</li>
 	<li>Logs are your friends.</li>
 	<li>Using kubectl exec on a container is a useful debugging tool.</li>
 	<li>Note that broadly allowing kubectl exec is a serious security risk, as it pretty much lets the Kubernetes operator do what they want in the Pods they have access to.</li>
 	<li>Anything printed to stdout and stderr shows up in the logs (independent of the application/language/logging framework).</li>
</ul>
</li>
 	<li>Kubernetes uses liveness and readiness probes to monitor the availability of your
applications. Each probe serves a different purpose:
<ul>
 	<li>A liveness probe monitors the availability of an application while it is running. If a liveness probe fails, Kubernetes will restart your Pod. This could be useful to catch deadlocks, infinite loops, or just a "stuck" application.</li>
 	<li>A readiness probe monitors when your application becomes available. If a readiness probe fails, Kubernetes will not send any traffic to unready Pods. This is useful if your application has to go through some configuration before it becomes available, or if your application could become overloaded but recover from the additional load.</li>
</ul>
</li>
 	<li>A readiness probe can be used to temporarily stop traffic to your Pod, so it has to suffer less load. A liveness probe is used to restart your Pod if there is an actual failure in your Pod.</li>
 	<li>Requests and limits are used to perform capacity management in a cluster.</li>
 	<li>To collect the relevant metrics and logs into Insights, Azure connects to the Kubernetes API to collect the metrics and then stores them in Azure Monitor.</li>
 	<li>Note: Logs of a container could contain sensitive information. Therefore, the rights to review logs should be controlled and audited.</li>
</ul>
<h2>Chapter 8: Connecting an app to an Azure database</h2>
<ul>
 	<li>OSBA is an implementation of OSB for multiple Azure services. It allows a user to use the OSB API to create any of 14 supported Azure services</li>
 	<li>It is typically recommended to turn on audit logging to verify who has accessed your database and to turn on slow query monitoring to track any queries that are running slowly</li>
</ul>
<h2>Chapter 9: Connecting to Azure Event Hubs</h2>
<ul>
 	<li>A graph database is a database that is focused on storing the relationship between different elements. You can query a graph database with questions, such as give me the common friends of user X and user Y.</li>
</ul>
<h2>Chapter 10: Securing your AKS cluster</h2>
<ul>
 	<li>The benefits of establishing RBAC are that it not only acts as a guardrail against the accidental deletion of critical resources but also that it is an important security feature that limits full access to the cluster to roles that really need it.</li>
 	<li>Anywhere between 22% and 29% (<a href="https://blog.storagecraft.com/data-loss-statistics-infographic/" target="_blank" rel="noopener noreferrer">https://blog.storagecraft.com/data-loss-statistics-infographic/</a>) of data loss is attributed to human error. You don't want to be part of that statistic.</li>
 	<li>A role contains a set of permissions. A role has a default of no permissions, and every permission needs to be specifically called out. The role also contains which resources these permissions are given to.</li>
 	<li>The subject is either a person or a service account that is assigned a role. In AKS, these subjects can be Azure AD users or groups.</li>
 	<li>A RoleBinding links a subject to a role in a certain namespace or, in the case of a ClusterRoleBinding, the whole cluster.</li>
 	<li>An important notion to understand is that when interfacing with AKS, there are two layers of RBAC: Azure RBAC and Kubernetes RBAC. Azure RBAC deals with the roles given to people to make changes in Azure, such as creating, modifying, and deleting clusters. Kubernetes RBAC deals with the access rights to resources in a cluster. Both are independent control planes but can use the same users and groups originating in Azure AD.</li>
 	<li>RBAC in Kubernetes is an optional feature. The default in AKS is to create clusters that
have RBAC enabled. However, by default, the cluster is not integrated with Azure AD.
This means that by default you cannot grant Kubernetes permissions to Azure AD users.</li>
 	<li>Our secret is of the Opaque type, which means that, from Kubernetes' perspective, the schema of the contents is unknown. It is an arbitrary key-value pair with no constraints, as opposed to Docker registry or TLS secrets, which have a schema that will be verified as having the required details.</li>
 	<li>Base64 encoding isn't secure. It scrambles the secret so it isn't easily readable by an operator, but any bad actor can easily decode a base64-encoded secret.</li>
 	<li>In Azure, Azure Container Registry (ACR) is most frequently used to store container images. There are two ways in which the cluster can connect to ACR. The first way is using a secret in the cluster like we just described. The second way – which is the recommended way – is to use a service principal.</li>
 	<li>Mounting secrets as files is the best way to consume secrets in your application.</li>
 	<li>Note that this is more succinct than the env definition, as you don't have to define a name for each and every secret. However, applications need to have a special code to read the contents of the file in order to load it properly.</li>
 	<li>Although it is a common practice to use secrets as environment variables, it is more secure to mount secrets as files. Kubernetes treats secrets as environment variables securely, but the Docker runtime doesn't treat them securely.</li>
 	<li>Note: RBAC is also very important for controlling secrets. A person who has access to the cluster and has the right role has access to the secrets that are stored. As secrets are only base64-encoded, anybody with RBAC permissions to the secrets can decode them. It is recommended to treat access to secrets carefully and be very careful about giving people access to use the kubectl exec command to get a shell to containers.</li>
 	<li>Note: Key Vault FlexVolume supports a number of authentication options. We are now using a pre-created service principal. FlexVolume also supports the use of Virtual managed identities, either using a Pod identity or using the identity of the Machine Scale Set (VMSS) (hosting the cluster. These other authentication options will not be explored in this book, but you are encouraged to read more at <a href="https://github.com/Azure/kubernetes-keyvault-flexvol" target="_blank" rel="noopener noreferrer">https://github.com/Azure/kubernetes-keyvault-flexvol</a>)</li>
 	<li>A service mesh is a network between microservices. A service mesh is implemented as a piece of software that controls and monitors traffic between those different microservices. Typically, a service mesh makes use of a sidecar to implement functionality transparently.</li>
 	<li>Note: A service mesh controls much more than simply network security. If all you require is network security in your cluster, please consider adopting network policies.</li>
 	<li>Istio is the control plane portion of the service mesh. Istio by default makes use of the Envoy sidecar.</li>
 	<li>By implementing a service mesh, you can control traffic in order to implement A/B testing or canary rollouts. Without a service mesh, you would need to implement that logic in your application's core code, whereas with a service mesh, that logic is implemented outside of the application.</li>
 	<li>Policies can be used to either rate limit certain traffic (for example, only allow x transactions a minute), handle the whitelisting and blacklisting of access to services, or implement header rewrites and redirects.</li>
 	<li>Out of the box, Istio can perform traffic tracing, monitoring, and logging of the traffic between your services. You can use this information to create dashboards to demonstrate application performance and use this information to more effectively debug application failures.</li>
 	<li>Note: If you want more information on the end-to-end security framework within Istio, please read <a href="https://istio.io/docs/concepts/security/#authentication-policies" target="_blank" rel="noopener noreferrer">https://istio.io/docs/concepts/security/#authentication-policies</a>.
For more details on mutual TLS, please read <a href="https://istio.io/docs/concepts/security/#mutual-tls-authentication" target="_blank" rel="noopener noreferrer">https://istio.io/docs/concepts/security/#mutual-tls-authentication</a>.</li>
 	<li>Note: We are applying the mTLS very coarsely and aggressively. Typically, in a production system, you will introduce mTLS more slowly. Istio has a special mTLS enforcement mode called permissive to help achieve this. With mTLS in the permissive mode, Istio will try to implement mTLS where possible and log a warning where it is not possible. However, the traffic will continue to flow.</li>
</ul>
<h2>Chapter 11: Serverless functions</h2>
<ul>
 	<li>Microsoft operates Azure Functions as a managed service on Azure and has open-sourced the complete solution and made it available to run on any system (<a href="https://github.com/Azure/azure-functions-host" target="_blank" rel="noopener noreferrer">https://github.com/Azure/azure-functions-host</a>). This also makes the Azure Functions programming model available on top of Kubernetes.</li>
 	<li>KEDA is a custom autoscaler that can allow Deployments to scale to and from 0 Pods.</li>
 	<li>Scaling to and from 0 Pods is not possible using the default Horizontal Pod Autoscaler (HPA) in Kubernetes.</li>
 	<li>KEDA also makes additional metrics available to the Kubernetes HPA to make scaling decisions based on metrics from outside the cluster (for example, the number of messages in a queue).</li>
 	<li>Note: For production use cases, it is not recommended to connect to Azure storage using the access key. Any user with that access key has full access to the storage account and can read and delete all files on it. It is recommended to either generate a shared access signatures (SAS) token to connect to storage or to use Azure AD-integrated security. To learn more about SAS token authentication to storage, refer to <a href="https://docs.microsoft.com/en-ca/rest/api/storageservices/delegate-access-with-shared-access-signature" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/rest/api/storageservices/delegate-access-with- shared-access-signature</a>. To learn more about Azure AD authentication to Azure storage, please refer to <a href="https://docs.microsoft.com/rest/api/storageservices/authorize-with-azure-active-directory" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/rest/api/storageservices/authorize-with-azure-active-directory</a>.</li>
</ul>
