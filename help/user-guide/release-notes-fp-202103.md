---
title: Notes de mise à jour du pack de fonctionnalités 202103
description: Découvrez le pack de fonctionnalités 202103 AEM Screens, publié le 5 mars 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 55%

---

# Notes de mise à jour du pack de fonctionnalités 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe vous recommande d’effectuer la mise à niveau vers la dernière version de Adobe Experience Manager (AEM). AEM Screens assure la prise en charge de la maintenance de la plateforme AEM 6.3 Screens.

## Disponibilité {#availability}

AEM Screens inclus dans le Feature Pack 7 d’AEM 6.5.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.7 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html) à l’aide de votre Adobe ID. Accédez au **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack intitulé **AEM 6.5 Screens FP7**.

## Date de publication {#release-date}

La date de publication du pack de fonctionnalités 202103 d’AEM Screens est le 5 mars 2021.

### Nouveautés {#what-is-new}

* **Enregistrement automatique des lecteurs dans AEM Screens**

  L’enregistrement manuel en bloc de milliers de lecteurs est lourd, chronophage et coûteux. Pour simplifier ce processus, la fonctionnalité Enregistrement automatique des lecteurs vous permet de spécifier une clé prépartagée dans AEM. Cette clé peut être configurée dans un lecteur via un fichier de configuration ou une solution de gestion des appareils mobiles (MDM).

  Pour plus d’informations, consultez [Enregistrement automatique des lecteurs](/help/user-guide/auto-registration-players.md).


* **Approvisionneer en bloc un lecteur Android™ à l’aide d’Enterprise Mobility Management**

  Lors du déploiement en masse du lecteur Android™, il devient fastidieux d’enregistrer chaque lecteur manuellement avec AEM. Il est vivement recommandé d’utiliser une solution EMM (Enterprise Mobility Management, par exemple), comme `VMWare Airwatch`, `MobileIron`, ou `Samsung Knox` pour configurer et gérer votre déploiement à distance. Le lecteur Android™ AEM Screens prend en charge la norme EMM AppConfig pour permettre l’approvisionnement à distance.

  Pour plus d’informations, reportez-vous à [Approvisionnement en bloc d’un lecteur Android™ à l’aide d’une solution Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation).


### Correctifs {#bug-fixes}

* Performances améliorées pour le calcul de `clientlib` et de `asset hashes`.

* La migration SmartSync interrompt le lecteur si le cache n’a pas été invalidé.

* Les caches hors ligne n’étaient pas créés si l’affectation était paramétrée sur *OfflineConfig*.

* Les mises à jour du lecteur `Tizen` ne s’appliquaient pas, car la politique de référent « strict-origin-when-cross-origin » n’était pas prise en charge.

* Modification de la planification du canal affecté *Répéter* endommageait l’interface utilisateur.

* La mise à jour du contenu hors ligne échouait avec des exceptions de requête.

* Le délai entre les transitions au cours de l’interaction dans une expérience interactive est maintenant fixe.

* Une demande de mise à jour de configuration ayant échoué provoquait des écrans vierges.

### Lecteurs AEM Screens publiés

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.5 Feature Pack 7 :

* Chrome OS
* Windows
* Linux®

#### Téléchargements du lecteur AEM Screens

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, voir **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
