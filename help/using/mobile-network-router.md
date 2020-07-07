---
title: Réseau mobile avec routeur de données mobiles et composants réseau actifs
description: La page décrit le réseau mobile avec routeur de données mobiles et composants réseau actifs
translation-type: tm+mt
source-git-commit: ec8af4e49694937a79ccbd78d51569f1031ca251
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 75%

---


# Réseau mobile avec routeur de données mobile et composants réseau actifs {#mobile-network-setup}

Il est possible de connecter les lecteurs Adobe AEM Screens à l’aide de réseaux mobiles ou cellulaires qui sont au moins en 3G.

Dans AEM Screens, le contenu requis est téléchargé physiquement sur le contrôleur du lecteur ou sur l’ordinateur, et stocké de manière appropriée dans le système d’exploitation associé. Par conséquent, la bande passante fournie n’a un impact que sur les temps de téléchargement initiaux, ainsi que sur les mises à jour du contenu, et n’a aucune incidence sur les performances de lecture régulière des Affichages.

L&#39;avantage de cette configuration est que le routeur mobile peut être placé dans un emplacement optimisé pour garantir la meilleure couverture réseau disponible. Il s&#39;agit généralement d&#39;une position élevée et ouverte, avec le moins de béton ou de métal environnant que possible.
Cette configuration permet aux utilisateurs d’AEM Screen de bénéficier d’une souplesse car aucune ligne fixe n’est nécessaire pour se connecter aux AEM Screens. Ceci est particulièrement intéressant pour les configurations éphémères ou mobiles.

Le schéma suivant représente la configuration de réseau mobile avec routeur de données mobiles et composants réseau actifs. Celle-ci contient un accès Internet pour l’un des contrôleurs AEM Screens par un accès Internet direct à l’aide d’une liaison de données 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Connexion du lecteur AEM Screens au réseau mobile avec routeur de données mobile et composants réseau actifs {#connecting-aem-screens-players}

Procédez selon les étapes ci-dessous pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration :

La configuration alloue un accès Internet à chaque contrôleur AEM Screens par accès Internet direct à l&#39;aide d&#39;un lien de données 3/4/5G dédié.

1. Assurez-vous que le routeur de données mobile est correctement connecté au réseau de données cellulaire comme indiqué dans le système d’exploitation et que chacun des lecteurs d’écran AEM Screens est connecté au réseau de routeurs.
1. Testez la connexion Internet en appelant une URL dans votre navigateur système.
   >[!NOTE]
   >Si une erreur est signalée, vérifiez les paramètres réseau. Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle


1. Assurez-vous que le paramètre d’adaptateur réseau correspond à votre paramètre de routeur.

1. Vérifiez si le routeur est correctement connecté au réseau étendu du FAI (liaison Internet). Vous pouvez également l’identifier à l’aide d’un voyant sur les routeurs standard.
1. Si l’appel de l’URL aboutit, vous pouvez continuer à installer AEM Screens et vous enregistrer. Lancez AEM Screens.

   >[!NOTE]
   >**Conseil de dépannage**
   >Si AEM Screens ne se connecte pas correctement et que le contenu attendu ne s’affiche pas :
   >
   >1. Vérifiez dans le pare-feu de votre routeur Internet s’il existe des restrictions concernant `TCP/IP Port 80/443`.



## Configuration d’un réseau mobile avec routeur de données mobile et composants réseau actifs {#requirements-direct}

La configuration réseau peut être scindée logiquement en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

Les performances de la connexion Internet, en plus de l&#39;accessibilité réseau déjà décrite, doivent fournir une bande passante suffisante pour effectuer des téléchargements de contenu AEM Screens en douceur.

*Suffisant* dépend de la quantité de périphériques AEM screens connectés et de l&#39;utilisation d&#39;autres clients sur le réseau, tels que les Smartphones, les Tablets, les Caissiers, les Ordinateurs ou les réseaux Wi-Fi invités.
Gardez à l&#39;esprit que tous les périphériques ont un accès simultané à la connexion Internet et que la bande passante diminue habituellement de façon linéaire tout en ajoutant plus de consommateurs/ordinateurs au réseau.
Outre la connexion théorique spécifique au réseau, il faut s&#39;assurer que la couverture du routeur mobile est au moins &quot;bonne&quot;. De plus, la formule mensuelle associée doit couvrir une capacité de données et une bande passante suffisantes pour répondre aux besoins de tous les clients connectés au réseau local.

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
>Le package de données nécessaire doit respecter les conditions suivantes :
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>Pour le chargement initial des fichiers multimédias, par exemple pour l’intégration de nouveaux lecteurs, il est probable que le volume de données et la durée de téléchargement seront plus importants, ce qui devra être repris dans les hypothèses ci-dessus. Un réseau 4G possédant une *bonne* couverture et un volume de données illimité devrait correspondre aux installations les plus courantes de cette configuration de réseau.


### Réseau local {#lan-connection}

Les performances du réseau local, en plus de l&#39;accessibilité réseau déjà décrite, doivent fournir une bande passante suffisante pour faire fonctionner les téléchargements de contenu AEM Screens en douceur. Actuellement, le réseau local atteint généralement un débit de 100 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Si vous utilisez d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante du réseau.

Par exemple, les composants réseau doivent correspondre au moins à la norme standard de 100 Mbit/s et à la bande passante de l’accès Internet ou de la spécification du routeur.

Si une solution Wi-Fi est envisagée pour connecter Screens à Internet, il est recommandé d’utiliser au minimum des standards Wi-Fi modernes tels que IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Les normes plus *récentes* comme 802.11h-n sont de meilleure qualité. Si un répéteur Wi-Fi est requis, il est fortement recommandé d’utiliser des technologies de point d’accès Wi-Fi maillé comme Google Nest Mesh Wi-Fi, ou un dispositif similaire.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour les opérations normales, par exemple une liste de lecture définie qui n’est pas très souvent actualisée au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.
Les tableaux ci-dessous offrent une bonne vue d’ensemble des données clés de connectivité réseau en ce qui concerne les performances prévisibles et les temps d’attente potentiels.

>[!NOTE]
>Toutes ces informations font référence à la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/mobile-router-download.png)



