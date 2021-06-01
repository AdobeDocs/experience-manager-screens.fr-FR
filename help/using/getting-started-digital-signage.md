---
title: Principes de base de la signalétique digitale pour [!UICONTROL AEM Screens]
seo-title: Principes de base de la signalétique digitale pour [!UICONTROL AEM Screens]
description: Ce guide décrit les principes de base d’un projet de signalétique digitale
seo-description: Ce guide décrit les principes de base d’un projet de signalétique digitale
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 100%

---


# Principes de base d’un projet de signalétique digitale{#basics-digital-signage}

Avant de passer aux meilleures pratiques de mise en œuvre d’AEM Screens, il convient de considérer le projet comme un projet de signalétique digitale, plutôt que comme un projet de développement logiciel traditionnel.

Cette section fournit des recommandations sur les éléments qui sont essentiels avant la mise en œuvre d’un projet AEM Screens.

## Éléments clés d’un projet de signalétique digitale {#key-elements}

Les *éléments clés* d’un projet de signalétique digitale sont les suivants  :

![](/help/assets/Elements-Revised.png)

La définition des éléments clés est une étape essentielle avant la mise en œuvre d’un projet de signalétique digitale :

1. **Matériel**

   Le matériel définit les composants matériels idéaux pour la mise en œuvre de votre projet de signalétique digitale :
   * Le périphérique dispose-t-il d’un espace de stockage suffisant pour exécuter toutes les variantes des expériences hors ligne ?
   * Avons-nous autorisé le type et la longueur de câble vidéo ? Le périphérique prend-il en charge les résolutions souhaitées (HD, Full HD, 4K, etc.) et les codecs vidéo que je prévois de déployer (h.264, h.265, etc.) ?
   * Utilisation de fils de cuivre physiques
   * Taille des écrans
   * Nombre d’écrans
      * Orientation
      * Rapport d’aspect
      * Préférence de résolution

1. **Connectivité**

   La connectivité met l’accent sur les questions suivantes :
   * Réseau (cellulaire ou Wi-Fi) ou autonome ?
      * Devons-nous autoriser les mises à jour de contenu USB ?
      * Devons-nous autoriser la collecte de données d’utilisation ?

1. **Installation**

   L’installation comprend les éléments suivants :
   * Modes d’affichage : paysage ou portrait
   * Comment l’écran sera-t-il monté ?
      * Portrait ou paysage
      * Boîtier complet
      * Plaque de recouvrement
   * Support de l’appareil
   * Personnel : responsable de l’installation du matériel et de sa connexion au réseau
   * À quelle distance la source d’alimentation se trouve-t-elle de l’appareil ?
   * À quelle distance le panneau physique se trouve-t-il du périphérique proprement dit ?

1. **Contenu**

   Questions relatives au contenu :
   * Zone unique ou plusieurs zones ?
      * Quel est le nombre de ressources multimédias affichées simultanément à l’écran ?
      * Combien de pages y a-t-il pour les applications interactives ?
      * Définition de la boucle d’interface utilisateur
      * S’agit-il d’un contenu piloté par les données ?
   * Gestion de version

1. **Interactivité**

   Questions relatives à l’interactivité :
   * Type d’écran tactile préféré (résistif, capacitif, multipoint) ?
      * Pression de boutons
      * Gestes
   * Déclenchement des données (E/S) ?
      * Envoi/réception de commandes série (fermeture de contact, PLC, etc.)
      * Les données entrantes s’affichent à l’écran (RSS) ou déclenchent du contenu
      * RFID/NFC/Bluetooth/iBeacon
      * Services externes (météo, trafic)

1. **Environnement**

   L’environnement met l’accent sur les points suivants :
   * Emplacement de l’affichage ?
      * Intérieur ou extérieur
      * Hors d’atteinte ou directement accessible
   * Y a-t-il des exigences particulières en matière de température ?
   * Le matériel est-il à l’épreuve du vandalisme ?
   * Fort éclairage ambiant ? Contrastes élevés ?

1. **Maintenance**

   La maintenance met l’accent sur les points suivants :

   * L’utilisation de guides d’installation/utilisation détaillés est-elle requise ?
   * Le périphérique est-il configuré (programmé) avant l’expédition ?
   * Devons-nous capturer chaque numéro de série à des fins de suivi ?
   * Existe-t-il des exigences d’alimentation de secours (alimentation continue) ?
   * Comment les mises à jour du système sont-elles déployées ? Comment les périphériques sont-ils contrôlés à distance ? Une solution MDM est-elle requise ?
