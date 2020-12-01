---
title: Canal de prise de contrôle à usage unique
seo-title: Canal de prise de contrôle à usage unique
description: Suivez ce cas d’utilisation pour créer un canal de prise de contrôle à usage unique.
seo-description: Suivez ce cas d’utilisation pour créer un canal de prise de contrôle à usage unique.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 100%

---


# Canal de prise de contrôle à usage unique {#single-use-takeover-channel}

La page suivante présente un cas d’utilisation qui met l’accent sur la configuration d’un projet concernant la création d’un canal de prise de contrôle à usage unique, lu une seule fois pendant une durée spécifique.


## Description du cas d’utilisation {#use-case-description}

Ce cas d’utilisation explique comment créer un canal qui *prend le contrôle* du canal normalement lu pour un affichage ou un groupe d’affichages. La prise de contrôle ne se produira qu’une fois et pour une durée spécifique.
Par exemple, il existe un canal de prise de contrôle unique lu le vendredi de 9h00 à 10h00. Pendant ce temps, aucun autre canal ne doit être lu. Avant et après cette période, le canal de prise de contrôle à usage unique n’est pas lu. L’exemple suivant présente la création d’un canal de prise de contrôle unique qui permet au contenu d’être lu pendant 2 minutes avant 12h00 le 31 décembre jusqu’à 12h01.

### Conditions préalables {#preconditions}

Avant de commencer ce cas d’utilisation, vous devez comprendre comment :

* **[Création et gestion des canaux](managing-channels.md)**
* **[Création et gestion des emplacements](managing-locations.md)**
* **[Création et gestion des planifications](managing-schedules.md)**
* **[Enregistrement de périphériques](device-registration.md)**

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

1. Créez un canal **TakeOver** qui prend le contrôle du contenu dans **MainAdChannel** et est lu uniquement un jour et une heure spécifiques.

1. Sélectionnez le canal **TakeOver** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser certaines ressources vers votre canal. L’exemple suivant présente une image de zone unique ajoutée à ce canal.

   ![ressource](assets/single-takeover4.png)

1. Configurez un emplacement et un affichage pour vos canaux. Par exemple, l’emplacement **Lobby** et l’affichage **MainLobbyDisplay** suivants sont configurés pour ce projet.

   ![ressource](assets/single-takeover5.png)

**Affectation de canaux à un affichage**

1. Sélectionnez l’affichage **MainLobbyDisplay** dans le dossier **Locations** (Emplacements). Cliquez sur **Attribuer le canal** dans la barre d’actions.

   ![ressource](assets/single-takeover6.png)

   >[!NOTE]
   >Pour savoir comment attribuer un canal à un affichage, reportez-vous à **[Attribution de canaux](channel-assignment.md)**.

1. Renseignez les champs (**Chemin du canal**, **Priorité** et **Événements pris en charge**) de la boîte de dialogue **Attribution de canaux** et cliquez sur **Enregistrer**. Vous venez d’attribuer le canal **MainAdChannel** à votre affichage.

   ![ressource](assets/single-takeover7.png)

1. Sélectionnez l’affichage **TakeOver** dans le dossier **Locations** (Emplacements). Cliquez sur **Attribuer un canal** dans la barre d’actions pour attribuer le canal de prise de contrôle à usage unique.

1. Pour attribuer le canal **TakeOver** à votre affichage à une heure planifiée et renseigner les champs suivants de la boîte de dialogue **Attribution de canaux**, cliquez sur **Enregistrer** :

   * **Chemin du canal** : sélectionnez le chemin d’accès au canal TakeOver.
   * **Priorité** : attribuez à ce canal une priorité supérieure à celle du canal **MainAdChannel**. Par exemple, la priorité définie dans cet exemple est 8.

      >[!NOTE]
      >La priorité peut être une valeur supérieure à la valeur de priorité du canal normalement lu.
   * **Événements pris en charge** : sélectionnez l’**Écran inactif** et le **Minuteur**.
   * **Planification** : Entrez le texte de la planification selon laquelle ce canal doit exécuter l’affichage. Par exemple, le texte permet ici au contenu d’être lu pendant 2 minutes avant 12h00 le 31 décembre et jusqu’à 12h01.
Le texte de la **Planification** mentionnée dans cet exemple est *le 31 décembre après 23h58 et également le 1er janvier avant 00h01*.

      ![ressource](assets/single-takeover8.png)

      Accédez à l’affichage à partir de **SingleUseTakeOver** --> **Emplacements** --> **Lobby** --> **MainLobbyDisplay** et cliquez sur **Tableau de bord** dans la barre d’actions pour afficher les canaux attribués avec leurs priorités, comme illustré ci-dessous.

      >[!NOTE]
      >Il est obligatoire de définir la priorité du canal de prise de contrôle sur le niveau le plus élevé.

      ![ressource](assets/single-takeover9.png)

>[!NOTE]
>
>Il est recommandé de supprimer le canal de prise de contrôle à usage unique une fois qu’il est lu.