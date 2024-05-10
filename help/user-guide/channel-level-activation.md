---
title: Activation au niveau du canal - Lecture d’un événement unique
description: Découvrez l’activation au niveau du canal à l’aide de la lecture d’événement unique.
topic-tags: authoring
feature: Authoring Screens, Channels
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '1791'
ht-degree: 71%

---

# Activation au niveau des canaux {#channel-level-activation-single-event-playback}

Cette page décrit l’activation au niveau des canaux des ressources utilisées dans les canaux.

Cette section aborde les sujets suivants :

* Vue d’ensemble
* Fenêtre d’activation
* Utilisation de l’activation au niveau des canaux comme lecture d’événement unique
* Gestion de la périodicité des ressources dans un canal
   * Tranches horaires
   * Tranches hebdomadaires
   * Tranches mensuelles
   * Combinaison de tranches
* Utilisation de l’activation au niveau des canaux comme lecture d’événement unique

## Vue d’ensemble {#overview}

L ***’activation au niveau des canaux*** permet aux canaux de permuter selon une planification définie. Le canal d’événement unique remplace le canal principal après une planification définie et il est lu pendant une période donnée, jusqu’à ce que le canal principal exécute à nouveau son contenu.

L’exemple suivant fournit une solution en se concentrant sur les termes clés suivants :

* un ***canal de séquence principal*** pour la séquence globale
* un ***canal d’événement unique*** qui s’exécute une seule fois à un moment défini
* une ***planification et une priorité définies*** de l’événement de lecture unique qui se produit dans le canal de séquence principal

## Fenêtre d’activation {#using-channel-level-activation}

La section suivante explique la création d’une lecture d’événement unique dans un canal pour un projet AEM Screens.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, veillez à ce que les conditions préalables suivantes soient satisfaites avant de commencer à implémenter l’activation au niveau du canal :

* Créez un projet AEM Screens, dans cet exemple : **Activation au niveau du canal**.

* Création d’un canal comme **MainAdChannel** sous le **Canaux** dossier.

* Créez un autre canal comme **TargetedSinglePlay** sous le **Canaux** dossier.

* Ajoutez les ressources appropriées aux deux canaux.

L’image suivante montre la variable **Activation au niveau du canal** projet avec **MainAdChannel** et **TargetedSinglePlay** canaux dans la **Canaux** dossier.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Pour plus d’informations sur la création d’un projet et la création d’un canal de séquence, reportez-vous aux ressources ci-dessous :
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
   >Pour savoir comment créer un emplacement, reportez-vous à **[Création et gestion des emplacements](managing-locations.md)**.

1. **Créer un affichage sous Emplacement**

   1. Accédez à **Channel Level Activation** > **Emplacements** > **Région**.
   1. Cliquez sur **Région** et cliquez sur **+ Créer** dans la barre d’actions.
   1. Cliquez sur **Affichage** à partir de l’assistant et créez un affichage intitulé **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Affecter des canaux à un affichage**

   Pour **MainAdChannel :**

   1. Accédez à **Channel Level Activation** > **Emplacements** > **Région** > **RegionDisplay** puis cliquez sur **Affecter un canal** dans la barre d’actions.
   1. Dans le **Attribution de canaux** boîte de dialogue, cliquez sur **Canal de référence** par chemin.
   1. Cliquez sur le bouton **Chemin du canal**, puis cliquez sur **Activation au niveau du canal** > ***Canaux*** > ***MainAdChannel***.
   1. Le **Rôle du canal** est défini comme **mainadchannel**.
   1. Cliquez sur le bouton **Priorité** et définissez sur **1**.
   1. Cliquez sur le bouton **Événements pris en charge** par exemple **Charge initiale** et **Écran inactif**.
   1. Cliquez sur **Enregistrer**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Vous pouvez également attribuer le canal à partir du tableau de bord de l’affichage. Accédez à **Activation au niveau du canal** > **Emplacements** > **Région** > **RegionDisplay**. Dans la barre d’actions, sélectionnez **Tableau de bord**. Dans la **CANAUX ET PLANIFICATIONS AFFECTÉS** panneau, cliquez sur **+ Attribuer le canal**.

   De même, affectez le canal **TargetedSinglePlay** afin qu’il soit affiché** :

   1. Accédez à **Channel Level Activation** > **Emplacements** > **Région** > **RegionDisplay** puis cliquez sur **Affecter un canal** dans la barre d’actions.
   1. Dans le **Attribution de canaux** , cliquez sur **Canal de référence** par chemin.
   1. Cliquez sur le bouton **Chemin du canal**, puis cliquez sur **Activation au niveau du canal** > ***Canaux*** > ***TargetedSinglePlay***.
   1. Le **Rôle de canal** est renseigné avec le contenu **targetedsingleplay**.
   1. Définissez la variable **Priorité** to **2**.
   1. Cliquez sur le bouton **Événements pris en charge**, et définissez **Charge initiale**, **Écran inactif**, et **Minuteur**, comme illustré dans la figure ci-dessous.
   1. Dans **actif depuis**, défini sur le 27 novembre 2018, à 23 h 59, et dans **actif jusqu’à**, fixée au 28 novembre 2018 à 12h05.
   1. Cliquez sur **Enregistrer**.

   >[!CAUTION]
   >
   >Définissez la priorité de la variable **TargetedSinglePlay** canal supérieur à **MainAdSegment** canal.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   >
   >Pour choisir le même jour, cliquez sur le jour suivant, puis modifiez manuellement la date pour qu’elle soit le même jour, mais pour une heure ultérieure. La personne ne peut donc pas sélectionner une date antérieure. Considérez l’exemple suivant :

   ![new1](assets/new1.gif)

## Affichage des résultats {#viewing-the-results}

Une fois la configuration des canaux et l’affichage terminés, lancez le lecteur AEM Screens pour afficher le contenu.

Le lecteur affiche le contenu de **MainAdChannel** et exactement à 23 h 59 (comme défini dans le planning), le canal **TargetedSinglePlay** affiche son contenu jusqu’à 00 h 05, puis le canal **MainAdChannel** reprend la lecture de son contenu.

>[!NOTE]
>
>Pour en savoir plus sur le lecteur AEM Screens, consultez les ressources suivantes :
>[Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/)
>[Utiliser le lecteur AEM Screens](working-with-screens-player.md)


## Gestion de la périodicité des ressources dans un canal {#handling-recurrence-in-assets}

Vous pouvez planifier l’exécution quotidienne, hebdomadaire ou mensuelle des ressources d’un canal à certains intervalles, selon vos besoins.

Supposons que vous souhaitiez afficher le contenu d’un canal uniquement le vendredi de 13 h 00 à 22 h 00. Vous pouvez utiliser l’onglet **Activation** pour définir l’intervalle périodique souhaité pour votre ressource.

### Tranches horaires {#day-parting}

1. Cliquez sur le canal, puis sur **Tableau de bord** dans la barre d’actions.

1. Après avoir renseigné la date et l’heure de début et la date et l’heure de fin dans la boîte de dialogue **Attribution de canaux**, vous pouvez utiliser une expression ou une version de texte naturel pour définir le planning de périodicité.

   >[!NOTE]
   >
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Plannings, selon vos besoins.

1. Saisissez l’expression dans le **Planning**. Votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions pour les tranches horaires {#example-one}

Le tableau suivant résume quelques exemples d’expressions que vous pouvez ajouter au planning lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| Avant 8 h 00. | La ressource du canal est lue avant 8 h 00 tous les jours. |
| Après 14 h 00. | La ressource du canal est lue après 14 h 00 tous les jours. |
| Après 12 h 15 et avant 12 h 45. | La ressource du canal est lue après 12 h 15 tous les jours pendant 30 minutes. |
| Avant 12 h 15 et après 12 h 45. | La ressource du canal est lue avant 12 h 15 et après 12 h 45 tous les jours. |
| Lun,Mar,Mer ou Lun-Mer | La ressource du canal est lue du lundi au mercredi. |
| le premier jour de janvier après 14 h 00, le deuxième jour de janvier et le troisième jour de janvier avant 3 h 00. | La lecture de la ressource du canal commence après 14 h 00 le 1er janvier et se poursuit toute la journée du 2 janvier jusqu’à 3 h 00 le 3 janvier. |
| Le 1er et 2 janvier après 14 h 00 et le 2-3 janvier avant 03 h 00. | La lecture de la ressource du canal commence après 14 h 00 le 1er janvier, se poursuit jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et se poursuit jusqu’à 3 h 00 le 3 janvier. |

>[!NOTE]
>
>Vous pouvez également utiliser la notation d’_heure militaire_ (14:00) au lieu de *A.M./P.M.* (14 h 00).

### Tranches hebdomadaires {#week-parting}

1. Cliquez sur le canal, puis sur **Tableau de bord** dans la barre d’actions.

1. Après avoir renseigné la date et l’heure de début et la date et l’heure de fin dans la boîte de dialogue **Attribution de canaux**, vous pouvez utiliser une expression ou une version de texte naturel pour définir le planning de périodicité.

   >[!NOTE]
   >
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Plannings, selon vos besoins.

1. Saisissez l’expression dans le **Planning**. Votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions pour les tranches hebdomadaires {#example-two}

Le tableau suivant résume quelques exemples d’expressions que vous pouvez ajouter au planning lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| Lun,Mar,Mer ou Lun-Mer | La ressource du canal est lue du lundi au mercredi. |
| Avant 8 h 00. | La ressource du canal est lue avant 8 h 00 tous les jours. |
| Après 14 h 00. | La ressource du canal est lue après 14 h 00 tous les jours. |
| Après 12 h 15 et avant 12 h 45. | La ressource du canal est lue après 12 h 15 tous les jours pendant 30 minutes. |
| Avant 12 h 15 et après 12 h 45. | Le canal est lu avant 12 h 15 et après 12 h 45 tous les jours. |

>[!NOTE]
>
>Vous pouvez également utiliser la notation d’_heure militaire_ (14:00) au lieu de *A.M./P.M.* (14 h 00).


### Tranches mensuelles {#month-parting}

1. Cliquez sur le canal, puis sur **Tableau de bord** dans la barre d’actions.

1. Après avoir renseigné la date et l’heure de début et la date et l’heure de fin dans la boîte de dialogue **Attribution de canaux**, vous pouvez utiliser une expression ou une version de texte naturel pour définir le planning de périodicité.

   >[!NOTE]
   >
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Plannings, selon vos besoins.

1. Saisissez l’expression dans le **Planning**. Votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions pour les tranches mensuelles {#example-three}

Le tableau suivant résume quelques exemples d’expressions que vous pouvez ajouter au planning lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| de `February,May,August,November` | La ressource est lue dans le canal en février, mai, août et novembre. |

>[!NOTE]
>
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées ou complètes comme Lun/Lundi et Jan/Janvier.

>[!NOTE]
>
>Vous pouvez également utiliser la notation d’_heure militaire_ (14:00) au lieu de *A.M./P.M.* (14 h 00).

### Combinaison de tranches {#combined-parting}

1. Cliquez sur le canal, puis sur **Tableau de bord** dans la barre d’actions.

1. Après avoir renseigné la date et l’heure de début et la date et l’heure de fin dans la boîte de dialogue **Attribution de canaux**, vous pouvez utiliser une expression ou une version de texte naturel pour définir le planning de périodicité.

   >[!NOTE]
   >
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Plannings, selon vos besoins.

1. Saisissez l’expression dans le **Planning**. Votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions de combinaison de tranches {#example-four}

Le tableau suivant résume quelques exemples d’expressions que vous pouvez ajouter au planning lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| Après 6 h 00 et avant 18 h 00 les lundis et mercredis de janvier à mars | la ressource est lue dans le canal entre 6 h et 18 h les lundis et mercredis de janvier à fin mars |
| le premier jour de janvier après 14 h 00, le deuxième jour de janvier et le troisième jour de janvier avant 3 h 00. | La lecture de la ressource du canal commence après 14 h 00 le 1er janvier et se poursuit toute la journée du 2 janvier jusqu’à 3 h 00 le 3 janvier. |
| Le 1er et 2 janvier après 14 h 00 et le 2-3 janvier avant 03 h 00. | La lecture de la ressource du canal commence après 14 h 00 le 1er janvier, se poursuit jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et se poursuit jusqu’à 3 h 00 le 3 janvier. |

>[!NOTE]
>
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées ou complètes comme Lun/Lundi et Jan/Janvier. Vous pouvez également utiliser la notation d’_heure militaire_ (14:00) au lieu de *A.M./P.M.* (14 h 00).
