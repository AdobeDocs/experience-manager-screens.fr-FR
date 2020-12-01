---
title: Superposition de texte
seo-title: Superposition de texte
description: La superposition de texte est une fonctionnalité disponible dans AEM Screens qui vous permet de créer une expérience attrayante dans un canal de séquence en incluant un titre ou une description superposés à une image. Consultez cette page pour en savoir plus.
seo-description: La superposition de texte est une fonctionnalité disponible dans AEM Screens qui vous permet de créer une expérience attrayante dans un canal de séquence en incluant un titre ou une description superposés à une image. Consultez cette page pour en savoir plus.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: 651627223e1b9bd0f650b010d2b92f004b9e2ea2
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 100%

---


# Superposition de texte {#text-overlay}

Cette section couvre les sujets suivants :

* **Présentation**
* **Utilisation de la superposition de texte**
* **Présentation des propriétés de superposition de texte**
* **Utilisation des valeurs ContextHub dans la superposition de texte**

>[!CAUTION]
>
>La fonction **Superposition de texte** n’est disponible que si vous avez installé AEM 6.3 Feature Pack 5 ou AEM 6.4 Feature Pack 3.

## Présentation {#overview}

La superposition de texte est une fonctionnalité disponible dans AEM Screens qui vous permet de créer une expérience attrayante dans un canal de séquence en incluant un titre ou une description superposés à une image.

Pour savoir comment créer votre propre composant personnalisé, reportez-vous à la section **Extension d’un composant AEM Screens**.

Cette section explique uniquement comment utiliser et exploiter le composant poster dans un projet AEM Screens et l’utiliser comme superposition de texte dans l’un de vos canaux de séquence.

## Utilisation de la superposition de texte{#using-text-overlay}

La section ci-dessous décrit l’utilisation de la superposition de texte dans un projet AEM Screens.

**Conditions préalables**

Avant de commencer à implémenter cette fonctionnalité, assurez-vous d’avoir configuré un projet, condition préalable pour commencer à implémenter la superposition de texte. Par exemple :

* Créez un projet AEM Screens (dans cet exemple, **TextOverlayDemo**)

* Créez un canal de séquence portant le titre **TextSample** sous le dossier **Canaux**.

* Ajoutez du contenu à votre canal **TextSample**

L’image suivante montre le projet **TextOverlayDemo** avec le canal **TextSample** dans le dossier **Channels** (Canaux).

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Pour utiliser la superposition de texte dans un canal AEM Screens, procédez comme suit :

1. Accédez à **TextOverlayDemo** --> **Canaux** --> **TextSample** et cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Sélectionnez l’image et cliquez sur **Configurer** (icône en forme de clé) pour ouvrir la boîte de dialogue des propriétés.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Sélectionnez l’option **Superposition de texte** dans la barre de navigation de la boîte de dialogue, comme illustré dans la figure ci-dessous.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Présentation des propriétés de superposition de texte{#understanding-text-overlay-properties}

Les propriétés de superposition de texte vous permettent d’ajouter du texte à n’importe quel composant de votre projet Screens. La section suivante présente un aperçu des propriétés disponibles dans Superposition de texte :

![texte](assets/text.gif)

Vous pouvez ajouter du texte à la zone de texte et utiliser des styles typographiques tels que le gras, l’italique, le soulignement, etc.

**Variante de couleur** Cette option permet d’afficher le texte en foncé (texte en noir) ou clair (texte en blanc).

**Dimensionnement et positionnement** Cette option permet à l’utilisateur d’aligner le texte horizontalement ou verticalement, ou encore d’utiliser des outils d’ajustement précis pour l’alignement du texte.

>[!NOTE]
>
>Pour utiliser correctement les outils d’ajustement précis, veillez à identifier la position correcte en pixels en utilisant (px) comme suffixe, par exemple 200 px. Le résultat de cette expression sera de 200 pixels à partir du point de départ.

## Utilisation des valeurs ContextHub dans la superposition de texte {#using-text-overlay-context-hub}

La section ci-après décrit l’utilisation des valeurs d’un magasin de données, par exemple, des feuilles de calcul Google Sheets dans le composant de superposition de texte.

**Conditions préalables**

Vous devez définir des configurations ContextHub pour votre projet AEM Screens.

Pour savoir comment configurer et gérer les modifications de ressources pilotées par les données à l’aide d’un magasin de données, voir [Configuration de ContextHub dans AEM Screens](https://docs.adobe.com/content/help/fr-FR/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

Une fois que vous avez défini les configurations requises pour votre projet, suivez les étapes ci-dessous pour utiliser les valeurs d’une feuille de calcul Google Sheets :

1. Accédez à **TextOverlayDemo** --> **Canaux** --> **TextSample** et cliquez sur **Propriétés** dans la barre d’actions.

1. Sélectionnez l’onglet **Personnalisation** pour définir les configurations ContextHub.

   1. Sélectionnez le **Chemin d’accès ContextHub** **libs** > **settings** > **cloudsettings** > **default** > **Configurations ContextHub** et cliquez sur **Sélectionner**.

   1. Sélectionnez le **Chemin d’accès aux segments** **conf** > **screens** > **settings** > **wcm** > **segments** et cliquez sur **Sélectionner**.

   1. Cliquez sur **Enregistrer et fermer**.

      >[!NOTE]
      >
      >Utilisez le chemin ContextHub et le chemin des segments où vous avez initialement enregistré vos segments et configurations ContextHub.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Accédez à **TextOverlayDemo** --> **Canaux** --> **TextSample** et cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Ajoutez une image et ajoutez-lui un composant de superposition de texte, comme décrit dans la section [Utilisation de la superposition de texte](/help/user-guide/text-overlay.md#using-text-overlay) de cette page.

1. Cliquez sur **Configurer** (icône de clé à molette) pour ouvrir la boîte de dialogue **Image**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Accédez à l’onglet **ContextHub** depuis la boîte de dialogue **Image**. Cliquez sur **Ajouter**.

   >[!NOTE]
   >Si vous n’avez pas configuré vos configurations ContextHub, cette option sera désactivée pour votre projet.

1. Saisissez **Valeur** dans le champ **Espace réservé**, sélectionnez la ligne à utiliser dans votre feuille de calcul Google Sheets au niveau de **Variable ContextHub** (dans ce cas, la valeur est récupérée à partir de la ligne 2 et de la colonne 1 de la feuille de calcul Google Sheets), puis saisissez la **Valeur par défaut** **20**, comme illustré dans la figure ci-dessous. Une fois que vous avez terminé, cliquez sur la coche.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >À titre de référence, l’image suivante présente la valeur récupérée à partir de la feuille de calcul Google Sheets :

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Accédez à l’onglet **Superposition de texte** à partir de la boîte de dialogue Image et ajoutez le texte *Température actuelle {Valeur}*, comme illustré dans la figure ci-dessous.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Cliquez sur **Aperçu** pour afficher la sortie souhaitée.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)















