# FAQ Git pour developpez.com

## 7.5 Contribuer à un projet OpenSource

### Quels sont les usages à respecter habituellement avant de proposer une contribution ?

Le fichier `README.md` du dépôt doit être lu en intégralité et très attentivement. Par convention c'est le point d'entrée documentaire de tout projet.
Il est affiché par défaut par les outils web type GitHub / GitLab lorsqu'on accède au dépôt du projet.
Les premières instructions pour utiliser le projet (installation des dépendances, compilation, exécution, ...) sont souvent rédigées dans ce fichier.
Ces informations sont généralement reprises sur le wiki du projet et sur le site de présentation si il en dispose.

Certains projets ont d'autres fichiers servant à rentrer plus dans le détail, souvent au format markdown, qu'il est utile de lire.
Parmi ces fichiers ont peut trouver :

- `CONTRIBUTE.md` ou `CONTRIBUTING.md`, certains projets proposent un fichier dédié aux informations liées aux contributions.
- `LICENSE.md`, important de savoir quelle sera la licence de votre contribution.
- `ISSUE_TEMPLATE.md`, un template pour la création d'issue. Il est de bon ton de le respecter !
- `PULL_REQUEST_TEMPLATE.md`, un template pour la création des Pull Request. De même il est de bon ton de le respecter !
- `CODE_OF_CONDUCT.md`, un code de conduite à tenir dans vos échanges avec les autres contributeurs. Il est parfois nécessaire de l'accepter en même temps que la première Pull Request.
- `CODING_STYLE.md`, décrit ou donne des liens décrivant le style de code à utiliser. Ce fichier est parfois associé à un linter qui sera exécuté dans l'intégration continue avec les tests.

### Comment proposer un sujet de contribution ?

Ouvrez une issue ! C'est le canal de discussion principal et c'est en quelque sorte la liste des tâches (le *backlog*) du projet.

Il vaut mieux proposer une contribution par ce biais avant de se lancer dans le code.
Inutile de perdre du temps à écrire du code si les mainteneurs du projet ne sont pas d'accord avec votre proposition.

Toutefois, s'il s'agit d'une modification mineure n'hésitez pas à proposer directement une Pull Request.

Certains projets utilisent beaucoup les outils communautaires type Discord, Slack, IRC. Il existe aussi [Gitter](https://gitter.im/) qui bénéficie d'une excellente intégration avec GitHub.
C'est un excellent moyen de prendre la température d'autant que les historiques de discussion sont souvent publics.

### Pourquoi est-il nécessaire de forker le projet sur lequel on souhaite contribuer ?

Cela simplifie considérablement la gestion des droits du dépôt principal pour les mainteneurs du projet.
Avec un fork les contributeurs n'écrivent pas sur le dépôt principal, ils écrivent des commits sur leur fork et la Pull Request est un merge de ce fork vers le dépôt central.

### Comment initialiser son dépôt local pour préparer une contribution ?

Après avoir lu entièrement la documentation et forké le dépôt principal il faut cloner sur votre machine le dépôt central : `git clone <url-depot>`.
Ensuite il faut ajouter à votre dépôt local votre fork en tant que dépôt distant : `git remote add <alias> <chemin/url>`.

Si vous fonctionnez de cette manière l'alias du dépôt distant principal sera `origin` et votre fork aura le nom que vous lui donnerez.
Personnellement j'appelle mon fork tout simplement `fork`.

On peut tout à fait faire l'inverse, c'est à dire cloner votre fork et ajouter le dépôt distant de référence.
C'est une question de nommage qui n'affecte que votre dépôt local. Faites comme vous le souhaitez.

### Quelles sont les étapes habituelles d'une contribution de code ?

Après avoir lu entièrement la documentation, forké le dépôt principal et initialisé votre dépôt local, vous pouvez commencer à écrire du code.

Attention, **on n'ajoute jamais de commit sur la branche de collaboration**. Si vous voyez une branche `master` ou parfois `develop`, n'écrivez pas dessus.
Vous devez créer une branche dédiée à vos modifications. Tout ceci est généralement documenté par le projet.

Si vous n'avez pas mis à jour votre dépôt local depuis quelques temps ou que le projet est très actif il faut commencer par récupérer les dernières mises à jour.

Si la branche de collaboration est `master`, assurez-vous d'être positionné sur `master` (`git checkout master`) puis récupérez l'état de cette branche via `git pull origin master`.

Créez ensuite votre branche de travail : `git checkout -b <nom-de-votre-branche`.

A ce stade vous pouvez librement écrire vos commits.

Une fois terminé, il faut rebaser votre travail. En effet vous avez pu passer plusieurs jours ou semaines à préparer votre contribution, et donc d'autres personnes auront probablement fait avancer `master`.

Il convient donc de récupérer leur travail : `git checkout master` puis `git pull origin master`.

Ceci fait retournez sur votre branche de travail (`git checkout <nom-de-votre-branche>`) et rebasez là avec master : `git rebase master`.

On peut également rebaser directement sa branche de travail sans tirer master via `git rebase origin/master`.
Attention il sera nécessaire de mettre à jour votre représentation locale du dépôt distant au préalable via `git fetch origin`.

Si vous avez des conflits fixez les, puis vous pouvez pousser votre branche sur votre fork : `git push fork <nom-de-votre-branche>`.

A ce stade, l'outil que vous utilisez pour collaborer vous proposera de créer une Pull Request (si GitHub) ou une Merge Request (si GitLab).

Une fois créée, c'est aux mainteneurs de travailler.
Selon comment ils fonctionnent et ont configuré leur projet, le fait d'avoir proposé une contribution a pu déclencher un job dans l'intégration continue.
Il convient de vérifier son résultat car si il est en erreur c'est à vous qu'il revient d'effectuer la correction, la Pull Request restera bloquée tant que la correction n'aura pas été effectuée.

Si tout va bien, les mainteneurs vont effectuer une revue de code de votre contribution. Restez attentif ils pourront vous proposer ou exiger des améliorations.

Notez qu'il est rare qu'une contribution (surtout les premières) soit acceptée au premier essai, il ne faut pas s'en offusquer le propre des Pull Request est d'échanger sur la collaboration apportée.

Si tout va bien vos commits seront ajoutés à la branche de collaboration.

Notez également que les mainteneurs demandent parfois de `squash` vos commits en un seul, un rebase intéractif suivi d'un `git push --force fork <nom-de-votre-branche>` sera nécessaire.
Sinon depuis peu les mainteneurs peuvent `squash` les commits eux-mêmes via l'interface web (sur GitHub comme sur GitLab).

### Qu'est-ce que cela m'apporte de contribuer à un projet OpenSource ?

Indépendamment de la fonctionnalité que vous ajoutez et de la contribution technique pure, cela améliorera sensiblement vos compétences sur Git.

Pouvoir montrer une contribution effectuée à un projet OpenSource c'est aussi mettre en avant :

- votre autonomie et votre esprit d'initiative notamment dans l'optique d'un télétravail.
- une capacité à s'adapter à un contexte de travail spécifique (les règles spécifiques du projet).
- une capacité à travailler à l'international (principalement en anglais).
