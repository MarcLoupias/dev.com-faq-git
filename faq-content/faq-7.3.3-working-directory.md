# FAQ Git pour developpez.com

## 7.3.3 La working directory

### Qu'est-ce que la working directory (répertoire de travail) ?

Littérallement, il s'agit du répertoire de travail de votre dépôt.

Il expose l'état actuel d'une branche, d'un commit ou d'un tag.

C'est depuis la working directory que l'on effectue les modifications souhaitées sur nos fichiers.

### Comment changer l'état du répertoire de travail (working directory) ?

La commande `git checkout` peut prendre en paramètre un hash de commit, un nom de branche ou un nom de tag. L'exécution de cette commande change le répertoire de travail (*working directory*) pour exposer l'état du commit, de la branche ou du tag.

```bash
git checkout 3ffb92fe20b6785d801023783d2f18c4de6e1593
```

A pour effet de changer l'état du répertoire de travail (*working directory*) en l'état correspondant au commit désigné. Concrètement, Git modifie les fichiers traqués pour les mettre dans l'état correspondant au commit désigné.

Idem avec un nom de branche :

```bash
git checkout master
```

Ou avec un tag :

```bash
git checkout 1.0.0
```

### Comment connaitre l'état du répertoire de travail (working directory) selon Git ?

```bash
$ git status
On branch master
nothing to commit, working directory clean
```

Indique qu'on a `checkout` la branche `master` et que rien n'est modifié.

**En cas de doute**, toujours exécuter un `git status` pour savoir dans quel état se situe Git.

### Comment annuler les modifications effectuées sur un fichier du répertoire de travail ?

Si nous avons modifié le fichier `nom-fichier.txt` :

```bash
git checkout -- nom-fichier.txt
```

A pour effet de supprimer toutes les modifications effectuées dans le fichier.

### Que veut dire `"detached HEAD" state` après avoir effectué un `git checkout` ?

Vous obtenez ce genre de message après un `checkout` sur un commit ou sur un tag :

```bash
$ git checkout 0.4.14
Note: checking out '0.4.14'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD est maintenant sur 2ef6cee... Version bump
```

La variable `HEAD` est un alias du commit de tête de la branche courante. Lorsque vous ajoutez des commits à la branche, la variable `HEAD` est mise à jour.

En mode détaché ce ne sera plus le cas.

Pour ajouter des commits au dépôt il est donc nécessaire de se trouver sur une branche, c'est le concept qui représente une ligne de développement.

### Quel est l'intérêt de faire un checkout sur un tag ?

Une raison courante de vouloir `checkout` un tag est de vouloir créer un hotfix. Dans ce cas on va `checkout` le tag puis immédiatement créer une nouvelle branche :

```bash
git checkout 0.4.14
git checkout -b hotfix/0.4.15
```

Le développement du hotfix peut alors démarrer sur la branche `hotfix/0.4.15`.
