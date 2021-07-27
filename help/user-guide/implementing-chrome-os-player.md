---
title: Mise en œuvre du lecteur Chrome OS
seo-title: Mise en œuvre du lecteur Chrome OS
description: Suivez cette page pour découvrir comment mettre en œuvre le lecteur Chrome OS à l’aide de la console de gestion de Chrome.
seo-description: Suivez cette page pour découvrir comment mettre en œuvre le lecteur Chrome OS à l’aide de la console de gestion de Chrome.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administration d’AEM Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: ht
source-wordcount: '829'
ht-degree: 100%

---

# Mise en œuvre du lecteur Chrome OS  {#implementing-chrome-os-player}

Cette section décrit comment mettre en œuvre le lecteur Chrome OS Player à l’aide de la console de gestion de Chrome.

## Utilisation de la console de gestion de Chrome {#using-chrome-management-console}

Pour installer la console de gestion de Chrome, exécutez la procédure suivante :

1. Enregistrez-vous pour obtenir la console de gestion de Chrome. Vous devez obtenir une licence pour la console de gestion de Chrome. Pour plus d’informations sur la gestion des paramètres des appareils Chrome, contactez le [Support Google](https://support.google.com/chrome/a/answer/1375678?hl=fr&amp;ref_topic=2935995).
1. Enregistrez votre appareil Chrome OS dans le domaine. Attendez 15 minutes que l’appareil se synchronise avec la console de gestion de Chrome. Pour en savoir plus sur l’enregistrement d’un appareil Chrome, cliquez [ici](https://support.google.com/chrome/a/answer/1360534?hl=fr).
1. Le lecteur Chrome sera disponible dans le Chrome Web Store.

>[!NOTE]
>
>Une solution de gestion des appareils, comme la console de gestion de Chrome, est recommandée pour le déploiement et la gestion des appareils Chrome OS. Même si ce document contient la mise en œuvre de la console de gestion de Chrome, d’autres fournisseurs proposent des fonctionnalités similaires. Contactez le fournisseur de votre logiciel de gestion d’appareils.

## Nommage du lecteur Chrome OS {#name-chrome}

Vous pouvez attribuer un nom d’appareil convivial à votre lecteur Chrome et envoyer le nom d’appareil choisi à Adobe Experience Manager (AEM). Cette fonctionnalité vous permet non seulement de nommer votre lecteur Chrome, mais également d’attribuer facilement le contenu approprié.

Pour configurer le nom dans le lecteur Chrome, procédez comme suit :

1. Vous pouvez éventuellement autoriser les intégrateurs AV ou les administrateurs informatiques à définir l’ID et l’emplacement de la ressource dans le cadre de l’inscription de l’entreprise.

   ![image](/help/user-guide/assets/chrome-device/chrome1.png)

1. Les options s’affichent lorsque vous pouvez inscrire l’appareil.

   ![image](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. Vous pouvez définir l’ID de ressource dans le cadre de l’inscription à l’entreprise, ainsi que dans la console de gestion de Chrome.

   ![image](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Les lecteurs Chrome doivent être inscrits dans l’inscription d’entreprise et le lecteur Chrome doit être déployé à l’aide de la console de gestion de Chrome. Sinon, l’ID de ressource reviendra vide (par exemple, avec Chrome comme extension). Le nom de l’appareil n’est enregistré qu’au moment de l’inscription. Les modifications ultérieures ne seront pas prises en compte par Adobe Experience Manager (AEM).

### Activation du mode kiosque {#enabling-kiosk-mode}

Pour activer le mode de kiosque, procédez comme suit :

1. Connectez-vous à la console de développement de Chrome.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Sélectionnez **Gestion des appareils** > **Gestion de Chrome** > **Paramètres d’appareil**.
1. Faites défiler l’écran jusqu’à **Paramètres du kiosque** et cliquez sur **Gérer les applications du kiosque**.

   ![kiosque](assets/kiosk.png)

1. Sélectionnez le lecteur AEM Screens dans le Chrome Web Store.

   >[!NOTE]
   >
   >Une application publiée récemment peut mettre 15 minutes environ à s’afficher dans cette liste.

1. Sélectionnez **Lecteur AEM Screens** dans la liste déroulante **Application de kiosque à lancement automatique**.

   L’opération peut prendre quelques minutes en fonction du réseau pour que les modifications soient appliquées. Il est recommandé de démarrer.

#### Vérification du statut des appareils distants {#checking-remote-device-status}

1. Connectez-vous à la console de développement de Chrome.
1. Sélectionnez **Gestion des appareils** > **Appareils Chrome** et sélectionnez l’appareil à contrôler.
1. Cliquez sur **Activité du système et résolution des incidents**.
1. Vérifiez les propriétés **Redémarrer l’appareil** et **Copie d’écran** de l’appareil. Vous pouvez également vérifier le statut de l’appareil et ses informations d’intégrité.

>[!NOTE]
>
>Notez que ces paramètres peuvent être activés quelques minutes après l’enregistrement de l’appareil. Chaque option peut être activée au fil du temps.

### Configuration de la configuration à distance des lecteurs Chrome OS {#configuring-remote-configuration-of-chrome-os-players}

Le lecteur AEM Screens est une application du kiosque, qui permet également de configurer des règles à distance pour les lecteurs Chrome OS.

Pour configurer les différentes options du lecteur, procédez comme suit :

1. Connectez-vous à la console de gestion de Chrome.
1. Sélectionnez **Gestion des appareils** > **Gestion de Chrome** > **Gestion des applications**. Le lecteur AEM Screens s’affiche dans la liste.
1. Cliquez sur l’application **Lecteur AEM Screens**.
1. Cliquez sur **Paramètres du kiosque** et sélectionnez votre organisation (*si vous utilisez un environnement de test*).
1. Cliquez sur **Charger un fichier de configuration** et chargez la règle de configuration (*fichier JSON*).
1. Cliquez sur **Enregistrer**. Vous devez redémarrer l’appareil pour synchroniser la règle.

>[!NOTE]
>
>Redémarrez l’appareil pour synchroniser les modifications apportées à la règle.

#### Exemple de fichier JSON de règle {#example-policy-json-file}

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

### Attributs et objectif des règles {#policy-attributes-and-purpose}

Le tableau ci-dessous récapitule les règles avec leurs fonctions.

| **Nom de la règle** | **Objectif** |
|---|---|
| *server* | Adresse URL du serveur Adobe Experience Manager |
| *resolution* | Résolution de l’appareil Chrome OS |
| *rebootSchedule* | Planification du redémarrage du lecteur Chrome |
| *enableAdminUI* | Activez l’interface utilisateur d’administration pour que les techniciens configurent l’appareil sur le site. Définissez la valeur sur false une fois qu’elle est entièrement configurée et en production. |
| *enableOSD* | Activez l’interface utilisateur du sélecteur de canal pour que les utilisateurs changent de canaux sur l’appareil. Pensez à la définir sur false une fois qu’elle est entièrement configurée et en production. |
| *enableActivityUI* | Activez cette règle pour afficher la progression des activités, comme le téléchargement et la synchronisation. Activez-la pour résoudre les incidents et désactivez-la une fois que l’interface est entièrement configurée et en production. |

>[!NOTE]
>
>Les configurations de règles sont appliquées strictement et ne sont pas remplacées manuellement dans l’interface utilisateur d’administration du lecteur. Pour permettre la configuration manuelle du lecteur pour une règle particulière, ne spécifiez pas la règle lors de la ***configuration des règles***, par exemple, si vous souhaitez permettre la configuration manuelle de la planification du redémarrage, ne spécifiez pas la clé ***rebootSchedule*** lors de la configuration des règles.
