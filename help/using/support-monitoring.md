---
title: Suivi de l’assistance
description: Découvrez le suivi de l’assistance dans le cadre du guide des bonnes pratiques d’AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: ht
source-wordcount: '218'
ht-degree: 100%

---

# Suivi de l’assistance {#support-monitoring}

Cette section décrit les bonnes pratiques relatives à la gestion des anomalies de contenu et d’appareil dans un projet de signalétique digitale.

Le suivi de l’assistance comprend les activités suivantes :

* **Surveillance de l’appareil**
* **Surveillance du contenu**

## Surveillance du contenu {#content-monitoring}

La surveillance du contenu permet de résoudre les problèmes liés au contenu qui ne s’affiche pas correctement à l’écran :

1. Si un problème d’écran vide se produit, procédez comme suit :

   * Vérifiez la *prévisualisation* pour voir si le canal affiche un écran noir.
   * Sur votre ordinateur portable, enregistrez un *lecteur Chrome local* (en tant qu’extension) sur cet écran et regardez si un écran noir s’affiche.
   * Cliquez avec le bouton droit et examinez les *journaux correspondants*.

   Si le problème se produit uniquement sur l’appareil, mais pas sur le lecteur local, procédez comme suit :

   * Vérifiez le *type de média* (en cours d’utilisation) qui peut présenter des problèmes sur cet appareil et assurez-vous également que le contenu a bien été téléchargé en local (effacez le cache du canal dans l’interface d’administration).
   * Incluez les *journaux d’appareil* dans le dossier d’incident afin d’accélérer la procédure de dépannage.
   * *Collectez les journaux* de l’appareil à partir d’AEM.

## Surveillance de l’appareil {#device-monitoring}

Cette activité consiste à contrôler l’appareil physique si vous rencontrez un problème d’écran vide :

1. Si un problème d’écran vide se produit, procédez comme suit :

   * Vérifiez que le *dispositif d’affichage* est allumé.
   * Vérifiez que l’*ordinateur* est allumé et envoie un signal.
   * Cliquez avec le bouton droit et examinez les *journaux appropriés*.
