# Apuntes de Git

## ⚙️ Comandos de configuración
- `git config --global user.name "Nombre Apellido"` -> Configura tu nombre de usuario para Git. El nombre que configures aquí se asociará con todos los commits que hagas desde tu repositorio local
- `git config --global user.email email@email.com` -> Configura tu dirección de correo electrónico para Git
- `git config core.autocrlf true` ->  Configura la conversión automática de los caracteres de retorno de carro (CR) y salto de línea (LF) al trabajar con archivos de texto en Git. Cuando "core.autocrlf" está configurado como true, Git automáticamente convertirá los finales de línea en los archivos de texto al formato adecuado para el sistema operativo en el que estás trabajando. Por ejemplo, si estás en un sistema operativo Windows, Git convertirá los saltos de línea LF (utilizados en sistemas Unix y Linux) a CR LF, que es el formato de fin de línea utilizado en Windows. Si estás en un sistema operativo Unix o Linux, Git convertirá los finales de línea CR LF a LF.
- `git config --global help.autocorrect 1` -> Habilita la corrección automática en Git para sugerir comandos correctos si el comando ingresado tiene una coincidencia cercana. El valor "1" habilita esta función. Por ejemplo, si introduces un comando incorrecto, Git intentará encontrar un comando similar y ejecutarlo automáticamente después de un breve período de tiempo si no se realizan otras acciones. Esto puede ayudar a reducir errores tipográficos al utilizar Git.

### Comandos más avanzados de configuración
- `git config credential.helper store`-> Almacenar de forma permanente las credenciales de autenticación para un servidor remoto en el disco duro local en texto plano. Cuando configuras Git con "credential.helper store", Git recordará tu nombre de usuario y contraseña para un servidor remoto y las guardará en un archivo de texto en tu sistema. Esto evita que Git solicite tus credenciales cada vez que realizas una operación que requiere autenticación, como un push o un pull. Esto guarda tus credenciales **sin encriptar** en tu disco, por eso es mejor utilizar el comando que aparece a continuación.
- `git config --global credential.helper cache` -> Guarda tus credenciales por defecto durante 15 minutos, y es la forma segura de trabajar con ellas
- `git config --global credential.helper 'cache --timeout=1800'` -> Almacena las contraseñas durante 1800 segundos, es decir, 30 minutos.

### Ver configuración
- `git config --global -e` -> Te muestra el archivo de configuración global
- `git config --list` -> Enseña todas las configuraciones de Git.
### Cambiar configuración
- `git config --global --replace-all user.name "Nombre Apellido"` -> Establece o actualiza el nombre de usuario global.
- `git config --global --replace-all user.email email@email.com` -> Establece o actualiza el correo electrónico global.

## 🏡 Al iniciar un repo desde local
- `git init` -> Empieza el control de versiones en este directorio, es como si inicializase el repositorio
- `git config --global init.defaultBranch main` -> Le decimos que cuando hagamos init, la rama que se cree por defecto que se llame main en vez de master

## 📈 Comandos básicos
- `git clone urlHTTPS` -> Clona un repositorio existente de GitHub en tu repositorio remoto
- `git help [comando]` -> Da información resumida sobre comandos de Git lo cual se utiliza como una guía de ayuda. Si pones "git help commit", se va a abrir una ventana en el navegador con un Manual Page con información sobre "git commit"
### git add
- `git add nombreArchivo` -> Agrega ese archivo al staging area de Git
- `git add .` -> Agrega todos los archivos modificados al área de preparación (staging area) de Git
- `git add *.extensiónArchivos` -> Añade al stage todos los archivos con una extensión en específico, por ejemplo "git add *.html"
- `git add nombreCarpeta/` -> Agrega al stage todos los archivos que están en esa carpeta
- `git add nombreCarpeta/*.extensiónArchivos` -> Añade al stage todos los archivos con una extensión en específico que estén en esa carpeta, por ejemplo "git add js/*.js" añade todos los archivos .js que estén en la carpeta "js"
### git reset (Se puede hacer lo mismo que con un add, es como su opuesto)
- `git reset nombreArchivo` -> Elimina del staging area ese archivo si no ha sido commiteado
- `git reset .` -> Borra todos los archivos modificados al área de preparación (staging area) de Git
- `git reset *.extensiónArchivos` -> Elimina al stage todos los archivos con una extensión en específico, por ejemplo "git reset *.html"
- `git reset nombreCarpeta/` -> Borra al stage todos los archivos que están en esa carpeta
- `git reset nombreCarpeta/*.extensiónArchivos` -> Elimina al stage todos los archivos con una extensión en específico que estén en esa carpeta, por ejemplo "git reset js/*.js" elimina todos los archivos .js que estén en la carpeta "js"
### git commit
- `git commit -m "Mensaje"` ->  Crea un nuevo commit con los cambios que se encuentran en el staging area. El mensaje (-m "Mensaje") es una descripción breve de los cambios que se incluyen en el commit
- `git commit -am "Mensaje"` -> Hace un git add y un git commit a la vez gracias al "-a" que es la abreviatura de git add (la "m" es la abreviatura del mensaje que también utilizábamos en el anterior comando)
- `git commit --amend -m "Nuevo Mensaje"` -> Cambia el mensaje del último commit que has hecho por el nuevo mensaje

### git push
- `git push` -> Sube los commits del repositorio local al repositorio remoto de GitHub
### git pull
- `git pull` -> Descarga los cambios del repositorio remoto de GitHub a tu repositorio local
  
## 📒 Para saber información
### git status
- ``git status`` -> Muestra el estado actual del repositorio de trabajo y el área de preparación. Proporciona información sobre qué archivos han sido modificados, agregados o eliminados desde el último commit, así como también los archivos que están en el área de preparación esperando ser confirmados en el próximo commit.

- `git status --short` -> Hace un resumen muy condensado de la información de cada archivo excepto de los que hayas commiteado pero no hayas modificado más.

## git log
- ``git log`` -> Muestra un historial de todos los commits en tu repositorio. Cada commit incluye un ID de commit único, el autor del commit, la fecha y hora del commit, y un mensaje de commit que describe los cambios realizados en ese commit (por eso es muy importante configurar el nombre y el mail)

- ``git log --graph`` -> Igual que el git log de siempre pero con una información visual a mayores de las ramas 

- ``git log --graph --pretty=oneline`` -> Igual que el anterior pero todo resumido en una línea

- ``git log --decorate --all --oneline`` -> Igual que el anterior pero con el hash mucho más simple en vez del largo

## git diff
- `git diff` -> Muestra las diferencias entre dos estados diferentes en el respositorio Git. Estos estados pueden ser entre el directorio de trabajo y el stage, entre el stage y el commit más reciente, o entre dos commits diferentes. Cuando ejecutas "git diff" sin ningún argumento adicional, muestra las diferencias entre el directorio de trabajo y el staging area, es decir, las modificaciones que aún no se han añadido al tatage. Esto te permite revisar los cambios que has realizado antes de confirmarlos con un commit. (Es más visual la herramienta de visualización de vscode)

- `git diff --staged` -> Enseña las diferencias entre el staging area y el último commit. Esto significa que te muestra los cambios que han sido añadidos al stage, pero aún no se han confirmado con un commit. Es lo mismo que hacer `git diff --cached` 

- `git diff HEAD`-> Muestra las diferencias entre el directorio de trabajo y el commit más reciente.
- `git diff hashCommit` -> Enseña las diferencias entre el directorio de trabajo y el commit especificado.
- `git diff hashCommitInicial hashCommitFinal` -> Muestra las diferencias entre dos commits específicos.
- `git diff ramaInicial ramaFinal` -> Enseña las diferencias entre dos ramas específicas.

## 📝 Para hacer modificaciones

### git checkout
- ``git checkout archivo/commit/rama`` -> Es para volver a un punto específico. Afecta a archivos, commits y ramas. En archivos, quita cambios que no están commiteados (cuando un archivo esta "M"); en commits, puedes moverte a otros commits y ver los archivos, pero hay que tener cuidado con "The Detached HEAD State"; y en ramas, puedes moverte a diferentes ramas.

- `git checkout -- .` -> Recupera el estado de los archivos como estaban en el último commit. Si tienes algún archivo modificado que tiene un error pero cuando hiciste commit estaba bien, puedes volver a la versión del archivo que estaba bien con este comando. Esto no afecta a los archivos que hemos creado, son nuevos y nunca han sido stageados (son los que tienen una U de "untracked"), pero sí a cualquier otro archivo (incluso restaura los que borraste).

### git reset
- ``git reset []`` -> Permite RESTABLECER tu estado actual a un estado específico. Puedes restablecer el estado de archivos específicos, así como el de toda una rama. Esto es útil si aún no has subido tu commit a GitHub o a otro repositorio remoto. El git reset también se podía usar como la antítesis de "git add" como vimos anteriormente.

- `git reset --soft HEAD^Numero/hashCommit` -> Borra un commit pero guarda los cambios (gracias al --soft). Aquí se puede usar "HEAD^Numero" o el propio hash del commit que queramos eliminar. Si queremos eliminar el último commit sería "git reset --soft HEAD^1". Esto se usa por ejemplo si en el commit x se te olvidó poner otros archivos y quieres incluirlos. Tu lo que haces es borrar ese commit y crear uno nuevo con los archivos del commit anterior (con sus modificaciones guardadas) y los que quisieras añadir. **Esto se puede hacer antes de hacer un push, si se ha hecho, evita hacerlo**

- `git reset --hard HEAD^Numero/hashCommit` -> Elimina permanentemente el commit con todos los cambios, es decir, que los archivos modificados que se guardasen en ese commit, volverían a estar como estaban en el último commit antes de ese. Por ejemplo si tengo tres commits y hago el reset hard del segundo commit, los archivos que estuvieran modificados y guardados en el segundo commit, volverían a su estado inicial guardado en el primer commit, pero no se guardarían las modificaciones que se hicieron entre el primer y el segundo commit (porque estaban guardadas en el segundo commit que ha sido borrado). **Esto se puede hacer antes de hacer un push, si se ha hecho, evita hacerlo**


## 🕵 Para alias
``git config --global alias.nombreAlias "comando"`` -> Esto te crea un alias que luego puedes utilizar haciendo "git nombreAlias" y hace el mismo comando que estás poniendo ahí.

> [!NOTE]
> Para más información sobre los alias, por favor mira el archivo Alias.md 

## 🌳 Ramas
##### ⭐ Comandos para crear una rama y saber en cual estás
- `git branch` -> Muestra todas las ramas locales de tu repositorio de GitHub y la rama en la que te encuentras actualmente se marca con un asterisco y un color diferente
- `git branch nombreRama` -> Crea una nueva rama con el nombre especificado
- `git checkout nombreRama` -> Cambia tu rama actual por la rama que has especificado
- `git branch -m nombreAntiguoRama nombreNuevoRama` -> Cambiamos el nombre a la rama en la que estamos por el nombreNuevoRama. Esto se suele hacer mucho para cambiar el nombre de rama master a main.
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


## Otros archivos
- `.gitignore` -> Se utiliza para especificar archivos y directorios que Git debe ignorar al rastrear los cambios en un repositorio. Puedes usar patrones de coincidencia de nombres de archivo para definir qué archivos y carpetas deben ser ignorados por Git. Por ejemplo, puedes incluir patrones para ignorar archivos de compilación, archivos temporales o archivos específicos generados por el sistema. Esto ayuda a mantener el repositorio limpio y evitar que archivos innecesarios sean incluidos en el control de versiones.

- `.gitkeep` -> A diferencia de .gitignore, este archivo no es un archivo oficial de Git. Algunos proyectos pueden utilizarlo para mantener vacíos los directorios vacíos en Git. Git no rastrea los directorios vacíos, por lo que si necesitas que un directorio vacío sea parte de tu repositorio, puedes agregar un archivo .gitkeep dentro de él. Este archivo generalmente está vacío; su nombre sugiere su propósito, que es mantener el directorio dentro del control de versiones.