---
title: Application de transitions
description: Découvrez comment appliquer des transitions à vos projets AEM Screens.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
TQID: https://experienceleague.adobe.com/t4JTCyQhe7kb5v-dveK4Np9dAAGLBeatCN2kyTM6ELc
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: e8696a6a-4caa-4059-b0b2-3fbb66f5ab7eid: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 276
ht-degree: 100%

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
>Créez un projet AEM Screens **TestProject** avec un canal **TestTransition**. Configurez également un emplacement et un affichage pour visualiser la sortie.

1. Accédez au canal **TestTransition** et cliquez sur **Modifier** dans la barre d’actions.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >Le canal **TestTransition** comporte déjà quelques ressources (images et vidéos). Par exemple, le canal **TestTransition** comprend trois images et deux vidéos, comme illustré ci-dessous :

   ![image2](assets/transitions2.png)


1. Faites glisser et déposez le composant **Transition** dans votre éditeur.

   >[!CAUTION]
   >
   >Avant d’ajouter la transition à vos ressources dans votre canal, assurez-vous que vous n’ajoutez pas de transition avant la première ressource dans le canal séquentiel. Le premier élément de votre canal doit être une ressource et non une transition.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >Par défaut, les propriétés du composant de transition, telles que **Type**, sont définies sur **Fondu** et la **Durée** sur *1 600 millisecondes*. En outre, il n’est pas conseillé de définir une durée de transition plus longue que la ressource à laquelle cette durée s’applique.

1. De plus, si vous ajoutez un composant **Séquence incorporée** (qui inclut un canal de séquence) à cet éditeur de canal, vous pouvez ajouter un composant de transition à la fin. Cela garantit que le contenu est lu dans l’ordre correct, comme dans l’image suivante :

   ![image3](assets/transitions5.png)
