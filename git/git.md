> # this place is for tips about Git syntax

> 1. how to set up git and connect it on your github repo

>> ####Mac has installed git and ssh-keygen.

>>> first of first, generate ssh key.
>>> use "ssh-keygen -t rsa" to generate a public ssh key.
>>> then go to "cd ~/.ssh" to locate that folder
>>> vim rsa-id.pub to get key and paste to your Github setting area
>>> it's done

>> how to download your repo from Github
>>> So, you need to "mkdir" one folder first, and "cd" there then "git init".
>>> the last step type "git clone git@xxxxxxxxxxxx"
>>> It's done.

# the followings are the steps to create and push the changes

  1. git checkout -b "branch-name"
  > this is the command for create new branch

  2. git add .
  > this is the command for stage the changes

  3. git commit -m "xxx"
  > this is for log the commit name

    [1]. git status
      > this command is for checking if changes has been staged and commit

    [2]. git diff
      > this command will tell you where the code changes compare to the original

  4. git checkout master
  > this command will make you switch to master brand!

  5. git merge "branch name just create"
  > this is for merge the branch to master

  6. git push
  > this will push all changes to Github repo
