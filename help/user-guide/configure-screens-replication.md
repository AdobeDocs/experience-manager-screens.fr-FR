---
title: Configure Screens Replication Agents
description: Consultez cette page pour obtenir des informations sur la configuration des agents de réplication Screens.
role: Developer
level: Intermediate
source-git-commit: ede0eb02c97c99732c64a92c603e51bedecdbac8
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 5%

---


# Configuration des agents de réplication Screens {#configuring-screens-replication-agent}

This following page describes how to configure Screens Replication Agents.

## Objectif {#objective}

The Screens Replication Agent is responsible for bringing commands data such as, *user*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep*, and many more such values from publish to author. It is essential to configure this so that the author can show the device ping.

>[!NOTE]
>To learn more about Screens Replication Agents, see [Screens Replication Agents and Commands](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Vous devez remplir les deux sections pour terminer la configuration de l’agent de réplication Screens :

1. [Enabling Users and Updating the Password](#enable-users)
1. [Updating Settings for Screens Replication Agent](#replicate-agent)

## Activation des utilisateurs et mise à jour du mot de passe {#enable-users}

Suivez les étapes ci-dessous pour activer les utilisateurs et mettre à jour le mot de passe pour screens-receiver-user :

>[!NOTE]
>Pour des raisons de sécurité, il est recommandé d’éviter d’utiliser le mot de passe administrateur pour screens-receiver-user.

1. Accédez à votre instance AEM Author.

1. Click on tools --> **Security** --> **Users**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Search for **screens-receiver-user**.

1. Sélectionnez la **screens-receiver-user** et cliquez sur **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Cliquez sur **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Once you have enabled the user, you will see the **screens-receiver-user** as **Enabled** under the **Status** field.

   ![image](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Select the **screens-receiver-user** and click on **Properties** from the action bar.

   ![image](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Cliquez sur **Modifier le mot de passe** under **Paramètres du compte** de la **Détails** , comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Saisissez un nouveau mot de passe dans le champ **Modifier le mot de passe** , puis cliquez sur **Enregistrer**.

   >[!NOTE]
   >You should enter the existing admin user password in **Your Password** field.

   ![image](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Click on **Save &amp; Close**.

1. Sélectionnez la **screens-receiver-user** et cliquez sur **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Cliquez sur **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Sélectionnez la **screens-receiver-user** et cliquez sur **Désactiver** dans la barre d’actions.

   >[!IMPORTANT]
   > Désactivation **screens-receiver-user** désactive uniquement cet utilisateur de l’instance d’auteur et tous les utilisateurs de l’instance de publication restent principaux. Ne cliquez pas sur **Désactiver** dans la barre d’actions, la désactivation supprime également l’utilisateur des instances de publication.

   ![image](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Cliquez sur **OK** pour confirmer.

## Mise à jour des paramètres de l’agent de réplication Screens {#replicate-agent}

Consultez la section ci-dessous pour mettre à jour les paramètres de l’agent de réplication Screens :

>[!IMPORTANT]
>Vous devez effectuer les étapes suivantes sur TOUS les agents de réplication Screens existants.

1. Accédez à votre instance AEM.

1. Cliquez sur Outils —> **Déploiement** —> **Réplication**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Cliquez sur **Agents sur l’auteur**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Search for the all Screens Replication agents on author and click the link, as shown in the figure below.

   >[!NOTE]
   >Recherchez tous les agents de réplication Screens. Le nom de l’agent de réplication Screens comprend une lettre. **s** dans le titre.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Cliquez sur **Modifier**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Vérifier **Activé** de la **Paramètres** .

   ![image](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Accédez à **Transport** à partir de l’onglet **Paramètres de l’agent** et mettre à jour la boîte de dialogue **Utilisateur** to **screens-receiver-user** et saisissez le même mot de passe que celui que vous avez défini à l’étape (8) de [Activation des utilisateurs et mise à jour du mot de passe](#enable-users).

   ![image](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Cliquez sur **OK**.

1. Une fois les étapes précédentes effectuées, vous pouvez cliquer sur **Tester la connexion** pour vérifier la connexion.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   If the connection verification is successful, you have completed configuring Screens Replication Agent.