---
title: Mise en oeuvre du lecteur cloud
seo-title: Implementing Cloud Player
description: Consultez cette page pour en savoir plus sur la mise en oeuvre du lecteur cloud.
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: 718ef76b620accd7096be2e4b7ac53658cb7fce7
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Mise en oeuvre du lecteur cloud  {#implementing-cloud-player}

Cette section décrit la mise en oeuvre du lecteur cloud.

>[!NOTE]
>
>La compatibilité du lecteur Cloud requiert un navigateur moderne avec prise en charge de PWA pour garantir des performances homogènes sur divers appareils.

## Installation de Cloud Player {#installing-cloud-player}

L’installation du lecteur cloud peut varier selon les plateformes. En règle générale, toute plateforme disposant d’un navigateur moderne peut exécuter l’application du lecteur cloud en procédant comme suit :

1. Ouvrez le navigateur et saisissez la variable [URL du lecteur cloud](https://player.adobescreens.com) dans la barre d’adresse.
1. Le navigateur vérifie que le lecteur cloud est installable, puis affiche une icône d’installation dans la barre d’adresse.

![image](/help/user-guide/assets/cloud-player-install.png)

1. Cliquez sur l’icône d’installation et cliquez sur le bouton d’installation dans la boîte de dialogue de confirmation. Le lecteur cloud sera installé en tant qu’application autonome sur votre appareil et peut être lancé à l’aide d’une icône.

### Option d’installation du lecteur cloud {#cloud-player-install-option}

1. L’option d’installation d’un PWA est également connue sous le nom de fonctionnalité &quot;Ajouter à l’écran d’accueil&quot; ou A2HS.  La prise en charge de l’installation de PWA à partir du web varie en fonction du navigateur et de la plateforme.
1. Chaque navigateur comporte des critères différents pour vérifier si l’application du PWA est installable ou non. En règle générale, le navigateur vérifie ces informations (plus de détails ici) :
   * Si l’application dispose d’un fichier json manifeste avec un minimum de clés requises pour l’installation de l’application sur la plateforme, c’est-à-dire son nom, ses icônes, son adresse start_url, afficher
   * Si l’application comporte un fichier de travail de service avec un écouteur d’événement de récupération.
   * L’application doit être diffusée via https.
1. L’option d’installation peut être visible à différents emplacements dans différents navigateurs et types d’appareils. Certains navigateurs peuvent masquer l’icône d’installation dans la barre de menus des options.

## Approvisionnement en masse du lecteur cloud {#bulk-provisioning}

Pour effectuer la mise en service en masse du lecteur cloud sur plusieurs appareils :

1. Choisissez une solution MDM qui prend en charge l’exécution d’un navigateur avec une URL en mode kiosque.
1. Vous pouvez appliquer les mêmes configurations à tous les appareils en procédant comme suit :
   1. Hébergez config.json sur un serveur de sorte qu’il soit accessible, par exemple : https://&lt;config_server_host>/config.json
   1. Pour installer le lecteur cloud et appliquer les configurations hébergées, utilisez l’URL du lecteur cloud comme : https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host>
   1. L’application du lecteur Cloud recherche config.json à la racine de &lt;config_server_host>, analysez le fichier config.json pour obtenir les configurations personnalisées et appliquer ces configurations.
   1. Ces configurations seront appliquées à chaque rechargement du lecteur.

## Approvisionnement en masse sur Chrome OS {#bulk-provisioning-chrome}

Pour en savoir plus sur la mise en service en bloc sur Chrome OS, voir : [Installation de Cloud Player sur Chrome OS](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## Configuration requise sur les instances AEM {#bulk-provisioning-config-aem}

En fonction du type d’instance AEM, sélectionnez l’un des guides suivants pour activer l’AEM et le lecteur cloud CORS :
* [AEM sur site/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

