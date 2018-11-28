# FAQ Git pour developpez.com

## 1 Généralités

- [Qu'est ce que Git ?](section-001/001.q001.md)
- [Que signifie Git ?](section-001/001.q002.md)
- [Où trouver de la documentation pour Git ?](section-001/001.q003.md)
- [Où trouver le code source de Git ?](section-001/001.q004.md)
- [Quelles sont les différences entre un SCM centralisé comme Subversion et un SCM décentralisé comme Git ?](section-001/001.q005.md)
- [Qu'est-ce qu'un dépôt (repository) Git ?](section-001/001.q006.md)
- [Qu'est-ce qu'un dépôt distant (*remote*) ?](section-001/001.q007.md)
- [Que désignent les termes upstream et downstream ?](section-001/001.q008.md)

## 2 Installation et configuration

- [Comment installer Git sur Windows ?](section-002/002.q001.md)
- [Comment installer Git sur macOS ?](section-002/002.q002.md)
- [Comment installer Git sur Linux ?](section-002/002.q003.md)
- [Comment connaitre la liste des commandes Git ?](section-002/002.q004.md)
- [Comment connaitre la version de votre Git ?](section-002/002.q005.md)
- [Quels sont les fichiers de configuration de Git ?](section-002/002.q006.md)
- [Comment afficher la configuration courante de Git ?](section-002/002.q007.md)
- [Comment exclure des fichiers ?](section-002/002.q008.md)
- [Comment changer son nom d'utilisateur ?](section-002/002.q009.md)
- [Comment changer son email ?](section-002/002.q010.md)
- [Comment changer l'URL d'un dépôt distant ?](section-002/002.q011.md)

## 3 Initialisation d'un dépôt

- [Comment initialiser un dépôt ?](section-003/003.q001.md)
- [Comment initialiser un dépôt nu (*bare repository*) ?](section-003/003.q002.md)
- [Comment cloner un dépôt ?](section-003/003.q003.md)
- [Comment connaitre l'état du dépôt ?](section-003/003.q004.md)

## 4 Les dépôts distants (*remotes*)

- [Comment lister les dépôts distants d'un dépôt ?](section-004/004.q001.md)
- [Comment ajouter un dépôt distant ?](section-004/004.q002.md)
- [Comment inspecter un dépôt distant ?](section-004/004.q003.md)
- [Comment supprimer un dépôt distant ?](section-004/004.q004.md)
- [Comment renommer un dépôt distant ?](section-004/004.q005.md)
- [Comment mettre à jour la représentation locale d'un dépôt distant (`fetch`) ?](section-004/004.q006.md)
- [Comment mettre à jour une branche locale avec une branche distante (`pull`) ?](section-004/004.q007.md)
- [Comment mettre à jour un dépôt distant (`push`) ?](section-004/004.q008.md)

## 5 Le répertoire de travail (*working directory*)

- [Qu'est-ce que le répertoire de travail (*working directory*) ?](section-005/005.q001.md)
- [Comment changer l'état du répertoire de travail ?](section-005/005.q002.md)
- [Comment connaitre l'état du répertoire de travail selon Git ?](section-005/005.q003.md)
- [Comment annuler les modifications effectuées sur un fichier du répertoire de travail ?](section-005/005.q004.md)
- [Que veut dire `"detached HEAD" state` après avoir effectué un `git checkout` ?](section-005/005.q005.md)
- [Quel est l'intérêt de faire un *checkout* sur un tag ?](section-005/005.q006.md)

## 6 L'index (*staging area*)

- [Qu'est ce que l'index ?](section-006/006.q001.md)
- [Comment ajouter un fichier à l'index ?](section-006/006.q002.md)
- [Comment retirer un fichier de l'index ?](section-006/006.q003.md)

## 7 Les commits

- [Qu'est ce qu'un *commit* ?](section-007/007.q001.md)
- [Comment créer un *commit* ?](section-007/007.q002.md)
- [Comment ajouter un message en créant un *commit* ?](section-007/007.q003.md)
- [Comment modifier le message d'un *commit* existant ?](section-007/007.q004.md)
- [Comment supprimer le dernier *commit* de la branche courante sans perdre les modifications ?](section-007/007.q005.md)
- [Comment supprimer le dernier *commit* de la branche courante avec les modifications ?](section-007/007.q006.md)
- [Comment supprimer les "n" derniers *commits* de la branche courante sans perdre les modifications ?](section-007/007.q007.md)
- [Comment supprimer les "n" derniers *commits* de la branche courante avec les modifications ?](section-007/007.q008.md)
- [Comment ajouter un *commit* d'une branche A dans une branche B sans effectuer un merge (*cherry-pick*) ?](section-007/007.q009.md)
- [Comment ajouter un *commit* provenant d'une branche d'un autre dépôt à la branche courante de ce dépôt (*cherry-pick*) ?](section-007/007.q010.md)
- [Comment annuler un *commit* existant (*revert*) ?](section-007/007.q011.md)

## 8 Les branches

- [Qu'est-ce qu'une branche ?](section-008/008.q001.md)
- [Comment lister les branches locales ?](section-008/008.q002.md)
- [Comment lister toutes les branches (locales, distantes, traquées, non-traquées) ?](section-008/008.q003.md)
- [Comment créer une branche ?](section-008/008.q004.md)
- [Comment créer une branche sur une dépôt distant ?](section-008/008.q005.md)
- [Comment supprimer une branche ?](section-008/008.q006.md)
- [Comment supprimer une branche distante ?](section-008/008.q007.md)
- [Comment renommer une branche ?](section-008/008.q008.md)
- [Comment comparer deux branches ?](section-008/008.q009.md)
- [Comment comparer deux branches pour connaître les historiques des *commits* ?](section-008/008.q010.md)
- [Comment comparer deux branches pour connaître les contenus des *commits* ?](section-008/008.q011.md)
- [Comment comparer les historiques de deux branches ?](section-008/008.q012.md)
- [Comment comparer l'état de tous les fichiers présents dans deux branches ?](section-008/008.q013.md)
- [Comment comparer l'état d'un fichier présent dans deux branches ?](section-008/008.q014.md)

## 9 Les fusions de branches (*merge*)

- [Qu'est-ce qu'une fusion (*merge*) ?](section-009/009.q001.md)
- [Comment fusionner une branche `toto` dans une branche `master` ?](section-009/009.q001.md)
- [Quelle est la différence entre *merge fast-forward* et un *merge no-fast-forward* ?](section-009/009.q001.md)
- [Comment annuler une fusion terminée ?](section-009/009.q001.md)
- [Qu'est-ce qu'un conflit ?](section-009/009.q001.md)
- [Comment gérer un conflit ?](section-009/009.q001.md)
- [Comment annuler une fusion en cours ?](section-009/009.q001.md)

## 10 Réécriture de l'historique (*rebase*)

- [Qu'est-ce qu'un *rebase* ?](section-010/010.q001.md)
- [Pourquoi effectuer un *rebase* ?](section-010/010.q002.md)
- [Comment effectuer un *rebase* ?](section-010/010.q003.md)
- [Qu'est-ce qu'un *rebase* intéractif ?](section-010/010.q004.md)
- [Pourquoi effectuer un *rebase* intéractif ?](section-010/010.q005.md)
- [Comment effectuer un *rebase* intéractif ?](section-010/010.q006.md)
- [Comment annuler un *rebase* en cours ?](section-010/010.q007.md)
- [Comment résoudre un conflit lors d'un *rebase* ?](section-010/010.q008.md)

## 11 Les tags

- [Qu'est-ce qu'un tag ?](section-011/011.q001.md)
- [Comment créer une tag ?](section-011/011.q001.md)
- [Comment supprimer une tag ?](section-011/011.q001.md)
- [Comment renommer une tag ?](section-011/011.q001.md)
- [Comment lister les tags existants ?](section-011/011.q001.md)
- [Comment comparer deux tags ?](section-011/011.q001.md)
- [Comment comparer l'état d'un fichier présent dans deux tags ?](section-011/011.q001.md)

## 12 Les logs

- [Qu'est-ce que le log ?](section-012/012.q001.md)
- [Comment afficher le log ?](section-012/012.q002.md)
- [Comment afficher le log sous forme graphique dans la console ?](section-012/012.q003.md)
- [Comment afficher le log sur une seule ligne pour chaque commit ?](section-012/012.q004.md)
- [Comment afficher un changelog entre deux tags ?](section-012/012.q005.md)
- [Comment filtrer le log sur la base des messages de commit ?](section-012/012.q006.md)
- [Comment filtrer le log sur la base de l'auteur des commits ?](section-012/012.q007.md)
- [Comment afficher la liste des fichiers modifiés pour chaque commit du log ?](section-012/012.q008.md)
- [Comment trouver qui a modifié quelle ligne dans un fichier donné ? (`blame`)](section-012/012.q009.md)

## 13 Outils

- [GitHub](section-013/013.q001.md)
- [GitLab](section-013/013.q002.md)
- [Qu'elle est la différence entre une pull request (GitHub) et une merge request (GitLab) ?](section-013/013.q003.md)

## 14 Contribuer à un projet OpenSource

- [Quels sont les usages à respecter habituellement avant de proposer une contribution ?](section-014/014.q001.md)
- [Comment proposer un sujet de contribution ?](section-014/014.q002.md)
- [Pourquoi est-il nécessaire de forker le projet sur lequel on souhaite contribuer ?](section-014/014.q003.md)
- [Comment initialiser son dépôt local pour préparer une contribution ?](section-014/014.q004.md)
- [Quelles sont les étapes habituelles d'une contribution de code ?](section-014/014.q005.md)
- [Qu'est-ce que cela m'apporte de contribuer à un projet OpenSource ?](section-014/014.q006.md)
