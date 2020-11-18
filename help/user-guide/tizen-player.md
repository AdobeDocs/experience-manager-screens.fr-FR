---
title: Lecteur Tizen
description: Cette page décrit l'installation et le fonctionnement de Tizen Player.
translation-type: tm+mt
source-git-commit: b439cfab068dcbbfab602ad8d31aaa2781bde805
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 1%

---


# Mise en oeuvre de Tizen Player {#tizen-player}

## Installation de Tizen Player {#installing-tizen-player}

Pour mettre en oeuvre Tizen Player pour AEM Screens, procédez comme suit :

1. Accédez à la page Téléchargements [**du lecteur**](https://download.macromedia.com/screens/) AEM 6.5 pour télécharger Tizen Player.

1. Installez le fichier Tizen player (.zip) depuis l’ordinateur local.

1. Obtenez l&#39;adresse IP de votre ordinateur local.

   >[!NOTE]
   >Pour **Mac** et **Windows** , tapez la commande `ifconfig` dans le terminal.

1. Depuis l’utilitaire Terminal, accédez au même répertoire que le dossier du programme d’installation décompressé et vérifiez si l’hôte local fonctionne.

   >[!NOTE]
   >Pour **Mac**, tapez `http://localhost` et vérifiez si le `http` serveur est en cours d’exécution.

1. Le lecteur Tizen téléchargera le programme d&#39;installation à partir du serveur local.

1. Copiez les deux fichiers extraits `AEMScreensPlayer.wgt` et `sssp_config.xml` dans `/Library/WebServer/Documents`.

### Mises à jour de configuration sur le périphérique SamSung {#config-updates}

Suivez les étapes ci-dessous sur le périphérique Samsung pour terminer l&#39;installation du lecteur AEM Screens sur le périphérique :

1. Cliquez sur le bouton **Accueil** de la télécommande Samsung.
1. Sélectionnez Lecteur **** d’URL dans les **paramètres**.
1. Sélectionnez **Remote** dans le mode développeur.
1. Installez l’application Web et entrez l’adresse IP de votre ordinateur.
AEM Screens Player doit s&#39;installer automatiquement sur le périphérique Samsung.


