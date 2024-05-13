---
title: Application de transitions
description: Découvrez comment appliquer des transitions à vos projets AEM Screens.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 45%

---

# Application de transitions {#applying-transitions}

Cette section décrit comment vous pouvez appliquer le composant **Transition** entre différentes ressources (images et vidéos) et des séquences incorporées dans un canal.

>[!CAUTION]
>
>Pour en savoir plus sur les propriétés du composant **Transition**, reportez-vous à [Transitions](adding-components-to-a-channel.md#transition).

## Ajout d’un composant Transition aux ressources dans un canal {#adding-transition}

Pour ajouter un composant de transition à votre projet AEM Screens, procédez comme suit :

>[!NOTE]
>
>**Prérequis**
>
>Créez un projet AEM Screens **TestProject** avec un canal **TestTransition**. Configurez également un emplacement et un affichage pour afficher la sortie.

1. Accédez au canal **TestTransition** et cliquez sur **Modifier** dans la barre d’actions.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >La variable **TestTransition** channel contient déjà quelques ressources (images et vidéos). Par exemple, le canal **TestTransition** comprend trois images et deux vidéos, comme illustré ci-dessous :

   ![image2](assets/transitions2.png)


1. Faites glisser et déposez le composant **Transition** dans votre éditeur.

   >[!CAUTION]
   >
   >Avant d’ajouter la transition à vos ressources dans votre canal, veillez à ne pas ajouter la transition avant la première ressource dans le canal séquentiel. Le premier élément de votre canal doit être une ressource et non une transition.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >Par défaut, les propriétés du composant de transition, telles que **Type** est défini sur **Fondu** et la variable **Durée** est défini sur *1 600 millisecondes*. En outre, il n’est pas conseillé de définir une durée de transition plus longue que la ressource à laquelle elle est appliquée.

1. En outre, si vous ajoutez une **Séquence incorporée** (qui inclut un canal de séquence) à cet éditeur de canal, vous pouvez ajouter un composant de transition à la fin. Cela permet de s’assurer que le contenu est lu dans le bon ordre, comme dans l’image suivante :

   ![image3](assets/transitions5.png)
