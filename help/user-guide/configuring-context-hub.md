---
title: Configuration de ContextHub dans AEM Screens
seo-title: Configuration de ContextHub dans AEM Screens
description: Consultez cette page pour en savoir plus sur ContextHub dans le moteur de ciblage afin de définir le magasin de données en vue de la modification du contenu du déclencheur de données.
seo-description: Consultez cette page pour en savoir plus sur ContextHub dans le moteur de ciblage afin de définir le magasin de données en vue de la modification du contenu du déclencheur de données.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: 593107de8775ffa1f87173c4e9e7be5c3ccb0b90

---


# Configuration de ContextHub dans AEM Screens {#configuring-contexthub-in-aem-screens}

Cette section met l’accent sur la création et la gestion des modifications de ressources liées aux données à l’aide d’un magasin de données.

## Termes clés {#key-terms}

Avant de vous attaquer aux détails de la création et de la gestion des canaux pilotés par l’inventaire dans votre projet AEM Screens, vous devez connaître quelques-uns des termes clés importants et pertinents pour les différents scénarios.

**Marque** Fait référence la description générale de votre projet.

**Zone** Fait référence au nom de votre projet AEM Screens, comme par exemple signalétique numérique publicitaire

**Activité** Définit la catégorie de règles, comme Basé sur l’inventaire, Basé sur la météo, Basé sur la disponibilité du service, etc.

**Audience** Définit la règle.

**Segment** Fait référence à la version de la ressource à lire pour la règle donnée, par exemple : si la température est inférieure à 10 degrés Celsius, l’écran affiche une image d’un café chaud. Sinon, il affiche une image d’une boisson froide.

Le diagramme ci-dessous illustre visuellement comment les configurations ContextHub coïncident avec l’activité, l’audience et les canaux.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Conditions préalables {#preconditions}

Avant de commencer à définir les configurations ContextHub d’un projet AEM Screens, vous devez configurer Google Sheets (à des fins de démonstration).

>[!IMPORTANT]
>
>Google Sheets est utilisé dans l’exemple suivant à titre d’exemple de système de base de données à partir duquel les valeurs sont récupérées et uniquement à des fins pédagogiques. Adobe n’approuve pas l’utilisation de Google Sheets dans des environnements de production.
>
>Pour plus d’informations, reportez-vous à la section [Obtenir la clé d’API](https://developers.google.com/maps/documentation/javascript/get-api-key) dans la documentation Google.

## Étape 1 : configuration d’un magasin de données {#step-setting-up-a-data-store}

Vous pouvez configurer l’entrepôt de données en tant qu’événement d’E/S local ou d’événement de base de données local.

L’exemple de déclencheurs de données au niveau des ressources suivant montre un de base de données local qui configure un magasin de données, tel qu’une feuille Excel qui vous permet d’utiliser les configurations ContextHub et le chemin d’accès aux segments vers le AEM Screens .

Une fois la feuille google configurée correctement, par exemple, comme illustré ci-dessous :

![image](/help/user-guide/assets/context-hub/context-hub1.png)

La validation suivante est ce que vous  lorsque vous vérifiez votre connexion en saisissant les deux valeurs, ID *de feuille* Google et clé ** API, au format ci-dessous :

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![image](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
> L’exemple spécifique ci-dessous présente les feuilles Google comme un magasin de données qui déclenchera un changement de fichier si la valeur est supérieure à 100 ou inférieure à 50.

## Étape 2 : Configuration des configurations de stockage {#step-setting-store-configurations}

1. **Accès à ContextHub**

   Accédez à votre instance AEM et cliquez sur l’icône Outils dans la barre latérale gauche. Cliquez sur **Sites** —> **ContextHub**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Création d’une configuration de magasin ContextHub**

   1. Accédez au de configuration  intitulé **écrans**.

   1. Click **Create** > **Create Configuration Container** and enter the title as **ContextHubDemo**.

      ![image](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Accédez** à **ContextHubDemo** > **Créer** une configuration **** ContentHub et cliquez sur Enregistrer.****

      >[!NOTE]
      > Une fois que vous avez cliqué sur **Enregistrer** , vous vous trouvez dans l’écran de configuration **de** ContextHub.

   1. Dans l’écran Configuration **de** ContextHub, cliquez sur **Créer** > Configuration de la boutique **ContentHub.**

      ![image](/help/user-guide/assets/context-hub/context-hub5.png)

   1. Enter the **Title** as **Google Sheets**, **Store Name** as **googlesheets**, and **Store Type** as **contexthub.generic-jsonp** and click **Next**.
      ![image](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Entrez votre configuration json spécifique. Par exemple, vous pouvez utiliser le fichier json suivant à des fins de démonstration, puis cliquer sur **Enregistrer** . La configuration du magasin s’affichera sous le nom de feuilles **** Google dans la configuration ContextHub.

      >[!IMPORTANT]
      >Make sure to replace the code with your *&lt;Sheet ID>* and *&lt;API Key>*, that you fetched while setting up the Google Sheets.

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
      Dans l’exemple de code ci-dessus, **pollInterval** définit la fréquence d’actualisation des valeurs (en ms).
Remplacez le code par l’*&lt;ID de feuille>* et la *&lt;clé API>*, que vous avez récupérés lors de la configuration des Google Sheets.

      >[!CAUTION]
      Si vous créez vos configurations de stockage Google Sheets en dehors du dossier global (par exemple dans votre propre dossier de projet), le ciblage ne fonctionnera pas de manière prête.

1. **Configuration de la segmentation du magasin**

   1. Accédez à Configuration du magasin **ContentHub.** et créez une autre configuration de stockage dans le de configuration des écrans et définissez le **Titre** sur **segmentation-contexthub**, le Nom de **magasin** sur **segmentation et le Type demagasin  sur le champ aem.segmentation.**********

      ![image](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Click **Next** and then **Save**.

      >[!NOTE]
Vous devez ignorer le processus de définition du fichier json et le laisser vide.


## Étape 3 : Configuration de segments dans   de {#setting-up-audience}

1. **Création de segments dans les audiences**

   1. Navigate from your AEM instance to **Personalization** > **Audiences** > **screens**.

   1. Cliquez sur **Créer** > **Créer un segment ContextHub.** La boîte de dialogue **Nouveau segment ContextHub** s’ouvre.

   1. Enter the **Title** as **Higherthan50** and click **Create**. Similarly, create another segment titled as **Lowerthan50**.

      ![image](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Select the segment **Higherthan50** and click **Properties** from the action bar.
      ![image](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Sélectionnez l’onglet **Personnalisation** dans Propriétés **du** segment. Définissez **ContextHub Path** sur `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub` et **Segments Path** sur `/conf/screens/settings/wcm/segments` et cliquez sur **Save, comme illustré dans la figure ci-dessous.**

      ![image](/help/user-guide/assets/context-hub/context-hub13.png)

   1. De même, définissez **ContextHub Path** et **Segments Path** pour le segment inférieur50 **** également.

## Étape 4 : Configuration de la marque et de la zone {#setting-brand-area}

Suivez les étapes ci-dessous pour créer une marque dans votre   et dans votre zone sous la marque :

1. **Création d’une marque dans les activités**

   1. Dans votre instance AEM, accédez à **Personnalisation** > **Activités**.

   1. Cliquez sur **Créer** > **Créer une marque**.

   1. Dans l’assistant **Créer une page**, sélectionnez **Marque** et cliquez sur **Suivant**.

   1. Enter the **Title** as **ScreensBrand** and click **Create**. Votre marque a été créée, comme illustré ci-dessous.

      ![image](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Problème connu :
Pour ajouter une zone, supprimez le gabarit de l’URL, par exemple
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Création d’une zone dans votre marque**

   Pour créer une zone dans la marque, procédez comme suit :

   1. Cliquez sur **Créer**, puis sur **Créer une zone**.

      ![image](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Sélectionnez **Zone** à partir de l’assistant de **Création de pager****et cliquez sur Suivant**.

   1. Enter the **Title** as **ScreensValue** and click **Create**.
Une zone sera créée dans votre marque.

## Étape 5 : Création de segments dans un  {#step-setting-up-audience-segmentation}

Une fois que vous avez configuré un magasin de données et défini votre  de  (marque et zone), suivez les étapes ci-dessous pour créer des segments dans votre  de.

1. **Création de segments dans   de**

   1. Navigate from your AEM instance to **Personalization** > **Activities** > **ScreensBrand** >**ScreensValue**.

   1. Click **Create** > **Create Activity.** L&#39;Assistant **Configurer** s&#39;ouvre.

   1. Saisissez le **Titre** comme **ValeurCheck50** et **Nom** **comme ValeurCheck50.** Sélectionnez le moteur **de ciblage** en tant que **ContextHub (AEM)** dans la liste déroulante et cliquez sur **Suivant**.

      ![image](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Cliquez sur Expérience **Ajouter** dans l’Assistant **de** configuration de .

   1. Dans le ****, sélectionnez **Plus élevé que50** , cliquez sur **Ajouter expérience** et saisissez le **Titredont le nom est supérieur à50Nomest supérieur à500.************** Cliquez sur **OK**.

   1. Dans le ****, sélectionnez **Moins de 50** et cliquez sur **Ajouter expérience** et saisissez le **Titrecomme inférieur à 50Nomcomme inférieur à 50000000.************** Cliquez sur **OK**.

      ![image](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Click **Next** and then **Save**. **Le  ValueCheck50** est désormais créé et configuré.

      ![image](/help/user-guide/assets/context-hub/context-hub16.png)

## Étape 5 : Modification des segments dans {#editing-audience-segmentation}

1. **Modification des segments**

   1. Navigate from your AEM instance to **Personalization** > **Audiences** > **screens**.

   1. Select the segment **Higherthan50**, and click **Edit** from the action bar.

   1. Faites glisser le composant **Comparaison : Propriété - Valeur** et déposez-le dans l’éditeur.

   1. Cliquez sur l’icône en forme de clé pour ouvrir la boîte de dialogue **Comparer une propriété une valeur**.

   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**.

   1. Select the **Operator** as **greater-than** from the drop-down menu.

   1. Saisissez la **valeur** **50**.
   >[!NOTE]
   AEM valide alors vos données de la feuille de calcul Google en affichant votre segment en vert.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   De même, modifiez les valeurs de propriété sur **Lower50**.

   1. Faites glisser le composant **Comparaison : Propriété - Valeur** et déposez-le dans l’éditeur.

   1. Cliquez sur l’icône en forme de clé pour ouvrir la boîte de dialogue **Comparer une propriété une valeur**.

   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**.

   1. Select the **Operator** as **less-than** from the drop-down menu.

   1. Saisissez la **valeur** **50**.



## Enabling Targeting in Channels {#step-enabling-targeting-in-channels}

Suivez les étapes ci-dessous pour activer le ciblage dans vos canaux.

1. Accédez à l’un des canaux AEM Screens. Les étapes suivantes montrent comment activer le ciblage à l’aide de **DataDrivenRetail** créé dans un canal AEM Screens.

1. Sélectionnez le canal **DataDrivenRetail** et cliquez sur **Propriétés** dans la barre d’actions.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Sélectionnez l’onglet **Personnalisation** pour définir les configurations ContextHub.

   1. Sélectionnez le **Chemin d’accès ContextHub** **libs** > **settings** > **cloudsettings** > **default** > **Configurations ContextHub** et cliquez sur **Sélectionner**.

   1. Sélectionnez le **chemin d’accès aux segments** **conf** > **We.Retail** > **settings** > **wcm** > **segments** et cliquez sur **Sélectionner**.

   1. Cliquez sur **Enregistrer et fermer**.
   >[!NOTE]
   Utilisez le chemin ContextHub et le chemin des segments où vous avez initialement enregistré vos segments et configurations ContextHub.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Accédez à **DataDrivenRetail** et sélectionnez-le dans **DataDrivenAssets** > **Canaux**, puis cliquez sur **Modifier** dans la barre d’actions.

   >[!NOTE]
   Si vous avez tout correctement configuré, l’option **Ciblage** s’affiche dans la liste déroulante de l’éditeur, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Une fois que vous avez défini les configurations ContextHub pour votre canal, veillez à respecter les étapes 1 à 4 précédentes pour les trois autres canaux de séquence si vous souhaitez suivre tous les cas d’utilisation ci-dessous.

## En savoir plus : exemples de cas d’utilisation {#learn-more-example-use-cases}

Après avoir configuré ContextHub pour votre projet AEM Screens, vous pouvez suivre les différents cas d’utilisation pour comprendre comment les ressources déclenchées par des données jouent un rôle essentiel dans différents secteurs d’activité :

1. **[Activation ciblée du stock de vente au détail](retail-inventory-activation.md)**
1. **[Activation de la température de l’agence de voyages](local-temperature-activation.md)**
1. **[Activation de la réservation d’hébergements](hospitality-reservation-activation.md)**
