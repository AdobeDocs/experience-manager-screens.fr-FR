---
title: Attribution de canaux
seo-title: Attribution de canaux
description: Consultez cette page pour en savoir plus sur l’attribution de canaux et sur les créneaux horaires.
seo-description: Consultez cette page pour en savoir plus sur l’attribution de canaux et sur les créneaux horaires.
uuid: fe429485-dcc9-4507-864c-b04393cedeee
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 212adcd1-835b-453d-9d3e-775366abf181
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Attribution de canaux {#channel-assignment}

Cette section traite des sujets suivants :

* **Attribution d’un canal**
* **Présentation des propriétés de la boîte de dialogue Affectation de canal**
* **Créneaux horaires**

Une fois que vous avez défini un affichage, vous devez lui attribuer un canal.

Cette page vous explique comment attribuer un canal à vos affichages.

**Conditions préalables**:

* [Configuration et déploiement de Screens](configuring-screens-introduction.md)
* [Création et gestion d’écrans](creating-a-screens-project.md)
* [Création et gestion des canaux](managing-channels.md)
* [Création et gestion des emplacements](managing-locations.md)
* [Création et gestion des écrans](managing-displays.md)

## Attribution d’un canal {#assign-a-channel}

Suivez les étapes ci-dessous pour attribuer un canal à un affichage :

1. Accédez à l'affichage requis, par exemple **DemoProject** —&gt; **Locations** —&gt; **SanJose** —&gt; **StoreDisplay.**

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. Appuyez/cliquez sur **Attribuer un canal **dans la barre d’actions.

   Ou,

   Tap/click **Dashboard** and click **+Assign Channel** from the **ASSIGNED CHANNNELS** panel to open the **Channel Assignment** dialog box.

   ![screen_shot_2018-08-23at25938pm](assets/screen_shot_2018-08-23at25938pm.png)

   Vous pouvez configurer les propriétés suivantes dans la boîte de dialogue **Attribution des canaux** :

   **Rôle du canal** :

   Le rôle du canal définit le contexte de l’affichage. Le rôle est ciblé par diverses actions ; il est indépendant du canal qui remplit le rôle.

   **Canal de référence** :

   Le canal de référence vous permet de fournir une référence pour le canal souhaité, par nom ou chemin de canal.

   * **Par chemin** : vous fournissez une référence explicite à l’aide du chemin absolu du canal.
   * **par nom**: Vous saisissez le nom du canal qui sera résolu en canal réel par contexte. Cette fonction vous permet de créer la version locale d’un canal pour diffuser dynamiquement le contenu spécifique à un emplacement. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.
   **Priorité** :

   La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celle présentant la valeur la plus élevée est toujours prioritaire par rapport aux valeurs plus faibles. Par exemple, s’il existe deux canaux A et B, A ayant une priorité de 1 et B une priorité de 2, alors le canal B est affiché, car il présente une priorité supérieure à celle de A.

   La priorité d’un canal est définie sous forme numérique (1 au minimum) dans la boîte de dialogue **Attribution de canaux**, comme indiqué ci-dessus. En outre, les canaux attribués sont triés en fonction de la priorité décroissante.

   **Événements pris en charge** :

   * **Chargement initial** : charge le canal lorsque le lecteur démarre. Il peut être attribué à plusieurs canaux en combinaison avec la planification.
   * **Écran inactif** : charge lorsque l’écran est inactif. Il peut être attribué à plusieurs canaux en combinaison avec la planification.
   * **Minuteur** : il doit être défini lorsqu’une planification est fournie.
   * **Interaction de l’utilisateur** : le lecteur passera au canal spécifié s’il existe une interaction de l’utilisateur sur l’écran (tactile) dans un canal inactif et se chargera en cas de pression sur l’écran.
   **Planification** :

   La planification vous permet de fournir une description textuelle lorsque le canal doit apparaître. Il vous permet également de définir une date de début (**Actif à partir de**) et une date de fin (**Actif jusqu’à**) pour l’affichage du canal. La syntaxe de l’expression de planification est basée sur le texte de later.js et les syntaxes cron :

   * [https://bunkat.github.io/later/parsers.html#text](https://bunkat.github.io/later/parsers.html#text)
   * [https://bunkat.github.io/later/parsers.html#cron](https://bunkat.github.io/later/parsers.html#cron)
   **Afficher l’info-bulle d’attraction** :

   Afficher l’info-bulle d’attraction définit si l’info-bulle d’attraction (« *Appuyez n’importe où pour commencer* ») doit être affichée ou non lorsque le canal est en cours d’exécution.

1. Cliquez sur **Enregistrer** pour attribuer le canal créé à un affichage.

### Créneaux horaires {#dayparting}

Schedules when when combined with **Dayparting**, allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

Les créneaux horaires consistent à fractionner une journée en tranches horaires et à indiquer quel contenu diffuser à l’heure désirée. AEM Screens vous permet de planifier des canaux en termes de créneaux horaires au cours d’une journée, d’une semaine ou d’un mois en fonction des besoins.

Les exemples suivants présentent les créneaux horaires dans les canaux selon trois scénarios différents :

#### Diffusion du contenu au cours d’une même journée divisée en plusieurs créneaux horaires {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Cet exemple illustre la façon dont un restaurant utilise les créneaux horaires pour afficher le menu du petit-déjeuner, du déjeuner et du dîner.

Ici, nous divisons chaque jour en trois créneaux horaires différents, afin que le contenu du canal soit lu selon l’heure spécifiée de la journée :

| **Canal** | **Rôle** | **Priorité** | **Planification** |
|---|---|---|---|
| Menu_A | Petit déjeuner |  | après 6h00 et avant 11h00 |
| Menu_B | Déjeuner |  | après 11h00 et avant 15h00 |
| Menu_C | Dîner |  | après 15h00 et avant 20h00 |

#### Diffusion du contenu pendant un jour de la semaine {#playing-content-on-a-particular-day-of-the-week}

Cet exemple présente les créneaux horaires suivis dans un casino où un événement se produit en direct chaque week-end à partir de 20 h et jusqu’à 22 h, et les plats du jour sont disponibles pour le menu du dîner après 22 h et jusqu’à 1 h du matin.

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
   <td>21 octobre 2017 - 22 octobre 2017 <br /> après 20:00 avant 22:00</td>
  </tr>
  <tr>
   <td>SpecialsDinner</td>
   <td>Week-end</td>
   <td> </td>
   <td>21 octobre 2017 - 22 octobre 2017 <br /> après 22 heures avant 13 heures</td>
  </tr>
 </tbody>
</table>

#### Diffusion du contenu pendant un ou plusieurs mois particuliers {#playing-content-for-a-particular-month-months}

Cet exemple présente les créneaux horaires d’un magasin qui affiche sa collection d’été de juin à août, et sa collection d’automne de septembre à fin octobre.

Vous allez créer des créneaux horaires selon les mois, de sorte que le contenu du canal soit diffusé pendant les mois de l’année spécifiés.

| **Canal** | **Rôle** | **Priorité** | **Planification** |
|---|---|---|---|
| SummerCollection | Été |  | 1 juin 2017 - 31 août 2017 |
| FallCollection | Automne |  | 01 septembre 2017 - 30 octobre 2017 |

>[!NOTE]
>
>En outre, vous pouvez définir la ***priorité**de chacun des canaux.* Par exemple, si deux canaux sont définis sur le même jour et la même heure, ou sur le même mois, alors le canal dont la priorité est supérieure est diffusé en premier. La valeur de priorité minimale est de 0.

#### Diffusion de contenu pour les canaux ayant la même priorité {#playing-content-for-channels-with-same-priority}

Cet exemple présente les créneaux horaires d’un magasin qui affiche sa collection d’hiver avec la même planification pendant le mois décembre. Toutefois, puisque la priorité du canal B est définie sur 2 au cours de cette semaine, son contenu est diffusé plutôt que celui du canal A.

| **Canal** | **Rôle** | **Priorité** | **Planification** |
|---|---|---|---|
| A | Hiver | 1 | 1 décembre 2017 - 31 décembre 2017 |
| B | Noël | 2 | 24 décembre 2017 - 31 décembre 2017 |

