---
layout: page
title: Book Review: Designing Distributed Systems
date: 2020-10-30 09:51
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/10/Designing-Distributed-Systems-BookCover.png"><img class="alignleft size-medium wp-image-33646" src="/wp-content/uploads/2020/10/Designing-Distributed-Systems-BookCover-220x300.png" alt="" width="220" height="300" /></a>Recently, I finished reading <a href="https://azure.microsoft.com/en-us/resources/designing-distributed-systems/" target="_blank" rel="noopener noreferrer">Designing Distributed Systems</a> by Brendan Burns.

Even though I am not a programmer, understanding the different patterns and models of distributed systems was helpful. I particularly appreciated the simple examples that were provided with each pattern to help illustrate how the work, and the potential challenges with using them.

Below are my highlights from reading this specific publication, to help you decide if this is the book for you, and if it will provide what you are looking for. Note that not every chapter will have highlights (depending on the content and the main focus of my work).

If my highlights peak your interest, I strongly recommend that you pick up a copy for yourself.
<h2>Chapter 1: Introduction</h2>
<ul>
 	<li>The potential for rapid, viral growth of a service means that every application has to be built to scale nearly instantly in response to user demand.</li>
 	<li>This, then, is the first value of patterns: they allow us to learn from the mistakes of others.</li>
 	<li>Consequently, another significant value of patterns is to provide a common set of names and definitions so that we don't waste time worrying about naming, and instead get right down to discussing the details and implementation of the core concepts.</li>
 	<li>Patterns provide another important tool for computer programming: the ability to identify common components that can be implemented once.</li>
 	<li>Today, every system ever written stands on the shoulders of thousands if not hundreds of thousands of years of human effort.</li>
</ul>
<h2>Section 1: Single-Node Patterns</h2>
<ul>
 	<li>In the end, groups of containers co-located on a single machine make up the atomic elements of distributed system patterns.</li>
 	<li>In general, the goal of a container is to establish boundaries around specific resources (e.g., this application needs two cores and 8 GB of memory).</li>
 	<li>Likewise, the boundary delineates team ownership (e.g., this team owns this image).</li>
 	<li>Finally, the boundary is intended to provide separation of concerns (e.g., this image does this one thing).</li>
 	<li>Small, focused applications are easier to understand and have fewer couplings to other systems.</li>
</ul>
<h2>Chapter 2: The Sidecar Pattern</h2>
<ul>
 	<li>The role of the sidecar is to augment and improve the application container, often without the application container's knowledge.</li>
 	<li>Fortunately, the sidecar pattern again can be used to provide new functionality that augments a legacy application without changing the existing application.</li>
 	<li>One of the other main advantages of using the sidecar pattern is modularity and reuse of the components used as sidecars.</li>
 	<li>However, this modularity and reusability, just like achieving modularity in high-quality software development requires focus and discipline. In particular, you need to focus on developing three areas:
<ul>
 	<li>Parameterizing your containers</li>
 	<li>Creating the API surface of your container</li>
 	<li>Documenting the operation of your container</li>
</ul>
</li>
 	<li>Parameterizing your containers is the most important thing you can do to make your containers modular and reusable regardless of whether they are sidecars or not, though sidecars and other add-on containers are especially important to parameterize.</li>
 	<li>There are two ways in which such parameters can be passed to your container: through environment variables or the command line.</li>
 	<li>As you think about defining modular, reusable containers, it is important to realize that all aspects of how your container interacts with its world are part of the API defined by that reusable container.</li>
 	<li>Even though EXPOSE is not necessary, it is a good practice to include it in your Dockerfile and also to add a comment that explains what exactly is listening on that port.</li>
 	<li>Finally, you should always use the LABEL directive to add metadata for your image; for example, the maintainer's email address, web page, and version of the image.</li>
</ul>
<h2>Chapter 3: Ambassadors</h2>
<ul>
 	<li>An ambassador container brokers interactions between the application container and the rest of the world.</li>
 	<li>This process is called service discovery, and the system that performs this discovery and linking is commonly called a service broker.</li>
</ul>
<h2>Chapter 4: Adapters</h2>
<ul>
 	<li>In the adapter pattern, the adapter container is used to modify the interface of the application container so that it conforms to some predefined interface that is expected of all applications.</li>
</ul>
<h2>Section 2: Serving Patterns</h2>
<ul>
 	<li>But of course there are downsides to the microservices approach to system design as well.</li>
 	<li>The two foremost disadvantages are that because the system has become more loosely coupled, debugging the system when failures occur is significantly more difficult.</li>
 	<li>As a corollary, microservices-based systems are also difficult to design and architect. A microservices-based system uses multiple methods of communicating between services; different patterns (e.g., synchronous, asynchronous, message-passing, etc.); and multiple different patterns of coordination and control among the services.</li>
</ul>
<h2>Chapter 5: Replicated Load-Balanced Services</h2>
<ul>
 	<li>The simplest distributed pattern, and one that most are familiar with, is a replicated load-balanced service.</li>
 	<li>In a three-nines service, you get 1.4 minutes of downtime per day (24 x 60 x 0.001). Assuming that you have a service that never crashes, that still means you need to be able to do a software upgrade in less than 1.4 minutes in order to hit your SLA with a single instance.</li>
 	<li>When designing a replicated service, it is equally important to build and deploy a readiness probe to inform the load balancer.</li>
 	<li>When building an application for a replicated service pattern, be sure to include a special URL that implements this readiness check.</li>
 	<li>Generally speaking, this session tracking is performed by hashing the source and destination IP addresses and using that key to identify the server that should service the requests.</li>
 	<li>NOTE: IP-based session tracking works within a cluster (internal IPs) but generally doesn't work well with external IP addresses because of network address translation (NAT). For external session tracking, application-level tracking (e.g., via cookies) is preferred.</li>
 	<li>Even if you plan on using SSL for communication between layers in your cluster, you should still use different certificates for the edge and your internal services.</li>
 	<li>Indeed, each individual internal service should use its own certificate to ensure that each layer can be rolled out independently.</li>
</ul>
<h2>Chapter 6: Sharded Services</h2>
<ul>
 	<li>Replicated services are generally used for building stateless services, whereas sharded services are generally used for building stateful services.</li>
 	<li>The downside of a shared service is twofold. First, because it is a shared service, you will have to scale it larger as demand load increases. Second, using the shared service introduces an extra network hop that will add some latency to requests and contribute network bandwith to the overall distributed system.</li>
 	<li>The hash function has two important characteristics for our sharding:
<ul>
 	<li>Determinism
<ul>
 	<li>The output should always be the same for a unique input.</li>
</ul>
</li>
 	<li>Uniformity
<ul>
 	<li>The distribution of outputs across the output space should be equal.</li>
</ul>
</li>
</ul>
</li>
 	<li>Determinism is important because it ensures that a particular request R always goes to the same shard in the service. Uniformity is important because it ensures that load is evenly spread between the different shards.</li>
 	<li>instead of hashing the entire request object, a much better sharding function would be shard(request.path). When we use request.path as the shard key, then we map both requests to the same shard, and thus the response to one request can be served out of the cache to service the other.</li>
 	<li>Determining the appropriate key for your sharding function is vital to designing your sharded system well. Determining the correct shard key requires an understanding of the requests that you expect to see.</li>
 	<li>Consistent hashing functions are special hash functions that are guaranteed to only remap # keys / # shards, when being resized to # shards.</li>
</ul>
<h2>Chapter 7: Scatter/Gather</h2>
<ul>
 	<li>Specifically, the scatter/gather pattern allows you to achieve parallelism in servicing requests, enabling you to service them significantly faster than you could if you had to service them sequentially.</li>
 	<li>Like replicated and sharded systems, the scatter/gather pattern is a tree pattern with a root that distributes requests and leaves that process those requests.</li>
 	<li>However, in contrast to replicated and sharded systems, with scatter/gather requests are simultaneously farmed out to all of the replicas in the system. Each replica does a small amount of processing and then returns a fraction of the result to the root. The root server then combines the various partial results together to form a single complete response to the request and then sends this request back out to the client.</li>
 	<li>Scatter/gather can be seen as sharding the computation necessary to service the request, rather than sharding the data (although data sharding may be part of it as well).</li>
 	<li>Instead of parallelizing an application across cores on a single machine, we can use the scatter/gather pattern to parallelize requests across multiple processes on many different machines. In this way, we can improve our overall latency requests, since we are no longer bound by the number of cores we can get on a single machine.</li>
 	<li>While applying the replicated data scatter/gather pattern allows you to reduce the processing time required for handling user requests, it doesn't allow you to scale beyond an amount of data that can be held in the memory or disk of a single machine.</li>
 	<li>Increased parallelization comes at a cost, and thus choosing the right number of leaf nodes in the scatter/gather pattern is critical to designing a performant distributed system.</li>
 	<li>It is important to remember that in a scatter/gather system, the root node waits for requests from all of the leaf nodes to return before sending a response back to the end user. Since data from every leaf node is required, the overall time it takes to process a user request is defined by the slowest leaf node that sends a response.</li>
 	<li>Together, these complications of scatter/gather systems lead us to some conclusions:
<ul>
 	<li>Increased parallelism doesn't always speed things up because of overhead on each node.</li>
 	<li>Increased parallelism doesn't always speed things up because of the straggler problem.</li>
 	<li>The performance of the 99th percentile is more important than in other systems because each user request actually becomes numerous requests to the service.</li>
</ul>
</li>
 	<li>Given these challenges of reliability and scale, the correct approach is to replicate each of the individual shards so that instead of a single instance at each leaf node, there is a replicated service that implements each leaf shard.</li>
</ul>
<h2>Chapter 8: Functions and Event-Driven Processing</h2>
<ul>
 	<li>Because there is no artifact to create or push beyond the source code itself, FaaS makes it simple to go from code on a laptop or web browser to running code in the cloud.</li>
 	<li>Developing systems using FaaS forces you to strongly decouple each piece of your service. Each function is entirely independent. The only communication is across the network, and each function instance cannot have local memory, requiring all states to be stored in a storage service.</li>
 	<li>Since each function is radically decoupled from the other functions, there is no real representation of the dependencies or interactions between different functions.</li>
 	<li>For now, when adopting FaaS, you must be vigilant to adopt rigorous monitoring and alerting for how your system is behaving so that you can detect situations and correct them before they become significant problems.</li>
 	<li>Because of the serverless nature of the implementation of theses services, the runtime of any particular function instance is generally time bounded. This means that FaaS is usually a poor fit for situations that require processing.</li>
 	<li>But if you have a sufficient number of requests to keep a function active, then it's likely you are overpaying for the requests you are processing.</li>
 	<li>One ideal way to scale FaaS is to run an open source FaaS that runs on a container orchestrator like Kubernetes. That way, you can still take advantage of the developer benefits of FaaS, while taking advantage of the pricing models of virtual machines.</li>
 	<li>Because decoration transformations are generally stateless, and also because they are often added after the fact to existing code as the service evolves, they are ideal services to implement via FaaS.</li>
 	<li>Requests are part of a larger series of interactions or sessions; generally each user request is part of a larger interaction with a complete web application or API.</li>
 	<li>Events, as I see them, instead tend to be single-instance and asynchronous in nature. Events are important and need to be properly handled, but they are fired off from a main interaction and responded to some time later.</li>
</ul>
<h2>Chapter 9: Ownership Election</h2>
<ul>
 	<li>Often, establishing distributed ownership is both the most complicated and most important part of designing a reliable distributed system.</li>
 	<li>One of the key components of designing a distributed system is deciding when the "distributed" part is actually unnecessarily complex.</li>
 	<li>There are two ways to implement this master election. This first is to implement a distributed consensus algorithm like Paxos or RAFT</li>
 	<li>Operators are still a new idea but represent an important new direction in building reliable distributed systems.</li>
 	<li>The simplest form of synchronization is the mutual exclusion lock (aka Mutex).</li>
 	<li>NOTE: When using distributed locks, it is critical to ensure that any processing you do doesn't last longer than the TTL of the lock. One good practice is to set a watchdog timer when you acquire the lock. The watchdog contains an assertion that will crash your program if the TTL of the lock expires before you have called unlock.</li>
</ul>
<h2>Chapter 10: Work Queue Systems</h2>
<ul>
 	<li>Consequently, it is a best practice to always add versions to your APIs even if</li>
 	<li>youâ€™re not sure they will ever change. Better safe than sorry.</li>
 	<li>Additionally, Kubernetes has annotations for each Job object that enable us to mark each job with the work item it is processing.</li>
 	<li>the multi-worker pattern transforms a collection of different</li>
 	<li>worker containers into a single unified container that implements the worker interface, yet delegates the actual work to a collection of different, reusable containers.</li>
</ul>
<h2>Chapter 11: Event-Driven Batch Processing</h2>
<ul>
 	<li>Work queues are great for enabling individual transformations of one input to one output.</li>
 	<li>The operation of an event-driven batch processor is similar to event-driven FaaS. Consequently, without an overall blueprint for how the different event queues relate to each other, it can be hard to fully understand how the system is operating.</li>
 	<li>The first pattern for coordinating work queues is a copier. The job of a copier is to take a single stream of work items and duplicate it out into two or more identical streams.</li>
 	<li>The role of a filter is to reduce a stream of work items to a smaller stream of work items by filtering out work items that don't meet particular criteria.</li>
 	<li>The role of a splitter is to evaluate some criteria just like a filter but instead of eliminating input, the splitter sends different inputs to different queues based on that criteria.</li>
 	<li>A splitter can also be a copier if it sends the same output to multiple queues.</li>
 	<li>It is interesting to note that a splitter can actually also be implemented by a copier and two different filters. But the splitter pattern is a more compact representation that captures the job of the splitter more succinctly.</li>
 	<li>The role of a sharder in a workflow is to divide up a single queue into an evenly divided collection of work items based upon some sort of sharding function.</li>
 	<li>The last pattern for event-driven or workflow batch systems is a merger. A merger is the opposite of a copier; the job of a merger is to take two different work queues and turn them into a single work queue.</li>
 	<li>Initializing Helm deploys a cluster-side component named tiller to your cluster and installs some templates to your local filesystem.</li>
 	<li>NOTE: Helm templates have different levels of production hardening and support. stable templates are the most strictly vetted and supported, whereas incubator templates like Kafka are more experimental and have less production mileage. Regardless, incubator templates are useful for quick proof of concepts as well as a place to start from when implementing a production deployment of a Kubernetes-based service.</li>
 	<li>The replication factor is how many different machines messages in the topic will be replicated to. This is the redundancy that is available in case things crash. A value of 3 or 5 is recommended.</li>
</ul>
<h2>Chapter 12: Coordinated Batch Processing</h2>
<ul>
 	<li>The reduce step is an example of coordinated processing that eventually reduces a large number of outputs down to a single aggregate response.</li>
 	<li>Merge simply blends the output of two work queues into a single work queue for additional processing. While the merge pattern is sufficient in some cases, it does not ensure that a complete dataset is present prior to the beginning of processing.</li>
 	<li>Join is similar to joining a thread. The basic idea is that all of the work is happening in parallel, but work items aren't released out of the join until all of the work items that are processed in parallel are completed. This is also generally known as barrier synchronization in concurrent programming.</li>
 	<li>The value of the join is that it ensures that all of the data in the set is present. The downside of the join pattern is that it requires that all data be processed by a previous stage before subsequent computation can begin. This reduces the parallelism that is possible in the batch workflow, and thus increases the overall latency of running the workflow.</li>
 	<li>This is a fortunate contrast to the join pattern, because unlike join, it means that reduce can be started in parallel while there is still processing going on as part of the map/shard phase. Of course, in order to produce a complete output, all of the data must be processed eventually, but the ability to begin early means that the batch computation executes more quickly overall.</li>
</ul>
<h2>Chapter 13: Conclusion: A New Beginning?</h2>
<ul>
 	<li>None</li>
</ul>
