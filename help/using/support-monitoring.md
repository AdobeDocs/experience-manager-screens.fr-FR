---
title: Suivi de l’assistance
description: En savoir plus sur le suivi de l’assistance pour le guide des bonnes pratiques d’AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 23%

---

# Suivi de l’assistance {#support-monitoring}

Cette section décrit les bonnes pratiques relatives à la gestion des anomalies de contenu et d’appareil dans un projet de signalétique digitale.

Le suivi de l’assistance comprend les activités suivantes :

* **Surveillance de l’appareil**
* **Surveillance du contenu**

## Surveillance du contenu {#content-monitoring}

La surveillance du contenu vous permet de résoudre les problèmes liés au contenu qui ne s’affiche pas correctement à l’écran :

1. Si un problème d’écran vide se produit :

   * Vérifiez les *aperçu* vous pouvez donc voir si le canal affiche un écran noir.
   * Enregistrement d’une *lecteur Chrome local* (comme extension) sur votre ordinateur portable à cet affichage et vérifiez s’il affiche un écran noir.
   * Cliquez avec le bouton droit de la souris, puis examinez le *logs applicables*.

   En outre, si le problème ne se produit pas sur le lecteur local, mais uniquement sur l’appareil :

   * Vérifiez les *type de média* (en cours d’utilisation) qui peut présenter des problèmes sur cet appareil et confirmer si le contenu a bien été téléchargé localement (effacer le cache du canal de l’interface utilisateur d’administration).
   * Incluez les *journaux d’appareil* dans le dossier d’incident afin d’accélérer la procédure de dépannage.
   * *Collectez les journaux* de l’appareil à partir d’AEM.

## Surveillance de l’appareil {#device-monitoring}

Surveillance de l’appareil liée à la surveillance de l’appareil physique si vous rencontrez un problème d’écran vide :

1. Si un problème d’écran vide se produit :

   * Vérifiez que le *dispositif d’affichage* est allumé.
   * Vérifiez si la variable *machine* est allumé et envoie un signal.
   * Cliquez avec le bouton droit de la souris, examinez et *logs applicables*.
