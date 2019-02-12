# invie-github
Este proyecto es solo para probar GIT


Sistemas de Control de Versiones
¿Qué es un Sistema de Control de Versionas?
Un Version Control Systems (VCS) es una herramienta que ayuda a administrar los cambios en el código fuente a lo largo del tiempo. Este sistema se encarga de monitorear el código e informa si el mismo ha sido modificado con el fin de registrar dicho cambio, es así de simple, tal como lo lees. Version Control System
Existen diferentes tipos de Sistemas de Control de Versiones, estan los:
Locales: En este tipo el repositorio vive en tu computador.
Centralizados: Existe un repositorio central (en un super-servidor) donde se encuentra todo el código.
Distribuidos: Cada programador tiene una copia propia en su computador del repositorio original, de esta forma los cambios que realice de forma local no afectarán al resto de programadores que se encuentran trabajando para el proyecto. Git es distribuido.
¿Que es Git?
Git es un Sistema de Control de Versiones, de hecho, es el más moderno y usado en el mundo. Git fue desarrollado por Linus Torvalds en el 2005 y es un proyecto de Open Source muy maduro y en constante mantenimiento por la comunidad.

Git es tan confiable que una cantidad asombrosa de proyectos confian en el, incluso la NASA.

Los tres estados de Git
Lo más importante que se debe conocer de Git son sus tres estados principales: Working Directory, Staging Area and Git Repository
Working Directory: Es al lugar donde se trabajan los archivos.
Staging Area: Es el área de preparación de los archivos que serán registrados en el repositorio.
Git Repository: Es el lugar donde se almacena el código de forma segura.
¿Que es GitHub?
GitHub es una plataforma de alojamiento de código para control de versiones y colaboración. Te permite a ti y a otros trabajar juntos en proyectos desde cualquier lugar. GitHub
Instalación y configuración de Git
Para instalar Git en Linux especificamente en las distribución de Debian/Ubuntu o derivadas, se ejecuta el comando:
apt-get install git Instala Git en Linux.
git --version Muestra la versión de Git instalada (este comando ayuda a verificar si Git se instaló correctamente).
git config --global user.email [e@mail.com] Establece un correo electronico.
git config --global user.name [username] Establece un nombre de usuario.
git config --global color.ui [true or false] Habilita colores en la UI.
Puedes obtener más información sobre las configuraciones de Git en la Documentación Oficial de Git.

Flujos de trabajo en Git
Creando y Eliminando Repositorios (git init)
git init [dir-name] Crea un repositorio, el nombre de la carpeta es opcional, en caso de colocarlo se creará dicho directorio, en caso de no hacerlo simplemente se creará el repositorio partiendo de la carpeta actual.
rm -rf .git Eliminar la carpeta .git es lo mismo a eliminar el repositorio (de forma local).
Agregando, quitando y viendo el estatus de archivos (git add | rm | status)
git add -A Agrega todos los archivos del Working Directory al Staging Area.
git add [file or directory] Agrega un archivo o carpeta del Working Directory al Staging Area.
git add -n [file or directory] Simula el agregado de un archivo o directorio al Staging Area pero la verdad no lo hace.
git rm --cached [file or directory] Elimina un archivo o carpeta del Staging Area y lo deja en el Working Directory.
git rm -f [file or directory] Fuerza la eliminación de un archivo o carpeta del Staging Area tanto así que hasta lo borra del Working Directory.
git status Muestra el estado de los archivos o directorios.
Los archivos que salen en rojo: Se encuentran en el Working Directory.
Los archivos que salen en verde: Se encuentran en el Staging Area.
Confirmando cambios (git commit)
git commit -m "[description...]" Agrega los archivos del Staging Area al Git Repository con una descripción.
git commit -m --amend En caso de equivocarse con algún registro (commit) con la bandera --amend se puede rectificar y concatenar los cambios al último commit. Si se usa la bandera -m "[description...]" el nuevo mensaje sobrescribirá al anterior, en caso de no hacerlo se mantendrá el antiguo.
Etiquetando confirmaciones (git tag)
git tag -a [1.x] -m "[descripcion]" Registra un tag.
git tag -l Lista los tags existentes..
git tag [1.x] [Commit HASH] Le registra un tag a un Commit en especifico por medio de su HASH.
git tag -f -a [1.x] -m "[description...]" [Commit HASH] Permite renombrar un tag.
git tag -d [1.x] Elimina un tag.
Revisando la historia de nuestro proyecto (git log)
git log Muestra el historial de los registros (commits) del proyecto con sus respectivos autores, hora especifica y descripciones (en caso de tenerlo).
git config --global alias.[superlog] "log ..." Permite agregarle alias a git log
    git config --global alias.superlog "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
Revisando los cambios entre versiones (git diff)
git diff [Commit HASH] Muestra los cambios que se han realizados entre el estado actual y el commit especificado por su HASH.
git diff [Commit HASH #1] [Commit HASH #2] Muestra los cambios que se han realizados entre el commit #1 y el commit #2 especificado por su HASH.
Cuando las comparaciones salen en rojo significa que se eliminaron cosas en cambio si sale en verde significa que se agregaron cosas.

Revertir cambios en Git
git reset --soft [HASH] Partiendo de un Commit identificado por su HASH, elimina todos los Commits futuros a el y mantiene todos esos cambios (registrados en los Commits eliminados) en el Staging Area.
git reset --mixed [HASH] Partiendo de un Commit identificado por su HASH, elimina todos los Commits futuros a el y mantiene todos esos cambios (registrados en los Commits eliminados) en el Working Directory.
git reset --hard [HASH] Partiendo de un Commit identificado por su HASH, elimina todos los Commits futuros a el y no mantiene los cambios ni en el Staging Area ni en el Working Directory de los Commits eliminados.
Múltiples entornos de trabajo
Múltiples variantes del repositorio (git branch)
Una rama es una línea alterna del tiempo (del proyecto). La rama por defecto es master, la rama de GitHub Pages es gh-pages y cuando se trabaja como colaborador se identifica el proyecto principal con la rama upstream.

git branch [name-branch] Crea una nueva rama.
git checkout -b [name-branch] Crea una nueva rama y se posiciona en ella.
git branch -l Lista todos las ramas que existen.
git branch -d [name-branch] Elimina una rama. Con -D se fuerza el borrado.
git branch -m [old-name-branch] [new-name-branch] Permite renombrar una nueva rama.
Moviéndonos entre ramas y versiones (git checkout)
git checkout [name-branch or commit-HASH] Permite moverse entre ramas o entre los Commits de una rama.
Mezclando ramas y resolviendo conflictos
En Git se pueden mezclar ramas, al realizar una fusión ocurrirá que la operación se realizó con éxito (Fast-Forward) o que la operación presentó unos conflictos (Manual Merge) ¿no te quedó claro?
Fast-Forward: Es lo que ocurre cuando ocurre un cambio en una rama y al fusionarla con la otra no presenta conflictos ¿por qué no presenta problemas? Porque solo en una rama ocurrió un cambio en la misma línea de código por lo tanto se agrega la nueva y se reemplaza la vieja.
Manual Merge: Es lo que ocurre cuando en ambas ramas se realizaran modificaciones afectando las mismas líneas de código ¿que pasa con esto? Sencillo, Git te pedirá que elijas con cual fragmento de código (cambio) te quedarás y lo dividirá con unas flechas, por ejemplo:
     <<<<< [Rama A]
     [Aquí estará el código de la modificación  número 1]
     =====
     [Aquí estará el código de la modificación  número 2]
     >>>>> [Rama B]
git merge [name-branch] Fusiona una rama con la actual (con la rama en la que nos encontramos posicionados).
Guardando cambios temporalmente (git stash)
git stash Guarda el status de forma temporal (pero los archivos deben estar en el Staging Area).
git stash list Lista los Stashes.
git stash drop stash@{#} Elimina un Stash por medio de su ID.
git stash apply Aplica el último Stash creado.
Cherry pick eligiendo commits selectivamente
git cherry pick [HASH] Mueve un Commit hecho en una rama (Branch A) a otra rama (Branch B).
GitHub
Clonando repositorios remotos (git clone/fork)
git clone [SSH/HTTPS] Clona un repositorio desde GitHub a nuestro equipo local.
Añadiendo un repositorio remoto a uno local (git remote)
git remote add [origin] [SSH/HTTPS] Conecta un repositorio con nuestro equipo local.
git remote -v Lista las conexiones existentes.
git remote remove [origin] Elimina una conexión con algún repositorio.
Trayendo cambios desde el repositorio remoto (git fetch/pull)
git fetch [origin] Descarga cambios de GitHub y crea una rama llamada origin/master que luego se debe fusionar con la master de nuestro entorno local.
git pull [origin] Descarga cambios de GitHub y los fusiona automáticamente la rama espejo origin/master a la rama master de nuestro entorno local.
Enviando cambios al repositorio remoto
git push -u [origin] [name-branch] Empujar una rama a el repositorio remoto en GitHub.
