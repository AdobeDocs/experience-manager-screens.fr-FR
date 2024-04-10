---
title: Durée de lecture des images au niveau du projet
description: Découvrez comment définir la durée de lecture des images au niveau du projet.
contentOwner: jsyal
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 36%

---


# Durée de lecture des images au niveau du projet {#project-level-image-playback}

## Vue d’ensemble {#overview}

Cette fonctionnalité vous permet de définir la durée de lecture des images au niveau du projet. Par défaut, toutes les images héritent de cette durée de lecture. Si aucune durée n’est définie au niveau du projet, la lecture par défaut de 8 secondes se poursuit.

### Conditions préalables {#prerequisites}

Avant d’utiliser cette fonctionnalité, configurez un projet comme condition préalable pour commencer à mettre en oeuvre cette fonctionnalité. par exemple,

1. Créez un projet AEM Screens (dans cet exemple, **ProjectLevelPlayback**).
1. Créez un canal de séquence sous la forme **PlayBackChannel** under **Canaux** dossier.
1. Ajouter du contenu à **PlayBackChannel**.

   ![ressources](assets/image_playback1.png)

   Par exemple, l’image ci-dessous présente les images ajoutées à l’éditeur **PlayBackChannel** :

   ![ressources](assets/image_playback2.png)

## Modification de l’attribution d’une durée de lecture des images d’un projet {#editing-project-level-image-playback-duration-assignment}

La section ci-après explique comment modifier la durée de lecture d’un contenu d’un projet AEM Screens.

### Mise à jour de la durée de lecture des images au niveau d’un projet {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Si vous souhaitez mettre à jour une image ou une durée de lecture au niveau du canal, reportez-vous à la section [Durée de lecture des images au niveau du canal](channel-level-image-playback.md).

Suivez les étapes ci-dessous pour savoir comment mettre à jour la durée de lecture des images d’un projet :

1. Accédez au projet **ProjectLevelPlayback** et cliquez sur **Propriétés** dans la barre d’actions.
   ![ressources](assets/image_playback3.png)

1. Sélectionnez toutes les images du canal, puis cliquez sur l’icône en forme de clé à molette en haut à gauche (comme illustré dans la figure ci-dessous) afin d’ouvrir la boîte de dialogue de configuration de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. La variable **Page** s’ouvre.

   >[!NOTE]
   >
   >Par défaut, les images d’un canal sont définies sur une durée de lecture de 8 secondes et les vidéos sont lues selon leur durée par défaut.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Modifiez la variable **Durée** de 8 000 (millisecondes) à 3 000 (millisecondes), c’est-à-dire 3 secondes. Cochez la case en haut à droite du **Page** pour enregistrer vos modifications.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Affichage du résultat {#viewing-the-result}

Après avoir mis à jour la durée de lecture du canal (dans cet exemple, les trois images), notez que les images sont désormais lues pendant 3 secondes au lieu de 8 secondes (valeur par défaut).

![channel_preview](assets/channel_preview.gif)

