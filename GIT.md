# Git help

## Get the url of repo

`git config --get remote.origin.url`

## Check is this folder associated with some git repo

`git --no-pager rev-parse --is-inside-work-tree`
`true` = yes, `False` = not associated

## Command to remove the git attachment from the folder (locally)

`rm -rf .git`

## Directly open the git repo on browser from git folder

`git config --get remote.origin.ur`

then
open "url we got"

## Remove `HEAD` from a Git repository

Removes the last commit from local >> `git reset --hard HEAD~`

Reset the `HEAD` to a previous commit >> `git reset --hard HEAD~1`

Branch will be reset >> `git push origin <branch_name> --force`
