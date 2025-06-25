---
title: Notes de mise à jour du pack de fonctionnalités AEM Screens 20250327
description: Découvrez le pack de fonctionnalités 20250327 AEM Screens publié le vendredi 27 mars 2025.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: cadd83cd-fe64-436d-b3fd-6d72b9565885
source-git-commit: 6cdf350fa4e45b816d50b64252b8ed6d5e0904d0
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 34%

---

# Notes de mise à jour du pack de fonctionnalités 20250327 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobe recommande d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager 6.5 (AEM 6.5). Pour obtenir des informations sur la dernière version, cliquez [ici](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/release-notes/release-notes).
>>Adobe vous recommande d’utiliser FP11.6 avec SP(servicepack) >= 21.

## Disponibilité {#availability}

AEM Screens inclus dans le pack de fonctionnalités 11,6 d’AEM 6.5.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.11.6 à partir du [Portail de distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack appelé **AEM 6.5 Screens FP11.6**.

## Date de publication {#release-date}

La date de publication du pack de fonctionnalités 20250327 d’AEM Screens est le vendredi 27 mars 2025.

### Nouveautés {#what-is-new}

* Cette version corrige le conflit de package auquel les utilisateurs sont confrontés avec le pack de services 21 et versions ultérieures.

* Cette version corrige le problème d’affichage des cartes avec le SP22 et les versions ultérieures.

* **Mise à jour concernant les lecteurs AEM Screens**
   * Le lecteur AEM Screens basé sur Linux est officiellement obsolète. Il est conseillé aux utilisateurs de migrer vers un autre système d’exploitation pris en charge par AEM Screens.
   * Aucune autre mise à jour ou amélioration n’est apportée au lecteur AEM Screens basé sur Android. Nous recommandons aux utilisateurs de migrer vers un autre système d’exploitation pris en charge par AEM Screens.

### Correctifs {#bug-fixes}

* Conflit de packages avec le pack de services 21 et le pack de fonctionnalités Screens. (SCRNS-4638)

* Le tableau de bord Screens ne fonctionne pas. (SCRNS-4749)

* Problème XSS à /libs/screens/dcc/components/dashboard/clientlibs/device-clear-cache.js (SCRNS-4761)
