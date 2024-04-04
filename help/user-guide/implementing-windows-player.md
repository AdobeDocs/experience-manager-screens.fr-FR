---
title: Mise en œuvre du lecteur Windows 10
seo-title: Implementing Windows 10 Player
description: Suivez cette page pour en savoir plus sur la configuration du lecteur AEM Screens Windows 10.
seo-description: Follow this page to learn about configuring AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 99%

---

# Mise en œuvre du lecteur Windows 10 {#implementing-windows-player}

Cette section décrit la configuration du lecteur AEM Screens Windows 10. Elle fournit des informations sur le fichier de configuration, les options disponibles, ainsi que des recommandations indiquant quels paramètres utiliser pour le développement et le test.

## Installation du lecteur Windows {#installing-windows-player}

Pour mettre en œuvre le lecteur Windows pour AEM Screens, installez le lecteur Windows pour AEM Screens.

Consultez la page [**Téléchargements du lecteur AEM 6.5**](https://download.macromedia.com/screens/).

>[!NOTE]
>Il n’existe pas de mode fenêtre dans le lecteur Windows. Celui-ci est toujours en mode Plein écran.

### Configuration de l’environnement pour le Service Pack AEM Screens 6.5.5 {#fp-environment-setup}

>[!NOTE]
>Vous devez configurer un environnement pour le lecteur Windows si vous utilisez le Service Pack AEM Screens 6.5.5.

Changez la valeur de **SameSite attribute for the login-token cookies** de **Lax** à **None** dans **Configuration de la console web Adobe
Experience Manager** sur toutes les instances de création et de publication AEM.

Suivez les étapes ci-dessous :

1. Accédez à **Configuration de la console web Adobe
Experience Manager** en utilisant `http://localhost:4502/system/console/configMgr`.

1. Recherchez *Adobe Granite Token Authentication Handler*.

1. Changez la valeur de **SameSite attribute for the login-token cookies** de **Lax** à **None**.
   ![image](/help/user-guide/assets/granite-updates.png)

1. Cliquez sur **Save**.

### Méthode ad hoc {#ad-hoc-method}

La méthode ad hoc vous permet d’installer le dernier lecteur Windows (*.exe*). Visitez la page [**Téléchargements du lecteur AEM 6.5**](https://download.macromedia.com/screens/).

Une fois l’application téléchargée, suivez les étapes du lecteur pour terminer l’installation ad hoc :

1. Appuyez longuement dans l’angle supérieur gauche pour ouvrir le panneau d’administration.
1. Accédez à **Configuration** depuis le menu d’actions de gauche et saisissez l’emplacement (adresse) de l’instance AEM à laquelle vous souhaitez vous connecter, puis cliquez sur **Enregistrer**.
1. Accédez au lien **Device** **Registration** (Enregistrement de l’appareil) depuis le menu d’actions de gauche pour vérifier le statut du processus d’enregistrement de l’appareil.

>[!NOTE]
>
>Si le **Statut** est **ENREGISTRÉ**, vous remarquerez que le champ **ID d’appareil** est renseigné.
>
>Si le **Statut** est **NON ENREGISTRÉ**, vous pouvez utiliser le **Jeton** pour enregistrer l’appareil.

## Nommage du lecteur Windows {#name-windows}

Vous pouvez attribuer un nom d’appareil convivial à votre lecteur Windows et envoyer le nom d’appareil choisi à Adobe Experience Manager (AEM). Cette fonctionnalité vous permet non seulement de nommer votre lecteur Windows, mais également d’attribuer facilement le contenu approprié.

>[!NOTE]
>Vous ne pouvez choisir le nom du lecteur qu’avant l’enregistrement. Une fois le lecteur enregistré, son nom ne peut plus être modifié.

Pour configurer le nom dans le lecteur Windows, procédez comme suit :

1. Cliquez sur **start** > **run**
1. Enter `system.cpl`
1. Utilisez l’onglet du nom d’ordinateur pour définir le nom d’hôte de l’ordinateur

## Modification des options par défaut dans Windows Installer {#changing-default-options}

Suivez cette section pour savoir comment modifier les options par défaut dans Windows Installer et la liste des personnalisations disponibles.

## Installation à l’aide de l’interface de ligne de commande (PowerShell) {#install-powershell}

1. Créez un emplacement personnalisé **dédié** pour le lecteur Screens, par exemple :
   `C:\Users\User\screens-player`)
1. Installer
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. Ouvrez
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**Exemple**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Enregistrement groupé du lecteur Windows {#bulk-registration}

Lors de la mise en œuvre du lecteur Windows, vous n’avez pas besoin de configurer manuellement chaque lecteur. Au lieu de cela, vous pouvez mettre à jour le fichier de configuration JSON une fois qu’il est testé et prêt à être déployé.

La configuration garantit que tous les lecteurs envoient un ping au même serveur spécifié dans le fichier de configuration. Vous devez toujours enregistrer manuellement chaque lecteur.

Pour configurer le lecteur Windows 10, procédez comme suit :

1. Installez le lecteur Windows.
1. Recherchez le fichier de configuration sous ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Mettez à jour le fichier JSON de configuration en utilisant les informations ci-dessous, puis copiez le même dossier sur tous les systèmes où réside le lecteur.

### Attributs de politique {#policy-attributes}

Le tableau suivant résume les attributs de politique et inclut un exemple de politique JSON à titre de référence :


| **Nom de la politique** | **Objectif** |
|---|---|
| serveur | L’URL du serveur Adobe Experience Manager (AEM). |
| registrationKey | Utilisé pour l’enregistrement en masse des appareils à l’aide d’une clé pré-partagée. |
| resolution | Résolution de l’appareil. |
| rebootSchedule | Planification du redémarrage du lecteur. |
| enableAdminUI | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Définissez la valeur sur false une fois qu’elle est entièrement configurée et en production. |
| enableOSD | Activez l’interface utilisateur du sélecteur de canal pour que les utilisateurs changent de canaux sur l’appareil. Pensez à la définir sur false une fois qu’elle est entièrement configurée et en production. |
| enableActivityUI | Activez cette règle pour afficher la progression des activités, comme le téléchargement et la synchronisation. Activez cette règle pour le dépannage et désactivez-la une fois qu’elle est entièrement configurée et en production. |
| cloudMode | Définissez cette valeur sur true si vous souhaitez que le lecteur Windows se connecte à Screens as a Cloud Service. Définissez cette variable sur false pour vous connecter à AMS ou à AEM On-Premise. |
| cloudToken | Jeton d’enregistrement à enregistrer dans Screens as a Cloud Service. |

#### Exemple de fichier JSON de politique {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## Activation du mode kiosque {#enabling-kiosk-mode}

Lorsque vous déployez le lecteur Windows, il est important d’activer un mode Kiosque afin que d’autres applications ou la barre des tâches n’apparaissent pas sur le bureau Windows.

>[!CAUTION]
>
>Adobe recommande une solution de gestion des appareils pour activer Kiosque pour Windows. Suivez les étapes ci-dessous, si vous ne disposez pas d’une solution de gestion des appareils pour activer le mode Kiosque. Cette méthode utilise la fonction Shell Launcher disponible dans Windows 10 Enterprise et Edu. Vous pouvez également utiliser toute autre méthode recommandée par Microsoft pour les applications non UWP pour activer Kiosque, en particulier sur d’autres éditions de Windows.

Pour activer le mode Kiosque, procédez comme suit :

>[!NOTE]
>
>Avant de suivre les étapes ci-dessous, veillez à utiliser Windows 10 Enterprise ou Education.

1. Activez Shell Launcher.

   Pour plus d’informations, reportez-vous à la section ***Configuration de Shell Launcher*** à la page **[Shell Launcher](https://docs.microsoft.com/fr-fr/windows-hardware/customize/enterprise/shell-launcher)** de l’assistance Microsoft Windows.

1. Créez un utilisateur non administratif (si vous n’en avez pas déjà) à utiliser pour Kiosque. Il peut s’agir d’un utilisateur local ou de domaine.
1. Installez le lecteur Windows pour cet utilisateur Kiosque à partir de la page [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/).
1. Pour plus d’informations, reportez-vous à [Utilisation de Shell Launcher pour créer un kiosque Windows 10](https://docs.microsoft.com/fr-fr/windows/configuration/kiosk-shelllauncher) afin de modifier votre script PowerShell.

   Modifiez le script PowerShell pour remplacer le nom d’utilisateur par celui que vous avez créé. Assurez-vous que le chemin d’accès au fichier exécutable de l’application est correct. Le shell personnalisé sera défini comme application du lecteur Windows pour l’utilisateur Kiosque et la valeur par défaut explorer.exe pour les autres utilisateurs.

1. Exécutez le script PowerShell en tant qu’administrateur.
1. Redémarrez et connectez-vous en tant qu’utilisateur Kiosque et l’application du lecteur devrait démarrer immédiatement.

### Résolution des problèmes {#troubleshooting}

Si vous obtenez un écran noir lorsque vous vous connectez en tant qu’utilisateur Kiosque, cela signifie que vous avez peut-être mal spécifié le chemin d’accès au fichier exécutable du lecteur Windows. Connectez-vous à nouveau en tant qu’administrateur et vérifiez et réexécutez le script.

Le chemin d’installation par défaut du lecteur Windows est le suivant :

***C:\Users\&amp;lt;votre utilisateur>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

L’exemple de script dans les liens active et désactive le shell personnalisé. Vous devrez donc peut-être diviser le script en deux et activer/désactiver les lignes applicables ci-dessous :

>[!NOTE]
>
>Dans certains environnements Windows, les scripts PowerShell peuvent être restreints par la politique (en particulier les scripts non signés). Pour exécuter votre script, vous devrez peut-être désactiver provisoirement cette restriction puis la réactiver pour exécuter le script. Ouvrez une fenêtre PowerShell et utilisez ces commandes.
>
>*set-executionpolicy unrestricted* - pour supprimer provisoirement les restrictions
>
>*set-executionpolicy restricted* - pour réactiver la restriction après l’exécution du script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Utiliser la commande à distance Screens {#using-remote-control}

AEM Screens offre une fonctionnalité de commande à distance. Pour en savoir plus sur cette fonctionnalité, cliquez ici : [Commande à distance Screens](implementing-remote-control.md)