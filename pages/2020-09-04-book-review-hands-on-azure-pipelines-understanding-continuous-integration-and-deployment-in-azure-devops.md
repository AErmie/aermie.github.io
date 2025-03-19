---
layout: page
title: Book Review: Hands-on Azure Pipelines - Understanding Continuous Integration and Deployment in Azure DevOps
date: 2020-09-04 22:37
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/09/HandsOnAzurePipelines-BookCover.jpg"><img class="alignleft wp-image-33527 size-medium" src="/wp-content/uploads/2020/09/HandsOnAzurePipelines-BookCover-210x300.jpg" alt="" width="210" height="300" /></a>Recently, I finished reading <a href="https://www.apress.com/us/book/9781484259016" target="_blank" rel="noopener noreferrer">Hands-on Azure Pipelines: Understanding Continuous Integration and Deployment in Azure DevOps</a> by Chaminda Chandrasekara, and Pushpa Herath. This is one book in a multi-book series about the various Azure DevOps features. The other books (that I am aware of) include:
<ul>
 	<li><a href="https://www.apress.com/us/book/9781484250457" target="_blank" rel="noopener noreferrer">Hands-on Azure Boards - Configuring and Customizing Process Workflows in Azure DevOps Services</a></li>
 	<li><a href="https://www.apress.com/us/book/9781484254240" target="_blank" rel="noopener noreferrer">Hands-on Azure Repos - Understanding Centralized and Distributed Version Control in Azure DevOps Services</a></li>
</ul>
I am already somewhat experienced with Azure DevOps, so most of the concepts I was already familiar with.

Normally, I just share my highlights from reading a publication, but I have to share a few less than positive remarks (which I don't normally do).

Firstly, I found the writing style/method highly repetitive. There was a lot of duplication in points that were made, either in the subsequent paragraph, or even in some cases immediate after the original sentence! Secondly, one thing that I found extremely annoying about this book, is that all throughout the first 2 chapters, the phrase/sentence "we will discuss more details on topic XYZ in future chapters of this book" was constantly used, and even in further chapters it used this (but not quite as much). That really got on my nerves. Third, it was really poorly written. For a publishing company like Apress, I would expect there to be a copy editor/reviewer that would catch the simple things like word tense, grammar, sense stress, etc. I mean, sure, I can read through it and understand what they're trying to say, but I would expect a multi-book series published by Apress, to have at least <b><i>some </i></b>polish! Case in point, take a look at my highlights, which are verbatim from the publication.

Also, at various places throughout the book, when mentioning a specific topic (like Service Principals), it would make the effective statement "we already covered this in our <b><i>other </i></b>book"! I do not like that. If it's relevant to this book's topic, you should cover it within this book. Don't effective force people/try to sell some other book for one sub-topic that you're not willing to properly cover (again). Heck, you could have easily copy/pasted entire sections from other books you wrote, we wouldn't know!

Speaking of trying to sell some other books, this is a further point that I really disliked about this book series. If you go to the Apress site for this publication (linked above), you will see that you can buy the book for one price (which is fine), but further down the page, for approximately $5 less than the price of the <strong><em>whole</em> </strong>book, you can buy an individual chapter! Really?!? You are going to try to sell each individual chapter? If someone were to purchase each chapter individually, they would spend <strong>over 10x</strong> the amount compared to just purchasing the whole book itself!

&nbsp;

Originally, my interest was peaked that there was a book dedicated to each Azure DevOps feature, and thought it would provide real deep-level insights (after all, most other Azure DevOps books cover all the features in a single book). But after reading this one, I doubt that I will read any others within this series.

Here are my highlights by chapter.
<h2>Chapter 1: Understanding the Importance of Software Delivery Automation</h2>
<ul>
 	<li>This requires an organization to adopt a collaborative culture where automation is a key belief.</li>
 	<li>People are the most important aspect of DevOps. People need to adapt practices and processes that help them to collaborate and contribute to the teamâ€™s goals and create a culture where automation plays a significant role in delivering value to software users.</li>
 	<li>To ensure the stability of the code base, two factors can be used. The first one is making sure the code compiles without errors. The second factor is making sure all unit tests are passed, with the latest code changes and code coverage of unit tests being at a very high percentage.</li>
 	<li>In addition to the unit tests, validation for code security vulnerabilities can be integrated into the build pipelines to improve the security aspects of a project/product.</li>
 	<li>In a nutshell, CD is delivering software changes more frequently and reliably, and DevOps can be considered a product of continuous delivery.</li>
 	<li>Continuous deployment lets every change be automatically deployed to production. To implement continuous deployment, one must have continuous delivery in place, since continuous deployment is created by automating the approval steps of continuous delivery.</li>
</ul>
<h2>Chapter 2: Overview of Azure Pipelines</h2>
<ul>
 	<li>There are two types of agent pools:
<ul>
 	<li>Azure Pipelines: Microsoft-hosted agent pool containing machines with all platforms, Windows, Linux, and MacOS with many software tools installed in them.</li>
 	<li>Private /self-hosted Agent Pools: A default private pool is available and you can create more private agent pools as per your requirements. Then you can register machines in these private pools to be used as build or deployment machines.</li>
</ul>
</li>
 	<li>Public projects let you use ten parallel executions on hosted pipelines at a time while private projects (where your source code or other project details are hidden from public access) only let you use one execution of a build or deployment at a given time.</li>
 	<li>Deployment groups are also similar to agent pools. A deployment group is a set of machines set up with agents. The specialty of the deployment group is that each machine is an actual deployment target dedicated to each deployment environment with a role.</li>
 	<li>Azure DevOps build pipelines can be used to build your source code to identify issues with the code early by using a continuous integration option. You can build, test, and create deployable packages of your code using Azure DevOps build pipelines.</li>
 	<li>Azure DevOps supports two types of builds: namely, classic builds and YAML Ain't Markup Language (YAML) builds. Classic editor allows you to use a graphical view and create build pipelines according to your requirements. But when it comes to a YAML build, you need to have a good understanding of YAML syntax to write declarative scripts to define the build pipelines as a code.</li>
 	<li>In build pipelines, there are agent phases that allow you to group agents' tasks under each phase. Azure DevOps has two phases:
<ul>
 	<li>Agent phase - It is connected with the agent in the agent pool and uses the agent pool agent to execute the tasks.</li>
 	<li>Agentless phase - It doesn't have the capability to connect with an agent in an agent pool. All the tasks under this phase will execute in Azure DevOps server itself.</li>
</ul>
</li>
 	<li>The Azure DevOps pipeline has an artifacts section and stage section. The artifact is the starting point of a release pipeline and can be used for setting up a continuous deployment trigger. It is required to add a type of artifact to enable the deployment. The artifact section allows you to select different types of artifacts such as build output, a package from artifact feed, and third-party artifacts like Jenkins.</li>
 	<li>In pre-deployment conditions, Azure DevOps has three main triggers:
<ul>
 	<li>Manual trigger, start deployment after creating a new release, and trigger the deployment of the given stage if the deployment of the previous stages of pipeline have succeeded.</li>
</ul>
</li>
 	<li>Gates allow you to set various conditions based on Azure functions, REST API, work items queries, and several other gates.</li>
 	<li>Azure DevOps provides us with a task group feature where we can create a group of tasks that can be used in multiple pipelines and send parameter values relevant to each pipeline.</li>
 	<li>The Azure DevOps Environment represents a collection of resources that can be targeted by deployment pipelines.</li>
 	<li>Azure DevOps provides multiple parallel job execution capabilities to public projects.</li>
 	<li>If you create a self-hosted agent for a public project, it has unlimited parallel jobs.</li>
 	<li>If the project was created as a private project, the Microsoft-hosted agent provides 1,800 mins for month.</li>
 	<li>When it comes to self-hosted agents, it also has one parallel job. But if the organization has Visual Studio Enterprise subscriptions, one parallel job is added to the self-hosted agent.</li>
 	<li>It provides the Microsoft-hosted agent one parallel job and the self-hosted agent one parallel job for free. Boards and Repo are free for up to five users. Also, it provides up to 2GB artifact storage for free.</li>
</ul>
<h2>Chapter 3: Setting Up Pools, Deployment Groups, and Agents</h2>
<ul>
 	<li>The major advantage of having a self-hosted agent would be to facilitate a couple of needs that we would not be able to satisfy with Azure-hosted Pipelines. One such need is having custom versions of software requirements to build your software projects.</li>
 	<li>Another good use of self-hosted (on-premises could be even cloud VMs) agents would be when you try to deploy to on-premises environments where the machines sit behind cooperate firewalls.</li>
 	<li>Pools can be defined on two levels. First, you can define a pool at the Azure DevOps organization and have it added to all existing team projects.</li>
 	<li>You can only add the pool to existing projects at the time of the creation of the pool (see Figure 3-3) or by going to an individual team project and adding the</li>
 	<li>existing pool.</li>
 	<li>The PAT needs to have the Agent pool Manage and Read scope defined.</li>
 	<li>Instead of a PAT, you can use negotiate or alt as an authentication option and provide the username and password to register the agent, or use an integrated authentication type to use logged-on windows credentials.</li>
 	<li>The credential you use only needs to set up the agent and it would not be the credentials used to maintain the connectivity of the agent to Azure DevOps. Hence, it is not required for you to keep a PAT or other credentials active after setting up an agent as the agent and Azure DevOps communicate using a different secret token setup at the time of setting up the agent, which is not visible to you.</li>
 	<li>Running an agent as a service is advisable as long as it doesn't need to perform any interactive activity.</li>
</ul>
<h2>Chapter 4: Creating Build Pipelines-Classic-Source Control, Templates, Jobs, and Tasks</h2>
<ul>
 	<li>The main purposes of the build pipeline are building source code, executing unit tests, and publishing and packaging the built source code as deployable artifacts.</li>
 	<li>Agent job a.k.a. agent phase is where you can define the build agent that is used to execute the tasks under a build pipeline. Also, the agent job/phase can be used to define some configuration that is relevant to all the tasks under that agent phase.</li>
 	<li>We can manually add steps/tasks to build pipelines to perform actions inside an agent job.</li>
</ul>
<h2>Chapter 5: Creating Build Pipelines – Classic – Variables, Triggers, Filters, Options, and Retaining</h2>
<ul>
 	<li>You can use system variables as well as custom variables in any pipeline task by using the syntax of $(variableName).</li>
 	<li>System.debug is a variable that is useful to set at the queue time, as it allows you to decide to run the current build you are queueing in the debug mode emitting more diagnostic log details.</li>
 	<li>Build pipelines can be triggered manually. However, it is important to have different trigger options for builds.</li>
 	<li>The exclude allows the path to be ignored so that a push to that path alone would not trigger the build pipeline.</li>
 	<li>The simplest way to format a build number is by setting the build number format in the options tab in a given build pipeline definition. You can use predefined variables in the Build number format to create builds with the number format of your preference.</li>
 	<li>The $(Rev:rr) can be used to add a two-digit revision number as with a preceding zero when the revision is a single digit.</li>
 	<li>The build number can be referred in any script or task in the Azure Pipeline with a predefined variable $(Build.BuildNumber).</li>
 	<li>This option Paused is useful when you want to commit/push changes to a source code repo that could trigger multiple builds, but you want to get another build executed as priority.</li>
 	<li>A build job timeout specifies the maximum number of minutes that build steps can be executed in a given agent before cancelling it.</li>
 	<li>If you make a cancel request on a build job, the time in minutes that the job will wait before the server terminates the job if the cancel has not occurred, is determined by the build job cancellation timeout.</li>
 	<li>It is possible to revert back a pipeline to a given history point, which would be really useful while doing maintenance or upgrade work on a build pipeline.</li>
 	<li>Even if the time limit exceeds to retain builds, the "number of recent runs to keep" value will decide, how many of last runs of builds will be kept available or retained, regardless of the number of days specification.</li>
</ul>
<h2>Chapter 6: Creating Build Pipelines –Classic-Queuing, Debugging, Task Groups, Artifacts, and Import/Export Options</h2>
<ul>
 	<li>But for secret variables, as the agent does not create environment variables in it, we cannot access the secret variables with the $env:variable format. The only possible way to access secret variables in PowerShell would be with a $(variablename) format.</li>
 	<li>Before executing any REST API call, it is necessary to use authentication mechanisms to allow the API to perform authorized operations.</li>
 	<li>In Azure DevOps, the Personal Access Token (PAT) is the most common way of providing authentication. But a OAuth configuration in the agent phase allows us to execute API calls without using a PAT as a parameter for authentication.</li>
 	<li>A task group is grouping a set of repetitive tasks and maintaining it as the shared component for multiple pipelines.</li>
 	<li>There are situations where you need to do some activities that do not require a machine to perform tasks such as waiting for an approval. For these waiting type of purposes, you can use agentless phases in build pipelines.</li>
 	<li>The most well-known, simple way of keeping artifacts is to save the published artifacts to the pipeline itself using the publish artifacts task.</li>
 	<li>Before we import the build pipeline json to another project, it is required to make a small change to the exported json file. Azure DevOps projects have unique ids for each team project. When you export the build pipeline, it contains the project id of the source team project in the json file. This project id is required to be replaced with the project id of the destination team project id.</li>
</ul>
<h2>Chapter 7: Using Artifacts</h2>
<ul>
 	<li>No highlights!</li>
</ul>
<h2>Chapter 8: Creating and Using YAML Build Pipelines</h2>
<ul>
 	<li>The most important benefit we get by using YAML pipelines is that the user can version control the build, which helps to track the changes made to the pipelines.</li>
 	<li>There is an auto-cancel Boolean option that is by default true, which will make an in-progress pull request build be cancelled automatically if there are more changes pushed to the same pull request.</li>
 	<li>You can define global variables that can be used in multiple jobs and stages. Also, you can define variables that can be used inside the specified job.</li>
 	<li>You can use the variables from the variable group in your pipeline tasks with two syntaxes: macro style and runtime expression style.</li>
 	<li>Jobs are used to define pipeline execution phases. A job can be defined with steps/tasks to perform required actions.</li>
 	<li>you can define other repos and check them out if required in your pipeline steps using a checkout task.</li>
 	<li>You can find a list of all available tasks in the link <a href="https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/?view=azure-devops" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/?view=azure-devops</a> and find out a YAML snippet for each of them.</li>
 	<li>There are four kinds of templates available in Azure YAML pipelines. Stage, Job, Step, and Variable</li>
</ul>
<h2>Chapter 9: Azure Release Pipelines – Service Connections, Templates, Artifacts, Stages, and Environments</h2>
<ul>
 	<li>An endpoint in a given resource should be authenticated, and a connection should be made to the endpoint as a service connection from Azure DevOps, in order to allow the pipelines to interact with the resource.</li>
 	<li>Pull request deployment enabling will allow the release based on pull requests to be deployed to the given stage; however, it is advisable to keep this disabled for production stages.</li>
 	<li>Gates let you invoke third-party calls and wait for desired outcomes before proceeding with a particular stage. In other words, gates are for performing a gatekeeper job before a given stage is deployed.</li>
 	<li>You have the option to set up a redeployment trigger when a deployment stage is failed, so that it deploys previous successful deployments of the current stage again to the stage.</li>
 	<li>A collection of resources that can be used as targets for deployments can be set up as an environment in Azure DevOps.</li>
 	<li>The environment can be added with checks, which is a bit similar to gates. The checks even include approver evaluation of artifacts as well.</li>
 	<li>YAML pipelines can use the environments as targets for deployment actions.</li>
</ul>
<h2>Chapter 10: Azure Release Pipelines – Jobs, Deployment Groups, Variables, and Other Options</h2>
<ul>
 	<li>You can set the Allow scripts to access the OAuth token in an agent phase so that any script task in an agent job can use the system access token to access a REST API of Azure DevOps.</li>
 	<li>There is no option to define dependencies as in build agent jobs, which are not required as execution happens in the sequence the jobs are set up in the release pipeline.</li>
 	<li>A timeout and job cancellation timeout settings that you can use to determine how much time a job can be executed before timing out and how much time is allowed to complete the job once a cancellation request is made before terminating, respectively.</li>
 	<li>In agentless jobs, there are minimal sets of settings compared to the agent or deployment group jobs.</li>
 	<li>The run conditions allow you to define if the agentless phase should be executed based on previous step success or failure; or using a custom condition</li>
 	<li>Regardless of the number of days, the number of releases specified in the minimum number of releases to keep will be preserved.</li>
</ul>
<h2>Chapter 11: REST API, Command Line, and Extension Development</h2>
<ul>
 	<li>Programmatic access to the build and release pipelines is useful to generate reports, manipulate pipelines behavior, or even implement extensibility to pipelines.</li>
 	<li>If you want to copy over branch protection build policies in one version branch to another, there is no out-of-the-box way to do it. You have to manually create the branch protection build policies in a new branch. However, you may use REST API and implement a PowerShell script by getting the policies of one branch and applying it to another.</li>
 	<li>You have options to set up pipeline extensions with typescript based or PowerShell based ones. However, only windows agents are able to run PowerShell-based tasks. It is advisable to use typescript for developing pipeline extensions if you intend to run it on all agent platforms.</li>
</ul>
<h2>Chapter 12: Integrating Tests to Pipelines</h2>
<ul>
 	<li>Build pipelines can be used to execute unit tests written with many types of unit testing tools. The general practice is to build the code and then execute the unit tests and package the code as deployable binaries.</li>
 	<li>To publish tests results, you can use the Publish Test Results task and specify the result output file and the format of test results of the test execution so that it will be published to the pipeline.</li>
 	<li>Automation and running the automated functional tests with deployment pipelines enable teams to run most of their tests, for each release, so that higher quality in delivered applications can be achieved.</li>
</ul>
