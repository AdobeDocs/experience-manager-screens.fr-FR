---
title: Notes de mise à jour du pack de fonctionnalités 202008
description: En savoir plus sur le pack de fonctionnalités 202008 AEM Screens, publié le 3 septembre 2020.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: bd466576-a6d3-494c-82e5-c5326b6e0aca
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: ht
source-wordcount: '342'
ht-degree: 100%

---

# Notes de mise à jour du pack de fonctionnalités 202008 {#release-notes-for-feature-pack}

>[!CAUTION]
>
>Adobe recommande d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). AEM Screens fournit une prise en charge de maintenance pour la plateforme AEM 6.3 Screens.

## Disponibilité {#availability}

AEM Screens inclus dans le pack de fonctionnalités 5 d’AEM 6.5.

Vous pouvez télécharger le dernier pack de fonctionnalités pour AEM Screens 6.5.3 à partir du [Portail de distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier pack de fonctionnalités.

## Date de publication {#release-date}

La date de publication du pack de fonctionnalités 202008 d’AEM Screens est le 3 septembre 2020.

### Nouveautés {#what-is-new}

* **Mode Chronologie sur le tableau de bord de planification**

  Le mode Chronologie permet à l’utilisateur d’afficher les planifications attribuées au canal à l’aide du tableau de bord d’affichage.

  Voir [Mode Chronologie](/help/user-guide/channel-assignment-latest-fp.md#timeline-view) pour plus d’informations.

* **Planning de périodicité**

  Le planning de périodicité permet de définir un planning récurrent pour votre canal. Vous pouvez configurer plusieurs plannings de périodicité pour un canal.

  Pour plus d’informations, voir [Planning de périodicité](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule).

* **Fonctionnalités de reconnaissance vocale pour AEM Screens**

  La fonction de reconnaissance vocale permet de modifier le contenu d’un canal AEM Screens par interaction vocale.

  Un auteur ou une autrice de contenu peut configurer un affichage pour permettre la reconnaissance vocale. Cette fonctionnalité permet aux clientes et clients d’utiliser la voix pour interagir avec leurs écrans.

  Voir [Reconnaissance vocale](voice-recognition.md) pour plus d’informations.

### Problèmes connus et correctifs {#known-issues}

Vous devez configurer un environnement pour le lecteur Windows ou Android™ si vous utilisez le pack de services AEM Screens 6.5.5.

Changez la valeur de **SameSite attribute for the login-token cookies** de **Lax** à **None** dans **Configuration de la console web Adobe
Experience Manager** sur toutes les instances de création et de publication AEM.

* Voir [Mise en œuvre du lecteur Windows 10](implementing-windows-player.md#fp-environment-setup) pour plus d’informations.

* Voir [Mise en œuvre du lecteur Android™](implementing-android-player.md#fp-environment-setup) pour plus d’informations.

### Lecteurs AEM Screens publiés

Les lecteurs AEM Screens suivants sont publiés pour la version d’AEM Screens incluse dans le pack de fonctionnalités 5 d’AEM 6.5.

* Chrome OS
* Windows
* Android™

#### Téléchargements du lecteur AEM Screens

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, reportez-vous à la section **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
