---
title: Utilisation d’un processus pour automatiser les mises à jour des ressources pour un canal AEM Screens
seo-title: Utilisation d’un processus pour automatiser les mises à jour des ressources pour un canal AEM Screens
description: Découvrez comment créer un processus pour traiter automatiquement les ressources chargées vers Adobe Experience Manager et les affecter dynamiquement à un canal Screens. Dans cet exemple, l’ajout d’une image à un dossier spécifique déclenche un processus qui applique un filigrane dynamique et affecte l’image à un canal Screens. Cet exemple peut être appliqué à de nombreux scénarios d’automatisation.
seo-description: Découvrez comment créer un processus pour traiter automatiquement les ressources chargées vers Adobe Experience Manager et les affecter dynamiquement à un canal Screens. Dans cet exemple, l’ajout d’une image à un dossier spécifique déclenche un processus qui applique un filigrane dynamique et affecte l’image à un canal Screens. Cet exemple peut être appliqué à de nombreux scénarios d’automatisation.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Développement dans Screens
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 94%

---


# Utilisation d’un processus pour automatiser les mises à jour des ressources pour un canal AEM Screens {#automate-channel-updates-workflow}

Découvrez comment créer un processus pour traiter automatiquement les ressources chargées vers Adobe Experience Manager et les affecter dynamiquement à un canal Screens. Dans cet exemple, lorsqu’une image est ajoutée à un dossier spécifique, un processus est déclenché qui applique une incrustation de texte dynamique (processus de filigrane) et affecte l’image à un canal d’écrans. Cet exemple peut être appliqué à de nombreux scénarios d’automatisation.

## Prérequis {#prerequisites}

Pour suivre ce tutoriel, vous avez besoin de :

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=fr)
1. [AEM Service Pack 8 ou une version supérieure](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=fr)
1. [AEM 6.5 Screens FP7 ou une version supérieure](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html?lang=fr)

## Configuration rapide {#quick-setup}

La vidéo ci-dessous explique comment installer un exemple de package de code qui va introduire un nouveau processus pour Adobe Experience Manager. Cette fonctionnalité permet à un utilisateur de mettre à jour les propriétés d’un dossier dans AEM Assets pour pointer vers un canal Screens. Chaque fois qu’une image est ajoutée à ce dossier, elle est aussi ajoutée au canal Screens spécifié.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Téléchargez le package de code compilé : **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Installez le package ci-dessus à l’aide du gestionnaire de modules AEM.

## Modèle de workflow {#workflow-model}

Un schéma de métadonnées de dossier personnalisé a été créé pour capturer le canal cible de Screens dans lequel les images doivent être ajoutées. Deux modèles de workflows sont utilisés pour automatiser le traitement des ressources. Le processus **Ressource de mise à jour de DAM** est modifié pour appeler un processus personnalisé, **Traitement de ressource de démo Screens**, qui inspectera le dossier contenant la ressource pour déterminer le canal Screens cible. Le processus **Traitement des ressources de démo Screens** est également responsable de l’application du filigrane à l’image.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Étapes de processus de workflow personnalisé {#workflow-process-step}

Deux étapes de processus de workflow personnalisés sont utilisées dans le cadre du workflow de **traitement de ressource de démo Screens**.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` est un processus de workflow personnalisé qui effectue une vérification de la charge utile du workflow afin de déterminer si le payload est une ressource et si le dossier contenant est configuré pour pointer vers un canal Screens. Si toutes les exigences sont remplies, l’étape de processus conserve deux propriétés, `screen-channel` et `asset-path`, dans les métadonnées du workflow.

`AddAssetToChannel.java` est une étape de processus de workflow personnalisé qui inspecte les métadonnées du workflow et qui met à jour le canal Screens pour référencer l’image.

1. Téléchargez le code source : **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Décompressez et visionnez le code à l’aide de l’EDI de votre choix.
