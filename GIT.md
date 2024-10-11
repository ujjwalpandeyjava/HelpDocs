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

## Tags

Tags mark important points in a project's history for easy reference, like version releases. Simplifies tracking and versioning.

1. List tags
    - git tag
    - git tag -l

2. Create a tag
    - git tag tag_name
    - git push origin tag_name

3. Example:
    - git tag v1.0
    - git push origin v1.0

## Stash

Temporarily save your uncommitted changes without committing them to the repository.\
This is particularly useful when you need to switch branches or perform other operations but want to keep your current work intact.

Multiple Stash (LIFO)

Git Stash Commands

1. Stash Changes : `git stash` or `git stash save "optional message"` Stashes uncommitted changes and reverts directory to match the last commit.\
2. List Stashes: `git stash list` Displays all stashed changes in LIFO.\
3. Show Stash Contents: `git stash show stash@{index}` or `git stash show -p stash@{index}` Shows a summary of changes.\
4. Apply Stashed Changes: `git stash apply` or `git stash apply stash@{index}` apply without removing.\
5. Pop Stashed Changes: `git stash pop` or `git stash pop stash@{index}` apply and remove.\
6. Drop a Stash: `git stash drop stash@{index}` Deletes a specific stash entry.\
7. Clear All Stashes: `git stash clear` remove all.
