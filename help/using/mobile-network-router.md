---
title: Réseau mobile avec routeur de données mobile et composants réseau actifs
description: La page décrit le réseau mobile avec routeur de données mobiles et composants réseau actifs
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 98%

---

# Réseau mobile avec routeur de données mobile et composants réseau actifs {#mobile-network-setup}

Il est possible de connecter les lecteurs Adobe AEM Screens à l’aide de réseaux mobiles ou cellulaires qui sont au moins en 3G.

Dans AEM Screens, le contenu requis est téléchargé physiquement sur le contrôleur du lecteur ou sur l’ordinateur, et stocké de manière appropriée dans le système d’exploitation associé. Par conséquent, la bande passante fournie n’a un impact que sur les temps de téléchargement initiaux, ainsi que sur les mises à jour du contenu, et n’a aucune incidence sur les performances de lecture ordinaire sur les affichages.

L’avantage de cette configuration est que le routeur mobile peut être placé en un point optimisé pour garantir la meilleure couverture réseau disponible. Cet endroit est généralement une position élevée et ouverte, où les structures environnantes de béton et de métal sont les moins nombreuses possibles.
Cette configuration offre une certaine flexibilité aux utilisateurs et utilisatrices d’AEM Screens, car aucune ligne fixe n’est requise pour se connecter. Cela est particulièrement intéressant pour les configurations éphémères ou mobiles.

Le diagramme suivant montre la connexion du lecteur AEM Screens au réseau mobile avec routeur de données mobile et composants réseau actifs. La configuration contient un accès Internet pour tous les contrôleurs AEM Screens par un accès Internet direct à l’aide d’une liaison de données 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Connecter le lecteur AEM Screens au réseau mobile avec routeur de données mobile et composants réseau actifs {#connecting-aem-screens-players}

Pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration, procédez comme suit :

La configuration alloue un accès Internet à chaque contrôleur ou contrôleuse AEM Screens par accès Internet direct à l’aide d’un lien de données 3/4/5G dédié.

1. Assurez-vous que le routeur de données mobile est correctement connecté au réseau de données cellulaire comme indiqué dans le système d’exploitation. Veillez à ce que chacun des lecteurs AEM Screens soit connecté au réseau des routeurs.
1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si une erreur s’affiche, vérifiez les paramètres réseau. Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle

1. Assurez-vous que le paramètre d’adaptateur réseau correspond à votre paramètre de routeur.

1. Assurez-vous que le routeur est correctement connecté au réseau étendu du FAI (liaison Internet). Vous pouvez vérifier à l’aide d’un voyant sur les routeurs standard.
1. Si l’appel de l’URL aboutit, vous pouvez continuer à installer AEM Screens et vous enregistrer. Lancez AEM Screens.

   >[!TIP]
   >Il se peut que la connexion AEM Screens ne fonctionne pas correctement. Le contenu attendu ne s’affiche pas. Dans ce cas, vérifiez le pare-feu de votre routeur Internet s’il existe des restrictions concernant `TCP/IP Port 80/443`.


## Configurer un réseau mobile avec routeur de données mobile et composants réseau actifs {#requirements-direct}

La configuration réseau peut être scindée logiquement en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

Au-delà de l’accessibilité réseau déjà décrite, les performances de la connexion internet tiennent à la capacité à fournir suffisamment de bande passante pour qu’AEM Screens télécharge le contenu de manière fluide. 

*Suffisant* dépend du nombre d’appareils AEM Screens connectés. Cela dépend également de l’utilisation d’autres consommateurs sur le réseau, tels que les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.
Gardez à l’esprit que tous les appareils ont un accès simultané à la connexion Internet et que la bande passante diminue de façon linéaire à mesure que des appareils consommateurs/ordinateurs sont ajoutés au réseau.
Outre la connexion théorique au réseau spécifique, une couverture du routeur mobile de qualité au moins *bonne* doit être garantie. De plus, la formule mensuelle associée doit couvrir une capacité de données et une bande passante suffisantes pour répondre aux besoins des clientes et clients connectés au réseau local.

Le tableau suivant présente les réseaux de données avec leur bande passante standard :

| Réseau de données | Bande passante |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 à 10 000 Mbit/s |

Lors de la réflexion relative au choix du réseau de données à utiliser, il est recommandé de répondre aux questions suivantes :

* Combien de clients sont connectés au routeur ?
* Combien de changements de contenu sont prévus et quelle est la taille moyenne des fichiers ?

>[!NOTE]
>
>Le package de données nécessaire doit respecter les conditions suivantes :
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Pour le chargement initial des fichiers multimédias, lors de l’intégration de nouveaux lecteurs, il faut s’attendre à un volume de données plus importante et à une durée de téléchargement plus longue. Cela est également reflété dans les hypothèses ci-dessus. Un réseau 4G possédant une *bonne* couverture et un volume de données illimité devrait correspondre aux installations les plus courantes de cette configuration de réseau.


### Réseau local {#lan-connection}

Au-delà de l’accessibilité réseau déjà décrite, les performances du réseau local tiennent à la capacité à fournir suffisamment de bande passante pour qu’AEM Screens télécharge le contenu de manière fluide. Actuellement, le réseau local atteint généralement un débit de 100 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Lors de l’utilisation d’autres composants réseau actifs, il est obligatoire qu’ils correspondent tous aux exigences de bande passante du réseau.

Par exemple, les composants du réseau doivent correspondre au minimum à la norme standard de 100 Mbit/s et à la bande passante fournie par l’accès à internet ou les spécifications du routeur.

Si une solution Wi-Fi est envisagée pour connecter l’écran à Internet, il est recommandé d’utiliser au minimum les normes Wi-Fi modernes comme IEEE `802.11g`. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Les normes *plus récentes* comme `802.11h-n` sont de meilleure qualité. Si un répéteur Wi-Fi est requis, il est fortement recommandé d’utiliser des technologies de point d’accès Wi-Fi maillé comme Google Nest Mesh Wi-Fi, ou un dispositif similaire.

## Télécharger des médias et des ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs et utilisatrices de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour les opérations normales, avec une liste de lecture définie qui n’est pas très souvent actualisée au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate. Cela garantit la meilleure expérience client possible.
Les tableaux ci-dessous offrent une bonne vue d’ensemble des données clés de connectivité réseau en ce qui concerne les performances prévisibles et les temps d’attente potentiels.

>[!NOTE]
>
>Toutes ces informations font référence à la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/mobile-router-download.png)
