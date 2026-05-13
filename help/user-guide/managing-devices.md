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
TQID: https://experienceleague.adobe.com/BtVUYTZ9GisSxK6-M-QsYRGdykFB51IchqI7CX-vsa8
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 242
ht-degree: 83%

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

   Cliquez sur (**...**) dans le coin supérieur droit du panneau **APPAREILS** pour ajouter la configuration de l’appareil ou mettre à jour les appareils.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Chaque fois que vous ajoutez un premier appareil à un nouveau projet Screens, un groupe d’utilisateurs est créé.
>Par exemple, si le nom du nœud de projet est *we-retail*, le nom du groupe d’utilisateurs est *screens-we-retail-devices*.
>Ce groupe est ajouté en tant que membre au groupe **Contributeurs et contributrices**, comme illustré ci-dessous :

![chlimage_1-39](assets/chlimage_1-39.png)

### Étapes suivantes {#the-next-steps}

Une fois que la procédure d’attribution d’un canal à un affichage n’a plus de secret pour vous, consultez [Surveiller et résoudre les problèmes](monitoring-screens.md).
