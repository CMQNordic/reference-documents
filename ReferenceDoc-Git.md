
<p align=right><a align=right href="#https://github.com/CMQNordic/reference-documents#reference-documents">↩ main menu</a></p>

<h1 id="git">Reference Guide - Git</h1>

This is a reference document with usefull information about git. 
Written while learning for educational purposes and for quick reference and look-up. 
<br> 
<br>
<p align=right>Written by Martin Czerwinski ®CMQ Nordic AB</p>
   
---
<p id="table-of-content"></p>

### **TABLE OF CONTENT**

- [**What is Git and why from command line?**](#what-is-git)
- [**Shortly on how git works and how to get started**](#general-basics)
- [**Useful Git commands:**](#useful-git-commands-m)<br> [Help, info & status](#info-status-commands) ◦ [Initial configuration](#configuration-commands) ◦ [Create a local repo](#create-new-repo-commands) ◦ [Check out a branch or file](#check-out-branch-commands) ◦ [Stage & commit](#stage-commit-commands) ◦ [Undo & rollback](#undo-correct-commands) ◦ [Create/delete a branch](#create-new-branch-commands) ◦ [Remote connections](#remote-connections-in-git) ◦ [Merge & rebase](#merge-rebase-commands) ◦ [Handling conflicts & Logs](#diff-logs-commands)
- [**Common Git expressions:**](#common-expressions)<br> [Type of files in Git](#files-in-git) ◦ [Cloning](#cloning-in-git) ◦ [Check-out & change branches](#check-out-change-branches) ◦ [Working directory](#working-directory) ◦ [Clean working directory](#clean-working-directory) ◦ [Stage](#stage) ◦ [Commit](#commit) ◦ [Commit Hash & Tag](#commit-hash-tag) ◦ [Stashing files](#stashing-files) ◦ [Working tree](#working-tree) ◦ [Stage or Index](#stage-or-index) ◦ [Repo history](#repo-history) ◦ [Remote](#remote) ◦ [Git Branch](#git-branch) ◦ [Tracking relationship](#tracking-relationship) ◦ [Local&nbsp;branch&nbsp;& Tracking&nbsp;branch&nbsp;& Remote&#8209;tracking&nbsp;branch](#local-branch) ◦ [Remote & Upstream branch](#remote-branch) ◦ [HEAD](#head) ◦ [Detached HEAD](#detached-head) ◦ [Merge & Rebase](#merge-rebase) ◦ [Fetch & Pull](#fetch-pull) ◦ [Push](#push) ◦ [Merge Conflicts](#merge-conflict) ◦ [Unrelated Histories errors](#unrelated-histories-error) ◦
- [**Useful Git aliases**](#useful-git-aliases-m)
- [**Useful Cmd commands**](#useful-cmd-commands-m)
- [**Example of an .gitignore file**](#git-ignore-file-m)

---

</nav>

<p align=right><a id="what-is-git" align=right href="#table-of-content">↩ Back To Top</a></p>

## **What is Git and why use it from command line?**

[Git](https://git-scm.com/) is the most popular version control system used for tracking changes in code during software development. Git is a distributed system meaning that your local version of the repository has all the same features as the central remote repository. You can work with your clone of content on you local machine, without internet access, independently from others. When connected to central repository you can in an easy manner push your changes to central remote repository. VSCode editor has an integrated graphical interface for git but we still recommend to get familiar with and memorize frequently used commands and understand the most [common git expresions](#common-expressions). At workplaces around the world it is often required to run git commands from a command line.

Some recommended tutorials to gest started:  
Introduction to Git - Core Concepts [here](https://www.youtube.com/watch?v=uR6G2v_WsRA '30 min, Core concepts')  
Introduction to Git - Branching and Merging [here](https://www.youtube.com/watch?v=FyAAIHHClqI&t=1233s '30 min, Branch & merges')  
Introduction to Git - Remotes [here](https://www.youtube.com/watch?v=Gg4bLk8cGNo&t=7s '30 min , Remotes')  
Good article explaining merging and rebasing: [here](https://www.atlassian.com/git/tutorials/merging-vs-rebasing 'Merging And Rebasing explained')

<br>

<p align=right><a id="general-basics" align=right href="#table-of-content">↩ Back To Top</a></p>

## **Shortly on how git works and how to get started**

There are 2 ways of starting to work on a project with git. This is equivalent to creating a **local repository** as there is where git saves all changes done to your files in a directory on a local computer.

1. One way of creating an new empty git repository from is by running `git init` in from a command window in a folder on your local machine. Then you can start adding files and folders to this folder and subsequently "commit" all those new files and changes into git. Then those are not any saved but controlled by git running on your local machine and can be restored. Such a local repository has a _.git_ folder in its root where all history of changes done to that folder (called "working directory") is saved.
2. Another way is byn cloning an existing project (remote repository). Then we download all versions of files to our local folder. In git world it is called "cloning". A connection between our local and remote repository is then automatically established. After the changes are and done and locally committed (saved in git locally) than those changes can be easily uploaded (pushed) back to remote repository.

When you add new files folders you project those changes are defined by git as "untracked" modifications because they have never been saved within git (they have been saved with normal save on the file system). In order to commit the change or several changes to several files at once, meaning permanently save them into git with a "label") you should first **stage** them. When changes you are ready and tested in "staging state" you do commit them to local git history, all at once. Once a new file been staged or committed at least one time it is not longer "untracked", it is then "tracked" by git. In order to be sure not ever loose those changes or to share them with other we then can puch those to a remote git repository in i.e. github.

There are **branches** with **commits** in git. A commit is a labled group of all changes at a given moment. To differantate diffrent commits, for example for diffrent product releases we have diffrent branches.The default branch name usually by default created by Git is called master. Note that is can be forced to be called something else i.e. main. When you create a new git repository you get automatically a master branch created on your system and by default it has no commits. At a commit (your group all changes) git gives then a unique hash, a unique number. Next time you commit changes to same branch, the commit is added on top of the previous one, and so on. Often in git world you head HEAD and it is is a reference (a pointer) to the last commit in the current check-out branch. By default it moves automatically to point to the commit that you "see" in you working folder on you computer that you work with.

When you work on a feature you normally create your own branch that originates (forks out) from a certain commit on i.e. master. Then your work is done in an isolated environment on your own branch and you do not interfare with others, white master branch might live its own life with new commits from others meanwhile. When you are done with implementation on your local branch, then you commit, update with latest changes from originating branch (merge updates) and then you can merge your your changes to master and git do automatically a merge with whatever changes might have happened there in same feature back to that main branch you forked from. There might be merging conflicts in case you changed a piece of code on your branch and someone changed exactly same piece of code. <br><br> Download a cheat-sheet with some git commands [here](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)

<br>

<p align=right><a id="useful-git-commands-m" align=right href="#table-of-content">↩ Back To Top</a></p>

## **Useful Git commands**

---

Here comes a short summary of those most common git commands.

##### **TABLE OF CONTENT**

- [Help, info & status](#info-status-commands) - _Informative and help related commands, not doing anything._
- [Initial configuration](#configuration-commands) - _Configuration done before getting started._
- [Create a local repo](#create-new-repo-commands) - _Create or clone existing repo._
- [Check out a branch or file](#check-out-branch-commands) - _How to check out a branch or file_
- [Stage & commit](#stage-commit-commands) - _What to do after changes are done._
- [Undo & rollback](#undo-correct-commands) - _Rolling back changed and removing files._
- [Create/delete a branch](#create-new-branch-commands) - _Creation of a new branch_
- [Remote connections](#remote-connections-in-git) - _How to modify connecttion and its url_.
- [Merge & rebase](#merge-rebase-commands) - Merge and rebase
- [Handling conflicts & Logs](#diff-logs-commands)

<br>

![most common git commads](https://raw.githubusercontent.com/CMQNordic/MyReferenceGuides/main/assets/git/git-1.jpg)

<br><br>

| Help,&nbsp;Info&nbsp;&&nbsp;Status&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | <a id="info-status-commands" href="#useful-git-commands-m" title="Back to top">↩</a> |
| :-- | :-- |
| `git --version` | Prints current git version. `git` list all commands. |
| `git [command] -h (--help)` | Prints help, -h for short help while --help for extensive help in new online window. |
| `git config --list` | Prints current git configuration. |
| `git status` | Prints current repo status. |
| `git remote -v` | Prints all remote connections with name and url (used for push/pull). |
| `git branch -a -vv` | Prints all branches (include remote tracking branche with corresponding upstream status). Read more [here](#remote-and-upstream-branches-in-git). |
| `git log --all --oneline --graph -5` | Prints 5 commits from top of the branch (thanks to --all), each on one line in nice graph. Easy to see hashes and where HEAD and remote tracking branches point to in the history tree. Apply for specific file only by `git log --all --oneline -5 <file-name>`. Note if --all is skipped only 5 from HEAD down would be printed but in detached HEAD state we want to see the top of the branch and then --all is necessary. |
| `git diff --staged <file>` | Prints changes in a file between staging area and committed in git history. If `--staged` is not used then comparison is made between working tree and staging area. |
| `git branch --no-merged` | Prints branches that are not merged. Use `--merged` to list opposite. |

<br>

| Initial&nbsp;configuration&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | <a id="configuration-commands" href="#useful-git-commands-m" title="Back to top">↩</a> |
| :-- | :-- |
| `git config --global user.name [your-name]` | Sets desired name used to be in commits (shown to others). |
| `git config --global user.email [your-email]` | Sets desired email used in commits (shown to others). |

<br>

| Create&nbsp;a&nbsp;local&nbsp;repository&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | <a id="create-new-repo-commands" href="#useful-git-commands-m" title="Back to top">↩</a> |
| :-- | :-- |
|  | There are two ways of creating a local repo on your machine. Either a new empty from scratch or copy already existing one. In both ways a branch called "master" will be created locally in background. In case you clone existing repo from remote branch files will be automatically checked out. That means that they will become visible and editable in your your working directore (your project folder controlled by git).<br><br>**Flow 1: Create a new empty local repo: (init)** |
| `git init` | Converts a normal folder to a new local git repository when run in such a folder. No need for folder to be empty. To create the repo in a new sub-folder use `git init <folder-to-be-created>` |
| `git remote add <connection-name> <remote-git-url>` | Adds new remote (i.e origin) and sets its url (i.e. to github repo). To change url only use `git remote set-url <connection> <url>`. To delete connection use `git remote remove <connection>`. Result can be checked with `git remote -v`. <br> Example:<br> `git remote add origin https://url.git` |
| `git push -u <remote-connection> <branch-to-push>` | After adding some changes push (upload) all local files to remote repo. The `-u` flag shall be used first time to force git not only to create a remote-tracking branch but also connect an upstream. Read more [here](#remote-and-upstream-branches-in-git). |
|  | When cloning existing remote repo Git automatically creates a local "master branch", a "remote connection" named "origin" and sets belonging "remote url" (where we clone from) automatically. Additionally a local "_remote-tracking branch_" (usually called "origin/master") is created in background and to be used by the local _master_ branch as its "upstream" so no parameters needed to be used in subsequent push/pull commands. (read more about it here TODO). If not differently instructed by default clone command will check-out that branch which in remote is marked with HEAD - usually _master_. If different branch or commit is desired to be checked out after our clone then add `-b <branch-name-to-check-out>` (read more about it here TODO)<br><br>**Flow 2: Clone existing repo from remote:** |
| `git clone <remote-url> .` | **Clones whole remote repo** into a empty folder (the one you run the command in) on your local machine. Remote repo is copied with ALL its branches and all diffrent versions of all files. This command do much in background i.e. creates "remote connection", "remote tracking" branch and checks out files. Files that are then checked out are from commit marked with HEAD on active branch in remote (usually latest commit on master or main branch). If a new folder shall be created in the folder you run the command in - then just skip the dot`.`<br><br>Note! Clone (and fetch) sets in background a "remote connection" (usually by default called"origin") and creates a "remote tracking branch" (usually by default called "origin/master"). |
| `git clone <remote-url> . --single-branch` | **Clones only one branch from a remote repo** into an empty folder we run this in. Files that are then checked out are from commit marked with HEAD on active branch in the remote. The branch that is cloned is only the specified one. This is usefull as sometimes we do not want to copy all branches for huge projects but only the branch of interest. Note! If you wish to clone not active branch in remote but a branch a specific name then you must specify it by adding `-b <remote-branch-name>` at end of this command. |
| `git branch -a -vv` | Control the result and print created branches. |

<br>

| Check&nbsp;out&nbsp;a&nbsp;branch&nbsp;or&nbsp;file&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | <a id="check-out-branch-commands" href="#useful-git-commands-m" title="Back to top">↩</a> |
| :-- | :-- |
|  | The files we see and can edit (files in our working directory) are from a branch that is checked out. We can check out another branch and it can be done with "check out" command. It results in overwriting files we see and can edit with other versions. If we have changes in working tree or staged changes that are not committed then checking out of onther branch **will fail** as we can switch branch only with a clean working directory. Therefore we first must commit all our changes or stash them.<br><br>Important to understand is that `git checkout -- .` works a bit differently. It will always OVERWRITE whatever is changed but not staged (or committed) in our working tree. Then your changes will lost. This command is used to make sure all files in out working direcory are those in latest commit (or staging area) on the branch we are on.<br><br> To check out from previous commit use `git checkout HEAD^` or from 2 commits before the latest commit use `git checkout HEAD~2`. |
| `git checkout -- .` | **Overwrites all changes in working tree.** Overwrites all saved changes in working tree with those that we have in stage are or latest commit in branch we are currently on. Can be used to clear or reset the working directory. Important! Not committed or staged changes will be lost! |
| `git checkout <other-branch>` | **Checks out latest commit on other branch**. Working tree and stage area must be clean otherwise this fails. |
| `git checkout -b <new-branch>` | **Creates new branch & checks it out**. Forking out from current HEAD (= tip of the branch we are currently on). To fork out from latest commit on another branch use `git checkout -b <new-branch> <from-branch>`. |
| `git checkout -- <file-name>` | **Checks out latest committed version only of a single file** from the branch we are on. If the file shall be checked out from a special tag use `git checkout <hash> -- <file>`. To check out file from previous commit use `git checkout HEAD^ <file-name>`. If the file shall be checked out from 2 commits before the latest commit we can use `git checkout HEAD~2 -- <file-name>`. |

<br>

| Stage&nbsp;&&nbsp;Commit&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | <a id="stage-commit-commands" align=left href="#useful-git-commands-m" title="go to top">↩</a> |
| :-- | :-- |
|  | Files and folders that are newly added are by git classified as "untracked" and must first be staged before they can be committed. The normal workflow is to finsh the changes ans normal save. Then when files are ready add then into stage area (stage the files) to finally from stage all at once commit the changes to git repo history. |
| `git add . (or <file>) ` | Stages all files (or defined one) from working tree to index (stage). |
| `git commit -m "txt"` | Commits all files from stage. note only those in stage are committed. |
| `git commit -am "txt"` | Commits all changed files from **both** working tree and stage. Bypasses stage. NOTE! But untracked (new) files are not included, those must be staged first. |

<br>

| Undo&nbsp;&&nbsp;Rollback&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | <a id="undo-correct-commands" align=left href="#useful-git-commands-m" title="go to top">↩</a> |
| :-- | :-- |
|  | There are different ways to undo saved, staged or committed changes. Note! Newly added files and folders are untracked before staged and therefore removed in slightly different way. Importan when unrolling changes is to have clean working space or at least be sure that same file is not modified in layes we roll back to, otherwise the changes can be lost! |
| `git restore . (or <file>)` | **Roll back unstaged file(s).** Permanently delete changes in all files (or defined one) from working area. Important! Changes in working tree will be permanently deleted (but not the staged once, those are untauched)! `git checkout -- . [or <file>]` does the same thing. |
| `git restore --staged . (or <file>)` | **Roll back staged file(s).** Moves changes in all files (or defined one) from staging area to working tree. Important! Clean working tree (or make sure same file is not modified in both places) otherwise you will loose staged changes if same file is modified in working tree! `git reset . (or <file>)` does the same thing. |
| `git checkout <hash> -- <file>` | **Recover a file from earlier commits.** Moves status of a fiule in a certain commit to working tree and staging area. Usually 6 first digits of hash are enough to provide. |
| `git reset --soft HEAD^` | **Roll back latest commit.** Undo last commit (updates HEAD one step down) and moves all commited changes to stage. Important! Clean stage index (or make sure same file is not modified in both places) otherwise risk to loose commited changes if same file as we roll back is modified in stage! |
| `git reset --hard ` | **Delete all uncommited changes.** Deletes all changes in files that are not commited. Clears **BOTH stage** and **working tree**. Importan! All changes are permanently deleted. Note! Files in ".gitignore" and "untracked" remain untouched. |
| `git clean -fd . (or <file>)` | **Delete untracked file(s).** Deletes all newly added "untracked" files (and folders due to -d) (or defined one) from working tree and filesystem. Note! Run ALWAYS first with -n flag set to control what would be removed. |
| `git reset HEAD^`<br>and<br>`git checkout --` | **Roll back to previous commit** Replaces all file in our working directory with the once in previous commit. The first command undo latest commit and moves all changes (including staged ones) to working tree (aka index). HEAD is subsequently moved to point to previous commit. The second command overwrites everything in working tree with code in latest commit (the one that HEAD now points at). Important! All changes in working are will be permanently deleted. |
| `git commit --amend -m "txt"` | **Correct commit message** Updates the message on latest commit. |
| ` git rm <file-name> -f` | **Delete tracked file(s).** Deletes a file from the project. Only for files that are tracked (has been commited at leased once). Differs from `git clean` as it will only delete it if file's actually untracked. Note! that the file is deleted from working tree and index but this is a change and is in staging area. To complete permanently delete the file this change must be commitet. |

<br>

| Create/delete&nbsp;a&nbsp;&nbsp;branch&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | <a id="create-new-branch-commands" href="#useful-git-commands-m" title="Back to top">↩</a> |
| :-- | :-- |
|  | Common to creation of a branch is that the new branch originates from latest commif (HEAD). |
| `git branch <new-branch>` | **Create. No check out.** Creates new branch originating from HEAD on branch we are on. Does NOT check out any files, meaning it does not change anything in working tree (working directory), HEAD still points to same commit as before. |
| `git branch <new-branch> <hash-or-tag>` | **Create. No check out.** Creates new branch originating from a specific hash or tag. Does NOT check out any files, meaning it does not change anything in working tree (working directory), HEAD still points to same commit as before. |
| `git checkout -b <new-branch-name>` | **Create and check out.** Creates new branch originating from HEAD on branch we are on and check out newly created branch. |
| `git branch -d <branch-name>` | **Deletes a brancht.** You can not delete a branch while you have it checked out. You can not delete a branch if it is not merged (unless you used forced delete with -D). If the branch has uncommited changes it will not allow a merge unless you use `-D` (forced merge) insted of` -d`. |

<br>

| Remote&nbsp;connections&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | <a id="remote-connections-in-git" href="#useful-git-commands-m" title="Back to top">↩</a> |
| :-- | :-- |
|  | A "remote connection" is in git world a connection with a url pointing to a remote repo. It has a name/alias in so we can simply refer to it i.e. "origin". When we fetch data from a remote repository for the first time then git, in background, adds a "remote connection" to our local repo (view it with `git remote -vv`). Git names it by default "origin" simply becouse the data we are fetching for the first time originates from there. Therfore we can simply refer to this connection by its short name (alias) insted of having to write out long url every time. We can have several connections added and with `remote add` command we can manualy add a connection with our self-defined name and url. We can also change a name or url of existing connections.<br><br>A clone command do internally a fetch, therfore after a clone we do not need to add connection manually as git adds a connection "origin" in the background by default.<br><br> Use `git remote -v` to list all existing connections. |
| `git remote add <connection-name> <remote-url>` | Add new remote connection with given name (alias) and url. |
| `git remote remove <connection-name>` | Delete a remote connection |
| `git remote set-url`<br>`<connection-name> <remote-url>` | Changes url for an existing remote connection. If it does not exist then it must forst be created (added). |
|  | **Synchronize local repo with remote:**<br><br>While we work on files localy in our repo on a branch, others might commit changes to same branch in remote. Commands `fetch`, `pull` and `push` are used for synchronizing with remote. Git do not know that someone might have updated something in remote, we must instruct git to download those changes and there where those commands are used.<br><br>Before we can upload (push) our committed changes to remote we must make sure that our local branch is up-to-date with remote, otherwise the push command will fail. This because push command do not perform any merge at target destination. We must first fetch the changes from remote, do merges is necessary (or rebase) locally and afterwards we can push it all back to remote.<br><br>**Note!** "Git pull" runs two different git commands in background (fetch & merge). You're better off, until you are well-experienced, to use separate "git fetch" and "git merge" commands. Make sure to have a clean working directory here.<br><br>**Note!** If we push to a branch to remote that do not exist in remote then such a branch is created in remote (same when we fetch).<br><br>**Note!** When do clone or pull then git automatically creates a new internal branch names "origin/master". This is used to mirror the same branch (here master) in remote and it is this branch only that is updated when we go a fetch. Therfore we must manually merge commits from this branch to our in ardet to get changes from remote. |
| `git fetch <from-remote><branch>` | Fetch commits from a remote connection i.e. `git fetch origin master`. If we have only one remote connection and are currently on master we can just write `git fetch` to do same thing.We can securily run this command even if we have unstaged or uncommitted changed in our working directory.<br><br>Note! Downloaded changes will not be visible in our working directory by default as fetch do not perform any merge but just updates a "remote tracking branch". We must manualy trig a merge with `git merge <remote-tracking-branch> in order to update our working directory with fetched changes. |
| `git pull <from-remote><branch>` | Fetch commits from a remote connection, do merge and check out the changes in our working directory i.e. `git pull origin master`. If we have only one remote connection and are currently on master we can just write `git pull` and to do the same thing.<br><br> Note! This will both update our local "remote tracking branch" and merge and check out our working directory with fetched changes. Do it only with clean working tree! |
| `git push <remote-connection-name> <branch-to-push-from>` | Pushes latest commit from a local branch to remote i.e. `git push origin master`. Here "master" might be our main local branch and "origin" the connection we cloned from. Note! in order to push we must be sure our local branch was updated with changes that might have been commited to remote. Run fetch & merge or pull previously. Remote tracking branch "origina/master" must not have any changes that are unmerged and not included in our code. This can be seen by in git graph or run `git log --oneline --all --graph -4` |
| `git push <remote-connection-name> --all` | Pushes latest commits in all existing local branches to corresponding remote i.e. `git push origin -all`. It updates remote from all branches we have locally (not only the checked out one). Note if branches do not exist in remote then those will be created. |

<br>

| Merge&nbsp;&&nbsp;Rebase&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | <a id="merge-rebase-commands" align=left href="#useful-git-commands-m" title="go to top">↩</a> |
| :-- | :-- |
|  | Both of these commands are designed to integrate changes from one branch into another branch but they do it in different ways. When rebasing you move the base of the change ending point. Merging adds a new commit to your history. Merge preserves history whereas rebase rewrites it. Rebase will present conflicts one commit at a time whereas merge will present them all at once. It is better and much easier to handle the conflicts but you shouldn’t forget that reverting a rebase is much more difficult than reverting a merge if there are many conflicts. The golden rule of git rebase is to never use it on public branches. The first step in any workflow that leverages git rebase is to create a dedicated branch for each feature. This gives you the necessary branch structure to safely utilize rebasing. If you would prefer a clean, linear history free of unnecessary merge commits, you should reach for git rebase instead of git merge when integrating changes from another branch.<br><br>On the other hand, if you want to preserve the complete history of your project and avoid the risk of re-writing public commits, you can stick with git merge. Either option is perfectly valid, but at least now you have the option of leveraging the benefits of git rebase. <br><br>**Conflicts:**<br>We get merging conflicts when we a merge/rebase need our intervention. Also when pulling from remote sometimes an internal merge can fail due to conflicts. Then the pull is aborted and conflicted files are added to "working tree" and must be resolved and committed to fullfil the merge. We recommend always to start a pull/merge/rebase with empty "working tree" and "index"<br><br>First show files with git status. Then edit all conflicted files in your in i.e. VSCode. Git adds line `=======` in each "center" of the conflict. Above we find code we merge from (origin). Below is the code we merge to (local). Remove unwanted code, make sure file looks as expected, test and save. Finally commit with "`git commit`" and the merging operation will finnish. |
| `git merge <branch-to-merge-from>` | Merges latest commit from a specific branch. The branch that you merge to must be checked out. Always start the merge with crean working directory. |
| `git rebase TODO` | **TODO** |

<br>

| DIFF & LOGS<a id="diff-logs-commands" align=left href="#useful-git-commands-m" title="go to top">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |  |  |  |
| :-- | --- | --- | --- |
|  | It is easier to use graphical tools or VSCode plugins to show diffs but here are some command to use in command window. |  |  |
| `git log -4 --oneline` | Shows last 4 commits for current branch, each on one line, nicely printed. |  |  |
| `git log --all --oneline -- <file-name>` | Shows all commits for given file, each on one line. |  |  |
| `git diff -- <file-name>` **TODO** do we need -- | Show changes for a file:. **working tree** vs **index** |  |  |
| `git diff --staged -- <file-name>` **TODO** do we need -- | Show changes for a file: **index** vs **committed** |  |  |

<br>

<p align=right><a id="common-expressions" align=right href="#table-of-content">↩ Back To Top</a></p>

## **Common Git expressions**

##### **TABLE OF CONTENT**

[Repository](#repository) ◦ [Working directory](#working-directory) ◦ [Remote](#remote) ◦ [Cloning](#cloning-in-git) ◦ [Stage & Index](#stage-or-index) ◦ [Add & Commit](#add-and-commit) ◦ [Check-out a branch](#check-out-change-branches) ◦ [Filetypes](#files-in-git) ◦ [Commit Hash & Tag](#commit-hash-tag) ◦ [Stashing files](#stashing-files) ◦ [Working tree](#working-tree) ◦ [Repo history](#repo-history) ◦ [Git Branch](#git-branch) ◦ [Tracking relationship](#tracking-relationship) ◦ [Local&nbsp;branch&nbsp;& Tracking&nbsp;branch&nbsp;& Remote&#8209;tracking&nbsp;branch](#local-branch) ◦ [Remote & Upstream branch](#remote-branch) ◦ [HEAD](#head) ◦ [Detached HEAD](#detached-head) ◦ [Merge & Rebase](#merge-rebase) ◦ [Fetch & Pull](#fetch-pull) ◦ [Push](#push) ◦ [Merge Conflicts](#merge-conflict) ◦ [Unrelated Histories errors](#unrelated-histories-error)

| <a id="untracked-files">Untracked files</a><a href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp; ↩ &nbsp;&nbsp;&nbsp;</a> |
| :-- |
| when a new file is created it is moved to working tree but if it was never staged before then it is of type "untracked". That means that git command backing the change like reset or restore do not have any affect on changes in files of this type. if the file was at lease added to stage once then it is tracked!<br><br> |

| <a id="repository">Repository</a><a href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp; ↩ &nbsp;&nbsp;&nbsp;</a> |
| :-- |
| A Git repository (a repo) is a location in which git tracks changes to files and folders. A _local repository_ contain a folder named _.git_ that is placed in the root. Git stores history of changes in it.<br><br> A normal folder on our machine is not a repo, but when you run a `git init` command in this folder then it automatically is turned into a local repo with a newly created hidden .git folder in its root. It then starts tracking all changes! By deleting this ".git" folder all history will be lost and git will no longer track changes to such a folder. A _remote repository_ is usually a central repo that you can clone files from or upload your local changes to. It might be stored on a hosting services like [GitHub](https://github.com/) or [Bitbucket](https://bitbucket.org/).<br><br> You can always change the name of a local repo simply by renaming the folder on your hard drive. This do not affect anyone outside. But be aware that changing name of a remote repo on i.e. GitHub may affect persons who already use it as the old name as it is part of the URL in their local configurations. |

| <a id="working-directory">Working directory</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| A working directory is essentially your project folder, your workspace. It is a term used for all the files and folders that we can view and edit in our project folder/workspace. Expression _clean working directory_ is widely used in Git documentation. It is when there are no uncommitted changes in our working directory (not in the [working tree](#working-tree) nor in [index](#stage-or-index)(stage).<br><br> If you are in progress with some changes that are uncommitted, and are not ready to [stage](#stage) nor [commit](#commit) before checking out other branch, then you can [_stash_](#stash-files) the changes to temporally ot clean up your working directory. |

| <a id="working-tree">Working tree</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Term working tree is widely used and refers to an "area" where changes to files and folders in your working directory are saved. At same moment as a change in a file in your working directory is saved - then is added to working tree. This is the "first level" of tracking of our change and those files are called "untracked changes" as those have not been added to staging area not commited yet. Note that changes saved here can not be restored if i.e. accidentally the file is deleted. |

| <a id="stage-or-index">Staging area (index)</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Staging area is often in git documentation shortly called "index". It refers to an "area" within git where modifications are saved before they are finally _commited_. This is the "second level" of tracking of a change. From stage/index a file can be restored or a change backed to its original state. From staging area we can commit all changes to "git history" (third and final state of a change)<br><br>Note that there is a possibility in Git to commit changes directly from working tree and omit the staging area. This is done with help of commad `git commit -am <file>`.<br><br> |

| <a id="remote">Remote</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Expression "remote" is widely used in git documentation and usually refers to other repository or a remote branch, depending on the context.<br><br> A remote command in Git provides functionality for connecting of a local repo to a remote repo. Such a _remote connection_ can be created from any local repo and given a name (alias)<br><br> Git automatically creates a remote connection when we clone a remote repo to a local destination and names it then "origin". A widely used expression "fetching data from remote" means we download data from a remote repo, usually for a single branch, from url that our remote connection is configured with.<br><br> |

| <a id="cloning-in-git">Cloning</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Cloning is making a copy of a repository and saving it to another location. It is done with `git clone`command. This command also automatically checks-out the branch witch in remote is marked with HEAD. Usually it is a _"master"_ branch and therefore when we clone a remote repo then locally a branch called "`master`" is automatically created and checked out in our working directory.<br><br> |

| <a id="git-branch">Git Branch</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Consider a chain of objects connected to each other. Each object (in git called "commit" or "blob") contains a version of code labeled with an unique id. There is a start and end of this chain and latest object is at the end tip of this chain. Such a chain with connected commits is a "git branch". It start from a certain commit from another branch. A _branch_ is a movable pointer that points to latest object in this chain of commits. Every time you commit something to a branch then this branch pointer moves automatically forward to point this latest commit.<br><br> Usually when we work on a new feature we "branch out" - spawn a new branch - from the latest commit of a "parent" branch and give that new branch a special name i.e. "feat-x-branch". This because we want to encapsulate our changes while working and committing without affecting the parent branch. Finally when we are satisfied with work on our isolated "feature" branch we can update the "parent" branch. This can be done by pushing to or [pulling](#fetch-&-pull) from parent with help of merge/rebase commands - see [Merge & Rebase](#merge-&-rebase)<br><br> In more complex projects we can have hundreds of commits on dozen of branches i.e. dev-, release- or feature- branches of all kinds. Note that the first by git automatically created branch when new repo is created is by default called `master`.<br><br> |

| <a id="check-out-change-branches">Check-out a branch</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Checking out a branch (also called _changing branch_) is loading of a new specific group of files and folders into our working directory. Git overwrites all current files and folders in our working directory with the ones that we are checking out. We can check out a _branch_, a specific a _commit hash_ or a _tag_. See check-out commands [here](#check-out-branch-commands). Additionally our local HEAD pointer is moved to point toward the [_commit_](#commit) that is checked out. It is recommended to have a clean working directory when checking out.<br><br> What happens to [_uncommitted_](#files-in-git) changes when checking-out?<br> If we try to check out our current working directory while having uncommitted changes in it, then sometimes the checkout will fail. Git never overwrites your changes if there is risk to lose then. Therefore if "parent" of any modified file differs in any way from same file in the commit we aim to check out from, then Git abort the check out process. To perform a check out in such a case you must either [_commit_](#commit), restore or [_stash_](#stash-files) your changes.<br><br>Note that if we check out a specific commit instead of a branch then we check out the working directory in [_detached HEAD_](#detached-head) state.<br><br> |

| <a id="add-and-commit">Add & Commit</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| When we commit a changes in Git we permanently save modified file(s) to local repo´s history and label all the committenets with an unique hash-id, description and name of the committer.<br><br>The word "commit" also often refers to a unique labeled "snapshot" of files and directories at a certain moment. It is also called a blob.<br><br> A commit operation can be manually triggered with a `git commit` command but can also be a background job as part of other command such as `git merge`.<br><br> |

| <a id="repo-history">Repo history</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| When we commit a change then it is automatically added to our repo history, also called shortly "history". All commits with their hashes, descriptions and tags are stored in our local repo history.<br><br> |

| <a id="head">HEAD</a><a href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| When working with Git, only one branch can be checked out at a time - and this is what's called the "HEAD" branch. Often, this is also referred to as the "active" or "current" branch. HEAD is a movable pointer referencing to the last commit in currently checked out branch in our working directory. HEAD in normal cases always points on the latest commit on checked-out branch. Branch and HEAD pointers are in such a case "attached". Normally when you switch branches with git checkout, the HEAD revision changes to point to the tip of the new branch.<br><br> Note that there are cases when we need to check out a specific commit or tag and not a branch! Then the HEAD points directly to this specific commit/tag and not the latest commit on any named branch. This scenario is a bit specific and called [detached HEAD](#detached-head).<br><br> |

![Git commands](./app/assets/images/GIT_structure.JPG)

| <a id="files-in-git">File types & workflow</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| There exist 4 types of files in Git:<br><br> ⋅ _Untracked:_ Newly added files.<br> ⋅ _Modified:_ Existing changed files and saved in working tree.<br> ⋅ _Staged:_ Added to our staging area.<br> ⋅ _Committed:_ Saved in the repo history.<br><br>_Untracked files_ are basically files that Git do not have any previous version of in its history. Files that are newly added to your project get the status _untracked_. Those are added to the working tree but in order to become tracked and get a first initial version they must be either [_staged_](#stage) or [_committed_](#commit). Many Git commands like `git reset` or `git revert `do not affect untracked files and there is a special `git clear` command to remove those files from the project.<br><br>The _working tree_, or working directory, consists of files that you are currently working on. You can think of a working tree as a file system where you can view and modify files.<br><br>The _index_, or _staging area_, is where commits are prepared. The index compares the files in the working tree to the files in the repo. When you make a change in the working tree, the index marks the file as modified before it is committed.<br><br>When a file is first modified, the change can only be found in the working tree. You must stage the changes you want to be included in your next commit. The index contains all file changes that will be committed. Once you have finished staging files, commit them with a message describing what you changed. The modified files are now safely stored in the repo.<br><br> |

| <a id="commit-hash-tag">Hash & Tag</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| A _commit hash_ is an unique unchangeable 40 characters long SHA-1 hash that is created as unique identification for each commit of files to a repo. Example of a commit hash is `4c511f16ef2644854d04cabebfcecc82be0eb04f`. Normally only 7 first characters are enough to identify a commit within a normal project and therefore short "7-chars-version" can be used to refer to a commit.<br><br>A commit _tag_ is a label/stamp that can be manually added to a commit to mark a particular commit with a human readable label. Example: rel-v.1.8.5.<br><br> |

| <a id="stashing-files">Stashing files</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Stashing takes your modified files in working tree and index ("dirty" state of your working directory), and save those on a "stash-stack" of unfinished changes. Later you that you can reapply those changes.<br><br> Note! By default git do not stash [untracked](#files-in-git) files therefore to handle those you need to use "-u" flag. The command `git stash -u` will add all changes including untracked) to the stash stack.<br><br> Later to get back those stashed changes simply run command `git stash pop` and your latest stashed changes will be reverted to current working directory and the stashed object removed from stash-stack. To list all stashed objects in stack run `git stash list` command.<br><br> |

| <a id="tracking-relationship">Tracking relationship</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Understanding and making use of tracking relationships in git makes version control a whole lot easier. Very often we work on a local copy of a project that is hosted in a central remote repo. This means that our local branch have a "sibling" branch, a copy of itself, usually (but not necessarily) with same name in the remote repo. This remote branch can be updated by others independently as we commit to corresponding local branch.<br><br> Often we want to know how our local branch differ from its "_remote sibling_". We want to know if any commits were made to same branch in remote by other developers while we were working on a local copy. Here is where "tracking" and "upstream" branches described in detail below help us. When a local branch is turned into a [_tracking branch_](#local-branch) then it automatically tracks its [_upstream branch_](#remote-branch) (its "sibling" in remote) through a [_remote-tracking branch_](#local-branch). <br><br>**Local branch** (local, _i.e. master_) **-->** **Remote-tracking branch** (local, _i.e. origin/master_) **-->** **Upstream branch** (remote, _i.e. master_)<br><br> |

| <a id="remote-and-upstream-branches-in-git">Local branches: Local, Tracking and Remote&#8209;tracking</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| There are several types of _local branches_ and it's important to get familiar with the terminology used in order to follow git documentation.<br><br>_Local branch (tracking or non-tracking):_<br> Simply a branch that exists on your local machine, in your local repo. Can be named as "master", "dev" or "feature-x". A local branch be of type tracking (tracking branch) or non-tracking. A local branch becomes tracking when its upstres is set. This is done in some specials circumstnaces, see HERE. Tracking branches are local branches that have a direct relationship to a remote branch.<br><br>_Remote-tracking branch:_<br> A special type of local branch that is created automatically by git in the background. Its only purpose is to mirror corresponding remote branch (its upstream) and compare difference of commits. This type of local branch is always automatically created or updated in the background whenever any network communication toward corresponding remote branch is made when push/pull/fetch are performed. Its name always consists of two parts: [remote-alias]/[remote-connection-name] for example "origin/master" och "origin-repo-x/feat-x-branch".<br><br>All existing _remote-tracking branches_ in our local repo can be listed with a `git branch -r` command. To list all local branches run `git branch -a -vv` command with result can might look like this:<br><br> _\* master&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;33f45fe&nbsp;&nbsp;[origin/master: ahead 1, behind 2]&nbsp;&nbsp;Added print.<br>&nbsp;&nbsp;feature-x-branch&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;09c51c6&nbsp;&nbsp;Merge from master branch.<br>&nbsp;&nbsp;remotes/origin/master&nbsp;&nbsp;&nbsp;a9a5bfc&nbsp;&nbsp;Added special character._<br><br>What does above mean?<br>_\* master_<br>Local branch and as marked with "*" it's our checked out branch. It tracks corresponding *upstream\* branch (also names master) through its remote name _origin_. This means this local branch has its upstream set. As it is a a trucking branch then pull/push commands can be performed without parameters (read more [here](#upstream)). When corresponding remote-tracking branch "_origin/master_" was synched last time then remote had 1 new commit that is not included in our local "master" branch, and our local "master" had 2 new commits that are not included in remote upstream.<br><br>_feature-x-branch_<br>A normal non-tracking local branch with its last commit labeled 09c51c6.<br><br>_remote/origin/master_<br>Remote-tracking branch that refers and mirrors corresponding upstream branch (in remote) named "master".<br><br> |

| <a id="remote-branch">Remote branch & Upstream</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| _Remote branch_ is a branch that exists in a remote repository i.e. GitHub. A remote branch that is connected/referenced from a local system is in this context also called an "upstream branch". You can often see expression that a "local branch tracks its upstream". It means the local branch is connected to its sibling in remote and tries to know everything that happens to him. Procedure of connecting a local branch with its corresponding branch in remote is in Git documentation often called as "setting [upstream](#upstream) for a local branch".<br><br> **How to set upstream for a local branch?**<br><br>It can be done in two ways:<br><br>▸ Manually: If you already have a local branch and want to set it to a remote branch you just pulled down, or want to change the upstream branch you’re tracking, you can use the -u or --set-upstream-to option<br>`git branch --set-upstream-to or -u [name of "remote-tracking branch" i.e origin/server-fix]`.<br><br>▸ Automatic: Whenever you run any first push/pull/fetch command to corresponding remote branch add `-u` flag. Example:<br>`git fetch -u [remote-connection i.e. origin] [local-branch i.e. master]`<br>This will not only create a remote-tracking branch localy but also connect corresponding local branches upstream so it tracks it remote.<br><br>Note! When cloning (`git clone`) a repo from a remote then git automatically checks out a default local branch and automatically make it a "tracking branch" by setting its upstream in the background. Therefore in most common cases after cloning from a remote we end up with two local branches, "master" and "origin/master" and we can run git `Git pull & push` commands without any additional parameter straight out of the box for this checkout branch. `git fetch` is not do ing this.<br><br> |

| <a id="detached-head">Detached HEAD</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Detached HEAD means that our [HEAD](#head) pointer do not point to a branch pointer but points to a specific commit hash or tag. This happens when we check out a specific commit, check out a [_remote-tracking branch_](#local-branch) or sometimes this also might happen when a rebase fails and leave us "hanging" in an unfinished state. Simple `git status` command will inform you that you are in this special state. In this state you can look around at code, edit files and even commit your changes as usual but be aware that you will not be able to push/pull from/to this "detached workspace" and your precious work with commits or staged changes will eventually be lost when you check out something else. This because internally in detached state Git creates a branch without any starting point (unreferenced branch) and after a week or so Git garbage collector will deletes unreferenced branches from the memory!<br><br> Usual procedure to save you staged changes and commits that you have done in a "detached mode" is simply to create new branch when in a detached working directory and commit you changes to this new branch. Following will do the trick:<br><br> `git checkout -b temp-branch-from-detached`<br> `git commit -am "Committing changes done in detached HEAD state."` <br><br> |

| <a id="merge-rebase">Merge & Rebase</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| There are two ways in Git to integrate changes from one branch into another one - merge or rebase. Both have their advantages and disadvantages.<br><br> **MERGE:** Can be performed in two ways and it is important to understand how both work, specially if you want to merge your feature into a branch that many other persons work on.<br> **1. Fast-forward merge:** Is possible only if the point where the both branches diverge from has not forked, meaning only the branch that we merge from received any new commits. When we run `git merge` command this type of merge is performed if possible by default. In a case when Git has possibility to do a fast-forward merge then the branch pointer of the branch we merge into (here called parent) is simply moved to point to same commit/branch that we merge from. This results in that ALL commits in our "feature-branch" are now "added" to the tip of the parent me merged to. It this desirable? Sometimes yes but consider a situation when feature you worked on contains of many many minor commits on your "feature-branch". In case of a fast-forward merge ALL the commits with with their descriptions and hashes will be visible as part of parent branch. This can often be a disadvantage as it is much clearer from the point of reviewer to be able to see only one single commit telling when "feature-x" was delivered instead of "15 commits" with comments you made originally working on your privater feature branch. Also in case of reverting the feature it is impossible to see from Git history which of the commit objects in parent really implement the feature. You would have to manually read all the log messages making reverting such a feature added in this way a true headache.<br> **2. Non fast-forward merge:** Sometimes done by git automatically when commits do not fullfil criteria for fast-forward merge - but it can be forced by adding `--no-ff` flag to the git merge command. Then git will never do fast-forward merge and add our committed feature in ONE new commit on the parent. Note, merge do not rewrite any history of already existing commits on the destination branch witch is regarded as more safe than rebase.<br><br>**REBASE:** This is changing the base of your "feature-branch" to tip of the branch making appear as if you'd created your "feature" branch from latest commit. As a result we get a linear succession of commits. It differs from merge by rewriting the commit history of already existing commits on the destination (parent) branch. Usage: If you want to get the latest updates from parent (= the branch you branched from) into your "feature-branch", but you want to keep your branch's history clean so it appears as if you've been working off the latest commit. This gives you also later the benefit of a clean merge of your feature branch back into parent! Usually you rebase toward your own "feature" branch that you are in full control of and can afford messing up and take time to solve if something goes wrong, and you do a merge back to master or dev-branch or whatever you branched from.<br><br> |

| <a id="fetch-pull">Fetch & Pull</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Synchronizing data between your local machine and remote is an essential step in our daily work as the data we locally look at is just a "snapshot" and up-to-date only as the last time we explicitly downloaded fresh data from the remote with a fetch or pull command.<br><br>▸ **Fetch** downloads commits on all branches in a remote repository and stores all in local repo's corresponding [_remote-tracking branches_](#local-branch) but DO NOT integrate any of this new data into files in our currently working directory. To integrate the any commits into currently checked out branch we have to run a `git merge` command toward the corresponding the [_remote-tracking branch_](#local-branch). <br><br>▸ **Pull** on the other hand not only downloads all remote branches but also updates our files current working directory (=checked out branch) with the downloaded changes by making a merge. Since "pull" in background always by default tries perform to merge changes from remote into our local ones, a so-called [_merge conflict_](#merge-conflict) can occur. `Git pull` can also be flagged to do a [rebase](#merge-&-rebase) instead of a background merge with help of `--rebase` flag. There are many opinions on whether or not preferably use pull with rebase option but as long as you pull to your private feature branch that only you work on, then this is our recommendation. Like for many other actions it's highly recommended to start a pull only with a [_clean working directory_](#clean-working-director).<br><br> |

| <a id="push">Push</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| With `git push` we upload commits from our local branch to corresponding remote branch. When we execute the command while having checked out a local branch that is a [_tracking branch_](#local-branch), then a simple `git push` command will instruct Git to take changes only from the branch we currently are on and update corresponding "upstream branch" in remote. On the other hand if the current local branches not a "tracking branch" then we must give `git push` command additional instructions in order for Git to know the destination. Then the same command looks like `git push <remote-connection>`. Git will then connect to remote repo´s url specified in "remote connection" i.e. "origin", take changes in the branch we are on and copy those commits to remote branch that is named same. <br><br> |

| <a id="merge-conflict">Merge Conflicts</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| A merge conflicts arise when two commits that we are merging together have changed in the same parts of code and Git do not know how to solve this. For example when one developer deleted a file in master while another developer on his feature-branch was modifying same file. In such cases Git will mark the file as being conflicted and halt the merging process with terminal output "Automatic merge failed - fix conflicts and then commit the result" and it is developers' responsibility to resolve the conflict. Code from both files are then checked out in the working directory and separated with string "`=============`". The files must be manually edit and saved and manually committed in order for the merge to finalize.<br><br> |

| <a id="unrelated-histories-error">Unrelated Histories errors</a><a align=left href="#common-git-expressions">&nbsp;&nbsp;&nbsp;&nbsp;↩&nbsp;&nbsp;&nbsp;</a> |
| :-- |
| Sometimes our local .git directory with its history get deleted or corrupted. This leads Git to be unaware of the local history and will throw this error when you try to clone/fetch/push from remote. This will also happen when a new remote repo is created (i.e. on GitHub) with README file as initial commit. Then this repo will get its own history due to the first commit. If you simultaneously create new local repo and commit a single change then your local repo also gets a history created. In this case trying to clone one to another will fail with this error as both already got their own histories on their own. This can be solved using `--allow-unrelated-histories` flag on the command that fails. |

<br>

<p align=right><a id="useful-git-aliases-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### [**Useful Git aliases**](#)

Copy those aliases to command prompt. Those are used often. A time saver.

List current status:<br> `alias sta=" echo '____________' && echo '> git status' && echo ' ' && git status "`

All commits in a nice graph:<br> `alias gra=" echo '___________________________________________' && echo '> git log -all --decorate --oneline --graph' && echo ' ' && git log --all --decorate --oneline --graph "`

Prints common status information:<br> `alias status=" echo '_________________________________________' && echo '> git log -4 --decorate --oneline --graph --first-parent' && echo ' ' && git log -4 --decorate --oneline --graph --first-parent && echo ' ' && git remote -v && echo ' ' && echo '>>> git branch -a -v' && echo ' ' && git branch -a -v && echo ' ' && echo '>>> git status' && echo ' ' && git status "`

<br>

<p align=right><a id="useful-cmd-commands-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### [**Useful Cmd Commands:**](#)

It is good to know and memorize those basic command that are often used:

| Cmd&nbsp;command | Description |
| :-- | :-- |
| `pwd` | Print Working Directory. Writes out full path of currently executing folder. |
| `ls -force` \| `dir -force` <br> `ls -a` \| `dir -a` | List all content (including hidden files) in current working directory. <br> "- force" for VSCode terminal /powershell) and "-a". for Git Bash. |
| `ls -a` | List all in a directory. To check if it really is emty. |
| `cd [path]` <br> `cd ..` | Change location to path or back |
| `mkdir [dirName]` | Creates a new directory in current location |
| `cp [file] [copy-of-file]` | Make a copy of a file |
| `rm [dirName]` | Deletes a directory |
| `touch [fileName]` | Creates a new file in current location |
| `cat [fileName]` | Prints content of a file in terminal window |
| `ipconfig` | detailed information about your current network adapter connection including current IP address |
| `copy [soure] [dest]` | Copies a source file to destination |
| `cls` or `clear` | Clear the command screen |

<br>

<p align=right><a id="git-ignore-file-m" align=right href="#table-of-content">↩ Back To Top</a></p>

### [**.gitignore file**](#)

Gitignore file is a file in root of your project which tells Git which files not to track. #todo who creates it?.<br> A gitignore file may look like following:

```
# Numerous always-ignore extensions
*.diff
*.err
*.orig
*.log
*~
*.sass-cache
node_modules/
.tmp/

# OS or Editor folders
.DS_Store
Thumbs.db
.cache
.__project__
.settings

...
```
