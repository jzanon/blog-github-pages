+++
author = "Julien Zanon"
categories = ["DevOps"]
date = "2016-12-06"
description = "Au-secours! Ma prod est sous Docker"
linktitle = ""
title = "Docker en Prod: au DevFest et ailleurs"
type = "post"
+++

Ce post était initialement prévu pour être un retour du DevFest 2016 Toulousain 
sur la présentation "Au-secours! Ma prod est sous Docker" de François Teychené. 
Mais le temps de sa rédaction, je me suis rendu compte que j'avais un peu plus de matière à ma disposition: 
depuis quelques semaines ma timeline twitter est envahie d'avis et discutions de gens ayant un avis sur Docker.

Je rédige donc ce post sous la forme d'un résumé (légèrement biaisé par ma vision sur le sujet) de la présentation du DevFest
 et des quelques billets les plus intéressants du moment sur le sujet.

## Le REX de François Teychené

François Teychené nous a fait un retour très dynamique sur sa propre expérience de mise en production de Docker.
Sur un fond très intéressant il a su placer quelques punchlines bien senties pour faire de sa présentation un show tout à fait agréable!

Le présentateur introduit le sujet de manière assez directe: 
"Dire qu'on a du Docker en prod: c'est cool, mais les débuts sont terriblement difficiles"

Par exemple il ne faut pas en attendre plus que son essence: **Docker n'est qu'une isolation de process**.

Voici un résumé des points les plus marquants de sa présentation sur la pratique de Docker en production.

### Les applications:

* Il est recommandé de ne pas chercher à "réparer" une application mais plutôt de la "remplacer": Mode cattle vs mode pet.

Donc on ne demande pas au responsable de la prod d'aller appliquer un patch applicatif directement sur ses plateformes.
On reconstruit l'environnement que l'on relivre.
Et oui, cela implique donc d'être serein sur la chaîne d'intégration continue.
Elle doit non plus seulement être capable de tester/valider automatiquement votre code,
 mais aussi préparer un livrable (incluant la doc c'est mieux) directement exploitable par la prod.
Ah et il faut que ce processus soit rapide...

* Quid des patchs de sécurité?

On dépasse ici la question de la sécurité applicative: si le responsable de la prod doit appliquer un patch de sécurité
il faut qu'il en ai les moyens. C'est à dire qu'il doit être capable de modifier votre DockerFile pour y intégrer le patch.
Il prend alors la casquette de développeur (qui a dit "DevOps"? ;-) ).
Mais est-il prêt pour cela? On touche là à une question d'organisation de l'entreprise, je ne m'étendrai pas plus sur le sujet.


* Il faut être résilient au changement et respecter la méthodologie de l'application  12 facteurs ([12-factor app](https://12factor.net/))

Docker ou pas, les 12 facteurs sont à connaître et à respecter.


### Les orchestrateurs

L'objectif de l'outil Docker est d'assurer que le conteneur sera exactement le même en dev qu'en prod.
Son rôle n'est pas d'assurer que les interactions **entre** les conteneurs seront les mêmes.
Donc lorsqu'on démarre plein de docker: c'est "sympa" mais il faut les administrer (ie. les orchestrer), 
et là: c'est plus compliqué.

Pour nous aider, des éditeurs proposent des outils d'orchestration.
Le marché est encore jeune: les produits sont nombreux **mais** ne sont pas forcément matures 
et en plus, l'éditeur de Docker lui-même se positionne en concurrence sur ce marché. 

On a donc de nouveaux outils qui tentent d'apporter des réponses à cette problématique (pas si nouvelle de l'orchestration)
et qui mettent en avant une nouvelle couche de complexité que les DevOps devront appréhender
pour seulement pouvoir prétendre à mettre du Docker en production!


### Les données

La définition initiale définissait Docker comme une isolation de **process**. 
Docker n'apporte pas de solution magique à la problématique de scalabilité des espaces de stockage des données.

Par défaut les VOLUMES ont un cycle de vie dépendant des conteneurs.
Est-ce que l'on veut vraiment stocker nos données dans des conteneurs sensés être "jetables"?

Plusieurs solutions existent comme:
* Créer des conteneurs dédiés au stockage de données qu'on s'assurera de ne pas supprimer.
* Externaliser le stockage dans un espace indépendant, 
mais dans ce cas on délègue la responsabilité à un mécanisme externe à notre contexte Docker


### Le monitoring

Le temps commençait à manquer et le présentateur nous a fait plus un listing des solutions possible qu'un vrai REX commenté:

* Des solutions possibles pour pouvoir exploiter les logs que produit votre application dans un conteneur:
  * Mettre un appender dans le logger de l'application
  * S'appuyer sur le Docker Logging Driver mais pour le moment il semblerait que l'on ne puisse en utiliser qu'1 seul par container
  * Alternative: les Docker agents de logs
* Les performances
  * Utiliser des monitoring agent comme cAdvisor, DockerBeats...

## D'autres REX et débats

* [Docker in production: An history of failure](https://thehftguy.com/2016/11/01/docker-in-production-an-history-of-failure/)

L'auteur de ce post pointe ce qu'il considère comme des manquement à une application apte à tourner en production.

Certains de ces points sont vrais, d'autres pleins de mauvaise foi et certains sont même erronés. (cf. l'article suivant)
Cet article est intéressant à lire et doit être complété par la lecture d'autres points de vues sur le sujet.

* [Docker in Production: A retort](https://patrobinson.github.io/2016/11/05/docker-in-production/)

4 jours après la diffusion du post précédent un autre blogger lui répond, parfois avec autant de mauvaise foi.

A eux seuls ces 2 posts ont déclenchés de longues discutions sur les forums (de trolleurs) tels que Hacker News et Reddit.

* [Running Docker in production for 6 months](http://racknole.com/blog/running-docker-in-production-for-6-months/)

Ici l'article est plus modéré, l'auteur nous donne son avis sur les limitations de Docker.

Sa conclusion recommandant de ne pas mettre Docker à toutes les sauces me parait des plus avisées.

## Alors: Docker en prod ou pas?

Soyons clair: le sujet divise et l'éditeur de Docker joue un rôle dans cet imbroglio.

Je suis d'accord qu'en terme de communication il est "hype" d'inclure Docker dans la plaquette de son produit.
Ca attirera des développeurs "de type hipsters", **oui**. Mais faire le buzz n'est pas la raison première du développement logiciel.
On parle ici de mettre en production des logiciels qui répondent à un besoin métier, 
dont la raison même d'être en production est de générer de la plus-value.

Docker est un outil, pas une _Silver-bullet_. 

Il faut en **connaître les limites et apprendre à l'utiliser**, 
ensuite seulement, il pourra **peut-être vous aider à améliorer vos plus-values**.


 
## Références

Les slides: https://t.co/Ob3aisFB0p

Le speaker: [@fteychene](https://twitter.com/fteychene)



