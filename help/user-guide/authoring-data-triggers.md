---
title: Création avec des déclencheurs de données
seo-title: Création avec des déclencheurs de données
description: Suivez cette page pour apprendre à créer des déclencheurs de données.
translation-type: tm+mt
source-git-commit: 9490eb2aa089268884d0f39a32eb8c53de110ed7

---


# Création avec des déclencheurs de données {#authoring-with-data-triggers}

Cette section explique comment activer le ciblage dans votre  de.

>[!IMPORTANT]
> La version minimale qui prend en charge les déclencheurs de données dans un AEM Screens est AEM 6.4.3 Feature Pack 3.

## Conditions préalables {#prereqs}

Avant de suivre les étapes ci-dessous pour activer le ciblage dans les  de, vous devez connaître les termes [clés de la section Configuration dans les écrans](configuring-context-hub.md) AEM requise pour comprendre ContextHub et le ciblage dans les écrans AEM.

>[!IMPORTANT]
> Il est recommandé de comprendre et de configurer les configurations ContextHub avant d’activer le ciblage dans un  d’écrans AEM.

Suivez les liens ci-dessous pour en savoir plus :

1. **[Configuration du magasin de données](configuring-context-hub.md)**
1. **[Configuration de   de la segmentation du](configuring-context-hub.md)**

Une fois les étapes précédentes terminées, vous êtes prêt à activer le ciblage dans votre .

## Présentation de la création avec des déclencheurs de données {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Activation du ciblage dans un AEM Screens {#enabling-targeting}

Suivez les étapes ci-dessous pour activer le ciblage dans vos canaux.

1. Accédez à l’un des canaux AEM Screens. The following steps demonstrate how to enable targeting by using **DataDrivenRetail** *(sequence channel)* created in an AEM Screens Channel.

1. Sélectionnez le canal **DataDrivenRetail** et cliquez sur **Propriétés** dans la barre d’actions.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Sélectionnez l’onglet **Personnalisation** pour définir les configurations ContextHub.

   1. Sélectionnez le **Chemin d’accès ContextHub** **libs** > **settings** > **cloudsettings** > **default** > **Configurations ContextHub** et cliquez sur **Sélectionner**.

   1. Sélectionnez le **chemin d’accès aux segments** **conf** > **We.Retail** > **settings** > **wcm** > **segments** et cliquez sur **Sélectionner**.

   1. Cliquez sur **Enregistrer et fermer**.
   >[!NOTE]
   >
   >Utilisez le chemin ContextHub et le chemin des segments où vous avez initialement enregistré vos segments et configurations ContextHub.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Accédez à **DataDrivenRetail** et sélectionnez-le dans **DataDrivenAssets** > **Canaux**, puis cliquez sur **Modifier** dans la barre d’actions.

   >[!NOTE]
   >
   >Si vous avez tout correctement configuré, l’option **Ciblage** s’affiche dans la liste déroulante de l’éditeur, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   >
   >Une fois que vous avez défini les configurations ContextHub pour votre canal, veillez à respecter les étapes 1 à 4 précédentes pour les trois autres canaux de séquence si vous souhaitez suivre tous les cas d’utilisation ci-dessous.

### En savoir plus : exemples de cas d’utilisation {#learn-more-example-use-cases}

Après avoir configuré ContextHub pour votre projet AEM Screens, vous pouvez suivre les différents cas d’utilisation pour comprendre comment les ressources déclenchées par des données jouent un rôle essentiel dans différents secteurs d’activité :

1. **[Activation ciblée du stock de vente au détail](retail-inventory-activation.md)**
1. **[Activation de la température de l’agence de voyages](local-temperature-activation.md)**
1. **[Activation de la réservation d’hébergements](hospitality-reservation-activation.md)**

