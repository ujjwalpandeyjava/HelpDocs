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

- `git rm -r --cached .` Removes the files from the Git index
- Now `git add .` to add in stage
- `git commit -m "removed files should not be on git"` to commit
- `git push` now push code.
- Delete local branches only -- `git fetch --prune`

## Remove `HEAD` from a Git repository

`git reset --soft HEAD~1`
   Undo last commit but keep changes staged

`git reset --hard HEAD~1`
   Undo last commit and delete all changes

`git reset --mixed HEAD~1` or `git reset HEAD~1` (default)
   Undo last commit and move changes to unstaged

`git reset HEAD hash_code` (mixed)
   Undo last commit and move file changes to unstageds

`git push origin --force` >> Branch will be reset

## merge source branch → target branch

Ways

### Basic command

First make sure both branch are in sync (pull, push)

git checkout target-branch
git merge source-branch

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

## Merge Repos

Two ways

### Merge repo-b into repo-a (same root)

git remote add repo-b <repo-b-url>
git fetch repo-b
git merge repo-b/main --allow-unrelated-histories
git commit -m "Merged repo-b into root"
git push

### Merge repo-b into repo-a inside a folder

git remote add repo-b <repo-b-url>
git fetch repo-b
git read-tree --prefix=repo-b-folder/ -u repo-b/main
git commit -m "Merged repo-b into folder"
git push