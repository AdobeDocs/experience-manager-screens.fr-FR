---
title: Lecteur Tizen
description: Découvrez comment installer et utiliser le lecteur Tizen.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 96%

---

# Implémentation du lecteur Tizen {#tizen-player}

## Installation du lecteur Tizen {#installing-tizen-player}

Pour implémenter le lecteur Tizen dans AEM Screens, procédez comme suit :

1. Accédez à la page [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/) pour télécharger le lecteur Tizen.

1. Installez le fichier *(.zip)* du lecteur Tizen à partir de votre ordinateur local.

## Configuration du serveur HTTP {#setting-local-server}

>[!NOTE]
> Extrayez le fichier zip et rendez le lecteur Tizen disponible via un `http server`. (Il n’est pas nécessaire que le `http server` soit un serveur local ou Apache).

Suivez les étapes ci-dessous :

1. Copiez les deux fichiers extraits (`AEMScreensPlayer.wgt` et `sssp_config.xml`) dans le répertoire racine de votre serveur web Apache local.

   >[!NOTE]
   >Le fichier `AEMScreensPlayer.wgt` est l’application du lecteur Tizen, tandis que le fichier `sssp_config.xml` contient des informations sur ce mappage qui vous aide à l’installer sur l’appareil Tizen.

1. Obtenez l’adresse IP ou l’URL de votre serveur HTTP local (et le chemin d’accès du dossier qui contient les fichiers extraits à l’étape 2 s’ils sont extraits dans un sous-dossier et non dans le dossier racine).

1. Le lecteur Tizen télécharge le programme d’installation à partir du serveur local.

### Nommer un lecteur Tizen {#name-tizen}

Vous pouvez attribuer un nom d’appareil convivial à votre lecteur Tizen et envoyer le nom d’appareil choisi à Adobe Experience Manager (AEM). Cette fonctionnalité vous permet non seulement de nommer votre lecteur Tizen, mais également d’affecter facilement du contenu approprié.

>[!NOTE]
>Vous ne pouvez choisir le nom du lecteur qu’avant l’enregistrement. Une fois le lecteur enregistré, son nom ne peut plus être modifié.

Pour configurer le nom dans le lecteur Tizen, procédez comme suit :

1. Cliquez sur le bouton menu de votre télécommande.
1. Accédez à **Réseau** > **Nom de l’appareil** pour attribuer un nom au lecteur.

### Configuration des mises à jour sur l’appareil Samsung {#config-updates}

Suivez les étapes ci-dessous sur l’appareil Samsung pour finaliser l’installation du lecteur AEM Screens sur cet appareil :

1. Accédez à votre appareil Samsung et activez-le.
1. Cliquez sur le bouton **MENU** de la télécommande de l’appareil et faites défiler la liste jusqu’à **System** (Système) dans la barre de navigation de gauche.
1. Faites défiler la page vers le bas et sélectionnez l’option **Lecture via** et sélectionnez l’option **Lanceur d’URL**.
   ![image](/help/user-guide/assets/tizen/rms-2.png)
1. Une fois le lanceur d’URL défini, appuyez sur le bouton **Accueil** de votre télécommande.
1. Accédez à **Paramètres du lanceur d’URL**, saisissez l’adresse IP de votre serveur hôte local et cliquez sur **Terminé**.

   >[!NOTE]
   >Le lecteur Tizen doit maintenant pouvoir se connecter au serveur HTTP.

1. Le lecteur AEM Screens est automatiquement installé et lancé sur votre appareil Samsung.

   >[!NOTE]
   >L’appareil Tizen et le serveur `http` doivent pouvoir se connecter les uns aux autres, c’est-à-dire que le serveur doit être accessible au lecteur Tizen.


## Exonération des agents utilisateur avec le problème de cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Cette section s’applique à Adobe Experience Manager (AEM) versions 6.5.5 à 6.5.7**
>
>Certains moteurs de navigation sont incompatibles avec l’attribut *`SameSite=None`* utilisé dans le jeton de connexion émis par AEM versions 6.5.5 à 6.5.7. Le problème peut en général être résolu en mettant à jour le navigateur vers la dernière version disponible. Parfois, de telles mises à niveau peuvent ne pas être possibles, par exemple avec des écrans intelligents, des décodeurs ou d’autres appareils avec des moteurs de navigation intégrés.

Suivez les étapes ci-dessous pour exempter ces clients incompatibles lors de l’utilisation de l’attribut *SameSite=None* :

1. Mettez à niveau vers le Service Pack Adobe Experience Manager (AEM) 6.5.7.

1. Une fois AEM redémarré, accédez à `/system/console/configMgr` et recherchez **Adobe Granite Token Authentication Handler**. Définissez la valeur **SameSite** sur **None**.

1. Vous devriez voir une nouvelle option *`User agents to be exempted from samesite attribute`*. Renseignez ce champ avec une expression régulière correspondant aux agents utilisateur qui ne sont pas compatibles avec l’attribut *SameSite=None*.

   >[!NOTE]
   >
   >Consultez [SameSite=None : clients incompatibles connus](https://www.chromium.org/updates/same-site/incompatible-clients) pour plus d’informations. Pour le lecteur Tizen, utilisez l’expression régulière : `(.*)Tizen(.*)`.

1. Enregistrez le lecteur Tizen dans votre instance AEM 6.5.5 ou ultérieure ; il doit alors s’enregistrer et afficher le contenu normalement.

## Approvisionnement à distance du lecteur Tizen {#remote-provisioning}

L’approvisionnement à distance du lecteur Tizen vous permet de déployer des centaines, voire des milliers d’appareils utilisant Samsung Tizen sans effort. Cela évite d’avoir à configurer manuellement chaque lecteur avec l’URL du serveur et le code d’enregistrement en bloc, ou d’autres paramètres. Si AEM Screens as a Cloud Service est présent, configurez le mode cloud et le jeton cloud.

Cette fonctionnalité vous permet de configurer à distance le lecteur Tizen et de mettre à jour ces configurations de manière centralisée, si nécessaire. Tout ce dont vous avez besoin est le serveur `HTTP` utilisé pour héberger l’application Tizen `(wgt and xml file)` et un éditeur de texte pour enregistrer le code `config.json` avec les paramètres appropriés.

Assurez-vous d’avoir configuré l’adresse du lanceur d’URL sur l’appareil Tizen. Cliquez sur le bouton Accueil > Paramètres du lanceur d’URL.
Sur le serveur `HTTP` qui héberge l’application Tizen, placez le fichier `config.json` au même emplacement que le fichier `wgt`. Le nom du fichier doit être `config.json`.
Le lecteur Tizen s’installe et, au lancement (et à chaque redémarrage), vérifie et applique les paramètres du fichier `config.json`.

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

Le tableau ci-dessous récapitule les politiques et leurs fonctions.

>[!NOTE]
>Les configurations de la politique de l’interface d’administration du lecteur sont appliquées de manière stricte et ne peuvent pas être remplacées manuellement. Pour autoriser la configuration manuelle du lecteur pour une politique spécifique, ne spécifiez pas la politique dans la configuration de politique.
>&#x200B;>Par exemple, si vous souhaitez autoriser une configuration manuelle pour le planning du redémarrage, ne spécifiez pas la clé `rebootSchedule` dans la configuration de politique. Les configurations de politiques sont lues chaque fois que le lecteur se recharge.

| **Nom de la politique** | **Objectif** |
|---|---|
| serveur | L’URL du serveur Adobe Experience Manager (AEM). |
| registrationKey | Utilisé pour l’enregistrement en masse des appareils à l’aide d’une clé pré-partagée. |
| resolution | Résolution de l’appareil. |
| rebootSchedule | Planification du redémarrage du lecteur. |
| enableAdminUI | Activez l’interface utilisateur d’administration pour configurer l’appareil sur site. Définissez la valeur sur false une fois qu’elle est entièrement configurée et en production. |
| enableOSD | Activez l’interface d’utilisation du sélecteur de canal pour que les utilisateurs et utilisatrices changent de canaux sur l’appareil. Pensez à la définir sur false une fois qu’elle est entièrement configurée et en production. |
| enableActivityUI | Activez cette option pour pouvoir afficher la progression des activités, telles que le téléchargement et la synchronisation. Activez cette règle pour le dépannage et désactivez-la une fois qu’elle est entièrement configurée et en production. |
| cloudMode | Définissez cette variable sur true si vous souhaitez que le lecteur Tizen se connecte à Screens as a Cloud Service. Définissez cette variable sur false pour vous connecter à AMS ou à AEM On-Premise. |
| cloudToken | Jeton d’enregistrement à enregistrer dans Screens as a Cloud Service. |


## Enregistrement de l’appareil Tizen auprès du Remote Management Service (RMS) Samsung {#enroll-tizen-device-rms}

Suivez les étapes ci-dessous pour enregistrer l’appareil Tizen auprès du Remote Management Service (RMS) Samsung et configurer à distance le lanceur d’URL :

>[!NOTE]
>Vérifiez les paramètres réseau et le moniteur.

1. Accédez à **Menu** -> **Network** (Réseau) -> **Server Network Settings** (Paramètres réseau du serveur) et appuyez sur **Done** (Entrée).

1. Accédez à l’adresse du serveur, saisissez l’URL MagicInfo et appuyez sur **Terminer**.

1. Configurez TLS, si nécessaire. Accédez au port et sélectionnez le numéro de port du serveur, puis cliquez sur **Enregistrer**.

1. Accédez à l’onglet **Appareil** et recherchez l’appareil que vous avez configuré. Lorsqu’un appareil est trouvé, cochez la case, puis cliquez sur **Approuver**.

   >![image](/help/user-guide/assets/tizen/rms-3.png)

1. Renseignez les informations requises et sélectionnez un groupe d’appareils. Cliquez sur **OK**.

   >![Image](/help/user-guide/assets/tizen/rms-7.png)

1. Une fois l’appareil approuvé, il apparaît dans la liste des appareils. Sélectionnez *Informations* sur la vignette de votre appareil, comme illustré ci-dessous.

   >![image](/help/user-guide/assets/tizen/rms-6.png)

1. La boîte de dialogue présentant les informations sur l’appareil s’affiche. Sélectionnez l’onglet **Informations sur l’appareil** et cliquez sur **Modifier**.

   >![image](/help/user-guide/assets/tizen/rms-5.png)

1. Modifiez les options de l’appareil et sélectionnez l’onglet **Configuration**. Accédez à la section **Lanceur d’URL** et saisissez l’URL hébergeant le wgt et le `SSSP config file` pour installer une application `SSSP`, comme illustré ci-dessous.

   ![image](/help/user-guide/assets/tizen/rms-9.png)

1. Cliquez sur **Save**.

### Utiliser la commande à distance Screens {#using-remote-control}

AEM Screens offre une fonctionnalité de commande à distance. Pour en savoir plus sur cette fonctionnalité, cliquez ici : [Commande à distance Screens](implementing-remote-control.md)
