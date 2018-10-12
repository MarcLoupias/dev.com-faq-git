# FAQ GIT pour developpez.com

## 7.3.5 Les commits

### Qu'est ce qu'un commit ?

Un commit est une révision du code source. Il est identifié par une empreinte numérique générée par une fonction de hachage (algorithme SHA-1).

Un commit est composé de meta-données et du contenu (le code source) à versionner.

Les meta-données sont :

  - le message de commit
  - le committer (l'utilisateur qui a créé le commit)
  - la date de création du commit (Au format `RFC2822` par défaut, par exemple : `Tue Oct 9 00:58:43 2018 +0200`)
  - l'auteur (l'utilisateur qui a créé le contenu du commit)
  - la date de création du contenu (Au format `RFC2822`)
  - l'identifiant (SHA1 donc) du commit parent (avec 2 exceptions, si vous créez le premier commit du dépôt alors il n'y a pas de parents, et s'il s'agit d'un commit de merge alors il en a deux)

Sans rentrer dans les détails internes du fonctionnement de git, retenez simplement que par 'contenu' on entend à la fois les modifications
ajoutées à la zone de staging (index) et également les fichiers et répertoires non-modifiés. 

L'empreinte numérique est appliquée sur les meta-données ET le contenu.

Ainsi un commit bénéficie des propriétés des empreintes numériques :

  - c'est rapide
  - deux commits différents ne peuvent pas avoir le même identifiant
  - il n'est pas possible de modifier les méta données ou le contenu d'un commit sans modifier son identifiant

Pour plus de détails, on peut se référer à [la documentation officielle](https://git-scm.com/book/fr/v2/Les-tripes-de-Git-Plomberie-et-porcelaine) ou à [un tutoriel sur developpez.com](https://alm.developpez.com/tutoriel/fonctionnement-interne-de-git/).

### Comment créer un commit ?

Il est nécessaire d'avoir au préalable ajouté des fichiers à l'index (zone de staging).

```
$ git commit
```

Utilisée seule elle permet d'ouvrir l'éditeur de texte de votre CLI (vim sous Windows via git bash, nano sous Ubuntu par exemple) afin d'y
saisir le message de commit.

Si aucun fichier n'a été ajouté à l'index, il est possible de passer l'option `-a` qui demande à git de prendre tous les fichiers modifiés présents dans la working directory.

Une utilisation courante des options est : `git commit -am "message de commit"` ce qui permet de prendre toutes les modifications en cours et d'ajouter un message de commit dans le même temps.

### Comment ajouter un message en créant un commit ?

L'option `-m` permet d'ajouter un message.

Par exemple : 

```
$ git commit -m "message de commit"
```

### Comment modifier le message d'un commit existant ?

```
$ git commit --amend -m "nouveau message de commit"
```

Comme expliqué dans la première question, ceci a pour effet de modifier le sha1 du commit.

### Comment supprimer le dernier commit de la branche courante sans perdre les modifications ?

```
$ git reset --soft HEAD^
```

Les modifications qui étaient présentes dans le commit supprimé sont encore présente dans l'index.

### Comment supprimer le dernier commit de la branche courante avec les modifications ?

```
$ git reset --hard HEAD^
```

Les modifications qui étaient présentes dans le commit supprimé sont supprimées.

### Comment supprimer les "n" derniers commits de la branche courante sans perdre les modifications ?

```
$ git reset --soft HEAD~3
```

Les 3 derniers commits sont supprimés. Les modifications des 3 derniers commits sont présentes dans l'index.

### Comment supprimer les "n" derniers commits de la branche courante avec les modifications ?

```
$ git reset --hard HEAD~3
```

Les 3 derniers commits sont supprimés et les modifications qu'ils comportaient le sont avec. 

### Comment ajouter un commit d'une branche A dans une branche B sans effectuer un merge ? (cherry-pick)

Vous devez avoir checkout la branche de destination, puis vous exécutez un cherry-pick en lui passant en paramètre le hash du commit désiré.

Par exemple pour ajouter le commit `1234abcd` à la branche `master` :

```
$ git checkout master
$ git cherry-pick 1234abcd
```

### Comment ajouter un commit provenant d'une branche d'un autre repository à la branche courante de ce repository ? (cherry-pick)

L'astuce consiste à ajouter le repository source en tant que `remote` du repository courant et à `fetch` (et seulement `fetch`) ses branches.

Par exemple pour ajouter à `master` le commit `1234abcd` existant sur le repository `boubou` de l'utilisateur `toto` la marche à suivre est la suivante : 

```
$ git remote add boubou git://github.com/toto/boubou.git
$ git fetch boubou
$ git checkout master
$ git cherry-pick 1234abcd
```

### Comment annuler un commit existant ? (revert)

C'est la bonne manière d'annuler un commit existant dans un historique qui a été publié. En effet une pratique essentielle est de ne jamais réécrire ou supprimer
un historique qui a été publié et qui a donc pu être récupéré par un autre utilisateur.

Le `revert` ne supprime rien, il crée un nouveau commit qui est un miroir inverse du commit source.

```
$ git revert 1234abcd
```

Cette commande ajoute à la branche courante un nouveau commit qui sera l'exact inverse du commit `1234abcd`.

