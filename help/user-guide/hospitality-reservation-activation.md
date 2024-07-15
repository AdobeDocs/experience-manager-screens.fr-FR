---
title: Activation de la réservation d’hébergements
description: Découvrez comment ce cas d’utilisation montre l’utilisation de l’activation des réservations d’hébergements en fonction des valeurs renseignées dans Google Sheets.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 100%

---

# Activation de la réservation d’hébergements {#hospitality-reservation-activation}

Le cas d’utilisation ci-dessous montre comment utiliser l’activation des réservations d’hébergements en fonction des valeurs renseignées dans Google Sheets.

## Description {#description}

Pour ce cas d’utilisation, la feuille de calcul Google Sheet est renseignée avec le pourcentage de réservation de deux restaurants : **`Restaurant1`** et **`Restaurant2`**. Une formule est appliquée en fonction des valeurs de `Restaurant1` et `Restaurant2` et selon la formule, la valeur 1 ou 2 est affectée à la colonne **AdTarget**.

Si la valeur de **`Restaurant1`** > **`Restaurant2`**, alors la valeur **1** est affectée à **AdTaget**, sinon la valeur **2** est affectée à **AdTarget**. La valeur 1 génère l’option *Steak food* et la valeur 2 fait apparaître l’option *Thai food* sur votre écran.

## Prérequis {#preconditions}

Avant de commencer à mettre en œuvre l’activation de la réservation, découvrez comment configurer le ***magasin de données***, la ***segmentation d’audience*** et l’***activation du ciblage pour les canaux*** dans un projet AEM Screens.

Consultez [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md) pour plus d’informations.

## Flux de base {#basic-flow}

Pour mettre en œuvre l’activation des réservations d’hébergements pour votre projet AEM Screens, suivez les étapes du cas d’utilisation :

1. **Remplissage des feuilles de calcul Google Sheets et ajout de la formule**.

   Par exemple, appliquez la formule à la troisième colonne **AdTarget**, comme illustré ci-dessous.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuration des segments dans les audiences selon les besoins**

   1. Accédez aux segments de votre audience (reportez-vous à l’***Étape 2 : configuration de la segmentation de l’audience*** dans la page **[Configuration de ContextHub dans AEM Screens](configuring-context-hub.md)** pour plus d’informations).
   1. Cliquez sur **Sheets A1 1**, puis sur **Modifier**.
   1. Cliquez sur la propriété de comparaison, puis sur l’icône **Configuration**.
   1. Cliquez sur **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**.
   1. Cliquez sur l’**Opérateur** **égal** dans le menu déroulant.
   1. Saisissez la **valeur** **1**.
   1. De même, cliquez sur les feuilles **Sheets A1 2**, puis sur **Modifier**.
   1. Cliquez sur la propriété de comparaison, puis sur l’icône **Configuration**.
   1. Cliquez sur **googlesheets/value/1/2** dans la liste déroulante de **Nom de la propriété**.
   1. Cliquez sur l’**opérateur** **2**.

1. Naviguez et cliquez sur votre canal (), puis sur **Modifier** dans la barre d’actions. Dans l’exemple suivant, **DataDrivenRestaurant**, la fonctionnalité est illustrée au moyen d’un canal de séquence.

   >[!NOTE]
   >
   >Votre canal doit déjà comporter une image par défaut et les audiences doivent être préconfigurées comme décrit dans [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Vos **configurations** **ContextHub** utilisant l’onglet **Propriétés** > **Personnalisation** du canal doivent déjà avoir été effectuées à ce stade.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Cliquez sur **Ciblage** dans l’éditeur, puis sur **Marque** et l’**Activité** dans le menu déroulant, et sur **Commencer le ciblage**.
1. **Vérification de l’aperçu**

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de calcul Google et mettez à jour sa valeur.
   1. Mettez à jour la valeur dans les colonnes **`Restaurant1`** et **`Restaurant2`**. Si **`Restaurant1`** > **`Restaurant2`,** vous devriez voir une image de cuisine de type *Steak*, autrement, l’image de la nourriture *Thaï* apparaît à l’écran.

   ![result5](assets/result5.gif)
