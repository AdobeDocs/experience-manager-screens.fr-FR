---
title: Accès direct à Internet
description: Accès direct à Internet
exl-id: a393ce2f-b774-4cd5-9001-c5cc24d445ae
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 59%

---

# Réseau internet direct (câblé/sans fil) {#direct-internet-access}

Le réseau internet direct contient un point d’accès à Internet servant à atteindre les services cloud AEM auxquels AEM Screens doit se connecter.

Les ports standard pour la communication AEM Screens sont les suivants :

* `ssl-secured https (TCP Port 443)`
  <br>Ou,</br>

* `http (TCP Port 80)`, si votre cas d’utilisation particulier n’exige pas ce niveau de sécurité.

Les ports peuvent varier en fonction de la configuration de votre configuration AEM dédiée. Dans cette configuration, tous les appareils sont directement connectés à votre routeur internet, comme le montre la figure ci-dessous.

![](/help/assets/direct-access-2.png)

La configuration comporte également un accès internet proposé par différents fournisseurs d’accès (FAI) ainsi que sa ligne internet. La plupart des FAI fournissent un routeur Internet qui couvre le modem Internet, le commutateur réseau, le point d’accès Wi-Fi, le pare-feu et d’autres fonctionnalités réseau (selon le fabricant et le modèle).

## Connecter un lecteur AEM Screens à un accès internet direct

Pour vous assurer que les lecteurs AEM Screens sont correctement connectés dans cette configuration, procédez comme suit :

1. Assurez-vous que chacun des lecteurs d’écran AEM est connecté au réseau du routeur.
1. Testez la connexion internet en appelant une URL dans le navigateur de votre système.

   >[!NOTE]
   >Si vous recevez une erreur, vérifiez les paramètres réseau. Il existe essentiellement deux options pour une connexion réseau appropriée :
   >* DHCP
   >* Configuration IP manuelle

1. Assurez-vous que le paramètre de l’adaptateur réseau correspond aux paramètres de votre routeur ; vérifiez si le nombre maximal d’adresses IP disponibles dans votre réseau n’est pas atteint.
1. Vérifiez si le routeur est correctement connecté au réseau étendu du FAI (liaison Internet). Il peut également être identifié à l’aide d’un voyant sur les routeurs standard.
1. Si l’appel de l’URL aboutit, vous pouvez continuer à installer AEM Screens et vous enregistrer. Lancez AEM Screens.

   >[!NOTE]
   >**Conseil de dépannage**
   >Si AEM Screens ne se connecte pas correctement et que le contenu attendu ne s’affiche pas :
   >
   >1. Vérifiez dans le pare-feu de votre routeur Internet s’il existe des restrictions concernant `TCP/IP Port 80/443`.
   >1. Assurez-vous que tous les ports requis sont autorisés.

## Configurer un réseau internet direct {#requirements-direct}

Le réseau d’accès direct est logiquement scindé en deux blocs :

* Réseau étendu

* Réseau local

### Réseau étendu {#wan-connection}

Au-delà de l’accessibilité du réseau, les performances de la connexion Internet résident dans la capacité à fournir une bande passante suffisante pour utiliser AEM Screens.

*Suffisant* dépend du nombre d’AEM Screens connectées. Elle dépend également de l’utilisation d’autres consommateurs sur le réseau, comme les smartphones, tablettes, caisses enregistreuses, ordinateurs ou réseaux Wi-Fi invités.

>[!NOTE]
>
>Les appareils mentionnés ci-dessus ont un accès simultané à la connexion Internet et la bande passante diminue de façon linéaire lorsque vous ajoutez plus de consommateurs ou d’ordinateurs au réseau.

### Réseau local {#lan-connection}

Au-delà de l’accessibilité, les performances du réseau local tiennent à la capacité à fournir une bande passante suffisante pour utiliser AEM Screens.

Un réseau local correspond généralement à un débit de 100 Mbit/s, ce qui permet de disposer d’une bande passante suffisante pour connecter de nombreux appareils au système en assurant de bonnes performances.
Si une solution Wi-Fi est envisagée pour connecter AEM Screens à Internet, il est recommandé d’utiliser au minimum les standards Wi-Fi modernes comme `IEEE 802.11g`. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Les normes *plus récentes* comme `802.11h-n` sont de meilleure qualité.

>[!NOTE]
>
>Si un répéteur Wi-Fi est requis, Adobe recommande d’utiliser un point d’accès Wi-Fi maillé comme Google Nest Mesh Wi-Fi, ou un dispositif similaire. D’autres technologies de répéteurs de signaux Wi-Fi finissent par provoquer une perte massive de bande passante dans l’ensemble du réseau.

## Télécharger des médias et des ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs et utilisatrices de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. L’essentiel du trafic réseau a lieu lorsqu’un nouveau contenu doit être affiché sur un dispositif d’affichage spécifique.

Pour les opérations normales, par exemple une liste de lecture définie qui ne change pas très souvent au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.

Dans les scénarios où il y a plus d’interactions avec des capteurs ou des déclencheurs et du contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente un aperçu des données clés relatives à la connectivité réseau.

>[!NOTE]
>
>Ces informations vous permettent de visualiser la consommation de chaque appareil du réseau en demandant et en téléchargeant une source Internet. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/assets/download-times-direct.png)
