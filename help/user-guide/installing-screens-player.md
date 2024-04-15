---
title: Installation du lecteur Screens
description: Découvrez comment installer correctement un lecteur AEM Screens.
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 48%

---

# Installation du lecteur AEM Screens {#installing-player}

Cette page décrit comment installer le lecteur AEM Screens.

## Lecteur Screens disponible {#available-players}

Le lecteur AEM Screens est disponible pour Android, Chrome OS et Windows.

Pour télécharger le **lecteur AEM Screens**, consultez la page de [téléchargement du lecteur AEM 6.5](https://download.macromedia.com/screens/).

>[!NOTE]
>
>Après avoir téléchargé le dernier lecteur (*.exe*), suivez les étapes du lecteur pour terminer l’installation ad hoc :
>
>1. Appuyez longuement dans le coin supérieur gauche pour ouvrir le panneau d’administration.
>1. Accédez à **Configuration** dans le menu d’actions de gauche, saisissez l’adresse de l’emplacement de l’instance AEM dans **Serveur** et sélectionnez **Enregistrer**.
>1. Sélectionner **Enregistrement** à partir du menu d’actions de gauche et des étapes ci-dessous pour terminer le processus d’enregistrement du périphérique.

## Suivi de base de la lecture {#playback-monitoring}

Le lecteur signale différentes mesures de lecture pour chaque `ping` qui correspond par défaut à 30 secondes. Sur la base de ces mesures, il peut détecter divers cas de périphérie, tels que des problèmes de blocage, d’écran vide et de planification. Cela nous permet de comprendre et de résoudre les problèmes liés à l’appareil et d’accélérer ainsi l’examen des problèmes et les mesures correctives.

La surveillance de base de la lecture dans un lecteur AEM Screens vous permet d’effectuer les opérations suivantes :

* Surveiller à distance si un lecteur lit correctement le contenu

* Améliorer la réactivité des écrans vierges ou des expériences rompues dans ce champ

* Réduire les risques d’afficher une expérience rompue à l’utilisateur final

### Présentation des propriétés {#understand-properties}

Les propriétés suivantes sont incluses dans chaque `ping` :

| Propriété | Description |
|---|---|
| id {string} | identifiant du lecteur |
| activeChannel {string} | chemin du canal en cours de lecture ou valeur nulle si rien n’est planifié |
| activeElements {string} | chaînes séparées par des virgules, éléments actuellement visibles dans tous les canaux de séquence de lecture (plusieurs dans une disposition multizone) |
| isDefaultContent {boolean} | true si le canal de lecture est considéré comme un canal par défaut ou de secours (c’est-à-dire qu’il a la priorité 1 et aucune planification) |
| hasContentChanged {boolean} | true si le contenu a changé au cours des 5 dernières minutes, false dans le cas contraire |
| lastContentChange {string} | date et heure de la dernière modification du contenu |

>[!NOTE]
>Vous pouvez éventuellement activer une propriété plus avancée à partir des préférences du lecteur (activer le suivi de la lecture), à savoir :
>
>| Propriété | Description |
>|---|---|
>| isContentRendering {boolean} | true si le GPU peut confirmer qu’il lit du contenu réel (en fonction de l’analyse des pixels) |

### Restrictions {#limitations}

Vous trouverez ci-dessous quelques limitations au suivi de base de la lecture :

* Le lecteur signale son propre état de lecture au serveur ; il nécessite donc une connexion principale.

* La variable `isContentRendering` qui vérifie le GPU est trop gourmand en ressources pour être activé par défaut et nécessite une inclusion explicite dans les préférences du lecteur. Adobe recommande de ne pas l’utiliser avec des vidéos en production.

* Cette fonctionnalité est uniquement prise en charge pour les canaux de séquence et ne couvre pas encore le cas d’utilisation des canaux interactifs (SPA).

* Les mesures ne sont pas encore entièrement exposées aux clients. Adobe s’efforce d’activer prochainement des mécanismes de reporting et d’alerte de type tableau de bord.

### Autres ressources {#additional-resources}

Consultez les rubriques suivantes pour obtenir des informations détaillées :

* Pour télécharger le lecteur Android™, rendez-vous sur la page **Google Play**. Pour en savoir plus sur l’implémentation d’Android™ Watchdog, voir [Mise en oeuvre du lecteur Android™](implementing-android-player.md).

* Pour mettre en oeuvre le lecteur Chrome OS, voir [Console de gestion de Chrome](implementing-chrome-os-player.md) pour plus d’informations.

* Pour configurer le lecteur Windows AEM Screens, voir [Mise en oeuvre du lecteur Windows](implementing-windows-player.md).
