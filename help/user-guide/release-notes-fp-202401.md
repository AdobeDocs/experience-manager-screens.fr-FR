---
title: Notes de mise à jour du pack de fonctionnalités AEM Screens 202401
description: Consultez cette page pour obtenir des informations sur le pack de fonctionnalités AEM Screens 202401, publié le 2 janvier 2024.
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: bdc8ff6c1291b7f0dc749e4a9f3a4c1d21678303
workflow-type: ht
source-wordcount: '232'
ht-degree: 100%

---

# Notes de mise à jour du pack de fonctionnalités 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Il est recommandé d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM 6.5). Pour obtenir des informations sur la dernière version, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=fr).

## Disponibilité {#availability}

Le pack de fonctionnalités 11.1 d’AEM 6.5 a été publié pour AEM Screens.

Vous pouvez télécharger le dernier pack de fonctionnalités pour AEM Screens 6.5.11.1 à partir du [Portail de distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier pack de fonctionnalités appelé **AEM 6.5 Screens FP11.1**.

## Date de publication {#release-date}

La date de publication du pack de fonctionnalités AEM Screens 202204 est le 2 janvier 2024.

### Nouveautés {#what-is-new}

Cette version comprend uniquement des correctifs de sécurité.

### Correctifs {#bug-fixes}

* Problème XSS dans le champ « Texte inactif » du périphérique AEM Screens. (SCRNS-2614)

* Problème XSS sur `screens/dashboard/device.html` via le boîte de dialogue d’action `Clear cache`. (SCRNS-2632)

* Problème XSS dans la configuration du lecteur Screens sur `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* Le XSS stocké dans le titre du périphérique se déclenche lorsqu’un périphérique est supprimé. (SCRNS-2653)

* Problème XSS sur `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* XSS reflété avec le paramètre `item` sur `/screens/register-device-wizard.html`. (SCRNS-2670)

* XSS reflété sur `screens/dashboard/device.html` via le paramètre `returnPage`. (SCRNS-3056)

* Redirection ouverte sur assign-device-wizard.html. (SCRNS-3444)

* Redirection ouverte dans le tableau de bord du périphérique. (SCRNS-3443)

* Problème XSS sur `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Boutons Fixe, Absence de planning de périodicité et Ajouter un planning : problème détecté dans la planification des canaux. (SCRNS-2739)