---
title: Accès direct à Internet
description: Accès direct à Internet
translation-type: tm+mt
source-git-commit: 6afb71bd969ccfde91c2172ceb2d2f76645c7df1
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 6%

---


# Réseau Internet direct (câblé/sans fil) {#direct-internet-access}

Le réseau Internet direct contient un point d&#39;accès à Internet pour atteindre les AEM cloud services auxquels les AEM Screens doivent se connecter.

Les ports standard pour la communication AEM Screens sont les suivants :
* `http (TCP Port 80)`

   <br>Ou,</br>

* `ssl-secured https (TCP Port 443)`

Les ports peuvent varier en fonction de la configuration de votre configuration AEM dédiée. Dans cette configuration, tous les périphériques sont directement connectés à votre routeur Internet, comme le montre la figure ci-dessous.

![](/help/assets/direct-access-2.png)

La configuration inclut également un accès Internet par tout Prestataire Internet (FAI) et sa ligne Internet. La plupart des FAI fournissent un routeur Internet couvrant le modem Internet, le commutateur réseau, le point d’accès WIFI, le pare-feu et d’autres fonctionnalités réseau (selon le fabricant et le modèle).

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


## Configuration d’un réseau d’accès direct {#requirements-direct}

Le réseau Internet direct est logiquement séparé en deux blocs :

* Réseau étendu

* Réseau local

### Réseau étendu {#wan-connection}

Les performances de la connexion Internet en plus de l&#39;accessibilité du réseau sont de fournir une bande passante suffisante pour utiliser le AEM Screens.

*Suffisant* dépend du nombre d&#39;écrans AEM connectés et de l&#39;utilisation d&#39;autres consommateurs dans le réseau, tels que les smartphones, tablettes, caissiers, ordinateurs ou réseaux WIFI invités.

>[!NOTE]
>Tous les périphériques mentionnés ci-dessus ont un accès simultané à la connexion Internet et la bande passante diminue de façon linéaire lorsque vous ajoutez plus de consommateurs ou d&#39;ordinateurs au réseau.

### Réseau local {#lan-connection}

Les performances du réseau local (LAN), en plus de l&#39;accessibilité du réseau, fournissent une bande passante suffisante pour exploiter le AEM Screens.

Le réseau LAN correspond généralement à un réseau de 100 Mbit/s, de sorte qu&#39;il y ait suffisamment de bande passante pour connecter de nombreux périphériques avec de bonnes performances au système.
In case that a WIFI solution is envisaged to connect AEM Screens to the Internet Link it is recommended to use modern WIFI standards like `IEEE 802.11g` as a minimum. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Toute *nouvelle* norme telle que est de meilleure qualité.`802.11h-n`

>[!NOTE]
>Si un répéteur WIFI est requis, il est fortement recommandé d&#39;avoir un point d&#39;accès WIFI de maillage tel que Google Nest Mesh WIFI ou similaire. D&#39;autres technologies qui répètent le Wi-Fi finissent par provoquer une perte massive de bande passante dans l&#39;ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre localement tous les fichiers multimédias nécessaires, tels que les images et les vidéos. Le trafic réseau majeur survient lorsqu’un nouveau contenu doit être affiché sur un affichage spécifique.

Pour les opérations normales, par exemple, une liste de lecture définie qui se met à jour fréquemment au cours de la journée - offre une opération indépendante de la proximité du réseau, une fois que tous les fichiers ont été enregistrés sur le lecteur.

Dans le cas de scénarios où il y a davantage d&#39;interactions avec des capteurs ou des déclencheurs et du contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d&#39;écran immédiate afin d&#39;assurer une meilleure expérience client possible.

Le tableau suivant présente un aperçu des données clés de connectivité réseau.

>[!NOTE]
>Ces informations vous permettent de vue la consommation de chaque périphérique du réseau qui demande et télécharge une source Internet. Chacune de ces requêtes additionne et étend le temps de téléchargement.

![](/help/assets/download-times-direct.png)

