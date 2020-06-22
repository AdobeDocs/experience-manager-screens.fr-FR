---
title: Réseau d’entreprise fermé
description: Réseau d’entreprise fermé
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 90%

---


# Réseaux d’entreprise fermés {#enclosed-corporate-networks}

La configuration de réseau d’entreprise fermé s’applique aux PME et grandes entreprises. En théorie, la configuration logique peut être plus complexe, mais elle correspond toujours à l’illustration simplifiée ci-dessous.

## Conditions requises pour la configuration des réseaux d’entreprise fermés {#requirements-enclosed-networks}

La configuration réseau d&#39;entreprise enfermée peut être logiquement séparée en deux blocs. Le réseau étendu (WAN) et le réseau local interne (LAN).

![](/help/using/assets/enclosed-network-1.png)

### Réseau étendu {#wan-connection}

En plus de l’accessibilité réseau déjà décrite, la connexion Internet doit fournir suffisamment de bande passante pour qu’AEM Screens fonctionne correctement et de manière fluide.
Plus précisément, la bande passante suffisante dépend du nombre d’écrans AEM connectés et de l’utilisation d’autres appareils gourmands en bande passante sur le réseau, tels que les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.
Gardez à l’esprit que tous les appareils ont un accès simultané à la connexion Internet et que la bande passante diminue généralement de façon linéaire à mesure que des appareils gourmands/ordinateurs sont ajoutés au réseau.

### Réseau local {#lan-connection}

En plus de l’accessibilité réseau déjà décrite, le réseau local doit fournir suffisamment de bande passante pour qu’AEM Screens fonctionne correctement et de manière fluide. Actuellement, le réseau LAN des entreprises atteint généralement un débit de 1 000 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Si vous utilisez d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante réseau. Par exemple, les composants réseau doivent correspondre au moins à la norme 1 000 Mbit/s et à la bande passante fournie par l’accès Internet/la spécification du routeur.

### Autres caractéristiques des réseaux d’entreprise {#other-networks}

Généralement, les réseaux d’entreprise présentent un grand nombre d’appareils connectés. Ils peuvent également être séparés en divers sous-réseaux et posséder des connexions Internet redondantes ou multiplexées afin de fournir des performances suffisantes à plusieurs milliers d’accès simultanés.
Le schéma simplifié ci-dessus s’adapte dans la plupart des cas à l’environnement disponible pour le client.
Si une solution Wi-Fi est envisagée pour connecter l’écran à Internet, il est recommandé d’utiliser au minimum les standards Wi-Fi modernes tels que IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit. Toute nouvelle norme telle que 802.11h-n est de meilleure qualité. Si un répéteur Wi-Fi est requis, nous recommandons fortement les technologies de point d’accès Wi-Fi Mesh comme Google Nest Wi-Fi Mesh ou similaire.
D’autres technologies qui répètent le signal Wi-Fi finissent par provoquer une perte massive de bande passante dans l’ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour le fonctionnement normal, par exemple, si vous avez défini une liste de lecture qui ne change pas très souvent au cours de la journée, cela permet d’opérer de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur. Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Les tableaux suivants offre une bonne vue d&#39;ensemble des données clés de connectivité réseau pour les performances prévisibles et les temps d&#39;attente potentiels.

Toutes ces informations doivent être considérées comme la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.