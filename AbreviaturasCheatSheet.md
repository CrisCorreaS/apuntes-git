# Abreviaturas de Git
Esta es una lista de algunas de las abreviaturas comunes utilizadas en Git, sus significados equivalentes y el contexto mas un ejemplo:

| Abreviatura | Significado     | Contexto                                                                                                                         | Ejemplo                                     |
| ----------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| -a          | --all           | Utilizado en varios comandos, como `git branch` y `git fetch`, para incluir todas las ramas, tanto locales como remotas.         | `git branch -a`                             |
| -a          | --annotated     | Utilizado en el comando `git tag`, para crear etiquetas anotadas.         | `git tag -a v1.2.0`                             |
| -b          | --branch        | Utilizado en comandos como `git checkout`, para crear una nueva rama.                                                            | `git checkout -b feature`                   |
| -c          | --continue      | Utilizado en comandos como `git rebase`, para continuar una operación interrumpida.                                              | `git rebase --continue`                     |
| -c          | --create      | Utilizado en comandos como `git switch`, para crear una nueva rama y cambiar a ella.                                              | `git switch -c feature2`                     |
| -C          | --reuse-message | Utilizado en comandos como `git commit`, para reutilizar el mensaje del commit anterior.                                         | `git commit -C HEAD~2`                      |
| -D          | --delete --force       | Utilizado en comandos como `git branch`, para forzar eliminación de una rama.                                                                 | `git branch -D feature`                     |
| -d          | --delete        | Utilizado en comandos como `git branch`, para eliminar una rama.                                                                 | `git branch -d feature`                     |
| -e          | --edit          | Utilizado en comandos como `git commit`, para editar el mensaje del commit en un editor de texto.                                | `git commit -e`                             |
| -f          | --force         | Utilizado en comandos como `git push`, para forzar la actualización remota.                                                      | `git push -f origin master`                 |
| -F          | --file          | Utilizado en comandos como `git commit`, para tomar el mensaje del commit de un archivo.                                         | `git commit -F commit_message.txt`          |
| -h          | --help          | Utilizado en todos los comandos, para mostrar la ayuda de ese comando.                                                           | `git commit -h`                             |
| -i          | --interactive   | Utilizado en comandos como `git rebase`, para iniciar una rebase interactiva.                                                    | `git rebase -i HEAD~3`                      |
| -M          | --move --force  | Utilizado en comandos como `git branch`, para renombrar una rama. Fuerza el cambio incluso si la nueva rama ya existe.           | `git branch -M main`                        |
| -m | --move | Usado en comandos como `git branch` para renombrar una rama. | `git branch -m master main` |
| -m          | --message       | Utilizado en comandos como `git commit`, para incluir un mensaje en el commit.                                                   | `git commit -m "actualización del archivo"` |
| -n          | --dry-run       | Utilizado en comandos como `git merge`, para simular la fusión sin realizarla realmente.                                         | `git merge -n feature`                      |
| -p          | --patch         | Utilizado en comandos como `git add`, para agregar cambios de manera interactiva.                                                | `git add -p`                                |
| -q          | --quiet         | Utilizado en comandos como `git clone`, para reducir la cantidad de información mostrada.                                        | `git clone -q repo.git`                     |
| -r          | --recursive       | Utilizado en comandos como `git rm`, para eliminar el contenido de una carpeta                                                              | `git rm -r log/`                             |
| -r          | --remotes       | Utilizado en comandos como `git branch`, para listar ramas remotas.                                                              | `git branch -r`                             |
| -s          | --short         | Utilizado en comandos como `git status`, para mostrar información de manera concisa.                                             | `git status -s`                             |
| -S          | --gpg-sign      | Utilizado en comandos como `git commit`, para firmar commits con GPG.                                                            | `git commit -S -m "commit firmado"`         |
| -t          | --tags          | Utilizado en comandos como `git push`, para incluir etiquetas en la operación.                                                   | `git push -t origin main`                   |
| -t          | --track        | Utilizado en comandos como `git branch` o `git switch`, para hacer un seguimiento.                                                   | `git branch -t feature origin/feature`                   |
| -u          | --set-upstream  | Utilizado en comandos como `git push`, para establecer una relación de seguimiento entre una rama local y su contraparte remota. | `git push -u origin main`                   |
| -v          | --verbose       | Utilizado en comandos como `git status`, para mostrar información detallada.                                                     | `git status -v`                             |
| -x          | --exec          | Utilizado en comandos como `git rebase`, para ejecutar un comando en cada commit.                                                | `git rebase -i HEAD~3 -x "make test"`       |
