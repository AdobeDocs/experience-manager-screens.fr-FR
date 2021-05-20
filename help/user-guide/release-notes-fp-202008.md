---
title: Notes de mise à jour du Feature Pack 202008
description: Consultez cette page pour obtenir des informations sur AEM Screens Feature Pack 202008, publié le 3 septembre 2020.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: bd466576-a6d3-494c-82e5-c5326b6e0aca
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 100%

---

# Notes de mise à jour du Feature Pack 202008 {#release-notes-for-feature-pack}

>[!CAUTION]
>
>Il est recommandé d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). Screens fournit une prise en charge de maintenance pour la plate-forme AEM 6.3 Screens.

## Disponibilité {#availability}

AEM Screens inclus dans le Feature Pack 5 d’AEM 6.5.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.5 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack.

## Date de publication {#release-date}

La date de publication du Feature Pack 202008 d’AEM Screens est le 3 septembre 2020.

### Nouveautés {#what-is-new}

* **Mode Chronologie sur le tableau de bord de planification**

   Le mode Chronologie permet à l’utilisateur d’afficher les planifications attribuées au canal à l’aide du tableau de bord d’affichage.

   Voir [Mode Chronologie](/help/user-guide/channel-assignment-latest-fp.md#timeline-view) pour plus d’informations.

* **Planning de périodicité**

   Le planning de périodicité permet de définir une planification récurrente pour votre canal. Vous configurez plusieurs plannings de périodicité pour un canal.

   Pour plus d’informations, voir [Planning de périodicité](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule).

* **Fonctionnalités de reconnaissance vocale pour AEM Screens**

   La fonction de reconnaissance vocale permet de modifier le contenu d’un canal AEM Screens par interaction vocale.

   Un auteur de contenu peut configurer un affichage pour permettre la reconnaissance vocale. Cette fonction permet aux clients d’utiliser la voix pour interagir avec leurs écrans.

   Voir [Reconnaissance vocale](voice-recognition.md) pour plus d’informations.

### Problèmes et correctifs connus {#known-issues}

Vous devez configurer un environnement pour le lecteur Windows Android si vous utilisez le Service Pack AEM Screens 6.5.5.

Changez la valeur de **SameSite attribute for the login-token cookies** de **Lax** à **None** dans **Configuration de la console web Adobe
Experience Manager** sur toutes les instances de création et de publication AEM.

* Voir [Mise en œuvre du lecteur Windows 10](implementing-windows-player.md#fp-environment-setup) pour plus d’informations.

* Voir [Mise en œuvre du lecteur Android](implementing-android-player.md#fp-environment-setup) pour plus d’informations.

### Lecteurs AEM Screens publiés {#released-aem-screens-players}

Les lecteurs AEM Screens suivants sont publiés pour la version d’AEM Screens incluse dans le Feature Pack 5 d’AEM 6.5.

* Chrome OS
* Windows
* Android

#### Téléchargements du lecteur AEM Screens {#aem-screens-player-downloads}

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, reportez-vous à la section **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
