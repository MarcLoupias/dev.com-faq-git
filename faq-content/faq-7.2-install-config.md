# FAQ Git pour developpez.com

## 7.2 Installation et configuration

### Comment installer Git sur Windows ?

Téléchargez le client Git approprié depuis [la page officielle](https://git-scm.com/downloads), lancez l'installeur et suivez les instructions.

### Comment installer Git sur macOS ?

Il existe plusieurs façons d'installer Git sous macOS.

* La première façon consiste à installer XCode qui inclut Git (Apple Git-xy). Depuis un terminal, saisir la ligne de commande => `$ xcode-select --install`.
* La deuxième façon consiste à utiliser [git-osx-install](https://sourceforge.net/projects/git-osx-installer/). Téléchargez le fichier .dmg et lancez l'installation en suivant les instructions.
* La troisième façon consiste à utiliser [Homebrew](https://brew.sh/index_fr). En supposant que [Homebrew](https://brew.sh/index_fr) soit installé, depuis un terminal saisir la ligne de commande => `$ brew install git`.

### Comment connaitre la liste des commandes Git ?

```bash
$ git help
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

```bash
$ git version
git version 2.19.1
```

### Quels sont les fichiers de configuration de Git ?

Les fichiers de configuration de Git sont les suivants (l'ordre ci-dessous correspond à l'ordre de lecture par Git, la dernière valeur lue est la valeur prise en compte) :

1. `C:\ProgramData\Git\config`
2. system config (e.g. `C:\Program Files\Git\mingw64\etc\gitconfig`)
3. global config (`%HOMEPATH%\.gitconfig`)
4. local config (repository-specific `.git/config`)

### Comment afficher la configuration courante de Git ?

```bash
$ git config --list
user.name=marlou
user.email=pro@marc-loupias.fr
core.autocrlf=false
core.excludesfile=/home/marco/.gitignore_global
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
remote.origin.url=https://github.com/MarcLoupias/dev.com-faq-git.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.master.remote=origin
branch.master.merge=refs/heads/master
```

L'option `--show-origin` permet d'afficher en face d'une option dans quel fichier de configuration la configuration est définie.

```bash
$ git config --list --show-origin
file:/home/marco/.gitconfig     user.name=marlou
file:/home/marco/.gitconfig     user.email=pro@marc-loupias.fr
file:/home/marco/.gitconfig     core.autocrlf=false
file:/home/marco/.gitconfig     core.excludesfile=/home/marco/.gitignore_global
file:.git/config        core.repositoryformatversion=0
file:.git/config        core.filemode=true
file:.git/config        core.bare=false
file:.git/config        core.logallrefupdates=true
file:.git/config        remote.origin.url=https://github.com/MarcLoupias/dev.com-faq-git.git
file:.git/config        remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
file:.git/config        branch.master.remote=origin
file:.git/config        branch.master.merge=refs/heads/master

```

### Comment exclure des fichiers ?

Il existe 3 manières d'exclure des fichiers du champ de Git :

Par projet: créer un fichier `.gitignore` dans le dépôt

Par dépôt: dans le fichier `.git/info/excludes`

Par machine : au travers de la configuration utilisateur dans `~/.gitconfig`

### Comment changer son nom d'utilisateur ?

```bash
git config --global user.name "votre nom"
```

### Comment changer son email ?

```bash
git config --global user.email moi@domaine.tld
```

### Comment changer l'URL d'un dépôt distant ?

```bash
$ git remote set-url origin https://domaine.tld/repo.git
# ou
$ git remote add origin https://domaine.tld/repo.git
```

A pour effet de changer l'url pour le `fetch` et pour le `push`.

Pour limiter l'effet du changement à la `push` url uniquement, ajouter l'option `--push` :

```bash
git remote set-url --push origin https://domain.tld/repo.git
```

Notez l'absence d'une option `-fetch` pour changer la `fetch` url. Lorsque l'upstream de `pull` et l'upstream de `push` sont différents, il est recommandé d'avoir des alias différents pour les remotes plutôt qu'un seul alias avec 2 urls différentes.
