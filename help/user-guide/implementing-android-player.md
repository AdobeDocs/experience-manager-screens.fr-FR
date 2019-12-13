---
title: Mise en oeuvre du lecteur Android
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
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Mise en oeuvre du lecteur Android {#implementing-android-player}

Cette section décrit la configuration du lecteur Android. Elle fournit des informations sur le fichier de configuration, les options disponibles, ainsi que des recommandations indiquant quels paramètres utiliser pour le développement et le test.

Additionally, **Watchdog** is a solution to recover the player from crashes. Les applications doivent s’inscrire auprès du service watchdog, puis envoyer régulièrement des messages au service lui indiquant qu’elles sont actives. Au cas où le service watchdog ne reçoit pas de message de maintien en activité dans le délai imparti, le service tente de redémarrer l’appareil pour une restauration propre (s’il dispose des droits suffisants) ou de redémarrer l’application.

## Installation d’Android Player {#installing-android-player}

Pour mettre en oeuvre Android Player pour AEM Screens, installez Android Player pour AEM Screens.

Consultez la page Téléchargements [**du lecteur**](https://download.macromedia.com/screens/) AEM 6.4.

### Méthode ad hoc {#ad-hoc-method}

La méthode ad hoc vous permet d’installer le dernier lecteur Android (*.exe*). Visitez la page Téléchargements [**du lecteur**](https://download.macromedia.com/screens/) AEM 6.4.

Une fois l’application téléchargée, suivez les étapes du lecteur pour terminer l’installation ad hoc :

1. Appuyez longuement sur le coin supérieur gauche pour ouvrir le panneau d’administration.
1. Accédez à **Configuration** à partir du menu d’action de gauche, saisissez l’emplacement (adresse) de l’instance AEM à laquelle vous souhaitez vous connecter, puis cliquez sur **Enregistrer**.

1. Accédez au lien **Enregistrement** du périphérique **** à partir du menu d'action de gauche pour vérifier l'état du processus d'enregistrement du périphérique.

>[!NOTE]
>
>Si l' **État** est **ENREGISTRÉ**, vous remarquerez que le champ ID **de** périphérique est renseigné.
>
>Si l’ **État** est **NON ENREGISTRÉ**, vous pouvez utiliser le **jeton** pour enregistrer le périphérique.

## Mise en œuvre d’Android Watchdog {#implementing-android-watchdog}

En raison de l’architecture d’Android, le redémarrage de l’appareil requiert que l’application dispose d’autorisations système. Pour ce faire, vous devez signer le fichier apk à l’aide des clés de signature du fabricant, faute de quoi le service watchdog redémarre l’application du lecteur, mais pas l’appareil.

### Signature de fichiers apk Android à l’aide des clés du fabricant {#signage-of-android-apks-using-manufacturer-keys}

To access some of the privileged APIs of Android such as *PowerManager* or *HDMIControlServices*, you need to signtheandroid apk using the manufacturer's keys.

>[!CAUTION]
>
>Conditions préalables:
>
>Le kit SDK Android doit être installé avant que vous n’exécutiez les étapes suivantes.

Suivez les étapes ci-dessous pour signer le fichier apk Android à l’aide des clés du fabricant :

1. Download the apk from Google Play or from [AEM Screens Player Downloads](https://download.macromedia.com/screens/) page
1. Obtain the platform keys from the manufacturer to get a *pk8* and a *pem* file

1. Localisez l’outil apksigner dans le kit SDK Android à l’aide de la commande find ~/Library/Android/sdk/build-tools -name "apksigner"
1. &lt;pathto&gt; /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk
1. Recherchez le chemin de l’outil d’alignement zip dans le sdk android.
1. &lt;pathto&gt; /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. Installez ***aemscreensaligned.apk**via adb install sur l’appareil.*

## Mise en œuvre du watchdog Android {#android-watchdog-implementation}

The cross-Android watchdog service is implemented as a cordova plugin using *AlarmManager*.

Le diagramme suivant illustre la mise en œuvre du service watchdog :

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initialization** At the time of initialization of the cordova plugin, permissions are checked to see if we have system privileges and thus the Reboot permission. Si ces deux critères sont satisfaits, une tentative en attente d’exécution de Redémarrer est créée. Dans le cas contraire, une tentative en attente de redémarrage de l’application (en fonction de son activité de lancement) est créée.

**2. Keep Alive Timer** A keep alive timer is used to trigger an event every 15 seconds. Dans cet événement, vous devez annuler la tentative en attente existante (pour redémarrer l’application) et enregistrer une nouvelle tentative en attente pour les mêmes 60 secondes à l’avenir (en remettant à plus tard le redémarrage).

>[!NOTE]
>
>Sous Android, *AlarmManager* est utilisé pour enregistrer les *pendingIntents* qui peuvent s’exécuter même si l’application est en panne et que sa distribution d’alarme est incorrecte à partir d’API 19 (Kitkat). Conservez un certain espace entre l’intervalle du minuteur et l’alarme *pendingIntent* de *AlarmManager*.

**3. Application Crash** In case of a crash, the pendingIntent for Reboot registered with AlarmManager is no longer reset and thus it executes a reboot or restart of app (depending on permissions available at the time of initialization of the cordova plugin).
