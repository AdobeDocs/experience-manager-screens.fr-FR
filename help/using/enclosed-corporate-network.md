---
title: Réseau d’entreprise fermé
description: Réseau d’entreprise fermé
translation-type: tm+mt
source-git-commit: 8e62b3fc4ce324e02aaec6fca9df79b1aaf94d72
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 44%

---


# Réseaux d&#39;entreprise fermés (câblés/sans fil) {#enclosed-corporate-networks}

La configuration de réseau d’entreprise fermé s’applique aux PME et grandes entreprises. Il peut être théoriquement plus complexe, mais la configuration logique est présentée dans la figure ci-dessous.

![](/help/using/assets/enclosed-network-1.png)

## Conditions requises pour la configuration des réseaux d’entreprise fermés {#requirements-enclosed-networks}

La configuration réseau d&#39;entreprise enfermée peut être logiquement séparée en deux blocs :

* Réseau étendu (WAN)
* Réseau local interne (LAN).

### Réseau étendu {#wan-connection}

La performance de la connexion Internet en plus de l&#39;accessibilité du réseau, est de fournir suffisamment de bande passante pour fonctionner correctement en AEM Screens.
*Une bande passante* suffisante dépend de la quantité d’écrans AEM connectés et de l’utilisation d’autres clients sur le réseau, tels que les Smartphones, les Tablettes, les Caissiers, les Ordinateurs ou les réseaux WIFI invités.

>[!NOTE]
>Tous les périphériques ont un accès simultané à la connexion Internet et la bande passante diminue régulièrement lorsque vous ajoutez plus de consommateurs ou d&#39;ordinateurs au réseau.

### Réseau local {#lan-connection}

En plus de la facilité d&#39;accès au réseau, la performance du réseau local (LAN) est de fournir une bande passante suffisante pour un bon fonctionnement AEM Screens.

Actuellement, le réseau LAN des entreprises atteint généralement un débit de 1 000 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Lors de l&#39;utilisation d&#39;autres composants réseau actifs, il est obligatoire que tous ces composants correspondent aux exigences de bande passante réseau.

Par exemple, les composants réseau doivent correspondre au moins à la norme 1 000 Mbit/s et à la bande passante fournie par la spécification d&#39;accès Internet/routeur.

### Autres caractéristiques des réseaux d’entreprise {#other-networks}

Habituellement, les réseaux d&#39;entreprise ont une charge de périphériques connectés, peuvent être séparés en divers sous-réseaux et peuvent avoir des connexions Internet redondantes ou multiplexées pour fournir des performances suffisantes pour plusieurs milliers d&#39;accès simultanés.
Ce schéma est simplifié et s&#39;adapte dans la plupart des cas à l&#39;environnement disponible pour le client.

In case that an WIFI solution is envisaged to connect screen to the internet Link it is recommended to use modern WIFI standards like `IEEE 802.11g` as a minimum. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Toute *nouvelle* norme telle que est de meilleure qualité. `802.11h-n` Si un répéteur Wi-Fi est requis, nous recommandons fortement les technologies de point d’accès Wi-Fi Mesh comme Google Nest Wi-Fi Mesh ou similaire.
D’autres technologies qui répètent le signal Wi-Fi finissent par provoquer une perte massive de bande passante dans l’ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour le fonctionnement normal, par exemple, si vous avez défini une liste de lecture qui ne change pas très souvent au cours de la journée, cela permet d’opérer de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur. Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Les tableaux suivants offre une bonne vue d&#39;ensemble des données clés de connectivité réseau pour les performances prévisibles et les temps d&#39;attente potentiels.

>[!NOTE]
>Toutes ces informations doivent être considérées comme la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces requêtes additionne et étend le temps de téléchargement.

![](/help/using/assets/enclosed-network-download.png)