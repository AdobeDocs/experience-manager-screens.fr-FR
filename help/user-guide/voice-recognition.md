---
title: Reconnaissance vocale en AEM Screens
description: La page décrit la fonction de reconnaissance vocale en AEM Screens.
translation-type: tm+mt
source-git-commit: c46cd26f5067468aadf80a822fffce1d5f0b5d9a
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 12%

---


# Reconnaissance vocale en AEM Screens {#voice-recognition}

## Présentation {#overview}

La fonction de reconnaissance vocale permet de modifier le contenu dans un canal AEM Screens piloté par l’interaction vocale.

Un auteur de contenu peut configurer un affichage pour qu’il accepte la voix. Ceci permet à tous les joueurs enregistrés contre l&#39;affichage comprendre le discours. Vous devez activer la reconnaissance vocale pour l’affichage et associer chaque canal à une balise unique pour déclencher une transition de canal.

>[!NOTE]
>Le matériel du lecteur doit prendre en charge la saisie vocale, par exemple un microphone.

>[!IMPORTANT]
> La fonction de reconnaissance vocale est disponible uniquement sur les lecteurs Chrome et Electron.

## Mise en oeuvre de la reconnaissance vocale {#implementing}

La section suivante décrit comment activer et utiliser la fonctionnalité de reconnaissance vocale dans un projet AEM Screens.

### Configuration du projet {#setting-up}

Avant d’utiliser la fonction de reconnaissance vocale, assurez-vous d’avoir un projet et un canal avec du contenu configuré pour votre projet.

1. L’exemple suivant présente un projet de démonstration nommé **VoiceDemo** et trois canaux de séquence **Main**, **ColdDrinks** et **HotDrinks, comme illustré dans la figure ci-dessous.**

   >[!NOTE]
   >
   >Pour savoir comment créer un canal ou ajouter du contenu à un canal, voir [Création et gestion des canaux](/help/user-guide/managing-channels.md).

1. Accédez à chacun des canaux et ajoutez du contenu. Par exemple, accédez à **VoiceDemo** —> **Canaux** —> **Main** et sélectionnez le canal. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur et ajouter du contenu (images/vidéos) selon vos besoins. De même, ajoutez du contenu à **ColdDrinks** et au canal **HotDrinks** .

   Les canaux contiennent maintenant le contenu suivant, comme le montrent les figures ci-dessous.

   **Principal**:

   **ColdDrinks**:

   **HotDrinks**:

### Setting up Tags for Channels {#setting-tags}

Une fois que vous avez ajouté du contenu à vos canaux, vous devez accéder à chacun des canaux et ajouter les balises appropriées qui déclencheraient la reconnaissance vocale.

Pour ajouter des balises à votre canal, procédez comme suit :

1. Accédez à chacun des canaux et ajoutez du contenu. Par exemple, accédez à **VoiceDemo** —> **Canaux** —> **Main** et sélectionnez le canal.

1. Cliquez sur **Propriétés** dans la barre d’actions.

1. Accédez à l’onglet **Concepts de base** et sélectionnez une balise existante dans le champ **Balises** ou créez-en une nouvelle.

1. Cliquez sur **Enregistrer et fermer** une fois que vous avez terminé.


### Assigning Channel to a Display {#channel-assignment}

1. Créez un affichage dans le dossier **Emplacements**, comme illustré ci-dessous.

   >[!NOTE]
   >
   >To learn how to assign a channel to a display, refer to [Creating and Managing Displays](/help/user-guide/managing-displays.md).

1. Attribuez les canaux **Main**, **ColdDrinks** et **HotDrinks** à votre **LobbyDisplay.**


1. Définissez les propriétés suivantes sur chacun des canaux.

   >[!NOTE]
   >
   >To learn how to assign a channel to a display, refer to [Creating and Managing Displays](/help/user-guide/managing-displays.md).

1. Une fois que vous avez attribué des canaux à un affichage, accédez au **LobbyDisplay** et sélectionnez l’affichage. Sélectionnez **Propriétés** dans la barre d’actions.

1. Accédez à l’onglet **Affichage** et activez l’option **Voix activée** sous **Contenu**.

   >[!NOTE]
   >Il est obligatoire d’activer la fonction de reconnaissance vocale à partir de l’écran.

## Affichage du contenu dans Chrome Player {#viewing-content}

Une fois les étapes précédentes terminées, vous pouvez enregistrer votre périphérique chrome et vue la sortie.

Suivez les étapes ci-dessous :

1. Accédez au dossier **Appareils** et cliquez sur **Gestionnaire de périphériques** dans la barre d’actions pour enregistrer les appareils.







