---
title: Configuration et déploiement d’AEM Screens
seo-title: Configuration et déploiement de Screens
description: Le lecteur AEM Screens est disponible pour Android, Chrome OS, iOS et Windows. Cette page décrit la configuration et le déploiement d’AEM Screens et résume également les instructions de sélection d’équipement pour le périphérique de lecture.
seo-description: Le lecteur AEM Screens est disponible pour Android, Chrome OS, iOS et Windows. Cette page décrit la configuration et le déploiement d’AEM Screens et résume également les instructions de sélection d’équipement pour le périphérique de lecture.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: bca6dc0f6a022a4a9005053320e5047b9321270d
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 100%

---


# Configuration et déploiement d’AEM Screens {#configuring-and-deploying-aem-screens}

Cette page indique comment installer et configurer les lecteurs Screens sur vos périphériques.

## Configuration du serveur {#server-configuration}

>[!NOTE]
>
>**Important** :
>
>Le lecteur AEM Screens n’utilise pas le jeton CSRF (Cross-Site Request Forgery). Par conséquent, pour configurer un serveur AEM afin qu’il puisse être utilisé avec AEM Screens, ignorez le filtre de référent en autorisant les référents vides.

## Structure du contrôle de l’intégrité{#health-check-framework}

La structure du contrôle de l’intégrité permet à l’utilisateur de vérifier si deux configurations nécessaires sont configurées avant d’exécuter un projet AEM Screens.

Elle permet à l’utilisateur de vérifier les deux contrôles de configuration suivants afin d’exécuter un projet AEM Screens, c’est-à-dire de vérifier l’état des deux filtres suivants :

1. **Autoriser un référent vide**
2. **https**

Suivez les étapes ci-dessous pour vérifier si ces deux configurations essentielles sont activées pour AEM Screens :

1. Accédez au [contrôle de l’intégrité Sling de la console web Adobe Experience Manager](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![ressources](assets/health-check1.png)


2. Cliquez sur **Execute selected health checks (Exécuter les contrôles d’intégrité sélectionnés)** pour exécuter la validation des deux propriétés répertoriées ci-dessus.

   Si les deux filtres sont activés, le **service d’intégrité de la configuration de Screens** affiche le **résultat** comme étant **OK** avec les deux configurations activées.

   ![ressources](assets/health-check2.png)

   Si l’un des filtres ou les deux sont désactivés, une alerte s’affiche à l’intention de l’utilisateur, comme illustré ci-dessous.

   L’alerte suivante indique si les deux filtres sont désactivés :
   ![ressources](assets/health-check3.png)

>[!NOTE]
>
>* Pour activer le **filtre de référents Apache Sling**, voir [Autorisation des requêtes de référents vides](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Pour activer le service **HTTP**, reportez-vous au [service HTTP Apache Felix Jetty](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Conditions préalables {#prerequisites}

Les points clés suivants permettent de configurer le serveur AEM en vue de son utilisation avec AEM Screens.

#### Autorisation des requêtes de référents vides {#allow-empty-referrer-requests}

1. Accédez au gestionnaire de **Configuration de la console Web Adobe Experience Manager** via l’instance AEM —> icône en forme de marteau —> **Opérations** —> **Console Web**.

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **La configuration de la console Web d’Adobe Experience Manager** s’ouvre. Recherche de référent Sling.

   Pour rechercher la propriété référent Sling, appuyez sur **Command+F** pour **Mac** et **Ctrl+F** pour **Windows**.

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. Cochez l’option **Allow Empty** comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. Cliquez sur **Enregistrer** pour activer l’option Allow Empty d’Apache Sling Referrer Filter.

#### Service HTTP Apache Felix Jetty {#allow-apache-felix-service}

1. Accédez au gestionnaire de **Configuration de la console Web Adobe Experience Manager** via l’instance AEM —> icône en forme de marteau —> **Opérations** —> **Console Web**.

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **La configuration de la console Web d’Adobe Experience Manager** s’ouvre. Recherchez le service HTTP Apache Felix Jetty.

   Pour rechercher cette propriété, appuyez sur **Command+F** (**Mac**) ou **Ctrl+F** (**Windows**).

1. Cochez l’option **ENABLE HTTP** comme illustré ci-dessous.

   ![screen_shot_2019-07-31at91807am](assets/http-image.png)

1. Cliquez sur **Enregistrer** pour activer le service *http*.

#### Activation de l’interface utilisateur tactile pour AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens nécessite une IU TACTILE et ne fonctionne pas avec l’IU CLASSIQUE d’Adobe Experience Manager (AEM).

1. Accédez à *&lt;VotreInstanceAuteur>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Veillez à ce que le **mode d’UI de création par défaut** soit défini sur **TACTILE**, comme illustré dans la figure ci-dessous.

Vous pouvez également appliquer le même paramètre à l’aide des outils *&lt;votreInstanceAuteur>*->*(icône en forme de marteau)* -> **Opérations** -> **Console Web** et rechercher le service **WCM Authoring UI Mode**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Vous pouvez toujours activer l’interface utilisateur classique pour des utilisateurs spécifiques à l’aide des préférences utilisateur.

#### AEM en mode d’exécution NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

L’exécution d’AEM en production permet d’utiliser le mode d’exécution **NOSAMPLECONTENT**. Supprimez l’en-tête *X-Frame-Options=SAMEORIGIN* (dans la section de l’en-tête de réponse supplémentaire) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Cette opération est nécessaire pour que le lecteur AEM Screens joue des chaînes en ligne.

#### Restrictions de mot de passe {#password-restrictions}

Avec les dernières modifications apportées à ***DeviceServiceImpl***, vous n’avez pas à supprimer les restrictions de mot de passe.

Vous pouvez configurer ***DeviceServiceImpl*** à partir du lien ci-dessous pour activer la restriction de mot de passe lors de la création du mot de passe pour les utilisateurs de périphériques Screens :

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Suivez les étapes ci-dessous pour configurer ***DeviceServiceImpl***:

1. Accédez au gestionnaire de **Configuration de la console Web Adobe Experience Manager** via l’instance AEM —> icône en forme de marteau —> **Opérations** —> **Console Web**.

1. **La configuration de la console Web d’Adobe Experience Manager **s’ouvre. Recherchez deviceservice. Pour rechercher la propriété, appuyez sur **Command+F** pour **Mac** et **Ctrl+F** pour **Windows**.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configuration du dispatcher {#dispatcher-configuration}

Pour savoir comment configurer le dispatcher pour un projet AEM Screens, reportez-vous à la section [Configuration du dispatcher pour un projet AEM Screens](dispatcher-configurations-aem-screens.md).

#### Encodage Java {#java-encoding}

Définissez l’***encodage Java*** sur Unicode. Par exemple, *Dfile.encoding=Cp1252* ne fonctionnera pas.

>[!NOTE]
>
>**Recommandation :**
>
>Il est recommandé d’utiliser HTTPS pour le serveur AEM Screens utilisé en production.








