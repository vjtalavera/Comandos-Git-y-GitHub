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
