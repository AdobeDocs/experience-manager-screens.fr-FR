---
title: Environnements pour [!UICONTROL AEM Screens]
description: En savoir plus sur les environnements d’un projet AEM Screens.
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 61%

---


# Environnements {#environments}

Déterminer à l’avance quels environnements AEM le client possède et compte que vous utiliserez, à la fois pour *development* et *déploiement*.

>[!NOTE]
>
>Le fonctionnement d’AEM Screens nécessite plusieurs packages pour les projets. Tous les environnements doivent exécuter la même version d’Adobe Experience Manager.

Suivez les instructions ci-dessous afin de configurer l’environnement pour votre projet AEM Screens :

1. Exécutez les versions les plus récentes des packages suivants pour votre version d’Adobe Experience Manager :

   * **AEM Service Pack**
   * **Screens Feature Pack**
   * **AEM Cumulative Fix Pack**

1. Identifiez les packages de développement (les composants WCM Core, par exemple) ou les kits d’outils tiers (SAP Hybris, par exemple) qui sont éventuellement requis.

1. Installez les mêmes packages logiciels sur votre environnement de développement local.

1. Demandez à votre client d’adopter la même configuration sur tous ses serveurs de contrôle de la qualité, de production et intermédiaires. Des configurations de serveur incohérentes créent des problèmes lors du déploiement et du test.
