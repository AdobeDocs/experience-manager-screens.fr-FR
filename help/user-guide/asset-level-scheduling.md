---
title: Activation au niveau des ressources
seo-title: Activation au niveau des ressources
description: Consultez cette page pour apprendre comment activer une ressource spécifique dans un canal pour une période planifiée dans le fuseau horaire local du lecteur.
seo-description: Consultez cette page pour apprendre comment activer une ressource spécifique dans un canal pour une période planifiée dans le fuseau horaire local du lecteur.
feature: Authoring Screens, Asset Level Activation
role: Administrator, Developer
level: Intermediate
translation-type: ht
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: ht
source-wordcount: '1453'
ht-degree: 100%

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

>[!CAUTION]
>
>Cette fonctionnalité d’AEM Screens est disponible uniquement si vous avez installé AEM 6.3 Feature Pack 3 ou AEM 6.4 Screens Feature Pack 1.
>
>Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous disposez des autorisations nécessaires, vous pouvez le télécharger à partir de Package Share.

## Présentation {#overview}

L’***activation au niveau des ressources*** permet d’activer une ressource spécifique dans un canal pour une période planifiée dans le fuseau horaire local du lecteur. Cette option est disponible pour les images, les vidéos, les transitions, les pages et les canaux incorporés (dynamiques ou statiques).

*Par exemple*, vous souhaitez qu’une promotion spéciale s’affiche uniquement pendant la Happy Hour (de 14h00 à 17h00) les lundis et les mercredis.

Avec cette fonctionnalité, vous pouvez non seulement spécifier la date et l’heure de début et de fin, mais également un modèle de périodicité.

## Fenêtre d’activation {#single-event-playback}

La planification au niveau des ressources s’effectue en configurant l’onglet **Activation** lors de l’accès aux propriétés d’une ressource.

Suivez les étapes ci-dessous pour effectuer une planification au niveau des ressources :

1. Sélectionnez un canal et cliquez sur **Modifier** dans la barre d’actions pour ajouter ou modifier du contenu dans votre canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Pour apprendre en détail comment
   >
   >* créer un projet, voir [Création d’un projet](creating-a-screens-project.md).
   >* créer et ajouter du contenu à un canal, voir [Gestion des canaux](managing-channels.md).


1. Cliquez sur **Modifier** pour ouvrir l’éditeur de canal et sélectionnez une ressource à laquelle vous souhaitez appliquer la planification.

   ![image](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Sélectionnez la ressource et cliquez sur l’icône **Configurer** (en forme de clé à molette) en haut à gauche pour ouvrir les propriétés de l’image.

   Cliquez sur l’onglet **Activation**.

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Vous pouvez spécifier la date à l’aide des champs **Actif à partir de** et **Actif jusqu’à** du sélecteur de date.

   Si vous sélectionnez la date et l’heure dans **Actif à partir de** et **Actif jusqu’à**, la ressource s’affichera et en boucle uniquement entre cette date/heure de début et cette date/heure de fin, respectivement.

   ![image](/help/user-guide/assets/asset-activation/asset-level3.png)

## Gestion de la périodicité pour les ressources {#handling-recurrence-in-assets}

Vous pouvez planifier l’activation périodique des ressources à certains intervalles, tous les jours, toutes les semaines ou tous les mois, selon vos besoins.

Supposons que vous souhaitiez afficher une image uniquement le vendredi de 13h00 à 22h00. Vous pouvez utiliser l’onglet **Activation** pour définir l’intervalle périodique souhaité pour votre ressource.

### Tranches horaires {#day-parting}

1. Sélectionnez la ressource et cliquez sur l’icône **Configurer** (en forme de clé à molette) pour ouvrir la boîte de dialogue des propriétés.

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans la **Planification**. Votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions pour les tranches horaires {#example-one}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| avant 8 h 00 | la ressource du canal est lue avant 8 h 00 tous les jours |
| après 14 h 00 | la ressource du canal est lue après 14 h 00 tous les jours |
| après 12 h 15 et avant 12 h 45 | la ressource du canal est lue après 12 h 15 tous les jours pendant 30 minutes |
| avant 12 h 15 et après 12 h 45 | la ressource du canal est lue avant 12 h 15 et après 12 h 45 tous les jours |


>[!NOTE]
>
>Vous pouvez également utiliser la notation _sur 24 heures_ (14 h 00) au lieu de la notation *matin/après-midi* (AM/PM) (2 h 00 de l’après-midi).

### Tranches hebdomadaires {#week-parting}

1. Sélectionnez la ressource et cliquez sur l’icône **Configurer** (en forme de clé à molette) pour ouvrir la boîte de dialogue des propriétés.

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans la **Planification**. Votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions pour les tranches hebdomadaires {#example-two}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| Lun,Mer,Ven | la ressource est lue dans le canal les lundis, mercredis et vendredis |
| Lun-Jeu | la ressource est lue dans le canal du lundi au jeudi |

>[!NOTE]
>
>Vous pouvez également utiliser une notation _complète_ (c’est-à-dire lundi,mercredi,vendredi) au lieu d’une notation _abrégée_ (c’est-à-dire Lun,Mer,Ven).


### Tranches mensuelles {#month-parting}

1. Sélectionnez la ressource et cliquez sur l’icône **Configurer** (en forme de clé à molette) pour ouvrir la boîte de dialogue des propriétés.

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans la **Planification**. Votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions pour les tranches mensuelles {#example-three}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| de février,mai,août,novembre | la ressource est lue dans le canal en février, mai, août et novembre |
| de février-juillet | la ressource est lue dans le canal du mois de février à la fin du mois de juillet |

>[!NOTE]
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées ou complètes comme Lun/Lundi et Jan/Janvier.

### Combinaison de tranches {#combined-parting}

1. Sélectionnez la ressource et cliquez sur l’icône **Configurer** (en forme de clé à molette) pour ouvrir la boîte de dialogue des propriétés.

1. Après avoir saisi la date et l’heure de début et la date et l’heure de fin, vous pouvez utiliser une expression ou une version de texte naturel pour spécifier votre planification de périodicité.

   >[!NOTE]
   >Vous pouvez ignorer ou inclure les champs **Actif à partir de** et **Actif jusqu’à** et ajouter l’expression au champ Planifications, selon vos besoins.

1. Saisissez l’expression dans la **Planification**. Votre ressource s’affiche pour l’intervalle spécifique de jour et d’heure.

#### Exemples d’expressions de combinaison de tranches {#example-four}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| après 6 h et avant 18 h les lundis et mercredis de janvier à mars | la ressource est lue dans le canal entre 6 h et 18 h les lundis et mercredis, du mois de janvier à la fin du mois de mars |
| le 1er janvier après 14 h 00, ainsi que le 2 janvier et le 3 janvier avant 3 h 00 | la lecture de la ressource du canal commence après 14 h 00 le 1er janvier et se poursuit toute la journée du 2 janvier jusqu’à 3 h 00 le 3 janvier |
| les 1er et 2 janvier après 14 h 00 et le 2-3 janvier avant 3 h 00 | la lecture de la ressource du canal commence après 14 h 00 le 1er janvier, se poursuit jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et se poursuit jusqu’à 3 h 00 le 3 janvier |

>[!NOTE]
>Lors de la définition des jours de la semaine et des mois, vous pouvez utiliser les notations abrégées ou complètes comme Lun/Lundi et Jan/Janvier.  Vous pouvez également utiliser la notation _sur 24 heures_ (14 h 00) au lieu de la notation *matin/après-midi* (AM/PM) (2 h 00 de l’après-midi).


## Activation multiressource {#multi-asset-scheduling}

>[!CAUTION]
>
>La fonction d’**activation multiressource** n’est disponible que si vous avez installé AEM 6.3 Feature Pack 5 ou AEM 6.4 Feature Pack 3.

L’***activation multiressource*** permet à l’utilisateur de sélectionner plusieurs ressources et d’appliquer une planification d’exécution à toutes les ressources sélectionnées.

### Conditions préalables {#prerequisites}

Pour utiliser l’activation de plusieurs ressources, créez un projet AEM Screens avec un canal de séquence. Par exemple, le cas d’utilisation suivant montre l’implémentation de la fonctionnalité :

* Créez un projet AEM Screens intitulé **MultiAssetDemo**
* Créez un canal intitulé **MultiAssetChannel** et ajoutez du contenu au canal, comme illustré ci-dessous.

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Pour sélectionner plusieurs ressources et planifier leur affichage dans un projet AEM Screens, procédez comme suit :

1. Sélectionnez **MultiAssetChannel** et cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Sélectionnez plusieurs ressources dans l’éditeur, puis cliquez sur **Modifier l’activation** (icône en haut à gauche).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Sélectionnez la date et l’heure dans **Actif à partir de** et **Actif jusqu’à** dans la boîte de dialogue **Activation du composant**. Cliquez sur l’icône en forme de coche lorsque vous avez terminé de sélectionner les planifications.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Cliquez sur Actualiser pour vérifier les ressources auxquelles une planification multiressource est appliquée.

   >[!NOTE]
   >
   >L’icône de planification s’affiche dans l’angle supérieur droit pour les ressources ayant une activation multiressource.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

