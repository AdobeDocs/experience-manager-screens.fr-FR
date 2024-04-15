---
title: Incorporation d’une application REACT à l’aide de l’éditeur d’applications monopages AEM et intégration à AEM Screens Analytics
description: Découvrez comment incorporer une application interactive monopage à l’aide de REACT (ou Angular) à l’aide de l’éditeur SPA d’AEM.
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 49%

---

# Incorporation d’une application REACT à l’aide de l’éditeur d’applications monopages AEM et intégration à AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

Vous pouvez incorporer une application interactive monopage à l’aide de REACT (ou Angular). Pour ce faire, utilisez l’éditeur SPA d’AEM qui est configuré par les professionnels d’. Vous pouvez également apprendre à intégrer votre application interactive à Adobe Analytics hors ligne.

## Utilisation de l’éditeur d’applications monopages AEM {#using-the-aem-spa-editor}

Suivez les étapes ci-dessous pour utiliser l’éditeur d’applications monopages AEM :

1. Cliquez sur le rapport de l’éditeur d’applications monopages AEM à l’adresse [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Cet archétype crée un projet Adobe Experience Manager minimal qui s’appuie sur des bonnes pratiques pour que vous puissiez démarrer vos propres projets d’application monopage (SPA). Les propriétés qui doivent être fournies lors de l’utilisation de cet archétype vous permettent de nommer comme vous le souhaitez toutes les parties de ce projet.

1. Pour créer un projet d’archétype de l’éditeur d’AEM, suivez les instructions du fichier Lisez-moi :

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >Cette documentation utilise la méthode **GroupId** as ***com.adobe.aem.screens*** et la variable **ArtifactId** as ***Mon exemple de SPA*** (valeurs par défaut). Vous pouvez choisir les vôtres selon vos besoins.

1. Une fois le projet créé, utilisez un IDE ou un éditeur de votre choix et importez le projet Maven généré.
1. Déployez sur votre instance AEM locale à l’aide de la commande ***mvn clean install -PautoInstallPackage***.

### Modification de contenu dans l’application REACT {#editing-content-in-the-react-app}

Pour modifier le contenu dans l’application REACT :

1. Accédez à `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (remplacez le nom d’hôte, le port et le nom du projet, le cas échéant).
1. Vous devez pouvoir modifier le texte affiché dans l’application Hello world.

### Ajout de l’application interactive REACT à AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Suivez les étapes ci-dessous pour ajouter l’application interactive REACT à AEM Screens :

1. Créez un projet AEM Screens. Voir [Création et gestion de projets](creating-a-screens-project.md) pour plus d’informations.
1. Créez un **Canal d’application** (de préférence) (modèle 1x1 ou canal multizone) dans la variable **Canaux** de votre projet AEM Screens.

   >[!NOTE]
   >**Canaux de séquence** sont déconseillés pour ce cas d’utilisation, car ils s’accompagnent par nature d’une logique de diaporama qui entre en conflit avec la nature interactive de l’expérience.
   >Voir [Création et gestion des canaux](managing-channels.md) pour plus d’informations.

1. Modifiez un canal de séquence et faites glisser et déposez un composant de page incorporé.

   Voir [Ajout de composants à un canal](adding-components-to-a-channel.md) pour plus d’informations.

   >[!NOTE]
   >
   >Veillez à ajouter l’événement d’interaction utilisateur lors de l’attribution du canal à l’affichage.

1. Cliquez sur **Modifier** à partir de la barre d’actions afin de pouvoir modifier les propriétés du canal.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Faites glisser et déposez le **Page incorporée** , ou réutilisez le composant existant dans un canal d’application, puis sélectionnez la page d’accueil sous l’application mysamplespa, par exemple : ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Attribuez le canal à un affichage.

   >[!NOTE]
   >Veillez à ajouter l’événement d’interaction utilisateur lors de l’attribution du canal à l’affichage.

1. Enregistrez un lecteur sur ce projet et affectez-le à l’affichage. Vous devriez maintenant pouvoir voir votre application interactive s’exécuter sur AEM Screens.

   Voir [Enregistrement de périphérique](device-registration.md) pour plus d’informations sur l’enregistrement d’un périphérique.

## Intégration de l’application monopage avec Adobe Analytics avec la fonctionnalité hors ligne via AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Suivez les étapes ci-dessous pour intégrer l’application monopage à Adobe Analytics avec la fonctionnalité hors ligne via AEM Screens :

1. Configuration d’Adobe Analytics dans AEM Screens.

   Voir [Configuration d’Adobe Analytics avec AEM Screens](configuring-adobe-analytics-aem-screens.md) pour plus d’informations sur l’exécution du séquencement dans Adobe Analytics avec AEM Screens et l’envoi d’événements personnalisés à l’aide d’Adobe Analytics hors ligne.

1. Modifiez votre application de réaction dans l’IDE/l’éditeur de votre choix (en particulier le composant de texte ou tout autre composant dont vous souhaitez qu’il commence à émettre des événements).
1. Sur l’événement click ou tout autre événement que vous souhaitez capturer pour votre composant, ajoutez les informations d’analyse à l’aide du modèle de données standard.

   Voir [Configuration d’Adobe Analytics avec AEM Screens](configuring-adobe-analytics-aem-screens.md) pour plus d’informations.

1. Appelez l’API AEM Screens Analytics afin de pouvoir enregistrer l’événement hors ligne et l’envoyer en rafales à Adobe Analytics.

   Par exemple :

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >Le micrologiciel du lecteur ajoute automatiquement plus de détails sur le lecteur et son environnement d’exécution aux données d’analyse personnalisées que vous envoyez. Par conséquent, vous devrez peut-être capturer les détails du système d’exploitation/de l’appareil de bas niveau, sauf si nécessaire. Concentrez-vous sur les données d’analyse commerciale.
