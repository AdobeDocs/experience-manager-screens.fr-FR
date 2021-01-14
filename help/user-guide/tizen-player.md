---
title: Lecteur Tizen
description: Cette page décrit l’installation et le fonctionnement du lecteur Tizen.
translation-type: tm+mt
source-git-commit: 092be09ec9477c9ff7561347d8f05641a90a9b40
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 21%

---


# Implémentation du lecteur Tizen {#tizen-player}

## Installation du lecteur Tizen {#installing-tizen-player}

Pour mettre en œuvre le lecteur Tizen avec AEM Screens, procédez comme suit :

1. Accédez à la page [Téléchargements de lecteurs AEM 6.5](https://download.macromedia.com/screens/) pour télécharger le lecteur Tizen.

1. Installez le fichier du lecteur Tizen *(.zip)* depuis l’ordinateur local.

## Exonération des agents utilisateur avec la publication du cookie Samesite {#exempting-user-agents}

>[!IMPORTANT]
>**Cette section s&#39;applique à Adobe Experience Manager (AEM) 6.5.5 à AEM 6.5.7**
>Certains moteurs de navigateur sont incompatibles avec l&#39;attribut *SameSite=None* utilisé dans le jeton de connexion émis par AEM 6.5 à AEM 6.7. Dans la plupart des cas, le problème peut être résolu en mettant à niveau le navigateur vers la dernière version disponible. Dans certains cas, de telles mises à niveau peuvent ne pas être possibles, par exemple avec des écrans dynamiques, des décodeurs ou d&#39;autres périphériques avec des moteurs de navigation intégrés.

Suivez les étapes ci-dessous pour exempter ces clients incompatibles lors de l’utilisation de *SameSite=None* :

1. Mise à niveau vers Adobe Experience Manager (AEM) Service Pack 6.5.8.

1. Accédez à `/system/console/bundles` dans AEM et cliquez sur le bouton `install/update`.

1. Installez le fichier jar `crx-auth-token`. Vous devrez peut-être arrêter et redémarrer AEM après avoir installé ce fichier jar, car il est lié à l&#39;authentification.

1. Après AEM redémarrez, accédez à `/system/console/configMgr` et recherchez **Gestionnaire d&#39;authentification du jeton Granite Adobe**. Définissez la valeur **SameSite** sur **None**.

1. Vous devriez voir une nouvelle option *Agents utilisateur à exempter de l&#39;attribut samesite*. Renseignez ce champ avec un regex correspondant aux agents utilisateur qui est(sont) incompatible avec l’attribut *SameSite=None*.
   >[!NOTE]
   >Voir [SameSite=None: Clients incompatibles connus ](https://www.chromium.org/updates/same-site/incompatible-clients) pour plus d’informations. Pour le lecteur Tizen, utilisez l’expression regex : `(.*)Tizen (4|5)(.*)`.

1. Enregistrez le lecteur Tizen par rapport à votre instance AEM 6.5.5 et ultérieure et il doit s&#39;enregistrer et afficher le contenu normalement.


## Configuration du serveur local et extraction des fichiers ZIP {#setting-local-server}

Suivez les étapes ci-dessous pour configurer le serveur local et copier les fichiers extraits :

1. Obtenez l’adresse IP de votre ordinateur local.
   >[!NOTE]
   >Consultez la documentation officielle pour savoir comment activer le serveur local sur votre plateforme.

1. Depuis le terminal, accédez au même répertoire que le dossier du programme d’installation décompressé et vérifiez que l’hôte local fonctionne.

1. Le lecteur Tizen télécharge ensuite le programme d’installation à partir du serveur local.

1. Copiez les deux fichiers extraits tels que `AEMScreensPlayer.wgt` et `sssp_config.xml` dans le répertoire racine de votre serveur Web Apache local.

   >[!NOTE]
   >`AEMScreensPlayer.wgt`est l&#39;application réelle du lecteur Tizen et `sssp_config.xml` contient des informations sur ce mappage qui vous aide à l&#39;installer sur le périphérique Tizen.

### Configuration des mises à jour sur le périphérique Samsung {#config-updates}

Suivez les étapes ci-dessous sur le périphérique Samsung pour effectuer l’installation du lecteur AEM Screens :

1. Accédez à votre périphérique Samsung et activez-le.

1. Cliquez sur le bouton **MENU** de la télécommande du périphérique et faites défiler la liste jusqu&#39;à **Système** dans la barre de navigation de gauche.

1. Faites défiler l’écran vers le bas et sélectionnez l’option **Lecture via le lanceur d’URL**.
   ![image](/help/user-guide/assets/tizen/rms-2.png)

1. Appuyez sur le bouton **Accueil** de votre télécommande.

1. Entrez l’adresse IP de votre serveur localhost.

1. Sélectionnez **À distance** dans **Mode développeur**.

1. Cliquez sur le bouton **Accueil** de la télécommande du périphérique et sélectionnez **Lanceur d’URL**.

1. Le lecteur AEM Screens devrait alors être automatiquement installé et lancé sur votre appareil Samsung.

## Approvisionnement en bloc de Tizen Player {#bulk-provisioning-tizen-player}

>[!NOTE]
>Il peut s’avérer fastidieux de saisir manuellement l’adresse de votre serveur AEM dans l’interface utilisateur d’administration de chaque périphérique pour un grand nombre de périphériques. Il est recommandé d&#39;utiliser la solution Samsung Remote Management (RMS) pour déployer et gérer la solution. Pour plus d&#39;informations, consultez [Enrollment the Tizen Device to Samsung Remote Management Service (RMS)](#enroll-tizen-device-rm).

Suivez les étapes ci-dessous pour configurer l’application en bloc afin qu’elle pointe vers votre instance d’auteur AEM au lancement :

1. Téléchargez et installez [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Ouvrez le fichier `wgt` à l’aide de Tizen studio.
1. Ouvrez le fichier `firmware-platform.js`, recherchez `DEFAULT_PREFERENCES` et remplacez l’URL du serveur par l’URL d’auteur AEM et enregistrez-la.
1. Créez le nouveau fichier `wgt`.

   >[!NOTE]
   >Vous devrez peut-être créer ou configurer un certificat de signature.

1. Déployez ce nouveau fichier RMS `wgt` et lorsque le lecteur est lancé, il doit automatiquement pointer vers votre serveur afin que vous n&#39;ayez pas à le saisir manuellement pour chaque périphérique.

### Inscription du périphérique Tizen à Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

Suivez les étapes ci-dessous pour inscrire le périphérique Tizen à Samsung Remote Management Service (RMS) et configurer à distance le lanceur d’URL :

>[!NOTE]
>Vérifiez les paramètres réseau et le moniteur.

1. Accédez à **Menu** -> **Réseau** -> **Paramètres réseau du serveur** et appuyez sur **Entrée**.

   >[!NOTE]
   >Vérifiez que l’écran est configuré pour Lire via le lanceur d’URL.
   >![image](/help/user-guide/assets/tizen/rms-2.png)

1. Accédez à l’adresse du serveur et tapez dans l’accès à l’URL MagicInfo et appuyez sur Terminé.

1. Configurez TLS, si nécessaire. Accédez au port et sélectionnez le numéro de port sur le serveur. Cliquez sur **Enregistrer**.

1. Accédez à l&#39;onglet **Périphérique** et recherchez le périphérique que vous venez de configurer. Une fois qu&#39;un périphérique a été trouvé, cochez la case et sélectionnez **Approuver**.

1. Renseignez les informations requises et sélectionnez un groupe de périphériques. Cliquez sur **OK** pour terminer le processus d&#39;approbation.

   >![image](/help/user-guide/assets/tizen/rms-7.png)

1. Une fois le périphérique approuvé, il doit apparaître sur la Liste du périphérique. Cliquez sur le bouton *Information* situé dans la zone de votre périphérique, c&#39;est-à-dire **i**, comme indiqué dans la figure ci-dessous.

   >![image](/help/user-guide/assets/tizen/rms-6.png)

1. La boîte de dialogue d’informations sur le périphérique s’affiche. Sélectionnez l&#39;onglet **Informations sur le périphérique** et cliquez sur **Modifier**.

   >![image](/help/user-guide/assets/tizen/rms-5.png)

1. Modifiez les options du périphérique et sélectionnez l&#39;onglet **Configuration**. Accédez à la section **Lancement d&#39;URL** et saisissez l&#39;URL hébergeant le wgt et `SSSP config file` pour installer une application `SSSP`, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/tizen/rms-9.png)

1. Cliquez sur **Enregistrer** pour que les modifications s&#39;affichent sur l&#39;écran.




