---
title: Cas d’utilisation des transitions MultiZone vers SingleZone
description: Suivez cette page pour en savoir plus sur le cas d’utilisation de MultiZone vers SingleZone Transitions.
seo-description: Cas d’utilisation des transitions MultiZone vers SingleZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6f770734941635a0cd404986c259022137355af3

---


# Transition Zone multiple vers Zone unique {#multizone-to-singlezone-use-case}


## Description du cas d’utilisation {#use-case-description}

Cette section décrit un exemple de cas d’utilisation qui met l’accent sur la configuration d’un canal de mise en page à zones multiples qui alterne avec un canal de mise en page à zone unique. Le canal multi-zone comporte un séquencement des fichiers image/vidéo et montre comment configurer un projet qui évolue de zones multiples à zones simples et vice versa.

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

1. Créez un projet AEM Screens nommé **TakeoverLoop**, comme illustré ci-dessous.

   ![ressource](assets/mz-to-sz1.png)


1. **Création d’un canal d’écran multi-zone**

   1. Sélectionnez le dossier **Canaux** , puis cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant de création d’un canal.
   1. Sélectionnez **Gauche-L Barre fractionnée Canal** d’écran dans l’assistant et créez le canal intitulé **MultiZoneLayout**.
   1. Ajoutez du contenu au canal. Faites glisser les ressources vers chacune des zones. L’exemple suivant illustre un canal **MultiZoneLayout** comprenant une vidéo, une image et une bannière de texte (dans une séquence incorporée), comme illustré ci-dessous.
   ![ressource](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Pour en savoir plus sur la création d’une mise en page à zones multiples dans votre canal, consultez Mise en page [à zones](multi-zone-layout-aem-screens.md)multiples.


1. Créez un autre canal intitulé **TakeoverChannel** dans votre dossier **Canaux** .

   ![ressource](assets/mz-to-sz3.png)

1. Cliquez sur **Modifier** dans la barre d’actions pour ajouter du contenu à ce canal. Ajoutez un composant **Canal** et un fichier d’image vers lequel vous souhaitez passer, à ce canal, comme illustré dans la figure ci-dessous :

   ![ressource](assets/mz-to-sz4.png)

1. Ouvrez les paramètres du composant Canal et pointez-le sur le canal **MultiZoneLayout** que vous avez créé à l’ *étape 2*.

   ![ressource](assets/mz-to-sz5.png)

1. Définissez la durée du champ **Séquence** sur **1 000 ms**.

   ![ressource](assets/mz-to-sz6.png)

1. De même, ouvrez les paramètres de l’image (fichier ajouté) et définissez sa durée du champ **Séquence** sur **3 000 ms**.

   ![ressource](assets/mz-to-sz7.png)

## Vérification de l’aperçu {#checking-the-preview}

Vous pouvez afficher la sortie souhaitée à partir du lecteur ou simplement en cliquant sur l&#39; **Aperçu** dans l&#39;éditeur.

La sortie montre comment une disposition multi-zone est lue pendant *10 000 ms* , puis passe à une disposition à zone unique dont la durée de lecture est de *3 000 ms* , puis revient à la disposition multi-zone.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Vous pouvez personnaliser votre transition de canal (de la mise en page multi-zone à une seule zone ou vice versa), selon vos besoins.