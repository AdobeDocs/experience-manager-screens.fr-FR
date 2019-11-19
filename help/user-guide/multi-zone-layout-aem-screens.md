---
title: Disposition multizone
seo-title: Disposition multizone
description: La mise en page à zones multiples vous permet de créer plusieurs zones de contenu et d’utiliser divers fichiers, tels que des vidéos, des images et du texte, qui peuvent être combinés dans un seul écran. Consultez cette page pour en savoir plus.
seo-description: La mise en page à zones multiples vous permet de créer plusieurs zones de contenu et d’utiliser divers fichiers, tels que des vidéos, des images et du texte, qui peuvent être combinés dans un seul écran. Consultez cette page pour en savoir plus.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Disposition multizone {#multi-zone-layout}

La page suivante décrit l’utilisation de la mise en page multi-zone et aborde les sujets suivants :

* Présentation
* Création d’une mise en page multizone
* Conditions préalables
* Utilisation de ressources uniques dans une ou plusieurs zones
* Utilisation de contenu séquentiel dans une ou plusieurs zones

## Présentation {#overview}

***La mise en page*** multi-zone vous permet de créer plusieurs zones de contenu et d’utiliser divers fichiers, tels que des vidéos, des images et du texte, qui peuvent être combinés dans un seul écran. Vous pouvez y placer des images, des vidéos et du texte, ce qui permet à l’ensemble de se fondre et de créer une expérience numérique intuitive.

En fonction des exigences du projet, vous avez parfois besoin de plusieurs zones au sein d’un canal et de les modifier comme une unité entière. Par exemple, une séquence de produits avec un flux de réseaux sociaux associé qui s’exécute dans trois zones distinctes sur un seul canal.

## Création d’une mise en page multizone {#creating-multi-zone-layout}

Lors de la création d’un canal, vous pouvez utiliser différents modèles pour créer des zones dans votre canal. Vous pouvez ajouter une image, une vidéo ou un canal incorporé qui permet d’afficher plusieurs fichiers dans une séquence.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, assurez-vous que vous disposez d’un projet prêt comme condition préalable pour commencer à mettre en oeuvre la mise en page multi-zone. Par exemple :

* Création d’un projet AEM Screens intitulé **Zones**
* Créez un affichage sous **Emplacements** intitulé&#x200B;**MultiZoneDisplay**

Créez un canal intitulé **MultiZone** dans le projet **Zones** . Suivez les étapes ci-dessous :

**Création du canal**

1. Sélectionnez le lien Adobe Experience Manager (en haut à gauche), puis **Screens**. Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
1. Accédez au dossier **Canaux** et cliquez sur **Créer** dans la barre d’actions.

1. Sélectionnez **Gauche L-bar Diviser le canal** d’écran dans l’assistant **Créer** .

1. Cliquez sur **Suivant** et saisissez le **titre** sous la forme **MultiZone**.

1. Cliquez sur **Créer** pour terminer la création du canal.

![screen_shot_2018-12-07at120026pm](assets/screen_shot_2018-12-07at120026pm.png)

### Utilisation de ressources uniques dans une ou plusieurs zones {#using-single-assets-in-one-or-more-zones}

Vous pouvez utiliser des fichiers uniques tels qu’une image ou une vidéo dans les trois zones différentes. Suivez les étapes ci-dessous pour la mise en oeuvre :

1. **Ajout de contenu au canal**

   1. Accédez à **Zones** —&gt; **Canaux**—&gt;**MultiZone**.
   1. Select the **MultiZone** channel and click **Edit** from the action bar to open the editor.
   ![screen_shot_2018-12-07at14917pm](assets/screen_shot_2018-12-07at14917pm.png)

1. **Ajout d’images au canal**

   Pour lire une seule image ou une vidéo dans les trois zones, faites glisser l’image dans l’éditeur de canaux, comme illustré ci-dessous.

   ![new1-1](assets/new1-1.gif)

### Utilisation de contenu séquentiel dans une ou plusieurs zones {#using-sequenced-content-in-one-or-more-zones}

Si vous souhaitez que les zones affichent une séquence d’images ou de contenu et une image statique dans trois zones différentes, suivez les étapes ci-dessous pour plus de détails.

1. **Création d’un dossier Canal**

   1. Accédez à **Zones** —&gt; **MultiZone** —&gt; Canaux **et cliquez sur** **Créer dans la barre d’actions.**
   1. Select **Channels Folder** from the **Create** wizard and click **Next**.
   1. Enter the title as **EmbeddedChannels** and click **Create**.
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Ajout de deux autres canaux au dossier Canal**

   1. Accédez à **Zones** —&gt; **Canaux** —&gt; Canaux **incorporés et cliquez sur** **Créer dans la barre d’actions.**
   1. Sélectionnez Canal **de** séquence dans l’assistant **Créer** pour créer un canal intitulé** Zone1**.
   1. Select **Zone1** and click **Edit** from the action bar to open the editor.
   1. Faites glisser quelques images sur ce canal.
   De même, créez un autre canal de séquence intitulé **Zone2** dans le dossier **Canaux** incorporés.

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

1. **Ajout de séquences/composants incorporés au canal principal (MultiZone)**

   1. Accédez à **Zones** —&gt; **Canaux** —&gt; **MultiZone**.
   1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.
   1. Faites glisser et déposez le composant Séquence **** incorporée dans deux des zones, comme illustré dans la figure ci-dessous.
   ![new](assets/new.gif)

1. **Ajouter du contenu aux trois zones**

   1. Accédez à **Zones** —&gt; **Canaux** —&gt; **MultiZone**.
   1. Sélectionnez la séquence incorporée dans l’une des zones.
   1. Cliquez sur l’icône **Configurer** (clé à molette) pour accéder à l’une des séquences incorporées dans l’éditeur.
   1. Sélectionnez le chemin du canal comme **Zones** —&gt; **Canaux** —&gt; Canaux **incorporés —&gt;** **Zone1, comme illustré dans la figure ci-dessous.**
   De même, ajoutez **Zone2** à un autre composant de séquence incorporé dans l’éditeur. Ajoutez également une image à la troisième zone en bas, comme illustré ci-dessous.

   ![new2-1](assets/new2-1.gif)

#### Affichage du résultat {#viewing-the-result}

Une fois que vous avez mis en oeuvre des mises en page à zones multiples à l’aide des étapes précédentes, la sortie suivante s’affiche, comme illustré dans la figure ci-dessous.

La sortie suivante dans le lecteur d’écran affiche le contenu dans trois zones différentes. Les zones de gauche et de droite (toutes deux utilisant la séquence incorporée comme composant) affichent la séquence d’images et la zone ci-dessous affiche une image statique.

![new2-2](assets/new2-2.gif)

