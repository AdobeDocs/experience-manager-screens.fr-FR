---
title: Durée de lecture de l’image en bloc au niveau du canal
seo-title: Durée de lecture de l’image en bloc au niveau du canal
description: Cette page décrit comment modifier la durée de lecture d’un composant d’image spécifique.
seo-description: Cette page décrit comment modifier la durée de lecture d’un composant d’image spécifique.
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Durée de lecture de l’image en bloc au niveau du canal{#channel-level-bulk-image-playback-duration}

## Présentation {#overview}

Une fois que vous créez un canal de séquence et y ajoutez des images, toutes les images supposent par défaut la durée de lecture définie dans la configuration au niveau du canal. Toute image individuelle peut toujours remplacer la valeur par défaut et avoir une durée de lecture différente. Pour ce faire, modifiez la durée de lecture du composant d’image spécifique.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, assurez-vous d’avoir configuré un projet comme prérequis pour commencer à implémenter cette fonctionnalité. Par exemple :

1. Création d’un projet AEM Screens (dans cet exemple, **ChannelLevelPlayback**)

1. Création d’un canal de séquence en tant que **canal de lecture** sous le dossier **Canaux**

1. Ajouter du contenu à **PlaybackChannel**

## Modification de la durée de lecture de l’image au niveau du canal Affectation {#editing-channel-level-image-playback-duration-assignment}

La section ci-dessous explique comment modifier la durée de lecture du contenu dans un canal AEM Screens.

### Mise à jour de la durée de lecture des images d’un canal {#updating-the-playback-duration-for-images-in-a-channel}

Suivez les étapes ci-dessous pour savoir comment mettre à jour la durée de lecture de l’image au niveau du canal Affectation :

1. Accédez au canal de séquence **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Ajoutez plusieurs images dans l’éditeur de canaux, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Sélectionnez toutes les images du canal, puis cliquez sur l’icône en forme de clé à molette en haut à gauche (comme illustré dans la figure ci-dessous) pour ouvrir la boîte de dialogue Configurer au niveau du canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **La boîte de dialogue Page** s’ouvre.

   >[!NOTE]
   >
   >Par défaut, les images d’un canal sont définies sur une durée de lecture de 8 secondes.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Modifiez la **durée** de 8 000 (ms) à 3 000 (ms), c’est-à-dire 3 secondes. Cochez la case en haut à droite de la boîte de dialogue **Page** pour enregistrer vos modifications.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Affichage du résultat {#viewing-the-result}

Une fois que vous avez mis à jour la durée de lecture du canal (dans cet exemple, les trois images), vous constaterez que les images sont lues pendant 3 secondes au lieu de 8 secondes (valeur par défaut).

![channel_preview](assets/channel_preview.gif)

