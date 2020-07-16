# git magic :tada:

This is supposed to be a quick and dirty guide for the nice-to-have stuff of git!

So, here are a few of my best tips and tricks for git.

## sync upstream forks :fork_and_knife:
One problem I have hade in the git ecosystem is syncing my fork to the parent repo. 
I have a bulletproof way of achieving just that with a few simple commands.

First name the upstream repo something descriptive as `fork`, `parent`, `original`, so you can distinguish it from the standard origin.

Add the forks repo as an upstream repo and name it, here the name is `orignial` 
```
git remote add original git@gitlab.company.com:repo/cool-name.git
```
sync your local branch to the usual repo
```
git pull origin master
```
pull from the branch you want to sync, with --rebase from the upstream repo, named here `original`.
```
git pull --rebase original master
git push origin master --force-with-lease
```
go to your feature branch
```
git checkout feature-branch
git rebase master
```
push with --force-with-lease 

Note: you must push with `--force` or `--force-with-lease` when you have done a rebase, because the commit history will be altered. 

Note 2: ALWAYS try `--force-with-lease` first as it has some showstoppers, so stuff don't just explode :pray:!
```
git push --force-with-lease origin feature-branch
```
## git rebase interactive

## git stash
Let us imagine we are working on a feature, have local changes, and want to save them later or just try another approach we can do
```
git stash
```
This takes all the unstated local changes and places them on the git stack, which can be poped, listed, or dropped.
```
git stash list
```
Will give something like this
```
stash@{0}: WIP on feature/waveform: c6996a9a Refactor waveform generation fail early of waveform extraction failed.
stash@{1}: WIP on refactor/add-test: a645aef0 Add unit test for getDocumentOperations
```
If we then popped the stack, we will select (c6996a9a) and apply it to our codebase.
```
git stash pop
```

## git log for cool cats :octocat:
Get the cool commit-log history, like all the real hacker use:
```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
git lg
```
Enjoy with responsibility!


