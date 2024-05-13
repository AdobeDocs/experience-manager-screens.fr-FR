---
title: Configuration d’un workflow de placement direct
description: Cette page décrit la configuration d’un workflow de placement direct.
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 89%

---


# Configuration d’un workflow de placement direct {#direct-placement-workflow}

Consultez cette page pour en savoir plus sur la configuration d’un workflow de ressources. Vous pourrez ainsi insérer par programmation une ressource dans un canal AEM Screens prédéfini.

Cette section couvre les sujets suivants :

* Vue d’ensemble
* Configurer un workflow de placement direct

## Vue d’ensemble {#overview}

La configuration d’un workflow de placement direct consiste à mapper un canal de projet AEM Screens avec un dossier spécifique de ressources et permet de les placer dans ce dossier. Adobe recommande de déclencher une mise à jour hors ligne en bloc pour terminer la publication.

En tant qu’auteur de contenu, vous pouvez également cliquer manuellement sur **Mettre à jour le contenu hors ligne**.

>[!NOTE]
>
>Pour savoir comment utiliser la mise à jour hors ligne en bloc, voir [Mise à jour de contenu en tant que service](/help/user-guide/content-update-as-a-service.md).

## Configurer un workflow de placement direct {#configuring-workflow}

>[!IMPORTANT]
>
>Avant de commencer la configuration, installez le `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. Une fois le package installé, il devrait être possible de voir le workflow et d’y accéder à partir de votre instance AEM > Outils (icône) > **Workflow** > **Modèles de workflow**.

Pour configurer le workflow de placement direct, procédez comme suit :

1. Accédez à AEM Screens à partir de votre instance AEM et créez un projet Screens intitulé **Workflow de ressources**.

1. Créez un canal appelé **Workflow-Ressources** dans le dossier **Canaux**.

