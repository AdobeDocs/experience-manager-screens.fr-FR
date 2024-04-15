---
title: Création d’un processus de remplissage vidéo
description: En savoir plus sur la création d’un remplissage vidéo dans le workflow pour vos ressources.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 63%

---

# Création d’un processus de remplissage vidéo {#creating-a-video-padding-workflow}

Cette section couvre les sujets suivants :

* **Présentation**
* **Prérequis**
* **Création d’un processus de remplissage vidéo**
   * **Création d’un processus**
   * **Utilisation du workflow dans le projet AEM Screens**

* **Validation de la sortie pour le processus**

## Présentation {#overview}

Le cas d’utilisation suivant implique de placer une vidéo (par exemple : 1280 x 720) dans un canal où l’affichage est de 1920 x 1080 et où la vidéo doit être placée à 0x0 (en haut à gauche). La vidéo ne doit pas être étirée ni modifiée d’aucune manière et n’utilisez pas **la couverture** dans le composant vidéo.

La vidéo s’affiche sous la forme d’un objet de pixel 1 à pixel 1280 sur et de pixel 1 à pixel 720 vers le bas, et le reste du canal est la couleur par défaut.

## Conditions préalables {#prerequisites}

Avant de créer un workflow pour la vidéo, remplissez les conditions préalables suivantes :

1. Téléchargez une vidéo dans le dossier **Ressources** de votre instance AEM
1. Créez un projet AEM Screens (par exemple, **TestVideoRendition**) et un canal nommé (**VideoRendering**), comme illustré dans la figure ci-dessous :

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Création d’un processus de remplissage vidéo {#creating-a-video-padding-workflow-1}

Pour créer un processus de remplissage vidéo, vous devez créer un processus pour votre vidéo, puis l’utiliser dans le canal de votre projet AEM Screens.

Suivez les étapes ci-dessous pour créer et utiliser le processus :

1. Création d’un processus
1. Utilisation du processus dans un projet AEM Screens

### Création d’un processus {#creating-a-workflow}

Suivez les étapes ci-dessous pour créer un processus pour votre vidéo :

1. Accédez à votre instance AEM.
1. Cliquez sur Outils dans le rail latéral.
1. Sélectionner **Workflow** > **Modèles** vous pouvez donc créer un modèle.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Cliquez sur **Modèles** > **Créer** > **Créer un modèle**. Saisissez le **Titre** **VideoRendition** et le **Nom** dans le champ **Ajouter un modèle de processus**. Cliquez sur **Terminé** pour ajouter le modèle de processus.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Une fois le modèle de processus créé, sélectionnez le modèle (**VideoRendition**), puis cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Faites glisser et déposez le **`Command Line`** à votre workflow.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Sélectionnez la variable **`Command Line`** et ouvrez la boîte de dialogue des propriétés.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Sélectionnez la variable **Arguments** .
1. Dans le **Ligne de commande - Propriétés des étapes** , saisissez le format dans la zone **Types MIME** (en tant que ***video/mp4***) et la commande comme (***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hp.mp4***). Cette commande lance le workflow dans la fonction **Commandes** champ .

   Consultez les détails de la **Types MIME** et **Commandes** dans la note ci-dessous.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Sélectionnez le workflow (**VideoRenditions**).
1. Cliquez sur **Démarrer le processus** dans la barre d’actions.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Dans le **Exécuter le workflow** , sélectionnez le chemin d’accès de votre ressource dans la **Payload** (en tant que ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***) et saisissez la variable **Titre** as ***RunVideo*** et cliquez sur **Exécuter**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Utilisation du processus dans un projet AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Suivez les étapes ci-dessous pour utiliser le processus dans votre projet AEM Screens :

1. Accédez à un projet AEM Screens (**TestVideoRendition** > **Canaux** >**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Cliquez sur **Modifier** dans la barre d’actions. Faites glisser la vidéo que vous avez initialement téléchargée vers **Ressources**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Une fois la vidéo téléchargée, cliquez sur **Prévisualiser** pour afficher la sortie.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validation de la sortie pour le processus {#validating-the-output-for-the-workflow}

Vous pouvez valider votre sortie en procédant comme suit :

* Vérifier l’aperçu de la vidéo dans la chaîne
* Accédez au répertoire ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** dans CRXDE Lite, comme illustré dans la figure ci-dessous :

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
