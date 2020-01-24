---
title: Questions fréquentes sur AEM Screens
seo-title: Questions fréquentes sur AEM Screens
description: Consultez cette page pour obtenir des réponses aux questions fréquentes concernant un projet AEM Screens.
seo-description: Consultez cette page pour obtenir des réponses aux questions fréquentes concernant un projet AEM Screens.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: ht
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Questions fréquentes sur AEM Screens {#aem-screens-faqs}

La section suivante permet de répondre à une partie des questions fréquemment posées concernant un projet AEM Screens.

## Gestion de canaux {#channel-management}

### 1. Quelle est la différence entre un canal en ligne et un canal hors ligne ? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***canal en ligne ***affiche le contenu mis à jour dans l’environnement en temps réel, alors qu’un***canal hors ligne*** affiche le contenu en mémoire cache.

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

### 1. Si je détecte des points de terminaison, tels que des requêtes d’intégration et d’enregistrement de périphériques, je peux créer un script pour un grand nombre de périphériques et les enregistrer. Outre le verrouillage sur la connexion Wi-Fi d&#39;une succursale, la sécurisation de ces requêtes est-elle possible ? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

L’enregistrement n’est actuellement possible que sur l’instance d’auteur. Bien qu’il ne soit pas authentifié, le service d’enregistrement crée uniquement un périphérique en attente dans AEM ; il n’enregistre pas réellement le périphérique ni n’affecte aucun affichage.

Pour enregistrer un périphérique (c’est-à-dire créer un utilisateur pour le périphérique dans AEM), vous devez tout de même vous authentifier auprès de l’application et suivre manuellement les instructions de l’assistant d’enregistrement pour terminer l’enregistrement. En théorie, un utilisateur malveillant peut créer plusieurs périphériques en attente, mais il ne peut pas les enregistrer sans connexion à AEM.

### 2. Existe-t-il un moyen de transformer les requêtes HTTP GET en requêtes HTTP POST avec un type d’authentification donné ? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La requête d’enregistrement consiste dans une requête POST.

Il est recommandé d’obtenir l’ID du périphérique de la session au lieu de le transmettre en tant que paramètre. Ainsi, vous pouvez nettoyer les journaux du serveur, la mémoire cache du navigateur, etc. Il ne s&#39;agit pas pour l’instant d&#39;un problème de sécurité. Notez que la requête sémantique GET est utilisée en l&#39;absence de modification du statut sur le serveur et que la requête POST est appliquée dans le cas contraire.

### 3. Existe-t-il un moyen de refuser une requête d&#39;enregistrement de périphérique ? {#is-there-a-way-to-decline-a-device-registration-request}

Vous ne pouvez pas refuser les requêtes d’enregistrement. Elles doivent au contraire expirer après un délai configuré dans la [console Web Adobe Experience Manager](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceI). Par défaut, cette valeur est définie sur un jour et mise en mémoire cache.

## Rapports de surveillance et d’intégrité des périphériques {#device-monitoring-and-health-reports}

### 1. Comment résoudre le problème si mon lecteur AEM Screens affiche un écran noir ? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Vérifiez les possibilités suivantes pour résoudre le problème de l’écran noir :

* AEM ne peut pas diffuser le contenu hors ligne.
* Le canal ne comporte aucun contenu.
* Les ressources ne sont pas programmées pour apparaître à la date du jour.

### 2. Que faire si je ne peux pas enregistrer le lecteur AEM Screens et qu’il présente le statut d’échec ? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Vous devez activer le filtre Autoriser vide du référent Apache Sling. Cette activation est nécessaire pour optimiser le fonctionnement du protocole de contrôle entre le lecteur et le serveur AEM Screens.

1. Accédez à **Configuration de la console Web Adobe Experience Manager**.
1. Cochez l’option **allow.empty**.
1. Cliquez sur **Enregistrer**.

### 3. Comment résoudre le problème si le périphérique et les journaux de la console affichent respectivement les messages d’erreur « ÉCHEC » et « ENAME_NOT_FOUND » pendant l’enregistrement du lecteur AEM Screens ? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Ce problème peut se produire si le lecteur ne parvient pas à trouver le nom DNS du serveur AEM Screens. Vous pouvez essayer d’utiliser l’adresse IP pour vous connecter. Pour obtenir l’adresse IP du serveur, utilisez la syntaxe suivante : *arp &lt;nom_dns_serveur>*.

### 4. AMS recommande-t-il de mettre en œuvre un outil de surveillance Android sur tous les périphériques ? Le module de surveillance (Cordova) est-il fourni dans le kit de package Android (APK) ? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un outil de surveillance Android multiplateforme utilisant des API Android pures est déjà disponible dans ce kit. Aucun autre logiciel n&#39;est nécessaire mais, selon le périphérique employé, vous devrez peut-être retirer le kit de package Android afin d’obtenir des privilèges système pour un cycle d&#39;alimentation complet (API PowerManager). En l’absence de retrait via les clés du fabricant, ce kit permet de fermer, puis de relancer l&#39;application, mais pas le cycle d&#39;alimentation.

Pour plus d’informations sur la mise en œuvre du lecteur Android, reportez-vous à [**Mise en œuvre du lecteur Android **](implementing-android-player.md).

### 5. Quels outils (logiciels) tiers de surveillance et d’alerte à distance Adobe/AMS recommande-t-il d’utiliser pour surveiller chaque périphérique ?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Selon les résultats que vous souhaitez obtenir en dehors de la surveillance et des alertes, un nouveau service de notifications AEM Screens vous informe si un périphérique n’a pas envoyé de commande ping depuis longtemps. Les outils tiers dépendent du système d’exploitation utilisé et de ses fonctionnalités, ainsi que des besoins spécifiques du client.

Pour plus d’informations sur l’emplacement où vous pouvez surveiller l’activité des périphériques, reportez-vous à [**Service de notifications AEM Screens **](screens-notifications-service.md).

## Lecteur AEM Screens {#aem-screens-player}

### 1. Comment installer le lecteur Chrome OS en tant que module du navigateur Chrome ? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

Le lecteur Chrome OS peut être installé en tant que module du navigateur Chrome en mode Développeur sans que vous ayez à utiliser de lecteur Chrome réel. Pour l’installer, procédez comme suit :

1. Cliquez [ici](https://download.macromedia.com/screens/) pour télécharger la dernière version du lecteur Chrome.
1. Décompressez et enregistrez le fichier d’installation sur le disque.
1. Ouvrez le navigateur Chrome, cliquez sur le menu à 3 points, puis sélectionnez **Plus d’outils** —> **Extensions** dans l’angle supérieur droit de l’écran ou accédez directement à ***chrome://extensions ***.
1. Activez le **mode Développeur** dans l’angle supérieur droit de l’écran.
1. Cliquez sur **Charger les fichiers décompressés** dans l’angle supérieur gauche et chargez le lecteur Chrome décompressé.
1. Vérifiez si le module **Lecteur Chrome AEM Screens** est disponible dans la liste des extensions.
1. Ouvrez un nouvel onglet et cliquez sur l’icône **Applications** dans l’angle supérieur gauche de l’écran ou accédez directement à ***chrome://applications ***.
1. Cliquez sur le module **AEM Screens** pour lancer le lecteur Chrome. Par défaut, le lecteur est lancé en mode plein écran. Appuyez sur **Échap** pour quitter le mode plein écran.

### 2. Comment résoudre le problème si le lecteur Screens ne parvient pas à s’authentifier via l’instance de publication avec une balise d’erreur personnalisée ? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Le lecteur AEM Screens envoie une requête à ***/content/screens/svc.ping.json ***au démarrage et lorsqu’il affiche un message d’erreur 404. Il lance une requête d’authentification auprès de l’instance de publication. Si cette dernière comporte une balise d’erreur personnalisée, veillez à retourner le code de statut 404 pour l’utilisateur anonyme sur***/content/screens/svc.ping.json***.

### 3. Comment configurer l&#39;écran du périphérique pour qu&#39;il reste actif dans un lecteur Android ? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Pour activer l’option Rester éveillé sur un lecteur Android, procédez comme suit :

1. Accédez aux paramètres du lecteur Android —> **À propos de**
1. Appuyez 7 fois sur le numéro de version pour activer les **options du mode Développeur** dans **Paramètres.**
1. Accédez à **ces options**.
1. Activez **Rester éveillé**.

## Conseils pratiques de dépannage {#general-troubleshooting-tips}

### 1. Comment désactiver Livefyre pour éviter de recevoir un message d’erreur d’instance d&#39;auteur et/ou de publication dans Screens ? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Pour désactiver Livefyre afin d’éviter les erreurs de journal :

1. ***Désactivez le lot Livefyre :***

   * Accédez à `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`.
   * Recherchez le lot AEM Livefyre : `com.adobe.cq.social.cq-social-livefyre`
   * Cliquez sur **Arrêter**.

1. ***Désactivez l’interrogateur Livefyre :***

   * Dans CRXDE Lite, accédez à `/etc/importers/polling/livefyre-poller/jcr:content`.
   * Ajoutez une nouvelle propriété de *type* booléenne *activée*.
   * Définissez la **propriété activée** sur **false**.

