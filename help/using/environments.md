---
title: Environnements pour [!UICONTROL AEM Screens]
seo-title: Environnements pour [!UICONTROL AEM Screens]
description: Cette page décrit les environnements adaptés à un projet AEM Screens.
seo-description: Cette page présente les environnements adaptés à un projet AEM Screens.
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 100%

---


# Environnements {#environments}

Identifiez, au préalable, les environnements AEM gérés par le client et que ce dernier s’attend à ce que vous utilisiez, tant dans le cadre du *développement* que du *déploiement*.

>[!NOTE]
>
>Pour que les projets fonctionnent, AEM Screens a besoin de plusieurs packages. Tous les environnements doivent exécuter la même version d’Adobe Experience Manager.

Suivez les instructions ci-dessous afin de configurer l’environnement pour votre projet AEM Screens :

1. Exécutez les versions les plus récentes des packages suivants pour votre version d’Adobe Experience Manager :

   * **AEM Service Pack**
   * **Screens Feature Pack**
   * **AEM Cumulative Fix Pack**

1. Identifiez les packages de développement (les composants WCM Core, par exemple) ou les kits d’outils tiers (SAP Hybris, par exemple) qui sont éventuellement requis.

1. Installez les mêmes packages logiciels sur vos environnements de développement locaux. 

1. Demandez à votre client d’adopter la même configuration sur tous ses serveurs de contrôle de la qualité, de production et intermédiaires. Des configurations de serveur incohérentes entraîneront des problèmes lors des phases de déploiement et de test.
