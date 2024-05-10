---
title: Canal de prise de contrôle permanente
description: Découvrez comment créer un canal de prise de contrôle permanente.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 60%

---

# Canal de prise de contrôle permanente {#perpetual-takeover-channel}

La page suivante présente un cas d’utilisation qui met l’accent sur la configuration d’un projet concernant la création d’un canal de prise de contrôle permanente lu un jour et une heure spécifiques en continu.

## Description du cas d’utilisation {#use-case-description}

Ce cas pratique explique comment créer un canal qui *prend le relai* du canal de lecture normal pour un affichage ou un groupe d’affichages. La prise de contrôle a lieu de manière permanente pour un jour et une heure spécifiques.
Par exemple, il existe un canal de prise de contrôle permanente lu tous les vendredis de 9h00 à 10h00. Pendant cette période, aucun autre canal ne doit être lu. L’exemple suivant illustre la création d’un canal de prise de contrôle permanente qui permet au contenu d’être lu tous les mercredis pendant deux heures, de 14h00 à 16h00.

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

1. Créez un canal **TakeOver** qui prend le contrôle du contenu dans **MainAdChannel** et qui est lu tous les mercredis de 14 h 00 à 16 h 00.

1. Cliquez sur le bouton **TakeOver** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser certaines ressources vers votre canal. L’exemple suivant présente une image de zone unique ajoutée à ce canal.

   ![ressource](assets/p_usecase4.png)

1. Configurez un emplacement et un affichage pour vos canaux. Par exemple, l’emplacement **MainLobby** et l’affichage **MainLobbyDisplay** suivants sont configurés pour ce projet.

   ![ressource](assets/p_usecase5.png)

**Affectation de canaux à un affichage**

1. Cliquez sur l&#39;affichage **MainLobbyDisplay** de la **Emplacements** dossier. Cliquez sur **Attribuer un canal** dans la barre d’actions pour ouvrir la boîte de dialogue **Attribution de canaux**.

   >[!NOTE]
   >Pour savoir comment attribuer un canal à un affichage, consultez **[Attribution de canaux](channel-assignment.md)**.

1. Renseignez les champs (**Chemin du canal**, **Priorité** et **Événements pris en charge**) de la boîte de dialogue **Attribution de canaux** et cliquez sur **Enregistrer** pour attribuer le canal **MainAdChannel** à votre affichage.

   * **Chemin du canal**: cliquez sur le chemin d’accès au **MainAdChannel** channel
   * **Priorité** : Définissez la priorité de ce canal sur 1.
   * **Événements pris en charge**: cliquez sur le bouton **Charge initiale** et **Écran inactif**.

   ![ressource](assets/p_usecase6.png)

1. Cliquez sur l&#39;affichage **TakeOver** de la **Emplacements** dossier. Cliquez sur **Attribuer un canal** dans la barre d’actions pour attribuer le canal de prise de contrôle.

1. Attribution de la variable **TakeOver** vers votre affichage à une heure planifiée. Renseignez ensuite les champs suivants à partir du **Attribution de canaux** , puis sélectionnez **Enregistrer**:

   * **Chemin du canal**: cliquez sur le chemin d’accès au **TakeOver** channel
   * **Priorité** : attribuez à ce canal une priorité supérieure à celle du canal **MainAdChannel**. Par exemple, la priorité définie dans cet exemple est 8.
   * **Événements pris en charge**: cliquez sur le bouton **Écran inactif** et **Minuteur**.
   * **Planification**: saisissez le texte du planning selon lequel ce canal doit s’exécuter sur l’affichage. Le texte de la **Planification** mentionnée dans cet exemple est *le mercredi après 14 h 00 et avant 16 h 00*.

     >[!NOTE]
     >Pour en savoir plus sur les expressions que vous pouvez ajouter au **Planning**, consultez la section [Exemples d’expressions](#example-expressions) ci-dessous.
   * **actif à partir de** : Date et heure de début.
   * **actif jusqu’à** : Date et heure de fin.

     Par exemple, le texte du **Planning** et les heures et les dates **actif à partir de** et **actif jusqu’à** permettent au contenu d’être lu tous les mercredis de 14 h 00 à 16 h 00.


     ![ressource](assets/p_usecase7.png)

     Accédez à l’affichage à partir de **TakeOver** > **Emplacements** > **MainLobby** > **MainLobbyDisplay**, puis cliquez sur **Tableau de bord** depuis la barre d’actions afin de pouvoir visualiser les canaux attribués avec leurs priorités, comme illustré ci-dessous.

     >[!NOTE]
     >Il est obligatoire de définir la priorité du canal de prise de contrôle sur le niveau le plus élevé.

     ![Ressource](assets/p_usecase8.png)
Maintenant, le canal **TakeOver** prend le contrôle du canal **MainAdChannel** à 14 h 00 pendant deux heures jusqu’à 16 h 00 tous les mercredis et lit son contenu du 9 janvier 2020 au 31 janvier 2020.

## Exemples d’expressions {#example-expressions}

Le tableau suivant résume quelques exemples d’expressions que vous pouvez ajouter au planning lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| Avant 8 h 00. | Le canal est lu avant 8 h 00 tous les jours. |
| Après 14 h 00. | Le canal est lu tous les jours après 14 h 00. |
| Après 12 h 15 et avant 12 h 45. | Le canal est lu après 12 h 15 tous les jours pendant 30 minutes. |
| Avant 12 h 15 et après 12 h 45. | Le canal est lu avant 12 h 15 et après 12 h 45 tous les jours. |
| le premier jour de janvier après 14 h 00, le deuxième jour de janvier et le troisième jour de janvier avant 3 h 00. | la lecture du canal commence après 14 h 00 le 1er janvier, et se poursuit toute la journée du 02 janvier jusqu’à 3 h 00 le 3 janvier |
| les 1er et 2 jours de janvier après 14 h 00 et les 2 et 3 jours de janvier avant 3 h 00. | la lecture du canal commence après 14 h 00 le 1er janvier, se poursuit jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et se poursuit jusqu’à 3 h 00 le 3 janvier |

>[!NOTE]
>
>Vous pouvez également utiliser la notation d’_heure militaire_ (14:00) au lieu de *A.M./P.M.* (14 h 00).
