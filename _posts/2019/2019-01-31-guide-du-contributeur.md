---
layout: post
title: Guide du contributeur
description: Le Guide du contributeur galactique
date: 2019-01-31
post-cover: ''
preview-cover: ''
tags: communication
---

Avant de contribuer sur le blog du Powershell du Zéro, nous devons clarifier les prérequis en terme d'outillage, de compétences, et de gouvernance.
Ce dans le but de rendre toutes les contributions agréables et rapide !

# Pré-requis

![guide-du-contributeur11](/assets/img/post/2019/guide-du-contributeur11.png)

## Outils

Pour contribuer sur le bog du [Powershell du Zéro](https://powershell-du-zero.fr/), les outils suivants sont requis :

- [Docker](https://docs.docker.com/docker-for-windows/install/)
- [Ruby](https://rubyinstaller.org/)
- [Git](https://git-scm.com/)
- [Visual Studio Code](https://code.visualstudio.com/)

## Compétences

Ce point important mérite d'être clarifié rapidement.
Il n'y a absolument aucun niveau de compétence minimum requis pour contribuer sur le Powershell du Zéro.

Toutes les contributions seront relues, étudier et corrigé par le biais des outils de review de GitHub.

**Lancez-vous !**

# Monter son environnement

![guide-du-contributeur12](/assets/img/post/2019/guide-du-contributeur12.png)

Dans cette section nous allons voir comment mettre en place le dépôt (le code) et les dépendances.

## Dépôt

Nous hébergeons nos dépôts Git sur [Github](https://github.com/) à l'adresse suivante : [https://github.com/Powershell-du-Zero](https://github.com/Powershell-du-Zero)

Travailler sur le dépot du Powershell du Zero n'est pas faisable, il faudrait mettre trop de contributeur et poserait des problemes de sécurité et de gouverannce. Pour proposez votre article, vous devez donc faire un **fork du dépot**.

Un fork est copie du dépôt, permettant de faire ce que bon vous semble sans aucune restriction.
Pour forker un dépôt vous pouvez utiliser l'interface de Github :

![guide-du-contributeur01](/assets/img/post/2019/guide-du-contributeur01.png)

Une fois que vous avez forkez le projet, Github vous redirigera vers la copie de celui-ci:

![guide-du-contributeur02](/assets/img/post/2019/guide-du-contributeur02.png)

## Dépendances

Dans cette section nous allons voir comment mettre en place les dépendances afin de pour crée une version local du blog sur votre ordinateur. Vous aurez le choix entre une installation Manuelle ou via Docker.

### Docker

Nous recommandons **fortement** l'utilisation de docker pour effectuer le Lancement d'une version Local du blog. L'installation est vraiment très simple, il vous sufit juste de télécharger [docker pour windows](https://docs.docker.com/docker-for-windows/install/) et de l'installer sur votre ordinateur.

> Cette solution vous evitera d'avoir des problèmes avec les diférentes dépendances de Ruby.

### Manuelle

#### Ruby

Le moyen le plus simple d'installer Jekyll consiste à utiliser [RubyInstaller](https://rubyinstaller.org/) pour Windows.

#### Jekyll

Ouvrez une nouvelle fenêtre d'invite de commande à partir du menu démarrer, de sorte que les modifications apportées à la variable d'environnement ```PATH``` prennent effet.

Installez Jekyll et Bundler via la commande suivante :

```bash
gem install jekyll bundler
```

Pour vérifiez si Jekyll est installé correctement tapez la commande suivante :

```bash
bundle exec jekyll -v
```

### Lancer une version Local du blog

Jekyll embarque le serveur [WEBrick](https://fr.wikipedia.org/wiki/WEBrick), il est donc possible de voir directement le blog grâce à la commande serve.
Cette commande va générer le blog et créer les fichiers statiques correspondants.

#### Manuelle

```bash
bundle exec jekyll serve
```

#### Docker

```bash
docker-compose -f 'Docker-compose.yml' up
```

Il maintenant possible de voir le blog dans un navigateur à l'adresse suivante : **http://localhost:4000**

# Visual Studio Code

![guide-du-contributeur09](/assets/img/post/2019/guide-du-contributeur09.png)

## Les principaux avantages de Code

Code est basé sur le même socle technique qu’[Atom](https://atom.io/), mais la similitude s’arrête là…

- **Rapide** à lancer
- **Très rapide** à l’usage
- **Git** intégré (et plutôt pas mal, en plus)
- **Complétion de code** plutôt qualitative (mix définitions + inférence)
- Excellente UX de paramétrage
- Préférences de workspace, idéal pour partager des configurations
- Nombreuses **extensions** « indispensables » disponibles

## Installation

[Téléchargez VS Code](https://code.visualstudio.com/) et exécutez l’installeur, tout simplement.

## Extensions recommandées

Vous pouvez facilement obtenir la liste et installer manuellement les extensions recommandées juste en récupérant le dépôt du [Powershell du Zéro](https://powershell-du-zero.fr/) et en l’ouvrant dans VS Code : il vous signalera que le dépôt propose des extensions et vous proposera d’ouvrir la liste pour choisir les installations qui vous conviennent.

| Extension / ID                                                                 | Description rapide                                                                                                             |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Bracket Pair Colorizer / ```coenraads.bracket-pair-colorizer```                | Cette extension permet d’identifier facilement les bracket avec des couleurs                                                  |
| Markdown All in One / ```yzhang.markdown-all-in-one```                         | Linter dédié à Markdown, qui repère les erreurs et risques courants et vérifie aussi la sémantique et la structure du document |
| vscode-icons / ```robertohuertasm.vscode-icons```                              | Un thème d’icônes nettement plus détaillé                                                                                     |
| Markdown Preview Github Styling / ```bierner.markdown-preview-github-styles``` | Un thème de prévisuliation permettant d'avoir le même thème que sur Github                                                     |

## Paramétrage recommandé

Les codebases que nous fournissons comme socle de travail sont équipées de réglages de projet (workspace settings) adaptés, qui ont priorité sur vos réglages génériques. Ces réglages sont présents dans le fichier ```.vscode/settings.json```.

Vous pouvez tout a fait proposer des adaptations du workspace, via une pull request dédiée.

## La doc en ligne

Les [docs officielles](https://code.visualstudio.com/docs) regorgent de trucs utiles, mais j’attire principalement ton attention sur deux sections de ces docs :

- [Getting started](https://code.visualstudio.com/docs), qui reprend des contenus cités plus haut, mais en ajoute plein d’autres (thèmes, changement de la langue de l’éditeur, etc.)
- [User guide](https://code.visualstudio.com/docs/editor/codebasics), qui reprend pas à pas les points forts de Code, démos et illustrations à l’appui. On y trouve notamment des sujets avancés commes les multi-root workspaces.

## Les tâches

Code intègre une gestion d'éxécution de tache, qui permet d'effectuer rapidement des actions que nous avons préalablement configurer. Ces réglages sont présents dans le fichier ```.vscode/tasks.json```.

Donc afin d'ouvir le menu de recherche presser simultanement les touches ```CTRL``` + ```MAJ``` + ```P```, écrivez ensuite task afin de trouver "Tasks: Run Task"

![guide-du-contributeur05](/assets/img/post/2019/guide-du-contributeur05.png)

Code vous porpose maintenant une liste de tache a éxécuter

![guide-du-contributeur06](/assets/img/post/2019/guide-du-contributeur06.png)

Dans l'exemple d'éxécution ci-dessous, nous avons lancer la tache "Docker - Serve".

![guide-du-contributeur07](/assets/img/post/2019/guide-du-contributeur07.png)

# Le commit parfait

![guide-du-contributeur08](/assets/img/post/2019/guide-du-contributeur08.png)

Un bon message de commit doit permettre de savoir ce qui a changé et pourquoi.
Le comment c’est-à-dire la manière d’effectuer ces changements n’a pas à être expliqué.

Voici le format adopté par nos projets

```bash
<type>: <sujet>

<description>
```

On voit ici les différentes parties d’un commit et ce qu’elles doivent comporter. Voyons ces éléments dans le détail.
La première ligne comporte deux éléments : le type et le sujet. Voyons en quoi ils consistent.

## Type du commit

Nous utilisons [Gitmoji](https://gitmoji.carloscuesta.me/) afin de définir les types de commit.
Ce Projet vise à définir un style quant à l’usage des emojis dans les commit.

![guide-du-contributeur03](/assets/img/post/2019/guide-du-contributeur03.png)

Les emojis permettent de rapidement et visuellement transmettre du sens. De plus, un peu de fun dans les messages ne peut pas faire de mal.

## Le sujet

Le sujet contient une description **succincte** des changements.
En général, on se limite à 50 caractères.
De nombreux outils avertissent d’ailleurs lorsque l’on dépasse la longueur maximale.

![guide-du-contributeur04](/assets/img/post/2019/guide-du-contributeur04.png)

Pour adopter un style descriptif efficace, on utilise l’impératif présent : add, change, update, remove et non pas changed, removed, etc..

> Veuillez notez que le sujet doit etre toujours en anglais !

## Le corps du message

Beaucoup l’ignorent, mais les messages peuvent comporter un corps en markdown (pour le formatage :)) dans lequel on peut expliquer plus en détail la raison des changements.
De même que pour le sujet, on utilisera l’impératif présent.

# Créer des articles

![guide-du-contributeur10](/assets/img/post/2019/guide-du-contributeur10.png)

## Structure et organisation

Pour qu’un contenu ait du sens et soit cohérent, il faut déjà qu’il soit structuré.

### Organiser les sections

Il est possible et même conseillé de structurer vos sections en utilisant les balises titres de Markdown. Celles-ci sont au nombre de quatre :

```markdown
# Titre de niveau 1

## Titre de niveau 2

### Titre de niveau 3

#### Titre de niveau 4
```

En définitive, plus votre contenu sera structuré, plus il sera cohérent, dynamique et clair à suivre pour le lecteur.

## La mise en forme

La mise en forme d’un contenu n’est pas à négliger.

En effet, celle-ci permet de mettre en valeur certaines parties, de dynamiser la lecture ou encore d’illustrer le contenu.
Par exemple, un texte bien organisé et aéré donnera plus envie que le contraire n’est-ce pas ?

Ainsi, pour mettre en valeur un mot, nous pouvons le mettre en gras par exemple. Pour insérer une illustration, il suffit de l’importer dans la galerie et de se servir de la balise adéquate.
Ou encore, il est aussi possible d’ajouter des tableaux.
