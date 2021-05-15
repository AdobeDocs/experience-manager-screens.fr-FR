---
title: Utiliser le processus pour automatiser les mises à jour des ressources pour un canal AEM Screens
seo-title: Utiliser le processus pour automatiser les mises à jour des ressources pour un canal AEM Screens
description: Découvrez comment créer un processus pour traiter automatiquement les fichiers téléchargés vers Adobe Experience Manager et les affecter dynamiquement à un canal d’écrans. Dans cet exemple, lorsqu’une image est ajoutée à un dossier spécifique, un processus est déclenché qui applique un filigrane dynamique et affecte l’image à un canal d’écrans. Les leçons tirées de cet exemple peuvent être appliquées à une grande variété de scénarios d'automatisation.
seo-description: Découvrez comment créer un processus pour traiter automatiquement les fichiers téléchargés vers Adobe Experience Manager et les affecter dynamiquement à un canal d’écrans. Dans cet exemple, lorsqu’une image est ajoutée à un dossier spécifique, un processus est déclenché qui applique un filigrane dynamique et affecte l’image à un canal d’écrans. Les leçons tirées de cet exemple peuvent être appliquées à une grande variété de scénarios d'automatisation.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Développement dans Screens
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 4%

---


# Utilisez le processus pour automatiser les mises à jour des ressources pour un canal AEM Screens {#automate-channel-updates-workflow}

Découvrez comment créer un processus pour traiter automatiquement les fichiers téléchargés vers Adobe Experience Manager et les affecter dynamiquement à un canal d’écrans. Dans cet exemple, lorsqu’une image est ajoutée à un dossier spécifique, un processus est déclenché qui applique une incrustation de texte dynamique (processus de filigrane) et affecte l’image à un canal d’écrans. Les leçons tirées de cet exemple peuvent être appliquées à une grande variété de scénarios d&#39;automatisation.

## Prérequis {#prerequisites}

Pour terminer ce tutoriel, vous devez :

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=fr)
1. [AEM Service Pack 8 ou supérieur](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=fr)
1. [AEM 6.5 Écrans FP7 ou supérieurs](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## Configuration rapide {#quick-setup}

La vidéo ci-dessous illustre comment installer un exemple de package de code qui va introduire un nouveau flux de travail pour Adobe Experience Manager. Cette fonctionnalité permet à un utilisateur de mettre à jour les propriétés d’un dossier en AEM Assets pour pointer vers un canal Ecrans. Chaque fois qu’une image est ajoutée à ce dossier, elle est ajoutée au canal d’écrans spécifié.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Téléchargez le package de code compilé : **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Installez le package ci-dessus à l’aide d’AEM Package Manager.

## Modèle de workflow {#workflow-model}

Un schéma de métadonnées de dossier personnalisé a été créé pour capturer le canal cible Screens (Ecrans de ) dans lequel les images doivent être ajoutées. Deux modèles de workflows sont utilisés pour automatiser le traitement des ressources. Le workflow **DAM Update Asset** est modifié pour appeler un workflow personnalisé, **Screens Demo Asset Processing** qui inspectera le dossier contenant le fichier pour déterminer le canal des écrans de cible. Le flux de travail **Traitement des ressources de démonstration des écrans** est également responsable de l’application du filigrane à l’image.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Étapes de processus de workflow personnalisé {#workflow-process-step}

Inspect effectue deux étapes de processus de processus personnalisés qui sont utilisées dans le cadre du **processus de traitement des ressources de démonstration des écrans**.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` est un processus de flux de travaux personnalisé qui effectue une vérification de la charge utile du flux de travaux afin de déterminer si la charge est une ressource et si le dossier contenant est configuré pour pointer vers un canal d’écrans. Si les exigences sont satisfaites, l’étape de processus conserve deux propriétés, `screen-channel` et `asset-path`, aux métadonnées du flux de travail.

`AddAssetToChannel.java` est une étape personnalisée du processus qui inspecte les métadonnées du processus et met à jour le canal Ecrans pour référencer l’image.

1. Téléchargez le code source : **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Décompressez et vue le code à l’aide de votre IDE favori.
