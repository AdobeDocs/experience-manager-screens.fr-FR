---
title: Créer un workflow de remplissage vidéo
description: En savoir plus sur la création d’un remplissage vidéo dans le workflow de vos ressources.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 95%

---

# Créer un workflow de remplissage vidéo {#creating-a-video-padding-workflow}

Cette section couvre les sujets suivants :

* **Présentation**
* **Prérequis**
* **Création d’un processus de remplissage vidéo**
   * **Création d’un processus**
   * **Utilisation du workflow dans le projet AEM Screens**

* **Validation de la sortie pour le processus**

## Vue d’ensemble {#overview}

Le cas d’utilisation suivant implique de placer une vidéo (par exemple : 1280 x 720) dans un canal où l’affichage est de 1920 x 1080 et où la vidéo doit être placée à 0x0 (en haut à gauche). La vidéo ne doit pas être étirée ni modifiée d’aucune manière et n’utilisez pas **la couverture** dans le composant vidéo.

La vidéo s’affiche sous la forme d’un objet du pixel 1 au pixel 1 280 en largeur et du pixel 1 au pixel 720 en hauteur. Le reste du canal est la couleur par défaut.

## Conditions préalables {#prerequisites}

Avant de créer un workflow pour la vidéo, veuillez remplir les conditions préalables suivantes :

1. Chargez une vidéo dans le dossier **Ressources** de votre instance AEM.
1. Créez un projet AEM Screens (par exemple, **TestVideoRendition**) et un canal nommé (**VideoRendering**), comme illustré dans la figure ci-dessous :

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Créer un workflow de remplissage vidéo {#creating-a-video-padding-workflow-1}

Pour créer un workflow de remplissage vidéo, vous devez créer un workflow pour votre vidéo, puis l’utiliser dans le canal de votre projet AEM Screens.

Suivez les étapes ci-dessous pour créer et utiliser le processus :

1. Création d’un processus
1. Utilisation du processus dans un projet AEM Screens

### Création d’un processus {#creating-a-workflow}

Suivez les étapes ci-dessous pour créer un processus pour votre vidéo :

1. Accédez à votre instance AEM.
1. Cliquez sur Outils dans le volet latéral.
1. Cliquez sur **Workflow** > **Modèles** pour créer un modèle.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Cliquez sur **Modèles** > **Créer** > **Créer un modèle**. Saisissez le **Titre** (tel que **VideoRendition**) et le **Nom** dans le champ **Ajouter un modèle de workflow**. Cliquez sur **Terminé** pour ajouter le modèle de processus.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Une fois le modèle de workflow créé, sélectionnez le modèle (**VideoRendition**), puis cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Faites glisser et déposez le composant **`Command Line`** dans votre workflow.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Sélectionnez le composant **`Command Line`** et ouvrez la boîte de dialogue Propriétés.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Cliquez sur l’onglet **Arguments**.
1. Dans la boîte de dialogue **Ligne de commande - Propriétés des étapes**, saisissez le format dans le champ **Types MIME** (sous la forme ***video/mp4***) et la commande sous la forme (***`/usr/local/Cellar/ffmpeg -i ${filename} -vf "pad=1920:height=1080:x=0:y=0:color=black" cq5dam.video.fullhd-hp.mp4`***). Cette commande démarre le workflow dans le champ **Commandes**.

   Veuillez consulter les détails sur les **types Mime** et les **Commandes** dans la note ci-dessous.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Cliquez sur le workflow (**VideoRenditions**).
1. Sélectionnez **Démarrer le workflow** dans la barre d’actions.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Dans la boîte de dialogue **Exécuter le workflow**, cliquez sur le chemin d’accès de votre ressource dans **Payload** (***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***), saisissez le **Titre** ***RunVideo***, puis cliquez sur **Exécuter**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Utilisation du processus dans un projet AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Pour utiliser le workflow dans votre projet AEM Screens, procédez comme suit :

1. Accédez à un projet AEM Screens (**TestVideoRendition** > **Canaux** > **VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Cliquez sur **Modifier** dans la barre d’actions. Faites glisser la vidéo que vous avez initialement téléchargée vers **Ressources**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Une fois que vous avez chargé la vidéo, cliquez sur **Prévisualiser** pour afficher la sortie.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validation de la sortie pour le processus {#validating-the-output-for-the-workflow}

Vous pouvez valider votre sortie en procédant comme suit :

* Vérifier la prévisualisation de la vidéo dans le canal
* Accédez au répertoire ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** dans CRXDE Lite, comme illustré dans la figure ci-dessous :

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
