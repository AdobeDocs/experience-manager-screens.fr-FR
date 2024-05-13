---
title: Gérer les appareils
description: Découvrez l’attribution et la gestion des appareils dans AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 64%

---

# Gérer les appareils {#managing-devices}

Cette page décrit l’attribution du périphérique.

La console Appareils vous permet d’accéder au gestionnaire d’appareils afin d’attribuer votre appareil à un affichage.

>[!CAUTION]
>
>Avant d’attribuer votre périphérique, enregistrez-le. Voir [Enregistrement de périphérique](device-registration.md).

## Attribution des appareils {#device-assignment}

Suivez les étapes ci-dessous pour attribuer un appareil à un affichage :

1. Accédez au dossier Appareils de votre projet, par exemple :

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Cliquez sur **Périphériques** et cliquez sur **Gestionnaire de périphériques** dans la barre d’actions. Les appareils attribués et non attribués s’affichent.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Cliquez sur un périphérique non attribué dans la liste, puis cliquez sur le bouton **Attribuer le périphérique** dans la barre d’actions.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Cliquez sur l’affichage auquel vous souhaitez attribuer le périphérique dans la liste, puis cliquez sur le bouton **Attribuer**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Cliquez sur le bouton **Terminer** pour terminer le processus d’affectation.


   Le tableau de bord des affichages montre l’appareil attribué dans le volet **APPAREILS**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Cliquez sur (**...**) en haut à droite du panneau **APPAREILS** pour ajouter une configuration d’appareil ou mettre à jour les appareils.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Chaque fois que vous ajoutez un premier appareil à un nouveau projet Screens, un groupe d’utilisateurs est créé.
>Par exemple, si le nom du nœud de projet est *we-retail*, le nom du groupe d’utilisateurs est *screens-we-retail-devices*.
>Ce groupe est ajouté en tant que membre au groupe **Contributeurs et contributrices**, comme illustré ci-dessous :

![chlimage_1-39](assets/chlimage_1-39.png)

### Étapes suivantes {#the-next-steps}

Une fois que vous êtes familiarisé avec l’attribution d’un canal à un affichage, voir[Surveiller et résoudre les problèmes](monitoring-screens.md).
