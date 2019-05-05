+++
author = "Julien Zanon"
categories = ["Dev", "Conférence"]
date = "2019-05-05"
description = "Retour sur quelques confs"
linktitle = ""
title = "Devoxx France 2019"
type = "post"
+++

2 ans et demi plus tard je publie enfin un nouveau post sur mon blog poussiéreux.

Afin de le représenter, le [Toulouse JUG](http://www.toulousejug.org/) m'a offert une place cette année à Devoxx France. 
J'ai donc pu participer pour la première fois à ce super évènement et vous propose un petit retour basé sur ce que j'ai pu voir.
Je ne parlerai ici que des conférences et pas des rencontres, de l'ambiance, des BoF... 
Il y a énormément de conférences en parallèle, toutes filmées donc l'idée est juste de vous aider à **mieux choisir vos vidéos une fois qu'elles seront disponibles sur Youtube.**


## Université: Java keeps throttling up!

On fait le point sur Java et son futur. De belles choses sont à venir, c'est une bonne session pour en avoir un panorama.

* OpenJDK Project Metropolis: pourquoi re-écrire la JVM en Java? 

La JVM est en partie écrite en C++, avec des partie en Java. 
La ré-écrire en pur Java permettrait d'avoir un IDE et de profiter de tout l'outillage de l'éco-système pour la faire vivre.
Car lorsqu'on prévoit 1 release tous les 6 mois, il faut s'outiller!

Au final, grâce à Graal on pourra obtenir pour l'execution de la JDK du code assembleur équivalent au C++ compilé.


* Project Valhalla: "value type"

Explication puis démonstration intéressante permettant de constater le gain en performance qu'apporte la mise en place de "value class". 


* Project Loom ou "Jouons avec la stack"

Héritage des *actors* de Erlang: l'idée est de remonter le scheduling des threads dans la JVM: c'est le "continuation model".

L'utilisation de `Continuation` + `yield` nécessite de modifier l'ensemble du code.

Les `Fiber`, c'est magique! On code comme avant (sauf qu'on utilise des Fibers à la place des threads) et la JVM détecte qu'on est dans un Fiber.
L'avantage c'est que lorsqu'il y a un appel bloquant (I/O par exemple) alors la JVM fait automatiquement un `yield`.


* Project Amber: le fourre-tout
 * Mise en place du Pattern-matching en tant qu'expression. 
 * Data class: pas d'intérêt à l'exécution mais à la lecture
 * Mot-clé `record` : définit un objet immutable ( ca aide pour le pattern matching )
 * Ajout du mot-clé `sealed` que l'on connaît déjà en Kotlin.
 

Lien cfp : https://cfp.devoxx.fr/2019/talk/OXO-1187/Java_keeps_throttling_up!


## Conf: Junit, il serait temps de passer la 5ème

Présentée à 2 sous la forme d'une discussion technique que l'on pourrait tout naturellement avoir lors d'une session de pair programming,
cette session nous a montré la migration de tests JUnit 4 vers JUnit 5. Bien calibrée (même si le ton était souvent un peu forcé), très pédagogique, **j'ai beaucoup aimé!**

Lien cfp : https://cfp.devoxx.fr/2019/talk/TPC-2275/JUnit_:_il_serait_temps_de_passer_la_5eme_!


## Conf: Les multiples facettes du logging dans un container Docker

J'avoue cette conf à 18H30, je n'avais pas prévu de la voir. Mais j'étais fatigué et déjà sur place dans les fauteuils confortables de l'amphi principal...
Mais Nicolas Fränkel a su capter mon attention avec plein de petites démos toutes simples (simples parce qu'il avait bien préparé ses images Docker ;-)).
Le point que j'ai noté qui me conforte dans mon idée: aucun système complexe ne devrait tourner en prod sans agrégation des logs dans un système dédié.

Lien cfp : https://cfp.devoxx.fr/2019/talk/VUH-8553/Les_multiples_facettes_du_logging_dans_un_container_Docker


## Conf: SpringBoot avec Kotlin, Kofu et les coroutines

Sébastien DELEUZE nous a fait une conf pleine de code & de démo. J'ai réussi à suivre mais j'avoue avoir été à la limite du décrochage.
Ne vous y trompez pas: c'était bien, intéressant, mais je pense qu'il aurait fallu prendre plus de temps pour cette conf. Dommage.

Lien cfp : https://cfp.devoxx.fr/2019/talk/CWE-1971/Spring_Boot_avec_Kotlin,_Kofu_et_les_Coroutines


## Conf: The boring architecture ou comment construire une licorne sur un monolithe

Doctolib nous a présenté son domaine et son architecture. 
L'architecture repose sur du React pour le front, du Ruby-on-Rails pour l'applicatif
et PostgreSQL pour la base de données, avec un peu d'ElasticSearch pour le fulltext search. En très forte croissance (en terme d'utilisateurs et de charge), 
ils ont fait le choix radical de résister à la hype: toute amélioration de perf/fonctionnalité doit se faire avec la stack actuelle.
On lit la doc des outils, on se fait aider au besoin, on pousse la stack dans ses retranchements AVANT d'aller chercher un nouvel outil ou une nouvelle lib.
Au passage on ne se refuse pas de la scalabilité verticale pour se donner du souffle! 
Conf agréable à suivre!

Lien cfp : https://cfp.devoxx.fr/2019/talk/NQH-8951/The_Boring_Architecture,_ou_comment_construire_une_licorne_sur_un_monolith


## Conf: Ask The Java Architect

Mark Reinhold nous a offert un moment de détente très agréable: une séance de questions libres...
Il nous a par exemple confié que s'il y avait une chose dans la rétro-compatibilité de Java qu'il devait "casser" c'est bien la Serialization.
Bien que les `checked exceptions` soient elles aussi en bonne position!

Lien cfp : https://cfp.devoxx.fr/2019/talk/GNN-3371/Ask_the_Java_Architect

## Conf: D'architecte à métarchitecte: une évolution nécessaire

J'ai entendu quelqu'un dire que cette conf résonnait comme "le cri d'agonie d'un archi qui essaye de sauver son poste car il se retrouve dépassé par les agilistes".
Alors NON: Je ne suis pas d'accord du tout. J'espère que c'est le seul à avoir eu ce ressenti car cette conf m'a parlé... Vraiment! 
Peut-être fais-je déjà partie des "vieux" architectes et suis-je comme lui? Je ne le crois pas. 
Je me défini depuis quelques années comme "senior developer" et comme le dit Rémi COCULA, parfois on se *sent architecte*.
Je trouve qu'il a bien saisi cette "crise d'identité" des architectes débutée dans les années 2010 qui a terni ce titre.
Pourtant il insiste sur la nécessité de l'architecte, pas dans son ancienne forme imposant la vérité mais dans l'échange avec les équipe et le travail aidant à faire émerger l'architecture de l'équipe, sans l'imposer.
Bref, bon speaker & très bonne conf.

Lien cfp : https://cfp.devoxx.fr/2019/talk/SQO-0767/D%E2%80%99architecte_a_Metarchitecte_:_une_evolution_necessaire


## Tools-in-action: Construire son JDK en 10 étapes

Un peu déçu par cette session de José Paumard: il n'y a rien eu de "in-action".
Ce manque de démo peut s'expliquer par le fait que la compilation du JDK prend énormément de temps et surtout que les différentes étapes n'ont rien d'extraordinaire.
Ce qu'il faut retenir c'est que quand il fallait près de 6 mois pour packager un JDK on fait maintenant ça en quelques heures.
Cette amélioration du processus de build a permis la mise en place d'une chaîne d'Intégration Continue mettant les derniers builds à disposition de la communauté 
au travers d'[adoptopenjdk](https://adoptopenjdk.net/). 
Mais ce n'est pas tout: sans ça, il aurait été impossible de planifier une release officielle de Java tous les 6 mois !

Un Quickie aurait peut-être été un meilleur format pour cette session.

Lien cfp : https://cfp.devoxx.fr/2019/talk/IDC-9031/Contruire_son_JDK_en_10_etapes


## Tools-in-action: Intro à Apache Pulsar

Aucune démo. Juste des slides de présentation du produit. Je ne suis pas allé à Devoxx pour ça...

Lien cfp : https://cfp.devoxx.fr/2019/talk/MWG-3581/Introduction_a_Apache_Pulsar


## Tools-in-action: La boite à outils Chaos engineeging du Javaiste

Présentation du Chaos engineering, de l'intégration de la lib Chaos Monkey dans SpringBoot puis de l'outil Toxi-Proxy.
Le tout sous la forme de démos. Exactement ce que l'on peut attendre de ce genre de session!

Lien cfp : https://cfp.devoxx.fr/2019/talk/JYD-8305/la_boite_a_outils_Chaos_Engineering_du_Javaiste

## Divers

Quelques conférences que j'ai apprécié sans prendre de notes particulières, mais je les recommande:

- University: Quarkus: Pourquoi & Comment faire une appli Java Cloud Native avec Graal VM (https://cfp.devoxx.fr/2019/talk/GSE-9991/Quarkus:_Pourquoi_&_Comment_faire_une_appli_Java_Cloud_Native_avec_Graal_VM)
- Conf: Observabilité : mythes, réalité et Chaos (https://cfp.devoxx.fr/2019/talk/JNL-9407/Observabilite_:_mythes,_realite_et_Chaos)

