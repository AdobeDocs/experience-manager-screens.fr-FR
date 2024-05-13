---
title: Configuration des agents de réplication Screens
description: Découvrez comment configurer les agents de réplication Screens.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 64%

---

# Configuration des agents de réplication Screens {#configuring-screens-replication-agent}

Cette page décrit comment configurer les agents de réplication Screens.

## Objectif {#objective}

L’agent de réplication Screens est chargé d’apporter des données de commandes telles que *user*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep*, et de nombreuses autres valeurs de ce type, de la publication à l’auteur. Il est essentiel de configurer cet agent afin que l’auteur puisse afficher le ping de l’appareil.

>[!NOTE]
>Pour en savoir plus sur les agents de réplication Screens, voir [Agents et commandes de réplication Screens](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

Effectuez les deux étapes si vous souhaitez réaliser la configuration de l’agent de réplication Screens :

1. [Activation des utilisateurs et mise à jour du mot de passe](#enable-users)
1. [Mise à jour des paramètres de l’agent de réplication Screens](#replicate-agent)

## Activation des utilisateurs et mise à jour du mot de passe {#enable-users}

Pour activer les utilisateurs et utilisatrices et mettre à jour le mot de passe pour `screens-receiver-user`, procédez comme suit :

>[!NOTE]
>Pour des raisons de sécurité, il est recommandé d’éviter d’utiliser le mot de passe d’administration pour `screens-receiver-user`.

1. Accédez à votre instance d’auteur AEM.

1. Cliquez sur Outils > **Sécurité** > **Utilisateurs et utilisatrices**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Recherchez **`screens-receiver-user`**.

1. Cliquez sur le bouton **`screens-receiver-user`** et cliquez sur **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Cliquez sur **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Lorsque vous avez activé l’utilisateur, la variable **`screens-receiver-user`** as **Activé** sous le **État** champ .

   ![image](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Cliquez sur le bouton **`screens-receiver-user`** et cliquez sur **Propriétés** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Cliquez sur **Modifier le mot de passe** dans **Paramètres du compte** de l’onglet **Détails**, comme illustré ci-dessous.

   ![image](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Saisissez un nouveau mot de passe dans la boîte de dialogue **Modifier le mot de passe**, puis cliquez sur **Enregistrer**.

   >[!NOTE]
   >Vous devez saisir le mot de passe utilisateur d’administration existant dans le champ **Votre mot de passe**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Cliquez sur **Enregistrer et fermer**.

1. Cliquez sur le bouton **`screens-receiver-user`** et cliquez sur **Activer** dans la barre d’actions.

   ![image](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Cliquez sur **OK** pour confirmer.

   ![image](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Cliquez sur le bouton **`screens-receiver-user`** et cliquez sur **Désactiver** dans la barre d’actions.

   >[!IMPORTANT]
   > La désactivation de **`screens-receiver-user`** désactive uniquement cette personne de l’instance de création. Tous les utilisateurs et toutes les utilisatrices de l’instance de publication restent actifs. Ne cliquez pas sur **Désactiver** dans la barre d’actions, car la désactivation supprime également l’utilisateur ou l’utilisatrice des instances de publication.

   ![image](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Cliquez sur **OK** pour confirmer.

## Mise à jour des paramètres de l’agent de réplication Screens {#replicate-agent}

Consultez la section ci-dessous pour mettre à jour les paramètres de l’agent de réplication Screens :

>[!IMPORTANT]
>Effectuez les étapes suivantes sur TOUS les agents de réplication AEM Screens existants.

1. Accédez à votre instance AEM.
1. Cliquez sur Outils > **Déploiement** > **Réplication**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Cliquez sur **Agents sur l’instance de création**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Recherchez tous les agents de réplication AEM Screens sur l’auteur et cliquez sur le lien, comme illustré dans la figure ci-dessous.

   >[!NOTE]
   >Recherchez tous les agents de réplication AEM Screens. Le nom de l’agent de réplication Screens comprend la lettre **S** dans le titre.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Cliquez sur **Modifier**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Cochez **Activé** dans l’onglet **Paramètres**.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Accédez à l’onglet **Transfert** à partir de la boîte de dialogue **Paramètres d’agent**, mettez à jour l’**Utilisateur ou l’utilisatrice** avec **`screens-receiver-user`**, puis saisissez le même mot de passe que celui que vous avez défini à l’étape (8) intitulée [Activation des utilisateurs et utilisatrices et mise à jour du mot de passe](#enable-users).

   ![image](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Cliquez sur **OK**.

1. Une fois les étapes précédentes effectuées, cliquez sur **Tester la connexion** pour vérifier la connexion.

   ![image](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Si la vérification de la connexion est réussie, vous avez terminé la configuration de l’agent de réplication Screens.
