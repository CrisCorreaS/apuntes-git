# Archivo .gitconfig
## Configuraciones estéticas
### General
- `git config --global color.ui true` → Habilita el colorido de la interfaz de usuario de Git en general.
> ```
> [color]
>   ui = true
> ```
### git diff
- `git config --global color.diff auto` → Controla si Git va a mostrar las diferencias entre archivos en color cuando se visualicen cambios entre diferentes versiones de archivos. Habilita el colorido para la salida de las diferencias (diff) entre archivos. Cuando visualicemos diferencias de archivos con git diff, Git usará colores.
- `git config color.diff.parteDiff "colorLetra colorFondo tipoLetra"` → Establece una de las partes del diff (context, plain, meta, frag, func, old, new, whitespace, oldMoved, newMoved...) con un color y una forma específica. Por ejemplo: `git config color.diff.new "green black bold"`
> [!NOTE]
> Con estos comandos, cuando vemos el archivo de configuración nos debería de aparecer algo parecido a esto pero con los colores que queramos:
> ```
> [color]
> 	diff = auto
> 
> [color "diff"]
> 	meta = yellow bold
> 	frag = magenta bold
> 	old = red bold
> 	new = green bold
> ```
### git status
- `git config --global color.status auto` → Habilita el colorido para la salida del estado de los archivos en tu repositorio. Cuando ejecutes git status, Git mostrará información con colores.
- `git config color.status.estadoFichero "colorLetra colorFondo tipoLetra"` → Establece uno de los estados de los ficheros (Added, Changed, Untracked o Deleted) con un color y una forma específica. Por ejemplo: `git config color.status.untracked "141 bold"`
> [!NOTE]
> Con estos comandos, cuando vemos el archivo de configuración nos debería de aparecer algo parecido a esto pero con los colores que queramos:
> ```
> [color]
>   status = auto
>
> [color "status"]
>   added = green
>   changed = blue
>   untracked = magenta
>   deleted = red
> ```
### git branch
- `git config --global color.branch auto` →  Define si Git resaltará los cambios en la salida de git status y mostrará la información en color para hacerla más legible y distinguible.
- `git config color.branch.tipoRama "colorLetra colorFondo tipoLetra"` → Establece cada tipo de rama (current, local o remote) con un color y una forma específica. Por ejemplo: `git config color.branch.remote "magenta bold"`
> [!NOTE]
> Con estos comandos, cuando vemos el archivo de configuración nos debería de aparecer algo parecido a esto pero con los colores que queramos:
> ```
> [color]
>   branch = auto
>
> [color "branch"]
> 	current = normal cyan reverse
> 	local = 202
> 	remote = green bold
> ```

### Todas las configuraciones estéticas de mi .gitconfig
```
[color]
	ui = true
	diff = auto
	status = auto

[color "diff"]
	context = white dim
	meta = yellow
	frag = blue bold
	old = red bold
	new = green 
	
[color "status"]
	added = green bold
	changed = 208 bold
	untracked = red ul bold
```

> [!NOTE]
> - Para más información en general, puedes mirar este [link](https://git-scm.com/book/sv/v2/Customizing-Git-Git-Configuration)
> - Para más información en específico, puedes mirar este [link](https://git-scm.com/docs/git-config)
> - Para colores específicos, tanto de letras como de fondo, que no sean **normal, black, red, green, yellow, blue, magenta, cyan,** o **white**, podemos elegir los colores xterm-256. Un buen recurso para esto es copiar el "Xterm Number" del siguiente [link](https://www.ditig.com/publications/256-colors-cheat-sheet)
> - Los tipos de letra por ahora pueden ser lo siguientes: **bold, dim, ul, blink** y **reverse**. Donde: 
> 		- **bold** → es en negrita
>     - **dim** → es para que aparezca más atenuado en comparación con el texto normal. Esto es útil para despriorizar información menos importante.
>     - **ul** → es con subrayado
>     - **blink** → es para que parpadee. No es muy recomendable ni accesible
>     - **reverse** →  es para que aparezca el color del texto intercambiado con el del fondo.

## Configuraciones interesantes:
### En `core`
```
[core]
	editor = code --wait
	autocrlf = true
	whitespace = fix,-indent-with-non-tab,trailing-space,cr-at-eol
```
1. **Definición del editor por defecto** → Con `git config --global core.editor "code --wait"` definimos a VSCode como el editor de texto que se utilizará Git cuando necesite que el usuario ingrese un mensaje de confirmación o editar algún otro tipo de texto, como un merge o un mensaje de rebase interactivo. Es muy importante poner el `--wait` porque indica a VSCode que debe esperar hasta que el usuario haya terminado de editar el archivo antes de salir y permitir que el proceso de Git continúe. Esta opción es importante en el contexto de Git porque Git espera que el editor se cierre antes de proceder con la siguiente tarea.

2. **Convertir archivos automáticamente a CRLF** → Con `git config --global core.autocrlf true` conseguimos hacer una configuración necesaria únicamente en Windows. Gracias a esto podemos indicarle a Git que convierta automáticamente los retornos de carro (CR) al estilo de línea de Unix (LF) al hacer checkout y que los convierta de nuevo a retornos de carro al estilo de Windows (CRLF) al hacer commit. Un poco de contexto para entender mejor esto:
> La configuración de finales de línea (EOL) es importante en Git debido a las diferencias entre los sistemas operativos en la forma en que representan el final de una línea en un archivo de texto. Los diferentes sistemas operativos utilizan distintos caracteres de control para marcar el final de una línea:
> - **Windows**: Utiliza una secuencia de dos caracteres, CRLF (Carriage Return + Line Feed, \r\n).
> - **Unix/Linux/macOS**: Utiliza un solo carácter, LF (Line Feed, \n).
> 
> Diferentes estilos de fin de línea pueden causar conflictos innecesarios al fusionar ramas o aplicar parches, ya que Git puede detectar cambios en cada línea debido a las diferencias en los caracteres de fin de línea.

3. **Espacios en Blanco** → Con `git config --global core.whitespace "fix,-indent-with-non-tab,trailing-space,cr-at-eol"` podemos definir cómo Git debe manejar los problemas de espacio en blanco al trabajar con los archivos en el repositorio. Gracias a este comando, nos aseguramos de que Git intente corregir automáticamente los problemas comunes de espacio en blanco al trabajar con archivos en el repositorio. También ajusta cómo Git percibe ciertos aspectos del formato de código, como la indentación y los espacios al final de las líneas. Aquí está desglosada la configuración:
- `whitespace=fix`: Esta opción indica a Git que intente corregir automáticamente los problemas de espacio en blanco cuando sea posible. Por ejemplo, si hay espacios en blanco al final de una línea, Git intentará eliminarlos automáticamente.
- `-indent-with-non-tab`: El signo menos "-" delante de esta opción indica que Git no debe considerar la indentación con espacios en lugar de tabulaciones como un problema. A veces, los desarrolladores pueden preferir la indentación con espacios sobre las tabulaciones, por lo que esta opción evita que Git genere advertencias innecesarias al respecto.
- `trailing-space`: Elimina automáticamente los espacios en blanco al final de las líneas.
- `cr-at-eol`: Esta opción indica a Git que elimine automáticamente los caracteres de retorno de carro (CR) al final de las líneas. Los caracteres de retorno de carro pueden ser problemáticos en sistemas operativos que no los necesitan, como Linux o macOS.

### En `init`
```
[init]
	defaultBranch = main
```

1. **Nombre de la rama main por defecto**
Con `git config --global init.defaultBranch main` nos aseguramos de que cada vez que inicialicemos un repositorio con `git init` la rama que se cree se llame **main** en vez de **master**. Cuando creamos un repositorio en GitHub, la rama inicial ya se llama **main**, pero según qué versión de Git usemos, se iniciará con una rama **master**.