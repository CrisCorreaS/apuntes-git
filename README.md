# Apuntes de Git y GitHub
![Badge en Desarollo](https://img.shields.io/badge/STATUS-EN%20DESAROLLO-green)
<img align="right" alt="License MIT" src="https://img.shields.io/badge/LICENSE-MIT-green" /> <br/>
![Git](https://img.shields.io/badge/-Git-F05032?style=flat-square&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github&logoColor=white)

## Áreas de Git
![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img1.png)

> [!NOTE]
> Las letras mayúsculas que aparecen en git al lado de los archivos significan lo siguiente:
> - **U**: Untracked. Indica que el archivo es nuevo y no ha sido rastreado por Git.
> - **A**: Added. Indica que el archivo ha sido añadido al staging area pero aún no ha sido commiteado.
> - **M**: Modified. Indica que el archivo ha sido modificado desde el último commit.
> - **C**: Copied. Indica que el archivo ha sido copiado dentro del mismo repositorio.
> - **R**: Renamed. Indica que el archivo ha sido renombrado.
> - **D**: Deleted. Indica que el archivo ha sido eliminado del directorio de trabajo pero aún no ha sido commiteado el cambio.
> - **T**: Type-change. Indica que el tipo de archivo ha cambiado, por ejemplo, de un archivo regular a un enlace simbólico o viceversa.
> - **X** o **!**: Unmerged. Indica que el archivo tiene conflictos de fusión que aún no han sido resueltos.


## ⚙️ Comandos de configuración
### ⚠️ Obligatorios para cualquier persona
- `git config --global user.name "Nombre Apellido"` → Configura tu nombre de usuario para Git. El nombre que configures aquí se asociará con todos los commits que hagas desde tu repositorio local
- `git config --global user.email email@email.com` → Configura tu dirección de correo electrónico para Git
### Optativos
- `git config core.autocrlf true` → Configura la conversión automática de los caracteres de retorno de carro (CR) y salto de línea (LF) al trabajar con archivos de texto en Git. Cuando "core.autocrlf" está configurado como true, Git automáticamente convertirá los finales de línea en los archivos de texto al formato adecuado para el sistema operativo en el que estás trabajando. Por ejemplo, si estás en un sistema operativo Windows, Git convertirá los saltos de línea LF (utilizados en sistemas Unix y Linux) a CR LF, que es el formato de fin de línea utilizado en Windows. Si estás en un sistema operativo Unix o Linux, Git convertirá los finales de línea CR LF a LF.
- `git config --global help.autocorrect 1` → Habilita la corrección automática en Git para sugerir comandos correctos si el comando ingresado tiene una coincidencia cercana. El valor "1" habilita esta función. Por ejemplo, si introduces un comando incorrecto, Git intentará encontrar un comando similar y ejecutarlo automáticamente después de un breve período de tiempo si no se realizan otras acciones. Esto puede ayudar a reducir errores tipográficos al utilizar Git.

### Comandos más avanzados de configuración
- `git config credential.helper store`→ Almacenar de forma permanente las credenciales de autenticación para un servidor remoto en el disco duro local en texto plano. Cuando configuras Git con "credential.helper store", Git recordará tu nombre de usuario y contraseña para un servidor remoto y las guardará en un archivo de texto en tu sistema. Esto evita que Git solicite tus credenciales cada vez que realizas una operación que requiere autenticación, como un push o un pull. Esto guarda tus credenciales **sin encriptar** en tu disco, por eso es mejor utilizar el comando que aparece a continuación.
- `git config --global credential.helper cache` → Guarda tus credenciales por defecto durante 15 minutos, y es la forma segura de trabajar con ellas
- `git config --global credential.helper 'cache --timeout=1800'` → Almacena las contraseñas durante 1800 segundos, es decir, 30 minutos.

### Ver configuración
- `git config --global -e` → Te muestra el archivo de configuración global
- `git config --list` → Enseña todas las configuraciones de Git.
- `git config --global user.ParametroQueremosSaber` → Enseña el parámetro por defecto que has almacenado en la configuración global. Ej; "git config --global user.email" te devuelve el email que has guardado
- 
### Cambiar configuración
- `git config --global --replace-all user.name "Nombre Apellido"` → Establece o actualiza el nombre de usuario global.
- `git config --global --replace-all user.email email@email.com` → Establece o actualiza el correo electrónico global.

## 🏡 Al iniciar un repo desde local
- `git init` → Empieza el control de versiones en este directorio, es como si inicializase el repositorio
- `git config --global init.defaultBranch main` → Le decimos que cuando hagamos init, la rama que se cree por defecto que se llame main en vez de master

## 📈 Comandos básicos
- `git clone urlHTTPS` → Clona un repositorio existente de GitHub en tu repositorio remoto
- `git clone urlHTTPS .` → Clona un repositorio Git desde la URL especificada y lo coloca en el directorio actual (representado por el punto "."). Al especificar el punto "." al final, le decimos a Git que clone el repositorio en la carpeta actual en lugar de crear una nueva con el nombre del repositorio. Hay que tener cuidado con esto porque la carpeta donde ejecutemos este comando tiene que estar vacía o si no nos dará este tipo de error: **fatal: destination path '.' already exists and is not an empty directory.**
- `git help [comando]` → Da información resumida sobre comandos de Git lo cual se utiliza como una guía de ayuda. Si pones "git help commit", se va a abrir una ventana en el navegador con un Manual Page con información sobre "git commit"
### git add
- `git add nombreArchivo` → Agrega ese archivo al staging area de Git
- `git add .` → Agrega todos los archivos modificados al área de preparación (staging area) de Git
- `git add *.extensiónArchivos` → Añade al stage todos los archivos con una extensión en específico, por ejemplo "git add *.html"
- `git add nombreCarpeta/` → Agrega al stage todos los archivos que están en esa carpeta
- `git add nombreCarpeta/*.extensiónArchivos` → Añade al stage todos los archivos con una extensión en específico que estén en esa carpeta, por ejemplo "git add js/*.js" añade todos los archivos .js que estén en la carpeta "js"
- `git add -A` → Añade los archivos modificados en el directorio de trabajo al staging area. E igual que `git add .` pero incluye también los archivos que se han eliminado del directorio de trabajo. Es una manera abreviada de escribir `git add --all`. Ten cuidado porque `git add -a` no existe, es con "A" mayúscula. (Es más fácil usar `git add .`)
- `git add -u` → Solo añade al stage archivos modificados y eliminados, pero no los nuevos archivos no rastreados (untracked). Es lo mismo que usar `git add update`. (Es más fácil usar `git add .`)

### git reset (Se puede hacer lo mismo que con un add, es como su opuesto)
- `git reset nombreArchivo` → Elimina del staging area ese archivo si no ha sido commiteado
- `git reset .` → Borra todos los archivos modificados al área de preparación (staging area) de Git
- `git reset *.extensiónArchivos` → Elimina al stage todos los archivos con una extensión en específico, por ejemplo "git reset *.html"
- `git reset nombreCarpeta/` → Borra al stage todos los archivos que están en esa carpeta
- `git reset nombreCarpeta/*.extensiónArchivos` → Elimina al stage todos los archivos con una extensión en específico que estén en esa carpeta, por ejemplo "git reset js/*.js" elimina todos los archivos .js que estén en la carpeta "js"
### git commit
- `git commit -m "Mensaje"` →  Crea un nuevo commit con los cambios que se encuentran en el staging area. El mensaje (-m "Mensaje") es una descripción breve de los cambios que se incluyen en el commit
- `git commit -am "Mensaje"` → Hace un git add y un git commit a la vez gracias al "-a" que es la abreviatura de "--all". Al poner el "-a" hacemos lo mismo que un `git add .`. La "m" es la abreviatura del mensaje que también utilizábamos en el anterior comando.
- `git commit --amend` → Abre en la terminal información sobre el último commit y se puede cambiar el mensaje de este. Pero es mucho más sencillo hacerlo de la siguiente manera:
- `git commit --amend -m "Nuevo Mensaje"` → Cambia el mensaje del último commit que has hecho por el nuevo mensaje
- `git commit --amend --no-edit` → Es un comando perfecto para arreglar errores en los commits. Si en un commit nos falta añadir algún archivo importante, podemos hacer un `git add nombreArchivo` para poner el archivo en el stage, y luego utilizar el comando `git commit --amend --no-edit` para modificar el último commit y añadir ese archivo. "--no-edit" indica que no se debe abrir el editor de texto para modificar el mensaje del commit existente. En otras palabras, mantiene el mensaje de commit tal como está y solo modifica el contenido del commit.

> [!NOTE]
> Para saber más sobre los commits, qué es un hash, qué significa HEAD y demás, puedes consultar el archivo [Commit.md](https://github.com/CrisCorreaS/apuntes-git/blob/main/Commit.md)

### git push
- `git push` → Sube los commits del repositorio local al repositorio remoto de GitHub
### git pull
- `git pull` → Descarga los cambios del repositorio remoto de GitHub a tu repositorio local
  
## 📚 Para saber información
### git status
- ``git status`` → Muestra el estado actual del repositorio de trabajo y el área de preparación. Proporciona información sobre qué archivos han sido modificados, agregados o eliminados desde el último commit, así como también los archivos que están en el área de preparación esperando ser confirmados en el próximo commit.
- `git status -b` → Es lo mismo que el anterior comando pero dándonos dos líneas de información sobre la rama en la que estamos y si esta está up to date o no. Es igual a poner `git status --branch`
- `git status -s` → Hace un resumen muy condensado de la información de cada archivo excepto de los que hayas commiteado pero no hayas modificado más. Es igual a poner `git status --short`.
> [!NOTE]
> El comando `git status -s` muestra un resumen compacto del estado del repositorio, utilizando códigos de dos letras para representar los cambios en los archivos.
> - A → indica que el archivo es nuevo y ha sido añadido al stage.
> - M → indica que el archivo ha sido modificado en el directorio de trabajo y también ha sido añadido al stage.
> - ?? → indica que el archivo es un archivo no rastreado por Git. Es Untracked.
- `git status -sb` → Hace lo mismo pero añadiendo información sobre las ramas. Me gusta bastante este comando y creo que es muy útil cuando estás utilizando también las configuraciones de colores de status.

### git log
- ``git log`` → Muestra un historial de todos los commits en tu repositorio. Cada commit incluye un ID de commit único, el autor del commit, la fecha y hora del commit, y un mensaje de commit que describe los cambios realizados en ese commit (por eso es muy importante configurar el nombre y el mail)
```
commit cccfd17f3dbb554ff4f997591c8e735ff2a96fec 
Author: Cristina Correa <cristina.correa.segade@gmail.com>
Date:   Fri May 24 14:28:22 2024 +0200

    json modificado
```
- `git log nombreArchivo` → Para ver solo los commits que incluyen cambios en ese archivo. Esto es útil para rastrear la historia de un archivo en particular a lo largo del tiempo 
- `git log --name-only` → Nos devuelve el log un poco más descriptivo poniendo los nombres de los archivos del commit.
```
commit cccfd17f3dbb554ff4f997591c8e735ff2a96fec 
Author: Cristina Correa <cristina.correa.segade@gmail.com>
Date:   Fri May 24 14:28:22 2024 +0200

    json modificado

other/info.json
other/other.json
other/otro.json
other/prueba.json
```
- `git log --name-status` → Es una alternativa que nos da información sobre los nombres de los archivos como `git --stat` pero en vez de darnos información sobre las líneas modificadas, simplemente nos da información sobre los cambios realizados en los archivos. El "--name-status" se puede combinar con otras opciones de `git log` para hacer un log más informativo
```
commit cccfd17f3dbb554ff4f997591c8e735ff2a96fec 
Author: Cristina Correa <cristina.correa.segade@gmail.com>
Date:   Fri May 24 14:28:22 2024 +0200

    json modificado

A       other/info.json
R100    other/temp.json other/other.json
D       other/otro.json
M       other/prueba.json
```
> [!NOTE]
> Los códigos de estado en la salida del comando `git log --name-status` indican qué tipo de cambio se ha realizado en cada archivo. Aquí tienes lo que significan cada uno de esos códigos:
> - **A** = Added (Añadido). Indica que el archivo ha sido añadido en el commit. Es un nuevo archivo que no existía antes.
> - **D** = Deleted (Eliminado). Indica que el archivo ha sido eliminado en el commit.
> - **M** = Modified (Modificado). Indica que el archivo ha sido modificado. Se refiere a un archivo existente que ha sido editado.
> - **R100** = **R**: Renamed (Renombrado). Indica que el archivo ha sido renombrado. En este caso, other/temp.json ha sido renombrado a other/other.json. El número **100** indica el porcentaje de similitud entre los dos archivos. Un 100 significa que el archivo ha sido renombrado sin cambios (100% similar).
- `git log --stat` → Es una versión más descriptiva del `git log` que nos da información detallada sobre los archivos que fueron modificadas y cuántas líneas se añadieron o eliminaron en cada commit. El "--stat" se puede combinar con otras opciones de `git log` para hacer un log más informativo
```
commit cccfd17f3dbb554ff4f997591c8e735ff2a96fec 
Author: Cristina Correa <cristina.correa.segade@gmail.com>
Date:   Fri May 24 14:28:22 2024 +0200

    json modificado

 other/info.json                 | 1 +
 other/{temp.json => other.json} | 0
 other/otro.json                 | 0
 other/prueba.json               | 8 ++++----
 4 files changed, 5 insertions(+), 4 deletions(-)
```
- `git log -p` → Es lo mismo que hacer `git log --patch`. Esta es una versión mucho más descriptiva que la anterior. Aquí no solo muestra los archivos que fueron modificados y el número de líneas totales, sino que también muestra los cambios exactos. Ej: Nos dice que en "index.html" añadimos una lista desordenada mostrándola en verde, y que quitamos el encabezado de nivel uno que ahora aparece en rojo. El "-p" se puede combinar con otras opciones de `git log` para hacer un log más informativo
- `git log --graph` → Igual que el "git log" de siempre pero con una información visual a mayores de las ramas. El "--graph" se puede combinar con otras opciones de `git log` para hacer un log más informativo
- `git log --graph --pretty=oneline` → Igual que el anterior pero todo resumido en una línea
```
* cccfd17f3dbb554ff4f997591c8e735ff2a96fec (HEAD -> main) json modificado
* d76e7c57cb94831c57f3d109d57ad75ae2380adb json añadido
* 74b7c7fe5410f535adf41a0af0c6afce41cd0ea7 fotografias añadidas
```
- `git log --decorate --all --oneline` → Igual que el anterior pero con el hash mucho más simple en vez del largo
```
cccfd17 (HEAD -> main) json modificado
d76e7c5 json añadido
74b7c7f fotografias añadidas   
```
- `git log --stat --pretty=format:"%h - %an, %ar : %s"` → Es como un `git log --stat` pero la opción "--pretty=format:" personaliza la salida del log. Dentro de las comillas, se pueden usar varios placeholders para mostrar diferentes partes de cada commit.
```
cccfd17 - Cris Correa, 12 minutes ago : json modificado                                            
 other/info.json                 | 1 +                                                             
 other/{temp.json => other.json} | 0                                                               
 other/otro.json                 | 0                                                               
 other/prueba.json               | 8 ++++----                                                      
 4 files changed, 5 insertions(+), 4 deletions(-)    
```
> [!NOTE]
> Veamos qué significa cada placeholder de "--pretty=format:"
> - **%h** = El hash abreviado del commit.
> - **%an** = El nombre del autor del commit.
> - **%ar** = La fecha del commit en formato relativo (por ejemplo, "2 weeks ago").
> - **%s** = El mensaje del commit.
- `git log --since [numeroAño/]numeroMes/numeroDía` → Nos da todo el histórico de commits desde el día que hayamos puesto. Ej: `git log --since 3/6` nos da el histórico desde el 6 de Marzo de este año y `git log --since 2024/10/1` nos da el histórico desde el 1 de Octubre de 2024

### git diff
- `git diff` → Muestra las diferencias entre dos estados diferentes en el respositorio Git. Estos estados pueden ser entre el directorio de trabajo y el stage, entre el stage y el commit más reciente, o entre dos commits diferentes. Cuando ejecutas "git diff" sin ningún argumento adicional, muestra las diferencias entre el directorio de trabajo y el staging area, es decir, las modificaciones que aún no se han añadido al tatage. Esto te permite revisar los cambios que has realizado antes de confirmarlos con un commit. (Es más visual la herramienta de visualización de vscode)
- `git diff --staged` → Enseña las diferencias entre el staging area y el último commit. Esto significa que te muestra los cambios que han sido añadidos al stage, pero aún no se han confirmado con un commit. Es lo mismo que hacer `git diff --cached` 
- `git diff HEAD`→ Muestra las diferencias entre el directorio de trabajo y el commit más reciente.
- `git diff hashCommit` → Enseña las diferencias entre el directorio de trabajo y el commit especificado.
- `git diff hashCommitInicial hashCommitFinal` → Muestra las diferencias entre dos commits específicos.
- `git diff ramaInicial ramaFinal` → Enseña las diferencias entre dos ramas específicas.
- `git diff --color-words='[^[:space:]]'` → Es una forma avanzada de usar `git diff` que destaca las diferencias en un modo más granular y enfocado en palabras individuales en lugar de líneas completas. Básicamente muestra el documento completo poniendo en rojo las letras o palabras eliminadas y en verde las añadidas sin poner el antes y el después.La opción `--color-words` colorea las diferencias a nivel de palabras en lugar de líneas completas. La expresión regular `'[^[:space:]]'` especifica cómo definir una "palabra" para el propósito del resaltado de diferencias. `[^...]` es una clase de caracteres negados, que coincide con cualquier carácter que no esté dentro de los corchetes y `[:space:]` es una clase de caracteres POSIX que coincide con cualquier carácter de espacio en blanco (como espacio, tabulación, nueva línea, etc.). En conjunto, `[^[:space:]]` coincide con cualquier carácter que no sea un espacio en blanco. En otras palabras, cada secuencia continua de caracteres no espaciales se considera una "palabra".

### git reflog
- `git reflog` → Muestra un registro de referencia del historial de cambios realizados en HEAD (puntero a la rama actual) y otras referencias de Git, como ramas y etiquetas. La palabra "reflog" es una abreviatura de "registro de referencia de log". Este registro puede ser útil para recuperar cambios perdidos o deshacer acciones no deseadas, como restablecer ramas a estados anteriores o recuperar commits eliminados accidentalmente con `git reset --hard`.

### git show
- `git show hashCommit` → Muestra información detallada sobre un commit específico identificado por su hash. Proporciona detalles específicos del commit seleccionado, incluyendo el autor, la fecha, el mensaje del commit y los cambios introducidos por ese commit. No solo muestra las diferencias como hace "git diff", sino también la información del commit en sí (autor, fecha y mensaje). Es útil para inspeccionar un commit específico en detalle y comprender qué cambios se introdujeron en él.
- `git show --color-words='[^[:space:]]'` → Es similar a `git diff --color-words='[^[:space:]]'` en términos de funcionalidad y propósitos, pero se usa específicamente para mostrar los detalles de un commit en particular. (mirar la referencia para más explicaciones)
- `git show nombreTag` →  Nos enseña información sobre la tag. Para info más detallada ir a "tags"

## 📝 Para hacer modificaciones
### git checkout
- ``git checkout archivo/commit`` → Es para volver a un punto específico. Afecta a archivos, commits y ramas. En archivos, quita cambios que no están commiteados (cuando un archivo esta "M"); en commits, puedes moverte a otros commits y ver los archivos, pero hay que tener cuidado con "The Detached HEAD State"; y en ramas, puedes moverte a diferentes ramas. Utilizar "git checkout" con ramas está desaconsejado desde la versión 2.23 de Git, por lo que ahora para esa funcionalidad utilizamos "git switch"
- `git checkout -- .` → Recupera el estado de los archivos como estaban en el último commit. Si tienes algún archivo modificado que tiene un error pero cuando hiciste commit estaba bien, puedes volver a la versión del archivo que estaba bien con este comando. Esto no afecta a los archivos que hemos creado, son nuevos y nunca han sido stageados (son los que tienen una U de "untracked"), pero sí a cualquier otro archivo (incluso restaura los que borraste).

### git reset
- ``git reset []`` → Permite RESTABLECER tu estado actual a un estado específico. Puedes restablecer el estado de archivos específicos, así como el de toda una rama. Esto es útil si aún no has subido tu commit a GitHub o a otro repositorio remoto. El git reset también se podía usar como la antítesis de "git add" como vimos anteriormente.
- `git reset --soft HEAD^Numero/hashCommit` → Borra un commit pero guarda los cambios en el stage (gracias al --soft). Es decir, git moverá la rama actual hacia el commit especificado, pero mantendrá los cambios realizados en el staging area. Esto significa que los cambios se retiran del commit, pero permanecen listos para ser confirmados nuevamente con un nuevo commit. Aquí se puede usar "HEAD^Numero" o el propio hash del commit que queramos eliminar. Si queremos eliminar el último commit sería `git reset --soft HEAD^1`. Esto se usa por ejemplo si en el commit x se te olvidó poner otros archivos y quieres incluirlos. Tu lo que haces es borrar ese commit y crear uno nuevo con los archivos del commit anterior (con sus modificaciones guardadas) y los que quisieras añadir. **Esto se puede hacer antes de hacer un push, si se ha hecho, evita hacerlo**
- `git reset --mixed HEAD^Numero/hashCommit` → Borra un commit, no guarda los cambios en el stage pero sí que los guarda en el área de trabajo local (gracias al --mixed). Este es el comportamiento predeterminado de `git reset` si no se especifica ningún argumento. Con "--mixed", Git moverá la rama actual hacia el commit especificado y deshará los cambios en el staging area, pero mantendrá los cambios en el directorio de trabajo. Esto significa que los cambios deshechos no se perderán, pero tendrás que agregarlos nuevamente al stage si deseas confirmarlos nuevamente. **Esto se puede hacer antes de hacer un push, si se ha hecho, evita hacerlo**
- `git reset --hard HEAD^Numero/hashCommit` → Elimina el commit con todos los cambios, es decir, que los archivos modificados que se guardasen en ese commit, volverían a estar como estaban en el último commit antes de ese. Es una acción "destructiva", por lo que se debe tener cuidado al usarlo, ya que los cambios deshechos no se pueden recuperar fácilmente. Se recomienda utilizarlo con precaución y asegurarse de que realmente deseas eliminar los cambios. Por ejemplo si tengo tres commits y hago el reset hard del segundo commit, los archivos que estuvieran modificados y guardados en el segundo commit, volverían a su estado inicial guardado en el primer commit, pero no se guardarían las modificaciones que se hicieron entre el primer y el segundo commit (porque estaban guardadas en el segundo commit que ha sido borrado). Si borramos algo que no deberíamos, podemos hacer un `git reflog` ver a qué punto queremos volver, buscar el hash que nos interesa restaurar y hacer un `git reset --hard` con ese hash. **Esto se puede hacer antes de hacer un push, si se ha hecho, evita hacerlo**
- `git reset --hard` → Resetea el stage y el directorio de trabajo al último commit actual. Esto significa que todos los cambios no commiteados en el directorio de trabajo y en el stage serán descartados, y el estado del repositorio volverá al último commit. Este comando es muy poderoso y debe usarse con precaución, ya que los cambios no commiteados se perderán permanentemente. Es bastante parecido a `git checkout -- .`, salvo que el `git checkout -- .` sí que guarda los cambios que se subieron al stage.
> [!NOTE]
> **Si queremos eliminar el último commit**, lo ideal es hacer `git reset --soft HEAD~1` para mantener los cambios en el directorio de trabajo. Esto moverá la rama actual para que apunte al commit anterior, pero los cambios realizados en el último commit permanecerán en el stage.

### git mv
- `git mv nombreAntiguo nombreNuevo` → Renombra o mueve archivos o directorios de Git. En lugar de usar el comando "mv" del sistema de archivos, que Git puede interpretar como eliminar el archivo antiguo y agregar uno nuevo, "git mv" realiza la acción de manera más inteligente, lo que ayuda a mantener el historial de versiones del archivo. Cuando cambiamos el archivo de nombre con "git mv", nos aparece una "R" de Rename. Ejemplos de esto serían: "git mv app/index.html app/indexcambiado.html" para cambiar un archivo de una carpeta o "git mv css styles" para cambiar el nombre de una carpeta

## 🗑 Para borrar archivos
### git rm
- `git rm nombreArchivo.extensionArchivo` → Elimina el archivo del repositorio de Git y también del sistema de archivos local. Este comando es útil cuando deseas eliminar un archivo que ya no necesitas y quieres que este cambio se refleje en el repositorio. Al ejecutar `git rm`, el archivo se elimina del directorio de trabajo y del stage, pero no se elimina del historial de commits. Para que este cambio se registre en el historial, es necesario hacer un commit después de ejecutar `git rm`
- `git rm -r nombreDirectorio/` → Elimina el directorio y todo su contenido del repositorio de Git y también del sistema de archivos local. Con "-r" que es "--recursive" indicamos que elimine no solo el directorio especificado, sino también todo su contenido, incluidos los archivos y subdirectorios que pueda contener.
- `git rm --cached nombreArchivo.extensionArchivo` → Elimina el archivo de una forma diferente al `git rm` estándar porque en vez de eliminarlo del sistema de archivos local, aparece el archivo como "Untracked". 
> [!NOTE] 
> Si creamos un archivo, lo añadimos al stage y lo commiteamos, nos aparecerá un log como este al hacer `git log --name-status`:
> ```
> commit 74c789a8c4bcfc3b29037b94c89b1da1affe3731 (HEAD -> main)
> Author: Cris Correa <cristina.correa.segade@gmail.com>
> Date:   Fri May 47 12:56:40 2024 +0200
> 
>     json añadido
> 
> A       other/file.json
> ```
> Ahora si hacemos `git rm other/file.json` eliminamos el archivo del repositorio y nos aparece la siguiente información si hacemos un `git status`:
> ```
> Changes to be committed:
>   (use "git restore --staged <file>..." to unstage)
>         deleted:    other/file.json
> ```
> Sin embargo, si en vez de haber hecho `git rm other/file.json` hacemos `git rm --cached other/file.json` y luego ejecutamos un `git status`, nos aparecerá la siguiente información:
> ```
> Changes to be committed:
>   (use "git restore --staged <file>..." to unstage)
>         deleted:    other/file.json
> 
> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
>         other/file.json
> ```
> Ahí podemos ver que cuando no añadimos "--cached", el archivo se elimina y desaparece del repositorio, mientras que si sí que añadimos "--cached", el archivo aparece en el repositorio como untracked.
### git clean
- `git clean -n` → El comando `git clean` se utiliza para eliminar archivos no rastreados en el directorio de trabajo (untracked). Esto es útil para limpiar el directorio de trabajo de archivos innecesarios que no están bajo control de versiones. Cuando añadimos "-n", que significa "dry run" o "prueba en seco", Git simula la operación de limpieza y muestra qué archivos serían eliminados sin realmente borrarlos. Es una manera segura de ver los cambios que se realizarán antes de llevarlos a cabo. Si ejecutamos `git clean -n` cuando tenemos un archivo untracked, nos aparecería un mensaje `Would remove nombreArchivo.extensionArchivo` por cada archivo untracked.
- `git clean -f` → Elimina todos los archivos untracked y nos devuelve un mensaje por cada archivo borrado de la siguiente manera: `Removing nombreArchivo.extensionArchivo`
- `git clean -df` → Elimina los archivos no rastreados (untracked) y los directorios (con "-d") del directorio de trabajo. El "-d" requiere de otras opciones para poder borrar carpetas con archivos. Si queremos borrar la carpeta "log/" con varios archivos .log y ejecutamos `git clean -d` nos dará el siguiente error: `fatal: clean.requireForce defaults to true and neither -i, -n, nor -f given; refusing to clean` pero si ejecutamos `git clean -fd` nos devolverá `Removing log/` ya que "-f" fuerza el borrado.
- `git clean -xf` → Elimina todos los archivos ignorados por .gitignore, además de los archivos no rastreados. Necesita añadir "-f" o dará el mismo error que en el anterior comando.
- `git clean -Xf` → Elimina únicamente los archivos ignorados por .gitignore.
> [!NOTE]
> Si en un .gitignore ponemos que se ignoren los archivos con extensión ".py" y creamos los archivos: prueba.py y prueba.java. El ".py" será ignorado y el ".java" estará untracked.
> - Si ejecutamos `git clean -xf`, se eliminarán tanto prueba.py como prueba.java
> - Si ejecutamos `git clean -Xf`, se eliminará únicamente el prueba.py
> - Si ejecutamos `git clean -f`, se eliminará únicamente el prueba.java
> ```
> $ git clean -xf
>   Removing prueba.java
>   Removing prueba.py
>
> $ git clean -Xf
>   Removing prueba.py
>
> $ git clean -f
>   Removing prueba.java
> ```
## 🕵 Para alias
- ``git config --global alias.nombreAlias "comando"`` → Esto te crea un alias que luego puedes utilizar haciendo "git nombreAlias" y hace el mismo comando que estás poniendo ahí. Cuando decimos "comando", nos referimos a todo lo que vaya después de "git", ya que si en el comando ponemos "git ..." nos va a dar el error "expansion of alias 'nombreAlias' failed; 'git' is not a git command", por lo que **NO ponemos "git" dentro del comando"

> [!NOTE]
> Para más información sobre los alias, por favor mira el archivo [Alias.md](https://github.com/CrisCorreaS/apuntes-git/blob/main/Alias.md)

## 🏷 Para tags
### git tag
- `git tag` → Vemos todas las tags que tenemos.
- `git tag nombreTag` → Creamos una tag ligera, que es una referencia a un commit específico, y con esta, podemos descargar el proyecto justo como se encontraba en ese instante. Si no especificamos el hash del commit, lo va a crear en el último commit en el que estemos y debemos tener en cuenta que esta etiqueta no contiene metadatos adicionales como el nombre del autor, la fecha de creación o un mensaje asociado. En general las etiquetas se suelen utilizar para marcar versiones o releases de nuestro código. Ej: creamos un tag que marque la versión 1.0.0 del código con el comando "git tag v1.0.0".
- `git tag nombreTag hashCommit` → Creamos una tag ligera en un commit específico, no en el commit actual. Ej: "git tag v0.0.3 c9032ec"
- `git tag -a nombreTag` → Creamos una tag anotada, ya que "-a" significa annotated. Una etiqueta anotada es un objeto Git completo en sí mismo. Almacena un hash completo del commit al que apunta, así como metadatos adicionales como el nombre del autor, la fecha de creación y un mensaje asociado. Son útiles para marcar hitos importantes en la historia del proyecto y para proporcionar información adicional sobre esos hitos. Al escribir este comando nos va a mandar poner un mensaje, como si hacemos "git commit" y no incluimos el mensaje, por eso es mejor hacer el siguiente comando:
- `git tag -a nombreTag -m "Mensaje"` → Creamos una tag anotada con el mensaje. Es lo mismo que el anterior comando pero añadiendo un mensaje como metadato. Ej: "git tag -a v1.0.0 -m 'Versión 1.0.0 lista'"
- `git tag -a nombreTag hashCommit -m "Mensaje"` → Creamos una tag anotada que hace referencia a un commit en concreto que no es en el que estamos. Si no ponemos el hash, la tag se crearía en el commit en el que estemos como habíamos estado haciendo hasta ahora. Ejemplo de una tag anotada en un commit en concreto: "git tag -a v0.1.0 0d34c9e -m 'La versión 0.1.0 está lista'"
- `git tag -d nombreTag` → Eliminamos el tag con ese nombre.

### git show
- `git show nombreTag` → Nos enseña información sobre la tag. Si hacemos que nos enseñe info de una tag ligera, solo nos enseñará información sobre el commit al que apunta. Si hacemos lo mismo pero con una tag anotada, nos aparecerá la misma información del commit al que apunta y a mayores, información sobre la propia tag (autor, fecha y mensaje). Ej: "git show v0.1.0" 

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
### git branch
- `git branch` → Muestra todas las ramas locales de tu repositorio de GitHub y la rama en la que te encuentras actualmente se marca con un asterisco y un color diferente
- `git branch -a` → Muestra una lista de todas las ramas en el repositorio, tanto locales como remotas. Es útil para ver todas las ramas disponibles en el proyecto y poder cambiar a la que queramos. El "-a" significa "--all".
> Un ejemplo de la diferencia entre `git branch` y `git branch -a` sería el siguiente:
> Si ejecutamos el comando `git branch` en un repositorio que acabamos de clonar y donde aún no hemos creado ninguna rama, solo nos aparecerá la rama main donde estamos situados.
> ```
> * main
> ```
> Si escribimos el comando `git branch -a` podremos ver las ramas remotas que existen en el repositorio como: dev, feature1 y feature2
> ```
> * main 
>   remotes/origin/HEAD -> origin/main
>   remotes/origin/dev
>   remotes/origin/feature1
>   remotes/origin/feature2
>   remotes/origin/main
> ```
- `git branch -r` → Muestra únicamente las ramas remotas del repositorio. Las ramas remotas son las que existen en el servidor remoto (como GitHub, GitLab, etc.) y no necesariamente están disponibles localmente. El "-r" significa "--remote". Si no hay ninguna rama remota, simplemente no devolverá ninguna rama. Con el ejemplo anterior, si hacemos `git branch -r` nos devolverá lo siguiente:
```
  remotes/origin/HEAD -> origin/main
  remotes/origin/dev
  remotes/origin/feature1
  remotes/origin/feature2
  remotes/origin/main
```
- `git branch nombreRama` → Crea una nueva rama con el nombre especificado
- `git branch -m nombreAntiguoRama nombreNuevoRama` → Cambiamos el nombre a la rama en la que estamos por el nombreNuevoRama. Esto se suele hacer mucho para cambiar el nombre de rama master a main. "-m" significa "--move"
- `git branch -M nombreNuevoRama` → Renombra la rama en la que nos encontramos sin importar si ya existe una rama con ese nombre. Si hacemos `git branch -M dev` renombrará la rama en la que nos encontramos a "dev" y por lo tanto, cualquier rama "dev" previamente existente será reemplazada por la rama actual. Esto significa que cualquier trabajo que se haya realizado en la rama "dev" anterior será perdido si no se ha fusionado en otra rama antes de ejecutar este comando. Por esta razón, es importante usar este comando con precaución, especialmente en un entorno de trabajo colaborativo. "-M" con "M" mayúscula significa "--move --force"
- `git branch -d nombreRamaBorrar` → Borra la rama que queramos ya que el "-d" significa delete. Si hay algún cambio en la rama que no esté mergeado, nos lo va a decir y nos va a preguntar si estamos seguros. Lo ideal es tener cuidado con la rama en la que estemos, pero no va a haber ningún problema si estamos en la rama "feature1" y hacemos un ´git branch -d feature1` ya que nos moverá automáticamente a otra rama, por ejemplo a "dev" o a "main".
- `git branch -d nombreRamaBorrar -f` → Fuerza la eliminación de la rama ya que el "-f" significa force. En este caso, si hay algún cambio en la rama que no esté mergeado, lo va a borrar sin preguntar si estamos seguros. Es mejor utilizar el comando anterior y no este. Es lo mismo que hacer `git branch -D nombreRamaBorrar` ("-D" con D mayúscula es como la suma de "-d" y "-f")
- `git branch -t nombreRama origin/nombreRama` → Crea una nueva rama local llamada y establece una relación de seguimiento con la rama remota. Esto significa que la nueva rama local estará vinculada a la rama remota y Git configurará de manera automática el seguimiento para permitir comandos como git pull y git push sin especificar explícitamente las ramas remotas y locales. El "-t" es igual a "--track". Un ejemplo de este comando sería `git branch --track feature1 origin/feature1` 
### git switch
- `git switch nombreRama` → Cambia tu rama actual por la rama que has especificado. Antes de la versión de Git 2.23 se usaba "git checkout nombreRama" para hacer esto, pero ahora es recomendable hacerlo con "git switch". Si quieres cambiar de rama cuando tienes código en el área de trabajo local que no has subido al stage, te va a dar un fallo como este: *error: Your local changes to the following files would be overwritten by checkout: nombre de archivo* *Please commit your changes or stash thm before you switch branches.* *Aborting*. Esto quiere decir que como tienes el código sin guardar, no vas a poder cambiarte de rama porque si no se te perderían todas las modificaciones. Para eso o bien haces un commit o bien subes los cambios al stash.
- `git switch -` → Cambia a la rama en la que estabas anteriormente. Si antes estabas en main y ahora estás en dev, vuelves a main.
- `git switch -c nombreRama` → Crea una nueva rama y te mueve directamente a la rama que has creado ya que "-c" significa "--create". Este es el equivalente al hacer un "git branch x" para crear la rama y luego un "git switch x" para moverte a la rama, pero simplificadamente. Anteriormente se hacía "git checkout -b nombreRama" para hacer lo mismo, pero desde la versión 2.23 de Git, esto ha cambiado.
- `git switch -c ramaNueva -t ramaOrigen` → Crea una nueva rama basada en otra existente. Tenemos que usar la opción "-c" de "create" junto con la opción "-t" de "--track" para especificar la rama de origen. La opción "-t" establece la nueva rama para rastrear la rama especificada, lo que significa que cuando cambiamos a la nueva rama, Git intentará rebasear automáticamente los cambios de la rama de origen. 

### 3️⃣ tipos de merges que existen con las ramas
![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img2.png)
![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img3.png)
![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img4.png)

- `git merge ramaConCambios` → Une los cambios de la "ramaConCambios" a la rama en donde nos encontramos. Siempre que se vaya a unir una rama a otra, debemos de estar en la rama que va a recibir los cambios. Si queremos actualizar la rama "dev" con una nueva funcionalidad de la rama "feature1", tenemos que colocarnos en "dev" para recibir esos cambios y luego hacer un "git merge feature1". Normalmente (e idealmente), siempre se hará un Fast-forward lo cual significa que no hay ningún conflicto.

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
- `git clone urlHTTPS` → Clona un repositorio existente de GitHub en tu repositorio remoto
- `git branch` → Muestra todas las ramas locales de tu repositorio de GitHub y la rama en la que te encuentras actualmente se marca con un asterisco y un color diferente. Si solo aparece la rama "main" tienes que hacer los siguientes comandos
  - `git fetch` → Recupera los cambios remotos (como ramas y commits) desde el repositorio de GitHub pero no los fusiona con tu rama actual. Es útil para obtener información actualizada sobre las ramas remotas sin modificar tu trabajo actual.
  - `git config --local --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/*` → Configura la recuperación remota de ramas específicas. En este caso, está configurando Git para recuperar todas las ramas desde el repositorio remoto (origin) y almacenarlas localmente en la carpeta refs/remotes/origin/.
  - `git fetch origin` → Recupera cambios específicos desde el repositorio remoto llamado "origin". Esto trae los cambios de las ramas del repositorio remoto a tus referencias remotas locales
  - `git config --get remote.origin.fetch` → Muestra la configuración de recuperación remota para el remoto llamado "origin". En este caso, está configurado para recuperar todas las ramas.
  - `git fetch --all` → Recupera cambios desde todos los remotos configurados en tu repositorio
  - `git branch -a` → Muestra todas las ramas, tanto locales como remotas. Si te aparecen las ramas así:
    `CatiaCrisMarta>git branch -a` <br>
    `* main`<br>
    ` remotes/origin/HEAD → origin/main` <br>
    ` remotes/origin/catia` <br>
    ` remotes/origin/cris` <br>
    ` remotes/origin/main` <br>
    ` remotes/origin/marta` <br>
- `git switch nombreRama` → Cambia a la rama llamada "nombreRama"
- `git branch` → Muestra todas las ramas locales de tu repositorio de GitHub y la rama en la que te encuentras actualmente se marca con un asterisco y un color diferente.


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
``git checkout -b "dev"`` → Con esto creamos la rama dev a partir de la rama en la que estamos (main) y nos situamos en la rama dev
<br><br>
2️⃣ Una vez creada la rama **dev**, desarrollamos cualquier cosa y hacemos un commit _(el primer circulito de la rama dev)_ tenemos que crear a partir de esta, la rama **feature1** (la azul):
<br>
``git checkout -b "feature1"`` → Con esto creamos la rama feature1 a partir de la rama dev y nos situamos en la rama feature1
<br><br>
3️⃣ Ahora, en la rama **feature1**, desarrollamos código y hacemos commits _(todos los círculos que tiene la rama feature1 azul)_
<br><br>
4️⃣ Por otro lado, nos vamos a pasar a **dev** para corregir un bug ``git switch dev`` y una vez corregido, hacemos un commit _(el segundo círculito de la rama dev)_ . Ahora que está corregido el bug, creamos la rama **feature2**:
<br>
``git checkout -b "feature2"`` → Con esto creamos la rama feature2 a partir de la rama en la que estamos (dev), y nos situamos en feature2
<br><br>
5️⃣ En la rama **feature2**, desarrollamos código y hacemos un commit para guardarlo _(el único circulito de la rama feature2 naranja)_. Nos pasamos a la rama **dev** con el comando ``git switch dev`` y en la rama **dev** cambiamos el README.md y hacemos un commit _(el tercer circulito de la rama dev)_ 
<br><br>
6️⃣ Ahora, vamos a hacer un merge de la rama **feature2** en la rama **dev**. Para esto tenemos que estar en la rama **dev** y escribir el siguiente comando:
<br>
``git merge feature2`` → Con este comando estamos volcando todos cambios guardados en los commits de la rama feature2, en la rama dev. Si hemos cambiado cosas en la rama dev que no afectan a los cambios de la rama feature2, no va a haber nignún problema. Si al contrario, hemos cambiado el README.md tanto en el tercer commit de la rama dev, como en el primero de la rama feature2, habrá un merge conflict.
<br><br>
7️⃣ Vamos a interpretar que no hubo ningún merge conflict y que se ha hecho el merge correctamente. Al hacer un merge, siempre se hace un commit automáticamente _(este sería el cuarto circulito de la rama dev)_
<br><br>
8️⃣ Por último, vamos a borrar la rama **feature2** porque ya no vamos a hacer ninguna funcionalidad que tenga que ver con lo que hicimos en **feature2**, así que nos vamos a cualquier rama que no sea **feature2** _(lo normal es seguir en dev)_ y hacemos:
<br>
``git branch -d feature2``
<br><br>

> [!NOTE]
> Los comandos más importantes que usaremos de ramas serán:
> - ``git switch -c ramaNueva``
> - ``git merge ramaQueQueremosFusionarConLaRamaEnLaQueEstamos``
> - ``git branch -d ramaQueBorramos``


![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img6.png)


### 🗺 git rebase
- `git rebase main` → Actualiza tu rama actual incorporando los cambios realizados en la rama main en la que otros colaboradores pueden haber estado trabajando. El rebase reorganiza los commits de tu rama actual sobre los commits más recientes de la rama especificada (en este caso, "main"), lo que puede ayudar a mantener un historial de commits más limpio y lineal. Esto es útil para evitar la creación de bifurcaciones innecesarias y conflictos en el historial de tu repositorio.


![](https://github.com/CrisCorreaS/apuntes-git/blob/main/img/img7.png)
<br />
- `git rebase -i HEAD~X/Hash` → Es para un rebase **interactivo**. Si hacemos `git rebase -i HEAD~3` sería un rebase interactivo en la rama actual, pero limitando la interacción a los últimos tres commits. '-i' (o '--interactive') indica que el rebase será interactivo, lo que significa que Git abrirá un editor de texto para que puedas realizar cambios específicos en la historia de los commits. Cuando Git abre el editor de texto, se pueden realizar diversas acciones: reorganizar los commits, combinarlos, editar mensajes de commit, eliminar commits o incluso dividirlos en varios commits más pequeños. Este enfoque interactivo te brinda un mayor control sobre la historia de tu rama y te permite ajustarla según tus necesidades específicas.


## 🔐 Stash
El stash de Git es una funcionalidad que permite almacenar temporalmente y de forma segura los cambios realizados en el código sin necesidad de hacer un commit. Esto es útil cuando necesitas cambiar de rama, por ejemplo: para trabajar en otra rama sin perder los cambios de tu rama actual que no has subido al stage ni has commiteado. Los cambios almacenados en el stash se guardan en una pila provisional, permitiendo recuperarlos más adelante cuando estés lista para continuar con ellos.

Git permite tener múltiples stashes, manejar varios al mismo tiempo puede ser complicado debido a la falta de descripciones claras para cada uno. Por defecto, los stashes se identifican simplemente como "WIP" (Work in Progress) en la rama y el commit desde el cual se crearon, lo que puede dificultar recordar qué contiene cada stash. Lo idóneo es utilizar un stash a un tiempo o anotarlos con una descripción usando un comando que veremos a continuación.

### git stash
- `git stash` → Guarda los cambios del área de trabajo local en el stash y revierte el directorio de trabajo a como se veía en el último commit. Al realizar este comando primero tenemos que hacer un `git add` de todos los cambios que queremos guardar, es decir, que **los cambios para que se guarden en el stash, tienen que estar en el stage**. Si los cambios están en local y no en el stage, si hacemos este comando, nos dará el siguiente error: *No local changes to save*. Una vez hagamos `git stash` nos responde lo siguiente *Saved working directory and index state WIP on nombreRama: hashUltimoCommit mensajeUltimoCommit*. También se tiene que tener en cuenta que los cambios guardados están disponibles en cualquier rama del repositorio
- `git stash save "Mensaje opcional"` → Este comando es similar al anterior, pero permite añadir un mensaje opcional al guardar los cambios en el stash. Este mensaje puede ser útil para identificar rápidamente el propósito o el contexto de los cambios guardados en el stash.
- `git stash list` → Muestra los cambios guardados en el stash. Esto devuelve una lista de capturas guardadas en el stash con formato **stash@{0}: RAMA-STASHED-CAMBIOS-SON-PARA: MESSAGE**.
- `git stash list --stat` → Es lo mismo que el anterior comando pero al agregar --stat al comando, muestra además la información estadística de los cambios en cada stash. Esto incluye las líneas agregadas y eliminadas en cada archivo modificado en el stash. Es muy parecido a hacer `git stash show` pero de todos los stashes.
> [!NOTE]
> La parte de **stash@{0}** es el nombre del stash, y el número en las llaves ({ }) es el índice (index) del stash. Si se tiene múltiples conjuntos de cambios guardados en stash, cada uno tendrá un índice diferente.
- `git stash show indiceStash` → Muestra un resumen de los cambios en el stash. Si hacemos `git stash show`, nos dará la info del primer stash (índice = 0) y mostrará el siguiente resultado:
```
 resources/prueba.py      |  1 +
 resources/script copy.js | 11 +++++++++++
 2 files changed, 12 insertions(+)
```
- `git stash show -p indiceStash` → Es lo mismo que el anteior comando pero mostrando los cambios de forma más informativa. La información tiene un estilo muy parecido a cuando hacemos ´git diff´. Si hacemos `git stash show -p` (en un repo donde solo hay un stash), nos dará el siguiente resultado:
```
diff --git a/resources/prueba.py b/resources/prueba.py
new file mode 100644
index 0000000..770ba66
--- /dev/null
+++ b/resources/prueba.py
@@ -0,0 +1 @@
+// Esto es una prueba
\ No newline at end of file
diff --git a/resources/script copy.js b/resources/script copy.js
new file mode 100644
index 0000000..b9a5d52
--- /dev/null
+++ b/resources/script copy.js  
@@ -0,0 +1,11 @@
+let f=30;
+
+function suma(c, b) {
+  return c + b;
+}
+
+let total = suma(f, 30);
+console.log(total + 4);
+console.log(total + 7);
+console.log(total + f);
+console.log("total + f");
\ No newline at end of file
```
- `git stash apply` → Recupera los cambios en el último Stash dejando una copia de los mismos en el stash. Es lo mismo que hacer `git stash apply 0` sabiendo que "0" se refiere al índice del último stash
- `git stash apply indiceStash` → Recupera los cambios en el último Stash dejando una copia de los mismos en el stash. Es lo mismo que el anterior pero con un mensaje informativo
- `git stash pop` → Recupera los cambios en el último Stash eliminando los archivos del stash. Es lo mismo que hacer `git stash pop 0` sabiendo que "0" se refiere al índice del último stash
- `git stash pop indiceStash` → Recupera los cambios en el último Stash eliminando los archivos del stash. Es lo mismo que el anterior pero con un mensaje informativo
- `git stash drop indiceStash` → Borra los cambios guardados en stash sin aplicarlos
- `git stash clear` → Limpia todo del stash

## 💫 Pull Request (PR)
Una pull request es un mecanismo utilizado en plataformas de control de versiones como GitHub, Bitbucket y GitLab para solicitar que los cambios realizados en una rama de un repositorio sean mergeados en otra rama, generalmente la rama principal o master. Este proceso permite a los colaboradores de un proyecto contribuir con sus modificaciones, mejoras o correcciones de errores de manera organizada y revisada por otros miembros del equipo antes de ser incorporadas al código base principal.

### Pull Request en un proyecto ajeno
1. Buscamos info de cómo contribuír en el archivo Contributing
2. Hacemos un fork del repositorio y luego lo clonamos en local con `git clone url`
3. Creamos una rama nueva según la metodología que utilicen en el proyecto y nos movemos a esa rama con `git switch -c nombreRama` o creamos una rama a partir de una en específico **situándonos en la rama que queremos copiar** y haciendo `git checkout -b nombreRama`
4. Hacemos todos los cambios que queramos y hacemos un `git status` para saber que hemos hecho todos los cambios que queríamos
5. Commiteamos los cambios en la rama con el mensaje siguiendo el estilo del propio repositorio
6. Hacemos `git push origin nombreRama` para subir la rama
7. Desde GitHub situándonos en la rama nueva podemos hacer click tanto en **Compare & Pull Request** como en **Contribute > Open Pull Request**
8. Ahora vemos un formulario donde podemos poner el nombre de la PR, al igual que una descripción donde podemos añadir texto, enlaces e imágenes. También se pueden añadir reviewers, assigners, labels...
9. Cuando acabemos, hacemos click en **Create pull request**
Para más info pulsa [aquí](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project)

### Pull Request en un proyecto como colaborador
1. Buscamos info de cómo contribuír en el archivo Contributing
2. Clonamos el repositorio en local con `git clone url`
3. Creamos una rama nueva según la metodología que utilicen en el proyecto y nos movemos a esa rama con `git switch -c nombreRama` o creamos una rama a partir de una en específico **situándonos en la rama que queremos copiar** y haciendo `git checkout -b nombreRama`
4. Hacemos todos los cambios que queramos y hacemos un `git status` para saber que hemos hecho todos los cambios que queríamos
5. Commiteamos los cambios en la rama con el mensaje siguiendo el estilo del propio repositorio
6. Hacemos `git push origin nombreRama` para subir la rama
7. Desde GitHub situándonos en la rama nueva podemos hacer click tanto en **Compare & Pull Request** como en **Contribute > Open Pull Request**
8. Ahora vemos un formulario donde podemos poner el nombre de la PR, al igual que una descripción donde podemos añadir texto, enlaces e imágenes. También se pueden añadir reviewers, assigners, labels...
9. Cuando acabemos, hacemos click en **Create pull request**

## 🗃 Otros archivos

### .gitignore
- `.gitignore` → Se utiliza para especificar archivos y directorios que Git debe ignorar al rastrear los cambios en un repositorio. Puedes usar patrones de coincidencia de nombres de archivo para definir qué archivos y carpetas deben ser ignorados por Git. Por ejemplo, puedes incluir patrones para ignorar archivos de compilación, archivos temporales o archivos específicos generados por el sistema. Esto ayuda a mantener el repositorio limpio y evitar que archivos innecesarios sean incluidos en el control de versiones. Se suele poner en la raíz del proyecto, donde también debería de ir la carpeta ".git" que indica que se ha inicializado el repositorio. 

> [!NOTE]
> Para más información sobre .gitignore, mira el archivo [GitIgnore.md](https://github.com/CrisCorreaS/apuntes-git/blob/main/GitIgnore.md)

### .gitkeep
- `.gitkeep` → A diferencia de .gitignore, este archivo no es un archivo oficial de Git. Algunos proyectos pueden utilizarlo para mantener vacíos los directorios vacíos en Git. Git no rastrea los directorios vacíos, por lo que si necesitas que un directorio vacío sea parte de tu repositorio, puedes agregar un archivo .gitkeep dentro de él. Este archivo generalmente está vacío; su nombre sugiere su propósito, que es mantener el directorio dentro del control de versiones.
