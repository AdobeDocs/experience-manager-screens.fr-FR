---
title: Réseau mobile avec routeur de données mobile et composants réseau actifs
description: La page décrit le réseau mobile avec routeur de données mobiles et composants réseau actifs
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
TQID: https://experienceleague.adobe.com/uKyl9w97xF0m6W9kj-PTAbIgt5HtZRAgkOUCstAuti4
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 824
ht-degree: 86%

---

# Réseau mobile avec routeur de données mobile et composants réseau actifs {#mobile-network-setup}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Il est possible de connecter les lecteurs Adobe AEM Screens à l’aide de réseaux mobiles ou cellulaires qui sont au moins en 3G.

Dans AEM Screens, le contenu requis est téléchargé physiquement sur le contrôleur du lecteur ou sur l’ordinateur, et stocké de manière appropriée dans le système d’exploitation associé. Par conséquent, la bande passante fournie n’a un impact que sur les temps de téléchargement initiaux, ainsi que sur les mises à jour du contenu, et n’a aucune incidence sur les performances de lecture ordinaire sur les affichages.

L&#39;avantage de cette configuration est que le routeur mobile peut être placé dans un endroit optimisé pour assurer la meilleure couverture réseau disponible. Ce point est généralement en position élevée et ouverte, avec le moins de structures métalliques ou de béton environnantes possible.
Cette configuration donne aux utilisateurs d’AEM Screen de la flexibilité, car aucune ligne fixe n’est requise pour se connecter à AEM Screens. Il est également intéressant pour les configurations éphémères ou mobiles.

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

*Suffisant* dépend du nombre d’appareils AEM Screens connectés. Cela dépend également de l&#39;utilisation d&#39;autres consommateurs au sein du réseau, tels que les smartphones, les tablettes, les caissiers, les ordinateurs ou les réseaux Wi-Fi invités.
Gardez à l&#39;esprit que tous les appareils ont un accès simultané à la connexion Internet et que la bande passante diminue régulièrement tout en ajoutant plus de consommateurs/ordinateurs au réseau.
Outre la connexion réseau théorique spécifique, il faut s&#39;assurer que la couverture du routeur mobile est au moins *bonne*. En outre, le plan mensuel sous-jacent doit couvrir suffisamment de capacité de données et de bande passante pour desservir tous les clients connectés au sein du réseau local connecté.

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

AEM Screens offre un avantage significatif aux utilisateurs de signalétique numérique. Il télécharge et enregistre localement tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, le trafic réseau majeur se produit dans le cas où un nouveau contenu doit être affiché sur un écran spécifique.
Pour un fonctionnement normal, avec une liste de lecture définie qui n’est pas mise à jour fréquemment, il offre un fonctionnement quasi indépendant du réseau lorsque tous les fichiers sont enregistrés sur le lecteur.
Pour les cas d’utilisation où il existe davantage d’interactions avec les capteurs ou d’autres déclencheurs et où le contenu est dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction immédiate à l’écran. Cela garantit la meilleure expérience client possible.
Les tableaux suivants offrent un bon aperçu de la signification des données clés de connectivité réseau pour les performances attendues et les temps d’attente potentiels.

>[!NOTE]
>
>Toutes ces informations font référence à la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/mobile-router-download.png)
