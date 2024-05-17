# Cómo Configurar Claves SSH en Git y GitHub desde Windows
## Creación de la clave y configuración del sistema y GitHub
1. Crear una **clave SSH** usando el algoritmo ed25519 asociado al mail que estemos utilizando en GitHub. Eso lo hacemos abriendo una terminal y escribiendo `ssh-keygen -t ed25519 -C "Tu mail"`
      - Al escribir esto nos va a poner lo siguiente:
        ```
        Generating public/private ed25519 key pair.
        Enter file in which to save the key (C:\Users\Usuario/.ssh/id_ed25519):
        Created directory 'C:\\Users\\Usuario/.ssh'.
        Enter passphrase (empty for no passphrase):
        Enter same passphrase again:
        Your identification has been saved in C:\Users\Usuario/.ssh/id_ed25519
        Your public key has been saved in C:\Users\Usuario/.ssh/id_ed25519.pub
        The key fingerprint is: ...
        The key's randomart image is: ...
        ```
      - Nos avisa de que se ha creado un par de claves públicas/privadas
      - Nos pregunta donde vamos a guardar las claves, a lo que en mi caso le doy a `ENTER` para que me las guarde en la carpeta por defecto
      - Nos avisa que se ha creado la carpeta para guardar el par de claves
      - Ponemos una passphrase (una contraseña de toda la vida) para hacer el proceso más seguro y la repetimos
      - Nos avisa en la carpeta en la que se han guardado las claves y también nos avisa de cómo se han guardado (nos da el formato de la clave pública que es en `.pub`. La clave pública tendrá un nombre parecido a `id_nombreAlgoritmo.pub` y la privada igual pero sin extensión: `id_nombreAlgoritmo`). Es muy importante saber que la **clave privada es secreta** y debe de mantenerse segura
      - Por último nos da datos sobre la **clave pública**.
2. Comprobar y configurar el servicio **SSH Agent** en nuestro sistema. Para hacer esto ejecutamos, desde PowerShell como administradores, el comando ` Get-Service -Name ssh-agent | Set-Service -StartupType Manual` lo cual idealmente no nos devuelve nada.
3. Iniciar el servicio SSH Agent con el comando `Start-Service ssh-agent`. Idealmente no nos devuelve ningún mensaje.
4. Añadir la **clave privada** al SSH Agent de nuestro equipo. Esto lo hacemos con el comando `ssh-add c:/Users/Usuario/.ssh/id_ed25519`. Aquí si pusimos una contraseña en nuestra clave SSH, vamos a tener que escribirla. Lo ideal es que nos devuelva `Identity added: c:/Users/Usuario/.ssh/id_ed25519 (Tu mail)`
5. Ir a nuestro perfil de GitHub y `Hacer click en el Perfil > Settings > SSH and GPG keys > SSH keys > Pulsar el botón "New SSH key"`. Ahí deberemos de cubrir tres campos: **"Título", "Key Type"** y **"Key"**
6. Cubrir los datos anteriormente mencionados poniendo de "título" lo que sea, en "key type" **authentication key**, y en "key" copiamos el contenido de la clave pública y lo pegamos.
      - Para copiar el contenido de la **clave pública** tenemos que utilizar el siguiente comando `cat ~/.ssh/id_ed25519.pub | clip`
7. Darle al botón **Add SSH key**, poner nuestra contraseña de GitHub y ver que en el apartado de "SSH keys" aparece nuestra clave con el título y más información.

## Configuraciones de Git en nuestro equipo para asociar nuestra cuenta de GitHub
1. Ver nuestra configuración de Git. Nos situamos en el directorio home y escribimos el siguiente comando `git config --list` para que nos liste todas las configuraciones que tenemos en Git.
2. Comprobar que tanto el **user.username** como el **user.email** sean los que tenemos GitHub. Si no es así podemos cambiarlo haciendo un `git config --global -e` y poniendo lo siguiente:
      ```
      [user]
        name = LoQueQuieras
        username = ElNombreDeGitHub
        email = ElMailDeGitHub
      ```
3. Una vez que esté todo listo, para comprobar que funcione el SSH, vamos a un repositorio cualquiera, cogemos el código de clonado de SSH y hacemos un `git clone codigoClonadoSSH`. Lo ideal es que aparezca algo muy parecido a lo siguiente:
      ```
      Cloning into 'nombreRepositorio'...
      The authenticity of host 'github.com (ip)' can't be established.
      ED25519 key fingerprint is ...
      This key is not known by any other names.
      Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
      Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
      Enter passphrase for key '/c/Users/Usuario/.ssh/id_ed25519':
      ```
      - Cuando aparece `Are you sure you want to continue connecting (yes/no/[fingerprint])?` le decimos `yes`
      - Y luego nos preguntará por nuestra contraseña. Si ponemos todo bien, empezará el clonado del repositorio.

> [!NOTE]
> Links de Interés:
> - ["Generación de una nueva clave SSH y adición al agente SSH" - GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
> - ["Agregar una clave SSH nueva a tu cuenta de GitHub" - GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
> - [Generate a New SSH Key and Add it to your GitHub -  Geek Forever](https://www.youtube.com/watch?v=X40b9x9BFGo)
> - [Cómo Configurar Claves SSH para Git y GitHub -  Carlos Azaustre](https://www.youtube.com/watch?v=akuG7eRtaXc)