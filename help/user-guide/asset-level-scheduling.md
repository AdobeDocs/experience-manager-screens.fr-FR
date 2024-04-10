---
title: Activation au niveau des ressources
description: Découvrez comment activer une ressource spécifique dans un canal pour une période planifiée dans le fuseau horaire local du lecteur.
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 54%

---

# Activation au niveau des ressources {#asset-level-scheduling}

Cette page décrit l’activation au niveau des ressources utilisées dans les canaux.

Cette section aborde les sujets suivants :

* Présentation
* Fenêtre d’activation
* Lecture d’un événement unique
* Gestion de la périodicité pour les ressources
   * Tranches horaires
   * Tranches hebdomadaires
   * Tranches mensuelles
   * Combinaison de tranches
* Activation multiressource
* Remplacement global pour une heure de début universelle

<!-- REFERS TO ARCHIVED VERSIONS THAT ADOBE NO LONGER SUPPORTS>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, you must contact Adobe Support and request access. When you have permission, you can download it from Package Share. -->

## Vue d’ensemble {#overview}

***Activation au niveau des ressources*** permet d’activer une ressource spécifique dans un canal pendant une période planifiée dans le fuseau horaire local du lecteur. Cette option est disponible pour les images, les vidéos, les transitions, les pages et les canaux incorporés (dynamiques ou statiques).

*Par exemple*, vous souhaitez qu’une promotion spéciale s’affiche uniquement pendant la Happy Hour (de 14h00 à 17h00) les lundis et les mercredis.

Avec cette fonctionnalité, vous pouvez non seulement spécifier la date et l’heure de début et de fin, mais également un modèle de périodicité.

## Fenêtre d’activation {#single-event-playback}

La planification au niveau des ressources s’effectue en configurant l’onglet **Activation** lors de l’accès aux propriétés d’une ressource.

Suivez les étapes ci-dessous pour effectuer une planification au niveau des ressources :

1. Sélectionnez un canal, puis sélectionnez **Modifier** à partir de la barre d’actions.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Pour apprendre en détail comment
   >
   >* créer un projet, voir [Création d’un projet](creating-a-screens-project.md).
   >* créer et ajouter du contenu à un canal, voir [Gestion des canaux](managing-channels.md).

1. Sélectionner **Modifier** vous pouvez donc ouvrir l’éditeur de canal et sélectionner une ressource à laquelle appliquer la planification.

   ![image](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Sélectionnez la ressource, puis sélectionnez en haut à gauche. **Configurer** (icône clé à molette).

   Sélectionner le **Activation** onglet.

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Vous pouvez spécifier la date à l’aide des champs **Actif à partir de** et **Actif jusqu’à** du sélecteur de date.

   Si vous sélectionnez **Actif depuis** et **Actif jusqu’au** date et heure, la ressource s’affiche et effectue uniquement une boucle entre ces date et heure de début et de fin, respectivement.

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

## Gestion de la périodicité pour les ressources {#handling-recurrence-in-assets}

Vous pouvez planifier l’activation périodique des ressources à certains intervalles, tous les jours, toutes les semaines ou tous les mois, selon vos besoins.

Supposons que vous souhaitiez afficher une image uniquement le vendredi, de 13 h à 22 h. Vous pouvez utiliser l’onglet **Activation** pour définir l’intervalle périodique souhaité pour votre ressource.

### Tranches horaires {#day-parting}

1. Sélectionnez la ressource, puis sur . **Configurer** (icône clé à molette) pour ouvrir la boîte de dialogue des propriétés.

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
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

>[!NOTE]
>
>Vous pouvez également utiliser _temps militaire_ notation (14:00) au lieu de *A.M./P.M.* (14 H).

### Tranches hebdomadaires {#week-parting}

1. Sélectionnez la ressource, puis sélectionnez **Configurer** (icône clé à molette).

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans le champ **Planification** et votre ressource s’affiche pour l’intervalle de jour et d’heure spécifique.

#### Exemples d’expressions pour les tranches hebdomadaires {#example-two}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| `Mon,Wed,Fri` | la ressource est lue dans le canal à partir du lundi, du mercredi et du vendredi |
| `Mon-Thu` | la ressource est lue dans le canal du lundi au jeudi |

>[!NOTE]
>
>Vous pouvez également utiliser _plein_ notation (`Monday,Wednesday,Friday`) au lieu de _de courte main_ (`Mon,Wed,Fri`).


### Tranches mensuelles {#month-parting}

1. Sélectionnez la ressource, puis sélectionnez **Configurer** (icône clé à molette).

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans le champ **Planification** et votre ressource s’affiche pour l’intervalle de jour et d’heure spécifique.

#### Exemples d’expressions pour les tranches mensuelles {#example-three}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| `on February,May,August,November` | la ressource est lue sur le canal en février, mai, août et novembre |
| `on February-July` | la ressource est lue dans le canal de février à fin juillet |

>[!NOTE]
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées et nom complet, telles que Lun/Lundi et Janvier/Janvier.

### Combinaison de tranches {#combined-parting}

1. Sélectionnez la ressource, puis sélectionnez **Configurer** (icône clé à molette).

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans le champ **Planification** et votre ressource s’affiche pour l’intervalle de jour et d’heure spécifique.

#### Exemples d’expressions de combinaison de tranches {#example-four}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| `after 6:00 and before 18:00 on Mon,Wed of Jan-Mar` | la ressource est lue dans le canal entre 6 h et 18 h les lundis et mercredis, du mois de janvier à la fin du mois de mars |
| `on the 1st day of January after 2:00 P.M. also on the 2nd day of January also on the 3rd day of January before 3:00 A.M.` | la lecture de la ressource dans le canal commence après 14 h 00 le 1er janvier et se poursuit toute la journée le 2 janvier jusqu’à 3 h 00 le 3 janvier |
| `on the 1-2 days of January after 2:00 P.M. also on the 2-3 days of January before 3:00 A.M.` | la ressource sur le canal démarre le lecteur après 14 h 00 le 1er janvier, continue la lecture jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et continue jusqu’à 3 h 00 le 3 janvier |

>[!NOTE]
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées et nom complet, telles que Lun/Lundi et Janvier/Janvier. Vous pouvez également utiliser _temps militaire_ notation (14:00) au lieu de *A.M./P.M.*(14 H).


## Activation multiressource {#multi-asset-scheduling}

<!--
>[!CAUTION]
>
>The **Multi-asset Activation** feature is only available if you have installed AEM 6.3 Feature Pack 5 or AEM 6.4 Feature Pack 3. -->

***Activation multi-ressource*** permet de sélectionner plusieurs ressources et d’appliquer un planning de lecture à toutes les ressources sélectionnées.

### Prérequis {#prerequisites}

Pour utiliser l’activation de plusieurs ressources, créez un projet AEM Screens avec un canal de séquence. Par exemple, le cas d’utilisation suivant montre l’implémentation de la fonctionnalité :

* Créez un projet AEM Screens appelé . **Démonstration de plusieurs ressources**.
* Créez un canal intitulé **MultiAssetChannel** et ajoutez du contenu au canal, comme illustré dans la figure ci-dessous.

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Pour sélectionner plusieurs ressources et planifier leur affichage dans un projet AEM Screens, procédez comme suit :

1. Sélectionner **MultiAssetChannel**, puis sélectionnez **Modifier** à partir de la barre d’actions.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Sélectionnez plusieurs ressources dans l’éditeur, puis sélectionnez **Modifier l’activation** (icône en haut à gauche).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Sélectionnez la date et l’heure dans **Actif à partir de** et **Actif jusqu’à** dans la boîte de dialogue **Activation du composant**. Cochez l’icône lorsque vous avez terminé de sélectionner les plannings.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Sélectionnez Actualiser pour vérifier les ressources auxquelles la planification multi-ressources est appliquée.

   >[!NOTE]
   >
   >L’icône de planning est visible dans le coin supérieur droit pour les ressources qui ont une activation multi-ressource.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## Remplacement global pour une heure de début universelle {#global-override-scheduling}

***Remplacement global pour une heure de début universelle*** est un paramètre qui permet à l’auteur de contenu de définir la lecture d’une image ou d’une ressource vidéo selon une heure spécifique. Le paramètre d’heure/de fuseau horaire d’un lecteur individuel n’est pas utilisé.

En règle générale, la lecture est déterminée par l’heure locale d’un lecteur donné, mais grâce au remplacement global, une heure de début spécifique et universelle peut être utilisée pour lancer la lecture de la ressource.

Cela permet à l’auteur de contenu de désigner la lecture d’une ressource spécifique comme ayant lieu à une date/heure spécifique, indépendamment de l’horloge locale, sur les lecteurs auxquels le contenu est affecté.

Le remplacement global pour une heure de début universelle est effectué en configurant l’onglet **Activation** lors de l’accès aux propriétés d’une ressource. Suivez les étapes ci-dessous pour effectuer un remplacement global pour la planification des ressources :

1. Sélectionnez un canal, puis sélectionnez **Modifier** à partir de la barre d’actions afin que vous puissiez ajouter ou modifier du contenu dans votre canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. Sélectionnez **Modifier**.
1. Dans l’éditeur de canal, sélectionnez une ressource dont vous souhaitez appliquer le planning.

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. Pour un remplacement global, saisissez l’heure d’activation dans le champ **Remplacement du fuseau horaire** pour la ressource. Si vous ne saisissez rien dans cette zone, le fuseau horaire appliqué correspond à celui du lecteur.


