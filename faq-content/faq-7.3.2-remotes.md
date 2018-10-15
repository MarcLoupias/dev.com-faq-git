# FAQ Git pour developpez.com

## 7.3.2 Les remotes

### Comment lister les remotes d'un dépôt ?

```bash
$ git remote -v
origin https://www.domain.tld/git/repo.git (fetch)
origin https://www.domain.tld/git/repo.git (push)
```

Un remote est désigné par 2 urls, une url de `fetch` (indique où tirer les modifications effectuées par les autres développeurs) et une url de `push` (indique où pousser ses propres modifications).

Certaines organisations adoptent le forking model pour gérer la collaboration dans le projet. Un nouveau développeur clonera le projet depuis le dépôt central, forkera ensuite ce dépôt puis changera sa push url pour pousser sur son fork au lieu du repo central. Les modifications du fork vers le repo central seront effectuées au travers pull/merge request depuis l'outil web présent sur le repo central (GitHub, GitLab, ...). Ce modèle a pour avantage de simplifier et de sécuriser fortement la gestion des droits en écriture sur le dépôt central.

### Comment ajouter un remote ?

```bash
git remote add <alias> <chemin/url>
```

Où `<alias>` désigne le nom du `remote`.

### Comment inspecter un remote ?

```bash
$ git remote show origin
* distante origin
  URL de rapatriement : https://github.com/MarcLoupias/dev.com-faq-git.git
  URL push : https://github.com/MarcLoupias/dev.com-faq-git.git
  Branche HEAD : master
  Branche distante :
    master suivi
  Branche locale configurée pour 'git pull' :
    master fusionne avec la distante master
  Référence locale configurée pour 'git push' :
    master pousse vers master (à jour)

```

Affiche l'état du dépôt distant (fetch et push urls, liste des branches, si elles sont trackées ou non, branches locales configurées pour un pull et pour un push.

### Comment supprimer un remote ?

```bash
git remote rm <remote>
```

Où `remote` désigne le nom du dépôt distant.

### Comment renommer un remote ?

```bash
git remote rename <old> <new>
```

Où `<old>` désigne le nom du dépôt distant à changer et `<new>` le nouveau nom à donner.

Par exemple :

```bash
git remote rename origin dist
```

A pour effet de modifier le nom du dépôt distant de `origin` en `dist`.

### Comment mettre à jour la représentation locale d'un remote ? (fetch)

```bash
git fetch <remote>
```

Où `<remote>` correspond au nom du remote (`origin` par défaut lors d'un clone).

### Comment mettre à jour une branche locale avec une branche distance ?

```bash
git checkout <branche>
git pull <remote> <branche>
```

Où `<remote>` correspond au nom du remote (`origin` par défaut lors d'un clone) et `<branche>` au nom de la branche.

La commande `pull` exécute en réalité un `fetch` suivi d'un `merge`, au détail cela donnerait  :

```bash
git checkout master
git fetch origin
git merge origin/master
```

L'exécution d'une commande `pull` peut donc nécessiter de résoudre des conflits puisqu'il s'agit d'un `merge`.

### Comment mettre à jour un remote ? (push)

```bash
git push origin toto
```

A pour effet de mettre à jour la branche `toto` sur le remote nommé `origin`.

Si la branche n'existe pas sur le dépôt distant elle est créée.
