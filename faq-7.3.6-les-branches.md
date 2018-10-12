# FAQ GIT pour developpez.com

## 7.3.6 Les branches 

### Qu'est-ce qu'une branche ?

Conceptuellement, une branche est une ligne de développement dont le but est d'ajouter de nouveaux commits à l'arbre des commits constituants le repository.
 
C'est depuis une branche que l'utilisateur :

- modifie la working directory (modification des sources)
- ajoute à l'index ces modifications
- et qu'il crée des commits

Techniquement, une branche est une référence sur le dernier commit d'une série de commits. Tous les commits descendants font donc parti de la branche. 

Ainsi, manipuler une branche est une opération très rapide à exécuter puisqu'il s'agit d'un pointeur et non d'un container.
 
### Comment lister les branches locales ?

```
$ git branch -l

* master
```

### Comment lister toutes les branches (locales, distantes, traquées, non-traquées) ?

```
$ git remote show origin

* distante origin
  URL de rapatriement : https://github.com/<user>/<repo>.git
  URL push : https://github.com/<user>/<repo>.git
  Branche HEAD : master
  Branche distante :
    master suivi
  Branche locale configurée pour 'git pull' :
    master fusionne avec la distante master
  Référence locale configurée pour 'git push' :
    master pousse vers master (à jour)

```

### Comment créer une branche ?

```
$ git checkout -b <nom-branche>
```

Cette commande a pour effet une branche sur la base de celle actuellement active puis de `checkout` la branche nouvellement créée (la rendre active).

Cette création est évidemment seulement locale.

### Comment créer une branche sur une repository distant ?

Il faut créer la branche en local puis la pousser sur le repository distant :

```
$ git checkout -b <nom-branche>
$ git push <nom-remote> <nom-branche>
```

### Comment supprimer une branche ?

```
$ git branch -D <nom-branche>
```

L'option `-d` peut être utilisée à la place de l'option `-D` mais seulement si la branche a auparavant été `merge` dans la branche parente.

### Comment supprimer une branche distante ?

```
$ git push <nom-remote> --delete <nom-branche> 
```

### Comment renommer une branche ?

```
$ git branch -m <nouveau-nom>
```

### Comment comparer deux branches ?

Il y a deux axes de comparaison possibles, on peut vouloir comparer :

- les séries de commits des branches (les historiques des commits)
- l'état des fichiers (les contenus des commits)
 
La première question est donc d'abord de savoir ce que l'on cherche à comparer. 

Pour comparer les historiques de 2 branches, on se réfèrera à la commande `git log`, pour comparer l'état des fichiers on se réfèrera à la commande `git diff`.

La deuxième question est de savoir comment comparer les branches. 

Ceci est déterminé par les "range operator" "double dot" (`..`) et "triple dot" (`...`).

L'usage se fait de cette manière : `$ git log A..B` ou `$ git diff A..B`.

Attention, selon la commande utilisée (log ou diff), la sémantique des opérateurs est différente.

Dans le cas de `git log` :

- `..` permet de connaitre les éléments présents dans l'un mais pas dans l'autre.
- `...` permet de connaitre tous les éléments qui ne sont pas partagés.

Dans le cas de `git diff` :

- `..` permet de connaitre les différences de contenu entre les têtes (dernier commit, nommé souvent "tip" en anglais) des deux branches. 
- `...` permet de connaitre les différences entre la tête de B et la "merge base" (le dernier commit commun dans l'arbre) commune avec A.

### Comment comparer les historiques de 2 branches ?

Si je souhaite connaitre la liste des commits existants dans `release/v1.0.0` et qui n'existent pas dans `master` :
 
```
$ git log release/v1.0.0..master
```

Pour connaitre la liste des commits existants dans `master` et qui n'existent pas dans `release/v1.0.0`, on inverse simplement l'ordre :

```
$ git log master..release/v1.0.0
```

Certaines options de la commande log sont très pratiques pour affiner l'affichage brut de `git log`, elles peuvent être combinées :

`--oneline` permet de limiter l'affichage de chaque commit sur une seule ligne.

`--stat` affiche la liste des fichiers modifiés et le nombre d'ajouts et suppressions, par ex :

```
$ git log --oneline --stat release/v1.0.0..master

df76163 Logs the correct path to jsonresume.json
 lib/login/login-request.js | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
7ee2e20 update node version in engine section to drop unmaintained node version and match travis config
 package.json | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
e9a998f update superagent from 2.+ to 3.+
 package.json | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Dans le cas de l'usage de l'opérateur triple dot (`...`), l'ajout des options `--left-right`, `--decorate` et `--graph` permettent de rendre plus lisible le résultat.

`--left-right` ajoute à chaque ligne un `<` ou un `>` selon si la ligne fait référence à la première ou à la deuxième branche. 

`--decorate` affiche clairement les "refs" (tags, branches, `HEAD`) entre parenthèses après le SHA1 des commits.

`--graph` constitue un graphe en ASCII art.

Par exemple :

```
$ git log --oneline --decorate --left-right --graph release/v1.0.0...master

> 332d9e9 (HEAD -> master, origin/master) Fix for themes and version bump
> 7d5f8a7 Fixed delete account issues. removed PDF exports for now
>   6d6c792 Merge pull request #290 from MarcLoupias/fix/security
|\  
| > 7ee2e20 (fork/fix/security, fix/security) update node version in engine section to drop unmaintained node version and match travis config
| > e9a998f update superagent from 2.+ to 3.+
| > be7e49d moving to an up-to-date and actively maintained package to open the browser
> | df76163 Logs the correct path to jsonresume.json
|/  
>   5aaf9b8 (fork/master, fork/HEAD) Merge pull request #275 from brandenbird/pr/change-export-to-puppeteer
|\  
| > 6e1ec92 Fixed exports for pdfs
> | f0af5f6 Update node.js version to be tested on Travis CI
> | 4938d0e Update .nvmrc to use node.js v8.x LTS
> |   eef87b2 Merge pull request #273 from jouk0/patch-1
|\ \  
| |/  
|/|   
| > fa5130e Updated resume.json path change on the process arg
|/  
> ed2106d Added https to all external requests

```

### Comment comparer l'état de tous les fichiers présents dans deux branches ?

```
$ git diff release/v1.0.0..master
```

Cet affichage risque d'être assez indigeste si vous avez beaucoup de fichiers et de différences. 

Une première étape pour trier pourrait être de ne pas afficher les différences en tant que telles mais de listes les fichiers et le nombre de différences qu'ils contiennent avec l'option `--stat` :

```
$ git diff --stat release/v1.0.0..master

 .env                              |    2 +-
 .nvmrc                            |    2 +-
 .travis.yml                       |   12 +-
 README.md                         |   88 ++---
 index.js                          |  111 ++++--
 lib/builder/index.js              |   29 +-
 lib/export-resume/index.js        |  145 ++++----
 lib/export-resume/menu.js         |   24 --
 lib/init.js                       |  135 ++++---
 lib/login/login-request.js        |    4 +-
 lib/pre-flow/check-pkg-version.js |    2 +-
 lib/pre-flow/get-resume.js        |    8 +-
 lib/pre.js                        |    2 +-
 lib/publish/menu.js               |   44 +--
 lib/publish/publish-resume.js     |    6 +-
 lib/register/register-user.js     |    4 +-
 lib/register/validate.js          |    2 +-
 lib/serve.js                      |   33 +-
 lib/settings/change-password.js   |    2 +-
 lib/settings/change-theme.js      |    6 +-
 lib/settings/delete-user.js       |    2 +-
 lib/settings/menu.js              |   70 ++--
 lib/test.js                       |    6 +-
 lib/version.js                    |    2 +-
 package-lock.json                 | 1621 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 package.json                      |   29 +-
 test/index.js                     |    7 +-
 27 files changed, 2027 insertions(+), 371 deletions(-)
```

### Comment comparer l'état d'un fichier présent dans deux branches ?

On ajoute simplement le chemin relatif du fichier à comparer :

```
$ git diff release/v1.0.0..master lib/builder/index.js
```
