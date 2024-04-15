---
title: Utilisation de la synchronisation des commandes
description: En savoir plus sur l’utilisation de la synchronisation des commandes dans AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 50%

---

# Synchronisation des commandes {#command-sync}

La page suivante décrit l’utilisation de la synchronisation des commandes. La synchronisation des commandes permet une lecture synchronisée sur différents lecteurs. Les lecteurs peuvent lire un contenu différent, mais chaque ressource doit avoir la même durée.

>[!IMPORTANT]
>
>Cette fonctionnalité ne prend pas en charge les séquences incorporées, les séquences incorporées dynamiques, les canaux d’application ni les transitions.

## Présentation {#overview}

Les solutions de signalétique digitale doivent prendre en charge les murs vidéo et la lecture synchronisée pour prendre en charge des scénarios tels que les comptes à rebours du Nouvel An ou les vidéos volumineuses découpées pour être lues sur plusieurs écrans. C’est là que la synchronisation des commandes entre en jeu.

Pour utiliser la synchronisation des commandes, un lecteur agit comme *principal* et envoie une commande, tandis que tous les autres lecteurs agissent comme *clients* et procèdent à la lecture lorsqu’ils reçoivent la commande.

Le lecteur *principal* envoie une commande à tous les clients enregistrés lorsqu’il est sur le point de démarrer la lecture d’un élément. La payoad liée à cette opération peut être l’index de l’élément à lire et/ou le code html externe de l’élément à lire.

## Mise en œuvre de la synchronisation des commandes {#using-command-sync}

La section suivante décrit l’utilisation de la synchronisation des commandes dans un projet AEM Screens.

>[!NOTE]
>
>Pour la lecture synchronisée, il est nécessaire que tous les appareils présentent les mêmes spécifications matérielles et, de préférence, le même système d’exploitation. Il n’est pas recommandé de synchroniser des appareils et systèmes d’exploitation différents.

### Configuration du projet {#setting-up}

Avant d’utiliser la fonction de synchronisation des commandes, assurez-vous d’avoir un projet et un canal avec du contenu configuré pour le projet.

1. L’exemple suivant présente un projet de démonstration nommé **CommandSyncDemo** et un canal de séquence **ChannelLobby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Pour savoir comment créer un canal ou ajouter du contenu à un canal, voir [Création et gestion des canaux](/help/user-guide/managing-channels.md)

   Le canal contient le contenu suivant, comme illustré ci-dessous.

   ![image1](assets/command-sync/command-sync2-1.png)

1. Création d’un emplacement **Lobby** puis un affichage intitulé **LobbyDisplay** dans le **Emplacements** , comme illustré dans la figure ci-dessous.
   ![image1](assets/command-sync/command-sync3-1.png)

1. Affectez le canal **ChannelLobby** au canal **LobbyDisplay**. Vous pouvez afficher le canal affecté à l’affichage à partir du tableau de bord.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Pour savoir comment attribuer un canal à un affichage, voir [Création et gestion des affichages](/help/user-guide/managing-displays.md).

1. Accédez à **Périphériques** dossier.
1. Cliquez sur **Gestionnaire d’appareils** dans la barre d’actions.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Pour savoir comment enregistrer un appareil, voir [Enregistrement de périphérique](/help/user-guide/device-registration.md)

1. À des fins de démonstration, cet exemple présente un appareil Chrome et un lecteur Windows comme deux appareils distincts. Les deux appareils pointent vers le même affichage.
   ![image1](assets/command-sync6.png)

### Mise à jour des paramètres de canal

1. Accédez à **ChannelLobby**.
1. Cliquez sur **Modifier** dans la barre d’actions.
1. Sélectionnez l’ensemble du canal comme illustré ci-dessous.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Cliquez sur l’icône de clé à molette.
   ![image1](assets/command-sync/command-sync8-1.png)

1. Dans le **Page** , saisissez la *synchronisé* dans le **Stratégie** champ .
   ![image1](assets/command-sync/command-sync9-1.png)


### Configurer un lecteur principal {#setting-up-primary}

1. Accédez au tableau de bord d’affichage à partir de **CommandSyncDemo** > **Emplacements**  > **Lobby** > **LobbyDisplay** et cliquez sur **Tableau de bord** dans la barre d’actions.
Notez les deux appareils (Chrome et lecteur Windows) dans **APPAREILS** , comme illustré dans les sections suivantes :
   ![image1](assets/command-sync/command-sync10-1.png)

1. Dans la **APPAREILS** , sélectionnez le périphérique que vous souhaitez définir comme principal. L’exemple suivant illustre la configuration de l’appareil Chrome en tant qu’appareil principal. Cliquez sur **Défini comme périphérique principal**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Saisissez l’adresse IP dans **Défini comme périphérique principal** et cliquez sur **Enregistrer**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Vous pouvez configurer plusieurs appareils en tant que principaux.

### Synchronisation avec l’appareil principal {#sync-up-primary}

1. Une fois que vous avez défini l’appareil Chrome comme principal, synchronisez l’autre appareil (dans ce cas, le lecteur Windows) avec l’appareil principal.
Sélectionnez l’autre appareil (dans ce cas, le lecteur Windows) dans la **APPAREILS** et cliquez sur **Synchronisation avec l’appareil principal**.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Sélectionnez l’appareil dans la liste et cliquez sur **Enregistrer**.

   >[REMARQUE :]
   > La variable **Synchronisation avec l’appareil principal** La boîte de dialogue affiche la liste des appareils principaux. Sélectionnez la préférence.

1. Lorsque l’appareil (le lecteur Windows) est synchronisé avec l’instance principale (le lecteur Chrome), vous pouvez voir l’appareil synchronisé dans la variable **APPAREILS** du panneau.

   ![image1](assets/command-sync/command-sync14-1.png)

### Désynchronisation du lecteur principal {#desync-up-primary}

Une fois que vous avez synchronisé un ou plusieurs appareils avec un appareil principal, vous pouvez désynchroniser l’attribution à partir de cet appareil.

>[!NOTE]
>
>Si vous désynchronisez un appareil principal, cela annule également la liaison de tous les appareils clients qui lui sont associés.

Pour supprimer la synchronisation du périphérique principal, procédez comme suit :

1. Accédez au panneau **APPAREILS** et sélectionnez l’appareil.

1. Cliquez sur **Désynchroniser les appareils** vous pouvez donc désynchroniser le client avec l’appareil principal.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Cliquez sur **Confirmer** pour désynchroniser l’appareil sélectionné de l’appareil principal.

   >[REMARQUE :]
   > Si vous sélectionnez l’appareil principal et utilisez l’option de désynchronisation, tous les appareils connectés à l’appareil principal sont désynchronisés en une seule étape.
