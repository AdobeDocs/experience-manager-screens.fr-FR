---
title: Réseau mobile avec routeur de données mobile et composants réseau actifs
description: La page décrit le réseau mobile avec le routeur de données mobile et les composants réseau actifs
translation-type: tm+mt
source-git-commit: 5460e384e96553d9f0478113368e31cf266479a4
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 19%

---


# Réseau mobile avec routeur de données mobile et composants réseau actifs {#mobile-network-setup}

Les lecteurs AEM Screens Adobe peuvent également être connectés à l&#39;aide de réseaux mobiles/cellulaires exécutant au moins un réseau 3G.
Dans les AEM Screens, le contenu nécessaire est physiquement téléchargé sur le contrôleur/ordinateur du lecteur et correctement stocké dans le système d&#39;exploitation sous-jacent. Par conséquent, la bande passante donnée n’a qu’une incidence sur les temps de téléchargement initiaux et n’a aucune incidence sur les performances des systèmes d’affichage.
Connexion des lecteurs AEM Screens avec une connexion cellulaire 3/4/5G à votre fournisseur de données de service mobile. L&#39;avantage de cette configuration est que le routeur mobile peut être placé dans un emplacement optimisé pour garantir la meilleure couverture réseau disponible. Il s&#39;agit généralement d&#39;une position élevée et ouverte, avec le plus de béton ou de métal environnant le moins possible.
Cette configuration offre aux utilisateurs d’écran AEM une grande flexibilité car aucune ligne fixe n’est nécessaire pour connecter les AEM Screens.

![](/help/using/assets/mobile-network-1.png)

## Connexion d&#39;un lecteur AEM Screens à un réseau mobile direct {#connecting-aem-screens-players}

Suivez les étapes ci-dessous pour vous connecter aux lecteurs d’écran AEM dans cette configuration :

La configuration contient un accès Internet de l&#39;un des contrôleurs AEM Screens par accès direct à Internet en utilisant un lien de données 3/4/5G.
La connexion appropriée des lecteurs d’écran AEM dans cette configuration est simple :

1. Assurez-vous que le routeur de données mobile est correctement connecté au réseau de données cellulaires, comme indiqué dans le système d&#39;exploitation.
1. Assurez-vous que chacun des lecteurs d’écran AEM est connecté au réseau Routeurs.
1. Testez la connexion Internet en appelant une URL dans votre navigateur système.
   >[!NOTE]
   >Si vous recevez un message d&#39;erreur, vérifiez les paramètres réseau.Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle


1. Assurez-vous que le paramètre de carte réseau correspond bien à votre paramètre de routeur.
1. Vérifiez si le routeur est correctement connecté au réseau étendu du fournisseur de services Internet (lien Internet). Il peut également être identifié à l&#39;aide d&#39;une DEL de signal sur les routeurs standard. Si ce n&#39;est pas le cas, veuillez contacter votre service ISP pour vérifier votre routeur à distance.
iv. Si tous les éléments ci-dessus sont correctement configurés et qu&#39;un message d&#39;erreur s&#39;affiche toujours, vérifiez les composants réseau actifs tels que les commutateurs ou les routeurs supplémentaires s&#39;il existe une restriction de port.
1. Si l’appel d’URL a réussi, vous pouvez continuer à installer les AEM Screens et à l’enregistrer en conséquence. AEM Screens Débuts

   >[!NOTE]
   >**Conseil de dépannage**
   >Si le AEM Screens ne se connecte pas correctement et n’affiche pas le contenu attendu :
   >
   >1. Vérifiez dans le pare-feu de votre routeur Internet s’il existe des restrictions concernant `TCP/IP Port 80/443`.
   >1. Assurez-vous que tous les ports nécessaires sont autorisés.



## Configuration requise pour la configuration de la configuration réseau mobile {#requirements-direct}

La configuration réseau peut être logiquement séparée en deux blocs :

* Connexion Internet mobile

* Réseau local

### Connexion Internet mobile {#mobile-internet-connection}

Les performances de la connexion Internet ont, en plus de l&#39;accessibilité réseau déjà décrite, pour fournir suffisamment de Bandwith pour opérer AEM Screens gentiment et en douceur. En détail, &quot;suffisant&quot; dépend de la quantité d’écrans AEM connectés et de l’utilisation d’autres consommateurs du réseau, tels que les Smartphones, les Tablettes, les Caissiers, les Ordinateurs ou les réseaux Wifi invités.
Gardez à l&#39;esprit que tous les appareils ont un accès simultané à la connexion Internet et Bandwith diminue habituellement de façon linéaire tout en ajoutant plus de consommateurs/ordinateurs au réseau.
En plus de la connexion réseau théorique spécifique, il doit être assuré, que la couverture du routeur mobile est au moins &quot;bonne&quot; (veuillez consulter le manuel de votre routeur mobile). De plus, le plan mensuel sous-jacent doit couvrir suffisamment de capacité de données et de bande passante pour desservir tous les clients connectés au sein du réseau local connecté.
Les réseaux de données fournissent des Bandwith standard ayant environ.. jusqu&#39;à :
* 3Go 42Mbit/s ・ 4Go 150Mbit/s ・ 5Go 1000Mbit/s-10000Mbit/sLors de l&#39;examen du réseau de données à utiliser, il est recommandé de répondre aux questions suivantes :
・ Combien de clients sont connectés au routeur ?
・ Combien de changements de contenu dois-je attendre et quelles sont ces tailles de fichier moyennes ?
Pour donner suite, le Package de données nécessaire doit au moins être :
   `Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`
Assurez-vous qu&#39;il y a suffisamment de tampon.
Attention : Pour le téléchargement initial des fichiers multimédia, par exemple, lors de l’intégration de nouveaux lecteurs, une plus grande quantité de données et une durée de téléchargement accrue doivent être attendues et être reflétées dans les hypothèses ci-dessus.


### Réseau local {#lan-connection}

La performance du réseau local a, outre la disponibilité déjà décrite, de fournir un Bandwith suffisant pour opérer les AEM Screens gentiment et en douceur. En ce moment, le réseau LAN correspond généralement à un réseau de 100 Mo/s, de sorte qu&#39;il devrait y avoir suffisamment de Bandwith pour connecter de nombreux périphériques avec de bonnes performances au système. En utilisant d&#39;autres composants réseau actifs, il est obligatoire que tous ceux-ci correspondent à la bande réseau avec les exigences. Par exemple, les composants réseau doivent correspondre au moins à la norme 100 Mbit/s et à la bande fournie par la spécification d&#39;accès Internet/routeur.
Si une solution WiFI est envisagée pour connecter l&#39;écran à Internet Link, il est recommandé d&#39;utiliser au minimum des normes WIFI modernes comme IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit. Toute nouvelle norme telle que 802.11h-n est de meilleure qualité. Si un répéteur Wifi est requis, nous recommandons vivement la technologie Mesh Wifi Access Point comme Google Nest Mesh Wifi ou similaire.
D&#39;autres technologies qui répètent le Wi-Fi finissent par provoquer une perte massive de Bandwith dans l&#39;ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour le fonctionnement normal, par exemple, si vous avez défini une liste de lecture qui ne change pas très souvent au cours de la journée, cela permet d’opérer de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.
Les tableaux ci-dessous offrent une bonne vue d’ensemble des données clés de connectivité réseau en ce qui concerne les performances prévisibles et les temps d’attente potentiels.
Toutes ces informations doivent être considérées comme la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/mobile-router-download.png)



