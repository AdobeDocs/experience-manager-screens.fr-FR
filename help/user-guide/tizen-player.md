---
title: Lecteur Tizen
description: Cette page décrit l’installation et le fonctionnement du lecteur Tizen.
translation-type: tm+mt
source-git-commit: 1ec3e3541755550f719dbe53e83326d9796de14f
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 28%

---


# Implémentation du lecteur Tizen {#tizen-player}

## Installation du lecteur Tizen {#installing-tizen-player}

Pour mettre en œuvre le lecteur Tizen avec AEM Screens, procédez comme suit :

1. Accédez à la page [Téléchargements de lecteurs AEM 6.5](https://download.macromedia.com/screens/) pour télécharger le lecteur Tizen.

1. Installez le fichier du lecteur Tizen *(.zip)* depuis l’ordinateur local.

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
   ![image](/help/user-guide/assets/tizen/url-launcher.png)

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

Suivez les étapes ci-dessous pour inscrire Tizen Device à Samsung Remote Management Service (RMS) et configurer à distance le lanceur d&#39;URL :

>[!NOTE]
>Vérifiez les paramètres réseau et le moniteur.

1. Appuyez sur Menu sur votre télécommande, accédez à Système, puis appuyez sur Entrée sur Play Via.

   >[!NOTE]
   >Vérifiez que l’écran est configuré pour Lire par le lanceur d’URL.
1. Accédez à **Menu** -> **Réseau** -> **Paramètres réseau du serveur** et appuyez sur **Entrée**.

1. Accédez à l’adresse du serveur et tapez dans l’accès à l’URL MagicInfo et appuyez sur Terminé.

1. Accédez à l&#39;onglet Périphérique une fois connecté au SIG.
1. Recherchez le périphérique que vous venez de configurer en examinant l’adresse IP et/ou son adresse Mac.
1. Une fois qu&#39;un périphérique a été trouvé, cochez la case et sélectionnez Approuver.
1. Vérifiez que l&#39;écran est configuré pour Lecture via le lanceur d&#39;URL.
1. Appuyez sur Menu sur votre télécommande, accédez à Système, puis appuyez sur Entrée sur Lecture via
1. Accédez au menu -> Réseau -> Paramètres réseau du serveur et appuyez sur Entrée.
1. Accédez à l’adresse du serveur et saisissez l’URL d’accès MagicInfo et appuyez sur Terminé.
1. Configuration de TLS à utiliser ou à ne pas utiliser selon le cas
1. Accédez au port et sélectionnez le numéro de port sur le serveur.
1. Cliquez sur Enregistrer une fois que les options sont prêtes.



