---
title: Accès direct à Internet
description: Accès direct à Internet
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 92%

---


# Accès direct à Internet {#direct-internet-access}

La configuration de l’accès direct à Internet contient un point d’accès pour l’accès à Internet afin d’atteindre les services cloud AEM auxquels AEM Screens doit se connecter.

Les ports standard pour la communication AEM Screens sont les suivants :
* `http (TCP Port 80)`
Ou,
* `ssl-secured https (TCP Port 443)`

Les ports peuvent varier en fonction de la configuration de votre configuration AEM dédiée. Dans cette configuration, tous les appareils sont directement connectés à votre routeur Internet, comme le montre la figure ci-dessous.

![](/help/assets/direct-access-2.png)

La configuration inclut également un accès Internet par tout Prestataire Internet (FAI) et sa ligne Internet. La plupart des FAI fournissent un routeur Internet couvrant le modem Internet, le commutateur réseau, le point d&#39;accès WIFI, le pare-feu et d&#39;autres fonctionnalités réseau (selon le fabricant et le modèle).

>[!NOTE]
>**Conseil de dépannage **>Si AEM Screens ne se connecte pas correctement et affiche le contenu attendu :
>
>1. Vérifiez dans le pare-feu de votre routeur Internet s’il existe des restrictions concernant `TCP/IP Port 80/443`.
>1. Assurez-vous que tous les ports requis sont autorisés et réessayez.


## Configuration d’un réseau d’accès direct {#requirements-direct}

La configuration du réseau d’accès direct peut être séparée logiquement en deux blocs. Le bloc WAN/monde extérieur/connexion Internet et le réseau local/interne.

### WAN/connexion Internet {#wan-connection}

En plus de l’accessibilité réseau déjà décrite, la connexion Internet doit fournir suffisamment de bande passante pour qu’AEM Screens fonctionne correctement et de manière fluide. Plus précisément, la bande passante suffisante dépend du nombre d’écrans AEM connectés et de l’utilisation d’autres appareils gourmands en bande passante sur le réseau, tels que les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.
Gardez à l’esprit que tous les appareils ont un accès simultané à la connexion Internet et que la bande passante diminue généralement de façon linéaire à mesure que des appareils gourmands/ordinateurs sont ajoutés au réseau.

### Connexion de réseau local {#lan-connection}

En plus de l’accessibilité réseau déjà décrite, le réseau local doit fournir suffisamment de bande passante pour qu’AEM Screens fonctionne correctement et de manière fluide. Actuellement, le réseau LAN atteint généralement un débit de 100 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances.
Si une solution Wi-Fi est envisagée pour connecter l’écran à Internet, il est recommandé d’utiliser au minimum les standards Wi-Fi modernes tels que IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit. Toute *nouvelle* norme telle que 802.11h-n est de meilleure qualité. Si un répéteur Wi-Fi est requis, nous recommandons fortement les technologies de point d’accès Wi-Fi Mesh comme Google Nest Wi-Fi Mesh ou similaire.
D’autres technologies qui répètent le signal Wi-Fi finissent par provoquer une perte massive de bande passante dans l’ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour le fonctionnement normal, par exemple, si vous avez défini une liste de lecture qui ne change pas très souvent au cours de la journée, cela permet d’opérer de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.
Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente un aperçu des données clés sur la connectivité réseau :

![](/help/assets/download-times-direct.png)

>[!NOTE]
>Vous voyez ainsi la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.