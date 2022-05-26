---
title: Mise en oeuvre du contrôle à distance
seo-title: Impementing the Remote Control
description: Consultez cette page pour en savoir plus sur la fonction de contrôle à distance de Screens.
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: ff59c3748ea69a37ca68e81e5bf753881e8464b0
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Utilisation de la commande à distance Screens  {#implementing-remote-control}

La fonctionnalité de contrôle à distance facilite l’accès à l’interface utilisateur d’administration, au sélecteur de canal ou à des fonctionnalités telles que Effacer le cache et recharger. En outre, il vous fournit une méthode pour afficher la version du microprogramme local et les informations système sur le lecteur. Cela s’avère particulièrement utile, car il peut s’avérer difficile de connecter une souris et de fonctionner sur des appareils de production hors de portée, et encore plus si le lecteur a perdu la connexion avec AEM. Cela s’avère également utile lors de l’utilisation de Samsung RMS, car la différence de résolution peut rendre très difficile la localisation et l’ouverture de l’interface utilisateur d’administration à l’aide d’une souris.

## Combinaisons de clés de contrôle à distance courantes {#using-common-remote-control}

Sur tous les lecteurs, vous pouvez utiliser les combinaisons de touches suivantes dans la télécommande Screens :

1. Activer/désactiver l’interface utilisateur d’administration - Ctrl + 1
1. Activer/désactiver le sélecteur de canal - Ctrl + 2
1. Effacer le cache - Ctrl + ALT + 3
1. Recharger le lecteur - Ctrl + 4

## Tizer les combinaisons de clés de contrôle à distance spécifiques {#using-tizen-remote-control}

Spécifique au lecteur Tizen, vous pouvez utiliser la télécommande matérielle ou la télécommande logicielle disponible dans Samsung RMS pour accéder à ces fonctionnalités :

1. A - Activation/désactivation de l’interface utilisateur d’administration
1. B - Activer/désactiver le sélecteur de canal
1. C - Effacer le cache
1. D - Rechargement du lecteur

## Remarques supplémentaires sur l’utilisation {#using-additional-remote-control}

1. Une fois l’interface utilisateur d’administration ouverte, vous pouvez utiliser les flèches haut et bas pour parcourir les onglets afin d’afficher les informations dans les onglets.
1. Une fois le sélecteur de canal ouvert, vous pouvez utiliser les flèches haut et bas pour naviguer dans les canaux et appuyer sur la touche Entrée (ou sur le bouton situé au centre des flèches de la télécommande) pour changer de canal.

Le diagramme suivant illustre l’utilisation des clés sur une télécommande Samsung :
![image](assets/tizen/remote.png)

>[!NOTE]
>Si vous définissez les valeurs de configuration de l’appareil enableAdminUI et/ou enableOSD sur false, la télécommande n’activera pas l’interface utilisateur d’administration et le sélecteur de canal. Vous ne pourrez pas non plus utiliser les touches fléchées pour naviguer dans l’interface utilisateur ou les canaux d’administration. Cependant, vous pouvez toujours effacer le cache et recharger le lecteur. Vous pouvez désactiver la fonction de contrôle à distance si l’une des combinaisons de clavier est en conflit avec votre contenu interactif à l’aide de ce code :

```javascript require(/['util/ScreensDisplay'/], function() /{window.ScreensDisplay.ignoreRemoteControl = true;/}); ```
