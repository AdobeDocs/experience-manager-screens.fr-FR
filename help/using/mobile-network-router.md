---
title: Réseau mobile avec routeur de données mobile et composants réseau actifs
description: La page décrit le réseau mobile avec routeur de données mobiles et composants réseau actifs
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: ht
source-wordcount: '1035'
ht-degree: 100%

---


# Réseau mobile avec routeur de données mobile et composants réseau actifs {#mobile-network-setup}

Il est possible de connecter les lecteurs Adobe AEM Screens à l’aide de réseaux mobiles ou cellulaires qui sont au moins en 3G.

Dans AEM Screens, le contenu requis est téléchargé physiquement sur le contrôleur du lecteur ou sur l’ordinateur, et stocké de manière appropriée dans le système d’exploitation associé. Par conséquent, la bande passante fournie n’a un impact que sur les temps de téléchargement initiaux, ainsi que sur les mises à jour du contenu, et n’a aucune incidence sur les performances de lecture ordinaire sur les affichages.

L’avantage de cette configuration est que le routeur mobile peut être placé en un point optimisé pour garantir la meilleure couverture réseau disponible. Il s’agit généralement d’une position élevée et ouverte, où les constructions environnantes de béton et de métal sont les moins nombreuses possibles.
Cette configuration offre une certaine flexibilité aux utilisateurs d’AEM Screens, car aucune ligne fixe n’est requise pour se connecter. Cela est particulièrement intéressant pour les configurations éphémères ou mobiles.

Le schéma suivant représente la configuration de réseau mobile avec routeur de données mobiles et composants réseau actifs. Celle-ci contient un accès Internet pour l’un des contrôleurs AEM Screens par un accès Internet direct à l’aide d’une liaison de données 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Connexion du lecteur AEM Screens au réseau mobile avec routeur de données mobile et composants réseau actifs {#connecting-aem-screens-players}

Procédez selon les étapes ci-dessous pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration :

La configuration alloue un accès Internet à chaque contrôleur AEM Screens par accès Internet direct à l’aide d’un lien de données 3/4/5G dédié.

1. Assurez-vous que le routeur de données mobile est correctement connecté au réseau de données cellulaire comme indiqué dans le système d’exploitation et que chacun des lecteurs AEM Screens est connecté au réseau de routeurs.
1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.
   >[!NOTE]
   >Si une erreur est signalée, vérifiez les paramètres réseau. Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle


1. Assurez-vous que le paramètre d’adaptateur réseau correspond à votre paramètre de routeur.

1. Vérifiez si le routeur est correctement connecté au réseau étendu du FAI (liaison Internet). Vous pouvez également l’identifier à l’aide d’un voyant sur les routeurs standard.
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

Plus précisément, cette bande passante *suffisante* tient à la quantité de postes AEM Screens connectés et à l’utilisation d’autres appareils consommateurs sur le réseau, comme les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.
Gardez à l’esprit que tous les appareils ont un accès simultané à la connexion Internet et que la bande passante diminue généralement de façon linéaire à mesure que des appareils consommateurs/ordinateurs sont ajoutés au réseau.
Outre la connexion théorique au réseau spécifique, une couverture du routeur mobile de qualité au moins « bonne » doit être garantie. De plus, la formule mensuelle associée doit couvrir une capacité de données et une bande passante suffisantes pour répondre aux besoins de tous les clients connectés au réseau local.

Le tableau suivant présente les réseaux ATA avec leur bande passante standard :

| Réseau de données | Bande passante |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 à 10 000 Mbit/s |

Lors de la réflexion relative au choix du réseau à utiliser, il est recommandé de répondre aux questions suivantes :

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

Au-delà de l’accessibilité réseau déjà décrite, les performances du réseau local tiennent à la capacité à fournir suffisamment de bande passante pour qu’AEM Screens télécharge le contenu de manière fluide. Actuellement, le réseau local atteint généralement un débit de 100 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Si vous utilisez d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante du réseau.

Par exemple, les composants réseau doivent correspondre au moins à la norme standard de 100 Mbit/s et à la bande passante de l’accès Internet ou de la spécification du routeur.

Si une solution Wi-Fi est envisagée pour connecter Screens à Internet, il est recommandé d’utiliser au minimum des standards Wi-Fi modernes tels que IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Les normes plus *récentes* comme 802.11h-n sont de meilleure qualité. Si un répéteur Wi-Fi est requis, il est fortement recommandé d’utiliser des technologies de point d’accès Wi-Fi maillé comme Google Nest Mesh Wi-Fi, ou un dispositif similaire.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour les opérations normales, par exemple une liste de lecture définie qui n’est pas très souvent actualisée au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.
Les tableaux ci-dessous offrent une bonne vue d’ensemble des données clés de connectivité réseau en ce qui concerne les performances prévisibles et les temps d’attente potentiels.

>[!NOTE]
>
>Toutes ces informations font référence à la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/mobile-router-download.png)
