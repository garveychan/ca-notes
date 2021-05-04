# Git Notes 

###Resources
https://git-scm.com/
https://www.atlassian.com/git/tutorials

### Handy Notes
.gitignore - File in git repo which we can use to specify files to ignore - namely .DS_Store which is the MacOS directory preferences file.

### Git Workflow (Local)
*git init* - Initialize Git project.

1. Working Directory
    - Make changes to files:
        - Additions
        - Deletions
        - Modifications

*git add* - Stage your alterations.

2. Staging Area
    - Files are ready for commit

*git commit -m "message"* - Commit changes and add a message.
~Messages should be written like recipe instructions e.g. Add salt to broth.~

3. Repository
    - Changes are saved to repository as a commit

##### Commands
|Command|Options|Description|
|:-:|:-:|:-:|
|git init|none|Initializes git repo i.e. turns your working directory into a git repo|
|git add [file]|none<br>-p|Adds file(s) to staging area.<br>View all changes to be committed and prompt for confirmation.|
|git rm [file]|--cached|Remove staged file|
|git diff [file]|none<br>--cached|View differences in unstaged file<br>View differences in staged file|
|git commit -m "message"|none|Commits your staged changes and adds a message. Message should be written like a recipe instruction e.g. 'Add salt to broth'.|
|git status|none|Show current git status - current branch, modified, deleted and  untracked files.|
|git log|none<br>--oneline<br>--graph<br>--all|Shows detailed log of git commits.<br>Shows details in one line each.<br>Graphs branches.<br>Shows commits in the history of branches, tags, and other refs. Doesn't show commits that are not reachable from any ref.|

### Git Backtracking

https://dev.to/neshaz/when-to-use-git-reset-git-revert--git-checkout-18je

##### Workflow

Before resetting:
- HEAD = most recent commit in branch

After resetting:
- HEAD = previously made commit of your choice

|Command|Options|Description|
|:-:|:-:|:-:|
|git show [commit]|none|Shows commits and details of specified commit.|
|git checkout [commit] [file]|none| Moves HEAD pointer to specified commit, rolling back changes to that commit. May overwrite files in working directory and unstage any uncommitted changes.<br>Checkout function can also be used to switch between branches.|
|git revert [commit] [file]|none|Good for *committed* changes - Rolls back changes you have committed and creates a new commit based on the specified commit. May overwrite files in working directory.|
|git reset [commit]/[SHA] [file]|none|Good for *uncommitted* changes - Rewinds the entire working tree back to the specified commit. Does not make changes to your files. It merely unstages any changes.|

### Git Branching/Forking

##### Resources

https://learngitbranching.js.org/

#*Distinguish between branching/forking here.*
https://support.atlassian.com/bitbucket-cloud/docs/branch-or-fork-your-repository/

##### Workflow

*git branch* - Create new (giver) branch.

*git checkout* - Switch to new (giver) branch.

~New changes staged and committed.~

*git checkout* - Switch to main (receiver) branch.

*git merge* - Bring changes from giver branch to receiver branch.

~Resolve potential conflicts.~

Conflicts will emerge when there are changes between committed versions of files in different branches.

Conflicts will be displayed in the following format:

````
<<<<<<<HEAD
main version of line
=========================
branched version of line
>>>>>>>branch
````

~Delete branch if no longer required.~

*git branch -D* - Delete specified branch, -D option required if branch was never merged.

##### Helpful Commands
|Command|Options|Description|
|:-:|:-:|:-:|
|git branch|none|Shows which branch you're currently on.|
|git branch [branch]|none<br>-b|Creates new branch.<br>Creates new branch and switches to it.|
|git checkout [branch]|none|Switch to specified branch.|
|git merge [branch]|none|Bring changes from specified branch (giver) into main branch (receiver)|
|git rebase [branch]|none|Rebase your current branch to the specified branch i.e. it now points to the specified branch's last commit as a parent rather than where the branch initially diverged - Changes will be encapsulated within the staging process.|

### Git Remote

Teamwork is facilitated through the use of *remotes*. A remote is a shared Git repo that allows for collaborators to work on the same Git project from multiple locations.

##### Resources
https://dev.to/wceolin/mistakes-i-made-in-code-reviews-and-what-i-do-now-kk6

##### Workflow

1. *git clone* - Clone the remote repo to your local working directory.

2. *git fetch/pull* - Fetch and merge changes from the remote into your local main branch.

3. *git branch* - Create a branch to work on a new project feature.

4. *git commit* - Develop the feature on your branch and commit your work.

5. *git fetch* - Fetch and merge from the remote again (in case new commits were made while you were working).

6. *git push* - Push your branch up to the remote for review.

##### Commands
|Command|Options|Description|
|:-:|:-:|:-:|
|git remote|none<br>-v<br>add<br>rm|Show remote repos associated with current directory.<br>Show remote repos associated with current directory in detail.<br>Add a remote repo.<br>Remove a remote repo.|
|git clone [remote repo][local repo]|none|Clone remote repo files to local repo to begin work.|
|git fetch [repo]|none|See if changes have been made to the remote repo and bring them into a local 'remote branch'. This will *not* merge with your local files.|
|git pull [repo]|none|Pulls files from remote repo and attempts to merge with your local directory.|
|git push [repo][branch]|none|Pushes commits from specified branch to remote repo.|
