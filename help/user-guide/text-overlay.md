---
title: Superposition de texte
seo-title: Superposition de texte
description: L’incrustation de texte est une fonctionnalité disponible dans les écrans AEM qui vous permet de créer une expérience fascinante dans un canal de séquence en fournissant un titre ou une description superposé au-dessus d’une image. Consultez cette page pour en savoir plus.
seo-description: L’incrustation de texte est une fonctionnalité disponible dans les écrans AEM qui vous permet de créer une expérience fascinante dans un canal de séquence en fournissant un titre ou une description superposé au-dessus d’une image. Consultez cette page pour en savoir plus.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Superposition de texte {#text-overlay}

Cette section traite des sujets suivants :

* **Présentation**
* **Utilisation de l’incrustation de texte**
* **Conditions préalables**
* **Présentation des propriétés d’incrustation de texte**

>[!CAUTION]
>
>La fonction **Text Overlay** n’est disponible que si vous avez installé AEM 6.3 Feature Pack 5 ou AEM 6.4 Feature Pack 3.

## Présentation {#overview}

L’incrustation de texte est une fonctionnalité disponible dans les écrans AEM qui vous permet de créer une expérience fascinante dans un canal de séquence en fournissant un titre ou une description superposé au-dessus d’une image.

Pour savoir comment créer votre propre composant personnalisé, reportez-vous à la section **Extension d’un composant** AEM Screens.

Cette section explique uniquement comment utiliser et exploiter le composant d’affiche dans un projet AEM Screens et l’utiliser comme incrustation de texte dans l’un de vos canaux de séquence.

## Utilisation de l’incrustation de texte {#using-text-overlay}

La section suivante décrit l’utilisation de l’incrustation de texte dans un projet AEM Screens.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, assurez-vous d’avoir configuré un projet comme prérequis pour commencer à implémenter l’incrustation de texte. Par exemple :

* Création d’un projet AEM Screens (dans cet exemple, **TextOverlayDemo**)

* Création d’un canal en tant que **TextSample** sous le dossier **Canaux**

* Ajouter du contenu à votre canal **TextSample**

L’image suivante montre le projet **TextOverlayDemo** avec le canal **TextSample** dans le dossier **Canaux** .

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

1. Accédez à **TextOverlayDemo** —&gt; **Canaux** —&gt; **TextSample** et cliquez sur **Modifier dans la barre d’actions pour ouvrir l’éditeur.**

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Sélectionnez l’image et cliquez sur **Configurer** (icône en forme de clé à molette) pour ouvrir la boîte de dialogue des propriétés.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Sélectionnez l’option Recouvrement **de** texte dans la barre de navigation de la boîte de dialogue, comme illustré dans la figure ci-dessous.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Présentation des propriétés d’incrustation de texte {#understanding-text-overlay-properties}

Les propriétés d’incrustation de texte vous permettent d’ajouter du texte à n’importe quel composant de votre projet Ecrans. La section suivante présente un aperçu des propriétés disponibles dans l’incrustation de texte :

![text](assets/text.gif)

Vous pouvez ajouter un texte à la zone de texte et mettre l’accent sur des caractères typographiques tels que le gras, l’italique, le soulignement, etc.

**Variante** de couleur Cette option permet au texte d’être foncé (texte en noir) ou clair (texte en blanc).

**Dimensionnement et positionnement** Cette option permet à l’utilisateur d’aligner le texte horizontalement ou verticalement, ou encore d’utiliser des outils affinés pour l’alignement du texte.

>[!NOTE]
>
>Pour utiliser correctement des outils à grains fins, veillez à identifier la position correcte en pixels en utilisant (px) comme suffixe, par exemple 200 px. Le résultat de cette expression sera de 200 pixels à partir du point de départ.

