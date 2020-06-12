---
title: Accès direct à Internet
description: Accès direct à Internet
translation-type: tm+mt
source-git-commit: 3527dd38898399e692e114edb492825b18b28f86
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# Accès direct à Internet {#direct-internet-access}

La configuration Direct Internet Access contient un point d’accès à Internet pour accéder aux services AEM Cloud auxquels AEM Screens doit se connecter.

Les ports standard pour la communication AEM Screens sont les suivants :
* `http (TCP Port 80)`
Ou,
* `ssl-secured https (TCP Port 443)`

Les ports peuvent varier en fonction de la configuration de votre configuration AEM dédiée. Dans cette configuration, tous les périphériques sont directement connectés à votre routeur Internet, comme le montre la figure ci-dessous.

![](/help/assets/direct-access-2.png)

La configuration inclut également un accès Internet par tout prestataire Internet et sa ligne Internet. La plupart des FAI fournissent un routeur Internet couvrant le modem Internet, le commutateur réseau, le point d’accès WIFI, le pare-feu et d’autres fonctionnalités réseau (selon le fabricant et le modèle).

>[!NOTE]
>**Conseil de dépannage **>Si AEM Screens ne se connecte pas correctement et affiche le contenu attendu :
>
>1. Vérifiez dans votre pare-feu de routeur Internet s&#39;il existe des restrictions concernant `TCP/IP Port 80/443`.
>1. Assurez-vous que tous les ports requis sont autorisés et réessayez.


## Configuration d&#39;un réseau Direct Access {#requirements-direct}

La configuration du réseau Direct Access peut être logiquement séparée en deux blocs. Le bloc de connexion WAN/External World/Internet et le réseau local/local interne.

### Connexion WAN/Internet {#wan-connection}

Les performances de la connexion Internet ont pour but, en plus de l’accessibilité réseau déjà décrite, de fournir une bande passante suffisante pour faire fonctionner AEM Screens de manière agréable et fluide. En détail, &quot;suffisant&quot; dépend de la quantité d’écrans AEM connectés et de l’utilisation d’autres consommateurs du réseau, tels que les Smartphones, les Tablettes, les Caissiers, les Ordinateurs ou les réseaux WIFI invités.
Gardez à l&#39;esprit que tous les périphériques ont un accès simultané à la connexion Internet et que la bande passante diminue habituellement de façon linéaire tout en ajoutant plus de consommateurs/ordinateurs au réseau.

### Connexion LAN {#lan-connection}

Les performances du réseau local ont, en plus de l&#39;accessibilité réseau déjà décrite, pour fournir une bande passante suffisante pour faire fonctionner AEM Screens de manière agréable et sans heurts. En ce moment, le réseau LAN correspond généralement à un réseau de 100 Mo/s, de sorte qu&#39;il devrait y avoir suffisamment de bande passante pour connecter de nombreux périphériques avec de bonnes performances au système.
Si une solution WIFI est envisagée pour connecter l&#39;écran à Internet Link, il est recommandé d&#39;utiliser au minimum les standards WIFI modernes tels que IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit. Toute *nouvelle* norme telle que 802.11h-n est de meilleure qualité. Si un répéteur WIFI est requis, nous recommandons fortement les technologies de point d&#39;accès Mesh WIFI comme Google Nest Mesh WIFI ou similaire.
D&#39;autres technologies qui répètent le Wi-Fi finissent par provoquer une perte massive de bande passante dans l&#39;ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de Digital Signage. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que des images et des vidéos. En raison de ce concept, le trafic réseau majeur se produit au cas où un nouveau contenu s’afficherait sur un écran spécifique.
Pour une opération normale, par exemple, après avoir défini une liste de lecture qui ne change pas très souvent pendant la journée, cette opération offre une opération indépendante du réseau proche, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d&#39;utilisation où il y a plus d&#39;interactions avec des capteurs ou d&#39;autres déclencheurs et le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d&#39;écran immédiate afin d&#39;assurer une expérience client optimale.

Le tableau suivant présente un aperçu des données clés de connectivité réseau :

![](/help/assets/direct-access-1.png)

>[!NOTE]
>Ces informations vous permettent de vue la consommation de chaque périphérique du réseau qui demande et télécharge une source Internet. Ainsi, chacune de ces requêtes additionne et étend le temps de téléchargement.