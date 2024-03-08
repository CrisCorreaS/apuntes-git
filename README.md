# Apuntes de Git

## ⚙️ Comandos de configuración
- `git config --global user.name "Nombre Apellido"` -> Configura tu nombre de usuario para Git. El nombre que configures aquí se asociará con todos los commits que hagas desde tu repositorio local
- `git config --global user.email email@email.com` -> Configura tu dirección de correo electrónico para Git
- `git config --global -e` -> Te muestra el archivo de configuración global

## 🏡 Al iniciar un repo desde local
- `git init` -> Empieza el control de versiones en este fichero
- `git config --global init.defaultBranch main` -> Le decimos que cuando hagamos init, la rama que se cree por defecto que se llame main en vez de master

## 📈 Comandos básicos
- `git clone urlHTTPS` -> Clona un repositorio existente de GitHub en tu repositorio remoto
- `git add nombreArchivo` -> Agrega ese archivo al stagin area de Git
- `git add .` -> Agrega todos los archivos modificados al área de preparación (staging area) de Git
- `git commit -m "Mensaje"` ->  Crea un nuevo commit con los cambios que se encuentran en el staging area. El mensaje (-m "Mensaje") es una descripción breve de los cambios que se incluyen en el commit
- `git push` -> Sube los commits del repositorio local al repositorio remoto de GitHub
- `git pull` -> Descarga los cambios del repositorio remoto de GitHub a tu repositorio local
  
## 📒 Para saber información
- ``git status`` -> Muestra el estado actual del repositorio de trabajo y el área de preparación. Proporciona información sobre qué archivos han sido modificados, agregados o eliminados desde el último commit, así como también los archivos que están en el área de preparación esperando ser confirmados en el próximo commit.
- ``git log`` -> Muestra un historial de todos los commits en tu repositorio. Cada commit incluye un ID de commit único, el autor del commit, la fecha y hora del commit, y un mensaje de commit que describe los cambios realizados en ese commit (por eso es muy importante configurar el nombre y el mail)

### 💅 Variantes interesantes del git log:
- ``git log --graph`` -> Igual que el git log de siempre pero con una información visual a mayores de las ramas 

- ``git log --graph --pretty=oneline`` -> Igual que el anterior pero todo resumido en una línea

- ``git log --decorate --all --oneline`` -> Igual que el anterior pero con el hash mucho más simple en vez del largo

## 📝 Para hacer modificaciones
- ``git checkout archivo/commit/rama`` -> Es para volver a un punto específico. Afecta a archivos, commits y ramas. En archivos, quita cambios que no están commiteados (cuando un archivo esta "M"); en commits, puedes moverte a otros commits y ver los archivos, pero hay que tener cuidado con "The Detached HEAD State"; y en ramas, puedes moverte a diferentes ramas.

- ``git reset []`` -> Permite RESTABLECER tu estado actual a un estado específico. Puedes restablecer el estado de archivos específicos, así como el de toda una rama. Esto es útil si aún no has subido tu commit a GitHub o a otro repositorio remoto.

## 🕵 Para alias
``git config --global alias.nombreAlias "comando"`` -> Esto te crea un alias que luego puedes utilizar haciendo "git nombreAlias" y hace el mismo comando que estás poniendo ahí

## 🌳 Ramas
##### ⭐ Comandos para crear una rama y saber en cual estás
- `git branch` -> Muestra todas las ramas locales de tu repositorio de GitHub y la rama en la que te encuentras actualmente se marca con un asterisco y un color diferente
- `git branch nombreRama` -> Crea una nueva rama con el nombre especificado
- `git checkout nombreRama` -> Cambia tu rama actual por la rama que has especificado
- `git branch -m nombreNuevoRama` -> Cambiamos el nombre a la rama en la que estamos por el nombreNuevoRama. Esto se suele hacer mucho para cambiar el nombre de rama master a main.
##### 💻 Comandos para llegar a tu rama de GitHub desde tu ordenador 
- `git clone urlHTTPS` -> Clona un repositorio existente de GitHub en tu repositorio remoto
- `git branch` -> Muestra todas las ramas locales de tu repositorio de GitHub y la rama en la que te encuentras actualmente se marca con un asterisco y un color diferente. Si solo aparece la rama "main" tienes que hacer los siguientes comandos
  - `git fetch` -> Recupera los cambios remotos (como ramas y commits) desde el repositorio de GitHub pero no los fusiona con tu rama actual. Es útil para obtener información actualizada sobre las ramas remotas sin modificar tu trabajo actual.
  - `git config --local --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/*` -> Configura la recuperación remota de ramas específicas. En este caso, está configurando Git para recuperar todas las ramas desde el repositorio remoto (origin) y almacenarlas localmente en la carpeta refs/remotes/origin/.
  - `git fetch origin` -> Recupera cambios específicos desde el repositorio remoto llamado "origin". Esto trae los cambios de las ramas del repositorio remoto a tus referencias remotas locales
  - `git config --get remote.origin.fetch` -> Muestra la configuración de recuperación remota para el remoto llamado "origin". En este caso, está configurado para recuperar todas las ramas.
  - `git fetch --all` -> Recupera cambios desde todos los remotos configurados en tu repositorio
  - `git branch -a` -> Muestra todas las ramas, tanto locales como remotas. Si te aparecen las ramas así:
    `CatiaCrisMarta>git branch -a` <br>
    `* main`<br>
    ` remotes/origin/HEAD -> origin/main` <br>
    ` remotes/origin/catia` <br>
    ` remotes/origin/cris` <br>
    ` remotes/origin/main` <br>
    ` remotes/origin/marta` <br>
- `git checkout nombreRama` -> Cambia a la rama llamada "nombreRama"
- `git branch` -> Muestra todas las ramas locales de tu repositorio de GitHub y la rama en la que te encuentras actualmente se marca con un asterisco y un color diferente.

#### 👉 Comandos para gestionar las ramas
> [!IMPORTANT]
> Antes de empezar con las ramas, por favor mira este apartado porque es importante para saber bien cómo hacer con las ramas

**Para crear una estructura como esta:**

![](https://buddy.works/blog/images/gitflow.png)

**Ramas**:
- 💜 main/master
- ❤️ dev
- 🩵 feature1
- 🧡 feature2

1️⃣ Cuando creamos un repositorio ya creamos por defecto la rama **main**, por lo que tenemos que crear la rama **dev** a partir de la rama main:
<br>
``git checkout -b dev main`` -> Con esto creamos la rama dev a partir de la rama main y nos situamos en la rama dev
<br><br>
2️⃣ Una vez creada la rama **dev**, desarrollamos cualquier cosa y hacemos un commit _(el primer circulito de la rama dev)_ tenemos que crear a partir de esta, la rama **feature1** (la azul):
<br>
``git checkout -b feature1 dev`` -> Con esto creamos la rama feature1 a partir de la rama dev y nos situamos en la rama feature1
<br><br>
3️⃣ Ahora, en la rama **feature1**, desarrollamos código y hacemos commits _(todos los círculos que tiene la rama feature1 azul)_
<br><br>
4️⃣ Por otro lado, nos vamos a pasar a **dev** para corregir un bug ``git checkout dev`` y una vez corregido, hacemos un commit _(el segundo círculito de la rama dev)_ . Ahora que está corregido el bug, creamos la rama **feature2**:
<br>
``git checkout -b feature2 dev`` -> Con esto creamos la rama feature2 a partir de la rama dev, y nos situamos en feature2
<br><br>
5️⃣ En la rama **feature2**, desarrollamos código y hacemos un commit para guardarlo _(el único circulito de la rama feature2 naranja)_. Nos pasamos a la rama **dev** con el comando ``git checkout dev`` y en la rama **dev** cambiamos el README.md y hacemos un commit _(el tercer circulito de la rama dev)_ 
<br><br>
6️⃣ Ahora, vamos a hacer un merge de la rama **feature2** en la rama **dev**. Para esto tenemos que estar en la rama **dev** y escribir el siguiente comando:
<br>
``git merge feature2`` -> Con este comando estamos volcando todos cambios guardados en los commits de la rama feature2, en la rama dev. Si hemos cambiado cosas en la rama dev que no afectan a los cambios de la rama feature2, no va a haber nignún problema. Si al contrario, hemos cambiado el README.md tanto en el tercer commit de la rama dev, como en el primero de la rama feature2, habrá un merge conflict.
<br><br>
7️⃣ Vamos a interpretar que no hubo ningún merge conflict y que se ha hecho el merge correctamente. Al hacer un merge, siempre se hace un commit automáticamente _(este sería el cuarto circulito de la rama dev)_
<br><br>
8️⃣ Por último, vamos a borrar la rama **feature2** porque ya no vamos a hacer ninguna funcionalidad que tenga que ver con lo que hicimos en **feature2**, así que nos vamos a cualquier rama que no sea **feature2** _(lo normal es seguir en dev)_ y hacemos:
<br>
``git branch -d feature2``
<br><br>

> [!NOTE]
> Los comandos más importantes que usaremos de ramas serán:
> - ``git checkout -b ramaNueva ramaDesdeLaQueCreamosLaRamaNueva``
> - ``git merge ramaQueQueremosFusionarConLaRamaEnLaQueEstamos``
> - ``git branch -d ramaQueBorramos``
