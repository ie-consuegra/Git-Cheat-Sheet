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
|`git init`| Initialize the current directory as a git repository |
|`git add`| Update the index of the specified directory or files to prepare for the next commit. e.g. `git add assets` add all the files of the assets directory|
|`git add .`| Add all the files, directories and subdirectories of the current directory|
|`git commit -m "Commit message"` | Create a new commit (record the changes to the repository). If the `-m` flag is not included, it launches a text editor to define the message of the commit |
|`git commit -am "Commit message"`|It is like running `git add .` and `git commit -m ...` at the same time|
|`git reset HEAD`||
|**Get information**||
|`git config --list`|List all variables set in config file|
|`git status`|Show the working tree status ("changes not staged", "changes to be committed" (staged), "nothing to commit" ...)|
|`git branch`|List branches. The current branch will be highlighted and marked with an asterisk. Add `-r` to show remote branches or `-a` to show them all|
|`git log <path>`|Show commit logs (commit id, author, date and message), the "history", of the specified file or directory|
|`git log --stat`|Show commit logs and how much it changed in each one|
|`git log --all --decorate --oneline --graph`|Show a simplified tree of logs ⭐|
|`git show`|Show the commit logs and what changed in each one (diff)|
|`git diff <commit A> <commit B>`|Show the differences between two commits (no need to write the whole commit id, the first 4 letters are ok) If just one commit is written, it compares it with the last one, the HEAD|

## Branches
|Git commands |Description|
|--|--|
|**Create/Delete**||
|`git branch <branch>`|Creates the specified branch|
|`git branch -d <branch>`|Deletes the specified branch|
|**Switch**||
|`git checkout <branch>`|The "classic" way to switch to other branch|
|`git switch <branch>`|Added in Git 2.23, switch provides a clearer and sleek command to do this|
|`git switch -c <branch>`|Creates a new branch and switches to it|
|`git switch -`|Switch back to the last checked branch|
|**Merge and Rebase**||
|`git merge <branch>`|Merge the specified branch with the current one. The current branch has priority|
|`git rebase <branch>`||

## Remote repositories
|Git commands |Description|
|--|--|
|`git clone <url>`|Clone a remote repository into the current directory|
|`git remote`|Show the remote repositories (by name). Add the flag `-v` to see the urls too|
|`git remote add <name> <url>`|Create a new connection to a remote repository. This will be called by the specified name (generally called, "origin" and "upstream")|
|`git push <name> <branch>`|Update the branch of the remote repo based on the local one|
|`git push -u <name> <branch>`|The same as above. But, set up tracking. So, after running it, you can use `git pull` or `git push`, without specifying the name of the remote repo nor the branch|
|`git pull <name> <branch>`|Update the branch of the local repo based on the remote one|
|`git pull <name> <branch> --allow-unrelated-histories`|Pull even when the projects mismatch commit histories. Useful when you just created a remote repo and added at least one commit, as local and remote repos are now unrelated, you need to "allow unrelated histories"|

## Tags
|Git commands |Description|
|--|--|
|`git tag`|List all tags|
|`git show-ref --tags`|List tags and their commit ids|
|`git tag -a <tag> -m "Message" <commit>`|Add a tag to the specified commit|
|`git tag -d <tag>`|Delete tag|
|`git push <name> --tags`|Add the local tags to the remote repository|
|`git push <name> :refs/tags/<tag>`|Delete the specified tag in the remote repository|

## Additional options
|Git commands |Description|
|--|--|
|`git stash`||
|`git stash list`||
|`git stash pop <stash>`||
|`git stash branch <branch>`||
|`git stash drop <stash>`||
|`git clean`||
|`git clean --dry-run`||
|`git clean -f`||
|`git cherry-pick <commit>`||
|`git commit-ammend`||

## Search in files and commits, find authors
|Git commands |Description|
|--|--|
|`git grep <word>`|Search the specified word in the repository files. It is case sensitive. Add `-n` to show the line where the word appears, `-c` to show how many times it appears|
|`git log -S "word"`|Search the specified word in the repository's history|
|`git blame <file>`|Show the author of each line of code of the specified file: Commit id, file name, Author, timestamp of last change, line, line content|
|`git blame -L<line>,<line> <file>`|Show the author of the specified lines after `-L`. i.e. `git blame -L45,50 README.md` shows the author of the lines 45 to 50 of the README file|

## Reset and rm
|Git commands |Description|
|--|--|
|`git reset`||
|`git reset --hard`||
|`git reset <commit>`||
|`git reset --soft`||
|`git reset rm --cached`||
|`git reset rm --force`||

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

|Comandos de git |Descripción|
|--|--|
|**Iniciar con git**||
|`git init`| Inicializa el directorio actual como un repositorio de git|
|`git add`| *(add: Añadir, agregar)* Actualiza el índice usando el contenido del directorio o archivos especificados, preparándolos para el siguiente commit. p. ej. `git add assets` añade todos los archivos del directorio assets|
|`git add .`| Añade todos los archivos, directorios y subdirectorios del directorio actual|
|`git commit -m "Mensaje del commit"` |*(commit: Comprometer)* Crea un nuevo commit (graba los cambios al repositorio). Si el flag `-m` no se incluye, se lanza un editor de texto para definir el mensaje del commit|
|`git commit -am "Mensaje del commit"`| Equivalente a ejecutar `git add .` y `git commit -m ...` al mismo tiempo|
|`git reset HEAD`||
|**Obtener información**||
|`git config --list`|Muestra una lista de todas las variables establecidas en el archivo config|
|`git status`|Muestra el estado del árbol de trabajo ("changes not staged", "changes to be committed" (staged), "nothing to commit" ...)|
|`git branch`|Muestra una lista de las ramas. La rama actual se resalta y marca con un asterisco. Añade `-r` para mostrar las ramas remotas o `-a` para mostrarlas todas|
|`git log <path>`|*(log: Bitácora)* Muestra el historial de commits (id del commit, autor, fecha y mensaje), del archivo o directorio especificado|
|`git log --stat`|Muestra el historial de commits y cuanto cambió en cada uno|
|`git log --all --decorate --oneline --graph`|Muestra un árbol simplificado de logs (historial de commits) ⭐|
|`git show`|*(show: Mostrar)* Muestra el historial de commits y que cambió en cada uno (diff)|
|`git diff <commit A> <commit B>`|*(diff: de difference: diferencia)* Muestra las diferencias entre dos commits (no es necesario escribir todo el id del commit, las 4 primeras letras están bien) Si solo se escribe un commit, lo compara con el último (HEAD)|

## Ramas
|Comandos de git |Descripción|
|--|--|
|**Crear/Eliminar**||
|`git branch <branch>`|Crea la rama especificada|
|`git branch -d <branch>`|Elimina la rama especificada|
|**Switch**||
|`git checkout <branch>`|La forma "Clásica" de cambiar a otra rama|
|`git switch <branch>`|*(switch: Cambiar)* Añadido en Git 2.23, switch provee un comando más claro y elegante para hacer esto|
|`git switch -c <branch>`|Crea una nueva rama y se cambia hacia esta|
|`git switch -`|Se cambia de regreso a la rama donde se hallaba anteriormente|
|**Merge y Rebase**||
|`git merge <branch>`|*(merge: Fusionarse, combinarse)* Fusiona la rama especificada con la rama actual. La rama actual tiene prioridad|
|`git rebase <branch>`||

## Repositorios remotos
|Comandos de git |Descripción|
|--|--|
|`git clone <url>`|Clona un repositorio remoto al directorio local|
|`git remote`|Muestra los repositorios remotos (Por nombre). Añade la bandera `-v` para ver las urls también|
|`git remote add <nombre> <url>`|Crea una nueva conexión a un repositorio remoto. Este será llamado por el nombre especificado ("origin" y "upstream" son nombres usuales)|
|`git push <nombre> <rama>`|Actualiza la rama del repositorio remoto basado en el local|
|`git push -u <nombre> <rama>`|Igual que el mencionado arriba. Sin embargo, establece una conexión o rastreo. Es decir, después de ejecutarlo podrás usar `git pull` o `git push`, sin especificar el nombre del repositorio remoto ni la rama|
|`git pull <nombre> <rama>`|Actualiza la rama del repositorio local basado en el remoto|
|`git pull <nombre> <rama> --allow-unrelated-histories`|Hace el "pull" aún cuando los proyectos no compartan la misma historia de commits. Es útil cuando acabas de crear un repositorio remoto y has añadido al menos un commit, como los repositorios local y remoto no están relacionados, se necesita "evitar historias no relacionadas" *"allow unrelated histories"*|

## Tags
|Comandos de git |Descripción|
|--|--|
|`git tag`|Muestra la lista de tags|
|`git show-ref --tags`|Muestra la lista de tags y sus id|
|`git tag -a <tag> -m "Mensaje" <commit>`|Añade un tag al commit especificado|
|`git tag -d <tag>`|Elimina el tag especificado|
|`git push <nombre> --tags`|Añade los tags locales al repositorio remoto|
|`git push <nombre> :refs/tags/<tag>`|Elimina el tag especificado del repositorio remoto|

## Opciones adicionales
|Comandos de git |Descripción|
|--|--|
|`git stash`||
|`git stash list`||
|`git stash pop <stash>`||
|`git stash branch <branch>`||
|`git stash drop <stash>`||
|`git clean`||
|`git clean --dry-run`||
|`git clean -f`||
|`git cherry-pick <commit>`||
|`git commit-ammend`||

## Buscar en archivos y commits, encontrar autores
|Comandos de git |Descripción|
|--|--|
|`git grep <palabra>`|Busca la palabra especificada en los archivos del repositorio. Distingue mayúsculas y minúsculas. Añade `-n` para mostrar la línea donde la palabra aparece, `-c` para mostrar cuantas veces|
|`git log -S "palabra"`|Busca la palabra especificada en la historia del repositorio|
|`git blame <archivo>`|Muestra el autor de cada línea de código del archivo especificado, además de esta información: id del commit, nombre del archivo, Autor, fecha y hora del último cambio, línea, contenido de la línea|
|`git blame -L<línea>,<línea> <archivo>`|Muestra el autor de las líneas especificadas después de `-L`. p. ej. `git blame -L45,50 README.md` muestra el autor de las líneas 45 a 50 del archivo README|

## Reset y rm
|Comandos de git |Descripción|
|--|--|
|`git reset`||
|`git reset --hard`||
|`git reset <commit>`||
|`git reset --soft`||
|`git reset rm --cached`||
|`git reset rm --force`||

## Básico
### Para iniciar
Inicializar el directorio actual como un repositorio de git.

	git init

**Más información:** `git init` crea el directorio (.git), todos los subdirectorios y archivos necesarios por este para funcionar. En caso de ejecutar `git init` en un repositorio existente, no se sobreescribirán las cosas que ya estén allí. [Documentación.](https://git-scm.com/docs/git-init)

#### No olvides
* README.md
* .gitignore
* License

The information of this cheatsheet is mainly based on this [Git and GitHub course](https://platzi.com/clases/git-github/).
La información de este *cheatsheet* está basado principalmente en este [curso de Git y Github](https://platzi.com/clases/git-github/).