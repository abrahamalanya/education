# Comandos m&aacute;s populares para abrahamalanya
- inicializa git en el ***index*** 
```
git init
```

- agregar cambios al stage
```
git add <nombre_archivo>
```

- 
```
git commit -m "mensaje descriptivo de la historia"
```

- listar todas las historias, `git log`
    - el `--all` lista todo
    - el `--graph` muestra graficamente las historias
    - el `--decorate` se encarga del formato visual
    - el `--oneline` muestra en una sola l&iacute;nea todas las historias
```
git log --all --graph --decorate --oneline
```

- Explicacion detallada
    - Si hemos creado nuestro proyecto en local y estuvimos trabajando sin ningun repositorio remoto
    - Luego ya existe ese repositorio con cambios o archivos existentes
    - Cuando queremos conectarnos a ese repositorio usamos estos comandos
    - `git remote add origin <url_repositorio>`
    - luego tenemos que hacer un `git pull origin main` y `git push origin main`
    - Pero no se podra, por tener este caso especial de los proyectos en local y remoto con cambios, asi que usamos este comando
```
git pull origin master --allow-unrelated-histories
```
    - De esa manera podremos descargar todos los cambios y hacer el merge inmeditamente
    - Si no deseas usar este comando, entonces primero usas un `git fetch` y luego un `git merge`

