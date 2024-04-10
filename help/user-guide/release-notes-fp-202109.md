---
title: Notes de mise à jour du Feature Pack 202109
description: Découvrez le Feature Pack 202109 d’AEM Screens, publié le 23 septembre 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 59%

---

# Notes de mise à jour du Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Il est recommandé d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). AEM Screens assure la prise en charge de la maintenance de la plateforme AEM 6.3 Screens.

## Disponibilité {#availability}

Le Feature Pack 9 d’AEM 6.5 a été publié pour AEM Screens.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.9 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack appelé **AEM 6.5 Screens FP9**.

## Date de publication {#release-date}

La date de publication du Feature Pack 202109 d’AEM Screens est le 23 septembre 2021.

### Nouveautés {#what-is-new}

* **Prise en charge des miniatures de vidéos**

  Les miniatures de vidéos sont désormais prises en charge dans AEM Screens. Un auteur de contenu définit une miniature pour les vidéos afin que l’image soit utilisée comme espace réservé. Ils testent également correctement la lecture et le ciblage du contenu, tandis que la vidéo est finalisée par l’équipe appropriée. L’image peut également être utilisée si la lecture de la vidéo échoue.
Pour plus d’informations, voir [Prise en charge des miniatures de vidéos](/help/user-guide/thumbnail-support.md).

* **Suivi de base de la lecture**

  AEM Screens prend désormais en charge le suivi de base de la lecture. Le lecteur signale désormais diverses mesures de lecture pour chaque ping (30 secondes par défaut). Selon les mesures, il détecte divers cas de périphérie (expérience bloquée, écran vide, problème de planification, etc.). Cette fonctionnalité permet à l’équipe de surveiller à distance si un lecteur lit correctement du contenu et améliore la réactivité aux écrans vierges ou aux expériences rompues sur le terrain. Cela réduit également le risque d’afficher une expérience rompue à l’utilisateur final.
Pour plus d’informations, voir [Suivi de base de la lecture](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring).

* **Mises à jour du rapport d’affectation de contenu**

  Le rapport d’affectation de contenu est désormais optimisé et amélioré avec une expérience utilisateur améliorée. Le rapport téléchargeable présente les entités améliorées liées au lecteur, telles que les emplacements, les affichages et les appareils, dans un seul onglet de feuille de calcul, ainsi que les informations sur les fournisseurs de contenu, telles que les canaux et les ressources dans un autre onglet.
Pour plus d’informations, voir [Rapport d’affectation de contenu](/help/user-guide/content-assignment-report.md).

* **Rendus adaptatifs**

  Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client.

  En tant que développeur AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques pour un appareil afin qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu. Voir [Rendus adaptatifs : présentation et configurations de l’architecture](/help/user-guide/adaptive-renditions.md) pour plus d’informations.

  En outre, en tant qu’auteur de contenu AEM Screens, vous pouvez configurer vos ressources pour utiliser les rendus adaptatifs. Vous pouvez également migrer vos appareils pour que les grands réseaux utilisent cette fonctionnalité dans vos canaux AEM Screens. Voir [Utilisation des rendus adaptatifs dans AEM Screens](/help/user-guide/using-adaptive-renditions.md) pour plus d’informations.

* **Prise en charge des manifestes V3**

  Vous pouvez désormais configurer Dispatcher pour les manifestes version v3. Pour activer le manifeste v3, vous devez :

   * Effacez toutes les tâches de contenu hors ligne en attente dans l’auteur et dans la publication.

      * Accédez à CRXDE Lite dans les instances de création et de publication.

      * Cliquez sur Outils > Requête.

      * Dans la requête, utilisez `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`.

      * Cette section répertorie toutes les tâches de contenu hors ligne en cours d’exécution ou en attente dans la file d’attente.

      * Attendez qu’il n’y ait plus de tâches de contenu hors ligne renvoyées par la requête.

   * Désactiver ContentSync dans `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

   * Activer SmartSync dans `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

   * Mettez à jour Dispatcher.

   * Mettre à jour le composant personnalisé.


   * Pour plus d’informations, consultez [Configuration de Dispatcher pour les manifestes v3](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3).
   * Si vous utilisez des composants personnalisés dans le cadre de versions Manifest v3, consultez la section [Modèle pour les gestionnaires personnalisés](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers).


### Correctifs {#bug-fixes}

**Côté lecteur**

* Résolution des erreurs de mise en cache des fichiers en remplaçant les ressources par des rendus.

* Les lecteurs n’exposent désormais que les rendus de ressources si le mappage de rendu est présent.

* Amélioration du ping pour la réauthentification si la réponse n’est pas un fichier JSON valide.

* Les noms et rôles des canaux numériques étaient laissés vide.

* Téléchargez des rendus optimisés via SmartSync.

* Le mappage a été transformé en liste de clés de rendu.

* Suppression de l’accès à `cmd.exe` et `reg.exe` dans le lecteur Windows.

* Un lecteur doit signaler son dernier événement de lecture réussi.

* Un lecteur doit signaler son état de lecture.

* Le lecteur ne retélécharge pas les ressources lorsque `ALL` Le cache est effacé.

* En tant qu’administrateur du lecteur, vous pouvez désormais choisir un nom de lecteur.

* La suppression de l’affectation de canal de l’affichage n’est pas répercutée sur le lecteur.

* Si le lecteur est rechargé pendant le téléchargement de la mise à jour du canal, le lecteur ignore la mise à jour.

* Le composant de page incorporé respecte désormais l’événement tactile.

* La mise en service à distance du lecteur Tizen est désormais prise en charge.

**Côté serveur**

* La vidéo cible ne s’affiche pas.
* Conditions de race lors de la diffusion des données d&#39;affichage vers les séquences.

* L’aperçu de canal ne fonctionne pas pour les canaux contenant des vidéos.

* Le mode Aperçu s’affiche vide pour le canal d’écran partagé.

* Les miniatures vidéo s’affichent vides avec les rendus adaptatifs activés.

* Mettre automatiquement à jour le manifeste du canal si la page référencée est publiée.

* Les périphériques supprimés ne bloquent désormais pas la file d’attente de réplication Screens.

* Le manifeste ne contenait pas de contenu ciblé ni de pages incorporées Sites. Ce problème a été résolu.

* Un nouveau composant d’image principal est maintenant ajouté au manifeste du canal.

* Le téléchargement de rendus optimisés via SmartSync est désormais pris en charge.

* Lire le rendu optimisé pour toutes les ressources.

* Ajout de la prise en charge de plusieurs types de fournisseurs de contenu

* La stratégie de lecture de séquence incorporée était rompue et ce problème a maintenant été corrigé.

* Manifeste hors ligne utilisant le paramètre de requête `wcmmode` pour l’entrée HTML, ce qui rend la mise en cache impossible.

* Une séquence incorporée dynamique vide provoquait parfois un écran vide.

* Le lecteur signale désormais son état de lecture.

* La vidéo était lue dans `Tiny mode` et n’était pas lue comme vidéo plein écran sur l’appareil et le problème a été corrigé maintenant.

### Lecteurs AEM Screens publiés

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.5 Feature Pack 9 :

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Téléchargements du lecteur AEM Screens

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, voir **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
