---
title: Activation de la température de l’agence de voyages
description: Avec AEM Screens, découvrez comment ce cas pratique illustre l’utilisation de l’activation de la température locale de l’agence de voyages en fonction des valeurs renseignées dans les feuilles de calcul Google.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: a8055c5f859e401f7b1da4f5d95f1268dee243ad
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 57%

---

# Activation de la température de l’agence de voyages {#travel-center-temperature-activation}

Le cas d’utilisation suivant illustre l’utilisation de l’activation de la température locale de l’agence de voyages en fonction des valeurs renseignées dans Google Sheets.

## Description {#description}

Pour ce cas d’utilisation, si la valeur dans les feuilles de calcul Google est inférieure à 50, une image avec des boissons chaudes s’affiche. Si la valeur est supérieure ou égale à 50, une image avec des boissons fraîches s’affiche. S’il existe une autre valeur ou aucune valeur, le lecteur affiche une image par défaut.

## Prérequis {#preconditions}

Avant de commencer à mettre en œuvre l’activation de la température locale de l’agence de voyages, vous devez apprendre à configurer le ***magasin de données***, la ***segmentation de l’audience*** et l’***activation du ciblage des canaux*** dans un projet AEM Screens.

Voir [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md) pour plus d’informations.

## Flux de base {#basic-flow}

Suivez les étapes ci-dessous pour mettre en œuvre le cas d’utilisation de l’activation de température locale de l’agence de voyages :

1. **Remplissage des feuilles de calcul Google Sheets**

   1. Accédez à la feuille de calcul Google appelée ContextHubDemo.
   1. Ajoutez une colonne avec **`Heading1`** avec la valeur correspondante pour la température.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuration des segments dans les audiences selon les besoins**

   1. Accédez aux segments de votre audience (voir ***Étape 2 : configuration de la segmentation de l’audience*** in **[Configuration de ContextHub dans AEM Screens](configuring-context-hub.md)** pour plus d’informations).

   1. Sélectionnez **Sheets A1 1** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône de configuration.
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**

   1. Sélectionnez l’**opérateur** **supérieur ou égal à** (greater-than-or-equal) dans le menu déroulant.

   1. Saisissez la **valeur** **50**

   1. De même, sélectionnez les feuilles **Sheets A1 2** et cliquez sur **Modifier**.

   1. Sélectionnez la variable **Propriété de comparaison - Valeur** et cliquez sur l’icône de configuration.
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**

   1. Sélectionnez l’**Opérateur** **inférieur à** (lower-than) dans le menu déroulant

   1. Saisissez la **valeur** **50**

1. Naviguez et sélectionnez votre canal (), puis cliquez sur **Modifier** dans la barre d’actions. Dans l’exemple ci-dessous, **DataDrivenWeather**, la fonctionnalité est illustrée au moyen d’un canal de séquence.

   >[!NOTE]
   >
   >Votre canal doit déjà comporter une image par défaut et les audiences doivent être préconfigurées comme décrit dans [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Vous devez avoir configuré votre **ContextHub** **Configurations** utilisation du canal **Propriétés** > **Personnalisation** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Sélectionnez **Ciblage** dans l’éditeur. Sélectionnez ensuite **Marque** et l’**Activité** dans le menu déroulant, puis cliquez sur **Commencer le ciblage.**

   ![new_activity3](assets/new_activity3.gif)

1. **Vérification de l’aperçu**

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de calcul Google Sheet et mettez à jour sa valeur.
   1. Définissez la valeur sur moins de 50. Vous devriez pouvoir voir une image d&#39;une boisson froide. Si la valeur de Google Sheets est supérieure ou égale à 50, une image de boisson chaude devrait s’afficher.

   ![result3](assets/result3.gif)
