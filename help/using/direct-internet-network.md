---
title: Accès direct à Internet
description: Accès direct à Internet
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 94%

---


# Réseau Internet direct (câblé/sans fil) {#direct-internet-access}

Le réseau Internet direct contient un point d’accès à Internet servant à atteindre les services cloud AEM auxquels AEM Screens doit se connecter.

Les ports standard pour la communication AEM Screens sont les suivants :
* `ssl-secured https (TCP Port 443)`

   <br>Ou,</br>

* `http (TCP Port 80)`, si votre cas d&#39;utilisation particulier n&#39;exige pas ce niveau de sécurité.

Les ports peuvent varier en fonction de la mise en place de votre configuration AEM dédiée. Dans cette configuration, tous les appareils sont directement connectés à votre routeur Internet, comme le montre la figure ci-dessous.

![](/help/assets/direct-access-2.png)

La configuration comporte également un accès Internet proposé par différents fournisseurs d’accès (FAI) ainsi que sa ligne Internet. La plupart des FAI fournissent un routeur Internet qui sert de modem Internet, commutateur réseau, point d’accès Wi-Fi et pare-feu, et peut également remplir d’autres fonctionnalités réseau (selon le fabricant et le modèle).

## Connexion d’un lecteur AEM Screens à un accès Internet direct {#connecting-aem-screens-players}

Procédez selon les étapes ci-dessous pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration :

1. Assurez-vous que chacun des lecteurs d’écran AEM est connecté au réseau du routeur.
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


## Configuration d’un réseau d’accès direct {#requirements-direct}

Le réseau d’accès direct est logiquement scindé en deux blocs :

* Réseau étendu

* Réseau local

### Réseau étendu {#wan-connection}

Au-delà de l’accessibilité du réseau, les performances de la connexion Internet résident dans la capacité à fournir une bande passante suffisante pour utiliser AEM Screens.

Plus précisément, cette bande passante *suffisante* tient au nombre de postes AEM Screens connectés et à l’utilisation d’autres appareils consommateurs sur le réseau, comme les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.

>[!NOTE]
>
>Tous les appareils mentionnés ci-dessus ont un accès simultané à la connexion Internet et la bande passante diminue de façon linéaire lorsque vous ajoutez des appareils consommateurs ou des ordinateurs au réseau.

### Réseau local {#lan-connection}

Les performances du réseau local (LAN), outre l’accessibilité du réseau, correspondent à une bande passante suffisante pour exploiter AEM Screens.

Un réseau local correspond généralement à un débit de 100 Mbit/s, ce qui permet de disposer d’une bande passante suffisante pour connecter de nombreux appareils au système en assurant de bonnes performances.
Si une solution Wi-Fi est envisagée pour connecter AEM Screens à Internet, il est recommandé d’utiliser au minimum les standards Wi-Fi modernes comme `IEEE 802.11g`. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Les normes *plus récentes* comme `802.11h-n` sont de meilleure qualité.

>[!NOTE]
>
>Si un répéteur Wi-Fi est requis, il est fortement recommandé d’utiliser un point d’accès Wi-Fi maillé comme Google Nest Mesh Wi-Fi, ou un dispositif similaire. D’autres technologies de répéteurs de signaux Wi-Fi finissent par provoquer une perte massive de bande passante dans l’ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. L’essentiel du trafic réseau a lieu lorsqu’un nouveau contenu doit être affiché sur un dispositif d’affichage spécifique.

Pour les opérations normales, par exemple une liste de lecture définie qui ne change pas très souvent au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.

Pour les scénarios où il y a davantage d’interactions avec des capteurs ou d’autres déclencheurs et un contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente un aperçu des données clés relatives à la connectivité réseau.

>[!NOTE]
>
>Vous voyez ainsi la consommation de chaque appareil du réseau qui demande une source Internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/assets/download-times-direct.png)

