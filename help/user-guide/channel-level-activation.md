---
title: Activation au niveau du canal - Lecture d’un seul événement
seo-title: Activation au niveau du canal - Lecture d’un seul événement
description: Suivez ce guide pour comprendre l’activation au niveau du canal à l’aide de la lecture d’événement unique.
seo-description: Suivez ce guide pour comprendre l’activation au niveau du canal à l’aide de la lecture d’événement unique.
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Activation au niveau du canal - Lecture d’un seul événement {#channel-level-activation-single-event-playback}

L’activation au niveau du canal couvre les rubriques suivantes :

* Présentation
* Utilisation de l’activation au niveau du canal comme lecture d’événement unique

## Présentation {#overview}

***L'activation*** au niveau du canal permet aux canaux de basculer après un calendrier donné. Le canal d’événement unique remplace le canal principal après un calendrier défini et est lu pendant une période donnée, jusqu’à ce que le canal principal réexécute son contenu.

L’exemple suivant fournit une solution en se concentrant sur les termes clés suivants :

* un canal ***de séquence*** principal pour la séquence globale
* canal ***d’événement*** unique qui s’exécute une seule fois à la fois
* planification ***définie et priorité*** de l’événement de lecture unique qui se produit dans le canal de séquence principal

## Utilisation de l'activation au niveau du canal {#using-channel-level-activation}

La section suivante explique la création d’une lecture d’événement unique dans un canal pour un projet AEM Screens.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, assurez-vous que les conditions préalables suivantes sont prêtes à commencer à implémenter l’activation au niveau du canal :

* Création d’un projet AEM Screens, dans cet exemple, Activation au niveau du **canal**

* Créer un canal en tant que **canal publicitaire** principal sous le dossier **Canaux**

* Créer un autre canal comme **Lecture** unique **ciblée sous le dossier** Canaux

* Ajouter des ressources appropriées aux deux canaux

L’image suivante montre le projet d’activation **au niveau du** canal avec les canaux **AdChannel** principal et **SinglePlay** **ciblés dans le dossier Canaux.**

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Pour plus d'informations sur la création d'un projet et la création d'un canal de séquence, reportez-vous aux ressources ci-dessous :
>
>* [Création et gestion de projets](creating-a-screens-project.md)
   >
   >
* [Gestion d’un canal](managing-channels.md)
>



### Mise en œuvre {#implementation}

L’implémentation de l’activation au niveau du canal dans un projet AEM Screens implique trois tâches principales :

1. **Configuration de la taxonomie du projet, y compris les canaux, emplacements et écrans**
1. **Affectation de canaux à afficher**
1. **Configuration d’un calendrier et d’une priorité**

Suivez les étapes ci-dessous pour mettre en oeuvre la fonctionnalité :

1. **Créer un emplacement**

   Accédez au dossier **Emplacements** dans votre projet AEM Screens et créez un emplacement en tant que **région**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Pour savoir comment créer un emplacement, reportez-vous à **[Création et gestion des emplacements](managing-locations.md)**.

1. **Créer un affichage sous Emplacement**

   1. Accédez à Activation **au niveau du** canal &gt; **Emplacements** &gt; **Région**.
   1. Select **Region** and click **+ Create** from the action bar.
   1. Sélectionnez **Afficher** dans l’assistant et créez un affichage intitulé **Affichage de région.**
   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Affecter des canaux à afficher**

   Pour **MainAdChannel :**

   1. Accédez à Activation **au niveau du** canal &gt; **Emplacements** &gt; **Région** &gt; **Affichage de la région et cliquez sur Affecter un canal dans la barre d’actions.******
   1. La boîte de dialogue **Attribution de canaux** s’ouvre.
   1. Select **Reference Channel**.. by path.
   1. Sélectionnez le chemin du **canal** comme Activation **au niveau du** canal —&gt; ***Canaux*** —&gt; ***MainAdChannel.***
   1. Le rôle **** de canal est renseigné en tant que canal **** principal.
   1. Sélectionnez la **Priorité** comme **1**.
   1. Select the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. Cliquez sur **Enregistrer**.
   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Vous pouvez également affecter un canal à partir du tableau de bord d'affichage en accédant à Activation **au niveau du** canal —&gt; **Emplacements** —&gt; **Région** **—&gt; Affichage région et en cliquant sur Tableau de bord dans la barre d'actions.****** Cliquez sur **+ Attribuer un canal** dans le panneau CANAUX ET PLANIFICATIONS **** AFFECTÉS.

   De même, affectez channel **TargetedSinglePlay** pour display*** :

   1. Accédez à Activation **au niveau du** canal —&gt; **Emplacements** —&gt; **Région** —&gt; **RégionDisplay et cliquez sur Affecter un canal dans la barre d'actions.******
   1. La boîte de dialogue **Attribution de canaux** s’ouvre.
   1. Select **Reference Channel**.. by path.
   1. Sélectionnez le chemin **de canal** comme Activation **au niveau du** canal* —&gt; ***Canaux*** —&gt; ***CiblageLecture unique.***
   1. Le rôle **** de canal est renseigné sous la forme de jeu **unique** ciblé.
   1. Définissez la **priorité** sur **2**.
   1. Sélectionnez les événements **** pris en charge en tant que charge **** initiale, **écran d’inactivité** et **minuteur, *comme illustré dans la figure ci-dessous.**
   1. Choisissez la date **active à partir** du 27 novembre 2018 à 23h59 et **** active jusqu’au 28 novembre 2018 à 12h05.
   1. Cliquez sur **Enregistrer**.
   >[!CAUTION]
   Vous devez définir la priorité pour le canal **TargetSinglePlay** plus élevée que le canal **MainAdSegment** .

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Pour choisir le même jour, vous devez sélectionner le jour suivant et modifier manuellement la date au même jour, mais pour une date ultérieure. L’utilisateur ne peut donc pas sélectionner une date antérieure. Reportez-vous à l'exemple ci-dessous :

   ![new1](assets/new1.gif)

## Affichage des résultats {#viewing-the-results}

Une fois que vous avez configuré les canaux et que l’affichage est terminé, lancez le lecteur AEM Screens pour afficher le contenu.

Le lecteur affiche le contenu de **MainAdChannel** et exactement à 23h59 (comme défini dans la planification), le canal **Target SinglePlay** affiche son contenu jusqu’à 12h05, puis le canal **MainAdChannel** reprend la lecture de son contenu.

>[!NOTE]
Pour en savoir plus sur le lecteur d’écran AEM, consultez les ressources suivantes :
* [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/)
* [Utilisation d’AEM Screens Player](working-with-screens-player.md)

