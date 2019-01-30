---
layout: post
title: Passer une variable $Null à un paramètre du type Boolean
description: Rencontre du 3ème type de Boolean
date: 2019-01-29
author: Thomas ILLIET
post-cover: /assets/img/banner/tips-tricks-cover.png
preview-cover: /assets/img/banner/tips-tricks-preview.png
tags: powershell fonction type parametre
---

Aujourd'hui, j'ai eu une découverte intéressante sur l'un de mes projets **PowerShell DSC**, concernant l'utilisation des paramètres de type [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean).

Le problème que j'ai rencontré était centré sur faite d'avoir un paramètre facultatif de type [boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean).
Je veux donc m'assurer que les seules options valides sont **$true** ou **$false**.
Tout fonctionnait parfaitement jusqu'à ce que je réalise qu'il y avait en réalité une autre option possible…

Avant de pouvoir comprendre le problème, nous devons étudier le comportement du script suivant :

```powershell
Function Test-ParamBoolean
{
  param(
    [System.boolean]
    $TestCase
  )
  Write-Output "The test case is $TestCase"
}
```

Quand j'exécute cette **fonction** sur mon environnement de test, je constate rapidement que si je passe le paramètre ```TestCase``` avec **$true** ou **$false**, cette fonction retournera exactement ce que j'attendais, mais si je ne passe pas de paramètre la fonction retournera **$false**.

> N'oubliez pas qu'un type booléen est un switch et peut être activé ou désactivé.

![comment-passer-une-variable-null-a-un-parametre-du-type-booleen-01](/assets/img/posts/comment-passer-une-variable-null-a-un-parametre-du-type-booleen-01.png)

Comment pouvons-nous permettre la valeur **$null** en plus des valeur **$True** et **$False** pour le paramètre ```TestCase```.

J'ai donc trouvé qu'il y avait l'option ```[AllowNull()]``` qui pouvait être ajoutée à mon paramètre. Ceci n’a pas fonctionné et m’a donné les mêmes résultats.

Après quelques recherches, j'ai trouvé un article intéressant sur une classe .NET [Nullable (T) Struct](https://docs.microsoft.com/en-us/dotnet/api/system.nullable-1).
grâce à cet article j'ai rapidement compris je pouvais placer a l'intérieur de ```[System.Nullable]``` le type ```[System.Boolean]```, ce qui me permet enfin de pouvoir gérer ```$true```, ```$false``` et ```$null```.


```powershell
Function Test-ParamBoolean
{
  param(
    [System.Nullable[System.boolean]]
    $TestCase
  )
  if( -not [string]::IsNullOrEmpty($TestCase) )
  {
    Write-Output "The test case is $TestCase"
  }
  else
  {
    Write-Output "Hey buddy, I don't read minds!"
  }
}
```

![comment-passer-une-variable-null-a-un-parametre-du-type-booleen-02](/assets/img/posts/comment-passer-une-variable-null-a-un-parametre-du-type-booleen-02.png)

Je me suis rapidement rendu compte que j'avais besoin de modifier le comportement de base de mon paramètre, en effet celui-ci renvoie ```$null``` alors que mon script powershell a besoin que cette variable soit a ```$false``` par défaut !

Voici donc ci-dessous la modification que j'ai effectuée pour résoudre ce problème :

```powershell
Function Test-ParamBoolean
{
  param(
    [System.Nullable[System.boolean]]
    $TestCase = $false
  )
  if( -not [string]::IsNullOrEmpty($TestCase) )
  {
    Write-Output "The test case is $TestCase"
  }
  else
  {
    Write-Output "Hey buddy, I don't read minds!"
  }
}
```

![comment-passer-une-variable-null-a-un-parametre-du-type-booleen-03](/assets/img/posts/comment-passer-une-variable-null-a-un-parametre-du-type-booleen-03.png)
