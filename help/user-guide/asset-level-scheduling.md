---
title: Activation au niveau des ressources
description: Découvrez comment activer une ressource spécifique dans un canal pour une période planifiée dans le fuseau horaire local du lecteur.
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
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
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permission, you can download it from Package Share. -->

## Vue d’ensemble {#overview}

***Activation au niveau des ressources*** vous permet d’activer une ressource spécifique dans un canal pour une période planifiée dans le fuseau horaire local du lecteur. Cette option est disponible pour les images, les vidéos, les transitions, les pages et les canaux incorporés (dynamiques ou statiques).

*Par exemple*, vous souhaitez qu’une promotion spéciale s’affiche uniquement pendant la Happy Hour (de 14h00 à 17h00) les lundis et les mercredis.

Avec cette fonctionnalité, vous pouvez non seulement spécifier la date et l’heure de début et de fin, mais également un modèle de périodicité.

## Fenêtre d’activation {#single-event-playback}

La planification au niveau des ressources s’effectue en configurant l’onglet **Activation** lors de l’accès aux propriétés d’une ressource.

Suivez les étapes ci-dessous pour effectuer une planification au niveau des ressources :

1. Sélectionnez un canal, puis cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Pour apprendre en détail comment
   >
   >* créer un projet, voir [Création d’un projet](creating-a-screens-project.md).
   >* créer et ajouter du contenu à un canal, voir [Gestion des canaux](managing-channels.md).

1. Sélectionner **Modifier** vous pouvez donc ouvrir l’éditeur de canal et sélectionner une ressource à laquelle vous souhaitez appliquer la planification.

   ![image](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Sélectionnez la ressource, puis cliquez sur en haut à gauche. **Configurer** (icône de clé à molette).

   Sélectionnez la variable **Activation** .

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Vous pouvez spécifier la date à l’aide des champs **Actif à partir de** et **Actif jusqu’à** du sélecteur de date.

   Si vous sélectionnez l’option **Actif à partir de** et **Actif jusqu’à** date et heure, la ressource affiche et effectue une boucle uniquement entre cette date/heure de début et cette date/heure de fin, respectivement.

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

## Gestion de la périodicité pour les ressources {#handling-recurrence-in-assets}

Vous pouvez planifier l’activation périodique des ressources à certains intervalles, tous les jours, toutes les semaines ou tous les mois, selon vos besoins.

Supposons que vous souhaitiez afficher une image uniquement le vendredi de 13 h 00 à 22 h 00. Vous pouvez utiliser l’onglet **Activation** pour définir l’intervalle périodique souhaité pour votre ressource.

### Tranches horaires {#day-parting}

1. Sélectionnez la ressource et cliquez sur **Configurer** (icône de clé à molette) pour ouvrir la boîte de dialogue des propriétés.

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans la propriété **Planification** et votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions pour les tranches horaires {#example-one}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| avant 8 h | la ressource du canal est lue avant 8 h 00 tous les jours |
| après 14 heures | la ressource du canal est lue après 14 h 00 tous les jours |
| après 12 h 15 et avant 12 h 45 | la ressource du canal est lue après 12h15 tous les jours pendant 30 minutes |
| avant 12 h 15 et après 12 h 45 | la ressource du canal est lue avant 12h15 tous les jours, puis après 12h45. |

>[!NOTE]
>
>Vous pouvez également utiliser _temps militaire_ au lieu de *A.M./P.M.* (14 h 00).

### Tranches hebdomadaires {#week-parting}

1. Sélectionnez la ressource, puis cliquez sur **Configurer** (icône de clé à molette).

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans la propriété **Planification** et votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions pour les tranches hebdomadaires {#example-two}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| `Mon,Wed,Fri` | la ressource est lue dans le canal le lundi, le mercredi et le vendredi. |
| `Mon-Thu` | la ressource est lue dans le canal du lundi au jeudi |

>[!NOTE]
>
>Vous pouvez également utiliser _full_ notation (`Monday,Wednesday,Friday`) au lieu de _short-hand_ (`Mon,Wed,Fri`).


### Tranches mensuelles {#month-parting}

1. Sélectionnez la ressource, puis cliquez sur **Configurer** (icône de clé à molette).

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans la propriété **Planification** et votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions pour les tranches mensuelles {#example-three}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| `on February,May,August,November` | la ressource est lue dans le canal en février, mai, août et novembre |
| `on February-July` | la ressource est lue dans le canal de février à fin juillet |

>[!NOTE]
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées et complètes, telles que Lun/Lundi et Jan/Janvier.

### Combinaison de tranches {#combined-parting}

1. Sélectionnez la ressource, puis cliquez sur **Configurer** (icône de clé à molette).

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans la propriété **Planification** et votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions de combinaison de tranches {#example-four}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| `after 6:00 and before 18:00 on Mon,Wed of Jan-Mar` | la ressource est lue dans le canal entre 6 h et 18 h les lundis et mercredis, du mois de janvier à la fin du mois de mars |
| `on the 1st day of January after 2:00 P.M. also on the 2nd day of January also on the 3rd day of January before 3:00 A.M.` | la lecture de la ressource du canal commence après 14 h 00 le 1er janvier et se poursuit toute la journée du 2 janvier jusqu’à 3 h 00 le 3 janvier |
| `on the 1-2 days of January after 2:00 P.M. also on the 2-3 days of January before 3:00 A.M.` | la lecture de la ressource du canal commence après 14 h 00 le 1er janvier, se poursuit jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et se poursuit jusqu’à 3 h 00 le 3 janvier |

>[!NOTE]
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées et complètes, telles que Lun/Lundi et Jan/Janvier. Vous pouvez également utiliser _temps militaire_ au lieu de *A.M./P.M.*(14 h 00).


## Activation multiressource {#multi-asset-scheduling}

<!--
>[!CAUTION]
>
>The **Multi-asset Activation** feature is only available if you have installed AEM 6.3 Feature Pack 5 or AEM 6.4 Feature Pack 3. -->

***Activation multiressource*** permet à l’utilisateur de sélectionner plusieurs ressources et d’appliquer une planification de lecture à toutes les ressources sélectionnées.

### Prérequis {#prerequisites}

Pour utiliser l’activation de plusieurs ressources, créez un projet AEM Screens avec un canal de séquence. Par exemple, le cas d’utilisation suivant montre l’implémentation de la fonctionnalité :

* Créez un projet AEM Screens intitulé **MultiAssetDemo**.
* Créez un canal intitulé **MultiAssetChannel** et ajoutez du contenu au canal, comme illustré dans la figure ci-dessous.

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Pour sélectionner plusieurs ressources et planifier leur affichage dans un projet AEM Screens, procédez comme suit :

1. Sélectionner **MultiAssetChannel**, puis sélectionnez **Modifier** dans la barre d’actions.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Sélectionnez plusieurs ressources dans l’éditeur, puis sélectionnez **Modifier l’activation** (icône en haut à gauche).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Sélectionnez la date et l’heure dans **Actif à partir de** et **Actif jusqu’à** dans la boîte de dialogue **Activation du composant**. Sélectionnez l’icône en forme de coche lorsque vous avez terminé de sélectionner les plannings.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Sélectionnez Actualiser pour vérifier les ressources auxquelles une planification multiressource est appliquée.

   >[!NOTE]
   >
   >L’icône de planification s’affiche dans le coin supérieur droit pour les ressources qui disposent d’une activation multiressource.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## Remplacement global pour une heure de début universelle {#global-override-scheduling}

***Remplacement global pour une heure de début universelle*** est un paramètre qui permet à l’auteur de contenu de définir la lecture d’une image ou d’une ressource vidéo selon une heure spécifique. Le paramètre d’heure/de fuseau horaire d’un lecteur individuel n’est pas utilisé.

En règle générale, la lecture est déterminée par l’heure locale d’un lecteur donné, mais grâce au remplacement global, une heure de début spécifique et universelle peut être utilisée pour lancer la lecture de la ressource.

Cela permet à l’auteur de contenu de désigner la lecture d’une ressource spécifique comme ayant lieu à une date/heure spécifique, indépendamment de l’horloge locale, sur les lecteurs auxquels le contenu est affecté.

Le remplacement global pour une heure de début universelle est effectué en configurant l’onglet **Activation** lors de l’accès aux propriétés d’une ressource. Suivez les étapes ci-dessous pour effectuer un remplacement global pour la planification des ressources :

1. Sélectionnez un canal, puis cliquez sur **Modifier** dans la barre d’actions afin de pouvoir ajouter ou modifier du contenu dans votre canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. Sélectionnez **Modifier**.
1. Dans l’éditeur de canal, sélectionnez une ressource dont vous souhaitez appliquer le planning.

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. Pour un remplacement global, saisissez l’heure d’activation dans la variable **Remplacement du fuseau horaire** pour la ressource. Si vous ne saisissez rien dans cette zone, le fuseau horaire appliqué correspond au fuseau horaire du lecteur.


