# FAQ Git pour developpez.com

## 7.4 Outils

### GitHub

GitHub est la plus grosse plateforme mondiale d'hébergement web de dépôts Git.

L'entreprise [a été rachetée en juin 2018 par Microsoft](https://www.developpez.com/actu/207383/C-est-officiel-Microsoft-debourse-7-5-milliards-pour-s-offrir-GitHub-le-geant-de-Redmond-se-montre-plus-genereux-que-ce-que-disaient-les-rumeurs/).

GitHub s'utilise comme une solution SaaS hébergée dans le cloud. Il est possible d'héberger un serveur sur son réseau local mais cette solution est payante et relativement chère (plusieurs dizaines d'euros par utilisateur).

Par défaut tous les dépôts sont publics, il faut payer pour disposer de dépôts privés.

La solution propose un grand nombre de fonctionnalités, de manière non-exhaustive on trouve :

- les *issues* qui peuvent être utilisées comme un bug tracker ou/et comme un planificateur de tâches.
- les *milestones* qui permettent de relier les *issues* à une version en devenir.
- les *releases* qui permettent d'associer des tags à un *CHANGELOG* (bon de livraison).

La solution s'intègre aussi avec une grande quantité de services externes, intégration continue, code coverage, etc ...

Les tarifs de GitHub se trouvent [à cette adresse](https://github.com/pricing).

### GitLab

GitLab est le concurrent direct de GitHub bien qu'il couvre une surface fonctionnelle plus importante mais moins flexible (intégration moins importante avec les autres fournisseurs de services).

En effet GitLab ne se limite pas à la gestion du code source, il inclut tout le cycle de vie du projet, de la gestion du dépôt jusqu'au déploiement.

GitLab propose un service SaaS similaire à celui de GitHub mais il est également possible de le déployer sur un réseau local gratuitement.

Les tarifs de GitLab se trouvent [à cette adresse](https://about.gitlab.com/pricing/). L'hébergement de dépôts privés est gratuit.

### Qu'elle est la différence entre une pull request (GitHub) et une merge request (GitLab) ?

Conceptuellement il n'y a aucune différence, il s'agit simplement d'une question de point de vue pour nommer cette opération.

Sur une "pull request" on demande au mainteneur de tirer (`pull`) sa branche pour une relecture suivie d'une fusion (`merge`). La notion de fusion est implicite.

Sur une "merge request" on demande explicitement au mainteneur de gérer la demande de fusion.
