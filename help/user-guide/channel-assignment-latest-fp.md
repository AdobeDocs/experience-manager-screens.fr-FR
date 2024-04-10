---
title: Attribution de canaux - Dernier FP
description: Découvrez l’attribution de canaux et le partage des journées.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 47%

---

# Attribution de canaux {#channel-assignment}

>[!IMPORTANT]
>
>Cette section décrit l’attribution et la planification des canaux pour le Feature Pack AEM Screens 6.5.5 et versions ultérieures.

Une fois que vous avez configuré un affichage, vous devez lui attribuer un canal pour afficher votre contenu.

Cette page montre l’attribution d’un canal à votre affichage, les propriétés du canal et les tranches horaires.

>[!NOTE]
>
>Vous pouvez attribuer plusieurs canaux à un affichage.


## Attribution d’un canal {#assign-a-channel-new-release}

Procédez comme indiqué dans les sections ci-dessous pour créer un projet AEM Screens et attribuer un canal à un affichage.

### Création d’un projet AEM Screens et de canaux {#creating-project}

Pour configurer un projet et un canal, procédez comme suit :

1. Créez un projet AEM Screens intitulé **DemoScreens**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Consultez [Création et gestion des projets](creating-a-screens-project.md) pour savoir comment créer un projet AEM Screens.

1. Créez un canal de séquence intitulé **Cafeteria** dans le dossier **Canaux**.

1. Sélectionnez le canal, puis sélectionnez **Modifier** à partir de la barre d’actions.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Par exemple, le canal **Cafeteria** affiche désormais les images suivantes :

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Créez un emplacement intitulé **SanJose** et un affichage appelé **Lobby**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Attribution d’un canal à un affichage {#assigning-channel-to-display}

Une fois la configuration du projet terminée, vous devez attribuer le canal à un affichage pour afficher le contenu.

1. Accédez à l’affichage requis, par exemple, . **DémoScreens** > **Emplacements** > **San José** > **Hall**.

1. Appuyez/cliquez sur **Attribuer le canal** dans la barre d’actions.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Ou,

   Appuyez/cliquez sur **Tableau de bord** dans la barre d’actions et cliquez sur **+Attribuer le canal** dans le panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. La boîte de dialogue **Attribution de canaux** s’ouvre.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. L’option **Paramètres** permet de choisir le canal **par chemin** ou **par nom**, et d’entrer le **rôle du canal**, la **priorité**, les **événements pris en charge** ainsi que les **méthodes d’interruption**. Vous pouvez également activer l’info-bulle d’attraction à partir de cette boîte de dialogue.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Consultez la section [Propriétés des canaux](#channel-properties) pour en savoir plus sur les propriétés d’attribution de canaux.

1. À partir du **Planification** , sélectionnez **Fenêtre d’activation** et **Planning de récurrence**.
   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Consultez la section [Propriétés des canaux](#channel-properties) pour en savoir plus sur les propriétés d’attribution de canaux.

1. Cliquez sur **Enregistrer** une fois vos préférences configurées.

### Affichage du contenu dans le lecteur Chrome {#viewing-content-output}

Cet exemple présente une sortie sur un lecteur Chrome. Une fois le canal attribué à votre écran, vous devez enregistrer l’appareil sur un lecteur.

Voir [Enregistrement des appareils](device-registration.md) pour savoir comment enregistrer un appareil sur un lecteur AEM Screens.

Vous pouvez afficher la sortie suivante en fonction du lecteur de votre choix :

![new1](assets/channel-assignment/channel-assign-output.gif)

## Mode Chronologie {#timeline-view}

Une fois un canal attribué à un affichage et un planning de périodicité configuré, vous pouvez afficher la chronologie à partir du panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**.

Suivez les étapes ci-dessous pour accéder à l’affichage de la chronologie :

1. Accédez à l’affichage requis, par exemple, . **DémoScreens** > **Emplacements** > **San José** > **Hall**.

1. Appuyez/cliquez sur **Attribuer le canal** dans la barre d’actions.

   Ou,

   Appuyez/cliquez sur **Tableau de bord** et cliquez sur **Chronologie** dans le panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**.

   ![image](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Présentation des propriétés des canaux figurant dans la boîte de dialogue Attribution des canaux {#channel-properties}

Les propriétés suivantes sont définies à partir de l’option **Paramètres** de la boîte de dialogue **Attribution de canaux**.

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Sélectionner un canal {#select-channel}

La sélection d’un canal vous permet de fournir une référence au canal souhaité, soit par nom de canal, soit par chemin de canal.

* **Par chemin** - Vous fournissez une référence explicite à l’aide du chemin d’accès absolu du canal.
* **Par nom** - Vous saisissez le nom du canal qui est résolu sur un canal réel par contexte. Cette fonctionnalité vous permet de créer une version locale d’un canal afin de résoudre dynamiquement le contenu spécifique à un emplacement. Par exemple, un canal portant le nom *offres du jour*, dont le contenu serait différent dans deux villes, mais avec le même rôle de canal sur tous les affichages.

### Rôle du canal {#role-channel}

Le rôle du canal définit le contexte de l’affichage. Le rôle est ciblé par différentes actions et est indépendant du canal réel qui remplit le rôle.

### Priorité {#priority-channel}

La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celle présentant la valeur la plus élevée est toujours prioritaire par rapport aux valeurs plus faibles. Par exemple, s’il existe deux canaux A et B et que A a une priorité de 1 et B une priorité de 2, alors le canal B s’affiche, car il a une priorité plus élevée que A.

>[!NOTE]
>
>La priorité d’un canal est définie sous forme numérique (1 au minimum) dans la boîte de dialogue **Attribution de canaux**, comme indiqué ci-dessus. En outre, les canaux attribués sont triés en fonction de la priorité décroissante.

### Événements pris en charge {#supported-events-channel}

* **Charge Initiale** - Charge le canal au démarrage du lecteur. Il peut être affecté à plusieurs canaux avec un planning.
* **Écran inactif** : se charge lorsque l’écran est inactif. Il peut être affecté à plusieurs canaux avec un planning.
* **Minuteur** - Doit être défini lorsqu’une planification est fournie.
* **Interaction utilisateur** - Le lecteur bascule sur le canal spécifié s’il y a une interaction de l’utilisateur à l’écran (toucher) dans un canal inactif et se charge lorsque l’écran est touché.

### Méthode d’interruption {#interruption-method-channel}

>[!IMPORTANT]
> Cette option est disponible uniquement avec <!--AEM 6.4 Feature Pack 8 or-->Pack de fonctionnalités 4 d’AEM 6.5.

En tant qu’auteur de contenu, vous pouvez spécifier le moment où un canal est interrompu. Cela permet de choisir de couper le contenu non critique. Mais elle vous donne également la possibilité de laisser le contenu important être lu en entier avant de le couper à cause de la planification.

Sélectionnez l’une des options suivantes disponibles pour définir la méthode d’interruption dans la boîte de dialogue **Attribution de canaux** :

* **Immédiatement** - Chaque fois que le planning est activé ou qu’une mise à jour est reçue, vous pouvez interrompre la lecture et actualiser ou lire immédiatement le nouveau contenu
* **Fin de l&#39;élément actif** - Lorsqu’un nouveau planning est activé ou qu’une mise à jour est reçue, vous pouvez éventuellement attendre la fin de la lecture de l’élément actif de la séquence. Ensuite, vous pourrez uniquement actualiser ou lire le nouveau contenu.

  >[!NOTE]
  >Cette option est sélectionnée par défaut.

* **À la fin de la séquence** - Lorsqu’un nouveau planning est activé ou qu’une mise à jour est reçue, vous pouvez éventuellement attendre que la séquence entière atteigne sa fin. Ensuite, juste avant la séquence souhaitée, vous pouvez revenir au premier élément, actualiser ou lire le nouveau contenu.

  >[!NOTE]
  >L’utilisation de la deuxième ou de la troisième option peut entraîner un léger report des heures de planification définies sur l’affectation. La raison est que le lecteur attend la fin de l’élément ou de la séquence (après l’heure spécifiée) avant de s’actualiser. Le délai dépend de la durée de lecture de l’élément.

Les propriétés suivantes sont définies à partir de l’option **Planification** de la boîte de dialogue **Attribution de canaux**.

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Fenêtre d’activation {#activation-window}

La fenêtre d’activation permet de sélectionner une **Date de début** et un **Date de fin** pour afficher votre contenu.

### Planning de périodicité {#recurrence-schedule}

La planification de récurrences vous permet de définir une planification de récurrences pour votre contenu. Sélectionner **+ Ajouter un planning** pour ajouter une planification de récurrences à votre canal.

>[!NOTE]
>Vous pouvez ajouter plusieurs plannings de périodicité à votre canal.
>Les plannings de périodicité introduisent *Partage des jours* vous pouvez ainsi définir une planification globale avec plusieurs canaux s’exécutant à des moments spécifiques de la journée et réutiliser simultanément cette configuration pour tous vos affichages.

Vous pouvez configurer les options suivantes :

* **Nom** - Titre de votre planification de récurrences.
* **Répéter** - Choisissez si le planning s’exécute **Quotidienne**, **Hebdomadaire**, **Mensuel**, ou **Annuel**.
* **Démarrer** - Heure de début de votre planning.
* **Fin** - Heure de fin de votre planning. Vous pouvez le définir par heure ou par durée.
   * **Heure** - Le planning se termine à une heure spécifiée.
   * **Durée** - Le planning s’exécute pendant une durée spécifique, en heures ou minutes.

### Tranches horaires {#dayparting}

Le Partage de journée consiste à fractionner une journée en plages horaires et à spécifier le contenu lu à l’heure souhaitée. AEM Screens vous permet de planifier les canaux en termes de Partage de jour au cours d’un jour, d’une semaine ou d’un mois, selon vos besoins.

Les exemples suivants présentent les tranches horaires dans les canaux selon trois scénarios différents :

#### Diffusion du contenu au cours d’une même journée divisée en plusieurs tranches horaires {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Cet exemple montre comment un restaurant utilise DayParting pour présenter son menu du petit-déjeuner, du déjeuner et du dîner tous les jours.

Ici, chaque jour est divisé en différents créneaux horaires, de sorte que le contenu du canal soit lu selon l’heure spécifiée de la journée. Définissez les propriétés suivantes du planning de périodicité pour que votre canal lise le contenu conformément à ce cas d’utilisation.

| **Nom** | **Répétition** | **Début** | **Fin** |
|---|---|---|---|
| Petit déjeuner | Quotidienne | 06:00 | 11:00 |
| Déjeuner | Quotidienne | 11:00 | 15:00 |
| Dîner | Quotidienne | 15:00 | 20 H |

#### Diffusion du contenu pendant un jour donné de la semaine {#playing-content-on-a-particular-day-of-the-week}

Cet exemple montre le DayParting implémenté dans un casino où un événement en direct se produit tous les week-ends de 20h00 à 22h00 et où des plats spéciaux sont disponibles pour le menu du dîner après 22h00 à 1h00.

| **Nom** | **Répétition** | **Début** | **Fin** |
|---|---|---|---|
| Week-end | Hebdomadaire : samedi et dimanche | 20 H | 22 H |
| Plats du jour | Tous les jours : du lundi au vendredi | 22 H | 01:00 |

>[!NOTE]
>
>Vous pouvez également définir ***Priorité*** pour chacun des canaux. Par exemple, si deux canaux sont définis sur le même jour et la même heure, ou sur le même mois, alors le canal qui possède la priorité supérieure est diffusé en premier. La valeur minimale de la priorité peut être définie sur 0.
