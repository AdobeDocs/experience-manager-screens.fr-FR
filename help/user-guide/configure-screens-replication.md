---
title: Configuration de l’agent de réplication Screens
description: Consultez cette page pour obtenir des informations sur la configuration de l’agent de réplication Screens.
role: Developer
level: Intermediate
source-git-commit: 99d66e5ac4239a6e43c15bb835f1e41ca94d908b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 9%

---


# Configuration de l’agent de réplication Screens {#configuring-screens-replication-agent}

Cette page décrit comment configurer l’agent de réplication Screens.

>[!NOTE]
>Pour en savoir plus sur les agents de réplication Screens, voir [Agents et commandes de réplication Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Vous devez remplir les deux sections pour terminer la configuration de l’agent de réplication Screens :

1. [Activation des utilisateurs et mise à jour du mot de passe](#enable-users)
1. [Mise à jour de l’agent de réplication Screens](#replicate-agent)

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

1. Cliquez sur **Agents sur l’auteur**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Recherchez le lien avec la lettre **s** et cliquez dessus, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Cliquez sur **Modifier**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Vérifier **Activé** de la **Paramètres** .

   ![image](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Accédez à **Transport** à partir de l’onglet **Paramètres de l’agent** et saisissez le même mot de passe que celui que vous avez défini à l’étape (8) de [Activation des utilisateurs et mise à jour du mot de passe](#enable-users). Cliquez sur **OK**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1f.png)

1. Une fois les étapes précédentes effectuées, vous pouvez cliquer sur **Tester la connexion** pour vérifier la connexion.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Si la vérification de la connexion est réussie, vous avez terminé la configuration de l’agent de réplication Screens.