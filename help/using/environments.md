---
title: Environnements pour [!UICONTROL AEM Screens]
description: En savoir plus sur les environnements d’un projet AEM Screens.
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 67%

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

1. Installez les mêmes packages logiciels dans votre environnement de développement local.

1. Demandez à votre client ou cliente d’adopter la même configuration sur tous ses serveurs de contrôle de la qualité, de production et intermédiaires. Des configurations de serveur incohérentes entraîneront des problèmes lors des phases de déploiement et de test.
