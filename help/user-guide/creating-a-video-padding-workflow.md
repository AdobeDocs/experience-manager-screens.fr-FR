---
title: Création d’un processus de remplissage vidéo
seo-title: Création d’un processus de remplissage vidéo
description: Consultez cette page pour en savoir plus sur la création d’un remplissage vidéo dans le processus pour vos ressources.
seo-description: Consultez cette page pour en savoir plus sur la création d’un remplissage vidéo dans le processus pour vos ressources.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 91%

---


# Création d’un processus de remplissage vidéo {#creating-a-video-padding-workflow}

Cette section couvre les sujets suivants :

* **Présentation**
* **Conditions préalables**
* **Création d’un processus de remplissage vidéo**
   * **Création d’un processus**
   * **Utilisation du processus dans le projet AEM Screens**

* **Validation de la sortie pour le processus**

## Présentation {#overview}

Le cas d’utilisation suivant implique de placer une vidéo (par exemple : 1280 x 720) dans un canal où l’affichage est de 1920 x 1080 et où la vidéo doit être placée à 0x0 (en haut à gauche). La vidéo ne doit pas être étirée ni modifiée d’aucune manière et n’utilisez pas **la couverture** dans le composant vidéo.

La vidéo s’affichera sous la forme d’un objet de pixel 1 à pixel 1280 sur et de pixel 1 à pixel 720 vers le bas et le reste du canal sera la couleur par défaut.

## Conditions préalables {#prerequisites}

Avant de créer un processus pour la vidéo, veuillez remplir les conditions préalables suivantes :

1. Téléchargez une vidéo dans le dossier **Ressources** de votre instance AEM
1. Créez un projet AEM Screens (par exemple, **TestVideoRendition**) et un canal nommé (**VideoRendering**), comme illustré dans la figure ci-dessous :

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Création d’un processus de remplissage vidéo {#creating-a-video-padding-workflow-1}

Pour créer un processus de remplissage vidéo, vous devez créer un processus pour votre vidéo, puis l’utiliser dans le canal de votre projet AEM Screens.

Suivez les étapes ci-dessous pour créer et utiliser le processus :

1. Création d’un processus
1. Utilisation du processus dans un projet AEM Screens

### Création d’un processus {#creating-a-workflow}

Suivez les étapes ci-dessous pour créer un processus pour votre vidéo:

1. Accédez à votre instance AEM et cliquez sur Outils à partir du rail latéral. Sélectionnez **Processus** —> **Modèles** pour créer un nouveau modèle.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Cliquez sur **Modèles** —> **Créer** —> **Créer un modèle**. Saisissez le **Titre** **VideoRendition** et le **Nom** dans le champ **Ajouter un modèle de processus.** Cliquez sur **Terminé** pour ajouter le modèle de processus.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Une fois le modèle de processus créé, sélectionnez le modèle (**VideoRendition**), puis cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Drag and drop the **Command Line** component to your workflow.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Sélectionnez le composant **Ligne de commande** et ouvrez la boîte de dialogue Propriétés.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Sélectionnez l’onglet **Arguments** pour renseigner les champs dans la boîte de dialogue **Ligne de commande - Propriétés des étapes**.

   Saisissez le format dans les **Types Mime** (***vidéo/mp4***) et la commande (**/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hd .mp4***) pour démarrer le processus dans le champ **Commandes** .

   Veuillez consulter les détails sur les **types Mime** et les **Commandes** dans la note ci-dessous.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Select the workflow (**VideoRenditions**) and click **Start Workflow** from the action bar to open the **Run Workflow** dialog box.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Select the path of your asset in the **Payload** (as ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***) and enter the **Title** as ***RunVideo*** and click **Run**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Utilisation du processus dans un projet AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Suivez les étapes ci-dessous pour utiliser le processus dans votre projet AEM Screens :

1. Accédez à un projet AEM Screens (**TestVideoRendition** —> **Canaux** —>**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Cliquez sur **Modifier** dans la barre d’actions. Faites glisser la vidéo que vous avez initialement téléchargée vers **Ressources**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Une fois la vidéo téléchargée, cliquez sur **Prévisualiser** pour afficher la sortie.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validation de la sortie pour le processus{#validating-the-output-for-the-workflow}

Vous pouvez valider votre sortie en procédant comme suit :

* Vérifier l’aperçu de la vidéo dans la chaîne
* Accédez au répertoire ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** dans CRXDE Lite, comme illustré dans la figure ci-dessous :

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

