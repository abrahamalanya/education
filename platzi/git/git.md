# GIT - GITHUB
[Comandos Git - populares](./comandosGit.md)

# Introducci&oacute;n a Git
# Comando b&aacute;sicos en Git
# Flujo de trabajo b&aacute;sico en Git

# Trabajando con repositorios remotos en GitHub
## Tags y versiones en Git y Github
Muestra toda las historias desde que inicio el proyecto u repositorio
```
git log --all --graph --decorate --oneline
```

Para poder colocar alias a c&oacute;digo anterior
```
alias robot="git log --all --graph --decorate --oneline"
```

**Tag**
- Creando un tag
    - el `-a` significa que vamos agregar un tag, es como un *add*
    - el `v0.1`  es el nombre del tag, generalmente se usa para versiones
    - el `-m` significa que vagregaremos un mensaje
    - el `hash` es el codigo de nuestro commit (**96f523h**)
```
git tag -a v0.1 -m "mensaje_descriptivo_del_tag" <hash>
```

- Listar todos los tags
```
git tag
```

- Visualar que tag pertenece a que hash o commit
```
git show-ref --tags
```

- Enviar los tags al repositorio
```
git push origin --tags
```

- Eliminar un tag en el local
```
git tag -d <nombre_tag>
```

- Eliminar tag de nuestro repositorio web (github)
```
git push origin :refs/tags/<nombre_tag>
```
## Manejo de ramas en github


# Flujos de trabajo profesionales
# Multiples entornos de trabajo en Git
# Comandos de Git para casos de emergencia
# Bonus sobre Git y Github