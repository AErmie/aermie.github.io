---
layout: page
title: Book Review: Using Chef with Microsoft Azure
date: 2018-10-03 10:03
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2018/10/Using-Chef-With-Microsoft-Azure-BookCover.jpg"><img class="alignleft size-medium wp-image-31668" src="/wp-content/uploads/2018/10/Using-Chef-With-Microsoft-Azure-BookCover-210x300.jpg" alt="" width="210" height="300" /></a>Recently, I finished reading the <a href="https://www.apress.com/gp/book/9781484214770" target="_blank" rel="noopener">Using Chef with Microsoft Azure</a> book by Stuart Preston.

When I started reading this book, I had no experience with Chef (but a high-level understanding of its use case) and a lot of experience with Azure. And so, I was looking for a book that would provide a good foundation around Chef specific to Azure (as a lot of the resources out there are focused on AWS).

I particularly found chapter 6 <strong>("Integrating Quality Tooling into the Chef Development Life Cycle”)</strong> and chapter 7 <strong>("Chef Concepts in the Real World")</strong>, of most value, because it focused on not just using Chef, but quality/standards testing, and real-world examples that are relatable.

Although this book was published a few years ago (which means some of the material may be dated), it was still a good reference. It would be nice if there was an updated v2 release of the publication, but of course, we have the learning materials available on <a href="https://learn.chef.io/" target="_blank" rel="noopener">https://learn.chef.io/</a>.

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 1: Configuration Management using Chef</h2>
<ul>
 	<li>Simply put, a cookbook is made up from a collection of recipes, which in turn are an ordered set of instructions you would like to perform on a node (a node being defined as any server or device capable of running a Chef client).</li>
 	<li>Recipes themselves are written in the Chef domain specific language (DSL) built on top of the Ruby language.</li>
 	<li>Along with recipes and resources, a cookbook contains all the files and configuration templates required, as well as supporting artifacts such as any data that is used by the component being deployed. It also contains unit tests that can be used to ensure we have written our recipes correctly</li>
 	<li>Chef Server distributes cookbooks to the nodes based on their configuration. So on your nodes, you need to install the Chef Client and configure it so that it can connect to the server and retrieve the cookbooks. This installation process is commonly referred to as ‘bootstrapping’</li>
 	<li>Before we can start developing our recipes, we need to initialize our environment. Put simply this means ensuring that Chef and Ruby paths and environment variables are correctly pointing at the location ChefDK installed them to</li>
 	<li>When given the option to adjust your PATH environment you should select the option to Use Git from the Windows Command Prompt to ensure Git is available to all processes on the system</li>
 	<li>When asked to configure the terminal emulator to use with Git Bash, select Use Windows’ default console window as shown in Figure 1-11 as this is most compatible with the command-line tools used in Chef development</li>
 	<li><strong>Tip </strong>If you would like to learn more about Git basics, there’s a great reference available online at <a href="http://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository" target="_blank" rel="noopener">http://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository</a></li>
 	<li><strong>Tip </strong>The Ruby language style guide encourages the use of two spaces per indentation level. Many editors have 4 spaces or a Tab as the default setting. This can usually be changed in your code editor’s settings. For further discussion see <a href="https://github.com/bbatsov/ruby-style-guide#source-code-layout" target="_blank" rel="noopener">https://github.com/bbatsov/ruby-style-guide#source-code-layout</a></li>
 	<li><strong>Tip</strong> I recommend creating an Organization with the name &lt;CompanyName&gt;-&lt;OrganizationName&gt; as this is a shared service and Organizations are named on a first-come-first-served basis</li>
 	<li><strong>Note </strong>Do not download the starter kit more than once as this will reset your access to this Chef organization!</li>
 	<li><strong>Warning </strong>Be sure not to check the .chef folder into source control, especially not a publicly hosted Git solution such as GitHub</li>
</ul>
<h2>Chapter 2: Microsoft Azure Terminology and Concepts</h2>
<ul>
 	<li>NONE</li>
 	<li>Note: I skipped this chapter, as I am already familiar with Azure terminology and concepts. If you're not, I would recommend reading this chapter</li>
</ul>
<h2>Chapter 3: Chef Azure VM Extensions</h2>
<ul>
 	<li><strong>Note </strong>VM extensions can technically be added to any compute (VM) resource including those servicing PaaS roles (such as web and worker processes</li>
 	<li>Chef worked with Microsoft to build and certify the Chef VM Extension as a more efficient way of enabling the Chef client on a machine</li>
 	<li>To bootstrap a VM with a Chef client in Azure the following requirements must be met:
<ul>
 	<li>The target machine must have WinRM (Windows) or SSH (Linux) protocol enabled
and configured to be listening.</li>
 	<li>You must be able to route to the machine directly, either over the Internet, VPN, or
ExpressRoute.</li>
 	<li>Firewalls must be opened to allow connections to the target machine from your
client on ports TCP/5985-5986 (WinRM) or port TCP/22 (SSH).</li>
 	<li>The target machine must have access to the Chef Server via HTTPS.</li>
</ul>
</li>
 	<li>The Azure VM Extension is deployed as a resource, so the prerequisites to use the extension are much simpler:
<ul>
 	<li>The target machine only requires outbound network connectivity via an Internet
gateway to retrieve the installer files (enabled by default).</li>
 	<li>The target machine must have access to the Chef Server via HTTPS</li>
</ul>
</li>
 	<li>When specifying the version in an ARM template, we need to specify only the Major and Minor versions in the template (e.g., 1210.12).</li>
</ul>
<h2>Chapter 4: Using Chef Provisioning to Provision Machines</h2>
<ul>
 	<li>The primary advantage a Service Principal has over using a standard User object in Azure Active Directory is that a Service Principal is not subject to any restrictions when multifactor authentication is enabled.</li>
 	<li><strong>Note </strong>~ (tilde) is an alias in most shells (including PowerShell) for the user’s home directory. This is the equivalent of using $env:USERPROFILE in Windows PowerShell or $HOME in OS X or a Unix shell :create is the default action so does not need to be specified in the recipe</li>
 	<li>Chef Client lets us specify the items that should be in the runlist itself using the -r or -o options. The -r option will persist the run-list to the server so that it would run next time whereas the -o option simply overrides the run-list for that run.</li>
 	<li>A good library of predefined templates is available at <a href="https://github.com/Azure/azure-quickstart-templates" target="_blank" rel="noopener">https://github.com/Azure/azure-quickstart-templates</a></li>
</ul>
<h2>Chapter 5: Advanced Chef Provisioning Techniques</h2>
<ul>
 	<li>None</li>
 	<li>Note: I did not have any highlights from this chapter, as it mostly contained PowerShell and CLI command lines and ARM template code</li>
</ul>
<h2>Chapter 6: Integrating Quality Tooling into the Chef Development Life Cycle</h2>
<ul>
 	<li>Linting is the process of checking the source code for problems before execution. Two tools have emerged as the most popular in this area: Rubocop and FoodCritic. Rubocop is a static code analyzer that focuses on Ruby code style errors, FoodCritic focuses on common errors in Chef recipes</li>
 	<li>It takes just a few seconds to run Rubocop and FoodCritic, so there’s no reason not to run both regularly against your cookbooks as part of your development process</li>
 	<li>We can use Rubocop to do the following:
<ul>
 	<li>Enforce style conventions and best practices</li>
 	<li>Evaluate the code in a cookbook against metrics such as “line length” and “function size”</li>
 	<li>Help every member of a team to author similarly structured code</li>
 	<li>Establish uniformity of source code</li>
 	<li>Set expectations for fellow (and future) project contributors</li>
</ul>
</li>
 	<li>Each rule in Rubocop may be enabled and disabled, either at a global level by configuring a .rubocop.yml file at the root of your project or by adding special comments to each Ruby file that exclude offenses from being counted</li>
 	<li>While there are some Rubocop violations that have multiple possible fixes, Rubocop does a good job of correcting code automatically by simply typing rubocop -a. Autocorrect works best when there is only one solution to the problem; otherwise, it will leave the offense alone</li>
 	<li>If you have a legitimate reason to suppress an offense there are a few ways to accomplish this:
<ul>
 	<li>1. You may generate a .rubocop_todo.yml file from your failing tests, with the
intent of fixing them later.</li>
 	<li>2. You may add blanket exclusions to your .rubocop.yml file.</li>
 	<li>3. You may add per-line exclusions as a comment in each file.</li>
 	<li>4. You may exclude sections of files.</li>
 	<li>5. You may exclude entire files.</li>
</ul>
</li>
 	<li>Generate a rubocop-todo.yml file by using rubocop --auto-gen-config</li>
 	<li>To take on the new configuration, you can either specify rubocop -c .rubocop_todo.yml from the command line, or (the preferred approach) is to create a new file called .rubocop.yml and insert the following line: inherit_from: .rubocop_todo.yml</li>
 	<li>You would place rules you wanted to suppress permanently for the whole team in the .rubocop.yml file and rules that you eventually want to fix in the .rubocop_todo.yml file</li>
 	<li>We can use the -D parameter to see the full cop name, which we’ll need to use to specify our exclusion.</li>
 	<li>A per-section Rubocop suppression is achieved by surrounding the code with a comment to disable and then enable the rule</li>
 	<li>FoodCritic is a static code analyzer that checks for what it considers to be poor cookbook authoring practices when using the Chef language</li>
 	<li>It can also flag problems that would cause your Chef Client run to fail.</li>
 	<li>There are currently 58 default FoodCritic rules that are executed against the specified cookbooks. A complete list can be generated by using the command foodcritic -l</li>
 	<li>Each FoodCritic rule is documented at <a href="http://foodcritic.io" target="_blank" rel="noopener">http://foodcritic.io</a></li>
 	<li><strong>Note </strong>On a Windows machine, the path to the cookbook must be passed in with forward slashes (e.g.,cookbooks/chefazure-ch06) rather than backslashes (e.g., cookbooks\chefazure-ch06).</li>
 	<li>Rules in FoodCritic are identified by a tag, which takes the format FC + number: for example, FC001. To exclude rules with specific tags, the -t option is used with a ~ in front of the tag name</li>
 	<li>To exclude rules for all users of a repo, we can create a .foodcritic file at the root of the specific cookbook, containing a list of the rules we want to exclude</li>
 	<li>FoodCritic has a number of additional options that can be seen by typing foodcritic -h</li>
 	<li>Cookbook Testing with Chef generally falls into two areas: Unit Testing and Acceptance Testing. From a Unit Testing perspective, we’re interested in testing individual units of code, independently of other circumstances in the system, such as the state of the environment</li>
 	<li>From an Acceptance Testing perspective, we’re interested in testing that once we apply our code to an environment, the described target state is reached</li>
 	<li>The Chef ecosystem has a great Unit Testing tool called ChefSpec, which is a set of extensions on top of the popular behavior-driven development (BDD) testing framework RSpec, and a great tool for Acceptance Testing called Test Kitchen that is a complete framework that allows you to test your cookbooks against multiple platforms</li>
 	<li>ChefSpec is a framework that simulates a Chef Client run and allows you to test resources and recipes without any other external dependencies</li>
 	<li>ChefSpec tests are typically placed early in a CI system’s pipeline after static analysis and are typically the first indicator of problems that may exist within a cookbook</li>
 	<li>ChefSpec is based on a behavior-driven development (BDD) framework called RSpec that uses a natural language domain-specific language (DSL) to describe scenarios in which systems are being tested. RSpec allows a scenario to be set up, then executed with dummy parameters. The results are then compared to a predefined set of expectations</li>
 	<li>Cookbooks by default have a default set of ChefSpec tests created. They can be found under &lt;cookbook&gt;/spec/unit/recipes. Test ‘specifications’ by convention are named _spec.rb so that tools can find them by this pattern.</li>
 	<li>ChefSpec tests are executed from the cookbook directory and not the root of the repo.</li>
 	<li><strong>Tip </strong>Use the -f documentation flag to get a list of the tests that are executed, also if your terminal supports it you can add the --color flag to get results in color</li>
 	<li>The statement require 'spec_helper' means that this file is including some statements from the common file spec/spec_helper.rb . All of the spec files will require this statement at the top of the file otherwise ChefSpec will not get loaded correctly</li>
 	<li>What we are trying to do with ChefSpec test is provide tests that cover each scenario you are writing recipes for, so that we can write the minimum recipe code that satisfies the test and eventually allows safe refactoring of the recipe code</li>
 	<li>This style of test-first development is a commonly accepted practice in the development world. We, first of all, write our test, see it fail, write the minimum amount of code to satisfy the test, and then refactor our solution, maintaining test success all the while.</li>
 	<li>ChefSpec offers a crude code coverage mechanism to let you know which resources have been touched by your tests as a percentage. To enable it, simply add the following line to your spec_helper.rb file (found in your cookbook within the spec folder): at_exit { ChefSpec::Coverage.report! }</li>
 	<li>Test Kitchen in the context of Chef makes it easy to add Acceptance Tests to our infrastructure code because we can spin up a brand new machine, execute our recipes, and then run tests to ensure the system is in the desired state after execution</li>
 	<li>There are four primary stages of the Test Kitchen workflow: create, converge, verify, and destroy</li>
 	<li>Test Kitchen is driven from a single, declarative configuration file called .kitchen.yml that resides in the root of your repo</li>
 	<li><strong>Tip </strong>If you do not have a .kitchen.yml file in your repo, one can be created automatically by typing kitchen in the location you want one init</li>
 	<li>We can see our default configuration file has four mains sections
<ul>
 	<li><strong>Driver</strong> - in this section we provide the name of the driver to be used</li>
 	<li><strong>Provisioner</strong> - the provisioner is used to specifying what action should be taken when we ’converge’ our machine. We want to use the chef_zero provisioner, which
provides the capability to transfer and execute recipes from our cookbook(s) within
the machine itself</li>
 	<li><strong>Platforms</strong> - a list of platforms can be provided here. Test Kitchen builds a test matrix
based on a combination of platforms and suites</li>
 	<li><strong>Suites</strong> - a suite is where we provide a run list containing the list of Chef recipes we
wish to execute in order. We can also override any attributes that are settable within
those recipes</li>
</ul>
</li>
 	<li>The image_urn parameter is a four-part string in the format Publisher:Offer:Sku:Version that uniquely identifies an image in Azure</li>
 	<li>Converging an instance simply means bringing the machine toward the desired state so that it can be ready for testing. We have specified the chef_zero provisioner in our configuration file (it’s the default), which means that when we execute kitchen converge the following things will happen:
<ul>
 	<li>The repository and any cookbooks specified as a dependency are transferred to the
target machine using the specified transport (WinRM in our case).</li>
 	<li>If not installed already, a Chef Client will be downloaded and installed on the
machine.</li>
 	<li>Chef Client will execute the specified recipes on the machine</li>
</ul>
</li>
 	<li><strong>Note </strong>Each time you run kitchen converge with an updated recipe or suite of recipes you run the risk of changing the state of the machine to an unexpected starting position for the next run. It is always wise to destroy your machines regularly to ensure your recipes can run end to end.</li>
 	<li>InSpec is a recently released testing framework, similar to ChefSpec in that it uses BDD-like language constructs in the test specifications. However, InSpec does no simulation of the Chef Client run; instead, it tests the actual running state of the machine. This makes InSpec tests a powerful tool for post-convergence automated testing, as we can use it to ensure that each action specified in our recipe has brought the machine to the correct target state</li>
 	<li>A full list of Resources and Matches are available at <a href="https://docs.chef.io/inspec_reference.html" target="_blank" rel="noopener">https://docs.chef.io/inspec_reference.html</a>.</li>
 	<li>There are a couple of other commands that are useful to know about:
<ul>
 	<li>You can run kitchen test in order to execute all phases of Test Kitchen in order
without stopping.</li>
 	<li>You can run kitchen diagnose --all in order to diagnose problems with
configuration (note: most issues are caused by formatting issues in the .yml file.)</li>
 	<li>Finally, instead of running through each test suite and platform sequentially, these
can be executed in parallel by running kitchen &lt;command&gt; --concurrency &lt;n&gt;
where n is the number of threads you wish to start.</li>
</ul>
</li>
</ul>
<h2>Chapter 7: Chef Concepts in the Real World</h2>
<ul>
 	<li>Version constraints cannot be applied to the _default environment</li>
 	<li>If we cannot version a cookbook, it means that every time we upload a cookbook to the Chef server, the latest version of the cookbook will always be used in the Chef run. For this reason, where possible move your nodes to a specific environment at the earliest opportunity</li>
 	<li>It sounds simple, but having a set of Chef environments that match your application lifecycle usually makes the most sense. If you run your code through development and test before you reach production, you should have Chef environments to match</li>
 	<li>Environments are specified via an environment.json file that is added to your repo. The environments file is usually stored in the environments folder within a Chef repository; however, it does not take effect when you upload a cookbook. We must use the knife environment command to upload a new environment definition</li>
 	<li>There are three sections after the name and description field that are self-explanatory
<ul>
 	<li>1. <strong>cookbook_versions</strong> - in this section we can provide the specific list of cookbook
versions to “pin” for this environment. Any cookbooks that do not appear in the
list are essentially “unpinned” (i.e., the latest version will always be used).</li>
 	<li>2. <strong>default_attributes</strong> - environment default attributes take precedence over the recipe or attribute file-defined attributes. This means that putting attributes here gives us a mechanism to define attributes such as the name of a database server where you have one per environment.</li>
 	<li>3. <strong>override_attributes</strong> - if you have a default attribute defined, and a role that
overrides it with its own default attribute, you can use this section to define an
override_attribute. Essentially this attribute will override all recipe/cookbook/
role-defined default attributes. Useful when you need to enforce an attribute in a
particular environment.</li>
</ul>
</li>
 	<li>As we know, all nodes within Chef are assigned the default environment if one isn’t specified; this can be changed from either the server or the client, at the command line, or by modifying the client.rb file.</li>
 	<li><strong>Note </strong>You may also create environments using the management portal but this is not recommended as it is a manual, non-repeatable action, and doesn’t lend itself to good continuous delivery practices</li>
 	<li>Remembering that each node that runs Chef Client uses a configuration file client.rb, we can specify the environment in the client.rb and this has the effect of overriding the server-assigned environment for that run (and storing that value for future runs or for searches against the Chef server). We can also use the knife command or the Chef management portal in order to achieve this</li>
 	<li><strong>Tip </strong>If you are interested in managing your Chef Client configuration, have a look at the chef-client cookbook, available on the Chef Supermarket at <a href="https://supermarket.chef.io/cookbooks/chef-client" target="_blank" rel="noopener">https://supermarket.chef.io/cookbooks/chef-client</a></li>
 	<li>Remember that cookbooks can be versioned, and roles cannot. This means it is a bad practice to modify roles once deployed to a node, as any change to a role’s run list impacts all environments simultaneously. That would not be a controlled release process! So how we get around this? By sticking to the following principles during cookbook development:
<ul>
 	<li>1. No nesting of roles. Each role should refer to one or more “capability” recipes
that are provided by an application cookbook</li>
 	<li>2. Application cookbooks should include and manage the dependencies for that
application (remembering that dependencies are specified in the application
cookbook’s metadata.rb file).</li>
 	<li>3. Default attributes for each environment (e.g., the location of the database server in that environment) should be specified in the environment JSON file.</li>
 	<li>4. Default Role attributes should be avoided (as they override default environment
attributes that are unlikely to be desirable).</li>
 	<li>5. Each node should be assigned the relevant roles that exist within the
environment JSON file.</li>
</ul>
</li>
 	<li>The running version in each environment is now a composite of the application cookbook
version, combined with the attributes and version constraints from the environment cookbook.</li>
 	<li>There are 15 levels of attribute precedence that go from a default attribute in a cookbook through to a forced overridden attribute set at an environment level</li>
 	<li>When using the environment pattern we are generally interested in setting default attributes:
<ul>
 	<li>1.<strong> Attribute files</strong> (application cookbook) - here we are setting the default attributes
for our application, generally pointing them at Dev values (just in case they are
accidentally pushed to a Production environment).</li>
 	<li>2. <strong>Environment attributes</strong> (environment cookbook) - here we are setting the
default attributes for an environment. Conveniently these override those set in
an attribute file so we can use this mechanism to set environmental attributes
(such as the connection string to the database in each environment).</li>
 	<li>3. <strong>Roles</strong> - Generally the use of role attributes is not a good practice as they override
default Environment attributes. However, they can be a useful tool depending
on your implementation scenario. Just remember that if you want to use
Environment attributes over Role attributes in this scenario you’ll have to mark
the environment attribute as an override_attribute.</li>
</ul>
</li>
 	<li>Semantic versioning is a standard for versioning, created in the community that brings a common understanding to version numbering. Full details can be found at <a href="http://semver.org/spec/v2.0.0.html" target="_blank" rel="noopener">http://semver.org/spec/v2.0.0.html</a>.</li>
 	<li>The premise of Semantic versioning is simple; given a version number Major.Minor.Patch, increment the following:
<ul>
 	<li>Major version when you make incompatible API changes,</li>
 	<li>Minor version when you add functionality in a backward-compatible manner, and</li>
 	<li>Patch version when you make backward-compatible bug fixes</li>
</ul>
</li>
</ul>
<h2>Chapter 8: Pulling It All Together: Continuous Provisioning with Chef and Azure</h2>
<ul>
 	<li>Berkshelf takes the heavy lifting out of managing community cookbooks. It downloads the cookbooks to a location outside your repo on your local disk, ready for upload to the Chef server. Newer versions of dependencies can be downloaded by the tool automatically and it is also supported by most of the testing tools out there, including RSpec and Test Kitchen.</li>
 	<li><strong>Note</strong> More information about Berkshelf can be found at <a href="http://berkshelf.com" target="_blank" rel="noopener">http://berkshelf.com</a></li>
 	<li>The Berksfile lives in the cookbook folder, rather than the root of the repo</li>
 	<li><strong>Note </strong>Should be executed from the cookbook folder rather than the root of the repo
berks install</li>
</ul>
