# Cloning a Remote Repository
Clone is going to download the entire history of the project, all of the commits that have ever been made to the  repository

Lets clone jquery repository
```bash
$ git clone https://github.com/jquery/jquery.git
```
# Basic Repository Statistics
## Number of commits made to repository
```bash
ubuntu@git-standalone:~/jquery$ git log --oneline | wc -l
6264
```
## To find different merges and branches that has happened to repository
```bash
$ git log --oneline --graph
```
## To find author and commit message from each of them
shortlog can be used
```bash
$ git shortlog
```
# Get short log with number of commits decreasing and email address
```bash
$ git shortlog -sne
```
# Viewing commits
view the latest commit
```bash
$ git show HEAD
```
