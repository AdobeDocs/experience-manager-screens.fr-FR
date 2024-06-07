---
title: Cas d’utilisation des transitions Multizone vers Zone unique
description: Consultez cette page pour en savoir plus sur le cas d’utilisation Transitions Multizone vers Zone unique.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: ht
source-wordcount: '404'
ht-degree: 100%

---

# Transition Multizone vers Zone unique {#multizone-to-singlezone-use-case}

## Description du cas d’utilisation {#use-case-description}

Cette section décrit un exemple de cas d’utilisation qui met l’accent sur la configuration d’un canal de disposition multizone qui alterne avec un canal de disposition à zone unique. Le canal multizone comporte des ressources image/vidéo de séquencement et indique comment configurer un projet qui alterne entre multizone et zone unique.

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

   1. Cliquez sur le dossier **Canaux**, puis sur **Créer** dans la barre d’actions pour ouvrir l’assistant afin de créer un canal.
   1. Cliquez sur **Canal d’écran partagé barre en L à gauche** dans l’assistant et créez le canal intitulé **MultiZoneLayout**.
   1. Ajoutez du contenu au canal. Faites glisser les ressources vers chacune des zones. L’exemple suivant illustre un canal **MultiZoneLayout** comprenant une vidéo, une image et une bannière de texte (dans une séquence incorporée), comme illustré ci-dessous.

   ![ressource](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Pour en savoir plus sur la création d’une disposition multizone dans votre canal, reportez-vous à [Disposition multizone](multi-zone-layout-aem-screens.md).


1. Créez un autre canal intitulé **TakeoverChannel** dans votre dossier **Channels** (Canaux).

   ![ressource](assets/mz-to-sz3.png)

1. Cliquez sur **Modifier** dans la barre d’actions pour ajouter du contenu à ce canal. Ajoutez à ce canal un composant **Canal** et une ressource image vers lesquels vous souhaitez basculer, comme illustré ci-dessous :

   ![Ressource](assets/mz-to-sz4.png)

1. Ouvrez les paramètres du composant Canal et faites pointer ce composant sur le canal **MultiZoneLayout** que vous avez créé à l’*étape 2*.

   ![Ressource](assets/mz-to-sz5.png)

1. Définissez la durée dans le champ **Séquence** sur **10 000 ms**.

   ![ressource](assets/mz-to-sz6.png)

1. De même, ouvrez les paramètres de l’image (ressource que vous avez ajoutée) et définissez sa durée dans le champ **Séquence** sur **3 000 millisecondes**.

   ![ressource](assets/mz-to-sz7.png)

## Vérification de l’aperçu {#checking-the-preview}

Vous pouvez afficher la sortie souhaitée à partir du lecteur ou simplement en sélectionnant **Aperçu** dans l’éditeur.

La sortie montre comment une disposition multizone est lue pendant *1 000 millisecondes*. Ensuite, elle passe à une disposition à zone unique dont la durée de lecture est *3 000 millisecondes*. Enfin, elle revient à la disposition multizone.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Vous pouvez personnaliser votre transition de canal (de la disposition multizone à la disposition à zone unique ou vice versa), selon vos besoins.
