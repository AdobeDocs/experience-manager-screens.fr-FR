---
title: Installation du lecteur Screens
description: Découvrez comment installer correctement un lecteur AEM Screens.
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
TQID: https://experienceleague.adobe.com/Lu1KYTTaDEiaC1xP4k0V8KqDVoe5gIzqkut-JB0G4fg
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 552
ht-degree: 86%

---

# Installer le lecteur AEM Screens {#installing-player}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Cette page détaille comment installer un lecteur AEM Screens.

## Lecteur Screens disponible {#available-players}

Le lecteur AEM Screens est disponible pour Android™, Chrome OS et Windows.

Pour télécharger le **lecteur AEM Screens**, consultez la page des [téléchargements du lecteur AEM 6.5](https://download.macromedia.com/screens/).

>[!NOTE]
>
>Une fois que vous avez téléchargé la dernière version du lecteur (*.exe*), suivez les étapes du lecteur pour terminer l’installation ad hoc :
>
>1. Appuyez longuement dans l’angle supérieur gauche pour ouvrir le panneau d’administration.
>1. Accédez à **Configuration** à partir du menu d’actions de gauche, saisissez l’adresse de l’emplacement de l’instance AEM dans **Serveur** et cliquez sur **Enregistrer**.
>1. Cliquez sur le lien **Enregistrement** dans le menu d’actions de gauche et suivez les étapes ci-dessous pour terminer le processus d’enregistrement de l’appareil.

## Suivi de base de la lecture {#playback-monitoring}

Le lecteur signale différentes mesures de lecture pour chaque `ping` qui correspond par défaut à 30 secondes. En fonction de ces mesures, il peut détecter divers cas de périphérie, tels que des problèmes de lecture bloquée, d’écran vide et de planification. Cela nous permet de comprendre et de résoudre les problèmes liés à l’appareil et d’accélérer ainsi l’examen de vos problèmes et la mise en place de correctifs.

La surveillance de base de la lecture d’un lecteur AEM Screens vous permet d’effectuer les opérations suivantes :

* Surveiller à distance si un lecteur lit correctement le contenu

* Améliorer la réactivité des écrans vierges ou des expériences rompues dans ce champ

* Réduire les risques d’afficher une expérience rompue à l’utilisateur final

### Présentation des propriétés {#understand-properties}

Les propriétés suivantes sont incluses dans chaque `ping` :

| Propriété | Description |
|---|---|
| id {string} | identifiant du lecteur |
| {string} activeChannel | chemin du canal en cours de lecture ou valeur nulle si rien n’est planifié |
| {string} activeElements | chaîne séparée par des virgules, éléments actuellement visibles dans tous les canaux de séquence de lecture (plusieurs dans le cas d’une disposition multizone) |
| isDefaultContent {boolean} | true si le canal de lecture est considéré comme un canal par défaut ou de secours (c’est-à-dire qu’il a la priorité 1 et aucune planification) |
| hasContentChanged {boolean} | true si le contenu a changé au cours des 5 dernières minutes, false dans le cas contraire |
| lastContentChange {string} | date et heure de la dernière modification du contenu |

>[!NOTE]
>
>Vous pouvez éventuellement activer une propriété plus avancée à partir des préférences du lecteur (activer le suivi de la lecture), à savoir :
>
>| Propriété | Description |
>|---|---|
>| isContentRendering {boolean} | true si le GPU peut confirmer qu’il lit du contenu réel (en fonction de l’analyse des pixels) |

### Limites {#limitations}

Vous trouverez ci-dessous quelques limitations concernant la surveillance de base de la lecture :

* Le lecteur signale son propre état de lecture au serveur ; il nécessite donc une connexion active.

* La propriété `isContentRendering` qui vérifie le GPU nécessite actuellement trop de ressources pour être activée par défaut et nécessite une activation explicite dans les préférences du lecteur. Adobe vous recommande de ne pas l’utiliser avec les vidéos en production.

* Cette fonctionnalité est uniquement prise en charge pour les canaux de séquence et ne couvre pas encore le cas d’utilisation des canaux interactifs (SPA).

* Les mesures ne sont pas encore entièrement accessibles aux clientes et aux clients. Adobe travaille à la mise en place prochaine d’un mécanisme de création de rapports et d’alertes, de type tableau de bord.

### Autres ressources {#additional-resources}

Reportez-vous aux rubriques suivantes pour obtenir des informations détaillées :

* Pour télécharger le lecteur Android™, rendez-vous sur **Google Play**. Pour en savoir plus sur l’implémentation d’Android™ Watchdog, voir [Implémenter le lecteur Android™](implementing-android-player.md).

* Pour plus d’informations sur la mise en œuvre du lecteur Chrome OS, voir [Console de gestion de Chrome](implementing-chrome-os-player.md).

* Pour configurer le lecteur Windows dans AEM Screens, voir [Implémentation du lecteur Windows](implementing-windows-player.md).
