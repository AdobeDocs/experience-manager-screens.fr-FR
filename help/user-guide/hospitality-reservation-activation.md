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
TQID: https://experienceleague.adobe.com/WwFvV7ZVDRUPpsXWQUKYkz6-gmEjBcpkApcHxzx5vII
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: ff2b9b37-92e0-45fc-b853-379d44c08c89
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 499
ht-degree: 88%

---

# Activation de la réservation d’hébergements {#hospitality-reservation-activation}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

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
   1. Sélectionnez **Sheets A1 1** et cliquez sur **Modifier**.
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

1. Sélectionnez **Ciblage** dans l’éditeur. Sélectionnez ensuite la **Marque** et l’**Activité** dans le menu déroulant, puis cliquez sur **Commencer le ciblage**.
1. **Vérification de l’aperçu**

   1. Cliquez sur **Aperçu.** Ouvrez également vos feuilles Google et mettez à jour sa valeur.
   1. Mettez à jour la valeur dans les colonnes **`Restaurant1`** et **`Restaurant2`**. Si **`Restaurant1`** > **`Restaurant2`,** vous devriez voir une image de cuisine de type *Steak*, autrement, l’image de la nourriture *Thaï* apparaît à l’écran.

   ![result5](assets/result5.gif)
