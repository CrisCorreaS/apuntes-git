# Alias en Git
## Alias que utilizo

## Otros alias interesantes
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
        redate = rebase --committer-date-is-author-date
      	st = status
      	staging = !git checkout staging && git pull origin staging
      	unstage = reset --soft HEAD^
```
> [!NOTE]
> Estos alias pueden encontrarse en:
> - [Repo de @johnpolacek](https://gist.github.com/johnpolacek/69604a1f6861129ef088)
> - [Must Have Git Aliases: Advanced Examples](https://www.durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/)
