---
title: Application de transitions
seo-title: Application de transitions
description: Suivez cette page pour savoir comment appliquer des transitions à vos projets d’écrans.
seo-description: Suivez cette page pour savoir comment appliquer des transitions à vos projets d’écrans.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 02acf7ffc447c92efb75d756071d2cd5f4aaf104

---


# Application de transitions {#applying-transitions}

Cette section décrit comment un composant **Transition** vous permet d’ajouter une transition à votre projet d’écrans.


>[!CAUTION]
>
>Pour en savoir plus sur les propriétés du composant Transition, voir [Transitions.](adding-components-to-a-channel.md#transition)

## Ajout d’un composant de transition {#adding-transition}

Suivez les étapes ci-dessous pour ajouter un composant de transition à votre projet AEM Screens :

>[!NOTE]
>
>**Conditions préalables**
> Créez un projet AEM Screens **TestProject** avec un canal **TestTransition**. Configurez également un emplacement et un affichage pour afficher la sortie.

1. Accédez à Channel **TestTransition** et cliquez sur **Modifier** dans la barre d’actions.



   >[!NOTE]
   >
   >Le canal **TestTransition** comporte déjà peu de ressources (images et vidéos). Par exemple, le canal **TestTransition** comprend cinq images et une vidéo, comme illustré ci-dessous :



1. Faites glisser et déposez le composant **Transition** dans votre éditeur.

   > [!NOTE]
   >
   >Par défaut, le composant de transition est défini sur Type comme **Normal** avec **Durée** définie sur *600 ms*.


   >[!CAUTION]
   >
   >Avant d’ajouter la transition à vos ressources dans votre canal, assurez-vous que :
Vous n’ajoutez pas de transition avant le premier fichier dans le canal séquentiel. Le premier élément de votre canal doit être une ressource et non une transition.
