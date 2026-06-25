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
TQID: https://experienceleague.adobe.com/orHLShhCxLB8T9Dm8Vvihvy7GNGrmJQZt8toCPs5c3k
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: d8e42837-75d7-4e4e-accd-d0cdd8efe1f4id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 710
ht-degree: 86%

---

# Création et gestion des affichages {#creating-and-managing-displays}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Un affichage est un groupe virtuel d’écrans positionnés les uns à côté des autres. L’affichage est généralement permanent par rapport à une installation. Les auteurs et autrices utilisent ce contenu d’objet et s’y réfèrent toujours en tant qu’affichage logique plutôt qu’à leurs équivalents physiques.

Lorsque vous avez créé un emplacement, vous devez créer un affichage pour cet emplacement.

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
1. Cliquez sur votre dossier d’emplacements, puis sur **Créer** en regard de l’icône « + » dans la barre d’actions.
1. Cliquez sur **Affichage** à partir de l’assistant **Créer**, puis sur **Suivant**.
1. Saisissez le **Nom** et le **Titre** de l’emplacement de l’affichage.
1. Dans l’onglet **Affichage**, sélectionnez les détails de la mise en page. Choisissez la **résolution** souhaitée, par exemple, **Full HD**. Choisissez le nombre d’appareils horizontalement et verticalement.
1. Cliquez sur **Créer**.

L’affichage (*StoreDisplay*) est créé et ajouté à l’affichage de l’emplacement (*SanJose*).

![Affichage](assets/display.gif)

Lorsque l’affichage est en place, l’étape suivante consiste à créer une configuration d’appareil pour cet affichage.

>[!NOTE]
>
>**Prochaine étape** :
>
>Lorsque vous créez un affichage pour votre emplacement, attribuez-lui un canal pour utiliser le contenu.
>
>Voir la section [Attribuer des canaux](channel-assignment.md) pour savoir comment attribuer un canal à l’affichage.

## Création d’une configuration d’appareil {#creating-a-new-device-config}

Une configuration d’appareil fonctionne comme un espace réservé pour un appareil de signalétique numérique qui n’est pas encore installé.

1. Accédez à l’affichage souhaité, par exemple `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Cliquez sur votre dossier d’affichage, puis sur **Afficher le tableau de bord** dans la barre d’actions.
1. Cliquez sur **+ Ajouter la configuration de l’appareil** en haut à droite du panneau **Appareils**.

1. Cliquez sur le modèle **Configuration de l’appareil** comme modèle requis, puis sur **Suivant**.

1. Saisissez les propriétés demandées, puis cliquez sur **Créer**.

La configuration de l’appareil est créée et ajoutée à l’affichage en cours (dans la démonstration suivante, la nouvelle configuration de l’appareil s’appelle *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>Lorsque vous avez ajouté la configuration d’appareil à votre affichage dans l’emplacement, l’étape suivante est d’attribuer un canal à votre affichage.
>
>Comme illustré ci-dessous, si la configuration de l’appareil est affichée comme non attribuée dans le panneau **APPAREILS**, aucun canal n’est attribué à cette configuration de l’appareil.
>
>Vous devez d’abord comprendre comment créer et gérer des canaux. Voir [Création et gestion des canaux](managing-channels.md) pour en savoir plus.

![chlimage_1-9](assets/chlimage_1-9.png)

## Tableau de bord des affichages {#display-dashboard}

Le tableau de bord des affichages vous fournit différents panneaux pour la gestion des appareils d’affichage. Il vous permet également de configurer votre appareil.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Vous pouvez cliquer sur les listes du tableau de bord et déclencher des actions en masse sur les éléments, au lieu de parcourir chaque élément individuellement.
>
>Par exemple, l’image suivante montre comment cliquer sur plusieurs canaux à partir du tableau de bord d’affichage.

![cqdoc9456](assets/cqdoc9456.gif)

### Panneau Informations d’affichage {#display-information-panel}

Le panneau **INFORMATIONS D’AFFICHAGE** affiche les propriétés de l’affichage.

Clic (**...**) dans le coin supérieur droit du panneau **INFORMATIONS D’AFFICHAGE** afin que vous puissiez afficher les propriétés et prévisualiser l’affichage.


#### Afficher des propriétés {#viewing-properties}

Cliquez sur **Propriétés** pour pouvoir afficher ou modifier les propriétés de votre affichage.

Vous pouvez également régler la valeur du retardateur d’événements pour votre canal interactif sous l’onglet **Affichage**. Par défaut, cette valeur est définie sur *300 secondes*.

Utilisez **CRXDE Lite** pour accéder à la propriété **idleTimeout**, à savoir `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`.


### Panneau Canaux attribués {#assigned-channels-panel}

Le panneau **CANAUX ATTRIBUÉS** affiche les canaux attribués à cet appareil.


### Panneau Appareils {#devices-panel}

Le panneau **APPAREILS** fournit des informations sur les configurations des appareils.

Clic (**...**) dans le coin supérieur droit du panneau **APPAREILS** afin que vous puissiez ajouter des configurations d’appareils et mettre à jour des appareils.

Cliquez également sur la configuration de l’appareil pour afficher les propriétés, attribuer un appareil ou le supprimer.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Étapes suivantes {#the-next-steps}

Lorsque vous avez créé un affichage pour votre emplacement, attribuez-lui un canal.

Reportez-vous à la section [Attribution des canaux](channel-assignment.md) pour plus de détails.
