# Git Configurations
* System - Applies to all users
Program Files\Git\etc\gitconfig
* User - Applies to single user
~Home\.gitconfig
* Project
my_project/.git/config

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
