---
title: Notes de mise à jour du Feature Pack 202103
description: Cette page présente les Notes de mise à jour de Feature Pack 202103.
translation-type: tm+mt
source-git-commit: 3701c6f72ceadb5b61cd608503a95af11d631c49
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 36%

---


# Notes de mise à jour du Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>Il est recommandé d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). Screens fournit une prise en charge de maintenance pour la plate-forme AEM 6.3 Screens.

## Disponibilité {#availability}

AEM Screens inclus dans le Feature Pack 7 d’AEM 6.5.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.7 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack appelé **AEM 6.5 Screens FP7**.

## Date de publication {#release-date}

La date de publication pour AEM Screens Feature Pack 202103 est le 05 mars 2021.

### Nouveautés {#what-is-new}

* **Enregistrement automatique des joueurs AEM Screens**

   L&#39;enregistrement en masse de milliers de joueurs manuellement est très lourd et ajoute du temps et des coûts. Pour simplifier ce processus, la fonction Enregistrement automatique des lecteurs vous permet de spécifier une clé pré-partagée dans AEM qui peut être configurée dans un lecteur soit par le biais d’un fichier de configuration, soit par une solution MDM (Mobile Device Management).

   Pour plus d&#39;informations, consultez [Enregistrement automatique des joueurs](/help/user-guide/auto-registration-players.md).


* **Approvisionnement en bloc du lecteur Android à l&#39;aide de la gestion de la mobilité d&#39;entreprise**

   Lors du déploiement en bloc du lecteur Android, il devient fastidieux d’enregistrer manuellement chaque lecteur avec AEM. Il est vivement recommandé d&#39;utiliser une solution EMM (Enterprise Mobility Management) telle que VMWare Airwatch, MobileIron ou Samsung Knox pour configurer et gérer votre déploiement à distance. Le lecteur Android AEM Screens prend en charge la norme EMM AppConfig pour permettre l’approvisionnement à distance.

   Pour plus d&#39;informations, reportez-vous à la section [Mise en service en bloc d&#39;Android Player à l&#39;aide de Enterprise Mobility Management](/help/user-guide/using-emm-bulkprovision-android-player.md).


### Correctifs {#bug-fixes}

* Performances améliorées pour l&#39;informatique `clientlib` et `asset hashes`.

* La migration SmartSync interromprait le lecteur si le cache n&#39;était pas invalidé.

* Les caches hors ligne n&#39;ont pas été créés si l&#39;affectation avait *OfflineConfig*.

* Mises à jour du lecteur Tizen rompues, car l’origine stricte de la stratégie de parrain lors d’origines croisées n’est pas prise en charge.

* La modification du calendrier de canal affecté *Répète* champ rompait l’interface utilisateur.

* La mise à jour du contenu hors ligne échouait avec des exceptions de requête.

* Le décalage entre les transitions au cours de l’interaction dans l’expérience interactive est maintenant corrigé.

* Échec de la demande de mise à jour de configuration provoquait l&#39;affichage de l&#39;écran vide.

### Lecteurs AEM Screens publiés {#released-aem-screens-players}

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.5 Feature Pack 7 :

* Chrome OS
* Windows
* Tizen
* Linux

#### Téléchargements du lecteur AEM Screens {#aem-screens-player-downloads}

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, reportez-vous à la section **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
