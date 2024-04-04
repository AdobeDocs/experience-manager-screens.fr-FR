---
title: Enregistrement d’appareils
seo-title: Device Registration
description: Cette page décrit le processus d’enregistrement des appareils dans un projet AEM Screens.
seo-description: This page describes the device registration process in an AEM Screens project.
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
feature: Administering Screens, Device Registration
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 85%

---

# Enregistrement d’appareils {#device-registration}

La page suivante décrit le processus d’enregistrement des appareils dans un projet AEM Screens.

## Enregistrement d’un appareil {#registering-a-device}

Le processus d’enregistrement des appareils est effectué sur 2 machines distinctes :

* L’appareil à enregistrer, par exemple l’affichage du message
* Serveur AEM utilisé pour enregistrer votre appareil

>[!NOTE]
>
>Une fois que vous avez téléchargé le dernier lecteur Windows (*.exe*), à partir de la page de téléchargement [du lecteur AEM 6.4](https://download.macromedia.com/screens/), suivez les étapes du lecteur pour terminer l’installation ad hoc :
>
>1. Appuyez longuement dans l’angle supérieur gauche pour ouvrir le panneau d’administration.
>1. Accédez à **Configuration** à partir du menu d’actions de gauche, saisissez l’adresse de l’emplacement de l’instance AEM dans **Serveur** et cliquez sur **Enregistrer**.
>1. Cliquez sur le lien **Enregistrement** dans le menu d’actions de gauche et suivez les étapes ci-dessous pour terminer le processus d’enregistrement de l’appareil.
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Sur votre appareil, démarrez le lecteur AEM Screens. L’interface utilisateur d’enregistrement s’affiche.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. Dans AEM, accédez au dossier **Appareils** de votre projet.

   >[!NOTE]
   >
   >Pour en savoir plus sur la création d’un nouveau projet pour Screens dans le tableau de bord AEM, voir [Création et gestion d’un projet Screens](creating-a-screens-project.md).

1. Appuyez/cliquez sur le bouton **Gestionnaire d’appareils** dans la barre d’actions.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Appuyez/cliquez sur le bouton **Enregistrement d’appareil** en haut à droite.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Sélectionnez l’appareil requis (comme pour l’étape 1) et appuyez/cliquez sur **Enregistrer l’appareil**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. Dans AEM, attendez que l’appareil envoie son code d’enregistrement.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. Sur votre appareil, vérifiez le **code d’enregistrement**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Si le **Code d’enregistrement** est le même sur les deux machines, appuyez/cliquez sur le bouton **Valider** dans AEM, comme indiqué à l’étape (6).
1. Saisissez le nom souhaité pour l’appareil, puis cliquez sur **Enregistrer**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Appuyez/cliquez sur **Terminer** pour terminer le processus d’enregistrement.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >L’option **Enregistrer nouveau** vous permet d’enregistrer un nouvel appareil.
   >
   >Le bouton **Attribuer l’affichage** permet d’ajouter directement l’appareil à un affichage.

   Si vous cliquez sur **Terminer**, vous devez attribuer l’appareil à un affichage.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Pour en savoir plus sur la création et la gestion d’un affichage pour votre projet Screens, consultez [Création et gestion des affichages](managing-displays.md).

### Attribution d’un appareil à un affichage {#assigning-device-to-a-display}

Si vous n’avez pas attribué l’appareil à un affichage, procédez comme suit pour attribuer l’appareil à un affichage dans votre projet AEM Screens :

1. Sélectionnez l’appareil et cliquez sur **Attribuer l’appareil** dans la barre d’actions.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Sélectionnez le chemin d’accès de l’affichage dans **Chemin de configuration de l’écran/appareil**.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Cliquez sur **Attribuer** lorsque vous sélectionnez le chemin.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Cliquez sur **Terminer** une fois que l’appareil a été attribué, comme illustré dans la figure ci-dessous.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   De plus, vous pouvez afficher le tableau de bord de l’affichage en cliquant sur **Terminer**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Recherche d’un appareil à partir du gestionnaire d’appareils {#search-device}

Une fois que vous avez enregistré des appareils sur votre lecteur, vous pouvez les afficher depuis l’interface utilisateur du Gestionnaire d’appareils.

1. Accédez à l’interface utilisateur du Gestionnaire de périphériques à partir de votre projet AEM Screens, par exemple : **DemoScreens** > **Périphériques**.

1. Sélectionnez le dossier **Appareils** et cliquez sur **Gestionnaire d’appareils** dans la barre d’actions.

   ![image](/help/user-guide/assets/device-manager/device-manager-1.png)

1. La liste des appareils enregistrés s’affiche.

1. Si vous disposez d’une longue liste d’appareils enregistrés, vous pouvez désormais effectuer une recherche à l’aide de l’icône de recherche de la barre d’actions.

   ![image](/help/user-guide/assets/device-manager/device-manager-2.png)

   Ou,

   Cliquez sur `/` (barre oblique) pour appeler la fonctionnalité de recherche.

   ![image](/help/user-guide/assets/device-manager/device-manager-3.png)


### Limites de la fonctionnalité de recherche {#limitations}

* L’utilisateur pourra rechercher n’importe quel mot existant dans l’*ID d’appareil* ou le *Nom de l’appareil*.

  >[!NOTE]
  >Il est recommandé de créer les noms d’appareils à l’aide de plusieurs mots, tels que *Boston Store Lobby*, plutôt qu’en un seul, *BostonStoreLobby*.

* Si vous créez des noms d’appareil tels que *Boston Store Lobby*, il est possible de rechercher n’importe quel mot *boston*, *store* ou *lobby*. Par contre, si le nom d’appareil est *BostonStoreLobby*, une recherche sur *boston* n’affichera pas les résultats.

* Le caractère générique `*` est pris en charge pour la recherche. Si vous souhaitez rechercher tous les appareils dont le nom commence par *boston*, vous pouvez utiliser *boston**.

* Si le nom de l’appareil est *BostonStoreLobby* et que vous recherchez *boston*, le résultat ne sera pas renvoyé. Par contre, si vous utilisez *boston** dans vos critères de recherche, le résultat sera renvoyé.

## Restrictions relatives à l’enregistrement d’appareils {#limitations-on-device-registration}

Les restrictions de mot de passe utilisateur à l’échelle du système peuvent entraîner un échec de l’enregistrement du périphérique. L’enregistrement du périphérique utilise un mot de passe généré de manière aléatoire pour créer l’utilisateur du périphérique.

Si le mot de passe est limité par la variable *AuthorizableActionProvider* , la création de l’utilisateur du périphérique peut échouer.

>[!NOTE]
>
>Le mot de passe aléatoire généré actuellement est composé de 36 caractères ASCII, compris entre 33 et 122 (inclut presque tous les caractères spéciaux).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur le lecteur AEM Screens, voir [Lecteur AEM Screens](working-with-screens-player.md).
