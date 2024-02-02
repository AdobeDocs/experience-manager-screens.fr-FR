---
title: Notes de mise à jour du Feature Pack 202401 de Screens
description: Consultez cette page pour obtenir des informations sur AEM Screens Feature Pack 202401, publié le 2 janvier 2024.
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: e172d2a4a3d2c1f3b555edc8f8ea41b663fc0a30
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 7%

---

# Notes de mise à jour du pack de fonctionnalités 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Il est recommandé d’effectuer la mise à niveau vers la dernière version de 6.5 Adobe Experience Manager (AEM 6.5). Nous pouvons obtenir les informations les plus récentes sur la version à partir de [here](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=en)

## Disponibilité {#availability}

AEM Screens a publié AEM 6.5 Feature Pack 11.1 .

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.11.1 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) à l’aide de votre Adobe ID. Accédez à **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack intitulé **AEM 6.5 Screens FP11.1**.

## Date de publication {#release-date}

La date de publication du Feature Pack 202204 d’AEM Screens est le 2 janvier 2024.

### Nouveautés {#what-is-new}

Cette version comprend uniquement des correctifs de sécurité.

### Correctifs {#bug-fixes}

* Problème XSS dans le champ &quot;Texte inactif&quot; du périphérique AEM Screens. (SCRNS-2614)

* Problème XSS à `screens/dashboard/device.html` via le `Clear cache` boîte de dialogue d’action. (SCRNS-2632)

* Problème XSS dans la configuration du lecteur Screens au niveau `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* Le fichier XSS stocké dans le titre du périphérique se déclenche lorsqu’un périphérique est supprimé. (SCRNS-2653)

* Problème XSS à `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* XSS reflété avec le paramètre `item` at `/screens/register-device-wizard.html`. (SCRNS-2670)

* XSS reflété dans `screens/dashboard/device.html` via le `returnPage` . (SCRNS-3056)

* Ouvrez Redirection sur assign-device-wizard.html. (SCRNS-3444)

* Ouvrez Redirection dans le tableau de bord du périphérique. (SCRNS-3443)

* Problème XSS à `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Boutons Fixe, Absente de planification de périodicité et Ajouter une planification : problème détecté dans la planification des canaux. (SCRNS-2739)

#### Téléchargements du lecteur AEM Screens   {#aem-screens-player-downloads}

Pour télécharger le dernier lecteur AEM Screens, voir **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
