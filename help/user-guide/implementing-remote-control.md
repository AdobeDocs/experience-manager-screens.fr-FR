---
title: Mettre en œuvre la commande à distance
seo-title: Impementing the Remote Control
description: Consultez cette page pour en savoir plus sur la fonction de commande à distance Screens.
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
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: 6cd68194bf3128464ec368f3e7fd69d20925c3d6
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 100%

---

# Utiliser la commande à distance Screens  {#implementing-remote-control}

La fonction de commande à distance facilite l’accès à l’interface utilisateur d’administration, au sélecteur de canaux ou à des fonctionnalités telles que Effacer le cache et recharger. En outre, elle vous permet de voir la version locale du micrologiciel et les informations système du lecteur. Ceci est particulièrement utile, car il peut être difficile de connecter une souris et d’utiliser des appareils de production hors de portée, et encore plus si le lecteur a perdu la connexion à AEM. Cela est également utile lorsque vous utilisez Samsung RMS, car la différence de résolution peut rendre très difficile la localisation et l’ouverture de l’interface utilisateur d’administration à l’aide d’une souris.

## Combinaisons de touches courantes de commande à distance {#using-common-remote-control}

Sur tous les lecteurs, vous pouvez utiliser les combinaisons de touches suivantes dans la commande à distance Screens :

1. Activer/désactiver l’interface utilisateur d’administration : Ctrl + 1
1. Activer/désactiver le sélecteur de canaux : Ctrl + 2
1. Vider le cache : Ctrl + Alt + 3
1. Recharger le lecteur : Ctrl + 4

## Combinaisons de touches de commande à distance spécifiques à Tizen {#using-tizen-remote-control}

Pour le lecteur Tizen, vous pouvez utiliser soit la télécommande matérielle, soit la télécommande logicielle disponible dans Samsung RMS pour accéder à ces fonctionnalités :

1. A : activer/désactiver l’interface utilisateur d’administration
1. B : activer/désactiver le sélecteur de canaux
1. C : vider le cache
1. D : recharger le lecteur

## Remarques supplémentaires sur l’utilisation {#using-additional-remote-control}

1. Lorsque l’interface utilisateur d’administration est ouverte, vous pouvez utiliser les flèches vers le haut et vers le bas pour naviguer entre les onglets et afficher les informations.
1. Lorsque le sélecteur de canaux est ouvert, vous pouvez utiliser les flèches vers le haut et vers le bas pour naviguer dans les canaux et vous pouvez appuyer sur la touche Entrée (ou le bouton au centre des flèches sur la télécommande) pour changer de canal.

La figure suivante illustre l’utilisation des touches sur une télécommande Samsung :
![image](assets/tizen/remote.png)

>[!NOTE]
>Si vous définissez les valeurs de configuration de l’appareil enableAdminUI et/ou enableOSD sur false, la télécommande ne pourra pas basculer entre l’interface utilisateur d’administration et le sélecteur de canaux. Vous ne pourrez pas non plus utiliser les touches fléchées pour naviguer dans l’interface utilisateur d’administration ou les canaux. Cependant, vous pouvez toujours vider le cache et recharger le lecteur. Vous pouvez désactiver la fonction de commande à distance si l’une des combinaisons de clavier est en conflit avec votre contenu interactif en utilisant ce code :

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
