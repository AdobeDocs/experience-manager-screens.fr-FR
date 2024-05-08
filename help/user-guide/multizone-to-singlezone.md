---
title: Cas d’utilisation des transitions Multizone vers Zone unique
description: Consultez cette page pour en savoir plus sur le cas d’utilisation Transitions Multizone vers Zone unique .
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 29%

---

# Transition Multizone vers Zone unique {#multizone-to-singlezone-use-case}

## Description du cas d’utilisation {#use-case-description}

Cette section décrit un exemple de cas d’utilisation qui met l’accent sur la configuration d’un canal de disposition multizone qui alterne avec un canal de disposition à zone unique. Le canal multizone comporte des ressources image/vidéo de séquencement et indique comment configurer un projet qui alterne entre plusieurs zones et une seule zone, et inversement.

### Prérequis {#preconditions}

Avant de commencer ce cas d’utilisation, vous devez comprendre comment :

* **[Création et gestion des canaux](managing-channels.md)**
* **[Création et gestion des emplacements](managing-locations.md)**
* **[Création et gestion des planifications](managing-schedules.md)**
* **[Enregistrement d’appareils](device-registration.md)**

### Acteurs principaux {#primary-actors}

Auteurs de contenu

## Configuration du projet {#setting-up-the-project}

Pour configurer un projet, procédez comme suit :

1. Créez un projet AEM Screens appelé **TakeoverLoop**, comme illustré ci-dessous.

   ![ressource](assets/mz-to-sz1.png)


1. **Création d’un canal Screens multizone**

   1. Cliquez sur le bouton **Canaux** et cliquez sur **Créer** depuis la barre d&#39;actions et en ouvrant l&#39;assistant pour créer un canal.
   1. Cliquez sur **Canal d’écran partagé Barre-L gauche** à partir de l’assistant et créez le canal intitulé **MultiZoneLayout**.
   1. Ajoutez du contenu au canal. Faites glisser les ressources vers chacune des zones. L’exemple suivant illustre une **MultiZoneLayout** canal comprenant une vidéo, une image et une bannière de texte (dans une séquence incorporée), comme illustré ci-dessous.

   ![ressource](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Pour en savoir plus sur la création d’une disposition multizone dans votre canal, voir [Disposition multizone](multi-zone-layout-aem-screens.md).


1. Créez un autre canal intitulé **TakeoverChannel** dans votre dossier **Channels** (Canaux).

   ![ressource](assets/mz-to-sz3.png)

1. Cliquez sur **Modifier** depuis la barre d’actions pour ajouter du contenu à ce canal. Ajouter un **Canal** et une ressource image vers laquelle vous souhaitez basculer pour ce canal, comme illustré dans la figure ci-dessous :

   ![ressource](assets/mz-to-sz4.png)

1. Ouvrez les paramètres du composant Canal et faites pointer ce composant sur le canal **MultiZoneLayout** que vous avez créé à l’*étape 2*.

   ![ressource](assets/mz-to-sz5.png)

1. Définissez la durée à partir du **Séquence** champ à **1 000 millisecondes**.

   ![ressource](assets/mz-to-sz6.png)

1. De même, ouvrez les paramètres de l’image (ressource que vous avez ajoutée) et définissez sa durée à partir de la propriété **Séquence** champ à **3 000 millisecondes**.

   ![ressource](assets/mz-to-sz7.png)

## Vérification de l’aperçu {#checking-the-preview}

Vous pouvez afficher la sortie souhaitée à partir du lecteur ou simplement en sélectionnant **Aperçu** à partir de l’éditeur.

La sortie montre comment une disposition multizone est lue pour *1 000 millisecondes* puis passe à une disposition à zone unique dont la durée de lecture est définie *3 000 millisecondes* puis revient à la disposition multizone.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Vous pouvez personnaliser votre transition de canal (de la disposition multizone à la disposition à zone unique ou inversement), selon vos besoins.
