---
layout: page
title: Book Review: Azure DevOps Explained - Get Started with Azure DevOps and Develop your DevOps Practices
date: 2020-11-23 08:08
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/11/AzureDevOps-BookCover.jpg"><img class="alignleft size-medium wp-image-33688" src="/wp-content/uploads/2020/11/AzureDevOps-BookCover-243x300.jpg" alt="" width="243" height="300" /></a>Recently, I finished reading <a href="https://www.packtpub.com/product/azure-devops-explained/9781800563513" target="_blank" rel="noopener noreferrer">Azure DevOps Explained: Get started with Azure DevOps and develop your DevOps practices</a> by Sjoukje Zaal, Stefano Demiliani, and Amit Malik.

I already have experience with Azure DevOps, pipelines, repos, etc. But what I appreciated about this book, is how simply it explained Azure DevOps features and concepts, without getting lost in the many different options/toggles that they could have talked about.

If you are new to Azure DevOps, I would absolutely recommend this book to help you get started.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

If my highlights peak your interest, I recommend that you pick up a copy for yourself.
<h2>Chapter 01: Azure DevOps Overview</h2>
<ul>
 	<li>Six DevOps principles that we think are essential when adopting a DevOps:
<ul>
 	<li>Principle 1 – Customer-centric action</li>
 	<li>Principle 2 – Create with the end in mind</li>
 	<li>Principle 3 – End-to-end responsibility
<ul>
 	<li>By adopting a DevOps way of working, the DevOps teams become fully responsible and accountable for the project they deliver. This means that once the product has been delivered by the team and it needs to be maintained, it still remains under the responsibility of the team. The team will also provide support for the product until it reaches its end of life. This greatly increases the level of responsibility of the team and the quality of the products that are developed.</li>
</ul>
</li>
 	<li>Principle 4 – Cross-functional autonomous teams
<ul>
 	<li>Examples of skills that every team member should have include development, requirement analysis, testing, and administration skills.</li>
</ul>
</li>
 	<li>Principle 5 – Continuous improvement</li>
 	<li>Principle 6 – Automate everything
<ul>
 	<li>This means that not only the software development process should be automated using continuous delivery (which includes continuous development and integration), but also the whole infrastructure landscape needs to be automated. The infrastructure also needs to be ready for new ways of working.</li>
</ul>
</li>
</ul>
</li>
 	<li>CI is used in the development phase of a project and refers to building and testing code in a fully automated way.</li>
 	<li>With CD, the delivery phase is automated. Every time a build artifact is available, the artifact is automatically deployed to the desired environment.</li>
 	<li>With TFVC, developers have only one version of each file on their local dev machines. All the others, as well as the historical data, are maintained only on the server.</li>
 	<li>Azure Test Plans offer features for planned manual testing, exploratory testing, user acceptance testing, and for gathering feedback from stakeholders.</li>
 	<li>With Azure Artifacts, you can create and share NuGet, npm, Python, and Maven packages from private and public sources with teams in Azure DevOps.</li>
 	<li>ARM Outputs : This extension reads the output values of ARM deployments and sets them as Azure Pipelines variables. You can download and install the extension from <a href="https://marketplace.visualstudio.com/items?itemName=keesschollaart.arm-outputs" target="_blank" rel="noopener noreferrer">https://marketplace.visualstudio.com/items?itemName=keesschollaart.arm-outputs</a>.</li>
 	<li>Team Project Health : This extension enables users to visualize the overall health of builds, thereby delivering a visual cue similar to Codify Build Light. You can download the extension from <a href="https://marketplace.visualstudio.com/items?itemName=ms-devlabs.TeamProjectHealth" target="_blank" rel="noopener noreferrer">https://marketplace.visualstudio.com/items?itemName=ms-devlabs.TeamProjectHealth</a>.</li>
</ul>
<h2>Chapter 02: Managing Projects with Azure DevOps Boards</h2>
<ul>
 	<li>The process and the templates define the building blocks of the Work Item tracking system that is used in Azure Boards.</li>
 	<li>When your team follows a more formal project method that requires a framework for process improvement and an auditable record of decisions, the Capability Maturity Model Integration (CMMI) process is more suitable.</li>
 	<li>The Work Items that are available to you are based on the process that was chosen when the project was created.</li>
 	<li>You can link it to another Work Item using "#" followed by "the name of the Work Item", link a particular pull request using "!" followed by the "name of the pull request", or mention a person using "@" followed by the "name of the person".</li>
 	<li>Choosing a process: <a href="https://docs.microsoft.com/en-us/azure/devops/boards/work-items/guidance/choose-process" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/devops/boards/work-items/guidance/choose-process</a></li>
</ul>
<h2>Chapter 03: Source Control Management with Azure DevOps</h2>
<ul>
 	<li>There are three main branching strategies that you can adopt: GitHub Flow, GitLab Flow, Git Flow.
<ul>
 	<li>GitHub Flow
<ul>
 	<li>According to this workflow, you start from a master branch (which always contains the deployable code). When you start developing a new feature, you create a new branch and you commit regularly to this new branch. When the development work has been completed, you create a pull request to merge the secondary branch with the master branch.</li>
 	<li>The only disadvantages are that you need to carefully check what you commit to the master branch. This is not recommended if you need to have multiple versions of your application in production.</li>
</ul>
</li>
 	<li>GitLab Flow is another popular branching strategy that's widely used, especially when you need to support multiple environments (such as production, staging, development, and so on) in your SCM process.
<ul>
 	<li>According to this workflow, you should have at least three branches:
<ul>
 	<li>Master: This is everyone's local version of the code.</li>
 	<li>Staging: This is the branch where the master branch is branched into for testing purposes.</li>
 	<li>Production: This is the released production code (where staging is merged). This is useful if you want to maintain a stable production release, work separately on new features that can be moved to a testing environment (in order to be tested), and then merge that environment into the production release when testing has been completed.</li>
</ul>
</li>
</ul>
</li>
 	<li>Git Flow is a workflow that's used when you have a scheduled release cycle.
<ul>
 	<li>Every time you add a new feature to your code base, you create a feature branch, starting from the develop branch, and then you merge the feature branch into develop when the implementation is finished. Here, you never merge into the master branch.</li>
</ul>
</li>
</ul>
</li>
 	<li>When you start a new project from scratch, Azure DevOps creates an empty repository for you.</li>
 	<li>In a single project, you can create different repositories and each can have its own set of permissions, branches, and commits.</li>
 	<li>In order to work with remote repositories on Azure DevOps with Visual Studio Code more efficiently, I recommend that you install an extension (from the Visual Studio Code Marketplace) called Azure Repos.</li>
 	<li>Please remember that when importing a repository from GitHub, the history and revision information is also imported into Azure DevOps for complete traceability.</li>
 	<li>It's important to note that locking a branch does not prevent cloning or fetching this branch locally.</li>
 	<li>Branch policies in Azure DevOps permit you to do the following: Limit the contributors to a specific branch Specify who can create branches.</li>
 	<li>Specify a set of naming conventions for branches Automatically include code reviewers for every code change in the branch Enforce the use of pull requests Start a build pipeline before committing the code to the branch.</li>
 	<li>This option allows you to require the associations of work items to a specific pull request for the complete traceability of activities and tasks. This is useful if you're using the project planning features</li>
 	<li>If a pull request is marked as a draft, required reviewers are not automatically added, voting is not permitted, and build policies (if activated) are not automatically executed.</li>
 	<li>Git Tags are references that point to specific points in the Git history. Tags are used in Azure DevOps for marking a particular release (or branch) with an identifier that will be shared internally in your team to identify, for example, the "version" of your code base.</li>
</ul>
<h2>Chapter 04: Understanding Azure DevOps Pipelines</h2>
<ul>
 	<li>A pipeline is normally composed of one or more stages (logical separation of concerns in a pipeline, such as building, testing, deployment, and so on; they can run in parallel), and each stage contains one or more jobs (a set of steps that can also run in parallel).</li>
 	<li>When using a Microsoft-hosted agent, you need to remember the following: You cannot sign in on the agent machine. The agent runs on a Standard DS2v2 Azure Virtual Machine and you cannot increase that capacity. It runs as an administrator user on the Windows platform and as a passwordless sudo user on the Linux platform.</li>
 	<li>The Microsoft-hosted agent runs in the same Azure geography as your Azure DevOps organization, but it's not guaranteed that it will run in the same region too (an Azure geography contains one or more regions).</li>
 	<li>When running the agent (interactively or as a service), it's recommended to run it as a service if you want to automate builds.</li>
 	<li>Please be aware of the user account you select for running the agent. The default account is the built-in Network Service user, but this user normally doesn't have all the needed permissions on local folders. Using an administrator account can help you solve a lot of problems.</li>
 	<li>Remember that you can also install multiple agents on the same machine (for example, if you want the possibility to execute core pipelines or handle jobs in parallel), but this scenario is only recommended if the agents will not share resources.</li>
 	<li>Microsoft-hosted agents are normally useful when you have a standard code base and you don't need particular software or environment configuration to build your code.</li>
 	<li>Self-hosted agents are also the way to go when you need to preserve the environment between each run of your builds.</li>
 	<li>A self-hosted agent is normally the right choice when you need to have better control of your agent or you wish to deploy your build to on-premise environments (not accessible externally).</li>
 	<li>YAML uses three dashes, --- , to separate directives from document content and to identify the start of a document.</li>
 	<li><strong>Important Note:</strong> Enabling CI is a recommended practice if you want every piece of code that's committed on a branch (for example, on the master branch) to always be tested and safely controlled. In this way, you can be assured that the code is always working as expected.</li>
 	<li>The Retention tab, on the other hand, is used for configuring the retention policy for this specific pipeline (how many days to keep artifacts for, the number of days to keep runs and pull requests for, and so on).</li>
 	<li>When you run a pipeline, Azure DevOps logs each step's execution and stores the final artifacts and tests for each run.</li>
 	<li>Azure DevOps has a default retention policy for pipeline execution of 30 days.</li>
 	<li><strong>Important Note:</strong> Remember that any data saved as artifacts with the Publish Build Artifacts task is periodically deleted.</li>
 	<li>Stages are logical boundaries inside a pipeline flow (units of works that you can assign to an agent) that allow you to isolate the work, pause the pipeline, and execute checks or other actions. By default, every pipeline is composed of one stage, but you can create more than one and arrange those stages into a dependency graph.</li>
 	<li>To use Azure Pipelines to build your GitHub repository, you need to add the Azure DevOps extension to your GitHub account.</li>
 	<li>A badge is a dynamically generated image that reflects the status of a build (never built, success, or fail).</li>
 	<li>Within an Azure Pipeline, you can also execute jobs in parallel. Each job can be independent of other jobs and can also be executed on a different agent.</li>
 	<li>To run a job inside a Windows container, you need to use the windows-2019 image pool. It's required that the kernel version of the host and the container match.</li>
</ul>
<h2>Chapter 05: Running Quality Tests in a Build Pipeline</h2>
<ul>
 	<li>However, there is a trade-off. Developers need to dedicate more time to writing and maintaining test code. However, by investing this extra time, the outcome will be higher quality code, and code that has been proven to function completely as expected.</li>
 	<li>With unit testing, you break up code into small pieces, called units, that can be tested independently from each other. These units can consist of classes, methods, or single lines of code. The smaller the better works best here.</li>
 	<li>In most cases, unit tests are written by the developer that writes the code.</li>
 	<li>There are two different ways of writing unit tests: before you write the actual production code, or after. Most programmers write it afterwards, which is the traditional way of doing things, but if you are using test-driven development (TDD), you will typically write them beforehand.</li>
 	<li>Unit tests are usually stored inside an assembly.</li>
 	<li>The results directory will always be cleaned before the tests are run.</li>
 	<li>Code coverage testing measures how many lines, blocks, and classes are executed while automated tests, such as unit tests, are running.</li>
 	<li>However, there is a drawback to Feature Flags: they introduce more complexity in your code, so it is better to constrain the number of toggles in your application.</li>
 	<li>Unit test basics: <a href="https://docs.microsoft.com/en-us/visualstudio/test/unit-test-basics?view=vs-2019" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/visualstudio/test/unit-test-basics?view=vs-2019</a>.</li>
 	<li>Run quality tests in your build pipeline by using Azure Pipelines: <a href="https://docs.microsoft.com/en-us/learn/modules/run-quality-tests-build-pipeline/" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/learn/modules/run-quality-tests-build-pipeline/</a>.</li>
</ul>
<h2>Chapter 06: Hosting Your Own Azure Pipeline Agent</h2>
<ul>
 	<li>Each execution of a pipeline initiates a job on one of the agents, and one agent can only run one job at a time.</li>
 	<li><strong>Important Note:</strong> Azure Pipelines supports running basic tasks, such as invoking the REST API or Azure Function without the need to have any agents. Please refer to <a href="https://docs.microsoft.com/en-us/azure/devops/pipelines/process/phases?view=azure-devops&amp;tabs=yaml#server-jobs" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/devops/pipelines/process/phases?view=azure-devops&amp;tabs=yaml#server-jobs</a> for more details about agentless execution of Azure Pipelines.</li>
 	<li>Self-hosted agents would be the only option in the case of highly secure and customized build pipelines that interact with other services running in your network.</li>
 	<li>Important note You will need to give additional permissions when creating a token if you plan to use deployment groups (more information here: <a href="https://docs.microsoft.com/en-us/azure/devops/pipelines/release/deployment-groups/?view=azure-devops)" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/devops/pipelines/release/deployment-groups/?view=azure-devops)</a>.</li>
 	<li>You can run the Azure pipeline agent in two modes:
<ul>
 	<li>-- Run Once: This will run the agent manually using the run batch file stored in the agent directory. Your agent will stop responding to pipelines if you stop the interactive authentication.</li>
 	<li>-- Run as Service: In this version, you configure the agent to run as a Windows service that will remain online all the time and auto-start on reboot. This is the recommended setup for production scenarios.</li>
</ul>
</li>
 	<li><strong>Important Note:</strong> If your self-hosted agent machine is behind a network firewall or proxy, you must define the proxy address while installing the Azure pipeline agent.</li>
</ul>
<h2>Chapter 07: Using Artifacts with Azure DevOps</h2>
<ul>
 	<li>In Azure Artifacts, packages are stored in feeds. A feed is a container that allows you to group packages and control who has access to them.</li>
</ul>
<h2>Chapter 08: Deploying Applications with Azure DevOps</h2>
<ul>
 	<li>With continuous delivery , you deliver code to a certain environment for testing or quality control, while continuous deployment is the phase where you release code to a final production environment.</li>
 	<li>A release pipeline is normally connected to an artifact store (a deployable component for an application and output of a build).</li>
 	<li>In a release pipeline, an artifact is deployed to an environment (where your final application will run).</li>
 	<li>Artifacts are all the items (output of a build) that must be deployed in your final environment, and Azure Pipelines can deploy artifacts that come from different artifact sources.</li>
 	<li>In Azure Pipelines, a gate allows you to automatically check for specific conditions from Azure DevOps from external services and then enable the release process only when the conditions are met.</li>
 	<li>A deployment group is a set of machines with a deployment agent installed on each of them. Each deployment group represents a physical environment and it defines a logical group of target machines for parallel deployment.</li>
 	<li>Deployment groups can only be used on release pipelines.</li>
 	<li>Environments are a group of resources targeted by a pipeline – for example, Azure Web Apps, virtual machines, or Kubernetes clusters.</li>
</ul>
<h2>Chapter 09: Integrating Azure DevOps with GitHub</h2>
<ul>
 	<li>Azure DevOps provides various RBAC levels, native enterprise identity integration, and so on, whereas GitHub enables simple collaboration across identities (while including AD integration in its Enterprise version).</li>
</ul>
<h2>Chapter 10: Using Test Plans with Azure DevOps</h2>
<ul>
 	<li>With exploratory testing, testers are exploring the application to identify and document potential bugs. It focuses on discovery and relies on the guidance of the individual tester to discover defects that are not easily discovered using other types of tests. This type of testing is often referred to as ad hoc testing.</li>
 	<li>Test Plans offers three main types of test management artifacts: Test plans, Test suites, and Test cases.</li>
 	<li>These artifacts are all stored in the work repository as special types of work items and can be exported and shared with the different team members or across different teams.</li>
 	<li>The three artifacts have the following capabilities:
<ul>
 	<li>Test plans: A test plan groups different test suites, configurations, and individual test cases together. In general, every major milestone in a project should have its own test plan.</li>
 	<li>Test suites: A test suite can group different test cases into separate testing scenarios within a single test plan. This makes it easier to see which scenarios are complete.</li>
 	<li>Test cases: With test cases, you can validate individual parts of your code or app deployments. They can be added to both test plans and test suites. They can also be added to multiple test plans and suites if needed. This way, they can be reused effectively without the need to copy them. A test case is designed to validate a work item in Azure DevOps, such as a feature implementation or a bug fix.</li>
</ul>
</li>
 	<li>You can create three different types of test suites: static, where you manually assign the test cases; requirement-based, where you create the suite based on common requirements; and query-based, where test cases are automatically added based on the outcome of a query.</li>
</ul>
<h2>Chapter 11: Real-World CI/CD Scenarios with Azure DevOps</h2>
<ul>
 	<li>In a production environment, you may choose to do so using the SQL Server Data.</li>
 	<li>Tools project in Azure Pipelines. Please refer to this documentation to learn more about doing Azure DevOps for SQL: <a href="https://devblogs.microsoft.com/azure-sql/devops-for-azure-sql/" target="_blank" rel="noopener noreferrer">https://devblogs.microsoft.com/azure-sql/devops-for-azure-sql/</a>.</li>
</ul>
