---
title: Configuration de l’agent de réplication Screens
description: Consultez cette page pour obtenir des informations sur la configuration de l’agent de réplication Screens.
role: Developer
level: Intermediate
source-git-commit: 9f0beddf87d9f5473fdedc292d3c24e96b85cdd4
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 10%

---


# Configuration de l’agent de réplication Screens {#configuring-screens-replication-agent}

Cette section décrit comment configurer l’agent de réplication Screens.

## Activation des utilisateurs et mise à jour du mot de passe {#enable-users}

Suivez les étapes ci-dessous :

1. Accédez à votre instance AEM.

1. Cliquez sur Outils —> **Sécurité** —> **Utilisateurs**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Rechercher **screens-receiver-user**.

1. Sélectionnez la **screens-receiver-user** et cliquez sur **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Cliquez sur **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Une fois que vous avez activé l’utilisateur, le **screens-receiver-user** as **Activé** sous le **État** champ .

   ![image](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Sélectionnez la **screens-receiver-user** et cliquez sur **Propriétés** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Cliquez sur **Modifier le mot de passe** under **Paramètres du compte** de la **Détails** , comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Saisissez un nouveau mot de passe dans le champ **Modifier le mot de passe** , puis cliquez sur **Enregistrer**.

   >[!NOTE]
   >Vous devez saisir **admin** in **Votre mot de passe** champ .

   ![image](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Cliquez sur **Enregistrer et fermer**.

1. Sélectionnez la **screens-receiver-user** et cliquez sur **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Cliquez sur **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Sélectionnez la **screens-receiver-user** et cliquez sur **Désactiver** dans la barre d’actions.

   >[!IMPORTANT]
   > Désactivation **screens-receiver-user** désactive uniquement cet utilisateur de l’instance d’auteur et tous les utilisateurs de l’instance de publication restent principaux. Ne cliquez pas sur **Désactiver** dans la barre d’actions, la désactivation supprime également l’utilisateur des instances de publication.

   ![image](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Cliquez sur **OK** pour confirmer.

## Mise à jour de l’agent de réplication Screens {#replicate-agent}

Consultez la section ci-dessous pour mettre à jour les paramètres de l’agent de réplication Screens :

1. Accédez à votre instance AEM.

1. Cliquez sur Outils —> **Déploiement** —> **Réplication**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1a.png)
