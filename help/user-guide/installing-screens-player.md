---
title: Installation du lecteur Screens
seo-title: Installing Screens Player
description: Rendez-vous sur cette page pour en savoir plus sur l’installation du lecteur AEM Screens disponible.
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 92%

---

# Installation du lecteur AEM Screens {#installing-player}

Cette page décrit comment installer le lecteur AEM Screens.

## Lecteur Screens disponible {#available-players}

Le lecteur AEM Screens est disponible pour Android, Chrome OS et Windows.

Pour télécharger le **lecteur AEM Screens**, consultez la page de [téléchargement du lecteur AEM 6.5](https://download.macromedia.com/screens/).

>[!NOTE]
>
>Une fois que vous avez téléchargé la dernière version du lecteur (*.exe*), suivez les étapes du lecteur pour terminer l’installation ad hoc :
>
>1. Appuyez longuement dans l’angle supérieur gauche pour ouvrir le panneau d’administration.
>1. Accédez à **Configuration** à partir du menu d’actions de gauche, saisissez l’adresse de l’emplacement de l’instance AEM dans **Serveur** et cliquez sur **Enregistrer**.
>1. Cliquez sur le lien **Enregistrement** dans le menu d’actions de gauche et suivez les étapes ci-dessous pour terminer le processus d’enregistrement de l’appareil.

## Suivi de base de la lecture {#playback-monitoring}

Le lecteur signale différentes mesures de lecture pour chaque `ping` qui correspond par défaut à 30 secondes. Sur la base de ces mesures, nous pouvons détecter différents cas de figure, tels que des problèmes de lecture bloquée, d’écran vide et de planification. Cela nous permet de comprendre et de résoudre les problèmes liés à l’appareil et d’accélérer ainsi l’examen des problèmes et les mesures correctives.

La surveillance de base de la lecture dans un lecteur AEM Screens nous permet d’effectuer les opérations suivantes :

* Surveiller à distance si un lecteur lit correctement le contenu

* Améliorer la réactivité des écrans vierges ou des expériences rompues dans ce champ

* Réduire les risques d’afficher une expérience rompue à l’utilisateur final

### Présentation des propriétés {#understand-properties}

Les propriétés suivantes sont incluses dans chaque `ping` :

| Propriété | Description |
|---|---|
| id {string} | identifiant du lecteur |
| activeChannel {string} | chemin du canal en cours de lecture ou valeur nulle si rien n’est planifié |
| activeElements {string} | chaîne séparée par des virgules, éléments actuellement visibles dans tous les canaux de séquence de lecture (plusieurs dans le cas d’une disposition multizone) |
| isDefaultContent {boolean} | true si le canal de lecture est considéré comme un canal par défaut ou de secours (c’est-à-dire qu’il a la priorité 1 et aucune planification) |
| hasContentChanged {boolean} | true si le contenu a changé au cours des 5 dernières minutes, false dans le cas contraire |
| lastContentChange {string} | date et heure de la dernière modification du contenu |

>[!NOTE]
>Vous pouvez éventuellement activer une propriété plus avancée à partir des préférences du lecteur (activer le suivi de la lecture), à savoir :
>|Property|Description|
>|---|---|
>|isContentRendering {boolean}|true si le GPU peut confirmer qu’il lit du contenu réel (en fonction de l’analyse des pixels)|

### Restrictions {#limitations}

Vous trouverez ci-dessous quelques limitations au suivi de base de la lecture :

* Le lecteur signale son propre état de lecture au serveur ; il nécessite donc une connexion principale.

* La propriété `isContentRendering` vérifiant le GPU nécessite actuellement trop de ressources pour être activée par défaut et nécessite une inclusion explicite dans les préférences du lecteur. Il est recommandé de ne pas l’utiliser conjointement avec les vidéos en production.

* Cette fonctionnalité est uniquement prise en charge pour les canaux de séquence et ne couvre pas encore le cas d’utilisation des canaux interactifs (SPA).

* Les mesures ne sont pas encore entièrement exposées aux clients. Nous nous efforçons d’activer prochainement un mécanisme de reporting et d’alerte de type tableau de bord.

### Ressources supplémentaires {#additional-resources}

Consultez les rubriques suivantes pour obtenir des informations détaillées :

* Pour télécharger le lecteur Android, rendez-vous sur **Google Play**. Pour en savoir plus sur l’implémentation d’Android Watchdog, voir [Mise en oeuvre du lecteur Android](implementing-android-player.md).

* Pour mettre en oeuvre le lecteur Chrome OS, voir [Console de gestion de Chrome](implementing-chrome-os-player.md) pour plus d’informations.

* Pour configurer le lecteur Windows AEM Screens, voir [Mise en oeuvre du lecteur Windows](implementing-windows-player.md).
