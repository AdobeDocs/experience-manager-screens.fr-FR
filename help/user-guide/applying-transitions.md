---
title: Application de transitions
seo-title: Application de transitions
description: Suivez cette page pour savoir comment appliquer des transitions à vos projets d’écrans.
seo-description: Suivez cette page pour savoir comment appliquer des transitions à vos projets d’écrans.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f6ee043e41e46690e057758266f9adc5323001d2

---


# Application de transitions {#applying-transitions}

Cette section décrit comment vous pouvez appliquer le composant **Transition** entre différents fichiers (images et vidéos) et des séquences intégrées dans un canal.


>[!CAUTION]
>
>Pour en savoir plus sur les propriétés du composant **Transition** , reportez-vous à [Transitions](adding-components-to-a-channel.md#transition).

## Ajout d’un composant de transition aux ressources dans un canal {#adding-transition}

Suivez les étapes ci-dessous pour ajouter un composant de transition à votre projet AEM Screens :

>[!NOTE]
>
>**Conditions préalables**
> Créez un projet AEM Screens **TestProject** avec un canal **TestTransition**. Configurez également un emplacement et un affichage pour afficher la sortie.

1. Accédez à Channel **TestTransition** et cliquez sur **Modifier** dans la barre d’actions.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >Le canal **TestTransition** comporte déjà peu de ressources (images et vidéos). Par exemple, le canal **TestTransition** comprend trois images et deux vidéos, comme illustré ci-dessous :

   ![image2](assets/transitions2.png)


1. Faites glisser et déposez le composant **Transition** dans votre éditeur.
   >[!CAUTION]
   >
   >Avant d’ajouter la transition à vos ressources dans votre canal, veillez à ne pas ajouter la transition avant le premier fichier dans le canal séquentiel. Le premier élément de votre canal doit être une ressource et non une transition.

   ![image3](assets/transitions3.png)

   > [!NOTE]
   >
   >Par défaut, les propriétés du composant de transition, tel que **Type** , sont définies sur **Normal** et la **Durée** sur *600 ms.*  En outre, il n’est pas conseillé de définir une durée de transition plus longue que la ressource à laquelle il est appliqué.

1. De plus, si vous ajoutez un composant Séquence **** incorporée (qui inclut un canal de séquence) à cet éditeur de canal, vous pouvez ajouter un composant de transition à la fin, de sorte que le contenu soit lu dans l’ordre, comme illustré dans la figure ci-dessous :

   ![image3](assets/transitions5.png)

## Ajout d’un composant de transition aux vidéos dans un canal {#adding-transition-videos}

Lors de l’application du composant de transition entre les vidéos, il est recommandé de définir le **type** sur **Fondu** et la durée **de la** séquence sur **1 600 ms.**

![image3](assets/transitions4.png)
