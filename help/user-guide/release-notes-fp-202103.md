---
title: Notes de mise à jour du Feature Pack 202103
description: En savoir plus sur AEM Screens Feature Pack 202103, publié le 5 mars 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 50%

---

# Notes de mise à jour du Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Il est recommandé d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). AEM Screens assure la prise en charge de la maintenance de la plateforme AEM 6.3 Screens.

## Disponibilité {#availability}

AEM Screens inclus dans le Feature Pack 7 d’AEM 6.5.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.7 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack appelé **AEM 6.5 Screens FP7**.

## Date de publication {#release-date}

La date de publication du Feature Pack 202103 d’AEM Screens est le 5 mars 2021.

### Nouveautés {#what-is-new}

* **Enregistrement automatique des lecteurs dans AEM Screens**

  L’enregistrement en masse de milliers de lecteurs manuellement est fastidieux et ajoute du temps et des coûts. Pour simplifier ce processus, la fonction Enregistrement automatique des lecteurs vous permet de spécifier une clé pré-partagée dans AEM. Cette clé peut être configurée dans un lecteur via un fichier de configuration ou une solution de gestion des périphériques mobiles (MDM).

  Voir [Enregistrement automatique des lecteurs](/help/user-guide/auto-registration-players.md) pour plus d’informations.


* **Approvisionnement en masse d’Android™ Player à l’aide de la gestion de la mobilité d’entreprise**

  Lors du déploiement en masse du lecteur Android™, il devient fastidieux d’enregistrer manuellement chaque lecteur avec AEM. Il est vivement recommandé d’utiliser une solution EMM (Enterprise Mobility Management, par exemple), comme `VMWare Airwatch`, `MobileIron`, ou `Samsung Knox` pour configurer et gérer votre déploiement à distance. Le lecteur AEM Screens Android™ prend en charge la configuration standard EMM AppConfig pour permettre la mise en service à distance.

  Voir [Approvisionnement en masse d’Android™ Player à l’aide de la gestion de la mobilité d’entreprise](/help/user-guide/implementing-android-player.md#implementation) pour plus d’informations.


### Correctifs {#bug-fixes}

* Performances améliorées pour le calcul de `clientlib` et de `asset hashes`.

* La migration SmartSync interrompait le lecteur si le cache n’était pas invalidé.

* Les caches hors ligne n’étaient pas créés si l’affectation était paramétrée sur *OfflineConfig*.

* Mises à jour de `Tizen` qui a échoué car la stratégie de référent strict-origin-when-cross-origin n’est pas prise en charge.

* La modification du champ de planning de canal affecté *Répète* affectait le fonctionnement de l’interface utilisateur.

* La mise à jour du contenu hors ligne échouait avec des exceptions de requête.

* Le délai entre les transitions au cours de l’interaction dans l’expérience interactive est maintenant corrigé.

* L’échec de la requête de mise à jour de la configuration causait l’apparition d’un écran vide.

### Lecteurs AEM Screens publiés

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.5 Feature Pack 7 :

* Chrome OS
* Windows
* Linux®

#### Téléchargements du lecteur AEM Screens

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, voir **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
