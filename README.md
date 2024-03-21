# Apuntes de Git

![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img1.png)

> [!NOTE]
> Las letras mayúsculas que aparecen en git al lado de los archivos significan lo siguiente:
> - **U**: Untracked. Indica que el archivo es nuevo y no ha sido rastreado por Git.
> - **A**: Added. Indica que el archivo ha sido añadido al staging area pero aún no ha sido commiteado.
> - **M**: Modified. Indica que el archivo ha sido modificado desde el último commit.
> - **C**: Copied. Indica que el archivo ha sido copiado dentro del mismo repositorio.
> - **R**: Renamed. Indica que el archivo ha sido renombrado.
> - **D**: Deleted. Indica que el archivo ha sido eliminado del directorio de trabajo pero aún no ha sido committeado el cambio.
> - **T**: Type-change. Indica que el tipo de archivo ha cambiado, por ejemplo, de un archivo regular a un enlace simbólico o viceversa.
> - **X** o **!**: Unmerged. Indica que el archivo tiene conflictos de fusión que aún no han sido resueltos.


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
- `git config --global user.ParametroQueremosSaber` -> Enseña el parámetro por defecto que has almacenado en la configuración global. Ej; "git config --global user.email" te devuelve el email que has guardado
- 
### Cambiar configuración
- `git config --global --replace-all user.name "Nombre Apellido"` -> Establece o actualiza el nombre de usuario global.
- `git config --global --replace-all user.email email@email.com` -> Establece o actualiza el correo electrónico global.

## 🏡 Al iniciar un repo desde local
- `git init` -> Empieza el control de versiones en este directorio, es como si inicializase el repositorio
- `git config --global init.defaultBranch main` -> Le decimos que cuando hagamos init, la rama que se cree por defecto que se llame main en vez de master

## 📈 Comandos básicos
- `git clone urlHTTPS` -> Clona un repositorio existente de GitHub en tu repositorio remoto
- `git help [comando]` -> Da información resumida sobre comandos de Git lo cual se utiliza como una guía de ayuda. Si pones "git help commit", se va a abrir una ventana en el navegador con un Manual Page con información sobre "git commit"
- `git rm nombreArchivo` -> Elimina el archivo del respositorio de Git y también del sistema de archivos local. Este comando es útil cuando deseas eliminar un archivo que ya no necesitas y quieres que este cambio se refleje en el repositorio. Al ejecutar "git rm", el archivo se elimina del directorio de trabajo y del stage, pero no se elimina del historial de commits. Para que este cambio se registre en el historial, es necesario hacer un commit después de ejecutar "git rm"
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
- `git commit -am "Mensaje"` -> Hace un git add y un git commit a la vez gracias al "-a" que es la abreviatura de "git add" (la "m" es la abreviatura del mensaje que también utilizábamos en el anterior comando)
- `git commit --amend` -> Abre en la terminal información sobre el último commit y se puede cambiar el mensaje de este. Pero es mucho más sencillo hacerlo de la siguiente manera:
- `git commit --amend -m "Nuevo Mensaje"` -> Cambia el mensaje del último commit que has hecho por el nuevo mensaje

> [!NOTE]
> Para saber más sobre los commits, qué es un hash, qué significa HEAD y demás, puedes consultar el archivo [Commit.md](https://github.com/CrisCorreaS/apuntes-git/blob/main/Commit.md)

### git push
- `git push` -> Sube los commits del repositorio local al repositorio remoto de GitHub
### git pull
- `git pull` -> Descarga los cambios del repositorio remoto de GitHub a tu repositorio local
  
## 📚 Para saber información
### git status
- ``git status`` -> Muestra el estado actual del repositorio de trabajo y el área de preparación. Proporciona información sobre qué archivos han sido modificados, agregados o eliminados desde el último commit, así como también los archivos que están en el área de preparación esperando ser confirmados en el próximo commit.
- `git status --short` -> Hace un resumen muy condensado de la información de cada archivo excepto de los que hayas commiteado pero no hayas modificado más.

### git log
- ``git log`` -> Muestra un historial de todos los commits en tu repositorio. Cada commit incluye un ID de commit único, el autor del commit, la fecha y hora del commit, y un mensaje de commit que describe los cambios realizados en ese commit (por eso es muy importante configurar el nombre y el mail)
- `git log nombreArchivo` -> Para ver solo los commits que incluyen cambios en ese archivo. Esto es útil para rastrear la historia de un archivo en particular a lo largo del tiempo 
- `git log --stat` -> Es una versión más descriptiva del "git log" que nos da información detallada sobre los archivos que fueron modificadas y cuántas líneas se añadieron o eliminaron en cada commit.
- `git log -p` -> Es lo mismo que hacer "git log --patch". Esta es una versión mucho más descriptiva que la anterior. Aquí no solo muestra los archivos que fueron modificados y el número de líneas totales, sino que también muestra los cambios exactos: Nos dice que en "index.html" añadimos una lista desordenada mostrándola en verde, y que quitamos el encabezado de nivel uno que ahora aparece en rojo
- `git log --since [numeroAño/]numeroMes/numeroDía` -> Nos da todo el histórico de commits desde el día que hayamos puesto. Ej: "git log --since 3/6" nos da el histórico desde el 6 de Marzo de este año y "git log --since 2024/10/1" nos da el histórico desde el 1 de Octubre de 2024
- ``git log --graph`` -> Igual que el "git log" de siempre pero con una información visual a mayores de las ramas 
- ``git log --graph --pretty=oneline`` -> Igual que el anterior pero todo resumido en una línea
- ``git log --decorate --all --oneline`` -> Igual que el anterior pero con el hash mucho más simple en vez del largo

### git diff
- `git diff` -> Muestra las diferencias entre dos estados diferentes en el respositorio Git. Estos estados pueden ser entre el directorio de trabajo y el stage, entre el stage y el commit más reciente, o entre dos commits diferentes. Cuando ejecutas "git diff" sin ningún argumento adicional, muestra las diferencias entre el directorio de trabajo y el staging area, es decir, las modificaciones que aún no se han añadido al tatage. Esto te permite revisar los cambios que has realizado antes de confirmarlos con un commit. (Es más visual la herramienta de visualización de vscode)
- `git diff --staged` -> Enseña las diferencias entre el staging area y el último commit. Esto significa que te muestra los cambios que han sido añadidos al stage, pero aún no se han confirmado con un commit. Es lo mismo que hacer `git diff --cached` 
- `git diff HEAD`-> Muestra las diferencias entre el directorio de trabajo y el commit más reciente.
- `git diff hashCommit` -> Enseña las diferencias entre el directorio de trabajo y el commit especificado.
- `git diff hashCommitInicial hashCommitFinal` -> Muestra las diferencias entre dos commits específicos.
- `git diff ramaInicial ramaFinal` -> Enseña las diferencias entre dos ramas específicas.

### git reflog
- `git reflog` -> Muestra un registro de referencia del historial de cambios realizados en HEAD (puntero a la rama actual) y otras referencias de Git, como ramas y etiquetas. La palabra "reflog" es una abreviatura de "registro de referencia de log". Este registro puede ser útil para recuperar cambios perdidos o deshacer acciones no deseadas, como restablecer ramas a estados anteriores o recuperar commits eliminados accidentalmente con "git reset --hard".

### git show
- `git show hashCommit` -> Muestra información detallada sobre un commit específico identificado por su hash. Proporciona detalles específicos del commit seleccionado, incluyendo el autor, la fecha, el mensaje del commit y los cambios introducidos por ese commit. No solo muestra las diferencias como hace "git diff", sino también la información del commit en sí (autor, fecha y mensaje). Es útil para inspeccionar un commit específico en detalle y comprender qué cambios se introdujeron en él.
- `git show nombreTag` ->  Nos enseña información sobre la tag. Para info más detallada ir a "tags"

## 📝 Para hacer modificaciones
### git checkout
- ``git checkout archivo/commit`` -> Es para volver a un punto específico. Afecta a archivos, commits y ramas. En archivos, quita cambios que no están commiteados (cuando un archivo esta "M"); en commits, puedes moverte a otros commits y ver los archivos, pero hay que tener cuidado con "The Detached HEAD State"; y en ramas, puedes moverte a diferentes ramas. Utilizar "git checkout" con ramas está desaconsejado desde la versión 2.23 de Git, por lo que ahora para esa funcionalidad utilizamos "git switch"
- `git checkout -- .` -> Recupera el estado de los archivos como estaban en el último commit. Si tienes algún archivo modificado que tiene un error pero cuando hiciste commit estaba bien, puedes volver a la versión del archivo que estaba bien con este comando. Esto no afecta a los archivos que hemos creado, son nuevos y nunca han sido stageados (son los que tienen una U de "untracked"), pero sí a cualquier otro archivo (incluso restaura los que borraste).

### git reset
- ``git reset []`` -> Permite RESTABLECER tu estado actual a un estado específico. Puedes restablecer el estado de archivos específicos, así como el de toda una rama. Esto es útil si aún no has subido tu commit a GitHub o a otro repositorio remoto. El git reset también se podía usar como la antítesis de "git add" como vimos anteriormente.
- `git reset --soft HEAD^Numero/hashCommit` -> Borra un commit pero guarda los cambios en el stage (gracias al --soft). Es decir, git moverá la rama actual hacia el commit especificado, pero mantendrá los cambios realizados en el staging area. Esto significa que los cambios se retiran del commit, pero permanecen listos para ser confirmados nuevamente con un nuevo commit. Aquí se puede usar "HEAD^Numero" o el propio hash del commit que queramos eliminar. Si queremos eliminar el último commit sería "git reset --soft HEAD^1". Esto se usa por ejemplo si en el commit x se te olvidó poner otros archivos y quieres incluirlos. Tu lo que haces es borrar ese commit y crear uno nuevo con los archivos del commit anterior (con sus modificaciones guardadas) y los que quisieras añadir. **Esto se puede hacer antes de hacer un push, si se ha hecho, evita hacerlo**
- `git reset --mixed HEAD^Numero/hashCommit` -> Borra un commit, no guarda los cambios en el stage pero sí que los guarda en el área de trabajo local (gracias al --mixed). Este es el comportamiento predeterminado de "git reset" si no se especifica ningún argumento. Con "--mixed", Git moverá la rama actual hacia el commit especificado y deshará los cambios en el staging area, pero mantendrá los cambios en el directorio de trabajo. Esto significa que los cambios deshechos no se perderán, pero tendrás que agregarlos nuevamente al stage si deseas confirmarlos nuevamente. **Esto se puede hacer antes de hacer un push, si se ha hecho, evita hacerlo**
- `git reset --hard HEAD^Numero/hashCommit` -> Elimina el commit con todos los cambios, es decir, que los archivos modificados que se guardasen en ese commit, volverían a estar como estaban en el último commit antes de ese. Es una acción "destructiva", por lo que se debe tener cuidado al usarlo, ya que los cambios deshechos no se pueden recuperar fácilmente. Se recomienda utilizarlo con precaución y asegurarse de que realmente deseas eliminar los cambios. Por ejemplo si tengo tres commits y hago el reset hard del segundo commit, los archivos que estuvieran modificados y guardados en el segundo commit, volverían a su estado inicial guardado en el primer commit, pero no se guardarían las modificaciones que se hicieron entre el primer y el segundo commit (porque estaban guardadas en el segundo commit que ha sido borrado). Si borramos algo que no deberíamos, podemos hacer un "git reflog" ver a qué punto queremos volver, buscar el hash que nos interesa restaurar y hacer un "git reset --hard" con ese hash. **Esto se puede hacer antes de hacer un push, si se ha hecho, evita hacerlo**
- `git reset --hard` -> Resetea el stage y el directorio de trabajo al último commit actual. Esto significa que todos los cambios no commiteados en el directorio de trabajo y en el stage serán descartados, y el estado del repositorio volverá al último commit. Este comando es muy poderoso y debe usarse con precaución, ya que los cambios no commiteados se perderán permanentemente. Es bastante parecido a "git checkout -- .", salvo que el "git checkout -- ." sí que guarda los cambios que se subieron al stage.

### git mv
- `git mv nombreAntiguo nombreNuevo` -> Renombra o mueve archivos o directorios de Git. En lugar de usar el comando "mv" del sistema de archivos, que Git puede interpretar como eliminar el archivo antiguo y agregar uno nuevo, "git mv" realiza la acción de manera más inteligente, lo que ayuda a mantener el historial de versiones del archivo. Cuando cambiamos el archivo de nombre con "git mv", nos aparece una "R" de Rename. Ejemplos de esto serían: "git mv app/index.html app/indexcambiado.html" para cambiar un archivo de una carpeta o "git mv css styles" para cambiar el nombre de una carpeta


## 🕵 Para alias
- ``git config --global alias.nombreAlias "comando"`` -> Esto te crea un alias que luego puedes utilizar haciendo "git nombreAlias" y hace el mismo comando que estás poniendo ahí. Cuando decimos "comando", nos referimos a todo lo que vaya después de "git", ya que si en el comando ponemos "git ..." nos va a dar el error "expansion of alias 'nombreAlias' failed; 'git' is not a git command", por lo que **NO ponemos "git" dentro del comando"

> [!NOTE]
> Para más información sobre los alias, por favor mira el archivo [Alias.md](https://github.com/CrisCorreaS/apuntes-git/blob/main/Alias.md)

## 🏷 Para tags
### git tag
- `git tag` -> Vemos todas las tags que tenemos.
- `git tag nombreTag` -> Creamos una tag ligera, que es una referencia a un commit específico, y con esta, podemos descargar el proyecto justo como se encontraba en ese instante. Si no especificamos el hash del commit, lo va a crear en el último commit en el que estemos y debemos tener en cuenta que esta etiqueta no contiene metadatos adicionales como el nombre del autor, la fecha de creación o un mensaje asociado. En general las etiquetas se suelen utilizar para marcar versiones o releases de nuestro código. Ej: creamos un tag que marque la versión 1.0.0 del código con el comando "git tag v1.0.0".
- `git tag nombreTag hashCommit` -> Creamos una tag ligera en un commit específico, no en el commit actual. Ej: "git tag v0.0.3 c9032ec"
- `git tag -a nombreTag` -> Creamos una tag anotada, ya que "-a" significa annotated. Una etiqueta anotada es un objeto Git completo en sí mismo. Almacena un hash completo del commit al que apunta, así como metadatos adicionales como el nombre del autor, la fecha de creación y un mensaje asociado. Son útiles para marcar hitos importantes en la historia del proyecto y para proporcionar información adicional sobre esos hitos. Al escribir este comando nos va a mandar poner un mensaje, como si hacemos "git commit" y no incluimos el mensaje, por eso es mejor hacer el siguiente comando:
- `git tag -a nombreTag -m "Mensaje"` -> Creamos una tag anotada con el mensaje. Es lo mismo que el anterior comando pero añadiendo un mensaje como metadato. Ej: "git tag -a v1.0.0 -m 'Versión 1.0.0 lista'"
- `git tag -a nombreTag hashCommit -m "Mensaje"` -> Creamos una tag anotada que hace referencia a un commit en concreto que no es en el que estamos. Si no ponemos el hash, la tag se crearía en el commit en el que estemos como habíamos estado haciendo hasta ahora. Ejemplo de una tag anotada en un commit en concreto: "git tag -a v0.1.0 0d34c9e -m 'La versión 0.1.0 está lista'"
- `git tag -d nombreTag` -> Eliminamos el tag con ese nombre.

### git show
- `git show nombreTag` -> Nos enseña información sobre la tag. Si hacemos que nos enseñe info de una tag ligera, solo nos enseñará información sobre el commit al que apunta. Si hacemos lo mismo pero con una tag anotada, nos aparecerá la misma información del commit al que apunta y a mayores, información sobre la propia tag (autor, fecha y mensaje). Ej: "git show v0.1.0" 

Ejemplo de tag ligera:
```
commit cccfd17f3dbb554ff4f997591c8e735ff2a96fec (tag: v0.0.3)
Author: Cristina Correa <cristina.correa.segade@gmail.com>
Date:   Tue Mar 19 03:52:53 2024 +0100

    Añadimos estructura html desde la rama prueba
...
```

Ejemplo de tag anotada:
```
tag v0.1.0
Tagger: Cristina Correa <cristina.correa.segade@gmail.com>
Date:   Tue Mar 19 05:54:52 2024 +0100

La versión 0.1.0 está lista

commit 0d34c9e7bc556c3d2a6a3f3a30562be235c9f2d8 (tag: v0.1.0)
Merge: c0fe687 8499e9e
Author: Cristina Correa <cristina.correa.segade@gmail.com>
Date:   Tue Mar 19 04:24:15 2024 +0100

    Merge branch 'prueba2' merge unión automática
```



> [!NOTE]
> Al crear un tag se puede poner un nombre o una versión semántica. Si usamos una versión semántica tenemos que tener en cuenta que:
> - El primer dígito significa que hubo cambios importantes en nuestra aplicación o que es una versión mayor. Ej: v1.0.0, v2.0.0 ...
> - El segundo dígito significa que hemos añadido alguna funcionalidad a la aplicación (una feature) pero no es considerada una versión mayor. Ej: v1.1.0, v1.2.0 ...
> - El tercer dígito significa que hemos arreglado un bug (bug fix) del código. Ej: v1.0.1, v1.0.2 ...
> - También se le pueden poner a mayores un "alpha" más un número Ej: v1.2.1-alpha.2, v1.2.1-alpha.3 ... 
> En definitiva la estructura sería la siguiente: **[major].[minor/feature].[patch]-[build/beta/rc/alpha]**
> Para saber más puedes consultar [este enlace](https://semver.org/) o [este de la documentación oficial](https://git-scm.com/book/en/v2/Git-Basics-Tagging)

## 🌳 Ramas
### Comandos básicos de ramas
- `git branch` -> Muestra todas las ramas locales de tu repositorio de GitHub y la rama en la que te encuentras actualmente se marca con un asterisco y un color diferente
- `git branch nombreRama` -> Crea una nueva rama con el nombre especificado
- `git switch nombreRama` -> Cambia tu rama actual por la rama que has especificado. Antes de la versión de Git 2.23 se usaba "git checkout nombreRama" para hacer esto, pero ahora es recomendable hacerlo con "git switch"
- `git switch -c nombreRama` -> Crea una nueva rama y te mueve directamente a la rama que has creado ya que "-c" significa create. Este es el equivalente al hacer un "git branch x" para crear la rama y luego un "git switch x" para moverte a la rama, pero simplificadamente. Anteriormente se hacía "git checkout -b nombreRama" para hacer lo mismo, pero desde la versión 2.23 de Git, esto ha cambiado.
- `git switch -c ramaNueva -t ramaOrigen` -> Crea una nueva rama basada en otra existente. Tenemos que usar la opción -c de "create" junto con la opción -t de "track" para especificar la rama de origen. La opción -t establece la nueva rama para rastrear la rama especificada, lo que significa que cuando cambiamos a la nueva rama, Git intentará rebasear automáticamente los cambios de la rama de origen. 
- `git branch -m nombreAntiguoRama nombreNuevoRama` -> Cambiamos el nombre a la rama en la que estamos por el nombreNuevoRama. Esto se suele hacer mucho para cambiar el nombre de rama master a main.
- `git branch -d nombreRamaBorrar` -> Borra la rama que queramos ya que el "-d" significa delete. Si hay algún cambio en la rama que no esté mergeado, nos lo va a decir y nos va a preguntar si estamos seguros. Lo ideal es tener cuidado con la rama en la que estemos, pero no va a haber ningún problema si estamos en la rama "feature1" y hacemos un "git branch -d feature1" ya que nos moverá automáticamente a otra rama, por ejemplo a "dev" o a "main".
- `git branch -d nombreRamaBorrar -f` -> Fuerza la eliminación de la rama ya que el "-f" significa force. En este caso, si hay algún cambio en la rama que no esté mergeado, lo va a borrar sin preguntar si estamos seguros. Es mejor utilizar el comando anterior y no este.

### 3️⃣ tipos de merges que existen con las ramas
![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img2.png)
![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img3.png)
![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img4.png)

- `git merge ramaConCambios` -> Une los cambios de la "ramaConCambios" a la rama en donde nos encontramos. Siempre que se vaya a unir una rama a otra, debemos de estar en la rama que va a recibir los cambios. Si queremos actualizar la rama "dev" con una nueva funcionalidad de la rama "feature1", tenemos que colocarnos en "dev" para recibir esos cambios y luego hacer un "git merge feature1". Normalmente (e idealmente), siempre se hará un Fast-forward lo cual significa que no hay ningún conflicto.

> [!NOTE]
> Si hacemos un merge de **unión automática** (merge made by the "recursive" strategy), nos va a aparecer una "ventana" en la terminal donde nos dice que tenemos que añadir un mensaje de commit ya que se va a hacer un commit que informe la unión de ambas ramas. Para escribir tenemos que pulsar la `A`, cuando acabemos de poner el mensaje de commit tenemos que pulsar en `ESC` y luego poner `:wq!` y darle a `ENTER`

> [!NOTE]
> Si hacemos un merge que nos ha dado un conflicto, tenemos que arreglarlo. Por ejemplo: Tenemos dos ramas: la rama "dev" y la rama "feature1" y vamos a crear un conflicto: 
> - 1º En la rama feature1 hicimos un commit en un archivo de css "style.css": 
> ```
> h1 {
>   font-size: large;
> }
> ```
> - 2º En la rama "dev" también hicimos un commit en el mismo archivo css "style.css" poniendo lo siguiente:
> ```
> p {
>   font-family: Arial, Helvetica, sans-serif;
> }
> ```
> - 3º Estamos en la rama "dev" y hacemos un `git merge feature1` y nos da un conflicto con el archivo "style.css" que se ve así:
> ```
> <<<<<<< HEAD
> p {
>     font-family: Arial, Helvetica, sans-serif;
> =======
> h1 {
>     font-size: large;
> >>>>>>> feature1
> }
> ```
> - 4º Queremos ambos cambios y lo queremos hacer manualmente, así que tenemos que quitar las líneas que vscode ha puesto para indicar el conflicto y dejar el archivo como queremos que esté (tenemos que quitar "<<<<<<< HEAD", "=======" y ">>>>>>> feature1" y modificar el archivo para que quede como nos gustaría) por lo que dejamos el archivo así:
> ```
> p {
>     font-family: Arial, Helvetica, sans-serif;
> }
> h1 {
>     font-size: large;
> }
> ```
> - 5º Ahora que tenemos el archivo como nos gustaría, tenemos que hacer un add y un commit para guardar los cambios y conseguir que se haga el merge de las dos ramas satisfactoriamente ya que resolvimos el conflicto. Si hacemos un `git status` en este momento nos va a poner "You have unmerged paths", por lo que hacemos `git commit -am "unión con feature1"`. Si ahora hacemos `git log`, podremos ver que todo está bien y ya se ha unido correctamente

### 💻 Comandos para llegar a tu rama de GitHub desde tu ordenador 
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
- `git switch nombreRama` -> Cambia a la rama llamada "nombreRama"
- `git branch` -> Muestra todas las ramas locales de tu repositorio de GitHub y la rama en la que te encuentras actualmente se marca con un asterisco y un color diferente.


### 👉 Comandos para gestionar las ramas
> [!IMPORTANT]
> Antes de empezar con las ramas, por favor mira este apartado porque es importante para saber bien cómo hacer con las ramas

**Para crear una estructura como esta:**

![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img5.png)

**Ramas**:
- ❤️ main/master
- 🩵 dev
- 💛 feature1
- 💜 feature2

1️⃣ Cuando creamos un repositorio ya creamos por defecto la rama **main**, por lo que tenemos que crear la rama **dev** a partir de la rama main:
<br>
``git switch -c dev -t main`` -> Con esto creamos la rama dev a partir de la rama main y nos situamos en la rama dev
<br><br>
2️⃣ Una vez creada la rama **dev**, desarrollamos cualquier cosa y hacemos un commit _(el primer circulito de la rama dev)_ tenemos que crear a partir de esta, la rama **feature1** (la azul):
<br>
``git switch -c feature1 -t dev`` -> Con esto creamos la rama feature1 a partir de la rama dev y nos situamos en la rama feature1
<br><br>
3️⃣ Ahora, en la rama **feature1**, desarrollamos código y hacemos commits _(todos los círculos que tiene la rama feature1 azul)_
<br><br>
4️⃣ Por otro lado, nos vamos a pasar a **dev** para corregir un bug ``git switch dev`` y una vez corregido, hacemos un commit _(el segundo círculito de la rama dev)_ . Ahora que está corregido el bug, creamos la rama **feature2**:
<br>
``git switch -c feature2 -t dev`` -> Con esto creamos la rama feature2 a partir de la rama dev, y nos situamos en feature2
<br><br>
5️⃣ En la rama **feature2**, desarrollamos código y hacemos un commit para guardarlo _(el único circulito de la rama feature2 naranja)_. Nos pasamos a la rama **dev** con el comando ``git switch dev`` y en la rama **dev** cambiamos el README.md y hacemos un commit _(el tercer circulito de la rama dev)_ 
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
> - ``git switch -b ramaNueva -t ramaDesdeLaQueCreamosLaRamaNueva``
> - ``git merge ramaQueQueremosFusionarConLaRamaEnLaQueEstamos``
> - ``git branch -d ramaQueBorramos``



## 🗃 Otros archivos

### .gitignore
- `.gitignore` -> Se utiliza para especificar archivos y directorios que Git debe ignorar al rastrear los cambios en un repositorio. Puedes usar patrones de coincidencia de nombres de archivo para definir qué archivos y carpetas deben ser ignorados por Git. Por ejemplo, puedes incluir patrones para ignorar archivos de compilación, archivos temporales o archivos específicos generados por el sistema. Esto ayuda a mantener el repositorio limpio y evitar que archivos innecesarios sean incluidos en el control de versiones. Se suele poner en la raíz del proyecto, donde también debería de ir la carpeta ".git" que indica que se ha inicializado el repositorio. 

> [!NOTE]
> Para más información sobre .gitignore, mira el archivo [GitIgnore.md](https://github.com/CrisCorreaS/apuntes-git/blob/main/GitIgnore.md)

### .gitkeep
- `.gitkeep` -> A diferencia de .gitignore, este archivo no es un archivo oficial de Git. Algunos proyectos pueden utilizarlo para mantener vacíos los directorios vacíos en Git. Git no rastrea los directorios vacíos, por lo que si necesitas que un directorio vacío sea parte de tu repositorio, puedes agregar un archivo .gitkeep dentro de él. Este archivo generalmente está vacío; su nombre sugiere su propósito, que es mantener el directorio dentro del control de versiones.
