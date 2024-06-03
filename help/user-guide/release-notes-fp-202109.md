---
title: Notes de mise à jour du pack de fonctionnalités 202109
description: Découvrez le pack de fonctionnalités 202109 d’AEM Screens, publié le 23 septembre 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: ht
source-wordcount: '916'
ht-degree: 100%

---

# Notes de mise à jour du pack de fonctionnalités 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobe recommande d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). AEM Screens fournit une prise en charge de maintenance pour la plateforme AEM 6.3 Screens.

## Disponibilité {#availability}

Le Feature Pack 9 d’AEM 6.5 a été publié pour AEM Screens.

Vous pouvez télécharger le dernier pack de fonctionnalités pour AEM Screens 6.5.9 à partir du [Portail de distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/fr/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier pack de fonctionnalités appelé **AEM 6.5 Screens FP9**.

## Date de publication {#release-date}

La date de publication du Feature Pack 202109 d’AEM Screens est le 23 septembre 2021.

### Nouveautés {#what-is-new}

* **Prise en charge des miniatures de vidéos**

  Les miniatures de vidéos sont désormais prises en charge dans AEM Screens. Un auteur ou une autrice de contenu définit une miniature pour les vidéos afin que l’image soit utilisée comme espace réservé. L’auteur ou l’autrice teste également correctement la lecture et le ciblage du contenu, tandis que l’équipe appropriée finalise la vidéo réelle. L’image peut également être utilisée au cas où la lecture de la vidéo échouerait.
Pour plus d’informations, voir [Prise en charge des miniatures de vidéos](/help/user-guide/thumbnail-support.md).

* **Suivi de base de la lecture**

  AEM Screens prend désormais en charge le suivi de base de la lecture. Le lecteur signale désormais diverses mesures de lecture pour chaque ping (30 secondes par défaut). Sur la base des mesures, il détecte différents cas de figure (problèmes de lecture bloquée, d’écran vide, de planning, etc.). Cette fonctionnalité permet à l’équipe de surveiller à distance si un lecteur lit correctement du contenu et améliore la réactivité aux problèmes d’écrans vides ou de ruptures sur le terrain). Elle réduit également les risques d’afficher une expérience rompue à l’utilisateur final ou l’utilisatrice finale.
Pour plus d’informations, voir [Suivi de base de la lecture](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring).

* **Mises à jour du rapport d’affectation de contenu**

  Le rapport d’attribution de contenu est désormais optimisé et amélioré avec une expérience d’utilisation améliorée. Le rapport téléchargeable présente des entités améliorées liées au lecteur. Ces entités incluent des emplacements, des affichages et des appareils dans un seul onglet de feuille de calcul. Il inclut également les informations du fournisseur de contenu telles que les canaux et les ressources dans un autre onglet.
Pour plus d’informations, voir [Rapport d’affectation de contenu](/help/user-guide/content-assignment-report.md).

* **Rendus adaptatifs**

  Les rendus adaptatifs permettent à l’appareil de cliquer automatiquement sur le meilleur rendu pour un appareil en fonction des règles définies par le client ou la cliente.

  En tant que développeur AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques pour un appareil afin qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu. Voir [Rendus adaptatifs : présentation et configurations de l’architecture](/help/user-guide/adaptive-renditions.md) pour plus d’informations.

  En outre, en tant qu’auteur ou autrice de contenu AEM Screens, vous pouvez configurer vos ressources pour utiliser les rendus adaptatifs. Vous pouvez également migrer vos appareils pour que les grands réseaux utilisent cette fonctionnalité dans vos canaux AEM Screens. Voir [Utilisation des rendus adaptatifs dans AEM Screens](/help/user-guide/using-adaptive-renditions.md) pour plus d’informations.

* **Prise en charge des manifestes V3**

  Vous pouvez désormais configurer Dispatcher pour les manifestes version v3. Pour activer le manifeste v3, procédez comme suit :

   * Effacer tous les traitements de contenu hors ligne en attente à la fois dans l’instance création et l’instance de publication.

      * Accéder à CRXDE Lite dans l’instance de création et de publication.

      * Cliquer sur Outils > Requête.

      * Dans Requête, utiliser `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`.

      * Cette opération répertorie tous les tâches de contenu hors ligne en cours d’exécution ou en attente dans la file d’attente.

      * Attendez la fin du renvoi des tâches de contenu hors ligne par la requête.

   * Désactiver ContentSync dans `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

   * Activer SmartSync dans `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

   * Mettre à jour Dispatcher.

   * Mettez à jour le composant personnalisé.


   * Pour plus d’informations, consultez [Configuration de Dispatcher pour les manifestes v3](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3).
   * Si vous utilisez des composants personnalisés dans le cadre de versions Manifest v3, consultez la section [Modèle pour les gestionnaires personnalisés](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers).


### Correctifs {#bug-fixes}

**Côté lecteur**

* Résolution des erreurs de mise en cache des fichiers en remplaçant les ressources par des rendus.

* Les lecteurs n’exposent désormais que les rendus de ressources si le mappage de rendu est présent.

* Amélioration du ping pour la réauthentification si la réponse n’est pas un fichier JSON valide.

* Les noms et rôles des canaux numériques étaient laissés vides.

* Téléchargez des rendus optimisés au moyen de SmartSync.

* Transformation du mappage en liste de clés de rendu.

* Suppression de l’accès à `cmd.exe` et `reg.exe` dans le lecteur Windows.

* Un lecteur doit signaler son dernier événement de lecture réussi.

* Un lecteur doit signaler son statut de lecture.

* Le lecteur ne retélécharge pas les ressources lorsque le cache `ALL` est effacé.

* En tant qu’administrateur du lecteur, vous pouvez désormais choisir un nom de lecteur.

* La suppression de l’affectation de canal de l’affichage n’est pas répercutée sur le lecteur.

* Si le lecteur est rechargé pendant le téléchargement de la mise à jour du canal, il ignore la mise à jour.

* Le composant de page incorporé respecte désormais l’événement tactile.

* La mise en service à distance du lecteur Tizen est désormais prise en charge.

**Côté serveur**

* La vidéo cible ne s’affiche pas.
* Situation de compétition lors de la diffusion des données d’affichage dans les sous-séquences.

* L’aperçu de canal ne fonctionne pas pour les canaux contenant des vidéos.

* Le mode Aperçu s’affiche vide pour le canal d’écran partagé.

* Les miniatures vidéo s’affichent vides avec les rendus adaptatifs activés.

* Mettez automatiquement à jour le manifeste du canal si la page référencée est publiée.

* Les appareils supprimés ne bloquent désormais plus la file d’attente de réplication de Screens.

* Le manifeste ne contenait pas de contenu ciblé ni de pages incorporées Sites. Ce bug est maintenant résolu.

* Un nouveau composant d’image principal est désormais ajouté au manifeste du canal.

* Le téléchargement de rendus optimisés via SmartSync est désormais pris en charge.

* Lire le rendu optimisé pour toutes les ressources.

* Ajout de la prise en charge de plusieurs types de fournisseurs de contenu

* La stratégie de lecture de séquence incorporée était rompue et ce bug a maintenant été corrigé.

* Manifeste hors ligne utilisant le paramètre de requête `wcmmode` pour l’entrée HTML, ce qui rend la mise en cache impossible.

* Une séquence incorporée dynamique vide provoquait parfois un écran vide.

* Le lecteur signale maintenant son statut de lecture.

* La vidéo était lue dans `Tiny mode` et n’était pas lue comme vidéo plein écran sur l’appareil et le problème a été corrigé maintenant.

### Lecteurs AEM Screens publiés

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.5 Feature Pack 9 :

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Téléchargements du lecteur AEM Screens

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, reportez-vous à la section **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
