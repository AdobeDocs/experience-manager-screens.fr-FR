---
title: Déclencheurs de données
description: Découvrez les déclencheurs de données dans AEM Screens.
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: ht
source-wordcount: '261'
ht-degree: 100%

---

# Dynamic Creative Optimizations {#dynamic-creative}

>[!NOTE]
>
>Cette activité est généralement réalisée par la personne chargée de l’implémentation d’AEM.

La technologie DCO (**Dynamic Creative Optimization**) permet de créer des expériences de signalétique numérique qui tiennent compte des conditions particulières d’un emplacement donné, à un moment particulier et pour un utilisateur ou une utilisatrice spécifique.

Cette utilisation est également appelée aplatissement du contenu côté client.

Le raisonnement consiste à s’assurer que chaque appareil ou point d’entrée du lecteur peut utiliser des jeux de données pour déterminer le meilleur contenu à lire automatiquement en fonction de différents facteurs.

Cette fonctionnalité élimine la nécessité d’une intervention humaine constante lors de la création de contenu. Cela permet également de réduire le coût total de possession pour l’exploitation du réseau et de rendre les expériences numériques plus pertinentes, plus contextuelles et plus efficaces.

Voici quelques exemples :

* Utilisation du niveau de stock actuel des produits présentés
* Température extérieure ou conditions météorologiques
* Diffusion d’une campagne publicitaire dans les médias locaux
* Trafic web et même événements locaux, comme lorsqu’un client choisit un produit pour l’examiner

Tous ces exemples, et bien d’autres encore, peuvent être utilisés pour fournir un niveau de contexte et de personnalisation plus élevé.

L’adoption d’une stratégie de marchandisage visuel incluant la technologie DCO peut entraîner une augmentation sensible de la consultation du réseau.

Il existe deux principaux types de déclencheurs de données :

* **Déclencheurs de données locaux** : ces déclencheurs de données se situent au niveau de l’appareil. Par exemple, si vous touchez l’écran, un capteur est activé, ce qui déclenche un commutateur de canal ou de ressource de données local.
* **Déclencheurs de données distants** : cela suppose que les données déclenchent un commutateur de canal ou de ressource sur la base des valeurs renvoyées par une API de service web.
