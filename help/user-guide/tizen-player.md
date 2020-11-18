---
title: Lecteur Tizen
description: Cette page décrit l'installation et le fonctionnement de Tizen Player.
translation-type: tm+mt
source-git-commit: 5275a4ff79404e946d5aa0806fc705ab3bce2fcd
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 1%

---


# Mise en oeuvre de Tizen Player {#tizen-player}

## Installation de Tizen Player {#installing-tizen-player}

Pour mettre en oeuvre Tizen Player pour AEM Screens, procédez comme suit :

1. Accédez à la page Téléchargements [**du lecteur**](https://download.macromedia.com/screens/) AEM 6.5 pour télécharger Tizen Player.

1. Installez le fichier Tizen player (.zip) depuis l’ordinateur local.

## Configuration du serveur local et extraction des fichiers Zip {#setting-local-server}

Suivez les étapes ci-dessous pour configurer le serveur local et copier les fichiers extraits :

1. Obtenez l&#39;adresse IP de votre ordinateur local.

   >[!NOTE]
   >Vous pouvez obtenir l&#39;adresse IP à partir du terminal de votre ordinateur à l&#39;aide des commandes suivantes :
   >* **Mac**: `ifconfig`
   >* **Windows**: `ipconfig`


1. Depuis l’utilitaire Terminal, accédez au même répertoire que le dossier du programme d’installation décompressé et vérifiez si l’hôte local fonctionne.

   >[!NOTE]
   >Pour **Mac**, tapez `http://localhost` et vérifiez si le `http` serveur est en cours d’exécution.

1. Le lecteur Tizen téléchargera le programme d&#39;installation à partir du serveur local.

1. Copiez les deux fichiers extraits `AEMScreensPlayer.wgt` et `sssp_config.xml` dans `/Library/WebServer/Documents`.

### Configuration des mises à jour sur le périphérique Samsung {#config-updates}

Suivez les étapes ci-dessous sur le périphérique Samsung pour terminer l&#39;installation du lecteur AEM Screens sur le périphérique :

1. Accédez à votre périphérique Samsung et pointez vers votre serveur localhost.
1. Sélectionnez Paramètres **du lanceur** d’URL et saisissez l’adresse IP de votre serveur hôte local.
1. Installez l’application Web.
1. Sélectionnez **Remote** dans le mode **** Développeur.
1. Le AEM Screens Player doit désormais automatiquement début l&#39;installation sur votre Samsung.


