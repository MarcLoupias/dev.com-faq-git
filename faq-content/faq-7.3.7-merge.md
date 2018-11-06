# FAQ Git pour developpez.com

## 7.3.7 Les fusions de branches (*merge*)

### Qu'est-ce qu'une fusion (*merge*) ?

C'est l'action de fusionner une branche avec une autre, généralement d'une branche enfant vers une branche parente.

Par exemple :

Ici nous avons une seule branche `master` avec un seul *commit* `M1`.

```text
---M1 master
```

Nous créons une branche `toto`, à la création ces deux branches pointent sur le *commit* `M1` :

```text
---M1 master, toto
```

Nous ajoutons un *commit* à la branche `toto` :

```text
---M1 master
   \
   B1 toto
```

La branche `master` est toujours constituée seulement du *commit* `M1`, la branche `toto` elle est constituée du *commit* `M1` suivi du *commit* `B1` qui a pour parent le *commit* `M1`.

Nous ajoutons de nouveaux *commits* sur la branche `toto` :

```text
---M1 master
   \
   B1---B2---B3 toto
```

La branche `master` est toujours constituée seulement du *commit* `M1`, la branche `toto` elle est constituée des *commits* `M1`, `B1`, `B2` et `B3`.

L'action de fusionner les *commits* de `toto` dans `master` est l'action pour obtenir par défaut (*merge fast-forward*) cet historique :

```text
M1---B1---B2---B3 master, toto
```

La branche `toto` qui n'a plus de raisons d'être peut être alors supprimée :

```text
M1---B1---B2---B3 master
```

### Comment fusionner une branche `toto` dans une branche `master` ?

Il faut se positionner sur la branche de destination au préalable (*checkout*) :

```text
git checkout master
```

Il est également important de n'avoir aucune modifications en cours dans le répertoire de travail (*working directory*) sinon Git refusera la fusion.

Ceci fait la fusion des deux branches est possible :

```text
git merge toto
```

C'est tout.

### Quelle est la différence entre un *merge fast-forward* et un *merge no-fast-forward* ?

Un *merge fast-forward* peut avoir lieu lorsque la branche parente n'a pas évolué depuis la création de la branche à fusionner.

Par exemple dans cette situation :

```text
---M1 master
   \
   B1---B2---B3 toto
```

L'exécution de `git merge toto` aboutira à un historique linéaire :

```text
M1---B1---B2---B3 master, toto
```

Notez que par défaut, Git essaiera d'effectuer un *merge fast-forward* sauf configuration ou option explicite pour forcer un *merge non fast-forward*.

Un *merge non fast-forward* a lieu lorsque la branche parente a évolué après la création de la branche enfante.

Par exemple avec la situation précédente :

```text
---M1 master
   \
   B1---B2---B3 toto  
```

Avant de fusionner `toto` dans `master`, admettons que `master` ait reçu des *commits*, la situation devient :

```text
---M1---M2---M3 master
   \
   B1---B2---B3 toto  
```

Dans ce cas Git rajoute un *commit* dit « de merge » qui aura la particularité d'avoir deux parents, ici `M3` et `B3` :

```text
---M1---M2---M3---M4 master, toto
    \            /
    B1---B2---B3
```

Le *commit* de *merge* est noté `M4`, il contient la somme des modifications de `B1`, `B2` et `B3`.

Même lorsque une branche peut être fusionnée en *merge fast-forward* on peut forcer la création du *commit* de *merge*, par exemple avec cette situation :

```text
---M1 master
   \
   B1---B2---B3 toto
```

L'exécution de la commande `git merge --no-ff toto` abouti à cette historique :

```text
---M1-------------M4 master, toto
    \            /
    B1---B2---B3
```

Certains utilisateurs aiment conserver la visibilité de l'existance des branches même après leur fusion et leur suppression :

```text
---M1-------------M4 master
    \            /
    B1---B2---B3
```

### Comment annuler une fusion terminée ?

La solution la plus simple consiste à supprimer les *commits* sur la branche de destination. Par exemple dans cette situation :

```text
---M1-------------M4 master, toto
    \            /
    B1---B2---B3
```

En se positionnant (*checkout*) sur la branche `master` on peut soit supprimer le dernier *commit* :

```text
git reset HEAD^
```

Soit donner à la commande `reset` le SHA1 du *commit* `M1` :

```text
git reset --hard 1234abcd
```

On revient alors à la situation précédant la fusion :

```text
---M1 master
   \
   B1---B2---B3 toto
```

### Qu'est-ce qu'un conflit ?

Un conflit apparait lors d'une fusion lorsque deux fichiers ont évolué sur la même ligne de code mais différemment.

Git ne peut pas savoir où est la vérité, il demande donc à l'utilisateur de trancher en modifiant le fichier source à fusionner en ajoutant les deux versions possibles encadrées par des marqueurs.

### Comment gérer un conflit ?

Par exemple avec un conflit sur le fichier `index.html` lors d'une fusion de `toto` dans `master` on aurait :

- `<<<<<<< HEAD` qui désigne le début de la version de `master`.
- `=======` qui sépare les deux versions et débute donc la version de `toto`.
- `>>>>>>> refs/heads/toto` qui désigne la fin de la version de `toto`.

Il convient ici de faire le tri et de supprimer ces marqueurs puis d'ajouter le fichier à l'index via un simple `git add index.html`.

Pour terminer la résolution de conflits vous pouvez utiliser la commande `git merge --continue` si votre version de Git est supérieure ou égale à la 2.12 sinon exécutez simplement un `git commit` sans aucune option.

### Comment annuler une fusion en cours ?

Pendant la résolution des conflits exécutez simplement un `git merge --abort`.
