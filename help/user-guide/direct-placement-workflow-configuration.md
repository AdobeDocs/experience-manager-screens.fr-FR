---
title: 'Configuration du flux de travail de positionnement direct '
seo-title: Configuration du flux de travail de positionnement direct
description: Cette page met en évidence la configuration du flux de travail de positionnement direct.
seo-description: Cette page met en évidence la configuration du flux de travail de positionnement direct.
translation-type: tm+mt
source-git-commit: 19baf90409eab4c72fb38e992c272338b0098d89

---


# Configuration du flux de travail de positionnement direct {#direct-placement-workflow}

Suivez cette page pour en savoir plus sur la configuration d’un flux de travaux de ressources qui vous permet d’insérer par programmation un fichier dans un AEM Screens prédéfini.

Cette section couvre les sujets suivants :

* Présentation
* Configuration du flux de travail de positionnement direct

## Présentation {#overview}

La configuration du flux de travaux de placement direct mappe un de projet AEM Screens vers un dossier spécifique dans les ressources et permet de placer n’importe quelle ressource dans ce dossier. Il est recommandé de déclencher une mise à jour hors ligne en masse pour terminer la publication.

En tant qu’auteur de contenu, vous pouvez également cliquer manuellement sur **Mettre à jour le contenu** hors ligne.

>[!NOTE]
> Pour savoir comment utiliser la mise à jour hors ligne en masse, reportez-vous à la section Mise à jour de [contenu en tant que service](/help/user-guide/content-update-as-a-service.md).

## Configuration du flux de travail de positionnement direct {#configuring-workflow}

>[!IMPORTANT]
> Avant de  la configuration, vous devez installer le package [de](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)démonstration. Une fois que vous avez installé le package, vous devez pouvoir le  et y accéder à partir de votre instance AEM —> Outils (icône) —> **Workflow** —> Modèles de **flux de travail**.

Suivez les étapes ci-dessous pour configurer le flux de travaux de placement direct :

1. Accédez à AEM Screens à partir de votre instance AEM et créez un projet Screens intitulé **Asset Workflow**.

1. Create a channel titled as **Workflow-Assets** under **Channels** folder.

1. 
