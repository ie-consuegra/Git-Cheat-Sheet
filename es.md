# Git Cheat Sheet (Es)

## Tabla de contenido

- [Iniciar con git](##iniciar-con-git-🏁)
- [Obtener información](#obtener-informacion-📜)
- [Ramas locales](#ramas-locales-🔀)
- [Volver en el tiempo, eliminar commits o archivos](#volver-en-el-tiempo-eliminar-commits-o-archivos-checkout-reset-y-rm-🕰️)
- [Repositorios remotos](#repositorios-remotos-📡)
- [Tags](#tags-🏷️)
- [Opciones adicionales](#opciones-adicionales-para-el-flujo-de-trabajo-🍒)
- [Buscar en archivos y commits, encontrar autores](#buscar-en-archivos-y-commits-encontrar-autores-🕵️‍♀️)

## Convenciones
- ⚠️- El uso puede considerarse una mala práctica.
- <> - Usados para definir una palabra variable como nombres de archivos o directorios, rutas, ids de commits, etc. Los signos <> no deben incluirse en el comando.

## Iniciar con git 🏁
|Comando de git |Descripción|
|--|--|
|`git init`| Inicializa el directorio actual como un repositorio de git|
|`git add`| *(Añadir, agregar)* Actualiza el índice usando el contenido del directorio o archivos especificados, preparándolos para el siguiente commit. p. ej. `git add assets` añade todos los archivos del directorio assets|
|`git add .`| Añade todos los archivos, directorios y subdirectorios del directorio actual|
|`git commit -m "Mensaje del commit"` |*(Comprometer)* Crea un nuevo commit (graba los cambios al repositorio). Si el flag `-m` no se incluye, se lanza un editor de texto para definir el mensaje del commit|
|`git commit -am "Mensaje del commit"`| Equivalente a ejecutar `git add .` y `git commit -m ...` al mismo tiempo|
|`git reset HEAD`|Saca los archivos del área de staging. Lo contrario a `git add`|

[Regresar a la tabla de contenido ↑](#tabla-de-contenido)

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

[Regresar a la tabla de contenido ↑](#tabla-de-contenido)

## Ramas locales 🔀
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

[Regresar a la tabla de contenido ↑](#tabla-de-contenido)

## Volver en el tiempo, eliminar commits o archivos (checkout, reset y rm) 🕰️
|Comando de git |Descripción|
|--|--|
|`git checkout <commit>`|Devuelve a la versión del commit especificado|
|`git reset`|Devuelve a la versión del commit especificado y elimina los commits que se hubieran hecho de ese commit en adelante|
|`git reset --hard <commit>`|Reset y elimina los cambios en staging ⚠️|
|`git reset --soft <commit>`|Reset y conserva los cambios en staging ⚠️|
|`git rm --cached <archivo>`|Elimina el/los archivo(s) del staging y del próximo commit pero los conserva en el disco duro|
|`git rm --force <archivo>`|Elimina el/los archivo(s) del staging y del próximo commit. Borra los archivos del disco duro|

[Regresar a la tabla de contenido ↑](#tabla-de-contenido)

## Repositorios remotos 📡
|Comando de git |Descripción|
|--|--|
|`git clone <url>`|Clona un repositorio remoto al directorio local|
|`git remote`|Muestra los repositorios remotos (Por nombre). Añade la bandera `-v` para ver las urls también|
|`git remote add <nombre> <url>`|Crea una nueva conexión a un repositorio remoto. Este será llamado por el nombre especificado ("origin" y "upstream" son nombres usuales)|
|`git push <nombre> <rama>`|Actualiza la rama del repositorio remoto basado en el local|
|`git push -u <nombre> <rama>`|Igual que el mencionado arriba. Sin embargo, establece una conexión o rastreo. Es decir, después de ejecutarlo podrás usar `git pull` o `git push`, sin especificar el nombre del repositorio remoto ni la rama|
|`git push <name> --delete <branch>`|Elimina una rama remota. Recuerda el flag `--delete`|
|`git push --set-upstream origin <localbranch>`|Crea una nueva rama en el repositorio remoto, en este ejemplo es llamado 'origin'|
|`git pull <nombre> <rama>`|Actualiza la rama del repositorio local basado en el remoto|
|`git pull <nombre> <rama> --allow-unrelated-histories`|Hace el "pull" aún cuando los proyectos no compartan la misma historia de commits. Es útil cuando acabas de crear un repositorio remoto y has añadido al menos un commit, como los repositorios local y remoto no están relacionados, se necesita "evitar historias no relacionadas" *"allow unrelated histories"*|

[Regresar a la tabla de contenido ↑](#tabla-de-contenido)

## Tags 🏷️
|Comando de git |Descripción|
|--|--|
|`git tag`|Muestra la lista de tags|
|`git show-ref --tags`|Muestra la lista de tags y sus id|
|`git tag -a <tag> -m "Mensaje" <commit>`|Añade un tag al commit especificado|
|`git tag -d <tag>`|Elimina el tag especificado|
|`git push <nombre> --tags`|Añade los tags locales al repositorio remoto|
|`git push <nombre> :refs/tags/<tag>`|Elimina el tag especificado del repositorio remoto|

[Regresar a la tabla de contenido ↑](#tabla-de-contenido)

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
|`git rm -r --cached .`|Refrescar gitignore. (Vaciar el git cache)|

[Regresar a la tabla de contenido ↑](#tabla-de-contenido)

## Buscar en archivos y commits, encontrar autores 🕵️‍♀️
|Comando de git |Descripción|
|--|--|
|`git grep <palabra>`|Busca la palabra especificada en los archivos del repositorio. Distingue mayúsculas y minúsculas. Añade `-n` para mostrar la línea donde la palabra aparece, `-c` para mostrar cuantas veces|
|`git log -S "palabra"`|Busca la palabra especificada en la historia del repositorio|
|`git blame <archivo>`|Muestra el autor de cada línea de código del archivo especificado, además de esta información: id del commit, nombre del archivo, Autor, fecha y hora del último cambio, línea, contenido de la línea|
|`git blame -L<línea>,<línea> <archivo>`|Muestra el autor de las líneas especificadas después de `-L`. p. ej. `git blame -L45,50 README.md` muestra el autor de las líneas 45 a 50 del archivo README|
|`git shortlog -sn`|Muestra cuantos commits ha hecho cada miembro del equipo. Añade `--all` Para incluir los miembros que han sido eliminados|

[Regresar a la tabla de contenido ↑](#tabla-de-contenido)

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