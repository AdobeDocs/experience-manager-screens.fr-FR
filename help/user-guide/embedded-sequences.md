---
title: Séquences incorporées
description: Découvrez les séquences incorporées pour les canaux qui vous permettent d’ajouter des composants dans le canal parent, de réutiliser également le contenu d’un autre canal et de l’incorporer dans le canal parent.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 31%

---

# Séquences incorporées {#embedded-sequences}

Utilisation ***Séquences incorporées***, pour les canaux, permet à l’utilisateur d’ajouter des composants dans le canal parent, ainsi que de réutiliser le contenu d’un autre canal et de l’incorporer dans le canal parent.

## Ajout de séquences incorporées {#adding-embedded-sequences}

Vous avez la possibilité d’ajouter les composants suivants à votre canal de séquence :

* Séquence incorporée
* Séquence incorporée dynamique

>[!NOTE]
>
>Pour en savoir plus sur l’utilisation d’autres composants dans votre projet Screens, voir [Ajout de composants à un canal](adding-components-to-a-channel.md).

### Ajout d’une séquence incorporée {#adding-an-embedded-sequence}

Vous pouvez ajouter une séquence incorporée à votre canal. Une séquence incorporée est un autre canal qui comprend des ressources telles que des images ou des vidéos. En ajoutant une séquence incorporée, l’utilisateur peut ajouter la séquence à un canal au niveau de ***Chemin du canal***.

>[!NOTE]
>***Chemin du canal*** définit une référence explicite au canal.
>Pour en savoir plus sur *Chemin du canal*, voir [Attribution de canaux](channel-assignment.md) dans Création dans Screens.

Pour ajouter une séquence incorporée à votre canal, procédez comme suit :

1. Sélectionnez le canal dans lequel vous souhaitez incorporer une page. Par exemple : **`We.Retail`En magasin** > **Canaux** > **Canal inactif**.

1. Sélectionner **Modifier** dans la barre d’actions.
1. En mode d’éditeur, sélectionnez l’icône de composants dans la barre de gauche afin d’ajouter la page incorporée. Faites glisser et déposez la **séquence incorporée** dans l’éditeur.
1. Double-cliquez sur le **Séquence incorporée** afin que vous puissiez ajouter le canal à votre canal de séquence d’origine.
1. Sélectionnez le **chemin du canal.**
1. Sélectionnez la variable **Durée (millisecondes)** pour votre canal incorporé dans le **Séquence** . Par défaut, la durée est définie sur **-1**, ce qui signifie que le canal incorporé est entièrement exécuté. Si l’utilisateur spécifie une durée, la séquence secondaire est interrompue (c’est-à-dire coupée) à l’heure indiquée.

1. Définissez la **Stratégie de lecture limitée** sur **normal**.

Par défaut, elle est définie sur **normal**. Définir la valeur sur **normal** (Lire tous les éléments) signifie que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parente. L’autre valeur possible est **Lire un seul élément**. Cette valeur n’affiche qu’un élément de la séquence secondaire à chaque exécution. Par exemple, le premier élément de la première boucle et le second élément de la deuxième boucle.

>[!IMPORTANT]
>
>Attribuez le canal utilisé dans la séquence incorporée au même affichage.
>
>Suivez les étapes ci-dessous après avoir ajouté une séquence incorporée à votre canal à partir des étapes précédentes :
>
>1. Accédez à l’affichage et sélectionnez l’affichage dans le dossier **Locations** (Emplacements).
>1. Sélectionner **Tableau de bord** dans la barre d’actions.
>1. Dans le tableau de bord d’affichage, sélectionnez **+ Attribuer des canaux** de la **CANAUX ATTRIBUÉS ET PANNEAUX PLANIFIÉS** pour ouvrir la **Boîte de dialogue Attribution de canaux**.
>
>1. Sélectionnez le chemin du canal (utilisé dans la séquence incorporée) dans **Chemin du canal**.
>1. Veillez à ce que la **priorité** soit inférieure au canal principal.
>
>1. Ne sélectionnez aucune **Événements pris en charge**.
>1. Sélectionner **Enregistrer** une fois terminé.
>

L’exemple suivant illustre l’ajout d’une séquence incorporée (**Canal inactif - Nuit**) à un canal existant (**Canal inactif**).

![new2](assets/new2.gif)

### Ajout d’une séquence incorporée dynamique {#adding-a-dynamic-embedded-sequence}

Vous pouvez ajouter une séquence incorporée dynamique à votre canal. Une séquence incorporée dynamique est similaire à une séquence incorporée, mais permet à l’utilisateur de suivre une hiérarchie où les modifications/mises à jour apportées à un canal sont propagées aux autres canaux dans la relation. Elle respecte une hiérarchie parent-enfant et comprend également des ressources telles que des images ou des vidéos. L’ajout d’une séquence dynamique permet à l’utilisateur d’ajouter un canal au niveau du rôle de canal.

>[!NOTE]
>
>***Rôle du canal*** définit le contexte de l’affichage.
>
>Pour en savoir plus sur *Rôle du canal*, voir [Attribution de canaux](channel-assignment.md) dans Création dans Screens.

Pour ajouter une séquence incorporée à votre canal, procédez comme suit :

1. Sélectionnez le canal dans lequel vous souhaitez incorporer une séquence dynamique. Par exemple : **`We.Retail`En magasin** > **Canaux** > **Canal inactif**.

1. Sélectionner **Modifier** dans la barre d’actions.
1. En mode éditeur, sélectionnez l’icône de composants dans la barre de gauche afin d’ajouter la séquence incorporée dynamique. Faites glisser et déposez le **Dynamique** **Séquence incorporée** à l’éditeur.

1. Double-cliquez sur le **Dynamique** **Séquence incorporée** afin que vous puissiez ajouter la page à votre canal de séquence.

1. Saisissez le **Rôle d’attribution de canaux**.
1. Définissez la **Stratégie de lecture limitée** sur **normal**. Par défaut, elle est définie sur **normal**. Définir la valeur sur **normal** (Lire tous les éléments) signifie que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parente. L’autre valeur possible est **Lire un seul élément**. Cette valeur n’affiche qu’un élément de la séquence secondaire à chaque exécution. Par exemple, le premier élément de la première boucle et le second élément de la deuxième boucle.

1. Sélectionnez la variable **Durée (millisecondes)** in **Séquence** de votre canal incorporé dans la séquence.

![dernier](assets/latest.gif)
