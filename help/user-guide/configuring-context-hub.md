---
title: Configuration de ContextHub dans AEM Screens
description: Découvrez ContextHub dans le moteur de ciblage afin de pouvoir définir l’entrepôt de données pour le changement de contenu du déclencheur de données.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '1452'
ht-degree: 46%

---

# Configuration de ContextHub dans AEM Screens {#configuring-contexthub-in-aem-screens}

Cette section met l’accent sur la création et la gestion des modifications de ressources pilotées par les données à l’aide d’un entrepôt de données.

## Termes clés {#key-terms}

Avant d’entrer dans les détails de la création et de la gestion des canaux pilotés par l’inventaire dans votre projet AEM Screens, découvrez certains des termes clés des différents scénarios.

**Marque** - Description de votre projet de haut niveau.

**Zone** : nom de votre projet AEM Screens, par exemple signalétique digitale

**Activité** - Définit les règles de catégorie telles que Basé sur l’inventaire, Basé sur la météo ou Basé sur la disponibilité du service.

**Audience** - Définit la règle.

**Segment** - Version de la ressource à lire pour la règle donnée. Par exemple, si la température est inférieure à 50 degrés Fahrenheit, l’écran affiche une image d’une boisson chaude, autrement une boisson froide.

Le diagramme ci-dessous illustre visuellement comment les configurations ContextHub coïncident avec l’activité, l’audience et les canaux.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Prérequis {#preconditions}

Avant de commencer à définir les configurations ContextHub d’un projet AEM Screens, vous devez configurer Google Sheets (à des fins de démonstration).

>[!IMPORTANT]
>
>Google Sheets est utilisé dans l’exemple suivant à titre d’exemple de système de base de données à partir duquel les valeurs sont récupérées et uniquement à des fins pédagogiques. Adobe n’approuve pas l’utilisation de Google Sheets dans des environnements de production.
>
>Pour plus d’informations, voir [Obtenir la clé API](https://developers.google.com/maps/documentation/javascript/get-api-key) dans la documentation de Google.

## Étape 1 : configuration d’un magasin de données {#step-setting-up-a-data-store}

Vous pouvez configurer le magasin de données en tant qu’événement d’E/S local ou d’événement de base de données local.

L’exemple suivant de triggers de données au niveau des ressources présente un événement de base de données local qui configure un entrepôt de données, tel qu’une feuille Excel, qui vous permet d’utiliser les configurations ContextHub et le chemin d’accès aux segments vers le canal AEM Screens.

Après avoir configuré la variable `google` , comme illustré dans l’exemple ci-dessous :

![image](/help/user-guide/assets/context-hub/context-hub1.png)

La validation suivante correspond à ce que vous voyez lorsque vous vérifiez votre connexion en saisissant les deux valeurs, `*google sheet ID*` et `*API key*` au format ci-dessous :

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![image](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>L’exemple spécifique ci-dessous présente les feuilles de calcul Google Sheets comme un entrepôt de données qui déclenche une modification de ressource si la valeur est supérieure à 100 ou inférieure à 50.

## Étape 2 : paramétrage des configurations de magasin {#step-setting-store-configurations}

1. **Accès à ContextHub**

   Accédez à votre instance AEM et cliquez sur l’icône Outils dans la barre latérale gauche. Cliquez sur **Sites** > **ContextHub**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Création d’une configuration de magasin ContextHub**

   1. Accédez au conteneur de configuration intitulé **screens**.

   1. Sélectionner **Créer** > **Créer un conteneur de configuration** et saisissez le titre **ContextHubDemo**.

      ![image](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Accédez** à **ContextHubDemo** > **Créer** **Configuration ContentHub**, puis cliquez sur **Enregistrer**.

      >[!NOTE]
      > Après avoir sélectionné **Enregistrer**, vous êtes dans la variable **Configuration ContextHub** écran.

   1. Dans la **Configuration ContextHub** écran, sélectionnez **Créer** > **Configuration du magasin ContentHub**

   ![image](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >Dans le cadre d’AEM 6.5 Feature Pack 4 ou d’AEM 6.4 Feature Pack 8, les clients doivent effectuer une mise à jour de `/conf/screens/settings/cloudsettings` vers `sling:Folder`.
   >
   >Suivez les étapes ci-dessous :
   >
   >1. Accédez à CRXDE Lite, puis à `/conf/screens/settings/cloudsettings`.
   >1. Vérifiez que `cloudsettings jcr:primaryType` se trouve dans `sling:Folder`. Si `jcr:primaryType` ne se trouve pas dans `sling:folder`, passez aux étapes suivantes.
   >1. Clic droit `/conf/screens/settings` et créez un noeud avec *name* as **cloudsettings1** et *Type* as **sling:Folder** et enregistrez les modifications.
   >1. Déplacez tous les nœuds sous `/conf/screens/settings/cloudsettings` vers `cloudsettings1`.
   >1. Supprimez `cloudsettings` et enregistrez.
   >1. Renommez `cloudsettings1` en `cloudsettings` et enregistrez.
   >1. Observez que `/conf/screens/settings/cloudsettings` has `jcr:primaryType` as `sling:Folder`.
   >
   >Procédez comme suit dans les sections Création et Publication avant ou après la mise à niveau.

   1. Saisissez le **Titre** **Google Sheets**, le **Nom du magasin** **googlesheets** et le **Type de magasin** **contexthub.generic-jsonp**, puis cliquez sur **Suivant**.

      >[!CAUTION]
      >Si vous utilisez Adobe Experience Manager (AEM) 6.4, saisissez le **Titre de configuration** **googlesheets** et le **Type de magasin** **contexthub.generic-jsonp**.

      ![image](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Entrez votre configuration json spécifique. Par exemple, vous pouvez utiliser le fichier json suivant à des fins de démonstration et sélectionner **Enregistrer**. La configuration du magasin s’affiche sous le titre **Google Sheets** dans la configuration ContextHub.

      >[!IMPORTANT]
      >Veillez à remplacer le code par votre `*<Sheet ID>*` et `*<API Key>*`, récupéré lors de la configuration des feuilles de calcul Google Sheets.

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
      >Dans l’exemple de code ci-dessus, **pollInterval** définit la fréquence d’actualisation des valeurs (en millisecondes).
      >
      >Remplacez le code par votre `*<Sheet ID>*` et `*<API Key>*`, récupéré lors de la configuration des feuilles de calcul Google Sheets.

      >[!CAUTION]
      >
      >Si vous créez des configurations de magasin Google Sheets en dehors du dossier global (par exemple, dans votre propre dossier de projet), le ciblage ne fonctionne pas d’usine.

1. **Configuration de la segmentation du magasin**

   1. Accédez à **Configuration du magasin ContentHub** et créez une autre configuration de magasin dans le conteneur de configuration AEM Screens, puis définissez la variable **Titre** as **segmentation-contexthub**, **Nom de la boutique** as **segmentation** et **Type de magasin** as **aem.segmentation**.

      ![image](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Cliquez sur **Suivant**, puis sur **Enregistrer**.

      >[!NOTE]
      >Ignorez le processus de définition du fichier json et laissez-le vide.


## Étape 3 : configuration de segments dans les audiences {#setting-up-audience}

1. **Création de segments dans les audiences**

   1. Dans votre instance AEM, accédez à **Personnalisation** > **Audiences** > **screens**.

   1. Cliquez sur **Créer** > **Créer un segment ContextHub.** La boîte de dialogue **Nouveau segment ContextHub** s’ouvre.

   1. Saisissez le **Titre** as `**Higherthan50**` et cliquez sur **Créer**. De même, créez un autre segment intitulé `**Lowerthan50**`.

      ![image](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Sélection du segment `**Higherthan50**` et cliquez sur **Propriétés** dans la barre d’actions.
      ![image](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Sélectionnez l’onglet **Personnalisation** dans **Propriétés du segment**. Définissez le **Chemin d’accès ContextHub** sur `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` et le **Chemin d’accès aux segments** sur `/conf/screens/settings/wcm/segments`, puis cliquez sur **Enregistrer**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/context-hub/context-hub13.png)

   1. De même, définissez la variable **Chemin ContextHub** et **Chemin d’accès aux segments** pour `**Lowerthan50**` également.

## Étape 4 : configuration de la marque et de la zone {#setting-brand-area}

Pour créer une marque dans vos activités et zones sous la marque, procédez comme suit :

1. **Création d’une marque dans les activités**

   1. Accédez à l’instance AEM à partir de l’instance **Personnalisation** > **Activités**.

   1. Sélectionner **Créer** > **Créer une marque**.

   1. Dans l’assistant **Créer une page**, sélectionnez **Marque** et cliquez sur **Suivant**.

   1. Saisissez le **Titre** **ScreensBrand**, puis cliquez sur **Créer**. Votre marque a été créée, comme illustré ci-dessous.

      ![image](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >Problème connu :
      >Pour ajouter une zone, supprimez l’élément principal de l’URL, comme
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Création d’une zone dans votre marque**

   Pour créer une zone dans la marque, procédez comme suit :

   1. Sélectionner **Créer** puis **Créer une zone**.

      ![image](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Sélectionner **Zone** de la **Créer une page** assistant et sélectionnez **Suivant**.

   1. Saisissez le **Titre** as **ScreensValue** et sélectionnez **Créer**.
Une zone est créée dans votre marque.

## Étape 5 : création de segments dans une activité {#step-setting-up-audience-segmentation}

Après avoir configuré un entrepôt de données et défini votre activité (marque et zone), suivez les étapes ci-dessous pour créer des segments dans votre activité.

1. **Création de segments dans les activités**

   1. Dans votre instance AEM, accédez à **Personnalisation** > **Activités** > **ScreensBrand** > **ScreensValue**.

   1. Sélectionner **Créer** > **Création d’une activité.** L’**assistant Configurer l’activité** s’ouvre.

   1. Saisissez le **titre** **ValueCheck50** et le **nom** **valuecheck50**. Sélectionnez la variable **Moteur de ciblage** as **ContextHub (AEM)** dans la liste déroulante, puis sélectionnez **Suivant**.

      ![image](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Sélectionner **Ajouter une expérience** de la `**Configure Activity**` assistant.

   1. Dans la **Audiences**, sélectionnez la variable `**Higherthan50**` et sélectionnez **Ajouter une expérience** et saisissez la variable **Titre** as `**higherthan50**` **Nom** as `**higherthan50**`. Sélectionner **Ok**.

   1. Dans la **Audiences**, sélectionnez la variable `**Lowerthan50**` et sélectionnez **Ajouter une expérience** et saisissez la variable **Titre** as `**lowerthan50**` **Nom** as `**lowerthan50**`. Sélectionner **Ok**.

   ![image](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Sélectionner **Suivant** puis **Enregistrer**. `**ValueCheck50**` l’activité est maintenant créée et configurée.

      ![image](/help/user-guide/assets/context-hub/context-hub16.png)

## Étape 5 : modification des segments dans les audiences{#editing-audience-segmentation}

1. **Modification des segments**

   1. Dans votre instance AEM, accédez à **Personnalisation** > **Audiences** > **screens**.

   1. Sélection du segment `**Higherthan50**`, puis sélectionnez **Modifier** dans la barre d’actions.

   1. Faites glisser le composant **Comparaison : Propriété - Valeur** et déposez-le dans l’éditeur.

   1. Cliquez sur l’icône de clé à molette pour ouvrir la fenêtre **Comparaison d’une propriété avec une valeur** de la boîte de dialogue

   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**.

      >[!NOTE]
      > La variable **googlesheets/value/1/0** fait référence à la ligne 2 et à la colonne , comme indiqué dans `google` les feuilles de la figure ci-dessous :

      ![image](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Sélectionnez l’**Opérateur** **supérieur à** (greater-than) dans le menu déroulant.

   1. Saisissez la **Valeur** **70**.

      >[!NOTE]
      >
      >AEM valide alors vos données dans la feuille de calcul Google en affichant votre segment en vert.

      ![image](/help/user-guide/assets/context-hub/context-hub18.png)

   De même, modifiez les valeurs de propriété en `**Lowerthan50**`.

   1. Faites glisser le composant **Comparaison : Propriété - Valeur** et déposez-le dans l’éditeur.

   1. Sélectionnez l’icône de clé à molette.

   1. Dans le **Comparaison d’une propriété avec une valeur** boîte de dialogue, sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**.

   1. Sélectionnez l’**Opérateur** **inférieur à** (lower-than) dans le menu déroulant.

   1. Saisissez la **Valeur** **50**.


## Activation du ciblage dans les canaux {#step-enabling-targeting-in-channels}

Suivez les étapes ci-dessous pour activer le ciblage dans vos canaux.

1. Accédez à l’un des canaux AEM Screens. Les étapes suivantes montrent comment activer le ciblage à l’aide de **DataDrivenChannel** créé dans un canal AEM Screens.

1. Sélectionnez le canal **TargetChannel** et cliquez sur **Propriétés** dans la barre d’actions.

   ![image](/help/user-guide/assets/context-hub/context-hub19.png)

1. Sélectionnez la variable **Personnalisation** pour pouvoir configurer les configurations ContextHub.

   1. Définissez le **Chemin d’accès ContextHub** sur `/conf/screens/settings/wcm/segments` et le **Chemin d’accès de segments** sur `/conf/screens/settings/wcm/segments`.
   1. Définissez la marque sur **ScreensBrand** dans la liste déroulante. **Définissez la référence de zone** sur **ScreensValue**.

   1. Cliquez sur **Enregistrer et fermer**.

      >[!NOTE]
      >
      >Utilisez le chemin ContextHub et le chemin des segments où vous avez initialement enregistré vos segments et configurations ContextHub.

      ![image](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. Accédez au canal **TargetChannel** et sélectionnez-le, puis cliquez sur **Modifier** dans la barre d’actions.

      >[!NOTE]
      >
      >Si vous avez tout configuré correctement, vous voyez **Ciblage** dans la liste déroulante de l’éditeur, comme illustré dans la figure ci-dessous.

      ![image](/help/user-guide/assets/context-hub/context-hub21.png)

## En savoir plus : exemples de cas d’utilisation {#learn-more-example-use-cases}

Après avoir configuré ContextHub pour votre projet AEM Screens, vous pouvez suivre les différents cas d’utilisation pour comprendre comment les ressources déclenchées par des données jouent un rôle essentiel dans différents secteurs d’activité :

1. **[Activation ciblée du stock de vente au détail](retail-inventory-activation.md)**
1. **[Activation de la température de l’agence de voyages](local-temperature-activation.md)**
1. **[Activation de la réservation d’hébergements](hospitality-reservation-activation.md)**
