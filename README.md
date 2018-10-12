# dev.com-faq-git

FAQ - fr : Foire Aux Questions - en : Frequently Asked Questions

[Appel à contribution pour une section Git dans la FAQ SCM](https://www.developpez.net/forums/d1844867/general-developpement/alm/contribuez/appel-contribution-section-git-faq-scm/)

A insérer avec les autres FAQ des SCM : https://alm.developpez.com/faq/scm

-----

## 7.1 [Généralités](faq-7.1-generalites.md)

- Qu'est ce que GIT ?
- Que signifie GIT ?
- Où trouver de la documentation pour GIT ?
- Où trouver le code source de GIT ?
- Quelles sont les différences entre un SCM centralisé comme Subversion et un SCM décentralisé comme GIT ?
- Qu'est-ce qu'un dépôt GIT ?
- Qu'est-ce qu'un remote ?
- Que désignent les termes upstream et downstream ?

## 7.2 [Installation et configuration](faq-7.2-install-config.md)

- Comment installer GIT sur Windows ?
- Comment connaitre la liste des commandes GIT ?
- Comment connaitre la version de votre GIT ?
- Quels sont les fichiers de configuration de GIT ?
- Comment afficher la configuration courante de GIT ?
- Comment exclure des fichiers ?
- Comment changer son nom d'utilisateur ?
- Comment changer son email ? 
- Comment changer l'URL d'un dépôt distant ?

## 7.3 Utilisation

## 7.3.1 [Initialisation d'un dépôt](faq-7.3.1-initialisation-repository.md)

- Comment initialiser un dépôt ?
### Comment initialiser un dépôt nu (*bare repository*) ?
- Comment cloner un dépôt ?
- Comment connaitre l'état du dépôt ? 

## 7.3.2 [Les remotes](faq-7.3.2-remotes.md)

- Comment lister les remotes d'un dépôt ?
- Comment ajouter un remote ?
- Comment inspecter un remote ?
- Comment supprimer un remote ?
- Comment renommer un remote ?
- Comment mettre à jour la représentation locale d'un remote ? (fetch)
- Comment mettre à jour une branche locale avec une branche distance ?
- Comment mettre à jour un remote ? (push)

## 7.3.3 [La working directory](faq-7.3.3-working-directory.md)

- Qu'est-ce que la working directory ?
- Comment changer l'état de la working directory ?
- Comment connaitre l'état de la working directory selon git ?
- Comment annuler les modifications effectuées sur un fichier de la working directory ?

## 7.3.4 [La zone de stagging](faq-7.3.4-zone-staging.md)

- Qu'est ce que la zone de stagging ?
- Comment ajouter un fichier à la zone de stagging ?
- Comment retirer un fichier de la zone de stagging ?

## 7.3.5 [Les commits](faq-7.3.5-les-commits.md)

- Qu'est ce qu'un commit ?
- Comment créer un commit ?
- Comment ajouter un message en créant un commit ?
- Comment modifier le message d'un commit existant ?
- Comment supprimer le dernier commit de la branche courante sans perdre les modifications ?
- Comment supprimer le dernier commit de la branche courante avec les modifications ?
- Comment supprimer les "n" derniers commits de la branche courante sans perdre les modifications ?
- Comment supprimer les "n" derniers commits de la branche courante avec les modifications ?
- Comment ajouter un commit d'une branche A dans une branche B sans effectuer un merge ? (cherry-pick)
- Comment ajouter un commit provenant d'une branche d'un autre dépôt à la branche courante de ce dépôt ? (cherry-pick)
- Comment annuler un commit existant ? (revert)

## 7.3.6 [Les branches](faq-7.3.6-les-branches.md) 

- Qu'est-ce qu'une branche ?
- Comment lister les branches locales ?
- Comment lister toutes les branches (locales, distantes, traquées, non-traquées) ?
- Comment créer une branche ?
- Comment créer une branche sur une dépôt distant ?
- Comment supprimer une branche ?
- Comment supprimer une branche distante ?
- Comment renommer une branche ?
- Comment comparer deux branches ?
- Comment comparer les historiques de 2 branches ?
- Comment comparer l'état de tous les fichiers présents dans deux branches ?
- Comment comparer l'état d'un fichier présent dans deux branches ?

## 7.3.7 [Les fusions de branches (`merge`)](faq-7.3.7-merge.md)

- Qu'est-ce qu'un `merge` ?
- Comment fusionner une branche `toto` dans une branche `master` ?
- Quelle est la différence entre `merge` *fast-forward* et un `merge` *no-fast-forward* ?
- Comment annuler une fusion terminée ?
- Qu'est-ce qu'un conflit ?
- Comment gérer un conflit ?
- Comment annuler une fusion en cours ?

## 7.3.8 [Réécriture de l'historique (`rebase`)](faq-7.3.8-rebase.md)

- Qu'est-ce qu'un `rebase` ?
- Pourquoi effectuer un `rebase` ?
- Comment effectuer un `rebase` ?
- Qu'est-ce qu'un `rebase` intéractif ?
- Pourquoi effectuer un `rebase` intéractif ?
- Comment effectuer un `rebase` intéractif ?
- Comment annuler un `rebase` en cours ?
- Comment résoudre un conflit lors d'un `rebase` ?

## 7.3.9 [Les tags](faq-7.3.9-tags.md)

- Qu'est-ce qu'un tag ?
- Comment créer une tag ?
- Comment supprimer une tag ?
- Comment renommer une tag ?
- Comment lister les tags existants ?
- Comment comparer deux tags ?
- Comment comparer l'état d'un fichier présent dans deux tags ?

## 7.3.10 [Les logs](faq-7.3.10-logs.md)

- Qu'est-ce que le log ?
- Comment afficher le log ?
- Comment afficher le log sous forme graphique dans la console ?
- Comment afficher le log sur une seule ligne pour chaque commit ?
- Comment afficher un changelog entre deux tags ?
- Comment filtrer le log sur la base des messages de commit ?
- Comment filtrer le log sur la base de l'auteur des commits ?
- Comment afficher la liste des fichiers modifiés pour chaque commit du log ?
- Comment trouver qui a modifié quelle ligne dans un fichier donné ? (`blame`)

## 7.4 [Outils](faq-7.4-outils.md)

- GitHub
- GitLab
- Qu'elle est la différence entre une pull request (GitHub) et une merge request (GitLab) ?

