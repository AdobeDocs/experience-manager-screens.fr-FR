---
title: Réplication des déclencheurs de données sur les serveurs de publication
seo-title: Réplication des déclencheurs de données vers le serveur de publication
description: Répliquez les déclencheurs de données au serveur de publication.
seo-description: Répliquez les déclencheurs de données au serveur de publication.
translation-type: tm+mt
source-git-commit: 47e0204ea734a1348385ddd3c7108038c88d1933

---


# Réplication des déclencheurs de données sur le serveur de publication {#replicating-data-triggers}

Lorsque vous utilisez ContextHub et AEM Targeting Engine pour personnaliser le contenu en fonction des déclencheurs de données dans une configuration de création/publication, toutes les configurations liées à ContextHub et à la personnalisation ne sont pas automatiquement répliquées avec les canaux lors de leur publication.

Suivez cette page pour découvrir les étapes manuelles requises pour publier ces configurations séparément.

Cela se résume essentiellement à la publication manuelle :

1. Configurations du magasin ContextHub et des modules d’interface utilisateur
1. Audiences de personnalisation
1. Activités de personnalisation

## Procédure de réplication des déclencheurs de données vers le serveur de publication {#replicating-data-triggers-publish}

Suivez les étapes ci-dessous pour répliquer les déclencheurs de données vers le serveur de publication.

### Étape 1 :Réplication des configurations ContextHub {#replicating-contexthub-configurations}

1. Accédez à **Outils** > **Déploiement** > **Distribution** > Agent de **publication puis cliquez sur l’agent de publication pour configurer vos paramètres.**

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!Nnote]
   >Vous pouvez également utiliser le [lien](http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish) pour accéder directement à l’écran afin de configurer et de tester la connexion.

1. Cliquez sur **Tester la connexion** dans la barre d’actions pour valider la communication de l’auteur avec l’instance de publication, comme illustré dans la figure ci-dessous.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!Nnote]
   >Si le test échoue, vous devez corriger la configuration de l’agent de réplication entre l’instance d’auteur et l’instance de publication. Pour plus d&#39;informations, reportez-vous à [Résolution des problèmes liés à Test Connection](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) .

1. Cliquez sur **Modifier** dans l’écran ci-dessus et vérifiez que l’URL du point de fin dans le champ Points de fin **de l’** importateur pointe également vers l’URL du serveur de publication dans Distribution Agent.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers3.png)

1. Sélectionnez **Ajouter** dans l&#39;arborescence de l&#39;agent **de** distribution et sélectionnez le chemin de configuration de votre projet, c&#39;est-à-dire `/conf/screens/settings/cloudsettings/configuration)`.

1. Cliquez sur **Envoyer**

### Réplication des audiences {#replicating-audiences}

1. Accédez à **Outils** > **Personnalisation** > **Audiences** ou utilisez le [lien pour naviguer directement.](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html)

1. Explorez le dossier de votre projet, c&#39;est-à-dire `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers5.png)

1. Sélectionnez toutes les audiences et tous les segments dans l’interface utilisateur.

1. Cliquez sur **Gérer la publication** dans la barre d’actions.

1. Cliquez sur **Suivant** et **Publier**.

### Réplication des activités {#replicating-activities}

1. Accédez à **Outils** > **Personnalisation** > **Activités** ou utilisez le [lien pour naviguer directement.](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html)

1. Explorez le dossier de votre projet, c&#39;est-à-dire `/content/campaigns/screens/…`.

1. Sélectionnez toutes les activités dans l’interface utilisateur.

1. Cliquez sur **Gérer la publication** dans la barre d’actions.

1. Cliquez sur **Suivant** et **Publier**.

   > [!Nnote]
   >La réplication des configurations et audiences ContextHub est effectuée pendant la configuration du projet, tandis que la réplication des activités et sera requise chaque fois que le ciblage est modifié dans un canal.

#### Résultat {#result}

Si la réplication est réussie, vous devez afficher la structure suivante sur l’instance de publication (ou similaire pour votre projet) :

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Dépannage de Test Connection {#troubleshoot-test}

Si la connexion test échoue lors de la réplication des configurations ContextHub, suivez la section ci-dessous pour résoudre le problème :

1. Accédez au champ Points de fin **de l’** importateur et vérifiez que l’URL du point de fin pointe vers l’URL du serveur de publication dans Distribution Agent.

1. Si vous n’utilisez pas les informations d’identification par défaut, vous devez configurer l’agent de distribution avec un mot de passe d’administrateur différent.
Suivez les étapes ci-dessous :

   1. Accédez à Outils > **Opérations** > Console Web** `http://localhost:4502/system/console/configMgr`pour ouvrir l’écran **de la console Web** Adobe Experience Manager.

   1. Search for **Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Créez une configuration en renseignant le **nom**, le nom **d’** utilisateur et le mot de passe **, par exemple***slingTransportSecretProvider..*
   1. Cliquez sur **Enregistrer**

   1. Recherchez le nom de votre agent de distribution à l&#39;aide de `Cmd +F`.

   1. Cliquez pour ouvrir la configuration osgi de l&#39;agent de distribution.

   1. Recherchez Transport Secret Provider dans la configuration osgi et mettez-le à jour avec `"(name=slingTransportSecretProvider)"`.

   1. Cliquez sur **Enregistrer** et exécutez la connexion test.

