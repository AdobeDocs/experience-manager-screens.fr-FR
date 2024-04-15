---
title: Utilisation d’un processus pour automatiser les mises à jour des ressources pour un canal AEM Screens
description: Découvrez comment créer un workflow pour traiter automatiquement les ressources chargées dans Adobe Experience Manager et les affecter dynamiquement à un canal Screens.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 56%

---


# Utilisation d’un processus pour automatiser les mises à jour des ressources pour un canal AEM Screens {#automate-channel-updates-workflow}

Découvrez comment créer un processus pour traiter automatiquement les ressources chargées vers Adobe Experience Manager et les affecter dynamiquement à un canal Screens. Dans cet exemple, l’ajout d’une image à un dossier spécifique déclenche un processus qui applique un recouvrement de texte dynamique (processus de filigrane) et affecte l’image à un canal Screens. Cet exemple peut être appliqué à de nombreux scénarios d’automatisation.

## Prérequis {#prerequisites}

Pour suivre ce tutoriel, vous avez besoin de :

1. [AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65)
1. [AEM Service Pack 8 ou version ultérieure](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/release-notes/release-notes)
1. [AEM 6.5 Screens FP7 ou version ultérieure](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103)

## Configuration rapide {#quick-setup}

La vidéo ci-dessous illustre comment installer un exemple de module de code qui introduit un nouveau workflow à Adobe Experience Manager. Cette fonctionnalité permet à un utilisateur de mettre à jour les propriétés d’un dossier dans AEM Assets pour pointer vers un canal Screens. Chaque fois qu’une image est ajoutée à ce dossier, elle est ajoutée au canal AEM Screens spécifié.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Téléchargez le package de code compilé : **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Installez le package ci-dessus à l’aide du gestionnaire de modules AEM.

## Modèle de processus {#workflow-model}

Un schéma de métadonnées de dossier personnalisé a été créé pour capturer le canal cible de Screens dans lequel les images doivent être ajoutées. Deux modèles de workflow sont utilisés pour automatiser le traitement des ressources. La variable **Ressource de mise à jour de gestion des actifs numériques** le workflow est modifié pour appeler un workflow personnalisé, **Traitement des ressources de démonstration Screens** qui examine le dossier contenant de la ressource pour déterminer le canal Screens cible. Le processus **Traitement des ressources de démo Screens** est également responsable de l’application du filigrane à l’image.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Étapes de processus de workflow personnalisées {#workflow-process-step}

Deux étapes de processus de workflow personnalisés sont utilisées dans le cadre du workflow de **traitement de ressource de démo Screens**.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

La variable `AssetProcessingCheck.java` workflow personnalisé est un processus qui vérifie la charge utile du workflow. Il détermine si la charge utile est une ressource et si le dossier contenant est configuré pour pointer vers un canal AEM Screens. Si toutes les exigences sont remplies, l’étape de processus conserve deux propriétés, `screen-channel` et `asset-path`, dans les métadonnées du workflow.

La variable `AddAssetToChannel.java` workflow personnalisé est une étape de processus qui inspecte les métadonnées du workflow et met à jour le canal AEM Screens pour référencer l’image.

1. Téléchargez le code source : **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Décompressez et visionnez le code à l’aide de l’EDI de votre choix.
