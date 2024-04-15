---
title: Lecteur Tizen
description: Cette page décrit l’installation et le fonctionnement du lecteur Tizen.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 52%

---

# Implémentation du lecteur Tizen {#tizen-player}

## Installation du lecteur Tizen {#installing-tizen-player}

Pour mettre en œuvre le lecteur Tizen avec AEM Screens, procédez comme suit :

1. Accédez au [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/) pour télécharger le lecteur Tizen.

1. Installez le fichier *(.zip)* du lecteur Tizen à partir de l’ordinateur local.

## Configuration du serveur HTTP {#setting-local-server}

>[!NOTE]
> Extrayez le fichier zip et rendez le lecteur Tizen disponible via un `http server`. (Il n’est pas nécessaire que le `http server` soit un serveur local ou Apache).

Suivez les étapes ci-dessous :

1. Copiez les deux fichiers extraits (`AEMScreensPlayer.wgt` et `sssp_config.xml`) dans le répertoire racine de votre serveur web Apache local.

   >[!NOTE]
   >Le fichier `AEMScreensPlayer.wgt` est l’application du lecteur Tizen, tandis que le fichier `sssp_config.xml` contient des informations sur ce mappage qui vous aide à l’installer sur l’appareil Tizen.

1. Obtenez l’adresse IP ou l’URL de votre serveur HTTP local (et le chemin d’accès au dossier contenant les fichiers extraits à l’étape 2 s’ils sont extraits dans un sous-dossier et non dans le dossier racine).

1. Le lecteur Tizen télécharge le programme d’installation à partir du serveur local.

### Nommage d’un lecteur Tizen {#name-tizen}

Vous pouvez attribuer un nom d’appareil convivial à votre lecteur Tizen, envoyant ainsi le nom d’appareil attribué à Adobe Experience Manager (AEM). Cette fonctionnalité vous permet non seulement d’attribuer un nom à votre lecteur Tizen, mais également d’attribuer facilement le contenu approprié.

>[!NOTE]
>Vous ne pouvez choisir le nom du lecteur qu’avant l’enregistrement. Une fois le lecteur enregistré, le nom du lecteur ne peut plus être modifié.

Pour configurer le nom dans le lecteur Tizen, procédez comme suit :

1. Sélectionnez le bouton de menu sur votre télécommande.
1. Accédez à **network** > **Nom de l’appareil** vous pouvez ainsi attribuer un nom au lecteur.

### Configuration des mises à jour sur l’appareil Samsung {#config-updates}

Suivez les étapes ci-dessous sur le périphérique Samsung afin de pouvoir terminer l’installation du lecteur AEM Screens sur le périphérique :

1. Accédez à votre appareil Samsung et activez-le.
1. Sélectionnez la variable **MENU** à partir de la télécommande de l’appareil et faites défiler l’écran jusqu’à **Système** dans la barre de navigation de gauche.
1. Faites défiler la page vers le bas et sélectionnez l’option **Play via** (Lecture sur) et remplacez-la par l’option **URL Launcher** (Lancement d’URL).
   ![image](/help/user-guide/assets/tizen/rms-2.png)
1. Lorsque le lanceur d’URL est défini, appuyez sur la touche **Accueil** à partir de votre télécommande.
1. Accédez au **Paramètres du lanceur d’URL** et saisissez l’adresse IP de votre serveur localhost, puis sélectionnez **Terminé**.

   >[!NOTE]
   >Le lecteur Tizen doit maintenant pouvoir se connecter au serveur http.

1. Le lecteur AEM Screens installe et se lance automatiquement sur votre périphérique Samsung.

   >[!NOTE]
   >L’appareil Tizen et le serveur `http` doivent pouvoir se connecter les uns aux autres, c’est-à-dire que le serveur doit être accessible au lecteur Tizen.


## Exonération des agents utilisateur avec le problème de cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Cette section s’applique à Adobe Experience Manager (AEM) 6.5.5 à AEM 6.5.7**
>
>Certains moteurs de navigateur sont incompatibles avec la variable *`SameSite=None`* utilisé dans le jeton de connexion émis par AEM 6.5.5 vers AEM 6.5.7. En règle générale, le problème peut être résolu en mettant à niveau le navigateur vers la dernière version disponible. Il arrive que de telles mises à niveau ne soient pas possibles, par exemple avec des affichages intelligents, des décodeurs ou d’autres périphériques avec des moteurs de navigation intégrés.

Suivez les étapes ci-dessous pour exempter ces clients incompatibles lors de l’utilisation de l’attribut *SameSite=None* :

1. Mettez à niveau vers le Service Pack Adobe Experience Manager (AEM) 6.5.7.

1. Une fois AEM redémarré, accédez à `/system/console/configMgr` et recherchez **Gestionnaire d’authentification des jetons Adobe Granite**. Définissez la valeur **SameSite** sur **None**.

1. Vous devriez voir une nouvelle option. *`User agents to be exempted from samesite attribute`*. Renseignez ce champ avec une expression régulière correspondant aux agents utilisateur qui ne sont pas compatibles avec l’attribut *SameSite=None*.

   >[!NOTE]
   >
   >Consultez [SameSite=None : clients incompatibles connus](https://www.chromium.org/updates/same-site/incompatible-clients) pour plus d’informations. Pour le lecteur Tizen, utilisez l’expression régulière : `(.*)Tizen(.*)`.

1. Enregistrez le lecteur Tizen dans votre instance AEM 6.5.5 ou ultérieure, il doit alors s’enregistrer et afficher le contenu normalement.

## Approvisionnement à distance du lecteur Tizen {#remote-provisioning}

La mise en service à distance du lecteur Tizen vous permet de déployer des centaines et des milliers d’affichages Samsung Tizen sans effort. Cela évite d’avoir à configurer manuellement chaque lecteur avec l’URL du serveur et le code d’enregistrement en masse, ou d’autres paramètres. Si AEM Screens est as a Cloud Service, configurez le mode cloud et le jeton cloud.

Cette fonctionnalité vous permet de configurer à distance le lecteur Tizen et de mettre à jour ces configurations de manière centralisée, si nécessaire. Tout ce dont vous avez besoin est le serveur `HTTP` utilisé pour héberger l’application Tizen `(wgt and xml file)` et un éditeur de texte pour enregistrer le code `config.json` avec les paramètres appropriés.

Assurez-vous d’avoir configuré l’adresse du lanceur d’URL sur le périphérique Tizen, c’est-à-dire le bouton d’accueil > les paramètres du lanceur d’URL.
Sur le serveur `HTTP` qui héberge l’application Tizen, placez le fichier `config.json` au même emplacement que le fichier `wgt`. Le nom du fichier doit être `config.json`.
Le lecteur Tizen installe et au lancement (et à chaque redémarrage), vérifie et applique les paramètres dans la variable `config.json` fichier .

### Exemple de politique JSON {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### Attributs et objectif des politiques {#policy-attributes}

Le tableau ci-dessous récapitule les politiques avec leurs fonctions.

>[!NOTE]
>Les configurations de politiques sont appliquées strictement et ne sont pas remplacées manuellement dans l’interface utilisateur d’administration du lecteur. Pour autoriser la configuration manuelle du lecteur pour une stratégie spécifique, ne spécifiez pas la stratégie dans la configuration de la stratégie.
>Par exemple, si vous souhaitez autoriser une configuration manuelle pour la planification du redémarrage, ne spécifiez pas la clé `rebootSchedule` dans la configuration de la stratégie. Les configurations de politiques sont lues chaque fois que le lecteur se recharge.

| **Nom de la politique** | **Objectif** |
|---|---|
| serveur | L’URL du serveur Adobe Experience Manager (AEM). |
| registrationKey | Utilisé pour l’enregistrement en masse des appareils à l’aide d’une clé pré-partagée. |
| resolution | Résolution de l’appareil. |
| rebootSchedule | Planification du redémarrage du lecteur. |
| enableAdminUI | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Définissez la valeur sur false une fois qu’elle est entièrement configurée et en production. |
| enableOSD | Activez l’interface utilisateur du sélecteur de canal pour que les utilisateurs changent de canaux sur l’appareil. Pensez à la définir sur false une fois qu’elle est entièrement configurée et en production. |
| enableActivityUI | Activez cette option pour afficher la progression des activités, telles que le téléchargement et la synchronisation. Activez cette règle pour le dépannage et désactivez-la une fois qu’elle est entièrement configurée et en production. |
| cloudMode | Définissez cette variable sur true si vous souhaitez que le lecteur Tizen se connecte à Screens as a Cloud Service. Définissez cette variable sur false pour vous connecter à AMS ou à l’AEM on-premise. |
| cloudToken | Jeton d’enregistrement à enregistrer dans Screens as a Cloud Service. |


## Enregistrement de l’appareil Tizen auprès du Remote Management Service (RMS) Samsung {#enroll-tizen-device-rms}

Suivez les étapes ci-dessous pour enregistrer l’appareil Tizen auprès du Remote Management Service (RMS) Samsung et configurer à distance le lanceur d’URL :

>[!NOTE]
>Vérifiez les paramètres réseau et le moniteur.

1. Accédez à **Menu** -> **Network** (Réseau) -> **Server Network Settings** (Paramètres réseau du serveur) et appuyez sur **Done** (Entrée).

1. Accédez à l’adresse du serveur, entrez l’URL MagicInfo et appuyez sur **Done** (Terminé).

1. Configurez TLS, si nécessaire. Accédez au port, sélectionnez le numéro de port sur le serveur, puis sélectionnez **Enregistrer**.

1. Accédez au **Appareil** et recherchez le périphérique que vous avez configuré. Lorsqu’un appareil est trouvé, cochez la case, puis sélectionnez **Approuver**.

   >![image](/help/user-guide/assets/tizen/rms-3.png)

1. Renseignez les informations requises et sélectionnez un groupe d’appareils. Sélectionnez **OK**.

   >![image](/help/user-guide/assets/tizen/rms-7.png)

1. Lorsque l’appareil est approuvé, il apparaît dans la liste des appareils. Sélectionner *Informations* sur la zone de votre périphérique, comme illustré ci-dessous.

   >![image](/help/user-guide/assets/tizen/rms-6.png)

1. La boîte de dialogue présentant les informations sur l’appareil s’affiche. Sélectionnez la variable **Informations sur le périphérique** et sélectionnez **Modifier**.

   >![image](/help/user-guide/assets/tizen/rms-5.png)

1. Modifiez les options de l’appareil et sélectionnez l’onglet **Setup** (Configuration). Accédez à **Lanceur d’URL** et saisissez l’URL hébergeant le wgt et `SSSP config file` pour pouvoir installer un `SSSP` , comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/tizen/rms-9.png)

1. Sélectionnez **Enregistrer**.

### Utiliser la commande à distance Screens {#using-remote-control}

AEM Screens offre une fonctionnalité de commande à distance. Pour en savoir plus sur cette fonctionnalité, cliquez ici : [Commande à distance Screens](implementing-remote-control.md)
