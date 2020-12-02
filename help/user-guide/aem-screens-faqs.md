---
title: Questions fréquentes sur AEM Screens
seo-title: Questions fréquentes sur AEM Screens
description: Consultez cette page pour obtenir des réponses aux questions fréquentes concernant un projet AEM Screens.
seo-description: Consultez cette page pour obtenir des réponses aux questions fréquentes concernant un projet AEM Screens.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 359c15d16c83e5d3cecee0bbe2ef7e68a815e660
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 86%

---


# Questions fréquentes sur AEM Screens {#aem-screens-faqs}

La section suivante permet de répondre à une partie des questions fréquemment posées concernant un projet AEM Screens.

## Problème d’écran vide {#blank-screen}

>[!NOTE]
>La liste des contrôles obligatoires qui doivent être testés par l&#39;assistance Principale ou l&#39;assistance côté client avant de soulever un problème.

### 1. Quelles doivent être les étapes de dépannage de Premiers soins pour tout client faisant face à un écran noir ou à un contenu non lu ? {#troubleshooting-blank-screen}

* Vérifiez si la prévisualisation de canal fonctionne.
* Vérifier si la prévisualisation d&#39;affichage fonctionne
* Essayez d&#39;enregistrer le lecteur en tant qu&#39;extension de navigateur sur votre système pour le même affichage et vérifiez si cela fonctionne.
* Lorsque le lecteur est en cours d’exécution sur votre système, accédez à `http://localhost:24502`. Vérifiez si tout le contenu est correctement téléchargé.
* Vérifiez les ressources pour lesquelles les rendus appropriés sont créés et le rendu correct est en cours de lecture.
* Recherchez tout contenu planifié et si les heures sont correctes. Vérifiez si l’heure configurée dans le lecteur est correcte.
* Inspect la console du lecteur enregistre et vérifie les erreurs éventuelles. Cliquez avec le bouton droit de la souris et examinez les journaux de la console pour afficher ces derniers. Si vous utilisez le lecteur windows, appuyez sur `CTRL + ALT +I` pour afficher la console de développement pour vue les journaux.

## Gestion de canaux {#channel-management}

### 1. Quelle est la différence entre un canal en ligne et un canal hors ligne ? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***canal en ligne*** affiche le contenu mis à jour dans l’environnement en temps réel, alors qu’un ***canal hors ligne*** affiche le contenu en mémoire cache.

### 2. Comment mettre un canal en ligne ? {#how-do-i-make-a-channel-online}

Sélectionnez le canal, puis accédez aux propriétés correspondantes depuis la barre d’actions. Cochez **Mode Développeur (forcer la mise en ligne du canal)** sous l’onglet **Canal** pour mettre le canal en ligne.

### 3. À quoi le champ Rôle du canal sert-il ? {#what-is-the-use-of-the-channel-role-field}

Le champ Rôle du canal représente l’abstraction du canal réel exécuté pour permettre à l’auteur de se concentrer directement sur l’expérience générique. Vous pouvez le considérer comme un type de balise qui identifie de manière unique le canal dans son contexte (affichage ou planning).

### 4. Comment la résolution réelle du canal se produit-elle ? {#how-does-actual-channel-resolution-happen}

*Références statiques* : la résolution suit simplement le chemin indiqué.

*Références dynamiques* : la résolution se produit une fois le canal affecté à l’affichage (et non au planning). Le chemin de l’affichage devient le contexte du canal et la résolution se produit comme suit (de la priorité la plus élevée à la plus faible) :

1. L’affichage comporte un nœud enfant qui correspond au nom du canal référencé.
1. L’affichage comporte un nœud frère qui correspond au nom du canal référencé.
1. L’emplacement parent de l’affichage comporte un nœud enfant qui correspond au nom du canal référencé.
1. L’emplacement parent principal de l’affichage comporte un nœud enfant qui correspond au nom du canal référencé.

Etc. jusqu’à ce que vous accédiez au dossier des emplacements et que vous vous en teniez là pour l’instant (vous ne pouvez donc pas référencer un canal qui se trouverait dans le dossier des canaux, par exemple, uniquement les canaux présents dans la sous-arborescence des emplacements).

## Enregistrement de périphériques {#device-registration}

### 1. Si je détecte des points de terminaison, tels que des requêtes d’intégration et d’enregistrement de périphériques, je peux créer un script pour un grand nombre de périphériques et les enregistrer. Outre le verrouillage sur la connexion Wi-Fi d’une succursale, la sécurisation de ces requêtes est-elle possible ? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

L’enregistrement n’est actuellement possible que sur l’instance d’auteur. Bien qu’il ne soit pas authentifié, le service d’enregistrement crée uniquement un périphérique en attente dans AEM ; il n’enregistre pas réellement le périphérique ni n’affecte aucun affichage.

Pour enregistrer un périphérique (c’est-à-dire créer un utilisateur pour le périphérique dans AEM), vous devez tout de même vous authentifier auprès de l’application et suivre manuellement les instructions de l’assistant d’enregistrement pour terminer l’enregistrement. En théorie, un utilisateur malveillant peut créer plusieurs périphériques en attente, mais il ne peut pas les enregistrer sans connexion à AEM.

### 2. Existe-t-il un moyen de transformer les requêtes HTTP GET en requêtes HTTP POST avec un type d’authentification donné ? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La requête d’enregistrement consiste dans une requête POST.

Il est recommandé d’obtenir l’ID du périphérique de la session au lieu de le transmettre en tant que paramètre. Ainsi, vous pouvez nettoyer les journaux du serveur, la mémoire cache du navigateur, etc. Il ne s’agit pas pour l’instant d’un problème de sécurité. Notez que la requête GET est utilisée en l’absence de modification d’état sur le serveur et que la requête POST est appliquée dans le cas contraire.

### 3. Existe-t-il un moyen de refuser une requête d’enregistrement d’appareil ? {#is-there-a-way-to-decline-a-device-registration-request}

Vous ne pouvez pas refuser les requêtes d’enregistrement. Elles doivent au contraire expirer après un délai configuré dans la [console web Adobe Experience Manager](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl). Par défaut, cette valeur est définie sur un jour et mise en mémoire cache.

## Rapports de surveillance et d’intégrité des périphériques {#device-monitoring-and-health-reports}

### 1. Comment résoudre le problème si mon lecteur AEM Screens affiche un écran noir ? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Vérifiez les possibilités suivantes pour résoudre le problème de l’écran noir :

* AEM ne peut pas diffuser le contenu hors ligne.
* Le canal ne comporte aucun contenu.
* Les ressources ne sont pas programmées pour apparaître à la date du jour.

### 2. Que faire si je ne peux pas enregistrer le lecteur AEM Screens et qu’il présente le statut d’échec ? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Vous devez activer le filtre Autoriser vide du référent Apache Sling. Cette activation est nécessaire pour optimiser le fonctionnement du protocole de contrôle entre le lecteur et le serveur AEM Screens.

1. Accédez à **Configuration de la console web Adobe Experience Manager**.
1. Cochez l’option **allow.empty**.
1. Cliquez sur **Enregistrer**.

### 3. Comment résoudre le problème si le périphérique et les journaux de la console affichent respectivement les messages d’erreur « ÉCHEC » et « ENAME_NOT_FOUND » pendant l’enregistrement du lecteur AEM Screens ? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Ce problème peut se produire si le lecteur ne parvient pas à trouver le nom DNS du serveur AEM Screens. Vous pouvez essayer d’utiliser l’adresse IP pour vous connecter. Pour obtenir l’adresse IP du serveur, utilisez la syntaxe suivante : *arp &lt;nom_dns_serveur>*.

### 4. AMS recommande-t-il de mettre en œuvre un outil de surveillance Android sur tous les périphériques ? Le module de surveillance (Cordova) est-il fourni dans le kit de package Android (APK) ? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un outil de surveillance Android multiplateforme utilisant des API Android pures est déjà disponible dans ce kit. Aucun autre logiciel n’est nécessaire, mais, selon l’appareil employé, vous devrez peut-être signer à nouveau le fichier apk Android afin d’obtenir des privilèges système pour un cycle d’alimentation complet (API PowerManager). En l’absence de nouvelle signature avec les clés du fabricant, ce kit peut fermer, puis relancer l’application, mais pas le cycle d’alimentation.

Pour plus d’informations sur la mise en œuvre du lecteur Android, reportez-vous à [**Mise en œuvre du lecteur Android**](implementing-android-player.md).

### 5. Quels outils (logiciels) tiers de surveillance et d’alerte à distance Adobe/AMS recommande-t-il d’utiliser pour surveiller chaque périphérique ?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Selon les résultats que vous souhaitez obtenir en dehors de la surveillance et des alertes, un nouveau service de notifications AEM Screens vous informe si un périphérique n’a pas envoyé de commande ping depuis longtemps. Les outils tiers dépendent du système d’exploitation utilisé et de ses fonctionnalités, ainsi que des besoins spécifiques du client.

Pour plus d’informations sur l’emplacement où vous pouvez surveiller l’activité des périphériques, reportez-vous à [**Service de notifications AEM Screens**](screens-notifications-service.md).

## Lecteur AEM Screens {#aem-screens-player}

### 1. Comment installer le lecteur Chrome OS en tant que module du navigateur Chrome ? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

Le lecteur Chrome OS peut être installé en tant que module du navigateur Chrome en mode Développeur sans que vous ayez à utiliser de lecteur Chrome réel. Pour l’installer, procédez comme suit :

1. Cliquez [ici](https://download.macromedia.com/screens/) pour télécharger la dernière version du lecteur Chrome.
1. Décompressez et enregistrez le fichier d’installation sur le disque.
1. Ouvrez le navigateur Chrome et sélectionnez **Extensions** dans le menu ou accédez directement à ***chrome://extensions***.
1. Activez le **mode Développeur** dans l’angle supérieur droit de l’écran.
1. Cliquez sur **Charger les fichiers décompressés** dans l’angle supérieur gauche et chargez le lecteur Chrome décompressé.
1. Vérifiez si le module **Lecteur Chrome AEM Screens** est disponible dans la liste des extensions.
1. Ouvrez un nouvel onglet et cliquez sur l’icône **Applications** dans l’angle supérieur gauche de l’écran ou accédez directement à ***chrome://applications***.
1. Cliquez sur le module **AEM Screens** pour lancer le lecteur Chrome. Par défaut, le lecteur est lancé en mode plein écran. Appuyez sur **Échap** pour quitter le mode plein écran.

### 2. Comment résoudre le problème si le lecteur Screens ne parvient pas à s’authentifier via l’instance de publication avec une balise d’erreur personnalisée ? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Le lecteur AEM Screens envoie une requête à ***/content/screens/svc.ping.json*** au démarrage et lorsqu’il affiche un message d’erreur 404. Il lance une requête d’authentification auprès de l’instance de publication. Si cette dernière comporte une balise d’erreur personnalisée, veillez à retourner le code de statut 404 pour l’utilisateur anonyme sur ***/content/screens/svc.ping.json***.

### 3. Comment configurer l’écran de l’appareil pour qu’il reste actif dans un lecteur Android ? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Pour activer l’option Rester éveillé sur un lecteur Android, procédez comme suit :

1. Accédez aux paramètres du lecteur Android —> **À propos de**
1. Appuyez 7 fois sur le numéro de version pour activer les **options du mode Développeur** dans **Paramètres.**
1. Accédez à **ces options**.
1. Activez **Rester éveillé**.

### 4. Comment activer le mode fenêtre dans le lecteur Windows ?{#enable-player}

Il n’existe pas de mode fenêtre dans le lecteur Windows. Celui-ci est toujours en mode Plein écran.

### 5. Comment résoudre le problème d’un lecteur AEM Screens qui envoie en continu des demandes de connexion ?{#requests-login}

Procédez comme suit pour résoudre les problèmes d’un lecteur AEM Screens qui envoie continuellement des requêtes à `/content/screens/svc.json` et `/libs/granite/core/content/login.validate/j_security_check` :

1. Lorsque le lecteur AEM Screens démarre, il le demande à `/content/screens/svc.json`. Lorsque le lecteur obtient un code d’état 404 en réponse, il initie une demande d’authentification à l’aide de `/libs/granite/core/content/login.validate/j_security_check` par rapport à l’instance de *publication*. Si l&#39;instance de *publication* comporte un gestionnaire d’erreur personnalisé, veillez à retourner le code d’état 404 pour l’utilisateur anonyme sur `/content/screens/svc.json` ou `/content/screens/svc.ping.json`.

1. Vérifiez si votre configuration de Dispatcher autorise ces requêtes dans la `/filters`.

   Pour plus d’informations, voir la section [Configuration des filtres Screens](https://docs.adobe.com/content/help/fr-FR/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters).

1. Vérifiez si les règles de réécriture de Dispatcher réécrivent les chemins Screens vers un chemin différent.

1. Vérifiez si vous avez des règles `/etc/map` sur l&#39;instance d’*auteur* ou de *publication* et si les chemins Screens correspondent à `sling:match` et sont redirigés en interne vers un autre chemin. La résolution de l’URL exacte dans /`/system/console/jcrresolver` permet d’identifier si l’instance de *publication* réécrit ces URL vers un autre chemin d’accès.

1. Vérifiez si la configuration Apache Sling Resource Resolver Factory provoque des réécritures internes.

## Conseils pratiques de dépannage {#general-troubleshooting-tips}

### 1. Comment désactiver Livefyre pour éviter de recevoir un message d’erreur d’instance d’auteur et/ou de publication dans Screens ? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Pour désactiver Livefyre afin d’éviter les erreurs de journal :

1. ***Désactivez le lot Livefyre :***

   * Accédez à `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`.
   * Recherchez le lot AEM Livefyre : `com.adobe.cq.social.cq-social-livefyre`
   * Cliquez sur **Arrêter**.

1. ***Désactivez l’interrogateur Livefyre :***

   * Dans CRXDE Lite, accédez à `/etc/importers/polling/livefyre-poller/jcr:content`.
   * Ajoutez une nouvelle propriété de *type* booléenne *activée*.
   * Définissez la **propriété activée** sur **false**.

### 2. Comment Ajouter l&#39;information sur l&#39;indice de chêne ? {#add-oak-index-info}

AEM Screens crée des définitions d’index pour les requêtes utilisées par le produit.
S&#39;il y a des WARN *Requête Traversal* dans `error.log`, créez un index personnalisé pour votre requête. Voir [Configuration des index](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) pour plus d&#39;informations.

Vous pouvez également consulter une ressource supplémentaire sur [Oak Documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


