# 💫 Pull Request (PR)
## 📜 Introducción
Una pull request es un mecanismo utilizado en plataformas de control de versiones como GitHub, Bitbucket y GitLab para solicitar que los cambios realizados en una rama de un repositorio sean mergeados en otra rama, generalmente la rama principal o master. Este proceso permite a los colaboradores de un proyecto contribuir con sus modificaciones, mejoras o correcciones de errores de manera organizada y revisada por otros miembros del equipo antes de ser incorporadas al código base principal.

## 😇 Buenas prácticas
A la hora de hacer PRs, es importante saber estas buenas prácticas:
1. Utilizar siempre mensajes de commits que vayan acordes con el estilo de los del repositorio.
2. En la descripción, añadir formatos de check como:
```
Tareas realizadas en esta PR:
- [x] Explicación breve de la tarea
```
3. Para hacer referencia a la resolución de una issue del repositorio, puedes hacerlo con `#númeroIssue`
4. Para crear una nueva etiqueta personalizada para las Pull Requests (PRs), sigue estos pasos:
      1. Haz clic en el apartado de "Labels" en el panel derecho dentro de una PR.
      2. En el buscador, escribe el nombre de la etiqueta que deseas crear.
      3. Selecciona la opción "Create new label 'nombreLabel'".
      4. Se abrirá un pequeño popup donde podrás asignar un nombre, una descripción y un color a la nueva etiqueta.
      5. Una vez completado, haz clic en el botón "Save".
5. Un buen esqueleto de la descripción de una PR es el siguiente:
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