---
title: Gestion des appareils
description: Découvrez l’attribution et la gestion des appareils dans AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 92%

---

# Gestion des appareils {#managing-devices}

Cette page décrit la procédure d’attribution des appareils.

La console Appareils vous permet d’accéder au gestionnaire de périphériques afin d’attribuer votre appareil à un affichage.

>[!CAUTION]
>
>Avant d’attribuer votre appareil, enregistrez-le. Voir [Enregistrement des appareils](device-registration.md).

## Attribution des appareils {#device-assignment}

Suivez les étapes ci-dessous pour attribuer un appareil à un affichage :

1. Accédez au dossier Appareils de votre projet, par exemple :

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Cliquez sur votre dossier **Appareils** et sur **Gestionnaire de périphériques** dans la barre d’actions. Les appareils attribués et non attribués s’affichent.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Cliquez sur un appareil non affecté dans la liste, puis, dans la barre d’actions, cliquez sur **Attribuer un appareil**.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Cliquez sur l’affichage auquel vous voulez attribuer l’appareil dans la liste, puis sur le bouton **Attribuer**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Cliquez sur **Terminer** pour terminer le processus d’attribution.


   Le tableau de bord des affichages montre l’appareil attribué dans le volet **APPAREILS**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Cliquez sur (**...**) en haut à droite du panneau **APPAREILS** pour ajouter une configuration d’appareil ou mettre à jour les appareils.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Chaque fois que vous ajoutez un premier appareil à un nouveau projet Screens, un groupe d’utilisateurs est créé.
>&#x200B;>Par exemple, si le nom du nœud de projet est *we-retail*, le nom du groupe d’utilisateurs est *screens-we-retail-devices*.
>&#x200B;>Ce groupe est ajouté en tant que membre au groupe **Contributeurs et contributrices**, comme illustré ci-dessous :

![chlimage_1-39](assets/chlimage_1-39.png)

### Étapes suivantes {#the-next-steps}

Une fois que la procédure d’attribution d’un canal à un affichage n’a plus de secret pour vous, consultez [Surveiller et résoudre les problèmes](monitoring-screens.md).
