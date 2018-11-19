# FAQ Git pour developpez.com

## 1 Généralités

- [Qu'est ce que Git ?](section-1/1.q001.md)
- [Que signifie Git ?](section-1/1.q002.md)
- [Où trouver de la documentation pour Git ?](section-1/1.q003.md)
- [Où trouver le code source de Git ?](section-1/1.q004.md)
- [Quelles sont les différences entre un SCM centralisé comme Subversion et un SCM décentralisé comme Git ?](section-1/1.q005.md)
- [Qu'est-ce qu'un dépôt Git ?](section-1/1.q006.md)
- [Qu'est-ce qu'un dépôt distant (*remote*) ?](section-1/1.q007.md)
- [Que désignent les termes upstream et downstream ?](section-1/1.q008.md)

## 2 Installation et configuration

- [Comment installer Git sur Windows ?](section-2/2.q001.md)
- [Comment installer Git sur macOS ?](section-2/2.q002.md)
- [Comment installer Git sur Linux ?](section-2/2.q003.md)
- [Comment connaitre la liste des commandes Git ?](section-2/2.q004.md)
- [Comment connaitre la version de votre Git ?](section-2/2.q005.md)
- [Quels sont les fichiers de configuration de Git ?](section-2/2.q006.md)
- [Comment afficher la configuration courante de Git ?](section-2/2.q007.md)
- [Comment exclure des fichiers ?](section-2/2.q008.md)
- [Comment changer son nom d'utilisateur ?](section-2/2.q009.md)
- [Comment changer son email ?](section-2/2.q010.md)
- [Comment changer l'URL d'un dépôt distant ?](section-2/2.q011.md)

## 3 Initialisation d'un dépôt

- [Comment initialiser un dépôt ?](section-3/3.q001.md)
- [Comment initialiser un dépôt nu (*bare repository*) ?](section-3/3.q002.md)
- [Comment cloner un dépôt ?](section-3/3.q003.md)
- [Comment connaitre l'état du dépôt ?](section-3/3.q004.md)

## 4 Les dépôts distants (*remotes*)

- [Comment lister les dépôts distants d'un dépôt ?](section-4/4.q001.md)
- [Comment ajouter un dépôt distant ?](section-4/4.q002.md)
- [Comment inspecter un dépôt distant ?](section-4/4.q003.md)
- [Comment supprimer un dépôt distant ?](section-4/4.q004.md)
- [Comment renommer un dépôt distant ?](section-4/4.q005.md)
- [Comment mettre à jour la représentation locale d'un dépôt distant (`fetch`) ?](section-4/4.q006.md)
- [Comment mettre à jour une branche locale avec une branche distante (`pull`) ?](section-4/4.q007.md)
- [Comment mettre à jour un dépôt distant (`push`) ?](section-4/4.q008.md)

## 5 La working directory

- [Qu'est-ce que le répertoire de travail (working directory) ?](section-5/5.q001.md)
- [Comment changer l'état du répertoire de travail ?](section-5/5.q002.md)
- [Comment connaitre l'état du répertoire de travail selon Git ?](section-5/5.q003.md)
- [Comment annuler les modifications effectuées sur un fichier du répertoire de travail ?](section-5/5.q004.md)
- [Que veut dire `"detached HEAD" state` après avoir effectué un `git checkout` ?](section-5/5.q005.md)
- [Quel est l'intérêt de faire un checkout sur un tag ?](section-5/5.q006.md)

## 6 L'index (*staging area*)

- [Qu'est ce que l'index ?](section-6/6.q001.md)
- [Comment ajouter un fichier à l'index ?](section-6/6.q002.md)
- [Comment retirer un fichier de l'index ?](section-6/6.q003.md)

## 7 Les commits

- [Qu'est ce qu'un *commit* ?](section-7/7.q001.md)
- [Comment créer un *commit* ?](section-7/7.q002.md)
- [Comment ajouter un message en créant un *commit* ?](section-7/7.q003.md)
- [Comment modifier le message d'un *commit* existant ?](section-7/7.q004.md)
- [Comment supprimer le dernier *commit* de la branche courante sans perdre les modifications ?](section-7/7.q005.md)
- [Comment supprimer le dernier *commit* de la branche courante avec les modifications ?](section-7/7.q006.md)
- [Comment supprimer les "n" derniers *commits* de la branche courante sans perdre les modifications ?](section-7/7.q007.md)
- [Comment supprimer les "n" derniers *commits* de la branche courante avec les modifications ?](section-7/7.q008.md)
- [Comment ajouter un *commit* d'une branche A dans une branche B sans effectuer un merge (*cherry-pick*) ?](section-7/7.q009.md)
- [Comment ajouter un *commit* provenant d'une branche d'un autre dépôt à la branche courante de ce dépôt (*cherry-pick*) ?](section-7/7.q010.md)
- [Comment annuler un *commit* existant (*revert*) ?](section-7/7.q011.md)

## 8 Les branches

- [Qu'est-ce qu'une branche ?](section-8/8.q001.md)
- [Comment lister les branches locales ?](section-8/8.q002.md)
- [Comment lister toutes les branches (locales, distantes, traquées, non-traquées) ?](section-8/8.q003.md)
- [Comment créer une branche ?](section-8/8.q004.md)
- [Comment créer une branche sur une dépôt distant ?](section-8/8.q005.md)
- [Comment supprimer une branche ?](section-8/8.q006.md)
- [Comment supprimer une branche distante ?](section-8/8.q007.md)
- [Comment renommer une branche ?](section-8/8.q008.md)
- [Comment comparer deux branches ?](section-8/8.q009.md)
- [Comment comparer deux branches pour connaître les historiques des *commits* ?](section-8/8.q010.md)
- [Comment comparer deux branches pour connaître les contenus des *commits* ?](section-8/8.q011.md)
- [Comment comparer les historiques de deux branches ?](section-8/8.q012.md)
- [Comment comparer l'état de tous les fichiers présents dans deux branches ?](section-8/8.q013.md)
- [Comment comparer l'état d'un fichier présent dans deux branches ?](section-8/8.q014.md)

## 9 Les fusions de branches (*merge*)

- [Qu'est-ce qu'une fusion (*merge*) ?](section-9/9.q001.md)
- [Comment fusionner une branche `toto` dans une branche `master` ?](section-9/9.q001.md)
- [Quelle est la différence entre *merge fast-forward* et un *merge no-fast-forward* ?](section-9/9.q001.md)
- [Comment annuler une fusion terminée ?](section-9/9.q001.md)
- [Qu'est-ce qu'un conflit ?](section-9/9.q001.md)
- [Comment gérer un conflit ?](section-9/9.q001.md)
- [Comment annuler une fusion en cours ?](section-9/9.q001.md)

## 10 Réécriture de l'historique (`rebase`)

- [Qu'est-ce qu'un `rebase` ?](section-10/10.q001.md)
- [Pourquoi effectuer un `rebase` ?](section-10/10.q002.md)
- [Comment effectuer un `rebase` ?](section-10/10.q003.md)
- [Qu'est-ce qu'un `rebase` intéractif ?](section-10/10.q004.md)
- [Pourquoi effectuer un `rebase` intéractif ?](section-10/10.q005.md)
- [Comment effectuer un `rebase` intéractif ?](section-10/10.q006.md)
- [Comment annuler un `rebase` en cours ?](section-10/10.q007.md)
- [Comment résoudre un conflit lors d'un `rebase` ?](section-10/10.q008.md)

## 11 Les tags

- [Qu'est-ce qu'un tag ?](section-11/11.q001.md)
- [Comment créer une tag ?](section-11/11.q001.md)
- [Comment supprimer une tag ?](section-11/11.q001.md)
- [Comment renommer une tag ?](section-11/11.q001.md)
- [Comment lister les tags existants ?](section-11/11.q001.md)
- [Comment comparer deux tags ?](section-11/11.q001.md)
- [Comment comparer l'état d'un fichier présent dans deux tags ?](section-11/11.q001.md)

## 12 Les logs

- [Qu'est-ce que le log ?](section-12/12.q001.md)
- [Comment afficher le log ?](section-12/12.q002.md)
- [Comment afficher le log sous forme graphique dans la console ?](section-12/12.q003.md)
- [Comment afficher le log sur une seule ligne pour chaque commit ?](section-12/12.q004.md)
- [Comment afficher un changelog entre deux tags ?](section-12/12.q005.md)
- [Comment filtrer le log sur la base des messages de commit ?](section-12/12.q006.md)
- [Comment filtrer le log sur la base de l'auteur des commits ?](section-12/12.q007.md)
- [Comment afficher la liste des fichiers modifiés pour chaque commit du log ?](section-12/12.q008.md)
- [Comment trouver qui a modifié quelle ligne dans un fichier donné ? (`blame`)](section-12/12.q009.md)

## 13 Outils

- [GitHub](section-13/13.q001.md)
- [GitLab](section-13/13.q002.md)
- [Qu'elle est la différence entre une pull request (GitHub) et une merge request (GitLab) ?](section-13/13.q003.md)

## 14 Contribuer à un projet OpenSource

- [Quels sont les usages à respecter habituellement avant de proposer une contribution ?](section-14/14.q001.md)
- [Comment proposer un sujet de contribution ?](section-14/14.q002.md)
- [Pourquoi est-il nécessaire de forker le projet sur lequel on souhaite contribuer ?](section-14/14.q003.md)
- [Comment initialiser son dépôt local pour préparer une contribution ?](section-14/14.q004.md)
- [Quelles sont les étapes habituelles d'une contribution de code ?](section-14/14.q005.md)
- [Qu'est-ce que cela m'apporte de contribuer à un projet OpenSource ?](section-14/14.q006.md)
