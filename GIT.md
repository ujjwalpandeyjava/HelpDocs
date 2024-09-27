# Git help

## Get the url of repo

git config --get remote.origin.url

## Check is this folder associated with some git repo

git --no-pager rev-parse --is-inside-work-tree
true mean yes, false mean no not associated

## Command to remove the git attachment from the folder (locally)

rm -rf .git
