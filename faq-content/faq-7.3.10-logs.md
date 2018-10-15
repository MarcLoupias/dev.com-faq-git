# FAQ Git pour developpez.com

## 7.3.10 Les logs

### Qu'est-ce que le log ?

Le log permet d'explorer l'historique des commits du dépôt.

Les options et possibilités sont très nombreuses, on peut filtrer l'affichage de beaucoup de manières, par références (branches, tags), par auteur de commit, par dates, etc ...

On peut aussi comparer les références entre elles (branches, tags) afin d'afficher un CHANGELOG des commits entre différentes versions par exemple.

C'est un outil indispensable pour comprendre l'historique, il est également très utile pour la maintenance.

### Comment afficher le log ?

Dans sa forme la plus simple :

```bash
$ git log

commit df76163ff6c90e8c62c588a06d82fb3d3f3aca66
Author: Thomas Davis <thomasalwyndavis@gmail.com>
Date:   Wed Oct 10 21:37:16 2018 +1100

    Logs the correct path to jsonresume.json

commit 7ee2e20e767a979b0d0113133e045f3fe44a6735
Author: marlou <pro@marc-loupias.fr>
Date:   Thu Oct 4 10:51:51 2018 +0200

    update node version in engine section to drop unmaintained node version and match travis config

commit e9a998f5b02fd2e9a01def86a8ebb470c1d246d4
Author: marlou <pro@marc-loupias.fr>
Date:   Thu Oct 4 10:50:59 2018 +0200

    update superagent from 2.+ to 3.+

commit be7e49d14e11620f8a37b4d65f8790eeae188b38
Author: marlou <pro@marc-loupias.fr>
Date:   Thu Oct 4 10:21:06 2018 +0200

    moving to an up-to-date and actively maintained package to open the browser

    - open@0.0.5 removed
    - opn@5.4.0 sindresorhus package added

```

On navigue avec les flèches du clavier et on sort en appuyant sur la touche `q`.

### Comment afficher le log sous forme graphique dans la console ?

```bash
git log --graph
```

### Comment afficher le log sur une seule ligne pour chaque commit ?

```bash
git log --oneline
```

### Comment afficher un changelog entre deux tags ?

```bash
git log 0.11.0..0.12.0 --oneline
```

### Comment filtrer le log sur la base des messages de commit ?

```bash
git log --grep 'regex'
```

Le contenu de `'regex'` doit être une regex POSIX valide.

### Comment filtrer le log sur la base de l'auteur des commits ?

```bash
git log --author="robert"
```

### Comment afficher la liste des fichiers modifiés pour chaque commit du log ?

```bash
git log --stat
```

### Comment trouver qui a modifié quelle ligne dans un fichier donné ? (`blame`)

La commande `blame` permet d'explorer l'historique à l'intérieur d'un fichier.

```bash
$ git blame sha1_file.c
0fcfd160 (Linus Torvalds  2005-04-18 13:04:43 -0700    8)  */
0fcfd160 (Linus Torvalds  2005-04-18 13:04:43 -0700    9) #include "cache.h"
1f688557 (Junio C Hamano  2005-06-27 03:35:33 -0700   10) #include "delta.h"
a733cb60 (Linus Torvalds  2005-06-28 14:21:02 -0700   11) #include "pack.h"
8e440259 (Peter Eriksen   2006-04-02 14:44:09 +0200   12) #include "blob.h"
8e440259 (Peter Eriksen   2006-04-02 14:44:09 +0200   13) #include "commit.h"
8e440259 (Peter Eriksen   2006-04-02 14:44:09 +0200   14) #include "tag.h"
8e440259 (Peter Eriksen   2006-04-02 14:44:09 +0200   15) #include "tree.h"
f35a6d3b (Linus Torvalds  2007-04-09 21:20:29 -0700   16) #include "refs.h"
70f5d5d3 (Nicolas Pitre   2008-02-28 00:25:19 -0500   17) #include "pack-revindex.h"628522ec (Junio C Hamano              2007-12-29 02:05:47 -0800   18) #include "sha1-lookup.h"
```

Chaque ligne du fichier est affichée, devant chaque ligne on a le SHA1 en version courte, le nom de l'auteur et le timestamp de création du commit.

On navigue comme avec les logs avec les flèches du clavier et on sort avec la touche `q`.
