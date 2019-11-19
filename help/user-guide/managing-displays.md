---
title: Création et gestion des affichages
seo-title: Gestion des affichages
description: Lisez cette page pour en savoir plus sur la création d’un affichage et d’une configuration de périphérique. Vous y trouverez également des informations sur le tableau de bord des affichages.
seo-description: Lisez cette page pour en savoir plus sur la création d’un affichage et d’une configuration de périphérique. Vous y trouverez également des informations sur le tableau de bord des affichages.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Création et gestion des affichages {#creating-and-managing-displays}

Un affichage est un groupe virtuel d’écrans généralement positionnés les uns à côté des autres. L’affichage est en général permanent dans une installation. C’est l’objet avec lequel les auteurs de contenu travaillent. Ils le désignent par ailleurs toujours par le terme d’affichage logique pour le distinguer de ses équivalents physiques.

Une fois que vous avez créé un emplacement, vous devez créer un affichage pour cet emplacement.

Vous découvrirez dans cette page comment créer et gérer des affichages pour Screens.

**Conditions préalables**:

* [Configuration et déploiement de Screens](configuring-screens-introduction.md)
* [Création et gestion d’écrans](creating-a-screens-project.md)
* [Création et gestion des canaux](managing-channels.md)
* [Création et gestion des emplacements](managing-locations.md)

## Création d’un affichage {#creating-a-new-display}

>[!NOTE]
>
>Vous devez créer un emplacement avant de créer un affichage. To see how to create a location, see [Create and Manage Locations](managing-locations.md) for more information.

Pour créer un affichage dans votre emplacement, suivez les étapes ci-dessous.

1. Navigate to the appropriate location, for example `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Sélectionnez votre dossier d’emplacements, puis appuyez ou cliquez sur **Créer** en regard de l’icône « + » dans la barre d’actions. Un assistant s’ouvre.
1. Select **Display** from the **Create** wizard and click **Next**.

1. Enter **Name** and **Title** for your display location.

1. Dans l’onglet **Affichage**, sélectionnez les détails de la mise en page. Choose the desired **Resolution** (example as, as **Full HD**). De plus, vous pouvez choisir le nombre de périphériques horizontalement et verticalement.

1. Cliquez sur **Créer**.

The display (*StoreDisplay*) is created and added to the location (*SanJose*).

![afficher](assets/display.gif)

Une fois que l’affichage est en place, l’étape suivante est de créer une configuration de périphérique pour cet affichage. Suivez la section ci-dessous pour créer une configuration de périphérique.

>[!NOTE]
>
>**Étape suivante** :
>
>Une fois que vous avez créé un affichage pour votre emplacement, vous devez attribuer un canal à votre affichage de façon à exploiter le contenu.
>
>See [Assign Channels](channel-assignment.md) section to learn how to assign a channel to the display.

## Création d’une configuration de périphérique {#creating-a-new-device-config}

Une configuration de périphérique fonctionne comme un espace réservé pour un périphérique d’affichage numérique qui n’est pas encore installé.

Suivez les étapes ci-dessous pour créer une configuration de périphérique.

1. Accédez à l’affichage approprié, par exemple `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Sélectionnez votre dossier d’affichage et appuyez ou cliquez ensuite sur **Afficher le tableau de bord** dans la barre d’actions.
1. Tap/click the **+ Add Device Config** on the top right of the **Devices** panel.

1. Select the **Device Config** as the required template as and tap/click **Next**.

1. Saisissez les propriétés demandées, puis appuyez ou cliquez sur **Créer**.

The device config is created and added to the current display (in the following demonstration, the new device config is *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

Une fois que vous avez ajouté la configuration de périphérique à votre affichage dans l’emplacement, l’étape suivante est d’attribuer un canal à votre affichage.

>[!NOTE]
>
>Une fois que vous avez ajouté la configuration de périphérique à votre affichage dans l’emplacement, l’étape suivante est d’attribuer un canal à votre affichage.
>
>As shown in the figure below, if the device config is displayed as unassigned in the **DEVICES** pannel, if no channel is assigned to that particular device config.
>
>Vous devez d’abord comprendre comment créer et gérer des canaux. Voir [Création et gestion des canaux](managing-channels.md) pour en savoir plus.

![chlimage_1-9](assets/chlimage_1-9.png)

## Tableau de bord des affichages {#display-dashboard}

Le tableau de bord des affichages présente plusieurs panneaux pour gérer les périphériques d’affichage et la configuration de votre périphérique.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Vous pouvez sélectionner les listes de tableaux de bord et déclencher des actions en masse sur des éléments, au lieu de passer par chaque élément individuellement.
>
>Par exemple, l’illustration suivante montre comment vous pouvez sélectionner plusieurs canaux à partir du tableau de bord.

![cqdoc9456](assets/cqdoc9456.gif)

### Panneau Informations d’affichage {#display-information-panel}

Le panneau **INFORMATIONS D’AFFICHAGE** affiche les propriétés de l’affichage.

Click on the (**...**) in the top right corner in the **DISPLAY INFORMATION **panel to view the properties and preview the display.

![chlimage_1-10](assets/chlimage_1-10.png)

#### Affichage des propriétés {#viewing-properties}

Cliquez sur **Propriétés** pour afficher ou modifier les propriétés de votre affichage.

Additionally, you can adjust the event timer value for your interactive channel in **Idle timeout **property under **Display** tab. Par défaut, cette valeur est définie sur *300 secondes*.

Use **CRXDE Lite**, to access the **idleTimeout** property, that is, `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .

![chlimage_1-1](assets/chlimage_1-1.gif)

### Panneau Canaux attribués {#assigned-channels-panel}

Le panneau **CANAUX ATTRIBUÉS** affiche les canaux attribués à ce périphérique.

![chlimage_1-11](assets/chlimage_1-11.png)

### Panneau Périphériques {#devices-panel}

Le panneau **PÉRIPHÉRIQUES** fournit des informations sur les configurations de périphérique.

Click on the (**...**) in the top right corner in the **DEVICES **panel to add device configs and update devices.

![chlimage_1-12](assets/chlimage_1-12.png)

De plus, cliquez sur la configuration du périphérique pour afficher les propriétés, affecter un périphérique ou le supprimer complètement.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Étapes suivantes {#the-next-steps}

Une fois que vous avez créé un affichage pour votre emplacement, vous devez lui attribuer un canal.

See [Assign Channels](channel-assignment.md) for more details.
