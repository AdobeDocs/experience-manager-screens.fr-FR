---
title: Réplication des déclencheurs de données sur les serveurs de publication
seo-title: Réplication des déclencheurs de données vers le serveur de publication
description: Répliquez les déclencheurs de données au serveur de publication.
seo-description: Répliquez les déclencheurs de données au serveur de publication.
translation-type: tm+mt
source-git-commit: a8ded0c15e0e3cbaf0999da796789991b20d24cb

---


# Réplication des déclencheurs de données sur le serveur de publication {#replicating-data-triggers}

Lorsque vous utilisez ContextHub et AEM Targeting Engine pour personnaliser le contenu en fonction des déclencheurs de données dans une configuration de création/publication, toutes les configurations liées à ContextHub et à la personnalisation ne sont pas automatiquement répliquées avec les canaux lors de leur publication.

Suivez cette page pour découvrir les étapes manuelles requises pour publier ces configurations séparément.

Cela se résume essentiellement à la publication manuelle :

1. Configurations du magasin ContextHub et des modules d’interface utilisateur
1. Audiences de personnalisation
1. Activités de personnalisation

## Procédure de réplication des déclencheurs de données vers le serveur de publication {#replicating-data-triggers-publish}

Pour répliquer les déclencheurs de données sur le serveur de publication, procédez comme suit :

### Réplication des configurations ContextHub {#replicating-contexthub-configurations}

1. Accédez à **Outils** > **Déploiement** > **Distribution** > Agent de **publicationhttp://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish**
1. Cliquez sur le bouton Tester la connexion pour vérifier que l’auteur peut communiquer correctement avec l’instance de publication.
1. Si le test échoue, vous devez corriger la configuration de l’agent de réplication entre l’auteur et la publication.
1. Vérifier que l’URL du point de fin pointe également vers l’URL du serveur de publication dans Distribution Agent
1. Edition > Points de fin de l’importateur
1. Cliquez sur l’onglet Répartir
1. Sélectionner le bouton d’option Ajouter une arborescence
1. Dans le navigateur de chemins, sélectionnez le chemin de configuration de votre projet (c.-à-d. /conf/screens/settings/cloudsettings/configuration)
1. Cliquez sur Envoyer

### Réplication des audiences {#replicating-audiences}

1. Accédez à Outils > Personnalisation > Audienceshttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html
1. Explorez le dossier de votre projet (c.-à-d. /conf/screens/)
1. Sélection de tous les publics/segments dans l’interface utilisateur
1. Cliquez sur Gérer la publication
1. Cliquez sur Suivant
1. Cliquez sur Publier

### Réplication des activités {#replicating-activities}

1. Accédez à Outils > Personnalisation > Activitéshttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html
1. Explorez le dossier de votre projet (c.-à-d. /content/campaigns/screens/...)
1. Sélectionner toutes les activités dans l’interface utilisateur
1. Cliquez sur Gérer la publication
1. Cliquez sur Suivant
1. Cliquez sur Publier

> [!Nnote]
>La réplication des configurations et audiences ContextHub est effectuée pendant la configuration du projet, tandis que la réplication des activités et sera requise chaque fois que le ciblage est modifié dans un canal.

#### Résultat {#result}

Si la réplication est réussie, vous devez afficher la structure suivante sur l’instance de publication (ou similaire pour votre projet) :

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`