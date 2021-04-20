---
title: Activation de la température de l’agence de voyages
seo-title: Activation de la température de l’agence de voyages
description: Le cas d’utilisation suivant illustre l’utilisation de l’activation de la température locale de l’agence de voyages en fonction des valeurs renseignées dans Google Sheets.
seo-description: Le cas d’utilisation suivant illustre l’utilisation de l’activation de la température locale de l’agence de voyages en fonction des valeurs renseignées dans Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Création dans Screens
role: Administrateur, développeur
level: Intermédiaire
translation-type: ht
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: ht
source-wordcount: '481'
ht-degree: 100%

---


# Activation de la température de l’agence de voyages {#travel-center-temperature-activation}

Le cas d’utilisation suivant illustre l’utilisation de l’activation de la température locale de l’agence de voyages en fonction des valeurs renseignées dans Google Sheets.

## Description {#description}

Pour ce cas d’utilisation, si la valeur de votre feuille de calcul Google Sheets est inférieure à 50, une image avec des boissons chaudes apparaît, et si la valeur est supérieure ou égale à 50, une image avec des boissons fraîches apparaît. En cas de valeur différente ou d’absence de valeur, le lecteur affiche une image par défaut.

## Conditions préalables {#preconditions}

Avant de commencer à mettre en œuvre l’activation de la température locale de l’agence de voyages, vous devez apprendre à configurer le ***magasin de données***, la ***segmentation de l’audience*** et l’***activation du ciblage des canaux*** dans un projet AEM Screens.

Consultez [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md) pour plus d’informations.

## Flux de base {#basic-flow}

Suivez les étapes ci-dessous pour mettre en œuvre le cas d’utilisation de l’activation de température locale de l’agence de voyages :

1. **Remplissage des feuilles de calcul Google Sheets**

   1. Accédez à la feuille de calcul Google appelée ContextHubDemo.
   1. Ajoutez une colonne **Heading1** avec la valeur de température correspondante.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuration des segments dans les audiences selon les besoins**

   1. Accédez aux segments de votre audience (reportez-vous à l’***Étape 2 : configuration de la segmentation de l’audience*** dans la page **[Configuration de ContextHub dans la AEM Screens](configuring-context-hub.md)** pour plus d’informations).

   1. Sélectionnez **Sheets A1 1** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône de configuration pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**

   1. Sélectionnez l’**opérateur** **supérieur ou égal à** (greater-than-or-equal) dans le menu déroulant.

   1. Saisissez la **valeur** **50**

   1. De même, sélectionnez les feuilles **Sheets A1 2** et cliquez sur **Modifier**.

   1. Sélectionnez la **propriété Comparaison - Valeur** et cliquez sur l’icône Configurer pour modifier les propriétés.
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
   >Vous devez avoir défini vos **configurations** ContextHub **à l’aide de l’onglet** Propriétés **du canal -->** **Personnalisation.**

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Sélectionnez **Ciblage** dans l’éditeur. Sélectionnez ensuite **Marque** et l’**Activité** dans le menu déroulant, puis cliquez sur **Commencer le ciblage.**

   ![new_activity3](assets/new_activity3.gif)

1. **Vérification de l’aperçu**

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de calcul Google Sheet et mettez à jour sa valeur.
   1. Définissez une valeur inférieure à 50. Vous devriez voir une image de boissons fraîches. Si la valeur dans la feuille de calcul Google est supérieure ou égale à 50, vous devriez voir une image de boisson chaude.

   ![result3](assets/result3.gif)

