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
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 33%

---

# Activation de la réservation d’hébergements {#hospitality-reservation-activation}

Le cas d’utilisation ci-dessous montre comment utiliser l’activation des réservations d’hébergements en fonction des valeurs renseignées dans Google Sheets.

## Description {#description}

Pour ce cas pratique, la feuille de calcul Google est renseignée avec le pourcentage de réservation de deux restaurants. **`Restaurant1`** et **`Restaurant2`**. Une formule est appliquée à partir des valeurs de `Restaurant1` et `Restaurant2` et, selon la formule, la valeur 1 ou 2 est affectée à la variable **AdTarget** Colonne.

Si la valeur de **`Restaurant1`** > **`Restaurant2`**, puis **AdTarget** est la valeur affectée **1** other **AdTarget** est la valeur affectée **2**. La valeur 1 génère une *Steak food* et Valeur 2 donnent un affichage de la valeur *La cuisine thaïlandaise* sur votre écran d’affichage.

## Prérequis {#preconditions}

Avant de commencer à mettre en oeuvre l’activation de la réservation, apprenez à configurer ***Entrepôt de données***, ***Segmentation de l’audience*** et ***Activation du ciblage des canaux*** dans un projet AEM Screens.

Consultez [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md) pour plus d’informations.

## Flux de base {#basic-flow}

Suivez les étapes du cas d’utilisation ci-dessous pour mettre en oeuvre l’activation de la réservation d’hébergements pour votre projet AEM Screens :

1. **Renseigner les feuilles de calcul Google Sheets et ajouter la formule**.

   Par exemple, appliquez la formule à la troisième colonne **AdTarget**, comme illustré ci-dessous.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuration des segments dans les audiences selon les besoins**

   1. Accédez aux segments de votre audience (reportez-vous à l’***Étape 2 : configuration de la segmentation de l’audience*** dans la page **[Configuration de ContextHub dans AEM Screens](configuring-context-hub.md)** pour plus d’informations).
   1. Cliquez sur le bouton **Sheets A1 1** et cliquez sur **Modifier**.
   1. Cliquez sur la propriété de comparaison, puis sur le **Configuration** Icône
   1. Cliquez sur **googlesheets/value/1/2** dans la liste déroulante de **Nom de la propriété**.
   1. Cliquez sur le bouton **Opérateur** as **equal** dans le menu déroulant.
   1. Saisissez la **valeur** **1**.
   1. De même, cliquez sur le bouton **Sheets A1 2** et cliquez sur **Modifier**.
   1. Cliquez sur la propriété de comparaison, puis sur le **Configuration** Icône
   1. Cliquez sur **googlesheets/value/1/2** dans la liste déroulante de **Nom de la propriété**.
   1. Cliquez sur le bouton **Opérateur** as **2**.

1. Recherchez et cliquez sur votre canal (), puis cliquez sur **Modifier** dans la barre d’actions. Dans l’exemple suivant, **DataDrivenRestaurant**, la fonctionnalité est illustrée au moyen d’un canal de séquence.

   >[!NOTE]
   >
   >Votre canal doit déjà comporter une image par défaut et les audiences doivent être préconfigurées comme décrit dans [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Votre **ContextHub** **Configurations** utilisation du canal **Propriétés** > **Personnalisation** a déjà dû être configuré.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Cliquez sur **Ciblage** dans l’éditeur, puis cliquez sur **Marque** et la variable **Activité** dans le menu déroulant et cliquez sur **Commencer le ciblage**.
1. **Vérification de l’aperçu**

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de calcul Google et mettez à jour sa valeur.
   1. Mettez à jour la valeur dans **`Restaurant1`** et **`Restaurant2`** colonnes. If **`Restaurant1`** > **`Restaurant2`,** vous devriez pouvoir afficher une image de *Steak* autrement, *Thaï* image de la nourriture s’affiche sur votre écran.

   ![result5](assets/result5.gif)
