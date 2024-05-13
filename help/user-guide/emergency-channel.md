---
title: Canal d’urgence
description: Découvrez comment créer et gérer un canal d’urgence que l’auteur de contenu peut basculer d’un canal de séquence s’il y a une condition préalable.
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 53%

---

# Canal d’urgence {#emergency-channel}

## Description du cas d’utilisation {#use-case-description}

Cette section décrit un exemple de cas d’utilisation. Il met l’accent sur la création et la gestion d’un canal d’urgence que l’auteur de contenu peut passer d’un canal de séquence, s’il y a une condition préalable.

### Prérequis {#preconditions}

Avant de commencer ce cas d’utilisation, vous devez comprendre comment :

* **[Création et gestion des canaux](managing-channels.md)**
* **[Création et gestion des emplacements](managing-locations.md)**
* **[Création et gestion des planifications](managing-schedules.md)**
* **[Enregistrement d’appareils](device-registration.md)**

### Acteurs principaux {#primary-actors}

Auteurs de contenu

## Flux de base : configuration du projet {#basic-flow-setting-up-the-project}

Pour configurer un canal d’urgence, procédez comme suit :

1. Créez un projet AEM Screens appelé **EmergencyChannel**, comme illustré ci-dessous.

   >[!NOTE]
   >Pour en savoir plus sur la création et la gestion de projets dans AEM Screens, voir Création d’un projet.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Création d’un canal de séquence**

   1. Cliquez sur le bouton **Canaux** et cliquez sur **Créer**.

   1. Cliquez sur **Canal de séquence** à partir de l’assistant et créez le canal intitulé **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Ajout de contenu à un canal de séquence**

   1. Cliquez sur le canal (**MainAdChannel**).
   1. Cliquez sur **Modifier** dans la barre d’actions.
   1. Faites glisser quelques ressources sur votre canal.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Création d’un canal d’urgence**

   1. Cliquez sur le bouton **Canaux** dossier.
   1. Cliquez sur **Créer**.
   1. Cliquez sur **Canal de séquence** à partir de l’assistant et créez le canal intitulé **EmergencyChannel**.

   >[!NOTE]
   >
   >Normalement, votre canal d’urgence est ajouté à votre projet de production préexistant.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Ajout de contenu à un canal d’urgence**

   1. Cliquez sur le canal (**Canal d’urgence)**.
   1. Cliquez sur **Modifier** dans la barre d’actions.
   1. Faites glisser vers votre canal la ressource que vous souhaitez exécuter en cas d’urgence.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Création d’un emplacement**

   1. Accédez au **Emplacements** dossier.
   1. Cliquez sur **Créer** à partir de la barre d’actions, puis créez un emplacement appelé **Boutique** à partir de l’assistant.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Création d’affichages dans votre emplacement**

   Accédez à votre emplacement (**Boutique**) et cliquez sur **Créer** dans la barre d’actions. Après l’assistant, créez deux **Affichages** intitulé **StoreFront** et **StoreRear**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Création d’une planification**

   1. Accédez au dossier **Schedules** (Planifications).
   1. Cliquez sur **Créer** dans la barre d’actions.
   1. Après l’assistant, créez un planning intitulé **StoreSchedule**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Affectation des deux affichages à votre planification et définition de priorités

   1. Cliquez sur le planning **(StoreSchedule)** et cliquez sur **Tableau de bord** dans la barre d’actions.

   1. Cliquez sur **+ Attribuer le canal** dans le panneau **CANAUX ATTRIBUÉS**.

   1. Dans la boîte de dialogue **Attribution de canaux** :

      1. Cliquez sur le chemin d’accès au **MainAdChannel**
      1. Définissez la **priorité** sur 2.
      1. Définissez les événements pris en charge **Chargement initial** et **Écran inactif**.
      1. Cliquez sur **Enregistrer**

      De même, procédez de nouveau aux mêmes étapes pour affecter la variable **EmergencyChannel** et définissez ses **Priorité**.

   >[!NOTE]
   >
   >La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celui qui a la valeur la plus élevée a toujours la priorité sur les valeurs les plus faibles.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Cliquez sur **+ Attribuer le canal** dans le panneau **CANAUX ATTRIBUÉS**.

1. Dans la boîte de dialogue **Attribution de canaux** :

   1. Cliquez sur le chemin d’accès au **EmergencyChannel**
   1. Définissez la **priorité** sur 1.

   1. Définissez les Événements pris en charge **Charge initiale**, **Écran inactif** et **Interaction utilisateur**

   1. Cliquez sur **Enregistrer**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   Vous pouvez afficher les canaux affectés à partir du tableau de bord **StoreSchedule**.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Attribution d’une planification à chaque affichage**

   1. Accédez à chaque affichage, par exemple : **EmergencyChannel** > **Emplacements** > **Magasin** >**StoreFront**.

   1. Cliquez sur **Tableau de bord** dans la barre d’actions.
   1. Cliquez sur **...** dans le panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**, puis sur **+Attribuer une planification**.

   1. Cliquez sur le chemin d’accès au planning (par exemple, ici, **EmergencyChannel** > **Planifications** >**StoreSchedule**).

   1. Cliquez sur **Enregistrer**.

   Vous pouvez afficher la planification affectée à l’affichage à partir du tableau de bord **StoreSchedule**.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Enregistrement d’appareils**

   Procédez à l’enregistrement du périphérique. Une fois enregistré, vous pouvez afficher la sortie suivante sur votre lecteur AEM Screens.

   ![new30](assets/new30.gif)

## Basculer vers le canal d’urgence {#switching-to-emergency-channel}

En cas d’urgence, procédez comme suit :

1. Accédez à **EmergencyChannel** > **Planifications** > **StoreSchedule** et cliquez sur **Tableau de bord** dans la barre d’actions.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Cliquez sur le bouton **EmergencyChannel** de la **StoreSchedule** tableau de bord et cliquez sur **Modifier l’affectation**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Définissez la **Priorité** de **EmergencyChannel** sur **3** depuis la boîte de dialogue **Attribution de canaux** et cliquez sur **Enregistrer**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. Lorsque la priorité du canal est mise à jour, tous les lecteurs AEM Screens affichent la variable **EmergencyChannel** contenu.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusion {#conclusion}

La variable **EmergencyChannel** continue d’afficher son contenu jusqu’à ce que l’auteur de contenu réinitialise la valeur de priorité sur 1.

Lorsque l’auteur du contenu reçoit les instructions indiquant que l’urgence a été effacée, il doit mettre à jour la priorité de la variable **MainAdChannel**. Cela entraîne la reprise de la lecture normale.
