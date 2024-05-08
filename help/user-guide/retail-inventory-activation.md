---
title: Activation ciblée du stock de vente au détail
description: Découvrez ce cas pratique AEM Screens qui présente le stock de vente au détail de trois sweat-shirts de couleurs différentes.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 31%

---

# Activation ciblée du stock de vente au détail {#retail-inventory-targeted-activation}

Le cas d’utilisation ci-dessous montre trois images différentes en fonction des valeurs de votre feuille de calcul Google.

## Description {#description}

Ce cas pratique présente le stock de vente au détail de trois sweat-shirts de couleurs différentes. Selon le nombre de sweat-shirts disponibles en stock enregistré dans Google Sheets, l’image (sweat-shirt rouge, vert ou bleu) avec le plus grand nombre est affichée à l’écran.

Pour ce cas d’utilisation, le sweat-shirt rouge, vert ou bleu s’affiche à l’écran en fonction de la valeur la plus élevée du nombre de sweaters disponible.

## Prérequis {#preconditions}

Avant de commencer à implémenter l’activation du ciblage du stock de vente au détail, découvrez comment configurer ***Entrepôt de données***, ***Segmentation de l’audience*** et ***Activation du ciblage des canaux*** dans un projet AEM Screens.

Voir [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md) pour plus d’informations.

## Flux de base {#basic-flow}

Pour mettre en œuvre le cas d’utilisation de l’activation du stock de vente au détail, procédez comme suit :

1. **Remplissage des feuilles de calcul Google Sheets**

   1. Accédez à la feuille de calcul Google appelée ContextHubDemo.
   1. Ajoutez trois colonnes (Rouge, Vert et Bleu) avec les valeurs correspondantes à trois sweat-shirts différents.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuration des audiences selon les besoins**

   1. Accédez aux segments de votre audience (voir ***Étape 2 : configuration de la segmentation de l’audience*** in **[Configuration de ContextHub dans AEM Screens](configuring-context-hub.md)** pour plus d’informations).

   1. Ajoutez trois nouveaux segments **For_Red**, **For_Green** et **For_Blue**.

   1. Cliquez sur **For_Red** et cliquez sur **Modifier** dans la barre d’actions.

   1. Faites glisser et déposez le **Comparaison : Propriété - Propriété** à l’éditeur.
   1. Cliquez sur le bouton **Configuration** Icône
   1. Cliquez sur **googlesheets/value/1/2** dans la liste déroulante de **First Property name**.
   1. Cliquez sur le bouton **Opérateur** as **supérieur à** dans le menu déroulant.
   1. Cliquez sur **Type de données** as **nombre**.
   1. Cliquez sur **googlesheets/value/1/1** dans la liste déroulante de **Second Property name**.
   1. Glisser-déposer **autre comparaison : Propriété - Propriété** dans l’éditeur, puis cliquez sur l’icône **Configuration** Icône
   1. Cliquez sur **googlesheets/value/1/2** dans la liste déroulante de **First Property name**.
   1. Cliquez sur le bouton **Opérateur** as **supérieur à** dans le menu déroulant.
   1. Cliquez sur **Type de données** as **nombre**.
   1. Cliquez sur **googlesheets/value/1/0** dans la liste déroulante de **Second Property name**.

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   De la même manière, modifiez et ajoutez des règles de propriétés de comparaison au segment **For_Blue**, comme illustré ci-dessous :

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   De même, modifiez et ajoutez des règles de propriété de comparaison à **For_Green** comme illustré dans la figure ci-dessous :

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Notez que pour les segments **For_Green** et **For_Green**, les données ne peuvent pas être résolues dans l’éditeur, car seule la première comparaison est actuellement valide, selon les valeurs de la feuille de calcul Google.

1. Naviguez et cliquez sur votre **DataDrivenRetail** channel (canal de séquence).
1. Cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Vous devez avoir configuré votre **ContextHub** **Configurations** utilisation du canal **Propriétés** > **Personnalisation** .

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >Cliquez sur les deux **Marque** et la variable **Zone** pour que les activités soient correctement répertoriées au démarrage du processus de ciblage.

1. **Ajout d’une image par défaut**

   1. Ajoutez une image par défaut à votre canal et cliquez sur **Ciblage**.
   1. Cliquez sur **Marque** et la variable **Activité** dans le menu déroulant et cliquez sur **Commencer le ciblage**.
   1. Cliquez sur **Commencer le ciblage**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >Avant de commencer le ciblage, ajoutez les segments (**For_Green**, **For_Red**, et **For_Blue**) en sélectionnant **+ Ajouter un ciblage d’expérience** du rail latéral, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Ajoutez les images aux trois scénarios différents comme illustré ci-dessous.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Vérification de l’aperçu**

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de calcul Google Sheet et mettez à jour sa valeur.
   1. Modifiez la valeur des trois colonnes différentes. Notez les mises à jour de l’image d’affichage en fonction de la valeur de stock la plus élevée.

   ![retail_result](assets/retail_result.gif)
