---
layout: page
title: Book Review: Ry's Git Tutorial
date: 2020-10-26 09:40
author: AdinErmie
comments: true
categories: []
---
<a href="/wp-content/uploads/2020/10/RysGitTutorial-BookCover.png"><img class="alignleft size-medium wp-image-33633" src="/wp-content/uploads/2020/10/RysGitTutorial-BookCover-219x300.png" alt="" width="219" height="300" /></a>Recently, I finished reading <a href="https://www.amazon.ca/Rys-Git-Tutorial-Ryan-Hodson-ebook/dp/B00QFIA5OC/ref=sr_1_1" target="_blank" rel="noopener noreferrer">Ry's Git Tutorial</a> by Ryan Hodson.

I've already have experience with DevOps, pipelines, source control, etc. But, to be honest, I am not as comfortable with using Git from the command-line, and am more inclined to use tools like <a href="https://desktop.github.com/" target="_blank" rel="noopener noreferrer">GitHub Desktop</a>, <a href="https://www.gitkraken.com/" target="_blank" rel="noopener noreferrer">GitKraken</a>, and <a href="https://code.visualstudio.com/" target="_blank" rel="noopener noreferrer">Visual Studio Code</a> when interacting with Git.

One thing I really appreciated about this book, was is how simply it explained the concepts, especially with the additional of an easy to follow diagram, like this:

[caption id="attachment_33639" align="aligncenter" width="300"]<a href="/wp-content/uploads/2020/10/GitDiagram.png"><img class="wp-image-33639 size-medium" src="/wp-content/uploads/2020/10/GitDiagram-300x237.png" alt="" width="300" height="237" /></a> Git Diagram[/caption]

<span style="color: #000000;">Below are my highlights from reading this specific publication, to help you decide if this is the book for you, and if it will provide what you are looking for. </span><span style="color: #000000;">Note that not every chapter will have highlights (depending on the content and the main focus of my work).</span>

If my highlights peak your interest, I strongly recommend that you pick up a copy for yourself.
<h2>Chapter 1: Introduction</h2>
<ul>
 	<li>None</li>
</ul>
<h2>Chapter 2: The Basics</h2>
<ul>
 	<li>The .git folder is the only difference between a Git repository and an ordinary folder , so deleting it will turn your project back into an unversioned collection of files.</li>
 	<li>An untracked file is one that is not under version control.</li>
 	<li>Git doesn’t automatically track files because there are often project files that we don’t want to keep under revision control.</li>
 	<li>To keep a project small and efficient, you should only track source files and omit anything that can be generated from those files.</li>
 	<li>A snapshot represents the state of your project at a given point in time.</li>
 	<li>Git’s term for creating a snapshot is called staging because we can add or remove multiple files before actually committing it to the project history.</li>
 	<li>Staging gives us the opportunity to group related changes into distinct snapshots — a practice that makes it possible to track the meaningful progression of a software project (instead of just arbitrary lines of code).</li>
 	<li>Staging files with the git add command doesn’t actually affect the repository in any significant way — it just lets us get our files in order for the next commit. Only after executing git commit will our snapshot be recorded in the repository.</li>
 	<li>The git status command will only show us uncommitted changes</li>
 	<li>Remember, we can see staged changes with git status, but not with git log. The latter is used only for committed changes.</li>
 	<li>The distinction between the working directory, the staged snapshot, and committed snapshots is at the very core of Git version control. Nearly all other Git commands manipulate one of these components in some way, so understanding the interplay between them is a fantastic foundation for mastering Git.</li>
</ul>
<h2>Chapter 3: Undoing Changes</h2>
<ul>
 	<li>Git only outputs the first 7 characters of the checksum (remember that you can see the full version with the default formatting of git log). These first few characters effectively serve as a unique ID for each commit.</li>
 	<li>Tags are convenient references to official releases and other significant milestones in a software project.</li>
 	<li>The -a flag tells Git to create an annotated tag, which lets us record our name, the date, and a descriptive message (specified via the -m flag).</li>
 	<li>It’s a good practice to run git status to see exactly what you’re committing before running git commit -m. This will keep you from unintentionally committing a file that doesn’t belong in the current snapshot.</li>
 	<li>You should never make changes directly to a previous revision.</li>
 	<li>When using git revert, remember to specify the commit that you want to undo — not the stable commit that you want to return to. It helps to think of this command as saying “undo this commit” rather than “restore this version.”</li>
 	<li>In either case, git reset only operates on the working directory and the staging area, so our git log history remains unchanged.</li>
 	<li>git clean -f this will remove all untracked files.</li>
 	<li>Be careful with git reset and git clean. Both operate on the working directory, not on the committed snapshots. Unlike git revert, they permanently undo changes, so make sure you really want to trash what you’re working on before you use them.</li>
 	<li>The git reset command undoes changes to the working directory and the staged snapshot, while git revert undoes changes contained in committed snapshots.</li>
</ul>
<h2>Chapter 4: Branches 1</h2>
<ul>
 	<li>In Git, a branch is an independent line of development.</li>
 	<li>The HEAD is Git’s internal way of indicating the snapshot that is currently checked out.</li>
 	<li>Creating a new branch is really just a way to request an independent working directory, staging snapshot, and history.</li>
</ul>
<h2>Chapter 5: Branches 2</h2>
<ul>
 	<li>Temporary branches like the latter are called topic branches because they exist to develop a certain topic, then they are deleted.</li>
 	<li>When the history of two branches diverges, a dedicated commit is required to combine the branches. This situation may also give rise to a merge conflict, which must be manually resolved before anything can be committed to the repository.</li>
 	<li>This brings us to my rule-of-thumb for using Git branches:
<ul>
 	<li>Create a new branch for each major addition to your project. Don’t create a branch if you can’t give it a specific name. Following these simple guidelines will have a dramatic impact on your programming efficiency.</li>
</ul>
</li>
 	<li>A 3-way merge occurs when you try to merge two branches whose history has diverged. It creates an extra merge commit to function as a link between the two branches.</li>
 	<li>Instead of using git add, we passed the -a flag to git commit. This convenient parameter tells Git to automatically include all tracked files in the staged snapshot. Combined with the -m flag, we can stage and commit snapshots with a single command. However, be careful not to include unintended files when using the -a flag.</li>
 	<li>When git branch creates a branch, it uses the current HEAD as the starting point for the new branch.</li>
 	<li>Conflicts occur when we try to merge branches that have edited the same content. Git doesn’t know how to combine the two changes, so it stops to ask us what to do.</li>
 	<li>The section labeled &lt;&lt;&lt;&lt;&lt;&lt;&lt;HEAD shows us the version in the current branch, while the part after the ======= shows the version in the crazy branch.</li>
 	<li>Fast-forward merges are not reflected in the project history. This is the tangible distinction between fast-forward merges and 3-way merges.</li>
 	<li>In addition to master, many programmers often add a second permanent branch called develop. This lets them use master to record really stable snapshots (e.g., public releases) and use develop as more of a preparation area for master.</li>
</ul>
<h2>Chapter 6: Rebasing</h2>
<ul>
 	<li>Rebasing lets us move branches around by changing the commit that they are based on.</li>
 	<li>After rebasing, the feature branch has a new parent commit, which is the same commit pointed to by master.</li>
 	<li>Instead of joining the branches with a merge commit, rebasing integrates the feature branch by building on top of master. The result is a perfectly linear history that reads more like a story than the hodgepodge of unrelated edits shown above.</li>
 	<li>Note that git add can also add entire directories to the staging area.</li>
 	<li>Also notice that, like the git merge command, git rebase requires you to be on the branch that you want to move.</li>
 	<li>Rebasing also allowed us to integrate the most up-to-date version of master without a merge commit.</li>
 	<li>That’s right, git rebase not only lets you move branches around, it enables you to manipulate individual commits as you do so.</li>
 	<li>By rebasing interactively, we can choose how each commit is transferred to the new base. Specify an interactive rebase by passing the -i flag to the rebase command.</li>
 	<li>Interactive rebasing gives you complete control over your project history, but this can also be very dangerous. For example, if you were to delete a line from the rebase listing, the associated commit wouldn’t be transferred to the new base, and its content would be lost forever.</li>
 	<li>The new ‑‑amend flag tells Git to replace the existing commit with the staged snapshot instead of creating a new one. This is also very useful for fixing premature commits that often occur during normal development.</li>
 	<li>If you ever find yourself lost in the middle of a rebase and you’re afraid to continue, you can use the ‑‑abort flag to abandon it and start over from scratch.</li>
</ul>
<h2>Chapter 7: Rewriting History</h2>
<ul>
 	<li>This is an example of a bad commit. It performed multiple, unrelated tasks, and it has a relatively generic commit message.</li>
 	<li>Thus far, we haven’t really specified when it’s appropriate to commit changes, but the general rules are essentially the same as for branch creation: Commit a snapshot for each significant addition to your project. Don’t commit a snapshot if you can’t come up with a single, specific message for it.</li>
 	<li>The git reset command moves the checked out snapshot to a new commit, and the HEAD~1 parameter tells it to reset to the commit that occurs immediately before the current HEAD (likewise, HEAD~2 would refer to second commit before HEAD).</li>
 	<li>The point to remember is that during a rebase you can add, delete, and edit commits to your heart’s content, and the entire result will be moved to the new base.</li>
 	<li>However, in general, git reset is used to move branch tips around and optionally alter the working directory via one of its many flags (e.g., --mixed or --hard).</li>
 	<li>Dangling commits are those that cannot be reached from any branch and are thus in danger of being lost forever.</li>
 	<li>The reflog is a chronological listing of our history, without regard for the repository’s branch structure. This lets us find dangling commits that would otherwise be lost from the project history.</li>
 	<li>At the beginning of each reflog entry, you’ll find a commit ID representing the HEAD after that action.</li>
 	<li>The -n 4 parameter tells Git to show only the last four commits from the current HEAD , making it the equivalent of the HEAD~4..HEAD syntax shown above.</li>
 	<li>The new --stat flag includes information about which files have been changed in each commit.</li>
 	<li>It’s important to realize that Git uses the tip of a branch to represent the entire branch. That is to say, a branch is actually a pointer to a single commit — not a container for a series of commits.</li>
</ul>
<h2>Chapter 8: Remotes</h2>
<ul>
 	<li>Again, we’re developing this in a branch as a best-practice step: our master branch is only for stable, tested code.</li>
 	<li>When you clone a repository, Git automatically adds an origin remote pointing to the original repository, under the assumption that you’ll probably want to interact with it down the road.</li>
 	<li>The git remote add command is used to bookmark another Git repository for easy access.</li>
 	<li>Remote branches are always listed in the form &lt;remote‑name&gt;/&lt;branch‑name&gt; so that they will never be mistaken for local branches.</li>
 	<li>Fetching and pushing are almost opposites, in that fetching imports branches, while pushing exports branches to another repository.</li>
 	<li>I said that git fetch and git push are almost opposites because pushing creates a new local branch, while fetching imports commits into remote branches.</li>
 	<li>So, as a general rule, you should never push into another developer’s repository.</li>
 	<li>An important property of git push is that it does not automatically push tags associated with a particular branch.</li>
 	<li>That said, it’s important to note that remotes are for people, whereas branches are for topics. Do not create separate branches for each of your developers — give them separate repositories and bookmark them with git remote add. Branches should always be for project development, not user management.</li>
</ul>
<h2>Chapter 9: Centralized Workflows</h2>
<ul>
 	<li>A central repository is only supposed to act as a storage facility — not a development environment.</li>
 	<li>After merging into master as we normally would, git push updates the central repository’s master branch to reflect our local master.</li>
 	<li>This brings us to the most important rule to remember while rebasing: Never, ever rebase commits that have been pushed to a shared repository.</li>
 	<li>It seems that Git won’t let anyone push to a remote server if it doesn’t result in a fast-forward merge.</li>
 	<li>Typically, you’ll want to rebase your changes on top of those found in your central repository. This is the equivalent of saying , “I want to add my changes to what everyone else has already done.” As previously discussed, rebasing also eliminates superfluous merge commits.</li>
</ul>
<h2>Chapter 10: Distributed Workflows</h2>
<ul>
 	<li>Never blindly merge content from a third - party contributor.</li>
 	<li>You’ll never have to worry about security using an integrator workflow because you’ll still be the only one with access to the “official” repository.</li>
</ul>
<h2>Chapter 11: Patch Workflows</h2>
<ul>
 	<li>A patch file represents a single set of changes (i.e., a commit) that can be applied to any branch, in any order. In this sense, the patch workflow is akin to interactive rebasing , except you can easily share patches with other developers.</li>
 	<li>While you don’t have to know the ins-and-outs of diffs to make use of patches, you do need to understand that a single patch file represents a complete commit.</li>
 	<li>The git am command takes a patch file and creates a new commit from it.</li>
 	<li>The git am command is configured to read from something called “standard input,” and the &lt;character is how we can turn a file’s contents into standard input.</li>
 	<li>Whereas remote repositories are a way to share entire branches, patches are a way to send individual commits to another developer.</li>
</ul>
<h2>Chapter 12: Tips &amp; Tricks</h2>
<ul>
 	<li>Removing the .git directory removes all version control information, and you’re left with a single snapshot of your project.</li>
 	<li>Similar to the git archive command, git bundle turns a repository into a single file. However, in this case, the file retains the versioning information of the entire project.</li>
 	<li>Bundles are a great way to backup entire Git repositories (not just an isolated snapshot like git archive). They also let you share changes without a network connection.</li>
 	<li>Each file or directory stored in .gitignore will be invisible to Git.</li>
 	<li>You can also specify entire directories in .gitignore or use the * wildcard to ignore files with a particular extension.</li>
 	<li>The git stash command hid these changes, giving us a clean working directory. We’re now able to switch to a new hotfix branch to make our important updates — without having to commit a meaningless snapshot just to save our current state.</li>
 	<li>Whereas patches represent a committed snapshot, a stash represents a set of uncommitted changes. It takes the uncommitted modifications, stores them internally, then does a git reset --hard to give us a clean working directory.</li>
 	<li>A hook is a script that Git executes every time a particular event occurs in a repository.</li>
 	<li>The git reset we’re accustomed to moves the current branch to a new commit and optionally updates the working directory to match. But when we pass a file path, git reset updates the staging area to match the given commit instead of the working directory, and it doesn’t move the current branch pointer.</li>
 	<li>If we add a file path to git checkout, it narrows its focus to only the specified file and does not update the branch pointer.</li>
 	<li>Passing a file path to git checkout reverts that file to the specified commit.</li>
</ul>
<h2>Chapter 13: Plumbing</h2>
<ul>
 	<li>This is the complete representation of a commit: a tree, a parent, user data, and a commit message.</li>
 	<li>A tree object is Git’s representation of the “snapshots” .</li>
 	<li>They record the state of a directory at a given point, without any notion of time or author. To tie trees together into a coherent project history, Git wraps each one in a commit object and specifies a parent, which is just another commit. By following the parent of each commit, you can walk through the entire history of a project.</li>
 	<li>So, blob objects are how Git stores our file data, tree objects combine blobs and other trees into a directory listing, then commit objects tie trees into a project history.</li>
 	<li>Note that blobs are pure content: there is no mention of a filename in the above output. That is to say, the name blue.html is stored in the tree that contains the blob, not the blob itself.</li>
 	<li>Since two blobs with the same data will have the same ID, Git must share blobs across multiple trees.</li>
 	<li>By not creating duplicate blobs for each tree object, Git vastly reduces the size of a repository.</li>
 	<li>That’s right, a branch is just a reference to a commit object, which means we can view it with a normal git cat-file.</li>
 	<li>Each object, regardless of type, is stored as a file, using its SHA-1 checksum as the filename (sort of). But, instead of storing all objects in a single folder, they are split up using the first two characters of their ID as a directory name.</li>
 	<li>The git gc command only changes Git’s storage mechanism — not the contents of a repository. Running git gc every now and then is usually a good idea, as it keeps your repository optimized.</li>
 	<li>The index is Git’s term for the staged snapshot.</li>
 	<li>The git commit-tree command creates a commit object from a tree and a parent ID, while the author information is taken from an environment variable set by Git.</li>
 	<li>Remember that Git is merely a tool for tracking your files, not a cure-all for managing software projects. No amount of intimate Git knowledge can make up for a haphazard set of conventions within a development team.</li>
</ul>
