---
layout: page
title: Book Review: Kubernetes Up and Running
date: 2019-11-29 10:16
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2019/11/KubernetesUpAndRunning-BookCover.jpg"><img class="alignleft size-medium wp-image-33043" src="/wp-content/uploads/2019/11/KubernetesUpAndRunning-BookCover-229x300.jpg" alt="" width="229" height="300" /></a>Recently, I finished reading <a href="https://www.amazon.ca/Kubernetes-Running-Dive-Future-Infrastructure/dp/1492046531/ref=sr_1_1?keywords=Kubernetes%3A+Up+and+Running&amp;qid=1574032595&amp;sr=8-1" target="_blank" rel="noopener noreferrer">Kubernetes: Up and Running, 2nd Edition</a> by Kelsey Hightower, Joe Beda, Brendan Burns.

When I started reading this book, I had very little knowledge or experience with Kubernetes. And so, I was looking for a book that would provide a good foundation.

I particularly found<span style="color: #000000;"> Chapter 5 (“<strong>Pods</strong>”), Chapter 9 (“<strong>ReplicaSets</strong>"), Chapter 10 (“<strong>Deployments</strong>”), and Chapter 11 ("<strong>DaemonSets</strong>")</span> of great value.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

&nbsp;
<h2>Chapter 1: Introduction</h2>
<ul>
 	<li>None</li>
</ul>
<h2>Chapter 2: Creating and Running Containers</h2>
<ul>
 	<li>There are several gotchas that come when people begin to experiment with container images that lead to overly large images. The first thing to remember is that files that are removed by subsequent layers in the system are actually still present in the images; they're just inaccessible.</li>
 	<li>Another pitfall that people fall into revolves around image caching and building. Remember that each layer is an independent delta from the layer below it. Every time you change a layer, it changes every layer that comes after it. Changing the preceding layers means that they need to be rebuilt, repushed, and repulled to deploy your image to development.</li>
 	<li>In general, you want to order your layers from least likely to change to most likely to change in order to optimize the image size for pushing and pulling</li>
 	<li>Don't build containers with passwords baked in, and this includes not just in the final layer, but any layers in the image</li>
 	<li>One of the counterintuitive problems introduced by container layers is that deleting a file in one layer doesn't delete that file from preceding layers. It still takes up space, and it can be accessed by anyone with the right tools; an enterprising attacker can simply create an image that only consists of the layers that contain the password.</li>
 	<li>Secrets and images should never be mixed. If you do so, you will be hacked, and you will bring shame to your entire company or department. We all want to be on TV someday, but there are better ways to go about that</li>
 	<li>Compiling code as part of the image build feels natural, and it is the easiest way to build a container image from your program. The trouble with doing this is that it leaves all of the unnecessary development tools, which are usually quite large, lying around inside of your image and slowing down your deployments.</li>
 	<li>The process of manually importing and exporting Docker images has human error written all over it. Just say no!</li>
 	<li>One of the key benefits to running applications within a container is the ability to restrict resource utilization. This allows multiple applications to coexist on the same hardware and ensures fair usage</li>
 	<li>It's important to note that unless you explicitly delete an image it will live on your system forever, even if you build a new image with an identical name. Building this new image simply moves the tag to the new image; it doesnâ€™t delete or replace the old image.</li>
 	<li>Docker provides a tool called docker system prune for doing general cleanup. This will remove all stopped containers, all untagged images, and all unused image layers cached as part of the build process. Use it carefully.</li>
</ul>
<h2>Chapter 3: Deploying a Kubernetes Cluster</h2>
<ul>
 	<li>The Kubernetes tools are backward- and forward-compatible with different versions of the Kubernetes API, so long as you stay within two minor versions for both the tools and the cluster and don't try to use newer features on an older cluster.</li>
 	<li>In Kubernetes, nodes are separated into master nodes that contain containers like the API server, scheduler, etc., which manage the cluster, and worker nodes where your containers will run.</li>
 	<li>Kubernetes won't generally schedule work onto master nodes to ensure that user workloads don't harm the overall operation of the cluster.</li>
 	<li>It's worth noting here that Kubernetes tracks both the requests and upper limits for resources for each Pod that runs on a machine</li>
 	<li>Resources requested by a Pod are guaranteed to be present on the node, while a Pod's limit is the maximum amount of a given resource that a Pod can consume. A Pod's limit can be higher than its request, in which case the extra resources are supplied on a best-effort basis. They are not guaranteed to be present on the node.</li>
 	<li>One of the interesting aspects of Kubernetes is that many of the components that make up the Kubernetes cluster are actually deployed using Kubernetes itself</li>
 	<li>The Kubernetes proxy is responsible for routing network traffic to load-balanced services in the Kubernetes cluster the proxy must be present on every node in the cluster</li>
 	<li>Kubernetes also runs a DNS server, which provides naming and discovery for the services that are defined in the cluster. This DNS server also runs as a replicated service on the cluster. Depending on the size of your cluster, you may see one or more DNS servers running in your cluster</li>
 	<li>There is also a Kubernetes service that performs load balancing for the DNS server</li>
 	<li>The UI is run as a single replica, but it is still managed by a Kubernetes deployment for reliability and upgrades.</li>
 	<li>The dashboard also has a service that performs load balancing for the dashboard</li>
</ul>
<h2>Chapter 4: Common kubectl Commands</h2>
<ul>
 	<li>Kubernetes uses namespaces to organize objects in the cluster. You can think of each namespace as a folder that holds a set of objects.</li>
 	<li>Everything contained in Kubernetes is represented by a RESTful resource.</li>
 	<li>Each Kubernetes object exists at a unique HTTP path</li>
 	<li>By default, kubectl uses a human-readable printer for viewing the responses from the API server, but this human-readable printer removes many of the details of the objects to fit each object on one terminal line</li>
 	<li>One way to get slightly more information is to add the -o wide flag, which gives more details, on a longer line. If you want to view the complete object, you can also view the objects as raw JSON or YAML using the -o json or -o yaml flags, respectively.</li>
 	<li>If you are interested in more detailed information about a particular object, use the describe command</li>
 	<li>Another common task is extracting specific fields from the object. kubectl uses the JSONPath query language to select fields in the returned object</li>
 	<li>The apply tool will only modify objects that are different from the current objects in the cluster. If the objects you are creating already exist in the cluster, it will simply exit successfully without making any changes. This makes it useful for loops where you want to ensure the state of the cluster matches the state of the filesystem. You can repeatedly use apply to reconcile state.</li>
 	<li>If you want to see what the apply command will do without actually making the changes, you can use the --dry-run flag to print the objects to the terminal without actually sending them to the server.</li>
 	<li>The apply command also records the history of previous configurations in an annotation within the object. You can manipulate these records with the edit-last-applied, set-last-applied, and view-last-applied commands</li>
 	<li>It is important to note that kubectl will not prompt you to confirm the deletion. Once you issue the command, the object will be deleted</li>
 	<li>Labels and annotations are tags for your objects.</li>
 	<li>By default, label and annotate will not let you overwrite an existing label. To do this, you need to add the --overwrite flag</li>
 	<li>By default, kubectl logs lists the current logs and exits. If you instead want to continuously stream the logs back to the terminal without exiting, you can add the -f (follow) command-line flag</li>
 	<li>If you want to access your Pod via the network, you can use the port-forward command to forward network traffic from the local machine to the Pod</li>
 	<li>This enables you to securely tunnel network traffic through to containers that might not be exposed anywhere on the public network</li>
</ul>
<h2>Chapter 5: Pods</h2>
<ul>
 	<li>In real-world deployments of containerized applications you will often want to colocate multiple applications into a single atomic unit, scheduled onto a single machine</li>
 	<li>Kubernetes groups multiple containers into a single atomic unit called a Pod. (The name goes with the whale theme of Docker containers, since a Pod is also a group of whales.)</li>
 	<li>A Pod represents a collection of application containers and volumes running in the same execution environment. Pods, not containers, are the smallest deployable artifact in a Kubernetes cluster. This means all of the containers in a Pod always land on the same machine</li>
 	<li>Each container within a Pod runs in its own cgroup, but they share a number of Linux namespaces</li>
 	<li>Applications running in the same Pod share the same IP address and port space (network namespace), have the same hostname (UTS namespace), and can communicate using native interprocess communication channels over System V IPC or POSIX message queues (IPC namespace)</li>
 	<li>Applications in different Pods are isolated from each other; they have different IP addresses, different hostnames, and more. Containers in different Pods running on the same node might as well be on different servers.</li>
 	<li>In general, the right question to ask yourself when designing Pods is, "Will these containers work correctly if they land on different machines?" If the answer is "no," a Pod is the correct grouping for the containers. If the answer is "yes," multiple Pods is probably the correct solution</li>
 	<li>The Kubernetes API server accepts and processes Pod manifests before storing them in persistent storage (etcd)</li>
 	<li>Scheduling multiple replicas of the same application onto the same machine is worse for reliability, since the machine is a single failure domain. Consequently, the Kubernetes scheduler tries to ensure that Pods from the same application are distributed onto different machines for reliability in the presence of such failures. Once scheduled to a node, Pods don't move and must be explicitly destroyed and rescheduled.</li>
 	<li>Pod manifests can be written using YAML or JSON, but YAML is generally preferred because it is slightly more human-editable and has the ability to add comments</li>
 	<li>All Pods have a termination grace period. By default, this is 30 seconds. When a Pod is transitioned to Terminating it no longer receives new requests. In a serving scenario, the grace period is important for reliability because it allows the Pod to finish any active requests that it may be in the middle of processing before it is terminated.</li>
 	<li>When your application needs debugging, it's helpful to be able to dig deeper than describe to understand what the application is doing. Kubernetes provides two commands for debugging running containers</li>
 	<li>The kubectl logs command downloads the current logs from the running instance</li>
 	<li>Adding the -f flag will cause you to continuously stream logs</li>
 	<li>The kubectl logs command always tries to get logs from the currently running container. Adding the --previous flag will get logs from a previous instance of the container. This is useful, for example, if your containers are continuously restarting due to a problem at container startup</li>
 	<li>Generally speaking, copying files into a container is an anti-pattern. You really should treat the contents of a container as immutable.</li>
 	<li>Liveness health checks run application-specific logic (e.g., loading a web page) to verify that the application is not just still running, but is functioning properly. Since these liveness health checks are application-specific, you have to define them in your Pod manifest</li>
 	<li>Liveness probes are defined per container, which means each container inside a Pod is health-checked separately</li>
 	<li>While the default response to a failed liveness check is to restart the Pod, the actual behavior is governed by the Pod's restartPolicy. There are three options for the restart policy: Always (the default), OnFailure (restart only on liveness failure or nonzero process exit code), or Never</li>
 	<li>Liveness determines if an application is running properly. Containers that fail liveness checks are restarted.</li>
 	<li>Readiness describes when a container is ready to serve user requests. Containers that fail readiness checks are removed from service load balancers</li>
 	<li>In addition to HTTP checks, Kubernetes also supports tcpSocket health checks that open a TCP socket; if the connection is successful, the probe succeeds. This style of probe is useful for non-HTTP applications; for example, databases or other non HTTP-based APIs.</li>
 	<li>Kubernetes allows exec probes. These execute a script or program in the context of the container. Following typical convention, if this script returns a zero exit code, the probe succeeds; otherwise, it fails. exec scripts are often useful for custom application validation logic that doesn't fit neatly into an HTTP call.</li>
 	<li>Utilization is defined as the amount of a resource actively being used divided by the amount of a resource that has been purchased</li>
 	<li>Kubernetes allows users to specify two different resource metrics. Resource requests specify the minimum amount of a resource required to run the application. Resource limits specify the maximum amount of a resource that an application can consume</li>
 	<li>The most commonly requested resources are CPU and memory, but Kubernetes has support for other resource types as well, such as GPUs and more</li>
 	<li>Resources are requested per container, not per Pod. The total resources requested by the Pod is the sum of all resources requested by all containers in the Pod.</li>
 	<li>Importantly, "request" specifies a minimum. It does not specify a maximum cap on the resources a Pod may use
<ul>
 	<li>CPU requests are implemented using the cpu-shares functionality in the Linux kernel</li>
 	<li>Memory requests are handled similarly to CPU, but there is an important difference. If a container is over its memory request, the OS can't just remove memory from the process, because it's been allocated. Consequently, when the system runs out of memory, the kubelet terminates containers whose memory usage is greater than their requested memory. These containers are automatically restarted, but with less available memory on the machine for the container to consume</li>
</ul>
</li>
 	<li>When you establish limits on a container, the kernel is configured to ensure that consumption cannot exceed these limits</li>
 	<li>It's important to note that not all containers are required to mount all volumes defined in the Pod.</li>
 	<li>Note that two different containers in a Pod can mount the same volume at different mount paths</li>
 	<li>Kubernetes supports a wide variety of remote network storage volumes, including widely supported protocols like NFS and iSCSI as well as cloud provider network storage like Amazon's Elastic Block Store, Azure's Files and Disk Storage, as well as Google's Persistent Disk.</li>
 	<li>Kubernetes supports the hostPath volume, which can mount arbitrary locations on the worker node into the container.</li>
 	<li>When using network-based storage, Kubernetes automatically mounts and unmounts the appropriate storage whenever a Pod using that volume is scheduled onto a particular machine.</li>
 	<li>Through a combination of persistent volumes, readiness and liveness probes, and resource restrictions, Kubernetes provides everything needed to run stateful applications reliably</li>
 	<li>Pods represent the atomic unit of work in a Kubernetes cluster. Pods are comprised of one or more containers working together symbiotically</li>
 	<li>Once a Pod is scheduled to a node, no rescheduling occurs if that node fails. Additionally, to create multiple replicas of the same Pod you have to create and name them manually</li>
</ul>
<h2>Chapter 6: Labels and Annotations</h2>
<ul>
 	<li>Labels and annotations let you work in sets of things that map to how you think about your application</li>
 	<li>Labels are key/value pairs that can be attached to Kubernetes objects such as Pods and ReplicaSets. They can be arbitrary, and are useful for attaching identifying information to Kubernetes objects. Labels provide the foundation for grouping objects</li>
 	<li>Annotations, on the other hand, provide a storage mechanism that resembles labels: annotations are key/value pairs designed to hold nonidentifying information that can be leveraged by tools and libraries</li>
 	<li>Labels provide identifying metadata for objects. These are fundamental qualities of the object that will be used for grouping, viewing, and operating</li>
 	<li>Label values are strings with a maximum length of 63 characters. The contents of the label values follow the same rules as for label keys</li>
 	<li>Label keys can be broken down into two parts: an optional prefix and a name, separated by a slash. The prefix, if specified, must be a DNS subdomain with a 253-character limit. The key name is required and must be shorter than 63 characters. Names must also start and end with an alphanumeric character and permit the use of dashes (-), underscores (_), and dots (.) between characters.</li>
 	<li>Labels can also be applied (or updated) on objects after they are created</li>
 	<li>You can remove a label by applying a dash suffix</li>
 	<li>If we specify two selectors separated by a comma, only the objects that satisfy both will be returned. This is a logical AND operation</li>
 	<li>In addition to enabling users to organize their infrastructure, labels play a critical role in linking various related Kubernetes objects.</li>
 	<li>Labels are a powerful and ubiquitous glue that holds a Kubernetes application together.</li>
 	<li>Annotations provide a place to store additional metadata for Kubernetes objects with the sole purpose of assisting tools and libraries.</li>
 	<li>Annotations can be used for the tool itself or to pass configuration information between external systems.</li>
 	<li>While labels are used to identify and group objects, annotations are used to provide extra information about where an object came from, how to use it, or policy around that object</li>
 	<li>During rolling deployments, annotations are used to track rollout status and provide the necessary information required to roll back a deployment to a previous state.</li>
 	<li>The value component of an annotation is a free-form string field. While this allows maximum flexibility as users can store arbitrary data, because this is arbitrary text, there is no validation of any format</li>
</ul>
<h2>Chapter 7: Service Discovery</h2>
<ul>
 	<li>Service-discovery tools help solve the problem of finding which processes are listening at which addresses for which services</li>
 	<li>Kubernetes provides a DNS service exposed to Pods running in the cluster. This Kubernetes DNS service was installed as a system component when the cluster was first created.</li>
 	<li>One nice thing the Service object does is track which of your Pods are ready via a readiness check</li>
 	<li>If you have support from the cloud that you are running on (and your cluster is configured to take advantage of it), you can use the LoadBalancer type. This builds on the NodePort type by additionally configuring the cloud to create a new load balancer and direct it at nodes in your cluster.</li>
 	<li>For every Service object, Kubernetes creates a buddy Endpoints object that contains the IP addresses for that service</li>
 	<li>The kube-proxy watches for new services in the cluster via the API server. It then programs a set of iptables rules in the kernel of that host to rewrite the destinations of packets so they are directed at one of the endpoints for that service. If the set of endpoints for a service changes (due to Pods coming and going or due to a failed readiness check), the set of iptables rules is rewritten</li>
 	<li>The service address range should not overlap with the IP subnets and ranges assigned to each Docker bridge or Kubernetes node.</li>
</ul>
<h2>Chapter 8: HTTP Load Balancing with Ingress</h2>
<ul>
 	<li>There is no "standard" Ingress controller that is built into Kubernetes, so the user must install one of many optional implementations</li>
 	<li>If you have an IP address for your external load balancer, you'll want to create A records. If you have a hostname, you'll want to configure CNAME records.</li>
 	<li>Many of the extended features are exposed via annotations on the Ingress object. Be careful, as these annotations can be hard to validate and are easy to get wrong. Many of these annotations apply to the entire Ingress object and so can be more general than you might like.</li>
 	<li>Due to an abundance of security caution, an Ingress object can only refer to an upstream service in the same namespace. This means that you can't use an Ingress object to point a subpath to a service in another namespace.</li>
 	<li>This cross-namespace behavior means that it is necessary that Ingress be coordinated globally across the cluster. If not coordinated carefully, an Ingress object in one namespace could cause problems (and undefined behavior) in other namespaces.</li>
 	<li>It is probably best to avoid subpaths if you can help it for any complicated applications.</li>
</ul>
<h2>Chapter 9: ReplicaSets</h2>
<ul>
 	<li>A ReplicaSet acts as a cluster-wide Pod manager, ensuring that the right types and number of Pods are running at all times.</li>
 	<li>Pods managed by ReplicaSets are automatically rescheduled under certain failure conditions, such as node failures and network partitions.</li>
 	<li>When we define a ReplicaSet, we define a specification for the Pods we want to create (the "cookie cutter"), and a desired number of replicas</li>
 	<li>With a ReplicaSet, it is the desired number of replicas and the definition of the Pod to replicate.</li>
 	<li>The reconciliation loop is constantly running, observing the current state of the world and taking action to try to make the observed state match the desired state.</li>
 	<li>Note that the reconciliation loop for ReplicaSets is a single loop, yet it handles user actions to scale up or scale down the ReplicaSet as well as node failures or nodes rejoining the cluster after being absent.</li>
 	<li>Though ReplicaSets create and manage Pods, they do not own the Pods they create. ReplicaSets use label queries to identify the set of Pods they should be managing.</li>
 	<li>Because ReplicaSets are decoupled from the Pods they manage, you can simply create a ReplicaSet that will "adopt" the existing Pod, and scale out additional copies of those containers. In this way, you can seamlessly move from a single imperative Pod to a replicated set of Pods managed by a ReplicaSet.</li>
 	<li>ReplicaSets are designed to represent a single, scalable microservice inside your architecture. The key characteristic of ReplicaSets is that every Pod that is created by the ReplicaSet controller is entirely homogeneous.</li>
 	<li>Generally speaking, ReplicaSets are designed for stateless (or nearly stateless) services. The elements created by the ReplicaSet are interchangeable; when a ReplicaSet is scaled down, an arbitrary Pod is selected for deletion.</li>
 	<li>The Pods are created using a Pod template that is contained in the ReplicaSet specification. The Pods are created in exactly the same manner as when you created a Pod from a YAML file in previous chapters, but instead of using a file, the Kubernetes ReplicaSet controller creates and submits a Pod manifest based on the Pod template directly to the API server.</li>
 	<li>The labels used for filtering are defined in the ReplicaSet spec section and are the key to understanding how ReplicaSets work.</li>
 	<li>ReplicaSets monitor cluster state using a set of Pod labels. Labels are used to filter Pod listings and track Pods running within a cluster.</li>
 	<li>To enable this kind of discovery, the ReplicaSet controller adds an annotation to every Pod that it creates. The key for the annotation is kubernetes.io/created-by.</li>
 	<li>Note that such annotations are best-effort; they are only created when the Pod is created by the ReplicaSet, and can be removed by a Kubernetes user at any time.</li>
 	<li>HPA requires the presence of the heapster Pod on your cluster. heapster keeps track of metrics and provides an API for consuming metrics that HPA uses when making scaling decisions. Most installations of Kubernetes include heapster by default.</li>
 	<li>Kubernetes makes a distinction between horizontal scaling, which involves creating additional replicas of a Pod, and vertical scaling, which involves increasing the resources required for a particular Pod (e.g., increasing the CPU required for the Pod).</li>
 	<li>Because of the decoupled nature of Kubernetes, there is no direct link between the HPA and the ReplicaSet. While this is great for modularity and composition, it also enables some anti-patterns. In particular, it's a bad idea to combine both autoscaling and imperative or declarative management of the number of replicas. If both you and an autoscaler are attempting to modify the number of replicas, it's highly likely that you will clash, resulting in unexpected behavior.</li>
 	<li>If you don't want to delete the Pods that are being managed by the ReplicaSet, you can set the --cascade flag to false to ensure only the ReplicaSet object is deleted and not the Pods</li>
 	<li>ReplicaSets should be used for any Pod you care about, even if it is a single Pod! Some people even default to using ReplicaSets instead of Pods. A typical cluster will have many ReplicaSets, so apply liberally to the affected area.</li>
</ul>
<h2>Chapter 10: Deployments</h2>
<ul>
 	<li>Deployments represent deployed applications in a way that transcends any particular version. Additionally, deployments enable you to easily move from one version of your code to the next. This "rollout" process is specifiable and careful. It waits for a user-configurable amount of time between upgrading individual Pods. It also uses health checks to ensure that the new version of the application is operating correctly, and stops the deployment if too many failures occur.</li>
 	<li>If you ever want to manage that ReplicaSet directly, you need to delete the deployment (remember to set --cascade to false, or else it will delete the ReplicaSet and Pods as well!).</li>
 	<li>You also need to run kubectl replace --save-config. This adds an annotation so that, when applying changes in the future, kubectl will know what the last applied configuration was for smarter merging of configs. If you always use kubectl apply, this step is only required after the first time you create a deployment using kubectl create -f.</li>
 	<li>The strategy object dictates the different ways in which a rollout of new software can proceed. There are two different strategies supported by deployments: Recreate and RollingUpdate.</li>
 	<li>Two of the most important pieces of information in the output are OldReplicaSets and NewReplicaSet. These fields point to the ReplicaSet objects this deployment is currently managing. If a deployment is in the middle of a rollout, both fields will be set to a value. If a rollout is complete, OldReplicaSets will be set to &lt;none&gt;.</li>
 	<li>You can use kubectl rollout history to obtain the history of rollouts associated with a particular deployment. If you have a current deployment in progress, you can use kubectl rollout status to obtain the current status of a rollout.</li>
 	<li>The best practice is to manage your deployments declaratively via the YAML files, and then use those files to update your deployment.</li>
 	<li>Make sure you add this annotation to the template and not the deployment itself, since the kubectl apply command uses this field in the Deployment object. Also, do not update the change-cause annotation when doing simple scaling operations. A modification of change-cause is a significant change to the template and will trigger a new rollout.</li>
 	<li>The revision history is given in oldest to newest order. A unique revision number is incremented for each new rollout.</li>
 	<li>The undo command works regardless of the stage of the rollout. You can undo both partially completed and fully completed rollouts. An undo of a rollout is actually simply a rollout in reverse (e.g., from v2 to v1, instead of from v1 to v2), and all of the same policies that control the rollout strategy apply to the undo strategy as well.</li>
 	<li>When using declarative files to control your production systems, you want to, as much as possible, ensure that the checked-in manifests match what is actually running in your cluster. When you do a kubectl rollout undo you are updating the production state in a way that isn't reflected in your source control. An alternative (and perhaps preferred) way to undo a rollout is to revert your YAML file and kubectl apply the previous version. In this way, your "change tracked configuration" more closely tracks what is really running in your cluster.</li>
 	<li>Additionally, you can roll back to a specific revision in the history using the --to-revision flag</li>
 	<li>Specifying a revision of 0 is a shorthand way of specifying the previous revision. In this way, kubectl rollout undo is equivalent to kubectl rollout undo --to-revision=0.</li>
 	<li>To accomplish this, use the revisionHistoryLimit property in the deployment specification</li>
 	<li>By default, the complete revision history of a deployment is kept attached to the Deployment object itself. Over time (e.g., years) this history can grow fairly large, so it is recommended that if you have deployments that you expect to keep around for a long time you set a maximum history size for the deployment revision history, to limit the total size of the Deployment object. For example, if you do a daily update you may limit your revision history to 14, to keep a maximum of 2 weeks' worth of revisions (if you don't expect to need to roll back beyond 2 weeks).</li>
 	<li>The Recreate strategy is the simpler of the two rollout strategies. It simply updates the ReplicaSet it manages to use the new image and terminates all of the Pods associated with the deployment. The ReplicaSet notices that it no longer has any replicas, and re-creates all Pods using the new image. Once the Pods are re-created, they are running the new version.</li>
 	<li>While this strategy is fast and simple, it has one major drawback - it is potentially catastrophic, and will almost certainly result in some site downtime. Because of this, the Recreate strategy should only be used for test deployments where a service is not user-facing and a small amount of downtime is acceptable.</li>
 	<li>The RollingUpdate strategy is the generally preferable strategy for any user-facing service. While it is slower than Recreate, it is also significantly more sophisticated and robust. Using RollingUpdate, you can roll out a new version of your service while it is still receiving user traffic, without any downtime.</li>
 	<li>It is critically important that each version of your software, and all of its clients, is capable of talking interchangeably with both a slightly older and a slightly newer version of your software.</li>
 	<li>No matter how you update your software, you have to maintain backward and forward compatibility for reliable updates. The nature of the RollingUpdate strategy simply makes it more clear and explicit that this is something to think about.</li>
 	<li>This sort of backward compatibility is critical to decoupling your service from systems that depend on your service. If you don't formalize your APIs and decouple yourself, you are forced to carefully manage your rollouts with all of the other systems that call into your service. This kind of tight coupling makes it extremely hard to produce the necessary agility to be able to push out new software every week, let alone every hour or every day.</li>
 	<li>There are two parameters you can use to tune the rolling update behavior: maxUnavailable and maxSurge.</li>
 	<li>The maxUnavailable parameter sets the maximum number of Pods that can be unavailable during a rolling update. It can either be set to an absolute number (e.g., 3, meaning a maximum of three Pods can be unavailable) or to a percentage (e.g., 20%, meaning a maximum of 20% of the desired number of replicas can be unavailable).</li>
 	<li>At its core, the maxUnavailable parameter helps tune how quickly a rolling update proceeds. For example, if you set maxUnavailable to 50%, then the rolling update will immediately scale the old ReplicaSet down to 50% of its original size. If you have four replicas, it will scale it down to two replicas. The rolling update will then replace the removed Pods by scaling the new ReplicaSet up to two replicas, for a total of four replicas (two old, two new). It will then scale the old ReplicaSet down to zero replicas, for a total size of two new replicas. Finally, it will scale the new ReplicaSet up to four replicas, completing the rollout.</li>
 	<li>However, there are situations where you don't want to fall below 100% capacity, but you are willing to temporarily use additional resources in order to perform a rollout. In these situations, you can set the maxUnavailable parameter to 0%, and instead control the rollout using the maxSurge parameter. Like maxUnavailable, maxSurge can be specified either as a specific number or a percentage.</li>
 	<li>Setting maxSurge to 100% is equivalent to a blue/green deployment. The deployment controller first scales the new version up to 100% of the old version. Once the new version is healthy, it immediately scales the old version down to 0%.</li>
 	<li>The maxSurge parameter controls how many extra resources can be created to achieve a rollout. To illustrate how this works, imagine we have a service with 10 replicas. We set maxUnavailable to 0 and maxSurge to 20%. The first thing the rollout will do is scale the new ReplicaSet up to 2 replicas, for a total of 12 (120%) in the service. It will then scale the old ReplicaSet down to 8 replicas, for a total of 10 (8 old, 2 new) in the service. This process proceeds until the rollout is complete. At any time, the capacity of the service is guaranteed to be at least 100% and the maximum extra resources used for the rollout are limited to an additional 20% of all resources.</li>
 	<li>The deployment controller examines the Pod's status as determined by its readiness checks. Readiness checks are part of the Pod's health probes</li>
 	<li>If you want to use deployments to reliably roll out your software, you have to specify readiness health checks for the containers in your Pod. Without these checks, the deployment controller is running blind.</li>
 	<li>Setting minReadySeconds to 60 indicates that the deployment must wait for 60 seconds after seeing a Pod become healthy before moving on to updating the next Pod.</li>
 	<li>In addition to waiting a period of time for a Pod to become healthy, you also want to set a timeout that limits how long the system will wait.</li>
 	<li>It is important to note that this timeout is given in terms of deployment progress, not the overall length of a deployment. In this context, progress is defined as any time the deployment creates or deletes a Pod. When that happens, the timeout clock is reset to zero.</li>
 	<li>By default, deleting a deployment deletes the entire service. It will delete not just the deployment, but also any ReplicaSets being managed by the deployment, as well as any Pods being managed by the ReplicaSets.</li>
 	<li>Use the --cascade=false flag to exclusively delete the Deployment object.</li>
</ul>
<h2>Chapter 11: DaemonSets</h2>
<ul>
 	<li>Another reason to replicate a set of Pods is to schedule a single Pod on every node within the cluster.</li>
 	<li>A DaemonSet ensures a copy of a Pod is running across a set of nodes in a Kubernetes cluster. DaemonSets are used to deploy system daemons such as log collectors and monitoring agents, which typically must run on every node.</li>
 	<li>ReplicaSets should be used when your application is completely decoupled from the node and you can run multiple copies on a given node without special consideration.</li>
 	<li>DaemonSets should be used when a single copy of your application must run on all or a subset of the nodes in the cluster.</li>
 	<li>You should generally not use scheduling restrictions or other parameters to ensure that Pods do not colocate on the same node.</li>
 	<li>If you find yourself wanting a single Pod per node, then a DaemonSet is the correct Kubernetes resource to use.</li>
 	<li>Likewise, if you find yourself building a homogeneous replicated service to serve user traffic, then a ReplicaSet is probably the right Kubernetes resource to use.</li>
 	<li>To ensure that specific software is installed on every machine despite upgrades and scale events, a DaemonSet is the right approach.</li>
 	<li>By default a DaemonSet will create a copy of a Pod on every node unless a node selector is used, which will limit eligible nodes to those with a matching set of labels.</li>
 	<li>As a result, Pods created by DaemonSets are ignored by the Kubernetes scheduler.</li>
 	<li>Kubernetes uses a decoupled approach where Pods are top-level objects. This means that every tool you have learned for introspecting Pods in the context of ReplicaSets (e.g., kubectl logs &lt;pod-name&gt;) is equally applicable to Pods created by DaemonSets.</li>
 	<li>DaemonSets require a unique name across all DaemonSets in a given Kubernetes namespace. Each DaemonSet must include a Pod template spec, which will be used to create Pods as needed. This is where the similarities between ReplicaSets and DaemonSets end. Unlike ReplicaSets, DaemonSets will create Pods on every node in the cluster by default unless a node selector is used.</li>
 	<li>Removing labels from a node that are required by a DaemonSet's node selector will cause the Pod being managed by that DaemonSet to be removed from the node.</li>
 	<li>DaemonSets can be rolled out using the same RollingUpdate strategy that deployments use. You can configure the update strategy using the spec.updateStrategy.type field, which should have the value RollingUpdate.</li>
 	<li>You will likely want to set spec.minReadySeconds to a reasonably long value, for example 30-60 seconds, to ensure that your Pod is truly healthy before the rollout proceeds.</li>
 	<li>The characteristics of your application and cluster environment dictate the relative values of speed versus safety. A good approach might be to set maxUnavailable to 1 and only increase it if users or administrators complain about DaemonSet rollout speed.</li>
 	<li>Deleting a DaemonSet will also delete all the Pods being managed by that DaemonSet. Set the --cascade flag to false to ensure only the DaemonSet is deleted and not the Pods.</li>
 	<li>The DaemonSet provides its own controller and scheduler to ensure key services like monitoring agents are always up and running on the right nodes in your cluster.</li>
</ul>
<h2>Chapter 12: Jobs</h2>
<ul>
 	<li>A job creates Pods that run until successful termination (i.e., exit with 0). In contrast, a regular Pod will continually restart regardless of its exit code.</li>
 	<li>Given that Pods have to be scheduled, there is a chance that your job will not execute if the required resources are not found by the scheduler.</li>
 	<li>This job pattern is defined by two primary attributes of a job, namely the number of job completions and the number of Pods to run in parallel.</li>
 	<li>=--restart=OnFailure is the option that tells kubectl to create a Job object.</li>
 	<li>After the job has completed, the Job object and related Pod are still around. This is so that you can inspect the log output. Note that this job won't show up in kubectl get jobs unless you pass the -a flag. Without this flag, kubectl hides completed jobs.</li>
 	<li>The Job object will automatically pick a unique label and use it to identify the Pods it creates.</li>
 	<li>If you aren't careful, this'll create a lot of "junk" in your cluster. For this reason, we suggest you use restartPolicy: OnFailure so failed Pods are rerun in place.</li>
</ul>
<h2>Chapter 13: ConfigMaps and Secrets</h2>
<ul>
 	<li>ConfigMaps are used to provide configuration information for workloads. This can either be fine-grained information (a short string) or a composite value in the form of a file.</li>
 	<li>One way to think of a ConfigMap is as a Kubernetes object that defines a small filesystem. Another way is as a set of variables that can be used when defining the environment or command line for your containers. The key thing is that the ConfigMap is combined with the Pod right before it is run. This means that the container image and the Pod definition itself can be reused across many apps by just changing the ConfigMap that is used.</li>
 	<li>Secrets are exposed to Pods via explicit declaration in Pod manifests and the Kubernetes API. In this way, the Kubernetes secrets API provides an application-centric mechanism for exposing sensitive configuration information to applications in a way that's easy to audit and leverages native OS isolation primitives.</li>
 	<li>By default, Kubernetes secrets are stored in plain text in the etcd storage for the cluster.</li>
 	<li>Anyone who has cluster administration rights in your cluster will be able to read all of the secrets in the cluster.</li>
 	<li>Secrets volumes are managed by the kubelet and are created at Pod creation time. Secrets are stored on tmpfs volumes (aka RAM disks), and as such are not written to disk on nodes.</li>
 	<li>A special use case for secrets is to store access credentials for private Docker registries.</li>
 	<li>The key names for data items inside of a secret or ConfigMap are defined to map to valid environment variable names. They may begin with a dot followed by a letter or number.</li>
 	<li>When selecting a key name, consider that these keys can be exposed to Pods via a volume mount. Pick a name that is going to make sense when specified on a command line or in a config file.</li>
 	<li>ConfigMap data values are simple UTF-8 text specified directly in the manifest. As of Kubernetes 1.6, ConfigMaps are unable to store binary data.</li>
 	<li>The maximum size for a ConfigMap or secret is 1 MB.</li>
 	<li>You can see the raw data (including values in secrets!) with something like kubectl get configmap my-config -o yaml or kubectl get secret kuard-tls -o yaml.</li>
 	<li>It is generally a bad idea to check secret YAML files into source control. It is too easy to push these files someplace public and leak your secrets.</li>
 	<li>Once a ConfigMap or secret is updated using the API, it'll be automatically pushed to all volumes that use that ConfigMap or secret.</li>
 	<li>Currently there is no built-in way to signal an application when a new version of a ConfigMap is deployed. It is up to the application (or some helper script) to look for the config files to change and reload them.</li>
</ul>
<h2>Chapter 14: Role-Based Access Control for Kubernetes</h2>
<ul>
 	<li>If you are focused on hostile multi-tenant security, do not believe that RBAC by itself is sufficient to protect you. You must isolate the Pods running in your cluster to provide effective multi-tenant security.</li>
 	<li>Interestingly enough, Kubernetes does not have a built-in identity store, focusing instead on integrating other identity sources within itself.</li>
 	<li>Kubernetes makes a distinction between user identities and service account identities.</li>
 	<li>Service accounts are created and managed by Kubernetes itself and are generally associated with components running inside the cluster.</li>
 	<li>User accounts are all other accounts associated with actual users of the cluster, and often include automation like continuous delivery as a service that runs outside of the cluster.</li>
 	<li>You cannot use namespaced roles for non-namespaced resources (e.g., CustomResourceDefinitions), and binding a RoleBinding to a role only provides authorization within the Kubernetes namespace that contains both the Role and the RoleDefinition.</li>
 	<li>When the Kubernetes API server starts up, it automatically installs a number of default ClusterRoles that are defined in the code of the API server itself. This means that if you modify any built-in cluster role, those modifications are transient.</li>
 	<li>Whenever the API server is restarted (e.g., for an upgrade) your changes will be overwritten.</li>
 	<li>By default, the Kubernetes API server installs a cluster role that allows system:unauthenticated users access to the API server's API discovery endpoint. For any cluster exposed to a hostile environment (e.g., the public internet) this is a bad idea, and there has been at least one serious security vulnerability via this exposure. Consequently, if you are running a Kubernetes service on the public internet or an other hostile environment, you should ensure that the --anonymous-auth=false flag is set on your API server.</li>
 	<li>You can use can-i to validate configuration settings as you configure your cluster, or you can ask users to use the tool to validate their access when filing errors or bug reports.</li>
 	<li>If you want to see changes before they are made, you can add the --dry-run flag to the command to print but not submit the changes.</li>
 	<li>Kubernetes RBAC supports the usage of an aggregation rule to combine multiple roles together in a new role. This new role combines all of the capabilities of all of the aggregate roles together, and any changes to any of the constituent subroles will automatically be propogated back into the aggregate role.</li>
 	<li>A best practice for managing ClusterRole resources is to create a number of fine-grained aggregate them together to form higher-level or broadly defined cluster roles. This is how the built-in cluster roles are defined.</li>
 	<li>It's generally a best practice to use groups to manage the roles that define access to the cluster, rather than individually adding bindings to specific identities.</li>
</ul>
<h2>Chapter 15: Integrating Storage Solutions and Kubernetes</h2>
<ul>
 	<li>When you create a service of type ExternalName, the Kubernetes DNS service is instead populated with a CNAME record that points to the external name you specified</li>
 	<li>External services in Kubernetes have one significant restriction: they do not perform any health checking. The user is responsible for ensuring that the endpoint or DNS name supplied to Kubernetes is as reliable as necessary for the application.</li>
 	<li>A persistent volume is a storage location that has a lifetime independent of any Pod or container.</li>
 	<li>You can declare volumes directly inside a Pod specification, but this locks that Pod specification to a particular volume provider (e.g., a specific public or private cloud). By using volume claims, you can keep your Pod specifications cloud-agnostic; simply create different volumes, specific to the cloud, and use a PersistentVolumeClaim to bind them together.</li>
 	<li>Remember that once scheduled to a machine, a bare Pod is bound to that machine forever.</li>
 	<li>With dynamic volume provisioning, the cluster operator creates one or more StorageClass objects.</li>
 	<li>Once a storage class has been created for a cluster, you can refer to this storage class in your persistent volume claim, rather than referring to any specific persistent volume.</li>
 	<li>Automatic provisioning of a persistent volume is a great feature that makes it significantly easier to build and manage stateful applications in Kubernetes. However, the lifespan of these persistent volumes is dictated by the reclamation policy of the PersistentVolumeClaim and the default is to bind that lifespan to the lifespan of the Pod that creates the volume.</li>
 	<li>This means that if you happen to delete the Pod (e.g., via a scale-down or other event), then the volume is deleted as well.</li>
 	<li>Persistent volumes are great for traditional applications that require storage, but if you need to develop high-availability, scalable storage in a Kubernetes-native fashion, the newly released StatefulSet object can be used instead.</li>
 	<li>StatefulSets are replicated groups of Pods, similar to ReplicaSets. But unlike a ReplicaSet, they have certain unique properties:
<ul>
 	<li>"Each replica gets a persistent hostname with a unique index (e.g., database-0, database-1, etc.).</li>
 	<li>Each replica is created in order from lowest to highest index, and creation will block until the Pod at the previous index is healthy and available. This also applies to scaling up.</li>
 	<li>When a StatefulSet is deleted, each of the managed replica Pods is also deleted in order from highest to lowest. This also applies to scaling down the number of replicas.</li>
</ul>
</li>
 	<li>Once the StatefulSet is created, we also need to create a "headless" service to manage the DNS entries for the StatefulSet.</li>
 	<li>Ensure that you keep the same ordering, since the StatefulSet definition relies on the ConfigMap definition existing.</li>
 	<li>When you add a volume claim template to a StatefulSet definition, each time the StatefulSet controller creates a Pod that is part of the StatefulSet it will create a persistent volume claim based on this template as part of that Pod.</li>
</ul>
<h2>Chapter 16: Extending Kubernetes</h2>
<ul>
 	<li>In the case of custom resources, the name is special. It has to be the following format: &lt;resource-plural&gt;.&lt;api-group&gt;. The reason for this is to ensure that each resource definition is unique in the cluster, because the name of each CustomResourceDefinition has to match this pattern, and no two objects in the cluster can have the same name.</li>
 	<li>The storage field must be true for only a single version for the resource.</li>
 	<li>There is also a scope field to indicate if the resource is namespaced or not (the default is namespaced), and a names field that allows for the definition of the singular, plural, and kind values for the resource.</li>
 	<li>It is important to note that you should not use the Kubernetes API server for application data storage. The Kubernetes API server is not designed to be a key/value store for your app</li>
 	<li>Operators are the most complicated pattern for API extension of Kubernetes, but they are also the most powerful, enabling users to get easy access to "self-driving" abstractions that are responsible not just for deployment, but also health checking and repair.</li>
</ul>
<h2>Chapter 17: Deploying Real-World Applications</h2>
<ul>
 	<li>None</li>
</ul>
<h2>Chapter 18: Organizing Your Application</h2>
<ul>
 	<li>Should you use the same repository for application source code as well as configuration? This can work for small projects, but in larger projects it often makes sense to separate the source code from the configuration to provide for a separation of concerns. Even if the same people are responsible for both building and deploying the application, the perspectives of the builder versus the deployer are different enough that this separation of concerns makes sense.</li>
 	<li>First, it enables the committing of code to the production branch long before the feature is ready to ship. This enables feature development to stay much more closely aligned with the HEAD of a repository, and thus you avoid the horrendous merge conflicts of a long-lived branch.</li>
 	<li>Additionally, it means that the enabling a feature simply involves a configuration change to activate the flag. This makes it very clear what changed in the production environment, and likewise makes it very simple to roll back the activation of the feature if it causes problems.</li>
 	<li>The third principle of application layout is that code lands in source control, by default off, behind a feature flag, and is only activated through a code-reviewed change to configuration files.</li>
 	<li>Much like modifying the layout of packages in source control, modifying your deployment configurations after the fact is a complicated and expensive refactor that</li>
 	<li>you'll probably never get around to.</li>
 	<li>The first cardinality on which you want to organize your application is the semantic component or layer (e.g., frontend, batch work queue, etc.). Though early on this might seem like overkill, since a single team manages all of these components, it sets the stage for team scaling eventually, a different team (or subteam) may be responsible for each of these components.</li>
 	<li>While Kubernetes allows for the creation of YAML files with multiple objects in the same file, this should generally be considered an anti-pattern. The only good reason for grouping a number of objects in the same file is if they are conceptually identical. When deciding what to include in a single YAML file, consider design principles similar to those for defining a class or struct. If grouping the objects together doesn't form a single concept, they probably shouldn't be in a single file.</li>
 	<li>Given the file and version control approach, there are two different approaches that you can use.</li>
 	<li>The first is to use tags, branches, and source-control features. This is convenient because it maps to the same way that people manage revisions in source control, and it leads to a more simplified directory structure.</li>
 	<li>The other option is to clone the configuration within the filesystem and use directories for different revisions. This approach is convenient because it makes simultaneous viewing of the configurations very straightforward.</li>
 	<li>One common error when cherry-picking fixes into a release branch is to only pick the change into the latest release. It's a good idea to cherry-pick it into all active releases, in case for some reason you need to roll back versions but the fix is still needed.</li>
 	<li>the key to a highly available system is limiting the effect or "blast radius" of any change that you might make.</li>
 	<li>When you put your release schedule together, it is important to follow it completely for every release, no matter how big or how small. Many outages have been caused by people accelerating releases either to fix some other problem, or because they believed it to be "safe."</li>
 	<li>It is essential to develop dashboards that can tell you at a glance what version is running in which region, as well as alerting that will fire when too many different versions of your application are deployed.</li>
 	<li>A best practice is to limit the number of active versions to no more than three: one testing, one rolling out, and one being replaced by the rollout. Any more active versions than this is asking for trouble.</li>
</ul>
