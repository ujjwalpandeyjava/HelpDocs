# Git help

## Command to config name and email

`git config --global user.name "Your Name"`

`git config --global user.email "your-email@example.com"`

## Verify Git Configuration

git config --global --list

## Get the url of repo

`git config --get remote.origin.url`

## Check is this folder associated with some git repo

`git --no-pager rev-parse --is-inside-work-tree`
`true` = yes, `False` = not associated

## Command to remove the git attachment from the folder (locally)

`rm -rf .git`

## Remove cached files

Files that are already tracked by Git and you added in .gitignore

> `git rm -r --cached .` Removes the files from the Git index
> Now `git add .` to add in stage
> `git commit -m "removed files should not be on git"` to commit
> `git push` now push code.
> Remove branches from local not on remote -- `git fetch --prune`

## Remove `HEAD` from a Git repository

Reset the last commit from local >> `git reset --hard HEAD~` or `git reset --hard HEAD~1`

Branch will be reset >> `git push origin --force`

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

`git stash list`

`git stash apply`

## Delete all local branch

git branch | grep -v "main" | xargs git branch -d

## Merge Repos

### Prepare Repo-B
```Bash
cd path/to/repo-b
```

### Connect and Fetch Repo-A
```Bash
git remote add repo-a-link https://github.com/user/repo-a.git
git fetch repo-a-link
```
### Merge Repo-A into Repo-B
```Bash
git merge repo-a-link/main --allow-unrelated-histories
```
### Organize Repo-A Files (Optional)
```Bash
mkdir repo-a-files
```
# Move Repo-A files into the new folder to avoid root clutter
```
git mv [file-list] repo-a-files/
git commit -m "Move Repo-A files into subdirectory"
```
### Cleanup and Push
```Bash
git remote remove repo-a-link
git push origin main
```
Quick Tip: If Repo-A uses master instead of main, ensure you swap the branch name in step 3.