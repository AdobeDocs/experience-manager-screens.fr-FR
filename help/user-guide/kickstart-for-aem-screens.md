---
title: Guide de démarrage rapide
seo-title: Guide de démarrage rapide
description: Suivez cette page pour créer un projet AEM Screens de démonstration. Vous pouvez créer une expérience de signalisation numérique à partir de l’installation et configurer un nouveau projet d’affichage de contenu dans le lecteur AEM Screens.
translation-type: tm+mt
source-git-commit: 78aab8e8ad8ad9e3a3caf20fef044f507b5298a0
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 63%

---


# Guide de démarrage rapide  {#kickstart-guide}

Cette section est un démarrage rapide de AEM Screens et explique comment configurer et exécuter un projet AEM Screens. Il vous guide tout au long des étapes nécessaires pour configurer une expérience de signature numérique de base et ajouter du contenu, tel que des ressources et/ou des vidéos, à chaque canal, puis publier le contenu sur un lecteur AEM Screens.

>[!NOTE]
>Avant de début à travailler sur les détails du projet, assurez-vous d’avoir installé le dernier Feature Pack. Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.5 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID.

## Création d’une expérience de signalisation numérique en 5 minutes {#creating-a-digital-signage-experience-in-minutes}

Suivez les étapes ci-dessous pour créer un exemple de projet pour AEM Screens et publier du contenu sur le lecteur d’écran.

>[!NOTE]
>Le didacticiel suivant présente la lecture du contenu de votre canal dans le lecteur Chrome OS.

>[!IMPORTANT]
>**Paramètres de configuration OSGi**
>Vous devez activer le référent vide pour autoriser le périphérique à publier des données sur le serveur. Par exemple, si la propriété de référent vide est désactivée, le périphérique ne pourra pas publier de capture d’écran. Actuellement, certaines de ces fonctionnalités ne sont disponibles que si le filtre de Parrain Apache Sling Allow Empty est activé dans la configuration OSGi. Le tableau de bord peut afficher un avertissement indiquant que les paramètres de sécurité peuvent empêcher l’utilisation de certaines de ces fonctions.
>Pour activer l’option ***Allow Empty d’Apache Sling Referrer Filter***, procédez comme suit :


## Autorisation des requêtes de référents vides {#allow-empty-referrer-requests}

1. Accédez au gestionnaire de **Configuration de la console Web Adobe Experience Manager** via l’instance AEM —> icône en forme de marteau —> **Opérations** —> **Console Web**.

   ![image](assets/config/empty-ref1.png)

1. La **configuration de la console web d’Adobe Experience Manager** s’ouvre. Recherche de référent Sling.

   Pour rechercher la propriété référent Sling, appuyez sur **Command+F** pour **Mac** et **Ctrl+F** pour **Windows**.

1. Cochez l’option **Allow Empty** comme illustré dans la figure ci-dessous.

   ![image](assets/config/empty-ref2.png)

1. Cliquez sur **Enregistrer** pour activer l’option Allow Empty d’Apache Sling Referrer Filter.


## Tutoriel {#tutorial}

### Création d’un projet AEM Screens {#creating-project}

La première étape consiste à créer un nouveau projet AEM Screens.

1. Accédez à votre instance Adobe Experience Manager (AEM) et cliquez sur **Ecrans**. Alternatively, you can navigate directly from `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Click **Create Screens Project** to create a new Screens project. Enter the title as **DemoScreens** and click **Save**.

   ![image](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Une fois le projet créé, il vous ramène à la page d&#39;accueil de projet Ecrans. Vous pouvez sélectionner votre projet. Dans un projet, il y a cinq dossiers différents intitulés **Applications**, **Canaux**, **Périphériques**, **Emplacements et Planifications.******


### Création d’un canal {#creating-channel}

Une fois que vous avez votre projet, vous devez créer une nouveau canal où vous pouvez gérer le contenu.

Pour créer un canal pour votre projet, procédez comme suit :

1. Une fois que vous avez créé un projet, sélectionnez le projet **DemoScreens** et sélectionnez le dossier **** Canaux, comme illustré dans la figure ci-dessous. Click **+ Create** from the action bar.

   ![image](assets/kickstart/demo-2.png)

1. Choose the **Sequence Channel** from the wizard and click **Next**.
   ![image](assets/kickstart/demo-3.png)

1. Saisissez le **titre** *TestChannel* et cliquez sur **Créer**.

   ![image](assets/kickstart/demo-4.png)

Le canal *TestChannel* est créé et ajouté au dossier de canaux, comme illustré dans la figure ci-dessous.

![image](assets/kickstart/demo-5.png)

### Ajout de contenu à un canal {#adding-content}

Une fois que vous avez votre canal, vous devez y ajouter le contenu que le lecteur Screens va afficher.

Suivez les étapes ci-dessous pour ajouter du contenu au canal (*TestChannel*) dans votre projet : 

1. Accédez au projet *DemoProject* que vous avez créé et sélectionnez le dossier **Channels** (Canaux).

1. Cliquez sur **Modifier** dans la barre d’actions (voir la figure ci-dessous). L’éditeur de *TestChannel* s’ouvre.

   ![image](assets/kickstart/demo-6.png)

1. Cliquez sur l’icône qui fait passer le panneau latéral du côté gauche de la barre d’actions pour ouvrir les ressources et les composants. 

1. Faites glisser et déposez les composants que vous souhaitez ajouter à votre canal. 

   ![image](assets/kickstart/demo-7.png)

### Création d’un emplacement {#creating-location}

Une fois votre canal en place, vous devez créer un emplacement.

>[!NOTE]
>***Locations*** compartmentalize your various digital signage experiences and contains the configurations of the displays according to where the various screens are.

Pour créer un emplacement pour votre projet, procédez comme suit :

1. Navigate to the *DemoProject* you created and select the **Locations** folder.

1. Click **+ Create** from the action bar.

1. Sélectionnez **Emplacement** dans l’assistant, puis cliquez sur **Suivant**.

1. Enter the **Name** for your location (enter the title as *TestLocation*) and click **Create**.

L’emplacement *TestLocation* est créé et ajouté à votre dossier **Locations** (Emplacements).


### Création d’un affichage pour un emplacement {#creating-display}

Une fois que vous avez créé un emplacement, vous devez créer un affichage pour celui-ci.

>[!NOTE]
>***Les affichages*** représentent l’expérience numérique qui s’exécute sur un ou plusieurs écrans.

1. Navigate to the **TestLocation** and select it.

1. Cliquez sur **Créer** dans la barre d’actions.

1. Sélectionnez **Affichage** à partir de l’assistant **Créer** et cliquez sur **Suivant**.

1. Saisissez le **Titre** (*LobbyDisplay*).

1. Cliquez sur **Créer**.

Un nouvel affichage (*TestDisplay*) est ajouté à votre emplacement (*TestLocation)*, comme le montre la figure ci-dessous. 

### Attribution d’un canal {#assigning-channel}

1. Accédez à l’affichage depuis *Test_Project* --> **Emplacements** --> *TestLocation* --> *TestDisplay*.

1. Select *TestDisplay* and tap/click **Assign Channel** from the action bar, *Or*,

1. Vous pouvez aussi cliquer sur **Tableau de bord** et sélectionner **+Attribuer un canal** en haut à droite du panneau **CANAUX ET PLANIFICATIONS ATTRIBUÉS**, comme illustré dans la figure ci-dessous. La boîte de dialogue **Attribution de canaux** s’ouvre.

1. Sélectionnez **Canal de référence** en fonction du **chemin d’accès**

1. Définissez le **rôle du canal** sur *LiveStream*.

1. Sélectionnez **Chemin d’accès au canal** (*Test_Project* --> *Canaux* --> *TestChannel*) dans le **canal**.

1. Définissez la **priorité** de ce canal sur *1*.

1. Choisissez les **événements pris en charge** **Chargement initial** et **Écran inactif**.

1. Entrez la **planification** et sélectionnez les dates dans **Active from (Actif à partir de)** et **Active until (Actif jusqu’à)**.

1. Cliquez sur **Enregistrer**.

Le canal est créé et ajouté au panneau.



### Enregistrement d’un périphérique {#registering-device}

Vous devez enregistrer votre périphérique à l’aide du tableau de bord AEM. 

>[!NOTE]
>Vous pouvez ouvrir le lecteur Screens à l’aide de l’application AEM’Screens que vous avez téléchargée ou à l’aide du navigateur web.



### Viewing the content in AEM Screens Player {#viewing-the-content-in-screens-player}

Une fois que vous avez ajouté les configurations ci-dessus, le lecteur doit automatiquement afficher le canal par défaut de l’affichage sur votre périphérique.



Pour plus d’informations sur le lecteur AEM Screens, voir [Lecteur AEM Screens](working-with-screens-player.md).
