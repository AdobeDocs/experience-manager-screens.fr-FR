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
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: ht
source-wordcount: '367'
ht-degree: 100%

---

# Rendus vidéo {#video-renditions}

Vous pouvez générer des rendus Full HD manuels et automatiques. La section suivante décrit le processus à suivre pour ajouter des rendus à vos ressources.

## Génération automatique de rendus Full HD {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Si les rendus vidéo AEM Screens ne sont pas lus de manière optimale sur votre appareil, contactez le fournisseur du matériel pour connaître les spécifications de la vidéo. Cela vous permet de bénéficier de performances optimales sur l’appareil. Vous pouvez ainsi créer votre propre profil vidéo personnalisé dans lequel vous fournissez les paramètres appropriés pour FFMPEG afin de générer votre rendu. Suivez ensuite les étapes ci-dessous pour ajouter votre profil vidéo personnalisé à la liste des profils.
>
>Consultez également [Résolution des problèmes liés aux vidéos](troubleshoot-videos.md) pour déboguer et résoudre les problèmes liés à la lecture de vidéos dans votre canal.

Suivez les étapes ci-dessous pour générer manuellement des rendus Full HD :

1. Cliquez sur le lien Adobe Experience Manager (en haut à gauche), puis sur l’icône en forme de marteau pour sélectionner **Workflow**.

   Cliquez sur **Modèles**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Dans la gestion des modèles de workflow, cliquez sur le modèle **Ressources de mise à jour de gestion des actifs**, puis cliquez sur **Modifier** dans la barre d’actions.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Dans la fenêtre **Ressources de mise à jour de gestion des actifs**, double-cliquez sur l’étape **Transcodage FFmpeg**.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Cliquez sur l’onglet **Traitement**.
1. Saisissez les profils Full HD dans la liste des **Arguments** comme suit :
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. Cliquez sur **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Cliquez sur **Enregistrer** en haut à gauche de l’écran **Ressources de mise à jour de gestion des actifs**.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Accédez à **Actifs** et téléchargez une nouvelle vidéo. Cliquez sur la vidéo et ouvrez le rail latéral Rendus. Vous pouvez observer les deux vidéos Full HD.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Ouvrez **Rendus** dans le rail latéral.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Vous pouvez observer les deux nouveaux rendus Full HD.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Génération manuelle de rendus Full HD {#manually-generating-full-hd-renditions}

Suivez les étapes ci-dessous pour générer manuellement des rendus Full HD :

1. Cliquez sur le lien Adobe Experience Manager (en haut à gauche), puis sur l’icône en forme de marteau, et sélectionnez **Workflow**.

   Cliquez sur **Modèles**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Dans le gestionnaire de modèles de workflow, sélectionnez le modèle **Ressources de mise à jour de Screens**, puis cliquez sur le **workflow de démarrage** pour ouvrir la boîte de dialogue du **workflow d’exécution**.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Sélectionnez la vidéo souhaitée dans la **payload** et cliquez sur **Exécuter**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Accédez à **Actifs**, recherchez votre ressource en descendant dans la hiérarchie, puis cliquez dessus.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Ouvrez le rail latéral **Rendus**. Vous pouvez observer les nouveaux rendus Full HD.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
