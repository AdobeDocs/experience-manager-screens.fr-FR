---
title: FAQ sur les écrans AEM
seo-title: FAQ sur les écrans AEM
description: Suivez cette page pour obtenir des réponses aux questions fréquentes relatives à un projet AEM Screens.
seo-description: Suivez cette page pour obtenir des réponses aux questions fréquentes relatives à un projet AEM Screens.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# FAQ sur les écrans AEM {#aem-screens-faqs}

La section suivante fournit des réponses à quelques-unes des questions fréquentes relatives à un projet AEM Screens.

## Gestion des canaux {#channel-management}

### 1. Quelle est la différence entre un canal en ligne et un canal hors ligne ? {#what-is-the-difference-between-an-online-and-an-offline-channel}

An ***Online Channel***, will show the updated content in the real time environment whereas an ***Offline Channel***, shows the cached content.

### 2. Comment faire un canal en ligne ? {#how-do-i-make-a-channel-online}

Sélectionnez le canal et accédez aux propriétés du canal à partir de la barre d’actions. Vérifiez le mode **Développeur (forcer le canal à être en ligne)** sous l’onglet **Canal** pour mettre le canal en ligne.

### 3. À quoi sert le champ Rôle de canal ? {#what-is-the-use-of-the-channel-role-field}

Le rôle de canal est l’abstraction du canal réel qui est exécuté afin que l’auteur puisse se concentrer directement sur l’expérience générique. Vous pouvez le considérer comme une sorte de balise qui identifie de manière unique le canal dans son contexte (affichage ou planification).

### 4. Comment la résolution réelle du canal se produit-elle ? {#how-does-actual-channel-resolution-happen}

Pour les références ** statiques, la résolution suit simplement le chemin spécifié.

Pour les références ** dynamiques, la résolution se produit une fois que le canal est affecté à l’affichage (et non à la planification). Le chemin d’affichage devient le contexte du canal et la résolution se produit comme suit (priorité la plus élevée à la plus faible) :

1. L’affichage comporte un noeud enfant qui correspond au nom du canal référencé.
1. L’affichage comporte un noeud frère qui correspond au nom du canal référencé.
1. L’emplacement parent de l’affichage comporte un noeud enfant qui correspond au nom du canal référencé.
1. L’emplacement parent principal de l’affichage comporte un noeud enfant qui correspond au nom du canal référencé.

Et ainsi de suite, jusqu’à ce que vous atteigniez le dossier des emplacements et que vous vous arrêtiez là pour le moment (vous ne pouvez donc pas référencer un canal qui se trouverait dans le dossier des canaux, par exemple, uniquement les canaux dans la sous-arborescence des emplacements).

## Enregistrement de périphérique {#device-registration}

### 1. Si je découvre des points de fin tels que les demandes d'intégration et d'enregistrement de périphériques, je peux écrire un script pour un grand nombre de périphériques et enregistrer ces périphériques. En plus de verrouiller cela sur une branche Wi-Fi, est-il possible de sécuriser ces demandes? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Actuellement, l’enregistrement n’est possible que sur l’instance d’auteur. Bien que le service d’enregistrement ne soit pas authentifié, il crée uniquement un périphérique en attente dans AEM et n’enregistre pas réellement le périphérique ni n’affecte aucun affichage.

Pour enregistrer un périphérique (c’est-à-dire créer un utilisateur pour le périphérique dans AEM), vous devez tout de même vous authentifier auprès d’AEM et suivre actuellement manuellement l’assistant d’enregistrement pour terminer l’enregistrement. En théorie, un utilisateur malveillant peut créer plusieurs périphériques en attente, mais ne peut pas en enregistrer sans connexion à AEM.

### 2. Existe-t-il un moyen de transformer les requêtes HTTP GET en HTTP POST avec une certaine forme d’authentification ? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La demande d’enregistrement est une demande POST.

Il est recommandé d’obtenir l’ID de périphérique de la session plutôt que de le transmettre en tant que paramètre. Cela nettoierait les journaux du serveur, le cache du navigateur, etc. Il ne s'agit pas actuellement d'un problème de sécurité. Notez que GET sémantique est utilisé lorsqu’il n’y a aucune modification de l’état sur le serveur et que POST est utilisé en cas de modification de l’état.

### 3. Y a-t-il un moyen de refuser une demande d'enregistrement d'appareil ? {#is-there-a-way-to-decline-a-device-registration-request}

Vous ne pouvez pas refuser les demandes d’enregistrement. Les demandes d’enregistrement doivent expirer après un délai d’expiration configuré dans la console [Web](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl)Adobe Experience Manager. Par défaut, cette valeur est définie sur un jour et est stockée dans un cache mémoire.

## Rapports de surveillance et d’intégrité des périphériques {#device-monitoring-and-health-reports}

### 1. Comment résoudre les problèmes si mon lecteur AEM Screens affiche un écran vide ? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Vérifiez les possibilités suivantes pour résoudre le problème de l’écran vide :

* AEM ne peut pas diffuser le contenu hors ligne
* Le canal ne comporte aucun contenu
* Aucune des ressources n’est planifiée pour s’afficher à l’heure actuelle.

### 2. Que dois-je faire si le lecteur AEM Screens ne peut pas s’enregistrer et que son état s’affiche comme échec ? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Vous devez activer le filtre Apache Sling Referrer Filter Allow Empty. Cette activation est nécessaire pour un fonctionnement optimal du protocole de contrôle entre le lecteur et le serveur AEM Screens.

1. Navigate to **Adobe Experience Manager Web Console Configuration**
1. Cochez l’option **allow.empty **.
1. Cliquez sur **Enregistrer**.

### 3. Comment dépanner si, lors de l’enregistrement d’un lecteur AEM Screens, le périphérique affiche FAILURE et que les journaux de la console affichent une erreur ENAME_NOT_FOUND ? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Ce problème peut se produire si le lecteur ne parvient pas à trouver le DNS du serveur AEM Screens. Vous pouvez essayer d’utiliser l’adresse IP pour vous connecter. Pour obtenir l’adresse IP du serveur, utilisez : *arp &lt;nom_dns_serveur&gt;*.

### 4. AMS recommande-t-il de mettre en oeuvre un outil de contrôle Android sur tous les périphériques ? Le plug-in Watchdog (Cordova) est-il inclus dans l'APK ? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un chien de garde multiplateforme Android utilisant des API Android pures fait déjà partie du kit. Aucun logiciel supplémentaire n'est nécessaire, mais en fonction du périphérique utilisé, vous devrez peut-être déconnecter le module pour obtenir des privilèges système pour un cycle d'alimentation complet (Powermanager api). S'il n'est pas démissionné à l'aide des clés du fabricant, il se ferme et redémarre l'application, mais pas le cycle d'alimentation.

Pour plus d'informations sur la mise en oeuvre d'Android Player, reportez-vous à [**Mise en oeuvre d'Android Player**](implementing-android-player.md).

### 5. Quels outils tiers de surveillance et d’alerte à distance (logiciels) Adobe/AMS recommande-t-il pour surveiller chaque périphérique ?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

En fonction de ce que vous souhaitez en dehors de la surveillance et des alertes, un nouveau service de notifications d’AEM Screens vous avertit si un périphérique n’a pas encore effectué de pinglage pendant un certain temps. Les outils tiers dépendent de votre système d’exploitation (système d’exploitation), de ses fonctionnalités et des besoins spécifiques du client.

Pour plus d’informations sur l’emplacement où vous pouvez surveiller l’activité des périphériques, reportez-vous au service [**de notifications d’**](screens-notifications-service.md)AEM Screens.

## Lecteur AEM Screens {#aem-screens-player}

### 1. Comment installer le lecteur ChromeOS en tant que module complémentaire du navigateur Chrome ? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

Le lecteur ChromeOS peut être installé en tant que module externe Chrome Browser en mode développeur sans nécessiter de périphérique de lecteur Chrome réel. Pour l’installation, procédez comme suit :

1. Cliquez [ici](https://download.macromedia.com/screens/) pour télécharger la dernière version de Chrome Player.
1. Décompressez et enregistrez-le sur le disque.
1. Ouvrez le navigateur Chrome, cliquez sur le menu à 3 points et sélectionnez **Plus d’outils** —&gt; **Extensions** dans le coin supérieur droit ou accédez directement à ***chrome://extensions***.
1. Activez le mode **** Développeur depuis le coin supérieur droit.
1. Cliquez sur **Charger les fichiers décompressés **depuis le coin supérieur gauche et chargez le lecteur Chrome décompressé.
1. Vérifiez **AEM Screens Chrome Player** plugin si disponible dans la liste des extensions.
1. Ouvrez un nouvel onglet et cliquez sur l’icône **Applications** dans le coin supérieur gauche ou accédez directement à ***chrome://apps***.
1. Cliquez sur **AEM Screens** Plugin pour lancer Chrome Player. Par défaut, le lecteur est lancé en mode plein écran. Appuyez sur **esc** pour quitter le mode plein écran.

### 2. Comment résoudre le problème si le lecteur d’écrans ne parvient pas à s’authentifier via l’instance de publication avec un gestionnaire d’erreurs personnalisé ? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Lorsque le lecteur AEM Screens démarre, il envoie une requête à ***/content/screens/svc.ping.json***, lorsque le lecteur reçoit une erreur 404. Le lecteur initie une demande d’authentification pour l’authentification auprès de l’instance de publication. S’il existe un gestionnaire d’erreurs personnalisé dans l’instance de publication, veillez à renvoyer le code d’état 404 pour l’utilisateur anonyme sur ***/content/screens/svc.ping.json***.

### 3. Comment configurer l'écran du périphérique pour qu'il reste allumé dans un lecteur Android ? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Suivez les étapes ci-dessous pour activer l’option Rester éveillé sur n’importe quel lecteur Android :

1. Accédez aux paramètres du lecteur Android —&gt; **A propos de**
1. Appuyez 7 fois sur le numéro de version pour activer les options **du** développeur dans les **paramètres.**
1. Accédez aux options **du développeur**
1. Activer le **réveil**

## Conseils généraux de résolution des incidents {#general-troubleshooting-tips}

### 1. Comment désactiver Livefyre pour éviter une erreur des écrans A/P ? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Afin de désactiver Livefyre pour éviter les erreurs de journal :

1. ***Désactiver le lot Livefyre :***

   * Accéder à `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * Recherchez le lot AEM Livefyre : `com.adobe.cq.social.cq-social-livefyre`
   * Cliquez sur **Arrêter**

1. ***Désactiver le pollen Livefyre :***

   * Dans CRXDE Lite, accédez à `/etc/importers/polling/livefyre-poller/jcr:content`
   * Ajouter une nouvelle propriété *de type* Boolean activée **
   * Définir la propriété **** activée sur **false**

