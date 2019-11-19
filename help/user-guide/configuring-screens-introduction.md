---
title: Configuration et déploiement d’AEM Screens
seo-title: Configuration et déploiement de Screens
description: Le lecteur AEM Screens est disponible pour Android, Chrome OS, iOS et Windows. Cette page décrit la configuration et le déploiement d’AEM Screens et résume également les instructions de sélection h/w pour le périphérique du lecteur.
seo-description: Le lecteur AEM Screens est disponible pour Android, Chrome OS, iOS et Windows. Cette page décrit la configuration et le déploiement d’AEM Screens et résume également les instructions de sélection h/w pour le périphérique du lecteur.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: 99f6817a0d126cfb1811887a3415f1b87079d6e7

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

Cette page indique comment installer et configurer les lecteurs Screens sur vos périphériques.

## Configuration du serveur {#server-configuration}

>[!NOTE]
>
>**Important**:
>
>Le lecteur AEM Screens n’utilise pas le jeton CSRF (Cross-Site Request Forgery). Par conséquent, pour configurer un serveur AEM afin qu’il puisse être utilisé avec AEM Screens, ignorez le filtre de référent en autorisant les référents vides.

### Conditions préalables {#prerequisites}

Les points clés suivants permettent de configurer le serveur AEM en vue de son utilisation avec AEM Screens :

#### Autoriser les requêtes de référents vides {#allow-empty-referrer-requests}

1. Accédez à **Configuration de la console Web d’Adobe Experience Manager **via l’instance AEM —&gt; icône de marteau —&gt; **Opérations** —&gt; Console **** Web.

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **La configuration** de la console Web d’Adobe Experience Manager s’ouvre. Recherchez le référent sling.

   Pour rechercher la propriété sling referrer, appuyez sur **Commande+F** pour **Mac** et **Ctrl+F** pour **Windows.**

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. Cochez l’option **Autoriser les champs vides **comme illustré dans la figure ci-dessous.

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. Cliquez sur **Enregistrer** pour activer le filtre Apache Sling Referrer Filter Allow Empty.

#### Activer l’interface utilisateur tactile pour les écrans AEM {#enable-touch-ui-for-aem-screens}

Les écrans AEM nécessitent une interface utilisateur TOUCH et ne fonctionnent pas avec l’interface utilisateur CLASSIC d’Adobe Experience Manager (AEM).

1. Accédez à *&lt;instanceAuteur&gt;/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Assurez-vous que le mode **d’interface utilisateur de création** par défaut est défini sur **TOUCH**, comme illustré dans la figure ci-dessous.

Vous pouvez également appliquer le même paramètre à l’aide des outils*&lt;votreInstanceAuteur&gt; *-&gt;* (icône en forme de marteau)* -&gt; **Opérations** -&gt;** Console Web*** et rechercher le service **** WCM Authoring UI Mode.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Vous pouvez toujours activer l’interface utilisateur classique pour des utilisateurs spécifiques à l’aide des préférences utilisateur.

#### AEM en mode d’exécution NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

Running AEM in production uses the **NOSAMPLECONTENT** runmode. *Supprimer l’en-tête SAMEORIGIN* X-Frame-Options (dans la section d’en-tête de réponse supplémentaire) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Cette opération est nécessaire pour que le lecteur AEM Screens joue des chaînes en ligne.

#### Restrictions de mot de passe {#password-restrictions}

Avec les dernières modifications apportées à ***DeviceServiceImpl***, vous n'avez pas à supprimer les restrictions de mot de passe.

Vous pouvez configurer ***DeviceServiceImpl*** à partir du lien ci-dessous pour activer la restriction de mot de passe lors de la création du mot de passe pour les utilisateurs de périphériques :

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Suivez les étapes ci-dessous pour configurer ***DeviceServiceImpl***:

1. Accédez à **Configuration de la console Web d’Adobe Experience Manager **via l’instance AEM —&gt; icône de marteau —&gt; **Opérations** —&gt; Console **** Web.

1. **La configuration de la console Web d’Adobe Experience Manager **s’ouvre. Recherchez deviceservice. Pour rechercher la propriété, appuyez sur **Commande+F** pour **Mac** et **Ctrl+F** pour **Windows.**

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configuration du dispatcher {#dispatcher-configuration}

Pour savoir comment configurer le répartiteur pour un projet AEM Screens, reportez-vous à la section [Configuration du répartiteur pour un projet](dispatcher-configurations-aem-screens.md)AEM Screens.

#### Encodage Java {#java-encoding}

Set the ***Java encoding*** to Unicode. Par exemple, *Dfile.encoding=Cp1252* ne fonctionnera pas.

>[!NOTE]
>
>**Recommandation :**
>
>Il est recommandé d’utiliser HTTPS pour le serveur AEM Screens utilisé en production.

