---
title: Configuration d’un workflow de placement direct
description: Cette page décrit la configuration d’un workflow de placement direct.
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 46%

---


# Configuration d’un workflow de placement direct {#direct-placement-workflow}

Consultez cette page pour en savoir plus sur la configuration d’un workflow de ressources qui vous permet d’insérer une ressource par programmation dans un canal AEM Screens prédéfini.

Cette section couvre les sujets suivants :

* Présentation
* Configuration d’un workflow de placement direct

## Vue d’ensemble {#overview}

La configuration d’un workflow de placement direct consiste à mapper un canal de projet AEM Screens avec un dossier spécifique de ressources et permet de les placer dans ce dossier. Adobe recommande de déclencher une mise à jour hors ligne en bloc pour terminer la publication.

En tant qu’auteur de contenu, vous pouvez également cliquer manuellement sur l’option **Mettre à jour le contenu hors ligne**.

>[!NOTE]
>
>Pour savoir comment utiliser la mise à jour hors ligne en bloc, voir [Mise à jour de contenu en tant que service](/help/user-guide/content-update-as-a-service.md).

## Configuration d’un workflow de placement direct {#configuring-workflow}

>[!IMPORTANT]
>
>Avant de commencer la configuration, vous devez installer le `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. Une fois le package installé, vous devez pouvoir le visualiser et y accéder à partir de votre instance AEM > Outils (icône) > **Workflow** > **Modèles de processus**.

Suivez les étapes ci-dessous pour configurer le workflow de placement direct :

1. Accédez à AEM Screens à partir de votre instance AEM et créez un projet Screens intitulé **Processus des ressources**.

1. Créez un canal appelé **Workflow-Ressources** dans le dossier **Canaux**.

