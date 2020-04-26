Git Commands
============

_A list of my commonly used Git commands_

*If you are interested in my Git aliases, have a look at my `.bash_profile`, found here: https://github.com/joshnh/bash_profile/blob/master/.bash_profile*

--

### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

### Basic Snapshotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git diff [source branch] [target branch]` | Preview changes before merging |


### Pretty git log in one line 

`git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit`

Add alias for git lon in one line
`git config --global alias.logline "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"`

Usage
`git logline`

(Source: https://ma.ttias.be/pretty-git-log-in-one-line)


### Git and GitHub workflow

| N | Description | Command |
|---| ----------- | ------- |
| 1 | Switch to a develop branch | `git checkout [develop branch]` |
| 2 | Update local repository to the newest commit from develop | `git pull` |
| 3 | Create a new branch and switch to it |`git checkout -b [branch name]`  |
| ..| ..................... | |
| 4 | Add/Remove/Edit files | |
| ..| ..................... | |
| 5 | Add a file to the staging area |`git add [file-name.txt]`  |
| 6 | Commit changes in new brach | `git commit -m "[commit message]"`  |
| 7 | Switch to a develop branch | `git checkout [develop branch]` |
| 8 | Update local repository to the newest commit from develop | `git pull` |
| 9 | Switch to a new branch | `git checkout [branch name]` |
| 10| Rebase new branch with develop branch | `git rebase [develop branch]` |
| ..| Resolve conflicts if any | |
| 11| Push a new branch to your remote repository| `git push origin [branch name]` |
| ..| With help of github create pull request and ask for approvals | |
| ..| If approvals got, with help of github squash and merge new remote branch into remote develop branch  | |
| ..| With help of github remove new remote branch | | 


### Other Git Commands

See difference between staged area and repository area (what's will be committed)

`git diff --cached`

Unstage file from stage area

`git restore --staged <file>`

or

`git rm --cached <file>`
 
 Move/Rename file

`git mv <old file> <new file>`
 
Remove (Reset) changes from working area and stage area, e.g. substitute them from repository area (destructive command)

`git reset --hard HEAD`
 
 
