
A insérer ici :

https://alm.developpez.com/faq/scm


7. GIT

7.1 Généralités
- Qu'est ce que GIT ?
- Où trouver de la documentation pour GIT ?
- Où trouver le code source de GIT ?
- Quelles sont les différences entre un SCM centralisé comme Subversion et un SCM décentralisé comme GIT ?
- Qu'est-ce qu'un repository GIT ?
- Qu'est-ce qu'un remote ?
- Que désignent les termes upstream et downstream ?

cf https://stackoverflow.com/questions/2739376/definition-of-downstream-and-upstream

7.2 Installation et configuration
- Comment installer GIT sur Windows ?
- Comment connaitre la liste des commandes GIT ?
- Comment connaitre la version de votre GIT ?
- Quels sont les fichiers de configuration de GIT ?
- Comment afficher la configuration courante de GIT ?
- Comment exclure des fichiers ?
- Comment changer son nom d'utilisateur ?
- Comment changer son email ? 
- Comment changer la push url ?

7.3 Utilisation

7.3.1 Initialisation d'un repository
- Comment initialiser un repository
- Comment intiialiser un bare repository
- Comment cloner un repository

7.3.2 Les remotes
- Comment lister les remotes d'un repository ?

```
$ git remote -v
origin https://www.domain.tld/git/repo.git (fetch)
origin https://www.domain.tld/git/repo.git (push)
```

Un remote est désigné par 2 urls, une url de `fetch` (indique où tirer les modifications effectuées par les autres développeurs) et une url de `push` (indique où pousser ses propres modifications).

Certaines organisations adoptent le forking model pour gérer la collaboration dans le projet. Un nouveau développeur clonera le projet depuis le repository central, forkera ensuite ce repository puis changera sa push url pour pousser sur son fork au lieu du repo central. Les modifications du fork vers le repo central seront effectuées au travers pull/merge request depuis l'outil web présent sur le repo central (github, gitlab, ...). Ce modèle a pour avantage de simplifier et de sécuriser fortement la gestion des droits en écriture sur le repository central.

- Comment ajouter un remote ?

```
$ git remote add <alias> <chemin/url>
```

Où `<alias>` désigne le nom du `remote`.

- Comment inspecter un remote ?

```
$ git remote show origin
```

Affiche l'état du repository distant (fetch et push urls, liste des branches, si elles sont trackées ou non, branches locales configurées pour un pull et pour un push.

- Comment supprimer un remote ?

```
$ git remote rm <remote>
```

Où `remote` désigne le nom du repository distant.

- Comment renommer un remote ?

```
$ git remote rename <old> <new>
```

Où `old` désigne le nom du repository distant à changer et `<new>` le nouveau nom à donner.

Par exemple :

```
$ git remote rename origin dist
```

A pour effet de modifier le nom du repository distant de 'origin' en 'dist'.

- Comment mettre à jour la représentation locale d'un remote ? (fetch)

```
$ git fetch <remote>
```

Où `<remote>` correspond au nom du remote (`origin` par défaut lors d'un clone).

- Comment mettre à jour une branche locale avec une branche distance ?

```
$ git checkout <branche>
$ git pull <remote> <branche>
```

Où `<remote>` correspond au nom du remote (`origin` par défaut lors d'un clone) et `<branche>` au nom de la branche.

La commande `pull` exécute en réalité un `fetch` suivi d'un `merge`, au détail cela donnerait  :

```
$ git checkout master
$ git fetch origin
$ git merge origin/master
```

L'exécution d'une commande `pull` peut donc nécessiter de résoudre des conflits puisqu'il s'agit d'un `merge`.

- Comment mettre à jour un remote ? (push)

7.3.3 La working directory
- Qu'est-ce que la working directory ?
- Comment changer la working directory ?

7.3.4 La zone de stagging
- Qu'est ce que la zone de stagging ?
- Comment ajouter un fichier à la zone de stagging ?
- Comment retirer un fichier de la zone de stagging ?

7.3.5 Les commits
- Qu'est ce qu'un commit ?
- Comment créer un commit ?
- Comment ajouter un message en créant un commit ?
- Comment modifier le message d'un commit existant ?
- Comment supprimer le dernier commit de la branche courante sans perdre les modifications ?
- Comment supprimer le dernier commit de la branche courante avec les modifications ?
- Comment supprimer les "n" derniers commits de la branche courante sans perdre les modifications ?
- Comment supprimer les "n" derniers commits de la branche courante avec les modifications ?
- Comment ajouter un commit d'une branche A dans une branche B sans effectuer un merge ? (cherry-pick)
- Comment annuler un commit existant ? (revert)

7.3.6 Les branches 
- Qu'est-ce qu'une branche ?
- Comment lister les branches locales ?
- Comment créer une branche ?
- Comment supprimer une branche ?
- Comment renommer une branche ?
- Comment comparer deux branches ?
- Comment comparer l'état d'un fichier présent dans deux branches ?

7.3.7 Les fusions de branches (merge)
- Qu'est-ce qu'un merge ?
- Comment merger une branche A dans une branche B ?
- Comment annuler un merge en cours ?
- Comment rollback un merge terminé ?
- Qu'est-ce qu'un conflit ?
- Comment gérer un conflit ?

7.3.8 Réécriture de l'historique (rebase)
- Qu'est-ce qu'un rebase ?
- Qu'est-ce qu'un rebase intéractif ?
- Pourquoi effectuer un rebase ?
- Pourquoi effectuer un rebase intéractif ?
- Comment annuler un rebase en cours ?

7.3.9 Les tags
- Qu'est-ce qu'un tag ?
- Comment créer une tag ?
- Comment supprimer une tag ?
- Comment renommer une tag ?
- Comment lister les tags existants ?
- Comment comparer deux tags ?
- Comment comparer l'état d'un fichier présent dans deux tags ?

7.3.10 Les logs
- Qu'est-ce que le log ?
- Comment afficher le log ?
- Comment afficher le log sous forme graphique dans la console ?
- Comment afficher le log sur une seule ligne pour chaque commit ?
- Comment afficher un changelog entre deux tags ?
- Comment filtrer le log sur la base des messages de commit ?
- Comment filtrer le log sur la base de l'auteur des commits ?
- Comment afficher la liste des fichiers modifiés pour chaque commit du log ?
- Comment trouver qui a modifié quelle ligne dans un fichier donné ? (blame)

7.4 Outils
- github
- gitlab
- qu'elle est la différence entre une pull request (github) et une merge request (gitlab) ?



