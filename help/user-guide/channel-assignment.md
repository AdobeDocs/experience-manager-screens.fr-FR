---
title: Attribution de canaux
description: Découvrez l’attribution de canaux et la répartition par jour.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 39%

---

# Attribution de canaux {#channel-assignment}

>[!IMPORTANT]
>Cette section décrit l’attribution et la planification des canaux pour les Feature Packs antérieurs à la version AEM 6.5.5 Screens.

Une fois que vous avez configuré un affichage, vous devez lui attribuer un canal pour afficher votre contenu.

Cette page explique comment attribuer un canal à votre affichage.

>[!NOTE]
>Vous pouvez attribuer plusieurs canaux à un affichage.

## Attribution d’un canal {#assign-a-channel}

Suivez les étapes ci-dessous pour attribuer un canal à un affichage :

1. Accédez à l’affichage requis, par exemple, . **Projet de démonstration** > **Emplacements** > **San José** > **StoreDisplay**.

   ![image](assets/screen_shot_2018-08-23at25359pm.png)

1. Sélectionner **Attribuer le canal** dans la barre d’actions.

   ou,

   Sélectionner **Tableau de bord** et sélectionnez **+Attribuer un canal** à partir du **CANAUX AFFECTÉS** pour pouvoir ouvrir le **Attribution de canaux** boîte de dialogue.

   ![image](/help/user-guide/assets/channel-assign1.png)

   Vous pouvez configurer les propriétés à partir de la boîte de dialogue **Attribution de canaux** en suivant la section ci-dessous. Consultez [Propriétés des canaux](#channel-properties) pour en savoir plus à ce propos.

## Présentation des propriétés des canaux à partir de l’attribution de canaux {#channel-properties}

### Canal de référence {#ref-channel}

Le canal de référence vous permet de fournir une référence au canal souhaité, soit par nom de canal, soit par chemin de canal.

* **par chemin** - Vous fournissez une référence explicite à l’aide du chemin d’accès absolu du canal.

* **par nom** - Vous saisissez le nom du canal qui est résolu sur un canal réel par contexte. Cette fonctionnalité vous permet de créer une version locale d’un canal pour résoudre dynamiquement le contenu spécifique à un emplacement. Par exemple, un canal portant le nom *offres du jour*, dont le contenu serait différent dans deux villes, mais avec le même rôle de canal sur tous les affichages.

### Rôle du canal {#role-channel}

Le rôle du canal définit le contexte de l’affichage. Le rôle est ciblé par différentes actions et est indépendant du canal réel qui remplit le rôle.

### Priorité {#priority-channel}

La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celle présentant la valeur la plus élevée est toujours prioritaire par rapport aux valeurs plus faibles. Par exemple, s’il existe deux canaux A et B et que A a une priorité de 1 et B une priorité de 2, alors le canal B s’affiche, car il a une priorité plus élevée que A.

>[!NOTE]
>La priorité d’un canal est définie sous forme numérique (1 au minimum) dans la boîte de dialogue **Attribution de canaux**, comme indiqué ci-dessus. En outre, les canaux attribués sont triés en fonction de la priorité décroissante.

### Événements pris en charge {#supported-events-channel}

* **Charge Initiale** - Charge le canal au démarrage du lecteur. Il peut être affecté à plusieurs canaux avec un planning.
* **Écran inactif** : se charge lorsque l’écran est inactif. Il peut être affecté à plusieurs canaux avec un planning.
* **Minuteur** - Doit être défini lorsqu’une planification est fournie.
* **Interaction utilisateur** - Le lecteur bascule sur le canal spécifié s’il y a une interaction de l’utilisateur à l’écran (toucher) dans un canal inactif et se charge lorsque l’écran est touché.

### Méthode d’interruption {#interruption-method-channel}

>[!IMPORTANT]
>
> Cette option est disponible uniquement avec <!--AEM 6.4 Feature Pack 8 or -->Pack de fonctionnalités 4 d’AEM 6.5.

En tant que personne en charge de la création de contenu, indiquez quand un canal est interrompu afin de pouvoir choisir de couper le contenu non critique, mais éventuellement de laisser le contenu important s’afficher avant de couper sa lecture en raison de la planification.

Sélectionnez l’une des options suivantes disponibles pour définir la méthode d’interruption dans la boîte de dialogue **Attribution de canaux** :

* **Immédiatement** - Chaque fois que le planning est activé ou qu’une mise à jour est reçue, vous pouvez interrompre la lecture et actualiser ou lire immédiatement le nouveau contenu.
* **À la fin de l&#39;élément actuel** - Lorsqu’un nouveau planning est activé ou qu’une mise à jour est reçue, vous pouvez éventuellement attendre la fin de la lecture de l’élément actif de la séquence. Ce n’est qu’après cela que vous pouvez actualiser ou lire le nouveau contenu.

  >[!NOTE]
  >Cette option est sélectionnée par défaut.
* **À la fin de la séquence** - Lorsqu’un nouveau planning est activé ou qu’une mise à jour est reçue, vous pouvez éventuellement attendre que la séquence entière atteigne sa fin. Ensuite, juste avant la séquence souhaitée, vous pouvez revenir au premier élément, actualiser ou lire le nouveau contenu.

  >[!NOTE]
  >L’utilisation de la deuxième ou de la troisième option peut entraîner un léger report des heures de planification définies sur l’affectation. La raison est que le lecteur attend la fin de l’élément ou de la séquence (après l’heure spécifiée) avant de s’actualiser. Le délai dépend de la durée de lecture de l’élément.

### Planification {#schedule-channel}

Le planning vous permet de fournir une description textuelle du moment où le canal doit apparaître. Il permet également de définir une date de début (**actif à partir de**) et une date de fin (**actif jusqu’au**) pour le canal à afficher.

**Afficher l’info-bulle d’attraction**

Afficher l’info-bulle d’attraction définit si l’info-bulle d’attraction («*Touchez où commencer.*») doit être affiché ou non pendant l’exécution du canal.

### Tranches horaires {#dayparting}

Horaires lorsqu’ils sont combinés avec **Partage des jours**, vous permet de définir une planification globale avec plusieurs canaux s’exécutant à des moments spécifiques de la journée et de réutiliser simultanément cette configuration pour tous vos affichages.

Cette fonctionnalité consiste à fractionner une journée en tranches horaires et à indiquer quel contenu diffuser à l’heure désirée. AEM Screens vous permet de planifier les canaux en termes de répartition par jour au cours d’un jour, d’une semaine ou d’un mois, selon vos besoins.

Les exemples suivants expliquent la répartition des jours dans les canaux dans trois scénarios différents :

#### Diffusion du contenu au cours d’une même journée divisée en plusieurs tranches horaires {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Cet exemple montre comment un restaurant utilise DayParting pour présenter son menu du petit-déjeuner, du déjeuner et du dîner.

Ici, vous divisez chaque jour en trois plages horaires différentes afin que le contenu du canal soit lu selon l’heure spécifiée de la journée :

| **Canal** | **Rôle** | **Priorité** | **Planification** |
|---|---|---|---|
| Menu_A | Petit déjeuner |  | Après 6h00 et avant 11:00 |
| Menu_B | Déjeuner |  | Après 11:00 et avant 15:00 |
| Menu_C | Dîner |  | Après 15:00 et avant 20:00 |

#### Diffusion du contenu pendant un jour donné de la semaine {#playing-content-on-a-particular-day-of-the-week}

Cet exemple montre le dayParting réalisé dans un casino où un événement en direct se produit tous les week-ends de 20h00 à 22h00 et où des plats spéciaux sont disponibles pour le menu du dîner après 22h00 à 1h00.

<table>
 <tbody>
  <tr>
   <td><strong>Canal</strong></td>
   <td><strong>Rôle</strong></td>
   <td><strong>Priorité</strong></td>
   <td><strong>Planification</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>Week-end</td>
   <td> </td>
   <td>Du 21 octobre 2017 au 22 octobre 2017 <br /> après 20 h avant 22 h</td>
  </tr>
  <tr>
   <td>SpecialsDinner</td>
   <td>Week-end</td>
   <td> </td>
   <td>Du 21 octobre 2017 au 22 octobre 2017 <br /> après 22h00 avant 1h00</td>
  </tr>
 </tbody>
</table>

#### Diffusion du contenu pendant un ou plusieurs mois particuliers {#playing-content-for-a-particular-month-months}

Cet exemple présente les tranches horaires d’un magasin qui affiche sa collection d’été de juin à août, et sa collection d’automne de septembre à fin octobre.

Ici, vous créez un Partage de jour en fonction du mois, de sorte que le contenu du canal soit lu selon les mois spécifiés de l’année.

| **Canal** | **Rôle** | **Priorité** | **Planification** |
|---|---|---|---|
| SummerCollection | Été |  | 01 juin 2017 - 31 août 2017 |
| FallCollection | Automne |  | 01 septembre 2017 - 30 octobre 2017 |

>[!NOTE]
>
>Vous pouvez également définir ***Priorité*** pour chacun des canaux. Par exemple, si deux canaux sont définis sur le même jour et la même heure, ou sur le même mois, alors le canal qui possède la priorité supérieure est diffusé en premier. La valeur minimale de la priorité peut être définie sur 0.

#### Diffusion de contenu pour les canaux ayant la même priorité {#playing-content-for-channels-with-same-priority}

Cet exemple montre le DayParting pour un magasin qui affiche sa collection d’hiver avec le même planning au mois de décembre. Toutefois, puisque la priorité du canal B est définie sur 2 au cours de cette semaine, c’est son contenu qui est diffusé plutôt que celui du canal A.

| **Canal** | **Rôle** | **Priorité** | **Planification** |
|---|---|---|---|
| A | Hiver | 1 | 01 décembre 2017 - 31 décembre 2017 |
| B | Noël | 2 | Du 24 décembre 2017 au 31 décembre 2017 |


>[!NOTE]
>
> Pour en savoir plus sur les tranches horaires, consultez les sections suivantes :
>
>* [Gestion de la périodicité pour les ressources](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [Gestion de la périodicité des ressources dans un canal](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)
