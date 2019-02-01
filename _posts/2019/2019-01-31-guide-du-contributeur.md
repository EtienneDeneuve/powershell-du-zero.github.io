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

## Outils

Pour contribuer sur le bog du [Powershell du Zéro](https://powershell-du-zero.fr/), les outils suivants sont requis :

- [Ruby](https://rubyinstaller.org/)
- [Git](https://git-scm.com/)
- [Visual Studio Code](https://code.visualstudio.com/)

## Compétences

Ce point important mérite d'être clarifié rapidement.
Il n'y a absolument aucun niveau de compétence minimum requis pour contribuer sur le Powershell du Zéro.

Toutes les contributions seront relues et étudier et corrigé par le biais des outils de review de GitHub. **Lancez-vous !**

# Monter son environnement

Dans cette section nous allons voir comment mettre en place le dépôt (le code) et les dépendances.

## Dépôt

Nous hébergeons nos dépôts Git sur [Github](https://github.com/) à l'adresse suivante : [https://github.com/Powershell-du-Zero](https://github.com/Powershell-du-Zero)

Bien sûr, vous n'allez pas travailler directement sur le dépôt du Powershell du Zero parce que vous n'avez pas les permissions et c'est une mauvaise pratique. Vous devez doc **forker le dépôt**.
Un fork est copie du dépôt, permettant de faire ce que bon vous semble sans aucune restriction.
Pour forker un dépôt je ous pouvez utiliser l'interface de Github :

![guide-du-contributeur01](/assets/img/post/2019/guide-du-contributeur01.png)

Une fois que vous avez fork le projet, Github vous redirigera vers la copie de celui-ci:

![guide-du-contributeur02](/assets/img/post/2019/guide-du-contributeur02.png)

## Dépendances

### Ruby

Le moyen le plus simple d'installer Jekyll consiste à utiliser [RubyInstaller](https://rubyinstaller.org/) pour Windows.

### Jekyll

Ouvrez une nouvelle fenêtre d'invite de commande à partir du menu démarrer, de sorte que les modifications apportées à la variable d'environnement PATH prennent effet.

Installez Jekyll et Bundler via la commande suivante :

```bash
gem install jekyll bundler
```

Pour vérifiez si Jekyll est installé correctement:

```bash
jekyll -v
```

### Lancer une version Local du blog

Jekyll embarque le serveur [WEBrick](https://fr.wikipedia.org/wiki/WEBrick), il est donc possible de voir directement le blog grâce à la commande serve.
Cette commande va générer le blog et créer les fichiers statiques correspondants.

```bash
jekyll serve
```

Il maintenant possible de voir le blog dans un navigateur à cette adresse : **http://localhost:4000**

# Visual Studio Code

## Les principaux avantages de Code

Code est basé sur le même socle technique qu’Atom, mais la similitude s’arrête là…

- **Rapide** à lancer
- **Très rapide** à l’usage
- **Git** intégré (et plutôt pas mal, en plus)
- **Complétion de code** plutôt qualitative (mix définitions + inférence)
- Excellente UX de paramétrage
- Préférences de workspace, idéal pour partager des configurations
- Nombreuses **extensions** « indispensables » disponibles

## Installation

[Télécharge VS Code](https://code.visualstudio.com/) et exécute l’installeur, tout simplement.

## Extensions recommandées

Vous pouvez facilement obtenir la liste et installer manuellement juste en récupérant le dépôt du [Powershell du Zéro](https://powershell-du-zero.fr/) et en l’ouvrant dans VS Code : il te signalera que le dépôt propose des extensions et te proposera d’ouvrir la liste pour choisir les installations qui te conviennent.

| Extension / ID                                                                 | Description rapide                                                                                                             |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Bracket Pair Colorizer / ```coenraads.bracket-pair-colorizer```                | Cette extension permet d’identifier facilement les bracket avec des couleurs                                                  |
| Markdown All in One / ```yzhang.markdown-all-in-one```                         | Linter dédié à Markdown, qui repère les erreurs et risques courants et vérifie aussi la sémantique et la structure du document |
| vscode-icons / ```robertohuertasm.vscode-icons```                              | Un thème d’icônes nettement plus détaillé                                                                                     |
| Markdown Preview Github Styling / ```bierner.markdown-preview-github-styles``` | Un thème de prévisuliation permettant d'avoir le même thème que sur Github                                                     |

## Paramétrage recommandé

Les codebases que nous fournissons comme socle de travail sont équipées de réglages de projet (workspace settings) adaptés, qui ont priorité sur vos réglages génériques. Ces réglages sont présents dans le fichier ```.vscode/settings.json```

Vous pouvez tout a fait proposer des adaptations du workspace, via une pull request dédiée.

## La doc en ligne

Les [docs officielles](https://code.visualstudio.com/docs) regorgent de trucs utiles, mais j’attire principalement ton attention sur deux sections de ces docs :

- [Getting started](https://code.visualstudio.com/docs), qui reprend des contenus cités plus haut, mais en ajoute plein d’autres (thèmes, changement de la langue de l’éditeur, etc.)
- [User guide](https://code.visualstudio.com/docs/editor/codebasics), qui reprend pas à pas les points forts de Code, démos et illustrations à l’appui. On y trouve notamment des sujets avancés commes les multi-root workspaces.

# Le commit parfait

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
