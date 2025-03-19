---
layout: page
title: Book Review: Learning Helm
date: 2021-04-12 08:58
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2021/04/LeaningHelm-BookCover.jpg"><img class="alignleft size-medium wp-image-33889" src="/wp-content/uploads/2021/04/LeaningHelm-BookCover-229x300.jpg" alt="" width="229" height="300" /></a>Recently, I finished reading <a href="https://www.oreilly.com/library/view/learning-helm/9781492083641/" target="_blank" rel="noopener">Learning Helm</a> by Matt Butcher, Matt Farina, Josh Dolitsky.

While I have some experience with Kubernetes (from an infrastructure / IT Ops perspective), I only have limited experience with creating Kubernetes manifests. I've always wanted to understand better why you would use Helm, if you already have various YAML files for application deployments.

This book helped to set that foundation, and then build on it.

I particularly liked Chapter 2 ("<strong>Beyond the Basics with Helm</strong>"), and Chapters 5 ("<strong>Developing Templates</strong>") and 6 ("<strong>Advanced Chart Features</strong>").

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).

If my highlights peak your interest, I recommend that you pick up a copy for yourself.
<h2>Chapter 1: Introducing Helm</h2>
<ul>
 	<li>A Deployment describes an application as a collection of identical pods. The Deployment is composed of some top-level configuration data as well as a template for how to construct a replica pod.</li>
 	<li>A Service is a persistent network resource (sort of like a static IP) that persists even if the pod or pods attached to it go away. In this way, Kubernetes Pods can come and go while the network layer can continue to route traffic to the same Service endpoint.</li>
 	<li>In Kubernetes, a namespace is an arbitrary grouping mechanism that defines a boundary between the things inside the namespace and the things outside.</li>
 	<li>Package management is typically confined to implementing three verbs: install, upgrade, and delete. Configuration management is a higher-order concept that focuses on managing an application or applications over time. This is sometimes called "day-two ops".</li>
 	<li>One of the common themes you will notice in Helm charts is that configuration options are often set up so that you can take the same chart and release a minimal version of it into your development environment, or (with different configuration options) a sophisticated version into your production environment.</li>
 	<li>In Helm's vocabulary, a package is called a chart. The name is a play on the nautical nature of Kubernetes (which means "ship's captain" in Greek) and Helm (which is the steering mechanism of a ship). A chart plots the way a Kubernetes application should be installed.</li>
 	<li>An unpacked Helm chart is just a directory. Inside, it will have a Chart.yaml, a values.yaml, a templates/ directory, and perhaps other things as well. A packed Helm chart contains the same information as an unpacked one, but it is tarred and gzipped into a single file.</li>
 	<li>A new release of an installation is created each time we use Helm to modify the installation.</li>
</ul>
<h2>Chapter 2: Using Helm</h2>
<ul>
 	<li>The Helm maintainers recommend using kubectl to manage your Kubernetes credentials and letting Helm merely autodetect these settings.</li>
 	<li>A Helm chart is an individual package that can be installed into your Kubernetes cluster.</li>
 	<li>A Helm chart repository is simply a set of files, reachable over the network, that conforms to the Helm specification for indexing packages.</li>
 	<li>Helm will search not just the package names, but also other fields like labels and descriptions.</li>
 	<li>By default, Helm tries to install the latest stable release of a chart, but you can override this behavior and install a specific version of a chart.</li>
 	<li>A chart version is the version of the Helm chart. The app version is the version of the application packaged in the chart. Helm uses the chart version to make versioning decisions, such as which package is newest. As we can see in the preceding example, multiple chart versions may contain the same app version.</li>
 	<li>Helm needs a way to distinguish between the different instances of the same chart. So an installation of a chart is a specific instance of the chart. One chart may have many installations. When we run the helm install command, we need to give it an installation name as well as the chart name.</li>
 	<li>In Helm 2, instance names were cluster-wide. You could only have an instance named mysite once per cluster. In Helm 3, naming has been changed. Now instance names are scoped to Kubernetes namespaces. We could install two instances named mysite as long as they each lived in a different namespace.</li>
 	<li>When working with namespaces and Helm, you can use the --namespace or -n flags to specify the namespace you desire.</li>
 	<li>There are several ways of telling Helm which values you want to be configured. The best way is to create a YAML file with all of the configuration overrides.</li>
 	<li>The Helm core maintainers consider it a good practice to keep your configuration values in a YAML file. It is important to keep in mind, though, that if a configuration file has sensitive information (like a password or authentication token), you should take steps to ensure that this information is not leaked.</li>
 	<li>One nice feature of Helm is that even the help text can be updated using values you provide.</li>
 	<li><strong>NOTE:</strong> You can specify the --values flag multiple times. Some people use this feature to have "common" overrides in one file and specific overrides in another.</li>
 	<li>There is a second flag that can be used to add individual parameters to an install or upgrade. The --set flag takes one or more values directly. They do not need to be stored in a YAML file.</li>
 	<li>Subsections are a little more complicated when using the --set flag. You will need to use a dotted notation: --set mariadb.db.name=my-database. This can get verbose when setting multiple values.</li>
 	<li>When we talk about upgrading in Helm, we talk about upgrading an installation, not a chart. An installation is a particular instance of a chart in your cluster. When you run helm install, it creates the installation. To modify that installation, use helm upgrade.</li>
 	<li>This is an important distinction to make in the present context because upgrading an installation can consist of two different kinds of changes:
<ul>
 	<li>You can upgrade the version of the chart</li>
 	<li>You can upgrade the configuration of the installation</li>
</ul>
</li>
 	<li>In the background, Helm will load the chart, generate all of the Kubernetes objects in that chart, and then see how those differ from the version of the chart that is already installed. It will only send Kubernetes the things that need to change. In other words, Helm will attempt to alter only the bare minimum.</li>
 	<li>One of the most important things to learn about Helm installs and upgrades is that configuration gets applied freshly on each release.</li>
 	<li>The --reuse-values flag will tell Helm to reload the server-side copy of the last set of values, and then use those to generate the upgrade. This method is okay if you are always just reusing the same values. However, the Helm maintainers strongly suggest not trying to mix --reuse-values with additional --set or --values options.</li>
</ul>
<h2>Chapter 3: Beyond the Basics with Helm</h2>
<ul>
 	<li>In other words, --set values override settings from passed-in values files, which in turn override anything in the chart's default values.yaml file.</li>
 	<li>The principal purpose of the --dry-run flag is to give people a chance to inspect and debug output before sending it on to Kubernetes.</li>
 	<li>While --dry-run is designed for debugging, helm template is designed to isolate the template rendering process of Helm from the installation or upgrade logic.</li>
 	<li>The template command performs the first four phases (load the chart, determine the values, render the templates, format to YAML). But it does this with a few additional caveats.
<ul>
 	<li>During helm template, Helm never contacts a remote Kubernetes server. The template command always acts like an installation.</li>
 	<li>Template functions and directives that would normally require contacting a Kubernetes server will instead only return default data. The chart only has access to default Kubernetes kinds.</li>
</ul>
</li>
 	<li>Helm does not have access to any CRDs during a helm template run, since CRDs are installed on the cluster and are not included in the Kubernetes libraries.</li>
 	<li>Because Helm does not contact a Kubernetes cluster during a helm template run, it does not do complete validation of the output. It is possible that Helm will not catch some errors in this case. You may choose to use the --validate flag if you want that behavior, but in this case Helm will need a valid kubeconfig file with credentials for a cluster.</li>
 	<li>The flag --post-renderer on the install, upgrade, rollback, and template will cause Helm to send the YAML data to the command, and then read the results back into Helm. This is a great way to work with tools like Kustomize.</li>
 	<li>Each time we upgrade that mysite installation, a new Secret will be created to track each release. In other words, a release record tracks each revision of an installation.</li>
 	<li>By default, Helm tracks up to ten revisions of each installation. Once an installation exceeds ten releases, Helm deletes the oldest release records until no more than the maximum remain.</li>
 	<li>There are five helm get subcommands (hooks, manifests, notes, values, and all).</li>
 	<li>Even failed releases have revisions attached to them.</li>
 	<li>One useful subcommand is values. You can use this to see which values were supplied during the last release.</li>
 	<li>Although helm get values does not have a way of showing you the default values, you can see those with helm inspect values CHARTNAME. This inspects the chart itself (not the release) and prints out the documented default values.yaml file.</li>
 	<li>The last helm get subcommand that we will cover is helm get manifest. This sub-command retrieves the exact YAML manifest that Helm produced using the Chart templates</li>
 	<li>One important detail about this command is that it does not return the current state of all of your resources. It returns the manifest generated from the template.</li>
 	<li>The helm history command even gives us the error message that Kubernetes returned when marking the release failed.</li>
 	<li>A rollback does not restore to a previous snapshot of the cluster. Helm does not track enough information to do that. What it does is resubmit the previous configuration, and Kubernetes attempts to reset the resources to match.</li>
 	<li>Rollbacks can on occasion cause some unexpected behavior, especially if the Kubernetes resources have been hand-edited by users. Helm and Kubernetes will attempt to preserve those hand-edits if they do not conflict with the rollback. Essentially, a rollback will generate a 3-way diff between the current state of the resources, the failed Helm release, and the Helm release that you roll back to. In some cases, the generated diff may result in rolling back handmade edits, while in other cases those discrepancies will be merged.</li>
 	<li>Normally, a deletion event will destroy all release records associated with that installation. But when --keep-history is specified, you can see the history of an installation even after it has been deleted.</li>
 	<li>When history is preserved, you can roll back a deleted installation.</li>
 	<li>With the --generate-name flag, we no longer need to provide a name as the first argument to helm install. Helm generates a name based on a combination of the chart name and a timestamp.</li>
 	<li>But here, it is worth pointing out that Helm 3 assumes by default that if you attempt to deploy a chart into a namespace, that namespace was already created.</li>
 	<li>By adding --create-namespace, we have indicated to Helm that we acknowledge that there may not be a namespace with that name already, and we just want one to be created. Be sure, of course, that if you use this flag on a production instance, you have other mechanisms for enforcing security on this new namespace.</li>
 	<li>Helm does not automatically delete namespaces that were created with --create-namespace.</li>
 	<li>The helm upgrade --install command will install a release if it does not exist already, or will upgrade a release if a release by that name is found. Underneath the hood, it works by querying Kubernetes for a release with the given name. If that release does not exist, it switches out of the upgrade logic and into the install logic.</li>
 	<li>In a normal install or upgrade, Helm marks a release as successful as soon as the Kubernetes API server accepts the manifests. This is similar to package managers that consider a package successfully installed as soon as the package contents are written to the correct storage locations.</li>
 	<li>But with --wait, the success criteria for an installation is modified. A chart is not considered successfully installed unless (1) the Kubernetes API server accepts the manifest and (2) all of the pods created by the chart reach the Running state before Helm's timeout expires.</li>
 	<li>One recommendation for using --wait in CI is to use a long --timeout (five or ten minutes) to ensure that Kubernetes has time to resolve any transient failures.</li>
 	<li>A second strategy is to use the --atomic flag instead of the --wait flag. This flag causes the same behavior as --wait unless the release fails. Then, instead of marking the release as failed and exiting, it performs an automatic rollback to the last successful release.</li>
</ul>
<h2>Chapter 4: Building a Chart</h2>
<ul>
 	<li>Helm has a feature called starter packs, which helm create can utilize to provide a different starting point to generate a chart from.</li>
 	<li>Helm is using the same configuration you're using when you use kubectl, the command-line application for Kubernetes.</li>
 	<li>The include template function enables including the output of one template in another template, and this works in pipelines.</li>
 	<li>If a moving tag, such as stable, is used, the pullPolicy should be set to Always so that changes are picked up.</li>
 	<li>In Kubernetes there are two built-in objects you can use to expose applications. The first is a Service. The service property will let you select the type of Service being used. While ClusterIP is used by default, other options such as NodePort and LoadBalancer can be used.</li>
 	<li>The second built-in object is the Ingress manifest, which can be paired with a Service, and the chart has the capability to generate them.</li>
 	<li>When you run applications in production, it is a good practice to set resource limits. This prevents, for example, a memory leak in one container from disrupting other containers.</li>
 	<li>To handle this variance in environment, the recommendation is to put in resource limits and then turn them into comments.</li>
 	<li>Workloads have the ability to specify details about where they are executed in a cluster by the settings node selector, tolerations, and affinity. Although these more advanced features are often not used, it is a good idea to include them in a chart for those who need them.</li>
</ul>
<h2>Chapter 5: Developing Templates</h2>
<ul>
 	<li>Each of the properties that can be in a Chart.yaml file is accessible. The names differ in that they start with a lowercase letter in Chart.yaml but start with an uppercase letter when they are properties on the .Chart object.</li>
 	<li>Property names on data objects passed into templates begin with uppercase letters. This is a product of Helm being written in the Go programming language. In Go, public properties start with an uppercase letter and private properties start with a lowercase letter. When accessing the data object you just need to remember that the first letter is uppercase.</li>
 	<li>When helm template is used, Helm does not interrogate a cluster the same way it does for helm install or helm upgrade.</li>
 	<li>When the scope changes, properties like .Capabilities.KubeVersion.Minor will become inaccessible at that location. When template execution begins, . is mapped to $ and $ does not change. Even when the scope changes, $.Capabilities.KubeVersion.Minor and other passed-in data is still accessible. You will find $ is typically only used when the scope has changed.</li>
 	<li>Functions provide a means to transform the data you have into the format you need rendered or to generate data where none exists.</li>
 	<li>In addition to toYaml, Helm has functions to convert data to JSON with toJson and to TOML with toToml. toYaml is often used when creating Kubernetes manifests, while toJson and toToml are more often used when creating configuration files to be passed to applications through Secrets and ConfigMaps.</li>
 	<li>Checking for the existence of resources and API groups is useful when dealing with custom resource definitions and multiple versions of Kubernetes resource types.</li>
 	<li><strong>WARNING:</strong> When helm template is used, Helm will use a default set of API versions for a compliant Kubernetes cluster instead of interacting with your cluster to generate the known capabilities. That means <em>and</em> comes before either of the two items being used. The same idea applies to the use of or, which is also implemented as a function.</li>
 	<li><strong>TIP:</strong> The pattern of checking a value using with and then sending it to output using the toYaml and nindent functions is common for elements you have in a values.yaml file that you want to directly output in a template. This is regularly used for image pull secrets, node selectors, and more.</li>
 	<li>Once a variable is created for one type, such as a string, you cannot set the value to another type, such as an integer.</li>
 	<li>The method to create a variable with an initial value is different from the method used to change the value of an existing variable. When you assign a new value to the existing variable, you use =.</li>
 	<li>The loop syntax in templates is a little different than that in many programming languages. Instead of for loops, there are range loops that can be used to iterate over dicts (also known as maps) and lists.</li>
 	<li>You can think of a list as an array, while a map, with a key name and value, is similar to dictionaries in Python or a HashMap in Java. Within Helm templates you can create your own dictionaries and lists using the dict and list functions.</li>
 	<li>There are two types of labels used in the templates. There are the labels used on higher-level resources, such as Deployments, and then there are the labels used in specifications that are paired with selectors used for updates. These labels need to be treated differently because the labels used on specifications and selectors are typically immutable. This means you won't want them to contain elements such as application versions because those can change as an application is upgraded, but the specifications and selectors cannot be updated with new versions.</li>
 	<li>There are two functions you can use to include another template in your template. The template function is a basic function for including another template. It cannot be used in pipelines. Then there is the include function that works in a similar manner but can be used in pipelines.</li>
 	<li>The include function takes two arguments. The first is the name of the template to call. This needs to be the full name including any namespace. The second is the data object to pass. This can be one you create yourself, using the dict function, or it can be all or part of the global object used within the template.</li>
 	<li>KUBERNETES RECOMMENDED LABELS
<ul>
 	<li>The Kubernetes documentation recommends a set of common labels that you can apply to your workload manifests. The chart generated by helm create includes templates that generate these labels for you.</li>
 	<li>The labels begin with the prefix app.kubernetes.io followed by / as a separator. The Kubernetes documentation for labels notes that a prefix should be used for any labels generated by automation and that those without a prefix are private to the user. "</li>
 	<li>These labels include the application's name, the instance of the application (you can run an application more than once in a cluster and even a single namespace), the version of the application, a component type used to show where it fits in a larger application, what the application is part of, and the name of the tool used to manage the life cycle of the application (e.g., Helm). These labels are useful when linking applications together, displaying metadata in a user interface, and querying for information at the Kubernetes API.</li>
</ul>
</li>
 	<li>A digest is immutable, and it is the most precise method to specify the revision of an image to use.</li>
 	<li>Multiple Kubernetes manifests can be in the same YAML file, which means that the templates for multiple Kubernetes manifests can be in the same file, too. Named templates can live in any of the template files and be referenced in the others.</li>
 	<li>The first pattern is that each Kubernetes manifest should be in its own template file and that file should have a descriptive name.</li>
 	<li>A second guideline is to put the named templates, which you include in your own templates, into a file named _helpers.tpl. Because these are essentially helper templates for your other templates, the name is descriptive.</li>
</ul>
<h2>Chapter 6: Advanced Chart Features</h2>
<ul>
 	<li>Helm charts use semantic versions as their versioning scheme. The version field used for dependencies accepts a version range, and there are some shorthand syntaxes for those ranges. For example, ^1.2.3 is shorthand for &gt;= 1.2.3, &lt; 2.0.0.</li>
 	<li>Helm supports ranges including =, !=, &lt;, &lt;=, &gt;, &gt;=, ^, ~, and -. Different ranges can be combined together using a space or comma to support logical and combinations and | to support logical or combinations.</li>
 	<li>Helm also supports using a wildcard character of either X or *. If you omit a section of a version, such as omitting the patch portion, Helm will assume the missing part is a wildcard.</li>
 	<li>~ is used for specifying patch ranges. Where ^ typically rounds up to the latest within a major version range, ~ rounds up within a minor version range as long as the minor version is specified.</li>
 	<li>There are benefits to tight coupling, such as a single Helm command being able to install the whole collection of charts. A tight coupling is useful when you want to distribute charts to others, outside your company or organization.</li>
 	<li>With a loose coupling you can change and upgrade each chart independently from the rest. This method is sometimes used when you create and run charts within your own organization.</li>
 	<li>The exports property is a special top-level property in a values.yaml file. When a child chart has declared an export property, its contents can be imported directly into a parent chart.</li>
 	<li>If you use helm create to create a new library chart, the first step is to remove the contents of the templates directory and the values.yaml file because neither of these will be used. Then, you need to tell Helm that this is a library chart. In the Chart.yaml file set the type to library.</li>
 	<li>The default value for type, when not set, is application.</li>
 	<li>Hooks are like regular templates and the functionality they encapsulate is provided through containers running in Kubernetes clusters alongside the other resources for your application.</li>
 	<li>What distinguishes hooks from other resources is when a special annotation is set. When Helm sees the helm.sh/hook annotation, it uses the resource as a hook instead of a resource to be installed as part of the application installed by the chart.</li>
 	<li>Hooks can be weighted and specify a deletion policy for the resources after they have run. The weight enables more than one hook for the same event to be specified while providing an order in which they will run. This gives you the ability to ensure a deterministic order.</li>
 	<li>By default, Helm keeps the Kubernetes resources used for hooks until the hook is run again. This provides the ability to inspect the logs or look at other information about a hook after it is run.</li>
 	<li>Helm has a helm test command that executes test hooks on a running instance of a chart. The resources implementing those hooks can check database access, that database schemas are properly in place, for working connections between workloads, and other operational details.</li>
 	<li><strong>NOTE:</strong> If you look at tests in some existing charts you might find the hook they use is test-success instead of test. In Helm version 2 there was a hook named test-success for running tests. Helm version 3 provides backward compatibility and will run this hook name as a test.</li>
 	<li><strong>TIP:</strong> If you need to have configuration installed as part of a test, you can put the test hook on a Kubernetes Secret or ConfigMap to have it installed with other test resources.</li>
 	<li>In the ci directory you can create a values file for each situation to test. You need to use the glob naming pattern *-values.yaml when you name each file.</li>
 	<li>A provenance file is a PGP signed message with a particular structure in the message. That hash in the message is used by Helm to validate integrity, and the PGP signature is used to validate who it came from.</li>
 	<li>The crds directory is a special directory you can add to a chart to hold your CRDs. Helm will install CRDs prior to installing other resources. This ensures that CRDs are available for any custom resources or controllers that may leverage them in the chart.</li>
</ul>
<h2>Chapter 7: Chart Repositories</h2>
<ul>
 	<li>None</li>
</ul>
<h2>Chapter 8: Helm Plugins and Starters</h2>
<ul>
 	<li>Unless otherwise specified, Helm will use the plugin.yaml and source code located on the default branch of the Git repo when installing a plugin. If you wish to specify a Git tag to use, use the --version flag on install</li>
 	<li>The name of the plugin will be the subcommand used to invoke this plugin from the Helm CLI (e.g., helm myplugin). Due to this, plugin names should not match any existing Helm subcommands (install, repo, etc.). The name can only contain the characters a-z, A-Z, 0-9, _, and -.</li>
 	<li>When Helm detects a custom protocol being used, it will attempt to locate an installed plugin that can handle it, then defers the resource request to that plugin.</li>
 	<li>By including a file called completion.yaml in the root of the plugin directory, Helm plugins can specify all of the expected flags and commands available for the plugin statically.</li>
 	<li>Each command in a commands section can contain its own list of flags and validArgs.</li>
 	<li>To enable dynamic completion, include an executable file named plugin.complete in the root of the plugin directory. This file can be any type of executable; for example, a shell script or binary.</li>
 	<li>For plugins containing a plugin.complete file, when completion is requested (i.e., pressing the Tab key), Helm will run this executable, passing along the text that needs completion as the first argument. This program should then return a list of possible results, each separated by a new line, and exit successfully (i.e., return code 0).</li>
 	<li><strong>NOTE:</strong> If you are already using static completion using a completion.yaml file, then dynamic completion is not used, even if a plugin.complete executable is present in the plugin's root directory.</li>
 	<li>Any Helm chart can be converted into a starter. The only thing that separates a starter from a standard chart is the presence of dynamic references to the chart name in a starter's templates.</li>
 	<li>To convert a standard chart into a starter, replace any hardcoded references to the chart's name with the string &lt;CHARTNAME&gt;.</li>
</ul>
<h2>Appendix A: Chart API Versions</h2>
<ul>
 	<li>Charts using API version 2 are guaranteed to be supported by Helm 3, but not necessarily by Helm 2.</li>
 	<li>Chart names must be composed of lowercase letters, numbers, and dashes (-).</li>
 	<li>As a rule of thumb, most updates to the chart version should be increments to the MINOR version.</li>
 	<li>As for an initial version to use for your chart, choose 0.1.0 or 1.0.0. When the MAJOR version is 0 (e.g., 0.1.0), this technically indicates no promises will be made regarding breaking changes between MINOR and PATCH upgrades. Versions 1.0.0 and higher indicate a certain level of stability and a strict adherence to SemVer 2.</li>
 	<li>At a bare minimum, each entry under the dependencies block should contain a name subfield, and either a repository or an alias subfield. A repository should be an absolute URL to a valid chart repository (serving /index.yaml). An alias should be the character @ followed by the name of a previously added chart repository (e.g., @myrepo).</li>
 	<li>In API version 1, there is an additional file called requirements.yaml that specifies the chart's dependencies. The format of this file is identical to the dependencies field as defined in API version 2.</li>
 	<li>In API version 1, the chart dependency lock file has the name requirements.lock. This file is identical in format and purpose to the Chart.lock file described under API version 2, just with a different name.</li>
</ul>
<h2>Appendix B: Chart Repository API</h2>
<ul>
 	<li>Usually only one URL entry is provided per chart version, but multiple can be provided, and Helm will try to download the next item in the list if the previous one is inaccessible.</li>
 	<li>Unlike .tgz files, .prov files have a unique URL path requirement. They must be accessible at the path of the associated .tgz suffixed with .prov. For example, if a .tgz file is located at https://charts.example.com/superapp-0.1.0.tgz, then the .prov file must be located at https://charts.example.com/superapp-0.1.0.tgz.prov.</li>
</ul>
