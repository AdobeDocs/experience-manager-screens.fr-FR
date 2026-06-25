---
title: Déclencheurs de données
description: Découvrez les déclencheurs de données dans AEM Screens.
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
TQID: https://experienceleague.adobe.com/oeJ7C6Rt8-Z9sFnEP1S1tn0VW4PuiKkXkeDYaz8Vd4s
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 85%

---

# Dynamic Creative Optimizations {#dynamic-creative}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

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
