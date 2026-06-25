---
title: Réseau mobile direct
description: Découvrez la configuration de réseau mobile direct dans AEM Screens.
exl-id: 6775bd10-7625-422f-a7af-4f7b8793fa42
TQID: https://experienceleague.adobe.com/nesp1a9TVyKUBaWjPR8bzW6n2dGyVVme1p5469h92LA
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 837
ht-degree: 89%

---

# Réseau mobile direct {#mobile-network-setup}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Il est possible de connecter les lecteurs AEM Screens à l’aide de réseaux mobiles ou cellulaires qui sont au moins en 3G.

Dans AEM Screens, le contenu requis est téléchargé physiquement sur le contrôleur du lecteur ou sur l’ordinateur, et stocké de manière appropriée dans le système d’exploitation associé. Par conséquent, la bande passante fournie n’a un impact que sur les temps de téléchargement initiaux, ainsi que sur les mises à jour du contenu, et n’a aucune incidence sur les performances de lecture ordinaire sur les affichages.

L’avantage de la connexion des lecteurs AEM Screens via le réseau 3/4/5G cellulaire de votre fournisseur de données mobiles est que le routeur mobile peut être placé en un point optimisé. Cela garantit la meilleure couverture réseau disponible. Cet emplacement est généralement une position élevée et ouverte, où les structures environnantes en béton et en métal sont les moins nombreuses possibles.

Cette configuration offre une grande flexibilité aux utilisateurs et utilisatrices d’AEM Screens, car aucune connexion fixe n’est requise pour se connecter. Cet arrangement est intéressant pour les configurations éphémères ou mobiles.

Le diagramme suivant illustre la configuration d’un réseau mobile direct. Il se compose d’un segment de connexion réseau unique et de la connexion de chaque lecteur au réseau de données mobile ou cellulaire.

![](/help/using/assets/direct-mobile-1.png)

## Connexion d’un lecteur AEM Screens à un réseau mobile direct

Pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration, procédez comme suit :

1. Veillez à ce que chacun des lecteurs AEM Screens soit connecté au réseau du routeur.

1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si un message d’erreur s’affiche, vérifiez les paramètres réseau et la présence d’une liaison réseau suffisante. Vérifiez également que le pare-feu du système d’exploitation est configuré pour autoriser l’accès au réseau lors de l’utilisation des ports de communication AEM Screens configurés.

1. Si l’appel de l’URL aboutit, vous pouvez continuer à installer AEM Screens et vous enregistrer. Lancez AEM Screens.

## Configuration d’un réseau mobile direct {#requirements-direct}

La configuration réseau peut être scindée logiquement en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

Au-delà de l’accessibilité du réseau, les performances de la connexion Internet tiennent à la capacité à fournir une bande passante suffisante pour utiliser AEM Screens de manière fluide.

Dans un réseau mobile direct, chaque lecteur est connecté au réseau de données du fournisseur à l’aide d’une carte de données mobile unique.

Le tableau suivant présente les réseaux de données avec leur bande passante standard :

| Réseau de données | Bande passante |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 à 10 000 Mbit/s |

Lors de la détermination du réseau de données à utiliser, tenez compte des points suivants :

La vitesse du réseau disponible dépend du plan de fournisseur de données mobiles spécifique et de la couverture disponible atteinte à l’emplacement du contrôleur AEM Screens.
Lors du suivi de cette configuration, considérez qu’en plus de la bande passante disponible, certains plans de fournisseurs de données mobiles limitent la quantité de données disponibles traversant la connexion au cours d’une période spécifique. Il faut s’assurer que les données et la bande passante disposent d’une capacité suffisante.
En guise de suivi, le package de données nécessaire doit être au moins :

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Pour le chargement initial des fichiers multimédias, lors de l’intégration de nouveaux lecteurs, il faut s’attendre à un volume de données plud important et à une durée de téléchargement plus longue, ce qui se reflète dans les hypothèses ci-dessus. Un réseau 4G possédant une *bonne* couverture et un volume de données *illimité* devrait correspondre aux installations les plus courantes de cette configuration de réseau.

>[!NOTE]
>Un forfait 3G minimal doté d’une bonne couverture réseau devrait permettre d’obtenir des performances de téléchargement acceptables pour un lecteur AEM Screens. Si la couverture disponible à un emplacement spécifique n’est que passable, envisagez la possibilité de basculer la configuration réseau globale sur un [réseau mobile avec routeur de données mobiles et composants réseau actifs](/help/using/mobile-network-router.md).


### Réseau local {#lan-connection}

Au-delà de l’accessibilité, les performances du réseau local tiennent à la capacité à fournir une bande passante suffisante pour utiliser AEM Screens de manière fluide. Pour les réseaux locaux, la vitesse recommandée est de 100 Mbit/s au moins, de sorte qu’il y ait suffisamment de bande passante pour connecter de nombreux appareils avec de bonnes performances système.

Lors de l’utilisation d’autres composants réseau actifs, il est obligatoire qu’ils correspondent tous aux exigences de bande passante du réseau. Par exemple, les composants réseau doivent correspondre au moins à la norme 100 Mbit/s et à la bande passante de l’accès Internet ou de la spécification du routeur. Sinon, la bande passante totale est limitée par le maillon le plus faible de la chaîne réseau.

## Télécharger des médias et des ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs et utilisatrices de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. L’essentiel du trafic réseau a lieu lorsqu’un nouveau contenu doit être affiché sur un dispositif d’affichage spécifique.

Pour les opérations normales, par exemple, une playlist définie qui se met à jour fréquemment au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.

Pour les scénarios où il y a davantage d’interactions avec des capteurs ou d’autres déclencheurs et un contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente une vue d’ensemble des données clés relatives à la connectivité réseau.

>[!NOTE]
>
>Toutes ces informations font référence à la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/download-times-mobile.png)
