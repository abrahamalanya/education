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
## Utilizando Pull Requests en GitHub
## Creando un Fork, contribuyendo a un repositorio
## Haciendo deployent a un servidor a un servidor
## Hazme un pull request
## Ignorar archivos en el repositorio con .gitignore
## Readme.md es una excelente pr&aacute;ctica
## Tu sitio web p&uacute;blico con GitHub Pages

# Multiples entornos de trabajo en Git
# Comandos de Git para casos de emergencia
# Bonus sobre Git y Github