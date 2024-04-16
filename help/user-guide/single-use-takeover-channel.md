---
title: Canal de prise de contrôle à usage unique
description: Suivez ce cas d’utilisation pour créer un canal de prise de contrôle à usage unique.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3317f07a-784f-4c4a-93ea-c84f4e42e9f2
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 39%

---

# Canal de prise de contrôle à usage unique {#single-use-takeover-channel}

La page suivante présente un cas d’utilisation qui met l’accent sur la configuration d’un projet concernant la création d’un canal de prise de contrôle unique lu une fois pendant une période spécifique.

## Description du cas d’utilisation {#use-case-description}

Ce cas pratique explique comment créer un canal qui *prend le relai* du canal de lecture normal pour un affichage ou un groupe d’affichages. La prise de contrôle ne se produit qu’une seule fois et pour une période spécifique.

Par exemple, il existe un canal de prise de contrôle unique lu le vendredi de 9 h 00 à 10 h 00. Pendant cette période, aucun autre canal ne doit être lu. Avant et après cette période, le canal de prise de contrôle à usage unique n’est pas lu. L’exemple suivant illustre la création d’un canal de prise de contrôle unique qui permet au contenu d’être lu pendant 2 minutes avant 12h00 le 31 décembre jusqu’à 12h01.

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

1. Cliquez sur le bouton **MainAdChannel** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser et déposez certaines ressources (images, vidéos, séquences incorporées) sur votre canal.

   ![ressource](assets/single-takeover2.png)


   >[!NOTE]
   >Le canal **MainAdChannel** de cet exemple illustre un canal de séquence qui lit le contenu en continu.

   ![ressource](assets/single-takeover3.png)

1. Créez un **TakeOver** canal qui prend le contrôle du contenu dans **MainAdChannel** et est uniquement lu pour un jour et une heure spécifiques.

1. Cliquez sur le bouton **TakeOver** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser certaines ressources vers votre canal. L’exemple suivant présente une image de zone unique ajoutée à ce canal.

   ![ressource](assets/single-takeover4.png)

1. Configurez un emplacement et un affichage pour vos canaux. Par exemple, les éléments suivants **Lobby** emplacement et  **MainLobbyDisplay** sont configurés pour ce projet.

   ![ressource](assets/single-takeover5.png)

**Affectation de canaux à un affichage**

1. Cliquez sur l&#39;affichage **MainLobbyDisplay** de la **Emplacements** dossier. Cliquez sur **Attribuer le canal** dans la barre d’actions.

   ![ressource](assets/single-takeover6.png)

   >[!NOTE]
   >Pour savoir comment attribuer un canal à un affichage, voir **[Attribution de canaux](channel-assignment.md)**.

1. Renseignez les champs (**Chemin du canal**, **Priorité** et **Événements pris en charge**) de la boîte de dialogue **Attribution de canaux** et cliquez sur **Enregistrer**. Vous venez d’attribuer le canal **MainAdChannel** à votre affichage.

   ![ressource](assets/single-takeover7.png)

1. Cliquez sur l&#39;affichage **TakeOver** de la **Emplacements** dossier. Cliquez sur **Attribuer le canal** à partir de la barre d’actions afin de pouvoir attribuer le canal de prise de contrôle à usage unique.

1. Attribuez le **TakeOver** à votre affichage à une heure planifiée et renseignez les champs suivants de la **Attribution de canaux** , puis cliquez sur **Enregistrer**:

   * **Chemin du canal**: cliquez sur le chemin d’accès au canal TakeOver ;
   * **Priorité** : attribuez à ce canal une priorité supérieure à celle du canal **MainAdChannel**. Par exemple, la priorité définie dans cet exemple est 8.

     >[!NOTE]
     >La priorité peut être toute valeur supérieure à la valeur de priorité du canal de lecture normal.
   * **Événements pris en charge**: cliquez sur le bouton **Écran inactif** et **Minuteur**.
   * **Planification** : Entrez le texte de la planification selon laquelle ce canal doit exécuter l’affichage. Par exemple, le texte ici permet au contenu d’être lu 2 minutes avant 12h00 le 31 décembre jusqu’à 12h01. Le texte dans la variable **Planification** mentionné dans cet exemple : *le 31 décembre après 23 h 58 et également le 1er janvier avant 00 h 01*.

     ![ressource](assets/single-takeover8.png)

     Accédez à l’affichage à partir de **SingleUseTakeOver** > **Emplacements** > **Lobby** > **MainLobbyDisplay** et cliquez sur **Tableau de bord** depuis la barre d’actions afin de pouvoir visualiser les canaux attribués avec leurs priorités, comme illustré ci-dessous.

     >[!NOTE]
     >Il est obligatoire de définir la priorité du canal de prise de contrôle sur le niveau le plus élevé.

     ![ressource](assets/single-takeover9.png)

>[!NOTE]
>
>Il est recommandé de supprimer le canal de prise de contrôle à usage unique une fois qu’il est lu.
