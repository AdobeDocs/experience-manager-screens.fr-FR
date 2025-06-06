---
cloud: Experience Cloud
product: experience manager
audience: end-user
user-guide-title: Aide d’Adobe Experience Manager Screens
breadcrumb-title: Guide d’AEM Screens
user-guide-description: Apprenez à utiliser une solution de signalétique numérique qui vous permet de publier des expériences et des interactions digitales dynamiques et interactives.
feature-set: Experience Manager Screens
feature: Content
role: User
source-git-commit: d8392b015c65e6bba35ba4c923d4f663e1121e0c
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 100%

---


# Guide de l’utilisateur AEM Screens {#user-guide}

+ [Présentation de Screens](aem-screens-introduction.md)
+ Aperçu et guide de démarrage rapide {#overview}
   + [Guide de démarrage rapide](kickstart-for-aem-screens.md)
   + [Guide des bonnes pratiques pour Screens](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/using/about-guide)
   + [Termes clés](screens-glossary.md)
   + [Terminologie et concepts de Screens](screens-concepts-feature-video-understand.md)
+ Notions de base sur les réseaux de signalétique numérique {#digital-signage-network}
   + [Partie 1 : rôles du projet et responsabilités](project-roles-responsibilities.md)
   + [Partie 2 : observations dans le cadre de la définition de la portée du projet](project-considerations.md)
   + [Partie 3 : tests, preuves de concept, pilotes et déploiements](testing-pocs-pilots-rollouts.md)
   + [Partie 4 : gestion et déploiement de projets](project-management-and-deployment.md)
   + [Partie 5 : facteurs liés à l’assistance](support-considerations.md)
+ Configuration et administration {#administering}
   + [Configurer le serveur Screens](configuring-screens-introduction.md)
   + [Paramétrage des configurations Dispatcher](dispatcher-configurations-aem-screens.md)
   + [Installation du lecteur Screens](installing-screens-player.md)
   + [Connexion à un lecteur Screens](working-with-screens-player.md)
   + [Enregistrement d’appareils](device-registration.md)
   + [Configuration des listes de contrôle d’accès](setting-up-acls.md)
   + [Liste de contrôle de sécurité d’AEM Screens](security-checklist.md)
   + [Transition de ContentSync à SmartSync](smartsync.md)
   + [Nouvel importateur de projet à partir d’un fichier](project-importer.md)
   + [Répliquer des déclencheurs de données sur les serveurs de publication](replicating-data-triggers.md)
   + [Configurer les agents de réplication sur Screens](configure-screens-replication.md)
   + Considérations spécifiques au client {#installing-client}
      + [Lecteur Chrome OS](implementing-chrome-os-player.md)
      + [Utilisation d’un lecteur Chrome comme extension à des fins de dépannage](using-chrome-player-as-an-extension.md)
      + [Android](implementing-android-player.md)
      + [Lecteur Windows](implementing-windows-player.md)
      + [Lecteur Tizen](tizen-player.md)
      + [Lecteur cloud](implementing-cloud-player.md)
      + [Enregistrement automatique des lecteurs](auto-registration-players.md)
      + [Utiliser la commande à distance](implementing-remote-control.md)
   + Instances d’auteur et de publication {#author-publish}
      + [Présentation de l’architecture des instances d’auteur et de publication](author-publish-architecture-overview.md)
      + [Configuration d’instances d’auteur et de publication](author-and-publish.md)
   + Intégration d’Adobe Analytics avec AEM Screens {#analytics-integration}
      + [Intégration d’Adobe Analytics](adobe-analytics-integration-aem-screens.md)
      + [Configuration d’Adobe Analytics avec AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ Exemples de cas de création et d’utilisation {#authoring}
   + Configurer un projet Screens {#setting-up-projects}
      + [Créer et gérer des projets](creating-a-screens-project.md)
      + [Création et gestion des canaux](managing-channels.md)
      + [Création et gestion des affichages](managing-displays.md)
      + [Création et gestion des emplacements](managing-locations.md)
      + [Créer et gérer les plannings](managing-schedules.md)
      + [Gérer les appareils](managing-devices.md)
      + Attribution de canaux {#assigning-channels}
         + [Attribution de canaux](channel-assignment-latest-fp.md)
         + [Attribution de canaux : anciennes versions de Feature Packs AEM Screens](channel-assignment.md)
   + Utilisation de fonctionnalités de base du produit {#product-features}
      + [Superposition de texte](text-overlay.md)
      + [Mise à jour hors ligne en bloc](bulk-offline-update.md)
      + [Service de notifications AEM Screens](screens-notifications-service.md)
      + [Utiliser des fragments d’expérience](experience-fragments-in-screens.md)
      + [Activation au niveau des ressources](asset-level-scheduling.md)
      + [Activation au niveau des canaux](channel-level-activation.md)
      + [Créer et gérer une Live Copy](managing-livecopy.md)
      + [Créer un workflow de remplissage vidéo](creating-a-video-padding-workflow.md)
      + [Ajout de composants à un canal](adding-components-to-a-channel.md)
      + [Séquences incorporées](embedded-sequences.md)
      + [Disposition multizone](multi-zone-layout-aem-screens.md)
      + [Rendus vidéo](generating-renditions.md)
      + [Séquence incorporée dynamique](dynamic-embedded-sequences.md)
      + [Durée de lecture d’images en bloc au niveau du canal](channel-level-image-playback.md)
      + [Synchronisation des commandes](using-command-sync.md)
      + [Création avec des déclencheurs de données](authoring-data-triggers.md)
      + [Utiliser les balises](tagging.md)
      + [Reconnaissance vocale](voice-recognition.md)
      + [Rapport d’attribution de contenu](content-assignment-report.md)
      + [Prise en charge des miniatures pour les vidéos](thumbnail-support.md)
      + [Utilisation des rendus adaptatifs dans AEM Screens](using-adaptive-renditions.md)
   + Gestion de mises à jour de contenus {#content-updates}
      + [Mise à jour du contenu à la demande](on-demand-content.md)
      + [Mise à jour de contenus en tant que service](content-update-as-a-service.md)
      + [Mise à jour du contenu à l’aide d’un lancement Screens](launches.md)
   + Exemples de cas d’utilisation {#use-case-examples}
      + [Canaux d’urgence](emergency-channel.md)
      + [Activation de la température pour une agence de voyages](local-temperature-activation.md)
      + [Activation de la réservation d’hébergements](hospitality-reservation-activation.md)
      + [Activation ciblée du stock de vente au détail](retail-inventory-activation.md)
      + [Application de transitions](applying-transitions.md)
      + [Transitions Multizone vers Zone unique](multizone-to-singlezone.md)
      + [Canal de prise de contrôle à usage unique](single-use-takeover-channel.md)
      + [Canal de prise de contrôle perpétuelle](perpetual-takeover-channel.md)
+ Ressources du développeur et ressources d’API {#developing}
   + [API REST](rest-api.md)
   + [Développer un composant personnalisé pour AEM Screens](developing-custom-component-tutorial-develop.md)
   + [Canaux hors ligne](offline-channels.md)
   + [Extension d’un composant AEM Screens](extending-component-tutorial-develop.md)
   + [Création de composants](creating-components.md)
   + [Incorporation d’une application REACT via la fonction d’éditeur d’application monopage (SPA) et intégration avec AEM Screens Analytics](embedding-react-app.md)
   + [Configuration de ContextHub dans AEM Screens](configuring-context-hub.md)
   + [Création de modèles personnalisés pour des dispositions multizones](creating-custom-templates-multizone-layouts.md)
   + [Application d’une valorisation de marque et de styles personnalisés aux superpositions de texte](custom-branding-text-overlays.md)
   + [Rendus adaptatifs : présentation et configurations de l’architecture](/help/user-guide/adaptive-renditions.md)
+ Dépannage et questions fréquentes {#troubleshooting}
   + [Questions fréquentes sur AEM Screens](aem-screens-faqs.md)
   + [Résolution de problèmes dans le Centre de contrôle des périphériques](monitoring-screens.md)
   + [Configuration de la lecture vidéo](troubleshoot-videos.md)
+ Notes de mise à jour {#release-notes}
   + [Notes de mise à jour du pack de fonctionnalités 20250327](release-notes-fp-20250327.md)
   + [Notes de mise à jour du pack de fonctionnalités 20250224](release-notes-fp-20250224.md)
   + [Notes de mise à jour du pack de fonctionnalités 20240715](release-notes-fp-20240715.md)
   + [Notes de mise à jour du pack de fonctionnalités 202401](release-notes-fp-20250215.md)
   + [Notes de mise à jour du pack de fonctionnalités 202401](release-notes-fp-202401.md)
   + [Notes de mise à jour du pack de fonctionnalités 20240116](release-notes-fp-20240116.md)
   + [Notes de mise à jour du pack de fonctionnalités 20240215](release-notes-fp-20240215.md)
   + [Notes de mise à jour du pack de fonctionnalités 202204](release-notes-fp-202204.md)
   + [Notes de mise à jour du Feature Pack 202203](release-notes-fp-202203.md)
   + [Notes de mise à jour du pack de fonctionnalités 202112](release-notes-fp-202112.md)
   + [Notes de mise à jour du Feature Pack 202109](release-notes-fp-202109.md)
   + [Notes de mise à jour du pack de fonctionnalités 202105](release-notes-fp-202105.md)
   + [Notes de mise à jour du pack de fonctionnalités 202103](release-notes-fp-202103.md)
   + [Notes de mise à jour du pack de fonctionnalités 202011](release-notes-fp-202011.md)
   + [Notes de mise à jour du pack de fonctionnalités 202008](release-notes-fp-202008.md)
   + [Notes de mise à jour du pack de fonctionnalités 202004](release-notes-fp-202004.md)
   + [Notes de mise à jour du pack de fonctionnalités 202001](release-notes-fp-202001.md)
   + [Notes de mise à jour du pack de fonctionnalités 201909](release-notes-fp-201909.md)
   + [Notes de mise à jour du pack de fonctionnalités 201907](release-notes-fp-201907.md)
   + [Notes de mise à jour du pack de fonctionnalités 201905](screens-release-notes-fp-201905.md)
   + [Notes de mise à jour du pack de fonctionnalités 201812](release-notes-fp-201812.md)
   + [Notes de mise à jour du pack de fonctionnalités 201809](screens-release-notes.md)
