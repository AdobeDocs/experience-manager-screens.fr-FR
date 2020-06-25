---
title: Réseau d’entreprise fermé
description: Réseau d’entreprise fermé
translation-type: tm+mt
source-git-commit: ed683a86b7e8c6ec06309577bd0a8690a9cc4684
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 29%

---


# Réseaux d&#39;entreprise fermés (câblés/sans fil) {#enclosed-corporate-networks}

La configuration de réseau d’entreprise fermé s’applique aux PME et grandes entreprises. Il peut être théoriquement plus complexe, mais la configuration logique est présentée dans la figure ci-dessous.

![](/help/using/assets/enclosed-network-1.png)


## Connexion d&#39;un lecteur AEM Screens à un accès Internet direct {#connecting-aem-screens-players}

Suivez les étapes ci-dessous pour vous assurer que les lecteurs d’écran AEM sont correctement connectés dans cette configuration :

1. Assurez-vous que chacun des lecteurs d’écran AEM est connecté au réseau des routeurs.
1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si vous recevez une erreur, vérifiez les paramètres réseau.Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle


1. Assurez-vous que le paramètre de carte réseau correspond bien à vos paramètres de routeur et vérifiez si le nombre maximal d&#39;adresses IP disponibles dans votre réseau n&#39;est pas atteint.

1. Vérifiez si le routeur est correctement connecté au réseau étendu du fournisseur de services Internet (lien Internet). Vous pouvez également l&#39;identifier à l&#39;aide d&#39;un voyant de signalisation sur les routeurs standard.
1. Si l’appel d’URL aboutit, vous pouvez continuer à installer les AEM Screens et à vous enregistrer. AEM Screens Débuts.

   >[!NOTE]
   >**Conseil de dépannage**
   >Si les AEM Screens ne se connectent pas correctement et que le contenu attendu n’est pas affiché :
   >
   >1. Check in your Internet Router firewall if there are any restrictions regarding `TCP/IP Port 80/443`.
   >1. Assurez-vous que tous les ports requis sont autorisés.


## Conditions requises pour la configuration des réseaux d’entreprise fermés {#requirements-enclosed-networks}

La configuration réseau d&#39;entreprise enfermée peut être logiquement séparée en deux blocs :

* Réseau étendu (WAN)
* Réseau local interne (LAN).

### Réseau étendu {#wan-connection}

La performance de la connexion Internet en plus de l&#39;accessibilité du réseau, est de fournir suffisamment de bande passante pour fonctionner correctement en AEM Screens.
*Une bande passante* suffisante dépend de la quantité d’écrans AEM connectés et de l’utilisation d’autres clients du réseau, tels que les Smartphones, les Tablettes, les Caissiers, les Ordinateurs ou les réseaux Wi-Fi invités.

>[!NOTE]
>Tous les périphériques ont un accès simultané à la connexion Internet et la bande passante diminue régulièrement lorsque vous ajoutez plus de consommateurs ou d&#39;ordinateurs au réseau.

### Réseau local {#lan-connection}

En plus de la facilité d&#39;accès au réseau, la performance du réseau local (LAN) est de fournir une bande passante suffisante pour un bon fonctionnement AEM Screens.

Actuellement, le réseau LAN des entreprises atteint généralement un débit de 1 000 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Lors de l&#39;utilisation d&#39;autres composants réseau actifs, il est obligatoire que tous ces composants correspondent aux exigences de bande passante réseau.

Par exemple, les composants réseau doivent correspondre au moins à la norme 1 000 Mbit/s et à la bande passante fournie par la spécification d&#39;accès Internet/routeur.

### Autres caractéristiques des réseaux d’entreprise {#other-networks}

Habituellement, les réseaux d&#39;entreprise ont une charge de périphériques connectés, peuvent être séparés en divers sous-réseaux et peuvent avoir des connexions Internet redondantes ou multiplexées pour fournir des performances suffisantes pour plusieurs milliers d&#39;accès simultanés.
Ce schéma est simplifié et s&#39;adapte dans la plupart des cas à l&#39;environnement disponible pour le client.

In case that an Wi-Fi solution is envisaged to connect screen to the internet Link it is recommended to use modern Wi-Fi standards like `IEEE 802.11g` as a minimum. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Toute *nouvelle* norme telle que est de meilleure qualité. `802.11h-n` Si un répéteur Wi-Fi est nécessaire, nous recommandons vivement les technologies de point d&#39;accès Wi-Fi Mesh telles que Google Nest Mesh Wi-Fi ou d&#39;autres technologies similaires.
D&#39;autres technologies qui répètent le Wi-Fi finissent par provoquer une perte massive de bande passante dans l&#39;ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. En raison de ce concept, la majorité du trafic réseau a lieu lorsqu’un nouveau contenu s’affiche sur un écran spécifique.
Pour le fonctionnement normal, par exemple, si vous avez défini une liste de lecture qui ne change pas très souvent au cours de la journée, cela permet d’opérer de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur. Pour les cas d’utilisation où il y a plus d’interactions avec des capteurs ou d’autres déclencheurs et lorsque le contenu est très dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Les tableaux suivants offre une bonne vue d&#39;ensemble des données clés de connectivité réseau pour les performances prévisibles et les temps d&#39;attente potentiels.

>[!NOTE]
>Toutes ces informations doivent être considérées comme la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces requêtes additionne et étend le temps de téléchargement.

![](/help/using/assets/enclosed-network-download.png)