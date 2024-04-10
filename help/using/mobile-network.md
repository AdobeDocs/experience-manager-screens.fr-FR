---
title: Réseau mobile direct
description: Découvrez la configuration du réseau mobile direct dans AEM Screens.
exl-id: 6775bd10-7625-422f-a7af-4f7b8793fa42
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 55%

---

# Réseau mobile direct {#mobile-network-setup}

Il est possible de connecter les lecteurs AEM Screens à l’aide de réseaux mobiles ou cellulaires qui sont au moins en 3G.

Dans AEM Screens, le contenu requis est téléchargé physiquement sur le contrôleur du lecteur ou sur l’ordinateur, et stocké de manière appropriée dans le système d’exploitation associé. Par conséquent, la bande passante donnée n’a un impact que sur les temps de téléchargement initiaux et les mises à jour de contenu, et n’influence pas les performances de lecture régulière des affichages.

L’avantage de la connexion des lecteurs AEM Screens via le réseau 3/4/5G cellulaire à votre fournisseur de données de service mobile est que le routeur mobile peut être placé dans un emplacement optimisé pour assurer la meilleure couverture réseau disponible. Il s&#39;agit généralement d&#39;une position élevée et ouverte avec le moins de structures métalliques ou de béton environnantes possible.

Cette configuration offre une grande flexibilité aux utilisateurs d’AEM Screens, car aucune connexion fixe n’est requise pour se connecter. Ceci est intéressant pour les configurations éphémères ou mobiles.

Le schéma suivant représente la configuration d’un réseau mobile direct. Il se compose d’un segment de connexion réseau unique et de la connexion de chaque lecteur au réseau de données mobile ou cellulaire.

![](/help/using/assets/direct-mobile-1.png)

## Connexion d’AEM Screens Player à un réseau mobile direct

Procédez selon les étapes ci-dessous pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration :

1. Veillez à ce que chacun des lecteurs AEM Screens soit connecté au réseau du routeur.

1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si vous recevez un message d’erreur, vérifiez les paramètres réseau et vérifiez s’il existe un lien réseau suffisant. Vérifiez également que le pare-feu du système d’exploitation est configuré pour autoriser l’accès réseau lors de l’utilisation des ports de communication AEM Screens configurés.

1. Si l’appel de l’URL aboutit, vous pouvez continuer à installer AEM Screens et vous enregistrer. Lancez AEM Screens.

## Configuration du réseau mobile direct {#requirements-direct}

La configuration réseau peut être scindée logiquement en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

Au-delà de l’accessibilité du réseau, les performances de la connexion Internet tiennent à la capacité à fournir une bande passante suffisante pour utiliser AEM Screens de manière fluide.

Dans Direct Mobile Network, chaque lecteur est connecté au réseau de données du fournisseur à l’aide d’une carte de données mobile unique.

Le tableau suivant met en évidence les réseaux de données avec leur bande passante standard :

| Réseau de données | Bande passante |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 à 10 000 Mbit/s |

Lors de la sélection du réseau de données à utiliser, tenez compte des points suivants :

Le débit réseau disponible dépend du forfait spécifique du fournisseur de données mobiles et de la couverture disponible au point où se trouve le contrôleur AEM Screens.
Lors du suivi de cette configuration, considérez qu’en plus de la bande passante disponible, certains plans de fournisseurs de données mobiles limitent la quantité de données disponibles traversant la connexion au cours d’une période spécifique. Il faut s’assurer que les données et la bande passante disposent d’une capacité suffisante.
En guise de suivi, le package de données nécessaire doit être au moins :

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Pour le chargement initial des fichiers multimédias, par exemple pour l’intégration de nouveaux lecteurs, il est probable que le volume de données et la durée de téléchargement seront plus importants, ce qui devra être repris dans les hypothèses ci-dessus. Un réseau 4G possédant une *bonne* couverture et un volume de données *illimité* devrait correspondre aux installations les plus courantes de cette configuration de réseau.

>[!NOTE]
>Un forfait 3G minimal doté d’une bonne couverture réseau devrait permettre d’obtenir des performances de téléchargement acceptables pour un lecteur AEM Screens. Si seule une couverture équitable est disponible à un emplacement spécifique, pensez à basculer la configuration réseau globale sur [Réseau mobile avec routeur de données mobile et composants réseau actifs](/help/using/mobile-network-router.md).


### Réseau local {#lan-connection}

Au-delà de l’accessibilité, les performances du réseau local tiennent à la capacité à fournir une bande passante suffisante pour utiliser AEM Screens de manière fluide. La recommandation pour les vitesses de réseau local est de commencer au moins à 100 Mbps réseaux, de sorte qu&#39;il y ait suffisamment de bande passante pour connecter de nombreux appareils avec de bonnes performances au système.

Si vous utilisez d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante du réseau. Par exemple, les composants réseau doivent correspondre au moins à la norme 100 Mbit/s et à la bande passante de l’accès Internet ou de la spécification du routeur. Dans le cas contraire, la bande passante totale est limitée par le maillon le plus faible de la chaîne réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un avantage significatif aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. L’essentiel du trafic réseau a lieu lorsqu’un nouveau contenu doit être affiché sur un dispositif d’affichage spécifique.

Pour les opérations normales, par exemple, une liste de lecture définie qui se met fréquemment à jour au cours de la journée offre un fonctionnement presque indépendant du réseau, une fois tous les fichiers enregistrés sur le lecteur.

Pour les scénarios où il y a davantage d’interactions avec des capteurs ou d’autres déclencheurs et un contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente un aperçu des données clés relatives à la connectivité réseau.

>[!NOTE]
>
>Toutes ces informations font référence à la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces requêtes s’additionne et prolonge la durée du téléchargement.

![](/help/using/assets/download-times-mobile.png)
