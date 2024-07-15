---
title: Créer et gérer une Live Copy
description: Découvrez comment créer et gérer des Live Copies de canaux dans AEM Screens.
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 4a4b3a83-2b02-42a0-86a7-fce6bbf47c7d
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 100%

---

# Créer et gérer une Live Copy {#creating-and-managing-a-live-copy}

Cette page décrit la création et la gestion des Live Copies des canaux.

Une ***Live Copy*** est une copie du contenu spécifique d’un site pour laquelle une relation directe avec la source d’origine est conservée. Ces relations en direct permettent à la Live Copy d’hériter des propriétés du contenu et de la page de la source.

Cette page décrit la création d’une Live Copy d’un canal, l’affichage des propriétés, la vérification du statut et la propagation des modifications d’un canal à sa Live Copy.


## Création d’une Live Copy {#creating-a-live-copy}

Procédez comme suit pour créer la Live Copy d’un canal dans le dossier de votre projet.

1. Cliquez sur le lien Adobe Experience Manager (en haut à gauche), puis sur **Screens**. Vous pouvez également utiliser le lien d’accès direct : `http://localhost:4502/screens.html/content/screens`.

1. Accédez au projet Screens, puis cliquez sur **Canaux**.
1. Cliquez sur **Créer**, puis sur **Live Copy** pour créer une Live Copy du canal.
1. Sélectionnez la destination, puis cliquez sur **Suivant**.
1. Sélectionnez l’emplacement où peut être placée la Live Copy.
1. Saisissez le **Titre** et le **Nom** dans la page **Créer une Live Copy**.

1. Cliquez sur **Ouvrir** pour afficher le contenu de la nouvelle Live Copy ou sur **Terminé** pour revenir à la page principale.

Vous pouvez également suivre les étapes ci-dessous pour obtenir une représentation visuelle afin de créer une Live Copy d’un canal.

L’exemple suivant illustre la création d’une Live Copy (***IdleLiveCopy***) pour le ***Canal inactif***, dont le dossier de destination est ***Canaux***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Affichage du contenu du canal de Live Copy {#viewing-content-of-the-live-copy-channel}

Une Live Copy est une copie d’un canal qui existe.

Pour afficher le contenu de votre Live Copy, procédez comme suit :

1. Accédez au projet Screens et cliquez sur l’emplacement où vous avez créé la Live Copy à l’origine, comme illustré dans la section ci-dessus. (Ici, l’emplacement qui a été sélectionné est le dossier **Canaux**.)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Cliquez sur **Modifier** dans la barre d’actions.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Lorsque vous affichez le contenu d’un canal de Live Copy, vous affichez un élément supplémentaire dans le menu sous la forme **Statut de la Live Copy**. Consultez la section ci-dessous pour plus de détails.

### Affichage des propriétés d’une Live Copy {#viewing-properties-of-a-live-copy}

Vous pouvez également afficher les propriétés de votre canal de Live Copy.

1. Accédez à votre canal de Live Copy et cliquez sur **Propriétés** dans la barre d’actions.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Cliquez sur l’onglet **Live Copy** pour consulter les détails de votre canal.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### État de Live Copy {#live-copy-status}

Le mode **Statut de la Live Copy**, comme illustré ci-dessous, permet d’afficher le statut des relations de tous les éléments du canal.

1. Cliquez sur **Modifier** et choisissez **État de Live Copy**. Vous pouvez également afficher l’association du contenu de votre canal avec le canal d’origine à partir duquel la Live Copy est générée.

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Cliquez sur **Statut de la Live Copy** pour afficher la page de prévisualisation.

   Toutes les ressources avec une bordure verte montrent que le contenu est hérité du canal d’origine.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Rupture de l’héritage {#breaking-the-inheritance}

Vous pouvez également annuler l’héritage de la Live Copy, de sorte que le contenu soit indépendant de la branche d’origine.

L’exemple suivant vous indique de sélectionner l’image en mode d’édition et de cliquer sur le symbole Annuler l’héritage en haut à droite.

![chlimage_1-24](assets/chlimage_1-24.png)

### Propagation des modifications au canal de Live Copy {#propagating-changes-to-the-live-copy-channel}

Si vous effectuez des modifications ou des mises à jour dans le canal d’origine, vous devez également les propager au canal de votre Live Copy.

Suivez les étapes ci-dessous pour vous assurer que vos modifications sont propagées du canal d’origine au canal de Live Copy :

1. Cliquez sur le canal d’origine (***Canal inactif***), puis sur **Modifier** dans la barre d’actions.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Apportez des modifications au contenu de ce canal. Supprimez une image de ce canal, par exemple.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Cliquez sur la Live Copy du canal (***IdleLiveCopy***), puis sur **Modifier** dans la barre d’actions. Notez que l’image que vous avez supprimée est toujours visible dans la Live Copy.

   Pour propager les modifications, synchronisez le canal.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Pour propager les modifications au canal de Live Copy, accédez au tableau de bord AEM et cliquez sur le canal de Live Copy, puis sur **Propriétés** dans la barre d’actions.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Cliquez sur l’onglet **Live Copy** puis sur **Synchroniser** dans la barre d’actions.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Cliquez sur **Synchronisation**, puis sur **Enregistrer et fermer** pour revenir au tableau de bord AEM.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Vous remarquerez que l’image est maintenant également supprimée du canal de Live Copy.
