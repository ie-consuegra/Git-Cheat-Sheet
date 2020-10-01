### Choose your language / Escoge tu idioma
* [English](#git-cheat-sheet-en)
* [Español](#git-cheat-sheet-es)

<!--
### Symbols / Convenciones
⚠️- Mandatory. You have to run it at some point. / Obligatorio, debes ejecutarlo en algún momento.
⭐- Favorite. Just my preference on certain commands / Favorito, Solo es mi preferencia en algunos comandos
<>- Must not be included in the command / No deben incluirse en el comando
-->

# Git Cheat Sheet (En)
|Git commands |Description|
|--|--|
|**Start with git**||
|`git init`| Initializes the current directory as a git repository |
|`git add`| Stage all changes of the specified directory or files for the next commit. e.g. `git add assets` stage all the files of the assets directory|
|`git add .`| Stage all changes of all the files, directories and subdirectories of the repository|
|`git commit -m "Commit message"` | Commits the staged snapshot. If the -m flag is not included, it launches a text editor to define the message of the commit |
|`git commit -am "Commit message"`|It is like running `git add .` and `git commit -m ...` at the same time|
|`git reset HEAD`||
|**Get information**||
|`git config --list`||
|`git status`||
|`git branch`|List branches. The current branch will be highlighted and marked with an asterisk|
|`git log <path>`|Show commit logs (commit id, author, date and message), the "history", of the specified file or directory|
|`git log --stat`|Show commit logs and how much it changed in each one|
|`git log --all --decorate --oneline --graph`|Show a simplified tree of logs ⭐|
|`git show`|Show the commit logs and what changed in each one (diff)|
|`git diff <commit A> <commit B>`|Show the differences between two commits (no need to write the whole commit id, the first 4 letters are ok) If just one commit is written, it compares it with the last one, the HEAD|

## Branches
|Git commands |Description|
|--|--|
|**Create/Delete**||
|`git branch < branch >`|Creates a branch called branch|
|`git branch -d < branch >`|Deletes the branch called branch|
|**Switch**||
|`git checkout < branch >`|The "classic" way to switch to other branch|
|`git switch < branch >`|Added in Git 2.23, switch provides a clearer and sleek command to do this|
|`git switch -c < branch >`|Creates a new branch and switches to it|
|`git switch -`|Switch back to the last checked branch|
|``||


## Basics
### Start
Initialize the current directory as a git repository.

	git init
	 
**More info:** `git init` creates the directory (.git), all the subdirectories and files required for it to work. In case of running `git init` in a existing repository, it will not overwrite things that are already there. [Documentation.](https://git-scm.com/docs/git-init)
#### Don't forget
* README.md
* .gitignore
* License

### Remember how to show a graph of branches
Command: `git log --all --decorate --oneline --graph`

**Mnemonics**
🐕 A dog = git log --**a**ll --**d**ecorate --**o**neline --**g**raph


# Git Cheat Sheet (Es)
## Básico
### Para iniciar
Inicializar el directorio actual como un repositorio de git.

	git init

**Más información:** `git init` crea el directorio (.git), todos los subdirectorios y archivos necesarios por este para funcionar. En caso de ejecutar `git init` en un repositorio existente, no se sobreescribirán las cosas que ya estén allí. [Documentación.](https://git-scm.com/docs/git-init)
#### Don't forget
* README.md
* .gitignore
* License
