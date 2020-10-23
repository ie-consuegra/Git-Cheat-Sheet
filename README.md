### Choose your language / Escoge tu idioma

**English - Table of content**

- [Start](#git-cheat-sheet-en)
- [Get information]()
- [Branches](#branches-)
- ["Go back in time" and deletion of files or commits](#go-back-in-time-and-deletion-of-files-or-commits-checkout-reset-rm-%EF%B8%8F)
- [Remote repositories](#remote-repositories-)
- [Tags](#tags-%EF%B8%8F)
- [Additional options](#additional-options-)
- [Search in files and commits, find authors](#search-in-files-and-commits-find-authors-%EF%B8%8F%EF%B8%8F)

**Español - Tabla de contenido**

- [Iniciar](#git-cheat-sheet-)
- [Ramas](#ramas-)
- [Volver en el tiempo, eliminar commits o archivos](#volver-en-el-tiempo-eliminar-commits-o-archivos-checkout-reset-y-rm-%EF%B8%8F)
- [Repositorios remotos](#repositorios-remotos-)
- [Tags](#tags-%EF%B8%8F-1)
- [Opciones adicionales](#opciones-adicionales-)
- [Buscar en archivos y commits, encontrar autores](#buscar-en-archivos-y-commits-encontrar-autores-%EF%B8%8F%EF%B8%8F)

## Symbols / Convenciones
- ⚠️- Usage can be seen as a bad practice / El uso puede considerarse una mala práctica.
- <> - Used to enclose a variable word, such as file/directory names, paths, commits ids, etc. The <> signs must not be written. / Usados para definir una palabra variable como nombres de archivos o directorios, rutas, ids de commits, etc. Los signos <> no deben incluirse en el comando.

# Git Cheat Sheet (En)

## Start with git 🏁
|Git command |Description|
|--|--|
|`git init`| Initialize the current directory as a git repository |
|`git add`| Update the index of the specified directory or files to prepare for the next commit. e.g. `git add assets` add all the files of the assets directory|
|`git add .`| Add all the files, directories and subdirectories of the current directory|
|`git commit -m "Commit message"` | Create a new commit (record the changes to the repository). If the `-m` flag is not included, it launches a text editor to define the message of the commit |
|`git commit -am "Commit message"`|It is like running `git add .` and `git commit -m ...` at the same time|
|`git reset HEAD`|Unstage the files. The opposite of `git add`|

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

## Branches 🔀
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

## "Go Back in time" and deletion of files or commits (checkout, reset, rm) 🕰️
|Git command |Description|
|--|--|
|`git checkout <commit>`|Return to the version of the specified commit|
|`git reset`|Return to the version of the specified commit but delete all the commits done from that point on|
|`git reset --hard <commit>`|Reset and delete the staged changes ⚠️|
|`git reset --soft <commit>`|Reset and keep the staged changes ⚠️|
|`git rm --cached <archivo>`|Delete the staged files but keep them on the hard disk|
|`git rm --force <archivo>`|Delete the staged files and the files from the hard disk|

## Remote repositories 📡
|Git command |Description|
|--|--|
|`git clone <url>`|Clone a remote repository into the current directory|
|`git remote`|Show the remote repositories (by name). Add the flag `-v` to see the urls too|
|`git remote add <name> <url>`|Create a new connection to a remote repository. This will be called by the specified name (generally called, "origin" and "upstream")|
|`git push <name> <branch>`|Update the branch of the remote repo based on the local one|
|`git push -u <name> <branch>`|The same as above. But, set up tracking. So, after running it, you can use `git pull` or `git push`, without specifying the name of the remote repo nor the branch|
|`git pull <name> <branch>`|Update the branch of the local repo based on the remote one|
|`git pull <name> <branch> --allow-unrelated-histories`|Pull even when the projects mismatch commit histories. Useful when you just created a remote repo and added at least one commit, as local and remote repos are now unrelated, you need to "allow unrelated histories"|

## Tags 🏷️
|Git command |Description|
|--|--|
|`git tag`|List all tags|
|`git show-ref --tags`|List tags and their commit ids|
|`git tag -a <tag> -m "Message" <commit>`|Add a tag to the specified commit|
|`git tag -d <tag>`|Delete tag|
|`git push <name> --tags`|Add the local tags to the remote repository|
|`git push <name> :refs/tags/<tag>`|Delete the specified tag in the remote repository|

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

## Search in files and commits, find authors 🕵️‍♀️
|Git command |Description|
|--|--|
|`git grep <word>`|Search the specified word in the repository files. It is case sensitive. Add `-n` to show the line where the word appears, `-c` to show how many times it appears|
|`git log -S "word"`|Search the specified word in the repository's history|
|`git blame <file>`|Show the author of each line of code of the specified file: Commit id, file name, Author, timestamp of last change, line, line content|
|`git blame -L<line>,<line> <file>`|Show the author of the specified lines after `-L`. i.e. `git blame -L45,50 README.md` shows the author of the lines 45 to 50 of the README file|


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

___

# Git Cheat Sheet (Es)

## Iniciar con git 🏁
|Comando de git |Descripción|
|--|--|
|`git init`| Inicializa el directorio actual como un repositorio de git|
|`git add`| *(Añadir, agregar)* Actualiza el índice usando el contenido del directorio o archivos especificados, preparándolos para el siguiente commit. p. ej. `git add assets` añade todos los archivos del directorio assets|
|`git add .`| Añade todos los archivos, directorios y subdirectorios del directorio actual|
|`git commit -m "Mensaje del commit"` |*(Comprometer)* Crea un nuevo commit (graba los cambios al repositorio). Si el flag `-m` no se incluye, se lanza un editor de texto para definir el mensaje del commit|
|`git commit -am "Mensaje del commit"`| Equivalente a ejecutar `git add .` y `git commit -m ...` al mismo tiempo|
|`git reset HEAD`|Saca los archivos del área de staging. Lo contrario a `git add`|

## Obtener información 📜
|Comando de git |Descripción|
|--|--|
|`git config --list`|Muestra una lista de todas las variables establecidas en el archivo config|
|`git status`|Muestra el estado del árbol de trabajo ("changes not staged", "changes to be committed" (staged), "nothing to commit" ...)|
|`git branch`|Muestra una lista de las ramas. La rama actual se resalta y marca con un asterisco. Añade `-r` para mostrar las ramas remotas o `-a` para mostrarlas todas|
|`git log <path>`|*(Bitácora)* Muestra el historial de commits (id del commit, autor, fecha y mensaje), del archivo o directorio especificado|
|`git log --stat`|Muestra el historial de commits y cuanto cambió en cada uno|
|`git log --all --decorate --oneline --graph`|Muestra un árbol simplificado de logs (historial de commits)|
|`git show`|*(Mostrar)* Muestra el historial de commits y que cambió en cada uno (diff)|
|`git diff <commit A> <commit B>`|*(diff: de difference: diferencia)* Muestra las diferencias entre dos commits (no es necesario escribir todo el id del commit, las 4 primeras letras están bien) Si solo se escribe un commit, lo compara con el último (HEAD)|
|`git reflog`|Muestra un log del movimiento o posición del HEAD a través del tiempo. Cada commit, cambio de rama, merge, incluso los resets!|
|`git <comando> --help`|Muestra la documentación del comando|

## Ramas 🔀
|Comando de git |Descripción|
|--|--|
|**Crear/Eliminar/Renombrar**||
|`git branch <rama>`|Crea la rama especificada|
|`git branch -d <rama>`|Elimina la rama especificada|
|`git branch -m <ramavieja> <ramanueva>`|Cambia el nombre de rama vieja a rama nueva|
|**Switch**||
|`git checkout <rama>`|La forma "Clásica" de cambiar a otra rama|
|`git switch <rama>`|*(Cambiar)* Añadido en Git 2.23, switch provee un comando más claro y elegante para hacer esto|
|`git switch -c <rama>`|Crea una nueva rama y se cambia a esta|
|`git switch -`|Se cambia de regreso a la rama donde se hallaba anteriormente|
|**Merge y Rebase**||
|`git merge <rama>`|*(Fusionar, combinar)* Fusiona la rama especificada con la rama actual. La rama actual tiene prioridad|
|`git rebase <rama>`|Reescribe la historia del repositorio: aplica los commits de una rama a otra ⚠️|

## Volver en el tiempo, eliminar commits o archivos (checkout, reset y rm) 🕰️
|Comando de git |Descripción|
|--|--|
|`git checkout <commit>`|Devuelve a la versión del commit especificado|
|`git reset`|Devuelve a la versión del commit especificado y elimina los commits que se hubieran hecho de ese commit en adelante|
|`git reset --hard <commit>`|Reset y elimina los cambios en staging ⚠️|
|`git reset --soft <commit>`|Reset y conserva los cambios en staging ⚠️|
|`git rm --cached <archivo>`|Elimina el/los archivo(s) del staging y del próximo commit pero los conserva en el disco duro|
|`git rm --force <archivo>`|Elimina el/los archivo(s) del staging y del próximo commit. Borra los archivos del disco duro|

## Repositorios remotos 📡
|Comando de git |Descripción|
|--|--|
|`git clone <url>`|Clona un repositorio remoto al directorio local|
|`git remote`|Muestra los repositorios remotos (Por nombre). Añade la bandera `-v` para ver las urls también|
|`git remote add <nombre> <url>`|Crea una nueva conexión a un repositorio remoto. Este será llamado por el nombre especificado ("origin" y "upstream" son nombres usuales)|
|`git push <nombre> <rama>`|Actualiza la rama del repositorio remoto basado en el local|
|`git push -u <nombre> <rama>`|Igual que el mencionado arriba. Sin embargo, establece una conexión o rastreo. Es decir, después de ejecutarlo podrás usar `git pull` o `git push`, sin especificar el nombre del repositorio remoto ni la rama|
|`git pull <nombre> <rama>`|Actualiza la rama del repositorio local basado en el remoto|
|`git pull <nombre> <rama> --allow-unrelated-histories`|Hace el "pull" aún cuando los proyectos no compartan la misma historia de commits. Es útil cuando acabas de crear un repositorio remoto y has añadido al menos un commit, como los repositorios local y remoto no están relacionados, se necesita "evitar historias no relacionadas" *"allow unrelated histories"*|

## Tags 🏷️
|Comando de git |Descripción|
|--|--|
|`git tag`|Muestra la lista de tags|
|`git show-ref --tags`|Muestra la lista de tags y sus id|
|`git tag -a <tag> -m "Mensaje" <commit>`|Añade un tag al commit especificado|
|`git tag -d <tag>`|Elimina el tag especificado|
|`git push <nombre> --tags`|Añade los tags locales al repositorio remoto|
|`git push <nombre> :refs/tags/<tag>`|Elimina el tag especificado del repositorio remoto|

## Opciones adicionales para el flujo de trabajo 🍒
|Comando de git |Descripción|
|--|--|
|`git stash`|*(Esconder, escondite)* Guarda trabajos en proceso, es decir cambios que no merecen un commit aún. Se guardan en un índice o arreglo|
|`git stash list`|Muestra la lista de trabajos en proceso guardados mediante stash|
|`git stash pop <stash@{num_stash}>`|Recupera los cambios del trabajo en proceso especificado. Si no se escribe el índice del stash, recupera el trabajo guardado en la posición 0. Pero no lo elimina del índice, se necesita `git stash drop` para eso|
|`git stash branch <branch>`|Aplica los cambios de un stash y crea una rama nueva con ellos|
|`git stash drop <stash@{num_stash}>`|Elimina el trabajo en proceso indicado. Si no se escribe el índice del stash, elimina el trabajo guardado en la posición 0. Es buena práctica eliminar los trabajos en procesos cuando ya no se necesitan|
|`git clean --dry-run`|Muestra los archivos que eventualmente se borrarían de ejecutarse el comando `git clean -f`|
|`git clean -f`|*(Limpiar)* Borra los archivos con los que no se esté trabajando, es decir que no estén indexados por git. Tiene en cuenta el .gitignore|
|`git cherry-pick <commit>`|Toma el commit de otra rama y la fusiona a la rama actual sin hacer un merge ⚠️|
|`git commit --amend`|*(Remendar commit)* Agrega cambios al último commit hecho. Como al hacer un commit, se requiere un `git add` antes de ejecutarlo|
|`git mv <ruta origen> <ruta destino>`|Mueve o renombra un archivo de manera segura dentro del repositorio. Es decir, conserva el cambio dentro del historial|

## Buscar en archivos y commits, encontrar autores 🕵️‍♀️
|Comando de git |Descripción|
|--|--|
|`git grep <palabra>`|Busca la palabra especificada en los archivos del repositorio. Distingue mayúsculas y minúsculas. Añade `-n` para mostrar la línea donde la palabra aparece, `-c` para mostrar cuantas veces|
|`git log -S "palabra"`|Busca la palabra especificada en la historia del repositorio|
|`git blame <archivo>`|Muestra el autor de cada línea de código del archivo especificado, además de esta información: id del commit, nombre del archivo, Autor, fecha y hora del último cambio, línea, contenido de la línea|
|`git blame -L<línea>,<línea> <archivo>`|Muestra el autor de las líneas especificadas después de `-L`. p. ej. `git blame -L45,50 README.md` muestra el autor de las líneas 45 a 50 del archivo README|
|`git shortlog -sn`|Muestra cuantos commits ha hecho cada miembro del equipo. Añade `--all` Para incluir los miembros que han sido eliminados|


## Básico
### Para iniciar
Inicializar el directorio actual como un repositorio de git.

	git init

**Más información:** `git init` crea el directorio (.git), todos los subdirectorios y archivos necesarios por este para funcionar. En caso de ejecutar `git init` en un repositorio existente, no se sobreescribirán las cosas que ya estén allí. [Documentación.](https://git-scm.com/docs/git-init)

#### No olvides
* README.md
* .gitignore
* License

## git checkout <commitId>
Como se explica, este comando devuelve los archivos en el tiempo al commit que se indique. Sin embargo queda en un estado *detached HEAD*, por así decirlo, es una rama anónima temporal que permite revisar y editar sin afectar la rama en la que se estaba al ejecutar el checkout.

Para "volver al presente" ejecuta `git switch -`, si deseas crear cambios en ese commit y que queden en una rama, ejecuta `git switch -c <nombrerama>`.

### Recuerda como ver el árbol de commits
Comando: `git log --all --decorate --oneline --graph`

**Mnemotecnia**: 🐕 A dog (Un perro, en inglés) = git log --**a**ll --**d**ecorate --**o**neline --**g**raph
___
The information of this cheatsheet is mainly based on this [Git and GitHub course](https://platzi.com/clases/git-github/).

La información de este *cheatsheet* está basado principalmente en este [curso de Git y Github](https://platzi.com/clases/git-github/).