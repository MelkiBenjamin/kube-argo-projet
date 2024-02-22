# THE BIG CHALLENGE

Soufflez, prenez le temps, nous passerons plusieurs jours sur ce challenge.

## Etape 1: on code une application multi composants.
A l'aide de votre ami chatgpt vous allez construire une application composée de deux composants:
- Un composant backend: on l'appellera simplement back.
  Back est une API qui renvoie une ligne aléatoire lue dans un fichier texte.
  back utilisera le framework flask pour la partie API et ne répondra qu'à une simple requête sur l'URI /racontemoiunehistoire en GET.
- Un composant frontend: basé sur une simple page HTML + javascript qui fera des requêtes vers notre composant back pour récupérer la ligne renvoyée par /racontemoiunehistoire.
  Attention, l'URL complète (http://....../racontemoiunehistoire) devra etre configurable sous la forme d'une variable javascript.

Testez ces deux composants, et enregistrez les prompts chatgpt dans votre repo dans: appli/chatgpt/prompt-front.txt et appli/chatgpt/prompt-back.txt

## Etape 2: Dockerisation de front et back
Vous allez créer 2 Dockerfile:
- appli/front/Dockerfile: sera le Dockerfile permettant de construire une image docker basée sur Nginx qui remplacera le index.html de nginx par le html + js généré à l'étape 1.
  (ATTENTION: on ne surchargera pas les CMD et ENTRYPOINT de l'image nginx officielle)
- appli/back/Dockerfile: sera une image basée sur python qui executera notre api en lancant directement flask sur le port 5000. 
  On veillera lors de la construction de l'image à:
    - Bien configurer les variables d'environnement ou python pour que flask soit en écoute sur l'adresse 0.0.0.0
    - que les librairies soient bien installées à l'aide d'un fichier requirements.txt.

## Etape 3: Préparation des manifests.
L'application sera composée de:
- un deployment pour le back
- un deployment pour le front
- un service de type ClusterIP pour le back
- un service de type LoadBalancer pour le front

à ce stade il faudra modifier et re builder votre image docker front pour qu'elle utilise l'url du service clusterIP pour joindre le back

## Etape 4: Chart Helm
Intégrez vos fichiers yaml dans une chart Helm, on stockera cette chart dans ce repos dans: helmchart

## Etape 5: Testez votre Chart Helm dans une application ArgoCD
Créez manuellement une application ArgoCD (sans iaac): les repos, projets, applications seront tous précédés de e6- dans leurs noms, pour faciliter la correction.

## Etape 6: Creez les fichiers de IaaC permettant de déployer votre chart Helm
Sur la base de l'exemple disponible sur Github.

