---
title: Gestion des appareils
description: Découvrez l’attribution et la gestion des périphériques dans AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 64%

---

# Gestion des appareils {#managing-devices}

Cette page décrit la procédure d’attribution des appareils.

La console Périphériques vous permet d’accéder au gestionnaire de périphériques afin d’affecter votre périphérique à un affichage.

>[!CAUTION]
>
>Avant d’attribuer votre périphérique, vous devez l’enregistrer. Pour plus d’informations, reportez-vous à la section [Enregistrement des appareils](device-registration.md).

## Attribution des appareils {#device-assignment}

Suivez les étapes ci-dessous pour attribuer un appareil à un affichage :

1. Accédez au dossier Appareils de votre projet, par exemple :

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Sélectionnez votre dossier **Appareils** et appuyez ou cliquez ensuite sur **Gestionnaire d’appareils** dans la barre d’actions. Les appareils attribués et non attribués s’affichent.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Sélectionnez un appareil non attribué dans la liste et appuyez/cliquez sur **Attribuer l’appareil** dans la barre d’actions.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Sélectionnez l’affichage auquel vous souhaitez attribuer le périphérique dans la liste, puis appuyez/cliquez sur le bouton **Attribuer**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Appuyez/cliquez sur **Terminer** pour terminer la procédure d’attribution.


   Le tableau de bord des affichages montre l’appareil attribué dans le volet **APPAREILS**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Cliquez sur (**..**) dans le coin supérieur droit du **APPAREILS** pour ajouter une configuration de périphérique ou mettre à jour les périphériques.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Chaque fois que vous ajoutez un premier appareil à un nouveau projet Screens, un groupe d’utilisateurs est créé.
>Par exemple, si le nom du nœud de projet est *we-retail*, le nom du groupe d’utilisateurs est *screens-we-retail-devices*.
>Ce groupe est ajouté en tant que membre du groupe **Contributeurs** , comme illustré dans la figure ci-dessous :

![chlimage_1-39](assets/chlimage_1-39.png)

### Étapes suivantes {#the-next-steps}

Une fois que vous êtes familiarisé avec la procédure d’attribution d’un canal à un affichage, consultez les ressources suivantes :

* [Contrôle et dépannage](monitoring-screens.md)
