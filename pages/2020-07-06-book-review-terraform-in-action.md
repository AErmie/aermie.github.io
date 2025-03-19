---
layout: page
title: Book Review: Terraform in Action
date: 2020-07-06 09:17
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/07/TerraformInAction_BookCover.png"><img class="alignleft size-medium wp-image-33422" src="/wp-content/uploads/2020/07/TerraformInAction_BookCover-239x300.png" alt="" width="239" height="300" /></a>Recently, I finished reading <a href="https://www.manning.com/books/terraform-in-action" target="_blank" rel="noopener noreferrer">Terraform in Action</a> by Scott Winkler.

For those that know me, I already have a decent amount of hands-on and real-world experience with Terraform, and even deliver presentations/training on it.

But when I saw this publication, it caught my attention for the following reasons:
<ul>
 	<li>It offered advanced designs, such as zero-downtime deployments and creating your own Terraform provider</li>
 	<li>It included advanced templating techniques</li>
 	<li>Module planning/structure, and</li>
 	<li>Advanced Terraform state concepts</li>
</ul>
I particularly found<span style="color: #000000;"> the whole book helpful but in particular Chapter 4 ("<strong>Deploying a Multi-Tiered Web Application in AWS</strong>"), and Chapter 9 ("<strong>Zero Downtime Deployments</strong>").</span>

<span style="color: #000000;">I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).</span>
<h2>Chapter 1: Getting Started with Terraform</h2>
<ul>
 	<li>The main use case of Terraform is to deploy ephemeral, on-demand infrastructure in a predictable and repeatable fashion.</li>
 	<li>Configuration management (CM) tools, like Chef, Puppet, Ansible and SaltStack, were all designed to install and manage software on existing servers. They work by performing push or pull updates and restoring software to a desired state if drift has occurred.</li>
 	<li>CM tools favor mutable infrastructure, whereas Terraform and other provisioning tools, favor immutable infrastructure.</li>
 	<li>HCL attempts to strike a balance between human and machine readability and was influenced by earlier field attempts such as libucl and Nginx configuration.</li>
 	<li>HashiCorp has repeatedly stated that they do not have any intentions to offer a premium version of Terraform, now or ever. Instead they plan to make money by offering specialized tooling that makes it easier to run Terraform in high-scale, multi-tenant environments.</li>
 	<li>The difference between declarative and imperative programming is the difference between getting in a car and driving yourself from point A to point B, vs. calling an Uber and having your chauffeur drive you.</li>
 	<li><strong>Note:</strong> Declarative programming cares about the destination, not the journey. Imperative programming cares about the journey, not the destination</li>
 	<li>The way Terraform integrates with all the different clouds is through providers. Providers are plugins for Terraform that are designed to interface with external APIs.</li>
 	<li>When Terraform runs it will read all files in the current working directory with a “.tf” extension and concatenate them together.</li>
 	<li>Resources are declared as HCL objects, with type resource and exactly two labels. The first label specifies the type of resource you want to create, and the second is the resource name. Name has no special significance and is only used to reference the resource within a given module scope</li>
 	<li><span style="color: #ff0000;"><strong>Warning:</strong></span> It is important not to manually edit or delete the terraform.tfstate file, or else Terraform will lose track of all managed resources</li>
 	<li><strong>Note:</strong> <em>terraform destroy</em> does exactly the same thing as if you were to delete all the configuration code and run a terraform apply.</li>
 	<li>The contents of a data source code block are called query constraint arguments and behave exactly the same as arguments do for resources. The query constraint arguments are used to specify which resource(s) to fetch data from. Data sources are unmanaged resources that Terraform can read data from but doesn’t directly control.</li>
</ul>
<h2>Chapter 2: Lifecycle of a Terraform Resource</h2>
<ul>
 	<li><strong>Tip:</strong> The &lt;&lt;- sequence indicates an indented heredoc string. Anything between the opening identifier and the closing identifier (EOT) is interpreted literally. Leading whitespace, however, is ignored (unlike traditional heredoc syntax).</li>
 	<li><em>terraform init</em> always must be run at least once, but you’ll have to run it again each time you add new provider or module dependency.</li>
 	<li>After initialization, Terraform creates a hidden .terraform directory for installing plugins and modules.</li>
 	<li><strong>Tip:</strong> version lock any providers you use, whether they are implicitly or explicitly defined to ensure that any deployment you make is always repeatable.</li>
 	<li><em>terraform plan</em> not only informs you what Terraform intends to do, it acts as a linter, letting you know of any syntax or dependency errors you might have. It’s a read only action that does not alter the state of deployed infrastructure, and like <em>terraform init</em>, it’s idempotent.</li>
 	<li><strong>Tip:</strong> if <em>terraform plan</em> is running slow, turn off trace level logging and consider increasing parallelism (-parallelism=n )</li>
 	<li>Regardless of how you generate an execution plan, it’s always a good idea to review the contents of the plan before applying. During an <em>apply</em>, Terraform creates and destroys real infrastructure, which of course has real-world consequences.</li>
 	<li><span style="color: #ff0000;"><strong>Warning:</strong> </span>It’s important to not edit, delete or otherwise tamper with the terraform.tfstate file, or else Terraform could potentially lose track of the resources it manages. It is possible to restore a corrupted or missing state file, but it’s difficult and time consuming to do so.</li>
 	<li>When terraform plan is run, Terraform will call Read() on each resource in the state file.</li>
 	<li><em>terraform apply -auto-approve</em>. The optional -auto-approve flag tells Terraform to skip the manual approval step and immediately apply changes.</li>
 	<li><span style="color: #ff0000;"><strong>Warning:</strong></span> -auto-approve can be dangerous if you have not already reviewed the results of the plan</li>
 	<li>The surprising outcome of <em>terraform plan</em> is merely the result of the provider choosing to do something a little odd with the way Read() was implemented. I don’t know exactly why they chose to do it the way that they did, but they decided that if the contents of the file don’t exactly match up exactly with what’s in the state file, then the resource doesn’t exist anymore. The consequence is that Terraform thinks that the resource no longer exists, even though there’s still a file with the same name.</li>
 	<li>You can think of <em>terraform refresh</em> like a <em>terraform plan</em> that also happens to alter the state file. It’s a read-only operation that does not modify managed existing infrastructure, just Terraform state.</li>
 	<li><strong>Note:</strong> deleting all configuration files and running terraform apply is equivalent to <em>terraform destroy</em></li>
</ul>
<h2>Chapter 3: Functional Programming and Advanced Templating Techniques</h2>
<ul>
 	<li>Variable names must be unique within a module scope (we’ll go over what this means in the next chapter), and cannot use certain reserved names, but otherwise have few restrictions.</li>
 	<li>Variables accept three optional input arguments: · default – a literal value to set the variable to when no other value is found. Leaving this argument blank means the variable is mandatory and must be set · description – a string value that provides some helpful documentation to the user type – a type constraint to set for the variable. Types can be either primitive (e.g. string, integer, bool) or complex (e.g. list, set, map, object, tuple)</li>
 	<li>All primitive types in HCL can be coerced to string types. For example, Boolean true/false values evaluate to “true” and “false” and likewise, all numbers are converted to string representations when parsed.</li>
 	<li>Enforcing a strict type schema on all of your variables is important to fail fast and prevent bad input from corrupting your downstream resources, but it’s not without its limitations. If you need more granular validation on input values, you could use conditional expressions.</li>
 	<li><span style="color: #ff0000;"><strong>Warning:</strong></span> Conditional expressions can make code difficult to read, if not done with care. Use them sparingly.</li>
 	<li><span style="color: #ff0000;"><strong>Warning:</strong></span> Not all functions in Terraform are idempotent. You should avoid non-idempotent legacy functions such as uuid() and timestamp() , because they may cause subtle bugs within Terraform. Terraform was built around the notion of resource immutability; as soon as you take that assumption away, you’re going to have a bad time.</li>
 	<li>The brackets that go around the for expression determine the type of the output. The previous code used [] , which means the output will be a list. If instead we used {}, then the result would be an object.</li>
 	<li>Execution order for an apply starts at the bottom and works its way up, so nodes with fewer dependencies are created first while nodes having more dependencies are created last.</li>
 	<li><strong>Note:</strong> You can combine count with a conditional expression to toggle whether or not you want a resource to be created (e.g. count = var.shuffle_enabled ? 1 : 0 )</li>
 	<li>The expression “count.index” is how to reference the current index of a resource when count is set.</li>
 	<li>Explicit dependencies are declared using the “depends_on” meta argument and are reserved for situations where you have a hidden dependency between resources.</li>
 	<li>Explicit dependencies behave exactly like implicit dependencies but are confusing and should be used cautiously – only when absolutely necessary.</li>
 	<li>Data sources are not considered resources for the purposes of an apply</li>
</ul>
<h2>Chapter 4: Deploying a Multi-Tiered Web Application in AWS</h2>
<ul>
 	<li>Modules are self-contained packages of code that allow you to create reusable components by grouping multiple related resources together. They allow you to view pieces of infrastructure only in terms of the inputs and outputs, without requiring any knowledge of the internal workings.</li>
 	<li>Like resources and data sources, modules have inputs and outputs</li>
 	<li>Modules can be endlessly nested within other modules, so they make for excellent tools for breaking complexity into small, reusable bits.</li>
 	<li>You typically don’t want to have more than three or four levels of nested modules, otherwise it becomes difficult to reason about (like a deeply nested class hierarchy).</li>
 	<li>In accordance with established code conventions and best practices from HashiCorp, we’ll split module code into three unambiguously named configuration files:
<ul>
 	<li>main.tf – the primary entry point containing all resources and data sources</li>
 	<li>outputs.tf – declarations for all output values</li>
 	<li>variables.tf – declarations for all input variables</li>
</ul>
</li>
 	<li>A root module is just the entry point for Terraform, so wherever you initialize and apply Terraform, that directory is the de-facto root module.</li>
 	<li>We’ll be using the root module mostly for code organization and won’t use it to actually deploy any resources as that’s the job of the nested modules.</li>
 	<li>You should always evaluate for yourself whether or not it’s worth the tradeoff to use an external module vs. writing the Terraform code yourself. Using other people’s code can save you time in the short term, but it can also be a source of tech debt later down the road, especially if something were to break in an unexpected way.</li>
 	<li><strong>Tip:</strong> reasoning about how data needs to pass between modules will often make it clear how you should componentize your software systems. Modules that need to share a lot of data should be closer together, while modules that are more independent can be further apart.</li>
 	<li><span style="color: #ff0000;"><strong>Warning:</strong></span> while it may be tempting to overuse the any type constraint, it’s a lazy coding habit that will get you in trouble more often than not. Only use any when passing data between modules, and never for configuring the variables of the root module.</li>
 	<li><strong>Tip:</strong> never grant more access to data than a given module needs for legitimate purposes. As in normal software development, the inputs and outputs of a module represent the interface, so don’t pass in more data than required by the interface.</li>
 	<li>Whenever I am planning out the code for a Terraform module, I always consider inter-resource dependencies (i.e. what depends on what) because it helps me predict potential race conditions that require an explicit depends_on.</li>
 	<li>Only outputs from the root module show up in the command line after applying.</li>
 	<li>As directed by HashiCorp, it is best practice that each module has at least the following three files: main.tf, variables.tf and outputs.tf.</li>
</ul>
<h2>Chapter 5: Serverless Made Easy</h2>
<ul>
 	<li>It’s important to recognize that by breaking your application into functions, you’re accepting a tradeoff between decreased code complexity and increased wiring requirements between components.</li>
 	<li><strong>Tip:</strong> As a rule of thumb, I would suggest having no more than a few hundred lines of code per Terraform configuration file. Any more and it becomes difficult to build a mental map of how the code actually works.</li>
 	<li>The real world is a messy place and doesn’t usually lend itself well to categorization.</li>
 	<li>Here is a list of steps that I suggest taking when tackling a new problem with Terraform:
<ul>
 	<li>1. Define the problem and goals</li>
 	<li>2. Research potential solutions, while keeping an open mind</li>
 	<li>3. Select key technologies and tools to leverage</li>
 	<li>4. Build a prototype to determine if further investment is warranted</li>
 	<li>5. Develop final product</li>
</ul>
</li>
 	<li>If you want to solve useful problems with Terraform, you also have to be willing to try new things and make mistakes.</li>
 	<li><strong>Tip:</strong> problem solving is an art, and the only way to get better is with practice if there are some Terraform resources that are poorly implemented, or are otherwise incomplete and don’t have all the features that the corresponding ARM template has, you may be better off deploying an ARM template with Terraform.</li>
</ul>
<h2>Chapter 6: Terraform with Friends</h2>
<ul>
 	<li>A backend in Terraform determines how state is loaded and how operations like terraform plan and terraform apply are executed.</li>
 	<li>Enhanced backends are relatively new and allow you to do sophisticated things like run CLI operations on a remote machine and stream the results back to your local terminal.</li>
 	<li>Flat modules (as opposed to nested modules) are when you organize your code by creating lots of little .tf files within a single monolithic module. Each file in the module contains all the code for deploying an individual component, which would otherwise be broken out into its own module. The primary advantage of flat module structures over nested modules is reduced boilerplate, and easier codebase navigation.</li>
 	<li><strong>Tip:</strong> There’s no fixed rule about how long the configuration code in a single file can be, but I find it best to stick to a ~200 lines maximum rule of thumb</li>
 	<li><span style="color: #ff0000;"><strong>Warning:</strong></span> Think carefully before deciding to use a flat module structure for code organization. This pattern permits a high degree of inter-component coupling, which can make your code difficult to navigate and understand.</li>
 	<li>Believe it or not, having a README.md is actually a requirement for registering a module with the Terraform Module Registry.</li>
 	<li><strong>Tip:</strong> there’s a neat open source tool called terraform-docs that automatically generates documentation from your configuration code</li>
 	<li><strong>Note:</strong> You’ll need to upload your code to GitHub even if you only wish to use the Terraform Module Registry, because the Terraform Module Registry sources from public GitHub repos</li>
 	<li>Create a repo with a name of the form: terraform-- . There’re no rules about what “provider” and “name” mean in the context of a module, but I typically think of “provider” as the cloud that I am deploying to, while “name” is a helpful descriptor of the project.</li>
 	<li>Workspaces allow you to have more than one state file for the same configuration code. This means that you can deploy multiple environments without resorting to copy-pasting your configuration code into different folders. Each workspace can use its own variables definitions file to parameterize the environment</li>
 	<li>Technically workspaces are no different than simply renaming state files. The reason you would use workspaces is because remote state backends support workspaces and not the -state argument.</li>
</ul>
<h2>Chapter 7: CI/CD Pipelines as Code</h2>
<ul>
 	<li>Passing a provider explicitly means that you override the implicit (or default) provider with another provider.</li>
 	<li>When more than one provider declaration is present, one provider will always be designated as the default provider, while any others are designated as non-default providers.</li>
 	<li><strong>Tip:</strong> passing providers explicitly is most commonly used for multi-region deployments.</li>
 	<li>The for_each meta-attribute accepts a map, or set of strings, and creates an instance for each element in that map or set.</li>
 	<li>For_each does not guarantee sequential iteration (because sets and maps are inherently unordered collections).</li>
 	<li>For-each is most similar to the meta-attribute count, but has a number of distinct advantages, namely:
<ul>
 	<li>1. Intuitive –For-each is a much more natural concept, compared to iterating by index</li>
 	<li>2. Less verbose – syntactically, for_each is shorter and more pleasing to the eye</li>
 	<li>3. Ease of use – instead of storing instances in an array, instances are stored in a map. This makes individual resource instances much easier to reference.</li>
</ul>
</li>
 	<li>For-each is the recommended approach for creating dynamic configurations, unless you have specific reason to access something by index</li>
 	<li>By inserting delays with the local-exec provisioner, you can solve many of these strange race condition style bugs.</li>
 	<li>Beware that Terraform does not keep track of changes to provisioners in the same way it does for resources attributes; no copy is stored in the state file and there is no way to calculate diffs.</li>
 	<li>HashiCorp has stated that resource provisioners are an anti-pattern and they may even be deprecated entirely in a newer version of Terraform.</li>
 	<li>Dynamic blocks can only be used within other blocks, and only when the use of repeatable nested configuration blocks is supported (surprisingly uncommon).</li>
 	<li>Dynamic nested blocks act much like for expressions but produce nested configuration blocks instead of complex types. They iterate over complex types (such as maps and lists) and generate configuration blocks for each element.</li>
 	<li><span style="color: #ff0000;"><strong>Warning:</strong></span> Backdoors to Terraform (i.e. local-exec provisioners) are inherently dangerous and should be avoided whenever possible. Use them only as a means of last resort.</li>
</ul>
<h2>Chapter 8: A Multi-Cloud MMORPG</h2>
<ul>
 	<li>Being a Terraform guru means having the wisdom to know that just because you can do something doesn’t necessarily mean you should.</li>
 	<li><strong>Tip:</strong> Under no circumstances should you skip creating a versions.tf , no matter how much you are tempted! It has saved me more than once from breaking changes in new provider versions.</li>
 	<li>Nomad is a general-purpose application scheduler made by HashiCorp that functions as a type of container orchestration platform.</li>
 	<li>Consul, on the other hand, is a service mesh solution (also produced by HashiCorp) and is most similar to Istio</li>
 	<li>Cluster federation is indispensable for organizations wishing to support operations in multiple clouds, without needing proportionally large teams of engineers to do so.</li>
 	<li><strong>Note:</strong> Consul and Nomad follow raft consensus protocol, meaning there must be an odd number of servers (with a minimum number of three) to have quorum. One of these servers is designated the leader while the others are followers. There is no such restrictions for clients.</li>
 	<li>In many ways, working with Terraform is a lot like building with Lego bricks. Terraform has all these providers, which much like individual Lego sets, give you a huge assortment of pieces to work with. You don’t need any specialized tools to assemble them -- they just fit together because that’s how they were designed.</li>
 	<li>Keep an open mind when working with Terraform. The best design may not always be the most obvious one.</li>
 	<li>Terraform is the glue that binds managed services together as part of a single deployment</li>
 	<li>Two-stage deployments are best when there is a clear distinction between “infrastructure” and “application”. Infrastructure is any of the virtual machines, clusters and managed services that applications run on. Each stage should have its own state.</li>
</ul>
<h2>Chapter 9: Zero Downtime Deployments</h2>
<ul>
 	<li>Zero Downtime Deployment (ZDD) describes the practice of keeping services always running and available to customers during software deployments.</li>
 	<li>Due to the way provisioners were implemented, a resource is not marked as “created” or “destroyed” unless all creation-time and destruction-time provisioners have executed with no errors. This means that we can use a local-exec provisioner to perform creation-time health checks</li>
 	<li>Although it would appear that create_before_destroy is an easy way to perform zero downtime deployments, it does have a number of quirks and shortcomings that should be kept in mind: · Confusing – once you start messing with the default behavior of Terraform, it’s harder to reason about how changes to your configuration files and variables will affect the outcome of an apply. This is especially true when local-exec</li>
 	<li>Provisioners are thrown in the mix.
<ul>
 	<li>Redundant – Everything you could accomplish with create_before_destroy could also be done with two Terraform workspaces or modules</li>
 	<li>Namespace Collisions – because both the new and old resource must exist at the same time, you have to choose parameters that will not conflict with each other.</li>
</ul>
</li>
 	<li>This is often awkward, and sometimes even impossible, depending on how the parent provider implemented the resource. Force New vs. In-place – not all attributes force the creation of a new resource. Some attributes are updated in-place, which means that the old resource is never actually destroyed, but merely altered. This also means any attached resource provisioners won’t be triggered.</li>
 	<li><strong>Tip:</strong> I personally do not use create_before_destroy as I have found it to be more trouble than it is worth</li>
 	<li><strong>Note:</strong> Managing stateful data for Blue/Green deployments is notoriously tricky. Many people recommend including databases in the base layer, so that all production data is shared between Blue and Green.</li>
 	<li>When performing the manual cutover, you mitigate risk by not having all your infrastructure in the same workspace.</li>
 	<li>Access keys should be rotated as frequently as possible – at least once every 90 days. The last thing you want is give someone more time to mine cryptocurrency in your account and/or hack customer data.</li>
 	<li>Serials and lineages are how Terraform internally validates state files. It’s how Terraform “knows” that a state file is not stale (i.e. out of date) or, worse, from another workspace entirely.</li>
 	<li>In the newly created state, Terraform also assigns a serial number which begins at one. Each time the state file is changed, due to modifications in the configuration code or what have you, the serial number is incremented by one.</li>
 	<li>You can think of lineage as a fingerprint to ensure continuity of a state file within a given workspace. Terraform always expects the lineage to remain the same from deployment to deployment, or else something is drastically wrong.</li>
 	<li>Some remote state backends will actually throw an error if you try to deploy with the wrong serial number because it’s better for Terraform to fail fast than proceed with invalid input.</li>
 	<li>It is absolutely critical to ensure that the lineage is preserved, and the serial number is incremented by one to avoid any potential complications when modifying state.</li>
 	<li>Corrupt state files occur most often when dealing with buggy providers, upgrading state files from Terraform 0.11 to 0.12, and importing resources that do not support the import command.</li>
 	<li><strong>Note:</strong> Best practice is to not edit the state file manually!</li>
 	<li><strong>Tip:</strong> Whenever I perform a major refactor, I always keep a copy of the old configuration code and state around just in case I make a mistake and need to start over. Better safe than sorry.</li>
 	<li>In general, I find loading multi-line strings works best with the file() function rather than EOF because it reduces visual clutter in the Terraform code and allows you to use the auto-formatting and syntax highlighting features available in most IDE’s.</li>
 	<li>There are three options for modifying state: 1. Manually editing the state file 2. Moving state data with terraform state mv 3. Deleting the old resource with terraform state rm and then reimporting the resource with terraform import</li>
 	<li><strong>Tip:</strong> Manually editing the state is not recommended under ordinary circumstances. You would only do this if you needed to manually change one of the attribute values on a managed resource for some reason.</li>
 	<li>We will use method two, terraform state mv, to move the IAM resources around. This command will move an item, such as a resource or module, matched by the source address, into the destination address. It can be used for resource renaming, moving items to and from modules, moving entire modules around, and more.</li>
 	<li>The terraform import command allows you to import existing resources into Terraform, which allows you to bring unmanaged resources under the yolk of Terraform. Not all resources support the import operation, but most do.</li>
 	<li><strong>Tip:</strong> If you are stuck with a corrupted state file, which means you can’t successfully apply or destroy, it’s usually easier to remove the offending resource from state than to solve whatever error Terraform is throwing your way.</li>
 	<li>Address is the valid resource address of where you want your resource to be imported to. The ID is the unique ID of the resource which can be used to find the existing resource from the API</li>
</ul>
<h2>Chapter 10: Refactoring and Testing</h2>
<ul>
 	<li>
<div id="8" class="readable-text" data-hash="ddbf7123629d76c9e1faba55fa0625ec">

 <i><span class="highlighted-text highlight-480025 highlight-color-yellow">Refactoring</span></i><span class="highlighted-text highlight-480025 highlight-color-yellow"> is the art of improving the design of code without changing existing behavior or adding new functionality.</span> <span class="highlighted-text highlight-480026 highlight-color-yellow">Benefits of refactoring include:</span>

</div>
<ul>
 	<li id="9" class=" readable-text" data-hash="e6d975a0cacaecc1fc603746989bec91"><strong><span class="highlighted-text highlight-480026 highlight-color-yellow">Maintainability</span></strong><span class="highlighted-text highlight-480026 highlight-color-yellow"> – the ability to quickly fix bugs and address problems faced by customers.</span></li>
 	<li id="10" class=" readable-text" data-hash="e429f335fd17c887e7af3702e1b5c877"><strong><span class="highlighted-text highlight-480026 highlight-color-yellow">Extensibility</span></strong><span class="highlighted-text highlight-480026 highlight-color-yellow"> – how easy it is to add new features. If your software is extensible, then you are more agile and able to respond to marketplace changes.</span></li>
 	<li id="11" class=" readable-text" data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><strong><span class="highlighted-text highlight-480026 highlight-color-yellow">Reusability</span></strong><span class="highlighted-text highlight-480026 highlight-color-yellow"> – removing duplicated and highly coupled code. Reusable code is readable and easier to maintain.</span></li>
</ul>
</li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c">There are (at least) three levels of software testing to consider: unit tests, integration tests and system tests.</li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><span class="highlighted-text highlight-480033 highlight-color-yellow selected-highlight">What we do care about is </span><i><span class="highlighted-text highlight-480033 highlight-color-yellow selected-highlight">integration tests</span></i><span class="highlighted-text highlight-480033 highlight-color-yellow selected-highlight">. In other words, for a given set of inputs, does a subsystem of Terraform (i.e. a module) deploy without errors, and produce the expected output?</span></li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><span class="highlighted-text highlight-480036 highlight-color-yellow">We can target the destruction and recreation of individual resources with the </span><kbd><span class="highlighted-text highlight-480036 highlight-color-yellow">terraform taint</span></kbd><span class="highlighted-text highlight-480036 highlight-color-yellow"> command.</span></li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><strong>Note:</strong> <span class="highlighted-text highlight-480038 highlight-color-yellow">if you ever taint the wrong resource, you can always undo your mistake with the complementary command: </span><kbd><span class="highlighted-text highlight-480038 highlight-color-yellow">terraform untaint</span></kbd></li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c">The biggest refactoring improvement we can make it to put reusable code into modules.</li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><span class="highlighted-text highlight-480040 highlight-color-yellow">Module expansions make it possible to use </span><kbd><span class="highlighted-text highlight-480040 highlight-color-yellow">count</span></kbd><span class="highlighted-text highlight-480040 highlight-color-yellow"> and </span><kbd><span class="highlighted-text highlight-480040 highlight-color-yellow">for_each</span></kbd><span class="highlighted-text highlight-480040 highlight-color-yellow"> on a module in the same way you could for a resource. Instead of declaring modules multiple times, now you only have to declare it once.</span></li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><span class="highlighted-text highlight-480041 highlight-color-yellow selected-highlight">Like </span><kbd><span class="highlighted-text highlight-480041 highlight-color-yellow selected-highlight">for_each</span></kbd><span class="highlighted-text highlight-480041 highlight-color-yellow selected-highlight"> on resources, </span><kbd><span class="highlighted-text highlight-480041 highlight-color-yellow selected-highlight">for_each</span></kbd><span class="highlighted-text highlight-480041 highlight-color-yellow selected-highlight"> on a module requires providing configuration via either a set or a map.</span></li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><strong>Why Not Use Sets?</strong> <span class="highlighted-text highlight-480046 highlight-color-yellow">I recommend using maps instead of sets whenever you have more than one attribute that needs to be set on a module. Maps allow you to pass entire objects, whereas sets do not. Moreover, you can only pass in a set of type </span><kbd><span class="highlighted-text highlight-480046 highlight-color-yellow">set(string)</span></kbd><span class="highlighted-text highlight-480046 highlight-color-yellow">, meaning you would have to awkwardly encode data in the form of a JSON string and then decode it with </span><kbd><span class="highlighted-text highlight-480046 highlight-color-yellow">jsondecode()</span></kbd><span class="highlighted-text highlight-480046 highlight-color-yellow">if you wanted to pass more than a single attribute worth of data.</span></li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><span class="highlighted-text highlight-480051 highlight-color-yellow">The reason why embedding string literals, especially multi-line string literals, is generally a bad idea, is because it hurts readability. Having too many string literals in Terraform configuration makes it messy and hard to find what you’re looking for. Better just to keep this information in a separate file, and read from it using either </span><kbd><span class="highlighted-text highlight-480051 highlight-color-yellow">file()</span></kbd><span class="highlighted-text highlight-480051 highlight-color-yellow"> or </span><kbd><span class="highlighted-text highlight-480051 highlight-color-yellow">fileset()</span></kbd><span class="highlighted-text highlight-480051 highlight-color-yellow">.</span></li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c">Although convenient, splat expressions are less useful than they could be since they only operate on lists.</li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c">Unfortunately for us, Terraform state migration is rather difficult and tedious. It’s difficult because it requires intimate knowledge about how state is stored and it’s tedious because – although not entirely manual – it would take a long time to migrate more than a handful of resources.</li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c">To migrate state, we need to move or import resources into a correct destination resource address.</li>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><span class="highlighted-text highlight-480057 highlight-color-yellow">There are three options when it comes to migrating state:</span>
<ul>
 	<li data-hash="22f9b6ecdea9744e33c5e1bd7bb03d7c"><span class="highlighted-text highlight-480057 highlight-color-yellow">Manually editing the state file (not recommended)</span></li>
 	<li id="135" class=" readable-text" data-hash="d79afb55955b9825b6f18cb69553fce4"><span class="highlighted-text highlight-480057 highlight-color-yellow">Moving stateful data with </span><kbd><span class="highlighted-text highlight-480057 highlight-color-yellow">terraform state mv</span></kbd></li>
 	<li id="136" class=" readable-text" data-hash="40836efd4fba906e98db5e2453129abe"><span class="highlighted-text highlight-480057 highlight-color-yellow">Deleting old resources with </span><kbd><span class="highlighted-text highlight-480057 highlight-color-yellow">terraform state rm</span></kbd><span class="highlighted-text highlight-480057 highlight-color-yellow"> and reimporting with </span><kbd><span class="highlighted-text highlight-480057 highlight-color-yellow">terraform import</span></kbd></li>
</ul>
</li>
 	<li class=" readable-text" data-hash="40836efd4fba906e98db5e2453129abe">Of the three methods, the first is the most flexible, but also the most dangerous because of the potential for human error. Methods two and three are easier and safer.</li>
 	<li data-hash="40836efd4fba906e98db5e2453129abe"><strong>Note:</strong> you can move a resource or module to any address, even one that does not exist within your current configuration. This can cause unexpected behavior, which is why you have to be careful to get the right address.</li>
 	<li data-hash="40836efd4fba906e98db5e2453129abe"><strong>Note:</strong> check with the relevant Terraform provider documentation to ensure imports are allowed for a given resource</li>
 	<li data-hash="40836efd4fba906e98db5e2453129abe"> <span class="highlighted-text highlight-480079 highlight-color-yellow">A resource’s ID is set at the provider level, and is not always what you think it should be, but it is guaranteed to be unique. You can see what it is with </span><kbd><span class="highlighted-text highlight-480079 highlight-color-yellow">terraform show</span></kbd><span class="highlighted-text highlight-480079 highlight-color-yellow">, or figure it out yourself by reading through provider documentation.</span></li>
 	<li data-hash="40836efd4fba906e98db5e2453129abe"><span class="highlighted-text highlight-480080 highlight-color-yellow">I<span class="highlighted-text highlight-480080 highlight-color-yellow selected-highlight">mporting resources is the same as performing a </span><kbd><span class="highlighted-text highlight-480080 highlight-color-yellow selected-highlight">terraform refresh</span></kbd><span class="highlighted-text highlight-480080 highlight-color-yellow selected-highlight"> on a remote resource. It reads the current state of the resource and stores it in Terraform state.</span></span></li>
 	<li data-hash="40836efd4fba906e98db5e2453129abe">Being a tool developed by HashiCorp, terraform-exec has feature parity with Terraform, whereas Terratest does not. You can run all Terraform CLI commands with terraform-exec, using any combination of flags, while Terratest only allows a small subset of the most common commands.</li>
 	<li data-hash="40836efd4fba906e98db5e2453129abe"><span class="highlighted-text highlight-480088 highlight-color-yellow selected-highlight">Because of how hard refactoring can be, it’s often a good idea to test your code at the module level. You can do this with either Terratest or the terraform-exec library. I recommend terraform-exec, because it was developed by HashiCorp, and is the more complete of the two. Ideally you should perform integration testing on all modules within your organization.</span></li>
</ul>
<h2>Chapter 11: Extending Terraform by Writing your own Provider</h2>
<ul>
 	<li>The main job of any Terraform provider is to expose resources to Terraform and initialize any shared configuration objects.</li>
 	<li>Terraform will always initialize these shared configuration objects first, before performing any actions against provider resources.</li>
 	<li><strong>Note:</strong> If a provider fails or “hangs” during initialization, it is almost always due to a shared configuration object having invalid or expired credentials there are normally two prerequisites to creating your own provider: 1. Existing API – this one should be pretty obvious, but it’s also easily overlooked. Since Terraform makes calls against a remote API, there must be an existing remote API to make calls to. This may be your own API or someone else’s. 2. Golang Client SDK for the API – as providers are written in golang, you should have a golang client SDK for your API in place before proceeding. This will save you from having to make ugly, raw HTTP requests against the API</li>
 	<li><strong>Tip:</strong> Always have separate repositories for the client SDK and the provider! Providers are already sufficiently complicated, and there’s no need to make it harder on yourself by combining SDK code with provider code.</li>
 	<li>Providers are plugins for Terraform which communicate with Terraform over RPC (remote procedure calls). As long as providers implement the expected interface, they can be written in any language.</li>
 	<li><strong>Note:</strong> Normally provider authors create matching read-only resources (a.k.a. data sources) to compliment managed resources</li>
 	<li>The provider schema is important because it defines the attributes for the provider configuration, enumerates resources made available by the provider, and initializes any shared configuration objects. All this takes place during the terraform init step, when the provider is first installed.</li>
 	<li>Schema is a parameter that outlines the allowed provider configuration attributes in Terraform.</li>
 	<li>schema.EnvDefaultFunc. This function makes it possible to set a default environment variable to use if the attribute is not directly set in the provider configuration.</li>
 	<li><strong>Tip:</strong> it is good idea to make critical configuration attributes, such as access keys and addresses, optionally configurable as environment variables – for ease in automation the terraform providers schema command can be used to print detailed schemas for the providers used in the current configuration.</li>
 	<li>It’s important to know when each of the four CRUD functions will be invoked, to be able to predict and handle any errors that may occur.</li>
 	<li>ID is important because without it, the resource won’t be marked as “created” by Terraform, and neither will it be persisted to the state file.</li>
 	<li><span style="color: #ff0000;"><strong>Warning!</strong></span> Read() should always returns the same resource from the API. If it does not, you will end up with orphaned resources. Orphaned resources are resources originally created by Terraform, which have been lost track of, and are now considered unmanaged.</li>
 	<li>Force new updates are inconvenient from a user perspective because it takes longer for changes to propagate. This is an example where a good user experience matters more than ease of development or strict adherence to infrastructure immutability.</li>
 	<li>Writing good tests can be tough, but well it’s worth the effort, especially on large code bases with multiple contributors.</li>
 	<li>At a bare minimum, however, a resource test file requires the following:
<ul>
 	<li>Basic create/destroy test with validation that attributes get set in the state file</li>
 	<li>A function to check that all test resources have been destroyed</li>
 	<li>Test HCL configuration with all input attributes set</li>
</ul>
</li>
 	<li><strong>Tip:</strong> Most provider authors use a Makefile and CI triggers to automate the steps of building, testing, and distributing the provider. I recommend looking at some simpler providers, like terraform-provider-null and terraform-provider-tfe for inspiration</li>
 	<li><strong>Note:</strong> It is helpful to set TF_LOG=TRACE when testing providers, to ensure that API requests and responses are as expected</li>
 	<li>Where I see developing custom providers fitting best is with micro-APIs and self-service platforms.</li>
 	<li>Acceptance testing means writing tests for the provider schema and any resources exposed by the provider. Acceptance testing hardens code and is crucial for production readiness.</li>
</ul>
<h2>Chapter 12: Terraform in Automation</h2>
<ul>
 	<li>Having a manual approval stage is important to allow stakeholders (i.e. anyone that has an invested interest in the outcome of a Terraform deployment) read the output of terraform plan before approving an apply.</li>
 	<li>There are five default environment variables:
<ul>
 	<li>TF_IN_AUTOMATION ,</li>
 	<li>TF_INPUT ,</li>
 	<li>CONFIRM_DESTROY ,</li>
 	<li>WORKING_DIRECTORY and</li>
 	<li>BACKEND .</li>
 	<li>The first two are for configuring the Terraform runtime, the third is a flag for triggering a destroy run, the fourth sets the current working directory, and the fifth configures the remote state backend.</li>
</ul>
</li>
 	<li>Most Terraform configurations are written in HCL because it’s an easy language for humans to read and understand, but it’s also possible to write Terraform configuration in JSON instead. This alternative syntax (suffixed with the .tf.json extension) is normally reserved for automation purposes, because it is more machine friendly than HCL, and because many programming languages already have native libraries for processing JSON.</li>
 	<li><span style="color: #ff0000;"><strong>Warning!</strong></span> it is not recommended to turn off manual approval for anything mission critical! It’s like performing a terraform apply -auto-approve without even checking the results of the plan first. There should always be at least one human that is verifying the results of the plan before changes are applied</li>
</ul>
<h2>Chapter 13: Secrets Management</h2>
<ul>
 	<li>Terraform does not treat attributes containing sensitive data any differently than it treats non-sensitive attribute. Therefore, any and all sensitive data gets put in the state file, which is stored as plaintext JSON.</li>
 	<li>There are only three configuration blocks that can store stateful data (sensitive or otherwise) in Terraform. These being:
<ul>
 	<li>resources,</li>
 	<li>data sources, and</li>
 	<li>output values</li>
</ul>
</li>
 	<li>Removing unnecessary secrets is always a good idea, but it won’t prevent your state file from being leaked in the first place. To do that, you need to treat the state file itself as secret and gate who has access to it.</li>
 	<li>If you are using Terraform Enterprise or Terraform Cloud, your data is automatically encrypted at rest by default. In fact, they double encrypt it, once with KMS and again with Vault.</li>
 	<li>Every single API call that Terraform makes to AWS appears in the trace logs– with the complete request and response objects included.</li>
 	<li><strong>Tip:</strong> always turn off trace logging except when actively debugging local-exec provisioners are inherently dangerous and should be avoided whenever possible.</li>
 	<li>Even when trace logging is disabled, local-exec provisioners can be used to print secrets in the log files</li>
 	<li><strong>Note:</strong> AWS access keys are not the only thing that local-exec provisioners can expose. Any secrets stored in the filesystem or runtime environment of the machine running Terraform are also vulnerable.</li>
 	<li><strong>Tip:</strong> in case you are interested in creating custom resources without writing your own provider I recommend looking into the Shell provider for Terraform</li>
 	<li>External data sources are particularly nefarious because they run during a terraform plan, which means that all a malicious user would need to do is sneak this code into your configuration code and make sure it gets run during a terraform plan in order to gain access to all of your secrets. No manual confirmation of an apply necessary.</li>
 	<li><strong>Tip:</strong> always skim through any module you’d like to use, even if it comes from the official module registry, to ensure that no malicious code is present</li>
 	<li><strong>Note:</strong> External data sources are perhaps the most dangerous resource in all of Terraform. Be extremely judicious with their use, as there are many clever and devious ways that sensitive information can be leaked with them.</li>
 	<li>If you have continuous integration webhooks setup on a repository, do not allow terraform plan to be run for pull requests initiated from forks. This would allow hackers to run external data sources without your explicit approval.</li>
 	<li>There are two major ways to pass static secrets into Terraform: A) as environment variables and b) as Terraform variables. I recommend passing secrets in as environment variables whenever possible because it is far safer than the alternative. For one, environment variables do not show up in the state or plan files, and for two it’s harder for malicious users to access your sensitive values as compared to Terraform variables.</li>
 	<li>When configuring a Terraform provider, you definitely do not want to pass sensitive information in as regular Terraform variables</li>
 	<li>In general, configuring sensitive information in providers with Terraform variables is dangerous. The reason why it is so bad is because it opens you up to the possibility of someone redirecting secrets and using them elsewhere.</li>
 	<li><span style="color: #ff0000;"><strong>Warning!</strong></span> malicious Terraform code can access any secret stored anywhere on the local machine running Terraform!</li>
 	<li>By ensuring that Terraform runs are always linked to a Git commit, troublemakers will not be able to insert malicious code without leaving behind incriminating evidence in the Git history.</li>
 	<li>Ideally, secrets should not even exist until they are needed (i.e. leased or created “just-in-time”) and they should be revoked immediately after use. Secrets like these are called dynamic secrets, and they are substantially more secure than static secrets.</li>
 	<li>Sentinel policies are not written in HCL, as you might expect, instead they are written in Sentinel. Sentinel is its own domain specific programming language, which has a passing resemblance to Python.</li>
 	<li><strong>Note:</strong> Sentinel policies are not easy to write! You should expect a high learning curve, even if you are already a skilled programmer.</li>
</ul>
