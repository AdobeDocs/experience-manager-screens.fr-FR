---
title: Accès direct à Internet
description: Accès direct à Internet
translation-type: tm+mt
source-git-commit: 6d6637d5222e861fa9a83f555baf0699f56f150a
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 36%

---


# Accès direct à Internet {#direct-internet-access}

Le Direct Internet Access SetUp contient un point d&#39;accès pour l&#39;accès à Internet afin d&#39;atteindre les AEM cloud services auxquels les AEM Screens doivent se connecter.

Les ports standard pour la communication AEM Screens sont les suivants :
* `http (TCP Port 80)`
Ou,
* `ssl-secured https (TCP Port 443)`

Les ports peuvent varier en fonction de la configuration de votre configuration AEM dédiée. Dans cette configuration, tous les appareils sont directement connectés à votre routeur Internet, comme le montre la figure ci-dessous.

![](/help/assets/direct-access-2.png)

La configuration inclut également un accès Internet par tout Prestataire Internet (FAI) et sa ligne Internet. La plupart des FAI fournissent un routeur Internet couvrant le modem Internet, le commutateur réseau, le point d&#39;accès WIFI, le pare-feu et d&#39;autres fonctionnalités réseau (selon le fabricant et le modèle).

## Connexion d&#39;un lecteur AEM Screens à un accès Internet direct {#connecting-aem-screens-players}

Suivez les étapes ci-dessous pour vous connecter aux lecteurs d’écran AEM dans cette configuration :

1. Assurez-vous que chacun des lecteurs d’écran AEM est connecté au réseau des routeurs.
1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si vous recevez un message d&#39;erreur, vérifiez les paramètres réseau.Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle


1. Assurez-vous que le paramètre de carte réseau correspond bien à votre paramètre de routeur et vérifiez si le nombre maximal d&#39;adresses IP disponibles dans votre réseau n&#39;est pas atteint.

1. Vérifiez si le routeur est correctement connecté au réseau étendu du fournisseur de services Internet (lien Internet). Il peut également être identifié à l&#39;aide d&#39;une DEL de signal sur les routeurs standard.
1. Si l&#39;appel d&#39;URL a réussi, vous pouvez continuer à installer les AEM Screens et à l&#39;enregistrer en conséquence.
1. AEM Screens Débuts.

   >[!NOTE]
   >**Conseil de dépannage**
   >Si le AEM Screens ne se connecte pas correctement et n’affiche pas le contenu attendu :
   >
   >1. Vérifiez dans le pare-feu de votre routeur Internet s’il existe des restrictions concernant `TCP/IP Port 80/443`.
   >1. Assurez-vous que tous les ports nécessaires sont autorisés.


## Configuration d’un réseau d’accès direct {#requirements-direct}

La configuration du réseau Direct Access peut être logiquement séparée en deux blocs :

* Réseau étendu

* Réseau local

### Réseau étendu {#wan-connection}

La performance de la connexion Internet en plus de l&#39;accessibilité du réseau, est de fournir suffisamment de bande passante pour fonctionner correctement en AEM Screens. Plus précisément, la bande passante suffisante dépend du nombre d’écrans AEM connectés et de l’utilisation d’autres appareils gourmands en bande passante sur le réseau, tels que les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.

>[!NOTE]
>Tous les périphériques ont un accès simultané à la connexion Internet et la bande passante diminue habituellement de façon linéaire lorsque vous ajoutez plus de consommateurs/ordinateurs au réseau.

### Réseau local {#lan-connection}

Les performances du réseau local (LAN), en plus de l&#39;accessibilité du réseau, fournissent une bande passante suffisante pour un bon fonctionnement AEM Screens.

Le réseau LAN correspond généralement au moins à un réseau de 100 Mo/s, de sorte qu&#39;il y a suffisamment de bande passante pour connecter de nombreux périphériques avec de bonnes performances au système.
Si une solution WIFI est envisagée pour connecter les AEM Screens à Internet Link, il est recommandé d&#39;utiliser au minimum des standards WIFI modernes tels que IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Toute *nouvelle* norme telle que 802.11h-n est de meilleure qualité.

>[!NOTE]
>Si un répéteur Wi-Fi est requis, nous recommandons fortement les technologies de point d’accès Wi-Fi Mesh comme Google Nest Wi-Fi Mesh ou similaire. D’autres technologies qui répètent le signal Wi-Fi finissent par provoquer une perte massive de bande passante dans l’ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre localement tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, le trafic réseau majeur survient lorsqu’un nouveau contenu doit être affiché sur un écran spécifique.
Pour le fonctionnement normal, par exemple, si vous avez défini une liste de lecture qui ne change pas très souvent au cours de la journée, cela permet d’opérer de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente un aperçu des données clés sur la connectivité réseau :

![](/help/assets/download-times-direct.png)

>[!NOTE]
>Vous voyez ainsi la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.