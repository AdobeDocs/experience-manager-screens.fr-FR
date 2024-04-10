---
title: Création et gestion des affichages
description: Découvrez comment créer un affichage et une configuration de périphérique dans AEM Screens. En savoir plus sur le tableau de bord des affichages.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 46%

---

# Création et gestion des affichages {#creating-and-managing-displays}

Un affichage est un groupe virtuel d’écrans positionnés les uns à côté des autres. L&#39;affichage est permanent par rapport à une installation. Il s’agit de l’objet avec lequel les auteurs de contenu travaillent et font toujours référence à comme affichage logique plutôt qu’à leurs parties de compteur physiques.

Une fois que vous avez créé un emplacement, vous devez créer un affichage pour celui-ci.

Cette page présente la création et la gestion des affichages pour Screens.

**Conditions préalables** :

* [Configuration et déploiement de Screens](configuring-screens-introduction.md)
* [Création et gestion de projet Screens](creating-a-screens-project.md)
* [Création et gestion des canaux](managing-channels.md)
* [Création et gestion des emplacements](managing-locations.md)

## Création d’un affichage {#creating-a-new-display}

>[!NOTE]
>
>Créez un emplacement avant de créer un affichage. Voir [Création et gestion des emplacements](managing-locations.md) pour plus d’informations.

1. Accédez à l’emplacement souhaité, par exemple `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Sélectionnez votre dossier d’emplacement et sélectionnez **Créer** en regard de l’icône plus dans la barre d’actions.
1. Sélectionner **Affichage** de la **Créer** assistant, puis sélectionnez **Suivant**.
1. Saisissez le **nom** et le **titre** de l’emplacement de l’affichage.
1. Dans l’onglet **Affichage**, sélectionnez les détails de la mise en page. Choisissez la **Résolution**, par exemple **Full HD**. Sélectionnez le nombre de périphériques horizontalement et verticalement.
1. Sélectionnez **Créer**.

L’affichage (*StoreDisplay*) est créé et ajouté à l’affichage de l’emplacement (*SanJose*).

![Affichage](assets/display.gif)

Lorsque l’affichage est en place, l’étape suivante consiste à créer une configuration de périphérique pour cet affichage particulier.

>[!NOTE]
>
>**La prochaine étape** :
>
>Lorsque vous créez un affichage pour votre emplacement, vous devez lui attribuer un canal pour utiliser le contenu.
>
>Voir [Attribution de canaux](channel-assignment.md) pour savoir comment attribuer un canal à l’affichage.

## Création d’une configuration d’appareil {#creating-a-new-device-config}

Une configuration d’appareil fonctionne comme un espace réservé pour un appareil d’affichage numérique qui n’est pas encore installé.

1. Accédez à l’affichage souhaité, par exemple `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Sélectionnez votre dossier d’affichage et choisissez **Afficher le tableau de bord** dans la barre d’actions.
1. Sélectionner **+ Ajouter la configuration de périphérique** en haut à droite de la **Périphériques** du panneau.

1. Sélectionnez **Configuration de l’appareil** comme modèle requis, puis appuyez/cliquez sur **Suivant**.

1. Saisissez les propriétés demandées, puis appuyez ou cliquez sur **Créer**.

La configuration de l’appareil est créée et ajoutée à l’affichage en cours (dans la démonstration suivante, la nouvelle configuration de l’appareil s’appelle *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

Une fois que vous avez ajouté la configuration d’appareil à votre affichage dans l’emplacement, l’étape suivante est d’attribuer un canal à votre affichage.

>[!NOTE]
>
>Une fois que vous avez ajouté la configuration d’appareil à votre affichage dans l’emplacement, l’étape suivante est d’attribuer un canal à votre affichage.
>
>Comme illustré dans la figure ci-dessous, si la configuration du périphérique s’affiche comme non attribuée dans la variable **APPAREILS** , si aucun canal n’est affecté à cette configuration de périphérique spécifique.
>
>Vous devez d’abord comprendre comment créer et gérer des canaux. Voir [Création et gestion des canaux](managing-channels.md) pour en savoir plus.

![chlimage_1-9](assets/chlimage_1-9.png)

## Tableau de bord des affichages {#display-dashboard}

Le tableau de bord des affichages présente plusieurs panneaux pour gérer les appareils d’affichage et la configuration de votre appareil.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Vous pouvez sélectionner les listes du tableau de bord et déclencher des actions en bloc sur les éléments, au lieu de parcourir chaque élément individuellement.
>
>Par exemple, l’illustration suivante montre comment sélectionner plusieurs canaux à partir du tableau de bord d’affichage.

![cqdoc9456](assets/cqdoc9456.gif)

### Panneau Informations d’affichage {#display-information-panel}

Le panneau **INFORMATIONS D’AFFICHAGE** affiche les propriétés de l’affichage.

Cliquez sur (**..**) dans le coin supérieur droit du **AFFICHAGE DES INFORMATIONS** pour afficher les propriétés et un aperçu de l’affichage.


#### Affichage des propriétés {#viewing-properties}

Cliquez sur **Propriétés** vous pouvez ainsi afficher ou modifier les propriétés de votre affichage.

Vous pouvez également régler la valeur du minuteur d’événement pour votre canal interactif dans **Délai d’inactivité** propriété sous **Affichage** . Par défaut, cette valeur est définie sur *300 secondes*.

Utilisez **CRXDE Lite** pour accéder à la propriété **idleTimeout**, à savoir `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`.


### Panneau Canaux attribués {#assigned-channels-panel}

Le panneau **CANAUX ATTRIBUÉS** affiche les canaux attribués à cet appareil.


### Panneau Appareils {#devices-panel}

Le panneau **APPAREILS** fournit des informations sur les configurations des appareils.

Sélectionnez (**..**) dans le coin supérieur droit du **APPAREILS** afin que vous puissiez ajouter des configurations de périphérique et mettre à jour les périphériques.

Cliquez également sur la configuration du périphérique pour afficher les propriétés, attribuer un périphérique ou le supprimer complètement.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Étapes suivantes {#the-next-steps}

Lorsque vous créez un affichage pour votre emplacement, attribuez-lui un canal.

Reportez-vous à la section [Attribution des canaux](channel-assignment.md) pour plus de détails.
