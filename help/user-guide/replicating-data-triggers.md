---
title: Réplication des triggers de données sur les serveurs de publication
description: Découvrez comment répliquer les triggers de données sur le serveur de publication pour AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 40%

---

# Réplication des triggers de données sur les serveurs de publication {#replicating-data-triggers}

Lorsque vous utilisez ContextHub et le moteur de ciblage AEM pour personnaliser le contenu en fonction des triggers de données dans une configuration de création/publication, toutes les configurations liées à ContextHub et à la personnalisation ne sont pas automatiquement répliquées avec les canaux lors de leur publication.

Cette page vous aide à découvrir les étapes manuelles requises pour publier ces configurations séparément.

Cela se résume essentiellement à la publication manuelle :

1. Configurations du magasin ContextHub et des modules d’interface utilisateur
1. Audiences personnalisées
1. Activités personnalisées

## Procédure de réplication des triggers de données sur le serveur de publication {#replicating-data-triggers-publish}

Suivez les étapes ci-dessous pour répliquer les triggers de données sur le serveur de publication.

### Étape 1 : réplication des configurations ContextHub {#replicating-contexthub-configurations}

1. Accédez à **Outils** > **Déploiement** > **Distribution** > **Publier l’agent** et cliquez sur l’agent de publication pour pouvoir configurer vos paramètres.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Vous pouvez également utiliser `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` pour accéder directement à l’écran afin de configurer et de tester la connexion.

1. Cliquez sur **Tester la connexion** à partir de la barre d’actions afin que vous puissiez valider la communication de l’auteur avec l’instance de publication, comme illustré ci-dessous :

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Si le test échoue, corrigez la configuration de l’agent de réplication entre l’instance d’auteur et l’instance de publication. Voir [Dépannage du test de la connexion](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) pour plus d’informations.

1. Cliquez sur **Ajouter** de la **Agent de distribution** arborescence d’écran et cliquez sur le chemin de configuration de votre projet, par exemple : `/conf/screens/settings/cloudsettings/configuration`.

1. Cliquez sur **Envoyer**.

### Réplication des audiences {#replicating-audiences}

1. Accédez à votre instance AEM > **Personnalisation** > **Audiences** ou utilisez `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` pour naviguer directement.

1. Explorez le dossier de votre projet, par exemple `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Cliquez sur toutes les audiences et tous les segments dans l’interface utilisateur.

1. Cliquez sur **Gérer la publication** dans la barre d’actions.

1. Cliquez sur **Suivant** et **Publier**.

### Réplication des activités  {#replicating-activities}

1. Accédez à votre instance AEM > **Personnalisation** > **Activités** ou utilisez `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` pour naviguer directement.

1. Explorez le dossier de votre projet, c’est-à-dire `/content/campaigns/screens/…`.

1. Cliquez sur toutes les activités de l’interface utilisateur.

1. Cliquez sur **Gérer la publication** dans la barre d’actions.

1. Cliquez sur **Suivant** et **Publier**.

>[!IMPORTANT]
>
>La réplication des configurations et des audiences ContextHub est effectuée lors de la configuration du projet lors de la réplication des activités et est requise chaque fois que le ciblage est modifié dans un canal.

#### Résultat {#result}

Si la réplication est réussie, vous devez voir la structure suivante sur l’instance de publication (ou similaire pour votre projet) :

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Dépannage du test de la connexion {#troubleshoot-test}

Si le test de la connexion échoue lors de la réplication des configurations ContextHub, suivez la section ci-dessous pour résoudre le problème :

1. Accédez à Outils > **Déploiement** > **Distribution** > **Publier l’agent**.

1. Cliquez sur **Modifier** dans la barre d’actions et assurez-vous que l’URL du point de terminaison dans **Points de terminaison de l’importateur** pointe également vers l’URL du serveur de publication dans l’agent de distribution.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Si vous n’utilisez pas les informations d’identification d’administrateur par défaut, vous devez configurer l’agent de distribution avec un nom d’utilisateur et un mot de passe différents.

   Suivez les étapes ci-dessous :

   1. Accédez à Outils > **Opérations** > **Console web** `http://localhost:4502/system/console/configMgr`pour ouvrir la **Écran de la console web Adobe Experience Manager**.
   1. Recherchez **Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Créez une configuration en renseignant **Nom**, **Nom d’utilisateur**, et **password**, par exemple : *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Cliquez sur **Enregistrer**
   1. Utilisation `Cmd +F` pour rechercher **Agent de distribution Apache Sling - Fabrique d’agents de transfert** pour ouvrir les configurations et rechercher **Fournisseur secret de transport**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Mettez à jour `(name=default)` avec `(name=slingTransportSecretProvider)`.
   1. Cliquez sur **Enregistrer** et relancez le test de connexion à partir de l’écran **Agent de distribution** à partir de votre instance AEM.
