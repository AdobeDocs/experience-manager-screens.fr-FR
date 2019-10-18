---
title: Surveillance du support
seo-title: Prise en charge de la surveillance pour les écrans AEM
description: La page décrit le guide des bonnes pratiques de la surveillance de l’assistance pour les écrans AEM.
seo-description: La page décrit le guide des bonnes pratiques de la surveillance de l’assistance pour les écrans AEM.
translation-type: tm+mt
source-git-commit: 3c91e0ec80b29bebcc066f45a1eef1fd74e00a13

---


# Surveillance du support {#support-monitoring}

Cette section décrit les meilleures pratiques relatives à la gestion des anomalies de périphérique et de contenu dans un projet de signalisation numérique.

La surveillance de l'assistance comprend :

* **Surveillance des périphériques**
* **Surveillance du contenu**

## Surveillance du contenu {#content-monitoring}

La surveillance du contenu vous permet de résoudre les problèmes liés au contenu qui ne s’affiche pas correctement à l’écran :

1. Si un problème d’écran vide se produit :

   * Vérifiez *l’aperçu* pour voir si le canal affiche un écran noir.
   * Enregistrez un lecteur *chromé* local (comme extension) sur votre ordinateur portable à cet écran et voyez si cela montre un écran noir.
   * Cliquez avec le bouton droit de la souris et examinez et vérifiez les journaux ** applicables.
   En outre, si cela ne se produit pas sur le lecteur local mais uniquement sur le périphérique :

   * Vérifiez le type *de* média (en cours d’utilisation) qui peut présenter des problèmes sur ce périphérique et vérifiez si le contenu a bien été téléchargé localement (l’interface utilisateur d’administration a effacé le cache du canal).
   * Incluez les journaux *des* périphériques dans le ticket pour un dépannage rapide.
   * *Collecte des journaux* du périphérique à partir d’AEM.


## Surveillance des périphériques {#device-monitoring}

Surveillance du périphérique liée à la surveillance du périphérique physique si vous rencontrez un problème d’écran vide :

1. Si un problème d’écran vide se produit :

   * Vérifiez si l’ *affichage* est activé.
   * Vérifiez si l' *ordinateur* est sous tension et envoie le signal.
   * Cliquez avec le bouton droit de la souris, inspectez et vérifiez les journaux ** applicables.

