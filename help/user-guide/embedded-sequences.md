---
title: Séquences incorporées
description: Découvrez les séquences incorporées pour les canaux, qui vous permettent d’ajouter des composants dans le canal parent. Vous pouvez également réutiliser le contenu d’un autre canal et l’incorporer dans le canal parent.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 100%

---

# Séquences incorporées {#embedded-sequences}

Avec les ***séquences incorporées*** pour les canaux, l’utilisateur ou l’utilisatrice peut ajouter des composants dans le canal parent, ainsi que réutiliser le contenu d’un autre canal et l’incorporer dans le canal parent.

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
>Pour en savoir plus sur le *Chemin du canal*, voir [Attribution de canaux](channel-assignment.md) dans l’instance de création Screens.

Pour ajouter une séquence incorporée à votre canal, procédez comme suit :

1. Cliquez sur le canal dans lequel vous souhaitez incorporer une page. Par exemple, **`We.Retail`en magasin** > **Canaux** > **Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions.
1. En mode d’édition, cliquez sur l’icône de composants dans la barre de gauche afin d’ajouter la page incorporée. Faites glisser et déposez la **séquence incorporée** dans l’éditeur.
1. Double-cliquez sur le composant **Séquence incorporée** pour ajouter le canal à votre canal de séquence d’origine.
1. Cliquez sur le **chemin du canal**.
1. Cliquez sur la **durée (en millisecondes)** de votre canal incorporé dans l’onglet **Séquence**. Par défaut, la durée est définie sur **-1**, ce qui signifie que le canal incorporé est entièrement exécuté. Si l’utilisateur ou l’utilisatrice spécifie une durée, la séquence secondaire est interrompue (c’est-à-dire coupée) à l’heure indiquée.

1. Définissez la **Stratégie de lecture limitée** sur **normal**.

Par défaut, elle est définie sur **normal**. La définition de la valeur sur **normal** (Lire tous les éléments) signifie que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parent. L’autre valeur possible est **Lire un seul élément**. Cette valeur n’affiche qu’un élément de la séquence secondaire à chaque exécution. Par exemple, le premier élément de la première boucle et le second élément de la deuxième boucle.

>[!IMPORTANT]
>
>Attribuez le canal utilisé dans la séquence incorporée au même affichage.
>
>Suivez les étapes ci-dessous après avoir ajouté une séquence incorporée à votre canal à partir des étapes précédentes :
>
>1. Accédez à l’affichage et cliquez sur l’affichage dans le dossier **Emplacements**.
>1. Cliquez sur **Tableau de bord** dans la barre d’actions.
>1. Dans le tableau de bord des affichages, cliquez sur **+ Attribuer des canaux** dans **CANAUX ATTRIBUÉS ET PANNEAUX PLANIFIÉS** pour ouvrir la **boîte de dialogue Attribution de canaux**.
>
>1. Cliquez sur le chemin du canal utilisé dans la séquence incorporée, dans **Chemin du canal**.
>1. Veillez à ce que la **priorité** soit inférieure au canal principal.
>
>1. Ne cliquez sur aucun **événement pris en charge**.
>1. Lorsque vous avez terminé les modifications, cliquez sur **Enregistrer**.
>

L’exemple suivant illustre l’ajout d’une séquence incorporée (**Canal inactif - Nuit**) à un canal existant (**Canal inactif**).

![new2](assets/new2.gif)

### Ajout d’une séquence incorporée dynamique {#adding-a-dynamic-embedded-sequence}

Vous pouvez ajouter une séquence incorporée dynamique à votre canal. Une séquence incorporée dynamique est semblable à une séquence incorporée, mais permet à la personne de suivre une hiérarchie où les modifications/mises à jour effectuées sur un canal sont propagées aux autres canaux liés. Elle respecte une hiérarchie parent-enfant et comprend également des ressources telles que des images ou des vidéos. L’ajout d’une séquence dynamique permet d’ajouter un canal au niveau du rôle du canal.

>[!NOTE]
>
>Le ***rôle du canal*** définit le contexte de l’affichage.
>
>Pour en savoir plus sur le *Rôle du canal*, voir [Attribution de canaux](channel-assignment.md) dans l’instance de création Screens.

Pour ajouter une séquence incorporée à votre canal, procédez comme suit :

1. Cliquez sur le canal dans lequel vous souhaitez incorporer une séquence dynamique. Par exemple, **`We.Retail`en magasin** > **Canaux** > **Canal inactif**.

1. Cliquez sur **Modifier** dans la barre d’actions.
1. En mode d’édition, cliquez sur l’icône de composants dans la barre de gauche afin d’ajouter la séquence incorporée dynamique. Faites glisser et déposez la **séquence incorporée** **dynamique** dans l’éditeur.

1. Double-cliquez sur le composant **séquence incorporée** **dynamique** pour ajouter la page à votre canal de séquence.

1. Saisissez le **Rôle d’attribution de canaux**.
1. Définissez la **Stratégie de lecture limitée** sur **normal**. Par défaut, elle est définie sur **normal**. La définition de la valeur sur **normal** (Lire tous les éléments) signifie que la séquence secondaire s’exécute entièrement à chaque cycle de la séquence parent. L’autre valeur possible est **Lire un seul élément**. Cette valeur n’affiche qu’un élément de la séquence secondaire à chaque exécution. Par exemple, le premier élément de la première boucle et le second élément de la deuxième boucle.

1. Cliquez sur la **Durée (en millisecondes)** dans l’onglet **Séquence** pour votre canal incorporé dans la séquence.

![Plus récent](assets/latest.gif)
