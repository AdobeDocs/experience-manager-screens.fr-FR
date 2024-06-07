---
title: Durée de lecture des images au niveau du projet
description: Découvrez comment définir la durée de lecture des images au niveau du projet.
contentOwner: jsyal
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: ht
source-wordcount: '329'
ht-degree: 100%

---


# Durée de lecture des images au niveau du projet {#project-level-image-playback}

## Vue d’ensemble {#overview}

Cette fonctionnalité vous permet de définir la durée de lecture des images au niveau du projet. Par défaut, toutes les images héritent de cette durée de lecture. Si aucune durée n’est définie au niveau du projet, la lecture par défaut de 8 secondes se poursuit.

### Conditions préalables {#prerequisites}

Avant de commencer à utiliser cette fonctionnalité, configurez un projet comme condition préalable du lancement de sa mise en œuvre. Par exemple :

1. Créer un projet AEM Screens (dans cet exemple, **ProjectLevelPlayback**).
1. Créez un canal de séquence **PlayBackChannel** dans le dossier **Canaux**.
1. Ajouter du contenu à **PlayBackChannel**.

   ![ressources](assets/image_playback1.png)

   Par exemple, l’image ci-dessous présente les images ajoutées à l’éditeur **PlayBackChannel** :

   ![ressources](assets/image_playback2.png)

## Modification de l’attribution d’une durée de lecture des images au niveau d’un projet {#editing-project-level-image-playback-duration-assignment}

La section ci-après explique comment modifier la durée de lecture d’un contenu d’un projet AEM Screens.

### Mise à jour de la durée de lecture des images au niveau d’un projet {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Si vous souhaitez mettre à jour une image ou une durée de lecture au niveau d’un canal, voir [Durée de lecture des images au niveau d’un canal](channel-level-image-playback.md).

Suivez les étapes ci-dessous pour savoir comment mettre à jour la durée de lecture des images d’un projet :

1. Accédez au projet **ProjectLevelPlayback** et cliquez sur **Propriétés** dans la barre d’actions.
   ![ressources](assets/image_playback3.png)

1. Cliquez sur toutes les images du canal, puis sur l’icône en forme de clé à molette en haut à gauche (comme l’illustre la figure ci-dessous) pour pouvoir ouvrir la boîte de dialogue de configuration de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. La boîte de dialogue **Page** s’ouvre.

   >[!NOTE]
   >
   >Par défaut, les images d’un canal sont définies sur une durée de lecture de 8 secondes et les vidéos sont lues selon leur durée par défaut.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Remplacez la **durée** 8 000 (millisecondes) par 3 000 (millisecondes), c’est-à-dire 3 secondes. Cochez la case en haut à droite de la boîte de dialogue **Page** pour que vos modifications soient enregistrées.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Afficher le résultat {#viewing-the-result}

Après avoir mis à jour la durée de lecture du canal (en l’occurrence, les trois images), vous constatez que la durée de lecture de ces images n’est pas de 8 secondes (valeur par défaut), mais de 3 secondes.

![channel_preview](assets/channel_preview.gif)

