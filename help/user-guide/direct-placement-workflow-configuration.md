---
title: Configuration d’un workflow de placement direct
seo-title: Direct Placement Workflow Configuration
description: Cette page décrit la configuration d’un workflow de placement direct.
seo-description: This page highlights Direct Placement Workflow Configuration.
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 87%

---


# Configuration d’un workflow de placement direct {#direct-placement-workflow}

Consultez cette page pour en savoir plus sur la configuration d’un workflow de ressources. Vous pourrez ainsi insérer par programmation une ressource dans un canal AEM Screens prédéfini.

Cette section couvre les sujets suivants :

* Présentation
* Configuration d’un workflow de placement direct

## Vue d’ensemble {#overview}

La configuration d’un workflow de placement direct consiste à mapper un canal de projet AEM Screens avec un dossier spécifique de ressources et permet de les placer dans ce dossier. Il est recommandé de lancer une mise à jour hors ligne groupée pour terminer la publication.

En tant qu’auteur de contenu, vous pouvez également cliquer manuellement sur l’option **Mettre à jour le contenu hors ligne**.

>[!NOTE]
>
>Pour savoir comment utiliser la mise à jour hors ligne groupée, voir [Mise à jour de contenu en tant que service](/help/user-guide/content-update-as-a-service.md).

## Configuration d’un workflow de placement direct {#configuring-workflow}

>[!IMPORTANT]
>
>Avant de démarrer la configuration, vous devez installer le [package de démonstration](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). Une fois que vous avez installé le package, vous devez pouvoir le visualiser et y accéder à partir de votre instance AEM > Outils (icône) > **Workflow** > **Modèles de processus**.

Suivez les étapes ci-dessous pour configurer le workflow de placement direct :

1. Accédez à AEM Screens à partir de votre instance AEM et créez un projet Screens intitulé **Workflow de ressources**.

1. Créez un canal appelé **Workflow-Ressources** dans le dossier **Canaux**.

