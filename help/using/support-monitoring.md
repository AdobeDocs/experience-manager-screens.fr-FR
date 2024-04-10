---
title: Suivi de l’assistance
description: En savoir plus sur le suivi de l’assistance pour le guide des bonnes pratiques d’AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 65%

---

# Suivi de l’assistance {#support-monitoring}

Cette section décrit les bonnes pratiques relatives à la gestion des anomalies de contenu et d’appareil dans un projet de signalétique digitale.

Le suivi de l’assistance comprend les activités suivantes :

* **Surveillance de l’appareil**
* **Surveillance du contenu**

## Surveillance du contenu {#content-monitoring}

La surveillance du contenu vous permet de résoudre les problèmes liés au contenu qui ne s’affiche pas correctement à l’écran :

1. Si un problème d’écran vide se produit :

   * Vérifier *aperçu* vous pouvez donc voir si le canal affiche un écran noir.
   * Sur votre ordinateur portable, enregistrez un *lecteur Chrome local* (en tant qu’extension) sur cet écran et voyez si un écran noir s’affiche.
   * Cliquez avec le bouton droit de la souris, puis examinez *logs applicables*.

   En outre, si cela ne se produit pas sur le lecteur local mais uniquement sur l’appareil :

   * Vérifiez le *type de média* (en cours d’utilisation) qui peut présenter des problèmes sur cet appareil et assurez-vous également que le contenu a bien été téléchargé en local (effacer le cache du canal dans l’interface d’administration).
   * Incluez les *journaux d’appareil* dans le dossier d’incident afin d’accélérer la procédure de dépannage.
   * *Collectez les journaux* de l’appareil à partir d’AEM.

## Surveillance de l’appareil {#device-monitoring}

Cette activité consiste à contrôler l’appareil physique si vous rencontrez un problème d’écran vide :

1. Si un problème d’écran vide se produit :

   * Vérifiez que le *dispositif d’affichage* est allumé.
   * Vérifiez que l’*ordinateur* est allumé et envoie un signal.
   * Cliquez avec le bouton droit de la souris, examinez et *logs applicables*.
