---
title: Réseau mobile avec routeur de données mobile et composants réseau actifs
description: La page décrit le réseau mobile avec routeur de données mobiles et composants réseau actifs
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
source-git-commit: 02929219a064e3b936440431e77e67e0bf511bf6
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 49%

---

# Réseau mobile avec routeur de données mobile et composants réseau actifs {#mobile-network-setup}

Il est possible de connecter les lecteurs Adobe AEM Screens à l’aide de réseaux mobiles ou cellulaires qui sont au moins en 3G.

Dans AEM Screens, le contenu requis est téléchargé physiquement sur le contrôleur du lecteur ou sur l’ordinateur, et stocké de manière appropriée dans le système d’exploitation associé. Par conséquent, la bande passante fournie n’a un impact que sur les temps de téléchargement initiaux et les mises à jour du contenu, et n’a aucune incidence sur les performances de lecture ordinaire des affichages.

L’avantage de cette configuration est que le routeur mobile peut être placé en un point optimisé pour assurer la meilleure couverture réseau disponible. Il s’agit généralement d’une position élevée et ouverte, avec le moins possible de structures environnantes en béton ou en métal.
Cette configuration offre une certaine flexibilité aux utilisateurs d’AEM Screens, car aucune ligne fixe n’est requise pour se connecter à AEM Screens. Ceci est intéressant pour les configurations éphémères ou mobiles.

Le diagramme suivant illustre la configuration du réseau mobile avec routeur de données mobile et composants réseau actifs. Il contient un accès Internet à l’un des contrôleurs AEM Screens par un accès Internet direct à l’aide d’une liaison de données 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Connexion du lecteur AEM Screens à un réseau mobile avec routeur de données mobile et composants réseau actifs {#connecting-aem-screens-players}

Procédez selon les étapes ci-dessous pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration :

La configuration alloue un accès Internet à chaque contrôleur AEM Screens par accès Internet direct à l’aide d’un lien de données 3/4/5G dédié.

1. Assurez-vous que le routeur de données mobile est correctement connecté au réseau de données cellulaire comme indiqué dans le système d’exploitation et que chacun des lecteurs AEM Screens est connecté au réseau de routeurs.
1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si une erreur s’affiche, vérifiez les paramètres réseau. Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle

1. Assurez-vous que le paramètre d’adaptateur réseau correspond à votre paramètre de routeur.

1. Vérifiez si le routeur est correctement connecté au réseau étendu du fournisseur d’accès Internet (liaison Internet). Vous pouvez également l’identifier à l’aide d’un voyant sur les routeurs standard.
1. Si l’appel de l’URL aboutit, vous pouvez continuer à installer AEM Screens et vous enregistrer. Lancez AEM Screens.

   >[!NOTE]
   >**Conseil de dépannage**
   >Si AEM Screens ne se connecte pas correctement et que le contenu attendu n’est pas affiché, vérifiez si le pare-feu de votre routeur Internet présente des restrictions concernant `TCP/IP Port 80/443`.


## Configuration d’un réseau mobile avec routeur de données mobile et composants réseau actifs {#requirements-direct}

La configuration réseau peut être scindée logiquement en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

En plus de l’accessibilité réseau déjà décrite, la connexion Internet doit fournir suffisamment de bande passante pour qu’AEM Screens fonctionne de manière fluide.

*Suffisant* Dépend du nombre d’appareils AEM Screens connectés et de l’utilisation d’autres appareils consommateurs sur le réseau, comme les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.
Gardez à l’esprit que tous les appareils ont un accès simultané à la connexion Internet et que la bande passante diminue de façon linéaire tout en ajoutant d’autres appareils consommateurs/ordinateurs au réseau.
Outre la connexion théorique au réseau spécifique, il faut s&#39;assurer que la couverture du routeur mobile est au moins &quot;bonne&quot;. De plus, la formule mensuelle associée doit couvrir une capacité de données et une bande passante suffisantes pour répondre aux besoins de tous les clients connectés au réseau local.

Le tableau suivant met en évidence les réseaux de données avec leur bande passante standard :

| Réseau de données | Bande passante |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 à 10 000 Mbit/s |

Lors de l’examen du réseau de données à utiliser, Adobe vous recommande de répondre aux questions suivantes :

* Combien de clients sont connectés au routeur ?
* Combien de changements de contenu sont prévus et quelle est la taille moyenne des fichiers ?

>[!NOTE]
>
>Le package de données nécessaire doit respecter les conditions suivantes :
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Pour le chargement initial des fichiers multimédias, par exemple pour l’intégration de nouveaux lecteurs, il est probable que le volume de données et la durée de téléchargement seront plus importants, ce qui devra être repris dans les hypothèses ci-dessus. Un réseau 4G possédant une *bonne* couverture et un volume de données illimité devrait correspondre aux installations les plus courantes de cette configuration de réseau.


### Réseau local {#lan-connection}

Au-delà de l’accessibilité réseau déjà décrite, les performances du réseau local tiennent à la capacité à fournir suffisamment de bande passante pour qu’AEM Screens télécharge le contenu de manière fluide. Actuellement, le réseau local correspond généralement à un réseau de 100 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Lors de l’utilisation d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante du réseau.

Par exemple, les composants réseau doivent correspondre au moins à la norme standard de 100 Mbit/s et à la bande passante de l’accès Internet ou de la spécification du routeur.

Si une solution Wi-Fi est envisagée pour connecter l’écran à Internet, il est recommandé d’utiliser les standards Wi-Fi modernes tels que IEEE. `802.11g` au minimum. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Les normes *plus récentes* comme `802.11h-n` sont de meilleure qualité. Si un répéteur Wi-Fi est requis, Adobe recommande les technologies de point d’accès Wi-Fi maillé telles que Google Nest Mesh Wi-Fi, ou un dispositif similaire.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un avantage important aux utilisateurs de signalétique digitale. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, le trafic réseau majeur se produit au cas où un nouveau contenu s’afficherait sur un écran spécifique.
Pour un fonctionnement normal, par exemple, si vous avez défini une liste de lecture qui n’est pas fréquemment mise à jour au cours de la journée, cela offre un fonctionnement presque indépendant du réseau lorsque tous les fichiers sont enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et où le contenu est dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.
Les tableaux ci-dessous offrent une bonne vue d’ensemble des données clés de connectivité réseau en ce qui concerne les performances prévisibles et les temps d’attente potentiels.

>[!NOTE]
>
>Toutes ces informations font référence à la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces requêtes additionne et prolonge la durée de téléchargement.

![](/help/using/assets/mobile-router-download.png)
