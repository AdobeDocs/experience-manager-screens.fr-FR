---
title: Superposition de texte
description: Découvrez la superposition de texte dans AEM Screens qui vous permet de créer une expérience attrayante dans un canal de séquence en fournissant un titre ou une description superposé au-dessus d’une image.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 58%

---

# Superposition de texte {#text-overlay}

Cette section couvre les sujets suivants :

* **Présentation**
* **Utilisation de la superposition de texte**
* **Présentation des propriétés de superposition de texte**
* **Utilisation des valeurs ContextHub dans la superposition de texte**

>[!CAUTION]
>
>La variable **Superposition de texte** Cette fonctionnalité n’est disponible que si vous avez installé AEM 6.3 Feature Pack 5 ou AEM 6.4 Feature Pack 3.

## Vue d’ensemble {#overview}

La superposition de texte est une fonctionnalité disponible dans AEM Screens qui vous permet de créer une expérience attrayante dans un canal de séquence en fournissant un titre ou une description superposé au-dessus d’une image.

Pour savoir comment créer votre propre composant personnalisé, voir **Extension d’un composant AEM Screens**.

Cette section explique uniquement l’utilisation et l’exploitation du composant affiche dans un projet AEM Screens et son application comme superposition de texte dans l’un de vos canaux de séquence.

## Utilisation de la superposition de texte {#using-text-overlay}

La section ci-dessous décrit l’utilisation de la superposition de texte dans un projet AEM Screens.

**Prérequis**

Avant de mettre en oeuvre cette fonctionnalité, assurez-vous d’avoir configuré un projet comme condition préalable au démarrage de l’implémentation de la superposition de texte. Par exemple :

* Créez un projet AEM Screens (dans cet exemple, **TextOverlayDemo**)

* Créez un canal de séquence portant le titre **TextSample** sous le dossier **Canaux**.

* Ajoutez du contenu à votre canal **TextSample**

L’image suivante montre le projet **TextOverlayDemo** avec le canal **TextSample** dans le dossier **Channels** (Canaux).

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Pour utiliser la superposition de texte dans un canal AEM Screens, procédez comme suit :

1. Accédez à **TextOverlayDemo** > **Canaux** > **TextSample** et cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Sélectionnez l’image et cliquez sur **Configurer** (icône en forme de clé) pour ouvrir la boîte de dialogue des propriétés.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Sélectionnez l’option **Superposition de texte** dans la barre de navigation de la boîte de dialogue, comme illustré dans la figure ci-dessous.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Présentation des propriétés de superposition de texte {#understanding-text-overlay-properties}

Les propriétés de superposition de texte vous permettent d’ajouter du texte à n’importe quel composant de votre projet Screens. La section suivante présente un aperçu des propriétés disponibles dans Superposition de texte :

![texte](assets/text.gif)

Vous pouvez ajouter du texte à la zone de texte ou encore des styles typographiques tels que le gras, l’italique, le soulignement, etc.

**Variante de couleur** Cette option permet d’afficher le texte en foncé (texte en noir) ou clair (texte en blanc).

**Redimensionnement et positionnement** Cette option permet à l’utilisateur d’aligner le texte horizontalement ou verticalement, ou encore d’utiliser des outils d’ajustement affinés pour l’alignement du texte.

>[!NOTE]
>
>Pour utiliser correctement les outils d’ajustement affinés, veillez à identifier la position correcte en pixels en utilisant (px) comme suffixe, par exemple 200 px. Le résultat de cette expression sera de 200 pixels à partir du point de départ.

## Utilisation des valeurs ContextHub dans la superposition de texte {#using-text-overlay-context-hub}

La section ci-après décrit l’utilisation des valeurs d’un magasin de données, par exemple, des feuilles de calcul Google Sheets dans le composant de superposition de texte.

**Prérequis**

Vous devez définir des configurations ContextHub pour votre projet AEM Screens.

Pour savoir comment configurer et gérer les modifications de ressources pilotées par les données à l’aide d’un entrepôt de données, voir [Configuration de ContextHub dans AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/configuring-context-hub).

Après avoir configuré les configurations requises pour votre projet, procédez comme suit pour utiliser les valeurs des feuilles de calcul Google Sheets :

1. Accédez à **TextOverlayDemo** > **Canaux** > **TextSample** et sélectionnez **Propriétés** dans la barre d’actions.

1. Sélectionnez la variable **Personnalisation** pour pouvoir configurer les configurations ContextHub.

   1. Sélectionnez la variable **Chemin ContextHub** as **libs** > **paramètres** > **cloudsettings** > **default** > **Configurations ContextHub** et sélectionnez **Sélectionner**.

   1. Sélectionnez la variable **Chemin d’accès aux segments** as **conf** > **screens** > **paramètres** > **wcm** > **segments** et sélectionnez **Sélectionner**.

   1. Sélectionnez **Enregistrer et fermer**.

      >[!NOTE]
      >
      >Utilisez le chemin ContextHub et le chemin des segments où vous avez initialement enregistré vos segments et configurations ContextHub.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Accédez à **TextOverlayDemo** > **Canaux** > **TextSample** et cliquez sur **Modifier** dans la barre d’actions.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Ajoutez une image et ajoutez-lui un composant de superposition de texte, comme décrit dans la section [Utilisation de la superposition de texte](/help/user-guide/text-overlay.md#using-text-overlay) de cette page.

1. Sélectionner sur **Configurer** (icône de clé à molette) pour ouvrir la **Image** de la boîte de dialogue

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Accédez à l’onglet **ContextHub** depuis la boîte de dialogue **Image**. Sélectionnez **Ajouter**.

   >[!NOTE]
   >Si vous n’avez pas configuré votre configuration ContextHub, cette option est désactivée pour votre projet.

1. Entrée **Valeur** dans le **Espace réservé** champ . Sélectionnez la ligne dans laquelle vous souhaitez obtenir la valeur de votre feuille Google. **Variable ContextHub**. Dans ce cas, la valeur est récupérée à partir de la ligne 2 et de la colonne 1 des feuilles de calcul Google. Définissez maintenant la **Valeur par défaut** sur **20**, comme illustré ci-dessous. Une fois que vous avez terminé, cliquez sur la coche.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >À titre de référence, l’image suivante présente la valeur récupérée à partir des feuilles de calcul Google Sheets :

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Accédez à l’onglet **Superposition de texte** à partir de la boîte de dialogue Image et ajoutez le texte *Température actuelle {Valeur}*, comme illustré dans la figure ci-dessous.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Sélectionnez **Aperçu**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
