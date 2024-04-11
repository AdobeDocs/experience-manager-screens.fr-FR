---
title: Déclencheurs de données
description: Découvrez les déclencheurs de données dans AEM Screens.
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
source-git-commit: a8055c5f859e401f7b1da4f5d95f1268dee243ad
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 70%

---

# Optimisations dynamiques des créations {#dynamic-creative}

>[!NOTE]
>
>Cette activité est généralement réalisée par l’implémentateur d’AEM.

La technologie DCO (**Dynamic Creative Optimization**) permet de créer des expériences de signalétique digitale qui tiennent compte des conditions particulières d’un emplacement donné, à un moment particulier et pour un utilisateur spécifique.

On parle également d’aplatissement du contenu côté client.

Cela permet de s’assurer que chaque appareil ou point de terminaison du lecteur peut utiliser des jeux de données pour déterminer automatiquement le meilleur contenu à lire en fonction de différents facteurs.

Cela évite d’avoir besoin d’une intervention humaine constante lors de la création de contenu. Cela permet également de réduire le coût total de propriété pour l’exploitation du réseau et de rendre les expériences numériques plus pertinentes, plus contextuelles et plus efficaces.

Voici quelques exemples :

* Utilisation du niveau de stock actuel des produits présentés
* Température extérieure ou conditions météorologiques
* Diffusion d’une campagne publicitaire dans les médias locaux
* Trafic web et même événements locaux, comme lorsqu’un client choisit un produit pour l’examiner

Tous ces éléments, et bien d’autres encore, peuvent être utilisés pour fournir un niveau de contexte et de personnalisation plus élevé.

L’adoption d’une stratégie de marchandisage visuel incluant la technologie DCO peut entraîner une augmentation sensible de la consultation du réseau.

Il existe deux principaux types de déclencheurs de données :

* **Déclencheurs de données locaux** : ces déclencheurs de données se situent au niveau de l’appareil. Par exemple, si vous touchez l’écran, un capteur est activé, ce qui déclenche un commutateur de canal ou de ressource de données local.
* **Déclencheurs de données distants** : cela suppose que les données déclenchent un commutateur de canal ou de ressource sur la base des valeurs renvoyées par une API de service web.
