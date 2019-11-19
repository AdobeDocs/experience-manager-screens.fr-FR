---
title: Intégration d’Adobe Analytics avec AEM Screens
seo-title: Intégration d’Adobe Analytics avec AEM Screens
description: Suivez cette page pour en savoir plus sur l’intégration immédiate d’AEM Screens à Adobe Analytics et vous fournir une preuve de lecture.
seo-description: Suivez cette page pour en savoir plus sur l’intégration immédiate d’AEM Screens à Adobe Analytics et vous fournir une preuve de lecture.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Intégration d’Adobe Analytics avec AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Cette fonctionnalité d’AEM Screens est disponible uniquement si vous avez installé AEM 6.4.2 Feature Pack 2 et AEM 6.3.3 Feature Pack 4.

>Pour accéder à l’un ou l’autre de ces Feature Packs, vous devez contacter l’assistance technique d’Adobe et demander l’accès. Une fois que vous disposez des autorisations, vous pouvez le télécharger à partir de Package Share.
>
Cette section traite des sujets suivants :

* **Présentation**
* **Détails architecturaux**
* **Configuration des propriétés**

## Présentation {#overview}

***Les écrans*** AEM tirent parti d’Adobe Analytics et vous permettent d’obtenir quelque chose d’unique sur le marché : des analyses cross-canal qui permettent de corréler le contenu affiché à l’emplacement avec d’autres sources de données.

AEM Screens fournit une intégration prête à l’emploi avec Adobe Analytics et vous fournit une preuve de lecture.

Cette section décrit les fonctionnalités suivantes liées à la connexion d’un projet AEM Screens à Adobe Analytics :

* Permet la création de rapports de preuve de lecture par périphérique
* Permet la création de rapports de preuve de jeu par fichier
* Garantit que tous les événements du lecteur sont capturés et horodatés
* Garantit que tous les événements du lecteur sont stockés localement si la lecture n’est pas connectée à un réseau
* Permet de créer des boucles de commentaires pour suivre les événements de lecture dans le temps.
* Permet au système de modifier le contenu et les mises en page en fonction des critères de réussite définis par l’auteur du contenu

L’intégration d’Adobe Analytics à AEM Screens permet d’appliquer les *objectifs* suivants :

* Activer le retour sur investissement à partir des implémentations de signature numérique
* Intégration d’Analytics en tant que base pour l’activation future de la collecte et de l’analyse des informations d’utilisation

## Détails architecturaux {#architectural-details}

Les clients d’AEM Screens souhaitent comprendre le contenu affiché à quelle heure et pendant combien de temps (agrégé). C'est une fonctionnalité commune de la solution de signalisation. Plutôt que de créer nos propres analyses, AEM Screens exploitera Adobe Analytics, ce qui nous permettra d’obtenir quelque chose d’unique sur le marché : des analyses intercanaux qui permettent de corréler le contenu affiché à l’emplacement géographique avec d’autres sources de données.

Le diagramme architectural suivant explique l’intégration d’Adobe Analytics avec les écrans AEM :

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Activation d’Adobe Analytics dans AEM Screens {#enabling-adobe-analytics-in-aem-screens}

Les paramètres Adobe Analytics peuvent être configurés à partir de la console OSGi.

Accédez à Configuration **de la console Web** Adobe Experience Manager pour configurer Adobe Analytics pour AEM Screens, comme illustré dans la figure ci-dessous :

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Analyse des écrans : Flux d'activation {#screens-analytics-enablement-flow}

>[!CAUTION]
Avant de configurer les propriétés, contactez votre gestionnaire des relations Adobe pour créer un ticket afin d’obtenir une clé **API** Analytics et un projet **d’** analyse à utiliser avec AEM Screens.

![]()

### Configuration des propriétés {#configuring-the-properties}

>[!CAUTION]
Avant de configurer les propriétés, contactez votre gestionnaire des relations Adobe pour créer un ticket afin d’obtenir une clé **API** Analytics et un projet **d’** analyse à utiliser avec AEM Screens.

Le tableau suivant met en évidence les propriétés avec leur description pour configurer Adobe Analytics pour les écrans AEM :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td><strong>URL Analytics</strong></td>
   <td>URL de publication des données d’analyse du lecteur<br /> </td>
  </tr>
  <tr>
   <td><strong>Clé d’API Analytics</strong></td>
   <td>Clé d’API pour l’authentification auprès du serveur Adobe Analytics (fournie par le gestionnaire de comptes)</td>
  </tr>
  <tr>
   <td><strong>Projet Analytics</strong></td>
   <td>Projet AEM Screens configuré sur vos analyses pour recevoir des données (fourni par le gestionnaire de comptes)</td>
  </tr>
  <tr>
   <td><strong>Environnement</strong></td>
   <td><p>Environnement d’étape ou de production.</p> <p><em>Pour le développement/l’étape</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> Pour la production <em></em> - https://cc-api-data.adobe.io/ingest/</p> </td>
  </tr>
  <tr>
   <td><strong>Fréquence d’envoi Analytics</strong></td>
   <td>Fréquence en minutes pour l’envoi de données d’analyse à partir des lecteurs. Par défaut, il est défini sur 15 minutes.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
Par défaut, la fréquence d’envoi **Analytics **est de 15 minutes.

#### Utilisation du service Adobe Analytics dans AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Ce scénario appelle l’API Analytics par le biais d’appels REST d’un service d’analyse dans les composants coeur du firmware et des écrans d’instruments afin de créer et d’envoyer explicitement des événements spécifiques à un cas d’utilisation particulier tout en autorisant l’extensibilité où tout message personnalisé peut être envoyé à Analytics à partir d’un canal développé personnalisé.

Les événements Analytics sont stockés hors ligne dans indexedDB et ultérieurement découpés et envoyés au cloud.

>[!NOTE]
Pour en savoir plus sur le ***séquencement*** et le modèle de données ***standard pour les événements***, reportez-vous à la section **[Configuration d’Adobe Analytics pour les écrans](configuring-adobe-analytics-aem-screens.md)** AEM.

