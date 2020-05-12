---
title: Disposition multizone
seo-title: Disposition multizone
description: La disposition multizone permet de créer du contenu multizone et d’utiliser diverses ressources telles que des vidéos, des images et du texte, qui peuvent être regroupées en un seul écran. Consultez cette page pour en savoir plus.
seo-description: La disposition multizone permet de créer du contenu multizone et d’utiliser diverses ressources telles que des vidéos, des images et du texte, qui peuvent être regroupées en un seul écran. Consultez cette page pour en savoir plus.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: ae05d169dce9d02562159524f9bf43e88a29e43f
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 54%

---


# Disposition multizone {#multi-zone-layout}

La page suivante décrit l’utilisation de la disposition multizone et aborde les sujets suivants :

* Présentation
* Création d’une disposition multizone
* Conditions préalables
* Utilisation de ressources uniques dans une ou plusieurs zones
* Utilisation de contenu séquentiel dans une ou plusieurs zones

## Présentation {#overview}

***La disposition multizone permet de créer du contenu multizone et d’utiliser diverses ressources telles que des vidéos, des images et du texte, qui peuvent être regroupées en un seul écran.*** Il est possible d’importer des images, des vidéos et du texte, et les mélanger de façon à créer une expérience numérique intuitive .

En fonction des exigences du projet, il est parfois nécessaire de disposer de plusieurs zones au sein d’un canal et dus modifier comme une unité entière. Par exemple, une séquence de produits avec un flux de réseaux sociaux associé qui s’exécute dans trois zones distinctes sur un seul canal.

## Création d’une disposition multizone {#creating-multi-zone-layout}

Lors de la création d’un canal, vous pouvez utiliser des modèles différents afin de créer des zones dans votre canal. Vous pouvez ajouter une image, une vidéo ou un canal incorporé qui permet d’afficher plusieurs ressources dans une séquence.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, assurez-vous que vous disposez d’un projet prêt comme condition préalable pour commencer à mettre en œuvre la disposition multizone. Par exemple :

* Créez un projet AEM Screens intitulé **Zones**
* Créez un affichage sous **Emplacements** intitulé&#x200B;**MultiZoneDisplay**.

Créez un canal intitulé **MultiZone** dans le projet **Zones**. Suivez les étapes ci-dessous :

**Création du canal**

1. Sélectionnez le lien Adobe Experience Manager (en haut à gauche), puis **Screens**. Vous pouvez également utiliser le lien d’accès direct : `http://localhost:4502/screens.html/content/screens`.
1. Accédez au dossier **Channels** (Canaux) et cliquez sur **Créer** dans la barre d’actions.

1. Sélectionnez Canal **d’écran partagé** 1x2 dans l’assistant **Créer** .

1. Cliquez sur **Suivant** et saisissez le **titre** **MultiZone**.

1. Cliquez sur **Créer** pour terminer la création du canal.

### {#using-single-assets-in-one-or-more-zones}Utilisation de ressources uniques dans une ou plusieurs zones

Vous pouvez utiliser des ressources uniques telles qu’une image ou une vidéo dans les trois zones différentes. Suivez les étapes ci-dessous pour la mise en œuvre :

1. **Ajout de contenu au canal**

   1. Accédez à **Zones** —> **Canaux**—>**MultiZone**.
   1. Sélectionnez le canal **MultiZone** et cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.

1. **Ajout d’images au canal**

   Pour lire une seule image ou une vidéo dans deux zones, il vous suffit de faire glisser une image dans chaque zone de l’éditeur de canal, comme illustré dans la figure ci-dessous :

   MultiZone-img3

   ![image](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Utilisation de contenu séquentiel dans une ou plusieurs zones {#using-sequenced-content-in-one-or-more-zones}

Si vous souhaitez que les zones affichent une séquence d’images ou de contenu et une image statique dans deux zones différentes, suivez les étapes ci-dessous pour plus de détails.

1. **Créer un dossier de canaux**

   1. Accédez à **Zones** —> **MultiZone** —> **Canaux** et cliquez sur **Créer** dans la barre d’actions.
   1. Sélectionnez **Dossier de canaux** dans l’assistant de **Création** et cliquez sur **Suivant**.
   1. Saisissez le titre **EmbeddedChannels** et cliquez sur **Créer**.
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Ajout de deux autres canaux au dossier de canaux**

   1. Accédez à **Zones** —> **Canaux** —> EmbeddedChannels **et cliquez sur** **Créer** dans la barre d’actions.
   1. Select **Sequence Channel** from the **Create** wizard to create a channel titled as **Zone1**.
   1. Sélectionnez **Zone1** et cliquez sur **Modifier** dans la barre d’action pour ouvrir l’éditeur.
   1. Faites glisser quelques images sur ce canal.
   De même, créez un autre canal de séquence intitulé **Zone2** dans le dossier **EmbeddedChannels**.

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Les images ajoutées à l’éditeur du canal de séquence **Zone1** sont présentées ci-dessous :

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   La vidéo ajoutée à l&#39;éditeur du canal de séquence **Zone2** est illustrée ci-dessous :

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Ajout de séquences incorporées (composant) au canal principal (MultiZone)**

   1. Accédez à **Zones** —> **Canaux** —> **MultiZone**.
   1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.
   1. Faites glisser le composant Séquence **** incorporée vers deux des zones.

1. **Ajouter du contenu aux trois zones**

   1. Accédez à **Zones** —> **Canaux** —> **MultiZone**.
   1. Sélectionnez la séquence incorporée dans l’une des zones.
   1. Cliquez sur l’icône **Configurer** (clé à molette) pour accéder à l’une des séquences incorporées dans l’éditeur.
   1. Sélectionnez le chemin du canal **Zones** —> **Canaux** —> **EmbeddedChannels** —> **Zone1**, comme illustré ci-dessous.
   De même, ajoutez **Zone2** à un autre composant de séquence incorporée dans l’éditeur.

   ![image](/help/user-guide/assets/multi-zone/multizone-3.png)

### Création de l’emplacement et de l’affichage {#creating-location}

Vous devez créer un emplacement et un affichage pour vue le contenu dans le lecteur d’écran. Suivez les étapes ci-dessous pour créer un emplacement et un affichage.

1. **Création d’un emplacement**

   1. Navigate to **Zones** --> **Locations** folder.
   1. Select the **Locations** folder and click **Create** from the action bar.
   1. Sélectionnez **Emplacement** à partir de l’assistant **Créer** et cliquez sur **Suivant**.
   1. Enter the **Title** as **SanJose** and click **Create**.

1. **Création d’un affichage**

   1. Navigate to **Zones** --> **Locations** folder.
   1. Sélectionnez l’emplacement **SanJose** et cliquez sur **Créer** dans la barre d’actions.
   1. Sélectionnez **Affichage** à partir de l’assistant **Créer** et cliquez sur **Suivant**.
   1. Enter the **Title** as **Lobby** and click **Create**.

### Affectation d’un Canal à l’affichage {#channel-channel}

Vous devez affecter les canaux à l’affichage pour vue du contenu. Suivez les étapes ci-dessous pour attribuer le canal à l’affichage.

1. **Affectation d’un Canal à l’affichage**

   1. Accédez à **Zones** —> **Emplacements** —> **SanJose**—> **Lobby.**
   1. Sélectionnez l’affichage **hall** et cliquez sur **Attribuer un Canal** dans la barre d’actions.
   1. Entrez le chemin d’accès au canal **MultiZone** dans le chemin **du** Canal.
   1. Set the **Supported Events** as **Initial Load**, **Idle Screen**, and **Timer**.
   1. Cliquez sur **Enregistrer**.

      ![image](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. De même, vous devez affecter les deux autres canaux incorporés (**Zone1** et **Zone2**) à cet affichage à l’aide de l’étape (2).
   1. Une fois que vous avez affecté les trois canaux à l&#39;affichage **du hall** , vous devez pouvoir vue les canaux affectés à partir du tableau de bord d&#39;affichage.

      ![image](/help/user-guide/assets/multi-zone/multizone-img8.png)
   >[!Important]
   > Une fois que vous avez affecté le canal principal (dans ce cas, **MultiZone**) à l’affichage, il est obligatoire d’affecter les deux autres canaux incorporés **Zone1** et **Zone2** également au même affichage.

### Enregistrement du périphérique {#registering-device}

Une fois que vous avez configuré un emplacement et un affichage, suivez les étapes ci-dessous pour enregistrer le périphérique et lui affecter l’affichage.

1. **Enregistrement du périphérique**

   1. Accédez au dossier **Zones** —> **Périphériques** .
   1. Select the **Devices** folder and click **Device Manager** from the action bar.
   1. Cliquez sur Enregistrement **du** périphérique et sélectionnez le périphérique en attente dans la liste.
      >[!NOTE]
      > Le titre du périphérique doit correspondre au jeton du périphérique (champ **Jeton** ) affiché dans l&#39;onglet Enregistrement **du** périphérique.
   1. Si le titre correspond au jeton du périphérique, sélectionnez le périphérique et cliquez sur **Enregistrer le périphérique** dans la barre d’actions.
   1. Si le code d’enregistrement correspond au code figurant dans l’onglet d’enregistrement du lecteur d’écran, cliquez sur **Valider** dans la barre d’actions.
      ![image](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Enter the **Title** as **Chrome-Device1** and click **Register**.
   1. Sélectionnez **Affecter l’affichage** et sélectionnez le chemin d’accès à la configuration du périphérique.

#### Affichage du résultat {#viewing-the-result}

Une fois que vous avez mis en œuvre des mises en page à zones multiples à l’aide des étapes précédentes, le résultat suivant s’affiche, comme illustré ci-dessous.

Consultez le lecteur d’écran pour vue la sortie qui affiche le contenu dans deux zones différentes. Les zones de gauche et de droite (toutes deux utilisent la séquence incorporée comme composant).

>[!NOTE]
>Si vous tentez de vue le contenu dans le lecteur d’écran, veillez à cliquer sur **Mettre à jour le contenu** hors ligne dans le tableau de bord de canal.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


