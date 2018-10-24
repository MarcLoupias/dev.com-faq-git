# FAQ Git pour developpez.com

## 7.5 Contribuer à un projet OpenSource

### Quels sont les usages à respecter habituellement avant de proposer une contribution ?

Le fichier `README.md` du dépôt doit être lu en intégralité et très attentivement. Par convention c'est le point d'entrée documentaire de tout projet.

La plupart des projets ont d'autres fichiers, souvent au format markdown, qu'il est utile de lire.
D'une manière générale il faut lire tout fichier texte présent à la racine du dépôt.

Parmi ces fichiers ont peut trouver :

- `CONTRIBUTE.md` ou `CONTRIBUTING.md`, certains projets proposent un fichier dédié aux informations liées aux contributions.
- `LICENSE.md`, important de savoir quelle sera la licence de votre contribution.
- `ISSUE_TEMPLATE.md`, un template pour la création d'issue. Il est de bon ton de le respecter !
- `PULL_REQUEST_TEMPLATE.md`, un template pour la création des Pull Request. De même il est de bon ton de le respecter !
- `CODE_OF_CONDUCT.md`, un code de conduite à tenir dans vos échanges avec les autres contributeurs. Il est parfois nécessaire de l'accepter en même temps que la première Pull Request.

### Comment proposer un sujet de contribution ?

Ouvrez une issue ! C'est le canal de discussion principal et c'est en quelque sorte le *backlog* (la liste des tâches) du projet.

Il vaut mieux proposer une contribution par ce biais avant de se lancer dans le code.
Inutile de perdre du temps à écrire du code si les mainteneurs du projet ne sont pas d'accord avec votre proposition.

### Pourquoi est-il nécessaire de forker le projet sur lequel on souhaite contribuer ?

Cela simplifie considérablement la gestion des droits du dépôt principal pour les mainteneurs du projet.

Avec un fork les contributeurs n'écrivent pas sur le dépôt principal, ils écrivent des commits sur leur fork et la Pull Request est un merge de ce fork vers le dépôt central.

Ainsi, cela permet à des inconnus de proposer des modifications à un projet sans que les mainteneurs n'aient besoin de configurer des droits sur le dépôt de référence.

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

Si vous avez des conflits fixez les, puis vous pouvez pousser votre branche sur votre fork : `git push fork <nom-de-votre-branche>`.

A ce stade, l'outil que vous utilisez pour collaborer vous proposera de créer une Pull Request (si GitHub) ou une Merge Request (si GitLab).

Une fois créée, c'est aux mainteneurs de travailler.
Selon comment ils fonctionnent et ont configuré leur projet, le fait d'avoir proposé une contribution a pu déclencher un job dans l'intégration continue.
Il convient de vérifier son résultat.

Si tout va bien, les mainteneurs vont effectuer une revue de code de votre contribution. Restez attentif ils pourront vous proposer ou exiger des améliorations.

Si tout va bien vos commits seront ajoutés à la branche de collaboration.

### Apprendre à contribuer à un projet OpenSource est-il utile pour ma carrière professionnelle ?

Oui ! Indépendamment de la contribution technique pure, cela améliorera sensiblement vos compétences sur Git, et ensuite de plus en plus d'entreprises fonctionnent en interne de la même manière pour collaborer.

Le mouvement DevOps incite fortement les entreprises à décloisonner leur organisation interne (casser les silos) en ouvrant les codes sources entre les services.

En effet dans les grands comptes les services sont souvent historiquement très cloisonnés, au point de se facturer en interne leurs prestations.
Il en va de même pour le code source. Souvent il n'est pas ouvert entre les services d'une même entreprise comme s'il s'agissait d'entreprises différentes.

Ces pratiques d'un autre âge nuisent considérablement à la productivité et à l'agilité du système d'information.

On peut donc véritablement parler de compétence en la matière, et cette compétence est de plus en plus souvent appréciée sinon demandée.

Pouvoir montrer une contribution effectuée à un projet OpenSource c'est prouver que vous êtes capable de collaborer de cette manière. Cela peut vous être demandé lors de vos entretiens.
