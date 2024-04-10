---
title: Canal De Prise De Contrôle À Usage Unique
description: Suivez ce cas pratique pour créer un canal de prise de contrôle à usage unique.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: c142830a37461a36baae15f543bd43b0ae8a62a7
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 48%

---

# Canal de prise de contrôle à usage unique {#single-use-takeover-channel}

La page suivante présente un cas d’utilisation qui met l’accent sur la configuration d’un projet sur la création d’un canal de prise de contrôle unique lu une fois pendant une durée spécifique.


## Description du cas d’utilisation {#use-case-description}

Ce cas pratique explique comment créer un canal qui : *prend le relais* à partir du canal de lecture normal pour un affichage ou un groupe d’affichages. La prise de contrôle n&#39;a lieu qu&#39;une seule fois et pour une durée déterminée.

Par exemple, il existe un canal de prise de contrôle unique qui est lu du vendredi de 9 h à 10 h. Pendant ce temps, aucun autre canal ne doit être lu. Avant et après cette période, le canal de prise de contrôle à usage unique n’est pas lu. L’exemple suivant illustre la création d’un canal de prise de contrôle unique qui permet la lecture du contenu pendant 2 minutes avant 00 h 00, le 31 décembre, jusqu’à 00 h 01.

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

1. Créez un projet AEM Screens appelé **SingleUseTakeOver**, comme illustré ci-dessous.

   ![ressource](assets/single-takeover1.png)

1. Créez un canal **MainAdChannel** dans le dossier **Channels** (Canaux).

   ![ressource](assets/single-takeover2.png)

1. Sélectionnez le canal **MainAdChannel** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser et déposez certaines ressources (images, vidéos, séquences incorporées) sur votre canal.

   ![ressource](assets/single-takeover2.png)


   >[!NOTE]
   >Le canal **MainAdChannel** de cet exemple illustre un canal de séquence qui lit le contenu en continu.

   ![ressource](assets/single-takeover3.png)

1. Création d’un **TakeOver** canal qui reprend le contenu dans **MainAdChannel** et est lu uniquement pour un jour et une heure spécifiques.

1. Sélectionner le **TakeOver** et cliquez sur **Modifier** à partir de la barre d’actions. Faites glisser certaines ressources vers votre canal. L’exemple suivant présente une image de zone unique ajoutée à ce canal.

   ![ressource](assets/single-takeover4.png)

1. Configurez un emplacement et un affichage pour vos canaux. Par exemple, les éléments suivants : **Hall** emplacement et  **MainLobbyDisplay** Les affichages sont configurés pour ce projet.

   ![ressource](assets/single-takeover5.png)

**Affectation de canaux à un affichage**

1. Sélectionnez l’affichage **MainLobbyDisplay** dans le dossier **Locations** (Emplacements). Cliquez sur **Attribuer le canal** dans la barre d’actions.

   ![ressource](assets/single-takeover6.png)

   >[!NOTE]
   >Pour savoir comment attribuer un canal à un affichage, reportez-vous à **[Attribution de canaux](channel-assignment.md)**.

1. Renseignez les champs (**Chemin du canal**, **Priorité** et **Événements pris en charge**) de la boîte de dialogue **Attribution de canaux** et cliquez sur **Enregistrer**. Vous venez d’attribuer le canal **MainAdChannel** à votre affichage.

   ![ressource](assets/single-takeover7.png)

1. Sélectionnez l’affichage **TakeOver** dans le dossier **Locations** (Emplacements). Clic **Attribuer le canal** à partir de la barre d’actions afin que vous puissiez attribuer le canal de prise de contrôle à usage unique.

1. Attribuer le **TakeOver** effectuez un canal vers votre affichage à une heure planifiée et renseignez les champs suivants à partir du **Attribution de canaux** , puis cliquez sur **Enregistrer**:

   * **Chemin du canal** : sélectionnez le chemin d’accès au canal TakeOver.
   * **Priorité** : attribuez à ce canal une priorité supérieure à celle du canal **MainAdChannel**. Par exemple, la priorité définie dans cet exemple est 8.

     >[!NOTE]
     >La priorité peut être n’importe quelle valeur supérieure à la valeur de priorité du canal de lecture normal.
   * **Événements pris en charge** : sélectionnez l’**Écran inactif** et le **Minuteur**.
   * **Planification** : Entrez le texte de la planification selon laquelle ce canal doit exécuter l’affichage. Par exemple, le texte ici permet la lecture du contenu 2 minutes avant 00 h 00 le 31 décembre jusqu’à 00 h 01. Le texte dans le **Planification** mentionné dans cet exemple : *le 31 décembre après 23h58 et également le 1er janvier avant 00h01*.

     ![ressource](assets/single-takeover8.png)

     Accéder à l’affichage à partir de **SingleUseTakeOver** > **Emplacements** > **Hall** > **MainLobbyDisplay** et cliquez sur **Tableau de bord** à partir de la barre d’actions, vous pouvez afficher les canaux affectés avec leurs priorités, comme illustré ci-dessous.

     >[!NOTE]
     >Il est obligatoire de définir la priorité du canal de prise de contrôle sur le niveau le plus élevé.

     ![ressource](assets/single-takeover9.png)

>[!NOTE]
>
>Il est recommandé de supprimer le canal de prise de contrôle à usage unique une fois qu’il est lu.
