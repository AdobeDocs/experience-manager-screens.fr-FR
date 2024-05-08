---
title: Canal de prise de contrôle permanente
description: Suivez ce cas d’utilisation pour créer un canal de prise de contrôle permanente.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 36%

---

# Canal de prise de contrôle permanente {#perpetual-takeover-channel}

La page suivante présente un cas d’utilisation qui met l’accent sur la configuration d’un projet concernant la création d’un canal de prise de contrôle permanente lu un jour et une heure spécifiques en continu.

## Description du cas d’utilisation {#use-case-description}

Ce cas pratique explique comment créer un canal qui *prend le relai* du canal de lecture normal pour un affichage ou un groupe d’affichages. La prise de contrôle a lieu perpétuellement un jour et une heure spécifiques.
Par exemple, il existe un canal de prise de contrôle permanente lu tous les vendredis de 9 h 00 à 10 h 00. Pendant cette période, aucun autre canal ne doit être lu. L’exemple suivant présente la création d’un canal de prise de contrôle permanente qui lit le contenu tous les mercredis pendant deux heures, de 14h00 à 16h00.

### Prérequis {#preconditions}

Avant de commencer ce cas d’utilisation, vous devez comprendre comment :

* **[Création et gestion des canaux](managing-channels.md)**
* **[Création et gestion des emplacements](managing-locations.md)**
* **[Création et gestion des planifications](managing-schedules.md)**
* **[Enregistrement d’appareils](device-registration.md)**

### Acteurs principaux {#primary-actors}

Auteurs de contenu

## Configuration du projet {#setting-up-the-project}

Pour configurer un projet, procédez comme suit :

**Configuration des canaux et de l’affichage**

1. Créez un projet AEM Screens appelé **PerpetualTakeOver**, comme illustré ci-dessous.

   ![ressource](assets/p_usecase1.png)

1. Créez un canal **MainAdChannel** dans le dossier **Channels** (Canaux).

   ![ressource](assets/p_usecase2.png)

1. Cliquez sur le bouton **MainAdChannel** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser et déposez certaines ressources (images, vidéos, séquences incorporées) sur votre canal.

   ![ressource](assets/p_usecase3.png)


   >[!NOTE]
   >Le canal **MainAdChannel** de cet exemple illustre un canal de séquence qui lit le contenu en continu.

1. Créez un **TakeOver** canal qui prend le contrôle du contenu dans **MainAdChannel** et est lu tous les mercredis de 14h00 à 16h00.

1. Cliquez sur le bouton **TakeOver** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser certaines ressources vers votre canal. L’exemple suivant présente une image de zone unique ajoutée à ce canal.

   ![ressource](assets/p_usecase4.png)

1. Configurez un emplacement et un affichage pour vos canaux. Par exemple, l’emplacement suivant **MainLobby** et affichage **MainLobbyDisplay** sont configurés pour ce projet.

   ![ressource](assets/p_usecase5.png)

**Affectation de canaux à un affichage**

1. Cliquez sur l&#39;affichage **MainLobbyDisplay** de la **Emplacements** dossier. Cliquez sur **Attribuer le canal** à partir de la barre d’actions pour ouvrir la **Attribution de canaux** de la boîte de dialogue

   >[!NOTE]
   >Pour savoir comment attribuer un canal à un affichage, voir **[Attribution de canaux](channel-assignment.md)**.

1. Renseignez les champs (**Chemin du canal**, **Priorité** et **Événements pris en charge**) de la boîte de dialogue **Attribution de canaux** et cliquez sur **Enregistrer** pour attribuer le canal **MainAdChannel** à votre affichage.

   * **Chemin du canal**: cliquez sur le chemin d’accès au **MainAdChannel** channel
   * **Priorité** : Définissez la priorité de ce canal sur 1.
   * **Événements pris en charge**: cliquez sur le bouton **Charge initiale** et **Écran inactif**.

   ![ressource](assets/p_usecase6.png)

1. Cliquez sur l&#39;affichage **TakeOver** de la **Emplacements** dossier. Cliquez sur **Attribuer le canal** à partir de la barre d’actions afin de pouvoir attribuer le canal de prise de contrôle.

1. Attribution de la variable **TakeOver** à votre affichage à une heure planifiée et en remplissant les champs suivants à partir de la fonction **Attribution de canaux** , puis sélectionnez **Enregistrer**:

   * **Chemin du canal**: cliquez sur le chemin d’accès au **TakeOver** channel
   * **Priorité** : attribuez à ce canal une priorité supérieure à celle du canal **MainAdChannel**. Par exemple, la priorité définie dans cet exemple est 8.
   * **Événements pris en charge**: cliquez sur le bouton **Écran inactif** et **Minuteur**.
   * **Planification** : entrez le texte de la planification selon laquelle ce canal doit exécuter l’affichage. Le texte de la **Planification** mentionnée dans cet exemple est *le mercredi après 14 h 00 et avant 16 h 00*.

     >[!NOTE]
     >Pour en savoir plus sur les expressions que vous pouvez ajouter à la variable **Planification**, voir [Exemples d’expressions](#example-expressions) ci-dessous.
   * **actif à partir de** : Date et heure de début.
   * **actif jusqu’à** : Date et heure de fin.

     Par exemple, le texte de la section **Planification** et **actif depuis** et **actif jusqu’à** La date et l’heure ici permettent au contenu d’être lu tous les mercredis de 14 h 00 à 16 h 00.


     ![ressource](assets/p_usecase7.png)

     Accédez à l’affichage à partir de **TakeOver** > **Emplacements** > **MainLobby** > **MainLobbyDisplay** et cliquez sur **Tableau de bord** depuis la barre d’actions afin de pouvoir visualiser les canaux attribués avec leurs priorités, comme illustré ci-dessous.

     >[!NOTE]
     >Il est obligatoire de définir la priorité du canal de prise de contrôle sur le niveau le plus élevé.

     ![ressource](assets/p_usecase8.png)
Maintenant, le **TakeOver** le canal prend le relais **MainAdChannel** à 14 h 00 pendant deux heures jusqu’à 16 h 00 tous les mercredis et lit son contenu du 9 janvier 2020 au 31 janvier 2020.

## Exemples d’expressions {#example-expressions}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| avant 8 h | le canal est lu avant 8 h 00 tous les jours |
| après 14 heures | le canal est lu après 14 h 00 tous les jours |
| après 12 h 15 et avant 12 h 45 | le canal est lu après 12h15 tous les jours pendant 30 minutes |
| avant 12 h 15 et après 12 h 45 | le canal est lu avant 12h15 tous les jours et après 12h45. |
| le premier jour de janvier après 14 h 00, le deuxième jour de janvier également le troisième jour de janvier avant 3 h 00. | la lecture du canal commence après 14 h 00 le 1er janvier et se poursuit toute la journée du 2 janvier jusqu’à 03 h 00 le 3 janvier |
| les 1er et 2 jours de janvier après 14 h 00 et les 2 et 3 jours de janvier avant 3 h 00. | la lecture du canal commence après 14 h 00 le 1er janvier, se poursuit jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et se poursuit jusqu’à 3 h 00 le 3 janvier |

>[!NOTE]
>
>Vous pouvez également utiliser _temps militaire_ au lieu de *A.M./P.M.* (14 h 00).
