---
title: Intégration d’Adobe Analytics à AEM Screens
description: Découvrez l’intégration prête à l’emploi d’AEM Screens à Adobe Analytics et obtenez une preuve de lecture.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: ht
source-wordcount: '672'
ht-degree: 100%

---

# Intégration d’Adobe Analytics à AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Cette fonctionnalité d’AEM Screens est disponible uniquement si vous avez installé la version minimale du pack de fonctionnalités 2 d’AEM 6.4.2 ou du pack de fonctionnalités 4 d’AEM 6.3.3. Pour les clientes et clients du service cloud AEM Screens, contactez votre responsable des relations Adobe pour activer Adobe Analytics dans Screens Cloud.

>[!NOTE]
>
>Pour accéder à l’un de ces packs de fonctionnalités, contactez l’assistance technique Adobe et déposez une requête dans ce sens. Vous pouvez télécharger le dernier pack de fonctionnalités pour AEM Screens à partir du [Portail de distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html) en utilisant votre Adobe ID.

Cette section couvre les sujets suivants :

* **Présentation**
* **Particularités architecturales**
* **Configuration des propriétés**

## Vue d’ensemble {#overview}

***AEM Screens*** utilise Adobe Analytics ; vous obtenez ainsi une solution unique sur le marché : une analytique cross-canal permettant de mettre le contenu affiché à l’emplacement concerné en corrélation avec d’autres sources de données.

AEM Screens permet une intégration immédiate avec Adobe Analytics et vous fournit une preuve de lecture.

Cette section décrit les fonctionnalités suivantes liées à la connexion d’un projet AEM Screens avec Adobe Analytics :

* Permet de créer des rapports de preuve de lecture par appareil
* Permet de créer des rapports de preuve de lecture par ressource
* Veille à ce que tous les événements du lecteur soient capturés et horodatés
* Veille à ce que tous les événements du lecteur soient stockés localement s’il n’est pas connecté à un réseau
* Des boucles de rétroaction peuvent être créées pour suivre les événements de lecture à long terme.
* Permet au système de modifier le contenu et les dispositions selon les critères de réussite définis par l’auteur ou l’autrice du contenu

Ainsi, l’intégration d’Adobe Analytics avec AEM Screens permet de réaliser les *objectifs* suivants :

* Obtenir un retour sur investissement des implémentations d’affichage numérique
* Intégrer Analytics comme support employé pour collecter et analyser ultérieurement les informations d’utilisation

## Particularités architecturales {#architectural-details}

Un client ou une cliente AEM Screens souhaite connaître le contenu affiché, ainsi que sa durée et date et/ou heure d’affichage (affichage global). Il s’agit d’une fonctionnalité courante de la solution de signalétique numérique. Au lieu de créer une application d’analyse distincte, AEM Screens utilise Adobe Analytics. La combinaison nous permet d’obtenir quelque chose d’unique sur le marché : un analytique cross-canal qui permet de mettre le contenu affiché à l’emplacement en corrélation avec d’autres sources de données.

Le diagramme architectural suivant explique comment Adobe Analytics s’intègre avec AEM Screens :

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Activation d’Adobe Analytics dans AEM Screens {#enabling-adobe-analytics-in-aem-screens}

Les paramètres Adobe Analytics peuvent être configurés depuis la console OSGi.

Accédez à **Configuration de la console web Adobe Experience Manager** pour pouvoir configurer Adobe Analytics pour AEM Screens.

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics : flux d’activation {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Avant de configurer les propriétés, contactez le ou la responsable des relations Adobe pour créer un ticket et obtenir une **clé d’API Analytics**, ainsi qu’un **projet Analytics** afin de l’utiliser avec AEM Screens.

### Configuration des propriétés {#configuring-the-properties}

>[!CAUTION]
>
>Avant de configurer les propriétés, contactez le ou la responsable des relations Adobe pour créer un ticket et obtenir une **clé d’API Analytics**, ainsi qu’un **projet Analytics** afin de l’utiliser avec AEM Screens.

Le tableau suivant répertorie et décrit les propriétés permettant de configurer Adobe Analytics pour AEM Screens :

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td><strong>URL Analytics</strong></td>
   <td>URL de publication des données d’analyse depuis le lecteur. <br>
   Développement/étape</em> : https://cc-api-data-stage.adobe.io/ingest/<br /> <em>Production</em> : https://cc-api-data.adobe.io/ingest/<br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Clé d’API Analytics</strong></td>
   <td>Clé d’API utilisée à des fins d’authentification auprès du serveur Adobe Analytics (fournie par le responsable de compte Adobe).</td>
  </tr>
  <tr>
   <td><strong>Projet Analytics</strong></td>
   <td>Projet AEM Screens configuré sur les analyses de manière à recevoir des données (fourni par le responsable de compte Adobe).</td>
  </tr>
  <tr>
   <td><strong>Environnement</strong></td>
   <td><p>Environnement d’étape ou de production (sélectionnez Étape ou Production).</p></td>
  </tr>
  <tr>
   <td><strong>Fréquence d’envoi des données d’analyse</strong></td>
   <td>Fréquence d’envoi des données d’analyse depuis les lecteurs, en minutes. Par défaut, elle est définie sur 15 mn.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Par défaut, la **fréquence d’envoi des données d’analyse** est de 15 minutes.

#### Utilisation d’Adobe Analytics Service dans AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Ce scénario appelle l’API Analytics par le biais d’appels REST d’un service d’analyse du micrologiciel. Il instrumente également des composants AEM Screens pour créer et envoyer des événements spécifiques à un cas d’utilisation particulier. Toutes ces fonctionnalités tout en permettant l’extensibilité où tout message personnalisé peut être envoyé à Analytics à partir d’un canal développé de manière personnalisée.

Les événements Analytics sont stockés hors ligne dans indexedDB, puis segmentés et envoyés ultérieurement vers le cloud.

>[!NOTE]
>
>Pour en savoir plus sur le ***séquencement*** et le ***modèle de données standard d’événements***, voir **[Configuration d’Adobe Analytics pour AEM Screens](configuring-adobe-analytics-aem-screens.md)**.
