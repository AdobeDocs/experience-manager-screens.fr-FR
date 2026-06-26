---
title: Durée de lecture d’images en bloc au niveau du canal
description: Découvrez comment modifier la durée de lecture d’un composant d’image spécifique dans AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 95aa761a-1449-4e18-8115-3b151036dc54
TQID: https://experienceleague.adobe.com/6Cq6n8lfTfRC685rE4jWmnAQDPLsDJ4ptNTNjt-qmHc
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
source-wordcount: 387
ht-degree: 88%

---

# Durée de lecture d’images en bloc au niveau du canal {#channel-level-bulk-image-playback-duration}

## Vue d’ensemble {#overview}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Lorsque vous avez créé un canal de séquence et que vous y avez ajouté des images, toutes les images supposent par défaut la durée de lecture définie dans la configuration au niveau du canal. Toute image individuelle peut toujours remplacer la valeur par défaut et avoir une durée de lecture différente. Pour ce faire, modifiez la durée de lecture du composant d’image spécifique.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, veillez à configurer un projet comme condition préalable du lancement de sa mise en œuvre. Par exemple :

1. Créer un projet AEM Screens, **ChannelLevelPlayback**.

1. Créez un canal de séquence **PlaybackChannel** dans le dossier **Canaux**.

1. Ajouter un contenu à **PlaybackChannel**.

## Modification de l’attribution d’une durée de lecture des images d’un canal {#editing-channel-level-image-playback-duration-assignment}

La section suivante explique comment vous pouvez modifier la durée de lecture d’un contenu d’un canal AEM Screens.

### Mise à jour de la durée de lecture des images d’un canal {#updating-the-playback-duration-for-images-in-a-channel}

Suivez les étapes ci-dessous pour savoir comment mettre à jour l’attribution d’une durée de lecture des images d’un canal :

1. Accédez au canal de séquence **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Ajoutez plusieurs images à l’éditeur de canal, comme l’illustre la figure ci-dessous.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Cliquez sur toutes les images du canal, puis sur l’icône en forme de clé à molette en haut à gauche (comme l’illustre la figure ci-dessous) pour pouvoir ouvrir la boîte de dialogue de configuration de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. La boîte de dialogue **Page** s’ouvre.

   >[!NOTE]
   >Par défaut, les images d’un canal sont définies sur une durée de lecture de 8 secondes.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Remplacez la **durée** 8 000 (millisecondes) par 3 000 (millisecondes), c’est-à-dire 3 secondes. Cochez la case en haut à droite de la boîte de dialogue **Page** pour enregistrer vos modifications.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Afficher le résultat {#viewing-the-result}

Après avoir mis à jour la durée de lecture du canal (en l’occurrence, les trois images), vous constatez que la durée de lecture de ces images n’est pas de 8 secondes (valeur par défaut), mais de 3 secondes.

![channel_preview](assets/channel_preview.gif)

