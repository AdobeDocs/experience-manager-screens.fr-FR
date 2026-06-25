---
title: Création avec des déclencheurs de données
description: Découvrez comment créer avec des déclencheurs de données dans un canal AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
TQID: https://experienceleague.adobe.com/Iqb4pREvZNLalXSE6sNTZPV-uwqzBJKmztLuQtWfCW0
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
source-wordcount: 421
ht-degree: 89%

---

# Création avec des déclencheurs de données {#authoring-with-data-triggers}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Cette section explique comment activer le ciblage dans vos canaux.

>[!IMPORTANT]
>
>La version minimale prenant en charge les triggers de données dans un canal AEM Screens est AEM 6.5.3 Feature Pack 3.

## Conditions préalables {#prereqs}

Avant de suivre les étapes ci-dessous afin d’activer le ciblage dans les canaux, apprenez les [termes clés de la configuration dans AEM Screens](configuring-context-hub.md) qui sont nécessaires pour comprendre ContextHub et le ciblage dans AEM Screens.

>[!IMPORTANT]
>
>Il est recommandé de comprendre et de définir les configurations ContextHub avant d’activer le ciblage dans un canal AEM Screens.

Suivez les liens ci-dessous pour en savoir plus :

1. **[Configuration du magasin de données](configuring-context-hub.md)**
1. **[Configuration de la segmentation de l’audience](configuring-context-hub.md)**

Après avoir suivi les étapes précédentes, vous pouvez activer le ciblage dans vos canaux.

## Présentation de la création avec des triggers de données {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Activation du ciblage dans un canal AEM Screens {#enabling-targeting}

Suivez les étapes ci-dessous pour activer le ciblage dans vos canaux.

1. Accédez à l’un des canaux AEM Screens. Les étapes suivantes montrent comment activer le ciblage à l’aide de **DataDrivenRetail** *(canal de séquence)* créé dans un canal AEM Screens.

1. Cliquez sur le canal **DataDrivenRetail**, puis sur **Propriétés** dans la barre d’actions.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Cliquez sur l’onglet **Personnalisation** pour définir les configurations ContextHub et cliquez sur le chemin ContextHub et Segments.

   1. Cliquez sur le **Chemin d’accès ContextHub** **libs** > **settings** > **cloudsettings** > **default** > **Configurations ContextHub**, puis sur **Sélectionner**.

   1. Cliquez sur le **Chemin d’accès aux segments** **conf** > **`We.Retail`**&#x200B;**settings** > **wcm** > **segments**, puis sur **Sélectionner**.

   1. Cliquez sur **Enregistrer et fermer**.

   >[!NOTE]
   >
   >Utilisez le chemin ContextHub et le chemin des segments où vous avez initialement enregistré vos segments et configurations ContextHub.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Accédez à **DataDrivenRetail** et cliquez dessus dans **DataDrivenAssets** > **Canaux**, puis cliquez sur **Modifier** dans la barre d’actions. Faites glisser les ressources et déposez-les dans votre éditeur de canal.

   >[!NOTE]
   >
   >Si vous avez tout correctement configuré, l’option **Ciblage** s’affiche dans la liste déroulante de l’éditeur, comme illustré ci-dessous.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Cliquez sur **Ciblage**.

1. Cliquez sur **Marque** et l’**Activité** dans le menu déroulant, puis sur **Commencer le ciblage**.

### En savoir plus : exemples de cas d’utilisation {#learn-more-example-use-cases}

Après avoir configuré ContextHub pour votre projet AEM Screens, vous pouvez suivre les différents cas d’utilisation pour comprendre comment les ressources déclenchées par des données jouent un rôle essentiel dans différents secteurs d’activité :

1. **[Activation ciblée du stock de vente au détail](retail-inventory-activation.md)**
1. **[Activation de la température de l’agence de voyages](local-temperature-activation.md)**
1. **[Activation de la réservation d’hébergements](hospitality-reservation-activation.md)**
