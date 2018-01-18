7.3.3 La working directory
- Qu'est-ce que la working directory ?

Littérallement, il s'agit du répertoire de travail de votre repository.

Il expose l'état actuel d'une branche, d'un commit ou d'un tag.

- Comment changer l'état de la working directory ?

La commande git checkout peut prendre en paramètre un hash de commit, un nom de branche ou un nom de tag. L'exécution de cette commande change la working directory pour exposer l'état du commit, de la branche ou du tag.

```
$ git checkout 3ffb92fe20b6785d801023783d2f18c4de6e1593
```

A pour effet de changer l'état de la working directory en l'état correspondant au commit désigné.

Idem avec un nom de branche

```
$ git checkout master
```

Ou avec un tag

```
$ git checkout 1.0.0
```
