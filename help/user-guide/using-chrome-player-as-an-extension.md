---
title: Utilisation du lecteur Chrome comme extension
description: Découvrez comment installer le lecteur Chrome en tant qu’extension de navigateur pour AEM Screens.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 100%

---

# Utilisation du lecteur Chrome comme extension {#using-chrome-player}

Le lecteur Chrome OS peut être installé en tant que plug-in du navigateur Chrome en mode de développement sans que vous ayez à utiliser de lecteur Chrome réel.

>[!CAUTION]
>
> Il est recommandé d’utiliser le lecteur Chrome comme extension de résolution des problèmes pour des démonstrations rapides, le débogage et la résolution des problèmes de la clientèle. N’utilisez pas ce mécanisme pour les déploiements de production qui nécessitent le mode kiosque et une gestion centrale.

Consultez cette page pour obtenir des informations sur l’installation du lecteur Chrome en tant qu’extension de navigateur.

1. Cliquez [ici](https://download.macromedia.com/screens/) pour télécharger la dernière version du lecteur Chrome.

1. Décompressez-la et enregistrez-la sur le disque.

1. Ouvrez le navigateur Chrome, cliquez sur le menu à 3 points et cliquez sur **Plus d’outils** dans **Extensions** situé dans le coin supérieur droit ou accédez directement à `chrome://extensions`.

1. Activez le **mode Développement** dans l’angle supérieur droit de l’écran.

1. Cliquez sur **Charger les fichiers décompressés** dans l’angle supérieur gauche et chargez le lecteur Chrome décompressé.

1. Vérifiez si le module Lecteur Chrome AEM Screens est disponible dans la liste des extensions.

1. Ouvrez un nouvel onglet et cliquez sur l’icône Applications dans l’angle supérieur gauche ou accédez directement à `chrome://apps`.

1. Cliquez sur le **plug-in AEM Screens** afin de lancer le lecteur Chrome.

   >[!NOTE]
   >
   > Par défaut, le lecteur est lancé en mode plein écran. Appuyez sur **Échap** pour quitter le mode plein écran.


## Conseils de débogage avancés {#advanced-debugging-tips}

1. Lorsque le lecteur a téléchargé le contenu localement, vous pouvez parcourir le contenu téléchargé localement en accédant à `http://localhost:24502`.

   >[!NOTE]
   >
   > Si l’URL mentionnée ci-dessus ne fonctionne pas, cela signifie qu’aucun affichage n’a été affecté au lecteur ou que le contenu n’a pas été téléchargé correctement. Vérifiez l’onglet réseau du JSON de configuration du lecteur afin de voir si le lecteur obtient les détails corrects et pour tout problème réseau en matière de téléchargement.

1. Cliquez avec le bouton droit de la souris et inspectez trois calques du lecteur Chrome.
   **Déboguer le contenu** : cliquez avec le bouton droit et inspectez le contenu pour déboguer le contenu en cours d’exécution (un seul élément dénommé « Inspecter » devrait s’afficher dans le menu contextuel).

   **Déboguer le micrologiciel** : affichez l’interface d’utilisation de l’administration, puis cliquez avec le bouton droit et inspectez le code du micrologiciel (lecteur) pour le déboguer. (Il doit y avoir une option pour inspecter et inspecter la page d’arrière-plan et simuler le redémarrage du navigateur.)

   **Déboguer la page d’arrière-plan** : affichez l’interface d’utilisation de l’administration, puis cliquez avec le bouton droit et inspectez la page d’arrière-plan (pour les services en arrière-plan tels que le serveur HTTP).

## Mise à niveau de l’extension du lecteur {#upgrading-player}

Suivez les étapes ci-dessous pour mettre à niveau l’extension du lecteur si une nouvelle version du lecteur est publiée. Vous pouvez également suivre les instructions ci-dessous pour tester des scénarios de mise à niveau :

1. Fermez toutes les instances de Chrome et du lecteur en cours d’exécution.
1. Renommez l’ancien dossier avec les fichiers du lecteur
1. Extrayez le nouveau fichier compressé au même emplacement que l’ancien dossier.
1. Lancez Chrome et accédez à `chrome://extensions`
1. Vérifiez l’icône du lecteur et cliquez sur le bouton Actualiser ou Charger à nouveau.
