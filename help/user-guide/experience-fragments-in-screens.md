---
title: Utiliser des fragments d’expérience
description: Découvrez comment utiliser des fragments d’expérience dans AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 41%

---

# Utilisation de fragments d’expérience {#using-experience-fragments}

Cette page aborde les sujets suivants :

* **Présentation**
* **Utilisation de fragments d’expérience dans AEM Screens**
* **Propagation des modifications apportées à la page**

## Présentation {#overview}

Un ***fragment d’expérience*** est un groupe d’un ou plusieurs composants comprenant un contenu et une disposition pouvant être référencés dans les pages. Les fragments d’expérience peuvent contenir n’importe quel composant, par exemple un ou plusieurs composants pouvant contenir tout élément dans un système de paragraphes référencé dans l’expérience complète ou demandé par un point de terminaison tiers.


## Utilisation de fragments d’expérience dans AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>L’exemple suivant utilise **`We.Retail`** comme projet de démonstration à partir duquel le fragment d’expérience est appliqué à partir d’un **Sites** vers un projet AEM Screens.

Par exemple, le workflow suivant illustre l’utilisation de fragments d’expérience provenant de `We.Retail` dans Sites. Vous pouvez choisir une page web et utiliser ce contenu dans votre canal AEM Screens dans l’un de vos projets.

### Prérequis {#pre-requisites}

**Création d’un projet de démonstration avec un canal**

***Création d’un projet***

1. Pour créer un projet, sélectionnez **Créer un projet Screens**.
1. Saisissez le titre **DemoProject**.
1. Sélectionnez **Enregistrer**.

A **DemoProject** est ajouté à votre AEM Screens.

***Création d’un canal***

1. Accédez au projet **DemoProject** que vous avez créé et sélectionnez le dossier **Channels** (Canaux).

1. Sélectionner **Créer** dans la barre d’actions pour ouvrir l’assistant.
1. Choisissez la **Canal de séquence** modèle dans l’assistant et sélectionnez **Suivant**.

1. Saisissez le **Titre** as **TestChannel** et sélectionnez **Créer**.

A **TestChannel** est ajouté à la variable **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Création d’un fragment d’expérience {#creating-an-experience-fragment}

Pour appliquer le contenu à partir de **`We.Retail`** à votre **TestChannel** in **DemoProject**.

1. **Accédez à une page Sites dans We.Retail**

   1. Accédez à Sites et sélectionnez **`We.Retail`** > **États-Unis** > **Anglais** > **Matériel** et sélectionnez cette page afin de pouvoir l’utiliser comme fragment d’expérience pour votre canal Screens.

   1. Sélectionner **Modifier** dans la barre d’actions afin de pouvoir ouvrir la page que vous souhaitez utiliser comme fragment d’expérience pour votre canal Screens.

1. **Réutilisation du contenu**

   1. Sélectionnez le fragment à inclure dans votre canal.
   1. Sélectionnez la dernière icône à droite pour ouvrir le **Convertir en fragment d’expérience** de la boîte de dialogue

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Création d’un fragment d’expérience**

   1. Choisissez l’**action** **Créer un fragment d’expérience**.

   1. Sélectionnez le **Chemin d’accès parent**.
   1. Sélectionnez le **Modèle**. Sélectionnez ici le modèle **Fragment d’expérience - Variation Screens** (valeur dans le champ `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Saisissez le **Titre du fragment** **ScreensFragment**.

   1. Pour terminer la création d’un fragment d’expérience, cochez la case .

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Remarque : Pour sélectionner une option plus simple, cochez la case à droite du champ afin d’ouvrir la boîte de dialogue de sélection.

1. **Création d’une Live Copy du fragment d’expérience**

   1. Accédez à la page d’accueil d’AEM.
   1. Sélectionnez **Fragments d’expérience** et mettez en surbrillance **ScreensFragment**. Cliquez ensuite sur **Variation comme Live Copy**, comme illustré ci-dessous :

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Sélectionnez le fragment **ScreensFragment** depuis l’assistant **Créer une Live Copy**, puis cliquez sur **Suivant**.

   d. Saisissez le **Titre** et le **Nom** **Screens**.

   e. Sélectionnez **Créer** afin de pouvoir créer la Live Copy.

   f. Sélectionnez **Terminé** pour que vous puissiez revenir à **ScreensFragment** page.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Après avoir créé un fragment AEM Screens, vous pouvez en modifier les propriétés. Sélectionnez le fragment et cliquez sur **Propriétés** dans la barre d’actions.

   **Modification des propriétés d’un fragment Screens**

   1. Accédez au fragment **ScreensFragment** (que vous avez créé lors des étapes précédentes) et cliquez sur **Propriétés** dans la barre d’actions.

   1. Sélectionnez l’onglet **Configuration hors ligne**, comme illustré ci-dessous.

   Vous pouvez ajouter la variable **Bibliothèques côté client** (Java™ et css) et **Fichiers statiques** à votre fragment d’expérience.

   L’exemple suivant illustre l’ajout de bibliothèques côté client et de polices dans le cadre de fichiers statiques à votre fragment d’expérience.  ![fragment](assets/fragment.gif)

1. **Utilisation du fragment d’expérience comme composant dans un canal Screens**

   1. Accédez au canal Screens où vous souhaitez utiliser le fragment **Screens**.
   1. Sélectionnez le canal **TestChannel** et cliquez sur **Modifier** dans la barre d’actions.

   1. Cliquez sur l’icône des composants dans l’onglet latéral.
   1. Faites glisser le **fragment d’expérience** et déposez-le dans votre canal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Sélectionnez le **Fragment d’expérience** et sélectionnez l’icône en haut à gauche (clé à molette) pour ouvrir la **Fragment d’expérience** de la boîte de dialogue

   f. Sélectionnez la Live Copy **Screens** du fragment que vous avez créé à l’*étape 3* dans le champ **Chemin d’accès**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Sélectionnez la Live Copy **Screens** du fragment que vous avez créé à l’*étape 3* dans le champ **Fragment d’expérience**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Saisissez la valeur en millisecondes dans **Durée**.

   i. Sélectionnez le **Configuration hors ligne** de la **Fragments d’expérience** pour définir les bibliothèques côté client et les fichiers statiques.

   >[!NOTE]
   >
   >Pour ajouter des bibliothèques côté client ou des fichiers statiques à ce que vous avez configuré à l’étape (4), vous pouvez les ajouter à partir de la **Configuration hors ligne** dans le **Fragment d’expérience** de la boîte de dialogue

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Sélectionnez la coche pour terminer le processus.

### Validation du résultat {#validating-the-result}

Une fois les étapes précédentes terminées, vous pouvez valider votre fragment d’expérience dans **ChannelOne** par :

1. accédant à **TestChannel** ;
1. sélectionnant l’**Aperçu** dans la barre d’actions.

Affichez le contenu à partir du **Sites** (Live Copy du fragment d’expérience) dans votre canal, comme illustré dans la figure ci-dessous :\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagation des modifications apportées à la page {#propagating-changes-from-the-master-page}

Une ***Live Copy*** désigne la copie (de la source), gérée par des actions de synchronisation telles que définies par les configurations de déploiement.

Parce que le fragment d’expérience que vous avez créé est une Live Copy de la **Sites** et que vous modifiez ce fragment à partir de la page principale, vous affichez les modifications dans votre canal. Vous pouvez également afficher la destination où vous avez utilisé le fragment d’expérience.

>[!NOTE]
>
>Pour plus d’informations sur la Live Copy, voir Réutilisation de contenu : Multi-site Manager et Live Copy.

Pour propager les modifications du canal principal vers votre canal de destination, procédez comme suit :

1. Sélectionnez le fragment d’expérience dans la **Sites** (principal) et cliquez sur l’icône en forme de crayon afin de pouvoir modifier les éléments du fragment d’expérience.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Sélectionnez le fragment d’expérience et cliquez sur l’icône en forme de clé à molette pour ouvrir la boîte de dialogue permettant de modifier les images.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. La boîte de dialogue **Grille de produits** apparaît.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. Vous pouvez modifier n’importe quelle image. Par exemple, ici, la première image est remplacée dans ce fragment.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Sélectionnez le fragment d’expérience et cliquez sur l’icône Déployer afin de propager les modifications au fragment utilisé dans votre canal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Sélectionnez Déployer.

   Les modifications sont déployées.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validation des modifications {#validating-the-changes}

Pour confirmer les modifications dans votre canal, procédez comme suit :

1. Accédez au **Screens** > **Canaux** > **TestChannel**.

1. Cliquez sur **Aperçu** dans la barre d’actions.

L’image suivante illustre les modifications apportées à votre canal **TestChannel**:\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
