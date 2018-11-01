# This place is for tips about Git commands

 1. how to set up git and connect it on your github repo

    ### Mac has installed <git> and <ssh-keygen>

  [1]. sh-keygen -t rsa
    > this command to generate a public ssh key.

  [2]. cd ~/.ssh
    > then go to "cd ~/.ssh" to locate that folder

  [3]. vim rsa-id.pub
    > this will help read ssh public file

 2. how to download your repo from Github

  [1]. mkdir your-folder
    > this will make a folder for clone the repo

  [2]. git init
    > this will help initial the folder to use git command

  [3]. git clone git@xxxxxxxxxxxx
    > this command will help download the source code from repo


# The followings are the steps to create and push the changes

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
