---
title: Gestion du trafic réseau
description: La page décrit les configurations réseau standard et comment gérer le trafic réseau.
translation-type: tm+mt
source-git-commit: d27abdfd92336279bf2c6abe4d2ae38b6e9077bf
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 4%

---


# Gestion du trafic réseau {#managing-network-traffic}

Une configuration réseau peut avoir différentes structures. Cette section décrit les configurations de réseau les plus courantes et les approches généralisées suivies au sein d&#39;une organisation.

Ce guide présente les serveurs proxy, suivis des différentes structures réseau configurées au sein de différentes organisations.

>[!NOTE]
>
>**Configuration requise pour le réseau AEM Screens**
>
>Les AEM Screens communiquent directement avec AEM en tant que Cloud Service. Il est donc nécessaire d’établir une connexion stable entre les deux noeuds. Les pare-feu sont absolument obligatoires pour l&#39;accès à Internet commercial et, en tant que client, vous devez comprendre quels ports de communication doivent être ouverts dans ces pare-feu et d&#39;autres composants réseau liés à la sécurité informatique.

## Présentation des serveurs proxy {#proxy-servers}

Une connexion Internet repose sur l&#39;utilisation d&#39;un serveur proxy. Un serveur proxy est un ordinateur dédié ou un système logiciel s&#39;exécutant sur un ordinateur qui agit comme intermédiaire entre un périphérique de point de terminaison, tel qu&#39;un ordinateur, et un autre serveur à partir duquel un utilisateur ou un client demande un service. Le serveur proxy peut exister sur la même machine qu’un serveur de pare-feu ou sur un serveur distinct, qui transfère les requêtes par le biais du pare-feu.

L’un des avantages du serveur proxy est que son cache peut servir tous les utilisateurs. Si un ou plusieurs sites Internet sont fréquemment demandés, ils sont susceptibles d’être dans le cache du proxy, ce qui améliore encore le temps de réponse de l’utilisateur. Un proxy peut également consigner ses interactions, qui peuvent être utilisées pour le dépannage.

Lorsqu’un serveur proxy reçoit une demande de ressource Internet (telle qu’une page Web ou lors de la connexion à un éditeur AEM), il analyse son cache local d’URL précédemment appelées. S’il trouve la page, il la renvoie à l’utilisateur sans la transférer à Internet. Si la page ne se trouve pas dans le cache, le serveur proxy (agit en tant que client) au nom de l’utilisateur et demande la page au serveur sur Internet. Lorsque le contenu est renvoyé, le serveur proxy le rattache à la requête d’origine et le transfère à l’utilisateur.

## Understanding the Standard Network Setups {#network-setups}

Pour mettre en oeuvre une configuration réseau, vous devez vous référer aux scénarios suivants avec leurs points forts et leurs détails de déploiement.

Ce guide met en évidence quatre types de configurations réseau au sein d&#39;une organisation :

* **[Réseau Internet direct (câblé/sans fil)](/help/using/direct-internet-network.md)**
* **[Réseau mobile direct](/help/using/mobile-network.md)**
* **[Réseau mobile avec routeur de données mobile et composants réseau actifs](/help/using/mobile-network-router.md)**
* **[Réseau d&#39;entreprise fermé (câblé/sans fil)](/help/using/enclosed-corporate-network.md)**

Le tableau suivant décrit les différents types de configuration réseau avec des avantages et des inconvénients :

| Configuration réseau | Avantages | Inconvénients |
|--- |--- |--- |
| **Réseau Internet direct (câblé/sans fil)** | Facile et direct à<br>SetUpBon choix pour les<br>installations de taille moyenne ou supérieureLe réseau dédié peut être<br>capsuléPeu de points de<br>défaillanceRelativement<br>peu coûteuxBonne évolutivité | Plan de données Internet obligatoire |
| **Réseau mobile direct** | Facilité de<br>configurationBon choix pour les<br>installations de taille moyenne ou plus grandeBonne<br>évolutivitéÉcrans encapsulés | Connexion Internet obligatoire |
| **Réseau mobile avec routeur de données mobile et composants réseau actifs** | Facilité de<br>configurationBon choix pour les<br>installations de taille moyenne ou plus grandeLe réseau dédié peut être<br>capsuléPeu de points de<br>défaillanceRelativement<br>peu coûteuxBonne évolutivité | Plan de données Internet obligatoire |
| **Réseau d&#39;entreprise fermé (câblé/sans fil)** | Haute flexibilité et<br>évolutivitéTrès sécurisée en raison de lignes de<br>défense différentes<br>Réseaux encapsulésFacile à surveiller et à<br>gérerFiabilité | Compliqué et<br>onéreuxRecommandé pour les spécialistes du réseau ou les intégrateurs de systèmes |
