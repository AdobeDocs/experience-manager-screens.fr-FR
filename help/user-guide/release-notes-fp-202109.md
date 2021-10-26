---
title: Notes de mise à jour du Feature Pack 202109
description: Consultez cette page pour obtenir des informations sur AEM Screens Feature Pack 202109, publié le 23 septembre 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: 6d9dab9fd59289aafdb688682fea47589d3ec873
workflow-type: ht
source-wordcount: '859'
ht-degree: 100%

---

# Notes de mise à jour du Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Il est recommandé d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). Screens fournit une prise en charge de maintenance pour la plate-forme AEM 6.3 Screens.

## Disponibilité {#availability}

Le Feature Pack 9 d’AEM 6.5 a été publié pour AEM Screens.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.9 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack appelé **AEM 6.5 Screens FP9**.

## Date de publication {#release-date}

La date de publication du Feature Pack 202109 d’AEM Screens est le 23 septembre 2021.

### Nouveautés {#what-is-new}

* **Prise en charge des miniatures de vidéos**

   Les miniatures de vidéos sont désormais prises en charge dans AEM Screens. Un auteur de contenu peut définir une miniature de vidéos afin de pouvoir utiliser l’image en tant qu’espace réservé et de pouvoir tester correctement la lecture et le ciblage du contenu, alors que l’équipe concernée peut s’occuper de la finalisation de la vidéo elle-même. L’image peut également être utilisée au cas où la lecture de la vidéo échouerait.
Pour plus d’informations, voir [Prise en charge des miniatures de vidéos](/help/user-guide/thumbnail-support.md).

* **Suivi de base de la lecture**

   AEM Screens prend désormais en charge le suivi de base de la lecture. Le lecteur signale désormais diverses mesures de lecture pour chaque ping (30 secondes par défaut). Les mesures permettent de détecter différents cas de figure (lecture bloquée, écran vide, problème de time-code, etc.). Cette fonctionnalité permet à l’équipe concernée de surveiller à distance si un lecteur lit correctement du contenu, d’améliorer sa réactivité en cas d’écran vide ou d’interruption d’expérience et de réduire les risques d’offrir une expérience bancale à l’utilisateur final.
Pour plus d’informations, voir [Suivi de base de la lecture](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=fr#playback-monitoring).

* **Mises à jour du rapport d’affectation de contenu**

   Le rapport d’affectation de contenu est désormais optimisé et amélioré avec une expérience utilisateur améliorée. Le rapport téléchargeable présente les éléments améliorés liés au lecteur, tels que les emplacements, les affichages et les appareils, dans un seul onglet de feuille de calcul, ainsi que les informations sur les fournisseurs de contenu, telles que les canaux et les ressources dans un autre onglet.
Pour plus d’informations, voir [Rapport d’affectation de contenu](/help/user-guide/content-assignment-report.md).

* **Rendus adaptatifs**

   Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client.

   En tant que développeur AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques pour un appareil afin qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu. Voir [Rendus adaptatifs : présentation et configurations de l’architecture](/help/user-guide/adaptive-renditions.md) pour plus d’informations.

   En outre, en tant qu’auteur de contenu AEM Screens, vous pouvez configurer vos ressources pour utiliser les rendus adaptatifs et également migrer vos appareils pour les réseaux de grande taille afin de profiter de cette fonctionnalité, dans vos canaux AEM Screens. Voir [Utilisation des rendus adaptatifs dans AEM Screens](/help/user-guide/using-adaptive-renditions.md) pour plus d’informations.

* **Prise en charge des manifestes V3**

   Vous pouvez désormais configurer Dispatcher pour les manifestes version v3. Pour plus d’informations, consultez [Configuration de Dispatcher pour les manifestes version v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=fr#configuring-dispatcherv3).
De plus, si vous utilisez des composants personnalisés dans le cadre de manifestes v3, consultez [Modèle pour les gestionnaires personnalisés](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=fr#custom-handlers).


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

* Le lecteur ne retélécharge pas les ressources lorsque le cache `ALL` est effacé.

* En tant qu’administrateur du lecteur, vous pouvez désormais choisir un nom de lecteur.

* La suppression de l’affectation de canal de l’affichage n’est pas répercutée sur le lecteur.

* Si le lecteur est rechargé pendant le téléchargement de la mise à jour du canal, le lecteur ignore la mise à jour.

* Le composant de page incorporé respecte désormais l’événement tactile.

* La mise en service à distance du lecteur Tizen est désormais prise en charge.

**Côté serveur**

* La vidéo cible ne s’affiche pas
* Situation de compétition lors de la diffusion des données d’affichage dans les sous-séquences.

* L’aperçu de canal ne fonctionne pas pour les canaux contenant des vidéos.

* Le mode Aperçu s’affiche vide pour le canal d’écran partagé.

* Les miniatures vidéo s’affichent vides avec les rendus adaptatifs activés.

* Mettre automatiquement à jour le manifeste du canal si la page référencée est publiée.

* Les appareils supprimés ne bloquent désormais plus la file d’attente de réplication de Screens.

* Le manifeste ne contenait pas de contenu ciblé ni de pages incorporées Sites. Ce problème a été résolu.

* Les nouveaux composants d’image principaux sont désormais ajoutés au manifeste du canal.

* Le téléchargement de rendus optimisés via SmartSync est désormais pris en charge.

* Lire le rendu optimisé pour toutes les ressources.

* Ajout de la prise en charge de plusieurs types de fournisseurs de contenu

* La stratégie de lecture de séquence incorporée était rompue et ce problème a maintenant été corrigé.

* Manifeste hors ligne utilisant le paramètre de requête `wcmmode` pour l’entrée HTML, ce qui rend la mise en cache impossible.

* Une séquence incorporée dynamique vide provoquait parfois un écran vide.

* Le lecteur signale maintenant son état de lecture.

* La vidéo était lue dans `Tiny mode` et n’était pas lue comme vidéo plein écran sur l’appareil et le problème a été corrigé maintenant.

### Lecteurs AEM Screens publiés {#released-aem-screens-players}

Les lecteurs AEM Screens suivants sont publiés pour AEM 6.5 Feature Pack 9 :

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Téléchargements du lecteur AEM Screens   {#aem-screens-player-downloads}

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, reportez-vous à **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
