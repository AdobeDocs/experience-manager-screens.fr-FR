---
title: Notes de mise à jour du Feature Pack 202103
description: Consultez cette page pour obtenir des informations sur AEM Screens Feature Pack 202103, publié le 5 mars 2021.
feature: Feature Pack
role: Developer
level: Intermediate
translation-type: ht
source-git-commit: aa1338fad19893e56ead4bb466e4f32a90116b65
workflow-type: ht
source-wordcount: '398'
ht-degree: 100%

---


# Notes de mise à jour du Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Il est recommandé d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). Screens fournit une prise en charge de maintenance pour la plate-forme AEM 6.3 Screens.

## Disponibilité {#availability}

AEM Screens inclus dans le Feature Pack 7 d’AEM 6.5.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.7 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack appelé **AEM 6.5 Screens FP7**.

## Date de publication {#release-date}

La date de publication du Feature Pack 202103 d’AEM Screens est le 5 mars 2021.

### Nouveautés {#what-is-new}

* **Enregistrement automatique des lecteurs dans AEM Screens**

   L’enregistrement manuel en bloc de milliers de lecteurs est très lourd, chronophage et coûteux. Pour simplifier ce processus, la fonction Enregistrement automatique des lecteurs vous permet de spécifier une clé prépartagée dans AEM qui peut être configurée dans un lecteur soit par le biais d’un fichier de configuration, soit par une solution MDM (Mobile Device Management).

   Pour plus d’informations, consultez [Enregistrement automatique des lecteurs](/help/user-guide/auto-registration-players.md).


* **Approvisionnement en bloc d’un lecteur Android à l’aide d’Enterprise Mobility Management**

   Lors du déploiement en bloc d’un lecteur Android, il devient fastidieux d’enregistrer manuellement chaque lecteur dans AEM. Nous vous recommandons vivement d’utiliser une solution EMM (Enterprise Mobility Management) telle que VMWare Airwatch, MobileIron ou Samsung Knox pour configurer et gérer votre déploiement à distance. Le lecteur Android AEM Screens prend en charge la norme EMM AppConfig pour permettre l’approvisionnement à distance.

   Pour plus d’informations, reportez-vous à [Approvisionnement en bloc d’un lecteur Android à l’aide d’une solution Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation).


### Correctifs {#bug-fixes}

* Performances améliorées pour le calcul de `clientlib` et de `asset hashes`.

* La migration SmartSync interrompait le lecteur si le cache n’était pas invalidé.

* Les caches hors ligne n’étaient pas créés si l’affectation était paramétrée sur *OfflineConfig*.

* Les mises à jour du lecteur Tizen ne s’appliquaient pas, car la politique de référent « strict-origin-when-cross-origin » n’était pas prise en charge.

* La modification du champ de planning de canal affecté *Répète* affectait le fonctionnement de l’interface utilisateur.

* La mise à jour du contenu hors ligne échouait avec des exceptions de requête.

* Le délai entre les transitions au cours de l’interaction dans l’expérience interactive est maintenant corrigé.

* L’échec de la requête de mise à jour de la configuration causait l’apparition d’un écran vide.

### Lecteurs AEM Screens publiés {#released-aem-screens-players}

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.5 Feature Pack 7 :

* Chrome OS
* Windows
* Linux

#### Téléchargements du lecteur AEM Screens {#aem-screens-player-downloads}

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, reportez-vous à la section **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
