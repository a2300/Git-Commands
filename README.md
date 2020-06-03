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
 
 
 
 _Stashing_
 
 Stash changes in working area as well as in staging area
 
 `git stash --include-untracked`
 
 List of stashing changes
 
 `git stash list`
 
 Apply change from stash area to working area as well to stage area
 
 `git stash apply`
 
 Remove all the stash entries
 
 `git stash clear`
 
 Undo changes for single file from stage area. Content is taken from repository area.
 (Working area and stage are are affected, desctructive operation)
 
 `git checkout HEAD <file>`
 

_Exploring history_

One line git log history

`git log --graph --decorate --oneline`

See what's inside commit by <commit-id>
 
 `git show 77dac20`
 
 Reference to commit by HEAD
 
 `git show HEAD` - show HEAD commit
 `git show HEAD^` - show parent HEAD commit
 `git show HEAD^^` - show parent of parent HEAD commit
 `git show HEAD~3`
 
 Compare what was added in 2 last commit
 
 `git diff HEAD HEAD~2`
 
 Difference between 2 branches
 
 `git diff feature1 master`
 
 Output last 3 commits
 
 `git log -3 --oneline`
 
 Output last 5 commits
 
 `git log HEAD~5..HEAD^ --oneline`
 
Modify last commit

`git commit --amend`

Interactive rebase

`git rebase -i`

Access to reflogs

`git reflog`

Revert changes done in previous commit

`git revert HEAD`

### Generating a new SSH key pair

ED25519 SSH keys
`ssh-keygen -t ed25519 -C "my@mail.com"`

You'll see a response similar to:

`Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/user/.ssh/id_ed25519):
`

### Adding an SSH key to your GitLab account
1)Copy your public SSH key to a location that saves information in text format. The following options saves information for ED25519 keys to the clipboard
for the noted operating system:
Git Bash on Windows:
`cat ~/.ssh/id_ed25519.pub | clip`

2)Navigate to http://gitlab.com and sign in.


3)Select your avatar in the upper right corner, and click Settings


4)Click SSH Keys.


5)Paste the public key that you copied into the Key text box.


6)Make sure your key includes a descriptive name in the Title text box, such as Work Laptop or
Home Workstation.


7)Include an (optional) expiry date for the key under "Expires at" section. (Introduced in GitLab 12.9.)


8)Click the Add key button.


### Testing that everything is set up correctly
`ssh -T git@gitlab.com`
