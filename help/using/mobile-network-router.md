---
title: Réseau mobile avec routeur de données mobile et composants réseau actifs
description: La page décrit le réseau mobile avec le routeur de données mobile et les composants réseau actifs
translation-type: tm+mt
source-git-commit: ec8af4e49694937a79ccbd78d51569f1031ca251
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 8%

---


# Réseau mobile avec routeur de données mobile et composants réseau actifs {#mobile-network-setup}

Les lecteurs AEM Screens Adobe peuvent également être connectés à l&#39;aide de réseaux mobiles ou cellulaires exécutant au moins un réseau 3G.

En AEM Screens, le contenu requis est physiquement téléchargé sur le contrôleur du lecteur ou sur l’ordinateur et correctement stocké dans le système d’exploitation sous-jacent. Par conséquent, la bande passante fournie n’a un impact que sur les temps de téléchargement initiaux, ainsi que sur les mises à jour du contenu, et n’a aucune incidence sur les performances de lecture régulière des Affichages.

L&#39;avantage de cette configuration est que le routeur mobile peut être placé dans un emplacement optimisé pour garantir la meilleure couverture réseau disponible. Il s&#39;agit généralement d&#39;une position élevée et ouverte, avec le moins de béton ou de métal environnant que possible.
Cette configuration permet aux utilisateurs d’AEM Screen de bénéficier d’une souplesse car aucune ligne fixe n’est nécessaire pour se connecter aux AEM Screens. Ceci est particulièrement intéressant pour les configurations éphémères ou mobiles.

Le diagramme suivant présente le réseau mobile avec routeur de données mobiles et la configuration des composants réseau actifs et contient un accès Internet de l&#39;un des contrôleurs AEM Screens par accès Internet direct à l&#39;aide d&#39;un lien de données 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Connexion du lecteur AEM Screens au réseau mobile avec le routeur de données mobile et les composants réseau actifs {#connecting-aem-screens-players}

Suivez les étapes ci-dessous pour vous assurer que les lecteurs d’écran AEM sont correctement connectés dans cette configuration :

La configuration alloue un accès Internet à chaque contrôleur AEM Screens par accès Internet direct à l&#39;aide d&#39;un lien de données 3/4/5G dédié.

1. Assurez-vous que le routeur de données mobile est correctement connecté au réseau de données cellulaires comme indiqué dans le système d&#39;exploitation et que chacun des lecteurs d&#39;écran AEM est connecté au réseau de routeurs.
1. Testez la connexion Internet en appelant une URL dans votre navigateur système.
   >[!NOTE]
   >Si vous recevez une erreur, vérifiez les paramètres réseau.Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle


1. Assurez-vous que le paramètre de carte réseau correspond à votre paramètre de routeur.

1. Vérifiez si le routeur est correctement connecté au réseau étendu du fournisseur de services Internet (lien Internet). Il peut également être identifié à l&#39;aide d&#39;un voyant de signal sur les routeurs standard.
1. Si l’appel d’URL aboutit, vous pouvez continuer à installer les AEM Screens et à vous enregistrer. AEM Screens Débuts.

   >[!NOTE]
   >**Conseil de dépannage**
   >Si les AEM Screens ne se connectent pas correctement et que le contenu attendu n’est pas affiché :
   >
   >1. Check in your Internet Router firewall if there are any restrictions regarding `TCP/IP Port 80/443`.



## Configuration d&#39;un réseau mobile avec un routeur de données mobile et des composants réseau actifs {#requirements-direct}

La configuration réseau peut être logiquement séparée en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

Les performances de la connexion Internet, en plus de l&#39;accessibilité réseau déjà décrite, doivent fournir une bande passante suffisante pour effectuer des téléchargements de contenu AEM Screens en douceur.

*Suffisant* dépend de la quantité de périphériques AEM screens connectés et de l&#39;utilisation d&#39;autres clients sur le réseau, tels que les Smartphones, les Tablets, les Caissiers, les Ordinateurs ou les réseaux Wi-Fi invités.
Gardez à l&#39;esprit que tous les périphériques ont un accès simultané à la connexion Internet et que la bande passante diminue habituellement de façon linéaire tout en ajoutant plus de consommateurs/ordinateurs au réseau.
Outre la connexion théorique spécifique au réseau, il faut s&#39;assurer que la couverture du routeur mobile est au moins &quot;bonne&quot;. De plus, le plan mensuel sous-jacent doit couvrir suffisamment de capacité de données et de bande passante pour desservir tous les clients connectés au sein du réseau local connecté.

Le tableau suivant présente les réseaux de données avec leur bande passante standard :

| Réseau de données | Bande passante |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1 000 à 1 000 Mbit/s |

Tout en envisageant le réseau de données à utiliser, il est recommandé de répondre aux questions suivantes :

* Combien de clients sont connectés au routeur ?

* Combien de changements de contenu sont attendus et quelles sont ces tailles de fichier moyennes ?

>[!NOTE]
>Le Package de données nécessaire doit être au moins :
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>Pour le téléchargement initial des fichiers multimédia, par exemple, tout en intégrant de nouveaux lecteurs, il faut s’attendre à une plus grande quantité de données et à une augmentation du temps de téléchargement, ce qui est reflété dans les hypothèses ci-dessus. Un réseau 4G avec une *bonne* couverture et des données illimitées doit correspondre aux installations les plus courantes de cette configuration réseau.


### Réseau local {#lan-connection}

Les performances du réseau local, en plus de l&#39;accessibilité réseau déjà décrite, doivent fournir une bande passante suffisante pour faire fonctionner les téléchargements de contenu AEM Screens en douceur. En ce moment, le réseau LAN correspond généralement à un réseau 100 Mbit/s, de sorte qu&#39;il devrait y avoir suffisamment de bande passante pour connecter de nombreux périphériques avec de bonnes performances au système. Lors de l&#39;utilisation d&#39;autres composants réseau actifs, il est obligatoire que tous ces composants correspondent aux exigences de bande passante réseau.

Par exemple, les composants réseau doivent correspondre au moins à la norme 100 Mbit/s et à la bande passante fournie par la spécification d&#39;accès Internet/routeur.

Si une solution Wi-Fi est envisagée pour connecter l&#39;écran à Internet Link, il est recommandé d&#39;utiliser au minimum des normes modernes de Wi-Fi telles que IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Toute *nouvelle* norme telle que 802.11h-n est de meilleure qualité. Si un répéteur Wi-Fi est nécessaire, nous recommandons vivement les technologies de point d&#39;accès Wi-Fi Mesh telles que Google Nest Mesh Wi-Fi ou d&#39;autres technologies similaires.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre localement tous les fichiers multimédia nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour un fonctionnement normal, par exemple après avoir défini une liste de lecture qui n&#39;est pas mise à jour fréquemment pendant la journée, cette opération offre une opération indépendante du réseau proche, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.
Les tableaux suivants offre une bonne vue d&#39;ensemble des données clés de connectivité réseau pour les performances prévisibles et les temps d&#39;attente potentiels.

>[!NOTE]
>Toutes les informations font référence à la consommation de chaque périphérique du réseau demandant et téléchargeant une source Internet. Chacune de ces requêtes additionne et étend le temps de téléchargement.

![](/help/using/assets/mobile-router-download.png)



