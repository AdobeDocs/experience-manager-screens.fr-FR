---
title: Implémenter le lecteur Android&trade;
description: Découvrez l’implémentation d’Android&trade; Watchdog, une solution qui vous permet de restaurer le lecteur Android™ en cas de panne.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 94%

---

# Implémenter le lecteur Android™ {#implementing-android-player}

>[!CAUTION]
>Le lecteur AEM Screens basé sur Android est officiellement obsolète. Il est conseillé aux utilisateurs de migrer vers un autre système d’exploitation pris en charge par AEM Screens.

Cette section décrit la configuration du lecteur Android™. Elle fournit des informations sur le fichier de configuration, les options disponibles, ainsi que des recommandations indiquant quels paramètres utiliser pour le développement et le test.

Par ailleurs, **Watchdog** est une solution permettant de restaurer le lecteur suite à une panne. Les applications doivent s’enregistrer auprès du service Watchdog, puis envoyer régulièrement des messages au service lui indiquant qu’elles sont actives. Si le service Watchdog ne reçoit pas de message persistant dans un délai spécifié, il tente de redémarrer l’appareil. Il le fait pour une récupération propre (s’il dispose des privilèges suffisants) ou pour redémarrer l’application.

## Installer le lecteur Android™ {#installing-android-player}

Pour implémenter le lecteur Android™ pour AEM Screens, installez le lecteur Android™ pour AEM Screens.

Consultez la page [**Téléchargements du lecteur AEM 6.5**](https://download.macromedia.com/screens/).

### Configuration de l’environnement pour le pack de services AEM Screens 6.5.5 {#fp-environment-setup}

>[!NOTE]
>Vous devez configurer un environnement pour le lecteur Android™ si vous utilisez le pack de services AEM Screens 6.5.5.

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

La méthode ad hoc vous permet d’installer le dernier lecteur Android™ (*.exe*). Consultez la page [**Téléchargements du lecteur AEM 6.5**](https://download.macromedia.com/screens/).

Après avoir téléchargé l’application, suivez les étapes du lecteur pour terminer l’installation ad hoc :

1. Appuyez longuement dans l’angle supérieur gauche pour ouvrir le panneau d’administration.
1. Accédez à **Configuration** depuis le menu d’actions de gauche et saisissez l’emplacement (adresse) de l’instance AEM à laquelle vous souhaitez vous connecter, puis cliquez sur **Enregistrer**.

1. Accédez au lien **Enregistrement** des **appareils** depuis le menu d’actions de gauche pour vérifier le statut du processus d’enregistrement de l’appareil.

>[!NOTE]
>
>Si l’**État** est **ENREGISTRÉ**, vous remarquerez que le champ **ID d’appareil** est renseigné.
>
>Si le **Statut** est **NON ENREGISTRÉ**, vous pouvez utiliser le **Jeton** pour enregistrer l’appareil.

## Implémenter Android™ Watchdog {#implementing-android-watchdog}

En raison de l’architecture d’Android™, le redémarrage de l’appareil requiert que l’application dispose d’autorisations système. Signez le fichier apk à l’aide des clés de signature du fabricant. Sinon, Watchdog peut redémarrer l’application du lecteur et ne redémarre pas l’appareil.

### Signature de `apks` Android™ à l’aide des clés du fabricant {#signage-of-android-apks-using-manufacturer-keys}

Pour accéder à certaines des API privilégiées d’Android™, telles que *PowerManager* ou *HDMIControlServices*, signez le `apk` Android™ à l’aide des clés du fabricant.

>[!CAUTION]
>
>Conditions préalables :
>
>Le SDK Android™ doit être installé avant que vous n’exécutiez les étapes suivantes.

Pour signer le fichier apk Android™ à l’aide des clés du fabricant, procédez comme suit :

1. Télécharger le fichier apk à partir de Google Play ou de la page [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/)
1. Obtenir les clés de plateforme du fabricant pour obtenir un fichier *pk8* et un fichier *pem*

1. Rechercher l’outil `apksigner` dans le SDK Android™ à l’aide de l’outil find `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Rechercher le chemin d’accès à l’outil d’alignement zip dans le SDK Android™
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. Installez ***aemscreensaligned.apk*** via adb install sur l’appareil.

## Comprendre les services Android™ Watchdog {#android-watchdog-services}

Le service de surveillance cross-Android™ est implémenté sous la forme d’un plug-in Cordova à l’aide de *AlarmManager*.

Le diagramme suivant illustre la mise en œuvre du service Watchdog :

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initialisation** : au moment de l’initialisation du plug-in Cordova, les autorisations sont vérifiées pour voir si vous disposez des autorisations système et donc de l’autorisation Redémarrer. Si ces deux critères sont satisfaits, une tentative en attente d’exécution de Redémarrer est créée. Dans le cas contraire, une tentative en attente de redémarrage de l’application (en fonction de son activité de lancement) est créée.

**2. Minuteur de maintien en activité** : un minuteur de maintien en activité est utilisé pour déclencher un événement toutes les 15 secondes. Dans cet événement, vous devez annuler la tentative en attente existante (pour redémarrer l’application) et enregistrer une nouvelle tentative identique en attente pour 60 secondes plus tard (en remettant à plus tard le redémarrage).

>[!NOTE]
>
>Sous Android™, *AlarmManager* est utilisé pour enregistrer les *pendingIntents* qui peuvent s’exécuter même si l’application est en panne et que sa distribution d’alarme est incorrecte à partir de l’API 19 (Kitkat). Conservez un espace entre l’intervalle du minuteur et l’alarme des *pendingIntent* du *AlarmManager*.

**3. Crash de l’application** : en cas de crash, le pendingIntent pour le redémarrage enregistré avec AlarmManager n’est plus réinitialisé. Par conséquent, il exécute un redémarrage de l’application (en fonction des autorisations disponibles au moment de l’initialisation du plug-in Cordova).

## Approvisionnement en bloc du lecteur Android™ {#bulk-provision-android-player}

Lors du déploiement en masse du lecteur Android™, vous devez pouvoir configurer le lecteur pour qu’il pointe vers une instance AEM et pouvoir configurer d’autres propriétés sans les saisir manuellement par le biais de l’interface d’utilisation de l’administration.

>[!NOTE]
>Cette fonctionnalité est disponible sur le lecteur Android™ version 42.0.372.

Pour autoriser l’approvisionnement en bloc dans le lecteurAndroid™, procédez comme suit :

1. Créez un fichier de configuration JSON nommé `player-config.default.json`.
Reportez-vous à l’[exemple de politique JSON](#example-json) ainsi qu’au tableau qui décrit l’utilisation des différents [attributs de politique](#policy-attributes).

1. Utilisez un explorateur de fichiers MDM ou ADB ou Android™ Studio pour déposer ce fichier de politique JSON dans le dossier *sdcard* de l’appareil Android™.

1. Lorsque le fichier déployé, utilisez le MDM pour installer l’application du lecteur.

1. Lorsque l’application du lecteur est lancée, ce fichier de configuration est lu et pointe vers le serveur AEM approprié où il est enregistré puis contrôlé.

   >[!NOTE]
   >Ce fichier est *en lecture seule* la première fois que l’application est lancée et ne peut pas être utilisé pour les configurations suivantes. Si le lecteur est lancé avant l’abandon du fichier de configuration, il suffit de désinstaller et de réinstaller l’application sur l’appareil.

### Attributs de politique {#policy-attributes}

Le tableau suivant résume les attributs de politique et inclut un exemple de politique JSON à titre de référence :

| **Nom de la politique** | **Objectif** |
|---|---|
| *server* | L’URL du serveur Adobe Experience Manager. |
| *resolution* | Résolution de l’appareil. |
| *rebootSchedule* | La programmation du redémarrage s’applique à toutes les plates-formes. |
| *enableAdminUI* | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Définissez la valeur sur *false* une fois qu’elle est entièrement configurée et en production. |
| *enableOSD* | Activez l’interface d’utilisation du sélecteur de canal pour que les utilisateurs et utilisatrices changent de canaux sur l’appareil. Pensez à la définir sur *false* une fois qu’elle est entièrement configurée et en production. |
| *enableActivityUI* | Activez cette option pour afficher la progression des activités, telles que le téléchargement et la synchronisation. Activez cette règle pour le dépannage et désactivez-la une fois qu’elle est entièrement configurée et en production. |
| *enableNativeVideo* | Activez cette option afin d’utiliser l’accélération matérielle native pour la lecture vidéo (Android™ uniquement). |

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
>Tous les appareils Android™ disposent d’un dossier `*sdcard*`, qu’une `*sdcard*` ait été insérée ou non. Une fois déployé, ce fichier se trouvera au même niveau que le dossier Downloads. Certains MDM tels que Samsung Knox peuvent utiliser l’emplacement de dossier *sdcard* comme *stockage interne*.

## Approvisionnement en bloc d’un lecteur Android™ à l’aide d’Enterprise Mobility Management {#bulk-provisioning}

Lors du déploiement en masse d’un lecteur Android™, il devient fastidieux d’enregistrer manuellement chaque lecteur dans AEM. Utilisez une solution EMM (Enterprise Mobility Management), par exemple [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), MobileIron ou Samsung Knox afin que vous puissiez configurer et gérer votre déploiement à distance. Le lecteur Android™ AEM Screens prend en charge la norme EMM AppConfig pour permettre l’approvisionnement à distance.

## Nommer un lecteur Android™ {#name-android}

Vous pouvez attribuer un nom d’appareil convivial à votre lecteur Android™ et envoyer le nom d’appareil choisi à Adobe Experience Manager (AEM). Cette fonctionnalité vous permet non seulement de nommer votre lecteur Android™, mais également d’attribuer facilement le contenu approprié.

>[!NOTE]
>Vous ne pouvez choisir le nom du lecteur qu’avant l’enregistrement. Une fois le lecteur enregistré, son nom ne peut plus être modifié.

Pour configurer le nom dans le lecteur Android™, procédez comme suit :

1. Accédez à **Paramètres** > **À propos de l’appareil**.
1. Modifiez et définissez le nom de votre appareil pour nommer votre lecteur Android™.

### Implémenter l’approvisionnement en bloc du lecteur Android™ à l’aide d’une solution Enterprise Mobility Management {#implementation}

Pour autoriser l’approvisionnement en bloc dans le lecteur Android™, procédez comme suit :

1. Assurez-vous que votre appareil Android™ prend en charge les services Google Play.
1. Enregistrez vos appareils de lecteur Android™ dans votre solution EMM préférée prenant en charge AppConfig.
1. Connectez-vous à votre console EMM et extrayez l’application du lecteur AEM Screens de Google Play.
1. Cliquez sur la configuration gérée ou l’option associée.
1. Vous devriez maintenant voir la liste des options du lecteur qui peuvent être configurées, par exemple le code d’enregistrement en bloc et du serveur.
1. Configurez ces paramètres, enregistrez-les et déployez la politique sur les appareils.

   >[!NOTE]
   >Les appareils doivent recevoir l’application avec la configuration. Elle doit pointer vers le serveur AEM correct avec la configuration sélectionnée. Si vous choisissez de configurer le code d’enregistrement en bloc et que vous le conservez tel que configuré dans AEM, le lecteur doit être en mesure de s’enregistrer automatiquement. Si vous avez configuré un affichage par défaut, il peut également télécharger et afficher un certain contenu par défaut (qui peut être modifié ultérieurement selon vos besoins).

En outre, vous devez vérifier auprès de votre fournisseur de solution EMM si celle-ci prend en charge AppConfig. Les plus populaires, par exemple [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm),et [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) parmi d’autres prennent en charge cette norme du secteur.

### Utiliser la commande à distance Screens {#using-remote-control}

AEM Screens offre une fonctionnalité de commande à distance. Pour en savoir plus sur cette fonctionnalité, cliquez ici : [Commande à distance Screens](implementing-remote-control.md)
