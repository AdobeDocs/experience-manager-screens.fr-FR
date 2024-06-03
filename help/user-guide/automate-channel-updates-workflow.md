---
title: Utiliser un workflow pour automatiser les mises à jour des ressources pour un canal AEM Screens
description: Découvrez comment créer un workflow pour traiter automatiquement les ressources chargées dans Adobe Experience Manager et les affecter dynamiquement à un canal Screens.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 78%

---


# Utiliser un workflow pour automatiser les mises à jour des ressources pour un canal AEM Screens {#automate-channel-updates-workflow}

Découvrez comment créer un processus pour traiter automatiquement les ressources chargées vers Adobe Experience Manager et les affecter dynamiquement à un canal Screens. Dans cet exemple, un workflow est déclenché lorsqu’une image est ajoutée à un dossier spécifique. Le workflow applique une superposition de texte dynamique (processus de filigrane) et attribue l’image à un canal Screens. Cet exemple peut être appliqué à de nombreux scénarios d’automatisation.

## Conditions préalables {#prerequisites}

Pour suivre ce tutoriel, vous avez besoin de :

1. [AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65)
1. [Pack de services AEM 8 ou version ultérieure](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/release-notes/release-notes)
1. [AEM 6.5 Screens FP7 ou version ultérieure](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103)

## Configuration rapide {#quick-setup}

La vidéo ci-dessous explique comment installer un exemple de package de code qui va mettre en place un nouveau workflow dans Adobe Experience Manager. Cette fonctionnalité permet de mettre à jour les propriétés d’un dossier dans AEM Assets pour pointer vers un canal Screens. Chaque fois qu’une image est ajoutée à ce dossier, elle est aussi ajoutée au canal AEM Screens spécifié.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Téléchargez le package de code compilé : **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Installez le package ci-dessus à l’aide du gestionnaire de modules AEM.

## Modèle de workflow {#workflow-model}

Un schéma de métadonnées de dossier personnalisé a été créé pour capturer le canal Screens cible dans lequel les images doivent être ajoutées. Deux modèles de workflows sont utilisés pour automatiser le traitement des ressources. La variable **Ressource de mise à jour de gestion des actifs numériques** Le workflow est modifié pour appeler un workflow personnalisé, Traitement des ressources de démonstration **Screens , qui examine le dossier contenant la ressource pour déterminer le canal Screens cible. Le processus **Traitement des ressources de démo Screens** est également responsable de l’application du filigrane à l’image.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Étapes du processus de workflow personnalisé {#workflow-process-step}

Deux étapes de processus de workflow personnalisés sont utilisées dans le cadre du workflow de **traitement des ressources de démo Screens**.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

Le workflow personnalisé `AssetProcessingCheck.java` est un processus qui vérifie la payload du workflow. Il détermine si la payload est une ressource et si le dossier qui la contient est configuré pour pointer vers un canal AEM Screens. Si toutes les exigences sont remplies, l’étape de processus conserve deux propriétés, `screen-channel` et `asset-path`, dans les métadonnées du workflow.

Le workflow personnalisé `AddAssetToChannel.java` est une étape de processus qui inspecte les métadonnées du workflow et qui met à jour le canal AEM Screens pour référencer l’image.

1. Téléchargez le code source : **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Décompressez et visionnez le code à l’aide de l’EDI de votre choix.
