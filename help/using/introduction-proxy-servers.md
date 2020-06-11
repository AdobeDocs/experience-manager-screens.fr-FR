---
title: Comprendre les serveurs proxy
seo-title: Comprendre les serveurs proxy
description: La page décrit les serveurs proxy.
seo-description: La page décrit les serveurs proxy.
translation-type: tm+mt
source-git-commit: e8161ece44fcc945b66713b3797935a505675104
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Présentation des configurations réseau standard {#intro-standard-networks}

Une configuration réseau peut avoir différentes structures. Cette section présente un aperçu des structures réseau déployées dans un environnement.

## Proxy Servers {#proxy-servers}

Un serveur proxy est un ordinateur dédié ou un système logiciel s&#39;exécutant sur un ordinateur qui agit comme intermédiaire entre un périphérique de point de terminaison, tel qu&#39;un ordinateur, et un autre serveur à partir duquel un utilisateur ou un client demande un service. Le serveur proxy peut exister sur la même machine qu’un serveur de pare-feu ou sur un serveur distinct, qui transfère les requêtes par le biais du pare-feu.

L&#39;avantage d&#39;un serveur proxy est que son cache peut servir tous les utilisateurs. Si un ou plusieurs sites Internet sont fréquemment demandés, ils sont susceptibles d’être dans le cache du proxy, ce qui améliorera le temps de réponse de l’utilisateur. Un proxy peut également enregistrer ses interactions, ce qui peut s’avérer utile pour le dépannage.

## Présentation des configurations réseau {#network-setups}

Pour mettre en oeuvre une configuration réseau, vous devez vous référer aux scénarios suivants avec les avantages et les inconvénients. Il existe trois types principaux de configuration réseau :

1. Accès Internet
1. Configuration du réseau mobile
1. Réseaux d&#39;entreprise enfermés

