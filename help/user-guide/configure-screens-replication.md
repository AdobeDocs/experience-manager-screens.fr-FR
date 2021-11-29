---
title: Configuration des agents de réplication Screens
description: Consultez cette page pour obtenir des informations sur la configuration des agents de réplication Screens.
role: Developer
level: Intermediate
source-git-commit: ede0eb02c97c99732c64a92c603e51bedecdbac8
workflow-type: ht
source-wordcount: '507'
ht-degree: 100%

---


# Configuration des agents de réplication Screens {#configuring-screens-replication-agent}

Cette page décrit comment configurer les agents de réplication Screens.

## Objectif {#objective}

Un agent de réplication Screens est chargé de transférer les données de commande comme *user*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep*, et de nombreuses autres valeurs de ce type, de la publication vers l’auteur. Il est essentiel de le configurer pour que l’auteur puisse afficher le ping de l’appareil.

>[!NOTE]
>Pour en savoir plus sur les agents de réplication Screens, voir [Agents et commandes de réplication Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=fr#screens-replication-agents-and-commands).

Vous devez mettre en œuvre les deux sections pour effectuer la configuration de l’agent de réplication Screens :

1. [Activation des utilisateurs et mise à jour du mot de passe](#enable-users)
1. [Mise à jour des paramètres de l’agent de réplication Screens](#replicate-agent)

## Activation des utilisateurs et mise à jour du mot de passe {#enable-users}

Procédez comme suit pour activer les utilisateurs et mettre à jour le mot de passe pour screens-receiver-user :

>[!NOTE]
>Pour des raisons de sécurité, il est recommandé d’éviter d’utiliser le mot de passe administrateur pour screens-receiver-user.

1. Accédez à votre instance d’auteur AEM.

1. Cliquez sur Outils --> **Sécurité** --> **Utilisateurs**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Recherchez l’utilisateur **screens-receiver-user**.

1. Sélectionnez l’utilisateur **screens-receiver-user**, puis cliquez sur **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Cliquez sur **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Une fois que vous avez activé l’utilisateur, vous voyez que **screens-receiver-user** est **Activé** dans le champ **État**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Sélectionnez **screens-receiver-user**, puis cliquez sur **Propriétés** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Cliquez sur **Modifier le mot de passe** dans **Paramètres du compte** de l’onglet **Détails**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Saisissez un nouveau mot de passe dans le champ **Modifier le mot de passe**, puis cliquez sur **Enregistrer**.

   >[!NOTE]
   >Vous devez saisir le mot de passe utilisateur administrateur existant dans le champ **Votre mot de passe**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Cliquez sur **Enregistrer et fermer**.

1. Sélectionnez **screens-receiver-user**, puis cliquez sur **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Cliquez sur **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Sélectionnez l’utilisateur **screens-receiver-user**, puis cliquez sur **Désactiver** dans la barre d’actions.

   >[!IMPORTANT]
   > La désactivation de **screens-receiver-user** désactive uniquement cet utilisateur de l’instance d’auteur. Tous les utilisateurs de l’instance de publication restent actifs. Ne cliquez pas sur **Désactiver** dans la barre d’actions, car la désactivation supprime également l’utilisateur des instances de publication.

   ![image](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Cliquez sur **OK** pour confirmer.

## Mise à jour des paramètres de l’agent de réplication Screens {#replicate-agent}

Consultez la section ci-dessous pour mettre à jour les paramètres de l’agent de réplication Screens :

>[!IMPORTANT]
>Vous devez effectuer les étapes suivantes sur TOUS les agents de réplication Screens existants.

1. Accédez à votre instance AEM.

1. Cliquez sur Outils --> **Déploiement** --> **Réplication**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Cliquez sur **Agents sur l’auteur**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Recherchez tous les agents de réplication Screens sur l’auteur et cliquez sur le lien, comme illustré dans la figure ci-dessous.

   >[!NOTE]
   >Recherchez tous les agents de réplication Screens. Le nom de l’agent de réplication Screens comprend la lettre **S**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Cliquez sur **Modifier**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Cochez **Activé** dans l’onglet **Paramètres**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Accédez à l’onglet **Transfert** à partir de l’onglet **Paramètres d’agent**, mettez à jour la boîte de dialogue **Utilisateur** en indiquant **screens-receiver-user**, puis saisissez le même mot de passe que celui que vous avez défini à l’étape (8) intitulée [Activation des utilisateurs et mise à jour du mot de passe](#enable-users).

   ![image](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Cliquez sur **OK**.

1. Une fois les étapes précédentes effectuées, vous pouvez cliquer sur **Tester la connexion** pour vérifier la connexion.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Si la vérification de la connexion réussit, vous avez terminé la configuration de l’agent de réplication Screens.