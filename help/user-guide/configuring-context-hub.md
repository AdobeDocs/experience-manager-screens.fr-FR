---
title: Configuration de ContextHub dans AEM Screens
description: Découvrez ContextHub dans le moteur de ciblage, afin de pouvoir définir le magasin de données pour le changement de contenu du déclencheur de données.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 100%

---

# Configuration de ContextHub dans AEM Screens {#configuring-contexthub-in-aem-screens}

Cette section met l’accent sur la création et la gestion des modifications de ressources liées aux données à l’aide d’un magasin de données.

## Termes clés {#key-terms}

Avant de vous attaquer aux détails de la création et de la gestion des canaux pilotés par l’inventaire dans votre projet AEM Screens, vous devez connaître quelques-uns des termes clés importants et pertinents pour les différents scénarios.

**Marque** : description de votre projet de haut niveau.

**Zone** : fait référence au nom de votre projet AEM Screens, comme par exemple signalétique numérique publicitaire.

**Activité** : définit les règles de catégorie telles que Basé sur l’inventaire, Basé sur la météo ou Basé sur la disponibilité du service.

**Audience** : définit la règle.

**Segment** : version de la ressource à lire pour la règle donnée. Par exemple, si la température est inférieure à 50 degrés Fahrenheit, l’écran affiche une image d’une boisson chaude. Dans le cas contraire, une boisson froide est affichée.

Le diagramme ci-dessous illustre visuellement comment les configurations ContextHub coïncident avec l’activité, l’audience et les canaux.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Prérequis {#preconditions}

Avant de commencer à définir les configurations ContextHub d’un projet AEM Screens, vous devez configurer Google Sheets (à des fins de démonstration).

>[!IMPORTANT]
>
>Google Sheets est utilisé dans l’exemple suivant à titre d’exemple de système de base de données à partir duquel les valeurs sont récupérées et uniquement à des fins pédagogiques. Adobe n’approuve pas l’utilisation de Google Sheets dans des environnements de production.
>
>Pour plus d’informations, reportez-vous à la section [Obtenir la clé API](https://developers.google.com/maps/documentation/javascript/get-api-key) dans la documentation Google.

## Étape 1 : configuration d’un magasin de données {#step-setting-up-a-data-store}

Vous pouvez configurer le magasin de données en tant qu’événement d’E/S local ou d’événement de base de données local.

L’exemple suivant de déclencheurs de données au niveau des ressources présente un événement de base de données local. L’événement configure un magasin de données, tel qu’une feuille de calcul Excel, qui vous permet d’utiliser les configurations et le chemin des segments ContextHub vers le canal AEM Screens.

Après avoir configuré correctement la feuille `google`, comme illustré dans l’exemple ci-dessous :

![image](/help/user-guide/assets/context-hub/context-hub1.png)

La validation suivante correspond à ce que vous verrez si vous vérifiez votre connexion en saisissant les deux valeurs `*google sheet ID*` et `*API key*`, au format indiqué ci-dessous :

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![image](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>L’exemple spécifique ci-dessous présente Google Sheets comme un magasin de données chargé de déclencher un changement de ressource si la valeur est supérieure à 100 ou inférieure à 50.

## Étape 2 : paramétrage des configurations de magasin {#step-setting-store-configurations}

1. **Parcourir ContextHub**

   Accédez à votre instance AEM et cliquez sur l’icône Outils dans la barre latérale de gauche. Cliquez sur **Sites** > **ContextHub**, comme illustré ci-dessous.

   ![image](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Création une configuration de magasin ContextHub**

   1. Accédez au conteneur de configuration intitulé **screens**.

   1. Cliquez sur **Créer** > **Créer un conteneur de configuration** et saisissez le titre **ContextHubDemo**.

      ![image](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Accédez** à **ContextHubDemo** > **Créer** **Configuration ContentHub**, puis cliquez sur **Enregistrer**.

      >[!NOTE]
      > Après avoir cliqué sur **Enregistrer**, vous vous trouvez ensuite sur l’écran **Configuration ContextHub**.

   1. Sur l’écran **Configuration ContextHub**, cliquez sur **Créer** > **Configuration de magasin ContextHub**.

   ![image](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >Dans le cadre d’AEM 6.5 Feature Pack 4 ou d’AEM 6.4 Feature Pack 8, les clients doivent effectuer une mise à jour de `/conf/screens/settings/cloudsettings` vers `sling:Folder`.
   >
   >Suivez les étapes ci-dessous :
   >
   >1. Accédez à CRXDE Lite, puis à `/conf/screens/settings/cloudsettings`.
   >1. Vérifiez que `cloudsettings jcr:primaryType` se trouve dans `sling:Folder`. Si `jcr:primaryType` ne se trouve pas dans `sling:folder`, passez aux étapes suivantes.
   >1. Cliquez avec le bouton droit sur `/conf/screens/settings` et créez un nœud avec le *nom* **`cloudsettings1`** et le *type* **`sling:Folder`**, puis enregistrez les modifications.
   >1. Déplacez tous les nœuds sous `/conf/screens/settings/cloudsettings` vers `cloudsettings1`.
   >1. Supprimez `cloudsettings` et enregistrez.
   >1. Renommez `cloudsettings1` en `cloudsettings` et enregistrez.
   >1. Observez que `/conf/screens/settings/cloudsettings` dispose du `jcr:primaryType` `sling:Folder`.
   >
   >Vous devez suivre ces étapes dans l’instance de création et de publication avant ou après la mise à niveau.

   1. Saisissez le **Titre** **Google Sheets**, le **Nom du magasin** **`googlesheets`** et le **Type de magasin** **c`ontexthub.generic-jsonp`**, puis cliquez sur **Suivant**.

      >[!CAUTION]
      >Si vous utilisez Adobe Experience Manager (AEM) 6.4, saisissez le **Titre de configuration** **`googlesheets`** et le **Type de magasin** **c`ontexthub.generic-jsonp`**.

      ![image](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Entrez votre configuration json spécifique. Vous pouvez par exemple utiliser le code json ci-dessous à des fins de démonstration et cliquer sur **Enregistrer**. La configuration du magasin s’affiche sous le titre **Google Sheets** dans la configuration ContextHub.

      >[!IMPORTANT]
      >Veillez à remplacer le code par l’`*<Sheet ID>*` et la `*<API Key>*`, que vous avez récupérés lors de la configuration des Google Sheets.

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      >
      >Dans l’exemple de code ci-dessus, **pollInterval** définit la fréquence d’actualisation des valeurs (en ms).
      >
      >Remplacez le code par l’`*<Sheet ID>*` et la `*<API Key>*`, que vous avez récupérés lors de la configuration des Google Sheets.

      >[!CAUTION]
      >
      >Si vous créez vos documents Google Sheets pour stocker des configurations en dehors du dossier global (par exemple, dans votre propre dossier de projet), le ciblage ne fonctionnera pas immédiatement.

1. **Configuration de la segmentation du magasin**

   1. Accédez à **Configuration du magasin ContentHub** et créez une autre configuration de magasin dans le conteneur de configuration AEM Screens, puis définissez le **Titre** sur **segmentation-contexthub**, le **Nom du magasin** sur **segmentation** et le **Type de magasin** sur **aem.segmentation**.

      ![image](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Cliquez sur **Suivant**, puis sur **Enregistrer**.

      >[!NOTE]
      >Ignorez le processus de définition du fichier json et laissez-le vide.


## Étape 3 : configuration de segments dans les audiences {#setting-up-audience}

1. **Création de segments dans les audiences**

   1. Dans votre instance AEM, accédez à **Personnalisation** > **Audiences** > **screens**.

   1. Cliquez sur **Créer** > **Créer un segment ContextHub.** La boîte de dialogue **Nouveau segment ContextHub** s’ouvre.

   1. Saisissez le **Titre** `**Higherthan50**`, puis cliquez sur **Créer**. De la même manière, créez un autre segment intitulé `**Lowerthan50**`.

      ![image](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Sélectionnez le segment `**Higherthan50**`, puis cliquez sur **Propriétés** dans la barre d’actions.
      ![image](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Sélectionnez l’onglet **Personnalisation** dans **Propriétés du segment**. Définissez le **Chemin d’accès ContextHub** sur `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` et le **Chemin d’accès aux segments** sur `/conf/screens/settings/wcm/segments`, puis cliquez sur **Enregistrer**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/context-hub/context-hub13.png)

   1. De même, définissez le **Chemin d’accès ContextHub** et le **Chemin d’accès aux segments** pour le segment `**Lowerthan50**`.

## Étape 4 : configuration de la marque et de la zone {#setting-brand-area}

Pour créer une marque dans vos activités et une zone dans votre marque :

1. **Création d’une marque dans les activités**

   1. Dans votre instance AEM, accédez à **Personnalisation** > **Activités**.

   1. Cliquez sur **Créer** > **Créer une marque**.

   1. Dans l’assistant **Créer une page**, cliquez sur **Marque**, puis sur **Suivant**.

   1. Saisissez le **Titre** **ScreensBrand**, puis cliquez sur **Créer**. Votre marque a été créée, comme illustré ci-dessous.

      ![image](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >Problème connu :
      >Pour ajouter une zone, supprimez le principal de l’URL, par exemple
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Création d’une zone dans votre marque**

   Pour créer une zone dans la marque, procédez comme suit :

   1. Cliquez sur **Créer**, puis sur **Créer une zone**.

      ![image](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Sélectionnez **Zone** dans l’assistant **Créer une page**, puis cliquez sur **Suivant**.

   1. Saisissez le **Titre** **ScreensValue**, puis cliquez sur **Créer**.
Une zone sera créée dans votre marque.

## Étape 5 : création de segments dans une activité {#step-setting-up-audience-segmentation}

Après avoir configuré un magasin de données et défini votre activité (marque et zone), procédez comme suit pour créer des segments dans l’activité.

1. **Création de segments dans les activités**

   1. Dans votre instance AEM, accédez à **Personnalisation** > **Activités** > **ScreensBrand** > **ScreensValue**.

   1. Cliquez sur **Créer** > **Créer une activité.** L’**assistant Configurer l’activité** s’ouvre.

   1. Saisissez le **titre** **ValueCheck50** et le **nom** **valuecheck50**. Sélectionnez le **Moteur de ciblage** **ContextHub (AEM)** dans la liste déroulante, puis cliquez sur **Suivant**.

      ![image](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Cliquez sur **Ajouter une expérience** dans l’assistant `**Configure Activity**`.

   1. Dans **Audiences**, cliquez sur `**Higherthan50**`, puis sur **Ajouter une expérience** et saisissez le **Titre** `**higherthan50**` et le **Nom** `**higherthan50**`. Cliquez sur **OK**.

   1. Dans **Audiences**, cliquez sur `**Lowerthan50**`, puis sur **Ajouter une expérience** et saisissez le **Titre** `**lowerthan50**` et le **Nom** `**lowerthan50**`. Cliquez sur **OK**.

   ![image](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Cliquez sur **Suivant**, puis sur **Enregistrer**. L’activité `**ValueCheck50**` est désormais créée et configurée.

      ![image](/help/user-guide/assets/context-hub/context-hub16.png)

## Étape 5 : modification des segments dans les audiences{#editing-audience-segmentation}

1. **Modification des segments**

   1. Dans votre instance AEM, accédez à **Personnalisation** > **Audiences** > **screens**.

   1. Sélectionnez le segment `**Higherthan50**` et cliquez sur **Modifier** dans la barre d’actions.

   1. Faites glisser le composant **Comparaison : Propriété - Valeur** et déposez-le dans l’éditeur.

   1. Cliquez sur l’icône en forme de clé à molette pour ouvrir la boîte de dialogue **Comparer une propriété et une valeur**.

   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante du **Nom de la propriété**.

      >[!NOTE]
      > L’élément **googlesheets/value/1/0** fait référence à la ligne 2 et à la colonne renseignée dans `google` Sheets représentée ci-dessous :

      ![image](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Sélectionnez l’**Opérateur** **supérieur à** dans le menu déroulant.

   1. Saisissez la **Valeur** **70**.

      >[!NOTE]
      >
      >AEM valide alors vos données dans la feuille de calcul Google en affichant votre segment en vert.

      ![image](/help/user-guide/assets/context-hub/context-hub18.png)

   De même, modifiez les valeurs de propriété en indiquant `**Lowerthan50**`.

   1. Faites glisser le composant **Comparaison : Propriété - Valeur** et déposez-le dans l’éditeur.

   1. Cliquez sur l’icône en forme de clé à molette.

   1. Dans la boîte de dialogue **Comparer une propriété avec une valeur**, sélectionnez **googlesheets/value/1/0** dans la liste déroulante du **Nom de la propriété**.

   1. Sélectionnez l’**Opérateur** **inférieur à** dans le menu déroulant.

   1. Saisissez la **Valeur** **50**.


## Activation du ciblage dans les canaux {#step-enabling-targeting-in-channels}

Suivez les étapes ci-dessous pour activer le ciblage dans vos canaux.

1. Accédez à l’un des canaux AEM Screens. Les étapes suivantes montrent comment activer le ciblage à l’aide de **DataDrivenChannel** créé dans un canal AEM Screens.

1. Sélectionnez le canal **TargetChannel** et cliquez sur **Propriétés** dans la barre d’actions.

   ![image](/help/user-guide/assets/context-hub/context-hub19.png)

1. Cliquez sur l’onglet **Personnalisation** pour définir les configurations ContextHub.

   1. Définissez le **Chemin d’accès ContextHub** sur `/conf/screens/settings/wcm/segments` et le **Chemin d’accès de segments** sur `/conf/screens/settings/wcm/segments`.
   1. Définissez la marque sur **ScreensBrand** dans la liste déroulante. **Définissez la référence de zone** sur **ScreensValue**.

   1. Cliquez sur **Enregistrer et fermer**.

      >[!NOTE]
      >
      >Utilisez le chemin ContextHub et le chemin des segments où vous avez initialement enregistré vos segments et configurations ContextHub.

      ![Image](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. Accédez au canal **TargetChannel** et sélectionnez-le, puis cliquez sur **Modifier** dans la barre d’actions.

      >[!NOTE]
      >
      >Si vous avez tout configuré correctement, l’option **Ciblage** s’affiche dans la liste déroulante de l’éditeur, comme illustré ci-dessous.

      ![image](/help/user-guide/assets/context-hub/context-hub21.png)

## En savoir plus : exemples de cas d’utilisation {#learn-more-example-use-cases}

Après avoir configuré ContextHub pour votre projet AEM Screens, vous pouvez suivre les différents cas d’utilisation pour comprendre comment les ressources déclenchées par des données jouent un rôle essentiel dans différents secteurs d’activité :

1. **[Activation ciblée du stock de vente au détail](retail-inventory-activation.md)**
1. **[Activation de la température de l’agence de voyages](local-temperature-activation.md)**
1. **[Activation de la réservation d’hébergements](hospitality-reservation-activation.md)**
