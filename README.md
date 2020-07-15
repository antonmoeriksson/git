# git magic :tada:

This is suppose to be a quick and dirty guide for the nice-to-have stuff of git!

So, here is a few of my best tips and tricks for git.

## Sync Upstream Forks
One problem I have hade in the git eco system is syncing my own fork to the parent repo. 
I have a bullet proofe way of achinvingjust that with a few simple commands.
First name the upstream repo something desciptive av `fork`, `parent`, `original`, so you can distigivude it from the standard origin.

## git stash
Lets imaagine we are working on a feature and have local changes and want to save them for later or just try anouther approch we can do
```
git stash
```
This takes all the unstashed local changes and places them on the git stack, which can be poped, listed or droped.
```
git stash list
```
Will give something like this
```
stash@{0}: WIP on feature/waveform: c6996a9a Refactor waveform generation fail early of waveform extraction failed.
stash@{1}: WIP on refactor/add-test: a645aef0 Add unit test for getDocumentOperations
```
If we then popes the stack we will select (c6996a9a) and applay to our code base.
```
git stash pop
```
