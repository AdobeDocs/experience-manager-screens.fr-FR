---
title: Mise à jour de contenu en tant que service
description: Découvrez la mise à jour de contenu en tant que service.
contentOwner: Jyotika syal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
TQID: https://experienceleague.adobe.com/p-13F7oySwiZfXHItW8zTIJRWiab5dOKxx-iU99vE9w
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 340
ht-degree: 77%

---

# Mise à jour de contenu en tant que service {#content-update-as-a-service}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Cette section couvre les sujets suivants relatifs à la mise à jour de contenu en tant que service :

* **Présentation**
* **Utilisation de la mise à jour hors ligne en bloc**

<!--
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permission you can download it from Package Share. 
-->

## Vue d’ensemble {#overview}

La mise à jour hors ligne en masse vous permet de mettre à jour tous les canaux en masse. Cela évite d’avoir à naviguer vers un canal particulier pour en mettre à jour le contenu. Vous pouvez plutôt mettre à jour tout le contenu des canaux d’un projet spécifique en un seul instant.

Vous pouvez également planifier cette activité pour une période de trafic réseau plus faible.

>[!NOTE]
>
>La fonction Mise à jour hors ligne en bloc est optimisée de manière à ne mettre à jour que les canaux qui ont été modifiés.

## Utilisation de la mise à jour hors ligne en bloc {#using-bulk-offline-update}

Vous pouvez manuellement utiliser la mise à jour hors ligne en masse à partir de l’interface d’utilisation ou programmer la mise à jour en masse à partir des services OSGi.

### Utilisation de l’interface utilisateur d’AEM Screens {#using-aem-screens-user-interface}

Suivez les étapes ci-dessous pour utiliser la mise à jour hors ligne en bloc pour un projet AEM Screens :

1. Accédez à votre projet AEM Screens.
1. Cliquez sur le projet, puis sur **Mettre à jour le contenu hors ligne** dans la barre d’actions pour mettre manuellement à jour le contenu du canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuration de la console Web d’Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Suivez les étapes ci-dessous pour utiliser la mise à jour hors ligne en bloc pour un projet AEM Screens :

1. Configuration de la console Web d’Adobe Experience Manager.
1. Recherchez des services de mise à jour hors ligne en masse.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Ajoutez les propriétés suivantes :

   **Chemin du projet** - Indique le chemin de votre projet AEM Screens. Le chemin est habituellement `/content/screens/<Name of your project>`.

   *Par exemple*, `/content/screens/we-retail`. Vous pouvez trouver ce chemin dans l’URL en sélectionnant un projet sous AEM Screens (ne cliquez pas sur l’icône).

   >[!NOTE]
   >
   >Spécifiez le chemin du projet par rapport à votre canal.

   **Fréquence de planification** - Indique une heure, par exemple 17 :00 ou 17 :00 à laquelle ce service doit mettre à jour le contenu hors ligne.

1. Cliquez sur **Enregistrer** pour pouvoir enregistrer vos paramètres. Tout votre contenu est mis à jour à l’heure indiquée.

