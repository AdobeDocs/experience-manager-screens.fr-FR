---
title: Utiliser des fragments d’expérience
description: Apprenez à utiliser des fragments d’expérience dans AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 100%

---

# Utiliser des fragments d’expérience {#using-experience-fragments}

Cette page aborde les sujets suivants :

* **Présentation**
* **Utilisation de fragments d’expérience dans AEM Screens**
* **Propagation des modifications apportées à la page**

## Vue d’ensemble {#overview}

Un ***fragment d’expérience*** est un groupe d’un ou plusieurs composants comprenant un contenu et une disposition pouvant être référencés dans les pages. Les fragments d’expérience peuvent contenir n’importe quel composant. Par exemple, ils peuvent contenir n’importe quel composant pouvant contenir un élément dans un système de paragraphes, qui sera référencé dans l’expérience complète ou demandé par un point d’entrée tiers.


## Utilisation de fragments d’expérience dans AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>L’exemple ci-dessous utilise **`We.Retail`** comme projet de démonstration : le fragment d’expérience issu d’une page **Sites** est appliqué à un projet AEM Screens.

Par exemple, le workflow ci-après illustre l’utilisation de fragments d’expérience de `We.Retail` dans Sites. Vous pouvez choisir une page web et utiliser son contenu dans votre canal AEM Screens dans l’un de vos projets.

### Conditions préalables {#pre-requisites}

**Création d’un projet de démonstration avec un canal**

***Création d’un projet***

1. Pour créer un projet, cliquez sur **Créer un projet Screens**.
1. Saisissez le titre **DemoProject**.
1. Cliquez sur **Enregistrer**.

Un projet **DemoProject** est ajouté à AEM Screens.

***Créer un canal***

1. Accédez au projet **DemoProject** que vous avez créé et cliquez sur le dossier **Canaux**.

1. Cliquez sur **Créer** dans la barre d’actions pour ouvrir l’assistant.
1. Sélectionnez le modèle **Canal de séquence** dans l’assistant et cliquez sur **Suivant**.

1. Saisissez le **titre** **TestChannel** et cliquez sur **Créer**.

Un **TestChannel** est ajouté à votre **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Création d’un fragment d’expérience {#creating-an-experience-fragment}

Suivez les étapes ci-dessous pour appliquer le contenu de **`We.Retail`** dans le canal **TestChannel** de **DemoProject**.

1. **Accéder à une page Sites dans We.Retail**

   1. Accédez à Sites, cliquez sur **`We.Retail`** > **United States (États-Unis)** > **English (Anglais)** > **Equipment (Matériel)** et cliquez sur cette page pour l’utiliser comme fragment d’expérience pour votre canal Screens.

   1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir la page que vous souhaitez utiliser comme fragment d’expérience pour votre canal Screens.

1. **Réutiliser du contenu**

   1. Cliquez sur le fragment à inclure dans votre canal.
   1. Cliquez sur la dernière icône à droite pour ouvrir la boîte de dialogue **Convertir en fragment d’expérience**.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Créer un fragment d’expérience**

   1. Choisissez l’**Action** **Créer un fragment d’expérience**.

   1. Cliquez sur le **chemin d’accès parent**.
   1. Cliquez sur le **modèle**. Sélectionnez ici le modèle **Fragment d’expérience - Variation Screens** (valeur dans le champ `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Saisissez le **Titre du fragment** **ScreensFragment**.

   1. Pour terminer la création d’un fragment d’expérience, cliquez sur la coche.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Pour sélectionner une option plus simple, cochez la case à droite du champ afin d’ouvrir la boîte de dialogue de sélection.

1. **Création d’une Live Copy du fragment d’expérience**

   1. Accédez à la page d’accueil d’AEM.
   1. Cliquez sur **Fragments d’expérience** et mettez en surbrillance **ScreensFragment**. Cliquez ensuite sur **Variation comme Live Copy**, comme illustré ci-dessous :

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Cliquez sur **ScreensFragment** à partir de l’assistant **Créer une Live Copy**, puis sur **Suivant**.

   d. Saisissez le **Titre** et le **Nom** **Screens**.

   e. Cliquez sur **Créer** afin de pouvoir créer la Live Copy.

   f. Cliquez sur **Terminé** pour que vous puissiez revenir à la page **ScreensFragment**.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Après avoir créé un fragment AEM Screens, vous pouvez en modifier les propriétés. Cliquez sur le fragment, puis sur **Propriétés** dans la barre d’actions.

   **Modification des propriétés d’un fragment Screens**

   1. Accédez au fragment **ScreensFragment** (que vous avez créé lors des étapes précédentes) et cliquez sur **Propriétés** dans la barre d’actions.

   1. Cliquez sur l’onglet **Configuration hors ligne**, comme illustré ci-dessous.

   Vous pouvez ajouter les **bibliothèques côté client** (Java™ et CSS) et les **fichiers statiques** à votre fragment d’expérience.

   L’exemple ci-dessous illustre l’ajout de bibliothèques côté client et de polices en tant que fichiers statiques au fragment d’expérience. ![fragment](assets/fragment.gif)

1. **Utilisation du fragment d’expérience comme composant dans un canal Screens**

   1. Accédez au canal Screens où vous souhaitez utiliser le fragment **Screens**.
   1. Cliquez sur **TestChannel**, puis sur **Modifier** dans la barre d’actions.

   1. Cliquez sur l’icône des composants dans l’onglet latéral.
   1. Faites glisser le **fragment d’expérience** et déposez-le dans votre canal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Cliquez sur le composant **Fragment d’expérience**, puis sur l’icône en haut à gauche (clé à molette) pour ouvrir la boîte de dialogue **Fragment d’expérience**.

   f. Cliquez sur la Live Copy **Screens** du fragment que vous avez créé à l’*étape 3* dans le **chemin d’accès**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Cliquez sur la Live Copy **Screens** du fragment que vous avez créé à l’*étape 3* dans le **fragment d’expérience**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Saisissez la valeur en millisecondes dans **Durée**.

   i. Cliquez sur la **Configuration hors ligne** dans la boîte de dialogue **Fragments d’expérience** pour définir les bibliothèques côté client et les fichiers statiques.

   >[!NOTE]
   >
   >Si vous souhaitez ajouter des bibliothèques côté client ou des fichiers statiques à ce que vous avez configuré à l’étape (4), vous pouvez les ajouter à partir de l’onglet **Configuration hors ligne** de la boîte de dialogue **Fragment d’expérience**.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Cliquez sur la coche pour terminer le processus.

### Valider le résultat {#validating-the-result}

Une fois les étapes précédentes terminées, vous pouvez valider le fragment d’expérience dans **ChannelOne** en effectuant ce qui suit :

1. accédant à **TestChannel** ;
1. sélectionnant l’**Aperçu** dans la barre d’actions.

Vous voyez le contenu de la page **Sites** (Live Copy du fragment d’expérience) dans votre canal, comme illustré ci-dessous :\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagation des modifications apportées à la page {#propagating-changes-from-the-master-page}

Une ***Live Copy*** désigne la copie (de la source), gérée par des actions de synchronisation telles que définies par les configurations de déploiement.

Comme le fragment d’expérience que vous avez créé est une Live Copy des pages **Sites** et que vous modifiez ce fragment à partir de la page principale, vous affichez les modifications dans votre canal. Vous pouvez également afficher la destination où vous avez utilisé le fragment d’expérience.

>[!NOTE]
>
>Pour plus d’informations sur les Live Copy, voir Réutilisation de contenu : Multi Site Manager et Live Copy.

Pour propager les modifications du canal principal vers votre canal de destination :

1. Cliquez sur le fragment d’expérience sur la page (principale) **Sites** et cliquez sur l’icône en forme de crayon pour modifier les éléments du fragment d’expérience.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Cliquez sur le fragment d’expérience, puis sur l’icône en forme de clé à molette pour ouvrir la boîte de dialogue permettant de modifier les images.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. La boîte de dialogue **Grille de produits** apparaît.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. Vous pouvez modifier n’importe quelle image. Par exemple, ici, la première image est remplacée dans ce fragment.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Cliquez sur le fragment d’expérience, puis sur l’icône Déploiement pour propager les modifications sur le fragment utilisé dans votre canal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Cliquez sur Déployer.

   Les modifications sont déployées.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validation des modifications {#validating-the-changes}

Pour confirmer les modifications dans votre canal, procédez comme suit :

1. Accédez à **Screens** > **Canaux** > **TestChannel**.

1. Cliquez sur **Aperçu** dans la barre d’actions.

L’image suivante illustre les modifications apportées à votre canal **TestChannel**:\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
