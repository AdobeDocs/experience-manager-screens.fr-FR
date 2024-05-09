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
source-git-commit: 8a914d4b0237c327b7954c936c84a2c1aa719603
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 70%

---

# Durée de lecture d’images en bloc au niveau du canal {#channel-level-bulk-image-playback-duration}

## Vue d’ensemble {#overview}

Lorsque vous avez créé un canal de séquence et que vous y avez ajouté des images, toutes les images supposent par défaut la durée de lecture définie dans la configuration au niveau du canal. Toute image individuelle peut toujours remplacer la valeur par défaut et avoir une durée de lecture différente. Pour ce faire, modifiez la durée de lecture du composant d’image spécifique.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, veillez à configurer un projet comme condition préalable du lancement de sa mise en œuvre. Par exemple :

1. Créer un projet AEM Screens, **ChannelLevelPlayback**.

1. Créez un canal de séquence sous la forme **PlaybackChannel** sous le **Canaux** dossier.

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

1. Cliquez sur toutes les images du canal, puis sur l’icône en forme de clé à molette en haut à gauche (comme illustré dans la figure ci-dessous) pour ouvrir la boîte de dialogue Configuration de canal .

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. La boîte de dialogue **Page** s’ouvre.

   >[!NOTE]
   >Par défaut, les images d’un canal sont définies sur une durée de lecture de 8 secondes.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Remplacez la **durée** 8 000 (millisecondes) par 3 000 (millisecondes), c’est-à-dire 3 secondes. Cochez la case en haut à droite de la boîte de dialogue **Page** pour enregistrer vos modifications.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Afficher le résultat {#viewing-the-result}

Après avoir mis à jour la durée de lecture du canal (dans cet exemple, les trois images), notez que les images sont désormais lues pendant 3 secondes au lieu de 8 secondes (valeur par défaut).

![channel_preview](assets/channel_preview.gif)
