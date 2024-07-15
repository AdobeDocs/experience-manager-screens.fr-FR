---
title: Guide de démarrage rapide
description: Apprenez à créer un projet AEM Screens de démonstration. Vous pouvez créer une expérience de signalétique numérique à partir de l’installation et configurer un nouveau projet d’affichage de contenu dans le lecteur AEM Screens.
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 100%

---

# Guide de démarrage rapide {#kickstart-guide}

Cette section de démarrage rapide d’AEM Screens explique comment configurer et exécuter un projet AEM Screens. Elle vous guide tout au long des étapes nécessaires pour configurer une expérience de signalétique numérique de base et ajouter du contenu, tel que des ressources et/ou des vidéos, à chaque canal, puis publier le contenu sur un lecteur AEM Screens.

>[!NOTE]
>Avant de commencer à travailler sur les détails du projet, assurez-vous d’avoir installé le dernier pack de fonctionnalités pour AEM Screens. Vous pouvez télécharger le dernier pack de fonctionnalités à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html) en utilisant votre Adobe ID.

## Conditions préalables {#prerequisites}

Suivez les étapes ci-dessous afin de créer un exemple de projet pour AEM Screens et de publier du contenu sur le lecteur Screens.

>[!NOTE]
>Le tutoriel suivant présente la lecture du contenu de votre canal dans un lecteur Chrome OS.

>[!IMPORTANT]
>**Paramètres de configuration OSGi**
>Vous devez activer le référent vide pour autoriser l’appareil à publier des données sur le serveur. Par exemple, si la propriété de référent vide est désactivée, l’appareil ne pourra pas publier de capture d’écran. Actuellement, certaines de ces fonctions ne sont disponibles que si l’option Allow Empty d’Apache Sling Referrer Filter est activée dans la configuration OSGi. Le tableau de bord peut afficher un avertissement indiquant que les paramètres de sécurité peuvent empêcher l’utilisation de certaines de ces fonctions.
>Pour activer l’option ***Allow Empty d’Apache Sling Referrer Filter***, procédez comme suit :


## Autorisation des requêtes de référents vides {#allow-empty-referrer-requests}

1. Accédez à la **Configuration de la console web Adobe Experience Manager** via Instance AEM > icône en forme de marteau > **Opérations** > **Console web**.

   ![image](assets/config/empty-ref1.png)

1. **Configuration de la console web d’Adobe Experience Manager** s’ouvre. Recherche de référent Sling.

   Pour rechercher la propriété référent Sling, appuyez sur **Command+F** pour **Mac** et **Ctrl+F** pour **Windows**.

1. Cochez l’option **Allow Empty** comme illustré dans la figure ci-dessous.

   ![image](assets/config/empty-ref2.png)

1. Cliquez sur **Save** pour activer l’option Allow Empty d’Apache Sling Referrer Filter.

## Création d’une expérience de signalétique numérique en 5 minutes {#creating-a-digital-signage-experience-in-minutes}

### Création d’un projet AEM Screens {#creating-project}

La première étape consiste à créer un projet AEM Screens.

1. Accédez à votre instance Adobe Experience Manager (AEM) et cliquez sur **Screens**. Vous pouvez également y accéder directement depuis `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Cliquez sur **Créer un projet Screens** afin de créer un projet Screens.
1. Saisissez le titre **DemoScreens** et cliquez sur **Enregistrer**.

   ![image](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Une fois le projet créé, il vous ramène à la page d’accueil du projet AEM Screens. Vous pouvez cliquer sur votre projet. Un projet comporte cinq dossiers différents intitulés **Applications**, **Canaux**, **Appareils**, **Emplacements** et **Planifications**.

### Création d’un canal {#creating-channel}

Une fois que vous avez créé votre projet AEM Screens, créez un canal destiné à gérer le contenu.

Pour créer un canal pour votre projet, procédez comme suit :

1. Une fois que vous avez créé un projet, cliquez sur le projet **DemoScreens** et sur le dossier **Canaux**, comme illustré dans la figure ci-dessous. Cliquez sur **+ Créer** dans la barre d’actions.

   ![image](assets/kickstart/demo-2.png)

1. Sélectionnez le **Canal de séquence** dans l’assistant et cliquez sur **Suivant**.
   ![image](assets/kickstart/demo-3.png)

1. Saisissez le **titre** **TestChannel** et cliquez sur **Créer**.

   ![image](assets/kickstart/demo-4.png)

   Le canal **TestChannel** est alors ajouté au dossier de canaux, comme illustré dans la figure ci-dessous.

   ![image](assets/kickstart/demo-5.png)

### Ajout de contenu à un canal {#adding-content}

Une fois que vous avez votre canal, vous devez y ajouter le contenu que le lecteur AEM Screens peut afficher.

Suivez les étapes ci-dessous pour ajouter du contenu au canal (**TestChannel**) dans votre projet :

1. Accédez au projet **DemoProject** que vous avez créé et cliquez sur le canal **TestChannel** dans le dossier **Canaux**.

1. Cliquez sur **Modifier** dans la barre d’actions (voir la figure ci-dessous). L’éditeur de **TestChannel** s’ouvre.

   ![image](assets/kickstart/demo-6.png)

1. Cliquez sur l’icône qui active l’ouverture du panneau latéral gauche de la barre d’actions pour ouvrir les ressources et les composants.

1. Faites glisser et déposez les composants que vous souhaitez ajouter à votre canal.

   ![image](assets/kickstart/demo-7.png)

### Création d’un emplacement {#creating-location}

Une fois que vous disposez du canal, vous devez créer un emplacement.

>[!NOTE]
>Les ***emplacements*** permettent de compartimenter vos diverses expériences de signalétique numérique et contiennent les configurations de leurs affichages en fonction de l’endroit où se trouvent les différents écrans.

Pour créer un emplacement pour votre projet, procédez comme suit :

1. Accédez au projet **DemoProject** que vous avez créé et cliquez sur le dossier **Emplacements**.
1. Cliquez sur **+ Créer** dans la barre d’actions.
1. Cliquez sur **Emplacement** dans l’assistant, puis sur **Suivant**.
1. Saisissez le **nom** de votre emplacement (saisissez le titre **TestLocation**), puis cliquez sur **Créer**.

L’emplacement **TestLocation** est créé et ajouté à votre dossier **Locations** (Emplacements).


### Création d’un affichage pour un emplacement {#creating-display}

Une fois que vous avez créé un emplacement, vous devez créer un affichage pour celui-ci.

>[!NOTE]
>L’***affichage*** représente l’expérience digitale qui s’exécute sur un ou plusieurs écrans.

1. Accédez à l’emplacement **TestLocation** et cliquez dessus.
1. Cliquez sur **Créer** dans la barre d’actions.

   ![image](assets/kickstart/demo-disp1.png)

1. Cliquez sur **Affichage** à partir de l’assistant **Créer** et sur **Suivant**.

   ![image](assets/kickstart/demo-disp2.png)

1. Saisissez le **Titre** **LobbyDisplay** et cliquez sur **Créer**.

   ![image](assets/kickstart/demo-disp3.png)

   Un nouvel affichage intitulé **TestDisplay** est ajouté à votre emplacement **TestLocation**, comme le montre la figure ci-dessous.

   ![image](assets/kickstart/demo-disp4.png)

### Attribution d’un canal {#assigning-channel}

Lorsque le projet est configuré, attribuez le canal à un affichage pour afficher le contenu.

1. Accédez à l’affichage requis à partir de **DemoScreens** > **Emplacements** > **TestLocation** > **LobbyDisplay**.

1. Cliquez sur **Attribuer le canal** dans la barre d’actions.

   ![image](assets/kickstart/demo-assign1.png)

   Ou,

   Cliquez sur **Tableau de bord** dans la barre d’actions, puis sur **+Attribuer le canal** dans le panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**.

   ![image](assets/kickstart/demo-assign2.png)

1. La boîte de dialogue **Attribution de canaux** s’ouvre.

1. À partir de l’option **Paramètres**, choisissez le canal **par chemin** et les **Événements pris en charge** **Chargement initial** et **Écran inactif**.

   >[!NOTE]
   >
   >Les champs **Rôle du canal**, **Priorité** et **Méthodes d’interruption** sont tous renseignés par défaut. Consultez la section [Propriétés des canaux](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) pour en savoir plus sur les propriétés d’attribution de canaux.

   ![image](assets/kickstart/demo-assign3.png)

   Vous pouvez également cliquer sur la **Fenêtre d’activation** et le **Planning de périodicité**.

   >[!NOTE]
   >Le *Planning de périodicité* permet de définir un planning récurrent pour votre canal. Vous pouvez configurer plusieurs plannings de périodicité pour un canal.
   >Pour plus d’informations, voir [Planning de périodicité](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule).

1. Cliquez sur **Enregistrer** une fois vos préférences configurées.

### Enregistrement d’un appareil et attribution d’un appareil à un affichage {#registering-device}

Enregistrez votre appareil à l’aide du tableau de bord AEM.

>[!IMPORTANT]
>Le lecteur Chrome OS peut être installé en tant que plug-in du navigateur Chrome en mode Développement sans que vous ayez à utiliser de lecteur Chrome. Pour l’installer, procédez comme suit :
>
>1. Cliquez [ici](https://download.macromedia.com/screens/) pour télécharger la dernière version du lecteur Chrome.
>1. Décompressez-la et enregistrez-la sur le disque.
>1. Ouvrez le navigateur Chrome et cliquez sur **Extensions** dans le menu ou accédez directement à ***chrome://extensions***.
>1. Activez le **mode Développement** dans l’angle supérieur droit de l’écran.
>1. Cliquez sur **Charger les fichiers décompressés** dans l’angle supérieur gauche et chargez le lecteur Chrome décompressé.
>1. Vérifiez si le plug-in **Lecteur Chrome AEM Screens** est disponible dans la liste des extensions.
>1. Ouvrez un nouvel onglet et cliquez sur l’icône **Applications** dans l’angle supérieur gauche de l’écran ou accédez directement à ***chrome://apps***.
>1. Cliquez sur le plug-in **AEM Screens** afin de lancer le lecteur Chrome. Par défaut, le lecteur est lancé en mode plein écran. Appuyez sur **Échap** pour quitter le mode plein écran.

Après avoir activé votre lecteur Chrome OS, suivez les étapes ci-dessous pour enregistrer un appareil Chrome.

1. Accédez au dossier **Appareils** de votre projet à partir de votre instance AEM.

1. Cliquez sur **Gestionnaire d’appareils** dans la barre d’actions.

   ![image](assets/kickstart/demo-register1.png)

1. Cliquez sur **Enregistrement d’appareil** en haut à droite.

1. Cliquez sur l’appareil requis, puis sur **Enregistrer le périphérique**.

   ![image](assets/kickstart/demo-register2.png)

1. Attendez que l’appareil envoie son code d’enregistrement et, simultanément, vérifiez le **Code d’enregistrement** depuis votre appareil Chrome.
   ![image](assets/kickstart/demo-register3.png)

1. Si le **code d’enregistrement** est le même sur les deux machines, cliquez sur **Valider** dans AEM.

1. Définissez le nom souhaité **ChromeDeviceforDemo** pour l’appareil, puis cliquez sur **Enregistrer**.

   ![image](assets/kickstart/demo-register4.png)

1. Cliquez sur **Attribuer l’affichage** dans la boîte de dialogue **Appareil enregistré**.

   ![image](assets/kickstart/demo-register5.png)

1. Cliquez sur le chemin d’accès à votre affichage via **DemoScreens** > **Emplacements** > **TestLocation** > **LobbyDisplay**, puis cliquez sur **Attribuer**.

   ![image](assets/kickstart/demo-device6.png)

1. Une fois que l’appareil a été attribué, la confirmation suivante s’affiche.

   ![image](assets/kickstart/demo-register8.png)

1. Cliquez sur **Terminer** pour terminer le processus d’enregistrement. Votre appareil enregistré apparaît dans le tableau de bord des affichages.

   ![image](assets/kickstart/demo-register9.png)

### Affichage du contenu dans le lecteur Chrome {#viewing-content-output}

Toutes les ressources de votre canal sont à présent en cours de lecture sur votre lecteur Chrome OS.

Félicitations, vous lisez maintenant du contenu dans un canal AEM Screens !

![image](assets/kickstart/demo-video-screens.gif)
