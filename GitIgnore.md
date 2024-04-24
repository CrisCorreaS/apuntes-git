# 😶‍🌫️ El archivo .gitignore
- `.gitignore` -> Se utiliza para especificar archivos y directorios que Git debe ignorar al rastrear los cambios en un repositorio. Puedes usar patrones de coincidencia de nombres de archivo para definir qué archivos y carpetas deben ser ignorados por Git. Por ejemplo, puedes incluir patrones para ignorar archivos de compilación, archivos temporales o archivos específicos generados por el sistema. Esto ayuda a mantener el repositorio limpio y evitar que archivos innecesarios sean incluidos en el control de versiones. Se suele poner en la raíz del proyecto, donde también debería de ir la carpeta ".git" que indica que se ha inicializado el repositorio.


Para referirnos a diferentes elementos que queremos ignorar con el archivo .gitignore, tenemos que usar la siguiente sintaxis:
- **`nombreArchivo.extensiónArchivo`** -> Ignora un archivo en específico en la raíz del proyecto.
- **`nombreCarpeta/`** -> Ignora una carpeta en específico con todos sus archivos.
- **`nombreCarpeta/nombreArchivo.extensionArchivo`** -> Ignora un archivo en específico dentro de una carpeta en específico. Si hay una archivo con el mismo nombre en otra carpeta, no se ignorará.
- **`*.extensiónArchivo`** -> Ignora todos los archivos con esa extensión en específico.
- **`!nombreArchivo.extensiónArchivo`** -> Es una excepción para que a ese archivo en concreto no se le ignore.
- **`**/nombreCarpeta`** -> Ignora todas las carpetas con ese nombre en cualquier parte del repositorio. 
- **`nombreArchivo?.extensionArchivo`** -> Ignora archivos que tengan el mismo nombre más un solo carácter en el lugar del signo de interrogación. Ej: si ponemos "style?.css" ignorará "styles.css", "style1.css", ... pero no "styles1.css".
- **`nombreArchivo[0-9].extensionArchivo`** ->  Ignora archivos que tengan el mismo nombre más un dígito en el lugar del rango especificado. Ej: si ponemos "style[0-9].css" ignorará "style0.css", "style1.css", ... pero no "styles.css" o "style10.css".
- **`nombreArchivo[01].extensionArchivo`** ->  Ignora archivos que tengan el mismo nombre más un dígito específico (en este caso, 0 o 1) en el lugar del rango especificado. Ej: si ponemos "style[01].css" ignorará únicamente a "style0.css" y a "style1.css".
- **`nombreArchivo[!01].extensionArchivo`** -> Ignora archivos que tengan el mismo nombre más cualquier carácter excepto 0 o 1 en el lugar del rango especificado. Ej: si ponemos "style[!01].css" ignorará a "styles.css", "style2.css", ... pero no a "style0.css" ni a "style1.css".
- **`nombreArchivo[a-z].extensionArchivo`** -> Ignora archivos que tengan el mismo nombre y cualquier letra minúscula en el lugar del rango especificado.
- **`nombreCarpeta/**/nombreArchivo.extensionArchivo`** -> Ignora un archivo específico que se encuentre en cualquier subdirectorio de una carpeta específica.
- **`nombreCarpeta1/*nombreCarpeta2/nombreArchivo.extensionArchivo`** -> Ignora un archivo específico que se encuentre en un subdirectorio con un nombre específico variable dentro de una carpeta específica. Ej: si ponemos "logs/*day/debug.log" ignora cualquier archivo llamado "debug.log" que esté en "logs/monday/", "logs/tuesday/", ... pero no un archivo "debug.log" que esté en "logs/latest/" o "logs/currently/".

> [!NOTE]
> Para más información puedes consultar los siguientes links:
> [.gitignore Documentation](https://git-scm.com/docs/gitignore)
> [Ignoring files - GitHub Docs](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files)
> [.gitignore Tutorial - Atlassian](https://www.atlassian.com/es/git/tutorials/saving-changes/gitignore)
> [Gitignore Explicado - freeCodeCamp](https://www.freecodecamp.org/espanol/news/gitignore-explicado-que-es-y-como-agregar-a-tu-repositorio/)
> [.gitignore cheat sheet](https://gist.github.com/jstnlvns/ebaa046fae16543cc9efc7f24bcd0e31)
