---
title: Affectation de canal - Dernier FP
seo-title: Affectation de canal - Dernier FP
description: Suivez cette page pour en savoir plus sur les affectations de Canal et les heures de diffusion.
translation-type: tm+mt
source-git-commit: 1c6a7342288a5d78dbea91d29ff8e5d6c8fec486
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 64%

---


# Attribution de canaux {#channel-assignment}

>[!IMPORTANT]
>Cette section décrit l&#39;affectation et la planification des canaux pour AEM 6.5.5 Screens Feature Pack et versions ultérieures.

Une fois que vous avez configuré un affichage, vous devez affecter un canal à un affichage pour vue de votre contenu.

Cette page montre l&#39;affectation d&#39;un canal à votre affichage.

>[!NOTE]
>Vous pouvez attribuer plusieurs canaux à un affichage.


## Attribution d’un canal {#assign-a-channel-new-release}

Suivez les sections ci-dessous pour créer un projet AEM Screens et affecter un canal à un affichage.

### Création d&#39;un projet AEM Screens et de Canaux {#creating-project}

Pour configurer un projet et un canal, procédez comme suit :

1. Create an AEM Screens Project titled as **DemoScreens**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Consultez [Création et gestion de projets](creating-a-screens-project.md) pour savoir comment créer un projet AEM Screens.

1. Créez un canal de séquence intitulé **Cafeteria** dans le dossier **Canaux** .

1. Select the channel and click **Edit** from the action bar to add content to your channel.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Par exemple, le canal **Cafeteria** affiche désormais les images suivantes :

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Créez un emplacement intitulé **SanJose** et un affichage sous forme de **hall**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Assigning Channel to a Display {#assigning-channel-to-display}

Une fois le projet configuré, vous devez affecter le canal à un affichage pour la vue du contenu.

1. Navigate to the required display, for example, **DemoScreens** --> **Locations** --> **SanJose** --> **Lobby**.

1. Tap/click **Assign Channel** from the action bar.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Ou,

   Appuyez/cliquez sur **Tableau de bord** et cliquez sur **+Attribuer un Canal** dans le panneau CANAUX et calendriers **AFFECTÉS** .

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. The **Channel Assignment** dialog box opens.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. L&#39;option **Paramètres** vous permet de choisir le canal par chemin ou par nom, de saisir le rôle de canal, la priorité, les événements pris en charge et les méthodes d&#39;interruption. De plus, vous pouvez activer l&#39;option d&#39;info-bulle d&#39;attraction à partir de cette boîte de dialogue.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Consultez la section Propriétés [du](#channel-properties) Canal pour en savoir plus sur les propriétés du canal.

1. Dans l&#39;option **Planifications** , sélectionnez le fuseau horaire de **référence, la fenêtre****d&#39;Activation et le calendrier de** **répétition.**

1. Cliquez sur **Enregistrer** une fois que vous avez configuré vos préférences.

### Viewing the Content in Chrome Player {#viewing-content-output}

### Présentation des propriétés des canaux à partir de l’attribution de canaux {#channel-properties}

### Canal de référence {#ref-channel}

Le canal de référence vous permet de fournir une référence pour le canal souhaité, en utilisant soit le nom, soit le chemin du canal.

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