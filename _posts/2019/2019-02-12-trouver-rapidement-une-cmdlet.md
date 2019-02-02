---
layout: post
title:  Trouver rapidement une CmdLet
date: 2019-02-12
author: Thomas ILLIET
post-cover: /assets/img/banner/tips-tricks-cover.png
preview-cover: /assets/img/banner/tips-tricks-preview.png
tags: powershell
---

Comment trouver une cmdLet rapidement ? C'est une question que tout Administrateur s'est déjà posée !

Les commandes essentielles à absolument retenir sont **«[Get-Command](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/get-command)»** et **«[Get-Verb](https://docs.microsoft.com/fr-FR/powershell/module/microsoft.powershell.core/functions/get-verb)»**.

## Get-Verb

Que signifie selon vous ```Get-Verb``` ?

- **Get** = obtenir/voir
- **Verb** = verbe ? Oui !

Avec la commande ```Get-Verb``` vous retrouvez la liste complète des **«verbes»** + **«Groupes d’applications»** comme **«Common»** approuvés par Microsoft sur l’image suivante :

![gerer-les-strategies-dexecution-02](/assets/img/post/2019/trouver-rapidement-une-cmdlet-04.png)

## Get-Command

Cette commande permet découvrir toutes les **«commandes»** aussi que les **«alias»**  ou les **«fonctions»** de Powershell.

```powershell
Get-Commande
```

![trouver-rapidement-une-cmdlet-03](/assets/img/post/2019/trouver-rapidement-une-cmdlet-03.png)

> Mais si je veux afficher que les **«cmdlet»** ? Bonne question, comment savoir quels paramétrés ajouter ? Pour ça on va utiliser l’aide **«Get-Help»**.

## Get-Help

Comme son nom l'indique, cette commande affiche **«l’aide»**.
On sait afficher les commandes, mais pas que **«CmdLet»**, pour afficher **«l’aide»** intergé de Powershell.
Pour une commande, on peur utiliser commande **«Get-Help»** + **«la commande»** , comme dans notre cas on cherche savoir plus sur **«Get-Command»** .

```powershell
Get-Help Get-Command
```

![trouver-rapidement-une-cmdlet-02](/assets/img/post/2019/trouver-rapidement-une-cmdlet-02.png)

- **Pour consulter les exemples, tapez :** ```get-help Get-Command -examples```
- **Pour plus d’informations, tapez :** ```get-help Get-Command -detailed```
- **Pour obtenir des informations techniques, tapez :** ```get-help Get-Command -full```
- **Pour l’aide en ligne, tapez :** ```get-help Get-Command -online```

## Bonus

Voici une commande vous permettant de connaitre le nombre de CmdLet par type de **Verbe** :

```powershell
Get-Command | Group-Object -Property Verb | Sort-Object -Property count -Descending
```

![trouver-rapidement-une-cmdlet-01](/assets/img/post/2019/trouver-rapidement-une-cmdlet-01.png)
