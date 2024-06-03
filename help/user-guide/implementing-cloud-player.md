---
title: Implémenter Cloud Player
description: Découvrez comment mettre en œuvre Cloud Player.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 6720e20f5254e869bde814bd167730e426d0f8fe
workflow-type: ht
source-wordcount: '854'
ht-degree: 100%

---

# Implémenter Cloud Player {#implementing-cloud-player}

AEM Screens propose traditionnellement des applications de lecteur natives distinctes pour différentes plateformes, notamment ChromeOS, Windows, Android™ et `Tizen`. Cependant, en réponse aux besoins changeants de nos utilisateurs et utilisatrices, nous avons introduit une solution innovante : Cloud Player AEM Screens.

Cloud Player représente une différence significative par rapport à nos applications natives précédentes. Il s’agit d’une application web progressive (PWA), hébergée sur un serveur. Grâce à cette approche transformatrice, nos clientes et clients disposent d’un lecteur indépendant des plateformes qui s’exécute directement dans un navigateur web.

L’accès à Cloud Player est aussi simple que de consulter `https://player.adobescreens.com`. Les utilisateurs et utilisatrices peuvent l’installer sur leur appareil, quelle que soit la plateforme, et profiter d’une expérience de signalétique numérique transparente. La compatibilité du lecteur cloud dépend de la présence d’un navigateur moderne avec prise en charge des PWA, assurant des performances homogènes sur divers appareils. Dites adieu aux mises à jour manuelles et bonjour à un lecteur qui fournit automatiquement des correctifs et des fonctionnalités, en vous assurant que vous disposez toujours des dernières fonctionnalités à portée de main. Ce passage à un lecteur cloud PWA marque une évolution passionnante de nos offres de signalétique numérique et rend le lecteur plus accessible, polyvalent et convivial que jamais.

Cette section décrit l’implémentation de Cloud Player.

>[!NOTE]
>
>La compatibilité de Cloud Player requiert un navigateur moderne avec prise en charge de PWA pour garantir des performances homogènes sur divers appareils.

## Installation de Cloud Player {#installing-cloud-player}

L’installation de Cloud Player peut varier selon les plateformes. En règle générale, toute plateforme disposant d’un navigateur moderne peut exécuter l’application Cloud Player en procédant comme suit :

1. Ouvrez le navigateur et saisissez l’[URL de Cloud Player](https://player.adobescreens.com/content/dam/universal-player/firmware.html) dans la barre d’adresses.
1. Le navigateur vérifie que Cloud Player peut être installé, puis affiche une icône d’installation dans la barre d’adresses.

   ![image](/help/user-guide/assets/cloud-player-install.png)

1. Cliquez sur l’icône d’installation et le bouton d’installation dans la boîte de dialogue de confirmation. Cloud Player est installé en tant qu’application autonome sur votre appareil et peut être lancé à l’aide d’une icône.

>[!NOTE]
>
>### Option d’installation de Cloud Player {#cloud-player-install-option}
>
>1. L’option d’installation d’une PWA est également connue sous le nom de fonctionnalité « Ajouter à l’écran d’accueil » ou A2HS. La prise en charge de l’installation de PWA à partir du web varie en fonction du navigateur et de la plateforme.
>1. Chaque navigateur comporte des critères différents pour vérifier si l’application PWA peut être ou non installée. En règle générale, le navigateur peut vérifier (plus de détails ici) :
>
>* Si l’application dispose d’un fichier JSON manifeste avec un minimum de clés requises pour l’installation de l’application sur la plateforme, c’est-à-dire nom, icônes, start_url, affichage.
>* Si l’application comporte un fichier de worker de service avec un listener d’événement de récupération.
>* L’application doit être diffusée via https.
>
>1. L’option d’installation peut être visible à différents emplacements dans différents navigateurs et types d’appareils. Certains navigateurs peuvent masquer l’icône d’installation dans la barre de menus des options.

## Approvisionnement en bloc de Cloud Player {#bulk-provisioning}

Pour effectuer l’approvisionnement en bloc de Cloud Player sur plusieurs appareils :

1. Choisissez une solution MDM qui prend en charge l’exécution d’un navigateur avec une URL en mode Kiosk.
1. Vous pouvez appliquer les mêmes configurations à tous les appareils en procédant comme suit :

   1. Hébergez config.json sur un serveur de sorte qu’il soit accessible, par exemple : `https://<config_server_host>/config.json`.
   1. Pour installer Cloud Player et appliquer les configurations hébergées, utilisez l’URL de Cloud Player, par exemple : `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`.
   1. L’application Cloud Player recherche config.json à la racine de &lt;config_server_host>, et analyse ensuite le fichier config.json pour obtenir les configurations personnalisées et appliquer ces configurations.
   1. Ces configurations seront appliquées à chaque rechargement du lecteur.

## Approvisionnement en bloc sur le système d’exploitation Chrome {#bulk-provisioning-chrome}

En savoir plus sur la mise en service en masse sur Chrome OS. Voir [Installation de Cloud Player sur Chrome OS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/chromeos-install-cloud-player). &lt;!-- `https://www.adobe.com/go/aem_screens_cloud_player_en` >

## Configuration requise sur les instances AEM {#bulk-provisioning-config-aem}

En fonction du type d’instance AEM, cliquez sur l’un des guides suivants pour activer CORS entre AEM et Cloud Player :

* [AEM On-Promise/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams) <!-- `https://www.adobe.com/go/aem_screens_cors_ams_en` -->

* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs) <!-- `https://www.adobe.com/go/aem_screens_cors_aemaacs_en` -->


>[!NOTE]
>
>## Abandon des applications Chrome par Google
>
>1. Applications Chrome sur le matériel Chrome OS :
>
>Google abandonne activement les applications Chrome au profit des applications PWA, avec une migration prévue jusqu’en janvier 2025. Par conséquent, l’application du lecteur AEM Screens sous Chrome OS ne fonctionne plus en fonction de la chronologie partagée. Adobe invite les utilisateurs et utilisatrices qui utilisent actuellement le lecteur Chrome en production à planifier leur transition vers Cloud Player Screens.
>
>1. Lecteur d’extension Chrome sur Mac, Windows et Linux® :
>
>En raison du processus d’obsolescence de Google, à partir de la version 114 de Google Chrome, le lecteur d’extension Chrome Screens n’est plus pris en charge. Nous vous conseillons vivement de passer à Cloud Player Screens pour toutes vos exigences de développement et de test.

## Prise en charge hors ligne de la récupération de contenu externe {#offline-support}

Dans divers scénarios d’utilisation, les canaux peuvent nécessiter la récupération de contenu à partir d’une source externe (par exemple, des widgets météorologiques ou des applications monopages intégrées à Commerce) qui ne peuvent pas, par nature, fournir une prise en charge hors ligne. Pour activer la fonctionnalité hors ligne pour ces cas d’utilisation spécifiques, le lecteur cloud prend en charge l’en-tête personnalisé.

Cloud Player utilise une stratégie de mise en cache favorisant le réseau (Network First), ce qui signifie qu’il tente de récupérer du contenu du réseau (puis de mettre à jour le cache avec la dernière version), avant de revenir au contenu mis en cache s’il est disponible. Pour mettre en œuvre la prise en charge hors ligne de cette récupération de contenu, l’en-tête personnalisé doit être inclus dans la requête. Ensuite, la requête avec l’en-tête personnalisé sera mise en cache sur le lecteur, ce qui facilite l’accès hors ligne au contenu tout en conservant la stratégie de mise en cache Network First (réseau en priorité).

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```

## Commentaires

Nous apprécions vos commentaires. Faites-nous part de ce que vous pensez via ce [formulaire](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).
