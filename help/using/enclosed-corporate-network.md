---
title: Réseau d’entreprise fermé
description: Réseau d’entreprise fermé
exl-id: b8c52e72-86da-4089-ba02-0c643862419f
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: ht
source-wordcount: '710'
ht-degree: 100%

---

# Réseau d’entreprise fermé (câblé/sans fil) {#enclosed-corporate-networks}

La configuration de réseau d’entreprise fermé s’applique aux PME et grandes entreprises. Elle peut être plus complexe du point de vue théorique ; la configuration logique est présentée dans la figure ci-dessous.

![](/help/using/assets/enclosed-network-1.png)


## Connecter un lecteur AEM Screens à un accès internet direct

Pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration, procédez comme suit :

1. Veillez à ce que chacun des lecteurs AEM Screens soit connecté au réseau des routeurs.
1. Testez la connexion internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si une erreur s’affiche, vérifiez les paramètres réseau. Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle

1. Assurez-vous que le paramètre de l’adaptateur réseau correspond bien à vos paramètres de routeur et vérifiez si le nombre maximal d’adresses IP disponibles dans votre réseau n’est pas atteint.

1. Assurez-vous que le routeur est correctement connecté au réseau étendu du FAI (liaison internet). Vous pouvez également identifier la connexion à l’aide d’un voyant sur les routeurs standard.
1. Si l’appel de l’URL aboutit, vous pouvez continuer à installer AEM Screens et vous enregistrer. Lancez AEM Screens.

   >[!NOTE]
   >**Conseil de dépannage**
   >Si AEM Screens ne se connecte pas correctement et que le contenu attendu ne s’affiche pas :
   >
   >1. Vérifiez dans le pare-feu de votre routeur Internet s’il existe des restrictions concernant `TCP/IP Port 80/443`.
   >1. Assurez-vous que tous les ports requis sont autorisés.

## Configuration de réseaux d’entreprise fermés {#requirements-enclosed-networks}

La configuration de réseau d’entreprise fermé peut être séparée logiquement en deux blocs :

* Réseau étendu (WAN)
* Réseau local interne (LAN).

### Réseau étendu {#wan-connection}

Au-delà de l’accessibilité du réseau, les performances de la connexion internet résident dans la capacité à fournir une bande passante suffisante pour qu’AEM Screens télécharge le contenu de manière fluide.
La *bande passante suffisante* dépend du nombre d’appareils AEM Screens connectés. Cela dépend également de l’utilisation d’autres consommateurs sur le réseau, tels que les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.

>[!NOTE]
>
>Tous les appareils disposent d’un accès simultané à la connexion internet et la bande passante diminue de façon linéaire lorsque vous ajoutez des appareils consommateurs ou des ordinateurs au réseau.

### Réseau local {#lan-connection}

Au-delà de l’accessibilité, les performances du réseau local tiennent à la capacité à fournir une bande passante suffisante pour qu’AEM Screens télécharge le contenu de manière fluide.

Les réseaux locaux des entreprises atteignent généralement un débit de 1 000 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Si vous utilisez d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante du réseau.

Par exemple, les composants du réseau doivent correspondre au minimum à la norme standard de 100 Mbit/s et à la bande passante fournie par l’accès à internet ou les spécifications du routeur.

### Autres caractéristiques des réseaux d’entreprise {#other-networks}

Généralement, les réseaux d’entreprise présentent plusieurs appareils connectés. Ils peuvent également être séparés en divers sous-réseaux et posséder des connexions Internet redondantes ou multiplexées afin de fournir des performances suffisantes à plusieurs milliers d’accès simultanés.
Ce schéma est simplifié et convient le plus souvent aux environnements disponibles pour le client ou la cliente.

Si une solution Wi-Fi est envisagée pour connecter AEM Screens à Internet, il est recommandé d’utiliser au minimum les standards Wi-Fi modernes comme `IEEE 802.11g`. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Les normes *plus récentes* comme `802.11h-n` sont de meilleure qualité. Si un répéteur Wi-Fi est requis, il est fortement recommandé d’utiliser des technologies de point d’accès Wi-Fi maillé comme Google Nest Mesh Wi-Fi, ou un dispositif similaire.
D’autres technologies de répéteurs de signaux Wi-Fi finissent par provoquer une perte massive de bande passante dans l’ensemble du réseau.

## Télécharger des médias et des ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs et utilisatrices de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. L’essentiel du trafic réseau a lieu lorsqu’un nouveau contenu doit être affiché sur un dispositif d’affichage spécifique.

Pour les opérations normales, par exemple une liste de lecture définie qui ne change pas très souvent au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.

Pour les scénarios où il y a davantage d’interactions avec des capteurs ou d’autres déclencheurs et un contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente une vue d’ensemble des données clés relatives à la connectivité réseau.

>[!NOTE]
>Vous voyez ainsi la consommation de chaque appareil du réseau qui demande une source internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/enclosed-network-download.png)
