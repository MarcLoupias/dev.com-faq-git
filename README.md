# dev.com-faq-git

> FAQ Git pour developpez.com

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-sa/4.0/)
[![Build Status](https://travis-ci.com/MarcLoupias/dev.com-faq-git.svg?branch=master)](https://travis-ci.com/MarcLoupias/dev.com-faq-git)

## Contribuer

[Appel à contribution pour une section Git dans la FAQ SCM](https://www.developpez.net/forums/d1844867/general-developpement/alm/contribuez/appel-contribution-section-git-faq-scm/)

A insérer avec les autres FAQ des SCM : https://alm.developpez.com/faq/scm

### Préparez votre fork et votre dépôt local

Commencez par cloner ce dépôt en local chez vous : 

```bash
git clone https://github.com/MarcLoupias/dev.com-faq-git.git
```

Puis forkez ce dépôt sur GitHub.

Enfin, ajoutez un remote à votre dépôt local : 

```bash
git remote add fork <url-de-votre-fork>
```

De cette façon, lorsque vous aurez besoin de mettre à jour votre dépôt local avec les contributions des autres contributeurs vous exécuterez :

```bash
git pull origin master
```

Et lorsque vous souhaiterez effectuer une contribution, vous pousserez votre branche de travail (jamais `master`, elle est de toute façon protégée) sur votre fork :

```bash
git push fork <nom-branche-de-travail>
```

Il ne restera plus qu'à ouvrir votre *pull request* depuis l'interface GitHub de votre fork.

### Installation des dépendances

Ce projet utilise un outil de lint (cf ci-dessous).

Vous avez besoin de **Node.js** (version LTS minimum, donc `6+`) et de **npm** dans sa dernière version de préférence (`5.2+` minimum).

Si c'est le cas vous pouvez exécuter un bête :

```bash
npm install
```

Testez que tout fonctionne en exécutant le linter :

```bash
npm test
```

### Linting du markdown

Votre contribution devra passer ce contrôle pour être approuvée.

Lors de la rédaction de votre contribution vous pouvez contrôler qu'elle est valide en exécutant `npm test`, les alertes s'affichent dans le terminal qui exécute npm.

#### Informations complémentaires sur le linter

Linting avec [DavidAnson/markdownlint](https://github.com/DavidAnson/markdownlint) via [igorshubovych/markdownlint-cli](https://github.com/igorshubovych/markdownlint-cli).

[Liste des règles](https://github.com/DavidAnson/markdownlint/blob/master/doc/Rules.md#md001)

Config cf `.markdownlist.json` ([json schema](https://github.com/DavidAnson/markdownlint/blob/master/schema/markdownlint-config-schema.json)).

### Génération du sommaire

Le fichier `SUMMARY.md` est généré par le script `build-summary`.

## tester la FAQ avec les outils dev.com

Copier le fichier xml généré dans un répertoire du même nom (sans l'extension) sous le répertoire `documents/` à partir de la racine du kit.
Par exemple pour le fichier `dvlp-faq-git.xml`, on va le copier sous `documents/dvlp-faq-git/dvlp-faq-git.xml`.
Cf [doc du kit](http://club.developpez.com/outils/wiki/KitGeneration) pour les fichiers connexes (images, css, ...).

Dans un shell aller dans le répertoire du kit `script/` et exécuter le script `buildFaq` avec le nom du répertoire cible.
Par exemple pour construire la faq de l'exemple précédent : `sh buildFaq dvlp-faq-git`.

Le kit génère les fichiers de la faq dans `html/<nom-de-la-faq>`. Dans notre exemple précédent ça donne `html/dvlp-faq-git`.

Le bug css n'est pas résolu, il faut donc copier les css de `html/dvlp-faq-git/css/` à la racine de la faq.

On examine la faq en lançant simplement le fichier `index.html` dans un navigateur.

## visualiser la FAQ en html

La commande `npm run serve` permet de générer une version `html` de la FAQ dans le répertoire `dist/`.

Il s'agit simplement de pouvoir vérifier la FAQ dans un navigateur sans passer par le Kit. Aucune mise en forme disponible à ce stade.

## Utilisation

### Comment utiliser cette FAQ ?

Le projet ne dispose plus, pour le moment, de version HTML.
Si vous souhaitez la consulter, je vous invite à lire directement le fichier [markdown en ligne](https://github.com/MarcLoupias/dev.com-faq-git/blob/master/faq-content/SUMMARY.md).

## Licence et condition d'utilisation

Consultez le fichier [`LICENCE.md`](LICENCE.md) pour plus d'informations, s'il vous plaît.

## Contact

[Profil sur developpez.com](https://www.developpez.net/forums/u70899/marco46/)
