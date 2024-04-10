---
title: Mise en œuvre d’Android&trade; Player
description: Découvrez l’implémentation d’Android&trade; Watchdog, une solution qui vous permet de récupérer le lecteur Android&trade; suite à une panne.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 35%

---

# Mise en œuvre d’Android™ Player {#implementing-android-player}

Cette section décrit la configuration du lecteur Android™. Elle fournit des informations sur le fichier de configuration, les options disponibles, ainsi que des recommandations indiquant quels paramètres utiliser pour le développement et le test.

En outre, **Chien de garde** est une solution permettant de récupérer le lecteur suite à une panne. Une application doit s’enregistrer auprès du service watchdog, puis envoyer périodiquement des messages au service indiquant qu’elle est active. Si le service watchdog ne reçoit pas de message de maintien en vie dans un délai spécifié, le service tente de redémarrer l&#39;appareil pour une récupération correcte (s&#39;il dispose des privilèges suffisants) ou de redémarrer l&#39;application.

## Installation d’Android™ Player {#installing-android-player}

Pour mettre en œuvre Android™ Player pour AEM Screens, installez Android™ Player pour AEM Screens.

Consultez la page [**Téléchargements du lecteur AEM 6.5**](https://download.macromedia.com/screens/).

### Configuration de l’environnement pour le Service Pack AEM Screens 6.5.5 {#fp-environment-setup}

>[!NOTE]
>Configurez un environnement pour le lecteur Android™ si vous utilisez le pack de services AEM Screens 6.5.5.

Définissez la valeur de **SameSite attribute for the login-token cookies** de **Lax** sur **None** dans **Configuration de la console Web Adobe
Experience Manager** sur toutes les instances de création et de publication AEM.

Suivez les étapes ci-dessous :

1. Accédez à **Configuration de la console Web Adobe
Experience Manager** en utilisant `http://localhost:4502/system/console/configMgr`.

1. Recherchez *Adobe Granite Token Authentication Handler*.

1. Changez la valeur de **SameSite attribute for the login-token cookies** de **Lax** à **None**.
   ![image](/help/user-guide/assets/granite-updates.png)

1. Cliquez sur **Save**.


### Méthode ad hoc {#ad-hoc-method}

La méthode ad hoc vous permet d’installer le dernier lecteur Android™ (*.exe*). Visitez la page [**Téléchargements du lecteur AEM 6.5**](https://download.macromedia.com/screens/).

Une fois l’application téléchargée, suivez les étapes du lecteur pour terminer l’installation ad hoc :

1. Appuyez de manière prolongée sur dans le coin supérieur gauche pour ouvrir le panneau d’administration.
1. Accédez à **Configuration** depuis le menu d’actions de gauche et saisissez l’emplacement (adresse) de l’instance AEM à laquelle vous souhaitez vous connecter, puis cliquez sur **Enregistrer**.

1. Accédez à l’ **Périphérique** **Inscription** dans le menu d’action de gauche, cliquez sur le lien pour vérifier le statut du processus d’enregistrement des appareils.

>[!NOTE]
>
>Si le **État** est **ENREGISTRÉ**, vous pouvez voir que le **Identifiant de l’appareil** le champ est renseigné.
>
>Si le **Statut** est **NON ENREGISTRÉ**, vous pouvez utiliser le **Jeton** pour enregistrer l’appareil.

## Mise en œuvre d’Android™ Watchdog {#implementing-android-watchdog}

En raison de l’architecture d’Android™, le redémarrage de l’appareil nécessite que l’application dispose de privilèges système. Pour ce faire, signez l&#39;apk en utilisant les clés de signature du fabricant, sinon watchdog redémarre l&#39;application du lecteur et ne redémarre pas l&#39;appareil.

### Signature d’Android™ `apks` à l’aide des clés de fabricant {#signage-of-android-apks-using-manufacturer-keys}

Pour accéder à certaines des API privilégiées d’Android™ telles que : *PowerManager* ou *HDMIControlServices*, signez Android™ `apk` en utilisant les clés du fabricant.

>[!CAUTION]
>
>Conditions préalables :
>
>Le SDK Android™ doit être installé avant d’effectuer les étapes suivantes.

Suivez les étapes ci-dessous pour signer l’apk Android™ à l’aide des clés du fabricant :

1. Téléchargez le fichier apk à partir de Google Play ou de la page [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/)
1. Procurez-vous les clés de plateforme auprès du fabricant afin de pouvoir obtenir une *pk8* et un *pem* fichier

1. Localisez le `apksigner` outil dans le sdk Android™ à l’aide de la fonction de recherche `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Recherchez le chemin d’accès à l’outil d’alignement zip dans le sdk Android™
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. Installez ***aemscreensaligned.apk*** via adb install sur l’appareil.

## Présentation des services Android™ Watchdog {#android-watchdog-services}

Le service de surveillance Android est implémenté en tant que plug-in Cordova à l’aide de *AlarmManager*.

Le diagramme suivant illustre la mise en œuvre du service watchdog :

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initialisation** - Au moment de l’initialisation du plug-in Cordova, les autorisations sont vérifiées pour voir si vous disposez des privilèges système et donc de l’autorisation Redémarrer. Si ces deux critères sont satisfaits, une tentative en attente d’exécution de Redémarrer est créée. Dans le cas contraire, une tentative en attente de redémarrage de l’application (en fonction de son activité de lancement) est créée.

**2. Minuteur Keep Alive** - Un minuteur de maintien en vie est utilisé pour déclencher un événement toutes les 15 secondes. Dans ce cas, annulez l’intention en attente existante (redémarrer ou redémarrer l’application) et enregistrez une nouvelle intention en attente pendant les 60 mêmes secondes à l’avenir (ce qui revient essentiellement à reporter le redémarrage).

>[!NOTE]
>
>Sous Android™, le *AlarmManager* est utilisé pour enregistrer le *pendingIntents* qui peut s’exécuter même si l’application s’est bloquée et que sa diffusion d’alarme est inexacte de l’API 19 (Kitkat). Conservez un certain espacement entre l’intervalle du minuteur et le *AlarmManager&#39;s* *pendingIntent&#39;s* alarme.

**3. Blocage de l’application** - En cas de blocage, la propriété pendingIntent for Reboot enregistrée auprès de AlarmManager n&#39;est plus réinitialisée. Par conséquent, il exécute un redémarrage ou un redémarrage de l’application (en fonction des autorisations disponibles au moment de l’initialisation du plug-in Cordova).

## Approvisionnement en bloc du lecteur Android™ {#bulk-provision-android-player}

Lors du déploiement en bloc du lecteur Android™, il est nécessaire de configurer le lecteur pour qu’il pointe vers une instance AEM et configure d’autres propriétés sans saisir manuellement celles-ci dans l’interface utilisateur d’administration.

>[!NOTE]
>Cette fonctionnalité est disponible à partir du lecteur Android™ 42.0.372.

Suivez les étapes ci-dessous pour autoriser l’approvisionnement en bloc dans le lecteur Android™ :

1. Créez un fichier de configuration JSON nommé `player-config.default.json`.
Se référer à une [Exemple de politique JSON](#example-json) et un tableau qui décrit l’utilisation des différents [Attributs de politique](#policy-attributes).

1. Utilisez un explorateur de fichiers MDM, ADB ou Android™ Studio pour déposer ce fichier JSON de stratégie dans le *sdcard* sur l’appareil Android™.

1. Une fois le fichier déployé, utilisez le MDM pour installer l’application du lecteur.

1. Lorsque l’application du lecteur se lance, ce fichier de configuration est lu et pointe vers le serveur AEM applicable où il est enregistré, puis contrôlé.

   >[!NOTE]
   >Ce fichier est *lecture seule* la première fois que l’application est lancée et ne peut pas être utilisée pour les configurations suivantes. Si le lecteur est lancé avant la suppression du fichier de configuration, désinstallez et réinstallez simplement l’application sur l’appareil.

### Attributs de politique {#policy-attributes}

Le tableau suivant résume les attributs de politique et inclut un exemple de politique JSON à titre de référence :

| **Nom de la politique** | **Objectif** |
|---|---|
| *serveur* | L’URL du serveur Adobe Experience Manager. |
| *resolution* | Résolution de l’appareil. |
| *rebootSchedule* | La programmation du redémarrage s’applique à toutes les plates-formes. |
| *enableAdminUI* | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Définissez la valeur sur *false* une fois qu’elle est entièrement configurée et en production. |
| *enableOSD* | Activez l’interface utilisateur du sélecteur de canal pour que les utilisateurs changent de canaux sur l’appareil. Pensez à la définir sur *false* une fois qu’elle est entièrement configurée et en production. |
| *enableActivityUI* | Activez cette option pour afficher la progression d’activités telles que le téléchargement et la synchronisation. Activez cette règle pour le dépannage et désactivez-la une fois qu’elle est entièrement configurée et en production. |
| *enableNativeVideo* | Activez cette option pour utiliser l’accélération matérielle native pour la lecture vidéo (Android™ uniquement). |

### Exemple de politique JSON {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>Tous les appareils Android™ ont un `*sdcard*` dossier si un réel `*sdcard*` est inséré ou non. Une fois déployé, ce fichier se trouvera au même niveau que le dossier Downloads. Certains MDM tels que Samsung Knox peuvent utiliser l’emplacement de dossier *sdcard* comme *stockage interne*.

## Approvisionnement en bloc d’Android™ Player à l’aide d’Enterprise Mobility Management {#bulk-provisioning}

Lors du déploiement en bloc du lecteur Android™, il devient fastidieux d’enregistrer manuellement chaque lecteur avec AEM. Il est vivement recommandé d’utiliser une solution EMM (Enterprise Mobility Management), par exemple : [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), MobileIron ou Samsung Knox pour configurer et gérer à distance votre déploiement. Le lecteur AEM Screens Android™ prend en charge la configuration d’application EMM standard pour permettre l’approvisionnement à distance.

## Nommage du lecteur Android™ {#name-android}

Vous pouvez attribuer un nom d’appareil convivial à votre lecteur Android™ et envoyer le nom d’appareil attribué à AEM (Adobe Experience Manager). Cette fonctionnalité vous permet non seulement de nommer votre lecteur Android™, mais également d’attribuer facilement le contenu approprié.

>[!NOTE]
>Vous ne pouvez choisir le nom du lecteur qu’avant l’enregistrement. Une fois le lecteur enregistré, son nom ne peut plus être modifié.

Pour configurer le nom dans le lecteur Android™, procédez comme suit :

1. Accéder à **paramètres** > **À propos de l’appareil**
1. Modifier et définir le nom de votre appareil pour nommer votre lecteur Android™

### Mise en œuvre de l’approvisionnement en bloc d’Android™ Player à l’aide d’Enterprise Mobility Management {#implementation}

Suivez les étapes ci-dessous pour autoriser l’approvisionnement en bloc dans le lecteur Android™ :

1. Assurez-vous que votre appareil Android™ prend en charge les services Google Play.
1. Inscrivez vos appareils de lecteur Android™ à votre solution EMM préférée qui prend en charge AppConfig.
1. Connectez-vous à la console EMM et extrayez l’application AEM Screens Player de Google Play.
1. Sélectionnez Configuration gérée ou l’option associée.
1. Vous devriez maintenant voir la liste des options du lecteur qui peuvent être configurées, par exemple le code d’enregistrement en bloc et du serveur.
1. Configurez ces paramètres, enregistrez-les et déployez la stratégie sur les appareils.

   >[!NOTE]
   >Les appareils doivent recevoir l’application avec la configuration et pointer vers le serveur AEM approprié avec la configuration sélectionnée. Si vous choisissez de configurer le code d’enregistrement en bloc et que vous le conservez tel que configuré dans AEM, le lecteur doit être en mesure de s’enregistrer automatiquement. Si vous avez configuré un affichage par défaut, il peut également télécharger et afficher du contenu par défaut (qui peut être modifié ultérieurement selon vos besoins).

En outre, contactez votre fournisseur EMM pour obtenir de l’aide sur AppConfig. Les plus populaires, comme [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm), et [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) entre autres, ils appuient cette norme de l&#39;industrie.

### Utiliser la commande à distance Screens {#using-remote-control}

AEM Screens offre une fonctionnalité de commande à distance. Pour en savoir plus sur cette fonctionnalité, cliquez ici : [Commande à distance Screens](implementing-remote-control.md)
