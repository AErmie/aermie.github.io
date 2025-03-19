---
layout: page
title: Book Review: Pro Git, Second Edition
date: 2020-06-30 09:19
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/06/ProGit2nEdition_BookCover.png"><img class="alignleft size-medium wp-image-33372" src="/wp-content/uploads/2020/06/ProGit2nEdition_BookCover-243x300.png" alt="" width="243" height="300" /></a>Recently, I finished reading the <a href="https://git-scm.com/book/en/v2" target="_blank" rel="noopener noreferrer">Pro Git, Second Edition</a> written by Scott Chacon and Ben Straub.

I already have hands-on real-world experience with Git, and subsequent tools like GitHub and GitLab, but I still wanted to read this book. The reason being, I wanted to round out some of my understanding, and improve my efficiency with Git.

I particularly found<span style="color: #000000;"> the whole book helpful but in particular Chapter 2 ("<strong>Git Basics</strong>"), and Chapter 3 ("<strong>Git Branching</strong>").</span>

I’ve decided to share my highlights from reading this specific publication, in case the points that I found of note/interest will be of some benefit to someone else. So, here are my highlights (by chapter). Note that not every chapter will have highlights (depending on the content and the main focus of my work).
<h2>Chapter 01: Getting Started</h2>
<ul>
 	<li>In a DVCS (such as Git, Mercurial, Bazaar or Darcs), clients don’t just check out the latest snapshot of the files; rather, they fully mirror the repository, including its full history.</li>
 	<li>Every clone is really a full backup of all the data.</li>
 	<li>Git thinks of its data more like a series of snapshots of a miniature filesystem.</li>
 	<li>With Git, every time you commit, or save the state of your project, Git basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot.</li>
 	<li>Everything in Git is checksummed before it is stored and is then referred to by that checksum. This means it’s impossible to change the contents of any file or directory without Git knowing about it.</li>
 	<li>You can’t lose information in transit or get file corruption without Git being able to detect it.</li>
 	<li>Git stores everything in its database not by file name but by the hash value of its contents.</li>
 	<li>Git has three main states that your files can reside in: modified, staged, and committed:
<ul>
 	<li>Modified means that you have changed the file but have not committed it to your database yet.</li>
 	<li>Staged means that you have marked a modified file in its current version to go into your next commit snapshot.</li>
 	<li>Committed means that the data is safely stored in your local database.</li>
</ul>
</li>
 	<li>The three main sections of a Git project: the working tree, the staging area, and the Git directory.
<ul>
 	<li>The working tree is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.</li>
 	<li>The staging area is a file, generally contained in your Git directory, that stores information about what will go into your next commit.</li>
 	<li>The Git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.</li>
</ul>
</li>
 	<li>The first thing you should do when you install Git is to set your user name and email address. This is important because every Git commit uses this information, and it’s immutably baked into the commits you start creating</li>
 	<li>If you ever need help while using Git, there are three equivalent ways to get the comprehensive manual page (manpage) help for any of the Git commands: $ git help $ git --help $ man git-</li>
</ul>
<h2>Chapter 02: Git Basics</h2>
<ul>
 	<li>Instead of getting just a working copy, Git receives a full copy of nearly all data that the server has. Every version of every file for the history of the project is pulled down by default when you run git clone.</li>
 	<li>The git add command takes a path name for either a file or a directory; if it’s a directory, the command adds all the files in that directory recursively.</li>
 	<li>git add is a multipurpose command — you use it to begin tracking new files, to stage files, and to do other things like marking merge-conflicted files as resolved.</li>
 	<li>If you modify a file after you run git add, you have to run git add again to stage the latest version of the file</li>
 	<li>Setting up a .gitignore file for your new repository before you get going is generally a good idea so you don’t accidentally commit files that you really don’t want in your Git repository.</li>
 	<li>The rules for the patterns you can put in the .gitignore file are as follows: Blank lines or lines starting with # are ignored. Standard glob patterns work, and will be applied recursively throughout the entire working tree.</li>
 	<li>You can start patterns with a forward slash ( / ) to avoid recursivity. You can end patterns with a forward slash ( / ) to specify a directory. You can negate a pattern by starting it with an exclamation point ( ! ).</li>
 	<li>Glob patterns are like simplified regular expressions that shells use. An asterisk ( * ) matches zero or more characters; [abc] matches any character inside the brackets (in this case a, b, or c); a question mark ( ? ) matches a single character; and brackets enclosing characters separated by a hyphen ( [0-9] ) matches any character between them (in this case 0 through 9). You can also use two asterisks to match nested directories; a/**/z would match a/z , a/b/z , a/b/c/z , and so on.</li>
 	<li>It is also possible to have additional .gitignore files in subdirectories. The rules in these nested .gitignore files apply only to the files under the directory where they are located.</li>
 	<li>It’s important to note that git diff by itself doesn’t show all changes made since your last commit — only changes that are still unstaged. If you’ve staged all of your changes, git diff will give you no output.</li>
 	<li>For an even more explicit reminder of what you’ve modified, you can pass the -v option to git commit. Doing so also puts the diff of your change in the editor so you can see exactly what changes you’re committing.</li>
 	<li>Every time you perform a commit, you’re recording a snapshot of your project that you can revert to or compare to later.</li>
 	<li>Adding the -a option to the git commit command makes Git automatically stage every file that is already tracked before doing the commit, letting you skip the git add part</li>
 	<li>Git by default pipes all output through a pager so you see only one page of log output at a time.</li>
 	<li>The time-limiting options such as --since and --until are very useful.</li>
 	<li>The --author option allows you to filter on a specific author, and the --grep option lets you search for keywords in the commit messages.</li>
 	<li>You can specify more than one instance of both the --author and --grep search criteria, which will limit the commit output to commits that match any of the --author patterns and any of the --grep patterns; however, adding the --all-match option further limits the output to just those commits that match all --grep patterns.</li>
 	<li>To prevent the display of merge commits cluttering up your log history, simply add the log option --no-merges.</li>
 	<li>If you want to redo that commit, make the additional changes you forgot, stage them, and commit again using the --amend option</li>
 	<li>It’s important to understand that when you’re amending your last commit, you’re not so much fixing it as replacing it entirely with a new, improved commit that pushes the old commit out of the way and puts the new commit in its place. Effectively, it’s as if the previous commit never happened, and it won’t show up in your repository history.</li>
 	<li>It’s important to understand that git checkout -- is a dangerous command. Any local changes you made to that file are gone — Git just replaced that file with the most recently-committed version. Don’t ever use this command unless you absolutely know that you don’t want those unsaved local changes.</li>
 	<li>To see which remote servers you have configured, you can run the git remote command. It lists the shortnames of each remote handle you’ve specified. If you’ve cloned your repository, you should at least see origin — that is the default name Git gives to the server you cloned from</li>
 	<li>You can also specify -v , which shows you the URLs that Git has stored for the shortname to be used when reading and writing to that remote</li>
 	<li>If you clone a repository, the command automatically adds that remote repository under the name “origin”.</li>
 	<li>It’s important to note that the git fetch command only downloads the data to your local repository — it doesn’t automatically merge it with any of your work or modify what you’re currently working on. You have to merge it manually into your work when you’re ready.</li>
 	<li>Running git pull generally fetches data from the server you originally cloned from and automatically tries to merge it into the code you’re currently working on.</li>
 	<li>If you want just the entire list of tags, running the command git tag implicitly assumes you want a listing and provides one; the use of -l or --list in this case is optional. If, however, you’re supplying a wildcard pattern to match tag names, the use of -l or --list is mandatory.</li>
 	<li>A lightweight tag is very much like a branch that doesn’t change — it’s just a pointer to a specific commit.</li>
 	<li>Annotated tags, however, are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG).</li>
 	<li>It’s generally recommended that you create annotated tags so you can have all this information; but if you want a temporary tag or for some reason don’t want to keep the other information, lightweight tags are available too.</li>
 	<li>In “detached HEAD” state, if you make changes and then create a commit, the tag will stay the same, but your new commit won’t belong to any branch and will be unreachable, except by the exact commit hash.</li>
</ul>
<h2>Chapter 03: Git Branching</h2>
<ul>
 	<li>The git branch command only created a new branch — it didn’t switch to that branch.</li>
 	<li>To switch to an existing branch, you run the git checkout command.</li>
 	<li>By default, git log will only show commit history below the branch you’ve checked out. To show commit history for the desired branch you have to explicitly specify it: git log testing . To show all of the branches, add --all to your git log command.</li>
 	<li>It’s important to note that when you switch branches in Git, files in your working directory will change. If you switch to an older branch, your working directory will be reverted to look like it did the last time you committed on that branch.</li>
 	<li>Note that if your working directory or staging area has uncommitted changes that conflict with the branch you’re checking out, Git won’t let you switch branches. It’s best to have a clean working state when you switch branches.</li>
 	<li>This is an important point to remember: when you switch branches, Git resets your working directory to look like it did the last time you committed on that branch. It adds, removes, and modifies files automatically to make sure your working copy is what the branch looked like on your last commit to it.</li>
 	<li>When you try to merge one commit with a commit that can be reached by following the first commit’s history, Git simplifies things by moving the pointer forward because there is no divergent work to merge together — this is called a “fast-forward.”</li>
 	<li>Git adds standard conflict-resolution markers to the files that have conflicts, so you can open them manually and resolve those conflicts.</li>
 	<li>The options described above, --merged and --no-merged will, if not given a commit or branch name as an argument, show you what is, respectively, merged or not merged into your current branch.</li>
 	<li>To synchronize your work with a given remote, you run a git fetch command (in our case, git fetch origin ). This command looks up which server “origin” is (in this case, it’s git.ourcompany.com ), fetches any data from it that you don’t yet have, and updates your local database, moving your origin/master pointer to its new, more up-to-date position.</li>
 	<li>Your local branches aren’t automatically synchronized to the remotes you write to — you have to explicitly push the branches you want to share. That way, you can use private branches for work you don’t want to share, and push up only the topic branches you want to collaborate on.</li>
 	<li>It’s important to note that when you do a fetch that brings down new remote-tracking branches, you don’t automatically have local, editable copies of them.</li>
 	<li>Checking out a local branch from a remote-tracking branch automatically creates what is called a “tracking branch” (and the branch it tracks is called an “upstream branch”). Tracking branches are local branches that have a direct relationship to a remote branch. If you’re on a tracking branch and type git pull, Git automatically knows which server to fetch from and which branch to merge in.</li>
 	<li>While the git fetch command will fetch all the changes on the server that you don’t have yet, it will not modify your working directory at all. It will simply get the data for you and let you merge it yourself.</li>
 	<li>With the rebase command, you can take all the changes that were committed on one branch and replay them on a different branch.</li>
 	<li>There is no difference in the end product of the integration, but rebasing makes for a cleaner history. If you examine the log of a rebased branch, it looks like a linear history: it appears that all the work happened in series, even when it originally happened in parallel.</li>
 	<li>Rebasing replays changes from one line of work onto another in the order they were introduced, whereas merging takes the endpoints and merges them together.</li>
 	<li>Do not rebase commits that exist outside your repository and that people may have based work on.</li>
 	<li>When you rebase stuff, you’re abandoning existing commits and creating new ones that are similar but different. If you push commits somewhere and others pull them down and base work on them, and then you rewrite those commits with git rebase and push them up again, your collaborators will have to re-merge their work and things will get messy when you try to pull their work back into yours.</li>
 	<li>In general the way to get the best of both worlds is to rebase local changes you’ve made but haven’t shared yet before you push them in order to clean up your story, but never rebase anything you’ve pushed somewhere.</li>
</ul>
<h2>Chapter 04: Git on the Server</h2>
<ul>
 	<li>Git can use four distinct protocols to transfer data: Local, HTTP, Secure Shell (SSH) and Git.</li>
 	<li>If you have a shared mounted filesystem, then you can clone, push to, and pull from a local file-based repository.</li>
 	<li>Git operates slightly differently if you explicitly specify file:// at the beginning of the URL. If you just specify the path, Git tries to use hardlinks or directly copy the files it needs. If you specify file://, Git fires up the processes that it normally uses to transfer data over a network, which is generally much less efficient.</li>
 	<li>The main reason to specify the file:// prefix is if you want a clean copy of the repository with extraneous references or objects left out — generally after an import from another VCS or something similar</li>
 	<li>The pros of file-based repositories are that they’re simple and they use existing file permissions and network access.</li>
 	<li>This protocol does not protect the repository against accidental damage. Every user has full shell access to the “remote” directory, and there is nothing preventing them from changing or removing internal Git files and corrupting the repository.</li>
 	<li>Generally, you would either choose to run a read/write Smart HTTP server or simply have the files accessible as read-only in the Dumb manner. It’s rare to run a mix of the two services.</li>
 	<li>Git will automatically add group write permissions to a repository properly if you run the git init command with the --shared option. Note that by running this command, you will not destroy any commits, refs, etc. in the process.</li>
 	<li>If you do use a password, make sure to add the -o option; it saves the private key in a format that is more resistant to brute-force password cracking than is the default format.</li>
 	<li>Setting up Smart HTTP is basically just enabling a CGI script that is provided with Git called git-http-backend on the server. This CGI will read the path and headers sent by a git fetch or git push to an HTTP URL and determine if the client can communicate over HTTP (which is true for any client since version 1.6.6).</li>
</ul>
<h2>Chapter 05: Distributed Git</h2>
<ul>
 	<li>Martin Fowler has made a guide "Patterns for Managing Source Code Branches". This guide covers all the common Git workflows, and explains how/when to use them. There’s also a section comparing high and low integration frequencies. <a href="https://martinfowler.com/articles/branching-patterns.html" target="_blank" rel="noopener noreferrer">https://martinfowler.com/articles/branching-patterns.html</a></li>
 	<li>As a general rule, your messages should start with a single line that’s no more than about 50 characters and that describes the changeset concisely, followed by a blank line, followed by a more detailed explanation.</li>
 	<li>The git request-pull command takes the base branch into which you want your topic branch pulled and the Git repository URL you want them to pull from, and produces a summary of all the changes you’re asking to be pulled.</li>
 	<li>The --squash option takes all the work on the merged branch and squashes it into one changeset producing the repository state as if a real merge happened, without actually making a merge commit. This means your future commit will have one parent only and allows you to introduce all the changes from another branch and then make more changes before recording the new commit.</li>
 	<li>You use git format-patch to generate the mbox-formatted files that you can email to the list — it turns each commit into an email message with the first line of the commit message as the subject and the rest of the message plus the patch that the commit introduces as the body.</li>
 	<li>The nice thing about this is that applying a patch from an email generated with format-patch preserves all the commit information properly.</li>
 	<li>Git apply is an “apply all or abort all” model where either everything is applied or nothing is, whereas patch can partially apply patchfiles, leaving your working directory in a weird state.</li>
 	<li>If you can, encourage your contributors to use format-patch instead of diff to generate patches for you.</li>
 	<li>If you want Git to try a bit more intelligently to resolve the conflict, you can pass a -3 option to it, which makes Git attempt a three-way merge.</li>
 	<li>In the context of the git diff command, you can put three periods after another branch to do a diff between the last commit of the branch you’re on and its common ancestor with another branch</li>
 	<li>A cherry-pick in Git is like a rebase for a single commit. It takes the patch that was introduced in a commit and tries to reapply it on the branch you’re currently on.</li>
</ul>
<h2>Chapter 06: GitHub</h2>
<ul>
 	<li>When you “fork” a project, GitHub will make a copy of the project that is entirely yours; it lives in your namespace, and you can push to it.</li>
 	<li>Adding commits to an existing Pull Request doesn’t trigger a notification</li>
 	<li>If you merge this branch into the master branch and push it to GitHub, the Pull Request will automatically be closed.</li>
 	<li>What matters is the history and the final merge, so rebasing isn’t getting you much other than a slightly cleaner history and in return is far more difficult and error prone.</li>
 	<li>GitHub will look for task lists in your Issues and Pull Requests and show them as metadata on the pages that list them out.</li>
 	<li>If you highlight text in a comment that you want to directly reply to and hit the r key, it will quote that text in the comment box for you.</li>
 	<li>Many GitHub power users will simply turn off email notifications entirely and manage all of their notifications through this screen.</li>
 	<li>It’s also worth noting that if you have both email and web notifications enabled and you read the email version of the notification, the web version will be marked as read as well if you have images allowed in your mail client.</li>
 	<li>Like personal accounts, organizations are free if everything you plan to store there will be open source.</li>
 	<li>Without authenticating, you will be limited to 60 requests per hour. If you authenticate you can make up to 5,000 requests per hour.</li>
</ul>
<h2>Chapter 07: Git Tools</h2>
<ul>
 	<li>Git is smart enough to figure out what commit you’re referring to if you provide the first few characters of the SHA-1 hash, as long as that partial hash is at least four characters long and unambiguous; that is, no other object in the object database can have a hash that begins with the same prefix.</li>
 	<li>If you do happen to commit an object that hashes to the same SHA-1 value as a previous different object in your repository, Git will see the previous object already in your Git database, assume it was already written and simply reuse it. If you try to check out that object again at some point, you’ll always get the data of the first object.</li>
 	<li>It’s important to note that reflog information is strictly local — it’s a log only of what you’ve done in your repository. The references won’t be the same on someone else’s copy of the repository</li>
 	<li>Stashing takes the dirty state of your working directory — that is, your modified tracked files and staged changes — and saves it on a stack of unfinished changes that you can reapply at any time (even on a different branch).</li>
 	<li>If you don’t know what the git clean command is going to do, always run it with a -n first to double check before changing the -n to a -f and doing it for real.</li>
 	<li>The git grep command has a few advantages over normal searching commands like grep and ack. The first is that it’s really fast, the second is that you can search through any tree in Git, not just the working directory.</li>
 	<li>git filter-branch has many pitfalls, and is no longer the recommended way to rewrite history. Instead, consider using git-filter-repo, which is a Python script that does a better job for most applications where you would normally turn to filter-branch. Its documentation and source code can be found at https://github.com/newren/git-filter-repo.</li>
 	<li>It’s important to note that this flag ( --hard ) is the only way to make the reset command dangerous, and one of the very few cases where Git will actually destroy data.</li>
 	<li>It’s also interesting to note that like git add, the reset command will accept a --patch option to unstage content on a hunk-by-hunk basis. So you can selectively unstage or revert content.</li>
 	<li>By default, when Git sees a conflict between two branches being merged, it will add merge conflict markers into your code and mark the file as conflicted and let you resolve it.</li>
 	<li>Another cool thing about Git is that it doesn’t track file renames explicitly. It records the snapshots and then tries to figure out what was renamed implicitly, after the fact.</li>
 	<li>The bisect command does a binary search through your commit history to help you identify as quickly as possible which commit introduced an issue.</li>
 	<li>In fact, if you have a script that will exit 0 if the project is good or non-0 if the project is bad, you can fully automate git bisect.</li>
 	<li>Submodules allow you to keep a Git repository as a subdirectory of another Git repository. This lets you clone another repository into your project and keep your commits separate.</li>
 	<li>If you pass --recurse-submodules to the git clone command, it will automatically initialize and update each submodule in the repository, including nested submodules if any of the submodules in the repository have submodules themselves.</li>
 	<li>It’s important to note that submodules these days keep all their Git data in the top project’s .git directory, so unlike much older versions of Git, destroying a submodule directory won’t lose any commits or branches that you had.</li>
 	<li>The bundle command will package up everything that would normally be pushed over the wire with a git push command into a binary file that you can email to someone or put on a flash drive, then unbundle into another repository.</li>
</ul>
<h2>Chapter 08: Customizing Git</h2>
<ul>
 	<li>If your team has a commit-message policy, then putting a template for that policy on your system and configuring Git to use it by default can help increase the chance of that policy being followed regularly.</li>
 	<li>It’s important to note that client-side hooks are not copied when you clone a repository. If your intent with these scripts is to enforce a policy, you’ll probably want to do that on the server side</li>
</ul>
<h2>Chapter 09: Git and Other Systems</h2>
<ul>
 	<li>You should know two important things about git svn log . First, it works offline, unlike the real svn log command, which asks the Subversion server for the data. Second, it only shows you commits that have been committed up to the Subversion server. Local Git commits that you haven’t dcommited don’t show up; neither do commits that people have made to the Subversion server in the meantime. It’s more like the last known state of the commits on the Subversion server.</li>
 	<li>One thing you should know is that Mercurial doesn’t support rewriting history, only adding to it.</li>
 	<li>However, be careful with its creation because with Git it is impossible to re-include a file if a parent directory of that file is excluded.</li>
</ul>
<h2>Chapter 10: Git Internals</h2>
<ul>
 	<li>When Git packs objects, it looks for files that are named and sized similarly, and stores just the deltas from one version of the file to the next.</li>
 	<li>The “gc” stands for garbage collect, and the command does a number of things: it gathers up all the loose objects and places them in packfiles, it consolidates packfiles into one big packfile, and it removes objects that aren’t reachable from any commit and are a few months old.</li>
 	<li>You must have around 7,000 loose objects or more than 50 packfiles for Git to fire up a real gc command. You can modify these limits with the gc.auto and gc.autopacklimit config settings, respectively.</li>
</ul>
