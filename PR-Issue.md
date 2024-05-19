# 💫 Pull Request (PR) e Issues
## 📜 Introducción a las PRs
Una pull request es un mecanismo utilizado en plataformas de control de versiones como GitHub, Bitbucket y GitLab para solicitar que los cambios realizados en una rama de un repositorio sean mergeados en otra rama, generalmente la rama principal o master. Este proceso permite a los colaboradores de un proyecto contribuir con sus modificaciones, mejoras o correcciones de errores de manera organizada y revisada por otros miembros del equipo antes de ser incorporadas al código base principal.

## 💐 Creación de PRs
### Pull Request en un proyecto ajeno
1. Buscamos info de cómo contribuir en el archivo Contributing
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
1. Buscamos info de cómo contribuir en el archivo Contributing
2. Clonamos el repositorio en local con `git clone url`
3. Creamos una rama nueva según la metodología que utilicen en el proyecto y nos movemos a esa rama con `git switch -c nombreRama` o creamos una rama a partir de una en específico **situándonos en la rama que queremos copiar** y haciendo `git checkout -b nombreRama`
4. Hacemos todos los cambios que queramos y hacemos un `git status` para saber que hemos hecho todos los cambios que queríamos
5. Commiteamos los cambios en la rama con el mensaje siguiendo el estilo del propio repositorio
6. Hacemos `git push origin nombreRama` para subir la rama
7. Desde GitHub situándonos en la rama nueva podemos hacer click tanto en **Compare & Pull Request** como en **Contribute > Open Pull Request**
8. Ahora vemos un formulario donde podemos poner el nombre de la PR, al igual que una descripción donde podemos añadir texto, enlaces e imágenes. También se pueden añadir reviewers, assigners, labels...
9. Cuando acabemos, hacemos click en **Create pull request**

</hr>

## 📜 Introducción a las Issues
Una Issue es una herramienta utilizada para rastrear tareas, mejoras, errores y discusiones dentro de un proyecto de software. Es un componente esencial del flujo de trabajo colaborativo en GitHub, permitiendo a los usuarios comunicar problemas, proponer nuevas características o documentar tareas que necesitan ser realizadas.

Cada issue tiene un título que proporciona un resumen breve del problema o tarea, y una descripción detallada que ofrece más contexto, pasos para reproducir un error, capturas de pantalla, o cualquier otra información relevante. Las issues permiten discusiones colaborativas. Los miembros del proyecto pueden comentar para clarificar detalles, sugerir soluciones, o proporcionar actualizaciones.

### Usos Comunes de las Issues
- **Reporte de Errores:** Los usuarios pueden reportar bugs detallando los síntomas y cómo reproducir el problema.
- **Solicitudes de Características:** Los usuarios o colaboradores pueden proponer nuevas funcionalidades o mejoras.
- **Tareas y Pendientes:** Pueden utilizarse para documentar y asignar tareas específicas dentro del proyecto.
- **Discusión y Planificación:** Facilitan la comunicación y colaboración entre los miembros del proyecto para planificar futuras actualizaciones y cambios.

### Ventajas de Utilizar Issues en GitHub
- **Colaboración** Eficaz: Facilita la comunicación y colaboración entre los miembros del equipo.
- **Organización**: Ayuda a organizar y priorizar tareas y problemas.
- **Trazabilidad**: Proporciona un historial claro de decisiones y cambios en el proyecto.
- **Transparencia**: Permite a todos los colaboradores y usuarios ver el estado y progreso de diferentes aspectos del proyecto.

## 💐 Creación de Issues
Para crear una Issue debemos seguir los siguientes pasos:
1. Ve al repositorio donde deseas crear la issue.
2. Haz clic en la pestaña "Issues" en la página principal del repositorio.
3. Haz clic en el botón "New issue" para empezar a crear una nueva Issue.
4. Completa los detalles:
      - Título: Añade un título claro y conciso.
      - Descripción: Describe detalladamente la issue, incluyendo pasos para reproducir, si es necesario.
      - Etiquetas (opcional): Añade etiquetas para categorizar la issue.
5. Asigna la issue a una persona específica si es necesario.
6. Haz clic en "Submit new issue" para crear la Issue.
7. Comenta, cierra o reabre la issue según sea necesario.

## 😇 Buenas prácticas
A la hora de hacer PRs o Issues es importante saber estas buenas prácticas:
### PRs
1. Utilizar siempre mensajes de commits que vayan acordes con el estilo de los del repositorio.
2. En la descripción, añadir formatos de check como:
```
Tareas realizadas en esta PR:
- [x] Explicación breve de la tarea
```
3. Para hacer referencia a la resolución de una issue del repositorio, puedes hacerlo con `#númeroIssue`. Si se menciona una Issue en una PR, en la Issue aparecerá también una referencia a la PR que la menciona:
```
NombrePersona mentioned this issue #numeroIssue X time ago
Mensaje commit
X tasks
```
4. A la hora de hacer una PR tenemos que revisar lo siguiente:
      - Criterios de aceptación y que la tarea que teníamos se haya completado correctamente
      - Efectos secundarios como bugs
      - Legibilidad del código
      - Mantenibilidad y escalabilidad
      - Consistencia para que el código cumpla con los estándares de estilo definidos en el proyecto
      - Performance para verificar que el código esté optimizado
      - Manejo de excepciones
      - Simplicidad
      - Pruebas para verificar que no se rompa ningún test del código
5. A la hora de hacer un code review de una PR es importante:
      - Juzgar al código, no al desarrollador
      - Preguntar, no dar órdenes
      - Responder todos los comentarios o preguntas que te hayan hecho
      - Tratar a la gente con respeto
6. En las PRs podemos ir a **"Files changed"** y al darle al botón de la ruedita, podemos ver en qué formato de diff vamos a ver los cambios, personalmente a mí me gusta más el "Split"
7. Los números que se ven a la derecha de la PR que indican el total de líneas creadas y eliminadas se llaman "delta". Es una buena práctica que el delta de una PR no supere las 200 líneas, ya que más de 200 líneas son difíciles de revisar.
8. En una PR también podemos crear verificaciones especiales en el apartado de **"Checks"**. Con las verificaciones podemos limitar la posibilidad de hacer merge del PR. Estas verificaciones pueden ser checks de que todos los tests unitarios funcionan, y si hay alguno que falla, se bloquee el merge; también podemos verificar que el build del proyecto se ejecuta sin errores o que el código cumpla con ciertos estándares.
9.  Un buen esqueleto de la descripción de una PR es el siguiente:
```
## Descripción
Descripción breve de la tarea o tareas a realizar

## Problemas solucionados (si corresponde)
Descipción breve del problema que se ha solucionado

## Cambios propuestos
Descripción breve de lo que has hecho en la PR

## Capturas de pantalla (si corresponde)
"Estado inicial:"
imagen1

"Estado final:"
imagen2

## Comprobación de cambios:
- [x] He revisado que no haya ninguna PR (pull request) ya abierta con un problema similar, siguiendo el apartado de buenas prácticas
- [x] He revisado localmente los cambios para asegurarme de que no haya errores ni problemas.
- [x] He probado estos cambios en múltiples dispositivos y navegadores para asegurarme de que la landing page se vea y funcione correctamente.
- [x] He actualizado la documentación, si corresponde.

## Contexto adicional (si corresponde)
Enlace, recurso o explicación que pueda ser de utilidad

## Enlaces útiles (si corresponde)
Enlace de interés para ampliación 
```
### Issues
1. Si mencionamos a una Issue en una PR, podemos ir a la Issue y seleccionar la opción "Add page subtitle" en el apartado de "Development". De esta forma, cuando se cierre la PR, automáticamente también se cerrará la Issue.
2. Para crear una plantilla orientativa que le aparezca a cualquier persona que quiera crear una Issue, tenemos que ir a `Settings`, buscar `Features > Issues` y darle al botón de `Set up templates`. Ahora podremos elegir una o varias opciones entre: "Bug report", "Feature request" o "Custom template". Si elegimos "Custom template", podemos darle a `Preview and edit` para modificarla o a `Add template: select` para seleccionar otra de las anteriores opciones. Si le damos al primer botón de `Preview and edit`, le tenemos que dar al icono de lápiz para editar y luego añadir lo que se quiera.
3. Para deshabilitar las Issues, tenemos que ir a `Settings > Features > Issues` y dejar sin el check al apartado de "Issues"
### PRs e Issues
1. Para crear una nueva etiqueta personalizada, debemos seguir estos pasos:
      1. Haz clic en el apartado de "Labels" en el panel derecho dentro de una PR.
      2. En el buscador, escribe el nombre de la etiqueta que deseas crear.
      3. Selecciona la opción "Create new label 'nombreLabel'".
      4. Se abrirá un pequeño popup donde podrás asignar un nombre, una descripción y un color a la nueva etiqueta.
      5. Una vez completado, haz clic en el botón "Save".