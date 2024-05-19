# 📚 Todo sobre los commits
## 📜 Introducción
Un commit en Git es una instantánea de los cambios realizados en un proyecto que se almacena en el repositorio local. Es la base principal del trabajo con Git, ya que permite guardar cualquier cambio realizado en el proyecto. Los commits son esenciales para el control de versiones y por eso, cada commit en Git tiene asociado un mensaje que describe los cambios realizados. Estos mensajes son importantes porque ayudan a otros colaboradores (y a ti mismo en el futuro) a entender qué cambios se hicieron y por qué se realizaron.

Los commits en Git crean una "línea de tiempo" que muestra cómo ha evolucionado el proyecto. Puedes revisar los commits anteriores, deshacer cambios, comparar versiones anteriores del proyecto y colaborar con otros desarrolladores mediante el uso de commits en Git.

## 🔎 Ver nuestros commits
Si hacemos `git log --stat` nos aparece el historial de commits de un repositorio donde podemos ver información y las partes de un commit desde la consola:

```
commit 62b08e33f9da97f39539162ff13965b2147c5de9 (HEAD -> main, tag: v1.0.0)
Author: Cristina Correa <cristina.correa.segade@gmail.com>
Date:   Tue Mar 19 04:41:25 2024 +0100

    Primera versión del proyecto completa

 app/index.html | 11 +++++++++++
 app/script.js  |  1 +
 2 files changed, 12 insertions(+)


commit 90f68918395452098b50ec00b2ebb0cdcfd0ed2d
Author: Cristina Correa <cristina.correa.segade@gmail.com>
Date:   Tue Mar 19 04:38:40 2024 +0100

    Primer commit: inicio del repositorio

 app/style.css  | 0
 app/index.html | 0
 app/script.js  | 0
 prueba.docx    | 1 +
 prueba.md      | 0
 prueba.txt     | 1 +
 6 files changed, 2 insertions(+)
```

## 🗂️ Partes de los commits
En este repositorio podemos ver dos commits. Y vamos a analizar sus partes:
- **El hash**: Es el identificador único de un commit y se utiliza para referenciar específicamente ese commit. Tanto "62b08e33f9da97f39539162ff13965b2147c5de9" como "90f68918395452098b50ec00b2ebb0cdcfd0ed2d" son hashes de sus respectivos commits. Estos son cadenas de caracteres hexadecimales generadas mediante un algoritmo criptográfico seguro que permite reducir la posibilidad de que un atacante en algún momento pueda modificar de forma maligna el código fuente a partir del repositorio. También hay una versión reducida del hash que veremos más adelante.
- **El HEAD**: Es la parte de "(HEAD -> main, tag: v1.0.0)". "HEAD" quiere decir que este es el commit que tenemos ahora mismo en nuestro directorio de trabajo, que está apuntando a la rama "main" que es en la que nos encontramos y que en este commit existe una tag llamada "v1.0.0".
- **Los datos del autor**: Es el nombre y el email de la persona que hizo el comit. Es decir, los valores que ha guardado el autor del commit en su configuración global de git como "username" y "email".
- **La fecha del commit**: Es la fecha en formato "DíaSemana Mes DíaNumérico Hora:Minuto:Segundo Año FranjaHoraria" de cuando se hizo ese commit
- **El mensaje**: Es el mensaje que guardamos al hacer el commit que es informativo y nos ayuda a entender qué hemos hecho.
- **Snapshot del Proyecto**: Cada commit es una instantánea del estado del proyecto en un momento específico. Esto incluye todos los archivos que han sido modificados, añadidos o eliminados desde el último commit.

Si hacemos `git log --oneline` podemos ver una versión reducida en una línea del histórico de los commits donde solo aparece el hash reducido, a dónde apunta el head, las tags y el mensaje del commit:
```
62b08e3 (HEAD -> master, tag: v1.0.0) Primera versión del proyecto completa
90f6891 Primer commit: inicio del repositorio
```
## ✉ Buenas prácticas para los mensajes de commit
1. Los mensajes tienen que describir los cambios que estamos introduciendo en la nueva versión del código
2. Según la documentación de Git, los mensajes de los commits tienen **título**, que resume los cambios realizados en el commit, y una **descripción** detallada, aunque la descripción no siempre es necesaria. Si se utiliza una descripción, se deben de separa los párrafos con una línea en blanco.
```
This is a short commit subject

This paragraph contains details about the changes 
and should be added only if needed, most of the 
times a single line commit message is enough.
```
3. Según la documentación de Git, no se deben utilizar más de 50 caracteres en el título de un commit. Sin embargo, en GitHub, los mensajes de commit pueden visualizarse con hasta aproximadamente 70 caracteres; si se excede este límite, el mensaje se cortará y se mostrará con `...`.
4. El mensaje debe de responder a las preguntas ¿Qué? y ¿Por qué? ya que la pregunta ¿Cómo? se debería de responder viendo nuestro código.
```
✅ add event tracking to collect information about user interaction
❌ add data-trackId property to button element
```
5. Los verbos deben de estar en imperativo para ser compatibles con los mensajes que Git genera automáticamente al hacer un merge, revert.
```
✅ fix header transition on mobile
❌ fixed header transition on mobile
```
6. Es correcto hacer todos los commits en inglés ya que es el estándar y no dará ningún problema a la hora de ver tiles o "ñ"

### Definiciones de estilos
Para crear un log que es fácil de navegar y mejorar la mantenibilidad del proyecto, hay aspectos que también se deben de definir a la hora de escribir los mensajes de los commits:
- Si se debería de poner un punto "." al final del commit o no
- Si se debería de empezar con mayúsculas o minúsculas
- La estructura que va a seguir el mensaje