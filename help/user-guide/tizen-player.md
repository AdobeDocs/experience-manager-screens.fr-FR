---
title: Lecteur Tizen
description: Cette page décrit l’installation et le fonctionnement du lecteur Tizen.
translation-type: ht
source-git-commit: b3209d1dcce6defff347f288c704a1e7ea075ecf
workflow-type: ht
source-wordcount: '230'
ht-degree: 100%

---


# Implémentation du lecteur Tizen {#tizen-player}

## Installation du lecteur Tizen {#installing-tizen-player}

Pour mettre en œuvre le lecteur Tizen avec AEM Screens, procédez comme suit :

1. Accédez à la page [**Téléchargements de lecteurs AEM 6.5**](https://download.macromedia.com/screens/) pour télécharger le lecteur Tizen.

1. Installez le fichier du lecteur Tizen (.zip) à partir de l’ordinateur local.

## Configuration du serveur local et extraction des fichiers ZIP {#setting-local-server}

Suivez les étapes ci-dessous pour configurer le serveur local et copier les fichiers extraits :

1. Obtenez l’adresse IP de votre ordinateur local.
   >[!NOTE]
   >Consultez la documentation officielle pour savoir comment activer le serveur local sur votre plateforme.

1. Depuis le terminal, accédez au même répertoire que le dossier du programme d’installation décompressé et vérifiez que l’hôte local fonctionne.

1. Le lecteur Tizen télécharge ensuite le programme d’installation à partir du serveur local.

1. Copiez les deux fichiers extraits tels que `AEMScreensPlayer.wgt` et `sssp_config.xml` dans le répertoire racine de votre serveur local.

### Configuration des mises à jour sur le périphérique Samsung {#config-updates}

Suivez les étapes ci-dessous sur le périphérique Samsung pour effectuer l’installation du lecteur AEM Screens :

1. Accédez à votre périphérique Samsung.

1. Cliquez sur le bouton **Accueil** à l’aide de la télécommande du périphérique et sélectionnez **Paramètres du lanceur d’URL**.

1. Entrez l’adresse IP de votre serveur localhost.

1. Sélectionnez **À distance** dans **Mode développeur**.

1. Cliquez sur le bouton **Accueil** de la télécommande du périphérique et sélectionnez **Lanceur d’URL**.

1. Le lecteur AEM Screens devrait alors être automatiquement installé et lancé sur votre appareil Samsung.



