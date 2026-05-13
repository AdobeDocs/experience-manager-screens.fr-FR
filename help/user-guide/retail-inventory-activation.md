---
title: Activation ciblée du stock de vente au détail
description: Découvrez ce cas d’utilisation AEM Screens qui présente le stock de vente au détail de trois sweatshirts de couleurs différentes.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
TQID: https://experienceleague.adobe.com/RVv6pOsJlK-uDu7AfobsDvpYlKQJ6nj4Q0cKSbTlBv4
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aedid: eb3ad9f8-54a2-45f3-abb1-d3976415a718
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: ff2b9b37-92e0-45fc-b853-379d44c08c89
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 98%

---

# Activation ciblée du stock de vente au détail {#retail-inventory-targeted-activation}

Le cas d’utilisation ci-dessous montre trois images différentes en fonction des valeurs de votre feuille de calcul Google.

## Description {#description}

Ce cas d’utilisation présente le stock de vente au détail de trois modèles de sweatshirts de couleurs différentes. Selon le nombre de sweatshirts disponibles en stock enregistré dans Google Sheets, l’image (sweatshirt rouge, vert ou bleu) avec le plus grand nombre est affichée à l’écran.

Le sweatshirt rouge, vert ou bleu est affiché en fonction de la valeur la plus élevée du nombre de sweatshirts disponibles.

## Prérequis {#preconditions}

Avant de commencer à implémenter l’activation du ciblage du stock de vente au détail, apprenez à configurer le ***magasin de données***, la ***segmentation d’audience*** et l’***activation du ciblage des canaux*** dans un projet AEM Screens.

Consultez [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md) pour plus d’informations.

## Flux de base {#basic-flow}

Pour mettre en œuvre le cas d’utilisation de l’activation du stock de vente au détail, procédez comme suit :

1. **Remplissage des feuilles de calcul Google Sheets**

   1. Accédez à la feuille de calcul Google appelée ContextHubDemo.
   1. Ajoutez trois colonnes (Rouge, Vert et Bleu) avec les valeurs correspondantes à trois sweat-shirts différents.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuration des audiences selon les besoins**

   1. Accédez aux segments de votre audience (reportez-vous à l’***Étape 2 : configuration de la segmentation de l’audience*** dans la page **[Configuration de ContextHub dans AEM Screens](configuring-context-hub.md)** pour plus d’informations).

   1. Ajoutez trois nouveaux segments **For_Red**, **For_Green** et **For_Blue**.

   1. Cliquez sur **For_Red**, puis sur **Modifier** dans la barre d’actions.

   1. Faites glisser **Comparaison : Propriété - Propriété** et déposez-le dans l’éditeur.
   1. Cliquez sur l’icône **Configuration**.
   1. Cliquez sur **googlesheets/value/1/2** dans la liste déroulante de **Nom de la première propriété**.
   1. Cliquez sur l’**opérateur** **supérieur à** dans le menu déroulant.
   1. Cliquez sur **Type de données** **Nombre**.
   1. Cliquez sur **googlesheets/value/1/1** dans la liste déroulante **Nom de la deuxième propriété**.
   1. Faites glisser **autre comparaison : Propriété - Propriété** et déposez-le dans l’éditeur, puis cliquez sur l’icône **Configuration**.
   1. Cliquez sur **googlesheets/value/1/2** dans la liste déroulante de **Nom de la première propriété**.
   1. Cliquez sur l’**opérateur** **supérieur à** dans le menu déroulant.
   1. Cliquez sur **Type de données** **Nombre**.
   1. Cliquez sur **googlesheets/value/1/0** dans la liste déroulante **Nom de la deuxième propriété**.

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   De la même manière, modifiez et ajoutez des règles de comparaison des propriétés au segment **For_Blue** , comme illustré ci-dessous :

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   De la même manière, modifiez et ajoutez des règles de comparaison des propriétés au segment **For_Green**, comme illustré ci-dessous :

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Vous remarquerez que pour les segments **For_Blue** et **For_Green**, les données ne peuvent pas être résolues dans l’éditeur car seule la première comparaison est actuellement valide, selon les valeurs de la feuille de calcul Google Sheet.

1. Accédez à votre canal **DataDrivenRetail** (canal de séquence)et cliquez dessus.
1. Cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Vous devez avoir défini vos **configurations** **ContextHub** à l’aide des **Propriétés** du canal > onglet **Personnalisation**.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >Cliquez à la fois sur la **marque** et la **zone** pour que les activités soient correctement répertoriées au démarrage du processus de ciblage.

1. **Ajout d’une image par défaut**

   1. Ajoutez une image par défaut à votre canal et cliquez sur **Ciblage**.
   1. Cliquez sur **Marque** et sur l’**Activité** dans le menu déroulant, puis sur **Commencer le ciblage**.
   1. Cliquez sur **Commencer le ciblage**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >Avant de commencer le ciblage, ajoutez les segments (**For_Green**, **For_Red** et **For_Blue**) en cliquant sur **+ Ajouter le ciblage d’expérience** dans le rail latéral, comme illustré ci-dessous.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Ajoutez les images aux trois scénarios différents comme illustré ci-dessous.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Vérification de l’aperçu**

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de Google et mettez à jour sa valeur.
   1. Modifiez la valeur des trois colonnes différentes. Notez les mises à jour de l’image d’affichage selon la valeur la plus élevée du stock.

   ![retail_result](assets/retail_result.gif)
