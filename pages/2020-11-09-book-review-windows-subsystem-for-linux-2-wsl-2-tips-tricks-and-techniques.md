---
layout: page
title: Book Review: Windows Subsystem for Linux 2 (WSL 2) Tips, Tricks, and Techniques
date: 2020-11-09 08:33
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/11/WindowsSubsystemForLinux2-BookCover.jpg"><img class="alignleft size-medium wp-image-33669" src="/wp-content/uploads/2020/11/WindowsSubsystemForLinux2-BookCover-243x300.jpg" alt="" width="243" height="300" /></a>Recently, I finished reading <a href="https://www.packtpub.com/product/windows-subsystem-for-linux-2-wsl-2-tips-tricks-and-techniques/9781800562448" target="_blank" rel="noopener noreferrer">Windows Subsystem for Linux 2 (WSL 2) Tips, Tricks, and Techniques</a> by Stuart Leeks.

I've been using the Windows Subsystem for Linux (WSL) for a while, but I still found many good tips and reminders from this publication.

Below are my highlights from reading this specific publication, to help you decide if this is the book for you, and if it will provide what you are looking for. Note that not every chapter will have highlights (depending on the content and the main focus of my work).

If my highlights peak your interest, I recommend that you pick up a copy for yourself.
<h2>Chapter 01: Introduction to the Windows Subsystem for Linux</h2>
<ul>
 	<li>At a high level, WSL provides the ability to run Linux binaries on Windows.</li>
 	<li>When you first launch a terminal using WSL, you have a terminal application in Windows running a Linux shell.</li>
 	<li>Whereas the file systems are isolated by design in a VM, with the WSL file system access is configured for you by default. From Windows, you can access a new \\wsl$\ networked file share that is automatically available for you when the WSL is running and provides access to your Linux file systems.</li>
 	<li>Even more impressively, you can invoke processes in Linux from Windows and vice versa.</li>
 	<li>In the first version of WSL, the WSL team created a translation layer between Linux and Windows. This layer implements Linux syscalls on top of the Windows kernel and is what enables Linux binaries to run without modification.</li>
 	<li>With WSL 2, the WSL team went back to the drawing board and came up with a new solution: a virtual machine! This approach avoids the translation layer from WSL 1 by running the Linux kernel.</li>
 	<li>The big differences come with the use of what the documentation refers to as a Lightweight utility virtual machine (see <a href="https://docs.microsoft.com/en-us/windows/wsl/wsl2-about" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/windows/wsl/wsl2-about</a>).</li>
 	<li>One of these is that (at the time of writing) the generally available version of WSL 2 doesn't support GPU or USB access (full details at <a href="https://docs.microsoft.com/en-us/windows/wsl/wsl2-faq#can-i-access-the-gpu-in-wsl-2-are-there-plans-to-increase-hardware-support" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/windows/wsl/wsl2-faq#can-i-access-the-gpu-in-wsl-2-are-there-plans-to-increase-hardware-support</a>).</li>
 	<li>Another consideration is that because WSL 2 uses a virtual machine, applications running in WSL 2 will connect to the network via a separate network adapter from the host (which has a separate IP address).</li>
</ul>
<h2>Chapter 02: Installing and Configuring the Windows Subsystem for Linux</h2>
<ul>
 	<li>As well as having side-by-side versions, a distro can be converted between versions of WSL after installation. To achieve this, you use the wsl --set-version command.</li>
 	<li>In fact, if you run wsl without any arguments, it will launch a shell in your default distro!</li>
 	<li>As well as allowing you to select the Linux distro to run commands in, the wsl command also allows you to specify which user to run the commands as via the -u switch. The most common use I have found for this is running commands as root, which allows the use of sudo to run commands without being prompted for a password.</li>
 	<li>WSL provides a couple of places where you can configure its behavior. The first of these is wsl.conf, which provides a per-distro configuration, and the second is .wslconfig, which provides global configuration options.</li>
 	<li>The wsl.conf file follows the ini file structure with name/value pairs organized in sections.</li>
 	<li>The full documentation for wsl.conf can be found at <a href="https://docs.microsoft.com/en-us/windows/wsl/wsl-config#configure-per-distro-launch-settings-with-wslconf" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/windows/wsl/wsl-config#configure-per-distro-launch-settings-with-wslconf</a>.</li>
 	<li>As with the wsl.conf file, .wslconfig uses the ini file structure.</li>
 	<li>The memory value configures the limit for the memory consumed by the lightweight utility virtual machine that is used for version 2 of WSL. By default, this is 80% of the system memory.</li>
</ul>
<h2>Chapter 03: Getting Started with Windows Terminal</h2>
<ul>
 	<li>If you are interested in the roadmap for Windows Terminal, that can be found in the docs on GitHub at <a href="https://github.com/microsoft/terminal/blob/master/doc/terminal-v2-roadmap.md" target="_blank" rel="noopener noreferrer">https://github.com/microsoft/terminal/blob/master/doc/terminal-v2-roadmap.md</a>.</li>
 	<li>Profiles are a way of specifying what shell should be run in an instance of the terminal, for example, PowerShell or Bash.</li>
 	<li>The profiles shown were automatically generated by Windows Terminal - it detected what was installed on my machine and created the list of dynamic profiles. Better still, if I install a new WSL distro after Windows Terminal is installed, it will be automatically added to your list of available profiles!</li>
 	<li>The settings for Windows Terminal are all stored in a JSON file tucked away in your Windows profile.</li>
 	<li>The settings file is broken down into a few sections:
<ul>
 	<li>Global settings that are at the root of the JSON file Per-profile settings that define and configure each profile independently</li>
 	<li>Schemes that specify color schemes that profiles can use Key bindings that let you customize the keyboard shortcuts for performing tasks in Windows Terminal</li>
</ul>
</li>
 	<li>A full description of all of the settings is left to the documentation (<a href="https://docs.microsoft.com/en-us/windows/terminal/customize-settings/global-settings" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/windows/terminal/customize-settings/global-settings</a>).</li>
 	<li>The value for the defaultProfile setting allows you to use the name (or the associated guid) property for the profile you wish to set as the default profile. Be sure to enter the name exactly as specified in the profiles section.</li>
 	<li>One important thing to note is that each item in the list needs to be separated with a comma and there must not be a comma after the last list item. If you are changing the item at the end of the list, this can easily trip you up.</li>
 	<li>When you are changing the name for a profile, press Win + . to bring up the emoji picker and then continue typing to filter the emoji list.</li>
 	<li>Instead, to prevent a profile showing in the list, you can set the hidden property.</li>
 	<li>The default font for Windows Terminal is a new font face called Cascadia, which is freely available at <a href="https://github.com/microsoft" target="_blank" rel="noopener noreferrer">https://github.com/microsoft</a>.</li>
 	<li>Purely aesthetic or may be to make the terminal easier to use by increasing the font size, increasing the contrast, or using a specific font to make the content easier to read (for example, with the OpenDyslexic font available at <a href="https://www.opendyslexic.org/" target="_blank" rel="noopener noreferrer">https://www.opendyslexic.org/</a>).</li>
 	<li>CHANGING FONTS
<ul>
 	<li>The default font for Windows Terminal is a new font face called Cascadia, which is freely available at <a href="https://github.com/microsoft/cascadia-code/" target="_blank" rel="noopener noreferrer">https://github.com/microsoft/cascadia-code/</a> and ships with Windows Terminal.</li>
</ul>
</li>
 	<li>The font for each profile can be changed independently by setting the fontFace and fontSize properties in the profile.</li>
 	<li>Settings specified in the defaults section apply to all profiles, unless the profile overrides it.</li>
 	<li>For more fine-grained control over colors, you can create a color scheme under the schemes section in the settings file. Details on this can be found at <a href="https://docs.microsoft.com/en-us/windows/terminal/customize-settings/color-schemes" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/windows/terminal/customize-settings/color-schemes</a>, including a list of the built-in color schemes.</li>
</ul>
<h2>Chapter 04: Windows to Linux Interoperability</h2>
<ul>
 	<li>When you have WSL installed, you get a new \\wsl$ path that you can address in Windows Explorer and other programs. If you type \\wsl$ into the address bar in Windows Explorer, it will list any running Linux distributions (distros).</li>
 	<li>Tip: If you browse to \\wsl$ and don't see one of your installed distros, then it is an indication that the distro isn't running.</li>
 	<li>The first argument to Substring specifies where to start (0 indicates the start of the string) and the second argument is how many characters to take.</li>
 	<li>Fortunately, WSL forwards localhost addresses to Linux distros to preserve the natural workflow.</li>
 	<li>WSL forwards traffic for localhost in Windows into Linux distros.</li>
</ul>
<h2>Chapter 05: Linux to Windows Interoperability</h2>
<ul>
 	<li>By default, WSL automatically mounts your Windows drives inside WSL distributions (distros). These mounts are created in /mnt; for example, your C: drive is mounted as /mnt/c.</li>
 	<li>Important note: Under Windows, file systems are generally case-insensitive; that is, Windows treats SomeFile as the same as somefile. Under Linux, file systems are case-sensitive so those would be viewed as two separate files.</li>
 	<li>The result of this is that any application that you are used to being able to run in Windows without specifying the path can also be run in WSL without specifying the path. One difference is that in Windows, we don't need to specify the file extension (for example, we can run calc in PowerShell) but in WSL we do.</li>
 	<li>When you are running PowerShell scripts in WSL, you have two options: install PowerShell for Linux or call PowerShell in Windows to run the script.</li>
 	<li>Aliases in Bash allow you to create an alias, or an alternative name, for a command.</li>
 	<li>Running the alias command interactively in the terminal only sets the alias for the current instance of the shell. To add the alias permanently, copy the alias command into your .bashrc (or .bash_aliases) file so that the shell automatically sets it each time it starts.</li>
 	<li>The first part of the answer is that when Notepad is launched by WSL, it has its working directory set to the \\wsl$\... path that corresponds to the current working directory for the terminal in WSL.</li>
 	<li>The wslpath utility can be used to translate between Windows paths and Linux paths.</li>
 	<li>Important note: When specifying Windows paths in Bash, you must either escape them or surround the path with single quotes to avoid the need to escape them. The same applies to the dollar sign in \\wsl$\... paths.</li>
 	<li>To tell Git to use OpenSSH Authentication Agent to retrieve your SSH keys, you need to set the GIT_SSH environment variable to C:\Windows\System32\OpenSSH\ssh.exe (or whatever path it is installed to if your Windows folder is different).</li>
</ul>
<h2>Chapter 06: Getting More from Windows Terminal</h2>
<ul>
 	<li>A simple way to set the title is to right-click in the tab title to bring up the context menu and choose Rename Tab.</li>
 	<li>You can also use these functions to update the title as part of scripts, for example, to give an at-a-glance way to see the status of a long-running script via the tab title, even if a different tab has the focus.</li>
 	<li>Windows Terminal can be launched from the command-line or run dialog (Windows + R) using the wt.exe command.</li>
 	<li>Running wt.exe by itself will start Windows Terminal with the default profile loaded.</li>
 	<li>The tab title can be controlled with the --title switch.</li>
 	<li>Additionally, the --profile (or -p) switch allows us to specify which profile should be loaded.</li>
 	<li>Note: The new-tab argument requires a semi-colon before it, but many shells (including Bash and PowerShell) treat semi-colons as command separators. To use the previous commands successfully, any semi-colons need to be escaped using the backtick in PowerShell (`;).</li>
 	<li>Tip: If you are familiar with the tmux utility (<a href="https://github.com/tmux/tmux/wiki" target="_blank" rel="noopener noreferrer">https://github.com/tmux/tmux/wiki</a>), then this may look familiar, as tmux also allows splitting a window into multiple panels. But there are some differences. One feature of tmux is to allow you to disconnect and reconnect from terminal sessions, which can be handy when working with ssh as it preserves your session if your SSH (Secure Shell) connection drops, which Windows Terminal doesn't do (yet). On the other hand, with panes in Windows Terminal, you can run different profiles in each pane, which tmux doesn't do.</li>
 	<li>It is good to understand the capabilities of both tmux and Windows Terminal, and pick the right tool for the job - and you can always run tmux in a Bash shell in Windows Terminal for the best of both worlds!</li>
 	<li>The first commands are Alt + Shift + -, which will split the current pane in half horizontally, and Alt + Shift + +, which will split the pane vertically. Both of these commands will launch a new instance of the default profile in the newly created pane.</li>
 	<li>Pressing Alt + Shift + D will create a pane with a new instance of the profile from the current pane. The command will automatically determine whether to split horizontally or vertically based on the space available.</li>
 	<li>Instead of clicking normally, holding down the Alt key while clicking will launch the selected profile in a new pane.</li>
 	<li>To change the pane using the keyboard, you can use Alt + a cursor key, that is, Alt + cursor up will move the focus to a pane above the current one.</li>
 	<li>If any of the shells running in a pane exit, then that pane will close and the other panes will resize to fill its space.</li>
 	<li>Split-pane is used to specify a new pane and we can use the -p switch to specify which profile should be used for that pane. We can either let Windows Terminal pick how to split or we can use -H to split horizontally or -V to split vertically.</li>
 	<li>Windows Terminal allows each pane to have a title and displays the title of the currently focused pane as the tab title.</li>
</ul>
<h2>Chapter 07: Working with Containers in WSL</h2>
<ul>
 	<li>Under the covers, containers are a set of processes that are isolated through the use of features such as Linux namespaces and control groups (cgroups), to make it seem like those processes are running in their own environment (including with their own file system).</li>
 	<li>When you choose to integrate with a WSL distro, the socket for the Docker daemon is made available to that distro and the docker command-line interface (CLI) is added for you.</li>
 	<li>By default, docker ps outputs the short form of the container ID, whereas docker run outputs the full container ID value.</li>
 	<li>-d tells Docker to run this container detached from our terminal, that is, to run it in the background.</li>
 	<li>The first parameter to ADD specifies the content to add from the host folder, and the second parameter specifies where to place it in the container image.</li>
 	<li>When building an image, if Docker determines that the files used in a command match the previously built layer, then it will reuse that layer and indicate this with the ---&gt; Using cache output. If the files don't match, then Docker runs the command and invalidates the cache for any later layers.</li>
 	<li>When working with Kubernetes, using the latest image version means that Kubernetes will try to pull the image from a registry, even if it has the image locally.</li>
 	<li>Tip: When working with kubectl, you can improve your productivity by enabling bash completion. To configure this, run:
<ul>
 	<li>echo 'source &lt;(kubectl completion bash)' &gt;&gt;~/.bashrc</li>
</ul>
</li>
 	<li>This adds kubectl bash completion to your .bashrc file, so you will need to restart Bash to enable it (for full details see <a href="https://kubernetes.io/docs/tasks/tools/install-kubectl/#optional-kubectl-configurations" target="_blank" rel="noopener noreferrer">https://kubernetes.io/docs/tasks/tools/install-kubectl/#optional-kubectl-configurations</a>).</li>
</ul>
<h2>Chapter 08: Working with WSL Distros</h2>
<ul>
 	<li>Before we export a distro, we want to make sure that the default user for the distro is set in the /etc/wsl.conf file inside the distro.</li>
 	<li>Distros installed via the Store are installed in folders under $env:LOCALAPPDATA\Packages and you can use this path if you prefer to keep your imported distros in a similar location.</li>
 	<li>Here, we first use the useradd command to create a new user called stuart (but feel free to pick a different name!) and the -m switch ensures that the user home directory is created.</li>
 	<li>Typically, in a Dockerfile, you would see these commands concatenated as a single RUN step to help reduce the number and size of the layers.</li>
</ul>
<h2>Chapter 09: Visual Studio Code and WSL</h2>
<ul>
 	<li>There are some great introductory videos in the documentation (<a href="https://code.visualstudio.com/docs/getstarted/introvideos" target="_blank" rel="noopener noreferrer">https://code.visualstudio.com/docs/getstarted/introvideos</a>) as well as written tips and tricks (<a href="https://code.visualstudio.com/docs/getstarted/tips-and-tricks" target="_blank" rel="noopener noreferrer">https://code.visualstudio.com/docs/getstarted/tips-and-tricks</a>).</li>
 	<li>It's also worth noting that the command palette also shows the keyboard shortcuts for commands, giving an easy way to learn shortcuts for commonly used commands.</li>
 	<li>Unless you have configured an alternative, Git will use vi as its default editor.</li>
 	<li>To configure Git to use Visual Studio Code, we can run git config --global core.editor "code --wait".</li>
 	<li>Running the code command without the --wait switch launches Visual Studio Code and then exits (leaving Visual Studio Code running), which is generally what you want when using it to open a file or folder.</li>
 	<li>An alternative approach is to use an extension in Visual Studio Code such as Git Graph (<a href="https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph" target="_blank" rel="noopener noreferrer">https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph</a>)</li>
</ul>
<h2>Chapter 10: Visual Studio Code and Containers</h2>
<ul>
 	<li>The Remote-Containers extension for Visual Studio Code sits as part of the Remote-Development extension pack alongside Remote-WSL and Remote-SSH. All of these extensions allow you to separate the user interface aspects from the code interactions, such as loading, running, and debugging your code.</li>
 	<li>By using dev containers, we can replace the list of tools in the documentation with a set of steps in a Dockerfile that perform the steps for us.</li>
 	<li>See this blog post for more details: <a href="https://www.docker.com/blog/docker-desktop-wsl-2-best-practices/" target="_blank" rel="noopener noreferrer">https://www.docker.com/blog/docker-desktop-wsl-2-best-practices/</a>).</li>
 	<li>To add a dev container to a project, we need to create a .devcontainer folder with two files:
<ul>
 	<li>Dockerfile to describe the container image to build and run</li>
 	<li>devcontainer.json to add additional configuration</li>
</ul>
</li>
 	<li>Setting the name to be meaningful is particularly helpful if you sometimes have more than one dev container loaded at any time as it shows in the Window title.</li>
 	<li>To build and run Docker images inside your container, you may consider installing Docker inside the dev container. This is possible but can get quite complex and add performance issues.</li>
 	<li>The standard practice to refer to your user home folder is to use environment variables - for example, ${env:HOME}${env:USERPROFILE}/.kube).</li>
 	<li>By default, a dev container only requires that you have Visual Studio Code with Remote-Containers installed and a Docker daemon running, with the rest of the project requirements satisfied by the contents of the dev container.</li>
 	<li>Application package dependencies tend to evolve over time, and building them into the image (and rebuilding the image to install) feels a little heavyweight.</li>
 	<li>The Remote-Containers extension also has a feature called Always Installed Extensions (or Default Extensions). This feature allows you to configure a list of extensions that you always want to be installed in a dev container.</li>
 	<li>The dotfile support in Remote-Containers allows you to specify the URL for a Git repository containing your dotfiles, the location they should be cloned to in the dev container, and the command to run after cloning the repository.</li>
 	<li>To learn more about options for configuring dev containers, see <a href="https://code.visualstudio.com/docs/remote/containers" target="_blank" rel="noopener noreferrer">https://code.visualstudio.com/docs/remote/containers</a>.</li>
</ul>
<h2>Chapter 11: Productivity Tips with Command-Line Tools</h2>
<ul>
 	<li>If the partial command you have entered isn't sufficient to specify a single command, then bash completion will appear not to do anything, but pressing Tab twice will show the options.</li>
 	<li>Alternatively, if you are doing a mixture of development across Windows and WSL and want to share Git authentication between them, then you might want to configure Git Credential Manager for Windows for use in WSL.</li>
 	<li>See <a href="https://github.com/Microsoft/Git-Credential-Manager-for-Windows" target="_blank" rel="noopener noreferrer">https://github.com/Microsoft/Git-Credential-Manager-for-Windows</a> for more information.</li>
 	<li>The Git Graph extension is a handy addition for Visual Studio Code that allows you to view Git history graphically and works well with Remote-WSL.</li>
 	<li>When working in bash in a folder within a Git repository, the default prompt doesn't give you any hints about the status of the Git repository.</li>
 	<li>bash-git-prompt shows which branch you are currently on (main, in this example). It also indicates whether your local branch has commits to push or whether there are commits to pull from the remote branch via the up and down arrows.</li>
 	<li>Windows Terminal ships with a font called Cascadia and you can download Powerline variants of this font from <a href="https://github.com/microsoft/cascadia-code/releases" target="_blank" rel="noopener noreferrer">https://github.com/microsoft/cascadia-code/releases</a>.</li>
 	<li>The first tool we'll look at is jq, and it is a fantastically handy utility for working with JSON strings and is supported on the major platforms. Full installation options are listed on <a href="https://stedolan.github.io/jq/download/" target="_blank" rel="noopener noreferrer">https://stedolan.github.io/jq/download/</a>.</li>
 	<li>The playground can be a helpful environment when you are working on a complex query, and the Command Line section at the bottom even gives you the command line that you can copy and use in your scripts.</li>
 	<li>To assign this to a variable in a script, we typically want the value without quotes, and we can use the -r option with jq to get the raw output</li>
 	<li>For more information on the functions available in jq, check out the documentation at <a href="https://stedolan.github.io/jq/manual/#Builtinoperatorsandfunctions" target="_blank" rel="noopener noreferrer">https://stedolan.github.io/jq/manual/#Builtinoperatorsandfunctions</a>.</li>
 	<li>The tldr utility describes itself as simplified and community-driven man pages, and running tldr jq will give a shorter output than the man pages, with useful examples included.</li>
 	<li>The Select-Object cmdlet allows us to perform various manipulations on a set of objects, such as taking a specified number of items from the start or end of the set, or filtering to only unique items.</li>
 	<li>Because the default output format can be overridden, it is important to specify JSON output if that is what you want in scripts in case the user has configured a different default.</li>
 	<li>The az CLI also includes built-in querying capabilities using the JMESPath query language.</li>
 	<li>We also add --output tsv to use tab-separated output, which prevents the value from being wrapped in quotes.</li>
 	<li>Tip: You can find more details about JMESPath, and an interactive query tool, at <a href="https://jmespath.org" target="_blank" rel="noopener noreferrer">https://jmespath.org</a>. There is a jp CLI for running JMESPath queries, which can be installed from <a href="https://github.com/jmespath/jp" target="_blank" rel="noopener noreferrer">https://github.com/jmespath/jp</a>. Additionally, there is a jpterm CLI that provides an interactive JMESPath in your terminal, which can be installed from <a href="https://github.com/jmespath/jmespath.terminal" target="_blank" rel="noopener noreferrer">https://github.com/jmespath/jmespath.terminal</a>.</li>
 	<li>Tip: If you find kubectl too much to type, you can create an alias by running the following commands:
<ul>
 	<li>echo 'alias k=kubectl' &gt;&gt;~/.bashrc</li>
 	<li>echo 'complete -F __start_kubectl k' &gt;&gt;~/.bashrc</li>
 	<li>These commands add to .bashrc to configure k as an alias for kubectl and set up bash completion for k.</li>
</ul>
</li>
 	<li>For more details on JSONPath (including an online interactive evaluator), see <a href="https://jsonpath.com/" target="_blank" rel="noopener noreferrer">https://jsonpath.com/</a>.</li>
</ul>
