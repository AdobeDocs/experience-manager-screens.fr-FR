---
title: Lecteur Tizen
description: Cette page décrit l’installation et le fonctionnement du lecteur Tizen.
feature: Administration de Screens, lecteurs
role: Administrator
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 100%

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

## Approvisionnement en masse du lecteur Tizen {#bulk-provisioning-tizen-player}

>[!NOTE]
>Il peut s’avérer fastidieux de saisir manuellement l’adresse de votre serveur AEM dans l’interface utilisateur d’administration de chaque périphérique pour un grand nombre de périphériques. Il est recommandé d’utiliser la solution Samsung Remote Management (RMS) pour déployer et gérer des solutions plus volumineuses. Pour plus d’informations, consultez [Enregistrement du périphérique Tizen auprès du Remote Management Service (RMS) Samsung](#enroll-tizen-device-rm).

Suivez les étapes ci-dessous pour approvisionner l’application en masse afin qu’elle pointe vers votre instance d’auteur AEM au lancement :

1. Téléchargez et installez [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Ouvrez le fichier `wgt` à l’aide de Tizen Studio.
1. Ouvrez le fichier `firmware-platform.js`, recherchez `DEFAULT_PREFERENCES` et remplacez l’URL du serveur par l’URL d’auteur AEM et enregistrez-la.
1. Créez le fichier `wgt`.

   >[!NOTE]
   >Vous devrez peut-être créer ou configurer un certificat de signature.

1. Déployez ce nouveau fichier `wgt` à l’aide de RMS ou du lanceur d’URL ; lorsque le lecteur est lancé, il doit automatiquement pointer vers votre serveur afin que vous n’ayez pas à le saisir manuellement pour chaque périphérique.

### Enregistrement du périphérique Tizen auprès du Remote Management Service (RMS) Samsung {#enroll-tizen-device-rms}

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
