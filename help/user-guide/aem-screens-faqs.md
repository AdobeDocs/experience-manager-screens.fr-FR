---
title: Questions fréquentes sur AEM Screens
seo-title: AEM Screens FAQs
description: Consultez cette page pour obtenir des réponses aux questions fréquentes concernant un projet AEM Screens.
seo-description: Follow this page to get answers to FAQs related to an AEM Screens project.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: 6f491825c8cbc7159de1a41dd6f902b086325606
workflow-type: tm+mt
source-wordcount: '2040'
ht-degree: 92%

---

# Questions fréquentes sur AEM Screens {#aem-screens-faqs}

La section suivante permet de répondre à une partie des questions fréquemment posées concernant un projet AEM Screens.

## Problème d’écran vide {#blank-screen}

>[!NOTE]
>Liste des contrôles obligatoires qui doivent être testés par l’assistance principale ou l’assistance côté client avant de soulever un problème.

### 1. Quelles doivent être les étapes de dépannage initiales pour un client rencontrant un problème d’écran noir ou de contenu impossible à lire ?  {#troubleshooting-blank-screen}

* Vérifiez si l’aperçu de canal fonctionne.
* Vérifiez si l’aperçu d’affichage fonctionne.
* Essayez d’enregistrer le lecteur en tant qu’extension de navigateur sur votre système pour le même affichage et vérifiez si cela fonctionne.
* Lorsque le lecteur est en cours d’exécution sur votre système, accédez à `http://localhost:24502`. Vérifiez si tout le contenu est correctement téléchargé.
* Vérifiez les ressources pour lesquelles les rendus appropriés sont créés et que le rendu correct est en cours de lecture.
* Recherchez les contenus planifiés et vérifiez si les heures sont correctes. Vérifiez si l’heure configurée dans le lecteur est correcte.
* Examinez les journaux de la console du lecteur et vérifiez l’existence d’erreurs éventuelles. Cliquez avec le bouton droit de la souris et examinez les journaux de la console en les affichant. Si vous utilisez le lecteur Windows, appuyez sur `CTRL + ALT +I` pour faire apparaître la console de développement et afficher les journaux.

### 2. Comment résoudre le problème des écrans gris dans AEM Screens en créant un canal ou un planning par défaut ?

Pour éviter les problèmes d’écrans vierges ou grisés sur le terrain, créez un canal ou un planning global par défaut, affecté à chaque affichage avec une priorité de 1 (la moins élevée). En cas de problème avec les mises à jour de contenu (en raison du réseau, du lecteur, du serveur ou de la réplication), et étant donné que les lecteurs ont déjà mis ce contenu en cache sur le disque, le contenu en question devrait être lu correctement en évitant les écrans gris.

Tous les autres contenus, tels que les canaux ou les plannings, auront une priorité supérieure à 1, de sorte qu’un autre contenu sera prioritaire et que le contenu de canal ou de planning global (doté d’une priorité de 1) ne sera lu qu’en dernier recours.

## Gestion de canaux {#channel-management}

### 1. Quelle est la différence entre un canal en ligne et un canal hors ligne ?  {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***canal en ligne*** affiche le contenu mis à jour dans l’environnement en temps réel, alors qu’un ***canal hors ligne*** affiche le contenu en mémoire cache.

### 2. Comment mettre un canal en ligne ?  {#how-do-i-make-a-channel-online}

Sélectionnez le canal, puis accédez aux propriétés correspondantes depuis la barre d’actions. Cochez **Mode Développeur (forcer la mise en ligne du canal)** sous l’onglet **Canal** pour mettre le canal en ligne.

### 3. À quoi le champ Rôle du canal sert-il ?  {#what-is-the-use-of-the-channel-role-field}

Le champ Rôle du canal représente l’abstraction du canal réel exécuté pour permettre à l’auteur de se concentrer directement sur l’expérience générique. Vous pouvez le considérer comme un type de balise qui identifie de manière unique le canal dans son contexte (affichage ou planning).

### 4. Comment la résolution réelle du canal se produit-elle ?  {#how-does-actual-channel-resolution-happen}

*Références statiques* : la résolution suit simplement le chemin indiqué.

*Références dynamiques* : la résolution se produit une fois le canal affecté à l’affichage (et non au planning). Le chemin de l’affichage devient le contexte du canal et la résolution se produit comme suit (de la priorité la plus élevée à la plus faible) :

1. L’affichage comporte un nœud enfant qui correspond au nom du canal référencé.
1. L’affichage comporte un nœud frère qui correspond au nom du canal référencé.
1. L’emplacement parent de l’affichage comporte un nœud enfant qui correspond au nom du canal référencé.
1. L’emplacement parent principal de l’affichage comporte un nœud enfant qui correspond au nom du canal référencé.

Etc. jusqu’à ce que vous accédiez au dossier des emplacements et que vous vous en teniez là pour l’instant (vous ne pouvez donc pas référencer un canal qui se trouverait dans le dossier des canaux, par exemple, uniquement les canaux présents dans la sous-arborescence des emplacements).

### 5. Comment configurer la configuration hors ligne de la bibliothèque cliente personnalisée dans le canal AEM Screens ?

Lors de l’utilisation d’un code client personnalisé créé `clientlib` dans un canal AEM Screens, les étapes suivantes sont nécessaires pour s’assurer que la variable `clientlib` Les fichiers sont chargés correctement dans le canal (`manifest.json`) et contiendra le chemin d’accès de la variable `clientlib`.

Suivez les étapes ci-dessous à partir de l’éditeur de canal :

1. Sélectionnez un canal et cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur de canal.
1. Sélectionnez le composant dans lequel vous souhaitez ajouter le `clientlib`.
1. Cliquez sur le bouton de configuration (icône de clé à molette).
1. Accédez au **Configuration hors ligne** et ajoutez le chemin d’accès à votre bibliothèque cliente personnalisée dans **Bibliothèques côté client**.

## Enregistrement de périphériques {#device-registration}

### 1. Si je détecte des points de terminaison, tels que des requêtes d’intégration et d’enregistrement de périphériques, je peux créer un script pour un grand nombre de périphériques et les enregistrer. Outre le verrouillage sur la connexion Wi-Fi d’une succursale, la sécurisation de ces requêtes est-elle possible ?  {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

L’enregistrement n’est actuellement possible que sur l’instance d’auteur. Bien qu’il ne soit pas authentifié, le service d’enregistrement crée uniquement un périphérique en attente dans AEM ; il n’enregistre pas réellement le périphérique ni n’affecte aucun affichage.

Pour enregistrer un périphérique (c’est-à-dire créer un utilisateur pour le périphérique dans AEM), vous devez tout de même vous authentifier auprès de l’application et suivre manuellement les instructions de l’assistant d’enregistrement pour terminer l’enregistrement. En théorie, un utilisateur malveillant peut créer plusieurs périphériques en attente, mais il ne peut pas les enregistrer sans connexion à AEM.

### 2. Existe-t-il un moyen de transformer les requêtes HTTP GET en requêtes HTTP POST avec un type d’authentification donné ?  {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La requête d’enregistrement consiste dans une requête POST.

Il est recommandé d’obtenir l’ID du périphérique de la session au lieu de le transmettre en tant que paramètre. Ainsi, vous pouvez nettoyer les journaux du serveur, la mémoire cache du navigateur, etc. Il ne s’agit pas pour l’instant d’un problème de sécurité. Notez que la requête GET est utilisée en l’absence de modification d’état sur le serveur et que la requête POST est appliquée dans le cas contraire.

### 3. Existe-t-il un moyen de refuser une requête d’enregistrement d’appareil ?  {#is-there-a-way-to-decline-a-device-registration-request}

Vous ne pouvez pas refuser les requêtes d’enregistrement. Au lieu de cela, les demandes d’enregistrement doivent expirer au-delà d’un délai configuré dans `Adobe Experience Manager Web Console`. Par défaut, cette valeur est définie sur un jour et mise en mémoire cache.

## Rapports de surveillance et d’intégrité des périphériques {#device-monitoring-and-health-reports}

### 1. Comment résoudre le problème si mon lecteur AEM Screens affiche un écran noir ?  {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Vérifiez les possibilités suivantes pour résoudre le problème de l’écran noir :

* AEM ne peut pas diffuser le contenu hors ligne.
* Le canal ne comporte aucun contenu.
* Les ressources ne sont pas programmées pour apparaître à la date du jour.

### 2. Que faire si je ne peux pas enregistrer le lecteur AEM Screens et qu’il présente le statut d’échec ?  {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Vous devez activer le filtre Autoriser vide du référent Apache Sling. Cette activation est nécessaire pour optimiser le fonctionnement du protocole de contrôle entre le lecteur et le serveur AEM Screens.

1. Accédez à **Configuration de la console web Adobe Experience Manager**.
1. Cochez l’option **allow.empty**.
1. Cliquez sur **Enregistrer**.

### 3. Comment résoudre le problème si le périphérique et les journaux de la console affichent respectivement les messages d’erreur « ÉCHEC » et « ENAME_NOT_FOUND » pendant l’enregistrement du lecteur AEM Screens ?  {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Ce problème peut se produire si le lecteur ne parvient pas à trouver le nom DNS du serveur AEM Screens. Vous pouvez essayer d’utiliser l’adresse IP pour vous connecter. Pour obtenir l’adresse IP du serveur, utilisez la syntaxe suivante : *arp &lt;nom_dns_serveur>*.

### 4. AMS recommande-t-il de mettre en œuvre un outil de surveillance Android sur tous les périphériques ? Le module de surveillance (Cordova) est-il fourni dans le kit de package Android (APK) ?  {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un outil de surveillance Android multiplateforme utilisant des API Android pures est déjà disponible dans ce kit. Aucun autre logiciel n’est nécessaire, mais, selon l’appareil employé, vous devrez peut-être signer à nouveau le fichier apk Android afin d’obtenir des privilèges système pour un cycle d’alimentation complet (API PowerManager). En l’absence de nouvelle signature avec les clés du fabricant, ce kit peut fermer, puis relancer l’application, mais pas le cycle d’alimentation.

Pour plus d’informations sur la mise en œuvre du lecteur Android, reportez-vous à [**Mise en œuvre du lecteur Android**](implementing-android-player.md).

### 5. Quels outils (logiciels) tiers de surveillance et d’alerte à distance Adobe/AMS recommande-t-il d’utiliser pour surveiller chaque périphérique ?   {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Selon les résultats que vous souhaitez obtenir en dehors de la surveillance et des alertes, un nouveau service de notifications AEM Screens vous informe si un périphérique n’a pas envoyé de commande ping depuis longtemps. Les outils tiers dépendent du système d’exploitation utilisé et de ses fonctionnalités, ainsi que des besoins spécifiques du client.

Pour plus d’informations sur l’emplacement où vous pouvez surveiller l’activité des périphériques, reportez-vous à [**Service de notifications AEM Screens**](screens-notifications-service.md).

## Lecteur AEM Screens {#aem-screens-player}

### 1. Comment installer le lecteur Chrome OS en tant que module du navigateur Chrome ?  {#how-to-install-chromeos-player-as-chrome-browser-plugin}

Le lecteur Chrome OS peut être installé en tant que module du navigateur Chrome en mode Développeur sans que vous ayez à utiliser de lecteur Chrome réel. Pour l’installer, procédez comme suit :

1. Cliquez [ici](https://download.macromedia.com/screens/) pour télécharger la dernière version du lecteur Chrome.
1. Décompressez et enregistrez le fichier d’installation sur le disque.
1. Ouvrez le navigateur Chrome et sélectionnez **Extensions** dans le menu ou accédez directement à ***chrome://extensions***.
1. Activez le **mode Développeur** dans l’angle supérieur droit de l’écran.
1. Cliquez sur **Charger les fichiers décompressés** dans l’angle supérieur gauche et chargez le lecteur Chrome décompressé.
1. Vérifiez si le module **Lecteur Chrome AEM Screens** est disponible dans la liste des extensions.
1. Ouvrez un nouvel onglet et cliquez sur l’icône **Applications** dans l’angle supérieur gauche de l’écran ou accédez directement à ***chrome://applications***.
1. Cliquez sur le module **AEM Screens** pour lancer le lecteur Chrome. Par défaut, le lecteur est lancé en mode plein écran. Appuyez sur **Échap** pour quitter le mode plein écran.

### 2. Comment résoudre le problème si le lecteur Screens ne parvient pas à s’authentifier via l’instance de publication avec une balise d’erreur personnalisée ?  {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Le lecteur AEM Screens envoie une requête à ***/content/screens/svc.ping.json*** au démarrage et lorsqu’il affiche un message d’erreur 404. Il lance une requête d’authentification auprès de l’instance de publication. Si cette dernière comporte une balise d’erreur personnalisée, veillez à retourner le code de statut 404 pour l’utilisateur anonyme sur ***/content/screens/svc.ping.json***.

### 3. Comment configurer l’écran de l’appareil pour qu’il reste actif dans un lecteur Android ?  {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Pour activer l’option Rester éveillé sur un lecteur Android, procédez comme suit :

1. Accédez aux paramètres du lecteur Android —> **À propos de**
1. Appuyez 7 fois sur le numéro de version pour activer les **options du mode Développeur** dans **Paramètres.**
1. Accédez à **ces options**.
1. Activez **Rester éveillé**.

### 4. Comment activer le mode fenêtre dans le lecteur Windows ?{#enable-player}

Il n’existe pas de mode fenêtre dans le lecteur Windows. Celui-ci est toujours en mode Plein écran.

### 5. Comment résoudre le problème d’un lecteur AEM Screens qui envoie en continu des demandes de connexion ? {#requests-login}

Procédez comme suit pour résoudre les problèmes d’un lecteur AEM Screens qui envoie continuellement des requêtes à `/content/screens/svc.json` et `/libs/granite/core/content/login.validate/j_security_check` :

1. Lorsque le lecteur AEM Screens démarre, il le demande à `/content/screens/svc.json`. Lorsque le lecteur obtient un code d’état 404 en réponse, il initie une demande d’authentification à l’aide de `/libs/granite/core/content/login.validate/j_security_check` par rapport à l’instance de *publication*. Si l’instance de *publication* comporte un gestionnaire d’erreur personnalisé, veillez à retourner le code d’état 404 pour l’utilisateur anonyme sur `/content/screens/svc.json` ou `/content/screens/svc.ping.json`.

1. Vérifiez si votre configuration de Dispatcher autorise ces requêtes dans la `/filters`.

   Pour plus d’informations, voir la section [Configuration des filtres Screens](https://docs.adobe.com/content/help/fr-FR/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters).

1. Vérifiez si les règles de réécriture de Dispatcher réécrivent les chemins Screens vers un chemin différent.

1. Vérifiez si vous avez des règles `/etc/map` sur l’instance d’*auteur* ou de *publication* et si les chemins Screens correspondent à `sling:match` et sont redirigés en interne vers un autre chemin. La résolution de l’URL exacte dans `/system/console/jcrresolver` permet d’identifier si l’instance de *publication* réécrit ces URL vers un autre chemin d’accès.

1. Vérifiez si la configuration Apache Sling Resource Resolver Factory provoque des réécritures internes.

### 6. Comment obtenir les informations concernant l’affichage et le périphérique à partir de l’API du lecteur ?

Vous pouvez obtenir les informations sur l’affichage et le périphérique via :

* **une API JS interne** ;
* **une boutique ContextHub** : Trois magasins ContextHub sont définis dans `/libs/screens/clientlibs/contexthub` pour exposer les canaux, les périphériques et les informations d’affichage.

   Suivez les étapes ci-dessous pour utiliser ces valeurs de stockage ContentHub :

   * Modifiez les propriétés du canal et définissez le chemin ContextHub dans l’onglet de personnalisation sur la valeur (comme mentionné ci-dessus)
   * Dans le canal JS, vous pouvez utiliser :

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## Conseils pratiques de dépannage {#general-troubleshooting-tips}

### 1. Comment désactiver Livefyre pour éviter de recevoir un message d’erreur d’instance d’auteur et/ou de publication dans Screens ?  {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Pour désactiver Livefyre afin d’éviter les erreurs de journal :

1. ***Désactivez le lot Livefyre :***

   * Accédez à `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`.
   * Recherchez le lot AEM Livefyre : `com.adobe.cq.social.cq-social-livefyre`
   * Cliquez sur **Arrêter**.

1. ***Désactivez l’interrogateur Livefyre :***

   * Dans CRXDE Lite, accédez à `/etc/importers/polling/livefyre-poller/jcr:content`.
   * Ajoutez une nouvelle propriété de *type* booléenne *activée*.
   * Définissez la **propriété activée** sur **false**.

### 2. Comment ajouter des informations d’index Oak ?  {#add-oak-index-info}

AEM Screens crée des définitions d’index pour les requêtes utilisées par le produit.
Si des *AVERTISSEMENTS de requête de traversée* apparaissent dans `error.log`, créez un index personnalisé pour votre requête. Pour en savoir plus, consultez [Configuration des index](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=fr#configuring-the-indexes).

Vous pouvez également consulter une ressource supplémentaire dans la [documentation Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3. Éléments requis pour configurer les manifestes v3 {#configure-v3}

Pour activer le manifeste v3, vous devez :

* Mettez à jour Dispatcher.
Voir [Configuration de Dispatcher pour Manifest version v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=fr#configuring-dispatcherv3) pour plus d’informations.

* Mettre à jour le composant personnalisé.
Voir [Modèle pour les gestionnaires personnalisés](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=fr#custom-handlers) pour plus d’informations.

* Désactiver ContentSync dans `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* Activation de SmartSync dans `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.