---
title: Réseau mobile direct
description: La page décrit la configuration du réseau mobile direct.
translation-type: tm+mt
source-git-commit: 23bb59c719c675baa84c579f624adccc80377661
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 76%

---


# Réseau mobile direct {#mobile-network-setup}

Il est possible de connecter les lecteurs AEM Screens à l’aide de réseaux mobiles ou cellulaires qui sont au moins en 3G.

Dans AEM Screens, le contenu requis est téléchargé physiquement sur le contrôleur du lecteur ou sur l’ordinateur, et stocké de manière appropriée dans le système d’exploitation associé. Par conséquent, la bande passante fournie n’a d’incidence que sur les temps de téléchargement initiaux, ainsi que sur les mises à jour de contenu, et n’influence pas les performances de lecture régulière des Affichages.

L&#39;avantage de connecter des lecteurs AEM Screens via Cellular 3/4/5G à votre fournisseur de données de services mobiles est que le routeur mobile peut être placé dans un emplacement optimisé pour garantir une meilleure couverture réseau disponible. Il s’agit généralement d’une position élevée et ouverte, où les constructions environnantes de béton et de métal sont les moins nombreuses possibles.

Cette configuration permet aux utilisateurs d’AEM Screen d’avoir une grande flexibilité car aucune connexion fixe n’est requise pour se connecter aux AEM Screens. Cela est particulièrement intéressant pour les configurations éphémères ou mobiles.

Le schéma suivant représente la configuration d’un réseau mobile direct. Il se compose d’un segment de connexion réseau unique et de la connexion de chaque lecteur au réseau de données mobile ou cellulaire.

![](/help/using/assets/direct-mobile-1.png)

## Connexion d’un lecteur AEM Screens à un réseau mobile direct {#connecting-aem-screens-players}

Procédez selon les étapes ci-dessous pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration :

1. Veillez à ce que chacun des lecteurs AEM Screens soit connecté au réseau du routeur.

1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si vous recevez un message d’erreur, vérifiez les paramètres du réseau et contrôlez que la liaison réseau est suffisante et que le pare-feu du système d’exploitation est configuré pour autoriser l’accès au réseau à l’aide des ports de communication AEM Screens configurés.

1. Si l’appel de l’URL aboutit, vous pouvez continuer à installer AEM Screens et vous enregistrer. Lancez AEM Screens.

## Configuration d’un réseau mobile direct {#requirements-direct}

La configuration réseau peut être scindée logiquement en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

Au-delà de l’accessibilité du réseau, les performances de la connexion Internet tiennent à la capacité à fournir une bande passante suffisante pour utiliser AEM Screens de manière fluide.

Dans un réseau mobile direct, chaque lecteur est connecté au réseau de données du fournisseur à l’aide d’une carte de données mobile unique.

Le tableau suivant présente les réseaux ATA avec leur bande passante standard :

| Réseau de données | Bande passante |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 à 10 000 Mbit/s |

Lors de la réflexion relative au choix du réseau à utiliser, il est recommandé de répondre aux questions suivantes :

Le débit réseau disponible dépend du forfait spécifique du fournisseur de données mobiles et de la couverture disponible au point où se trouve le contrôleur AEM Screens.
Pour effectuer cette configuration, il faut également tenir compte du fait que, outre la bande passante disponible, certains forfaits de fournisseurs de données mobiles limitent la quantité de données disponibles transitant par la connexion pour une période donnée. Il faut s’assurer de disposer de capacités suffisantes en volumes de données et en bande passante.
Dans le prolongement de cette réflexion, le package de données nécessaire doit respecter les conditions suivantes :

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>
>Pour le téléchargement initial des fichiers multimédia, par exemple, lors de l’intégration de nouveaux lecteurs, une plus grande quantité de données et une durée de téléchargement accrue doivent être attendues et être reflétées dans les hypothèses ci-dessus. A 4G network with *good* coverage and *unlimited* data should match the most common installations in this Network Setup.

>[!NOTE]
>
>Un forfait 3G minimal doté d’une bonne couverture réseau devrait permettre d’obtenir des performances de téléchargement acceptables pour un lecteur AEM Screens. Si la couverture disponible à un emplacement spécifique n’est que passable, il faut envisager la possibilité de basculer la configuration réseau globale sur un [réseau mobile avec routeur de données mobiles et composants réseau actifs](/help/using/mobile-network-router.md).


### Réseau local {#lan-connection}

Outre l&#39;accessibilité au réseau, les problèmes de performances du réseau local (LAN) visent à fournir une bande passante suffisante pour le bon fonctionnement du AEM Screens. La recommandation pour les vitesses réseau LAN est de début à 100 Mbit/s au moins, de sorte qu&#39;il y ait suffisamment de bande passante pour connecter de nombreux périphériques avec de bonnes performances au système.

Si vous utilisez d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante du réseau. Par exemple, les composants réseau doivent correspondre au moins à la norme 100 Mbit/s et à la bande passante de l’accès Internet ou de la spécification du routeur. Sinon, la bande passante totale sera limitée par le maillon le plus faible de la chaîne réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. L’essentiel du trafic réseau a lieu lorsqu’un nouveau contenu doit être affiché sur un dispositif d’affichage spécifique.

Pour les opérations normales, par exemple une liste de lecture définie qui ne change pas très souvent au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.

Pour les scénarios où il y a davantage d’interactions avec des capteurs ou d’autres déclencheurs et un contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente un aperçu des données clés relatives à la connectivité réseau.

>[!NOTE]
>
>Toutes ces informations font référence à la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/download-times-mobile.png)



