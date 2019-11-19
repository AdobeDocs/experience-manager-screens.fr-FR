---
title: Activation ciblée du stock de vente au détail
seo-title: Activation ciblée du stock de vente au détail
description: Ce cas d’utilisation présente le stock de vente au détail de trois chemises à sweat-shirts de couleur différente. Selon le nombre de sweats disponibles en stock enregistrés dans les feuilles Google, l’image (rouge, vert ou bleu) avec le plus grand nombre de sweats est affichée à l’écran.
seo-description: Ce cas d’utilisation présente le stock de vente au détail de trois chemises à sweat-shirts de couleur différente. Selon le nombre de sweats disponibles en stock enregistrés dans les feuilles Google, l’image (rouge, vert ou bleu) avec le plus grand nombre de sweats est affichée à l’écran.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Activation ciblée du stock de vente au détail {#retail-inventory-targeted-activation}

Le cas d’utilisation suivant illustre trois images différentes en fonction des valeurs de votre feuille Google.

## Description {#description}

Ce cas d’utilisation présente le stock de vente au détail de trois chemises à sweat-shirts de couleur différente. Selon le nombre de sweats disponibles en stock enregistrés dans les feuilles Google, l’image (rouge, vert ou bleu) avec le plus grand nombre de sweats est affichée à l’écran.

Dans ce cas d’utilisation, le pull rouge, vert ou bleu s’affichera sur votre écran en fonction de la valeur la plus élevée du nombre de pulls disponibles.

## Conditions préalables {#preconditions}

Avant de commencer à mettre en oeuvre l’activation du ciblage du stock de vente au détail, vous devez apprendre à configurer le stockage ***de*** données, la segmentation ***de l’*** audience et l’ ***activation du ciblage des canaux*** dans un projet AEM Screens.

Consultez [Configuration de ContextHub dans les écrans](configuring-context-hub.md) AEM pour plus d’informations.

## Flux de base {#basic-flow}

Suivez les étapes ci-dessous pour mettre en oeuvre le cas d'utilisation de l'activation du stock de détail :

1. **Renseigner les feuilles de Google**

   1. Accédez à la feuille Google ContextHubDemo.
   1. Ajoutez trois colonnes (Rouge, Vert et Bleu) avec les valeurs correspondantes pour trois sweatshirts différents.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuration des audiences conformément aux exigences**

   1. Accédez aux segments de votre audience (Reportez-vous à l’ ***étape 2 : Configuration de la segmentation*** de l’audience dans **[Configuration de ContextHub dans la page AEM Screens](configuring-context-hub.md)** (pour plus d’informations).

   1. Ajoutez trois nouveaux segments **For_Red**, **For_Green** et **For_Blue**.

   1. Sélectionnez **For_Red** et cliquez sur **Modifier** dans la barre d’actions.

   1. Faites glisser et déposez la **comparaison : Propriété : propriété** de l’éditeur et cliquez sur l’icône Configurer pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante du nom de la **première propriété.**

   1. Sélectionnez l’ **opérateur** **supérieur à **dans le menu déroulant.

   1. Sélectionner le type **de** données comme **nombre**

   1. Sélectionnez **googlesheets/value/1/1** dans la liste déroulante du **deuxième nom de propriété.**

   1. Faire glisser et déposer **une autre comparaison : Propriété : propriété **de l’éditeur et cliquez sur l’icône Configurer pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante du nom de la **première propriété.**

   1. Sélectionnez l’ **opérateur** **supérieur à **dans le menu déroulant.

   1. Sélectionner le type **de** données comme **nombre**

   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante du **deuxième nom de propriété.**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   De même, modifiez et ajoutez des règles de propriétés de comparaison au segment **For_Blue** , comme illustré dans la figure ci-dessous :

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   De même, modifiez et ajoutez des règles de propriété de comparaison au ** For_Green **segment, comme illustré dans la figure ci-dessous :

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Vous remarquerez que pour les segments **For_Green** et **For_Green**, les données ne peuvent pas être résolues dans l’éditeur car seule la première comparaison est valide à ce jour, selon les valeurs de la feuille Google.

1. Recherchez et sélectionnez votre canal **DataDrivenRetail** (un canal de séquence), puis cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Vous auriez dû configurer vos **configurations** ContextHub **à l’aide de l’onglet** Propriétés **du canal —&gt;** **Personnalisation.**

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Vous devez sélectionner à la fois la **marque** et la **zone** pour que les activités soient correctement répertoriées au démarrage du processus de ciblage.

1. **Ajout d’une image par défaut**

   1. Ajoutez une image par défaut à votre canal et cliquez sur **Ciblage**.
   1. Sélectionnez **Marque** et **Activité** dans le menu déroulant, puis cliquez sur **Démarrer le ciblage**.

   1. Cliquez sur **Commencer le ciblage**.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Avant de commencer le ciblage, vous devez ajouter les segments (**For_Green**, **For_Red** et **For_Blue**) en cliquant sur **+ Ajouter le ciblage d’expérience dans le rail latéral, comme illustré dans la figure ci-dessous.**

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Ajoutez les images aux trois scénarios différents comme illustré ci-dessous.

   ![detail_targeting](assets/retail_targeting.gif)

1. **Vérification de l’aperçu**

   1. Click **Preview.** Ouvrez également votre feuille Google et mettez à jour sa valeur.
   1. Modifiez la valeur des trois colonnes et vous constaterez que l’image d’affichage est mise à jour en fonction de la valeur la plus élevée du stock.
   ![detail_result](assets/retail_result.gif)

