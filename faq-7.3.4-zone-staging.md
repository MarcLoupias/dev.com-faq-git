7.3.4 La zone de staging
- Qu'est ce que la zone de staging ?

Nommée également l'index ou encore la staging area. 

C'est le creuset dans lequel vous préparez le prochain commit à créer sur la branche courante.

Lorsque vous modifiez un fichier de la working directory, la modification doit être indexée (on dit aussi placée dans la zone de staging) pour être embarquée dans le prochain commit.

- Comment ajouter un fichier à la zone de stagging ?

Sur la branche master vous créez un fichier `nom-fichier.txt`, un git status vous indique l'état de la working directory :

```
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        nom-fichier.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Il suffit de lire l'output du CLI pour connaitre la commande à exécuter :

```
$ git add nom-fichier.txt
```

Ajoute le fichier `nom-fichier.txt` à la zone de staging. Un `git status` le confirme : 

```
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   nom-fichier.txt
```

- Comment retirer un fichier de la zone de stagging ?

Cela dépend s'il s'agit d'un fichier qui vient d'être créé et qui n'est donc pas déjà versionné par git ou s'il s'agit d'une modification d'un fichier existant. Dans l'exemple précédent nous avons créé un fichier la commande est donc :

```
$ git rm --cached nom-fichier.text
```

Si le fichier existait déjà la commande 

```
git reset HEAD nom-fichier.txt
```

Permet de supprimer les modifications. En fait on demande à git de réinitiliser l'état du fichier dans l'état qu'il a sur le dernier commit de la branche courante (`HEAD`).
