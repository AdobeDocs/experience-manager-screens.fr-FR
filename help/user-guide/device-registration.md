---
title: Enregistrement d’appareils
description: Découvrez le processus d’enregistrement des périphériques dans un projet AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens, Device Registration
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 36%

---

# Enregistrement d’appareils {#device-registration}

La page suivante décrit le processus d’enregistrement des appareils dans un projet AEM Screens.

## Enregistrement d’un appareil {#registering-a-device}

Le processus d’enregistrement des périphériques est effectué sur deux machines distinctes :

* L’appareil à enregistrer, par exemple l’affichage du message
* Serveur AEM utilisé pour enregistrer votre appareil

>[!NOTE]
>
>Après avoir téléchargé le dernier lecteur Windows (*.exe*), depuis [Téléchargements du lecteur AEM 6.4](https://download.macromedia.com/screens/) , suivez les étapes du lecteur pour terminer l’installation ad hoc :
>
>1. Appuyez longuement dans le coin supérieur gauche pour ouvrir le panneau d’administration.
>1. Accédez à **Configuration** à partir du menu d’actions de gauche, saisissez l’adresse de l’emplacement de l’instance AEM dans **Serveur** et cliquez sur **Enregistrer**.
>1. Cliquez sur le bouton **Enregistrement** à partir du menu d’actions de gauche et des étapes ci-dessous pour terminer le processus d’enregistrement du périphérique.
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Sur votre appareil, démarrez le lecteur AEM Screens. L’interface utilisateur d’enregistrement s’affiche.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. Dans AEM, accédez au dossier **Appareils** de votre projet.

   >[!NOTE]
   >
   >Pour plus d’informations sur la création d’un projet pour Screens dans le tableau de bord AEM, voir [Création et gestion de projet Screens](creating-a-screens-project.md).

1. Cliquez sur le bouton **Gestionnaire de périphériques** dans la barre d’actions.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Cliquez sur le bouton **Enregistrement de périphérique** en haut à droite.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Cliquez sur le périphérique requis (comme pour l’étape 1), puis cliquez sur **Enregistrer le périphérique**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. Dans AEM, attendez que l’appareil envoie son code d’enregistrement.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. Sur votre appareil, vérifiez le **code d’enregistrement**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Si la variable **Code d’enregistrement** est identique sur les deux machines, cliquez sur **Valider** dans AEM, comme indiqué à l’étape (6).
1. Saisissez le nom souhaité pour l’appareil, puis cliquez sur **Enregistrer**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Cliquez sur **Terminer** pour terminer le processus d’enregistrement.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >La variable **Enregistrer nouveau** vous permet d’enregistrer un nouveau périphérique.
   >
   >Le bouton **Attribuer l’affichage** permet d’ajouter directement l’appareil à un affichage.

   Cliquez sur **Terminer**, affectez le périphérique à un affichage.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Pour en savoir plus sur la création et la gestion d’un affichage pour votre projet Screens, voir [Création et gestion des affichages](managing-displays.md).

### Attribution d’un appareil à un affichage {#assigning-device-to-a-display}

Si vous n’avez pas attribué l’appareil à un affichage, procédez comme suit pour attribuer l’appareil à un affichage dans votre projet AEM Screens :

1. Cliquez sur le périphérique, puis sur **Attribuer le périphérique** dans la barre d’actions.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Cliquez sur le chemin de l’affichage dans **Chemin de configuration de l’affichage/du périphérique**.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Cliquez sur **Attribuer** lorsque vous cliquez sur le chemin.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Cliquez sur **Terminer** une fois que l’appareil a été attribué, comme illustré dans la figure ci-dessous.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Vous pouvez également afficher le tableau de bord de l’affichage en sélectionnant **Terminer**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Recherche d’un appareil à partir du gestionnaire d’appareils {#search-device}

Lorsque vous avez enregistré des périphériques sur votre lecteur, vous pouvez les afficher dans l’interface utilisateur du Gestionnaire de périphériques.

1. Accédez à l’interface utilisateur du Gestionnaire de périphériques à partir de votre projet AEM Screens, par exemple : **DemoScreens** > **Périphériques**.

1. Cliquez sur le bouton **Périphériques** et cliquez sur **Gestionnaire de périphériques** dans la barre d’actions.

   ![image](/help/user-guide/assets/device-manager/device-manager-1.png)

1. La liste des appareils enregistrés s’affiche.

1. Si vous disposez d’une longue liste d’appareils enregistrés, vous pouvez désormais effectuer une recherche à l’aide de l’icône de recherche de la barre d’actions.

   ![image](/help/user-guide/assets/device-manager/device-manager-2.png)

   Ou,

   Sélectionner `/` (barre oblique) pour appeler la fonctionnalité de recherche.

   ![image](/help/user-guide/assets/device-manager/device-manager-3.png)


### Limites de la fonctionnalité de recherche {#limitations}

* L’utilisateur peut rechercher n’importe quel mot existant dans la variable *ID de périphérique* ou *Nom de l’appareil*.

  >[!NOTE]
  >Il est recommandé de créer les noms d’appareils à l’aide de plusieurs mots, tels que *Boston Store Lobby*, plutôt qu’en un seul, *BostonStoreLobby*.

* Si vous créez des noms d’appareils tels que *Lobby du magasin Boston*, il recherche n’importe quel mot. *boston*, *store*, ou *lobby*. Cependant, si le nom de l’appareil est *BostonStoreLobby*, puis en recherchant *boston* n’affiche aucun résultat.

* Le caractère générique `*` est pris en charge pour la recherche. Si vous souhaitez trouver tous les périphériques dont le nom commence par *boston*, vous pouvez utiliser *boston**.

* Si le nom de l’appareil est *BostonStoreLobby* et la recherche *boston* ne renvoie pas le résultat, puis utilise *boston** dans vos critères de recherche renvoie le résultat.

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

### Autres ressources {#additional-resources}

Pour en savoir plus sur le lecteur AEM Screens, voir [Lecteur AEM Screens](working-with-screens-player.md).
