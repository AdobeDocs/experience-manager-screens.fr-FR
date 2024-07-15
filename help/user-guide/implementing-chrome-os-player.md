---
title: Mise en œuvre du lecteur Chrome OS
description: Découvrez comment mettre en œuvre le lecteur Chrome OS à l’aide de la console de gestion de Chrome.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 100%

---

# Mise en œuvre du lecteur Chrome OS {#implementing-chrome-os-player}

Cette section décrit comment mettre en œuvre le lecteur Chrome OS Player à l’aide de la console de gestion de Chrome.

## Utilisation de la console de gestion de Chrome {#using-chrome-management-console}

Pour installer la console de gestion de Chrome, procédez comme suit :

1. Enregistrez-vous pour obtenir la console de gestion de Chrome. Vous devez obtenir une licence pour la console de gestion de Chrome. Pour plus d’informations sur la gestion des paramètres des appareils Chrome, contactez le [Support Google](https://support.google.com/chrome/a/answer/1375678?hl=fr&amp;ref_topic=2935995).
1. Enregistrez votre appareil Chrome OS dans le domaine et attendez 15 minutes que l’appareil se synchronise avec la console de gestion de Chrome. Pour en savoir plus sur l’enregistrement d’un appareil Chrome, cliquez [ici](https://support.google.com/chrome/a/answer/1360534?hl=fr).
1. Le lecteur Chrome est disponible dans le Chrome Web Store.

>[!NOTE]
>
>Une solution de gestion des appareils, comme la console de gestion de Chrome, est recommandée pour le déploiement et la gestion des appareils Chrome OS. Même si ce document contient la mise en œuvre de la console de gestion de Chrome, d’autres fournisseurs proposent des fonctionnalités similaires. Veuillez contacter le fournisseur de votre logiciel de gestion des appareils.

## Attribution d’un nom au lecteur Chrome OS {#name-chrome}

Vous pouvez attribuer un nom d’appareil convivial à votre lecteur Chrome et envoyer le nom d’appareil choisi à Adobe Experience Manager (AEM). Cette fonctionnalité vous permet non seulement de nommer votre lecteur Chrome, mais également d’attribuer facilement le contenu approprié.

>[!NOTE]
>Vous ne pouvez choisir le nom du lecteur qu’avant l’enregistrement. Une fois le lecteur enregistré, son nom ne peut plus être modifié.

Pour configurer le nom dans le lecteur Chrome, procédez comme suit :

1. Vous pouvez éventuellement autoriser les intégrateurs et intégratrices audiovisuel ou les administrateurs et administratrices informatique à définir l’ID et l’emplacement de la ressource dans le cadre de l’inscription de l’entreprise.

   ![Image](/help/user-guide/assets/chrome-device/chrome1.png)

1. Les options s’affichent lorsque vous pouvez inscrire l’appareil.

   ![image](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. Vous pouvez définir l’ID de ressource dans le cadre de l’inscription d’entreprise, ainsi que dans la console de gestion de Chrome.

   ![Image](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Les lecteurs Chrome doivent être inscrits dans l’inscription d’entreprise et le lecteur Chrome doit être déployé à l’aide de la console de gestion de Chrome. Sinon, l’ID de ressource reviendra vide (par exemple, avec Chrome comme extension). Le nom de l’appareil n’est enregistré qu’au moment de l’inscription. Les modifications ultérieures ne seront pas prises en compte par Adobe Experience Manager (AEM).

### Activation du mode kiosque {#enabling-kiosk-mode}

Pour activer le mode de kiosque, procédez comme suit :

1. Connectez-vous à la Developer Console de Chrome.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Accédez à **Gestion des appareils** > **Gestion de Chrome** > **Paramètres d’appareil**.
1. Faites défiler l’écran jusqu’à **Paramètres du kiosque** et cliquez sur **Gérer les applications du kiosque**.

   ![kiosque](assets/kiosk.png)

1. Cliquez sur le lecteur AEM Screens dans le Chrome Web Store.

   >[!NOTE]
   >
   >Une application publiée récemment peut mettre 15 minutes environ à s’afficher dans cette liste.

1. Cliquez sur **Lecteur AEM Screens** dans la liste déroulante **Application de kiosque à lancement automatique**.

   L’opération peut prendre quelques minutes en fonction du réseau pour que les modifications soient appliquées. Il est recommandé de démarrer.

#### Vérification du statut des appareils distants {#checking-remote-device-status}

1. Connectez-vous à la Developer Console de Chrome.
1. Accédez à **Gestion des appareils** > **Appareils Chrome** et cliquez sur l’appareil à contrôler.
1. Cliquez sur **Activité du système et dépannage**.
1. Vérifiez les propriétés **Redémarrer l’appareil** et **Copie d’écran** de l’appareil. Vous pouvez également vérifier l’état du périphérique et les informations relatives à son intégrité.

>[!NOTE]
>
>Ces paramètres peuvent être activés plusieurs minutes après l’inscription de l’appareil. Chaque option peut être activée au fil du temps.

### Configuration de la configuration à distance des lecteurs Chrome OS {#configuring-remote-configuration-of-chrome-os-players}

Le lecteur AEM Screens est une application du kiosque, qui permet également de configurer des politiques à distance pour les lecteurs Chrome OS.

Suivez les étapes ci-dessous pour configurer différentes options du lecteur :

1. Connectez-vous à la console de gestion de Chrome.
1. Cliquez sur **Gestion des appareils** > **Gestion de Chrome** > **Gestion des applications**. Le lecteur AEM Screens s’affiche dans la liste.
1. Cliquez sur l’application **Lecteur AEM Screens**.
1. Cliquez sur **Paramètres du kiosque** et sur votre organisation (*si vous utilisez un environnement de test*).
1. Cliquez sur **Charger un fichier de configuration** et chargez la politique de configuration (*fichier JSON*).
1. Cliquez sur **Enregistrer**. Redémarrez l’appareil afin de pouvoir synchroniser la politique.

>[!NOTE]
>
>Redémarrez l’appareil afin de pouvoir synchroniser les modifications de politique.

#### Exemple de fichier JSON de politique {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### Attributs et objectif des politiques {#policy-attributes-and-purpose}

Le tableau ci-dessous récapitule les politiques et leurs fonctions.

| **Nom de la politique** | **Objectif** |
|---|---|
| serveur | L’URL du serveur Adobe Experience Manager (AEM). |
| registrationKey | Utilisé pour l’enregistrement en masse des appareils à l’aide d’une clé pré-partagée. |
| resolution | Résolution de l’appareil. |
| rebootSchedule | Planification du redémarrage du lecteur. |
| enableAdminUI | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Définissez la valeur sur false une fois qu’elle est entièrement configurée et en production. |
| enableOSD | Activez l’interface d’utilisation du sélecteur de canal pour que les utilisateurs et utilisatrices changent de canaux sur l’appareil. Pensez à la définir sur false une fois qu’elle est entièrement configurée et en production. |
| enableActivityUI | Activez cette règle pour afficher la progression des activités, comme le téléchargement et la synchronisation. Activez cette règle pour le dépannage et désactivez-la une fois qu’elle est entièrement configurée et en production. |
| cloudMode | Définissez cette valeur sur true si vous souhaitez que le lecteur Chrome se connecte à Screens as a Cloud Service. Définissez cette variable sur false pour vous connecter à AMS ou à AEM On-Premise. |
| cloudToken | Jeton d’enregistrement à enregistrer dans Screens as a Cloud Service. |

>[!NOTE]
>
>Les configurations de politique sont strictement appliquées et l’interface utilisateur d’administration du lecteur ne remplace pas manuellement. Pour permettre la configuration manuelle du lecteur pour une politique spécifique, ne spécifiez pas la politique dans la ***configuration de politique***. Par exemple, si vous souhaitez autoriser une configuration manuelle pour le planning du redémarrage, ne spécifiez pas la clé ***rebootSchedule*** dans la configuration de politique.

### Utiliser la commande à distance Screens {#using-remote-control}

AEM Screens offre une fonctionnalité de commande à distance. Pour en savoir plus sur cette fonctionnalité, cliquez ici : [Commande à distance Screens](implementing-remote-control.md)
