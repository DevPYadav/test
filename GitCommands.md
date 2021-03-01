# Git Configurations
* System - Applies to all users
** Program Files\Git\etc\gitconfig
* User - Applies to single user
** ~Home\.gitconfig
* Project
** my_project/.git/config

# How Git works
* Saving to Local Repo and pushing to Remote Repo *
**Local:** Working directory (Git Add) ---> Staging area (Git Commit) ---> Commited to Local Repo
**Remote:** Local Repo (Git Push) ---> Pushed to Remote Repo

# Initial Git Configuration Commands:

* $ git config --global user.name "Dev P. Yadav"

* $ git config --global user.email "devpyadav@gmail.com"

* Initializing a new repository locally

  *$ git init*

* Whether git is installed or not

  *$ which git*

* Which version of git is installed

  *$ git --version*

# Basic Commands:

## Adding and committing files to local git

* Add all the files that have been modified to the git repository

  *$ git add .*

* Add a specific file to git repository

  *$ git add <file name>*

* Committing the file to the repository

  *$ git commit -m <Comments>*

*  View the difference between the working directory, staging index and the local repository

  *$ git status*

## Removing files from local git

* Completely remove the file from git

  *$ git rm <file_to_delete>*

* Commit the file

  *$ git commit -m <comments>*

## Viewing the git log

* Shows the log of commits that have taken place

  *$ git log*

* Shows the last 2 commits

  *$ git log -n 2*

* Searches logs with message Init in the commit

  *$ git log --grep="Init"*

* Show the last 2 commits and the differences
  *$ git log -p -2*
  -2 shows the Last 2 changes
  -p shows the difference between each commit

  *$ git log --stat*
  Shows details of those changes

  *$ git log --pretty=oneline*
  Gives the reference for each commit and the commit text

  $* git log --pretty=format:"%h: %an, %ae, %cn, %cd, -%s" --graph*
  Shows the short hexa decimal code, author name, author email, common name of the person, common date, comments that were added while checking in and a visual representation

## Checking out a file from local repository to the working directory

  *$ git checkout -- secondary_file.txt*

## Working with branches on local

* List the branches in local repository

  *$ git branch*

* Creates a new branch

  *$ git branch new_feature*

* Now list all the branches and new_feature branch should be visible

  *$ git branch*

* Switching to another branch

  *$ git checkout new_feature*

* Switching back to master branch

  *$ git checkout master*

* Create and checkout to a new branch at the same time

  *$ git checkout -b shorten_title*

* Comparing branches

  *$ git diff master..new_feature*

  *$ git diff --color-words new_feature..shorten_title*

* List all branches are merged into the current branch

  *$ git branch --merged*

* Renaming and moving branches  --move and rename are same

  *$ git branch -m new_feature seo_title*

* Deleting branches

  *$ git branch -d <branch_to_delete>*

* Deleting a not merged branch

  *$ git branch -D branch_to_delete*

* From your git directory, you can change your command promopt to your branch

  *export PS1='$(__git_ps1 "(%s)") > '*

  *export PS1='\W$(__git_ps1 "(%s)") > '*

## Example for creating branches 

Multiple project development within a single product. 

 *$git status*
On branch master assumed as prod

 *$git branch -a*
* master
[ sometimes remote or origin master ] - just master

{ git uses snapshots to do a snapshot of the system at each individual task } 

 *$git checkout -b development*

 *$git status*
 master
 * dev

 *$git branch -a*
 * development
 master 

 *$git checkout master*
 Switched to branch master

 *$git status*
 # On branch master
 [ nothing to commit ]

 *$git branch -a*

 *$echo 'This is Master Only' > MASTERBRANCH.txt*
 *$git status*
 # On branch master

 *$git add MASTERBRANCH.txt*

 *$git commit MASTERBRANCH.txt -m 'largeassedmasterbranch'*

 *$git status*
 # On branch master nothing to commit

 *$git checkout development*
 => no MASTERBRANCH.txt

 development was branched before the file was added -> 

 *$echo 'Development Branch' > DEVELOPMENT.TXT*

 *$git add DEVELOPMENT.TXT*
 *$git commit DEVELOPMENT.TXT -m 'Dev'*

 *$git status*
 # On branch development
 DEVELOPMENT.txt 

 *$git checkout master*

 *$ls -lhtar
 = MASTERBRANCH.txt 

# Working with the Remote Server

## Git Remote

Remote locations are generally a build server, a team members machine or a centralised store such as Github.com. Remotes are added using the git remote command with a friendly name and the remote location, typically a HTTPS URL or a SSH connection for example https://github.com/OcelotUproar/ocelite.git or git@github.com:/OcelotUproar/ocelite.git.

The friendly name allows you to refer to the location in other commands. Your local repository can reference multiple different remote repositories depending on your scenario.

  *$ git remote add origin /s/remote-project/1*

Here the friendly name of the remote location is "origin" and "/s/remote-project/1" is the path of the remote location

## Git Push

When you're ready to share your commits you need to push them to a remote repository via git push. A typical Git workflow would be to perform multiple small commits as you complete a task and push to a remote at relevant points, such as when the task is complete, to ensure synchronization of the code within the team.

The git push command is followed by two parameters. The first parameter is the friendly name of the remote repository we defined in the first step. The second parameter is the name of the branch. By default all git repositories have a master branch where the code is worked on.

  *$ git push origin master*

If you are on a different branch, say "development" and want to push that branch to GitHub then use the below command

  *$ git push origin development*

## Git Pull

Where git push allows you to push your changes to a remote repository, git pull works in the reverse fashion. git pull allows you to sync changes from a remote repository into your local version.

The changes from the remote repository are automatically merge into the branch you're currently working on.

  *$ git pull origin master*

## Git Fetch

The command git pull is a combination of two different commands, git fetch and git merge. Fetch downloads the changes from the remote repository into a separate branch named remotes/<remote-name>/<remote-branch-name>. The branch can be accessed using git checkout.

Using git fetch is a great way to review the changes without affecting your current branch. The naming format of branches is flexible enough that you can have multiple remotes and branches with the same name and easily switch between them.

The following command will merge the fetched changes into master.

  *$ git merge remotes/<remote-name>/<remote-branch-name> master*

## Git Reset

If you're in the middle of a commit and have added files to the staging area but then changed your mind then you'll need to use the git reset command. git reset will move files back from the staging area to the working directory. If you want to reset all files then use a . to indicate current directory, otherwise list the files separated by spaces.

  *$ git reset HEAD .*

## Git Reset Hard

A git reset --hard will combine both git reset and git checkout in a single command. The result will be the files removed from the staging area and the working directory is taken back to the state of the last commit.

  *$ git reset --hard HEAD*

## Git Revert

If you have already committed files but realized you made a mistake then the command git revert allows you to undo the commits. The command will create a new commit which has the inverse affect of the commit being reverted.

  *$ git revert HEAD --no-edit*

## Git Merge

The git fetch command downloads changes into a separate branch which can be checked out and merge. During a merge Git will attempt to automatically combine the commits.

When no conflicts exist then the merge will be 'fast-forwarded' and you won't have to do anything. If a conflict does exist then you will retrieve an error and the repository will be in a merging state.

### Viewing Conflict -

When a conflict occurs the changes from both the local and remote will appear in the same file in the unix diff format. This is the same format used by git diff.

To read the format, the local changes will appear at the top between <<<<<<< HEAD and ======= with the remote changes being underneath between ======= and >>>>>>> remotes/origin/master.

To resolve the conflict the files need to be edited to match our desired end state.

### Resolving Conflict  -

The simplest way to fix a conflict is to pick either the local or remote version using git checkout --ours staging.txt or git checkout --theirs staging.txt. If you need to have more control then you can manually edit the file(s) like normal.

Once the files are in the state desired, either manually or using git checkout, then you need to stage and commit the changes. When committing a default commit message will be created with details of the merge and which files conflicted.

  *$ git merge development --no-ff*

The above command merges the development branch into the master with all the previous commits included.

# Connecting to Github

* SSH key generation to connect to github
  *$ ssh-keygen*

* Point to a remote repository
 *$ git remote add origin git@bitbucket.org:devpyadav/bitbuckettest.git*
 *$ git remote add origin git@github.com:devpyadav/test.git

* Cloning a directory from github
  *$ git clone git@github.com:DevPYadav/test.git*
  
# Resolving a merge conflict using the command line

1. Open your favorite text editor, such as Atom, and navigate to the file that has merge conflicts.

2. To see the beginning of the merge conflict in your file, search the file for the conflict marker <<<<<<<. 

When you open the file in your text editor, you willll see the changes from the HEAD or base branch after the line <<<<<<< HEAD. 

Next, you'll see =======, which divides your changes from the changes in the other branch, followed by >>>>>>> BRANCH-NAME. 

In this example, one person wrote "open an issue" in the base or HEAD branch and another person wrote "ask your question in IRC" in the compare branch or branch-a.

If you have questions, please

**_<<<< HEAD
open an issue
=======
ask your question in IRC.
>>>>>>> branch-a**

3. Decide if you want to keep only your branch's changes, keep only the other branch's changes, or make a brand new change, which may incorporate changes from both branches. Delete the conflict markers <<<<<<<, =======, >>>>>>> and make the changes you want in the final merge. In this example, both changes are incorporated into the final merge:

If you have questions, please open an issue or ask in our IRC channel if it's mo

4. Add or stage your changes.

*$ git add .*

5. Commit your changes with a comment

*$ git commit -m "Resolved merge conflict by incorporating both suggestions."*

# How to revert a merge commit that's already pushed to remote branch?

When you view a merge commit in the output of git log, you will see its parents listed on the line that begins with Merge:

commit 8f937c683929b08379097828c8a04350b9b8e183

Merge: 8989ee0 7c6b236

Author: Ben James <ben@example.com>

Date:   Wed Aug 17 22:49:41 2011 +0100

In this situation, git revert 8f937c6 -m 1 will get you the tree as it was in 8989ee0, and git revert -m 2 will reinstate the tree as it was in 7c6b236.

*$ git revert -m 1 <commit-hash>*

*$ git commit -m "Reverting the last commit which messed the repo."*

*$ git push -u origin master*
