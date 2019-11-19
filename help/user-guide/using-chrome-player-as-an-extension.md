---
title: Utilisation de Chrome Player comme extension
seo-title: Utilisation de Chrome Player comme extension
description: 'null'
seo-description: 'null'
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Utilisation de Chrome Player comme extension {#using-chrome-player}

Le lecteur ChromeOS peut être installé en tant que module externe Chrome Browser en mode développeur sans nécessiter de périphérique de lecteur Chrome réel.

>[!CAUTION]
>
> Il est recommandé d’utiliser Chrome Player comme extension de résolution des problèmes pour des démonstrations rapides, le débogage et la résolution des problèmes des clients. Ce mécanisme ne doit pas être utilisé pour les déploiements de production qui nécessitent le mode kiosque et la gestion centrale.

Suivez cette page pour en savoir plus sur l’installation du lecteur chrome en tant qu’extension de navigateur.

1. Cliquez ici pour télécharger la dernière version de Chrome Player.

1. Décompressez et enregistrez-le sur le disque.

1. Ouvrez le navigateur Chrome, cliquez sur le menu à 3 points et sélectionnez **Plus d’outils** dans **Extensions** situé dans le coin supérieur droit ou accédez directement à `chrome://extensions`.

1. Activez le mode **Développeur** depuis le coin supérieur droit.

1. Cliquez sur **Charger les fichiers décompressés** dans le coin supérieur gauche et chargez le lecteur Chrome non compressé.

1. Vérifiez le plug-in AEM Screens Chrome Player s’il est disponible dans la liste des extensions.

1. Ouvrez un nouvel onglet et cliquez sur l’icône Applications dans le coin supérieur gauche ou accédez directement à `chrome://apps`.

1. Cliquez sur **AEM Screens Plugin** pour lancer Chrome Player.
   >[!NOTE]
   >
   > Par défaut, le lecteur est lancé en mode plein écran. Appuyez sur **esc** pour quitter le mode plein écran.


## Conseils de débogage avancés {#advanced-debugging-tips}

1. Une fois que le lecteur a téléchargé le contenu localement, vous pouvez parcourir le contenu téléchargé localement en accédant à `http://localhost:24502`.

   >[!NOTE]
   >
   > Si l’URL mentionnée ci-dessus ne fonctionne pas, cela signifie que le lecteur ne se voit pas attribuer un affichage ou que le contenu n’a pas été téléchargé correctement. Vérifiez l’onglet réseau pour le JSON de configuration du lecteur afin de voir si les détails corrects sont obtenus par le lecteur et pour tout problème réseau en cours de téléchargement.

1. Vous pouvez cliquer avec le bouton droit et inspecter trois calques du lecteur de chrome
   **Contenu** de débogage : Cliquez avec le bouton droit de la souris et examinez le contenu pour déboguer le contenu en cours d’exécution (un seul élément doit s’appeler "Inspect" dans le menu contextuel).

   **Microprogramme** de débogage : Affichez l’interface utilisateur d’administration, puis cliquez avec le bouton droit de la souris et examinez le code du microprogramme (lecteur) (vous devez avoir la possibilité d’inspecter et d’inspecter la page d’arrière-plan et de simuler le redémarrage du navigateur).

   **Page** d’arrière-plan du débogage : Affichez l’interface utilisateur de l’administrateur, puis cliquez avec le bouton droit et examinez la page d’arrière-plan (pour les services en arrière-plan tels que le serveur http).

## Mise à niveau de Player Extension {#upgrading-player}

Suivez les étapes ci-dessous pour mettre à niveau l’extension du lecteur si une nouvelle version du lecteur est publiée. Vous pouvez également suivre les instructions ci-dessous pour tester les scénarios de mise à niveau :

1. Fermer toutes les instances de chrome et de lecteur en cours d’exécution
1. Renommer l’ancien dossier avec les fichiers du lecteur
1. Extrayez le nouveau fichier compressé au même emplacement que l’ancien dossier.
1. Lancez Chrome et accédez à `chrome://extensions`
1. Vérifiez l’icône du lecteur et cliquez sur le bouton Actualiser ou Actualiser.