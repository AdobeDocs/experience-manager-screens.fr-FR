---
title: Réseau d’entreprise fermé
description: 'Réseau d’entreprise fermé '
translation-type: tm+mt
source-git-commit: 143036005bcaecf17e6b57f4e71a5e8a1b0cfe52
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 86%

---


# Réseau d’entreprise fermé  (câblé/sans fil) {#enclosed-corporate-networks}

La configuration de réseau d’entreprise fermé s’applique aux PME et grandes entreprises. Il peut être théoriquement plus complexe et la configuration logique est présentée dans la figure ci-dessous.

![](/help/using/assets/enclosed-network-1.png)


## Connexion d’un lecteur AEM Screens à un accès Internet direct {#connecting-aem-screens-players}

Procédez selon les étapes ci-dessous pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration :

1. Veillez à ce que chacun des lecteurs AEM Screens soit connecté au réseau des routeurs.
1. Testez la connexion Internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si une erreur est signalée, vérifiez les paramètres réseau. Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle


1. Assurez-vous que le paramètre de l’adaptateur réseau correspond bien à vos paramètres de routeur et vérifiez si le nombre maximal d’adresses IP disponibles dans votre réseau n’est pas atteint.

1. Assurez-vous que le routeur est correctement connecté au réseau étendu du FAI (liaison Internet). Vous pouvez également l’identifier à l’aide d’un voyant sur les routeurs standard.
1. Si l’appel de l’URL aboutit, vous pouvez continuer à installer AEM Screens et vous enregistrer. Lancez AEM Screens.

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

Les performances de la connexion Internet, outre l&#39;accessibilité réseau, doivent fournir une bande passante suffisante pour que le contenu AEM Screens soit mis à jour en douceur.
Plus précisément, cette bande passante *suffisante* tient à la quantité de postes AEM Screens connectés et à l’utilisation d’autres appareils consommateurs sur le réseau, comme les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.

>[!NOTE]
>Tous les appareils ont un accès simultané à la connexion Internet et la bande passante diminue de façon linéaire lorsque vous ajoutez des appareils consommateurs ou des ordinateurs au réseau.

### Réseau local {#lan-connection}

Les performances du réseau local (LAN), en plus de l&#39;accessibilité du réseau, doivent fournir une bande passante suffisante pour faire fonctionner les mises à jour de contenu AEM Screens en douceur.

Les réseaux locaux des entreprises atteignent généralement un débit de 1 000 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Si vous utilisez d’autres composants réseau actifs, il est obligatoire qu’ils correspondent aux exigences de bande passante du réseau.

Par exemple, les composants réseau doivent correspondre au moins à la norme 100 Mbit/s et à la bande passante fournie par la spécification d&#39;accès Internet/routeur.

### Autres caractéristiques des réseaux d’entreprise {#other-networks}

Généralement, les réseaux d’entreprise présentent un grand nombre d’appareils connectés. Ils peuvent également être séparés en divers sous-réseaux et posséder des connexions Internet redondantes ou multiplexées afin de fournir des performances suffisantes à plusieurs milliers d’accès simultanés.
Ce schéma est simplifié et convient le plus souvent aux environnements disponibles pour le client.

Si une solution Wi-Fi est envisagée pour connecter Screens à Internet, il est recommandé d’utiliser au minimum les standards Wi-Fi modernes comme `IEEE 802.11g`. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Les normes *plus récentes* comme `802.11h-n` sont de meilleure qualité. Si un répéteur Wi-Fi est requis, il est fortement recommandé d’utiliser des technologies de point d’accès Wi-Fi maillé comme Google Nest Mesh Wi-Fi, ou un dispositif similaire.
D’autres technologies de répéteurs de signaux Wi-Fi finissent par provoquer une perte massive de bande passante dans l’ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. L’essentiel du trafic réseau a lieu lorsqu’un nouveau contenu doit être affiché sur un dispositif d’affichage spécifique.

Pour les opérations normales, par exemple une liste de lecture définie qui ne change pas très souvent au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.

Pour les scénarios où il y a davantage d’interactions avec des capteurs ou d’autres déclencheurs et un contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente un aperçu des données clés relatives à la connectivité réseau.

>[!NOTE]
>Vous voyez ainsi la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/enclosed-network-download.png)
