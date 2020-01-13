---
title: Canal piloté par le stock
seo-title: Canal piloté par le stock
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: a7e7aa08-8f9e-4458-bdce-225cf29a6da4
contentOwner: jsyal
discoiquuid: 9989ef4c-9fdd-4bf2-9f7c-0c74a9cc4e7f
docset: aem65
translation-type: ht
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Canal piloté par le stock{#inventory-driven-channel}

## Prise en main des canaux pilotés par le stock {#getting-started-with-inventory-driven-channels}

Cette section décrit un exemple de cas d’utilisation qui met l’accent sur la création et la gestion d’une modification de ressources pilotée par les données à l’aide de Google Sheets.

### Conditions préalables {#preconditions}

Avant de commencer ce cas d’utilisation, vous devez comprendre comment :

* **[Créer et gérer des canaux](managing-channels.md)**
* **[Créer et gérer des emplacements](managing-locations.md)**
* **[Créer et gérer des planifications](managing-schedules.md)**
* **[Enregistrer des périphériques](device-registration.md)**

### Acteurs principaux {#primary-actors}

Auteurs de contenu

### Terminologie {#terminolgies}

Utilisez les termes importants ci-dessous, qui facilitent la compréhension et la configuration du projet dans les différents cas d’utilisation :

**Activité** Activité fait référence à la catégorie.

**Domaine** Principales données du projet

**Audience** Emplacement des données

**Marque** Marque fait référence

**Segment** Segment fait référence à un conteneur de ressources que vous tentez de cibler.

### Flux de base : configuration du projet {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**Condition préalable requise :**
>
>Vous devez créer un projet AEM Screens avec un canal de séquence avant d’entrer dans les détails de la configuration et de l’utilisation d’une modification de ressources pilotée par les données dans un projet. À des fins de démonstration, le projet intitulé **DataDrivenAsset** est créé et les canaux de séquences intitulés **DataDrivenRestaurant**, **DataDrivenTextOverlay**, **DataDrivenWeather** et **DataDrivenRetail** sont ajoutés au projet, comme illustré dans la figure ci-dessous.
>
>La création de quatre canaux différents n’est utilisée qu’à des fins de démonstration et pour présenter quatre cas d’utilisation différents dans différents canaux. Si vous ne souhaitez suivre qu’un seul cas d’utilisation, vous êtes libre de ne créer qu’un seul canal de séquence.

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

Pour créer un exemple de projet portant sur la création et sur la gestion d’une modification de ressources pilotée par les données à l’aide de Google Sheets dans un projet AEM Screens, lisez les sections suivantes :

## Étape 1 : configuration d’une base de données {#step-setting-up-database}

>[!CAUTION]
>
>Google Sheets est utilisé dans l’exemple de système de base de données ci-dessous, donné à des fins pédagogiques uniquement, et à partir duquel les valeurs sont récupérées. Adobe n’approuve pas l’utilisation de Google Sheets dans des environnements de production.
>
>Pour plus d’informations, reportez-vous à la section [Obtenir la clé d’API](https://developers.google.com/maps/documentation/javascript/get-api-key) dans la documentation Google.

1. Connectez-vous à Google Docs.

   >[!NOTE]
   >
   >Vous devez disposer d’un compte dans Google Drive avant de créer une feuille de calcul Google.

1. Ouvrez une nouvelle feuille de calcul vide. Ajoutez du contenu à votre feuille de calcul Google et enregistrez-la. À des fins de démonstration, la feuille de calcul Google est appelée **ContextHubDemo**.
1. Cliquez sur **Partager** dans le coin supérieur droit de la feuille de calcul Google pour ouvrir la boîte de dialogue **Partager avec d’autres utilisateurs**. Cliquez sur l’option **Avancé** et définissez les paramètres sur **Activé : Toutes les personnes disposant du lien**, comme illustré dans la figure ci-dessous.

   Cette étape vous permet d’accéder aux valeurs dans la feuille de calcul Google.

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. Lorsque vous cliquez sur **Enregistrer** à l’étape précédente, vous obtenez le lien pour la feuille de calcul Google. Cliquez sur Enregistrer pour référence ultérieure et cliquez sur **Terminé**.

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>Google Sheets est utilisé dans l’exemple ci-après à des fins pédagogiques. Adobe n’approuve pas l’utilisation de Google Sheets dans des environnements de production.

## Étape 2 : activation des API REST de Google Sheets {#step-enabling-the-google-sheets-rest-apis}

Après avoir configuré votre feuille de calcul Google, vous devez activer l’API REST de Google Sheets pour accéder aux valeurs.

Pour découvrir comment activer les API REST pour Google Sheets, consultez la documentation des API Google.

1. Accédez à la [console des API Google](https://console.developers.google.com/apis/credentials). Cliquez sur **CRÉER** pour créer un projet

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. Saisissez le **nom du projet** **AssetChange** et cliquez sur **CRÉER**.
1. Une fois le projet créé, vous devez configurer la clé d’API. Cliquez sur **Créer les informations d’identification** et sélectionnez **Clé d’API **pour générer la clé d’API pour votre projet. Enregistrez la clé d’API pour référence ultérieure.

   >[!NOTE]
   >
   >Ce projet de démonstration utilise la clé d’API gratuite de Google. Pour plus d’informations sur la tarification et les restrictions, consultez le site web **Obtenir la clé d’API** de Google.

### Vérification de la configuration de Google Sheets {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;ID de votre feuille&gt;/values/Sheet1?key=&lt;votre clé d’API&gt;

Par exemple :

Si le lien** Google Sheets** est *du type :*

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`,

l’**ID de la feuille** est : `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

la **clé d’API** est : `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

En ajoutant les deux valeurs dans la syntaxe ci-dessus :

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Vous devriez maintenant pouvoir afficher vos données dans la feuille de calcul.

## Étape 2 : configuration d’AEM pour récupérer du contenu de Google Sheets {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

La section ci-dessous décrit comment configurer Adobe Experience Manager (AEM) pour récupérer du contenu de Google Sheets.

1. Accédez à votre instance AEM et cliquez sur l’icône Outils dans la barre latérale gauche. Cliquez sur **Sites** —&gt; **ContextHub**, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Créez une configuration de magasin ContextHub**

   1. Accédez à **global** &gt; **default** &gt; **Configuration de ContextHub**.

   1. Cliquez sur** Créer &gt; Conteneur de configuration **et saisissez le titre** ContextHubDemo**.

   1. **Accédez** à **ContextHubDemo** &gt; **Configuration du magasin ContentHub...** pour ouvrir l’**assistant de configuration**
   1. Saisissez le **Titre** **Google Sheets**, le **Nom du magasin** **googlesheets** et le **Type de magasin** **contexthub.generic-jsonp**
   1. Cliquez sur **Suivant**
   1. Entrez votre configuration json spécifique. Vous pouvez par exemple utiliser le code json ci-dessous à des fins de démonstration.
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
   >Remplacez le code par votre *&lt;ID de feuille&gt;* et par la *&lt;clé d’API&gt;*, que vous avez récupérée à l’**Étape 1 : configuration de la base de données.**

   >[!CAUTION]
   Si vous créez des configurations de magasin Google Sheets en dehors du dossier existant (par exemple dans votre propre dossier de projet), le ciblage ne fonctionnera pas immédiatement.
   Si vous souhaitez définir les configurations de magasin Google Sheets en dehors du dossier existant global, vous devez définir le **Nom du magasin** en tant que **segmentation** et le **Type de magasin** comme **aem.segmentation**. Vous devez par ailleurs ignorer le processus de définition du code json défini ci-dessus.

1. **Création d’une marque dans les activités**

   1. Dans votre instance AEM, accédez à **Personnalisation** &gt; **Activités**

   1. Cliquez sur** Créer** &gt; **Créer une marque**

   1. Dans l’assistant **Créer une page**, sélectionnez **Marque** et cliquez sur **Suivant**

   1. Saisissez le **Titre** **ContextHubDemo** et cliquez sur **Créer**. Votre marque a été créée, comme illustré ci-dessous.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
Problème connu :
Pour ajouter une zone, supprimez le gabarit de l’URL, par exemple
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. Création d’une zone dans votre marque**

   1. Cliquez sur **Créer** &gt; **Créer une zone**

   1. Dans l’assistant **Créer une page**, sélectionnez **Zone** et cliquez sur Suivant

   1. Saisissez le **Titre** **GoogleSheets** et cliquez sur **Créer**. Votre zone sera créée dans votre activité.

1. **Création de segments dans les audiences**

   1. Dans votre instance AEM, accédez à **Personnalisation** &gt; **Audiences** &gt; **We.Retail**.
   1. Cliquez sur **Créer** &gt; **Créer un segment Context Hub**. La boîte de dialogue Nouveau segment ContextHub apparaît.
   1. Saisissez le **Titre** **SheetA1 1** et cliquez sur **Créer**. De la même manière, créez un autre segment intitulé **SheetA2 2**.

1. **Modification des segments**

   1. Sélectionnez le segment **Sheets A1 1** (créé à l’étape 5), puis cliquez sur **Modifier** dans la barre d’actions.

   1. Faites glisser le composant **Comparaison : Propriété - Valeur** et déposez-le dans l’éditeur.
   1. Cliquez sur l’icône en forme de clé pour ouvrir la boîte de dialogue **Comparer une propriété à une valeur**.
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**.

   1. Sélectionnez l’**opérateur** **Égal **dans le menu déroulant.

   1. Saisissez la **valeur** **1**.
   >[!NOTE]
   AEM valide alors vos données de la feuille de calcul Google en affichant votre segment en vert.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   De la même manière, définissez les valeurs des propriétés sur **Sheets A1 2**.

   1. Faites glisser le composant **Comparaison : Propriété - Valeur** et déposez-le dans l’éditeur.
   1. Cliquez sur l’icône en forme de clé pour ouvrir la boîte de dialogue **Comparer une propriété à une valeur**.
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**.

   1. Sélectionnez l’**opérateur** **Égal **dans le menu déroulant.

   1. Saisissez la **valeur** **2**.
   >[!NOTE]
   Les règles appliquées lors des étapes précédentes ne sont qu’un exemple de configuration des segments pour la mise en œuvre des cas d’utilisation ci-dessous.

## Étape 3 : définition de configurations ContextHub dans le canal AEM Screens {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

Suivez les étapes ci-dessous pour définir des configurations ContextHub et des chemins de segments au le canal AEM Screens.

1. Pour commencer, accédez à l’un des canaux AEM Screens (**DataDrivenRetail**) que vous avez créés.
1. Sélectionnez le canal (**DataDrivenRetail**) et cliquez sur **Propriétés** dans la barre d’actions.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Sélectionnez l’onglet **Personnalisation** pour définir les configurations ContextHub.

   1. Sélectionnez le **Chemin d’accès ContextHub** **libs** &gt; **settings** &gt; **cloudsettings** &gt; **default** &gt; **Configurations ContextHub** et cliquez sur **Sélectionner**.

   1. Sélectionnez le **Chemin d’accès aux segments** **conf** &gt; **We.Retail **&gt; **settings** &gt; **wcm** &gt; **segments** et cliquez sur **Sélectionner**.

   1. Cliquez sur **Enregistrer et fermer**.
   >[!NOTE]
   Utilisez le chemin ContextHub et le chemin des segments où vous avez initialement enregistré vos segments et configurations ContextHub.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   Si vous ne sélectionnez pas la **Marque** sous **Configuration du ciblage** dans la boîte de dialogue ci-dessus, vous devez sélectionner la marque et l’activité lorsque vous lancez le processus de ciblage.

1. Naviguez et sélectionnez **DataDrivenRetail** depuis **DataDrivenAssets** &gt; **Canaux**, puis cliquez sur **Modifier** dans la barre d’actions.

   >[!NOTE]
   Si vous avez tout correctement configuré, l’option **Ciblage** s’affiche dans la liste déroulante de l’éditeur, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Une fois que vous avez défini les configurations ContextHub pour votre canal, veillez à respecter les étapes 1 à 4 précédentes pour les trois autres canaux de séquence si vous souhaitez suivre tous les cas d’utilisation ci-dessous.

## Cas d’utilisation 1 : activation du stock de vente au détail {#use-case-retail-inventory-activation}

Le cas d’utilisation ci-dessous montre trois images différentes en fonction des valeurs de votre feuille de calcul Google.

### Description {#description}

Ce cas d’utilisation présente le stock de vente au détail de trois modèles de sweat-shirts de couleurs différentes. Selon le nombre de sweat-shirts disponibles en stock enregistré dans Google Sheets, l’image (sweat-shirt rouge, vert ou bleu) avec le plus grand nombre est affichée à l’écran.

Pour ce cas d’utilisation, le sweat-shirt rouge, vert ou bleu apparaît à l’écran en fonction du plus grand nombre d’articles disponibles.

### Procédure {#procedure}

Pour mettre en œuvre le cas d’utilisation de l’activation du stock de vente au détail, procédez comme suit :

1. **Remplissage des feuilles de calcul Google Sheets**

   1. Accédez à la feuille de calcul Google appelée ContextHubDemo.
   1. Ajoutez trois colonnes (Rouge, Vert et Bleu) avec les valeurs correspondantes à trois sweat-shirts différents.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuration des audiences selon les besoins**

   1. Accédez aux segments de votre audience (créés à l’étape 5 de la section ***Étape 2 : configuration d’AEM pour récupérer du contenu de Google Sheets***).
   1. Ajoutez trois nouveaux segments **For_Red**, **For_Green** et **For_Blue**.

   1. Sélectionnez **For_Red** et cliquez sur **Modifier** dans la barre d’actions.

   1. Faites glisser **Comparaison : Propriété - Propriété** et déposez-le dans l’éditeur, puis cliquez sur l’icône de configuration pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante de **Nom de la première propriété**

   1. Sélectionnez l’**opérateur** **supérieur à **dans le menu déroulant

   1. Sélectionnez le **Type de données** **Nombre**

   1. Sélectionnez **googlesheets/value/1/1** dans la liste déroulante de **Nom de la deuxième propriété**

   1. Faites glisser **une autre comparaison : Propriété - Propriété** et déposez-la dans l’éditeur, puis cliquez sur l’icône de configuration pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante de **Nom de la première propriété**

   1. Sélectionnez l’**opérateur** **supérieur à **dans le menu déroulant

   1. Sélectionnez le **Type de données** **Nombre**

   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la deuxième propriété**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   De la même manière, modifiez et ajoutez des règles de propriétés de comparaison au segment **For_Blue**, comme illustré ci-dessous :

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   De la même manière, modifiez et ajoutez des règles de propriétés de comparaison au segment **For_Green**, comme illustré ci-dessous :

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   Pour les segments **For_Green** et **For_Green**, il est impossible de charger les données dans l’éditeur car seule la première comparaison est valide à ce jour, selon les valeurs dans la feuille de calcul Google.

1. Naviguez et sélectionnez votre canal **DataDrivenRetail** (canal de séquence) et cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   Vous devriez avoir défini vos **configurations** **ContextHub** à l’aide de l’onglet **Propriétés** --&gt; **Personnalisation**.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Si vous n’ajoutez pas la **marque** sous **Configurations de ciblage** lors de la définition des **Configurations ContextHub** pour votre projet, comme illustré ci-dessus, vous devez sélectionner la **marque** et l’**activité** lors du démarrage du processus de ciblage, à l’étape suivante.

1. **Ajout d’une image par défaut**

   1. Ajoutez une image par défaut à votre canal et cliquez sur **Ciblage**.
   1. Sélectionnez **Marque** et l’**Activité** dans le menu déroulant, puis cliquez sur **Commencer le ciblage**.

   1. Cliquez sur **Commencer le ciblage**.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Avant de commencer le ciblage, vous devez ajouter les segments (**For_Green**, **For_Red** et **For_Blue**) en cliquant sur **+ Ajouter le ciblage d’expérience** dans le rail latéral, comme illustré ci-dessous.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Ajoutez les images aux trois scénarios différents comme illustré ci-dessous.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Vérification de l’aperçu**

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de calcul Google et mettez à jour sa valeur.
   1. Modifiez la valeur des trois colonnes et notez que l’image d’affichage est mise à jour en fonction de la valeur de stock la plus élevée.
   ![retail_result](assets/retail_result.gif)

## Cas d’utilisation 2 : activation de la météo de l’agence de voyages {#use-case-travel-center-weather-activation}

Le cas d’utilisation ci-dessous montre deux images différentes en fonction des valeurs de votre feuille de calcul Google.

### Description {#description-1}

Pour ce cas d’utilisation, si la valeur de votre feuille de calcul Google Sheets est inférieure à 50, une image avec des boissons chaudes apparaît, et si la valeur est supérieure ou égale à 50, une image avec des boissons fraîches apparaît. En cas de valeur différente ou d’absence de valeur, le lecteur affiche une image par défaut.

### Procédure {#procedure-1}

Pour mettre en œuvre le cas d’utilisation de l’activation de la météo de l’agence de voyage pour votre projet AEM Screens, procédez comme suit :

1. **Remplissage des feuilles de calcul Google Sheets**

   1. Accédez à la feuille de calcul Google appelée ContextHubDemo.
   1. Ajoutez une colonne **Heading1** avec la valeur de température correspondante.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuration des segments dans les audiences selon les besoins**

   1. Accédez aux segments de votre audience (créés à l’étape 5 de la section ***Étape 2 : configuration d’AEM pour récupérer du contenu de Google Sheets***).
   1. Sélectionnez **Sheets A1 1** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône de configuration pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**

   1. Sélectionnez l’**opérateur** **supérieur ou égal à** dans le menu déroulant

   1. Saisissez la **valeur** **50**

   1. De même, sélectionnez les feuilles ** Sheets A1 2 ** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône de configuration pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante de **Nom de la propriété**

   1. Sélectionnez l’**opérateur** **inférieur à **dans le menu déroulant

   1. Saisissez la **valeur** **50**

1. Naviguez et sélectionnez votre canal (), puis cliquez sur **Modifier** dans la barre d’actions. Dans l’exemple ci-dessous, **DataDrivenWeather**, la fonctionnalité est illustrée au moyen d’un canal de séquence.

   >[!NOTE]
   Votre canal doit déjà comporter une image par défaut et les audiences doivent être préconfigurées comme indiqué à l’étape (3)

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   Vous devez avoir défini vos **configurations** **ContextHub** à l’aide de l’onglet **Propriétés** --&gt; **Personnalisation**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   Si vous n’ajoutez pas la **marque** sous **Configurations de ciblage** lors de la définition des **Configurations ContextHub** pour votre projet, comme illustré ci-dessus, vous devez sélectionner la **marque** et l’**activité** lors du démarrage du processus de ciblage, à l’étape suivante.

1. Sélectionnez **Ciblage** dans l’éditeur. Sélectionnez ensuite **Marque** et l’**Activité** dans le menu déroulant, puis cliquez sur **Commencer le ciblage**.

   >[!NOTE]
   Si vous avez ajouté la **Marque** sous **Configurations du ciblage** lors de la définition des configurations **ContextHub** pour votre projet, vous n’avez pas besoin de sélectionner la **Marque** ni l’**Activité** à cette étape.

   ![new_activity3](assets/new_activity3.gif)

1. Vérification de l’aperçu

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de calcul Google et mettez à jour sa valeur.
   1. Définissez une valeur inférieure à 50. Vous devriez voir une image de boissons fraîches. Si la valeur dans la feuille de calcul Google est supérieure ou égale à 50, vous devriez voir une image de boisson chaude.
   ![result3](assets/result3.gif)

## Cas d’utilisation 3 : activation de la réservation d’hébergements {#use-case-hospitality-reservation-activation}

Le cas d’utilisation ci-dessous montre deux images différentes en fonction des valeurs et de la formule appliquée dans votre feuille de calcul Google.

### Description {#description-2}

Pour ce cas d’utilisation, la feuille de calcul Google est renseignée avec le pourcentage de réservation de deux restaurants : **Restaurant1** et **Restaurant2**. Une formule est appliquée en fonction des valeurs de Restaurant1 et Restaurant2 et selon la formule, la valeur 1 ou 2 est affectée à la colonne **AdTarget**.

Si **Restaurant1** &gt; **Restaurant2**, la valeur **AdTarget** est de 1, sinon, une valeur de 2 est affectée à **AdTarget**. La valeur 1 génère l’option *Steak food* et la valeur 2 fait apparaître l’option *Thai food* sur votre écran.

### Approche procédurale {#procedural-approach}

Pour mettre en œuvre le cas d’utilisation de l’activation des réservations d’hébergements pour votre projet AEM Screens, procédez comme suit :

1. Remplissage des feuilles de calcul Google Sheets et ajout de la formule

   Par exemple, appliquez la formule à la troisième colonne **AdTarget**, comme illustré ci-dessous.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuration des segments dans les audiences selon les besoins**

   1. Accédez aux segments de votre audience (créés à l’étape 5 de la section ***Étape 2 : configuration d’AEM pour récupérer du contenu de Google Sheets***).
   1. Sélectionnez **Sheets A1 1** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône de configuration pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante de **Nom de la propriété**

   1. Sélectionnez l’**opérateur** **égal **dans le menu déroulant

   1. Saisissez la **valeur** **1**

   1. De même, sélectionnez les feuilles **Sheets A1 2** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône de configuration pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante de **Nom de la propriété**

   1. Sélectionnez l’**opérateur** **2**

1. Naviguez et sélectionnez votre canal (), puis cliquez sur **Modifier** dans la barre d’actions. Dans l’exemple suivant, **DataDrivenRestaurant**, la fonctionnalité est illustrée au moyen d’un canal de séquence.

   >[!NOTE]
   Votre canal doit déjà comporter une image par défaut et les audiences doivent être préconfigurées comme indiqué à l’étape (3).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   Vous devez avoir défini vos **configurations** **ContextHub** à l’aide de l’onglet **Propriétés** --&gt; **Personnalisation**.

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   Si vous n’ajoutez pas la **marque** sous **Configurations de ciblage** lors de la définition des **Configurations ContextHub** pour votre projet, comme illustré ci-dessus, vous devez sélectionner la **marque** et l’**Activité** lors du démarrage du processus de ciblage, à l’étape suivante.

1. Sélectionnez **Ciblage** dans l’éditeur. Sélectionnez ensuite **Marque** et l’**Activité** dans le menu déroulant, puis cliquez sur **Commencer le ciblage**.
1. Vérification de l’aperçu

   1. Cliquez sur **Aperçu.** Ouvrez également votre feuille de calcul Google et mettez à jour sa valeur.
   1. Définissez la valeur sur Restaurant1 &gt; Restaurant2. Vous devriez voir une image de steak. Si la valeur est Restaurant1 &lt; Restaurant2, vous devriez voir à l’écran une image de nourriture thaïlandaise.
   ![result5](assets/result5.gif)

## Cas d’utilisation 4 : superposition de texte sur des cartes numériques {#use-case-digital-menu-board-text-overlay}

L’exemple ci-dessous illustre l’utilisation de cartes numériques, devenue courante dans les restaurants et les établissements de restauration rapide.

### Description {#description-3}

Le cas d’utilisation ci-dessous décrit l’utilisation d’une superposition de texte dans un canal de séquence et l’actualisation de ce texte suite à une modification de prix dans Google Sheets.

### Approche procédurale {#procedural-approach-1}

Pour mettre en œuvre la carte numérique avec une superposition de texte pour votre projet AEM Screens, procédez comme suit :

1. **Remplissage des feuilles de calcul Google Sheets**

   1. Accédez à vos feuilles de calcul Google Sheets.
   1. Ajoutez une colonne de tarifs, comme illustré ci-dessous.
   ![screen_shot_2019-05-05at111344am](assets/screen_shot_2019-05-05at111344am.png)

1. **Ajout d’une image au canal de séquence**

   1. Naviguez et sélectionnez votre canal (**DataDrivenAssets** —&gt; **Canaux** —&gt; **DataDrivenTextOverlay**).

   1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.
   1. Faites glisser une image de tarte aux pommes et déposez-la dans l’éditeur.
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **Ajout d’une superposition de texte à l’image**

   1. Sélectionnez l’image dans l’éditeur, puis cliquez sur Configurer.
   1. Accédez à l’onglet **Superposition de texte** et ajoutez la superposition de texte à l’image. Pour récupérer la valeur dans vos feuilles de calcul Google Sheets, veillez à ce qu’elle soit placée entre accolades. Par exemple, le prix est récupéré dans les feuilles de calcul Google Sheets et est mentionné comme **{price}** lors de la définition de la superposition de texte.

   1. Accédez à l’onglet **ContextHub** et configurez la valeur à extraire des feuilles de calcul Google Sheets, comme illustré ci-dessous.
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **Vérification de l’aperçu**

   <!-- Edit text in steps below. wonky-->

   1. Cliquez sur **Aperçu**.  Ouvrez également votre feuille de calcul Google et mettez à jour sa valeur.
   1. Modifiez la valeur sous le **prix** et notez que ce changement est reflété dans la valeur utilisée dans la superposition de texte, comme illustré ci-dessous.
   ![textoverlay_result-1](assets/textoverlay_result-1.gif)
