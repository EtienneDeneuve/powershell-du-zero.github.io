---
layout: post
title: Gérer les stratégies d’exécution
date: 2019-01-20
author: Thomas ILLIET
post-cover: /assets/img/gerer-les-strategies-dexecution-06.png
tags: powershell securite gpo
---

Comme vous le savez sûrement, PowerShell dispose de certaines protections contre l’utilisation des scripts. Pour commencer, par défaut l’extension ".ps1" est associée a Notepad, afin de prévenir les utilisateurs d’une utilisation d’un script par simple double clic.

Ensuite, en fonction de votre système d’exploitation, l’exécution policy est limité par défaut :

* Windows 8.1, 10 et Server 2012 **(Restricted execution policy)**
* Windows 2012 R2 et 2016 **(RemoteSigned execution policy)**

Il est bien évidemment possible de changer votre *execution* *policy* avec la commande PowerShell Set-ExecutionPolicy ou par Group Policy.

Voici les différents modes existants :

* **Restricted** : cette politique interdit tout simplement l’exécution de n’importe quel script. Elle peut être appliquée dans le cas où vous ne feriez pas du tout de Powershell ou dans les environnements plus sensibles.
* **AllSigned** : autorise l’exécution des scripts signés par un éditeur approuvé (ce que nous verrons juste après).
* **RemoteSigned** : les scripts téléchargés doivent être signés par un éditeur approuvé avant leur exécution.
* **Unrestricted** (le mal): cette politique autorise l’exécution de tous les scripts Powershell, peu importe leur provenance. Ce mode représente une faille de sécurité non négligeable et n’est conseillé qu’en environnement de test.

Il est également possible de limiter la portée de cette *policy*

* **Process** : uniquement pour la session PowerShell en cours
* **CurrentUser** : uniquement pour l’utilisateur qui lance la commande
* **LocalMachine** : pour tous les utilisateurs du poste

```powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
```

Powershell est un outil très puissant et peut être dévastateur si un script malveillant est lancé sur votre infrastructure. Laisser la Politique d’exécution de script en *Unrestricted* n’est absolument pas recommandé.

Mais alors que faire ? Placer votre politique d’exécution en AllSigned et signer vous-même vos scripts semble être la meilleure solution.

## Mise en place

1. Exécutez **GPMC.msc**.
2. Sélectionnez l’OU (unité d’organisation) souhaitée, et faites un clic droit pour sélectionner **Create a GPO in this domain, and Link it here…**.

![gerer-les-strategies-dexecution-01](/assets/img/gerer-les-strategies-dexecution-01.png)

* Donnez un nom à la nouvelle GPO.

![gerer-les-strategies-dexecution-02](/assets/img/gerer-les-strategies-dexecution-02.png)

* Faites un clic droit et sélectionnez **Edit** sur la GPO fraîchement créée.

![gerer-les-strategies-dexecution-03](/assets/img/gerer-les-strategies-dexecution-03.png)

* Allez sous l’arborescence **Computer Configuration - Policies - Administrative Templates - Windows Components - Windows PowerShell**.

![gerer-les-strategies-dexecution-04](/assets/img/gerer-les-strategies-dexecution-04.png)

* Double cliquez sur le paramètre **Turn on Script Execution**, puis choisissez la stratégie d’exécution souhaitée.

![gerer-les-strategies-dexecution-05](/assets/img/gerer-les-strategies-dexecution-05.png)

* Enfin, fermez l’éditeur ...

## Conclusion

Vous voilà maintenant avec une GPO qui permet de définir la politique d'exécution de Powershell pour votre entreprise !

Enjoy ! 🙂
