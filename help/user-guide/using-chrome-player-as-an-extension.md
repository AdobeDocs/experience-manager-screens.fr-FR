---
title: Utilisation du lecteur Chrome comme extension
seo-title: Utilisation du lecteur Chrome comme extension
description: 'null'
seo-description: 'null'
translation-type: tm+mt
source-git-commit: 1753009451e4bed75eb8241bcca887f7abe2f77b

---


# Utilisation du lecteur Chrome comme extension {#using-chrome-player}

Le lecteur Chrome OS peut être installé en tant que module du navigateur Chrome en mode Développeur sans que vous ayez à utiliser de lecteur Chrome réel.

>[!CAUTION]
>
> Il est recommandé d’utiliser le lecteur Chrome comme extension de résolution des problèmes pour des démonstrations rapides, le débogage et la résolution des problèmes des clients. Ce mécanisme ne doit pas être utilisé pour les déploiements de production qui nécessitent le mode kiosque et une gestion centrale.

Consultez cette page pour en savoir plus sur l’installation du lecteur Chrome en tant qu’extension de navigateur.

1. Cliquez [ici](https://download.macromedia.com/screens/) pour télécharger la dernière version du lecteur Chrome.

1. Décompressez et enregistrez le fichier d’installation sur le disque.

1. Ouvrez le navigateur Chrome, cliquez sur le menu à 3 points et sélectionnez **Plus d’outils** dans **Extensions** situé dans le coin supérieur droit ou accédez directement à `chrome://extensions`.

1. Activez le mode **Développeur** depuis l’angle supérieur droit.

1. Cliquez sur **Charger les fichiers décompressés** dans l’angle supérieur gauche et chargez le lecteur Chrome décompressé.

1. Vérifiez si le module Lecteur Chrome AEM Screens est disponible dans la liste des extensions.

1. Ouvrez un nouvel onglet et cliquez sur l’icône Applications dans l’angle supérieur gauche ou accédez directement à `chrome://apps`.

1. Cliquez sur le module **AEM Screens** pour lancer le lecteur Chrome.
   >[!NOTE]
   >
   > Par défaut, le lecteur est lancé en mode plein écran. Appuyez sur **Échap** pour quitter le mode plein écran.


## Conseils de débogage avancés {#advanced-debugging-tips}

1. Une fois que le lecteur a téléchargé le contenu localement, vous pouvez parcourir le contenu téléchargé localement en accédant à `http://localhost:24502`.

   >[!NOTE]
   >
   > Si l’URL mentionnée ci-dessus ne fonctionne pas, cela signifie qu’aucun affichage n’a été affecté au lecteur ou que le contenu n’a pas été téléchargé correctement. Vérifiez l’onglet réseau du JSON de configuration du lecteur afin de voir si le lecteur obtient les détails corrects et pour tout problème réseau en matière de téléchargement.

1. Vous pouvez cliquer avec le bouton droit et inspecter trois couches du lecteur Chrome
   **Déboguer le contenu** : cliquez avec le bouton droit et examinez le contenu pour déboguer le contenu en cours d’exécution (un seul élément dénommé « Inspecter » devrait s’afficher dans le menu contextuel).

   **Déboguer le microgiciel** : affichez l’interface utilisateur d’administration, puis cliquez avec le bouton droit et examinez le code du micrologiciel (lecteur) (vous devez avoir la possibilité d’inspecter, d’inspecter la page d’arrière-plan et de simuler le redémarrage du navigateur).

   **Débloquer la page d’arrière-plan** : affichez l’interface utilisateur d’administration, puis cliquez avec le bouton droit et examinez la page d’arrière-plan (pour les services en arrière-plan tels que le serveur http).

## Mise à niveau de l’extension du lecteur {#upgrading-player}

Suivez les étapes ci-dessous pour mettre à niveau l’extension du lecteur si une nouvelle version du lecteur est publiée. Vous pouvez également suivre les instructions ci-dessous pour tester des scénarios de mise à niveau :

1. Fermez toutes les instances de Chrome et du lecteur en cours d’exécution
1. Renommez l’ancien dossier avec les fichiers du lecteur
1. Extrayez le nouveau fichier compressé au même emplacement que l’ancien dossier.
1. Lancez Chrome et accédez à `chrome://extensions`
1. Vérifiez l’icône du lecteur et cliquez sur le bouton Actualiser ou Charger de nouveau.