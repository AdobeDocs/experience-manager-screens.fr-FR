---
title: 'Configuration d’un workflow de placement direct '
seo-title: Configuration d’un workflow de placement direct
description: Cette page décrit la configuration d’un workflow de placement direct.
seo-description: Cette page décrit la configuration d’un workflow de placement direct.
translation-type: ht
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: ht
source-wordcount: '214'
ht-degree: 100%

---


# Configuration d’un workflow de placement direct {#direct-placement-workflow}

Consultez cette page pour en savoir plus sur la configuration d’un workflow de ressources. Vous pourrez ainsi insérer par programmation une ressource dans un canal AEM Screens prédéfini.

Cette section couvre les sujets suivants :

* Présentation
* Configuration d’un workflow de placement direct

## Présentation {#overview}

La configuration d’un workflow de placement direct consiste à mapper un canal de projet AEM Screens avec un dossier spécifique de ressources et permet de les placer dans ce dossier. Il est recommandé de lancer une mise à jour hors ligne groupée pour terminer la publication.

En tant qu’auteur de contenu, vous pouvez également cliquer manuellement sur l’option **Mettre à jour le contenu hors ligne**.

>[!NOTE]
>
>Pour savoir comment utiliser la mise à jour hors ligne groupée, voir [Mise à jour de contenu en tant que service](/help/user-guide/content-update-as-a-service.md).

## Configuration d’un workflow de placement direct {#configuring-workflow}

>[!IMPORTANT]
>
>Avant de démarrer la configuration, vous devez installer le [package de démonstration](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). Une fois le package installé, il devrait être possible de voir le workflow et d’y accéder à partir de votre instance AEM --> Outils (icône) --> **Workflow** --> **Modèles de workflow**.

Suivez les étapes ci-dessous pour configurer le workflow de placement direct :

1. Accédez à AEM Screens à partir de votre instance AEM et créez un projet Screens intitulé **Workflow de ressources**.

1. Créez un canal appelé **Workflow-Ressources** dans le dossier **Canaux**.

1. 
