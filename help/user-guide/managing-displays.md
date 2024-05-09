---
title: Création et gestion des affichages
description: Découvrez comment créer un affichage et une configuration d’appareil dans AEM Screens. Découvrez également le tableau de bord des affichages.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 53%

---

# Création et gestion des affichages {#creating-and-managing-displays}

Un affichage est un groupe virtuel d’écrans positionnés les uns à côté des autres. L’affichage est généralement permanent par rapport à une installation. Il s’agit de l’objet avec lequel les auteurs de contenu travaillent et font toujours référence à comme affichage logique plutôt qu’à leurs parties de compteur physiques.

Lorsque vous créez un emplacement, vous devez créer un affichage pour celui-ci.

Vous découvrirez dans cette page comment créer et gérer des affichages pour Screens.

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
1. Cliquez sur votre dossier d’emplacement, puis sur **Créer** en regard de l’icône plus dans la barre d’actions.
1. Cliquez sur **Affichage** de la **Créer** assistant, puis cliquez sur **Suivant**.
1. Saisissez votre **Nom** et **Titre** pour votre emplacement d’affichage.
1. Dans l’onglet **Affichage**, sélectionnez les détails de la mise en page. Choisissez la **résolution** souhaitée, par exemple, **Full HD**. Choisissez le nombre d’appareils horizontalement et verticalement.
1. Cliquez sur **Créer**.

L’affichage (*StoreDisplay*) est créé et ajouté à l’affichage de l’emplacement (*SanJose*).

![Affichage](assets/display.gif)

Lorsque l’affichage est en place, l’étape suivante consiste à créer une configuration de périphérique pour cet affichage.

>[!NOTE]
>
>**La prochaine étape** :
>
>Lorsque vous créez un affichage pour votre emplacement, attribuez-lui un canal pour utiliser le contenu.
>
>Voir [Attribution de canaux](channel-assignment.md) pour savoir comment attribuer un canal à l’affichage.

## Création d’une configuration d’appareil {#creating-a-new-device-config}

Une configuration d’appareil fonctionne comme un espace réservé pour un appareil de signalétique numérique qui n’est pas encore installé.

1. Accédez à l’affichage souhaité, par exemple `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Cliquez sur votre dossier d’affichage, puis sur **Afficher le tableau de bord** dans la barre d’actions.
1. Cliquez sur **+ Ajouter la configuration de périphérique** en haut à droite de la **Périphériques** du panneau.

1. Cliquez sur le bouton **Configuration du périphérique** comme modèle requis et cliquez sur **Suivant**.

1. Saisissez les propriétés demandées, puis cliquez sur **Créer**.

La configuration de l’appareil est créée et ajoutée à l’affichage en cours (dans la démonstration suivante, la nouvelle configuration de l’appareil s’appelle *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>Lorsqu’une configuration de périphérique est définie sur votre affichage à l’emplacement , l’étape suivante consiste à attribuer un canal à votre affichage.
>
>Comme illustré dans la figure ci-dessous, si la configuration de l’appareil est affichée comme non attribuée dans le panneau **APPAREILS**, aucun canal n’est attribué à cette configuration de l’appareil.
>
>Vous devez avoir une connaissance préalable de la création et de la gestion des canaux. Voir [Création et gestion des canaux](managing-channels.md) pour en savoir plus.

![chlimage_1-9](assets/chlimage_1-9.png)

## Tableau de bord des affichages {#display-dashboard}

Le tableau de bord des affichages vous fournit différents panneaux pour la gestion des périphériques d’affichage. Il vous permet également de configurer votre appareil.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Vous pouvez cliquer sur les listes du tableau de bord et déclencher des actions en bloc sur les éléments, au lieu de parcourir chaque élément individuellement.
>
>Par exemple, l’image suivante montre comment cliquer sur plusieurs canaux à partir du tableau de bord d’affichage.

![cqdoc9456](assets/cqdoc9456.gif)

### Panneau Informations d’affichage {#display-information-panel}

Le panneau **INFORMATIONS D’AFFICHAGE** affiche les propriétés de l’affichage.

Cliquez sur les points de suspension (**...**) dans le coin supérieur droit du panneau **INFORMATIONS SUR L’AFFICHAGE** pour pouvoir afficher les propriétés et un aperçu de l’affichage.


#### Affichage des propriétés {#viewing-properties}

Cliquez sur **Propriétés** pour pouvoir afficher ou modifier les propriétés de votre affichage.

En outre, vous pouvez ajuster la valeur du minuteur d’événement pour votre canal interactif sous le **Affichage** . Par défaut, cette valeur est définie sur *300 secondes*.

Utilisation **CRXDE Lite**, pour accéder au **idleTimeout** , à savoir : `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`.


### Panneau Canaux attribués {#assigned-channels-panel}

Le panneau **CANAUX ATTRIBUÉS** affiche les canaux attribués à cet appareil.


### Panneau Appareils {#devices-panel}

La variable **APPAREILS** Le panneau fournit des informations sur les configurations de l’appareil.

Cliquez sur (**..**) dans le coin supérieur droit du **APPAREILS** afin que vous puissiez ajouter des configurations de périphérique et mettre à jour les périphériques.

Cliquez également sur la configuration de l’appareil pour afficher les propriétés, attribuer un appareil ou le supprimer.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Étapes suivantes {#the-next-steps}

Lorsque vous avez créé un affichage pour votre emplacement, attribuez-lui un canal.

Reportez-vous à la section [Attribution des canaux](channel-assignment.md) pour plus de détails.
