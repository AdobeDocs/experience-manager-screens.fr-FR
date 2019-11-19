---
title: Configuration de ContextHub dans les écrans AEM
seo-title: Configuration de ContextHub dans les écrans AEM
description: Suivez cette page pour en savoir plus sur ContextHub dans le moteur de ciblage afin de définir le magasin de données en vue de la modification du contenu du déclencheur de données.
seo-description: Suivez cette page pour en savoir plus sur ContextHub dans le moteur de ciblage afin de définir le magasin de données en vue de la modification du contenu du déclencheur de données.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configuration de ContextHub dans les écrans AEM {#configuring-contexthub-in-aem-screens}

Cette section met l’accent sur la création et la gestion des modifications de ressources liées aux données à l’aide d’un magasin de données.

## Termes clés {#key-terms}

Avant d’entrer dans les détails de la création et de la gestion des canaux pilotés par l’inventaire dans votre projet AEM Screens, vous devez connaître quelques-uns des termes clés importants et pertinents pour les différents scénarios.

**Marque** Fait référence à votre description de projet de niveau supérieur.

**Zone** Fait référence au nom de votre projet AEM Screens, tel que Digital Ad Signing

**Activité** Définit la catégorie de règles telle que Pilotée par le stock, Par temps, Par disponibilité du service, etc.

**Audience** Définit la règle.

**Segment** Fait référence à la version de la ressource à lire pour la règle donnée, comme si la température est inférieure à 50 degrés Fahrenheit, alors l’écran affiche une image d’un café chaud ou d’une boisson froide.

Le diagramme ci-dessous illustre visuellement comment les configurations ContextHub coïncident avec l’activité, l’audience et les canaux.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Conditions préalables {#preconditions}

Avant de commencer à configurer une banque de données pour la configuration des configurations du concentrateur de contexte pour un projet AEM Screens, vous devez configurer des feuilles Google (à des fins de démonstration).

>[!CAUTION]
>
>Google Sheets est utilisé dans l'exemple suivant comme exemple de système de base de données à partir duquel les valeurs sont récupérées et uniquement à des fins éducatives. Adobe n’accepte pas l’utilisation de feuilles de calcul Google pour les environnements de production.
>
>Pour plus d'informations, reportez-vous à la section [Obtention de la clé](https://developers.google.com/maps/documentation/javascript/get-api-key) API dans la documentation Google.

## Étape 1 : Configuration d’un magasin de données {#step-setting-up-a-data-store}

Suivez les étapes ci-dessous pour configurer un magasin de données qui vous permet d’utiliser les configurations ContextHub et le chemin de segments vers le canal AEM Screens.

1. **Accès à ContextHub**

   Accédez à votre instance AEM et cliquez sur l’icône Outils dans la barre latérale gauche. Cliquez sur **Sites** —&gt; **ContextHub**, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Création d’une configuration de stockage ContextHub**

   1. Accédez à **global** &gt; **default** &gt; **ContextHub Configuration**.

   1. Cliquez sur** Créer &gt; Conteneur de configuration **et saisissez le titre sous** ContextHubDemo**.

   1. **** Accédez **à** ContextHubDemo **&gt;** Configuration du magasin ContentHub... pour ouvrir l’assistant **Configurer**.

   1. Saisissez le **Titre** en tant que feuilles **** Google, le Nom **du** magasin en tant que feuilles de **googlesheets et le TypeMagasin en tant que feuilles decontextecontexthub.generic-jsonp.**********

   1. Cliquez sur **Suivant**
   1. Entrez votre configuration JSON spécifique**.** Par exemple, vous pouvez utiliser le fichier json suivant à des fins de démonstration.
   1. Cliquez sur **Enregistrer**.

   ```
   {
     "service": {
       "host": "sheets.googleapis.com",
       "port": 80,
       "path": "/v4/spreadsheets/<your sheet it>/values/Sheet1",
       "jsonp": false,
       "secure": true,
       "params": {
         "key": "<your API key>"
       }
     },
     "pollInterval": 3000
   }
   ```

   >[!NOTE]
   >
   >Dans l’exemple de code ci-dessus, **pollInterval** définit la fréquence d’actualisation des valeurs (en ms).
   >
   >
   >Remplacez le code par votre *&lt;ID de feuille&gt;* et *&lt;clé API&gt;*, que vous avez récupérés lors de la configuration des feuilles Google.

   >[!CAUTION]
   Si vous créez vos configurations de stockage Google Sheets en dehors du dossier hérité (par exemple dans votre propre dossier de projet), le ciblage ne fonctionnera pas de manière prête.
   Si vous souhaitez configurer les configurations de stockage des feuilles Google en dehors du dossier hérité global, vous devez définir le nom **de la** boutique comme **segmentation** et le type **de** magasin comme **aem.segmentation.** De plus, vous devez ignorer le processus de définition du fichier json tel que défini ci-dessus.

1. **Création d’une marque dans les activités**

   1. Accédez à **Personnalisation** &gt; **Activités à partir de votre instance AEM.**

   1. Cliquez sur **Créer** &gt; **Créer une marque**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. Votre marque est maintenant créée comme illustré ci-dessous.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)


   >[!CAUTION]
   Problème connu :
   Pour ajouter une zone, supprimez le gabarit de l’URL, par exemple
   `https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master`

1. **Création d’une zone dans votre marque**

   Pour créer une zone de la marque, procédez comme suit :

   1. Cliquez sur **Créer** , puis **Créer une zone**

   1. Select **Area** from the **Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**.
Votre zone sera créée dans votre activité.

## Étape 2 : Configuration de la segmentation de l’audience {#step-setting-up-audience-segmentation}

Une fois que vous avez configuré un magasin de données et défini votre marque, suivez les étapes ci-dessous pour configurer les segments d’audience.

1. **Création de segments dans les audiences**

   1. Accédez à **Personnalisation** &gt; **Audiences** &gt; **We.Retail** depuis votre instance AEM.

   1. Cliquez sur **Créer** &gt; **Créer un segment Context Hub.** La boîte de dialogue **Nouveau segment** ContextHub s’ouvre.

   1. Enter the **Title** as **SheetA1 1** and click **Create**. De même, créez un autre segment intitulé **FeuilleA2 2**.

1. **Modification des segments**

   1. Sélectionnez les **feuilles de segment A1 1** (créées à l’étape (5)), puis cliquez sur **Modifier** dans la barre d’actions.

   1. Faites glisser et déposez la **comparaison : Propriété : composant Value** de l’éditeur.
   1. Cliquez sur l’icône de clé à molette pour ouvrir la boîte de dialogue **Comparaison d’une propriété avec une valeur** .
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante du nom **de la** propriété.

   1. Sélectionnez **Opérateur** comme **Égal** dans le menu déroulant.

   1. Saisissez la **valeur** **1**.
   >[!NOTE]
   AEM valide vos données de la feuille Google en affichant votre segment en vert.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   De même, modifiez les valeurs des propriétés en **feuilles A1 2**.

   1. Faites glisser et déposez la **comparaison : Propriété : composant Value** de l’éditeur.
   1. Cliquez sur l’icône de clé à molette pour ouvrir la boîte de dialogue **Comparaison d’une propriété avec une valeur** .
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante du nom **de la** propriété.

   1. Sélectionnez **Opérateur** comme **Égal** dans le menu déroulant.

   1. Saisissez la **valeur** **2**.
   >[!NOTE]
   Les règles appliquées dans les étapes précédentes ne sont qu’un exemple de configuration des segments pour la mise en oeuvre des cas d’utilisation suivants.

## Étape 3 : Activation du ciblage dans les canaux {#step-enabling-targeting-in-channels}

Suivez les étapes ci-dessous pour activer le ciblage sur vos canaux.

1. Accédez à l’un des canaux AEM Screens**. **Les étapes suivantes montrent comment activer le ciblage à l’aide de **DataDrivenRetail** créé dans un canal d’écrans AEM.

1. Sélectionnez le canal **DataDrivenRetail** et cliquez sur **Propriétés** dans la barre d’actions.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Sélectionnez l’onglet **Personnalisation** pour configurer les configurations ContextHub.

   1. Sélectionnez le chemin **ContextHub** en tant que **libs** &gt; **settings** &gt; **cloudsettings &gt; default &gt;Configurations ContextHub et cliquez surSelect.**************

   1. Sélectionnez le chemin d’accès **aux** segments en tant que **conf** &gt; **We.Retail** &gt; **settings &gt; wcm &gt;de segments et cliquez surSélectionner.**************

   1. Cliquez sur **Enregistrer et fermer**.
   >[!NOTE]
   Utilisez ContextHub et le chemin Segments, où vous avez initialement enregistré vos configurations et segments de concentrateur de contexte.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Accédez à **DataDrivenRetail** et sélectionnez-le dans **DataDrivenAssets** &gt; **Canaux** , puis cliquez sur **Modifier dans la barre d’actions.**

   >[!NOTE]
   Si vous avez correctement configuré tout, l’option **Ciblage** s’affiche dans la liste déroulante de l’éditeur, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Une fois que vous avez configuré les configurations ContextHub pour votre canal, veillez à suivre les étapes précédentes de 1 à 4, pour les trois autres canaux de séquence, si vous souhaitez suivre tous les cas d’utilisation ci-dessous.

## En savoir plus : Exemples d’utilisation {#learn-more-example-use-cases}

Après avoir configuré ContextHub pour votre projet AEM Screens, vous pouvez suivre les différents cas d’utilisation pour comprendre comment les ressources déclenchées par les données jouent un rôle essentiel dans différents secteurs d’activité :

1. **[Activation ciblée du stock de vente au détail](retail-inventory-activation.md)**
1. **[Activation de la température du centre de voyage](local-temperature-activation.md)**
1. **[Activation de réservation d'hébergement](hospitality-reservation-activation.md)**
