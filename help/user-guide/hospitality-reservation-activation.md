---
title: Activation de la réservation d’hébergements
description: Découvrez comment ce cas pratique illustre l’utilisation de l’activation des réservations d’hébergements en fonction des valeurs renseignées dans les feuilles de calcul Google Sheets.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 48%

---

# Activation de la réservation d’hébergements {#hospitality-reservation-activation}

Le cas d’utilisation ci-dessous montre comment utiliser l’activation des réservations d’hébergements en fonction des valeurs renseignées dans Google Sheets.

## Description {#description}

Pour ce cas d’utilisation, la feuille de calcul Google est renseignée avec le pourcentage de réservation de deux restaurants. **`Restaurant1`** et **`Restaurant2`**. Une formule est appliquée à partir des valeurs de `Restaurant1` et `Restaurant2` et selon la formule, la valeur 1 ou 2 est affectée à la variable **AdTarget** Colonne.

Si la valeur de **`Restaurant1`** > **`Restaurant2`**, puis **AdTarget** est la valeur affectée **1** other **AdTarget** est la valeur affectée **2**. Valeur 1 générée *Steak food* Option et Valeur 2 donne l’affichage de *La cuisine thaïlandaise* sur votre écran d’affichage.

## Prérequis {#preconditions}

Avant de commencer à mettre en œuvre l’activation de la réservation, vous devez apprendre à configurer le ***magasin de données***, la ***segmentation d’audience*** et l’***activation du ciblage pour les canaux*** dans un projet AEM Screens.

Voir [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md) pour plus d’informations.

## Flux de base {#basic-flow}

Suivez les étapes du cas d’utilisation ci-dessous pour mettre en oeuvre l’activation de la réservation d’hébergements pour votre projet AEM Screens :

1. **Renseigner les feuilles de calcul Google Sheets et ajouter la formule**.

   Par exemple, appliquez la formule à la troisième colonne **AdTarget**, comme illustré ci-dessous.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuration des segments dans les audiences selon les besoins**

   1. Accédez aux segments de votre audience (voir ***Étape 2 : configuration de la segmentation de l’audience*** in **[Configuration de ContextHub dans AEM Screens](configuring-context-hub.md)** pour plus d’informations).
   1. Sélectionnez **Sheets A1 1** et cliquez sur **Modifier**.
   1. Sélectionnez la propriété de comparaison et cliquez sur le bouton **Configuration** Icône
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante de **Nom de la propriété**.
   1. Sélectionnez la variable **Opérateur** as **equal** dans le menu déroulant.
   1. Saisissez la **valeur** **1**.
   1. De même, sélectionnez les feuilles **Sheets A1 2** et cliquez sur **Modifier**.
   1. Sélectionnez la propriété de comparaison et cliquez sur le bouton **Configuration** Icône
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante de **Nom de la propriété**.
   1. Sélectionnez la variable **Opérateur** as **2**.

1. Naviguez et sélectionnez votre canal (), puis cliquez sur **Modifier** dans la barre d’actions. Dans l’exemple suivant, **DataDrivenRestaurant**, la fonctionnalité est illustrée au moyen d’un canal de séquence.

   >[!NOTE]
   >
   >Votre canal doit déjà comporter une image par défaut et les audiences doivent être préconfigurées comme décrit dans [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Vous devez avoir configuré votre **ContextHub** **Configurations** utilisation du canal **Propriétés** > **Personnalisation** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Sélectionnez **Ciblage** dans l’éditeur. Sélectionnez ensuite **Marque** et l’**Activité** dans le menu déroulant, puis cliquez sur **Commencer le ciblage**.
1. **Vérification de l’aperçu**

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de calcul Google et mettez à jour sa valeur.
   1. Mettez à jour la valeur dans **`Restaurant1`** et **`Restaurant2`** colonnes. If **`Restaurant1`** > **`Restaurant2`,** vous devriez pouvoir afficher une image de *Steak* autrement, *Thaï* image de la nourriture s’affiche sur votre écran.

   ![result5](assets/result5.gif)
