# FAQ Git pour developpez.com

## 7.3.1 Initialisation d'un dépôt

### Comment initialiser un dépôt ?

```bash
$ cd /home/user/dev/projet-toto
$ git init
Initialized empty Git repository in /home/user/dev/projet-toto/.git/
```

Initialise un dépôt dans le répertoire courant. Le dépôt est composé du répertoire `.git` contenant les méta-data du dépôt et la working directory.

### Comment initialiser un dépôt nu (*bare repository*) ?

```bash
git init --bare
```

Un dépôt nu ne contient pas de working directory. On ne peut donc pas travailler (créer des commits etc ...) avec. Il sert seulement à partager son travail (utilisé comme source pour les autres). Généralement les bare dépôt sont créés par des outils web comme GitHub ou GitLab pour centraliser le travail entre développeurs et faciliter la collaboration via diverses fonctionnalités (gestion des issues, des milestones, etc ...)

### Comment cloner un dépôt ?

```bash
git clone <url>
```

Où `<url>` est l'url du dépôt Git à cloner.

### Comment connaitre l'état du dépôt ?

Indique sur quelle branche on se trouve actuellement et donne l'état de la working directory.

Par exemple avec une working directory propre :

```bash
$ git status
# On branch master
nothing to commit, working directory clean
```

Autre exemple avec une working directory contenant des modifications en cours :

```bash
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#      modified:   index.html
#
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#
#      modified:   lib/simplegit.rb
#
```

Dans cet exemple le fichier `index.html` a été modifié et a été indexé pour être embarqué dans le prochain commit. Le fichier `lib/simplegit.rb` a été modifié mais n'est pas indexé.
