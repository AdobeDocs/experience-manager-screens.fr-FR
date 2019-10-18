---
title: Principes de base de Digital Signing pour les écrans [!UICONTROL AEM]
seo-title: Principes de base de Digital Signing pour les écrans [!UICONTROL AEM]
description: Le guide décrit les bases d’un projet de signalisation numérique
seo-description: Le guide décrit les bases d’un projet de signalisation numérique
translation-type: tm+mt
source-git-commit: 30c724ea897fd2da5300bb5cad285d460af5de40

---


# Principes de base d’un projet de signature numérique {#basics-digital-signage}

Avant de vous plonger dans les meilleures pratiques d’implémentation d’AEM Screens, il est important de considérer le projet comme un projet de signalisation numérique, plutôt que comme un développement logiciel traditionnel.

Cette section fournit des recommandations sur les principaux éléments essentiels avant la mise en oeuvre d’un projet AEM Screens.

## Éléments clés dans Digital Signing {#key-elements}

Les éléments ** clés d’un projet de signalisation numérique sont les suivants :

![](/help/assets/Elements-Revised.png)

La définition des éléments clés est essentielle avant la mise en oeuvre d’un projet de signalisation numérique :

1. **Matériel**

   Le matériel définit les composants matériels idéaux pour la mise en oeuvre de votre projet de signalisation numérique :
   * Le périphérique dispose-t-il d’un espace de stockage suffisant pour exécuter toutes les variantes des expériences hors ligne ?
   * Avons-nous autorisé le type et la longueur des câbles vidéo ? Le périphérique prend-il en charge les deux résolutions souhaitées (HD, FullHD, 4K, etc.) ? et les codecs vidéo que je prévois de déployer (h.264, h.265, etc.)
   * Utilisation de fils de cuivre physiques
   * Taille des écrans
   * Nombre d’écrans
      * orientation
      * format
      * préférence de résolution

1. **Connectivité**

   La connectivité met l'accent sur les questions suivantes :
   * En réseau (cellulaire ou wi-fi) ou autonome ?
      * devons-nous autoriser les mises à jour de contenu USB ?
      * devons -nous autoriser la collecte des données d' utilisation?

1. **Installation**

   L'installation comprend :
   * Affichages : paysage ou portrait
   * Comment l'écran sera-t-il monté ?
      * Portrait ou Paysage
      * Logement complet
      * Plaque de couverture
   * Prise en charge de la fixation
   * Personnel : responsable de l'installation du matériel et de sa connexion au réseau
   * À quelle distance est la source d'énergie du fixateur ?
   * À quelle distance se trouve le panneau physique du périphérique réel ?

1. Le **contenu**

   Le contenu comprend :
   * Zone unique ou Zone multiple ?
      * Combien de fichiers multimédia se trouvent à l’écran en même temps ?
      * Combien de pages pour les applications interactives ?
      * Définition de la boucle d’interface
      * Contenu piloté par les données ?
   * Gestion de version

1. **Interactif**

   Interactif :
   * Type d’écran tactile préféré ? (résistif, capacitif, multipoint) ?
      * Touche Bouton
      * Gestes
   * Déclenchement des données (E/S) ?
      * Envoi/réception de commandes série (fermeture de contact, PLC, etc.)
      * Les données entrantes s’affichent à l’écran (RSS) ou déclenchent le contenu.
      * RFID/NFC/Bluetooth/iBeacon
      * Services externes (météo, trafic, etc.)

1. **de création**

   L’environnement met l’accent sur :
   * Afficher l'emplacement ?
      * Intérieur et extérieur
      * Excepté ou directement exposé
   * Conditions temporaires spéciales ?
   * Une preuve vandale ?
   * Lumière ambiante élevée ? De forts contrastes ?

1. **Maintenance**

   La maintenance met l'accent sur :

   * Des guides d’installation détaillés/des guides d’utilisation sont-ils requis ?
   * Sommes-nous en train de configurer (programmer) le dispositif avant l'expédition ?
   * Devons-nous capturer chaque numéro de série à des fins de suivi ?
   * Existe-t-il des besoins en alimentation de secours (alimentation sans interruption)?
   * Comment les mises à jour système sont-elles déployées ? Et comment les dispositifs sont-ils contrôlés à distance ? Une solution MDM est-elle nécessaire ?
