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
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Canal piloté par le stock{#inventory-driven-channel}

## Prise en main des canaux pilotés par le stock {#getting-started-with-inventory-driven-channels}

Cette section décrit un exemple de cas d'utilisation qui met l'accent sur la création et la gestion d'un changement de fichier lié aux données à l'aide de Google Sheets.

### Conditions préalables {#preconditions}

Avant de commencer cette utilisation, assurez-vous de comprendre comment :

* **[Création et gestion des canaux](managing-channels.md)**
* **[Création et gestion des emplacements](managing-locations.md)**
* **[Création et gestion de calendriers](managing-schedules.md)**
* **[Enregistrement de périphérique](device-registration.md)**

### Acteurs principaux {#primary-actors}

Auteurs de contenu

### Terminologie {#terminolgies}

Suivez les termes ci-dessous qui jouent un rôle important dans la compréhension et la mise en place du projet dans les différents cas d'utilisation :

**Activité** Activité fait référence à la catégorie.

**Projet de zone** principal

**Audience** Emplacement des données

**Marque** Marque

**Le segment** fait référence à un conteneur de ressources que vous tentez de cibler.

### Flux de base : Configuration du projet {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**Condition préalable requise :**
>
>Avant d’approfondir les détails de la configuration et de l’utilisation du changement de fichier lié aux données dans votre projet, veillez à créer un projet AEM Screens avec un canal de séquence. À des fins de démonstration, le projet intitulé **DataDrivenAsset** est créé et les canaux de séquence intitulés **DataDrivenRestaurant**, **DataDrivenTextOverlay**, **DataDrivenWeather et DataDrivenRetail sont ajoutés au projet, comme illustré dans la figure ci-dessous.******
>
>La création de quatre canaux différents n'est utilisée qu'à des fins de démonstration et pour présenter quatre cas d'utilisation différents dans différents canaux. Si vous ne souhaitez suivre qu'un seul cas d'utilisation, n'hésitez pas à créer un seul canal de séquence.

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

Suivez les sections ci-dessous pour créer un exemple de projet sur la création et la gestion d’un changement de fichier lié aux données à l’aide de feuilles Google dans un projet AEM Screens :

## Étape 1 : Configuration de la base de données {#step-setting-up-database}

>[!CAUTION]
>
>Google Sheets est utilisé dans l'exemple de système de base de données suivant à partir duquel les valeurs sont récupérées et est uniquement à des fins éducatives. Adobe n’accepte pas l’utilisation de feuilles de calcul Google pour les environnements de production.
>
>Pour plus d'informations, reportez-vous à la section [Obtention de la clé](https://developers.google.com/maps/documentation/javascript/get-api-key) API dans la documentation Google.

1. Connectez-vous à Google Docs.

   >[!NOTE]
   >
   >Vous devez disposer d’un compte dans Google Drive avant de créer une nouvelle feuille Google.

1. Démarrez une nouvelle feuille de calcul vide. Ajoutez du contenu à votre feuille Google et enregistrez-le. A des fins de démonstration, la feuille Google est nommée **ContextHubDemo**.
1. Cliquez sur **Partager** dans le coin supérieur droit de la feuille Google pour ouvrir la boîte de dialogue **Partager avec d’autres** . Cliquez sur l’option **Avancé** et définissez les paramètres sur **Activé - Toute personne disposant du lien**, comme illustré dans la figure ci-dessous.

   Cette étape vous permet d’accéder aux valeurs de la feuille de google.

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. Lorsque vous cliquez sur **Enregistrer** à partir de l’étape précédente, vous obtenez le lien pour la feuille Google. Enregistrez le clic pour les références ultérieures et cliquez sur **Terminé**.

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>Google Sheets est utilisé dans l'exemple suivant à des fins éducatives. Adobe n’accepte pas l’utilisation de feuilles de calcul Google pour les environnements de production.

## Étape 2 : Activation des API REST de Google Sheets {#step-enabling-the-google-sheets-rest-apis}

Une fois que vous avez configuré votre Google Sheet, vous devez activer l’API REST de Google Sheet pour accéder aux valeurs.

Pour savoir comment activer les API REST pour les feuilles Google, consultez la documentation des API Google.

1. Accédez à la Console [API](https://console.developers.google.com/apis/credentials)Google. Click **CREATE** to create a new project.

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. Saisissez le nom **du** projet **AssetChange** et cliquez sur **CRÉER**.
1. Une fois le projet créé, vous devez configurer la clé d'API. Cliquez sur **Créer les informations d’identification** et sélectionnez **clé API **pour générer la clé API pour votre projet. Enregistrez la clé API pour les références ultérieures.

   >[!NOTE]
   >
   >Ce projet de démonstration utilise la clé d'API gratuite de Google. Pour plus d'informations, consultez la section Tarification et restriction du site Web de Google **Obtenir la clé** API.

### Vérification de la configuration des feuilles Google {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;ID de votre feuille&gt;/values/Sheet1?key=&lt;clé de votre API&gt;

Par exemple :

Si le lien** Google Sheets** est *le suivant :*

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`, la variable

**L'ID** de feuille est : `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

**Clé** API : `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Ajout des deux valeurs dans la syntaxe ci-dessus :

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Vous devriez maintenant pouvoir afficher vos données dans la feuille.

## Étape 2 : Configuration d’AEM pour récupérer le contenu des feuilles Google {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

La section suivante décrit comment configurer Adobe Experience Manager (AEM) pour récupérer le contenu des feuilles Google.

1. Accédez à votre instance AEM et cliquez sur l’icône Outils dans la barre latérale gauche. Cliquez sur **Sites** —&gt; **ContextHub**, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Création d’une configuration de magasin ContextHub**

   1. Accédez à **global** &gt; **default** &gt; **ContextHub Configuration**.

   1. Cliquez sur** Créer &gt; Conteneur de configuration **et saisissez le titre sous** ContextHubDemo**.

   1. **** Accédez **à** ContextHubDemo **&gt;** Configuration du magasin ContentHub... pour ouvrir l’assistant **Configurer**
   1. Saisissez le **Titre** en tant que feuilles **** Google, le Nom **du** magasin en tant que feuilles de **googlesheets et le TypeMagasin en tant que feuilles decontextecontexthub.generic-jsonp.**********
   1. Cliquez sur **Suivant**
   1. Entrez votre configuration json spécifique. Par exemple, vous pouvez utiliser le fichier json suivant à des fins de démonstration.
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
   >Remplacez le code par votre *&lt;ID de feuille&gt;* et *&lt;clé API&gt;*, que vous avez récupéré à l’ **étape 1 : Configuration de la base de données.**

   >[!CAUTION]
   Si vous créez vos configurations de stockage Google Sheets en dehors du dossier hérité (par exemple dans votre propre dossier de projet), le ciblage ne fonctionnera pas de manière prête.
   Si vous souhaitez configurer les configurations de stockage des feuilles Google en dehors du dossier hérité global, vous devez définir le nom **de la** boutique comme **segmentation** et le type **de** magasin comme **aem.segmentation.** De plus, vous devez ignorer le processus de définition du fichier json tel que défini ci-dessus.

1. **Création d’une marque dans les activités**

   1. Accédez à **Personnalisation** &gt; **Activités à partir de votre instance AEM.**

   1. Cliquez sur** Créer** &gt; **Créer une marque**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. Votre marque est maintenant créée comme illustré ci-dessous.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
Problème connu :
Pour ajouter une zone, supprimez le gabarit de l’URL, par exemple
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. Création d'une zone dans votre marque**

   1. Cliquez sur **Créer** &gt; **Créer une zone**

   1. Select **Area** from the** Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**. Votre zone sera créée dans votre activité.

1. **Création de segments dans les audiences**

   1. Accédez à **Personnalisation** &gt; **Audiences** &gt; **We.Retail** depuis votre instance AEM.
   1. Cliquez sur **Créer** &gt; **Créer un segment** Context Hub. La boîte de dialogue Nouveau segment ContextHub s’ouvre.
   1. Enter the **Title** as **SheetA1 1** and click **Create**. De même, créez un autre segment intitulé **FeuilleA2 2**.

1. **Modification des segments**

   1. Sélectionnez les **feuilles de segment A1 1** (créées à l’étape (5)), puis cliquez sur **Modifier** dans la barre d’actions.

   1. Faites glisser et déposez la **comparaison : Propriété : composant Value** de l’éditeur.
   1. Cliquez sur l’icône de clé à molette pour ouvrir la boîte de dialogue **Comparaison d’une propriété avec une valeur** .
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante du nom **de la** propriété.

   1. Sélectionnez l’ **opérateur** **Egal **dans le menu déroulant.

   1. Saisissez la **valeur** **1**.
   >[!NOTE]
   AEM valide vos données de la feuille Google en affichant votre segment en vert.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   De même, modifiez les valeurs des propriétés en **feuilles A1 2**.

   1. Faites glisser et déposez la **comparaison : Propriété : composant Value** de l’éditeur.
   1. Cliquez sur l’icône de clé à molette pour ouvrir la boîte de dialogue **Comparaison d’une propriété avec une valeur** .
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante du nom **de la** propriété.

   1. Sélectionnez l’ **opérateur** **Egal **dans le menu déroulant.

   1. Saisissez la **valeur** **2**.
   >[!NOTE]
   Les règles appliquées dans les étapes précédentes ne sont qu’un exemple de configuration des segments pour la mise en oeuvre des cas d’utilisation suivants.

## Étape 3 : Configuration des configurations Context Hub dans le canal AEM Screens {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

Suivez les étapes ci-dessous pour configurer les configurations ContextHub et le chemin de segments vers le canal AEM Screens.

1. Accédez à l’un des canaux AEM Screens (**DataDrivenRetail**) que vous avez créé, en tant que prérequis.
1. Sélectionnez le canal (**DataDrivenRetail**) **et cliquez sur** Propriétésdans la barre d’actions.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Sélectionnez l’onglet **Personnalisation** pour configurer les configurations ContextHub.

   1. Sélectionnez le chemin **ContextHub** en tant que **libs** &gt; **settings** &gt; **cloudsettings &gt; default &gt;Configurations ContextHub et cliquez surSelect.**************

   1. Sélectionnez le chemin **des segments** en tant que **conf** &gt; **We.Retail **&gt; **Paramètres** &gt; **wcm &gt; segments, puis cliquez surSélectionner.**********

   1. Cliquez sur **Enregistrer et fermer**.
   >[!NOTE]
   Utilisez ContextHub et le chemin Segments, où vous avez initialement enregistré vos configurations et segments de concentrateur de contexte.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   Si vous ne sélectionnez pas la **marque** sous Configuration **du** ciblage dans la boîte de dialogue ci-dessus, vous devez sélectionner la marque et l’activité lorsque vous démarrez le processus de ciblage.

1. Accédez à **DataDrivenRetail** et sélectionnez-le dans **DataDrivenAssets** &gt; **Canaux **et cliquez sur **Modifier** dans la barre d’actions.

   >[!NOTE]
   Si vous avez correctement configuré tout, l’option **Ciblage** s’affiche dans la liste déroulante de l’éditeur, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Une fois que vous avez configuré les configurations ContextHub pour votre canal, veillez à suivre les étapes précédentes de 1 à 4, pour les trois autres canaux de séquence, si vous souhaitez suivre tous les cas d’utilisation ci-dessous.

## Cas d’utilisation 1 : Activation du stock de vente au détail {#use-case-retail-inventory-activation}

Le cas d’utilisation suivant illustre trois images différentes en fonction des valeurs de votre feuille Google.

### Description {#description}

Ce cas d’utilisation présente le stock de vente au détail de trois chemises à sweat-shirts de couleur différente. Selon le nombre de sweats disponibles en stock enregistrés dans les feuilles Google, l’image (rouge, vert ou bleu) avec le plus grand nombre de sweats est affichée à l’écran.

Dans ce cas d’utilisation, le pull rouge, vert ou bleu s’affichera sur votre écran en fonction de la valeur la plus élevée du nombre de pulls disponibles.

### Procédure {#procedure}

Suivez les étapes ci-dessous pour mettre en oeuvre le cas d'utilisation de l'activation du stock de détail :

1. **Renseigner les feuilles de Google**

   1. Accédez à la feuille Google ContextHubDemo.
   1. Ajoutez trois colonnes (Rouge, Vert et Bleu) avec les valeurs correspondantes pour trois sweatshirts différents.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuration des audiences conformément aux exigences**

   1. Accédez aux segments de votre audience (créés à l’étape(5) de la section ***Étape 2 : Configuration d’AEM pour récupérer le contenu des feuilles*** Google).
   1. Ajoutez trois nouveaux segments **For_Red**, **For_Green** et **For_Blue**.

   1. Sélectionnez **For_Red** et cliquez sur **Modifier** dans la barre d’actions.

   1. Faites glisser et déposez la **comparaison : Propriété : propriété** de l’éditeur et cliquez sur l’icône Configurer pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante du nom de la **première propriété.**

   1. Sélectionnez l’ **opérateur** **supérieur à **dans le menu déroulant.

   1. Sélectionner le type **de** données comme **nombre**

   1. Sélectionnez **googlesheets/value/1/1** dans la liste déroulante du **deuxième nom de propriété.**

   1. Faire glisser et déposer **une autre comparaison : Propriété : propriété **de l’éditeur et cliquez sur l’icône Configurer pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante du nom de la **première propriété.**

   1. Sélectionnez l’ **opérateur** **supérieur à **dans le menu déroulant.

   1. Sélectionner le type **de** données comme **nombre**

   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante du **deuxième nom de propriété.**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   De même, modifiez et ajoutez des règles de propriétés de comparaison au segment **For_Blue** , comme illustré dans la figure ci-dessous :

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   De même, modifiez et ajoutez des règles de propriété de comparaison au ** For_Green **segment, comme illustré dans la figure ci-dessous :

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   Vous remarquerez que pour les segments **For_Green** et **For_Green**, les données ne peuvent pas être chargées dans l’éditeur car seule la première comparaison est valide à ce jour, selon les valeurs de la feuille Google.

1. Naviguez et sélectionnez votre **canal **DataDrivenRetail (un canal de séquence) et cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   Vous auriez dû configurer vos **configurations** ContextHub **à l’aide de l’onglet** Propriétés **du canal —&gt;** **Personnalisation.**

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Si vous n’ajoutez pas la **marque** sous Configurations **de** ciblage lors de la configuration des configurations **ContextHub pour votre projet, comme illustré dans l’image ci-dessus, vous devez sélectionner la** **marque et Activity lors du démarrage du processus de ciblage, à l’étape suivante.******

1. **Ajout d’une image par défaut**

   1. Ajoutez une image par défaut à votre canal et cliquez sur **Ciblage**.
   1. Sélectionnez **Marque** et **Activité** dans le menu déroulant, puis cliquez sur **Démarrer le ciblage**.

   1. Cliquez sur **Commencer le ciblage**.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Avant de commencer le ciblage, vous devez ajouter les segments (**For_Green**, **For_Red** et **For_Blue**) en cliquant sur **+ Ajouter le ciblage d’expérience dans le rail latéral, comme illustré dans la figure ci-dessous.**

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Ajoutez les images aux trois scénarios différents comme illustré ci-dessous.

   ![detail_targeting](assets/retail_targeting.gif)

1. **Vérification de l’aperçu**

   1. Click **Preview.** Ouvrez également votre feuille Google et mettez à jour sa valeur.
   1. Modifiez la valeur des trois colonnes et vous constaterez que l’image d’affichage est mise à jour en fonction de la valeur la plus élevée du stock.
   ![detail_result](assets/retail_result.gif)

## Cas d’utilisation 2 : Activation météorologique du centre de voyage {#use-case-travel-center-weather-activation}

Le cas d’utilisation suivant illustre deux images différentes en fonction des valeurs de votre feuille Google.

### Description {#description-1}

Dans ce cas d’utilisation, si votre feuille Google a une valeur inférieure à 50, une image avec boissons chaudes s’affiche et si la valeur est supérieure ou égale à 50, l’image avec boissons froides s’affiche. En cas de valeur différente ou nulle, le lecteur affichera une image par défaut.

### Procédure {#procedure-1}

Suivez les étapes ci-dessous pour implémenter le cas d’utilisation d’activation météorologique du centre de voyage pour votre projet AEM Screens :

1. **Renseigner les feuilles de Google**

   1. Accédez à la feuille Google ContextHubDemo.
   1. Ajoutez une colonne avec **Titre1** avec la valeur correspondante pour la température.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuration des segments dans Audiences conformément aux exigences**

   1. Accédez aux segments de votre audience (créés à l’étape(5) de la section ***Étape 2 : Configuration d’AEM pour récupérer le contenu des feuilles*** Google).
   1. Sélectionnez les **feuilles A1 1** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône Configurer pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante du nom de la **propriété.**

   1. Sélectionnez l’ **opérateur** **supérieur ou égal à **dans le menu déroulant.

   1. Saisissez la **valeur** **50.**

   1. De même, sélectionnez les feuilles A1 2 *** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône Configurer pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/0** dans la liste déroulante du nom de la **propriété.**

   1. Sélectionnez l’ **opérateur** **Inférieur à **dans le menu déroulant.

   1. Saisissez la **valeur** **50.**

1. Naviguez et sélectionnez votre canal (), puis cliquez sur **Modifier** dans la barre d’actions. Dans l’exemple suivant, **DataDrivenWeather**, un canal séquentiel est utilisé pour présenter la fonctionnalité.

   >[!NOTE]
   Votre canal doit déjà avoir une image par défaut et les audiences doivent être préconfigurées comme décrit à l’étape (3)

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   Vous auriez dû configurer vos **configurations** ContextHub **à l’aide de l’onglet** Propriétés **du canal —&gt;** **Personnalisation.**

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   Si vous n’ajoutez pas la **marque** sous Configurations **de** ciblage lors de la configuration des configurations **ContextHub pour votre projet, comme illustré dans l’image ci-dessus, vous devez sélectionner la** **marque et Activity lors du démarrage du processus de ciblage, à l’étape suivante.******

1. Sélectionnez **Ciblage** dans l’éditeur, sélectionnez **Marque** et **Activité** dans le menu déroulant, puis cliquez sur **Démarrer le ciblage.**

   >[!NOTE]
   Si vous avez ajouté la **marque** sous Configurations **de** ciblage lors de la configuration des configurations **ContextHub pour votre projet, vous n’avez pas besoin de sélectionner la** **marque et Activity dans cette étape.******

   ![new_activity3](assets/new_activity3.gif)

1. Vérification de l’aperçu

   1. Click **Preview.** Ouvrez également votre feuille Google et mettez à jour sa valeur.
   1. Remplacez la valeur par une valeur inférieure à 50, vous devriez pouvoir voir une image des boissons d’été. Si la valeur de la feuille Google est supérieure ou égale à 50, vous pouvez afficher une image de boisson chaude.
   ![result3](assets/result3.gif)

## Cas d’utilisation 3 :Activation de réservation d'hébergement {#use-case-hospitality-reservation-activation}

Le cas d’utilisation suivant illustre deux images différentes en fonction des valeurs et de la formule appliquées dans votre feuille Google.

### Description {#description-2}

Dans ce cas d’utilisation, la feuille Google est renseignée avec le pourcentage de réservation sur deux restaurants **Restaurant1** et **Restaurant2**. Une formule est appliquée sur la base des valeurs de Restaurant1 et Restaurant2 et sur la base de la formule, la valeur 1 ou 2 est affectée à la colonne **AdTarget** .

Si **Restaurant1** &gt; **Restaurant2**, la valeur **AdTarget** est 1, sinon **AdTarget est affecté à la valeur 2.** La valeur 1 génère l’option *Steak food* et la valeur 2 affiche l’option *Thai food* sur votre écran.

### Approche procédurale {#procedural-approach}

Suivez les étapes ci-dessous pour implémenter le cas d’utilisation d’activation des réservations d’hébergement pour votre projet AEM Screens :

1. Renseigner les feuilles de Google et ajouter la formule.

   Par exemple, appliquez la formule à la troisième colonne **AdTarget**, comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuration des segments dans Audiences conformément aux exigences**

   1. Accédez aux segments de votre audience (créés à l’étape(5) de la section ***Étape 2 : Configuration d’AEM pour récupérer le contenu des feuilles*** Google).
   1. Sélectionnez les **feuilles A1 1** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône Configurer pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante du nom de la **propriété.**

   1. Sélectionnez l’ **opérateur** **égal **dans le menu déroulant.

   1. Saisissez la **valeur** comme **1**

   1. De même, sélectionnez les feuilles A1 2 *** et cliquez sur **Modifier**.

   1. Sélectionnez la propriété de comparaison et cliquez sur l’icône Configurer pour modifier les propriétés.
   1. Sélectionnez **googlesheets/value/1/2** dans la liste déroulante du nom de la **propriété.**

   1. Sélectionnez **Opérateur** comme **2**

1. Naviguez et sélectionnez votre canal (), puis cliquez sur **Modifier** dans la barre d’actions. Dans l’exemple suivant, **DataDrivenRestaurant**, un canal séquentiel est utilisé pour présenter la fonctionnalité.

   >[!NOTE]
   Votre canal doit déjà avoir une image par défaut et les audiences doivent être préconfigurées comme décrit à l’étape (3).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   Vous auriez dû configurer vos **configurations** ContextHub **à l’aide de l’onglet** Propriétés **du canal —&gt;** **Personnalisation.**

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   Si vous n’ajoutez pas la **marque** sous Configurations **de** ciblage lors de la configuration des configurations **ContextHub pour votre projet, comme illustré dans l’image ci-dessus, vous devez sélectionner la** **marque et Activity lors du démarrage du processus de ciblage, à l’étape suivante.******

1. Sélectionnez **Ciblage** dans l’éditeur, sélectionnez **Marque** et **Activité** dans le menu déroulant, puis cliquez sur **Démarrer le ciblage.**
1. Vérification de l’aperçu

   1. Click **Preview.** Ouvrez également votre feuille Google et mettez à jour sa valeur.
   1. Changez la valeur dans Restaurant1 &gt; Restaurant2, vous devriez pouvoir voir une image de steak et Restaurant1 &lt; Restaurant12, vous devriez pouvoir voir cette image de nourriture sur votre écran.
   ![result5](assets/result5.gif)

## Cas d’utilisation 4 : Incrustation de texte du menu numérique {#use-case-digital-menu-board-text-overlay}

Le cas d'utilisation suivant illustre un cas d'utilisation de carte de menu numérique courant dans les restaurants et les fast food.

### Description {#description-3}

Le cas d’utilisation suivant décrit l’utilisation de l’incrustation de texte dans un canal séquentiel et comment la mise à jour de la valeur du prix dans les feuilles Google déclenche une mise à jour dans la mise à jour du composant d’incrustation de texte.

### Approche procédurale {#procedural-approach-1}

Suivez les étapes ci-dessous pour mettre en oeuvre le panorama de menus numérique avec le cas d’utilisation d’incrustation de texte pour votre projet AEM Screens :

1. **Renseigner les feuilles de Google**

   1. Accédez à vos feuilles Google.
   1. Ajoutez une colonne avec la valeur de tarification pour le cas d’utilisation, comme illustré dans la figure ci-dessous.
   ![screen_shot_2019-05-05at111344am](assets/screen_shot_2019-05-05at111344am.png)

1. **Ajout d’une image au canal de séquence**

   1. Naviguez et sélectionnez votre canal (**DataDrivenAssets** —&gt; **Canaux** —&gt; **DataDrivenTextOverlay**).

   1. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.
   1. Faites glisser une image de tarte aux pommes dans l’éditeur.
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **Ajout d’une incrustation de texte à l’image**

   1. Sélectionnez l’image dans l’éditeur, puis cliquez sur Configurer.
   1. Accédez à l’onglet Incrustation **de** texte et ajoutez l’incrustation de texte à l’image. Pour obtenir la valeur de vos feuilles Google, assurez-vous que la valeur est entourée des accolades. Par exemple, le prix est récupéré dans les feuilles Google et est mentionné comme **{price}** lors de la définition de l’incrustation de texte.

   1. Accédez à l’onglet **ContextHub** et configurez la valeur à extraire des feuilles Google, comme illustré dans la figure ci-dessous.
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **Vérification de l’aperçu**

   <!-- Edit text in steps below. wonky-->

   1. Click **Preview**.  Ouvrez également votre feuille Google et mettez à jour sa valeur.
   1. Modifiez le sous **Prix** et vous noterez la valeur utilisée dans l’incrustation de texte en conséquence, comme illustré dans la figure ci-dessous.
   ![textoverlay_result-1](assets/textoverlay_result-1.gif)
