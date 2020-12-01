---
title: Gestion du trafic réseau
description: La page décrit les configurations de réseau standard et la gestion du trafic réseau.
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 100%

---


# Gestion du trafic réseau {#managing-network-traffic}

Une configuration réseau peut avoir différentes structures. Cette section décrit les configurations réseau les plus courantes et les approches généralisées appliquées au sein d’une organisation.

Ce guide présente les serveurs proxy mis en œuvre par diverses structures de réseaux configurées au sein de différentes organisations.

>[!NOTE]
>**Configuration requise pour le réseau AEM Screens**
>AEM Screens communique directement avec AEM as a Cloud Service. Il est donc nécessaire d’établir une connexion stable entre les deux nœuds. Les pare-feu sont absolument obligatoires pour l’accès à Internet à des fins commerciales. En tant que client, vous devez connaître les ports de communication qui doivent être ouverts dans ces pare-feu et d’autres composants de réseau liés à la sécurité informatique.

## Présentation des serveurs proxy {#proxy-servers}

Une connexion Internet repose sur l’utilisation d’un serveur proxy. Un serveur proxy est un ordinateur dédié ou un système logiciel s’exécutant sur un ordinateur qui agit comme intermédiaire entre un terminal de point d’entrée, tel qu’un ordinateur, et un autre serveur à partir duquel un utilisateur ou un client demande un service. Le serveur proxy peut exister sur la même machine qu’un serveur de pare-feu ou sur un serveur distinct qui transfère les demandes par le biais du pare-feu.

L’un des avantages du serveur proxy est que son cache peut servir tous les utilisateurs. Si un ou plusieurs sites Internet sont fréquemment demandés, ils sont susceptibles de se trouver dans le cache du proxy, ce qui contribue à réduire le temps de réponse pour l’utilisateur. Un proxy peut également consigner ses interactions, ce qui peut servir au dépannage.

Lorsqu’un serveur proxy reçoit une requête de ressource Internet (telle qu’une page web ou lors de la connexion à un éditeur AEM), il analyse son cache local contenant les URL appelées. S’il trouve la page, il la renvoie à l’utilisateur sans transférer la requête vers Internet. Si la page ne se trouve pas dans le cache, le serveur proxy agit en tant que client au nom de l’utilisateur et demande la page au serveur sur Internet. Lorsque le contenu est renvoyé, le serveur proxy le rattache à la requête d’origine et le transfère à l’utilisateur.

## Présentation des configurations réseau standard {#network-setups}

Pour mettre en œuvre une configuration réseau, vous devez vous référer aux scénarios suivants avec leurs avantages et les détails de leurs déploiements.

Ce guide met en évidence quatre types de configurations réseau au sein d’une organisation :

* **[Réseau Internet direct (câblé/sans fil)](/help/using/direct-internet-network.md)**
* **[Réseau mobile direct](/help/using/mobile-network.md)**
* **[Réseau mobile avec routeur de données mobile et composants réseau actifs](/help/using/mobile-network-router.md)**
* **[Réseau d’entreprise fermé (câblé/sans fil)](/help/using/enclosed-corporate-network.md)**

Le tableau suivant décrit les différents types de configurations réseau avec leurs avantages et inconvénients respectifs :

| Configuration du réseau | Avantages | Inconvénients |
|--- |--- |--- |
| **Réseau Internet direct (câblé/sans fil)** | Facile et simple à configurer<br>Bon choix pour les installations de taille moyenne ou supérieure<br>Le réseau dédié peut être encapsulé<br>Peu de points de défaillance<br>Relativement peu coûteux<br>Bonne évolutivité | Forfait de données Internet obligatoire |
| **Réseau mobile direct** | Facile à configurer<br>Bon choix pour les installations de taille moyenne ou supérieure<br>Bonne évolutivité<br>Screens encapsulé | Connexion Internet obligatoire |
| **Réseau mobile avec routeur de données mobile et composants réseau actifs** | Facile à configurer<br>Bon choix pour les installations de taille moyenne ou supérieure<br>Le réseau dédié peut être encapsulé<br>Peu de points de défaillance<br>Relativement peu coûteux<br>Bonne évolutivité | Forfait de données Internet obligatoire |
| **Réseau d’entreprise fermé (câblé/sans fil)** | Flexibilité et évolutivité élevées<br>Très sécurisé en raison de lignes de défense différentes<br>Réseaux encapsulés<br>Facile à surveiller et à maintenir<br>Fiabilité | Compliqué et onéreux<br>Recommandé pour les spécialistes des réseaux ou les intégrateurs de systèmes |
