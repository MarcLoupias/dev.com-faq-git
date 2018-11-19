# FAQ Git pour developpez.com

## 7.3.9 Les tags

### Qu'est-ce qu'un tag ?

C'est un label (une chaîne de caractère) pointant sur un et un seul commit.

Son rôle est d'identifier un commit, c'est à dire une révision du code source, correspondant à une version précise du livrable obtenu depuis ce commit.

Le nommage d'un tag obéit généralement à une convention, la spécification [semver](https://semver.org/) est de loin la plus utilisée.

Un tag peut être annoté pour donner des informations complémentaires en langage naturel.

### Comment créer une tag ?

En ligne de commande :

```bash
git tag -a v1.4.0 -m 'my version 1.4.0'
```

À pour effet de créer un tag identifiant le commit actuellement `checkout`.

Ce tag est créé localement, pour l'ajouter à un dépôt distant il est nécessaire de le pousser :

```bash
git push origin v1.4.0
```

### Comment supprimer une tag ?

```bash
git tag -d v1.4.0
```

La suppression est seulement locale.

Supprimer un tag rendu public est une **très** mauvaise pratique. La bonne pratique est de créer un nouveau tag !

### Comment renommer une tag ?

Supprimez le tag et créez-en un nouveau.

Comme pour la suppression de tag, renommer un tag rendu public est une **très** mauvaise pratique.

### Comment lister les tags existants ?

```bash
git tag
```

### Comment comparer deux tags ?

Exactement [comme avec les branches](faq-7.3.6-les-branches.md#comment-comparer-les-historiques-de-2-branches-), remplacez simplement les noms des branches par les noms des tags.

### Comment comparer l'état d'un fichier présent dans deux tags ?

Exactement [comme avec les branches](faq-7.3.6-les-branches.md#comment-comparer-létat-dun-fichier-présent-dans-deux-branches-), remplacez simplement les noms des branches par les noms des tags.
