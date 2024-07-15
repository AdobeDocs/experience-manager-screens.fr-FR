---
title: Répliquer des déclencheurs de données sur les serveurs de publication
description: Découvrez comment répliquer les déclencheurs de données sur le serveur de publication pour AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 100%

---

# Répliquer des déclencheurs de données sur les serveurs de publication {#replicating-data-triggers}

Lorsque vous utilisez ContextHub et le moteur de ciblage AEM pour personnaliser le contenu en fonction des déclencheurs de données dans une configuration de création/publication, toutes les configurations liées à ContextHub et à la personnalisation ne sont pas automatiquement répliquées avec les canaux lors de leur publication.

Cette page permet de découvrir les étapes manuelles requises pour publier ces configurations séparément.

Ce processus se résume essentiellement à la publication manuelle des éléments suivants :

1. Configurations du magasin ContextHub et des modules d’interface utilisateur
1. Audiences personnalisées
1. Activités personnalisées

## Procédure de réplication des déclencheurs de données sur le serveur de publication {#replicating-data-triggers-publish}

Suivez les étapes ci-dessous pour répliquer les déclencheurs de données sur le serveur de publication.

### Étape 1 : réplication des configurations ContextHub {#replicating-contexthub-configurations}

1. Accédez à **Outils** > **Déploiement** > **Distribution** > **Agent de publication** puis cliquez sur l’agent de publication pour configurer vos paramètres.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Vous pouvez également utiliser `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` pour accéder directement à l’écran afin de configurer et de tester la connexion.

1. Cliquez sur **Tester la connexion** dans la barre d’actions pour valider la communication de l’instance de création avec l’instance de publication, comme illustré ci-dessous :

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Si le test échoue, corrigez la configuration de l’agent de réplication entre l’instance de création et l’instance de publication. Pour plus d’informations, voir [Dépannage du test de la connexion](/help/user-guide/replicating-data-triggers.md#troubleshoot-test).

1. Cliquez sur **Ajouter** dans l’arborescence de l’**Agent de distribution** et sélectionnez le chemin de configuration de votre projet, par exemple `/conf/screens/settings/cloudsettings/configuration`.

1. Cliquez sur **Envoyer**.

### Répliquer les audiences {#replicating-audiences}

1. Accédez à votre instance AEM > **Personnalisation** > **Audiences** ou utilisez `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` pour y arriver directement.

1. Explorez le dossier de votre projet, par exemple `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Sélectionnez toutes les audiences et tous les segments dans l’interface d’utilisation.

1. Cliquez sur **Gérer la publication** dans la barre d’actions.

1. Cliquez sur **Suivant** et **Publier**.

### Répliquer les activités {#replicating-activities}

1. Accédez à votre instance AEM > **Personnalisation** > **Activités** ou utilisez `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` pour y arriver directement.

1. Explorez le dossier de votre projet, c’est-à-dire `/content/campaigns/screens/…`.

1. Sélectionnez toutes les activités dans l’interface d’utilisation.

1. Cliquez sur **Gérer la publication** dans la barre d’actions.

1. Cliquez sur **Suivant** et **Publier**.

>[!IMPORTANT]
>
>La réplication des configurations et audiences ContextHub est effectuée pendant la configuration du projet, tandis que la réplication des activités sera requise chaque fois que le ciblage est modifié dans un canal.

#### Résultat {#result}

Si la réplication est réussie, vous devez voir la structure suivante sur l’instance de publication (ou similaire pour votre projet) :

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Dépannage du test de la connexion {#troubleshoot-test}

Si le test de la connexion échoue lors de la réplication des configurations ContextHub, suivez la section ci-dessous pour résoudre le problème :

1. Accédez à **Outils** > **Déploiement** > **Distribution** > **Publier l’agent**.

1. Cliquez sur **Modifier** dans la barre d’actions et vérifiez que l’URL du point d’entrée dans le champ **Points d’entrée de l’importateur** pointe également vers l’URL du serveur de publication dans l’agent de distribution.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Si vous n’utilisez pas les informations d’identification d’administration par défaut, vous devez configurer l’agent de distribution avec un nom d’utilisateur ou d’utilisatrice et un mot de passe différents.

   Suivez les étapes ci-dessous :

   1. Accédez à Outils > **Opérations** > **Console web** `http://localhost:4502/system/console/configMgr`pour ouvrir l’**écran de la console web Adobe Experience Manager**.
   1. Recherchez **Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Créez une configuration en renseignant le **nom**, le **nom d’utilisateur ou d’utilisatrice** et le **mot de passe**, par exemple, *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Cliquez sur **Enregistrer**
   1. Utilisez `Cmd +F` pour rechercher **Apache Sling Distribution Agent - Forward Agents Factory**, ouvrez les configurations et recherchez **Fournisseur de transport secret**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Mettez à jour `(name=default)` avec `(name=slingTransportSecretProvider)`.
   1. Cliquez sur **Enregistrer** et relancez le test de connexion à partir de l’écran **Agent de distribution** à partir de votre instance AEM.
