## Git Configurations
* System - Applies to all users
Program Files\Git\etc\gitconfig
* User - Applies to single user
~Home\.gitconfig
* Project
my_project/.git/config

## Initial Git Configuration Commands:

* $ git config --global user.name "Dev P. Yadav"

* $ git config --global user.email "devpyadav@gmail.com"

* Initializing a new repository locally

  *$ git init*

* Whether git is installed or not

  *$ which git*

* Which version of git is installed

  *$ git --version*

## Basic Commands:

# Adding and committing files to local git

* Add all the files that have been modified to the git repository

  *$ git add .*

* Add a specific file to git repository

  *$ git add <file name>*

* Committing the file to the repository

  *$ git commit -m "<Comment>"*

*  View the difference between the working directory, staging index and the local repository

  *$ git status*

# Removing files from local git

* Completely remove the file from git

  *$ git rm <file_to_delete>*

* Commit the file

  *$ git commit -m "<comment>"*

# Viewing the git log

* Shows the log of commits that have taken place

  *$ git log*

* Shows the last 2 commits

  *$ git log -n 2*

* Searches logs with message Init in the commit

  *$ git log --grep="Init"*

# Checking out a file from local repository to the working directory
  *$ git checkout -- secondary_file.txt*

# Working with branches on local

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
