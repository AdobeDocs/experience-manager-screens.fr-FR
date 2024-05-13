---
title: Notes de mise à jour du pack de fonctionnalités AEM Screens 202401
description: Découvrez le pack de fonctionnalités AEM Screens 202401 publié le mercredi 2 janvier 2024.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 62%

---

# Notes de mise à jour du pack de fonctionnalités 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe vous recommande d’effectuer la mise à niveau vers la dernière version de Adobe Experience Manager 6.5 (AEM 6.5). Obtenez les informations les plus récentes sur la version [here](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/release-notes/release-notes).

## Disponibilité {#availability}

Le pack de fonctionnalités 11.1 d’AEM 6.5 a été publié pour AEM Screens.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.11.1 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html) à l’aide de votre Adobe ID. Accédez au **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack intitulé **AEM 6.5 Screens FP11.1**.

## Date de publication {#release-date}

La date de publication du pack de fonctionnalités AEM Screens 202204 est le 2 janvier 2024.

### Nouveautés {#what-is-new}

Cette version comprend uniquement des correctifs de sécurité.

### Correctifs {#bug-fixes}

* Problème XSS dans le champ « Texte inactif » du périphérique AEM Screens. (SCRNS-2614)

* Problème XSS à `screens/dashboard/device.html` au moyen de la fonction `Clear cache` boîte de dialogue d’action. (SCRNS-2632)

* Problème XSS dans la configuration du lecteur Screens sur `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* Le XSS stocké dans le titre du périphérique se déclenche lorsqu’un périphérique est supprimé. (SCRNS-2653)

* Problème XSS sur `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* XSS reflété avec le paramètre `item` sur `/screens/register-device-wizard.html`. (SCRNS-2670)

* XSS reflété dans `screens/dashboard/device.html` au moyen de la fonction `returnPage` . (SCRNS-3056)

* Redirection ouverte sur assign-device-wizard.html. (SCRNS-3444)

* Redirection ouverte dans le tableau de bord du périphérique. (SCRNS-3443)

* Problème XSS sur `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Boutons Fixe, Absence de planning de périodicité et Ajouter un planning : problème détecté dans la planification des canaux. (SCRNS-2739)
