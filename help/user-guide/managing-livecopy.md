---
title: Création et gestion d’une Live Copy
description: Découvrez comment créer et gérer des Live Copies de canaux dans AEM Screens.
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 4a4b3a83-2b02-42a0-86a7-fce6bbf47c7d
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 29%

---

# Création et gestion d’une Live Copy {#creating-and-managing-a-live-copy}

Cette page décrit la création et la gestion des Live Copies des canaux.

Une ***Live Copy*** est une copie du contenu spécifique d’un site pour laquelle une relation directe avec la source d’origine est conservée. Ces relations en direct permettent à la Live Copy d’hériter des propriétés du contenu et de la page de la source.

Cette page décrit la création d’une Live Copy d’un canal, l’affichage des propriétés, la vérification de l’état et la propagation des modifications d’un canal à sa Live Copy.


## Création d’une Live Copy {#creating-a-live-copy}

Procédez comme suit pour créer la Live Copy d’un canal dans le dossier de votre projet.

1. Sélectionnez le lien Adobe Experience Manager (en haut à gauche), puis **Screens**. Vous pouvez également utiliser le lien d’accès direct : `http://localhost:4502/screens.html/content/screens`.

1. Accédez au projet Screens, puis cliquez sur **Canaux**.
1. Cliquez sur **Créer** et sélectionnez **Live Copy** pour créer une Live Copy du canal.
1. Sélectionnez la destination et cliquez sur **Suivant**.
1. Sélectionnez l’emplacement où se trouve la Live Copy.
1. Saisissez le **Titre** et **Nom** dans le **Créer une Live Copy** page.

1. Cliquez sur **Ouvrir** pour afficher le contenu d’une nouvelle Live Copy ou **Terminé** pour revenir à la page principale.

Vous pouvez également suivre les étapes ci-dessous pour obtenir une représentation visuelle afin de créer une Live Copy d’un canal.

L’exemple suivant illustre la création d’une Live Copy (***IdleLiveCopy***) pour le ***Canal inactif***, dont le dossier de destination est ***Canaux***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Affichage du contenu du canal de Live Copy {#viewing-content-of-the-live-copy-channel}

Une Live Copy est une copie d’un canal qui existe.

Pour afficher le contenu de votre Live Copy, procédez comme suit :

1. Accédez au projet Screens et cliquez sur l’emplacement où vous avez créé la Live Copy à l’origine, comme illustré dans la section ci-dessus. (Ici, l’emplacement qui a été sélectionné est le dossier **Canaux**)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Cliquez sur **Modifier** dans la barre d’actions.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Lorsque vous affichez le contenu d’un canal de Live Copy, vous affichez un élément supplémentaire dans le menu sous la forme **État de Live Copy**. Pour plus d’informations, consultez la section ci-dessous.

### Affichage des propriétés d’une Live Copy {#viewing-properties-of-a-live-copy}

Vous pouvez également afficher les propriétés de votre canal de Live Copy.

1. Accédez à votre canal de Live Copy et cliquez sur **Propriétés** dans la barre d’actions.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Sélectionnez la variable **Live Copy** pour afficher les détails de votre canal.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### État de Live Copy {#live-copy-status}

Le mode **État de Live Copy**, comme illustré dans la figure ci-dessous, vous permet d’afficher l’état des relations de toutes les ressources du canal.

1. Cliquez sur **Modifier** afin que vous puissiez choisir la variable **État de Live Copy** et afficher l’association du contenu de votre canal avec le canal d’origine (à partir duquel la Live Copy est générée).

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Sélectionner **État de Live Copy** pour afficher la page d’aperçu.

   Toutes les ressources avec une bordure verte montrent que le contenu est hérité du canal d’origine.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Rupture de l’héritage {#breaking-the-inheritance}

Vous pouvez également annuler l’héritage de la Live Copy, de sorte que le contenu soit indépendant de la branche d’origine.

L’exemple suivant montre que vous sélectionnez l’image en mode d’édition et cliquez sur le symbole Annuler l’héritage en haut à droite.

![chlimage_1-24](assets/chlimage_1-24.png)

### Propagation des modifications au canal de Live Copy {#propagating-changes-to-the-live-copy-channel}

Si vous apportez des modifications ou des mises à jour au canal d’origine, propagez également ces modifications à votre canal Live Copy.

Suivez les étapes ci-dessous pour vous assurer que vos modifications sont propagées du canal d’origine au canal de Live Copy :

1. Sélectionnez le canal d’origine (***Canal inactif***) et sélectionnez **Modifier** dans la barre d’actions.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Apportez des modifications au contenu de ce canal. Supprimez une image de ce canal, par exemple.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Sélectionnez la Live Copy du canal (***IdleLiveCopy***) et sélectionnez **Modifier** dans la barre d’actions. Notez que l’image que vous avez supprimée est toujours visible dans la Live Copy.

   Pour propager les modifications, synchronisez le canal.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Pour propager les modifications au canal de Live Copy, accédez au tableau de bord AEM et sélectionnez le canal de Live Copy, puis cliquez sur **Propriétés** dans la barre d’actions.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Sélectionnez la variable **Live Copy** et sélectionnez **Synchroniser** dans la barre d’actions.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Sélectionner **Synchronisation**, puis sélectionnez **Enregistrer et fermer** pour revenir au tableau de bord AEM.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Notez que l’image est désormais également supprimée du canal de Live Copy.
