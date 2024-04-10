---
title: Attribution de canaux - Dernier FP
description: Découvrez l’attribution de canaux et les tranches horaires.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '1458'
ht-degree: 45%

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
   >Voir [Création et gestion de projets](creating-a-screens-project.md) pour savoir comment créer un projet AEM Screens.

1. Créez un canal de séquence intitulé **Cafeteria** dans le dossier **Canaux**.

1. Sélectionnez le canal, puis cliquez sur **Modifier** dans la barre d’actions.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Par exemple, le canal **Cafeteria** affiche désormais les images suivantes :

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Créez un emplacement intitulé **SanJose** et un affichage appelé **Lobby**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Attribution d’un canal à un affichage {#assigning-channel-to-display}

Une fois la configuration du projet terminée, vous devez attribuer le canal à un affichage pour afficher le contenu.

1. Accédez à l’affichage requis, par exemple : **DemoScreens** > **Emplacements** > **SanJose** > **Lobby**.

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

1. Dans la **Planification** , sélectionnez l’option **Fenêtre d’activation** et **Planning de périodicité**.
   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Consultez la section [Propriétés des canaux](#channel-properties) pour en savoir plus sur les propriétés d’attribution de canaux.

1. Cliquez sur **Enregistrer** une fois vos préférences configurées.

### Affichage du contenu dans le lecteur Chrome {#viewing-content-output}

Cet exemple présente une sortie sur un lecteur Chrome. Une fois le canal attribué à votre écran, vous devez enregistrer l’appareil sur un lecteur.

Voir [Enregistrement de périphérique](device-registration.md) pour savoir comment enregistrer un appareil sur un lecteur AEM Screens.

Vous pouvez afficher la sortie suivante sur le lecteur de votre choix :

![new1](assets/channel-assignment/channel-assign-output.gif)

## Mode Chronologie {#timeline-view}

Une fois un canal attribué à un affichage et un planning de périodicité configuré, vous pouvez afficher la chronologie à partir du panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**.

Suivez les étapes ci-dessous pour accéder à l’affichage de la chronologie :

1. Accédez à l’affichage requis, par exemple : **DemoScreens** > **Emplacements** > **SanJose** > **Lobby**.

1. Appuyez/cliquez sur **Attribuer le canal** dans la barre d’actions.

   Ou,

   Appuyez/cliquez sur **Tableau de bord** et cliquez sur **Chronologie** dans le panneau **CANAUX ET PLANIFICATIONS AFFECTÉS**.

   ![image](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Présentation des propriétés des canaux figurant dans la boîte de dialogue Attribution des canaux {#channel-properties}

Les propriétés suivantes sont définies à partir de l’option **Paramètres** de la boîte de dialogue **Attribution de canaux**.

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Sélectionner un canal {#select-channel}

La sélection d’un canal vous permet de fournir une référence au canal souhaité, soit par nom de canal, soit par chemin de canal.

* **Par chemin** - Vous fournissez une référence explicite à l’aide du chemin absolu du canal.
* **Par nom** - Vous saisissez le nom du canal qui correspond à un canal réel en fonction du contexte. Cette fonctionnalité vous permet de créer une version locale d’un canal afin que vous puissiez résoudre dynamiquement le contenu spécifique à un emplacement. Par exemple, un canal portant le nom *offres du jour*, dont le contenu serait différent dans deux villes, mais avec le même rôle de canal sur tous les affichages.

### Rôle du canal {#role-channel}

Le rôle du canal définit le contexte de l’affichage. Le rôle est ciblé par diverses actions et est indépendant du canal qui remplit le rôle.

### Priorité {#priority-channel}

La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celle présentant la valeur la plus élevée est toujours prioritaire par rapport aux valeurs plus faibles. Par exemple, s’il existe deux canaux A et B et que A a une priorité de 1 et B une priorité de 2, alors le canal B s’affiche, car il a une priorité plus élevée que A.

>[!NOTE]
>
>La priorité d’un canal est définie sous forme numérique (1 au minimum) dans la boîte de dialogue **Attribution de canaux**, comme indiqué ci-dessus. En outre, les canaux attribués sont triés en fonction de leur priorité descendante.

### Événements pris en charge {#supported-events-channel}

* **Charge initiale** charge le canal au démarrage du lecteur. Il peut être attribué à plusieurs canaux avec une planification.
* **Écran inactif** charge lorsque l’écran est inactif. Il peut être attribué à plusieurs canaux avec une planification.
* **Minuteur** - Doit être défini lorsqu’un planning est fourni.
* **Interaction de l’utilisateur** - Le lecteur bascule vers le canal spécifié s’il y a une interaction de l’utilisateur à l’écran (tactile) dans un canal inactif et se charge lorsque l’écran est touché.

### Méthode d’interruption {#interruption-method-channel}

>[!IMPORTANT]
> Cette option est disponible uniquement avec <!--AEM 6.4 Feature Pack 8 or-->AEM 6.5 Feature Pack 4.

En tant qu’auteur de contenu, vous pouvez spécifier le moment où un canal est interrompu. Cela vous permet de choisir de couper le contenu non essentiel. Mais il vous offre également la possibilité de laisser l’important contenu lire en intégralité avant de le réduire rapidement en raison de la planification.

Sélectionnez l’une des options suivantes disponibles pour définir la méthode d’interruption dans la boîte de dialogue **Attribution de canaux** :

* **Immédiatement** - Lorsque la planification est activée ou qu’une mise à jour est reçue, vous pouvez interrompre la lecture et immédiatement actualiser ou lire le nouveau contenu.
* **Fin de l’élément actif** - Lorsqu’une nouvelle planification est activée ou qu’une mise à jour est reçue, vous pouvez éventuellement attendre la fin de la lecture de l’élément actuel dans la séquence. Ensuite, vous pouvez actualiser ou lire le nouveau contenu uniquement après cela.

  >[!NOTE]
  >Cette option est sélectionnée par défaut.

* **À la fin de la séquence** - Lorsqu’une nouvelle planification est activée ou qu’une mise à jour est reçue, vous pouvez éventuellement attendre que la séquence entière arrive à sa fin. Ensuite, juste avant la séquence souhaitée, vous pouvez revenir au premier élément, l’actualiser ou lire le nouveau contenu.

  >[!NOTE]
  >L’utilisation de la deuxième ou de la troisième option peut entraîner un léger report des heures de planification définies sur l’affectation. Cela est dû au fait que le lecteur attend la fin de l’élément ou de la séquence (après l’heure spécifiée) avant de procéder à l’actualisation. Le délai dépend de la durée de lecture de l’élément.

Les propriétés suivantes sont définies à partir de l’option **Planification** de la boîte de dialogue **Attribution de canaux**.

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Fenêtre d’activation {#activation-window}

La fenêtre d’activation vous permet de sélectionner une **Date de début** et un **Date de fin** pour afficher votre contenu.

### Planning de périodicité {#recurrence-schedule}

Le Planning de périodicité permet de définir une planification récurrente pour votre contenu. Sélectionner **+ Ajouter une planification** pour ajouter un planning de périodicité à votre canal.

>[!NOTE]
>Vous pouvez ajouter plusieurs plannings de périodicité à votre canal.
>Les plannings de périodicité s’affichent *Tranches horaires* qui vous permet de définir une planification globale avec plusieurs canaux qui s’exécutent à des moments spécifiques de la journée et de réutiliser simultanément ces canaux configurés pour tous vos affichages.

Vous pouvez configurer les options suivantes :

* **Nom** - Titre de votre planning de périodicité.
* **Répéter** - Choisissez si la planification s’exécute **Qualité**, **Hebdomadaire**, **Mensuel**, ou **Annuel**.
* **Début** - L’heure de début de votre planning.
* **Fin** - L’heure de fin de votre planning. Vous pouvez le définir par heure ou par durée.
   * **Heure** - Le planning se termine à une heure spécifiée.
   * **Durée** - Le planning s’exécute pendant une durée spécifique en heures ou en minutes.

### Tranches horaires {#dayparting}

Les tranches horaires consistent à fractionner une journée en tranches horaires et à indiquer quel contenu diffuser à l’heure désirée. AEM Screens vous permet de planifier des canaux en termes de tranches horaires au cours d’une journée, d’une semaine ou d’un mois, selon vos besoins.

Les exemples suivants présentent les tranches horaires dans les canaux selon trois scénarios différents :

#### Diffusion du contenu au cours d’une même journée divisée en plusieurs tranches horaires {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Cet exemple illustre la manière dont un restaurant utilise les tranches horaires pour afficher chaque jour le menu du petit déjeuner, du déjeuner et du dîner.

Ici, chaque jour est divisé en différents créneaux horaires, de sorte que le contenu du canal soit diffusé selon l’heure spécifiée. Définissez les propriétés suivantes du planning de périodicité pour que votre canal lise le contenu conformément à ce cas d’utilisation.

| **Nom** | **Répétition** | **Début** | **Fin** |
|---|---|---|---|
| Petit déjeuner | Quotidienne | 06:00 | 11:00 |
| Déjeuner | Quotidienne | 11:00 | 15 heures |
| Dîner | Quotidienne | 15 heures | 20 h |

#### Diffusion du contenu pendant un jour donné de la semaine {#playing-content-on-a-particular-day-of-the-week}

Cet exemple présente les tranches horaires mises en oeuvre dans un casino où un événement se produit en direct chaque week-end à partir de 20 h et jusqu’à 22 h, et les plats du jour sont disponibles pour le menu du dîner après 22 h et jusqu’à 1 h du matin.

| **Nom** | **Répétition** | **Début** | **Fin** |
|---|---|---|---|
| Week-end | Hebdomadaire : samedi et dimanche | 20 h | 22 h |
| Plats du jour | Quotidien : du lundi au vendredi | 22 h | 1:00 |

>[!NOTE]
>
>Vous pouvez également définir ***Priorité*** pour chacun des canaux. Par exemple, si deux canaux sont définis sur le même jour et la même heure, ou sur le même mois, alors le canal qui possède la priorité supérieure est diffusé en premier. La valeur minimale de priorité peut être définie sur 0.
