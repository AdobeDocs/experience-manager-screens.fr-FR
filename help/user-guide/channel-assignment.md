---
title: Attribution de canaux
description: Découvrez l’attribution de canaux et les tranches horaires.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 34%

---

# Attribution de canaux {#channel-assignment}

>[!IMPORTANT]
>Cette section décrit l’attribution et la planification des canaux pour les Feature Packs antérieurs à la version AEM 6.5.5 Screens.

Lorsque vous avez configuré un affichage, affectez un canal à un affichage pour afficher votre contenu.

Cette page explique comment attribuer un canal à votre affichage.

>[!NOTE]
>Vous pouvez attribuer plusieurs canaux à un affichage.

## Attribution d’un canal {#assign-a-channel}

Suivez les étapes ci-dessous pour attribuer un canal à un affichage :

1. Accédez à l’affichage requis, par exemple : **DemoProject** > **Emplacements** > **SanJose** > **StoreDisplay**.

   ![image](assets/screen_shot_2018-08-23at25359pm.png)

1. Cliquez sur **Attribuer le canal** dans la barre d’actions.

   ou

   Cliquez sur **Tableau de bord** et cliquez sur **+Attribuer le canal** de la **CANAUX ATTRIBUÉS** pour ouvrir le panneau **Attribution de canaux** de la boîte de dialogue

   ![image](/help/user-guide/assets/channel-assign1.png)

   Vous pouvez configurer les propriétés à partir de la boîte de dialogue **Attribution de canaux** en suivant la section ci-dessous. Voir [Propriétés du canal](#channel-properties) pour plus d’informations sur les propriétés des canaux.

## Présentation des propriétés des canaux à partir de l’attribution de canaux {#channel-properties}

### Canal de référence {#ref-channel}

Canal de référence vous permet de fournir une référence au canal souhaité, soit par nom de canal, soit par chemin d’accès au canal.

* **par chemin** - Vous fournissez une référence explicite à l’aide du chemin absolu du canal.

* **par nom** - Vous saisissez le nom du canal qui correspond à un canal réel en fonction du contexte. Cette fonctionnalité vous permet de créer une version locale d’un canal afin de résoudre dynamiquement le contenu spécifique à un emplacement. Par exemple, un canal portant le nom *offres du jour*, dont le contenu serait différent dans deux villes, mais avec le même rôle de canal sur tous les affichages.

### Rôle du canal {#role-channel}

Le rôle du canal définit le contexte de l’affichage. Le rôle est ciblé par diverses actions et est indépendant du canal qui remplit le rôle.

### Priorité {#priority-channel}

La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celle présentant la valeur la plus élevée est toujours prioritaire par rapport aux valeurs plus faibles. Par exemple, s’il existe deux canaux A et B et que A a une priorité de 1 et B une priorité de 2, alors le canal B s’affiche, car il a une priorité plus élevée que A.

>[!NOTE]
>La priorité d’un canal est définie sous forme numérique (1 au minimum) dans la boîte de dialogue **Attribution de canaux**, comme indiqué ci-dessus. En outre, les canaux attribués sont triés en fonction de leur priorité descendante.

### Événements pris en charge {#supported-events-channel}

* **Charge initiale** charge le canal au démarrage du lecteur. Il peut être attribué à plusieurs canaux avec une planification.
* **Écran inactif** charge lorsque l’écran est inactif. Il peut être attribué à plusieurs canaux avec une planification.
* **Minuteur** - Doit être défini lorsqu’un planning est fourni.
* **Interaction de l’utilisateur** - Le lecteur bascule vers le canal spécifié s’il y a une interaction de l’utilisateur à l’écran (tactile) dans un canal inactif et se charge lorsque l’écran est touché.

### Méthode d’interruption {#interruption-method-channel}

>[!IMPORTANT]
>
> Cette option est disponible uniquement avec <!--AEM 6.4 Feature Pack 8 or -->AEM 6.5 Feature Pack 4.

En tant qu’auteur de contenu, spécifiez le moment où un canal est interrompu afin que vous puissiez choisir de couper le contenu non critique, mais éventuellement de laisser la lecture du contenu important avant de l’interrompre en raison de la planification.

Cliquez sur l’une des options suivantes disponibles pour définir la méthode d’interruption à partir de la variable **Attribution de canaux** boîte de dialogue :

* **Immédiatement** - Chaque fois que la planification est activée ou qu’une mise à jour est reçue, vous pouvez interrompre la lecture et immédiatement actualiser ou lire le nouveau contenu.
* **À la fin de l’élément actif** - Lorsqu’une nouvelle planification est activée ou qu’une mise à jour est reçue, vous pouvez éventuellement attendre la fin de la lecture de l’élément actuel dans la séquence. Ce n’est qu’après cela que vous pouvez actualiser ou lire le nouveau contenu.

  >[!NOTE]
  >Cette option est sélectionnée par défaut.
* **À la fin de la séquence** - Lorsqu’une nouvelle planification est activée ou qu’une mise à jour est reçue, vous pouvez éventuellement attendre que la séquence entière arrive à sa fin. Ensuite, juste avant la séquence souhaitée, vous pouvez revenir au premier élément, l’actualiser ou lire le nouveau contenu.

  >[!NOTE]
  >L’utilisation de la deuxième ou de la troisième option peut entraîner un léger report des heures de planification définies sur l’affectation. Cela est dû au fait que le lecteur attend la fin de l’élément ou de la séquence (après l’heure spécifiée) avant de procéder à l’actualisation. Le délai dépend de la durée de lecture de l’élément.

### Planification {#schedule-channel}

La planification vous permet de fournir une description textuelle du moment où le canal doit apparaître. Il permet également de définir une date de début (**actif depuis**) et une date de fin (**actif jusqu’à**) pour le canal à afficher.

**Afficher l’info-bulle d’attraction**

Afficher l’info-bulle d’attraction définit si l’info-bulle d’attraction (&quot;*Appuyez n’importe où pour commencer.*&quot;) doit s’afficher ou non pendant l’exécution du canal.

### Tranches horaires {#dayparting}

Planifications lorsque combinées avec **Tranches horaires**, vous permet de définir une planification globale avec plusieurs canaux qui s’exécutent à des moments spécifiques de la journée et de réutiliser simultanément ces canaux pour tous vos affichages.

Cette fonctionnalité consiste à fractionner une journée en tranches horaires et à indiquer quel contenu diffuser à l’heure désirée. AEM Screens vous permet de planifier des canaux en termes de tranches horaires au cours d’un jour, d’une semaine ou d’un mois, selon vos besoins.

Les exemples suivants présentent les tranches horaires dans les canaux selon trois scénarios différents :

#### Diffusion du contenu au cours d’une même journée divisée en plusieurs tranches horaires {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Cet exemple illustre la manière dont un restaurant utilise les tranches horaires pour afficher le menu du petit déjeuner, du déjeuner et du dîner.

Vous divisez chaque jour en trois tranches horaires, de sorte que le contenu du canal soit diffusé en fonction de l’heure de la journée :

| **Canal** | **Rôle** | **Priorité** | **Planification** |
|---|---|---|---|
| Menu_A | Petit déjeuner |  | Après 6 h et avant 11 h |
| Menu_B | Déjeuner |  | Après 11 h et avant 15 h |
| Menu_C | Dîner |  | Après 15 h et avant 20 h |

#### Diffusion du contenu pendant un jour donné de la semaine {#playing-content-on-a-particular-day-of-the-week}

Cet exemple présente les tranches horaires suivies dans un casino où un événement se produit en direct chaque week-end à partir de 20 h et jusqu’à 22 h, et les plats du jour sont disponibles pour le menu du dîner après 22 h et jusqu’à 1 h du matin.

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
   <td>21 octobre 2017 - 22 octobre 2017 <br /> après 20 h avant 22 h</td>
  </tr>
  <tr>
   <td>SpecialsDinner</td>
   <td>Week-end</td>
   <td> </td>
   <td>21 octobre 2017 - 22 octobre 2017 <br /> après 22 h avant 1 h</td>
  </tr>
 </tbody>
</table>

#### Diffusion du contenu pendant un ou plusieurs mois particuliers {#playing-content-for-a-particular-month-months}

Cet exemple présente les tranches horaires d’un magasin qui affiche sa collection d’été de juin à août, et sa collection d’automne de septembre à fin octobre.

Vous créez ici des tranches horaires par mois, de sorte que le contenu du canal soit diffusé pendant les mois de l’année spécifiés.

| **Canal** | **Rôle** | **Priorité** | **Planification** |
|---|---|---|---|
| SummerCollection | Été |  | 1er juin 2017 - 31 août 2017 |
| FallCollection | Automne |  | 1er septembre 2017 - 30 octobre 2017 |

>[!NOTE]
>
>Vous pouvez également définir ***Priorité*** pour chacun des canaux. Par exemple, si deux canaux sont définis sur le même jour et la même heure, ou sur le même mois, alors le canal qui possède la priorité supérieure est diffusé en premier. La valeur minimale de priorité peut être définie sur 0.

#### Diffusion de contenu pour les canaux ayant la même priorité {#playing-content-for-channels-with-same-priority}

Cet exemple présente les tranches horaires d’un magasin qui affiche sa collection d’hiver avec la même planification pendant le mois de décembre. Toutefois, puisque la priorité du canal B est définie sur 2 au cours de cette semaine, c’est son contenu qui est diffusé plutôt que celui du canal A.

| **Canal** | **Rôle** | **Priorité** | **Planification** |
|---|---|---|---|
| A | Hiver | 1 | 1er décembre 2017 - 31 décembre 2017 |
| B | Noël | 2 | 24 décembre 2017 - 31 décembre 2017 |


>[!NOTE]
>
> Pour en savoir plus sur les tranches horaires, consultez les sections ci-dessous :
>
>* [Gestion de la périodicité pour les ressources](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [Gestion de la périodicité des ressources dans un canal](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)
