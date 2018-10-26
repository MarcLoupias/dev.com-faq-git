# FAQ Git pour developpez.com

## 7.3.4 L'index (*staging area*)

### Qu'est ce que l'index ?

Nommée également *zone de staging* ou encore la *staging area*.

C'est le creuset dans lequel vous préparez le prochain commit à créer sur la branche courante.

Lorsque vous modifiez un fichier du répertoire de travail (*working directory*), la modification doit être indexée (on dit aussi placée dans l'index) pour être embarquée dans le prochain commit.

### Comment ajouter un fichier à l'index ?

Sur la branche `master` vous créez un fichier `nom-fichier.txt`, un `git status` vous indique l'état du répertoire de travail :

```bash
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        nom-fichier.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Il suffit de lire la sortie du CLI pour connaitre la commande à exécuter :

```bash
git add nom-fichier.txt
```

Ajoute le fichier `nom-fichier.txt` à l'index. Un `git status` le confirme :

```bash
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   nom-fichier.txt
```

### Comment retirer un fichier de l'index ?

Cela dépend s'il s'agit d'un fichier qui vient d'être créé et qui n'est donc pas déjà versionné par Git ou s'il s'agit d'une modification d'un fichier existant. Dans l'exemple précédent nous avons créé un fichier, la commande est donc :

```bash
git rm --cached nom-fichier.text
```

Si le fichier existait déjà la commande :

```bash
$ git reset HEAD nom-fichier.txt
Unstaged changes after reset:
M       nom-fichier.txt
```

Permet de retirer un fichier de l'index. **Les modifications ne sont pas supprimées**.

Git nous l'indique avec le `M` devant le nom du fichier. Il signifie qu'il y a des modifications dans le fichier `nom-fichier.txt` qui ne sont pas présentes dans l'index.
