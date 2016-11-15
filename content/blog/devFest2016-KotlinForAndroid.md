+++
author = "Julien Zanon"
categories = ["Dev", "Kotlin", "Android"]
date = "2016-11-15T13:22:11+01:00"
description = "Develop a reactive Android app with Kotlin - Animé par Arnaud G."
linktitle = ""
title = "DevFest Toulouse 2016 - Kotlin for Android"
type = "post"
+++

## Présentation

Cette première présentation de la journée est une présentation technique.

Arnaud G. nous présente le language Kotlin comme une alternative tout à fait viable pour le développement d'applications Android.

Kotlin v1.0 est marqué "Production Ready" par son éditeur JetBrains.

Il requiert au minimum Java 6 pour le faire tourner.
Soit dit en passant, aujourd'hui, QUI aurait l'idée de se lancer dans un nouveau développement sans utiliser la dernière version de Java disponible?!

Après une rapide présentation de quelques fonctionnalités du language, Arnaud avance l'argument qui à mon sens, 
est primordial dans le choix de l'utilisation d'un nouveau language: la forte diminution du "boiler code".

En effet, Java traîne comme un boulet 20 ans de rétro-compatibilité et concessions: 
difficile de changer les choses vu les intérêts divergeant des forces en présence.


## En vrac

La trame de la présentation était bien construite, voici quelques unes de mes notes:

* Kotlin est intégré de base avec Gradle. 
* Une fonctionnalité sympa dans IntelliJ: "Convert Java File to Kotlin". 
Pas uniquement pour migrer de l'existant mais aussi pour découvrir le language: une façon d'apprendre.
* Mot-clé : `val` / `var`  pour la déclaration de valeur/variable.
On retrouve de plus en plus ce concept dans les languages. Encore une fois, Java est à la traîne.
* Null safety: utilisation de '?' et '!!':
 *  `?` semblable aux Optional de Java 8
 * `!!` jettera une exception NPE si une variable est `null`
* Les variables doivent avoir des valeurs par défaut.
L'utilisation de `lateinit` permet d'indiquer au compilateur que l'initialisation de la variable est différé.
Sans cela le code ne compilera même pas!
* L'écriture de l'équivalent "POJO + Getter + Setter + hashcode + Constructor + ..." est EXTREMEMENT réduite
* Le concept Java de `static` n'existe plus mais une sorte d'équivalent `companion`est proposé
(ce sujet mérite d'être approfondi...)
* Utilisation des paramètres nommés (et leur ordre n'est pas fixé!)
* Mot-clé `when` qui permet de se passer de `if` et `switch` qu'on connaît en Java.
Il offre en plus la possibilité de faire du parttern matching.
* La déclaration d'une fonction ne nécessite pas forcément l'encapsulation de celle-ci dans une classe
* Niveau lambda expression on est proche de ce que propose Java 8
* `Pair` pour gérer des paire d'élement. Quelque chose de si simple et pourtant absent de Java!
* Interopérable avec Java (là où Swift l'est avec C pour faire un parallèle)
* La gestion des exceptions se fait comme en Java

### Et Android dans tous ca?

Une extension Kotlin peut être ajoutée dans un projet Android.
Cette extension propose quelques fonctionnalités utiles comme:

* celle de se passer du `findViewById`
* permettre la programmation réactive: les composants peuvent interagir sans se bloquer les uns les autres

Malheureusement la démo préparée par Arnaud a partiellement planté,
mais bon l'idée, le code et l'explication étaient tous là ;-)


### Conclusion

J'ai choisi cette session plus pour l'aspect Kotlin que pour le coté Android du sujet et je n'ai pas été déçu.

C'est une parfaite introduction au language, les exemples de code sont clair et le discours aussi.

Désormais si l'on me demande la techno pour un dev Android,
Kotlin sera une alternative que j'étudierai sérieusement.
 
Les slides: https://speakerdeck.com/agiuliani/making-android-reactive-app-with-kotlin

Le speaker: [@arnogiu](https://twitter.com/arnogiu) sur Twitter



