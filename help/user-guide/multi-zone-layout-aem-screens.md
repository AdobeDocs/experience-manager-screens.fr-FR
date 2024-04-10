---
title: Disposition multizone
description: Découvrez comment créer du contenu multizone et utiliser diverses ressources telles que des vidéos, des images et du texte qui peuvent être regroupées en un seul écran dans AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 49%

---

# Disposition multizone {#multi-zone-layout}

La page suivante décrit l’utilisation de la disposition multizone et aborde les sujets suivants :

* Présentation
* Création d’une disposition multizone
* Prérequis
* Utilisation de ressources uniques dans une ou plusieurs zones
* Utilisation de contenu séquentiel dans une ou plusieurs zones

## Présentation {#overview}

***Disposition multizone*** permet de créer du contenu multizone et d’utiliser différentes ressources telles que des vidéos, des images et du texte, qui peuvent être regroupées en un seul écran. Il est possible d’importer des images, des vidéos et du texte, et de les mélanger de façon à créer une expérience digitale intuitive.

En fonction des exigences du projet, il est parfois nécessaire de disposer de plusieurs zones au sein d’un canal et dus modifier comme une unité entière. Par exemple, une séquence de produits avec un flux de médias sociaux associé qui s’exécute dans trois zones distinctes sur un seul canal.


### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, vous devez posséder des connaissances conceptuelles sur :

* [Création d’un projet AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project)
* [Création d’un affichage](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays)
* [Affectation d’un canal à un affichage](/help/user-guide/channel-assignment.md)

## Création d’une disposition multizone {#creating-multi-zone-layout}

Lors de la création d’un canal, vous pouvez utiliser différents modèles pour créer des zones dans le canal. Vous pouvez ajouter une image, une vidéo ou un canal incorporé qui permet d’afficher plusieurs ressources dans une séquence.

**Création d’un canal**

1. Sélectionnez le lien Adobe Experience Manager (en haut à gauche), puis **Screens**. Vous pouvez également utiliser le lien d’accès direct : `http://localhost:4502/screens.html/content/screens`.
1. Accédez au dossier **Channels** (Canaux) et cliquez sur **Créer** dans la barre d’actions.

1. Sélectionnez **Canal d’écran partagé 1x2** dans l’assistant **Créer**.

1. Cliquez sur **Suivant** et saisissez le **titre** **MultiZone**.

1. Cliquez sur **Créer** pour terminer la création du canal.

### Utilisation de ressources uniques dans une ou plusieurs zones {#using-single-assets-in-one-or-more-zones}

Vous pouvez utiliser des ressources uniques telles qu’une image ou une vidéo dans chacune des zones. Suivez les étapes ci-dessous pour la mise en œuvre :

1. **Ajout de contenu au canal**

   1. Accédez à **Zones** > **Canaux**> **MultiZone**.
   1. Sélectionnez la variable **MultiZone** canal et clic **Modifier** dans la barre d’actions.

1. **Ajout d’images au canal**

   Pour lire une seule image ou une vidéo dans deux zones, il vous suffit de faire glisser une image dans chaque zone de l’éditeur de canal, comme illustré dans la figure ci-dessous :

   ![image](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Utilisation de contenu séquentiel dans une ou plusieurs zones {#using-sequenced-content-in-one-or-more-zones}

Si vous souhaitez que les zones affichent une séquence d’images et une vidéo dans les différentes zones, suivez les étapes ci-dessous pour plus de détails.

1. **Créer un dossier de canaux**

   1. Accédez à **Zones** > **MultiZone** > **Canaux** et cliquez sur **Créer** dans la barre d’actions.
   1. Sélectionnez **Dossier de canaux** dans l’assistant de **Création** et cliquez sur **Suivant**.
   1. Saisissez le titre **EmbeddedChannels** et cliquez sur **Créer**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Ajout de deux autres canaux au dossier de canaux**

   1. Accédez à **Zones** > **Canaux** > **EmbeddedChannels** et cliquez sur **Créer** dans la barre d’actions.
   1. Sélectionner **Canal de séquence** de la **Créer** pour créer un canal intitulé **`Zone1`**.
   1. Sélectionner **`Zone1`** et cliquez sur **Modifier** dans la barre d’actions.
   1. Faites glisser quelques images sur ce canal.
   1. De même, créez un autre canal de séquence intitulé **`Zone2`** in **EmbeddedChannels** dossier.
   1. Faites glisser une vidéo sur ce canal.

   La figure suivante montre les canaux **`Zone1`** et **`Zone2`**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   Les images ajoutées à l’éditeur de **`Zone1`** le canal de séquence est illustré ci-dessous :

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   La vidéo a été ajoutée à l’éditeur de **`Zone2`** le canal de séquence est illustré ci-dessous :

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Ajout de séquences incorporées (composant) au canal principal (MultiZone)**

   1. Accédez à **Zones** > **Canaux** > **MultiZone**.
   1. Cliquez sur **Modifier** dans la barre d’actions.
   1. Faites glisser le composant **Séquence incorporée** dans les deux zones.
   1. Sélectionnez la séquence incorporée dans l’une des zones.
   1. Cliquez sur l’icône **Configurer** (clé à molette) pour accéder à l’une des séquences incorporées dans l’éditeur.
   1. Sélectionnez le chemin du canal comme **Zones** > **Canaux** > **EmbeddedChannels** > **`Zone1`**, comme illustré dans la figure ci-dessous.
   1. De même, ajoutez le **`Zone2`** à un autre composant de séquence incorporée dans l’éditeur.

      ![image](/help/user-guide/assets/multi-zone/multizone-3.png)

### Création d’un emplacement et d’un affichage {#creating-location}

Créez un emplacement et un affichage afin de pouvoir afficher le contenu dans le lecteur AEM Screens.

1. **Création d’un emplacement**

   1. Accédez à **Zones** > **Emplacements** dossier.
   1. Sélectionnez la variable **Emplacements** et sélectionnez **Créer** dans la barre d’actions.
   1. Sélectionner **Emplacement** de la **Créer** assistant et sélectionnez **Suivant**.
   1. Saisissez le **Titre** as **SanJose** et sélectionnez **Créer**.

1. **Création d’un affichage**

   1. Accédez à **Zones** > **Emplacements** dossier.
   1. Sélectionnez la variable **SanJose** emplacement et sélectionnez **Créer** dans la barre d’actions.
   1. Sélectionner **Affichage** de la **Créer** assistant et sélectionnez **Suivant**.
   1. Saisissez le **Titre** as **Lobby** et sélectionnez **Créer**.

### Affectation de canaux à l’affichage {#channel-channel}

Vous devez affecter les canaux à l’affichage de façon à visualiser le contenu. Suivez les étapes ci-dessous pour affecter le canal à l’affichage.

1. **Affectation du canal à l’affichage**

   1. Accédez à **Zones** > **Emplacements** > **SanJose**> **Lobby**.
   1. Sélectionnez la variable **Lobby** afficher et sélectionner **Attribuer le canal** dans la barre d’actions.
   1. Entrez le chemin du canal **MultiZone** dans **Chemin du canal**.
   1. Définissez les **Événements pris en charge** suivants : **Chargement initial**, **Écran inactif** et **Minuteur**.
   1. Sélectionnez **Enregistrer**.

      ![image](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. De même, vous devez attribuer les deux autres canaux incorporés (**`Zone1`** et **`Zone2`**) à cet affichage.
   1. Une fois que vous avez affecté les trois canaux à l’événement **Lobby** , vous devriez pouvoir visualiser les canaux affectés à partir du tableau de bord d’affichage.

      ![image](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      >Après avoir affecté le canal principal (dans ce cas, **MultiZone**) à l’affichage, il est obligatoire d’attribuer les deux autres canaux incorporés. **`Zone1`** et **`Zone2`** également au même affichage.

### Enregistrement de l’appareil {#registering-device}

Lorsque vous avez configuré un emplacement et un affichage, suivez les étapes ci-dessous pour enregistrer le périphérique et lui attribuer un affichage.

1. **Enregistrement de l’appareil**

   1. Accédez à **Zones** > **Périphériques** dossier.
   1. Sélectionnez la variable **Périphériques** et sélectionnez **Gestionnaire de périphériques** dans la barre d’actions.
   1. Sélectionner **Enregistrement de périphérique** et sélectionnez l’appareil en attente dans la liste.

      >[!NOTE]
      > Le titre de l’appareil doit correspondre au jeton de l’appareil (champ **Jeton**) figurant dans l’onglet **Enregistrement du périphérique**.

   1. Si le titre correspond au jeton de l’appareil, sélectionnez l’appareil, puis sélectionnez **Enregistrer le périphérique** dans la barre d’actions.
   1. Si le code d’enregistrement correspond au code du lecteur Screens **Enregistrement de périphérique** onglet, sélectionnez **Valider** dans la barre d’actions.
      ![image](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Saisissez le **Titre** as **`Chrome-Device1`** et sélectionnez **Enregistrer**.
   1. Sélectionnez **Attribuer l’affichage** et choisissez le chemin de la configuration de l’appareil.

   >[!NOTE]
   >Si vous essayez d’afficher le contenu dans le lecteur Screens, veillez à sélectionner **Mettre à jour le contenu hors ligne** depuis le tableau de bord des canaux pour chacun des canaux affectés à l’affichage.

### Affichage du résultat {#viewing-the-result}

Lorsque vous implémentez des mises en page multizone à l’aide des étapes précédentes, la sortie suivante s’affiche.

Vérifiez le lecteur Screens afin de pouvoir visualiser la sortie qui affiche le contenu dans deux zones différentes. Les zones de gauche et de droite (toutes deux utilisent la séquence incorporée comme composant).

La zone de gauche est un canal de séquence et celle de droite inclut une vidéo.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
