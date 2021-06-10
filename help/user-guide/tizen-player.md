---
title: Lecteur Tizen
description: Cette page décrit l’installation et le fonctionnement du lecteur Tizen.
feature: Administration de Screens, lecteurs
role: Administrator
level: Intermediate
source-git-commit: ee731bc5169d2c76665bbfa18e3b8529619d83ce
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 72%

---


# Implémentation du lecteur Tizen {#tizen-player}

## Installation du lecteur Tizen {#installing-tizen-player}

Pour mettre en œuvre le lecteur Tizen avec AEM Screens, procédez comme suit :

1. Accédez à la page [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/) pour télécharger le lecteur Tizen.

1. Installez le fichier *(.zip)* du lecteur Tizen à partir de l’ordinateur local.

## Configuration du serveur local et extraction des fichiers ZIP {#setting-local-server}

>[!NOTE]
> Extrayez le fichier zip et rendez le lecteur Tizen disponible via un `http server`. (Il n’est pas nécessaire que le `http server` soit un serveur local ou Apache).

Suivez les étapes ci-dessous :

1. Copiez les deux fichiers extraits (`AEMScreensPlayer.wgt` et `sssp_config.xml`) dans le répertoire racine de votre serveur web Apache local.

   >[!NOTE]
   >Le fichier `AEMScreensPlayer.wgt` est l’application du lecteur Tizen, tandis que le fichier `sssp_config.xml` contient des informations sur ce mappage qui vous aide à l’installer sur le périphérique Tizen.

1. Obtenez l’adresse IP ou l’URL de votre serveur HTTP local (et le chemin d’accès au dossier contenant les fichiers extraits à l’étape 2 s’ils sont extraits dans un sous-dossier et non dans le dossier racine).

1. Le lecteur Tizen télécharge ensuite le programme d’installation à partir du serveur local.

### Lecteur Tizen portant le nom {#name-tizen}

Vous pouvez attribuer un nom d’appareil convivial à votre lecteur Tizen, envoyant ainsi le nom d’appareil attribué à Adobe Experience Manager (AEM). Cette fonctionnalité vous permet non seulement de nommer votre lecteur Tizen, mais également d’attribuer facilement le contenu approprié.

Pour configurer le nom dans le lecteur Tizen, procédez comme suit :

1. Cliquez sur le bouton de menu de votre télécommande.
1. Accédez à **network** —> **Nom du périphérique** pour attribuer un nom au lecteur.

### Configuration des mises à jour sur le périphérique Samsung {#config-updates}

Suivez les étapes ci-dessous sur le périphérique Samsung pour effectuer l’installation du lecteur AEM Screens :

1. Accédez à votre périphérique Samsung et activez-le.

1. Cliquez sur le bouton **MENU** de la télécommande du périphérique et faites défiler la liste jusqu’à **System** (Système) dans la barre de navigation de gauche.

1. Faites défiler la page vers le bas et sélectionnez l’option **Play via** (Lecture sur) et remplacez-la par l’option **URL Launcher** (Lancement d’URL).
   ![image](/help/user-guide/assets/tizen/rms-2.png)

1. Une fois le lanceur d’URL défini, appuyez sur le bouton **Home** (Accueil) de votre télécommande.

1. Accédez à **URL Launcher Settings** (Paramètres du lanceur d’URL), saisissez l’adresse IP de votre serveur hôte local et cliquez sur **Done** (Terminé).
   >[!NOTE]
   >Le lecteur Tizen doit maintenant pouvoir se connecter au serveur http.

1. Le lecteur AEM Screens devrait alors être automatiquement installé et lancé sur votre périphérique Samsung.

   >[!NOTE]
   >Le périphérique Tizen et le serveur `http` doivent pouvoir se connecter les uns aux autres, c’est-à-dire que le serveur doit être accessible au lecteur Tizen.


## Exonération des agents utilisateur avec le problème de cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Cette section s’applique à Adobe Experience Manager (AEM) versions 6.5.5 à 6.5.7**
>Certains moteurs de navigation sont incompatibles avec l’attribut *SameSite=None* utilisé dans le jeton de connexion émis par AEM versions 6.5 à 6.7. Dans la plupart des cas, le problème peut être résolu en mettant à jour le navigateur vers la dernière version disponible. Dans certains cas, de telles mises à niveau peuvent ne pas être possibles, par exemple avec des écrans intelligents, des décodeurs ou d’autres périphériques avec des moteurs de navigation intégrés.

Suivez les étapes ci-dessous pour exempter ces clients incompatibles lors de l’utilisation de l’attribut *SameSite=None* :

1. Mettez à niveau vers le Service Pack Adobe Experience Manager (AEM) 6.5.7.

1. Une fois AEM redémarré, accédez à `/system/console/configMgr` et recherchez **Adobe Granite Token Authentication Handler**. Définissez la valeur **SameSite** sur **None**.

1. Vous devriez voir une nouvelle option *Agents utilisateur à exempter de l’attribut samesite*. Renseignez ce champ avec une expression régulière correspondant aux agents utilisateur qui ne sont pas compatibles avec l’attribut *SameSite=None*.
   >[!NOTE]
   >Consultez [SameSite=None : clients incompatibles connus](https://www.chromium.org/updates/same-site/incompatible-clients) pour plus d’informations. Pour le lecteur Tizen, utilisez l’expression régulière : `(.*)Tizen(.*)`.

1. Enregistrez le lecteur Tizen dans votre instance AEM 6.5.5 ou ultérieure, il doit alors s’enregistrer et afficher le contenu normalement.

## Mise en service à distance du lecteur Tizen {#remote-provisioning}

La mise en service à distance du lecteur Tizen vous permet de déployer des centaines et des milliers d’affichages Samsung Tizen sans effort. Cela évite les efforts manuels fastidieux pour configurer chaque lecteur avec l’URL du serveur et le code d’enregistrement en masse, ou d’autres paramètres, et dans le cas de Screens en tant que Cloud Service pour configurer le mode cloud et le jeton cloud.

Cette fonctionnalité vous permet de configurer à distance le lecteur Tizen et de mettre à jour ces configurations de manière centralisée, si nécessaire. Tout ce dont vous avez besoin est le serveur `HTTP` utilisé pour héberger l’application Tizen `(wgt and xml file)` et un éditeur de texte pour enregistrer `config.json` avec les paramètres appropriés.

Assurez-vous d’avoir configuré l’adresse du lanceur d’URL sur le périphérique Tizen, c’est-à-dire les paramètres Bouton d’accueil —> Lancement d’URL .
Sur le serveur `HTTP` qui héberge l’application Tizen, placez le fichier `config.json` au même emplacement que le fichier `wgt`. Le nom du fichier doit être `config.json`.
Le lecteur Tizen s’installe et, au lancement (et à chaque redémarrage), vérifie et applique les paramètres du fichier `config.json`.

### Exemple de règle JSON {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### Attributs et objectif de la politique {#policy-attributes}

Le tableau ci-dessous récapitule les règles avec leurs fonctions.

>[!NOTE]
>Les configurations de stratégie sont strictement appliquées et ne sont pas remplacées manuellement dans l’interface utilisateur d’administration du lecteur. Pour permettre la configuration manuelle du lecteur pour une règle particulière, ne spécifiez pas la règle lors de la configuration des règles, par exemple, si vous souhaitez permettre la configuration manuelle de la planification du redémarrage, ne spécifiez pas la clé `rebootSchedule` lors de la configuration des règles. Les configurations de stratégie sont lues chaque fois que le lecteur se recharge.

| **Nom de la règle** | **Objectif** |
|---|---|
| server | URL du serveur Adobe Experience Manager (AEM). |
| registrationKey | Utilisé pour l’enregistrement en masse des appareils à l’aide d’une clé pré-partagée. |
| resolution | Résolution de l’appareil. |
| rebootSchedule | Planification de redémarrage du lecteur. |
| enableAdminUI | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Définissez la valeur sur false une fois qu’elle est entièrement configurée et en production. |
| enableOSD | Activez l’interface utilisateur du sélecteur de canal pour que les utilisateurs changent de canaux sur l’appareil. Pensez à définir sur false, une fois qu’il est entièrement configuré et en production. |
| enableActivityUI | Activez cette règle pour afficher la progression des activités, comme le téléchargement et la synchronisation. Activez-la pour résoudre les incidents et désactivez-la une fois que l’interface est entièrement configurée et en production. |
| cloudMode | Définissez cette variable sur true si vous souhaitez que le lecteur Tizen se connecte à Screens en tant que Cloud Service. Définissez cette variable sur false pour vous connecter à AMS ou à l’AEM on-Prem. |
| cloudToken | Jeton d’enregistrement à enregistrer auprès de Screens en tant que Cloud Service. |


## Enregistrement du périphérique Tizen auprès du Remote Management Service (RMS) Samsung {#enroll-tizen-device-rms}

Suivez les étapes ci-dessous pour enregistrer le périphérique Tizen auprès du Remote Management Service (RMS) Samsung et configurer à distance le lanceur d’URL :

>[!NOTE]
>Vérifiez les paramètres réseau et le moniteur.

1. Accédez à **Menu** -> **Network** (Réseau) -> **Server Network Settings** (Paramètres réseau du serveur) et appuyez sur **Done** (Entrée).

1. Accédez à l’adresse du serveur, entrez l’URL MagicInfo et appuyez sur **Done** (Terminé).

1. Configurez TLS, si nécessaire. Accédez au port et sélectionnez le numéro de port sur le serveur, puis cliquez sur **Save** (Enregistrer).

1. Accédez à l’onglet **Device** (Périphérique) et recherchez le périphérique que vous venez de configurer. Une fois le périphérique trouvé, cochez la case et sélectionnez **Approve** (Approuver).

   >![image](/help/user-guide/assets/tizen/rms-3.png)

1. Renseignez les informations requises et sélectionnez un groupe de périphériques. Cliquez sur **OK** pour terminer le processus d’approbation.

   >![image](/help/user-guide/assets/tizen/rms-7.png)

1. Une fois le périphérique approuvé, il doit apparaître dans la liste des périphériques. Cliquez sur le bouton *Information* situé dans l’icône de votre périphérique, c’est-à-dire le **i**, comme indiqué dans l’image ci-dessous.

   >![image](/help/user-guide/assets/tizen/rms-6.png)

1. La boîte de dialogue présentant les informations sur le périphérique s’affiche. Sélectionnez l’onglet **Device Info** (Informations sur le périphérique) et cliquez sur **Edit** (Modifier).

   >![image](/help/user-guide/assets/tizen/rms-5.png)

1. Modifiez les options du périphérique et sélectionnez l’onglet **Setup** (Configuration). Accédez à la section **URL Launcher** (Lancement d’URL) et saisissez l’URL hébergeant le wgt et le `SSSP config file` pour installer une application `SSSP`, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/tizen/rms-9.png)

1. Cliquez sur **Save** (Enregistrer) pour que les modifications s’affichent à l’écran.

