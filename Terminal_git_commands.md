# Useful Terminal Commands
[Cheat Sheet](https://learntocodewith.me/command-line/unix-command-cheat-sheet/)


#### To check and kill specific port #: 
* `lsof -n -i4TCP:PORT NUMBER`  or
* `lsof -i tcp:PORT NUMBER`
* Then kill the port with the PID (port ID):  `kill <PID>`

#### Create a link/reference to another file
* `ln [options] source target`

Flags include: 
* `-s` is a symbolic link
* `-i` is interactive mode
* `-f` forces the link
* `-n` 

# Git 
Swuash and Rebase

https://blog.carbonfive.com/2017/08/28/always-squash-and-rebase-your-git-commits/


git rebase -i [SHA]

### Stash
* To create a stash with a message: 
`git stash save "<MESSAGE>"`
* To apply a stash:
`git stash apply stash@{NUMBER}`