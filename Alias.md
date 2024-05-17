# 🥸 Alias en Git
Los alias en Git son atajos personalizados que permiten reemplazar comandos largos de Git con versiones más cortas, facilitando y acelerando el flujo de trabajo. Se crean utilizando el comando git config, que modifica los archivos de configuración de Git, donde se almacenan configuraciones específicas del usuario y del proyecto 35.

1. **Para crear un alias, se utiliza el siguiente comando:**
- `git config [--global] alias.NombreAlias "Comando"`
> [!NOTE]
> Si se incluye --global, el alias se aplicará a todos los repositorios en tu sistema; de lo contrario, se aplicará solo al repositorio actual
2. **Para ver los alias que has creado, puedes usar:**
- `git config --get-regexp alias`

3. **Para editar un alias**, simplemente crea uno nuevo con el mismo nombre, y el antiguo será reemplazado.
4. **Para borrar un alias**, puedes usar el comando:
- `git config --unset NombreAlias` 

> [!WARNING]
> Al crear alias, es importante tener cuidado con los nombres de los alias para evitar conflictos con comandos existentes de Git. Además, asegúrate de que los alias no sean demasiado similares a los comandos de Git existentes, ya que esto podría causar confusión. También es recomendable documentar los alias que creas para ti mismo o para tu equipo, especialmente si se utilizan en un entorno de trabajo compartido 345.
> 
> Al crear un alias hay que tener en cuenta que se debe de poner el comando sin el `git`, por ejemplo para hacer un alias llamado "ss" de "git status --short", deberías poner `git config --global alias.ss "status --short"`


## 🕵‍♀ Alias que utilizo
```
[alias]
	dfc = diff --color-words='[^[:space:]]'
	lg = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
	lgd = log --date-order --date=iso --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)%ad%x08%x08%x08%x08%x08%x08%x08%x08%x08%x08%x08%x08%x08%x08%x08 %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
	sts = status --short
	stsb = status -sb
```
> [!NOTE]
> - El alias **lg** usa la fecha relativa que muestra los commits en el orden predeterminado de Git y te dice hace cuanto se hizo el commit.
> - El alias **lgd** usa la fecha absoluta que ordena los commits cronológicamente en formato ISO (AAAA-MM-DD).

## 📍 Otros alias interesantes
```
[alias]
      	aa = add -A .
       	aacm = !git add -A . && git commit
      	aacm = !git add -A . && git commit -m
      	amend = commit --amend -m
      	br = branch
       	brd = branch -d
      	brD = branch -D
      	cm = commit -m
      	co = checkout **//** co = fetch && checkout
      	cob = checkout -b
        com = !f(){ git checkout $(git main) $@;}; f
      	coo = !git fetch && git checkout
        coom = !f() { git fetch origin master:\"$1\"; git checkout \"$1\";}; f
      	cp = cherry-pick
      	dev = !git checkout dev && git pull origin dev
				dfc = diff --color-words='[^[:space:]]'
        dl = !git ll -1
        dlc = diff --cached HEAD^
        dmerged = !git branch --merged | grep -v '\*' | xargs -n 1 git branch -d
       	f = "!git ls-files | grep -i"
        fl = log -u
      	gr = grep -Ii
        ignore_python = !wget -O ./.gitignore https://raw.githubusercontent.com/github/gitignore/master/Python.gitignore
      	la = !git config -l | grep alias | cut -c 7-
        ld = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=relative
        lds = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short
        le = log --oneline --decorate
      	ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
        lnc = log --pretty=format:"%h\\ %s\\ [%cn]"
      	ls = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate
      	main = !git checkout main && git pull origin **//** main = !git symbolic-ref refs/remotes/origin/HEAD | cut -d'/' -f4
      	master = !git checkout master && git pull origin 
      	merged = branch --merged
        pend = cherry -v origin/master
       	plo = pull origin
      	plod = pull origin dev
      	ploh = pull origin HEAD
      	plom = pull origin main
      	plos = pull origin staging
      	po = push origin
      	pod = push origin dev
      	pogm = !git push origin gh-pages && git checkout master && git pull origin master && git rebase gh-pages && git push origin master && git checkout gh-pages
      	poh = push origin HEAD
        pom = push origin main
      	pomg = !git push origin master && git checkout gh-pages && git pull origin gh-pages && git rebase master && git push origin gh-pages && git checkout master
      	pos = push origin staging
      	pu = !git push origin `git branch --show-current`
				prefab = cherry -v origin/fabrication
        redate = rebase --committer-date-is-author-date
				serve = !git daemon --reuseaddr --verbose --base-path=. --export-all ./.git
      	st = status
				stsb = status -sb
      	staging = !git checkout staging && git pull origin staging
      	unstage = reset --soft HEAD^
```
> [!NOTE]
> Estos alias pueden encontrarse en:
> - [Repo de @johnpolacek](https://gist.github.com/johnpolacek/69604a1f6861129ef088)
> - [Must Have Git Aliases: Advanced Examples](https://www.durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/)
