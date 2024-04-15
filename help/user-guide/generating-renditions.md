---
title: Rendus vidéo
description: Découvrez comment générer des rendus Full HD pour votre projet AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 20%

---

# Rendus vidéo {#video-renditions}

Vous pouvez générer des rendus Full HD manuels et automatiques. La section suivante décrit le processus à suivre pour ajouter des rendus à vos ressources.

## Génération automatique de rendus Full HD  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Si les rendus vidéo AEM Screens ne sont pas lus de manière optimale sur votre appareil, contactez le fournisseur du matériel pour connaître les spécifications de la vidéo. Cela permet d’obtenir les meilleures performances sur l’appareil et de créer ainsi votre propre profil vidéo personnalisé dans lequel vous fournissez les paramètres appropriés pour que FFMPEG génère votre rendu. Suivez ensuite les étapes ci-dessous pour ajouter votre profil vidéo personnalisé à la liste des profils.
>
>Voir aussi [Vidéos de dépannage](troubleshoot-videos.md) pour déboguer et résoudre les problèmes liés à la lecture de vidéos dans votre canal.

Suivez les étapes ci-dessous pour générer automatiquement des rendus Full HD :

1. Cliquez sur le lien Adobe Experience Manager (en haut à gauche) et sélectionnez l’icône en forme de marteau pour sélectionner **Workflow**.

   Sélectionner **Modèles**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Dans la gestion des modèles de workflow, sélectionnez la variable **Ressource de mise à jour de gestion des actifs numériques** model et select **Modifier** dans la barre d’actions.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Dans le **Ressource de mise à jour de gestion des actifs numériques** , double-cliquez sur le **Transcodage FFmpeg** étape .

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Sélectionnez la variable **Processus** .
1. Saisissez les profils Full HD dans la liste de **Arguments** comme suit :
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. Sélectionnez **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Sélectionner **Enregistrer** dans le coin supérieur gauche de la **Ressource de mise à jour de gestion des actifs numériques** écran.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Accédez à **Actifs** et téléchargez une nouvelle vidéo. Sélectionnez la vidéo et ouvrez le rail latéral Rendus . Notez les deux vidéos Full HD.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Ouvrez **Rendus** dans le rail latéral.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Notez deux nouveaux rendus Full HD.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Génération manuelle de rendus Full HD {#manually-generating-full-hd-renditions}

Suivez les étapes ci-dessous pour générer manuellement des rendus Full HD :

1. Cliquez sur le lien Adobe Experience Manager (en haut à gauche) et sélectionnez l’icône en forme de marteau afin de sélectionner les outils et de **Workflow**.

   Sélectionner **Modèles**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Dans la gestion des modèles de workflow, sélectionnez l’option **Ressources de mise à jour de Screens** et sélectionnez le modèle **Démarrer le processus** pour ouvrir le **Exécuter le workflow** de la boîte de dialogue

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Sélectionnez la vidéo de votre choix dans le **Payload** et sélectionnez **Exécuter**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Accédez à **Ressources**, accédez à votre ressource en descendant dans la hiérarchie, puis sélectionnez-la.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Ouvrez le **Rendus** rail latéral. Notez les nouveaux rendus Full HD.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
