---
layout: page
title: Book Review: GitOps and Kubernetes
date: 2020-09-03 08:35
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/07/GitOpsAndKubernetes-BookCover.png"><img class="alignleft size-medium wp-image-33453" src="/wp-content/uploads/2020/07/GitOpsAndKubernetes-BookCover-240x300.png" alt="" width="240" height="300" /></a>Recently, I finished reading <a href="https://www.manning.com/books/gitops-and-kubernetes" target="_blank" rel="noopener noreferrer">GitOps and Kubernetes</a> by Billy Yuen, Alexander Matyushentsev, Todd Ekenstam, and Jesse Suen.

I've already been well along my journey of learning Kubernetes, but adding GitOps to the mix is the next level/stage.

I found<span style="color: #000000;"> the whole book helpful but in particular Chapter 2 ("<strong>Kubernetes &amp; GitOps</strong>"), Chapter 4 ("<strong>Pipelines</strong>"), and Chapter 8 ("<strong>Observability</strong>") were helpful. I also found Chapter 11 ("<strong>Flux</strong>) really interesting.</span>

<span style="color: #000000;">I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).</span>

If my highlights peak your interest, I strongly recommend that you pick up a copy for yourself.
<h1>Chapter 1: Why GitOps?</h1>
<ul>
 	<li>GitOps is a new method of Continuous Deployment that uses Git as a single source of truth for declarative infrastructure and applications, providing both revision and change control.</li>
 	<li>The goal in a GitOps model is always to automate as much as possible and get to the point where you are comfortable with Continuous Deployment of your changes.</li>
 	<li>DevOps enables “Just in Time” deployment, but may lack the ability for traceability and release control in a form easy for developers to access.</li>
 	<li>When following a GitOps model, the desired configuration of the system is stored in a revision control system, such as Git, and an “operator” software process is responsible for changing the current state of the system into the desired state of the system.</li>
 	<li>In an ideal implementation of GitOps, manual changes to the system are not permitted, and all changes must be made to the configuration files stored in Git. In an extreme case, permission to change the system is only granted to the “operator” software process.</li>
 	<li>The role of the infrastructure and operations engineers in a GitOps model shifts from performing the infrastructure changes and application deployments to developing and maintaining the GitOps automation and helping teams review and approve changes using Git.</li>
 	<li>The truth of the matter is, GitOps does not enable the use of declarative methodologies, but rather the other way around.</li>
 	<li><strong>Note:</strong> that simply storing your provisioning scripts in Git, does not necessarily mean you are following GitOps principles, even if those scripts were written to be idempotent.</li>
 	<li>Without a source of truth of your desired state put in place, and without a mechanism to verify convergence to that source of truth, it is impossible to know that your environment is truly secure.</li>
 	<li>Git can also integrate with project management and bug tracking software, allowing full traceability of all changes and enable root cause analysis and other forensics.</li>
 	<li>Git’s strength in change control (Pull Request), traceability, and history authenticity along with Kubernetes’ Declarative Configuration naturally satisfy the Security, Availability, and Processing integrity principles of SOC 2.</li>
 	<li>Configuration specs such as Hashicorp Terraform, AWS CloudFormation, and most recently, Kubernetes manifests have emerged as a preferable way to recover infrastructure through recreation, versus restoration.</li>
 	<li>With GitOps, you are, in effect, practicing disaster recovery procedures on a regular basis, making you well prepared on the occasion that a real disaster strikes.</li>
 	<li>Since rollbacks are just another commit in the Git history, rollbacks are able to go through the same review process as normal deployments.</li>
</ul>
<h1>Chapter 2: Kubernetes &amp; GitOps</h1>
<ul>
 	<li>Namespaces also provide a way to isolate users and applications from each other through role-based access controls (RBAC), network policies, and resource quotas.</li>
 	<li>The manifest of a live resource includes all the fields which were specified in the file plus dozens of new fields such as more metadata, the status field as well as additional fields in the resource spec.</li>
 	<li>The controller populates information about resource state in the status field and applies default values of all unspecified optional fields</li>
 	<li>Every time the kubectl apply command updates a resource, it saves the input manifest in the kubectl.kubernetes.io/last-applied-configuration annotation.</li>
 	<li>You typically should not mix imperative commands, such as kubectl edit or kubectl scale, with declarative resource management. This will make the current state not match the last-applied-configuration annotation and will defeat the merge algorithm kubectl uses to determine deleted fields.</li>
 	<li>To pass control of the replicas field over to the Horizontal Pod Autoscaler, the replicas field must first be deleted from the file which contains the Deployment manifest. This is so the next kubectl apply does not override the replicas value set by the Horizontal Pod Autoscaler.</li>
 	<li>Each controller runs an infinite loop, and every iteration reconciles the desired and the actual state of the cluster resources it is responsible for.</li>
 	<li>The watch feature is provided by the Kubernetes API for most resource types and allows the caller to get a notification when a resource is created, modified, or deleted.</li>
 	<li>GitOps assumes that every piece of infrastructure is represented as a file that is stored in a revision control system, and there is an automated process that seamlessly applies changes to the application runtime environment.</li>
 	<li>Unlike traditional systems, in Kubernetes there are almost no APIs that can modify just a subset of some existing resources. For example, there is no (and never will be) API that modifies only the container image of a pod. Instead, the Kubernetes API server expects all API requests to provide a complete manifest of the resource to the API server.</li>
 	<li>A common mistake that people make is to use latest as their image tag (e.g., gitopsbook/sample-app:latest ) or re-using the same image tag from build to build.</li>
 	<li>Re-using image tags from build to build is bad practice, for several reasons:
<ul>
 	<li>The first reason why container tags should not be re-used is that when container image tags are re-used, Kubernetes will not actually deploy the new version to the cluster. This is because the second time the manifests are attempted to be applied, Kubernetes would not detect any change in the manifests, and the second kubectl apply would have zero effect.
<ul>
 	<li>Therefore, from the perspective of Kubernetes, there is no difference between what is being applied in build #1 versus build #2; the Deployment specs are the same. In fact, Kubernetes treats the second apply as a no-op (no operation) and does nothing.</li>
 	<li>In order for Kubernetes to redeploy, something needs to be different in the Deployment spec from the first build to the second. Using unique container image tags ensures there is a difference.</li>
</ul>
</li>
 	<li>Another reason for incorporating a unique version into the image tag is because it enables traceability. By incorporating something like the application’s Git commit-SHA into the tag, there is never any question about what version of the software is currently running in the cluster.</li>
 	<li>The third and possibly most important reason for not re-using image tags such as latest is that rollback to the older version becomes impossible. When you re-use image tags, you are overriding or rewriting the meaning of that overwritten image.</li>
</ul>
</li>
 	<li><strong>Note:</strong> kubectl rollout restart Kubectl has a convenience command, kubectl rollout restart, which causes all the pods of a deployment to restart (even if the image tag is the same). It is useful in dev and test scenarios where the image tag has been overwritten, and redeploy is desired. It works by injecting an arbitrary timestamp into the pod template metadata annotations. This causes the pod spec to be different than what it was before, which in turn causes a normal, rolling update of the pods.</li>
</ul>
<h1>Chapter 3: Environment Management</h1>
<ul>
 	<li>The right granularity should enable your code to be deployed without dependencies on other teams/code.</li>
 	<li>Namespaces provide a scope for unique resource naming, resource quotas, Role-Based Access Control (RBAC), hardware isolation, and network configuration.</li>
 	<li>Namespaces can also have their own dedicated hardware and networking policy to optimize their configuration based on application requirements.</li>
 	<li>By default, all namespaces are able to connect to services running in all other namespaces.</li>
 	<li>It is possible to apply a namespace network policy that restricts network communication between namespaces.</li>
 	<li>Network Policy is only supported if Container Native Interface (CNI) is configured</li>
 	<li>Correctly utilizing NetworkPolicy constraints are an important aspect of define environment boundaries.</li>
 	<li>The primary reason for having two separate clusters to host your environments is to protect your production environment from accidental outages or other impacts related to work being done with the pre-production environments.</li>
 	<li>Good Kubernetes configuration tools have the following properties:
<ul>
 	<li>Declarative: The config is unambiguous, deterministic, and not system dependent.</li>
 	<li>Readable: The config is written in a way that is easy to understand.</li>
 	<li>Flexible: The tool helps facilitate, and does not get in the way of accomplishing what you are trying to do.</li>
 	<li>Maintainable: The tool should promote reuse and composability.</li>
</ul>
</li>
</ul>
<h1>Chapter 4: Pipelines</h1>
<ul>
 	<li>The main difference between GitOps when compared to traditional CI is that with GitOps, the CI pipeline also updates the application manifest with the new image version after the build and test stages have completed successfully.</li>
 	<li>What makes GitOps CD different from traditional CD is the use of a GitOps operator to monitor the manifest changes and orchestrate the deployment. As long as the CI build is complete and the manifest is updated, GitOps Operator takes care of the eventual deployment.</li>
 	<li>Unit Tests are for verifying correctness at the module level, and functional tests are for verifying correctness across two or more modules.</li>
 	<li><strong>Note:</strong> In our experience, the most time-consuming portion of the build is downloading the dependencies. It is highly recommended to cache your dependencies in your build system to reduce the build time.</li>
 	<li>Unit tests should have no dependencies on code outside the unit tested.</li>
 	<li>Mocking is a “required” investment and will save the team time (faster test execution) and effort (troubleshooting flaky tests).</li>
 	<li>Code coverage measurement simply determines which statements in a body of code have been executed through a test run, and which statements have not.</li>
 	<li><strong>Note:</strong> Driving code coverage percentages higher alone can lead to wrong behavior and actually lower quality. Code coverage measures the percentage of lines being executed but does not measure the correctness of the code. 100% code coverage with partial assertions will NOT achieve the quality goal of unit testing.</li>
 	<li>Since Git creates a unique hash for each commit, it is recommended to use the Git Hash to tag the docker image instead of creating an arbitrary version number. In addition to uniqueness, each docker image can easily trace back to the Git repo history using the Git hash to</li>
 	<li>determine what the exact code is in the docker image.</li>
 	<li>Compliance requirements: For SOX2 or PCI requirements, build information such as test results, who did the release, and what was released are required anywhere from 14 months up to 7 years.</li>
 	<li>The git revert command can be considered an 'undo' command. Instead of removing the commit from the project history, it figures out how to invert the changes introduced by the commit and appends a new commit with the resulting inverse content. This prevents Git from losing history, which is important for the integrity of your revision history (compliance and auditability) and for reliable collaboration.</li>
</ul>
<h1>Chapter 5: Deployment strategies</h1>
<ul>
 	<li>A ReplicaSet is defined with the selector that specifies how to identify Pods, the number of replicas to be maintained, and a PodSpec.</li>
 	<li><strong>Note:</strong> Deployment and ReplicaSets A Deployment will create one ReplicaSet per image id and set the number of replicas to the desired value in the ReplicaSet with the matching image id. For all other ReplicaSets, Deployment will set those ReplicaSets’ replicas number to 0 in order to terminate all non-matching image id Pods.</li>
 	<li>Deployment ensures that only a certain number of Pods are down while they are being updated. By default, it ensures that at least 75% of the desired number of Pods are up (25% max unavailable).</li>
 	<li>Deployment also ensures that only a certain number of Pods are created above the desired number of Pods. By default, it ensures that at most 125% of the desired number of Pods are up (25% max surge).</li>
 	<li>The set of Pods targeted by a Service is determined by a selector that is a field within the Service manifest. Service will then forward traffic to pods with the matching labels as specified in the selector</li>
 	<li><strong>Note:</strong> Argo Rollouts The Argo Rollouts controller uses the Rollout custom resource to provide additional deployment strategies such as Blue-Green and Canary to Kubernetes. The Rollout custom resource provides feature parity with the deployment resource but with additional deployment strategies.</li>
 	<li><strong>Note:</strong> Argo Rollouts internally will maintain one replicaSet for “blue”, one replicaSet for “Green”. It will also ensure that the Green Deployment is fully scaled before updating the service selector to send all traffic over to Green. (Hence only one service is required in this case.) In addition, Argo Rollouts will also wait 30 seconds for all blue traffic to complete and scale down the Blue Deployment.</li>
 	<li>Progressive Delivery continuously collects and analyzes the health of the new pods in addition to scale-up the Progressive Deployment (Green) and scale-down the production deployment (blue), as long as the analysis is determined to be successful</li>
</ul>
<h1>Chapter 6: Access Control &amp; Security</h1>
<ul>
 	<li>With GitOps and Kubernetes, the engineering team is empowered to contribute to the security by writing Kubernetes access configs and using Git to enforce proper configuration change process.</li>
 	<li>Regardless of the domain area, access control includes three main components: subject, object, and reference monitor.</li>
 	<li>The subject is the entity that requests access to an object.
<ul>
 	<li>The object is the entity or resource being accessed.</li>
 	<li>The reference monitor is the entity controlling access to the protected object.</li>
</ul>
</li>
 	<li>With GitOps, direct access to the cluster is no longer strictly required, since environment management can go through a new alternate medium, git.</li>
 	<li>Unless you are using GitOps, the Kubernetes configuration is updated either manually or scripted in continuous integration. This approach, sometimes called CI Ops[38], usually makes the security team very nervous.</li>
 	<li>Git is built on top of the solid cryptographic foundation: it uses Merkle trees as a fundamental underlying data structure. The same data structure is used as a foundation for the blockchain</li>
 	<li>Git was not designed with strong identity guaranties.</li>
 	<li>So an intruder can easily create a commit and put your boss’s name into the commit metadata.</li>
 	<li>Github allows you to require that all commits to a particular repository be signed. The “Require signed commits” setting is available under the “Protected branches” section of the repository settings.</li>
 	<li>There are four well-known access control flavors:
<ul>
 	<li>Discretionary access control (DAC) With DAC models, the data owner decides on access. DAC is a means of assigning access rights based on rules that users specify.</li>
 	<li>Mandatory access control (MAC) MAC was developed using a nondiscretionary model, in which people are granted access based on an information clearance. MAC is a policy in which access rights are assigned based on regulations from a central authority.</li>
 	<li>Role-Based Access Control (RBAC) RBAC grants access based on a user’s role and implement key security principles, such as “least privilege” and “separation of privilege.” Thus, someone attempting to access information can only access data that are deemed necessary for their role.</li>
 	<li>Attribute-Based Access Control (ABAC) Attribute-based access control (ABAC), also known as policy-based access control, defines an access control paradigm whereby access rights are granted to users through the use of policies that combine attributes together.</li>
</ul>
</li>
 	<li>Currently, RBAC is the preferred authorization mechanism in Kubernetes and recommended to use for every application running on Kubernetes.</li>
 	<li>It is important to know that Roles are namespaced resources and provide access to the resources defined in the same namespace.</li>
 	<li>This means that a single role cannot provide access to the resources in multiple namespaces or cluster level resources.</li>
 	<li>The docker feature named Content Trust allows signing the image and push it into the registry along with the signature. The consumer can use the Content Trust feature to verify that the signed image content was not changed.</li>
 	<li>Disabling direct Kubernetes access for developers by default is a big step forward from a security perspective.</li>
 	<li>This can be accomplished using the Open Policy Agent (OPA), and an admission webhook that rejects manifests that reference an image coming from a prohibited image registry.</li>
</ul>
<h1>Chapter 7: Secrets</h1>
<ul>
 	<li>Exposing Secrets to containers as environment variables, while convenient, is arguably not the optimal way to consume secrets, since it is less secure than consuming it as a volume</li>
 	<li>mounted file.</li>
 	<li>A second disadvantage of using Secrets as environment variables, is that unlike Secrets projected into volumes, values of secret environment variables will not be updated if the Secret is ever updated after the container starts. A container or pod restart would be necessary to notice changes.</li>
 	<li>So in practice, the only real acceptable scenarios where Secrets could be stored as-is in git, are when the secrets do not contain any truly sensitive data, such as dev and test environments.</li>
 	<li>Baking the sensitive data directly into the container image has some very bad drawbacks, which should automatically rule it out as a viable option.</li>
 	<li>The first issue is that the container image itself is now sensitive. Due to the fact that the sensitive data was copied into the image, anyone or anything that has access to the container image (e.g. via a docker pull), can now trivially copy out and retrieve the secret.</li>
 	<li>Another problem is that because the secret is baked into the image, it makes updates to the secret data extremely burdensome. Whenever the credentials need to be rotated, it would require a complete rebuild of the container image.</li>
 	<li>A third problem is that the container image is not flexible enough to accomodate when the same image needs to run using different secret datasets.</li>
 	<li>With a strict scope, SealedSecrets encrypts the Secret in such a way that it can only be used for the namespace that it was encrypted for, and also with the exact same Secret name (my-password in our example).</li>
</ul>
<h1>Chapter 8: Observability</h1>
<ul>
 	<li>GitOps relies on the observability of Kubernetes and the application in order to do its job.</li>
 	<li>For Kubernetes, a fundamental aspect of observability is the ability to display the log output of all the various pods in the cluster.</li>
 	<li>Kubernetes provides basic metrics using an optional component called the metrics-server.</li>
 	<li>In addition to general CPU and memory utilization which is common across all Pods, applications can provide their own metrics by exposing an HTTP “metrics endpoint” that returns a list of metrics in the form of key-value pairs.</li>
 	<li>Whereas metrics typically give an aggregated view of the application in a particular system, tracing data usually gives a detailed view of the execution flow of an individual request, potentially across multiple services and systems.</li>
 	<li>Often tracing data is sampled at a configured rate and may have a much shorter retention period than, for example, application logs or metrics.</li>
 	<li>The Pod itself notifies Kubernetes when it is ready based on its own application-specific logic.</li>
 	<li>Each container in the Pod can specify a Readiness probe, in the form of a command or an HTTP request, that will indicate when the container is Ready . It is up to the container to provide this observability about its own internal state.</li>
 	<li>Once all the containers in the Pod are Ready , then the Pod itself is considered Ready and can be added to load balancers of matching Services and begin handling requests.</li>
 	<li>Application developers must properly implement these probes so that the application provides the correct observability of its operation.</li>
 	<li>At a high-level, a good framework for thinking about metrics was described by Rob Ewaschuk, who defined the “four golden signals” as the most important metrics to focus on.
<ul>
 	<li>Latency - The time it takes to service a request.</li>
 	<li>Traffic - A measure of how much demand is placed on the system.</li>
 	<li>Errors - The rate of requests that are not successful. · Saturation - How "full" your service is.</li>
</ul>
</li>
 	<li>Brendan Gregg proposed the USE Method for characterizing the performance of system resources (like infrastructure, such as Kubernetes nodes).
<ul>
 	<li>Utilization - The average time that the resource was busy servicing work.</li>
 	<li>Saturation - The degree to which the resource has extra work which it can't service, often queued.</li>
 	<li>Errors - The count of error events.</li>
</ul>
</li>
 	<li>For request-driven applications (like microservices), Tom Wilkie defined the RED Method.
<ul>
 	<li>Rate - The number of requests per second a service is processing</li>
 	<li>Errors - The number of failed requests per second</li>
 	<li>Duration - Distributions of the amount of time each request takes.</li>
</ul>
</li>
 	<li>The output of kubectl diff provides a preview of the changes that would be applied to the cluster if the deployment repo is synced. This is a key feature of GitOps observability.</li>
 	<li>However, it is our view that 2-way syncing is not desirable because it allows and encourages manual changes to the cluster and bypasses the security and review process that GitOps provides as one of it’s core benefits.</li>
 	<li>For GitOps, being able to look at the deployment repository logs is just as important as looking at the application logs when it comes to the observability of the GitOps system.</li>
</ul>
<h1>Chapter 9: Argo CD</h1>
<ul>
 	<li>The Kubernetes has a great built-in role-based access control system, but that is not enough when you have to deal with hundreds of clusters.</li>
 	<li>Sync Status answers whether the observed application resources state deviates from the resources state stored in the Git repository. The logic behind deviation calculation is equivalent to the logic of the kubectl diff command.</li>
 	<li>Argo CD provides a flexible role-based access control (RBAC) system which implementation is based on Casbin - powerful open-source access control library.</li>
</ul>
<h1>Chapter 10: Jenkins X</h1>
<ul>
 	<li>None</li>
</ul>
<h1>Chapter 11: Flux</h1>
<ul>
 	<li>The Flux project was created to automate container image delivery to Kubernetes and fill the gap between the Continuous Integration and Continuous Deployment processes.</li>
 	<li>Flux typically runs inside of the managed cluster and relies on Kubernetes RBAC.</li>
 	<li>One of the most important considerations is that Flux has to be configured and maintained by the Kubernetes end user. That implies that the team gets more power but also has more responsibility. The alternate approach, which is taken by Argo CD, is to provide GitOps function as a service.</li>
 	<li>Flux is able to scan the Docker registry and automatically update images in the deployment repository when new tags get pushed into the registry.</li>
 	<li>Instead of using the CI system and scripting, you can configure Flux to automatically update the deployment repository every time when a new image is pushed to the Docker registry.</li>
 	<li>It is common practice to maintain the base set of manifests for the application and generate environment specified manifests using tools like Kustomize or Helm.</li>
</ul>
