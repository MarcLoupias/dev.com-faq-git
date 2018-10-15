# FAQ Git pour developpez.com

## 7.3.8 Réécriture de l'historique (`rebase`)

### Qu'est-ce qu'un `rebase` ?

Conceptuellement il s'agit d'une réécriture de l'historique.

Techniquement il s'agit de changer le parent du commit à la base de la branche à `rebase` ce qui a pour conséquence de recréer tous les commits descendants (du fait du nouveau timestamp).

De ce fait il ne faut **jamais** `rebase` une branche qui a été publiée quelque part et donc le `rebase` ne doit s'appliquer qu'à des branches privées, c'est à dire qui n'existe que sur votre machine.

### Pourquoi effectuer un `rebase` ?

Principalement pour conserver un historique propre et lisible.

La bonne pratique est de systématiquement `rebase` une branche de travail avant de chercher à la fusionner avec une branche de collaboration (nommée généralement `master`).

Prenons la situation suivante :

```text
---M1 master
   \
   B1---B2---B3 toto
```

Dans ce cas de figure vous avez créé une branche `toto` sur la base d'une branche `master` qui est la branche de collaboration du projet (là où tout le monde déverse ses contributions).

Vous avez fini de travailler et vous allez fusionner votre branche avec `master`.

Or, d'autres utilisateurs ont fait avancé `master` et la situation sur le dépôt distant est en réalité :

```text
---M1---M2---M3 origin/master  
```

Si vous fusionnez en l'état vous ne pourrez pas obtenir un `merge` fast-forward et vous aurez peut être même des conflits lors de la fusion.

Que vous fassiez un `rebase` ou non vous allez d'abord devoir récupérer les modifications du dépôt distant :

```bash
git checkout master
git pull origin master
```

Ceci fait votre historique local est désormais :

```text
---M1---M2---M3 master
   \
   B1---B2---B3 toto
```

Si vous choisissez de `rebase` vous allez obtenir ceci :

```text
---M1---M2---M3 master
              \
              B1'---B2'---B3' toto
```

Le commit parent de `B1` était `M1` avant le `rebase`, il sera `M3` après.

De ce fait, Git va rejouer chaque commit en respectant l'ordre de filiation, d'abord `B1`, puis `B2`, etc ...

A chaque étape, si Git rencontre un conflit, il vous laissera la main pour le résoudre.

**Important** : Les commits après `rebase` sont identifiés avec un prime (`'`), `B1` devient `B1'`, `B2` devient `B2'` etc ...

En effet Git recrée de nouveaux commits même en l'absence d'un conflit, donc avec un timestamp différent, donc le SHA1 identifiant le commit est différent.

### Comment effectuer un `rebase` ?

Commencez par récupérer l'état de la branche parente sur le dépôt distant :

```bash
git checkout master
git pull origin master
```

Ensuite placez vous sur la branche à `rebase` et exécutez-le (la commande `rebase` prend en argument la branche servant de base, c'est à dire la branche parente) :

```bash
git checkout toto
git rebase master
```

### Qu'est-ce qu'un `rebase` intéractif ?

C'est un `rebase` étendu qui va vous permettre de définir quelle opération effectuer à chaque commit de votre branche subissant le `rebase`.

Les options à chaque étape sont les suivantes :

- `pick` pour utiliser le commit
- `reword` pour utiliser le commit et changer son message
- `edit` pour utiliser le commit mais pour pouvoir le modifier
- `squash` pour fusionner le commit avec le précédent
- `fixup` comme squash mais en supprimant le message de commit du commit fusionné
- `exec` pour exécuter une commande shell
- `drop` pour ignorer le commit qui n'existera donc plus dans votre historique au terme de l'opération

### Pourquoi effectuer un `rebase` intéractif ?

Pour nettoyer son historique avant de le publier.

Fusionner les commits qui n'ont pas lieu d'exister indépendamment, nettoyer les messages de commits, supprimer des configurations temporaires, modifier leur ordre etc ...

### Comment effectuer un `rebase` intéractif ?

Il suffit d'ajouter le paramètre `-i` à la commande et d'y adjoindre la profondeur (combien de commits depuis la tête de la branche seront concernés).

Par exemple :

```bash
git rebase -i HEAD~3
```

Aura pour effet de `rebase` les 3 derniers commits de votre branche.

L'exécution de cette commande entraine l'ouverture d'un éditeur de texte dans votre shell, sous Windows avec Git BASH c'est [VIM](https://www.vim.org/), sur Ubuntu [nano](https://www.nano-editor.org/).

L'éditeur de texte contient un fichier de configuration du `rebase` à effectuer, pour dire à chaque étape quelle opération vous souhaitez effectuez.

Par défaut on obtient `pick` pour chaque commit, par exemple :

```text
pick d1fdf88 cypress - video recording on
pick b065479 travis and cypress - some fix in e2e tests + baseUrl conf + http-server devDeps + travis conf
pick 933cf95 migration from old webapp to jsonresume generated website

# Rebase 10f5b97..933cf95 onto 10f5b97 (3 command(s))
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out

```

Il suffit de changer la commande à effectuer, d'enregistrer ce fichier et de quitter l'éditeur et Git démarrera l'opération de `rebase` intéractif.

Si par exemple je veux changer les messages de commit des 3 commits de ma branche je vais configurer ainsi :

```text
reword d1fdf88 cypress - video recording on
reword b065479 travis and cypress - some fix in e2e tests + baseUrl conf + http-server devDeps + travis conf
reword 933cf95 migration from old webapp to jsonresume generated website

# Rebase 10f5b97..933cf95 onto 10f5b97 (3 command(s))

...

```

Ceci fait, à chaque étape du `rebase` Git me proposera de saisir un nouveau message de commit via l'éditeur de texte du shell.

### Comment annuler un `rebase` en cours ?

Comme pour annuler une fusion :

```bash
git rebase --abort
```

Cette commande fonctionne pour le `rebase` standard comme pour le `rebase` intéractif.

### Comment résoudre un conflit lors d'un `rebase` ?

Comme pour annuler une fusion.

Une fois les conflits traités et ajoutés à l'index il vous suffira de dire à Git de poursuivre le `rebase` (surtout pas de commit !)

```bash
git rebase --continue
```

Vous pouvez très bien obtenir des conflits à chaque étape, tout dépend des modifications effectuez par vous et les autres utilisateurs.

Cette commande fonctionne pour le `rebase` standard comme pour le `rebase` intéractif.
