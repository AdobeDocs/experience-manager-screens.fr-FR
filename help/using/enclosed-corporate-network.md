---
title: Réseau d’entreprise fermé
description: Réseau d’entreprise fermé
exl-id: b8c52e72-86da-4089-ba02-0c643862419f
TQID: https://experienceleague.adobe.com/3lU7N2840DVcH38SAQ-mthEwBcbUeQPl9Xea5Ms0L9k
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 660
ht-degree: 78%

---

# Réseau d’entreprise fermé (câblé/sans fil) {#enclosed-corporate-networks}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

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

Les performances de la connexion Internet, en plus de l’accessibilité du réseau, doivent fournir une bande passante suffisante pour permettre le bon fonctionnement des mises à jour de contenu AEM Screens.
*Bande passante suffisante* dépend du nombre d’AEM Screens connectées. Cela dépend également de l&#39;utilisation d&#39;autres consommateurs au sein du réseau, tels que les smartphones, les tablettes, les caissiers, les ordinateurs ou les réseaux Wi-Fi invités.

>[!NOTE]
>
>Tous les appareils disposent d’un accès simultané à la connexion internet et la bande passante diminue de façon linéaire lorsque vous ajoutez des appareils consommateurs ou des ordinateurs au réseau.

### Réseau local {#lan-connection}

Outre l’accessibilité du réseau, les performances du réseau local doivent offrir une bande passante suffisante pour garantir la fluidité des mises à jour du contenu AEM Screens.

Les réseaux locaux des entreprises atteignent généralement un débit de 1 000 Mbit/s, de sorte qu’il devrait y avoir suffisamment de bande passante pour connecter de nombreux appareils au système avec de bonnes performances. Lors de l’utilisation d’autres composants réseau actifs, il est obligatoire qu’ils correspondent tous aux exigences de bande passante du réseau.

Par exemple, les composants du réseau doivent correspondre au minimum à la norme standard de 100 Mbit/s et à la bande passante fournie par l’accès à internet ou les spécifications du routeur.

### Autres caractéristiques des réseaux d’entreprise {#other-networks}

Les réseaux d&#39;entreprise disposent de plusieurs appareils connectés, sont séparés en différents sous-réseaux et disposent de connexions Internet redondantes ou multiplexées pour fournir des performances suffisantes pour plusieurs milliers d&#39;accès simultanés.
Ce schéma est simplifié et s’adapte dans la plupart des cas aux environnements disponibles pour le client.

Si une solution Wi-Fi est envisagée pour connecter AEM Screens à Internet, il est recommandé d’utiliser au minimum les standards Wi-Fi modernes comme `IEEE 802.11g`. Cette norme prend en charge les connexions jusqu&#39;à 54 Mbit/s. Toutes les normes *plus récentes* comme `802.11h-n` sont de meilleure qualité. Si un répéteur Wi-Fi est requis, Adobe recommande les technologies de point d’accès Wi-Fi maillé telles que Google Nest Mesh Wi-Fi ou similaires.
D&#39;autres technologies de répétition Wi-Fi aboutissent à une perte massive de bande passante dans le réseau global.

## Télécharger des médias et des ressources {#download}

AEM Screens offre un grand avantage aux utilisateurs et utilisatrices de signalétique numérique. Il télécharge et enregistre en local tous les fichiers multimédias nécessaires, tels que les images et les vidéos. L’essentiel du trafic réseau a lieu lorsqu’un nouveau contenu doit être affiché sur un dispositif d’affichage spécifique.

Pour les opérations normales, par exemple, une playlist définie qui se met à jour fréquemment au cours de la journée, il est possible de fonctionner de manière presque indépendante du réseau, une fois tous les fichiers enregistrés sur le lecteur.

Pour les scénarios où il y a davantage d’interactions avec des capteurs ou d’autres déclencheurs et un contenu dynamique, une connexion réseau rapide et fiable est essentielle pour une réaction d’écran immédiate afin d’assurer une expérience client optimale.

Le tableau suivant présente une vue d’ensemble des données clés relatives à la connectivité réseau.

>[!NOTE]
>Vous voyez ainsi la consommation de chaque appareil du réseau qui demande une source internet et la télécharge. Chacune de ces demandes s’additionne et prolonge le temps de téléchargement.

![](/help/using/assets/enclosed-network-download.png)
