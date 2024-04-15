---
title: Configuration des agents de réplication Screens
description: Découvrez comment configurer les agents de réplication Screens.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 32%

---

# Configuration des agents de réplication Screens {#configuring-screens-replication-agent}

Cette page décrit comment configurer les agents de réplication Screens.

## Objectif {#objective}

Un agent de réplication Screens est chargé de transférer les données de commande comme *user*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep*, et de nombreuses autres valeurs de ce type, de la publication vers l’auteur. Il est essentiel de le configurer pour que l’auteur puisse afficher le ping de l’appareil.

>[!NOTE]
>Pour en savoir plus sur les agents de réplication Screens, voir [Agents et commandes de réplication Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

Renseignez les deux sections si vous souhaitez terminer la configuration de l’agent de réplication Screens :

1. [Activation des utilisateurs et mise à jour du mot de passe](#enable-users)
1. [Mise à jour des paramètres de l’agent de réplication Screens](#replicate-agent)

## Activation des utilisateurs et mise à jour du mot de passe {#enable-users}

Pour activer les utilisateurs et mettre à jour le mot de passe de `screens-receiver-user`:

>[!NOTE]
>Pour des raisons de sécurité, il est recommandé d’éviter d’utiliser le mot de passe administrateur pour `screens-receiver-user`.

1. Accédez à votre instance d’auteur AEM.

1. Sélectionnez Outils > **Sécurité** > **Utilisateurs**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Recherchez **`screens-receiver-user`**.

1. Sélectionnez la variable **`screens-receiver-user`** et sélectionnez **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Sélectionner **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Lorsque vous avez activé l’utilisateur, la variable **`screens-receiver-user`** as **Activé** sous le **État** champ .

   ![image](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Sélectionnez la variable **`screens-receiver-user`** et sélectionnez **Propriétés** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Sélectionner **Modifier le mot de passe** under **Paramètres du compte** de la **Détails** , comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Saisissez un nouveau mot de passe dans le champ **Modifier le mot de passe** , puis sélectionnez **Enregistrer**.

   >[!NOTE]
   >Saisissez le mot de passe utilisateur admin existant dans **Votre mot de passe** champ .

   ![image](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Sélectionnez **Enregistrer et fermer**.

1. Sélectionnez la variable **`screens-receiver-user`** et sélectionnez **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Sélectionner **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Sélectionnez la variable **`screens-receiver-user`** et sélectionnez **Désactiver** dans la barre d’actions.

   >[!IMPORTANT]
   > Désactivation **`screens-receiver-user`** désactive uniquement cet utilisateur de l’instance de création et tous les utilisateurs de l’instance de publication restent actifs. Ne pas sélectionner **Désactiver** dans la barre d’actions, car la désactivation supprime également l’utilisateur des instances de publication.

   ![image](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Sélectionner **OK** pour confirmer.

## Mise à jour des paramètres de l’agent de réplication Screens {#replicate-agent}

Consultez la section ci-dessous pour mettre à jour les paramètres de l’agent de réplication AEM Screens :

>[!IMPORTANT]
>Effectuez les étapes suivantes sur TOUS les agents de réplication AEM Screens existants.

1. Accédez à votre instance AEM.
1. Sélectionnez Outils > **Déploiement** > **Réplication**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Sélectionner **Agents sur l’auteur**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Recherchez tous les agents de réplication AEM Screens sur l’auteur et sélectionnez le lien, comme illustré dans la figure ci-dessous.

   >[!NOTE]
   >Recherchez tous les agents de réplication AEM Screens. Le nom de l’agent de réplication Screens comprend la lettre **s** dans le titre.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Sélectionnez **Modifier**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Cochez **Activé** dans l’onglet **Paramètres**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Accédez à **Transport** à partir de la **Paramètres de l’agent** et mettre à jour la boîte de dialogue **Utilisateur** to **`screens-receiver-user`** et saisissez le même mot de passe que celui défini précédemment à l’étape (8) de [Activation des utilisateurs et mise à jour du mot de passe](#enable-users).

   ![image](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Sélectionnez **OK**.

1. Une fois les étapes précédentes terminées, sélectionnez **Tester la connexion** pour vérifier la connexion.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Si la vérification de la connexion réussit, vous avez terminé la configuration de l’agent de réplication Screens.
