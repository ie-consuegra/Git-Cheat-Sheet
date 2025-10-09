# Git Cheat Sheet (En)

## Table of content

- [Start with git](#start-with-git-🏁)
- [Get information](#get-information-📜)
- [Local branches](#local-branches-🔀)
- ["Go back in time" and deletion of files or commits](#go-back-in-time-and-deletion-of-files-or-commits-checkout-reset-rm-🕰️)
- [Remote repositories](#remote-repositories-📡)
- [Tags](#tags-🏷️)
- [Additional options](#additional-options-🍒)
- [Search in files and commits, find authors](#search-in-files-and-commits-find-authors-🕵️‍♀️)

## Symbols
- ⚠️- Usage can be seen as a bad practice.
- <> - Used to enclose a variable word, such as file/directory names, paths, commits ids, etc. The <> signs must not be written.

## Start with git 🏁
|Git command |Description|
|--|--|
|`git init`| Initialize the current directory as a git repository |
|`git add`| Update the index of the specified directory or files to prepare for the next commit. e.g. `git add assets` add all the files of the assets directory|
|`git add .`| Add all the files, directories and subdirectories of the current directory|
|`git commit -m "Commit message"` | Create a new commit (record the changes to the repository). If the `-m` flag is not included, it launches a text editor to define the message of the commit |
|`git commit -am "Commit message"`|It is like running `git add .` and `git commit -m ...` at the same time|
|`git reset HEAD`|Unstage the files. The opposite of `git add`|

[Go back to table of content ↑](#table-of-content)

## Get information 📜
|Git command |Description|
|--|--|
|`git config --list`|List all variables set in config file|
|`git status`|Show the working tree status ("changes not staged", "changes to be committed" (staged), "nothing to commit" ...)|
|`git branch`|List branches. The current branch will be highlighted and marked with an asterisk. Add `-r` to show remote branches or `-a` to show them all|
|`git log <path>`|Show commit logs (commit id, author, date and message), the "history", of the specified file or directory|
|`git log --stat`|Show commit logs and how much it changed in each one|
|`git log --all --decorate --oneline --graph`|Show a simplified tree of logs|
|`git show`|Show the commit logs and what changed in each one (diff)|
|`git diff <commit A> <commit B>`|Show the differences between two commits (no need to write the whole commit id, the first 4 letters are ok) If just one commit is written, it compares it with the last one, the HEAD|
|`git reflog`|Log of the HEAD movement or HEAD position through time. Each commit, switch, merge, even resets!|
|`git <command> --help`|Show the documentation of the command|

[Go back to table of content ↑](#table-of-content)

## Local branches 🔀
|Git command |Description|
|--|--|
|**Create/Delete/Rename**||
|`git branch <branch>`|Create the specified branch|
|`git branch -d <branch>`|Delete the specified branch|
|`git branch -m <oldbranch> <newbranch>`|Change the name of old branch to new branch|
|**Switch**||
|`git checkout <branch>`|The "classic" way to switch to other branch|
|`git switch <branch>`|Added in Git 2.23, switch provides a clearer and sleek command to do this|
|`git switch -c <branch>`|Create a new branch and switch to it|
|`git switch -`|Switch back to the last checked branch|
|**Merge and Rebase**||
|`git merge <branch>`|Merge the specified branch with the current one. The current branch has priority|
|`git rebase <branch>`|Rewrite the repo's history by applying the commits of one branch to another⚠️|

[Go back to table of content ↑](#table-of-content)

## "Go Back in time" and deletion of files or commits (checkout, reset, rm) 🕰️
|Git command |Description|
|--|--|
|`git checkout <commit>`|Return to the version of the specified commit|
|`git reset`|Return to the version of the specified commit but delete all the commits done from that point on|
|`git reset --hard <commit>`|Reset and delete the staged changes ⚠️|
|`git reset --soft <commit>`|Reset and keep the staged changes ⚠️|
|`git rm --cached <archivo>`|Delete the staged files but keep them on the hard disk|
|`git rm --force <archivo>`|Delete the staged files and the files from the hard disk|

[Go back to table of content ↑](#table-of-content)

## Remote repositories 📡
|Git command |Description|
|--|--|
|`git clone <url>`|Clone a remote repository into the current directory|
|`git remote`|Show the remote repositories (by name). Add the flag `-v` to see the urls too|
|`git remote add <name> <url>`|Create a new connection to a remote repository. This will be called by the specified name (generally called, "origin" and "upstream")|
|`git push <name> <branch>`|Update the branch of the remote repo based on the local one|
|`git push -u <name> <branch>`|The same as above. But, set up tracking. So, after running it, you can use `git pull` or `git push`, without specifying the name of the remote repo nor the branch|
|`git push <name> --delete <branch>`|Delete a remote branch. Remember the `--delete` flag|
|`git push --set-upstream origin <localbranch>`|Creates a new branch on the remote repository, in this example it is called 'origin'|
|`git pull <name> <branch>`|Update the branch of the local repo based on the remote one|
|`git pull <name> <branch> --allow-unrelated-histories`|Pull even when the projects mismatch commit histories. Useful when you just created a remote repo and added at least one commit, as local and remote repos are now unrelated, you need to "allow unrelated histories"|

[Go back to table of content ↑](#table-of-content)

## Tags 🏷️
|Git command |Description|
|--|--|
|`git tag`|List all tags|
|`git show-ref --tags`|List tags and their commit ids|
|`git tag -a <tag> -m "Message" <commit>`|Add a tag to the specified commit|
|`git tag -d <tag>`|Delete tag|
|`git push <name> --tags`|Add the local tags to the remote repository|
|`git push <name> :refs/tags/<tag>`|Delete the specified tag in the remote repository|

[Go back to table of content ↑](#table-of-content)

## Additional options 🍒
|Git command |Description|
|--|--|
|`git stash`|Save WIPs (Works in progress), in other words, changes that do not deserve to be committed yet. Stash arrange the WIPs so they can be retrieved by their indexes|
|`git stash list`|List the WIPs|
|`git stash pop <stash@{num_stash}>`|Retrieve the change of the specified WIP. If the index is not written, get the WIP at the 0 index. `pop` does not delete the WIP, to do so, run `git stash drop`|
|`git stash branch <branch>`|Apply the changes and creates a new branch with them|
|`git stash drop <stash@{num_stash}>`|Delete the specified WIP. If the index is not written, delete the WIP at the 0 index. Delete unnecesary WIPs is a good practice|
|`git clean --dry-run`|Show a list of files that a `git clean -f` command would delete if runned|
|`git clean -f`|Delete any file the user is not working on, those that are not tracked by git. The command takes into account the .gitignore file|
|`git cherry-pick <commit>`|Takes the commit of other branch and brings it to the current one without merging both branches ⚠️|
|`git commit --amend`|Add the changes to the last commit. Just as a `git commit` requires it, run `git add` before amending|
|`git mv <source> <destination>`|Move or rename a file safely. That is to say, track the change and keep the history registry of such a file|
|`git rm -r --cached .`|Refresh gitignore. (Clear the git cache)|

[Go back to table of content ↑](#table-of-content)

## Search in files and commits, find authors 🕵️‍♀️
|Git command |Description|
|--|--|
|`git grep <word>`|Search the specified word in the repository files. It is case sensitive. Add `-n` to show the line where the word appears, `-c` to show how many times it appears|
|`git log -S "word"`|Search the specified word in the repository's history|
|`git blame <file>`|Show the author of each line of code of the specified file: Commit id, file name, Author, timestamp of last change, line, line content|
|`git blame -L<line>,<line> <file>`|Show the author of the specified lines after `-L`. i.e. `git blame -L45,50 README.md` shows the author of the lines 45 to 50 of the README file|

[Go back to table of content ↑](#table-of-content)


## Basics
### Start
Initialize the current directory as a git repository.

    git init
     
**More info:** `git init` creates the directory (.git), all the subdirectories and files required for it to work. In case of running `git init` in a existing repository, it will not overwrite things that are already there. [Documentation.](https://git-scm.com/docs/git-init)
#### Don't forget
* README.md
* .gitignore
* License

## git checkout <commitId>
As explained on the cheatsheet, this command go back in time to the written commit. Nonetheless, what you see, is in a *detached HEAD* status, a kind of temporary anonymous branch that lets you check it out and edit it without altering the branch where you was when running the checkout command.

To "come back to the present" run `git switch -`. If what you want is to keep any change, you can create a new branch: `git switch -c <new branch>`.

### Remember how to show a graph of branches
Command: `git log --all --decorate --oneline --graph`

**Mnemonics**: 🐕 A dog = git log --**a**ll --**d**ecorate --**o**neline --**g**raph

[Go back to table of content ↑](#table-of-content)
