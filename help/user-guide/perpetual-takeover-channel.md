---
title: Canal de prise de contrôle permanente
description: Suivez ce cas d’utilisation pour créer un canal de prise de contrôle permanente.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 49%

---

# Canal de prise de contrôle permanente {#perpetual-takeover-channel}

La page suivante présente un cas d’utilisation qui met l’accent sur la configuration d’un projet concernant la création d’un canal de prise de contrôle permanente lu un jour et une heure spécifiques en continu.

## Description du cas d’utilisation {#use-case-description}

Ce cas pratique explique comment créer un canal qui : *prend le relais* à partir du canal de lecture normal pour un affichage ou un groupe d’affichages. La prise de contrôle a lieu pour un jour et une heure spécifiques de façon permanente.
Par exemple, il existe un canal de prise de contrôle permanente qui est lu tous les vendredis de 9 h à 10 h. Pendant ce temps, aucun autre canal ne doit être lu. L’exemple suivant illustre la création d’un canal de prise de contrôle permanente qui permet la lecture du contenu tous les mercredis pendant deux heures, de 14 heures à 16 heures.

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

1. Sélectionnez le canal **MainAdChannel** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser et déposez certaines ressources (images, vidéos, séquences incorporées) sur votre canal.

   ![ressource](assets/p_usecase3.png)


   >[!NOTE]
   >Le canal **MainAdChannel** de cet exemple illustre un canal de séquence qui lit le contenu en continu.

1. Création d’un **TakeOver** canal qui reprend le contenu dans **MainAdChannel** et joue tous les mercredis de 14 h à 16 h.

1. Sélectionner le **TakeOver** et cliquez sur **Modifier** à partir de la barre d’actions. Faites glisser certaines ressources vers votre canal. L’exemple suivant présente une image de zone unique ajoutée à ce canal.

   ![ressource](assets/p_usecase4.png)

1. Configurez un emplacement et un affichage pour vos canaux. Par exemple, l’emplacement suivant : **MainLobby** et afficher **MainLobbyDisplay** sont configurés pour ce projet.

   ![ressource](assets/p_usecase5.png)

**Affectation de canaux à un affichage**

1. Sélectionnez l’affichage **MainLobbyDisplay** dans le dossier **Locations** (Emplacements). Clic **Attribuer le canal** à partir de la barre d’actions pour pouvoir ouvrir le **Attribution de canaux** boîte de dialogue.

   >[!NOTE]
   >Pour savoir comment attribuer un canal à un affichage, reportez-vous à **[Attribution de canaux](channel-assignment.md)**.

1. Renseignez les champs (**Chemin du canal**, **Priorité** et **Événements pris en charge**) de la boîte de dialogue **Attribution de canaux** et cliquez sur **Enregistrer** pour attribuer le canal **MainAdChannel** à votre affichage.

   * **Chemin du canal** : sélectionnez le chemin d’accès au canal **MainAdChannel**.
   * **Priorité** : Définissez la priorité de ce canal sur 1.
   * **Événements pris en charge** : sélectionnez le **Chargement initial** et l’**Écran inactif**.

   ![ressource](assets/p_usecase6.png)

1. Sélectionnez l’affichage **TakeOver** dans le dossier **Locations** (Emplacements). Clic **Attribuer le canal** à partir de la barre d’actions afin que vous puissiez attribuer le canal de prise de contrôle.

1. Attribution du **TakeOver** à votre affichage à une heure planifiée et en remplissant les champs suivants à partir du **Attribution de canaux** boîte de dialogue et clic **Enregistrer**:

   * **Chemin du canal** : sélectionnez le chemin d’accès au canal **TakeOver**.
   * **Priorité** : Attribuez à ce canal une priorité supérieure à celle du canal **MainAdChannel**. Par exemple, la priorité définie dans cet exemple est 8.
   * **Événements pris en charge** : sélectionnez l’**Écran inactif** et le **Minuteur**.
   * **Planification** : entrez le texte de la planification selon laquelle ce canal doit exécuter l’affichage. Le texte de la **Planification** mentionnée dans cet exemple est *le mercredi après 14 h 00 et avant 16 h 00*.

     >[!NOTE]
     >Pour en savoir plus sur les expressions que vous pouvez ajouter à la **Planification**, consultez la section [Exemples d’expressions](#example-expressions) ci-dessous.
   * **actif à partir de** : Date et heure de début.
   * **actif jusqu’à** : Date et heure de fin.

     Par exemple, le texte dans **Planification** et **actif à partir de** et **actif jusqu’au** La date et l’heure ici permettent la lecture du contenu tous les mercredis de 14 h à 16 h.


     ![ressource](assets/p_usecase7.png)

     Accéder à l’affichage à partir de **TakeOver** > **Emplacements** > **MainLobby** > **MainLobbyDisplay** et cliquez sur **Tableau de bord** à partir de la barre d’actions, vous pouvez afficher les canaux affectés avec leurs priorités, comme illustré ci-dessous.

     >[!NOTE]
     >Il est obligatoire de définir la priorité du canal de prise de contrôle sur le niveau le plus élevé.

     ![actif](assets/p_usecase8.png)
Maintenant, le **TakeOver** le canal prend le contrôle de **MainAdChannel** à 14 h pendant deux heures jusqu’à 16 h tous les mercredis et diffuse son contenu du 9 janvier 2020 au 31 janvier 2020.

## Exemples d’expressions {#example-expressions}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| avant 8 h | la chaîne passe avant 8 h tous les jours |
| après 14 h | la chaîne passe après 14 heures tous les jours |
| après 12 h 15 et avant 12 h 45 | la chaîne passe après 12 h 15 tous les jours pendant 30 minutes |
| avant 12 h 15 et après 12 h 45 | la chaîne joue avant 12 h 15 tous les jours, puis après 12 h 45. |
| le premier jour de janvier après 14h00 et le deuxième jour de janvier, ainsi que le troisième jour de janvier avant 3h00. | la chaîne commence à jouer après 14 h le 1er janvier et continue à jouer toute la journée le 2 janvier jusqu’à 3 h le 3 janvier |
| les 1 à 2 jours de janvier à partir de 14 h, ainsi que les 2 à 3 jours de janvier avant 15 h . | le canal démarre le lecteur après 14 h 00 le 1er janvier, continue la lecture jusqu’à 3 h 00 le 2 janvier, puis recommence le 2 janvier à 14 h 00 et continue jusqu’à 3 h 00 le 3 janvier |

>[!NOTE]
>
>Vous pouvez également utiliser _temps militaire_ notation (14:00) au lieu de *A.M./P.M.* (14 H).
