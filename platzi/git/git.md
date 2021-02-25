# GIT - GITHUB
[Comandos Git - populares](./comandosGit.md)

# Introducci&oacute;n a Git
# Comando b&aacute;sicos en Git
# Flujo de trabajo b&aacute;sico en Git

# Trabajando con repositorios remotos en GitHub
## Tags y versiones en Git y Github
Muestra toda las historias desde que inicio el proyecto u repositorio
```git
git log --all --graph --decorate --oneline
```

Para poder colocar alias a c&oacute;digo anterior
```git
alias robot="git log --all --graph --decorate --oneline"
```

**Tag**
- Creando un tag
    - el `-a` significa que vamos agregar un tag, es como un *add*
    - el `v0.1`  es el nombre del tag, generalmente se usa para versiones
    - el `-m` significa que vagregaremos un mensaje
    - el `hash` es el codigo de nuestro commit (**96f523h**)
```git
git tag -a v0.1 -m "mensaje_descriptivo_del_tag" <hash>
```

- Listar todos los tags
```git
git tag
```

- Visualar que tag pertenece a que hash o commit
```git
git show-ref --tags
```

- Enviar los tags al repositorio
```git
git push origin --tags
```

- Eliminar un tag en el local
```git
git tag -d <nombre_tag>
```

- Eliminar tag de nuestro repositorio web (github)
```git
git push origin :refs/tags/<nombre_tag>
```
## Manejo de ramas en github
La rama principal es `main`
- Visualizar todas las ramas(`branch`)
```git
git show-branch --all
```

- Git muestra las historias de manera visual - funciona en `win10`
```git
gitk
```

- Muestra ramas `branch` en el index
```git
git branch
```

- Subir nuestra rama `branch` a Github, primero debemos estar en la rama que deseamos subir
```git
git push origin <nombre_branch>
```

- Podemos crear nuevas ramas `branch` y subirlo al instante desde `master` o `main`
```git
git branch <nueva_rama>
git branch <nueva_rama2>
git push origin <nueva_rama>
git push origin <nueva_rama2>
```

## Configurar m&uacute;ltiples colaboradores en un repositorio de GitHub
- Clonar un repositorio
```git
git clone <url_repositorio>
```

Para poder tener colaboradores en nuestro repositorio, debemos agregarlo como colaborador desde github, en los `setings` del repositorio.

# Flujos de trabajo profesionales
## Flujo de trabajo profesional: Haciendo merge de ramas de desarrollo a master
**desarrollador**
- Para traerse las ramas del repositorio remoto, automaticamente se realiza un merge.
```git
git pull origin <nombre_rama>
git checkout <nombre_rama>
```
**master o main**
- fusionar las ramas de los desarrolladores en el master, esto son los pasos
```git
git checkout <nombre_rama>
git pull origin <nombre_rama>
git checkout master
git merge <nombre_rama>
git pull origin master
git push origin master
```

## Flujo de trabajo profesional con Pull requests
Generalmente no se debe realizar `push` al master en los equipos de desarrollo, antes de eso se debe realizar un `code review` por eso existe el `pull request`

En nuestra rama tenemos el `master` o `main` como el branch principal que se conecta al servidor principal y tenemos otra que el `staging develop` que es sirve como una previa antes de suber todo al `master o main`.

`Pull Request` es una caracteristicas de GitHub
Las personas que realizan todo este desarrollo se les conoce como los **DevOps**

## Utilizando Pull Requests en GitHub
Para los Pull Request es como un commit intermedio

## Creando un Fork, contribuyendo a un repositorio
Podemos aportar a un proyecto publico, realizando un fork al repositorio.

- Los cambios se suben
```git
git push
```
- Si el proyecto original tiene cambios, podemos traer esos cambios a nuestro local
```git
git remote add upstream <url_repo_original>
git pull upstream master
git commit -am "Fusion"
git push origin master
```

## Haciendo deployent a un servidor a un servidor
Se sube en el servidor, todo nuestro proyecto para visualizar todo el proyecto.
A todo ese se le conoce como el trabajo de los **DevOps**

## Hazme un pull request
Pasos para hacer el PR a Freddy

- realizamos un fork
- Clonamos el proyecto
```git
git clone <url_repositorio>
```
-Realizamos los cambios
```git
git commit -am "Colocando el nombre"
git push
```
- En GitHub solicitamos el PR y esperamos a que hagan el merge.

## Ignorar archivos en el repositorio con .gitignore
Se crea un archivo `.gitignore`

## Readme.md es una excelente pr&aacute;ctica
Es la presentacion de nuestro repositorio, es lo que se muestra primero al entrar a un repositorio, esta escrito en markdown `.md`

## Tu sitio web p&uacute;blico con GitHub Pages
En settings buscamos una opcion GitHub Pages, y seleccionamos la rama que deseamos mostrar en la p&aacute;gina y listo.

# Multiples entornos de trabajo en Git
## Git Rebase: Reorganizando el trabajo realizado
Se recomienda utilizar en repositorios locales, son cambios silencioso.
- Primero se realiza `rebase` en la rama a la que cambia
- Segundo se realiza `rebase` a la rama final

```git
git branch experimento
git checkout experimento
git commit -am "mensaje de cmabios modificados"
git rebase master

git checkout master
git rebase experimento

git push origin master
```

***Nota:*** Si hay cambios en master y luego realizamos el commit y cambiamos a la rama `experimento`, podemos realizar el `git rebase master` y en las historias se muesta como se el ultimo cambio de master fuera el checkout inicial. Luego de terminar tus cambios en `experimento`, regresar a `master` y realizas el `git rebase experimento` y en las historias no existio los commit de la rama `experimento`.

## Git Stash: Guardar cambios en memoria y recuperarlos
Es una forma util para tener en temporal nuestros cambios y moverlo entre ramas
```git
#creamos un stash
git stash

#listar los stash
git stash list

#abrimos el stash que guardamos
git stash pop

#llevar nuestro stash a una rama
git stash branch <name_branch>

#Borrar un stash
git stash drop
```
## Git Clean: Limpiar tu proyecto de archivos no deseados
`git clean` solo borra las cosas que puede indexar

`git clean` detecta archivos nuevos, no es necesario que se trate de una copia de archivo, suficiente con que sea un archivo nuevo que creamos lo detectara
```git
#Muestra una previa de lo que va eliminar
git clean --dry-run

#Elimina todo lo que mostro, excepto copias carpetas con mismos archivos, eso lo realizamos de manera manual
git clean -f

#Tampoco elimina archivos que estan en .gitignore
```
## Git Cherry-pick: Traer commits viejos al head de un branch
```git
git cherry-pick <hash_commit_or_historie>
```

# Comandos de Git para casos de emergencia
## Reconstruir commits en Git con amend
Reconstruye el ultimo commit que realizamos 
```git
git commit --amend
git commit --amend -m "mensaje nuevo"
git commit --amend --no-edit #se utiliza el utlimo commit de la historia

#ver las estadisticas de los cambios
git --stat
```

## Git Reset y Reflog: &uacute;sese en caso de emergencia
```git
#Muestra todos los cambios del repositorio
git reflog
```

```git
git reset --hard <hash de historia>
```

## Buscar en archivos y commits de Git con Grep y Log
- Aqui buscamos palabras en todo nuestro repositorio
```git
#muestra donde usamos tal palabra
git grep <texto>

#muestra donde usamos cierta palabra  y que linea esta
git grep -n <texto>

#cuenta la cantidad de veces que utilizamos una palabra
git grep -c <texto>

#para utilizar que etiqueta utilizamos usamos comillas "<p>"
git grep "<etiqueta_html>"
```

- Aqui buscamos palabras en todo nuestra historia de commits
```git
git log -S "<texto a buscar>"
```

# Bonus sobre Git y Github
## Comandos y recursos colaborativos en Git y GitHub
```git
git shortlog -sn #cantidad commits del equipo
git shortlog -sn --all #todos los commit del equipo
git shortlog -sn --all --no-merge #todos los commits sin incluir los merge

#colocar un alias en la configuracion de git
git config --global alias.stats "git shortlog -sn --all --no-merge"
git stats

#Visualizamos que cambios hizo quien de cierto archivo
git blame <name_archivo>
git blame -c <name_archivo> #muestra de manera mas ordena, identada el codigo
git blame css/estilos.css -L35,53 #muestra que cambios se realizo de tal linea hasta cierta linea

#Ramas
git branch #muestra ramas locales
git branch -r #muestra ramas remotas
git branch -a #muestra ramas locales y remotas

#Visualizar un manual de cada comando
git <comand> --help
```

## Tu futuro con Git y Github
- Travis
- Jenkins = https://platzi.com/cursos/jenkins-basico/
- Azure DevOps
- Git Lab = https://platzi.com/cursos/gitlab/
- Curso de DevOps = https://platzi.com/cursos/devops/