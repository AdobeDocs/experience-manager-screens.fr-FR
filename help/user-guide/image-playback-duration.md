---
title: Durée de lecture des images
description: Découvrez la durée de lecture des images dans AEM Screens.
contentOwner: jsyal
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 53%

---


# Durée de lecture des images {#image-playback-duration}

## Vue d’ensemble {#overview}

Après avoir créé un canal de séquence et y avoir ajouté des images, toutes les images supposent par défaut la durée de lecture définie dans la configuration du canal. Chaque image peut toujours remplacer la valeur par défaut et présenter une autre durée de lecture. Pour ce faire, modifiez la durée de lecture du composant d’image concerné.

### Prérequis {#prerequisites}

Avant de mettre en oeuvre cette fonctionnalité, assurez-vous d’avoir configuré un projet comme condition préalable pour commencer à l’implémentation. Par exemple :

1. Créer un projet AEM Screens (en l’occurrence, **ChannelLevelPlayback**)
1. Créer un canal de séquence **PlaybackChannel** sous le dossier **Canaux**
1. Ajouter un contenu à **PlaybackChannel**

## Modification de l’attribution d’une durée de lecture des images d’un canal {#editing-channel-level-image-playback-duration-assignment}

La section suivante explique comment modifier la durée de lecture d’un contenu d’un canal AEM Screens.

### Mise à jour de la durée de lecture des images d’un canal {#updating-the-playback-duration-for-images-in-a-channel}

Suivez les étapes ci-dessous pour savoir comment mettre à jour l’attribution d’une durée de lecture des images d’un canal :

1. Accédez au canal de séquence **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Sélectionner **Modifier** dans la barre d’actions.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Ajoutez plusieurs images à l’éditeur de canal, comme l’illustre la figure ci-dessous.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Sélectionnez toutes les images du canal et cliquez sur l’icône en forme de clé à molette en haut à gauche (comme illustré dans la figure ci-dessous). La boîte de dialogue Configuration au niveau du canal s’ouvre.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **La boîte de dialogue Page** s’ouvre.

   >[!NOTE]
   >
   >Par défaut, les images d’un canal sont définies sur une durée de lecture de 8 secondes.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Modifiez la variable **Durée** de 8 000 (millisecondes) à 3 000 (millisecondes), c’est-à-dire 3 secondes. Cochez la case en haut à droite du **Page** pour enregistrer vos modifications.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Affichage du résultat {#viewing-the-result}

Lorsque vous avez mis à jour la durée de lecture du canal (dans cet exemple, les trois images), notez que les images sont désormais lues pendant 3 secondes au lieu de 8 secondes (valeur par défaut).

![channel_preview](assets/channel_preview.gif)

