---
title: Activation au niveau du canal - Lecture d’un événement unique
description: Découvrez l’activation au niveau du canal à l’aide de la lecture d’événement unique.
topic-tags: authoring
feature: Authoring Screens, Channels
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: c142830a37461a36baae15f543bd43b0ae8a62a7
workflow-type: tm+mt
source-wordcount: '1769'
ht-degree: 50%

---

# Activation au niveau des canaux {#channel-level-activation-single-event-playback}

Cette page décrit l’activation au niveau des canaux des ressources utilisées dans les canaux.

Cette section aborde les sujets suivants :

* Présentation
* Fenêtre d’activation
* Utilisation de l’activation au niveau des canaux comme lecture d’événement unique
* Gestion de la périodicité des ressources dans un canal
   * Tranches horaires
   * Tranches hebdomadaires
   * Tranches mensuelles
   * Combinaison de tranches
* Utilisation de l’activation au niveau des canaux comme lecture d’événement unique

## Présentation {#overview}

L ***’activation au niveau des canaux*** permet aux canaux de permuter selon une planification définie. Le canal d’événement unique remplace le canal principal après une planification définie et il est lu pendant une période donnée, jusqu’à ce que le canal principal exécute à nouveau son contenu.

L’exemple suivant fournit une solution en se concentrant sur les termes clés suivants :

* un ***canal de séquence principal*** pour la séquence globale
* un ***canal d’événement unique*** qui s’exécute une seule fois à un moment défini
* une ***planification et une priorité définies*** de l’événement de lecture unique qui se produit dans le canal de séquence principal

## Fenêtre d’activation {#using-channel-level-activation}

La section suivante explique la création d’une lecture d’événement unique dans un canal pour un projet AEM Screens.

### Prérequis {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, assurez-vous que vous disposez des conditions préalables suivantes pour commencer à implémenter l’activation au niveau du canal :

* Créez un projet AEM Screens, dans cet exemple, **Channel Level Activation**

* Créez un canal appelé **MainAdChannel** sous le dossier **Canaux**

* Créez un autre canal appelé **TargetedSinglePlay** sous le dossier **Canaux**

* Ajoutez les ressources appropriées aux deux canaux

L’image ci-après montre le projet **Channel Level Activation** avec les canaux **MainAdChannel** et **TargetedSinglePlay** dans le dossier **Canaux**.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Pour plus d’informations sur la création d’un projet et d’un canal de séquence, consultez les ressources suivantes :
>
>* [Création et gestion des projets](creating-a-screens-project.md)
>
>* [Gestion d’un canal](managing-channels.md)
>

### Mise en œuvre {#implementation}

L’implémentation de l’activation au niveau du canal dans un projet AEM Screens implique trois tâches principales :

1. **Configuration de la taxonomie du projet, y compris les canaux, emplacements et écrans**
1. **Affectation de canaux à un affichage**
1. **Configuration d’un calendrier et d’une priorité**

Suivez les étapes ci-dessous pour mettre en œuvre la fonctionnalité :

1. **Créez un emplacement**

   Accédez au dossier **Emplacements** dans votre projet AEM Screens et créez un emplacement en tant que **Région**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Pour savoir comment créer un emplacement, voir **[Création et gestion des emplacements](managing-locations.md)**.

1. **Créer un affichage sous Emplacement**

   1. Accédez à **Channel Level Activation** > **Emplacements** > **Région**.
   1. Sélectionnez **Région**, puis cliquez sur **+Créer** dans la barre d’actions.
   1. Sélectionnez **Afficher** dans l’assistant et créez un affichage intitulé **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Affecter des canaux à un affichage**

   Pour **MainAdChannel :**

   1. Accédez à **Channel Level Activation** > **Emplacements** > **Région** > **RegionDisplay** puis cliquez sur **Affecter un canal** dans la barre d’actions.
   1. La boîte de dialogue **Attribution de canaux** s’ouvre.
   1. Sélectionner **Canal de référence** par chemin.
   1. Sélectionner le **Chemin du canal** as **Activation au niveau du canal** > ***Canaux*** > ***MainAdChannel***.
   1. Le **Rôle du canal** est défini comme **mainadchannel**.
   1. Sélectionnez la **Priorité** **1**.
   1. Sélectionnez les **Événements pris en charge** : **Chargement initial** et **Écran inactif**.
   1. Sélectionnez **Enregistrer**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Vous pouvez également attribuer un canal à partir du tableau de bord d’affichage en accédant à . **Activation au niveau du canal** > **Emplacements** > **Region** > **RegionDisplay** et en cliquant **Tableau de bord** à partir de la barre d’actions. Cliquez sur **+ Attribuer un canal** dans le panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**.

   De même, affectez le canal **TargetedSinglePlay** afin qu’il soit affiché** :

   1. Accédez à **Channel Level Activation** > **Emplacements** > **Région** > **RegionDisplay** puis cliquez sur **Affecter un canal** dans la barre d’actions.
   1. La boîte de dialogue **Attribution de canaux** s’ouvre.
   1. Sélectionner **Canal de référence** par chemin.
   1. Sélectionner le **Chemin du canal** as **Activation au niveau du canal*** > ***Canaux*** > ***TargetedSinglePlay***.
   1. Le **Rôle de canal** est renseigné avec le contenu **targetedsingleplay**.
   1. Définissez la **Priorité** sur **2**.
   1. Sélectionner le **Événements pris en charge** as **Charge Initiale**, **Écran inactif**, et **Minuteur**, comme le montre la figure ci-dessous.
   1. Choisir la date dans **actif à partir de** le 27 novembre 2018 à 23 h 59 et à **actif jusqu’au** le 28 novembre 2018 à 12 h 05
   1. Sélectionnez **Enregistrer**.

   >[!CAUTION]
   >
   >Définir la priorité de **TargetedSinglePlay** canal supérieur à **MainAdSegment** canal.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   >
   >Pour choisir le même jour, sélectionnez le jour suivant, puis modifiez manuellement la date du même jour, mais pour une heure ultérieure. Cela empêche l’utilisateur de sélectionner une date passée. Considérez l’exemple suivant :

   ![new1](assets/new1.gif)

## Affichage des résultats {#viewing-the-results}

Une fois la configuration des canaux et de l’affichage terminée, lancez le lecteur AEM Screens pour afficher le contenu.

Le lecteur affiche le contenu de **MainAdChannel** et exactement à 23 h 59 (comme le prévoit l&#39;horaire), le **TargetedSinglePlay** le canal affiche son contenu jusqu’à 00 h 05, puis le **MainAdChannel** reprend la lecture de son contenu.

>[!NOTE]
>
>Pour en savoir plus sur AEM Screen Player, consultez les ressources suivantes :
>[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/)
>[Utilisation du lecteur AEM Screens](working-with-screens-player.md)


## Gestion de la périodicité des ressources dans un canal {#handling-recurrence-in-assets}

Vous pouvez planifier l’activation périodique des ressources d’un canal à certains intervalles, tous les jours, toutes les semaines ou tous les mois, selon vos besoins.

Supposons que vous souhaitiez afficher le contenu d’un canal uniquement le vendredi, de 13 h à 22 h. Vous pouvez utiliser l’onglet **Activation** pour définir l’intervalle périodique souhaité pour votre ressource.

### Tranches horaires {#day-parting}

1. Sélectionnez le canal, puis sélectionnez **Tableau de bord** à partir de la barre d’actions.

1. Après avoir renseigné la date et l’heure de début et la date et l’heure de fin dans la boîte de dialogue **Attribution de canaux**, vous pouvez utiliser une expression ou une version de texte naturel pour définir la planification de périodicité.

   >[!NOTE]
   >
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans le champ **Planification** et votre ressource s’affiche pour l’intervalle de jour et d’heure spécifique.

#### Exemples d’expressions pour les tranches horaires {#example-one}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| avant 8 h | la ressource dans la chaîne est lue avant 8 h tous les jours |
| après 14 h | la ressource de la chaîne est lue après 14 heures tous les jours |
| après 12 h 15 et avant 12 h 45 | la ressource de la chaîne est lue après 12 h 15 tous les jours pendant 30 minutes |
| avant 12 h 15 et après 12 h 45 | la ressource dans la chaîne est lue avant 12 h 15 tous les jours, puis également après 12 h 45. |
| Lun, Mar, Mer ou Lun-Mer | la ressource du canal est lue du lundi au mercredi |
| le premier jour de janvier après 14h00 et le deuxième jour de janvier, ainsi que le troisième jour de janvier avant 3h00. | la lecture de la ressource dans le canal commence après 14 h 00 le 1er janvier et se poursuit toute la journée le 2 janvier jusqu’à 3 h 00 le 3 janvier |
| les 1 à 2 jours de janvier après 14 h, ainsi que les 2 à 3 jours de janvier avant 3 h. | la ressource sur le canal démarre le lecteur après 14 h 00 le 1er janvier, continue la lecture jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et continue jusqu’à 3 h 00 le 3 janvier |

>[!NOTE]
>
>Vous pouvez également utiliser _temps militaire_ notation (14:00) au lieu de *A.M./P.M.* (14 H).

### Tranches hebdomadaires {#week-parting}

1. Sélectionnez le canal, puis sélectionnez **Tableau de bord** à partir de la barre d’actions.

1. Après avoir renseigné la date et l’heure de début et la date et l’heure de fin dans la boîte de dialogue **Attribution de canaux**, vous pouvez utiliser une expression ou une version de texte naturel pour définir la planification de périodicité.

   >[!NOTE]
   >
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans le champ **Planification** et votre ressource s’affiche pour l’intervalle de jour et d’heure spécifique.

#### Exemples d’expressions pour les tranches hebdomadaires {#example-two}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| Lun, Mar, Mer ou Lun-Mer | la ressource du canal est lue du lundi au mercredi |
| avant 8 h | la ressource dans la chaîne est lue avant 8 h tous les jours |
| après 14 h | la ressource de la chaîne est lue après 14 heures tous les jours |
| après 12 h 15 et avant 12 h 45 | la ressource de la chaîne est lue après 12 h 15 tous les jours pendant 30 minutes |
| avant 12 h 15 et après 12 h 45 | la chaîne joue avant 12 h 15 tous les jours, puis après 12 h 45. |

>[!NOTE]
>
>Vous pouvez également utiliser _temps militaire_ notation (14:00) au lieu de *A.M./P.M.* (14 H).


### Tranches mensuelles {#month-parting}

1. Sélectionnez le canal, puis sélectionnez **Tableau de bord** à partir de la barre d’actions.

1. Après avoir renseigné la date et l’heure de début et la date et l’heure de fin dans la boîte de dialogue **Attribution de canaux**, vous pouvez utiliser une expression ou une version de texte naturel pour définir la planification de périodicité.

   >[!NOTE]
   >
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans le champ **Planification** et votre ressource s’affiche pour l’intervalle de jour et d’heure spécifique.

#### Exemples d’expressions pour les tranches mensuelles {#example-three}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| de `February,May,August,November` | la ressource est lue sur la chaîne en février, mai, août et novembre. |

>[!NOTE]
>
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées et nom complet, telles que Lun/Lundi et Janvier/Janvier.

>[!NOTE]
>
>Vous pouvez également utiliser _temps militaire_ notation (14:00) au lieu de *A.M./P.M.* (14 H).

### Combinaison de tranches {#combined-parting}

1. Sélectionnez le canal, puis sélectionnez **Tableau de bord** à partir de la barre d’actions.

1. Après avoir renseigné la date et l’heure de début et la date et l’heure de fin dans la boîte de dialogue **Attribution de canaux**, vous pouvez utiliser une expression ou une version de texte naturel pour définir la planification de périodicité.

   >[!NOTE]
   >
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans le champ **Planification** et votre ressource s’affiche pour l’intervalle de jour et d’heure spécifique.

#### Exemples d’expressions de combinaison de tranches {#example-four}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| après 6h00 et avant 18h00 le lundi, mer de Jan-Mar | la ressource est lue dans le canal entre 6 h et 18 h les lundis et mercredis, du mois de janvier à la fin du mois de mars |
| le premier jour de janvier après 14h00 et le deuxième jour de janvier, ainsi que le troisième jour de janvier avant 3h00. | la lecture de la ressource dans le canal commence après 14 h 00 le 1er janvier et se poursuit toute la journée le 2 janvier jusqu’à 3 h 00 le 3 janvier |
| les 1 à 2 jours de janvier après 14 h, ainsi que les 2 à 3 jours de janvier avant 3 h. | la ressource sur le canal démarre le lecteur après 14 h 00 le 1er janvier, continue la lecture jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et continue jusqu’à 3 h 00 le 3 janvier |

>[!NOTE]
>
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées et nom complet, telles que Lun/Lundi et Janvier/Janvier. Vous pouvez également utiliser _temps militaire_ notation (14:00) au lieu de *A.M./P.M.* (14 H).
