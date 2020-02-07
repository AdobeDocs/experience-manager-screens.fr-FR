---
title: Canal de prise de contrôle permanente
seo-title: Canal de prise de contrôle permanente
description: Suivez ce cas d’utilisation pour créer un canal de prise de contrôle permanente.
seo-description: Suivez ce cas d’utilisation sur la configuration d’un projet qui crée un canal de prise de contrôle permanente lu un jour et une heure spécifiques en continu.
contentOwner: jsyal
translation-type: ht
source-git-commit: 75453128ce6c66e6fef9c5433a5e4389ef9f1c88

---


# Canal de prise de contrôle permanente {#perpetual-takeover-channel}

La page suivante présente un cas d’utilisation qui met l’accent sur la configuration d’un projet concernant la création d’un canal de prise de contrôle permanente lu un jour et une heure spécifiques en continu.

## Description du cas d’utilisation {#use-case-description}

Ce cas d’utilisation explique comment créer un canal qui *prend le contrôle* du canal normalement lu pour un affichage ou un groupe d’affichages. La prise de contrôle aura lieu perpétuellement un jour et une heure spécifiques.
Par exemple, il existe un canal de prise de contrôle permanente lu tous les vendredis de 09h00 à 10h00. Pendant ce temps, aucun autre canal ne doit être lu. L’exemple suivant présente la création d’un canal de prise de contrôle permanente qui lit le contenu tous les mercredis pendant 2 heures, de 14h00 à 16h00.

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

1. Créez un projet AEM Screens appelé **PerpetualTakeOver**, comme illustré ci-dessous.

   ![ressource](assets/p_usecase1.png)

1. Créez un canal **MainAdChannel** dans le dossier **Channels** (Canaux).

   ![ressource](assets/p_usecase2.png)

1. Sélectionnez le canal **MainAdChannel** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser et déposez certaines ressources (images, vidéos, séquences incorporées) sur votre canal.

   ![ressource](assets/p_usecase3.png)


   >[!NOTE]
   >Le canal **MainAdChannel** de cet exemple illustre un canal de séquence qui lit le contenu en continu.

1. Créez un canal **TakeOver** qui prend le contrôle du contenu dans **MainAdChannel** et est lu tous les mercredis de 14h00 à 16h00.

1. Sélectionnez le canal **TakeOver** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser certaines ressources vers votre canal. L’exemple suivant présente une image de zone unique ajoutée à ce canal.

   ![ressource](assets/p_usecase4.png)

1. Configurez un emplacement et un affichage pour vos canaux. Par exemple, l’emplacement **MainLobby** et l’affichage **MainLobbyDisplay** suivants sont configurés pour ce projet.

   ![ressource](assets/p_usecase5.png)

**Affectation de canaux à un affichage**

1. Sélectionnez l’affichage **MainLobbyDisplay** dans le dossier **Locations** (Emplacements). Cliquez sur **Attribuer un canal** dans la barre d’actions pour ouvrir la boîte de dialogue **Attribution de canaux**.

   >[!NOTE]
   >Pour savoir comment attribuer un canal à un affichage, reportez-vous à **[Attribution de canaux](channel-assignment.md)**.

1. Renseignez les champs (**Chemin du canal**, **Priorité** et **Événements pris en charge**) de la boîte de dialogue **Attribution de canaux** et cliquez sur **Enregistrer** pour attribuer le canal **MainAdChannel** à votre affichage.

   * **Chemin du canal** : sélectionnez le chemin d’accès au canal **MainAdChannel**.
   * **Priorité** : Définissez la priorité de ce canal sur 1.
   * **Événements pris en charge** : sélectionnez le **Chargement initial** et l’**Écran inactif**.
   ![ressource](assets/p_usecase6.png)

1. Sélectionnez l’affichage **TakeOver** dans le dossier **Locations** (Emplacements). Cliquez sur **Attribuer un canal** dans la barre d’actions pour attribuer le canal de prise de contrôle.

1. Pour attribuer le canal **TakeOver** à votre affichage à une heure planifiée et renseigner les champs suivants de la boîte de dialogue **Attribution de canaux**, cliquez sur **Enregistrer** :

   * **Chemin du canal** : sélectionnez le chemin d’accès au canal **TakeOver**.
   * **Priorité** : Attribuez à ce canal une priorité supérieure à celle du canal **MainAdChannel**. Par exemple, la priorité définie dans cet exemple est 8.
   * **Événements pris en charge** : sélectionnez l’**Écran inactif** et le **Minuteur**.
   * **Planification** : entrez le texte de la planification selon laquelle ce canal doit exécuter l’affichage. Le texte de la **Planification** mentionnée dans cet exemple est *le mercredi après 14h00 et avant 16h00*.
      >[!NOTE]
      >Pour en savoir plus sur les expressions que vous pouvez ajouter à la **Planification**, consultez la section [Exemples d’expressions](#example-expressions) ci-dessous.
   * **actif à partir de** : Date et heure de début.
   * **actif jusqu’à** : Date et heure de fin.

      Par exemple, le texte de la **Planification** et l’heure et la date **actif à partir de** et **actif jusqu’à** permettent au contenu d’être lu tous les mercredis de 14h00 à 16h00.


      ![ressource](assets/p_usecase7.png)

      Accédez à l’affichage à partir de **TakeOver** --> **Emplacements** --> **MainLobby** --> **MainLobbyDisplay** et cliquez sur **Tableau de bord** dans la barre d’actions pour afficher les canaux attribués avec leurs priorités, comme illustré ci-dessous.

      >[!NOTE]
      >Il est obligatoire de définir la priorité du canal de prise de contrôle sur le niveau le plus élevé.

      ![asset](assets/p_usecase8.png)
Désormais, le canal **TakeOver** prendra le contrôle du canal **MainAdChannelChannel** à 14h00 pendant deux heures jusqu’à 16h00 tous les mercredis et lira son contenu du 9 janvier 2020 au 31 janvier 2020.

## Exemples d’expressions {#example-expressions}

Le tableau suivant récapitule quelques exemples d’expressions que vous pouvez ajouter à la planification lors de l’attribution d’un canal à un affichage.

| **Expression** | **Interprétation** |
|---|---|
| avant 08h00 | le canal est lu avant 08h00 tous les jours |
| après 14h00 | le canal est lu tous les jours après 14h00 |
| après 12h15 et avant 12h45 | le canal est lu après 12h15 tous les jours pendant 30 minutes |
| avant 12h15 et après 12h45 | le canal est lu avant 12h15 et après 12h45 tous les jours |
| le 1er janvier après 14h00, et le 2 janvier et le 3 janvier avant 03h00 | la lecture du canal commence après 14h00 le 1er janvier et se poursuit toute la journée du 2 janvier jusqu’à 03h00 le 3 janvier |
| le 1er et 2 janvier après 14h00 et le 2-3 janvier avant 03h00 | la lecture du canal commence après 14h00 le 1er janvier, et se poursuit jusqu’à 03h00 le 2 janvier, puis recommence le 2 janvier à 14h00 et se poursuit jusqu’à 03h00 le 3 janvier. |

>[!NOTE]
>Vous pouvez également utiliser la notation _sur 24 heures_ (14h00) au lieu de la notation *am/pm* (2h00 pm).
