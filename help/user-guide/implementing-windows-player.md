---
title: Mise en oeuvre du lecteur Windows 10
seo-title: Mise en oeuvre du lecteur Windows 10
description: Suivez cette page pour en savoir plus sur la configuration du lecteur AEM Screens Windows 10.
seo-description: Suivez cette page pour en savoir plus sur la configuration du lecteur AEM Screens Windows 10.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Mise en oeuvre du lecteur Windows 10 {#implementing-windows-player}

Cette section décrit la configuration du lecteur AEM Screens Windows 10. Elle fournit des informations sur le fichier de configuration, les options disponibles, ainsi que des recommandations indiquant quels paramètres utiliser pour le développement et le test.

## Installation du Lecteur Windows {#installing-windows-player}

Pour mettre en oeuvre Windows Player pour AEM Screens, installez Windows Player pour AEM Screens.

Consultez la page Téléchargements [**du lecteur**](https://download.macromedia.com/screens/) AEM 6.4.

### Méthode ad hoc {#ad-hoc-method}

La méthode ad hoc vous permet d’installer le dernier lecteur Windows (*.exe*). Visitez la page Téléchargements [**du lecteur**](https://download.macromedia.com/screens/) AEM 6.4.

Une fois l’application téléchargée, suivez les étapes du lecteur pour terminer l’installation ad hoc :

1. Appuyez longuement sur le coin supérieur gauche pour ouvrir le panneau d’administration.
1. Accédez à **Configuration** à partir du menu d’action de gauche, saisissez l’emplacement (adresse) de l’instance AEM à laquelle vous souhaitez vous connecter, puis cliquez sur **Enregistrer**.
1. Accédez au lien **Enregistrement** du périphérique **** à partir du menu d'action de gauche pour vérifier l'état du processus d'enregistrement du périphérique.

>[!NOTE]
>
>Si l' **État** est **ENREGISTRÉ**, vous remarquerez que le champ ID **de** périphérique est renseigné.
>
>Si l’ **État** est **NON ENREGISTRÉ**, vous pouvez utiliser le **jeton** pour enregistrer le périphérique.

### Configuration du serveur en bloc : Enregistrement de plusieurs lecteurs Windows 10 avec une configuration unique {#bulk-server-configuration-registering-multiple-windows-players-with-one-configuration}

Une fois le lecteur Windows installé, vous pouvez enregistrer plusieurs lecteurs avec une configuration unique.

>[!NOTE]
>
>**Enregistrement en masse du lecteur Windows**
>
>Lors de la mise en œuvre du lecteur Windows, vous n’avez pas besoin de configurer manuellement chaque lecteur. À la place, vous pouvez mettre à jour le fichier JSON de configuration une fois qu’il a été testé et qu’il est prêt pour le déploiement.
>
>La configuration garantit que tous les lecteurs envoient un ping au même serveur spécifié dans le fichier de configuration. Vous devez encore enregistrer manuellement chaque lecteur.

Suivez les étapes ci-dessous pour configurer le lecteur Windows 10 :

1. Installez Windows Player.
1. Recherchez le fichier de configuration sous ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Mettez à jour le fichier JSON de configuration en utilisant les informations ci-dessous, puis copiez le même dossier sur tous les systèmes où réside le lecteur.

### Attributs de règle {#policy-attributes}

Le tableau suivant récapitule les attributs de règle et fournit un exemple de fichier JSON de règle pour référence :

| **Nom de la règle** | **Objectif** |
|---|---|
| server | URL du serveur Adobe Experience Manager (AEM). |
| resolution | Résolution de l’appareil. |
| rebootSchedule | Planification de redémarrage du lecteur. |
| enableAdminUI | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Lorsque la valeur est définie sur false, il est entièrement configuré et en production. |
| enableOSD | Activez l’interface utilisateur du sélecteur de canal pour que les utilisateurs changent de canaux sur l’appareil. Pensez à la définir sur false lorsqu’elle est entièrement configurée et en production. |
| enableActivityUI | Activez cette règle pour afficher la progression des activités, comme le téléchargement et la synchronisation. Activez-la pour résoudre les incidents et désactivez-la une fois que l’interface est entièrement configurée et en production. |

#### Exemple de fichier JSON de règles {#example-policy-json-file}

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

Lorsque vous déployez le lecteur Windows, il est important d’activer le mode Kiosque afin que d’autres applications ou la barre des tâches n’apparaissent pas sur le bureau Windows.

>[!CAUTION]
>
>Adobe recommande une solution de gestion des périphériques pour activer Kiosque pour Windows. Suivez les étapes ci-dessous, si vous ne disposez pas d’une solution de gestion des périphériques pour activer le mode Kiosque. Cette méthode utilise la fonction Shell Launcher disponible dans Windows 10 Enterprise et Edu. Tout autre support recommandé par Microsoft pour les applications non-UWP peut également être appliqué pour activer Kiosk, en particulier sur d'autres éditions de Windows.

Suivez les étapes ci-dessous pour activer le mode Kiosque :

>[!NOTE]
>
>Avant de suivre les étapes ci-dessous, veillez à utiliser Windows 10 Enterprise ou Education.

1. Activez Shell Launcher.

   Pour plus d'informations, consultez la section ***Configuration du lanceur*** Shell dans la page ** [Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)*** du support Microsoft Windows.

1. Créez un utilisateur non-administrateur (si vous n’en avez pas déjà) à utiliser pour Kiosque. Il peut s’agir d’un utilisateur local ou de domaine.
1. Installez le lecteur Windows pour cet utilisateur Kiosque à partir de la page Téléchargements [du lecteur](https://download.macromedia.com/screens/) AEM Screens Player.
1. Pour plus d'informations, reportez-vous à [Utilisation du lanceur Shell pour créer un kiosque](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) Windows 10 afin de modifier votre script PowerShell.

   Modifiez le script PowerShell pour remplacer le nom d'utilisateur par celui que vous avez créé. Assurez-vous que le chemin d’accès au fichier exécutable de l’application est correct. Le shell personnalisé sera défini comme application du lecteur Windows pour l’utilisateur du kiosque et la valeur par défaut explorer.exe pour les autres utilisateurs.

1. Exécutez le script PowerShell en tant qu’administrateur.
1. Redémarrez et connectez-vous en tant qu'utilisateur Kiosque et l'application du lecteur doit démarrer immédiatement.

### Résolution des incidents {#troubleshooting}

Si vous obtenez un écran noir lorsque vous vous connectez en tant qu'utilisateur du Kiosque, cela signifie que vous avez peut-être incorrectement spécifié le chemin d'accès au fichier exécutable du lecteur Windows. Connectez-vous en tant qu’administrateur et vérifiez et réexécutez le script.

Le chemin d’installation par défaut du lecteur Windows est :

***C:\Users\&amp;lt;your user&gt;\AppData\Local\Programs\@aem-screensscreens-player-électron\AEM Screens Player.exe***

L’exemple de script dans les liens active et désactive le shell personnalisé. Vous devrez donc peut-être diviser le script en deux et activer/désactiver les lignes applicables suivantes :

>[!NOTE]
>
>Dans certains environnements Windows, les scripts PowerShell peuvent être restreints par la stratégie (en particulier les scripts non signés). Pour exécuter votre script, vous devrez peut-être désactiver temporairement cette restriction et la réactiver pour exécuter le script. Ouvrez une fenêtre PowerShell et utilisez ces commandes.
>
>*set-exécututionpolicy sans restriction* - pour supprimer temporairement les restrictions
>
>*set-exécututionpolicy limited* - pour réactiver la restriction après l’exécution du script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

