---
title: Séquences incorporées
seo-title: Séquences incorporées
description: Suivez cette page pour en savoir plus sur les séquences incorporées pour les canaux qui permettent à l’utilisateur d’ajouter des composants dans le canal parent, et aussi de réutiliser le contenu d’un autre canal et de l’incorporer dans le canal parent.
seo-description: Suivez cette page pour en savoir plus sur les séquences incorporées pour les canaux qui permettent à l’utilisateur d’ajouter des composants dans le canal parent, et aussi de réutiliser le contenu d’un autre canal et de l’incorporer dans le canal parent.
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Séquences incorporées {#embedded-sequences}

Using ***Embedded Sequences***, for channels, allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.

## Ajout de séquences incorporées {#adding-embedded-sequences}

Vous avez la possibilité d’ajouter les composants suivants à votre canal de séquence :

* Séquence incorporée
* Séquence incorporée dynamique

>[!NOTE]
>
>Pour en savoir plus sur l’utilisation d’autres composants dans votre projet Screens, voir [Ajout de composants à un canal](adding-components-to-a-channel.md).

### Ajout d’une séquence incorporée {#adding-an-embedded-sequence}

Vous pouvez ajouter une séquence incorporée à votre canal. Une séquence incorporée est un autre canal qui comprend des fichiers tels que des images ou des vidéos. En ajoutant une séquence incorporée, l’utilisateur peut ajouter la séquence à un canal au niveau de ***Chemin du canal***.

>[!NOTE]
>
>***Chemin du canal ***définit une référence explicite au canal.
>
>Pour en savoir plus sur *Chemin du canal*, voir [Attribution de canaux](channel-assignment.md) dans la section Création dans Screens.

Suivez les étapes ci-dessous pour ajouter une séquence incorporée à votre canal :

1. Sélectionnez le canal où vous souhaitez incorporer une page. For example, **We.Retail In-Store** --&gt; **Channels** --&gt;** Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Cliquez sur l’icône de composants sur la barre de gauche pour ajouter la page incorporée. Drag and drop the **Embedded Sequence** to the editor.
1. Double-click the **Embedded Sequence** component to add the channel to your original sequence channel.
1. Sélectionnez le **chemin du canal.**
1. Select the **Duration (ms)** for your embedded channel in the **Sequence** tab. By default, the duration is set to **-1**, that means embedded channel is fully run. Si l’utilisateur spécifie une durée, la séquence secondaire est interrompue (c’est-à-dire coupée) à l’heure indiquée.

1. Définissez la stratégie **de lecture** limitée sur **normal**.

By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

>[!NOTE]
>
>**Important:**
>
>Vous devez affecter le canal (utilisé dans la séquence incorporée), au même affichage.
>
>Suivez les étapes ci-dessous après avoir ajouté une séquence incorporée à votre canal à partir des étapes précédentes :
>
>1. Accédez à l’affichage et sélectionnez l’affichage dans le dossier **Emplacements** .
>1. Cliquez sur **Tableau de bord** dans la barre d'action pour accéder au tableau de bord d'affichage.
>1. Sélectionnez **+ Attribuer des canaux** dans les panneaux **CANAUX ET PLANIFIÉS** AFFECTÉS pour ouvrir la boîte **de dialogue Affectation de** canal.
   >
   >
1. Sélectionnez le chemin du canal que vous (utilisé dans la séquence incorporée) dans le chemin du **canal**.
>1. Assurez-vous que la **priorité** est inférieure au canal principal.
   >
   >
1. Vous ne devez sélectionner aucun événement **** pris en charge.
>1. Cliquez sur **Enregistrer** une fois terminé.
>



L’exemple suivant illustre l’ajout d’une séquence incorporée (**Idle Channel - Night**) à un canal existant (**Idle Channel**).

![new2](assets/new2.gif)

### Ajout d’une séquence incorporée dynamique {#adding-a-dynamic-embedded-sequence}

Vous pouvez ajouter une séquence incorporée dynamique à votre canal. Une séquence incorporée dynamique est semblable à une séquence incorporée, mais permet à l’utilisateur de suivre une hiérarchie où les modifications/mises à jour effectuées sur un canal sont propagées aux autres canaux liés. Il suit la hiérarchie parent-enfant et inclut également des fichiers tels que des images ou des vidéos. L’ajout d’une séquence dynamique permet à l’utilisateur d’ajouter un canal au niveau du rôle de canal.

>[!NOTE]
>
>***Rôle de canal*** définit le contexte de l’affichage.
>
>Pour en savoir plus sur le *Rôle du canal*, voir [Attribution de canaux](channel-assignment.md) dans la section Création dans Screens.

Suivez les étapes ci-dessous pour ajouter une séquence incorporée à votre canal :

1. Sélectionnez le canal dans lequel vous voulez incorporer une séquence dynamique. For example, **We.Retail In-Store** --&gt; **Channels** --&gt; **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. Cliquez sur l’icône de composants sur la barre de gauche pour ajouter la séquence incorporée dynamique. Faites glisser et **déposez la séquence dynamique** **Incorporée **dans l’éditeur.

1. Double-click the **Dynamic** **Embedded Sequence **component to add the page to your sequence channel.

1. Enter the **Channel Assignment Role**.
1. Définissez la stratégie **de lecture** limitée sur **normal**. By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Select the **Duration (ms)** in **Sequence** tab for your embedded channel in the sequence.

![dernier](assets/latest.gif)

