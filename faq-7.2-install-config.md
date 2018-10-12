# FAQ Git pour developpez.com

## 7.2 Installation et configuration

### Comment installer Git sur Windows ?

Téléchargez le client git approprié depuis [la page officielle](https://git-scm.com/downloads), lancez l'installeur et suivez les instructions.

### Comment connaitre la liste des commandes Git ?

```
$ git help
```

Donne comme sortie :

```
usage: git [--version] [--help] [-C <path>] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Reapply commits on top of another base tip
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.

```

### Comment connaitre la version de votre Git ?

```
$ git version
```

### Quels sont les fichiers de configuration de Git ?

Les fichiers de configuration de git sont les suivants (l'ordre ci-dessous correspond à l'ordre de lecture par git, la dernière valeur lue est la valeur prise en compte) :

1. `C:\ProgramData\Git\config`
2. system config (e.g. `C:\Program Files\Git\mingw64\etc\gitconfig`)
3. global config (`%HOMEPATH%\.gitconfig`)
4. local config (repository-specific `.git/config`)

### Comment afficher la configuration courante de Git ?

```
$ git config --list
```

Affiche la configuration sous cette forme : 

```
core.symlinks=false
core.autocrlf=true
core.fscache=true
color.diff=auto
color.status=auto
color.branch=auto
color.interactive=true
help.format=html
```

L'option `--show-origin` permet d'afficher en face d'une option dans quel fichier de configuration la configuration est définie.

```
$ git config --list --show-origin
```

Donne en sortie :

```
file:"C:\\ProgramData/Git/config"       core.symlinks=false
file:"C:\\ProgramData/Git/config"       core.autocrlf=true
file:"C:\\ProgramData/Git/config"       core.fscache=true
file:"C:\\ProgramData/Git/config"       color.diff=auto
file:"C:\\ProgramData/Git/config"       color.status=auto
file:"C:\\ProgramData/Git/config"       color.branch=auto
file:"C:\\ProgramData/Git/config"       color.interactive=true
file:"C:\\ProgramData/Git/config"       help.format=html
file:"C:\\ProgramData/Git/config"       http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
file:"C:\\ProgramData/Git/config"       diff.astextplain.textconv=astextplain
file:"C:\\ProgramData/Git/config"       rebase.autosquash=true
file:"C:\\Program Files\\Git\\mingw64/etc/gitconfig"    credential.helper=manager
file:C:/Users/robert/.gitconfig  user.name=rob
file:C:/Users/robert/.gitconfig  user.email=me@robert.tld
file:C:/Users/robert/.gitconfig  core.autocrlf=false
file:.git/config        core.repositoryformatversion=0
file:.git/config        core.filemode=false
file:.git/config        core.bare=false
```

### Comment exclure des fichiers ?

Il existe 3 manières d'exclure des fichiers du champ de git :

Par projet: créer un fichier `.gitignore` dans le dépôt

Par dépôt: dans le fichier `.git/info/excludes`

Par machine : au travers de la configuration utilisateur dans `~/.gitconfig`

### Comment changer son nom d'utilisateur ?

```
$ git config --global user.name "Your Name Comes Here"
```

### Comment changer son email ? 

```
$ git config --global user.email you@yourdomain.example.com
```

### Comment changer l'URL d'un dépôt distant ?

```
$ git remote set-url origin https://domain.tld/repo.git
# ou
$ git remote add origin https://domain.tld/repo.git
```

A pour effet de changer l'url pour le `fetch` et pour le `push`.

Pour limiter l'effet du changement à la `push` url uniquement, ajouter l'option `--push` :

```
$ git remote set-url --push origin https://domain.tld/repo.git
```

Notez l'absence d'une option `-fetch` pour changer la `fetch` url. Lorsque l'upstream de `pull` et l'upstream de `push` sont différents, il est recommandé d'avoir des alias différents pour les remotes plutôt qu'un seul alias avec 2 urls différentes.
