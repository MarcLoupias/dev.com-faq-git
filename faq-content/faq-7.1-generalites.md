# FAQ Git pour developpez.com

## 7.1 Généralités

### Qu'est ce que Git ?

Git est un système de contrôle de révision décentralisé.

Il a été écrit en 2005 à l'initiative de Linus Torvalds pour gérer les sources du kernel Linux.

### Que signifie Git ?

Il n'y a pas de réponses précises, on ne sait pas s'il s'agit d'un acronyme ou d'un mot. Le nom date de la toute première livraison du projet.
Le fichier [README du projet](https://github.com/git/git/blob/master/README.md) contient quelques explications.
En argot britannique il s'agit également d'une insulte.

### Où trouver de la documentation pour Git ?

Le site officiel est hébergé sur [https://git-scm.com/](https://git-scm.com/), la documentation est hébergée [au même endroit](https://git-scm.com/doc).

### Où trouver le code source de Git ?

Un miroir du code du projet est hébergé sur [GitHub](https://github.com/git/git).

### Quelles sont les différences entre un SCM centralisé comme Subversion et un SCM décentralisé comme Git ?

Elles sont trop nombreuses pour être listées dans une FAQ mais d'une manière générale :

- pas d'autorité centrale obligatoire
- un utilisateur clonant un projet dispose de la totalité de l'historique sur sa machine
- tout est fait offline
- il n'y a pas besoin d'un serveur central pour partager du code entre 2 développeurs

### Qu'est-ce qu'un dépôt Git ?

La traduction française appropriée de *repository* est *dépôt*.
Il s'agit d'un répertoire versionné par Git. Ce répertoire contient à sa racine un répertoire `.git` contenant toutes les données liées à ce dépôt.
Un dépôt Git est donc autoporté via ce répertoire et peut être déplacé depuis le répertoire racine (pour backup ou autre).
Aucune information nécessaire à l'usage du dépôt n'est stockée à l'extérieur.

Un dépôt Git correspond généralement à un projet unique mais ce n'est pas forcément le cas.
Certaines organisations utilisent un dépôt unique pour gérer les codes sources de tous leurs projets.
Cette stratégie est nommée la "monorepo strategy".
C'est notamment le cas de Google qui a expliqué en détail sa stratégie lors d'[une conférence en 2015](https://www.youtube.com/watch?v=W71BTkUbdqE).

Un dépôt est donc composé d'un répertoire `.git` et de la working directory.
Le répertoire `.git` contient toutes les meta-données du dépôt.
La working directory (le répertoire courant en fait) reflète l'état actuel `checkout` par Git (un commit, une branche ou un tag).

### Qu'est-ce qu'un remote ?

Il s'agit d'un dépôt nu (*bare repository* en anglais) servant d'espace de partage.
Il peut être local (si vous exposez vos sources depuis votre propre machine) ou distant.
Il est généralement accompagné d'un client web pour fournir une solution de gestion de projet intégrée (GitHub, GitLab, Gitblit, ...).

### Que désignent les termes upstream et downstream ?

Ces termes sont souvent employés dans les conversations en anglais à propos de Git et également dans sa documentation officielle.

*upstream* désigne le dépôt distant depuis lequel vous tirez des informations vers votre dépôt local (`clone`, `pull`, `fetch`, ...) ou vers lequel vous poussez des informations (`push`).

*downstream* désigne tous les repositories qui dépendent d'un *upstream* pour leur synchronisation.

Si par exemple vous avez un projet hébergé sur un site comme GitHub ou GitLab, le dépôt sur ce site est l'*upstream* et chaque dépôt cloné depuis l'*upstream* est un *downstream*.
