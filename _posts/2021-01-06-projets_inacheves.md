---
title: Les projets inachevés
date: 2021-01-06 09:34:00 +0100
categories: [Blog, Projet]
tags: [projet, todo]
image: /assets/img/cover/long_road.jpg
---

## Le temps de reprendre des vieux projets...
Comme tout développeur qui se respecte, j'ai un tiroir plein de projets entamés qui n'ont jamais été terminés. Le dernier en date est un projet de jeu style Trivial Pursuit qui se joue à plusieurs en tant de confinement. Ah oui, il y a aussi le projet de gestion de ma bédéthèque qui prend la poussière depuis pas mal de temps. 

## Quiz !
L'idée est simple, faire un jeu en ligne / offline façon Trivial Pursuit. L'idée est de créer des cartes thématiques à partir de différentes sources (web, saisie manuelle, OCR). Ensuite, on crée une session de jeu, les potes rejoignent la partie et let's go!

### Principales fonctionnalités
Pour commencer, il faut une authentification. Bien qu'optionnelle, ca serait vraiment cool de pouvoir hoster un serveur d'identité, un gestionnaire de comptes et une page de statistiques pour permettre aux joueurs de voir l'historique de leur partie et surtout, permettre au moteur de ne pas reposer les questions précédemment posées au joueur. 

Il faut également un système de room suffisamment performant pour dispatcher des messages par web socket. Lorsqu'un nouveau joueur rejoint la partie, lorsqu'une équipe donne une réponse, lorsque la partie se termine... De mémoire, c'était un peu galère de reprendre une partie en cours, de gérer les déconnexions de la socket, etc.  C'est **LE** problème technique à résoudre.

Enfin, histoire de commencer soft, il faut un mode solo. Façon quiz en ligne, un joueur solo répond à des questions aléatoires et à la fin, on compte les points (pourcentage de réussite). C'est cette partie qu'il faudrait que j'arrive à finir rapidement.

### La stack
Depuis mon changement de boulot, je suis tombé dans le DDD. Il est donc naturel que j'essaye de suivre cette approche pour le développement. C'est un peu *overkill* mais en même temps, c'est très formateur. 

Une fois les bounded context posés, on enrobe tout ça avec du CQRS pour séparer strictement les commandes des queries. Et pour pimenter tout ça, le read est complètement séparé du write (services différents, stockage différent). Ben ouais, j'ai jamais eu l'occasion de faire de l'event store... Pourquoi ne pas commencer avec un projet perso ? Pour le read, une base de données relationnelle fait le taf en attendant de passer sur une base non relationnelle (Mongo ou autre en fonction du besoin).

L'API ne sera certainement écrite en REST FULL. CQRS et REST ne font pas bon ménage à mon sens et je n'arrive pas à voir l'intérêt du couplage de ces deux technologies. Deux choix donc
* Faire une API REST qui se connectera directement au repo de données
* Faire du CQRS en prenant en compte que la partie Query

Côté front, Angular + material. Rien de révolutionnaire, ca fonctionne et c'est plutôt relativement simple à mettre en place. Peut-être un bout event store côté front avec Redux histoire d'avoir les données de la partie partout et de découpler correctement les composants (smart et dumb components). Peut-être une approche micro frontend ? 

## BD, BD, BD
A chaque fois que je vais dans une librairie, j'attéris invariablement au rayon bandes-dessinées. C'est une constante. Et en plus, j'essaye d'initier mon fils aux joies des bulles. Globalement, c'est plutôt cool et franchement, y'a pire comme passe-temps...

Mais bon, quand on commence à avoir pas mal de BD, c'est compliqué de savoir ce qu'on a lu, ce qu'on a prévu de lire et qu'on a acheté, et ce qu'on a prévu de lire mais qu'on a pas encore. Ben du coup, si j'ai un doute, j'achète pas - et c'est relou.

En gros, ce que j'aimerais, c'est d'avoir en permanence ma bédéthèque à jour dans mon téléphone. Mais j'aimerais ne pas avoir à me taper la saisie des quelques centaines de BD que j'ai. Bref, le beurre et l'argent du beurre. 

### La problématique
Put*** de saisie ! Ben ouais, pour savoir ce qu'on a, il faut déjà répertorier tous les bouquins. S'assoir devant sa bibliothèque pendant des heures pour faire des saisies de titre, auteur, série, etc., ben ça fait pas rêver. Mais heureusement, y'a des codes sur chacun des bouquins qui sont censés être uniques et répertoriés dans des bases de données +- publiques aka l'ISBN. Ca fait moins de truc à saisir mais c'est quand même très chiant à faire et le risque d'erreur et plutôt conséquent. La solution ? L'OCR ! On passe son téléphone au-dessus de l'ISBN et tada, on sauvegarde ça quelque part (fichier, BDD) et on fait la moulinette des familles qui va interroger une API publique qui nous file toutes les infos utiles. C'est un peu le rêve et à part la reconnaissance, y'a pas énormément de boulot.

### c'est cool mais c'est quand qu'on le fait ?!
Et voilà le problème central. Le TEMPS. Après une bonne grosse journée de boulot (même si depuis le début de l'année, la reprise est un peu hardcore), j'ai pas forcément l'envie ni le temps de me remettre à coder... Pourtant, quand j'y suis, je suis plutôt à donf et j'ai du mal à décrocher. Mais avec un petit garçon de 7 ans et un manque total d'organisation, c'est un peu compliqué de s'y mettre raisonnablement et de manière efficace. En plus, j'ai tendance à commencer des trucs, les laisser de côte, tout recommencer from scratch et refaire le cycle encore et encore. 

## Conclusion
Faut que je m'y remette non de Zeus !