---
title: Notes de mise à jour du Feature Pack 202109
description: Consultez cette page pour obtenir des informations sur AEM Screens Feature Pack 202105, publié le 23 septembre 2021.
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: 375024848ed736104add828251ea494406a4f7ba
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 16%

---

# Notes de mise à jour du Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>Il est recommandé d’effectuer la mise à niveau vers la dernière version d’Adobe Experience Manager (AEM). Screens fournit une prise en charge de maintenance pour la plate-forme AEM 6.3 Screens.

## Disponibilité {#availability}

Le Feature Pack 9 d’AEM 6.5 a été publié pour AEM Screens.

Vous pouvez télécharger le dernier Feature Pack pour AEM Screens 6.5.9 à partir du [Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en utilisant votre Adobe ID. Accédez à l’onglet **Adobe Experience Manager** et recherchez **Screens** pour obtenir le dernier Feature Pack appelé **AEM 6.5 Screens FP9**.

## Date de publication {#release-date}

La date de publication du Feature Pack 202109 d’AEM Screens est le 23 septembre 2021.

### Nouveautés {#what-is-new}

* **Prise en charge des miniatures pour les vidéos**

   La prise en charge des miniatures pour les vidéos dans est désormais prise en charge dans AEM Screens. Un auteur de contenu peut définir une miniature pour les vidéos afin que l’image puisse être utilisée comme espace réservé et tester correctement la lecture et le ciblage du contenu, pendant que la vidéo réelle est en cours de finalisation par l’équipe appropriée. L’image peut également être utilisée, au cas où la lecture de la vidéo échouerait.
Pour plus d’informations, voir Prise en charge des miniatures pour les vidéos .

* **Surveillance de lecture de base**

   AEM Screens prend désormais en charge la surveillance de lecture de base. Le lecteur signale désormais diverses mesures de lecture pour chaque ping (30 secondes par défaut). En fonction des mesures, il permet de détecter différents cas de périphérie (expérience bloquée, écran vide, problème de planification, etc.). Cette fonctionnalité permet à l’équipe de surveiller à distance si un lecteur lit correctement du contenu, améliore la réactivité aux écrans vierges ou aux expériences rompues sur le champ et réduit le risque d’afficher une expérience rompue à l’utilisateur final.
Pour plus d’informations, voir Surveillance de lecture de base .

* **Mises à jour du rapport d’affectation de contenu**

   Le rapport d’affectation de contenu est désormais optimisé et amélioré avec une expérience utilisateur améliorée. Le rapport téléchargeable présente les entités améliorées liées au lecteur, telles que les emplacements, les affichages et les appareils, dans un seul onglet de feuille de calcul, ainsi que les informations sur les fournisseurs de contenu, telles que les canaux et les ressources dans un autre onglet.

* **Rendus adaptatifs**

   Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client.

   En tant que développeur AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques à l’appareil pour qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu. Voir Rendus adaptatifs : Présentation et configurations de l’architecture pour en savoir plus.

   En outre, en tant qu’auteur de contenu AEM Screens, vous pouvez désormais utiliser des rendus adaptatifs dans votre projet AEM Screens et appliquer également une stratégie de migration pour les grands réseaux. Pour plus d’informations, voir Utilisation des rendus adaptatifs .

* **Prise en charge des manifeste V3**

   Vous pouvez désormais configurer Dispatcher pour Manifest version v3. Pour plus d’informations, voir [Configuration de Dispatcher pour la version de manifeste v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) .
De plus, si vous utilisez des composants personnalisés dans le cadre de manifestes v3, voir [Modèle pour les gestionnaires personnalisés](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).


### Correctifs {#bug-fixes}

**Côté lecteur**

* Résolution des erreurs de mise en cache des fichiers en remplaçant les ressources par des rendus.

* Les lecteurs n’exposent désormais que les rendus de ressources, si le mappage de rendu est présent.

* Vous pouvez désormais configurer des alertes de slack en fonction des journaux de scunk.

* Amélioration du ping pour la réauthentification si la réponse n’est pas un fichier JSON valide.

* Les noms et rôles des canaux numériques étaient laissés vide.

* Téléchargez des rendus optimisés via SmartSync.

* Le mappage a été transformé en liste de clés de rendu.

* Suppression de l’accès à `cmd.exe` et `reg.exe` dans le lecteur Windows.

* Un lecteur doit signaler son dernier événement de lecture réussi.

* Un lecteur doit signaler son état de lecture.

* Le lecteur ne retélécharge pas les ressources lorsque `ALL` le cache est effacé.

* En tant qu’administrateur du lecteur, vous pouvez désormais choisir un nom de lecteur.

* La suppression de l’affectation de canal de l’affichage n’est pas répercutée sur le lecteur.

* Si le lecteur est rechargé pendant le téléchargement de la mise à jour du canal, le lecteur ignore la mise à jour.

* Le composant de page incorporé respecte désormais l’événement tactile.

* La mise en service à distance du lecteur Tizen est désormais prise en charge.

**Côté serveur**

* La vidéo cible ne s’affiche pas
* Condition de race lors de la diffusion des données d&#39;affichage aux séquences.

* L’aperçu de canal ne fonctionne pas pour les canaux contenant des vidéos.

* Le mode Aperçu s’affiche vide pour le canal d’écran partagé.

* Les miniatures vidéo s’affichent vides avec les rendus adaptatifs activés.

* Mettre automatiquement à jour le manifeste du canal si la page référencée est publiée.

* Les périphériques supprimés ne bloquent désormais pas la file d’attente de réplication Screens.

* Le manifeste ne contenait pas de contenu ciblé ni de pages incorporées Sites. Ce problème a été corrigé.

* De nouveaux composants d’image principaux sont désormais ajoutés au manifeste du canal.

* Le téléchargement de rendus optimisés via SmartSync est désormais pris en charge.

* Lire le rendu optimisé pour toutes les ressources.

* Ajout de la prise en charge de plusieurs types de fournisseurs de contenu

* La stratégie de lecture de séquence incorporée a été rompue et cela a maintenant été corrigé.

* Manifeste hors ligne utilisant le paramètre de requête `wcmmode` pour l’entrée html, ce qui rend la mise en cache impossible.

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

Pour télécharger le dernier lecteur AEM Screens et en savoir plus sur les correctifs, reportez-vous à la section **[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/index.html)**.
