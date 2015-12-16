---
layout: post
title:  "Git Tutorial"
date:   2015-12-04 03:38:55 -0800
categories: Preparation
permalink: /git-tutorial/
---

Chances are you already have git running on your computer or you at least have heard of Git before. For this training, you will need to know few basics about git.

#### Table of Contents
- [Git Tutorial](#git-tutorial)
    - [Get Git](#get-git)
    - [Fork a Repository to your Account](#fork-the-repository-to-your-account)
    - [Clone a sample node app Repository to your Machine](#clone-the-case-study-repository-to-your-machine)
    - [Creating a new Branch for your repo](#creating-a-new-branch-for-your-repo)
    - [Staging your Changes for a Commit](#staging-your-changes-for-a-commit)
    - [Commit your Changes](#commit-your-changes)
    - [Push your new Branch to Your Fork on GitHub](#push-your-new-branch-to-your-fork-on-github)

### Get Git
If you don't have Git installed, head over to the official [Git Download page and download it](https://git-scm.com/download). 

#### Get Git for Mac
There are several ways to install Git on a Mac. You can choose from one of the following ways:

1. If you want a more up to date version, you can also install it via a binary installer. An OSX Git installer is maintained and available for download at the Git website, at http://git-scm.com/download/mac.

2. If you already have Homebrew, you can install Git by executing:

```
$ brew install git
```

Make sure you update your `$PATH` environment variable to include the latest install path of Git. For example:

```
$ echo 'export PATH="/usr/local/bin:/usr/local/sbin:~/bin:$PATH"' >> ~/.bash_profile

```

3. If you don't mind registering an apple developer account, then install the Xcode Command Line Tools. Go to connect.apple.com and register an Apple Developer account. Once you’ve registered, go to developer.apple.com/xcode, then click on “View downloads” and finding the appropriate command line tools for your version of OS X in the list. When your download finishes, go ahead and open the DMG.
Run the Command Line Tools installer. On Mavericks (10.9) or above you can do this simply by trying to run git from the Terminal the very first time. If you don’t have it installed already, it will prompt you to install it. 

#### Get Git for Windows
If you're already using Chocolatey or Windows 10's package manager to install software, you can simply run the following command from an elevated PowerShell (right click, select 'Run as Administrator'):

```
cinst git.install
cinst poshgit

# Restart PowerShell / CMDer before moving on - or run
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")

cinst git-credential-winstore
cinst github
```

### Sign up for a Free GitHub account
Before we can get started, you need to register with GitHub for a free account. Either create or login into your account on [GitHub](https://github.com/join).

### Fork the Repository to your Account
Now you are ready to do more with Git. Let's start with a sample project. Head over to the [?](https://github.com/?) repository and click the little 'fork' button in the upper right.

![Fork the repo](https://raw.githubusercontent.com/ritazh/devopsfun/gh-pages/tutorial/fork.png)

This will create a copy of the repository as it exists in the `?` organization into your own account.

### Clone the Repository to your Machine
Visit your fork (which should be at github.com/{your_name}/?) and copy the "HTTPS Clone URL". Using this URL, you're able to `clone` the repository, which is really just a fancy way of saying "download the whole repository, including its history and information about its origin".

![Clone the repo](https://raw.githubusercontent.com/ritazh/devopsfun/gh-pages/tutorial/clone.png)

Now that you have Git installed, open up PowerShell on Windows or terminal on Mac. If everything worked correctly, you should be able to run `git --version`. If that works, navigate to a folder where you'd like to keep the `?` repository. To get a copy of your fork onto your local machine, run:

```
git clone https://github.com/{YOUR_USERNAME}/?
```

This should generate output that looks roughly like this:

```
$ git --version
git version 1.9.5.msysgit.1
$ git clone https://github.com/{YOUR_USERNAME}/?
Cloning into '?'...
remote: Counting objects: 1027, done.
remote: Compressing objects: 100% (4/4), done.
Receiving objects: 100% (1027/1027), 16.02 MiB | 9.11 MiB/s, done.
emote: Total 1027 (delta 0), reused 0 (delta 0), pack-reused 1023R
Resolving deltas:   5% (30/531)
Resolving deltas: 100% (531/531), done.
Checking connectivity... done.
```

You can run `explorer .` from PowerShell on Windows or `open .` from Terminal on Mac to open up the folder in Explorer or Finder respectively. All the files are there - including the history of the whole repository. The connection to your fork (`your_name/?`) is still there. 

### Creating a new Branch for your repo
In modern Git development, every single change that you want to make to the code base will be made in a "branch". Like a tree branch, the branch is "based" on a different branch, and unlike other SCM systems, Git branches are very lightweight. In our case, your base branch will always be `master`, which is the default branch name for GitHub repositories. In order to create a new branch, you can always run:

```
# This makes sure that your new branch is based on master
git checkout master
# This creates the new branch
git checkout -b my-new-branch
```
You can now go ahead and make your changes - adding files, writing code, fixing typos. Keep in mind that a branch should host isolated changes. You should create one branch that fixes typos; and another branch for each feature you want to implement.

### Staging your Changes for a Commit
Now that you made your changes, you can "stage" them for a commit. Whenever you stage a file for a commit, you make a snapshot of the file at the time you're staging it for a commit. If you change a file after you staged it, you will have to stage it again. To stage a file, simply run:

```
git add ./path-to/my-file.md
```

If you just want to stage all files in your current repository (including deletions), run:

```
git add --all .
```

### Commit your Changes
Now that your changes have been staged, we're ready to commit them. You can either pass the commit command a title for your commit - or omit the parameter, in which case Git will open up the default text editor to create a commit message.

###### Hint: Changing the Default Editor
The default editor will most likely be Vim. If you don't like that, use [GitPad](https://github.com/github/GitPad) - it'll make sure that you can edit all your Git messages with whatever editor is associated with `txt` files.

To commit the quick way:
```
git commit -m "Add new feature: Git is cool"
```

To commit the long way, allowing you to define both title and message of your commit:
```
git commit
```

### Push your new Branch to Your Fork on GitHub
You wrote a new feature, made some changes, committed - now we have to make sure that your changes also end up on GitHub. To do so, we have to push your local branch to your fork on GitHub. Run the command below (obviously using the name of the branch you want to push)

```
git checkout NAME_OF_YOUR_BRANCH
git push -u origin NAME_OF_YOUR_BRANCH
```

### Bonus: Make a Pull Request
Now, head over to the [?/?](https://github.com/?/?) repository. In most cases, GitHub will pick up on the fact that you just pushed a branch with some changes to your local fork, assuming that you probably want for those changes to end up in the upstream branch. To help you, it'll show a little box right above the code asking you if you want to make a pull request.

![Make a Pull Request](https://raw.githubusercontent.com/ritazh/devopsfun/gh-pages/tutorial/pullrequest.png)

Click that button. GitHub will open up the 'Create a Pull Request Page'. It is a good idea to list the feature you have created or the bug you have fixed by referencing an issue #. 

As soon as you hit the 'Create Pull Request' button, it'll show up in the list of pull requests and the bots will take over.

### Bonus: Updating Pull Requests
Once people have reviewed your pull request, it is very likely that you want to update it. Whenever you update the branch in your fork, your pull request will be automatically updated.

Let's look at a scenario: You just pushed your branch (using `git push -u origin NAME_OF_YOUR_BRANCH`), went to GitHub, and created a Pull Request.

To update the PR with additional changes, edit your files in your branch - then, commit the changes and push them to GitHub:

```
git checkout NAME_OF_YOUR_BRANCH
# Make changes, stage all changes for commit
git add --all .
# Commit
git commit
# Push to GitHub
git push
```

If you want to update your Pull Request without creating a new commit, you can "amend" your last commit. To do so, call `git commit` with the `--amend` parameter and force-push the result to GitHub, overwriting the previous version.

```
git checkout NAME_OF_YOUR_BRANCH
# Make changes, stage all changes for commit
git add --all .
# Commit
git commit --amend
# Push to GitHub
git push -f
```
### Bonus: Squashing Commits
You should commit often. It's a great practice to backup in case you mess up. At the same time, you don't want your pull request to contain all your commit history. In general, a pull request should contain one commit to keep upstream project clean. For that to happen, we need to rewrite history.

Rewriting Git history is a little bit scary, but it's easy to do. Here's the setup: You just made six commits to your branch. Before making a pull request, you want all those commits to be turned into one. To change the history of your last six commits, run:

```
git rebase -i HEAD~6
```

It is important that you change only commits that *you* made, since your branch will not be compatible with "upstream" if you rewrite history that is already present in the repository there. You can however mess with your own fork as much as you want to, since you should be the only person working with it.

Once you run the command, you will be presented with a screen that looks like this:

```
pick 4a67852 Update interactions.js
pick e9c1c12 Further Mini-JS Optimizations
pick 676adb6 Listener is always undefined
pick 6e8ba27 Automated Jekyll Deployment
pick fc0c120 Remove Gemfile Lock
pick 1cd833d Fix Deployment Folder
```

See how every single commit begins with the word `pick`, followed by its commit id and the title? You can replace the `pick` with an action of your choice. Available are:

 * `p`, `pick`: use commit
 * `r`, `reword`: use commit, but edit the commit message
 * `e`, `edit`: use commit, but stop for amending
 * `s`, `squash`: use commit, but meld into previous commit
 * `f`, `fixup`: like "squash", but discard this commit's log message
 * `x`, `exec`: run command (the rest of the line) using shell

In order to squash all six commits into the very first one you made, you would change the file to:

```
pick 4a67852 Update interactions.js
fixup e9c1c12 Further Mini-JS Optimizations
fixup 676adb6 Listener is always undefined
fixup 6e8ba27 Automated Jekyll Deployment
fixup fc0c120 Remove Gemfile Lock
fixup 1cd833d Fix Deployment Folder
```

Then, once you're done, update the branch on your own fork in GitHub. Push with the `f` parameter (force), telling Git to overwrite whatever GitHub has in the branch:

```
git push -f
```

If you never pushed the branch before, you can use the normal push command - there's no history that we need to overwrite with the `f` paramter.

```
git push -u origin NAME_OF_YOUR_BRANCH
```

### Bonus: Syncing Your Fork

After some time, you'll find that your fork has become out of sync with the upstream repository (as others add features and bug fixes and they get merged in). To sync your fork up, you just need to do a local rebase and then push those changes. There are few different ways to do this, but this is one that helps you rebase when syncing with the latest from upstream:

```
# Now make sure you're on master - the main branch for this project
git checkout master
# Get all of the latest from upstream master branch
git pull upstream master
# Push latest from local master branch to remote master
git push origin master
# Checkout your own branch
git checkout NAME_OF_YOUR_BRANCH
# Rebase in the changes from upstream master to your feature branch
git rebase master
# And then push those to your feature branch on your fork on GitHub
git push -f origin NAME_OF_YOUR_BRANCH
```