---
title: Introducion a Github
published: true
---

## Lista de requerimientos.

* Cuenta en Github.com (obligatorio)
* [Git](https://www.git-scm.com) 
* Una llave publica para autenticar en Github
* Terminal (Linux, Windows o Mac) para ejecutar git


### Crea un repositorio nuevo en tu cuenta de [Github](https://github.com)

![Screenshot](https://i.imgur.com/LvzsrrK.jpg)

### La salida de Github es la siguiente.

![Salida](https://i.imgur.com/ZOAFQXl.png)


1.- Generar una llave para autentificar y subirla a github.

 ```
  $ ssh-keygen -t ed25519 -C "your_email@example.com"

 ```

2.- Iniciar el ssh-agent para administrar las llaves.
 ```
   $ eval "$(ssh-agent -s)"
   > Agent pid 59566
  ```
 _En fish shell la linea de arriba no trabaja correctamente, en su lugar ejecutamos._

   ```
   $ eval (ssh-agent -c)
   ```

3.- Agregar la llave creada para Github al agente ssh-agent

 ```
  $ ssh-add ~/.ssh/id_ed25519
 ```

4.- Es posible editar un archivo en _~/.ssh/config_ y agregar los datos de tu llave y host.

 ```
  Host github.com
    Hostname ssh.github.com
    Port 443
    User git
    IdentityFile /home/ficovh/.ssh/id_ed25519_github
 ```

### Notas sobre la instalacion.

1. Clonar el repositorio.
2. Eliminar el archivo .git del directorio raiz.
3. Crear un repositorio en tu cuenta de Github (Ej. myblog)
4. Inicializar git en el directorio local
5. Hacer commits y subir los archivos a github.

```shell
  $ git clone  https://github.com/tocttou/hacker-blog ~/myblog
  $ cd ~/myblog
  $ rm -rfd .git
```
### Inicializar Git localmente

```
   $ git init
   $ git add *
   $ git remote add origin git@github.com:ficovh/myblog.git
```

### Subir el blog

 ```
    $ git commit -a -m "initial import"
    $ git push -u origin main
```

### Links de interes.
 *  [Autenticando con SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
 * [Agregando una llave ssh a Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)


