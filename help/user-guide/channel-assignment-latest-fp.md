---
title: Attribution de canaux - Dernier FP
seo-title: Attribution de canaux - Dernier FP
description: Suivez cette page pour en savoir plus sur l'affectation des Canaux et le partage de journée.
translation-type: tm+mt
source-git-commit: 421174dba8a5a7c39bffcaa2dddb54939eeba3bc
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 77%

---


# Attribution de canaux {#channel-assignment}

>[!IMPORTANT]
>Cette section décrit l&#39;affectation et la planification des canaux pour AEM 6.5.5 Screens Feature Pack et versions ultérieures.

Une fois que vous avez configuré un affichage, vous devez lui attribuer un canal pour afficher votre contenu.

Cette page montre l&#39;affectation d&#39;un canal à votre affichage, la compréhension des propriétés du canal et la division de journée.

>[!NOTE]
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

1. Sélectionnez le canal et cliquez sur **Modifier** dans la barre d’actions pour ajouter du contenu à votre canal.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Par exemple, le canal **Cafeteria** affiche désormais les images suivantes :

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Créez un emplacement intitulé **SanJose** et un affichage appelé **Lobby**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Attribution d’un canal à un affichage {#assigning-channel-to-display}

Une fois le projet configuré, vous devez affecter le canal à un affichage pour la vue du contenu.

1. Accédez à l’affichage requis, par exemple, **DemoScreens** --> **Emplacements** --> **SanJose** --> **Lobby**.

1. Appuyez/cliquez sur **Attribuer le canal** dans la barre d’actions.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Ou,

   Tap/click **Dashboard** from the action bar and click **+Assign Channel** from the **ASSIGNED CHANNELS &amp; SCHEDULES** panel.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. La boîte de dialogue **Attribution de canaux** s’ouvre.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. From the **Settings** option, you can choose the channel **by path** or **by name**, enter the **Channel Role**, **Priority**, **Supported Events**, and **Interruption Methods**. De plus, vous pouvez activer l&#39;info-bulle d&#39;attraction à partir de cette boîte de dialogue.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Refer to [Channel Properties](#channel-properties) section to learn more about channel assignment properties.

1. From the **Schedule** option select the **Activation Window** and **Recurrence Schedule**.
   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >Refer to [Channel Properties](#channel-properties) section to learn more about channel assignment properties.

1. Cliquez sur **Enregistrer** une fois vos préférences configurées.

### Affichage du contenu dans le lecteur Chrome {#viewing-content-output}

Cet exemple présente une sortie sur un lecteur Chrome. Une fois le canal attribué à votre écran, vous devez enregistrer l’appareil sur un lecteur.

Voir [Enregistrement des appareils](device-registration.md) pour savoir comment enregistrer un appareil sur un lecteur AEM Screens.

Vous allez afficher la sortie suivante sur le lecteur choisi :

![new1](assets/channel-assignment/channel-assign-output.gif)

## Timeline View {#timeline-view}

Une fois que vous avez affecté un canal à un affichage et que vous avez configuré un calendrier de répétition, vous pouvez vue le calendrier à partir du panneau CANAUX et calendriers **AFFECTÉS** .

Suivez les étapes ci-dessous pour accéder à la vue de chronologie :

1. Accédez à l’affichage requis, par exemple, **DemoScreens** --> **Emplacements** --> **SanJose** --> **Lobby**.

1. Appuyez/cliquez sur **Attribuer le canal** dans la barre d’actions.

   Ou,

   Tap/click **Dashboard** and click **Timeline** from the **ASSIGNED CHANNELS &amp; SCHEDULES** panel.

   ![image](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Understanding Channel Properties from Channel Assignment Dialog Box {#channel-properties}

Les propriétés suivantes sont définies à partir de l’option **Paramètres** de la boîte de dialogue **Attribution de canaux**.

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Sélectionner un canal {#select-channel}

La sélection d’un canal de référence permet de fournir une référence pour le canal souhaité, en utilisant soit le nom, soit le chemin du canal.

* **Par chemin** : vous fournissez une référence explicite à l’aide du chemin absolu du canal.

* **Par nom** : vous saisissez le nom du canal, qui désignera un canal réel en fonction du contexte. Cette fonction vous permet de créer la version locale d’un canal pour diffuser dynamiquement le contenu spécifique à un emplacement. Par exemple, un canal portant le nom *offres du jour*, dont le contenu serait différent dans deux villes, mais avec le même rôle de canal sur tous les affichages.

### Rôle du canal {#role-channel}

Le rôle du canal définit le contexte de l’affichage. Le rôle est ciblé par diverses actions ; il est indépendant du canal qui remplit le rôle.

### Priorité {#priority-channel}

La priorité est utilisée pour contrôler les attributions au cas où plusieurs d’entre elles correspondent aux critères de lecture. Celle présentant la valeur la plus élevée est toujours prioritaire par rapport aux valeurs plus faibles. Par exemple, s’il existe deux canaux A et B, A ayant une priorité de 1 et B une priorité de 2, alors le canal B est affiché, car il présente une priorité supérieure à celle de A.

>[!NOTE]
>La priorité d’un canal est définie sous forme numérique (1 au minimum) dans la boîte de dialogue **Attribution de canaux**, comme indiqué ci-dessus. En outre, les canaux attribués sont triés par ordre de priorité descendante.

### Événements pris en charge {#supported-events-channel}

* **Chargement initial** : charge le canal lorsque le lecteur démarre. Il peut être attribué à plusieurs canaux en combinaison avec la planification.
* **Écran inactif** : se charge lorsque l’écran est inactif. Il peut être attribué à plusieurs canaux en combinaison avec la planification.
* **Minuteur** : il doit être défini lorsqu’une planification est fournie.
* **Interaction de l’utilisateur** : le lecteur passera au canal spécifié s’il existe une interaction de l’utilisateur sur l’écran (tactile) dans un canal inactif et se chargera en cas de pression sur l’écran.

### Méthode d’interruption {#interruption-method-channel}

>[!IMPORTANT]
>
> Cette option est disponible uniquement avec AEM 6.4 Feature Pack 8 ou AEM 6.5 Feature Pack 4.

En tant qu’auteur de contenu, vous devez être en mesure de spécifier le moment où un canal est interrompu, de sorte que vous puissiez choisir de couper le contenu non essentiel, tout en ayant la possibilité de lire intégralement le contenu important avant de l’interrompre en raison de la planification.

Sélectionnez l’une des options suivantes disponibles pour définir la méthode d’interruption dans la boîte de dialogue **Attribution de canaux** :

* **Immédiatement** : chaque fois que la planification est activée ou qu’une mise à jour est reçue, vous pouvez interrompre la lecture et immédiatement actualiser ou lire le nouveau contenu.
* **À la fin de l’élément actuel** : lorsqu’une nouvelle planification est activée ou qu’une mise à jour est reçue, vous avez la possibilité d’attendre la fin de la lecture de l’élément en cours dans la séquence avant d’actualiser ou de lire le nouveau contenu.
   >[!NOTE]
   >Cette option est sélectionnée par défaut.
* **À la fin de la séquence** : lorsqu’une nouvelle planification est activée ou qu’une mise à jour est reçue, vous avez la possibilité d’attendre que la séquence entière se termine. Juste avant la séquence souhaitée, vous revenez sur le premier élément, actualisez ou lisez le nouveau contenu.

   >[!NOTE]
   >L’utilisation de la deuxième ou de la troisième option peut entraîner un léger report des heures de planification définies au niveau de l’attribution, car le lecteur attend la fin de l’élément ou de la séquence (après l’heure spécifiée) avant de procéder à l’actualisation. Le délai dépend de la durée de lecture de l’élément.


Les propriétés suivantes sont définies à partir de l’option **Planification** de la boîte de dialogue **Attribution de canaux**.

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Fenêtre d’activation {#activation-window}

La fenêtre d’activation permet de sélectionner une **Date de début** et une **Date de fin** pour afficher le contenu.

### Planning de périodicité {#recurrence-schedule}

Le planning de périodicité permet de définir une planification récurrente pour votre contenu. Cliquez sur **+ Ajouter un planning** pour ajouter un planning de périodicité à votre canal.

>[!NOTE]
>Vous pouvez ajouter plusieurs plannings de périodicité à votre canal.
>Les plannings de périodicité s’accompagnent de *tranches horaires*, ce qui permet de définir une planification globale avec plusieurs canaux qui s’exécutent à des moments spécifiques de la journée et de réutiliser simultanément cette configuration pour tous vos affichages.

Vous pouvez configurer les options suivantes :

* **Nom** : intitulé de votre planning de périodicité.
* **Répéter** : indiquez si la planification s’exécute de manière **quotidienne**, **hebdomadaire**, **mensuelle** ou **annuelle**.
* **Début** : heure de début de votre planning.
* **Fin** : heure de fin de votre planning. Vous pouvez le définir par heure ou par durée.
   * **Heure** : le planning se terminera à une heure définie.
   * **Durée** : le planning s’exécute pendant une durée particulière en heures ou en minutes.

### Tranches horaires {#dayparting}

DayParting désigne le fractionnement d’une journée en créneaux horaires et la spécification du contenu lu à l’heure souhaitée. AEM Screens vous permet de planifier des canaux en termes de tranches horaires au cours d’une journée, d’une semaine ou d’un mois en fonction des besoins.

Les exemples suivants présentent les tranches horaires dans les canaux selon trois scénarios différents :

#### Diffusion du contenu au cours d’une même journée divisée en plusieurs tranches horaires  {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Cet exemple montre comment un restaurant utilise DayParting pour présenter tous les jours son menu de petit-déjeuner, déjeuner et dîner.

Ici, nous divisons chaque jour en différents créneaux horaires, de sorte que le contenu du canal soit lu selon l’heure spécifiée de la journée. Définissez les propriétés suivantes du calendrier de répétition pour votre canal afin de lire le contenu selon ce cas d’utilisation.

| **Nom** | **Répète** | **Début** | **Fin** |
|---|---|---|---|
| Petit déjeuner | Quotidiennement | 6 h | 11 h |
| Déjeuner | Quotidiennement | 11 h | 15 h |
| Dîner | Quotidiennement | 15 h | 20 h |

#### Diffusion du contenu pendant un jour donné de la semaine {#playing-content-on-a-particular-day-of-the-week}

Cet exemple montre le partage de journée mis en oeuvre dans un casino où le événement en direct a lieu tous les week-ends de 20h à 22h et où des spécialités sont disponibles pour le menu du dîner après 22h00 et 1h00.

| **Nom** | **Répète** | **Début** | **Fin** |
|---|---|---|---|
| Weekend | Hebdomadaire : Samedi, Dimanche | 20 h | 22:00 |
| Spécialités | Quotidien : Lundi-vendredi | 22:00 | 1 h |

>[!NOTE]
>
>En outre, vous pouvez définir la ***priorité*** de chacun des canaux. Par exemple, si deux canaux sont définis sur le même jour et la même heure, ou sur le même mois, alors le canal qui possède la priorité supérieure est diffusé en premier. La valeur de priorité minimale est de 0.

