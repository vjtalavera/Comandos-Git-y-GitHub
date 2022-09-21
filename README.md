# Comandos-Git-y-GitHub

https://tecnologiasplexus.udemy.com/course/git-github/learn/lecture/7340564?start=0#overview

------------------ Git ----------------

git help                -- ayuda

git config --global user.name "Nombre"    -- hacer configuracion global
git config --global user.email "email@gmail.com"

git config --global -e                    -- datos del usuario

git init                               -- inicializa repositorio local

git config --global init.defaultBranch main --establece rama inicial a main

git status                 -- informacion sobre commit, rama en la que estas
                           -- que archivos han sido modificados

git add .             -- preparar los archivos para hacer seguimiento

git reset archivo     -- saca al archivo del stage

git clean -n          -- para ver una prueba de la ejecucion
git clean -f          -- para forzar la eliminación de archivos sin seguimiento
git clean -f -d       -- para forzar la eliminación de directorios sin seguimiento;
git clean -f -x       -- para eliminar el sin seguimiento a . gitignore ficheros y .
Add the -i switch to do an interactive 'git clean'.

git commit -m "nombre del commit"  -- hace foto de nuestro seguimiento

git log                  -- resumen de lo que has hecho
git log --stat           -- los archivos que se modificaron en cada commit
git log --patch          -- mas detalle que la linea anterior
git log --format=short
git log --oneline --graph --decorate --all
git log --graph --abbrev-commit --decorate --date=relative --all 

git log --pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --all


git checkout -- .         -- recupera version al ultimo commit

git branch               -- te dice en que rama estas

git branch -m master main  -- cambiar el nombre de la rama a main

git commit -am "texto"   -- es el equivalente a git add . git commit -m "texto"

git log --oneline        -- resumen de lo que has hecho resumido

git log --oneline --decorate --all --graph

git diff            -- comparar con los cambios anteriores
git diff --staged   -- comparar con los ultimos cambios

git log                  -- log de todos los cambios
muestra el hash, identificador unico
git log --decorate --graph --oneline --date-order

git add carpeta/         -- añada todas las carpetas y subcarpetas de carpeta

git config --global alias.s "status --short"      -- crea un alias llamado s que contiene el comando git status --short

git status             -- ver el estado actual
git status --short     -- ver el estado actual resumido
git status --short -b  -- ver el estado actual resumido y branch

git commit --amend -m "instalaciones actualizadas pendientes"  --actualiza ensaje ultimo enviado

git reset --soft HEAD^2       -- hace cambios en el tiempo el anterior al ultimo, puedes poner 3,4,etc....
git reset --soft "numeroHash"  -- los cambios los mantiene
git reset --mixed "numeroHash" -- los cambios no son destructivos y quedan listos para meterlos en el stage
git reset --hard "numeroHash"  -- los cambios son destructivos

git config core.autocrlf true    -- configurar salto de linea

git commit --amend               -- para revertir ultimo cambio y modificar algo

git reflog                    -- historico de git
y luego git reset --hard "numeroHash"     -- para recuperar a lo que querias

git restore --staged       --recupera el archivo del staged

git mv destruir-mundo.md salvar-mundo.md

git rm salvar-mundo.md        --borrar archivo
git rm .env --cached          --borrar archivo del repositorio

git reset --hard             --recupera archivo despues de borrarlo paso anterior


git branch nombre             -- crear ramas

git checkout rama-villanos    -- te mueves a la rama-villanos

git merge rama-villanos    -- une el contenido de la rama-villanos a master

git branch -d nombre -f    -- borra rama con -f fuerza a borrarla

git checkout -b nombre    --crea rama y te pasa a ella automaticamente

tags - etiquetas, son una referencia a un commit en el tiempo.

git tag version-final   -- crea etiqueta
git tag -d nombre       -- borra etiqueta
git tag -a v1.0 -m "Version 1.0"   -- crea version de tag de donde estas. Crea una version final.
git tag -a v0.1 numeroHash -m "Version 0.1 alfa"  --crea version a partir de un hash en concreto
git push --tags         -- sube los tags

------- stash y rebase ------

git stash               -- se usa para guardar nuestro trabajo realizdo, no perderlo, y pasar a un evento anterior.
                        -- Y para luego recuperar el stash y continuar por donde ibamos. 
			-- se usa sin hacerle commit a nuestro trabajo
git stash list          -- ver estado de los stash hechos

git stash pop           -- coge el ultimo stash y lo recupera

git commit -am "texto"  -- ya tienes actualizado tu ultimo trabajo recupeado.

git stash clear         -- borra todos los stash hechos, aunque con:

git reflog              -- te dice el historico de los cambios

git stash pop           -- restablece el ultimo stash

git stash apply stash@{2}  -- recupera un stash en particular

git stash drop stash@{2}   -- borra un stash en particular

git stash show stash@{2}   -- muestra informacion de un stash en particular

git stash save "nombre al stash" -- se da nombre al stash

git stash list --stat      -- detalle de los stash


git rebase    -- crea un area temporal para guardar nuestras ramas y luego recuperarlas
git checkout "rama-desarrollo"
git rebase master
git checkout master
git merge rama-desarrollo

git rebase -i HEAD~4                 
-- se usa para separar commits realizados
-- cuando no has subido tus cambios al repositorio
-- con sus opciones squash reword edit

git checkout -- README.md       -- recupera el archivo README.md a como estaba anteriormente.

git rebase -i HEAD~4

git rebase --continue


------------------------ GitHub -----------------

git remote -v  -- muestra los repositorios

git push -u origin master
-- origin nombre del repositorio
-- master rama que deseamos enviar
-- -u Nos ayuda a que la proxima vez que queramos hacer push, no necesitemos especificar la rama

...or create a new repository on the command line
echo "# liga-justicia" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/vjtalavera/liga-justicia.git
git push -u origin main

...or push an existing repository from the command line
git remote add origin https://github.com/vjtalavera/liga-justicia.git
git branch -M main
git push -u origin main

git tag                      -- ver los tag
git push --tags              -- desplegar los tag

git pull                  -- descarga informacion del repositorio remoto
git pull origin main      -- es lo mismo, tener en cuenta que el primero se hizo con la opcion -u

git config --global pull.ff only     -- se define la estrategia de fast-forward en los pull
git config --global -e

git clone https://github.com/vjtalavera/liga-justicia.git

git push -u origin main      -- sube archivos al repositorio origin rama main

git config --global -e       -- ver configuracion global del usuario

git config pull.rebase true           -- configuracion local rebase true
git config --global pull.rebase true  -- configuracion global

git rebase --continue
git rebase --skip
git rebase --abort

Pull requests ----- hacer analisis previo a la union de información.

git branch -d test-branch   --borra rama local
git branch -D <branch-name> --borra rama local independientemente de su estado
git push <remote-name> --delete <branch-name>     --borrar rama remota
---------- borrar ramas remotas --------
git push origin :rama-villanos

git remote prune origin   -- revisa y borra ramas remotas que ya no existen

git fetch    -- descarga los commits, archivos y referencias, pero sin obligar 
             -- a fusionar los cambios en tu repositorio
git fetch <remote> -- Recupera todas las ramas del repositorio. 
                   -- También descarga todos los commits y archivos requeridos del otro repositorio.
git fetch <remote> <branch>  -- Realiza la misma acción que el comando anterior, 
                             -- pero solo recupera la rama especificada.
git fetch --all   --Una función potente que recupera todos los repositorios remotos registrados 
                  --y sus ramas.

git fetch --dry-run   --ejecutará una demo del comando. Genera ejemplos de acciones que realizará durante 
                      --la recuperación, pero no los aplica.

git checkout  --El comando git checkout opera sobre tres entidades distintas: 
              --archivos, confirmaciones y ramas.
              --Te permite desplazarte entre las ramas creadas por git branch
              --Cambia entre versiones de código que ya se encuentran en el sistema local.




git remote     -- identifica el nombre del repositorio remoto

git remote add upstream [HTTPS] -- extraer los cambios desde el repositorio original a tu version local. Aquí, [HTTPS] es el URL que debes copiar del repositorio del propietario

git fetch upstream          -- Busca todos los cambios  del repositorio original. Las confirmaciones (commits) del repositorio original serán almacenadas en una rama local llamada upstream/master.

-------------------------- flujo para comprobacion --------------------
1.
git fetch
git branch -a                 --ver todas las ramas y remotas tambien
git checkout rama-capitan

2.
git checkout main
git merge rama-capitan
git push

--------------------- otra forma ------------------
1.
git push origin rama-silver
Pull Request

-------- crear una etiqueta con una version ---------
git tag -a v0.0.1 -m "Version inicial"
git push --tags            --para subir los tags

-------- subir las ramas --------
git push --set-upstream origin rama-usuario      -- hacerlo por primera vez y partir de ahi,
                                                 -- ya acepta el git push


git config --global -e
[alias]
        s = status --short --branch
        lg = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all


------ Borrar un commit 
---si NO hemos subido el commit a nuestro repositorio remoto (no hemos realizado push), lo podemos hacer de 2 formas: 

1) git reset --hard HEAD~1     
                               --head: Con esta opción estamos indicando que retrocedemos a el comit HEAD~1 y perdemos todas 
                               -- las confirmaciones posteriores. HEAD~1 es un atajo para apuntar al commit anterior al que nos encontramos. 
                               -- CUIDADO, con la opcion –head, ya que como he dicho se borran todos los commits posteriores al commit 
                               -- al que indicamos.
2) git reset --soft HEAD~1     ---
                               --soft: con esta opción estamos indicando que retrocedemos a el commit HEAD~1 y no perdemos 
                               --los cambios de los commits posteriores. Todos los cambios aparecerán como pendientes para realizar un commit.

--- Solución si hemos subido el commit a nuestro repositorio remoto (hemos realizado push):
--En caso de que queramos borrar un commit que ya hemos subido al servidor remoto, la mejor opcion es realizar un nuevo commit 
-- que borre el commit que queremos eliminar utilizando el comando revert.

1) git revert HEAD


----------------- Hacer que te pida usuario nuevamente --------------
git config --system --unset credential.helper    --- inicio de sesion en github al cambiar clave

git config --global credential.helper wincred    --- para que no te vuelva a pedir datos identificacion


----------- git fetch -------------
git fetch --all
Una función potente que recupera todos los repositorios remotos registrados y sus ramas:

git fetch --dry-run
La opción --dry-run ejecutará una demo del comando. Genera ejemplos de acciones que realizará durante la recuperación, pero no los aplica.


****** Archivos modificados en el área de trabajo  ************
1. Si cambiamos uno o varios archivos, pero no hemos hecho commit de dichos cambios podemos hacer:

git checkout -- ruta-archivo
y de esta manera, descarta todo cambio realizado en el archivo en el área de trabajo, es decir, que éste queda restablecido hasta HEAD (el último commit realizado).

2. Si cometimos el error de agregar al índice un archivo, haciendo git add ruta-archivo, realizando:

git reset ruta-archivo
Podemos devolverlo al área de trabajo sin borrar los cambios permanentemente, es decir, git reset ruta-archivo es lo contrario de git add ruta-archivo.  
Si quieres devolver todos los archivos del índice se puede usar simplemente git reset


*******  Cambiar el último commit ******
Si acabamos de hacer commit de unos cambios pero olvidamos incluir un archivo, podemos agregar dicho archivo (o todos los que se te hayan olvidado) al índice con:

git add ruta-archivo
y ahora usamos el comando git commit --amend, con el cual git toma los archivos que se encuentren en el índice para reescribir el commit, de esta manera:

git commit --amend -m "mensaje del commit"
Con ello, estaríamos modificando el anterior commit realizado para agregar el archivo faltante. Este comando también es útil cuando queremos modificar el mensaje del commit, con el cual podemos hacer:

git commit --amend -m "Nuevo mensaje del commit"
Así, los cambios realizados serán los mismos pero lo único que cambia es el mensaje del commit.


*********** Deshacer otros commits **************
Mientras estemos en una rama local, es decir, no se han subido los cambios a una remota, podemos deshacer un commit de las siguientes maneras:

git reset --hard HEAD~1
Este comando eliminará el commit y sus cambios se perderán por completo, es decir, has esto cuando ya no te importe los cambios que se hayan hecho en él.

En cambio, si quieres deshacer un commit, pero deseas mantener los cambios:

git reset --soft HEAD~1
Este comando eliminará el commit pero todos los cambios de él se pasarán al índice, es decir, justo antes de hacer commit y después de hacer git add.

Ahora, si lo que quieres es pasar todos los cambios hechos al área de trabajo:

git reset HEAD~1
HEAD~1 significa que retroceda en una posición con respecto al último commit. En caso de querer retroceder más, simplemente cambia el número por la cantidad de posiciones que se desea retroceder.


***************** Deshacer un commit público *****************
En caso de que queramos borrar un commit que ya hemos subido a una rama remota no podemos hacer git reset sino que debemos usar el siguiente comando:

git revert HEAD
Éste deshace un commit pero en vez de eliminarlo de la historia del repositorio, generará un nuevo commit que deshace todos los cambios introducidos en el commit 
que se desea eliminar. 
Esto para evitar conflictos con cualquier otra persona que trabaje en el repositorio. 
Pues de esta forma, los cambios deshechos se obtienen como cualquier otro commit haciendo git pull.

Otra ventaja que tiene git revert con respecto a git reset es que se puede deshacer un commit en particular sin tener que eliminar los commit que ocurrieron 
después del commit deseado, haciendo:

git revert <commit>
donde commit es el hash SHA-1 que lo identifica, el cual se puede obtener haciendo git log y buscando el commit a eliminar.

*******************************************************

HISTORICO DE CAMBIOS
git reflog

------------------------------

Deshacer el último commit (no publicado)
Si quieres mantener los cambios:
git reset --soft HEAD~1

Si NO quieres mantener los cambios:
git reset --hard HEAD~1

-------------------------------

Si quieres arreglar el último commit (y no has hecho push)

Sólo quieres arreglar el mensaje que has usado para el último commit:
git commit --amend -m "Este es el mensaje correcto"

Quieres añadir más cambios al último commit:
git add src/archivo-con-cambios.js
git commit --amend -m "Mensaje del commit"

El parámetro de --amend es muy útil pero sólo funciona con el último commit y siempre y cuando NO esté publicado. Si ya has hecho push de ese commit, esto no va a funcionar. Deberías hacer un git revert en su lugar.

----------------------------

Deshacer un commit (ya publicado)

git revert 74a1092

------------------------------------------

ELIMINAR UN COMMIT ESPECIFICO

git rebase -i {id del commit anterior al que queremos eliminar}

Hacer push a la rama
git push origin 2 --force

-------------------------------------

Eliminar el commit del historial

git reset --hard <commit>

Si lo que deseas es eliminar el commit, pero mantener los cambios que se introdujeron , entonces ejecuta :

git reset <commit>

--------------------------------

Eliminar un commit intermedio

Paso 1: Encontrar el commit justo anterior al commit que queremos borrar.
Paso 2: Hacemos un «checkout» de ese commit con el comando:
git checkout <commit hash>
Paso 3: Creamos una nueva rama utilizando nuestra posición actual:
git checkout -b <nueva branch>
Paso 4: Ahora tenemos que añadir el commit siguiente al commit que queremos borrar, para ello utilizamos el comando «cherry-pick»:
git cherry-pick <commit hash>
Paso 5: Repetimos el paso 4 para todos los commits que queremos mantener.
Paso 6: Volvemos a la branch original que queríamos arreglar:
git checkout <branch original>
Paso 7: Ahora hacemos un «hard reset» sobre la branch original al commit anterior al que queríamos borrar:
git reset --hard <commit hash>
Paso 8: Hacemos un merge con la branch que hemos creado para borrar los commits:
git merge <nueva branch>
Paso 9: Hacemos un push al repositorio.
git push --force origin <branch original>


-------------------------- MODIFICAR EL ULTIMO COMMIT -------------
git add *
git commit --amend                             ---- abre el editor
git commit --amend -m "nuevo mensaje"          ---- modifica mensaje
git commit --amend --no-edit                   ---- si no quieres modificar nada mas
git push

-----------------------------------------------------------


Si queremos evitar que git guarde automáticamente el usuario y contraseña de los repositorios que tengamos configurados en nuestro equipo
Le estamos diciendo a git que deshabilite el helper que evita introducir la contraseña cada vez que ejecutamos estas instrucciones.De esta manera, cada vez que hagamos pull o push de algún repositorio, se nos pedirá la contraseña.

git config --global --unset credential.helper

Este comando almacena en caché las credenciales en la memoria para que las utilicen futuros programas de Git

git config --global credential.helper cache

----------------------------------------------

Para ver servidores, ramas, asociaciones

git remote show origin

-------------------------------

Para ver las relaciones de ramas

git branch -vv

------------------------------ comandos para ver estados

git fetch -v        y git fetch -vv
git branch -vv      y git branch -v y git branch -a (ver todas las ramas)
git remote show origin
git pull -v

------------------------------


