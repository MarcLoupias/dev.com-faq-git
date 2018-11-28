# FAQ Git pour developpez.com

## 8 Les branches

### Comment comparer les historiques de deux branches ?

Si je souhaite connaitre la liste des *commits* existants dans `release/v1.0.0` et qui n'existent pas dans `master` :

```bash
git log release/v1.0.0..master
```

Pour connaitre la liste des *commits* existants dans `master` et qui n'existent pas dans `release/v1.0.0`, on inverse simplement l'ordre :

```bash
git log master..release/v1.0.0
```

Certaines options de la commande `log` sont très pratiques pour affiner l'affichage brut de `git log`, elles peuvent être combinées.

- `--oneline` permet de limiter l'affichage de chaque *commit* sur une seule ligne.

- `--stat` affiche la liste des fichiers modifiés et le nombre d'ajouts et suppressions, par ex :

```bash
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

Dans le cas de l'usage de l'opérateur *triple dot* (`...`), l'ajout des options `--left-right`, `--decorate` et `--graph` permettent de rendre plus lisible le résultat.

- `--left-right` ajoute à chaque ligne un `<` ou un `>` selon si la ligne fait référence à la première ou à la deuxième branche.

- `--decorate` affiche clairement les « refs » (tags, branches, `HEAD`) entre parenthèses après le SHA1 des *commits*.

- `--graph` constitue un graphe en ASCII art.

Par exemple :

```bash
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
