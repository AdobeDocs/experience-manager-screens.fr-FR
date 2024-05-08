---
title: Utilisation du lecteur Chrome comme extension
description: Découvrez comment installer le lecteur Chrome en tant qu’extension de navigateur pour AEM Screens.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 19%

---

# Utilisation du lecteur Chrome comme extension {#using-chrome-player}

Le lecteur Chrome OS peut être installé en tant que module externe de navigateur Chrome en mode développeur sans nécessiter de périphérique de lecteur Chrome réel.

>[!CAUTION]
>
> Il est recommandé d’utiliser le lecteur Chrome comme extension de résolution des problèmes pour des démonstrations rapides, le débogage et la résolution des problèmes des clients. N’utilisez pas ce mécanisme pour les déploiements de production qui nécessitent le mode kiosque et la gestion centrale.

Consultez cette page pour plus d’informations sur l’installation du lecteur Chrome en tant qu’extension de navigateur.

1. Cliquez sur [here](https://download.macromedia.com/screens/) pour télécharger le dernier lecteur Chrome.

1. Décompressez et enregistrez le fichier d’installation sur le disque.

1. Ouvrez le navigateur Chrome, cliquez sur le menu à 3 points, puis cliquez sur **Autres outils** de **Extensions** dans le coin supérieur droit ou accédez directement à `chrome://extensions`.

1. Activez l’option **Développeur** dans le coin supérieur droit.

1. Cliquez sur **Chargement décompressé** dans le coin supérieur gauche et chargez le lecteur Chrome décompressé.

1. Vérifiez si le module du lecteur AEM Screens Chrome est disponible dans la liste des extensions.

1. Ouvrez un nouvel onglet et cliquez sur l’icône Applications dans le coin supérieur gauche ou accédez directement à `chrome://apps`.

1. Cliquez sur **Module externe AEM Screens** vous pouvez donc lancer le lecteur Chrome.

   >[!NOTE]
   >
   > Par défaut, le lecteur est lancé en mode plein écran. Presse **Échap** pour quitter le mode plein écran.


## Conseils de débogage avancés {#advanced-debugging-tips}

1. Lorsque le lecteur a téléchargé du contenu localement, vous pouvez parcourir le contenu téléchargé localement en accédant à `http://localhost:24502`.

   >[!NOTE]
   >
   > Si l’URL mentionnée ci-dessus ne fonctionne pas, cela signifie que le lecteur ne se voit pas attribuer un affichage ou que le contenu n’a pas été téléchargé correctement. Consultez l’onglet réseau du fichier JSON de configuration du lecteur pour voir si le lecteur obtient les détails corrects et pour tout problème réseau en cours de téléchargement.

1. Cliquez avec le bouton droit de la souris et examinez trois calques du lecteur Chrome.
   **Déboguer le contenu**: cliquez avec le bouton droit et examinez le contenu pour déboguer le contenu en cours d’exécution (un seul élément appelé &quot;Inspect&quot; doit s’afficher dans le menu contextuel).

   **Déboguer le microprogramme**: affichez l’interface utilisateur d’administration, puis cliquez avec le bouton droit et examinez le code du micrologiciel (lecteur) pour le déboguer. (Il doit y avoir une option pour inspecter et inspecter la page d’arrière-plan et simuler le redémarrage du navigateur.)

   **Déboguer la page d’arrière-plan**: affichez l’interface utilisateur d’administration, puis cliquez avec le bouton droit et examinez la page d’arrière-plan (pour les services en arrière-plan tels que le serveur http).

## Mise à niveau de l’extension du lecteur {#upgrading-player}

Suivez les étapes ci-dessous pour mettre à niveau l’extension du lecteur si une nouvelle version du lecteur est publiée. Vous pouvez également suivre les instructions ci-dessous pour tester des scénarios de mise à niveau :

1. Fermez toutes les instances de Chrome et du lecteur en cours d’exécution
1. Renommez l’ancien dossier avec les fichiers du lecteur
1. Extrayez le nouveau fichier compressé au même emplacement que l’ancien dossier.
1. Lancez Chrome et accédez à `chrome://extensions`
1. Cochez l’icône du lecteur et cliquez sur le bouton Actualiser ou Charger à nouveau .
