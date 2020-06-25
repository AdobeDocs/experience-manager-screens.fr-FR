---
title: Réseau d’entreprise fermé
description: Réseau d’entreprise fermé
translation-type: tm+mt
source-git-commit: 768c40545907ab473d61a56367940cfbbf8f2dc9
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 5%

---


# Réseau d’entreprise fermé (câblé/sans fil) {#enclosed-corporate-networks}

La configuration de réseau d&#39;entreprise intégrée s&#39;applique aux petites, grandes et grandes entreprises. Il peut être théoriquement plus complexe et la configuration logique est présentée dans la figure ci-dessous.

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


## Configuration de réseaux d&#39;entreprise fermés {#requirements-enclosed-networks}

La configuration réseau d&#39;entreprise enfermée peut être logiquement séparée en deux blocs :

* Réseau étendu (WAN)
* Réseau local interne (LAN).

### Réseau étendu {#wan-connection}

Les performances de la connexion Internet en plus de l&#39;accessibilité du réseau, est de fournir suffisamment de bande passante pour fonctionner en AEM Screens gentiment et en douceur.
*Une bande passante* suffisante dépend de la quantité d’écrans AEM connectés et de l’utilisation d’autres clients du réseau, tels que les smartphones, tablettes, caissiers, ordinateurs ou réseaux Wi-Fi invités.

>[!NOTE]
>Tous les périphériques ont un accès simultané à la connexion Internet et la bande passante diminue de façon linéaire lorsque vous ajoutez plus de consommateurs ou d&#39;ordinateurs au réseau.

### Réseau local {#lan-connection}

En plus de l&#39;accessibilité au réseau, les performances du réseau local (LAN) sont suffisantes pour permettre un bon fonctionnement du AEM Screens.

Le réseau LAN au sein des entreprises est généralement d&#39;au moins 1000 Mo/s par réseau, de sorte qu&#39;il y a suffisamment de bande passante pour connecter de nombreux périphériques avec de bonnes performances au système. Lors de l&#39;utilisation d&#39;autres composants réseau actifs, il est obligatoire que tous ces composants correspondent aux exigences de bande passante réseau.

Par exemple, les composants réseau doivent correspondre au moins à la norme 1 000 Mbit/s et à la bande passante fournie par la spécification d&#39;accès Internet/routeur.

### Autres caractéristiques des réseaux d’entreprise {#other-networks}

Les réseaux d&#39;entreprise ont un certain nombre de périphériques connectés, sont séparés en divers sous-réseaux et ont des connexions Internet redondantes ou multiplexées pour fournir des performances suffisantes pour plusieurs milliers d&#39;accès simultanés.
Ce schéma est simplifié et convient le plus souvent aux environnements disponibles pour le client.

In case that a Wi-Fi solution is envisaged to connect Screens to the Internet Link it is recommended to use modern Wi-Fi standards like `IEEE 802.11g` as a minimum. Cette norme prend en charge les connexions jusqu’à 54 Mbit/s. Toute *nouvelle* norme telle que est de meilleure qualité. `802.11h-n` Si un répéteur Wi-Fi est nécessaire, nous recommandons fortement les technologies de point d&#39;accès à Mesh Wi-Fi telles que Google Nest Mesh Wi-Fi ou d&#39;autres technologies similaires.
D&#39;autres technologies qui répètent le Wi-Fi finissent par provoquer une perte massive de bande passante dans l&#39;ensemble du réseau.

## Téléchargement de médias et de ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs de signalétique numérique. Il télécharge et enregistre localement tous les fichiers multimédias nécessaires, tels que les images et les vidéos. Le trafic réseau majeur survient lorsqu’un nouveau contenu doit être affiché sur un affichage spécifique.

Pour les opérations normales, par exemple, une liste de lecture définie qui se met à jour fréquemment au cours de la journée - offre une opération indépendante de la proximité du réseau, une fois que tous les fichiers ont été enregistrés sur le lecteur.

Dans le cas de scénarios où il y a davantage d&#39;interactions avec des capteurs ou des déclencheurs et du contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d&#39;écran immédiate afin d&#39;assurer une meilleure expérience client possible.

Le tableau suivant présente un aperçu des données clés de connectivité réseau.

>[!NOTE]
>Ces informations vous permettent de vue la consommation de chaque périphérique du réseau qui demande et télécharge une source Internet. Chacune de ces requêtes additionne et étend le temps de téléchargement.

![](/help/using/assets/enclosed-network-download.png)