---
title: Mise en œuvre d’Android Player
seo-title: Mise en œuvre d’Android Player
description: Suivez cette page pour découvrir la mise en œuvre d’Android Watchdog, une solution pour restaurer le lecteur suite à une panne.
seo-description: Suivez cette page pour découvrir la mise en œuvre d’Android Watchdog, une solution pour restaurer le lecteur suite à une panne.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Administrator
level: Intermediate
translation-type: ht
source-git-commit: 6978d9d13f2b7f723812561554fdb0a606ddb4fc
workflow-type: ht
source-wordcount: '1441'
ht-degree: 100%

---


# Mise en œuvre d’Android Player {#implementing-android-player}

Cette section décrit la configuration du lecteur Android. Elle fournit des informations sur le fichier de configuration, les options disponibles, ainsi que des recommandations indiquant quels paramètres utiliser pour le développement et le test.

Par ailleurs, **Watchdog** est une solution permettant de restaurer le lecteur suite à une panne. Les applications doivent s’inscrire auprès du service watchdog, puis envoyer régulièrement des messages au service lui indiquant qu’elles sont actives. Au cas où le service watchdog ne reçoit pas de message de maintien en activité dans le délai imparti, le service tente de redémarrer l’appareil pour une restauration propre (s’il dispose des droits suffisants) ou de redémarrer l’application.

## Installation d’Android Player {#installing-android-player}

Pour mettre en œuvre Android Player pour AEM Screens, installez Android Player pour AEM Screens.

Consultez la page [**Téléchargements du lecteur AEM 6.5**](https://download.macromedia.com/screens/).

### Configuration de l’environnement pour le Service Pack AEM Screens 6.5.5 {#fp-environment-setup}

>[!NOTE]
>Vous devez configurer un environnement pour le lecteur Android si vous utilisez le Service Pack AEM Screens 6.5.5.

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

La méthode ad hoc vous permet d’installer le dernier lecteur Android (*.exe*). Visitez la page [**Téléchargements du lecteur AEM 6.5**](https://download.macromedia.com/screens/).

Une fois l’application téléchargée, suivez les étapes du lecteur pour terminer l’installation ad hoc :

1. Appuyez longuement dans l’angle supérieur gauche pour ouvrir le panneau d’administration.
1. Accédez à **Configuration** depuis le menu d’actions de gauche et saisissez l’emplacement (adresse) de l’instance AEM à laquelle vous souhaitez vous connecter, puis cliquez sur **Enregistrer**.

1. Accédez au lien **Device** **Registration** (Enregistrement de l’appareil) depuis le menu d’actions de gauche pour vérifier le statut du processus d’enregistrement de l’appareil.

>[!NOTE]
>
>Si le **Statut** est **ENREGISTRÉ**, vous remarquerez que le champ **ID de périphérique** est renseigné.
>
>Si le **Statut** est **NON ENREGISTRÉ**, vous pouvez utiliser le **Jeton** pour enregistrer le périphérique.

## Mise en œuvre d’Android Watchdog {#implementing-android-watchdog}

En raison de l’architecture d’Android, le redémarrage de l’appareil requiert que l’application dispose d’autorisations système. Pour ce faire, vous devez signer le fichier apk à l’aide des clés de signature du fabricant, faute de quoi le service watchdog redémarre l’application du lecteur, mais pas l’appareil.

### Signature de fichiers apk Android à l’aide des clés du fabricant {#signage-of-android-apks-using-manufacturer-keys}

Pour accéder à certaines des API privilégiées d’Android telles que *PowerManager* ou *HDMIControlServices*, vous devez signer le fichier apk Android à l’aide des clés du fabricant.

>[!CAUTION]
>
>Conditions préalables :
>
>Le SDK Android doit être installé avant que vous n’exécutiez les étapes suivantes.

Suivez les étapes ci-dessous pour signer le fichier apk Android à l’aide des clés du fabricant :

1. Téléchargez le fichier apk à partir de Google Play ou de la page [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/)
1. Procurez-vous les clés de plateforme du fabricant pour obtenir un fichier *pk8* et *pem*

1. Localisez l’outil apksigner dans le SDK Android à l’aide de la commande find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk
1. Recherchez le chemin d’accès à l’outil d’alignement zip dans le SDK Android.
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. Installez ***aemscreensaligned.apk*** via adb install sur l’appareil.

## Présentation des services Android Watchdog {#android-watchdog-services}

Le service watchdog Android est mis en œuvre en tant que module externe cordova via *AlarmManager*.

Le diagramme suivant illustre la mise en œuvre du service watchdog :

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initialisation** Au moment de l’initialisation du module externe cordova, les autorisations sont vérifiées pour voir si nous disposons des autorisations système et donc de l’autorisation Redémarrer. Si ces deux critères sont satisfaits, une tentative en attente d’exécution de Redémarrer est créée. Dans le cas contraire, une tentative en attente de redémarrage de l’application (en fonction de son activité de lancement) est créée.

**2. Minuteur de maintien en activité** Un minuteur de maintien en activité est utilisé pour déclencher un événement toutes les 15 secondes. Dans cet événement, vous devez annuler la tentative en attente existante (pour redémarrer l’application) et enregistrer une nouvelle tentative en attente pour les mêmes 60 secondes à l’avenir (en remettant à plus tard le redémarrage).

>[!NOTE]
>
>Sous Android, *AlarmManager* est utilisé pour enregistrer les *pendingIntents* qui peuvent s’exécuter même si l’application est en panne et que sa distribution d’alarme est incorrecte à partir d’API 19 (Kitkat). Conservez un certain espace entre l’intervalle du minuteur et l’alarme *pendingIntent* de *AlarmManager*.

**3. Panne d’application** En cas de panne, le pendingIntent pour la commande Redémarrer enregistré avec AlarmManager n’est plus réinitialisé et donc exécute un redémarrage de l’application (en fonction des autorisations disponibles lors de l’initialisation du module externe cordova).

## Approvisionnement en masse d’Android Player {#bulk-provision-android-player}

Lors de l’approvisionnement en masse d’Android Player, vous devez pouvoir configurer le lecteur pour qu’il pointe vers une instance AEM et pouvoir configurer d’autres propriétés sans les entrer manuellement par le biais de l’interface utilisateur d’administration.

>[!NOTE]
>Cette fonctionnalité est disponible sur Android Player version 42.0.372.

Suivez les étapes ci-dessous pour autoriser l’approvisionnement en masse dans Android Player :

1. Créez un fichier de configuration JSON nommé `player-config.default.json`.
Reportez-vous à l’[exemple de règle JSON](#example-json) ainsi qu’au tableau qui décrit l’utilisation des différents [attributs de règle](#policy-attributes).

1. Utilisez un explorateur de fichiers MDM ou ADB ou Android Studio pour déposer ce fichier de règle JSON dans le dossier *sdcard* de l’appareil Android.

1. Une fois le fichier déployé, utilisez le MDM pour installer l’application du lecteur.

1. L’application du lecteur, une fois lancée, lit ce fichier de configuration et pointe vers le serveur AEM approprié, où elle peut ensuite s’enregistrer et être contrôlée.

   >[!NOTE]
   >Ce fichier est *en lecture seule* la première fois que l’application est lancée et ne peut pas être utilisé pour les configurations suivantes. Si le lecteur est lancé avant que le fichier de configuration ne soit supprimé, il vous suffit de désinstaller et de réinstaller l’application sur l’appareil.

### Attributs de règle {#policy-attributes}

Le tableau suivant récapitule les attributs de règle et fournit un exemple de fichier JSON de règle pour référence :

| **Nom de la règle** | **Objectif** |
|---|---|
| *server* | L’URL du serveur Adobe Experience Manager. |
| *resolution* | Résolution de l’appareil. |
| *rebootSchedule* | La programmation du redémarrage s’applique à toutes les plates-formes. |
| *enableAdminUI* | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Définissez la valeur sur *false* une fois qu’elle est entièrement configurée et en production. |
| *enableOSD* | Activez l’interface utilisateur du sélecteur de canal pour que les utilisateurs changent de canaux sur l’appareil. Pensez à la définir sur *false* une fois qu’elle est entièrement configurée et en production. |
| *enableActivityUI* | Activez cette règle pour afficher la progression des activités, comme le téléchargement et la synchronisation. Activez-la pour résoudre les incidents et désactivez-la une fois que l’interface est entièrement configurée et en production. |
| *enableNativeVideo* | Activez cette option afin d’utiliser l’accélération matérielle native pour la lecture vidéo (Android uniquement). |

### Exemple de règle JSON {#example-json}

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
>Tous les appareils Android disposent d’un dossier *sdcard*, qu’une *carte SD* ait été insérée ou non. Une fois déployé, ce fichier se trouvera au même niveau que le dossier Downloads. Certains MDM tels que Samsung Knox peuvent utiliser l’emplacement de dossier *sdcard* comme *stockage interne*.

## Approvisionnement en bloc du lecteur Android à l’aide d’une solution Enterprise Mobility Management {#bulk-provisioning}

Lors du déploiement en bloc d’un lecteur Android, il devient fastidieux d’enregistrer manuellement chaque lecteur dans AEM. Nous vous recommandons vivement d’utiliser une solution EMM (Enterprise Mobility Management) telle que VMWare Airwatch, MobileIron ou Samsung Knox pour configurer et gérer votre déploiement à distance. Le lecteur Android AEM Screens prend en charge la norme EMM AppConfig pour permettre l’approvisionnement à distance.

### Mise en œuvre de l’approvisionnement en bloc du lecteur Android à l’aide d’une solution Enterprise Mobility Management {#implementation}

Suivez les étapes ci-dessous pour autoriser l’approvisionnement en bloc dans le lecteur Android Player :

1. Assurez-vous que votre périphérique Android prend en charge les services Google Play.
1. Enregistrez vos périphériques de lecteur Android dans votre solution EMM préférée prenant en charge AppConfig.
1. Connectez-vous à votre console EMM et extrayez l’application du lecteur AEM Screens de Google Play.
1. Sélectionnez Configuration gérée ou l’option associée.
1. Vous devriez maintenant voir la liste des options du lecteur qui peuvent être configurées, par exemple le code d’enregistrement en bloc et du serveur.
1. Configurez ces paramètres, enregistrez-les et déployez la stratégie sur les périphériques.

   >[!NOTE]
   >Les périphériques doivent recevoir l’application avec la configuration et pointer vers le serveur AEM approprié avec la configuration sélectionnée. Si vous choisissez de configurer le code d’enregistrement en bloc et que vous le conservez tel que configuré dans AEM, le lecteur doit être en mesure de s’enregistrer automatiquement. Si vous avez configuré un affichage par défaut, il peut également télécharger et afficher un certain contenu par défaut (qui peut être modifié ultérieurement selon vos besoins).

En outre, vous devez vérifier auprès de votre fournisseur de solution EMM si celle-ci prend AppConfig. Les plus populaires, parmi lesquels [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) et [Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm), prennent en charge cette solution standard dans ce domaine.
