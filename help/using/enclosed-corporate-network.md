---
title: Réseau d’entreprise fermé
description: Réseau d’entreprise fermé
translation-type: tm+mt
source-git-commit: 31a6b202cae200e43e87db1df4e60f6f9d75c1bf
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 1%

---


# Réseaux d’entreprise fermés {#enclosed-corporate-networks}

La configuration de réseau d&#39;entreprise intégrée s&#39;applique aux petites, grandes et grandes entreprises. Il peut être théoriquement plus complexe, mais la configuration logique est toujours comme illustré ci-dessous dans un exemple simplifié.

## Conditions requises pour la configuration de réseaux d&#39;entreprise fermés {#requirements-enclosed-networks}

La configuration réseau d&#39;entreprise enfermée peut être logiquement séparée en deux blocs. Le bloc de connexion WAN/External World/Internet et le réseau local/local interne.

### Connexion WAN/Internet {#wan-connection}

Les performances de la connexion Internet ont, en plus de l&#39;accessibilité réseau déjà décrite, pour fournir suffisamment de bande passante pour fonctionner correctement et en douceur AEM Screens.
En détail, &quot;suffisant&quot; dépend de la quantité d’écrans AEM connectés et de l’utilisation d’autres consommateurs du réseau, tels que les Smartphones, les Tablettes, les Caissiers, les Ordinateurs ou les réseaux WIFI invités.
Gardez à l&#39;esprit que tous les périphériques ont un accès simultané à la connexion Internet et que la bande passante diminue habituellement de façon linéaire tout en ajoutant plus de consommateurs/ordinateurs au réseau.

### Connexion LAN {#lan-connection}

Les performances du réseau local ont, en plus de l&#39;accessibilité réseau déjà décrite, pour fournir une bande passante suffisante pour fonctionner correctement et en douceur AEM Screens. En ce moment, le réseau LAN au sein des entreprises correspond généralement au moins à un réseau de 1000 Mo/s, de sorte qu&#39;il devrait y avoir suffisamment de bande passante pour connecter de nombreux périphériques avec de bonnes performances au système. En utilisant d&#39;autres composants réseau actifs, il est obligatoire que tous ceux-ci correspondent aux exigences de bande passante du réseau. Par exemple, les composants réseau doivent correspondre au moins à la norme 1000 Mbit/s et à la bande passante fournie par la spécification d&#39;accès Internet/routeur.

### Autres caractéristiques des réseaux d&#39;entreprise {#other-networks}

Habituellement, les réseaux d&#39;entreprise ont une charge de périphériques connectés, peuvent être séparés en divers sous-réseaux et peuvent avoir des connexions Internet redondantes ou multiplexées pour fournir des performances suffisantes pour plusieurs milliers d&#39;accès simultanés.
Le schéma ci-dessus est simplifié et s&#39;adapte dans la plupart des cas à l&#39;environnement disponible pour le client.
Si une solution WiFI est envisagée pour connecter l&#39;écran à Internet Link, il est recommandé d&#39;utiliser au minimum des normes WIFI modernes comme IEEE 802.11g. Cette norme prend en charge les connexions jusqu’à 54 Mbit. Les normes &quot;plus récentes&quot; comme 802.11h-n sont de meilleure qualité. Si un répéteur WIFI est requis, nous recommandons fortement la technologie Mesh WIFI Accesspoint comme Google Nest Mesh WIFI ou similaire.
D&#39;autres technologies qui répètent le Wi-Fi finissent par provoquer une perte massive de bande passante dans l&#39;ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

Le AEM Screens offre un grand avantage aux utilisateurs de Digital Signage. Il est en train de télécharger et d’enregistrer localement tous les fichiers multimédia nécessaires, tels que les images et les vidéos. En raison de ce concept, le trafic réseau majeur se produit au cas où un nouveau contenu s’afficherait sur un écran spécifique.
Pour un fonctionnement normal, par exemple après avoir défini une liste de lecture qui n’est pas changée très souvent pendant la journée, cela offre une opération indépendante du réseau proche, une fois tous les fichiers enregistrés sur le lecteur. Pour les cas d&#39;utilisation où il y a plus d&#39;interactions avec les capteurs ou d&#39;autres déclencheurs et le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d&#39;écran immédiate afin d&#39;assurer une expérience client optimale.

Les tableaux ci-dessous offre une bonne vue d&#39;ensemble des données clés de connectivité réseau pour les performances prévisibles et les temps de fuite potentiels.

Toutes les informations doivent être considérées comme la consommation de chaque périphérique du réseau demandant et téléchargeant une source Internet. Ainsi, chacune de ces requêtes additionne et étend le temps de téléchargement.