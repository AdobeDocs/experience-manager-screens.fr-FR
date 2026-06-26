---
title: Suivi de l’assistance
description: Découvrez le suivi de l’assistance dans le cadre du guide des bonnes pratiques d’AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
TQID: https://experienceleague.adobe.com/uqtkwa1zcJ58tJOxWT0gWkOhAM-C-5zEdcFLjrHa1-Q
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 82%

---

# Suivi de l’assistance {#support-monitoring}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Cette section décrit les bonnes pratiques relatives à la gestion des anomalies de contenu et d’appareil dans un projet de signalétique digitale.

Le suivi de l’assistance comprend les activités suivantes :

* **Surveillance de l’appareil**
* **Surveillance du contenu**

## Surveillance du contenu {#content-monitoring}

La surveillance du contenu permet de résoudre les problèmes liés au contenu qui ne s’affiche pas correctement à l’écran :

1. Si un problème d’écran vide se produit, procédez comme suit :

   * Vérifiez la *prévisualisation* pour voir si le canal affiche un écran noir.
   * Sur votre ordinateur portable, enregistrez un *lecteur Chrome local* (en tant qu’extension) sur cet écran et regardez si un écran noir s’affiche.
   * Cliquez avec le bouton droit et examinez les *journaux correspondants*.

   Si le problème se produit uniquement sur l’appareil, mais pas sur le lecteur local, procédez comme suit :

   * Vérifiez le *type de média* (en cours d’utilisation) qui peut présenter des problèmes sur cet appareil et assurez-vous également que le contenu a bien été téléchargé en local (effacez le cache du canal dans l’interface d’administration).
   * Incluez les *journaux d’appareil* dans le dossier d’incident afin d’accélérer la procédure de dépannage.
   * *Collectez les journaux* de l’appareil à partir d’AEM.

## Surveillance de l’appareil {#device-monitoring}

Cette activité consiste à contrôler l’appareil physique si vous rencontrez un problème d’écran vide :

1. Si un problème d’écran vide se produit, procédez comme suit :

   * Vérifiez que le *dispositif d’affichage* est allumé.
   * Vérifiez que l’*ordinateur* est allumé et envoie un signal.
   * Cliquez avec le bouton droit et examinez les *journaux appropriés*.

