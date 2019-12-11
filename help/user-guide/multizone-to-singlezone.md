---
title: Cas d’utilisation des transitions MultiZone vers SingleZone
description: Suivez cette page pour en savoir plus sur le cas d’utilisation de MultiZone vers SingleZone Transitions.
seo-description: Cas d’utilisation des transitions MultiZone vers SingleZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 0cae7c19759fe3418a13ab2d7cc68f1b220f397d

---


# Transition Zone multiple vers Zone unique {#multizone-to-singlezone-use-case}


## Description du cas d’utilisation {#use-case-description}

Cette section décrit un exemple de cas d’utilisation qui met l’accent sur la configuration d’un canal de mise en page multizone qui alterne avec un canal de mise en page de zone unique. Chaque canal comporte un séquencement des fichiers image/vidéo.

### Conditions préalables {#preconditions}

Avant de commencer cette utilisation, assurez-vous de comprendre comment :

* **[Création et gestion des canaux](managing-channels.md)**
* **[Création et gestion des emplacements](managing-locations.md)**
* **[Création et gestion de calendriers](managing-schedules.md)**
* **[Enregistrement de périphérique](device-registration.md)**

### Acteurs principaux {#primary-actors}

Auteurs de contenu

## Setting up the Project {#setting-up-the-project}

Pour configurer un projet, procédez comme suit :

1. Créez un projet AEM Screens nommé **ChannelTransition**, comme illustré ci-dessous.



1. **Création d’un canal d’écran partagé**

   1. Sélectionnez le dossier **Canaux** , puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant de création d’un canal.
   1. Sélectionnez **Gauche-L Barre fractionnée Canal** d’écran dans l’assistant et créez le canal intitulé **MultiZoneLayout**.



   1. Select the **MultiZoneLayout** channel and click **Edit** from the action bar to open the editor. Faites glisser les ressources vers chacune des zones. L’exemple suivant montre une vidéo, une image et une bannière de texte dans la chaîne, comme illustré ci-dessous.


1. **Création d’un canal 2X2 avec quatre images**

   1. Sélectionnez le dossier **Canaux** , puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant de création d’un canal.

   1. Sélectionnez le modèle de canal **d’écran partagé** 2X2 dans l’assistant et créez le canal intitulé **Deux canaux**.


   1. Sélectionnez le canal, puis cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur et faites glisser quatre images (quatre zones différentes) sur ce canal, comme illustré ci-dessous.


1. **Création d’un canal d’écran partagé 1X2 avec deux images**

   1. Sélectionnez le dossier **Canaux** , puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant de création d’un canal.

   1. Sélectionnez **1X2 Scinder le modèle de canal** d’écran dans l’assistant et créez le canal intitulé **OnebyTwoChannel**.


   1. Sélectionnez le canal, puis cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur et faites glisser deux images (deux zones différentes) sur ce canal, comme illustré ci-dessous.


1. **Création d’un canal avec une vidéo plein écran**

   1. Sélectionnez le dossier **Canaux** , puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant de création d’un canal.

   1. Sélectionnez le modèle Canal **de** séquence dans l’assistant et créez le canal intitulé **FullScreensVideo**.


   1. Sélectionnez le canal, puis cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur et faire glisser le composant vidéo sur ce canal, puis ajoutez la vidéo de votre choix, comme illustré ci-dessous.

