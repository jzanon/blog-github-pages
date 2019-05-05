+++
author = "Julien Zanon"
categories = ["Dev", "Actor"]
date = "2016-11-20"
description = "Le modèle Acteur - Animé par Frédéric Cabestre."
linktitle = ""
title = "DevFest Toulouse 2016 - Les Acteurs, un modèle pour dompter le parallélisme"
type = "post"
draft = true
+++

## Présentation

// TODO

## Introduction

* Mise en contexte:
* Année 1990-2005:
** Course au MHz
** Processeurs sur mesure (non-standard)
** Quelques multi processeurs
==> atteinte du "Power wall" (ca chauffe trop)
==> Solution proposée : le multi-coeurs

Impact: mise en place de caches et les problèmes qui en découlent

## Abstraction

* Execution (Thread)
* Syncrhonisation (du très bas niveau à la sémaphore)
* Les verrous de niveau "abstrait" ammènent de nouvelles problématiques (deadlock, etc...)
* Quelques solutions:
** Thread pool
** Event loop (modèle utilisé par NodeJS)

* Premier language acteur avec une réussite industrielle:  Erlang qui a fait des petits, comme Elixir

## Acteur

* 1 reférence vers:
** une NAL (boite aux lettres) qui contient 1 etat & un comportement
* Activités:
** création d'autres acteurs
** envoi/reception de messages à d'autres acteurs
** changer de comportement (state machine)
* Le système (scheduler) prend 1 thread + 1 acteur (et sa BAL) et l'execute

* Resilience : gestion des etats des acteurs (gestion d'erreur)
* Transparence: ?

* Quelques bémols:
** Typage dynamique
** Pas forcément adapté à la conccurence
** Akka: c'est une framework
** Akka: appels bloquants (bloquage de la JVM en cas de surconsommation/lock de resource)


### Conclusion

// TODO
 
### Références

Les slides:

Le speaker:



