---
title: Cas d’utilisation des transitions Multizone vers Zone unique
description: Consultez cette page pour en savoir plus sur le cas d’utilisation Transitions Multizone vers Zone unique.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
TQID: https://experienceleague.adobe.com/MTRkmtP5J3PL13VZWm9nalthBX-03nu-Z2OsbnMO1Q4
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 467
ht-degree: 90%

---

# Transition Multizone vers Zone unique {#multizone-to-singlezone-use-case}

## Description du cas d’utilisation {#use-case-description}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

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
