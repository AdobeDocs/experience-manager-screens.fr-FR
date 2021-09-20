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
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 36%

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
>1. Cliquez sur le lien **Enregistrement** dans le menu d’actions de gauche et suivez les étapes ci-dessous pour terminer le processus d’enregistrement du périphérique.


## Surveillance de lecture de base {#playback-monitoring}

Le lecteur signale différentes mesures de lecture pour chaque `ping` qui correspond par défaut à 30 secondes. Sur la base de ces mesures, nous pouvons détecter divers cas de périphérie, tels que des problèmes de blocage, d’écran vide et de planification. Cela nous permet de comprendre et de résoudre les problèmes liés à l’appareil et d’accélérer ainsi les enquêtes et les mesures correctives avec vous.

La surveillance de base de la lecture dans un lecteur AEM Screens nous permet d’effectuer les opérations suivantes :

* Surveillez à distance si un lecteur lit correctement le contenu.

* Améliorez la réactivité des écrans vierges ou des expériences rompues dans le champ.

* Réduit le risque d’afficher une expérience rompue à l’utilisateur final.

### Présentation des propriétés {#understand-properties}

Les propriétés suivantes sont incluses dans chaque `ping` :

| Propriété | Description |
|---|---|
| id {string} | l’identifiant du lecteur |
| activeChannel {string} | chemin du canal en cours de lecture ou valeur nulle si rien n’est planifié |
| activeElements {string} | chaîne séparée par des virgules, éléments actuellement visibles dans tous les canaux de séquence de lecture (plusieurs dans le cas d’une disposition multizone) |
| isDefaultContent {boolean} | true si le canal de lecture est considéré comme un canal par défaut ou de secours (c’est-à-dire qu’il a la priorité 1 et aucun planning) |
| hasContentChanged {boolean} | true si le contenu a changé au cours des 5 dernières minutes, false dans le cas contraire |
| lastContentChange {string} | date et heure de la dernière modification du contenu |

>[!NOTE]
>Vous pouvez éventuellement activer une propriété plus avancée à partir des préférences du lecteur (activer la surveillance de lecture), à savoir :
>|Property|Description|
>|—|—|
>|isContentRendering {boolean}|true si le GPU peut confirmer qu’il lit du contenu réel (en fonction de l’analyse des pixels)|

### Restrictions {#limitations}

Vous trouverez ci-dessous quelques limites à la surveillance de lecture de base :

* Le lecteur signale son propre état de lecture au serveur ; il nécessite donc une connexion principale.

* La propriété `isContentRendering` qui vérifie le GPU nécessite actuellement trop de ressources pour être activée par défaut et nécessite une inclusion explicite dans les préférences du lecteur. Il est recommandé de ne pas l’utiliser conjointement avec les vidéos en production.

* Cette fonctionnalité est uniquement prise en charge pour les canaux de séquence et ne couvre pas encore le cas d’utilisation des canaux interactifs (SPA).

* Les mesures ne sont pas encore entièrement exposées aux clients. Nous nous efforçons d’activer prochainement un mécanisme de reporting et d’alerte de type tableau de bord.

### Ressources supplémentaires {#additional-resources}

Reportez-vous aux rubriques suivantes pour obtenir des informations détaillées :

* Pour télécharger le lecteur Android, rendez-vous sur **Google Play**. Pour en savoir plus sur l’implémentation d’Android Watchdog, consultez [Mise en œuvre du lecteur Android](implementing-android-player.md).

* Pour plus d’informations sur la mise en œuvre du lecteur Chrome OS, consultez [Console de gestion de Chrome](implementing-chrome-os-player.md).

* Pour configurer le lecteur Windows d’AEM Screens, consultez la section [Mise en œuvre du lecteur Windows](implementing-windows-player.md).
